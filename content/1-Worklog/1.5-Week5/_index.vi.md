---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
## Mục tiêu tuần 5:

* Đánh giá và phân tích hiệu năng hoạt động của hệ thống Backend Smart Home trên các máy chủ Amazon EC2 đằng sau Nginx Reverse Proxy.
* Tối ưu hóa cấu hình Nginx Reverse Proxy, môi trường thực thi Backend và truy vấn cơ sở dữ liệu DynamoDB để giảm độ trễ (latency) khi xử lý lệnh điều khiển.
* Thiết lập cơ chế tự động mở rộng quy mô (Auto Scaling Group) và tích hợp điều phối Nginx Upstream giúp hệ thống tự động điều chỉnh tài nguyên EC2 theo lưu lượng thực tế.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :--- |
| **2** | - Phân tích hiệu năng Nginx & EC2 Backend hiện tại: <br>&emsp; + Giám sát mức độ sử dụng CPU, Memory, Network I/O và chỉ số Nginx Connection <br>&emsp; + Xác định điểm nghẽn (bottlenecks) trong luồng xử lý API qua Nginx Reverse Proxy <br>- **Thực hành:** Sử dụng công cụ benchmark đo độ trễ response time của Nginx & EC2 | 06/07/2026 | 06/07/2026 | [EC2 Performance](https://aws.amazon.com/ec2/) |
| **3** | - Tối ưu hóa Nginx & Database Query: <br>&emsp; + Tối ưu hóa Nginx config (worker_processes, keepalive, buffer, gzip) <br>&emsp; + Tối ưu mã nguồn Backend và truy vấn DynamoDB để giảm thời gian phản hồi <br>- **Thực hành:** Áp dụng Caching (In-memory/Redis) lưu tạm trạng thái thiết bị | 07/07/2026 | 07/07/2026 | [DynamoDB Best Practices](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html) |
| **4** | - Nghiên cứu giải pháp Tự động mở rộng (EC2 Auto Scaling & Nginx Routing): <br>&emsp; + Tìm hiểu khái niệm Launch Template, Auto Scaling Policies và Nginx Upstream Balancing <br>&emsp; + Thiết lập ngưỡng Scaling dựa trên chỉ số CPU/RAM và lưu lượng kết nối | 08/07/2026 | 08/07/2026 | [EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html) |
| **5** | - **Thực hành:** <br>&emsp; + Tạo Launch Template đóng gói cấu hình Backend chuẩn và Nginx Reverse Proxy <br>&emsp; + Khởi tạo Auto Scaling Group (ASG) quy định số lượng EC2 tối thiểu/tối đa <br>&emsp; + Cấu hình chính sách tự động tăng/giảm số lượng EC2 khi lưu lượng thay đổi | 09/07/2026 | 09/07/2026 | |
| **6** | - **Kiểm thử & Đánh giá:** <br>&emsp; + Thực hiện Stress Test (bơm tải ảo) kiểm tra phản ứng của Nginx Proxy và Auto Scaling <br>&emsp; + Đánh giá thời gian phản hồi của Backend EC2 trước và sau khi tối ưu | 10/07/2026 | 10/07/2026 | |

---

### Kết quả đạt được tuần 5:

#### 1. Tối ưu hóa Hiệu năng Nginx Reverse Proxy & EC2 Backend
* **Giảm Độ trễ Xử lý (Latency Reduction)**:
  * Tối ưu hóa thành công tham số Nginx (keepalive connections, buffer size) và mã nguồn Backend, giúp giảm độ trễ phản hồi API điều khiển thiết bị Smart Home.
  * Tích hợp cơ chế Caching lưu tạm trạng thái thiết bị, giảm số lượng truy vấn trực tiếp vào DynamoDB và tiết kiệm tài nguyên hệ thống.
* **Tối ưu hóa Tài nguyên Phần cứng**:
  * Điều chỉnh tham số cấu hình hệ điều hành Linux và runtime giúp ứng dụng EC2 Backend vận hành ổn định đằng sau Nginx, duy trì mức sử dụng CPU/RAM ở ngưỡng tối ưu.

#### 2. Triển khai Tự động Mở rộng EC2 Auto Scaling & Nginx Routing
* **Đóng gói Launch Template chuẩn hóa**: Tạo thành công Launch Template chứa đầy đủ môi trường, Nginx Reverse Proxy, mã nguồn Backend và cấu hình bảo mật phục vụ việc nhân bản máy chủ tự động.
* **Thiết lập Auto Scaling Group (ASG) linh hoạt**:
  * Cấu hình ASG tự động theo dõi tải hệ thống (Target Tracking Scaling Policy dựa trên CPU Utilization/Connection count).
  * Hệ thống tự động khởi tạo thêm máy chủ EC2 mới khi lưu lượng truy cập tăng đột biến và tự động thu hồi khi tải giảm, đảm bảo tối ưu chi phí vận hành.

#### 3. Kiểm thử Tải & Xác thực Cơ chế Mở rộng
* **Xác thực Stress Test**: Giả lập thành công lượng truy cập lớn vào Nginx Proxy và Backend; phát hiện kịp thời và tự động tăng số lượng EC2 Instance để gánh tải.
* **Đánh giá Tổng thể**: Hệ thống Backend Smart Home triển khai trên EC2 + Nginx đạt trạng thái tối ưu, duy trì hiệu năng cao và có khả năng tự động thích ứng với biến động lưu lượng thực tế.