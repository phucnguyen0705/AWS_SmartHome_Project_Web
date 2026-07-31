---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---


# [AWS AMPLIFY] LỰA CHỌN GỌN NHẸ ĐỂ HOST WEB LÀM DEMO / BÁO CÁO WORKSHOP

Xin chào mọi người,

Khi chuẩn bị bài báo cáo hoặc làm Demo, nhu cầu lớn nhất của mình thường là: Host trang web thật nhanh, thao tác đơn giản, không tốn thời gian cấu hình hạ tầng phức tạp.

Bình thường, nếu dựng web theo cách truyền thống trên AWS, luồng công việc của mình sẽ khá tốn thời gian:

Tạo S3 Bucket -> Cấu hình Static Website Hosting -> Tạo CloudFront Distribution -> Cài đặt Route 53 / SSL Certificate.

Tuy nhiên, sau khi tìm hiểu và trải nghiệm thực tế, mình nhận ra **AWS Amplify Hosting** mới là giải pháp lý tưởng để làm bài báo cáo Workshop gọn nhẹ và chuyên nghiệp nhất.

---

### Tính năng & Lợi ích chính:

* **Triển khai trong vài phút:** Kết nối với repository (GitHub/GitLab/Bitbucket) hoặc drag & drop trực tiếp thư mục code build (HTML/JS/React/Vue/Next.js) lên console.
* **Tự động hóa CI/CD:** Mỗi lần nhóm push code mới phục vụ Workshop, Amplify sẽ tự động build và deploy lại trang web ngay lập tức.
* **Sẵn SSL / Domain mặc định:** Ngay sau khi deploy, nhóm nhận ngay một đường link HTTPS dạng `https://main.xxx.amplifyapp.com` để gửi cho mọi người truy cập thử nghiệm.

---

### Tính năng mới: Tích hợp sẵn tường lửa AWS WAF

Trước đây, các dự án demo/workshop rất ngại bật bảo mật vì cấu hình rườm rà. Tuy nhiên, Amplify hiện đã tích hợp trực tiếp **AWS WAF (Web Application Firewall)** ngay trên giao diện Amplify Console.

Chỉ với vài thao tác click đơn giản, mình đã có thể trang bị cho bài demo các tính năng bảo vệ chuẩn enterprise:

* **Chặn IP:** Chỉ cho phép hoặc chặn các dải IP truy cập thử nghiệm.
* **Giới hạn địa lý:** Giới hạn truy cập theo quốc gia.
* **Bảo vệ tự động:** Chặn các lỗ hổng web phổ biến và IP độc hại dựa trên dữ liệu đe dọa của Amazon.

---

### Đánh giá trải nghiệm & Chi phí:

* **Tối giản hạ tầng:** Việc dùng Amplify giúp nhóm loại bỏ hoàn toàn các bước cấu hình mạng/hạ tầng rườm rà, đưa trải nghiệm về đúng nghĩa: **Code xong -> Push -> Có Web demo ngay**.
* **Tối ưu chi phí:** Dịch vụ này rất tiết kiệm và nằm trong gói AWS Free Tier cho các nhu cầu cơ bản. Tuy nhiên, cần lưu ý sẽ có phát sinh thêm chi phí nhỏ nếu bạn cấu hình Domain tùy chỉnh, sử dụng băng thông lớn hoặc bật các rule của AWS WAF.

---

### Đánh giá & Kết luận:

Nếu bạn đang chuẩn bị bài báo cáo Workshop, thuyết trình dự án môn học hoặc làm Demo MVP cho khách hàng, AWS Amplify Hosting chắc chắn là lựa chọn hàng đầu để tiết kiệm thời gian và công sức.

Cảm ơn mọi người đã đọc bài chia sẻ!

---

### Link bài viết chính thức từ AWS:

* [Firewall Support for AWS Amplify Hosted Sites](https://aws.amazon.com/blogs/aws/firewall-support-for-aws-amplify-hosted-sites/?fbclid=IwY2xjawTPp1BleHRuA2FlbQIxMABicmlkETFNYnpiUTR6MFlXVzU0VUlwc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHo0lvAi7DyFK9RJz0yuaw3CPM4QNkT9NrC-0qEVszM-385ZdVzScGEZmy_8q_aem_MUI1FfeLVhGideiv_cVscw)  
* [AWS Amplify Hosting Adds Web Application Firewall Protection](https://aws.amazon.com/blogs/mobile/aws-amplify-hosting-adds-web-application-firewall-protection-public-preview/?fbclid=IwY2xjawTPp2ZleHRuA2FlbQIxMABicmlkETFNYnpiUTR6MFlXVzU0VUlwc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHqXhzynO67qDjqNn3iCMDAfwPy9WEXcts29g6twMNkRuNRLowpWiyHPrmMr5_aem_0IyIORQVVOYTLh5ZvFYKfw)

---

### Hình ảnh bài viết:

![Bài viết trong nhóm](/static/blog_2_final.jpg)