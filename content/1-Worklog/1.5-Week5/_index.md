---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
## Week 5 Objectives:

* Evaluate and analyze the performance of the Smart Home Backend system running on Amazon EC2 instances behind an Nginx Reverse Proxy.
* Optimize Nginx configuration, Backend runtime environment, and DynamoDB database queries to reduce latency during device command execution.
* Establish an Auto Scaling Group mechanism with Nginx upstream routing to automatically adjust EC2 compute resources according to real-time traffic demand.

---

### Tasks to Implement This Week:

| Day | Task | Start Date | End Date | Resource / Doc |
| :---: | :--- | :---: | :---: | :--- |
| **Mon** | - Performance analysis of current Nginx & EC2 Backend: <br>&emsp; + Monitor CPU, Memory, Network I/O utilization, and Nginx connection metrics <br>&emsp; + Identify bottlenecks in API request flows through the Nginx Reverse Proxy <br>- **Hands-on:** Use benchmarking tools to measure response time latency for Nginx & EC2 | 2026-07-06 | 2026-07-06 | [EC2 Performance](https://aws.amazon.com/ec2/) |
| **Tue** | - Optimize Nginx & Database Query operations: <br>&emsp; + Tune Nginx configurations (worker_processes, keepalive, buffer limits, gzip) <br>&emsp; + Optimize Backend code and DynamoDB queries to improve response times <br>- **Hands-on:** Implement caching (In-memory/Redis) to temporarily cache device states | 2026-07-07 | 2026-07-07 | [DynamoDB Best Practices](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html) |
| **Wed** | - Research Auto Scaling solutions (EC2 Auto Scaling & Nginx Routing): <br>&emsp; + Learn Launch Template concepts, Auto Scaling Policies, and Nginx Upstream Balancing <br>&emsp; + Define scaling thresholds based on CPU/RAM metrics and active connections | 2026-07-08 | 2026-07-08 | [EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html) |
| **Thu** | - **Hands-on:** <br>&emsp; + Create a Launch Template packaging standard Backend code and Nginx Reverse Proxy configs <br>&emsp; + Provision Auto Scaling Group (ASG) defining minimum/maximum EC2 instance counts <br>&emsp; + Configure auto-scaling policy rules to scale out/in based on workload changes | 2026-07-09 | 2026-07-09 | |
| **Fri** | - **Testing & Evaluation:** <br>&emsp; + Execute stress tests (simulated high load) to evaluate Nginx Proxy and Auto Scaling responsiveness <br>&emsp; + Measure and compare EC2 Backend response times before and after optimization | 2026-07-10 | 2026-07-10 | |

---

### Week 5 Achievements:

#### 1. Performance Optimization for Nginx Reverse Proxy & EC2 Backend
* **Latency Reduction**:
  * Successfully optimized Nginx parameters (keepalive connections, buffer size) and Backend execution logic, significantly cutting API response latency for Smart Home control commands.
  * Integrated an in-memory caching mechanism for device state management, reducing direct queries to DynamoDB and preserving system compute capacity.
* **Hardware Resource Efficiency**:
  * Fine-tuned OS parameters and runtime settings to ensure stable EC2 Backend operation behind Nginx, keeping CPU and Memory utilization within optimal ranges.

#### 2. Automated EC2 Auto Scaling & Nginx Routing Deployment
* **Standardized Launch Template Packaging**: Created a reusable Launch Template incorporating the complete runtime environment, Nginx Reverse Proxy, Backend codebase, and security configurations for automatic instance cloning.
* **Flexible Auto Scaling Group (ASG) Setup**:
  * Configured ASG to monitor workload metrics continuously (Target Tracking Policy based on CPU Utilization and active connection load).
  * System automatically provisions new EC2 instances during traffic spikes and terminates idle instances when traffic normalizes, optimizing operational costs.

#### 3. Load Testing & Auto-scaling Verification
* **Stress Test Verification**: Successfully simulated high concurrent traffic against the Nginx Proxy and Backend; Auto Scaling Group detected load thresholds promptly and scaled out EC2 instances automatically.
* **Overall Assessment**: The Smart Home Backend deployed on EC2 + Nginx reached an optimized state, maintaining high throughput and self-adapting seamlessly to real-world traffic fluctuations.