---
title: "Blog 1: AWS Lambda Memory"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# INCREASING AWS LAMBDA MEMORY CAN REDUCE COSTS – HERE'S WHY

When configuring AWS Lambda, it is a common misconception that choosing the lowest memory tier (128 MB) is the best way to save money. In reality, because AWS allocates CPU power proportionally to the configured memory, increasing memory can significantly reduce execution time, which may ultimately lower your overall compute costs.

Key points to know:

* Memory configuration in Lambda does not just allocate RAM; it proportionally increases CPU power, network capabilities, and I/O throughput.
* Lambda pricing is calculated in GB-seconds (Allocated Memory × Execution Time). If a function with higher memory runs significantly faster, the total GB-seconds billed can be lower than running a low-memory function for a longer duration.
* Increasing memory is highly effective for CPU-bound workloads (e.g., data parsing, image resizing, heavy data transformations) and functions using large libraries like pandas or NumPy.
* It is less effective for I/O-bound tasks that spend most of their time waiting for external API or database responses, as the extra CPU cannot speed up external latency.
* Do not rely solely on the `Max Memory Used` metric to determine your configuration, as a function might not use all its RAM but could still be starving for CPU.
* It is highly recommended to use **AWS Lambda Power Tuning** (for active testing) or **AWS Compute Optimizer** (for historical data analysis) to find the perfect balance between cost and performance.

This optimization approach demonstrates that instead of asking "What is the lowest memory setting?", cloud engineers should ask "Which memory setting provides the best balance between execution speed and cost?"

**Original Post & References:**
* [My Original Post on FCAJ Group](https://www.facebook.com/groups/awsstudygroupfcj/posts/2228234364608190)
* [AWS Compute Optimizer](https://aws.amazon.com/compute-optimizer/)
* [AWS Lambda Power Tuning (GitHub)](https://github.com/alexcasalboni/aws-lambda-power-tuning)