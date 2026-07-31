---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---


Tại đây sẽ là phần liệt kê, giới thiệu các blogs mà các bạn đã đăng trên [AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj). Ví dụ:

### [Blog 1 - Amazon EMR on EC2: Tối ưu hóa Monitoring & Debugging với 5 tính năng mới](3.1-Blog1/_index.vi.md)
Blog này chia sẻ trải nghiệm thực tế về 5 tính năng mới trên Amazon EMR on EC2 (Stream Log CloudWatch, S3 Log per step, Live UI Console, Map EMR Step với YARN App ID, Custom Metrics). Giải pháp giúp đơn giản hóa quy trình giám sát, loại bỏ hạ tầng Proxy/Bastion Host phức tạp và tối ưu chi phí vận hành cho hệ thống Big Data.

### [Blog 2 - AWS Amplify: Lựa chọn gọn nhẹ để Host Web làm Demo / Báo cáo Workshop](3.2-Blog2/_index.vi.md)
Blog này giới thiệu giải pháp sử dụng AWS Amplify Hosting để triển khai nhanh các trang web Demo/Workshop mà không tốn thời gian dựng S3, CloudFront hay Route 53. Đồng thời cập nhật tính năng mới tích hợp sẵn tường lửa AWS WAF (Web Application Firewall) giúp bảo vệ trang web dễ dàng chỉ với vài click.

### [Blog 3 - Modernizing Lambda + S3 workloads with Amazon S3 Files](3.3-Blog3/_index.vi.md)
Blog này phân tích giải pháp thay thế luồng xử lý dữ liệu truyền thống giữa AWS Lambda và S3 bằng tính năng Amazon S3 Files. Nhờ cơ chế mount trực tiếp S3 Bucket qua VPC Endpoint, lập trình viên có thể loại bỏ hoàn toàn các đoạn mã trung chuyển qua thư mục tạm `/tmp`, giúp mã nguồn gọn gàng hơn và tránh tràn ổ đĩa khi xử lý file dung lượng lớn.
