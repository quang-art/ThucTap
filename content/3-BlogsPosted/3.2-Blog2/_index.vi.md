---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
# [AWS Tech Share] Biến Người Xem Thành Người Chơi: Xây Dựng Trải Nghiệm Game Tương Tác Với Amazon GameLift Streams & Amazon IVS
Hôm nay, tôi xin chia sẻ về cách AWS giải quyết bài toán "Interactive Streaming" (Luồng phát tương tác)—chuyển đổi trải nghiệm xem stream game thụ động thành các tương tác hai chiều thời gian thực với độ trễ cực thấp.

Trong lĩnh vực phát triển game, quy trình playtesting (chơi thử nghiệm) truyền thống thường tốn nhiều thời gian do phải tải bản build, cài đặt môi trường và kiểm tra các video ghi hình. Ngoài ra, việc giao tiếp với cộng đồng người xem trên các nền tảng stream cũng bị hạn chế khi khán giả chỉ có thể tương tác thụ động qua khung chat chữ. Để giải quyết các thách thức này, AWS đã đưa ra một mô hình kiến trúc kết hợp vô cùng hiệu quả.

# 3 Trụ Cột Chính Của Kiến Trúc Giải Pháp
1. **Amazon GameLift Streams:** Hỗ trợ phát trực tiếp game từ máy chủ đám mây xuống trình duyệt của người dùng thông qua giao thức WebRTC. Giải pháp này mang lại luồng video chất lượng cao lên đến 1080p ở tốc độ 60 FPS với độ trễ cực thấp mà người chơi không cần phải tải hay cài đặt trò chơi.
2. **Amazon IVS (Interactive Video Service):** Tiếp nhận luồng phát gameplay từ server và phân phối rộng rãi trên quy mô toàn cầu với độ trễ dưới 1 giây (subsecond latency).
3. **AWS AppSync:** Đóng vai trò làm cổng kết nối WebSocket thời gian thực, truyền tải tin nhắn, biểu cảm và các lệnh điều khiển từ người xem trực tiếp quay ngược trở lại game engine ngay lập tức.

# Luồng Xử Lý Của Hệ Thống
- Người dùng thao tác trên giao diện web được xây dựng bằng React Frontend, quá trình xác thực bảo mật được quản lý thông qua Amazon Cognito.
- Amazon API Gateway phối hợp với AWS Lambda chịu trách nhiệm điều phối và khởi tạo các phiên stream (Stream Sessions).
- Tại máy chủ game, Amazon GameLift Streams vận hành trò chơi đồng thời chạy một dịch vụ phụ trợ chạy ngầm gọi là "Broadcast Sidecar".
- Ứng dụng Sidecar này sẽ thu hình ảnh và âm thanh của game trực tiếp từ bộ nhớ, mã hóa video theo chuẩn H.264 và đẩy thẳng luồng stream lên stage của Amazon IVS với độ trễ chưa đầy 300ms.

# Điểm Nhấn Kỹ Thuật: Cơ Chế "Control Handoff" (Chuyển Giao Quyền Điều Khiển)
Điểm độc đáo nhất trong giải pháp này là cách hệ thống xử lý việc bàn giao quyền điều khiển (Control Handoff) cho người xem. Hệ thống tận dụng AWS AppSync Event API để đồng bộ các thông điệp điều khiển trạng thái một cách chặt chẽ:
- **`TAKEOVER_REQUEST`:** Được gửi khi một người xem yêu cầu giành quyền điều khiển từ người chơi hiện tại.
- **`TAKEOVER_APPROVED`:** Được máy chủ phê duyệt để bắt đầu chia sẻ phiên chơi thông qua API `CreateStreamSessionConnection`.

# Tổng Kết
Kiến trúc này không chỉ tối ưu hóa quy trình thử nghiệm game nội bộ của các studio mà còn mở ra những cơ hội tiếp thị đột phá. Giờ đây, khán giả xem livestream có thể tham gia trực tiếp vào diễn biến game (như bình chọn hướng đi hoặc triệu hồi quái vật) ngay trên trình duyệt web của họ với độ trễ gần như bằng không.

# Hình ảnh
![alt text](image-1.png)
![alt text](image-2.png)

# link bài viết gốc: 
https://aws.amazon.com/blogs/gametech/creating-interactive-gaming-experiences-with-amazon-gamelift-streams-and-amazon-interactive-video-service/