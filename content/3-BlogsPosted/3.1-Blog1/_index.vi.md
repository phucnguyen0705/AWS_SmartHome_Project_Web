---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "

---

# [AMAZON EMR ON EC2] TỐI ƯU HÓA MONITORING & DEBUGGING VỚI 5 TÍNH NĂNG MỚI
Xin chào mọi người,

Khi vận hành các hệ thống xử lý dữ liệu lớn (Big Data) trên Amazon EMR, việc theo dõi và debug thường tốn khá nhiều thời gian: log phân tán trên nhiều node, khó khớp EMR Step với YARN App, phải setup SSH/Proxy phức tạp để mở giao diện UI...

Với việc ra mắt các bản cập nhật mới nhất từ AWS, hệ thống đã bổ sung 5 tính năng lớn giúp đơn giản hóa toàn bộ quy trình giám sát và xử lý sự cố.
---
### Các tính năng mới:
* **Stream Log thời gian thực sang CloudWatch:** Tự động đẩy Step log, Spark Driver & Executor log sang CloudWatch ngay khi phát sinh. Cho phép tùy chỉnh Log Group, mã hóa KMS và lọc log nhanh qua CloudWatch Logs Insights.
* **Quản lý Log S3 chi tiết tới từng Step:** Cho phép cấu hình đường dẫn S3 và khóa KMS riêng biệt cho từng Step cụ thể, đảm bảo phân quyền bảo mật khắt khe cho mô hình dùng chung (multi-tenant).
* **Mở trực tiếp Live UI trên Console:** Mở trực tiếp YARN ResourceManager UI và Tez UI ngay trên AWS Console mà không cần cấu hình thủ công.
* **Map trực tiếp EMR Step với YARN Application ID:** Hiển thị ngay YARN Application ID trong giao diện thông tin chi tiết của Step giúp bấm chuyển tiếp nhanh sang YARN UI / Spark History.
* **Mở rộng Custom Metrics & Giám sát linh hoạt:** Thu thập metric chi tiết (tần suất 1 phút) của Hadoop, YARN, HBase qua CloudWatch Agent, cho phép thay đổi cấu hình metric trên cluster đang chạy mà không cần restart.

---

### Tối ưu chi phí:

* **Loại bỏ hạ tầng Proxy & Bastion Host:** Mở trực tiếp Live UI (YARN UI/Tez UI) ngay trên AWS Console giúp loại bỏ hoàn toàn việc dựng server trung gian, cấu hình SSH Tunnel, Proxy hay mở cổng mạng phức tạp. Điều này vừa giúp giảm chi phí duy trì tài nguyên mạng, vừa đảm bảo an toàn bảo mật.
* **Tối ưu hóa thời gian xử lý sự cố (MTTR):** Việc tra cứu log tức thì qua CloudWatch Logs Insights và link trực tiếp Step với YARN App giúp các kỹ sư tìm ra nguyên nhân gốc rễ lỗi pipeline nhanh chóng, giảm thiểu rủi ro pipeline bị nghẽn làm tăng giờ chạy EC2 không cần thiết.

*(Lưu ý: Việc stream log & metric sang CloudWatch sẽ phát sinh thêm một khoản chi phí nhỏ tùy theo dung lượng dữ liệu nạp vào).*

---

### Công dụng:

* **Truy vết và tìm nguyên nhân lỗi ngay lập tức:** Bấm trực tiếp từ EMR Step sang YARN UI / Spark History hoặc tra cứu log container trên S3 để khoanh vùng sự cố của job Spark/Hadoop mà không cần chờ đẩy file log hoàn tất hay SSH vào từng node.
* **Giám sát tập trung và xuất dữ liệu linh hoạt:** Tích hợp trực tiếp các chỉ số metric của Hadoop, YARN, HBase vào hệ thống giám sát hiện có như CloudWatch, Prometheus hoặc Grafana để xây dựng dashboard theo dõi toàn diện cho toàn bộ Data Pipeline.

---

### Đánh giá & Kết luận:

Các tính năng mới của Amazon EMR on EC2 thực sự đem lại trải nghiệm tuyệt vời cho các Data Engineer và Cloud Ops, giúp cắt giảm tối đa thời gian debug pipeline và đơn giản hóa khâu quản trị hệ thống. Bạn hoàn toàn có thể trải nghiệm ngay các tính năng này trên cluster EMR của mình hôm nay!


---

### Link bài viết chính thức từ AWS

* [Tối ưu hóa việc giám sát và gỡ lỗi cho Amazon EMR trên EC2](https://aws.amazon.com/blogs/big-data/streamlined-monitoring-and-debugging-for-amazon-emr-on-ec2/)

---
### Hình ảnh bài viết

![Bài viết trong nhóm](/static/blog_1_final.jpg)