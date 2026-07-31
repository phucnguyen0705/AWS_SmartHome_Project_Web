---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

## Week 4 Objectives:

* Master data management for Smart Home user configurations and device states on Amazon DynamoDB.
* Manage, rotate, and retain Smart Home device activity logs directly on the EC2 Backend server.
* Optimize Nginx Reverse Proxy and configure centralized log management for device history retrieval and system monitoring.

---

### Tasks to Implement This Week:

| Day | Task | Start Date | End Date | Resource / Doc |
| :---: | :--- | :---: | :---: | :--- |
| **Mon** | - Data management and configuration on Amazon DynamoDB: <br>&emsp; + Design table schema for managing user profiles and Smart Home device catalogs <br>&emsp; + Standardize data structures for storing device configuration <br>- **Hands-on:** Create and test query execution on DynamoDB device configuration tables | 2026-06-29 | 2026-06-29 | [DynamoDB](https://aws.amazon.com/dynamodb/?nc2=type_a) |
| **Tue** | - Secure and optimize DynamoDB query operations: <br>&emsp; + Configure Security Groups to strictly control inbound connectivity to EC2 Backend <br>&emsp; + Optimize device data queries using Primary Keys and Secondary Indexes <br>- **Hands-on:** Write scripts to query user and device configuration from EC2 | 2026-06-30 | 2026-06-30 | |
| **Wed** | - Explore Log Management and analysis solutions on EC2: <br>&emsp; + Design directory structure for storing device logs and Nginx Access/Error logs on EC2 <br>&emsp; + Configure standardized log formats (JSON format) for device activity history | 2026-07-01 | 2026-07-01 | |
| **Thu** | - **Hands-on:** <br>&emsp; + Configure Nginx custom log formats to capture detailed traffic and device control telemetry <br>&emsp; + Setup `logrotate` on Linux EC2 to automatically compress and partition logs daily (YYYY/MM/DD) | 2026-07-02 | 2026-07-02 | |
| **Fri** | - **Integrated Hands-on:** <br>&emsp; + Develop scripts to extract and aggregate device historical logs from DynamoDB / Log Files on EC2 <br>&emsp; + Test compression, long-term retention, and log querying directly on local EC2 | 2026-07-03 | 2026-07-03 | |

---

### Week 4 Achievements:

#### 1. Configuration Data Management on Amazon DynamoDB
* **Secure & Efficient Database Deployment**:
  * Standardized storage structures for user profiles, house catalogs, and device lists on Amazon DynamoDB.
  * Configured IAM Roles and Security Group rules allowing only authorized traffic from the EC2 Backend application.
* **Data Operations & Querying**:
  * Successfully created Secondary Indexes to accelerate device lookups based on room location or operational state.
  * Executed verification queries from the EC2 Client using the secure AWS SDK.

#### 2. Device Historical Log Management System Design on EC2 & Nginx
* **Optimized Log Data Architecture**:
  * Organized a centralized log directory on the EC2 server to record device history and incoming Nginx traffic.
  * Implemented standardized log formatting (JSON Format) to optimize log writing performance and speed up troubleshooting.
* **Automated Log Rotation & Retention**:
  * Utilized `logrotate` on Linux EC2 for automatic daily log splitting (Y/M/D) and compression of old logs to save disk space.
  * Established server retention policies to prevent disk capacity exhaustion and maintain system stability.

#### 3. Automated Log Synchronization & Retrieval Workflow
* **Automated Log Processing**: Successfully developed automated scripts to consolidate device historical records from the backend application into archived files.
* **History Retrieval Verification**: Ensured all Smart Home activity logs are safely backed up on EC2 and easily searchable via Backend APIs routed by Nginx.
