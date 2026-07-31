---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu tuần 8:

* Rà soát, gia cố bảo mật toàn bộ hệ thống Smart Home (IAM, Security Groups, Secrets Manager).
* Tối ưu hóa chi phí vận hành và hiệu năng hoạt động của các dịch vụ AWS trong kiến trúc dự án.
* Tổng kết toàn bộ dự án Smart Home trên AWS, nghiệm thu hệ thống và hoàn thiện tài liệu/báo cáo thực tập.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :--- |
| **2** | - Tăng cường bảo mật toàn bộ hạ tầng Smart Home: <br>&emsp; + Áp dụng nguyên tắc Least Privilege cho tất cả các IAM Roles/Policies <br>&emsp; + Rà soát và siết chặt các Inbound/Outbound Rules của Security Groups <br>&emsp; + Sử dụng AWS Secrets Manager / Parameter Store để lưu trữ chuỗi kết nối CSDL và API Keys | 27/07/2026 | 27/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **3** | - Tối ưu hóa chi phí & hiệu năng (Cost & Performance Optimization): <br>&emsp; + Sử dụng AWS Budgets & Cost Explorer thiết lập hạn mức chi phí cho hệ thống <br>&emsp; + Tối ưu hóa kích thước EC2 Instance Types, DynamoDB Provisioned/On-Demand capacity <br>&emsp; + Dọn dẹp các tài nguyên thừa không sử dụng (Unattached EBS volumes, Idle Elastic IPs) | 28/07/2026 | 28/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **4** | - **Kiểm thử nghiệm thu toàn bộ hệ thống (End-to-End System Integration Testing):** <br>&emsp; + Đánh giá tổng thể khả năng hoạt động liên tục: Web Dashboard -> API Gateway -> ALB -> EC2 Backend -> DynamoDB -> S3 -> CloudWatch/SNS <br>&emsp; + Đo đạc độ trễ phản hồi, độ chịu tải và kiểm thử quy trình khôi phục khi có sự cố | 29/07/2026 | 29/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **5** | - Cấu hình sao lưu & Khôi phục sau thảm họa (Backup & Disaster Recovery): <br>&emsp; + Thiết lập kịch bản sao lưu tự động cho DynamoDB và S3 Buckets <br>&emsp; + Đóng gói mã nguồn và tạo AMI / Launch Templates chuẩn bị cho khả năng mở rộng | 30/07/2026 | 30/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **6** | - **Tổng kết & Báo cáo dự án:** <br>&emsp; + Hoàn thiện sơ đồ kiến trúc tổng thể dự án Smart Home trên AWS <br>&emsp; + Tổng kết kết quả đạt được, đóng gói tài liệu kỹ thuật và chuẩn bị báo cáo bảo vệ thực tập | 31/07/2026 | 31/07/2026 | [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

---

### Kết quả đạt được tuần 8:

#### 1. Tăng cường Bảo mật Hạ tầng & Quản lý Truy cập
* **Chuẩn hóa Bảo mật IAM & Security Groups**:
  * Đã rà soát và thắt chặt toàn bộ chính sách phân quyền IAM theo đúng nguyên tắc Least Privilege (Quyền tối thiểu), loại bỏ các quyền dư thừa trên EC2 và API Gateway.
  * Đã cô lập thành công các tầng kết nối: Chặn các truy cập trực tiếp không hợp lệ vào EC2 Backend, chỉ cho phép giao tiếp từ API Gateway và Application Load Balancer.
* **Quản lý Cấu hình An toàn**:
  * Chuyển toàn bộ cấu hình bảo mật, API Keys và Secret Tokens từ cấu hình mã nguồn sang lưu trữ tập trung và mã hóa trên AWS Secrets Manager / Systems Manager Parameter Store.

#### 2. Tối ưu hóa Chi phí Vận hành & Hiệu năng
* **Quản lý Chi phí Chi tiết**:
  * Cấu hình thành công AWS Budgets để gửi cảnh báo tức thì qua Email/SNS nếu chi phí dự án vượt quá hạn mức cho phép.
  * Dọn dẹp hoàn toàn các tài nguyên dư thừa (EBS snapshots cũ, Elastic IPs chưa gán, CloudWatch logs dư thừa), giảm bớt chi phí duy trì hàng tháng.
* **Tối ưu Hiệu năng**:
  * Tinh chỉnh cấu hình DynamoDB Auto-scaling/On-Demand và điều chỉnh Instance Types của EC2 phù hợp với tải thực tế của hệ thống Smart Home.

#### 3. Nghiệm thu Hệ thống & Tổng kết Dự án Smart Home
* **Nghiệm thu Toàn diện (E2E Verified)**:
  * Kiểm thử thành công toàn bộ luồng hoạt động tổng thể từ người dùng thao tác trên Web Dashboard -> truyền qua API Gateway -> điều hướng bởi ALB -> xử lý tại EC2 Backend -> lưu trữ trạng thái tại DynamoDB -> lưu nhật ký lâu dài trên S3 và phát cảnh báo qua CloudWatch/SNS.
  * Hệ thống vận hành ổn định, thời gian phản hồi trung bình < 150ms và có khả năng phục hồi tự động khi gặp sự cố.
* **Hoàn thiện Báo cáo & Tài liệu Kỹ thuật**:
  * Đã vẽ và đóng gói sơ đồ kiến trúc tổng thể dự án Smart Home trên AWS.
  * Tổng hợp đầy đủ báo cáo kết quả thực tập 8 tuần, tài liệu hướng dẫn triển khai.
