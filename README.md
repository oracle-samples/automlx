# AutoMLx Demo Notebooks

This repository contains demo notebooks (sample code) for the AutoMLx (automated machine learning and explainability) package from Oracle Labs.

The notebooks are intended to show how to initialize, train and explain an AutoML model in a few lines of code. The notebooks also cover many of the advanced features available in the AutoMLx package.

## Installation

Pre-executed copies of each of the demo notebooks are available as html files, which can be viewed without installing anything.

To run the demo notebooks yourself:
1. Create a free trial account and a new project on the [OCI Data Science](https://apexapps.oracle.com/pls/apex/r/dbpm/livelabs/view-workshop?wid=673) service.
2. Install the [AutoMLx conda pack](https://docs.oracle.com/en-us/iaas/data-science/using/conda-automlx-fam.htm).
3. Import, open and run the demo notebooks.

## Documentation

The demo notebooks in this repository serve as supplementary documentation for the AutoMLx package. The AutoMLx class documentation is available on [docs.oracle.com](https://docs.oracle.com/en-us/iaas/tools/automlx/latest/latest/).

## Examples

These demo notebooks cover the five machine learning tasks supported by the AutoMLx package:
 - [Classification](./demos/OracleAutoMLx_Classification.ipynb) [(html)](./demos/OracleAutoMLx_Classification.html),
 - [Regression](./demos/OracleAutoMLx_Regression.ipynb) [(html)](./demos/OracleAutoMLx_Regression.html),
 - [Forecasting](./demos/OracleAutoMLx_Forecasting.ipynb) [(html)](./demos/OracleAutoMLx_Forecasting.html),
 - [Anomaly Detection](./demos/OracleAutoMLx_AnomalyDetection.ipynb) [(html)](./demos/OracleAutoMLx_AnomalyDetection.html),
 - [Text Classification](./demos/OracleAutoMLx_Classification_Text.ipynb) [(html)](./demos/OracleAutoMLx_Classification_Text.html),
 - [Image Classification](./demos/OracleAutoMLx_ImageClassification.ipynb) [(html)](./demos/OracleAutoMLx_ImageClassification.html),
 - [Recommendation](./demos/OracleAutoMLx_Recommendation.ipynb) [(html)](./demos/OracleAutoMLx_Recommendation.html),
 - [Fairness](./demos/OracleAutoMLx_Fairness.ipynb) [(html)](./demos/OracleAutoMLx_Fairness.html),
 - [Simple API](./demos/OracleAutoMLx_train_model.ipynb) [(html)](./demos/OracleAutoMLx_train_model.html), and
 - [Execution Engine Setup](./demos/OracleAutoMLx_ExecutionEngineSetup.ipynb) [(html)](./demos/OracleAutoMLx_ExecutionEngineSetup.html).

## Help

Create a GitHub [issue](https://github.com/oracle-samples/automlx/issues).

## Contributing

This project welcomes contributions from the community. Before submitting a pull request, please [review our contribution guide](./CONTRIBUTING.md).

## Security

Please consult the [security guide](./SECURITY.md) for our responsible security vulnerability disclosure process.

## License

Copyright (c) 2024 Oracle and/or its affiliates.

Released under the Universal Permissive License v1.0 as shown at [https://oss.oracle.com/licenses/upl/](https://oss.oracle.com/licenses/upl/).

## Third-Party Software

Developers choosing to distribute a binary implementation of this project are responsible for obtaining and providing all required licenses and copyright notices for the third-party code used in order to ensure compliance with their respective open source licenses.

## Third-Party Datasets

The AutoMLx demo notebooks download and use several third-party datasets to showcase AutoMLx functionality.

| Dataset            | License                                                                                                                  | Description                                                                                                                                                                                                           |
|--------------------|--------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Airlines           | No License                                                                                                               | The dataset consists of a large amount of records, containing flight arrival and departure details for all the commercial flights within the USA, from October 1987 to April 2008.                                    |
| M4 Competition     | [GPL 3.0](https://www.gnu.org/licenses/gpl-3.0.en.html) with [MOFC Terms](https://mofc.unic.ac.cy/terms-and-conditions/) | We select a series from the finance sector with weekly collection frequency (Finance W142) from the M4 forecasting competition.                                                                                       |
| Census Income      | [CC By 4.0](https://creativecommons.org/licenses/by/4.0/legalcode)                                                       | Census Income Dataset is used to predict whether income exceeds $50K/yr based on the 1994 US Census data. It is also frequently known as the "Adult" dataset.                                                         |
| Credit Card Fraud  | [ODC DbCL v1.0](https://opendatacommons.org/licenses/odbl/1-0/)                                                          | The dataset contains transactions made by credit cards in September 2013 by European cardholders. This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. |
| California Housing | No License                                                                                                               | This dataset was derived from the 1990 U.S. census, using one row per census block group. The target variable is the median house value for California districts.                                                     |
| Newsgroup 20       | No License                                                                                                               | The 20 Newsgroups data set is a collection of approximately 20,000 newsgroup documents, partitioned (nearly) evenly across 20 different newsgroups.                                                                   |
| PneumoniaMNIST     | [CC By 4.0](https://creativecommons.org/licenses/by/4.0/legalcode)                                                       | The PneumoniaMNIST is consist of 5,856 pediatric chest X-Ray images.                                                                   |
| MovieLens     | [Custom](https://files.grouplens.org/datasets/movielens/ml-32m-README.html)                                                       | MovieLens 100K movie ratings. Stable benchmark dataset. 100,000 ratings from 1000 users on 1700 movies.                                                                   |