---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Monitor cloud data flow using Amazon CloudWatch metrics.
* Secure the local project repository using Git best practices.
* Perform an end-to-end integration test and hand over the Raw Zone to the DE team.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn Amazon CloudWatch basics: <br>&emsp; + Dashboards, Logs, and Metrics. <br>&emsp; + Metric statistics (Average vs. Sum) and periods. | 06/29/2026 | 06/29/2026 | <https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/> |
| 3 | - **System Monitoring:** <br>&emsp; + Track `Rule executions` in IoT Core metrics. <br>&emsp; + Monitor S3 upload success rates. <br>&emsp; + Setup Error Actions to push failed rules to CloudWatch Logs. | 06/30/2026 | 06/30/2026 | |
| 4 | - **Code Security:** <br>&emsp; + Create a strict `.gitignore` file. <br>&emsp; + Exclude sensitive assets (`certs/`, `.env`), large datasets (`data/`, `*.csv`), and Python caches from version control. | 07/01/2026 | 07/01/2026 | <https://git-scm.com/docs/gitignore> |
| 5 | - **End-to-End Testing:** <br>&emsp; + Run the simulator for an extended period to generate a large batch of telemetry data. <br>&emsp; + Verify data integrity and folder structure in the S3 bucket with the team. | 07/02/2026 | 07/02/2026 | |
| 6 | - **Module Handover:** <br>&emsp; + Document the Ingestion pipeline details in `README.md`. <br>&emsp; + Push clean, secure code to the team's shared GitHub repository. <br>&emsp; + Officially hand over the S3 Raw Zone to the Data Engineering team for ETL processing. | 07/03/2026 | 07/03/2026 | |

### Week 5 Achievements:

* Successfully navigated Amazon CloudWatch to debug, monitor, and validate data ingestion metrics, converting statistics correctly to view accurate traffic volumes.
* Secured the source code repository by implementing strict Git ignore rules, preventing the accidental exposure of AWS private keys and large data files.
* Conducted a successful end-to-end system test, proving that data flows seamlessly from the local Python script, through AWS IoT Core, and into precisely partitioned S3 folders.
* Finalized the documentation for the Ingestion phase and smoothly transitioned the data pipeline to the Data Engineering team for the next phase of the project.