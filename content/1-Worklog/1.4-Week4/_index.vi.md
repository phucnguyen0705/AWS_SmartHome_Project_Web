---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

## Mục tiêu tuần 4:

* Nắm vững cách quản trị dữ liệu cấu hình người dùng và thiết bị Smart Home trên Amazon DynamoDB.
* Quản lý, xoay vòng (log rotation) và lưu trữ nhật ký hoạt động thiết bị Smart Home trực tiếp trên máy chủ EC2 Backend.
* Tối ưu hóa Nginx Reverse Proxy và cấu hình lưu trữ log tập trung phục vụ truy xuất lịch sử thiết bị và giám sát hệ thống.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :--- |
| **2** | - Quản trị và cấu hình dữ liệu hệ thống trên Amazon DynamoDB: <br>&emsp; + Thiết kế cấu trúc bảng quản lý thông tin người dùng và danh mục thiết bị Smart Home <br>&emsp; + Chuẩn hóa cấu trúc dữ liệu lưu trữ cấu hình thiết bị <br>- **Thực hành:** Tạo và kiểm thử truy vấn bảng cấu hình thiết bị trên DynamoDB | 29/06/2026 | 29/06/2026 | [DynamoDB](https://aws.amazon.com/dynamodb/?nc2=type_a) |
| **3** | - Bảo mật và tối ưu thao tác truy vấn DynamoDB: <br>&emsp; + Cấu hình Security Group kiểm soát quyền truy cập kết nối vào máy chủ Backend EC2 <br>&emsp; + Tối ưu hóa truy vấn dữ liệu thiết bị thông qua Primary Key và Secondary Index <br>- **Thực hành:** Viết script truy xuất cấu hình người dùng và thiết bị từ EC2 | 30/06/2026 | 30/06/2026 | |
| **4** | - Tìm hiểu giải pháp quản lý và phân tích nhật ký (Log Management) trên EC2: <br>&emsp; + Thiết kế cấu trúc thư mục lưu trữ Log thiết bị và Nginx Access/Error Logs trên EC2 <br>&emsp; + Cấu hình định dạng log chuẩn (JSON format) cho lịch sử hoạt động thiết bị | 01/07/2026 | 01/07/2026 | |
| **5** | - **Thực hành:** <br>&emsp; + Cấu hình Nginx Log format để ghi nhận chi tiết traffic và luồng điều khiển thiết bị <br>&emsp; + Thiết lập công cụ `logrotate` trên EC2 để tự động nén, phân tách log theo ngày (Năm/Tháng/Ngày) | 02/07/2026 | 02/07/2026 | |
| **6** | - **Thực hành tích hợp:** <br>&emsp; + Viết script trích xuất và tổng hợp nhật ký lịch sử thiết bị từ DynamoDB / File Log trên EC2 <br>&emsp; + Kiểm thử quá trình nén, lưu trữ dài hạn và truy xuất dữ liệu lịch sử tại local EC2 | 03/07/2026 | 03/07/2026 | |

---

### Kết quả đạt được tuần 4:

#### 1. Quản trị Dữ liệu Cấu hình trên Amazon DynamoDB
* **Triển khai CSDL An toàn & Hiệu quả**:
  * Chuẩn hóa cấu trúc lưu trữ thông tin người dùng, danh mục nhà và danh sách thiết bị trên Amazon DynamoDB.
  * Cấu hình phân quyền IAM Role và Security Group chỉ cho phép kết nối hợp lệ từ ứng dụng Backend EC2.
* **Vận hành & Truy vấn Dữ liệu**:
  * Thực hành tạo Secondary Index để tăng tốc độ tìm kiếm thông tin thiết bị theo phòng hoặc trạng thái hoạt động.
  * Thực thi các truy vấn kiểm tra dữ liệu từ EC2 Client thông qua AWS SDK an toàn.

#### 2. Thiết kế Hệ thống Quản lý Nhật ký Lịch sử Thiết bị trên EC2 & Nginx
* **Cấu trúc Dữ liệu Nhật ký Tối ưu**:
  * Quy hoạch thư mục lưu trữ log tập trung trên máy chủ EC2 phục vụ ghi nhận lịch sử hoạt động thiết bị và traffic qua Nginx.
  * Thiết kế định dạng log tiêu chuẩn (JSON Format) giúp tối ưu hiệu năng ghi chép và tra cứu lịch sử sự kiện Smart Home.
* **Tự động hóa Quản lý Log (Log Retention & Rotation)**:
  * Áp dụng công cụ `logrotate` trên Linux EC2 giúp tự động phân tách log theo ngày (Y/M/D), nén file log cũ để tiết kiệm dung lượng ổ cứng.
  * Thiết lập chính sách lưu trữ log hợp lý trên server, đảm bảo hệ thống EC2 vận hành ổn định không bị tràn ổ đĩa.

#### 3. Tự động hóa Luồng Đồng bộ & Truy xuất Log
* **Xử lý Nhật ký Tự động**: Xây dựng thành công kịch bản tự động tổng hợp lịch sử thiết bị từ ứng dụng backend và lưu trữ cấu trúc dưới dạng file nén trên máy chủ.
* **Kiểm thử Truy xuất Lịch sử**: Đảm bảo toàn bộ nhật ký lịch sử hoạt động của nhà thông minh được sao lưu an toàn trên EC2, dễ dàng tìm kiếm và truy xuất thông qua các API Backend điều hướng bởi Nginx.
