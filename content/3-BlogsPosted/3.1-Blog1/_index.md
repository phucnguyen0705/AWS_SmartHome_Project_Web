---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# [AMAZON EMR ON EC2] OPTIMIZING MONITORING & DEBUGGING WITH 5 NEW FEATURES

Hello everyone,

When operating Big Data processing systems on Amazon EMR, monitoring and debugging often take up a considerable amount of time: logs scattered across multiple nodes, difficulty in matching EMR Steps with YARN Applications, and the need to set up complex SSH/Proxy tunnels just to open web UIs...

With the latest updates from AWS, 5 major features have been added to simplify the entire monitoring and troubleshooting workflow.

---

### New Features:

* **Real-time Log Streaming to CloudWatch:** Automatically pushes Step logs, Spark Driver, and Executor logs to CloudWatch as they are generated. Allows customizing Log Groups, KMS encryption, and fast log filtering using CloudWatch Logs Insights without waiting to upload to S3 or SSHing into nodes.
* **Per-Step S3 Log Management:** Enables configuring separate S3 paths and KMS keys for individual steps, ensuring strict security and access control in multi-tenant environments.
* **Access Live UIs Directly from the Console:** Access YARN ResourceManager UI and Tez UI directly on the AWS Console without any manual SSH tunneling, Proxy setups, or port opening.
* **Map EMR Steps Directly to YARN Application IDs:** Displays the YARN Application ID directly on the Step details page, allowing quick navigation to the YARN UI / Spark History or searching container logs on S3 immediately.
* **Expanded Custom Metrics & Flexible Monitoring:** Collects detailed metrics (1-minute intervals) for Hadoop, YARN, and HBase via the CloudWatch Agent. Enables updating metric configurations on running clusters without restarting, and supports exporting data to Prometheus / Grafana.

---

### Cost Optimization:

* **Eliminate Proxy & Bastion Host Infrastructure:** Opening Live UIs (YARN UI/Tez UI) directly on the AWS Console removes the need to maintain intermediate servers, SSH Tunnels, or Proxies. This reduces infrastructure maintenance costs while improving security.
* **Optimize Mean Time to Resolution (MTTR):** Instant log querying via CloudWatch Logs Insights and direct linkage from Steps to YARN Applications help engineers find root causes quickly, reducing pipeline bottlenecks and preventing unnecessary EC2 uptime costs.

*(Note: Streaming logs and metrics to CloudWatch will incur additional costs depending on the volume of ingested data).*

---

### Use Cases & Benefits:

* **Trace and Troubleshoot Root Causes Instantly:** Jump directly from an EMR Step to the YARN UI / Spark History or inspect container logs on S3 to isolate issues in Spark/Hadoop jobs without waiting for log upload completion.
* **Centralized Monitoring & Flexible Data Export:** Integrate Hadoop, YARN, and HBase metrics seamlessly into existing monitoring setups like CloudWatch, Prometheus, or Grafana to build comprehensive observability dashboards for your entire Data Pipeline.

---

### Evaluation & Conclusion:

These new features in Amazon EMR on EC2 deliver a great experience for Data Engineers and Cloud Ops teams, significantly reducing pipeline debugging time and simplifying cluster management. You can start exploring these features on your EMR clusters today!

Thank you for reading!

---

### Official AWS Blog Post Link

* [Streamlined monitoring and debugging for Amazon EMR on EC2](https://aws.amazon.com/blogs/big-data/streamlined-monitoring-and-debugging-for-amazon-emr-on-ec2/)

---

### Article Image

![Blog post image](/static/blog_1_final.jpg)