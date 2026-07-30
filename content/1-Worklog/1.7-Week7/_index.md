---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Master serverless interactive querying using Amazon Athena.
* Perform Data Analytics and Feature Engineering on the cleaned AQI dataset.
* Validate data quality for the upcoming Machine Learning phase.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn Amazon Athena basics: <br>&emsp; + Serverless query architecture. <br>&emsp; + Integration with AWS Glue Data Catalog. | 07/13/2026 | 07/13/2026 | <https://docs.aws.amazon.com/athena/> |
| 3 | - **Data Analytics:** <br>&emsp; + Connect Amazon Athena to the S3 Processed Zone. <br>&emsp; + Run standard SQL queries directly on Parquet files to analyze AQI trends. | 07/14/2026 | 07/14/2026 | |
| 4 | - **Feature Engineering (Part 1):** <br>&emsp; + Extract time-series features (e.g., hour of day, day of week) using SQL. <br>&emsp; + Calculate rolling averages for PM2.5 and PM10 to smooth out noise. | 07/15/2026 | 07/15/2026 | |
| 5 | - **Feature Engineering (Part 2):** <br>&emsp; + Identify historical pollution spikes and correlate them with temperature/humidity metrics. | 07/16/2026 | 07/16/2026 | |
| 6 | - **Data Validation:** <br>&emsp; + Validate the consistency of the engineered features. <br>&emsp; + Export the final, feature-rich dataset for ML model training. | 07/17/2026 | 07/17/2026 | |

### Week 7 Achievements:

* Acquired hands-on experience with Amazon Athena, running complex SQL queries directly on S3 without provisioning databases.
* Successfully extracted meaningful business insights from the transformed AQI dataset.
* Performed advanced feature engineering, including calculating rolling averages and time-based metrics, which are crucial for time-series forecasting.
* Ensured high data quality and readiness for the ML pipeline by thoroughly validating the processed datasets.