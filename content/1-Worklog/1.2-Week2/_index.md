---
title: "Week 2 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Master AWS Identity and Access Management (IAM) and AWS IoT Core to implement role-based access control, registration, and secure connectivity for Smart Home devices.
* Learn and configure security controls for EC2 Backend server interacting with AWS IoT Core via MQTT protocol.
* Practice managing Amazon S3 buckets for storing Smart Home device logs, configuring data lifecycle rules, and securing storage resources.

---

### Weekly Tasks Schedule:

| Day | Task | Start Date | End Date | Resource Link |
| :---: | :--- | :---: | :---: | :--- |
| **Mon** | - AWS IAM Foundations & IoT Security Principles: <br>&emsp; + Concepts of IAM Users, Groups, Roles, and Policies <br>&emsp; + Principle of Least Privilege applied to Smart Home devices <br>- **Hands-on:** Create IAM Users, attach permission policies, and enforce MFA | 15/06/2026 | 15/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tue** | - AWS IoT Core Architecture & Application Security Overview: <br>&emsp; + IoT Things, Thing Shadows, MQTT Protocol concepts <br>&emsp; + X.509 Certificate encryption and IoT Policies <br>- Understand Security Groups firewall configuration and access controls for EC2 Backend | 16/06/2026 | 16/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wed** | - **Hands-on:** <br>&emsp; + Register Smart Home devices in AWS IoT Core, generate X.509 Certificates <br>&emsp; + Attach IoT Policies granting Publish/Subscribe permissions to specific MQTT Topics <br>&emsp; + Test updating and synchronizing device status via Device Shadows | 17/06/2026 | 17/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thu** | - Learn device log storage concepts on Amazon S3: <br>&emsp; + Buckets, Objects, Storage Classes (Standard, IA, Glacier) <br>&emsp; + Versioning and Lifecycle management rules for Smart Home device data | 18/06/2026 | 18/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Fri** | - **Hands-on:** <br>&emsp; + Create S3 Bucket for Smart Home device logs via Console and CLI <br>&emsp; + Configure S3 Bucket Policies and enable Block Public Access <br>&emsp; + Enable Versioning and define lifecycle rules for automated data retention | 19/06/2026 | 19/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

---

### Week 2 Outcomes:

#### 1. Security & IAM Identity Management for Smart Home
* **Mastered Principle of Least Privilege**: Understood critical security boundaries by restricting access rights strictly to required Smart Home resources and devices.
* **Detailed IAM Security Configuration**:
  * Created dedicated IAM Users and Groups mapped to specific functional roles like SmartHomeDevGroup and IoTAdminGroup.
  * Authored and attached custom Managed JSON Policies to control granular service access levels.
  * Enforced mandatory Multi-Factor Authentication (MFA) across all active IAM accounts.
* **IAM Roles for AWS IoT & EC2 Integration**: Successfully attached IAM Roles to EC2 instances and IoT services, enabling secure authentication without embedding hardcoded Access Keys or Secret Keys into application code.

#### 2. AWS IoT Core Device Management & Secure Connectivity
* **Proficiency in AWS IoT Core Management**:
  * Successfully registered Smart Home device entities in AWS IoT Core.
  * Provisioned, downloaded, and configured X.509 Certificates alongside IoT Policies to establish encrypted device communication over MQTT protocol.
  * Practiced status synchronization and state updates utilizing AWS IoT Device Shadows.
* **Secure Connection & Instance Level Firewall**:
  * Configured Security Group rules for EC2 Backend to restrict incoming and outgoing traffic for IoT communication and REST APIs.
  * Established secure interaction permissions between EC2 and AWS IoT Core leveraging IAM Roles.

#### 3. Storing Device Logs with Amazon S3
* **S3 Storage Operations & Management**:
  * Provisioned globally unique S3 Buckets for storing Smart Home device log data via AWS Management Console and CLI.
  * Uploaded, downloaded, and managed file permissions using AWS CLI synchronization commands.
* **Data Protection & Hardening**:
  * Enabled S3 Versioning to maintain, inspect, and recover historical versions of device configuration files.
  * Configured S3 Bucket Policies to enforce in-transit encryption (Enforce HTTPS TLS) and enabled Block Public Access settings.
