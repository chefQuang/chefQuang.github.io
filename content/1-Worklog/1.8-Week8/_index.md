---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Transition to the Machine Learning phase of the project.
* Set up the ML development environment.
* Train baseline time-series forecasting models using the processed AQI data.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn Amazon SageMaker basics: <br>&emsp; + SageMaker Notebook Instances / Studio. <br>&emsp; + Managed ML training environments. | 07/20/2026 | 07/20/2026 | <https://docs.aws.amazon.com/sagemaker/> |
| 3 | - **ML Environment Setup:** <br>&emsp; + Provision a SageMaker Notebook instance (or set up a local Jupyter environment connected to AWS). <br>&emsp; + Load the engineered dataset from S3 into a Pandas DataFrame using `boto3`. | 07/21/2026 | 07/21/2026 | <https://boto3.amazonaws.com/v1/documentation/api/latest/index.html> |
| 4 | - **Algorithm Research:** <br>&emsp; + Research suitable Time-Series forecasting models for air quality (e.g., ARIMA, Prophet, or LSTM). <br>&emsp; + Define evaluation metrics (RMSE, MAE). | 07/22/2026 | 07/22/2026 | |
| 5 | - **Baseline Model Training:** <br>&emsp; + Split the dataset into Training and Testing sets. <br>&emsp; + Train a baseline forecasting model (e.g., ARIMA or Facebook Prophet) to predict PM2.5 levels. | 07/23/2026 | 07/23/2026 | |
| 6 | - **Model Evaluation:** <br>&emsp; + Evaluate the model's performance on the test set. <br>&emsp; + Identify underfitting/overfitting issues and plan for hyperparameter tuning. | 07/24/2026 | 07/24/2026 | |

### Week 8 Achievements:

* Gained foundational knowledge of Amazon SageMaker and established a robust ML workspace connected directly to the AWS Data Lake.
* Successfully integrated the `boto3` SDK to securely fetch engineered datasets from Amazon S3 into the Jupyter environment.
* Researched and selected appropriate time-series algorithms and statistical metrics tailored for air quality forecasting.
* Trained and evaluated the first baseline ML model, establishing a performance benchmark for future optimizations.