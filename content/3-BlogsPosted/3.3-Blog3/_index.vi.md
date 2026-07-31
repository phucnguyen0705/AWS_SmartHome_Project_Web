---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---


# [AWS COMPUTE BLOG] MODERNIZING LAMBDA + S3 WORKLOADS WITH AMAZON S3 FILES – ĐIỀU CHÚNG MÌNH HỌC ĐƯỢC SAU KHU TÌM HIỂU GIẢI PHÁP THAY THẾ

Xin chào mọi người,

Trong quá trình làm việc với AWS, mô hình kết hợp giữa AWS Lambda và Amazon S3 là một pattern cực kỳ quen thuộc. Bình thường, khi cần xử lý file (như resize ảnh, đọc file CSV/Parquet hay làm bộ nhớ tạm cho AI Agent), luồng xử lý kinh điển của mình sẽ là: 

Tải file từ S3 về bộ nhớ tạm `/tmp` -> Xử lý file -> Upload kết quả ngược lại S3 -> Xóa file tạm `/tmp`.

Ban đầu mình nghĩ đây là cách làm tiêu chuẩn và tốt nhất. Tuy nhiên, khi đọc bài viết mới trên AWS Compute Blog về **Amazon S3 Files**, mình nhận ra rằng việc phải tự viết code quản lý download/upload, liên tục canh chừng giới hạn dung lượng `/tmp` hay dọn dẹp file thừa là những công việc không cần thiết.

---

### Thư mục `/tmp` là gì?

Thư mục `/tmp` (Ephemeral Storage) là vùng ổ đĩa tạm thời được AWS cấp sẵn cho mỗi môi trường chạy Lambda. Vùng tạm này có dung lượng giới hạn, chỉ tồn tại ngắn hạn và sẽ tự động bị xóa sạch khi Lambda ngừng hoạt động.

AWS hiện đã cho phép Lambda mount thẳng S3 Bucket như một ổ đĩa local thông qua tính năng **Amazon S3 Files**.

---

### Mô hình kiến trúc & Luồng hoạt động

![Sơ đồ kiến trúc Amazon S3 Files](/static/blog_3_architect.jpg)
*Hình 1: Sơ đồ kiến trúc kết hợp giữa AWS Lambda và S3 thông qua S3 VPC Endpoint*

Dựa trên sơ đồ kiến trúc trên, luồng xử lý của hệ thống bao gồm 4 bước chính:

1. **Event / Trigger:** Client gửi yêu cầu kích hoạt (trigger) hàm AWS Lambda.
2. **Direct Read/Write:** Thay vì tải file qua AWS SDK, AWS Lambda thực hiện đọc/ghi trực tiếp vào đường dẫn ổ đĩa local thông qua **S3 VPC Endpoint** được mount sẵn trong VPC.
3. **Auto Sync:** Dữ liệu sau khi ghi vào ổ đĩa mount sẽ được hệ thống file bên dưới tự động đồng bộ (Auto Sync) lên **Amazon S3 Bucket Storage**.
4. **Read Final Files:** Người dùng hoặc các dịch vụ khác có thể đọc trực tiếp các file kết quả hoàn chỉnh từ Amazon S3 Bucket.

---

### Không còn phải lo lắng về bộ nhớ `/tmp`

Mình học được là mình có thể loại bỏ hoàn toàn mã thư viện (như `boto3`) dùng để trung chuyển dữ liệu giữa S3 và Lambda. Thay vì viết dòng lệnh `s3.download_file()` hay `s3.upload_file()`, Lambda giờ đây có thể đọc/ghi trực tiếp vào một đường dẫn mount local (ví dụ: `/mnt/data` hoặc `/mnt/workspace`).

Theo cá nhân mình, cách làm này mang lại 3 lợi ích vượt trội:

* **Loại bỏ giới hạn dung lượng `/tmp`:** Xử lý các file lớn dễ dàng mà không sợ tràn ổ đĩa tạm.
* **Mã nguồn ngắn hơn hẳn:** Rút gọn từ vài chục dòng code phức tạp xuống chỉ còn vài dòng đọc/ghi file thuần túy (Native File I/O).
* **Không tốn lệnh gọi S3 API:** Loại bỏ hoàn toàn các lệnh `GET`/`PUT` Object giúp giảm thiểu chi phí và lỗi kết nối mạng trong quá trình truyền tải.

---

### AWS kết hợp VPC, S3 Files và Lambda như thế nào?

Để áp dụng kiến trúc này, AWS kết nối các dịch vụ thông qua cơ chế tích hợp mạng nội bộ:

1. **S3 File System & VPC:** Tạo một S3 File System cho Bucket, tạo Mount Target và Access Point trong Amazon VPC.
2. **AWS Lambda in VPC:** Đặt hàm Lambda vào trong VPC và cấu hình đính kèm File System với đường dẫn Mount Path (ví dụ: `/mnt/images`).
3. **Phân quyền IAM:** Cấp quyền `s3files:ClientMount` và `s3files:ClientWrite` cho IAM Role của Lambda để hàm có quyền truy cập ổ đĩa.
4. **Tối ưu hiệu năng:** Nếu xử lý file dung lượng lớn, chỉ cần cấp cho Lambda từ 512 MB RAM trở lên để bật cơ chế đọc trực tiếp (Direct Reads) từ S3.

---

### Đây là ví dụ điển hình về việc tối ưu trải nghiệm lập trình viên

Theo cá nhân mình, điểm thú vị nhất của Amazon S3 Files là nó đưa lập trình viên trở về với cách tư duy lập trình đơn giản nhất: **Thao tác với File System local**.

Lập trình viên khi nhìn vào đoạn mã chỉ thấy đúng logic nghiệp vụ cốt lõi (Resize ảnh, convert dữ liệu, ghi báo cáo). Trong khi đó, các thuật toán đồng bộ, quản lý trạng thái truyền dữ liệu hay tính toàn vẹn file đã được hệ thống file bên dưới tự động gánh vác.

---

### Điều mình rút ra sau khi tìm hiểu

Sau khi tìm hiểu tính năng Amazon S3 Files, mình nhận ra rằng tối ưu hóa hệ thống Serverless không phải lúc nào cũng là cố gắng quản lý các file tạm `/tmp` thật khéo léo, mà là loại bỏ luôn đoạn mã trung chuyển không cần thiết.

Tuy nhiên, mình cũng lưu ý rằng S3 Files đòi hỏi Lambda phải chạy trong VPC. Với các tác vụ cần dùng tính năng S3 API đặc thù như Presigned URL, S3 Select hay Multipart Upload, cách tiếp cận truyền thống qua SDK/API vẫn phải bắt buộc.

---

### Đánh giá & Kết luận

Do vậy, Amazon S3 Files không chỉ là một tính năng mới mà còn là một bước tiến giúp đơn giản hóa đáng kể kiến trúc Serverless trên AWS.

Nếu dự án của bạn đang vận hành các ETL Pipeline dữ liệu lớn, hay các hệ thống Multi-agent AI trên Lambda, đây chắc chắn là một giải pháp rất đáng để cân nhắc chuyển đổi nhằm làm sạch mã nguồn và giảm bớt các kịch bản xử lý lỗi.

Cảm ơn mọi người đã dành thời gian đọc bài tổng hợp của mình!

---

### Link bài viết chính thức từ AWS

👉 [Modernizing Lambda + S3 workloads with Amazon S3 Files](https://aws.amazon.com/blogs/compute/modernizing-lambda-s3-workloads-with-amazon-s3-files/)

---

### Hình ảnh bài viết

![Bài viết trong nhóm](/static/blog_3_final.jpg)