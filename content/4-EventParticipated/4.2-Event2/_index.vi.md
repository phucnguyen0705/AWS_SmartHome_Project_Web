---
title: "Event 2"
date: 2026-07-11
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---
# Bài thu hoạch “FCAJ x Agentic AI Build Week”

### Mục Đích Của Sự Kiện

- Chia sẻ các kinh nghiệm và trải nghiệm đáng nhớ trong cuộc thi Hackathon
- Giới thiệu phương pháp DDD và event-driven architecture
- Hướng dẫn lựa chọn compute services phù hợp


### Nội Dung Nổi Bật

#### Đưa ra các ảnh hưởng tiêu cực của kiến trúc ứng dụng cũ

- Thời gian release sản phẩm lâu → Mất doanh thu và bỏ lỡ cơ hội


#### Chuyển đổi sang kiến trúc Microservice hiện đại

Chuyển đổi thành hệ thống modular – từng chức năng là một **dịch vụ độc lập** giao tiếp với nhau qua **sự kiện** với 3 trụ cột cốt lõi:

- **Queue Management**: Xử lý tác vụ bất đồng bộ
- **Caching Strategy:** Tối ưu performance
- **Message Handling:** Giao tiếp linh hoạt giữa services

#### Domain-Driven Design (DDD)

- **Phương pháp 4 bước**: Xác định domain events → sắp xếp timeline → identify actors → xác định bounded contexts
- **Case study bookstore**: Minh họa cách áp dụng DDD thực tế
- **Context mapping**: 7 patterns tích hợp bounded contexts

#### Event-Driven Architecture

- **3 patterns tích hợp**: Publish/Subscribe, Point-to-point, Streaming
- **Lợi ích**: Loose coupling, scalability, resilience
- **So sánh sync vs async**: Hiểu rõ trade-offs (sự đánh đổi)


### Những Gì Học Được

#### Tư Duy Thiết Kế

- **Business-first approach**: Luôn bắt đầu từ business domain, không phải technology
- **Ubiquitous language**: Tầm quan trọng của từ vựng chung giữa business và tech teams
- **Bounded contexts**: Cách identify và quản lý sự phức tạp trong large systems

#### Kiến Trúc Kỹ Thuật

- **Event storming technique**: Phương pháp thực tế để mô hình hóa quy trình kinh doanh
- Sử dụng **Event-driven communication** thay vì synchronous calls
- **Integration patterns**: Hiểu khi nào dùng sync, async, pub/sub, streaming
- **Compute spectrum**: Criteria chọn từ VM → containers → serverless


### Ứng Dụng Vào Công Việc

- **Áp dụng DDD** cho project hiện tại: Tổ chức Event Storming sessions với business team
- **Refactor microservices**: Sử dụng bounded contexts để xác định service boundaries
- **Implement event-driven patterns**: Thay thế một số sync calls bằng async messaging


### Trải Nghiệm Sự Kiện & Bài Học Rút Ra Từ Video

Tham gia sự kiện **“FCAJ x Agentic AI Build Week”** (đồng tổ chức cùng JI Fund & AWS) mang lại nhiều giá trị thực tế qua các bài chia sẻ kỹ thuật và các phần pitch dự án:

#### Định hướng từ các chuyên gia hàng đầu
- Lắng nghe chia sẻ từ **Mr. Nguyễn Gia Hưng** (Head of Solutions Architect, AWS Vietnam) và **Mr. Joseph Marazota** (Head of Technology, AWS ASEAN).
- **Chuyển đổi tư duy trong kỷ nguyên Agentic AI**: Phát triển phần mềm truyền thống cập nhật theo chu kỳ nhiều tuần, trong khi AI Agent có thể tự động triển khai liên tục từng phút. Kỹ sư cần dám thử nghiệm và thoát khỏi tư duy cũ.
- **Giảm thiểu ma sát cho người dùng (Friction Reduction)**: Ứng dụng hiện đại tập trung cắt giảm các thao tác rườm rà (đăng ký phức tạp, menu nhiều quảng cáo) bằng cách giao trực tiếp tác vụ cho AI Agent thực thi.

#### Bài học từ Hackathon: Từ PoC đến Production
Tạo bản PoC trong thời gian ngắn của cuộc thi Hackathon giúp kiểm chứng ý tưởng nhanh chóng, nhưng để đưa vào thực tế cần giải quyết 3 bài toán lớn:
1. **Guardrails (Thành rào kiểm soát)**: Thiết lập cơ chế kiểm soát kỹ lưỡng đầu ra trước khi cho phép AI Agent ra quyết định.
2. **Chi phí vận hành**: Quản lý và tối ưu chi phí gọi API/LLM khi chạy các vòng lặp Agent liên tục.
3. **Vòng lặp tương tác (Human-in-the-loop)**: Xây dựng cơ chế cho phép AI Agent thu thập phản hồi từ chuyên gia (như Data Analyst) để liên tục tối ưu hóa kết quả.


### Hình Ảnh & Đường Dẫn Sự Kiện

![Ảnh chứng minh đi event](/event_2.png)
