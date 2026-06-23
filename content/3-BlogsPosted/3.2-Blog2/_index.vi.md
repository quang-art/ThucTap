---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# SESSION POLICIES TRONG AMAZON EKS POD IDENTITY

# [AWS Tech Share] Chuyển Đổi Người Xem Thành Người Chơi: Xây Dựng Trải Nghiệm Game Tương Tác Cùng GameLift Streams
Hôm nay mình xin chia sẻ về cách AWS giải quyết bài toán "Interactive Streaming" – biến trải nghiệm xem stream game thụ động thành tương tác thời gian thực hai chiều.
Trong phát triển game, việc tổ chức playtest thường tốn nhiều thời gian (tải build, setup, review video). Đồng thời, việc tương tác với cộng đồng người xem cũng gặp rào cản khi người xem chỉ có thể gõ chat thụ động. Để giải quyết bài toán này, AWS đã đưa ra một kiến trúc kết hợp vô cùng mạnh mẽ.
# 3 "TRỤ CỘT" CỦA KIẾN TRÚC GIẢI PHÁP:
Amazon GameLift Streams: Hỗ trợ stream trực tiếp game từ server xuống trình duyệt (WebRTC) với độ trễ cực thấp, đạt chất lượng lên đến 1080p ở 60 FPS mà không cần người chơi phải tải hay cài đặt game.
Amazon IVS (Interactive Video Service): Tiếp nhận luồng phát gameplay và phân phối toàn cầu với độ trễ dưới 1 giây (subsecond latency).
AWS AppSync: Đóng vai trò cầu nối, cung cấp WebSocket APIs để truyền tải tin nhắn, reaction và lệnh điều khiển từ khán giả ngược lại vào game ngay lập tức.
LUỒNG XỬ LÝ (ARCHITECTURE FLOW) HOẠT ĐỘNG NHƯ THẾ NÀO?
Người dùng thao tác trên giao diện React Frontend, được xác thực bảo mật thông qua Amazon Cognito.
Amazon API Gateway và AWS Lambda sẽ chịu trách nhiệm giao tiếp và khởi tạo phiên stream (Stream session).
Ở phía server, GameLift Streams chạy game, đồng thời khởi chạy một tiến trình ngầm gọi là "Broadcast Sidecar".
Ứng dụng Sidecar này sẽ thực hiện bắt hình ảnh/âm thanh, mã hóa video chuẩn H.264 và đẩy luồng stream thẳng lên stage của Amazon IVS với độ trễ dưới 300ms.
ĐIỂM NHẤN KỸ THUẬT: CƠ CHẾ "CONTROL HANDOFF" Điểm ấn tượng nhất trong giải pháp này là cách xử lý việc "nhường quyền điều khiển" (Control Handoff) cho những người tham gia. Hệ thống tận dụng AWS AppSync Event API để điều phối các message kiểm soát trạng thái rất rõ ràng, ví dụ như:
TAKEOVER_REQUEST: Yêu cầu nắm quyền điều khiển từ người chơi hiện tại.
TAKEOVER_APPROVED: Chấp thuận và bắt đầu chia sẻ session thông qua API CreateStreamSessionConnection.
# TỔNG KẾT 
Kiến trúc này không chỉ tối ưu hóa quy trình Playtesting nội bộ của các studio mà còn mở ra tiềm năng khổng lồ cho các chiến dịch truyền thông: nơi người xem stream có thể trực tiếp tham gia vào game (ví dụ: vote hướng đi, spawn quái vật) ngay trên trình duyệt mà không gặp trở ngại về độ trễ.
# Hình ảnh
![alt text](image-1.png)
![alt text](image-2.png)
# link bài viết gốc: 
https://aws.amazon.com/blogs/gametech/creating-interactive-gaming-experiences-with-amazon-gamelift-streams-and-amazon-interactive-video-service/