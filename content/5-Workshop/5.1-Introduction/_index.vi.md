---
title: "5.1 Gi?i thi?u"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b>  </b> "
---


## SmartHome_IoT là gì?

**SmartHome_IoT** là h? th?ng qu?n lý nhà thông minh g?m:

- **Frontend:** React + Vite (dashboard giám sát, di?u khi?n thi?t b?)
- **Backend:** Node.js (`backend/server.js`) — REST API, SSE real-time, MQTT bridge
- **Thi?t b?:** ESP32 th?t ho?c **Virtual ESP32** (ch?y trên EC2 qua PM2) — demo không c?n ph?n c?ng
- **Cloud:** DynamoDB, Cognito, IoT Core, CloudWatch trên AWS

Repo tham chi?u: `SmartHome_IoT-main/` trong workspace.

![Ki?n trúc t?ng quan SmartHome_IoT](/images/Diagram.png)

## Hai ch? d? ch?y

| Ch? d? | Auth | Database | Thi?t b? |
|--------|------|----------|----------|
| **Local dev** | JWT (`admin/admin123`) | File `backend/data/local-db.json` | Simulator HTTP |
| **Production EC2** | Cognito IdToken | DynamoDB | Virtual ESP32 (MQTT) ho?c ESP32 |

Workshop này t?p trung **Production EC2** — tri?n khai qua AWS Console + script deploy.

## Stack AWS (production)

| L?p | Công ngh? | Vai trò |
|-----|-----------|---------|
| Compute | **EC2** t3.micro + **Nginx** | Host UI + API proxy |
| Database | **DynamoDB** (`SmartHome`) | Single-table: sensor, settings, logs |
| Auth | **Cognito User Pool** | Nhóm `admin` / `user` |
| Messaging | **IoT Core** (MQTT) | Backend ? thi?t b? |
| Monitoring | **CloudWatch** Logs + Dashboard + Alarm | Audit, app log, login fail |

## Lu?ng deploy t?ng quan

```
? Chu?n b? AWS (region, key pair, VPC)
? C?u hình IoT Core (Policy + 2 Things + cert)
? Deploy CloudFormation ? EC2, DynamoDB, Cognito, CloudWatch
? Ghi Outputs (EC2 IP, Cognito Pool/Client ID, IoT endpoint)
? S?a ec2.env.template ? deploy code lên EC2
? T?o user Cognito demo
? Ki?m tra http://EC2_IP và di?u khi?n thi?t b?
```


## Yêu c?u tru?c khi b?t d?u

- Tài kho?n AWS (Free Tier d? cho demo)
- **Node.js 18+** trên máy local (build frontend)
- **AWS CLI v2** (tu? ch?n — script deploy dùng CLI)
- Mã ngu?n `SmartHome_IoT-main/` dã clone v? máy


