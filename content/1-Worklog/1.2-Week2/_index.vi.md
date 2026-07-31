---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Nắm vững dịch vụ AWS Identity and Access Management (IAM) và AWS IoT Core để triển khai phân quyền, đăng ký và kết nối an toàn cho thiết bị Smart Home.
* Tìm hiểu và cấu hình bảo mật máy chủ Backend EC2 kết nối với AWS IoT Core qua giao thức MQTT.
* Thực hành quản trị Amazon S3 bucket để lưu trữ nhật ký thiết bị Smart Home, cấu hình chính sách vòng đời dữ liệu và bảo mật lưu trữ.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :--- |
| **2** | - Tìm hiểu nền tảng AWS IAM & Bảo mật IoT: <br>&emsp; + Khái niệm IAM Users, Groups, Roles, và Policies <br>&emsp; + Nguyên tắc phân quyền tối thiểu áp dụng cho thiết bị Smart Home <br>- **Thực hành:** Tạo IAM Users, gán chính sách phân quyền và bắt buộc bật xác thực MFA | 15/06/2026 | 15/06/2026 |  |
| **3** | - Tìm hiểu Kiến trúc AWS IoT Core & Bảo mật ứng dụng Web: <br>&emsp; + Các khái niệm IoT Things, Thing Shadows, MQTT Protocol <br>&emsp; + Cơ chế mã hóa X.509 Certificates và IoT Policies <br>- Tìm hiểu cấu hình Tường lửa Security Groups và kiểm soát truy cập cho Backend EC2 | 16/06/2026 | 16/06/2026 | [AWS IOT Core](https://aws.amazon.com/iot-core/?nc2=type_a) |
| **4** | - **Thực hành:** <br>&emsp; + Đăng ký thiết bị Smart Home vào AWS IoT Core, tạo X.509 Certificates <br>&emsp; + Gán IoT Policy cho phép Publish/Subscribe đúng MQTT Topic của thiết bị <br>&emsp; + Thao tác cập nhật và đồng bộ trạng thái thiết bị thông qua Device Shadow | 17/06/2026 | 17/06/2026 |  [AWS IOT Core](https://aws.amazon.com/iot-core/?nc2=type_a) |
| **5** | - Tìm hiểu các khái niệm lưu trữ nhật ký thiết bị trên Amazon S3: <br>&emsp; + Buckets, Objects, các lớp lưu trữ Standard, IA, Glacier <br>&emsp; + Quản lý phiên bản, Lifecycle rules cho dữ liệu thiết bị Smart Home | 18/06/2026 | 18/06/2026 | [AWS S3](https://aws.amazon.com/s3/?nc2=type_a) |
| **6** | - **Thực hành:** <br>&emsp; + Khởi tạo S3 Bucket lưu trữ dữ liệu thiết bị Smart Home qua Console và CLI <br>&emsp; + Cấu hình S3 Bucket Policies và bật tính năng Block Public Access <br>&emsp; + Bật Versioning và thiết lập các quy tắc quản lý vòng đời dữ liệu | 19/06/2026 | 19/06/2026 | [AWS S3](https://aws.amazon.com/s3/?nc2=type_a) |

---

### Kết quả đạt được tuần 2:

#### 1. Bảo mật & Quản lý danh tính IAM cho Smart Home
* **Làm chủ Nguyên tắc Phân quyền Tối thiểu**: Hiểu rõ ranh giới bảo mật quan trọng trong việc chỉ giới hạn quyền truy cập vừa đủ cho tài nguyên và thiết bị Smart Home.
* **Cấu hình Bảo mật IAM Chi tiết**:
  * Tạo các IAM Users và Groups riêng biệt được ánh xạ theo đúng vai trò công việc như SmartHomeDevGroup, IoTAdminGroup.
  * Tự viết và gán các chính sách Managed JSON Policies để kiểm soát chính xác cấp độ truy cập dịch vụ.
  * Thiết lập bắt buộc xác thực 2 lớp Multi-Factor Authentication cho toàn bộ các tài khoản IAM đang hoạt động.
* **Sử dụng IAM Role cho AWS IoT & EC2**: Gán thành công IAM Role cho EC2 instance và dịch vụ IoT, cho phép máy chủ và dịch vụ kết nối an toàn mà không cần nhúng trực tiếp Access Key hay Secret Key vào mã nguồn ứng dụng.

#### 2. Quản lý thiết bị AWS IoT Core & Kết nối an toàn
* **Thành thạo Quản lý Thiết bị với AWS IoT Core**:
  * Đăng ký thành công các đối tượng thiết bị Smart Home vào AWS IoT Core.
  * Khởi tạo, tải xuống và cấu hình chứng chỉ bảo mật X.509 Certificates cùng IoT Policies để thiết lập kết nối mã hóa cho thiết bị qua giao thức MQTT.
  * Thao tác thử nghiệm cập nhật và đồng bộ trạng thái thiết bị thông qua Device Shadow.
* **Bảo mật Kết nối & Tường lửa Cấp độ máy chủ**:
  * Cấu hình tường lửa Security Group cho EC2 Instance để kiểm soát cổng kết nối cho giao tiếp IoT và REST API.
  * Thiết lập chính sách phân quyền cho phép EC2 giao tiếp an toàn với AWS IoT Core thông qua IAM Role.

#### 3. Lưu trữ Nhật ký Dữ liệu Thiết bị với Amazon S3
* **Thao tác & Quản lý S3 Storage**:
  * Khởi tạo thành công các S3 Bucket chứa dữ liệu nhật ký thiết bị Smart Home với tên duy nhất trên toàn cầu thông qua Console và AWS CLI.
  * Tải lên, tải về và quản lý quyền truy cập tập tin thông qua các câu lệnh đồng bộ CLI.
* **Bảo vệ Dữ liệu**:
  * Bật tính năng S3 Versioning để lưu trữ, truy xuất và khôi phục các phiên bản cũ của tệp cấu hình thiết bị.
  * Cấu hình S3 Bucket Policies để bắt buộc mã hóa dữ liệu trên đường truyền Enforce HTTPS TLS và chặn hoàn toàn việc công khai bucket ra ngoài.