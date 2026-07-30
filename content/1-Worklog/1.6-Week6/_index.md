---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Learn the fundamentals of Data Engineering on AWS.
* Design and implement an ETL (Extract, Transform, Load) pipeline.
* Transform raw JSON telemetry data into an optimized format for querying.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn AWS Glue concepts: <br>&emsp; + Data Catalog & Crawlers. <br>&emsp; + ETL Jobs (Visual & Script based). | 07/06/2026 | 07/06/2026 | <https://docs.aws.amazon.com/glue/> |
| 3 | - **Data Cataloging:** <br>&emsp; + Configure an AWS Glue Crawler to scan the S3 Raw Zone (`raw/telemetry/`). <br>&emsp; + Automatically infer the schema of the simulated JSON data. | 07/07/2026 | 07/07/2026 | |
| 4 | - **ETL Process Design:** <br>&emsp; + Set up an AWS Glue ETL job. <br>&emsp; + Map data fields and handle missing or outlier PM2.5/PM10 values. | 07/08/2026 | 07/08/2026 | <https://aws.amazon.com/glue/features/> |
| 5 | - **Data Transformation:** <br>&emsp; + Convert the data format from JSON to Apache Parquet for better read performance and cost efficiency. | 07/09/2026 | 07/09/2026 | |
| 6 | - **Processed Zone Setup:** <br>&emsp; + Output the cleaned and transformed Parquet files to a new S3 bucket (Processed/Cleaned Zone). <br>&emsp; + Verify data integrity post-transformation. | 07/10/2026 | 07/10/2026 | |

### Week 6 Achievements:

* Understood the core concepts of serverless data integration using AWS Glue.
* Successfully deployed Glue Crawlers to automatically discover and map the schema of incoming raw telemetry data in S3.
* Designed and executed an ETL job to clean data anomalies and handle missing values from the simulated IoT stations.
* Optimized data storage by converting heavy JSON files into the highly efficient Apache Parquet format.
* Established a structured Data Lake architecture by separating the "Raw Zone" from the "Processed Zone" in Amazon S3.