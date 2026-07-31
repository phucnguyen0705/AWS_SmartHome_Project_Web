---
title: "Week 1 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

* Connect and onboard with members of the First Cloud AI Journey (FCAJ) program.
* Master foundational knowledge of the AWS ecosystem, managing resources via AWS Management Console and AWS CLI.
* Understand the role of core services in Smart Home architecture: **EC2, DynamoDB, S3, Amplify, AWS IoT Core, Security Group/AWS WAF**.
* Practice launching, securely connecting to, and managing storage resources on Amazon EC2 virtual servers.

---

### Weekly Tasks Schedule:

| Day | Task | Start Date | End Date | Resource Link |
| :---: | :--- | :---: | :---: | :--- |
| **Mon** | - Onboard with FCAJ team members <br>- Read and memorize internal rules and guidelines | 08/06/2026 | 08/06/2026 | FCAJ Internal |
| **Tue** | - Overview of AWS Cloud and core services for Smart Home architecture: <br>&emsp; + **Compute & Frontend:** EC2, AWS Amplify <br>&emsp; + **Storage & Database:** S3, DynamoDB <br>&emsp; + **IoT & Security:** AWS IoT Core, Security Group, AWS WAF, IAM | 09/06/2026 | 09/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wed** | - Create AWS Free Tier account <br>- Explore AWS Console & AWS CLI <br>- **Hands-on:** <br>&emsp; + Setup personal account security <br>&emsp; + Install AWS CLI v2 on local machine <br>&emsp; + Configure Credentials using `aws configure` | 10/06/2026 | 10/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thu** | - Deep dive into EC2 virtual servers for hosting Smart Home Backend: <br>&emsp; + Instance Types, AMI Amazon Machine Image concepts <br>&emsp; + Block Storage EBS Volume, EBS Snapshot concepts <br>- Remote SSH methods to EC2: Key Pair, EC2 Instance Connect <br>- Understand Elastic IP static addressing | 11/06/2026 | 11/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Fri** | - **Hands-on:** <br>&emsp; + Launch EC2 Instance (Ubuntu or Amazon Linux) <br>&emsp; + Connect via SSH using Terminal or OpenSSH <br>&emsp; + Create, attach, format, and mount an additional EBS Volume to OS for Backend data | 12/06/2026 | 12/06/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

---

### Week 1 Outcomes:

#### 1. Foundational Knowledge & AWS Account
* **Comprehensive grasp of the AWS ecosystem**: Distinguished key service roles tailored for Smart Home infrastructure (**EC2** for backend processing, **DynamoDB** for device status, **S3** for log storage, **Amplify** for Web Dashboard deployment, **AWS IoT Core** for device connectivity, and **Security Group/WAF** for system protection).
* **Secure Account Provisioning**: Successfully created an AWS Free Tier account and configured initial security controls.

#### 2. AWS CLI Proficiency & Unified Management
* **Successful Installation & Configuration of AWS CLI v2**:
  * Configured **Access Key ID**, **Secret Access Key**, and Default Region using command-line tools.
* **Proficiency in Real-World AWS CLI Commands**:
  * **Account Verification**: Checked current IAM User status.
  * **EC2 Management**: Listed running virtual instances.
  * **Key Pair Management**: Generated SSH keys directly via CLI.
* **Dual-Management Mindset**: Understood that the AWS Console operates via underlying APIs identical to CLI, enabling seamless transition between GUI management and script automation.

#### 3. Advanced Hands-On with Amazon EC2 & EBS Storage
* **Virtual Server Deployment**:
  * Successfully launched a `t2.micro` / `t3.micro` EC2 Instance using Ubuntu/Amazon Linux 2023 as the Smart Home Backend server.
  * Configured Security Group inbound rules to open necessary ports: Port `22` (SSH) and Port `80`/`443` (HTTP/HTTPS).
* **Secure Access**:
  * Mastered SSH connectivity to EC2 via both terminal CLI and web-based **EC2 Instance Connect**.
* **EBS Storage Management**:
  * Provisioned an additional EBS volume within the same Availability Zone as the EC2 instance.
  * Successfully attached the volume to the running instance.
  * **Linux OS Level Operations**: Executed system commands to format the file system as `ext4` and mounted the new directory into the file system.