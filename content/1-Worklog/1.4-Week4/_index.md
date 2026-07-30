---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Configure AWS IoT Rules to intercept and route incoming MQTT messages.
* Resolve IAM permissions and Trust Policy issues for cross-service interaction.
* Implement a Direct-to-S3 ingestion pipeline for raw telemetry data.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn AWS IoT Message Routing: <br>&emsp; + IoT Rule SQL syntax. <br>&emsp; + Available Rule Actions. | 06/22/2026 | 06/22/2026 | <https://docs.aws.amazon.com/iot/latest/developerguide/iot-rules.html> |
| 3 | - **Data Routing Setup:** <br>&emsp; + Create an IoT Rule with the statement `SELECT * FROM 'telemetry/aqi/dev'`. <br>&emsp; + Attempt initial integration with Kinesis Firehose. | 06/23/2026 | 06/23/2026 | |
| 4 | - **Security & Troubleshooting:** <br>&emsp; + Resolve `sts:AssumeRole` rejection errors. <br>&emsp; + Modify IAM Trust Policies to allow `iot.amazonaws.com` to assume roles. | 06/24/2026 | 06/24/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html> |
| 5 | - **Pipeline Pivot:** <br>&emsp; + Bypass Firehose subscription limitations by designing a Direct-to-S3 approach. <br>&emsp; + Request and attach `s3:PutObject` policies to the IoT role. | 06/25/2026 | 06/25/2026 | <https://docs.aws.amazon.com/iot/latest/developerguide/s3-rule-action.html> |
| 6 | - **S3 Integration & Partitioning:** <br>&emsp; + Configure the S3 Rule Action. <br>&emsp; + Apply dynamic S3 Object Key: `raw/telemetry/${parse_time("yyyy/MM/dd/HH", timestamp())}/${newuuid()}.json`. | 06/26/2026 | 06/26/2026 | <https://docs.aws.amazon.com/iot/latest/developerguide/iot-sql-functions.html> |

### Week 4 Achievements:

* Mastered the creation of AWS IoT Rules to filter and process telemetry data using SQL-like syntax.
* Deepened understanding of AWS Identity and Access Management (IAM), specifically troubleshooting Trust Policies and cross-service roles.
* Successfully pivoted the ingestion architecture to a Direct-to-S3 model, ensuring the project timeline wasn't blocked by account limitations.
* Implemented automated data partitioning in Amazon S3 by injecting timestamp and UUID functions directly into the IoT Rule key configuration.