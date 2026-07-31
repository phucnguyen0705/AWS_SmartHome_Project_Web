---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---
### Week 7 Objectives:

* Build and develop an intuitive Web Dashboard interface allowing users to monitor and control Smart Home devices.
* Configure Amazon API Gateway as an entry point for managing, securing, and routing RESTful APIs.
* Fully integrate the Web Dashboard interface with API Gateway and Backend infrastructure (ALB / EC2) to execute synchronous data transfer.

---

### Tasks to Implement This Week:

| Day | Tasks | Start Date | Completion Date | Resources |
| :---: | :--- | :---: | :---: | :--- |
| **Mon** | - Develop Smart Home Web Dashboard user interface: <br>&emsp; + Design UI/UX for monitoring device status (Lights, Air Conditioner, Sensors) <br>&emsp; + Build control components for toggle actions and parameter adjustments <br>- **Hands-on:** Complete static Web App interface | 07/20/2026 | 07/20/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tue** | - Learn Amazon API Gateway services: <br>&emsp; + Core concepts: REST API, Resources, Methods (GET/POST/PUT), and Stages <br>&emsp; + Integration of API Gateway with ALB / EC2 Backend <br>- **Hands-on:** Initialize REST API `SmartHome-API` on API Gateway | 07/21/2026 | 07/21/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wed** | - Secure and manage API Gateway access: <br>&emsp; + Configure CORS (Cross-Origin Resource Sharing) for Frontend API calls <br>&emsp; + Declare Data Models, Request Validation, and Throttling limits <br>- **Hands-on:** Create Deployment Stage (`dev`/`prod`) and publish API | 07/22/2026 | 07/22/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thu** | - **Frontend & Backend Integration Practice:** <br>&emsp; + Connect Dashboard UI with endpoints on API Gateway <br>&emsp; + Handle device control commands (POST/PUT) and status fetching (GET) | 07/23/2026 | 07/23/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Fri** | - **E2E Testing & Evaluation:** <br>&emsp; + Conduct end-to-end testing: Web Dashboard -> API Gateway -> ALB / EC2 -> DynamoDB <br>&emsp; + Optimize UI response latency and verify CORS/HTTP status error handling | 07/24/2026 | 07/24/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

---

### Week 7 Achievements:

#### 1. Completed Smart Home Web Dashboard UI Development
* **Full UI/UX Implementation**:
  * Finalized the Web Dashboard layout featuring room management, device status control panels (lights, fans, door locks), and environmental metrics (temperature, humidity).
  * Optimized UI response to accurately display updated device statuses immediately upon issuing control actions.

#### 2. Amazon API Gateway Deployment & Configuration
* **RESTful API Layer Construction**:
  * Successfully created and deployed a REST API on Amazon API Gateway, serving as the single entry point for all Smart Home backend communications.
  * Established core API endpoints: `GET /devices` (fetch device list), `PUT /devices/{id}` (update device state), and `GET /logs` (view activity history).
* **API Security & Traffic Management**:
  * Configured Cross-Origin Resource Sharing (CORS) rules to resolve cross-domain request blocking from the Frontend.
  * Applied Throttling and Rate Limiting settings to safeguard backend resources against DDoS attacks and excessive API spamming.

#### 3. End-to-End System Integration (E2E)
* **Comprehensive Data Flow Integration**:
  * Successfully connected the Web Dashboard with API Gateway, enabling seamless real-time data communication down to the ALB / EC2 backend.
* **Operational Testing Verification**:
  * Verified end-to-end execution: User actions on the Dashboard trigger API Gateway requests, which are routed through the ALB to EC2 for business logic processing, updated in DynamoDB, and reflected back on the UI seamlessly.
