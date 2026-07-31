---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
### Mục tiêu tuần 3:

* Nắm vững cách thiết kế và tối ưu hóa cơ sở dữ liệu NoSQL Amazon DynamoDB để lưu trữ trạng thái thiết bị Smart Home.
* Tìm hiểu và triển khai ứng dụng Backend Service trên máy chủ Amazon EC2 để xử lý logic điều khiển thiết bị tự động.
* Tích hợp Amazon DynamoDB và máy chủ EC2 Backend để tạo luồng xử lý dữ liệu trạng thái thiết bị hiệu quả, ổn định và linh hoạt.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :--- |
| **2** | - Tìm hiểu dịch vụ NoSQL Amazon DynamoDB: <br>&emsp; + Khái niệm Tables, Items, Attributes <br>&emsp; + Partition Key, Sort Key, và chỉ mục Secondary Indexes <br>- **Thực hành:** Khởi tạo bảng lưu trữ trạng thái thiết bị Smart Home trên DynamoDB | 22/06/2026 | 22/06/2026 | [AWS DynamoDB](https://aws.amazon.com/dynamodb/?nc2=type_a) |
| **3** | - Tìm hiểu cơ chế phân quyền bảo mật IAM Role cho máy chủ EC2 (IAM Instance Profile): <br>&emsp; + Khái niệm EC2 Instance Profile và cách gán IAM Role cho EC2 <br>&emsp; + Cấu hình IAM Policy cấp quyền cho máy chủ EC2 truy cập và thao tác với DynamoDB | 23/06/2026 | 23/06/2026 | [EC2 Instance](https://aws.amazon.com/blogs/aws/amazon-ec2-instance-metadata-service-imdsv2-by-default/) |
| **4** | - **Thực hành:** <br>&emsp; + Viết ứng dụng Backend Service bằng Python hoặc Node.js chạy trên EC2 để xử lý logic cập nhật trạng thái thiết bị Smart Home <br>&emsp; + Cấu hình gán IAM Role cho EC2 để ứng dụng truy cập DynamoDB an toàn không cần hardcode credentials | 24/06/2026 | 24/06/2026 |  |
| **5** | - Tìm hiểu cơ chế xử lý logic tự động hóa trên EC2: <br>&emsp; + Xây dựng tiến trình xử lý ngầm (Background Worker/Daemon Process) trên EC2 <br>&emsp; + Thiết lập cơ chế kiểm tra định kỳ hoặc nhận lệnh API để xử lý tự động khi trạng thái thiết bị thay đổi | 25/06/2026 | 25/06/2026 |  |
| **6** | - **Thực hành:** <br>&emsp; + Triển khai Worker Service chạy ngầm trên máy chủ EC2 (sử dụng Systemd hoặc PM2) <br>&emsp; + Kiểm thử luồng xử lý tự động: Khi trạng thái thiết bị Smart Home thay đổi, dịch vụ trên EC2 tự động phát hiện và thực thi các quy tắc logic Backend đã định sẵn | 26/06/2026 | 26/06/2026 | |

---

### Kết quả đạt được tuần 3:

#### 1. Thiết kế & Quản trị Cơ sở dữ liệu DynamoDB cho Smart Home
* **Thành thạo Tối ưu Cấu trúc Dữ liệu NoSQL**:
  * Tự tay thiết kế và khởi tạo thành công các bảng DynamoDB chứa dữ liệu trạng thái thiết bị Smart Home.
  * Tối ưu hóa việc lựa chọn Partition Key và Sort Key giúp truy vấn dữ liệu thiết bị đạt hiệu năng tối đa với độ trễ thấp.
* **Thao tác Dữ liệu Chi tiết**: Thực hiện thành công các thao tác CRUD để cập nhật, đọc và chỉnh sửa trạng thái bật/tắt hoặc thông số của thiết bị Smart Home thông qua AWS Console và AWS CLI.

#### 2. Phát triển & Triển khai Backend Service trên EC2
* **Xây dựng Dịch vụ Backend trên EC2**:
  * Viết và đóng gói thành công mã nguồn ứng dụng Backend (Python/Node.js) chạy trực tiếp trên EC2 đảm nhận vai trò xử lý logic trung tâm cho ứng dụng Smart Home.
  * Thiết lập cấu hình biến môi trường Environment Variables và tối ưu hóa tài nguyên phần cứng cho dịch vụ chạy trên EC2.
* **Bảo mật & Phân quyền IAM Role cho EC2**:
  * Khởi tạo IAM Instance Profile dành riêng cho EC2 với các quyền tối thiểu để truy cập và thao tác với DynamoDB.
  * Đảm bảo ứng dụng trên EC2 chạy an toàn mà không cần lưu trữ thông tin xác thực cứng (Access Key / Secret Key) trong mã nguồn.

#### 3. Tích hợp Chuỗi Xử lý Tự động giữa EC2 Backend & DynamoDB
* **Cấu hình Background Worker trên EC2**: Quản lý và vận hành thành công Worker Service chạy dưới dạng tiến trình ngầm (Systemd/PM2) trên máy chủ EC2 để theo dõi và xử lý dữ liệu liên tục.
* **Tự động hóa Luồng Logic Smart Home**:
  * Kết nối thành công ứng dụng EC2 Backend với bảng DynamoDB bằng AWS SDK.
  * Kiểm thử thành công luồng xử lý tự động: Khi có yêu cầu thay đổi trạng thái thiết bị Smart Home, máy chủ EC2 tự động xử lý logic kinh doanh và cập nhật chính xác dữ liệu vào bảng DynamoDB.
