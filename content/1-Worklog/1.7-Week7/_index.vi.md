---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---
### Mục tiêu tuần 7:

* Xây dựng và phát triển giao diện Web Dashboard trực quan cho phép người dùng theo dõi và điều khiển thiết bị Smart Home.
* Thiết lập Amazon API Gateway làm điểm đầu nối (Entry point) quản lý, bảo mật và định tuyến các RESTful APIs.
* Tích hợp toàn diện giao diện Web Dashboard với API Gateway và hạ tầng Backend (ALB / EC2) để thực thi truyền nhận dữ liệu đồng bộ.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :--- |
| **2** | - Phát triển giao diện người dùng Web Dashboard Smart Home: <br>&emsp; + Thiết kế UI/UX theo dõi trạng thái thiết bị (Đèn, Điều hòa, Cảm biến) <br>&emsp; + Xây dựng các component điều khiển bật/tắt và điều chỉnh thông số <br>- **Thực hành:** Hoàn thiện giao diện tĩnh (Static Web App) | 20/07/2026 | 20/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **3** | - Tìm hiểu dịch vụ Amazon API Gateway: <br>&emsp; + Các khái niệm REST API, Resources, Methods (GET/POST/PUT), và Stages <br>&emsp; + Tích hợp API Gateway với ALB / EC2 Backend <br>- **Thực hành:** Khởi tạo REST API `SmartHome-API` trên API Gateway | 21/07/2026 | 21/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **4** | - Bảo mật và quản lý truy cập API Gateway: <br>&emsp; + Cấu hình CORS (Cross-Origin Resource Sharing) cho phép Frontend gọi API <br>&emsp; + Khai báo Data Models, Request Validation, và Throttling limits <br>- **Thực hành:** Tạo Deployment Stage (`dev`/`prod`) và xuất bản API | 22/07/2026 | 22/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **5** | - **Thực hành Tích hợp Frontend & Backend:** <br>&emsp; + Đấu nối giao diện Dashboard với endpoints trên API Gateway <br>&emsp; + Xử lý gửi lệnh điều khiển thiết bị (POST/PUT) và lấy trạng thái thiết bị (GET) | 23/07/2026 | 23/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **6** | - **Kiểm thử E2E & Đánh giá:** <br>&emsp; + Kiểm thử luồng thao tác hoàn chỉnh từ Web Dashboard -> API Gateway -> ALB / EC2 -> DynamoDB <br>&emsp; + Tối ưu độ trễ phản hồi giao diện và kiểm tra việc xử lý lỗi CORS/HTTP status | 24/07/2026 | 24/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

---

### Kết quả đạt được tuần 7:

#### 1. Hoàn thiện Giao diện Điều khiển Smart Home Web Dashboard
* **Phát triển UI/UX Hoàn chỉnh**:
  * Đã hoàn thiện giao diện Web Dashboard cho phép hiển thị danh sách các phòng, bảng điều khiển trạng thái bật/tắt thiết bị (đèn, quạt, khóa cửa) và các chỉ số môi trường (nhiệt độ, độ ẩm).
  * Tối ưu phản hồi giao diện hiển thị chính xác trạng thái thiết bị sau khi gửi lệnh điều khiển.

#### 2. Triển khai & Cấu hình Amazon API Gateway
* **Xây dựng RESTful API Layer**:
  * Tạo và xuất bản thành công REST API trên Amazon API Gateway làm điểm giao tiếp duy nhất cho toàn bộ ứng dụng Smart Home.
  * Thiết lập đầy đủ các endpoint cơ bản: `GET /devices` (lấy danh sách thiết bị), `PUT /devices/{id}` (cập nhật trạng thái), và `GET /logs` (xem lịch sử hoạt động).
* **Bảo mật & Quản lý Luồng API**:
  * Cấu hình chính xác tính năng CORS (Cross-Origin Resource Sharing), giải quyết triệt để lỗi chặn kết nối tên miền chéo từ Frontend.
  * Thiết lập Throttling và Rate Limiting giúp ngăn chặn các cuộc tấn công từ chối dịch vụ (DDoS) hoặc spam request tới hệ thống Backend.

#### 3. Tích hợp Hệ thống End-to-End (E2E)
* **Kết nối Luồng Dữ liệu Toàn diện**:
  * Đấu nối thành công Web Dashboard với API Gateway để truyền nhận dữ liệu thông suốt tới hạ tầng Backend (ALB / EC2).
* **Kiểm thử Luồng Hoạt động**:
  * Khi người dùng nhấn nút bật/tắt trên Dashboard, API Gateway nhận yêu cầu, chuyển hướng tới ALB / EC2 Backend để xử lý logic kinh doanh, cập nhật trạng thái thiết bị trong DynamoDB và phản hồi kết quả lại giao diện.