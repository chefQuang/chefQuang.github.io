---
title: "Blog 2: MQTT & Pub/Sub"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

### WHY REST API ISN'T ALWAYS THE ANSWER: THE POWER OF PUB/SUB AND MQTT IN DISTRIBUTED SYSTEMS

When designing communication between services, clients, or devices, REST API (HTTP) is often the default choice. The traditional client-server model—where a client sends a request and waits for the server's response—is highly familiar to most developers. 

However, as systems scale, especially when handling real-time data streams from edge gateways or integrating various cloud services, the synchronous Request/Response model of HTTP begins to reveal critical bottlenecks. 

In this post, I want to share insights into the Publish/Subscribe (Pub/Sub) model—specifically through the MQTT protocol—and how it fundamentally shapes Event-Driven Architectures on AWS.

---

#### 1. THE LIMITATIONS OF SYNCHRONOUS MODELS (HTTP/REST)

Imagine a real-time data collection system. If you rely on REST, your devices must continuously call the API (polling) to check for new commands, or your server must block and wait for a device to respond. This approach presents several challenges:

* **Timeouts:** If the network connection is unstable or drops, HTTP requests will inevitably time out.
* **Resource Heavy:** Maintaining open HTTP connections and parsing heavy HTTP headers consumes significant processing resources and network bandwidth.
* **Tight Coupling:** Services become strictly dependent on one another. If Service A crashes, Service B's API calls will immediately fail, potentially causing a cascading failure across the system.

#### 2. THE FREEDOM OF PUB/SUB AND MQTT

Unlike HTTP, MQTT is a protocol purposely built for systems requiring lightweight, asynchronous, and minimalist communication. In the Pub/Sub model, a **Message Broker** sits in the middle to orchestrate traffic.

* **Publisher:** Simply publishes data to a specific "Topic" and moves on to its next task. It does not need to know who (if anyone) will read the message.
* **Subscriber:** Subscribes to that specific "Topic." Whenever new data arrives, the Broker automatically pushes it to the subscriber.

This separation, known as **Decoupling**, is the core of Event-Driven Architecture. System components don't even need to know of each other's existence. The Broker absorbs traffic spikes and handles message distribution. Furthermore, MQTT's ultra-small payload significantly reduces network bandwidth costs.

#### 3. EXPANDING THE EVENT-DRIVEN ECOSYSTEM ON AWS

The Pub/Sub mindset extends far beyond just device communication. AWS provides a robust ecosystem that allows you to apply this Event-Driven architecture to your entire backend:

* **AWS IoT Core:** Acts as a massive, fully managed MQTT Broker. It seamlessly manages millions of connections secured by mTLS certificates (secure credentials) and provides intelligent message routing.
* **Amazon SNS (Simple Notification Service):** A pure Pub/Sub service for backend systems, allowing you to "fan-out" notifications simultaneously to multiple destinations.
* **Amazon EventBridge:** Allows you to build a centralized Event Bus for your entire enterprise, enabling AWS services, external SaaS applications, and your own custom code to communicate entirely via "events."

#### 4. REAL-WORLD APPLICATION: IOT TELEMETRY PIPELINE

Let's look at a practical scenario: Handling data from an MQTT Gateway. Instead of the gateway making direct, synchronous database calls, a decoupled architecture looks like this:

1. The Gateway publishes telemetry data to **AWS IoT Core** securely via the MQTT protocol.
2. The **AWS IoT Rules Engine** (acting as an SQL-based event filter) intercepts this message.
3. It automatically triggers a routing action, pushing the raw data into **Amazon Kinesis Firehose** to be batched and stored in an **Amazon S3** Data Lake.
4. Simultaneously, if the telemetry data exceeds a specific threshold, the rule triggers an **AWS Lambda** function to dispatch an immediate alert.

With this flow, no single server is "blocked" waiting for another process to finish. Everything is naturally and asynchronously triggered by events.

---

### CONCLUSION

REST API remains the king of traditional client-server communication. But as we step into the world of IoT, distributed gateways, and Microservices, synchronous thinking becomes a barrier. 

Transitioning to Pub/Sub and Event-Driven Architecture not only improves system scalability and fault tolerance but also provides the flexibility to seamlessly attach new features to your system without breaking existing logic.

*What are your thoughts on Event-Driven Architecture? Let me know!*

---
**Original Post & References:**
* [My Original Post on FCAJ Group](https://www.facebook.com/groups/awsstudygroupfcj/posts/2228776647887295)
* [AWS Architecture Blog: Enhancing existing workloads with Event-Driven Architecture](https://aws.amazon.com/blogs/architecture/enhancing-existing-workloads-with-event-driven-architecture/)
* [AWS IoT Blog: Modernizing connected device applications](https://aws.amazon.com/blogs/iot/modernizing-connected-device-applications/)