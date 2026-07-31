---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Nắm vững các khái niệm giám sát hệ thống Cloud với Amazon CloudWatch (Metrics, Logs, Alarms, Dashboards).
* Cấu hình dịch vụ gửi thông báo Amazon SNS (Simple Notification Service) để nhận tin nhắn cảnh báo khi hệ thống gặp sự cố.
* **Tự động hóa hoàn toàn:** Khai báo toàn bộ hạ tầng giám sát (SNS Topic, CloudWatch Alarms, CloudWatch Dashboard) trực tiếp vào CloudFormation template `smarthome-stack.yaml`.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :--- |
| **2** | - Tìm hiểu dịch vụ Amazon CloudWatch: <br>&emsp; + Các khái niệm Metrics, Logs, Dashboards, và CloudWatch Agent <br>&emsp; + Giám sát các thông số tài nguyên EC2, DynamoDB, ALB, S3 <br>- **Thực hành:** Khai báo cấu hình CloudWatch Agent trong UserData của EC2 qua CloudFormation | 13/07/2026 | 13/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **3** | - Tìm hiểu dịch vụ Amazon SNS (Simple Notification Service): <br>&emsp; + Mô hình Pub/Sub, SNS Topics, và Subscriptions (Email) <br>- **Thực hành:** Cập nhật `smarthome-stack.yaml` để khởi tạo tài nguyên `AWS::SNS::Topic` (`SmartHome-Alerts-Topic`) và `AWS::SNS::Subscription` | 14/07/2026 | 14/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **4** | - Cấu hình CloudWatch Alarms qua CloudFormation: <br>&emsp; + Khai báo tài nguyên `AWS::CloudWatch::Alarm` cho CPU utilization (> 80%), RAM usage, và HTTP 5xx errors <br>&emsp; + Liên kết `AlarmActions` trực tiếp với SNS Topic ARN | 15/07/2026 | 15/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **5** | - **Thiết kế Dashboard bằng CloudFormation:** <br>&emsp; + Khai báo tài nguyên `AWS::CloudWatch::Dashboard` tập trung hiển thị trạng thái hệ thống <br>&emsp; + Trực quan hóa các chỉ số quan trọng: CPU/RAM EC2, ALB Response Time, DynamoDB Throttling | 16/07/2026 | 16/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **6** | - **Thực thi Stack & Kiểm thử luồng cảnh báo:** <br>&emsp; + Deploy lại stack CloudFormation (`deploy-stack.ps1`) <br>&emsp; + Chạy Stress Test trên EC2 để kiểm tra Alarm chuyển sang trạng thái `ALARM` và gửi email qua SNS | 17/07/2026 | 17/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

---

### Kết quả đạt được tuần 6:

#### 1. Tự động hóa Giám sát qua CloudFormation (IaC)
* **Tích hợp CloudWatch Agent & Log Groups**:
  * Định nghĩa `AWS::Logs::LogGroup` trong template CloudFormation để quản lý tập trung ứng dụng log và system log.
  * Tự động cài đặt và kích hoạt CloudWatch Agent trên EC2 Backend thông qua script UserData/Init.

#### 2. Khai báo Dashboard Tập trung (CloudWatch Dashboard as Code)
* **Xây dựng Bảng điều khiển Tự động**:
  * Định nghĩa cấu trúc Dashboard bằng JSON trong tài nguyên `AWS::CloudWatch::Dashboard` của CloudFormation stack.
  * Tự động khởi tạo giao diện giám sát tải CPU/RAM EC2, thời gian phản hồi ALB và lưu lượng DynamoDB ngay khi stack deploy hoàn tất.

#### 3. Hệ thống Cảnh báo Tự động qua CloudFormation & SNS
* **Khởi tạo SNS Topic & Subscriptions**:
  * Khai báo `AWS::SNS::Topic` (`SmartHome-Alerts-Topic`) và tự động đăng ký Email nhận cảnh báo qua CloudFormation Parameter.
* **Thiết lập Alarms & Kiểm thử Tải (Stress Test)**:
  * Khai báo các `AWS::CloudWatch::Alarm` tự động gắn `AlarmActions` vào SNS Topic.
  * Chạy thử nghiệm Stress test: Hệ thống phát hiện CPU vượt ngưỡng, CloudWatch Alarm tự động chuyển trạng thái sang `ALARM` và gửi thông báo email cảnh báo tới quản trị viên.
