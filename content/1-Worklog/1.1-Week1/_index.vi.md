---
title: "Worklog Tuần 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

* Kết nối, làm quen với các thành viên trong chương trình First Cloud AI Journey (FCAJ).
* Nắm vững kiến thức nền tảng về hệ sinh thái AWS, cách quản lý tài nguyên thông qua AWS Management Console và AWS CLI.
* Hiểu rõ vai trò của các dịch vụ cốt lõi trong kiến trúc Smart Home: **EC2, DynamoDB, S3, Amplify, AWS IoT Core, Security Group/AWS WAF**.
* Thực hành khởi tạo, kết nối an toàn và quản lý tài nguyên lưu trữ trên máy chủ ảo Amazon EC2.

---

### Các công việc triển khai trong tuần:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :--- |
| **2** | - Làm quen với các thành viên FCAJ <br>- Đọc và ghi nhớ các nội quy, quy định tại đơn vị thực tập | 08/06/2026 | 08/06/2026 | Nội bộ FCAJ |
| **3** | - Tìm hiểu tổng quan về AWS Cloud và các nhóm dịch vụ cốt lõi cho kiến trúc Smart Home: <br>&emsp; + **Compute & Frontend:** EC2, AWS Amplify <br>&emsp; + **Storage & Database:** S3, DynamoDB <br>&emsp; + **IoT & Security:** AWS IoT Core, Security Group, AWS WAF, IAM | 09/06/2026 | 09/06/2026 |  |
| **4** | - Tạo tài khoản AWS Free Tier <br>- Tìm hiểu AWS Console & AWS CLI <br>- **Thực hành:** <br>&emsp; + Thiết lập bảo mật tài khoản cá nhân <br>&emsp; + Cài đặt AWS CLI v2 trên máy cục bộ <br>&emsp; + Cấu hình Credential `aws configure` | 10/06/2026 | 10/06/2026 | [AWS Cloud Console](https://aws.amazon.com/free/?trk=fbdf98be-fd82-4f85-ba7f-1fec88374081&sc_channel=ps&ef_id=ec8060e13ed319e671920a8660f751e1:G:s&msads_camp=487968829&msads_ag=1139095928684818&msads_ad=71193664952043&msads_kw=aws&msads_matchtype=e&msads_network=o&msads_device=c&msads_geo={LocationId}&msclkid=ec8060e13ed319e671920a8660f751e1) |
| **5** | - Tìm hiểu sâu về máy chủ ảo EC2 để lưu trữ ứng dụng Backend Smart Home: <br>&emsp; + Khái niệm Instance Types, AMI Amazon Machine Image <br>&emsp; + Khái niệm Block Storage EBS Volume, EBS Snapshot <br>- Các phương thức remote SSH vào EC2 như Key Pair, EC2 Instance Connect <br>- Tìm hiểu cơ chế gán IP tĩnh Elastic IP | 11/06/2026 | 11/06/2026 | [EC2](https://aws.amazon.com/search/?searchQuery=EC2) |
| **6** | - **Thực hành:** <br>&emsp; + Khởi tạo EC2 Instance Ubuntu hoặc Amazon Linux <br>&emsp; + Kết nối SSH qua Terminal hoặc OpenSSH <br>&emsp; + Tạo, đính kèm, định dạng và mount EBS Volume bổ sung vào OS để chuẩn bị cho dữ liệu Backend | 12/06/2026 | 12/06/2026 | [EC2](https://aws.amazon.com/search/?searchQuery=EC2) |

---

### Kết quả đạt được tuần 1:

#### 1. Kiến thức nền tảng & Tài khoản AWS
* **Hiểu rõ tổng quan hệ sinh thái AWS**: Phân biệt được vai trò của từng nhóm dịch vụ cốt lõi dành riêng cho hạ tầng Smart Home (**EC2** làm Backend xử lý, **DynamoDB** lưu trạng thái thiết bị, **S3** lưu log, **Amplify** triển khai Web Dashboard, **AWS IoT Core** kết nối thiết bị và **Security Group/WAF** bảo vệ hệ thống).
* **Khởi tạo tài khoản an toàn**: Khởi tạo thành công tài khoản AWS Free Tier và thiết lập các lớp bảo mật ban đầu.

#### 2. Thành thạo AWS CLI & Đồng bộ hóa quản lý
* **Cài đặt & Cấu hình thành công AWS CLI v2**:
  * Thực hiện lệnh để thiết lập thành công **Access Key ID**, **Secret Access Key**, Default Region.
* **Sử dụng thạo các câu lệnh AWS CLI thực tế**:
  * **Xác thực tài khoản**: Kiểm tra IAM User đang đăng nhập.
  * **Quản lý EC2**: Liệt kê danh sách các máy chủ ảo đang chạy.
  * **Quản lý Key Pair**: Khởi tạo khóa SSH trực tiếp từ dòng lệnh.
* **Tư duy quản lý song song**: Hiểu rõ cơ chế hoạt động bên dưới của AWS Console bản chất cũng gọi đến các API tương tự như CLI, giúp kết nối linh hoạt giữa việc thao tác giao diện trực quan và tự động hóa tác vụ bằng dòng lệnh.

#### 3. Thực hành chuyên sâu với Amazon EC2 & EBS Storage
* **Triển khai máy chủ ảo EC2**:
  * Tự tay launch thành công EC2 Instance thuộc dòng `t2.micro` / `t3.micro` sử dụng hệ điều hành Ubuntu/Amazon Linux 2023 làm máy chủ Backend Smart Home.
  * Cấu hình Security Group mở các cổng kết nối cần thiết: Port `22` (SSH) và Port `80`/`443` (HTTP/HTTPS).
* **Kết nối an toàn vào máy chủ**:
  * Phân biệt và thực hành thành công việc SSH vào EC2 bằng cả 2 cách: Dùng lệnh từ máy cục bộ và dùng giao diện web **EC2 Instance Connect**.
* **Làm chủ lưu trữ ổ đĩa EBS**:
  * Khởi tạo thêm 1 ổ đĩa EBS bổ sung trên cùng Availability Zone với EC2.
  * Thực hiện đính kèm ổ đĩa vào EC2 thành công.
  * **Thao tác trực tiếp trên Linux OS**: Sử dụng các lệnh hệ thống để khởi tạo định dạng file system `ext4` và mount thành công thư mục lưu trữ mới vào hệ thống.