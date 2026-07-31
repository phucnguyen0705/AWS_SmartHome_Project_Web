---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Review and harden system security across the entire Smart Home architecture (IAM, Security Groups, Secrets Manager).
* Optimize operational costs and overall performance for AWS services used in the project.
* Wrap up the Smart Home project on AWS, perform End-to-End acceptance testing, and finalize technical documentation/internship reports.

---

### Tasks to Implement This Week:

| Day | Tasks | Start Date | Completion Date | Resources |
| :---: | :--- | :---: | :---: | :--- |
| **Mon** | - Strengthen Smart Home infrastructure security: <br>&emsp; + Apply the Principle of Least Privilege across all IAM Roles/Policies <br>&emsp; + Audit and tighten Inbound/Outbound rules in Security Groups <br>&emsp; + Use AWS Secrets Manager / Parameter Store for sensitive DB connection strings and API keys | 07/27/2026 | 07/27/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tue** | - Cost & Performance Optimization: <br>&emsp; + Set up budget limits and alerts using AWS Budgets & Cost Explorer <br>&emsp; + Optimize EC2 Instance Types and DynamoDB Provisioned/On-Demand capacity <br>&emsp; + Clean up unattached EBS volumes, idle Elastic IPs, and unused resources | 07/28/2026 | 07/28/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wed** | - **End-to-End System Integration Testing:** <br>&emsp; + Evaluate complete system workflow: Web Dashboard -> API Gateway -> ALB -> EC2 Backend -> DynamoDB -> S3 -> CloudWatch/SNS <br>&emsp; + Measure response latency, system load capacity, and fault recovery mechanisms | 07/29/2026 | 07/29/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thu** | - Backup & Disaster Recovery Configuration: <br>&emsp; + Set up automated backup schedules for DynamoDB tables and S3 Buckets <br>&emsp; + Package source code and create custom AMIs / Launch Templates for future scaling | 07/30/2026 | 07/30/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Fri** | - **Project Wrap-Up & Final Reporting:** <br>&emsp; + Finalize overall Smart Home AWS Architecture Diagram <br>&emsp; + Summarize key achievements, package technical documentation, and prepare the final internship defense presentation | 07/31/2026 | 07/31/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

---

### Week 8 Achievements:

#### 1. Security Hardening & Access Control
* **Standardized IAM Policies & Security Groups**:
  * Audited and restricted all IAM permissions strictly according to the Principle of Least Privilege, removing excessive rights on EC2 and API Gateway resources.
  * Successfully isolated network tiers: Blocked direct unauthorized traffic to the EC2 Backend, restricting ingress traffic strictly from API Gateway and the Application Load Balancer.
* **Secure Configuration Management**:
  * Migrated all sensitive API keys, tokens, and database connection credentials from hardcoded source configs into AWS Secrets Manager and Systems Manager Parameter Store.

#### 2. Cost & Performance Optimization
* **Detailed Budgeting & Expense Control**:
  * Configured AWS Budgets to dispatch instant alerts via Email/SNS whenever projected or actual costs exceed set thresholds.
  * Removed all unused/idle resources (old EBS snapshots, unattached Elastic IPs, expired log streams), successfully lowering monthly operational overhead.
* **Performance Tuning**:
  * Fine-tuned DynamoDB capacity settings (On-Demand / Auto-scaling) and adjusted EC2 instance sizing to match actual load requirements.

#### 3. System Acceptance & Smart Home Project Wrap-Up
* **End-to-End System Acceptance (E2E Verified)**:
  * Successfully validated full-stack execution: User action on Web Dashboard -> API Gateway routing -> ALB load balancing -> EC2 Backend processing -> DynamoDB state updates -> S3 long-term logging -> CloudWatch/SNS alerts.
  * Confirmed robust system operation with average end-to-end latency < 150ms and automated fault-recovery capability.
* **Completed Documentation & Final Deliverables**:
  * Prepared and packaged the overall Smart Home Architecture Diagram on AWS.
  * Consolidated the 8-week internship report alongside deployment guides and technical documentation.
