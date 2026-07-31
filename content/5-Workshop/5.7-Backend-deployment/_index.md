---
title: "Deploy the FastAPI Backend"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

#### Overview

In this section, you will deploy the **Local AQI Forecasting & Alert System** Backend to an Amazon EC2 instance.

The Backend is built with FastAPI and provides the following functionality:

- Exposes APIs to check the system health.
- Accepts AQI alert subscription requests.
- Stores subscription information and cooldown status in Amazon DynamoDB.
- Invokes the SageMaker endpoint to generate forecast results.
- Sends alert emails through Amazon SNS.

Backend workflow:

```text
User
    → FastAPI on Amazon EC2
        → Amazon DynamoDB
        → Amazon SageMaker Endpoint
        → Amazon SNS
```

The Backend uses the EC2 instance's IAM role to access AWS services. The application is managed by `systemd`, allowing it to start automatically when the EC2 instance boots and restart if the process fails.

<!-- Add screenshot: Backend deployment architecture diagram -->

#### Contents

- [Prepare the EC2 Instance and IAM Role](5.7.1-prepare/)
- [Install and Configure the Backend](5.7.2-install/)
- [Run the Backend with systemd](5.7.3-systemd/)
- [Test the API and Alert Scheduling](5.7.4-test/)