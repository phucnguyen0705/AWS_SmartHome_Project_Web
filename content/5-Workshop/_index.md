---

title: "Workshop"

date: 2026-07-01

weight: 5

chapter: false

pre: " <b> 5. </b> "

---



# Workshop — Deploy SmartHome_IoT on AWS



This workshop documents the **SmartHome_IoT deployment workflow** on AWS, based on the project README and source in `SmartHome_IoT-main/`. Steps focus on the **AWS Management Console**, with **illustration image paths** — capture screenshots and place files in `content/images/workshop/`.



## Deployment architecture



```

[Browser] ──HTTP:80──► EC2 (Nginx)

                         ├─ /        → React SPA (/opt/smarthome/dist)

                         ├─ /api/*   → Node.js :5000 (PM2)

                         └─ virtual-esp32 (PM2, MQTT)

                                    │

                          DynamoDB · Cognito · IoT Core · CloudWatch

```



| AWS service | Role |

|-------------|------|

| **EC2 + Nginx** | Host React frontend, proxy `/api` → Node.js backend |

| **DynamoDB** | Store sensor data, settings, logs, login history |

| **Cognito** | Production login, `admin` / `user` groups |

| **IoT Core** | MQTT backend ↔ virtual ESP32 / real ESP32 |

| **CloudWatch** | Audit log, app log, dashboard, login-fail alarm |



**Recommended region:** `ap-southeast-2` (Sydney).



## Table of contents

| Step | Content |
|:---:|----------|
| [5.1 Introduction](5.1-introduction/_index.md) | Project overview, tech stack, and deployment flow |
| [5.2 AWS Prerequisites](5.2-prerequisites/_index.md) | Region, IAM, VPC, and EC2 Key Pair setup |
| [5.3 AWS IoT Core](5.3-iot-core/_index.md) | Policy, Thing, Certificate, and Endpoint setup |
| [5.4 CloudFormation](5.4-cloudformation/_index.md) | Deploy infrastructure stack (EC2, DynamoDB, Cognito, CloudWatch) |
| [5.5 Verify Infrastructure](5.5-verify-infrastructure/_index.md) | Confirm provisioned resources on AWS Console |
| [5.6 Deploy Application](5.6-deploy-application/_index.md) | `.env` configuration, code upload to EC2, Nginx + PM2 setup |
| [5.7 Cognito Users](5.7-cognito-users/_index.md) | Create demo users: `admin`, `user1`, `user2` |
| [5.8 Verification & Demo](5.8-verification-demo/_index.md) | Health check, user login, and device control demo |
| [5.9 Physical ESP32 (Optional)](5.9-optional-esp32/_index.md) | Flash firmware using device certificates |
| [5.10 Cleanup & Troubleshooting](5.10-cleanup-troubleshooting/_index.md) | Stack deletion, reset procedures, and troubleshooting guide |



## Full deploy checklist



```

□ Select region ap-southeast-2

□ Create EC2 Key Pair → save .pem (do not commit to Git)

□ Verify default VPC + public subnet

□ IoT Core: Policy + 2 Things + cert → backend/certs/ + certs-device/

□ Get IoT endpoint

□ CloudFormation: deploy smarthome-stack → record Outputs

□ Edit infrastructure/ec2.env.template

□ deploy-all.ps1 or manual upload to EC2

□ curl http://EC2_IP/api/health → ok

□ Create Cognito demo users

□ Open http://EC2_IP → login admin / Admin@Demo2024

□ Test light/fan/door control

□ pm2 logs virtual-esp32 → MQTT connected

```


