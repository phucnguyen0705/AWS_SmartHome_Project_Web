---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Master designing and optimizing Amazon DynamoDB NoSQL databases to store Smart Home device states.
* Learn and deploy Backend Services on Amazon EC2 servers to process automated device control logic.
* Integrate Amazon DynamoDB with EC2 Backend servers to create efficient, reliable, and flexible device state processing workflows.

---

### Weekly Tasks Schedule:

| Day | Task | Start Date | End Date | Resource Link |
| :---: | :--- | :---: | :---: | :--- |
| **Mon** | - Explore Amazon DynamoDB NoSQL service: <br>&emsp; + Tables, Items, and Attributes concepts <br>&emsp; + Partition Key, Sort Key, and Secondary Indexes <br>- **Hands-on:** Create DynamoDB tables for storing Smart Home device states | 22/06/2026 | 22/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tue** | - Learn IAM Role security mechanisms for EC2 instances (IAM Instance Profile): <br>&emsp; + EC2 Instance Profile concepts and attaching IAM Roles to EC2 <br>&emsp; + Configure IAM Policies granting EC2 permissions to access DynamoDB | 23/06/2026 | 23/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wed** | - **Hands-on:** <br>&emsp; + Write a Python or Node.js Backend Service running on EC2 to process Smart Home device state updates <br>&emsp; + Attach IAM Role to EC2 for secure DynamoDB access without hardcoded credentials | 24/06/2026 | 24/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thu** | - Learn automated processing logic on EC2 (Worker Service & Polling Mechanism): <br>&emsp; + Build background worker processes (Daemon Processes) on EC2 <br>&emsp; + Configure periodic polling mechanisms or API handling for state changes | 25/06/2026 | 25/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Fri** | - **Hands-on:** <br>&emsp; + Deploy background Worker Services on EC2 (using Systemd or PM2) <br>&emsp; + Test automated execution workflows: When a Smart Home device state changes, the EC2 service automatically processes predefined backend logic | 26/06/2026 | 26/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

---

### Week 3 Outcomes:

#### 1. DynamoDB Database Design & Management for Smart Home
* **Proficiency in NoSQL Data Structure Optimization**:
  * Designed and initialized DynamoDB tables holding Smart Home device state data.
  * Optimized Partition Key and Sort Key selection to ensure high-performance queries with low latency.
* **Detailed Data Operations**: Successfully executed CRUD operations to update, read, and modify device states or parameters via AWS Console and AWS CLI.

#### 2. Backend Service Development & Deployment on EC2
* **Building Backend Services on EC2**:
  * Developed and packaged Backend code (Python/Node.js) on EC2 acting as the central processing unit for the Smart Home system.
  * Configured Environment Variables and optimized server hardware utilization for EC2 workloads.
* **IAM Role Security & Authorization for EC2**:
  * Created dedicated IAM Instance Profiles for EC2 granting least privilege access to DynamoDB.
  * Ensured EC2 applications operate securely without storing hardcoded Access Keys or Secret Keys in source code.

#### 3. Automated Workflow Integration Between EC2 Backend & DynamoDB
* **Background Worker Setup on EC2**: Successfully managed Worker Services as background processes (Systemd/PM2) on EC2 to perform continuous processing.
* **Automated Smart Home Logic Execution**:
  * Integrated EC2 Backend with DynamoDB tables using AWS SDK.
  * Verified execution flows: Upon receiving device state modification requests, the EC2 server executes business logic and updates DynamoDB accurately.
