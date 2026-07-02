---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Báo cáo thu hoạch: AWS Cloud & DevOps Meetup & Workshop

## Tóm tắt sự kiện
Việc tham dự chuỗi sự kiện chia sẻ kỹ thuật và buổi workshop chuyên sâu này đã giúp em tích lũy được nhiều kiến thức quý báu về tư duy thiết kế hệ thống hiện đại, quá trình chuyển dịch từ kiến trúc nguyên khối (Monolithic) cũ sang hệ sinh thái điện toán đám mây (Cloud-native), cùng với cách thức vận hành tối ưu của các nhóm công nghệ lớn. Sự kiện quy tụ nhiều chuyên gia đầu ngành từ AWS, Endava Việt Nam và các tập đoàn đa quốc gia nhằm chia sẻ các bài học thực tiễn trong thiết kế kiến trúc hệ thống và xây dựng văn hóa làm việc.

## Danh sách diễn giả & Chủ đề chia sẻ
* **Đinh Trung Kiên & Nguyễn Minh Thọ:** *Thiết kế và co giãn hệ thống rút gọn liên kết (URL Shortener) trên hạ tầng AWS*
* **Đạt Phạm & Cường Nguyễn:** *Những câu chuyện trải nghiệm thực tế và văn hóa làm việc tại các tập đoàn công nghệ đa quốc gia (MNCs)*
* **Solutions Architect (SA):** *Đi sâu vào thế giới Serverless và ứng dụng thực tiễn trên AWS*
* **Danh Hoàng Hiếu Nghị:** *Hành trình dịch chuyển và mở rộng: Từ chương trình First Cloud AI Journey trở thành Đối tác của AWS*
* **Trọng H. Trương (DevOps Engineer @ Endava):** *Bản chất công việc và lộ trình phát triển của một kỹ sư DevOps*

---

## Nội dung kỹ thuật & Kiến thức cốt lõi

### 1. Hiện đại hóa các ứng dụng Legacy cũ
Meetup đã chỉ ra những điểm yếu chí tử của mô hình hệ thống nguyên khối truyền thống:
* **Chu kỳ phát hành kéo dài:** Quy trình cồng kềnh và thiếu tự động hóa làm chậm tiến độ ra mắt tính năng mới, giảm sức cạnh tranh.
* **Chi phí vận hành tăng cao:** Tài nguyên tính toán dư thừa gây lãng phí ngân sách và tốn nhiều công sức để bảo trì.
* **Rủi ro bảo mật tiềm ẩn:** Hệ thống cũ không đáp ứng được các tiêu chuẩn an toàn thông tin hiện đại và dễ bị tấn công dữ liệu.

### 2. Thiết kế Microservices và phương pháp Domain-Driven Design (DDD)
Chuyển đổi kiến trúc sang microservices đòi hỏi kỹ sư phải có tư duy tập trung vào nghiệp vụ (Business-first):
* **Giảm liên kết chéo (Loose Coupling):** Phân tách ứng dụng thành các dịch vụ độc lập giao tiếp qua thông điệp bất đồng bộ (Event-driven), tối ưu hóa luồng Queue, Caching và xử lý Message.
* **Quy trình Event Storming:** Chia nhỏ luồng nghiệp vụ bằng cách xác định các Domain events $\rightarrow$ sắp xếp theo dòng thời gian $\rightarrow$ định danh tác nhân $\rightarrow$ xác lập ranh giới ngữ cảnh (Bounded contexts).
* **Bản đồ ngữ cảnh (Context Mapping):** Thiết lập các mối quan hệ tích hợp rõ ràng giữa các phân vùng nghiệp vụ trong toàn bộ hệ thống.

### 3. Sự tiến hóa của hạ tầng Compute & Serverless
Lựa chọn mô hình tính toán đòi hỏi sự cân nhắc kỹ lưỡng về các tiêu chuẩn đánh đổi:
* **Các cấp độ Compute:** So sánh giữa máy ảo truyền thống (EC2), Container (ECS/Fargate) và Serverless (AWS Lambda).
* **Lợi thế của Serverless:** Loại bỏ gánh nặng quản lý máy chủ vật lý, tự động mở rộng theo lưu lượng thực tế và áp dụng mô hình chi phí tối ưu (chỉ trả tiền khi code chạy).
* **AI hỗ trợ phát triển phần mềm:** Sử dụng Amazon Q Developer để tự động hóa vòng đời phát triển (SDLC), hỗ trợ nâng cấp phiên bản code (Java, .NET) và di trú hệ thống.

### 4. Công việc thực tế của DevOps & Kỹ thuật Dữ liệu
* **Tư duy DevOps đúng nghĩa:** Vai trò cốt lõi của DevOps là xây dựng các đường ống CI/CD ổn định, quản lý hạ tầng dạng mã (IaC), và tự động hóa hệ thống giám sát để ngăn ngừa sự cố xảy ra từ trước, thay vì chỉ làm nhiệm vụ đi "chữa cháy" khi hệ thống sập.
* **Ứng dụng dữ liệu thực tế:** Case study từ Colgate-Palmolive (phân tích dữ liệu IoT trong nhà máy để giảm chi phí sản xuất) và Kamereo (xây dựng dashboard theo dõi GMV, tỷ lệ hoàn thành đơn hàng) giúp minh họa trực quan cách thức áp dụng phân tích dữ liệu vào kinh doanh.

---

## Bài học và Định hướng ứng dụng thực tế

### Về văn hóa và tư duy làm việc
* **Văn hóa Không Đổ Lỗi (No-Blame Post-Mortem):** Khi xảy ra lỗi hệ thống nghiêm trọng, nhóm tập trung phân tích nguyên nhân gốc rễ để vá lỗi và nâng cấp kiến trúc, tuyệt đối không quy trách nhiệm hay đổ lỗi cho cá nhân.
* **Lộ trình nâng cấp năng lực:** Định hướng bản thân chuyển dịch từ vai trò thực thi đơn thuần (*Follower*) sang tư duy kiến trúc toàn cảnh (*System Thinker*).
* **Chuẩn bị tuyển dụng chuẩn quốc tế:** Hiểu rõ các quy trình lọc hồ sơ qua ATS và kỹ năng trả lời phỏng vấn theo mô hình STAR.

### Kế hoạch áp dụng vào dự án
* Tổ chức các buổi thảo luận Event Storming chung giữa team công nghệ và team vận hành để định nghĩa ngôn ngữ chung (Ubiquitous Language).
* Thiết kế lại luồng đặt vé Flash Sale bằng cách đưa hàng đợi SQS vào thay thế các lệnh gọi API đồng bộ để tăng khả năng chịu lỗi.
* Sử dụng trợ lý AI Amazon Q Developer để tăng tốc độ rà soát code và viết tài liệu hệ thống.

---

## Một số hình ảnh khi tham gia sự kiện
![alt text](image.png)
