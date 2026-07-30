---
title: "Blogs Posted"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

This section lists and introduces the technical blogs I have researched, written, and posted to the [AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj) community during my internship.

### [Blog 1 - INCREASING AWS LAMBDA MEMORY CAN REDUCE COSTS – HERE'S WHY](3.1-Blog1/)
This blog explains the hidden relationship between AWS Lambda memory configuration, CPU allocation, execution time, and total compute costs. It highlights a counter-intuitive cloud concept: how increasing memory for CPU-bound workloads can actually decrease overall costs by significantly reducing execution time. The post also recommends using tools like AWS Lambda Power Tuning to find the optimal balance between performance and cost.

### [Blog 2 - WHY REST API ISN'T ALWAYS THE ANSWER: THE POWER OF PUB/SUB AND MQTT](3.2-Blog2/)
This blog discusses the limitations of synchronous HTTP/REST APIs in modern distributed systems and introduces the Publish/Subscribe (Pub/Sub) model using the lightweight MQTT protocol. It explores how leveraging AWS services—such as AWS IoT Core and Amazon EventBridge—enables a highly scalable, decoupled Event-Driven Architecture, which is especially critical for robust IoT telemetry data pipelines.