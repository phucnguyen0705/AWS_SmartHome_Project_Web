---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}

# Week 6: Cloud Infrastructure Monitoring & Automated Alerting (CloudWatch & SNS)

### Week 6 Objectives:

* Master Cloud system monitoring concepts using Amazon CloudWatch (Metrics, Logs, Alarms, Dashboards).
* Configure Amazon SNS (Simple Notification Service) to receive incident notifications.
* **Full IaC Automation:** Declare all monitoring infrastructure (SNS Topics, CloudWatch Alarms, Dashboards) directly inside the `smarthome-stack.yaml` CloudFormation template.

---

### Tasks to Implement This Week:

| Day | Tasks | Start Date | Completion Date | Resources |
| :---: | :--- | :---: | :---: | :--- |
| **Mon** | - Learn Amazon CloudWatch services: <br>&emsp; + Core concepts: Metrics, Logs, Dashboards, and CloudWatch Agent <br>&emsp; + Resource monitoring for EC2, DynamoDB, ALB, S3 <br>- **Hands-on:** Declare CloudWatch Agent configuration inside EC2 UserData via CloudFormation | 07/13/2026 | 07/13/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tue** | - Learn Amazon SNS (Simple Notification Service): <br>&emsp; + Pub/Sub model, SNS Topics, and Subscriptions (Email) <br>- **Hands-on:** Update `smarthome-stack.yaml` to provision `AWS::SNS::Topic` (`SmartHome-Alerts-Topic`) and `AWS::SNS::Subscription` | 07/14/2026 | 07/14/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wed** | - Configure CloudWatch Alarms via CloudFormation: <br>&emsp; + Declare `AWS::CloudWatch::Alarm` resources for CPU utilization (> 80%), RAM usage, and HTTP 5xx errors <br>&emsp; + Link `AlarmActions` directly to the SNS Topic ARN | 07/15/2026 | 07/15/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thu** | - **Dashboard Design via CloudFormation:** <br>&emsp; + Declare `AWS::CloudWatch::Dashboard` resource displaying centralized system health <br>&emsp; + Visualize key metrics: EC2 CPU/RAM, ALB Response Time, DynamoDB Throttling | 07/16/2026 | 07/16/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Fri** | - **Stack Execution & Alert Testing:** <br>&emsp; + Redeploy CloudFormation stack (`deploy-stack.ps1`) <br>&emsp; + Run Stress Test on EC2 to verify Alarm transitions to `ALARM` state and triggers SNS email | 07/17/2026 | 07/17/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

---

### Week 6 Achievements:

#### 1. Automated Monitoring via CloudFormation (IaC)
* **CloudWatch Agent & Log Groups Integration**:
  * Defined `AWS::Logs::LogGroup` inside CloudFormation template to manage application and system logs centrally.
  * Automated CloudWatch Agent installation and startup on EC2 Backend using UserData scripts.

#### 2. Centralized Dashboard Declaration (Dashboard as Code)
* **Automated Dashboard Provisioning**:
  * Defined Dashboard JSON structure within `AWS::CloudWatch::Dashboard` resource in CloudFormation.
  * Automatically generated monitoring widgets for EC2 CPU/RAM, ALB Latency, and DynamoDB throughput upon stack deployment completion.

#### 3. Automated Alerting Workflow with CloudFormation & SNS
* **SNS Topic & Subscriptions Provisioning**:
  * Declared `AWS::SNS::Topic` (`SmartHome-Alerts-Topic`) and automated email subscription via CloudFormation Parameters.
* **Alarms Setup & Stress Testing**:
  * Provisioned `AWS::CloudWatch::Alarm` resources automatically attached to the SNS Topic `AlarmActions`.
  * Conducted stress testing: System detected high CPU load, CloudWatch Alarm transitioned to `ALARM` state and dispatched alert emails to administrators.
