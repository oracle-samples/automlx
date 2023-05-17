# Reporting security vulnerabilities

Oracle values the independent security research community and believes that
responsible disclosure of security vulnerabilities helps us ensure the security
and privacy of all our users.

Please do NOT raise a GitHub Issue to report a security vulnerability. If you
believe you have found a security vulnerability, please submit a report to
[secalert_us@oracle.com][1] preferably with a proof of concept. Please review
some additional information on [how to report security vulnerabilities to Oracle][2].
We encourage people who contact Oracle Security to use email encryption using
[our encryption key][3].

We ask that you do not use other channels or contact the project maintainers
directly.

Non-vulnerability related security issues including ideas for new or improved
security features are welcome on GitHub Issues.

## Security updates, alerts and bulletins

Security updates will be released on a regular cadence. Many of our projects
will typically release security fixes in conjunction with the
[Oracle Critical Patch Update][3] program. Additional
information, including past advisories, is available on our [security alerts][4]
page.

## Security-related information

We will provide security related information such as a threat model, considerations
for secure use, or any known security issues in our documentation. Please note
that labs and sample code are intended to demonstrate a concept and may not be
sufficiently hardened for production use.

## Considerations for secure use

* On Data Validation
  * Pipeline consumes data inputs using Pandas DataFrame. We recommend to perform data type validation on loading, for example, by holding the known dtype of your application data in a separate file and passing it to read_csv() utility on data loading.
* On Logging 
  * By default, logging to console is enabled and logging to file is disabled. 
  * If logging to file is desired, we attach a filehandler to the logging module which helps duplicate console output to a disk-resident file. This file is created and edited with read-write persmissions to the POSIX user executing the automl appplication. It is recommended to further harden logfile permissions to 0400 once model training is complete. 
  * We recommend logging at logging.INFO loglevel. We assume that data column names are not sensitive attributes. If this assumption does not hold for your application, we recommend implementing a transform-inverse_transfrom wrapper to anonymize columns names before passing them to the automl.Pipeline fit() and predict() calls. 
  * In rare instances, on data read failures logging.INFO may reveal the line number and contents of bad data. Thus we recommend to use pandas read_csv() utility with error_bad_lines=False argument to supress record information leakage to the logfile.
  * Logging at logging.DEBUG level is not recommended. It is for use only by individuals who also have plaintext privileges to the input data. Debug information may reveal data record attributes.
* On execution engine
  * dask (respectively, local "python multiprocessing") execution backend requires write privilidges to the /tmp directory, wherein it writes to disk, socket (respectively, filedescriptor) metadata to coordinate communication between the parallel execution threads.
  * The default directory is chosen from a platform-dependent list (e.g., on POSIX Linux it is the /tmp directory), but the user of the application can control the directory location by setting the TMPDIR, TEMP or TMP environment variables.
  * While this metadata does not contain any sensitive information, the folder in /tmp directory is created with 0600 permissions using the python tempfile module. Note that on POSIX, a process that is terminated abruptly with SIGKILL cannot automatically delete any NamedTemporaryFiles it creates.
* On pipeline serialization for model persistence
  * After training the automl pipeline, it is desirable to persist the pipeline for future use without having to retrain. The pipeline object can be exported as a pickle dump, and/or in the ONNX format (except forecasting models which may only be pickled).
  * Loading the pickled (or ONNX) pipeline object from disk to memory is equivalnet to executing code. Therefore, it is critical to ensure integrity of the serialized object. Failure to do so may expose you to arbitrary code execution (ACE).
  * We expect the automl tool to be run by a single developer, on a single host, so the impact of this vulnerability in such scenarios is limited.
* Running untrusted automl pipeline/models
  * Only if you must, execute untrusted models inside a sandbox, such as that provided by the nsjail utlity.
  * If integrity of the pipeline object is in doubt, you may consider carefully auditing the pipeline object in a sandbox.
* On Machine Learning (ML) model security
  * This library provides no protection against security attacks on the internal parameters of the ML model. [Attacks][5] can range from Data Poisoning, Membership Inference, Attribute Inference, Adversarial, Byzantine to Model Extraction. 
  * If your application requires such protections, ensuring integrity of the data input to the pipeline is a must.


[1]: mailto:secalert_us@oracle.com
[2]: https://www.oracle.com/corporate/security-practices/assurance/vulnerability/reporting.html
[3]: https://www.oracle.com/security-alerts/encryptionkey.html
[4]: https://www.oracle.com/security-alerts/
[5]: https://en.wikipedia.org/wiki/Adversarial_machine_learning
