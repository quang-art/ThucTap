---
title: "Event 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Báo cáo thu hoạch: Workshop GenAI-powered App-DB Modernization & AWS Community Day

## Tóm tắt sự kiện
Buổi workshop chuyên sâu này đã mang lại cái nhìn toàn cảnh về các xu hướng công nghệ tiên tiến nhất hiện nay trong lĩnh vực Trí tuệ nhân tạo tạo sinh (GenAI), tối ưu hóa kiến trúc Mô hình ngôn ngữ lớn (LLM) và các kỹ thuật tối ưu hóa đường truyền mạng đám mây. Các diễn giả giàu kinh nghiệm từ VPBank, GoTymeX, và Cloud Kinetics đã chia sẻ các phương pháp thực tiễn để xây dựng hệ thống Multi-Agent phức tạp, làm chủ kỹ nghệ thiết kế ngữ cảnh (Context Engineering), và cấu hình CDN CloudFront nhằm đảm bảo hiệu năng tối đa cho doanh nghiệp.

---

## Chi tiết các chủ đề chia sẻ & Điểm nhấn kỹ thuật

### 1. Kiến trúc Multi-Agent trong doanh nghiệp tài chính
* **Diễn giả:** Vy Lam (Senior Business Systems Analyst tại VPBank)
* **Thực trạng nghiệp vụ:** Các quy trình đánh giá tín dụng truyền thống đòi hỏi nhiều năm báo cáo tài chính và tài sản thế chấp, hoàn toàn không tương thích với các doanh nghiệp khởi nghiệp vốn có cấu trúc dữ liệu thô và rời rạc.
* **Giải pháp:** Xây dựng mô hình *Virtual Credit Committee* (Ủy ban tín dụng ảo) phân rã công việc cho các trợ lý AI chuyên biệt (Phân tích tài chính, Kiểm soát tuân thủ, Đánh giá rủi ro) giao tiếp thông qua Model Context Protocol (MCP).
* **Hiệu quả:** Rút ngắn thời gian xử lý hồ sơ từ vài tuần xuống còn dưới 4 giờ, đồng thời giảm hơn 90% chi phí vận hành. Bảo mật được kiểm soát chặt chẽ bằng Bedrock AgentCore và các bộ lọc PII.

### 2. Tính chất phi tuyến tính (Non-Deterministic) của mô hình LLM
* **Diễn giả:** Đức Đào (Solutions Architect tại Cloud Kinetics)
* **Khái niệm cốt lõi:** Việc thiết đặt tham số Temperature = 0 (Greedy Decoding) trên thực tế không đảm bảo 100% kết quả đầu ra giống hệt nhau ở mọi lần chạy. Nguyên nhân do kiến trúc tính toán song song của phần cứng GPU, các sai số dấu phẩy động và giải thuật tối ưu hóa khi suy luận.
* **Giải pháp thực tiễn:** Thiết đặt nhiệt độ ở mức thấp ($T = 0.1$) để tránh các vòng lặp phản hồi lặp lại vô hạn, cấu hình hình phạt lặp lại (repetition penalty) và quản lý kết quả đầu ra bằng schema tham số định dạng cấu trúc JSON thay vì chỉ dùng Prompt.

### 3. Vượt qua giới hạn trong các cuộc thi Hackathon
* **Case Study:** Đội ngũ phát triển dự án UTMorpho tại Lotus Hacks (Team VIB)
* **Kinh nghiệm thực tiễn:** Cách thức đối mặt với áp lực thời gian (36 giờ liên tục), bài toán giới hạn token (Token limits) và phân bổ công việc dưới áp lực cực lớn. Dự án thành công nhờ tối ưu hóa quy trình tập trung viết code cô lập và đồng bộ hóa cấu trúc API nhanh chóng.

### 4. Tự động hóa công việc hành chính bằng Amazon Q
* **Diễn giả:** Hải Anh (G-AsiaPacific, AWS Community Builder)
* **Giải pháp:** Sử dụng Amazon Q kết nối hơn 40 nguồn dữ liệu doanh nghiệp để tự động hóa luồng việc văn phòng. Trợ lý AI (PM Assistant) tự động tổng hợp biên bản họp (MoM), gửi email thông báo cho các bên liên quan và tự lên lịch họp theo dõi tiến độ.

### 5. Tối ưu hóa CDN & Quản lý chi phí hạ tầng
* **Diễn giả:** Nguyễn Tuấn Thịnh (DevOps Engineer)
* **Giải pháp chi phí:** Áp dụng các gói thuê bao cố định của CloudFront để bảo vệ doanh nghiệp khỏi các đợt tăng vọt chi phí bất ngờ do lưu lượng tăng đột biến hoặc các đợt tấn công DDoS.
* **Hiệu năng hệ thống:** Tận dụng hơn 700 điểm phân phối (PoPs) toàn cầu giúp giảm tải CPU của máy chủ gốc (EC2) từ 5% xuống 1%. Giao thức HTTP/3 giúp tăng tốc độ tải tài nguyên, giảm thời gian phản hồi hệ thống 81% (từ 123ms xuống còn 24ms).

### 6. Kỹ nghệ thiết kế ngữ cảnh (Context Engineering)
* **Diễn giả:** Tịnh Trương (Platform Engineer tại GoTymeX)
* **Thông điệp cốt lõi:** Đầu ra kém chất lượng của AI đa phần do ngữ cảnh đầu vào (context) sơ sài hoặc sai cách, không phải do năng lực của mô hình LLM.
* **Sai lầm cần tránh:** Nhồi nhét tài liệu dài chưa qua xử lý vào chatbox (*the internet puller*), giải thích dài dòng các thiết lập công nghệ có sẵn, và không đưa ra các ràng buộc cụ thể.
* **Khung ngữ cảnh chuẩn (Simple Context Framework):** Một câu prompt chất lượng cần có đủ 4 yếu tố: **Mục tiêu (Goal)**, **Thông tin liên quan (Info)**, **Các ràng buộc (Constraints)**, và **Tiêu chí thành công (Success Criteria)**.

---

## Trải nghiệm thực tế & Kế hoạch áp dụng

### Bài học tư duy hệ thống
* **Tư duy hướng nghiệp vụ (Business-First):** Lựa chọn công nghệ phải đi sau việc giải quyết triệt để bài toán kinh doanh thực tế, không chạy theo trào lưu công nghệ.
* **Tư duy xác suất:** Khi làm việc với LLMs, lập trình viên cần thiết kế sẵn các lớp kiểm thử và xác thực dữ liệu đầu ra để xử lý các biến động phản hồi.
* **Tối ưu hóa biên (Edge computing):** Chuyển các logic định tuyến và kiểm tra bảo mật cơ bản ra CDN/CloudFront Functions để giảm tải cho backend chính.

### Dự định áp dụng vào dự án
* Áp dụng triệt để khuông ngữ cảnh 4 thành phần trong mọi giao tiếp hàng ngày với trợ lý AI.
* Nghiên cứu tích hợp các luồng Multi-Agent cho các tác vụ phân tích log hệ thống.
* Sử dụng CDN CloudFront kết hợp ẩn giấu IP máy chủ gốc (Origin Cloaking) cho đồ án tốt nghiệp nhằm tăng tính bảo mật trước các đợt tấn công giả lập DDoS.

---

## Hình ảnh tại sự kiện
![alt text](z7866450150269_87bf550e28462644de70351a8524597e.jpg)
![alt text](z7866450137122_fa7ac674224cf3e8b1fe76ae81263462.jpg)
![alt text](z7866450114341_f4f7bf1c450c1fbfc72d663d28be7689.jpg)