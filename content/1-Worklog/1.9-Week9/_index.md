---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:

* Optimize the Time-Series Machine Learning model.
* Automate the inference pipeline to generate continuous predictions.
* Export forecasting results to the Data Lake for visualization.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - **Model Optimization:** <br>&emsp; + Perform hyperparameter tuning on the baseline model to reduce forecasting errors (RMSE). <br>&emsp; + Compare performance between different algorithms (e.g., Prophet vs. LSTM). | 07/27/2026 | 07/27/2026 | |
| 3 | - **Inference Pipeline Design:** <br>&emsp; + Design a serverless inference flow using AWS Lambda to trigger predictions when new data arrives. | 07/28/2026 | 07/28/2026 | <https://docs.aws.amazon.com/lambda/> |
| 4 | - **Inference Automation:** <br>&emsp; + Deploy the trained model as a SageMaker Endpoint (or package it within an AWS Lambda layer). <br>&emsp; + Write a script to fetch the latest rolling averages and predict the next 24-hour PM2.5 levels. | 07/29/2026 | 07/29/2026 | |
| 5 | - **Prediction Storage:** <br>&emsp; + Format the model's output predictions into JSON/Parquet. <br>&emsp; + Automatically save the prediction results into a dedicated "Forecast Zone" in Amazon S3. | 07/30/2026 | 07/30/2026 | |
| 6 | - **Pipeline Integration Test:** <br>&emsp; + Run the Python IoT Simulator to verify the complete flow: Raw Data -> ETL -> Model Inference -> Forecast Storage. | 07/31/2026 | 07/31/2026 | |

### Week 9 Achievements:

* Successfully tuned and optimized the time-series forecasting model, significantly improving prediction accuracy for PM2.5 levels.
* Designed and implemented an automated inference pipeline utilizing serverless computing (AWS Lambda) to generate continuous forecasts.
* Established a structured storage mechanism in Amazon S3 for prediction outputs, preparing the data for the upcoming visualization phase.
* Validated the complete end-to-end cloud data pipeline, ensuring seamless integration between Data Ingestion, Data Engineering, and Machine Learning modules.