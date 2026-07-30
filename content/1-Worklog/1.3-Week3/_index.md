---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Set up the local development environment for the Python IoT Simulator.
* Configure mTLS security and successfully connect to AWS IoT Core.
* Develop a script to publish simulated AQI data to the cloud.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Set up Python virtual environment. <br> - Install required libraries (`paho-mqtt`, `pandas`). | 06/15/2026 | 06/15/2026 | <https://pypi.org/project/paho-mqtt/> |
| 3 | - **IoT Security Setup:** <br>&emsp; + Download and securely store X.509 certs, private keys, and Root CA. <br>&emsp; + Create and attach strict AWS IoT Policies to the Thing certificate. | 06/16/2026 | 06/16/2026 | <https://docs.aws.amazon.com/iot/latest/developerguide/iot-policies.html> |
| 4 | - **Simulator Development:** <br>&emsp; + Write a basic MQTT client script to load cleaned OpenAQ CSV data. <br>&emsp; + Publish a single JSON payload to the test topic. | 06/17/2026 | 06/17/2026 | |
| 5 | - **Simulator Optimization:** <br>&emsp; + Implement an asynchronous loop to simulate multiple AQI stations concurrently. <br>&emsp; + Format timestamps and payload precisely according to the Data Contract. | 06/18/2026 | 06/18/2026 | |
| 6 | - **Resiliency & Testing:** <br>&emsp; + Add error handling and auto-reconnect logic to the MQTT client. <br>&emsp; + Run local tests to verify real-time data streaming to the `telemetry/aqi/dev` topic. | 06/19/2026 | 06/19/2026 | |

### Week 3 Achievements:

* Successfully configured the Python environment and installed necessary dependencies for IoT simulation.
* Implemented strict mTLS authentication, allowing the local simulator to communicate securely with the AWS IoT Core broker.
* Developed a robust Python script capable of reading historical AQI data and converting it into continuous MQTT telemetry streams.
* Optimized the simulator to handle concurrent publishing for multiple virtual stations with auto-reconnect capabilities.
* Verified that messages correctly arrive at the designated AWS IoT topic in the agreed-upon JSON format.