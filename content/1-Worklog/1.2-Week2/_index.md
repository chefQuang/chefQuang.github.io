---
title: "Week 2 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Deepen understanding of Amazon S3 and AWS IoT Core.
* Design the system architecture for the Local AQI Forecasting System.
* Establish the Data Contract and prepare the historical dataset for simulation.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn Amazon S3 basics: <br>&emsp; + Buckets & Objects <br>&emsp; + Storage Classes & Lifecycle <br>&emsp; + IAM Policies for S3 <br> - **Practice:** Create S3 bucket, upload/download files via Console & CLI. | 06/08/2026 | 06/08/2026 | <https://docs.aws.amazon.com/s3/> |
| 3 | - Learn AWS IoT Core concepts: <br>&emsp; + Things & Device Registry <br>&emsp; + X.509 Certificates & IoT Policies <br>&emsp; + MQTT Message Broker <br> - **Practice:** Register a Thing and generate mTLS certificates. | 06/09/2026 | 06/09/2026 | <https://docs.aws.amazon.com/iot/> |
| 4 | - **System Architecture Design:** <br>&emsp; + Collaborate with the team to draw the end-to-end data flow (Edge -> AWS IoT Core -> Data Lake -> Analytics). <br>&emsp; + Define integration points between Ingestion and Data Engineering modules. | 06/10/2026 | 06/10/2026 | |
| 5 | - **Data Contract Definition:** <br>&emsp; + Standardize the JSON telemetry schema (`device_id`, `pm2_5`, `timestamp`) with the DE team. <br>&emsp; + Define the MQTT topic structure (`telemetry/aqi/dev`). | 06/11/2026 | 06/11/2026 | |
| 6 | - **Data Preparation:** <br>&emsp; + Research and extract historical air quality data from the OpenAQ dataset. <br>&emsp; + Clean and format the dataset to match the defined JSON schema for upcoming simulations. | 06/12/2026 | 06/12/2026 | <https://openaq.org/> |

### Week 2 Achievements:

* Mastered Amazon S3 fundamentals and successfully managed cloud storage resources via both CLI and Web Console.
* Grasped AWS IoT Core mechanisms, particularly the MQTT pub/sub model and mTLS security for IoT devices.
* Completed the high-level architecture diagram for the Local AQI Forecasting data pipeline.
* Finalized the Data Contract and JSON payload schema, ensuring strict alignment between the Ingestion and Data Engineering teams.
* Successfully acquired, cleaned, and evaluated the historical OpenAQ dataset, laying the groundwork for the Python telemetry simulator.