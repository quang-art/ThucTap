---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---
# Tìm Hiểu Giải Pháp Multi-Build Trên Amazon GameLift Servers
## Giới thiệu
Trong quá trình vận hành và phát triển các tựa game online, việc thử nghiệm và cập nhật liên tục các phiên bản máy chủ trò chơi là công việc diễn ra thường xuyên. Tuy nhiên, việc triển khai từng phiên bản mới lên toàn bộ hạ tầng máy chủ có thể tiêu tốn nhiều thời gian, làm gián đoạn luồng công việc của đội ngũ kiểm thử (QA) và chơi thử (playtest).

Nhằm khắc phục trở ngại này, AWS đã giới thiệu giải pháp Multi-Build trên Amazon GameLift Servers. Tính năng này cho phép nhà phát triển lưu trữ và chạy song song nhiều phiên bản máy chủ game trên cùng một fleet duy nhất, giúp đẩy nhanh tiến độ phát triển và tối ưu quy trình thử nghiệm.

# Amazon GameLift Là Gì?
Amazon GameLift là dịch vụ lưu trữ máy chủ game chuyên dụng được quản lý hoàn toàn bởi AWS. Dịch vụ này hỗ trợ các nhà phát triển game triển khai, vận hành và tự động mở rộng hệ thống máy chủ trên phạm vi toàn cầu, đảm bảo độ trễ thấp và tính ổn định cao cho hàng triệu game thủ.

# Khó Khăn Trong Quy Trình Cập Nhật Truyền Thống
Thông thường, mỗi khi có một bản cập nhật máy chủ game mới, quy trình thủ công bắt buộc nhà phát triển phải:
1. Thực hiện biên dịch lại mã nguồn máy chủ.
2. Khởi tạo và triển khai lại toàn bộ hạ tầng fleet mới.
3. Chờ cấu hình mạng và kiểm tra khả năng kết nối.
4. Chuyển đổi thủ công giữa các fleet khác nhau để phục vụ thử nghiệm chéo.
Quy trình này mất rất nhiều thời gian, đặc biệt là trong giai đoạn thử nghiệm Alpha và Beta khi các bản cập nhật được phát hành liên tục hàng ngày.

# Giải Pháp Multi-Build
Giải pháp Multi-Build cho phép nhiều bản build máy chủ trò chơi cùng tồn tại và hoạt động trên cùng một fleet Amazon GameLift. Thay vì phải tái khởi động lại toàn bộ hệ thống hạ tầng, quy trình được rút gọn như sau:
1. **Tải bản build lên Amazon S3:** Đóng gói và upload phiên bản mới lên S3 bucket.
2. **Đồng bộ hóa tự động:** Hệ thống chạy ngầm tự động đồng bộ hóa các tệp tin này xuống các máy chủ vật lý của GameLift.
3. **Chỉ định phiên bản:** Khi yêu cầu tạo Game Session (Phiên chơi game), chỉ cần truyền tham số `BuildVersion` mong muốn.
4. **Khởi chạy thông minh:** Máy chủ GameLift sẽ tự động kích hoạt tệp chạy của phiên bản tương ứng.
Nhờ cơ chế này, việc chuyển đổi giữa các phiên bản game diễn ra vô cùng nhanh chóng, linh hoạt và tối ưu tài nguyên.

# Kiến Trúc Hoạt Động
Mô hình giải pháp này vận hành thông qua sự kết hợp của hai container chính chạy song song trên mỗi máy chủ:

## 1. Game Server Container
- Chịu trách nhiệm thực thi các phiên bản game server.
- Tiếp nhận các yêu cầu khởi tạo game session từ người chơi.
- Khởi chạy chính xác phiên bản game dựa theo giá trị `BuildVersion` được yêu cầu.

## 2. S3 Sync Container
- Hoạt động liên tục ở chế độ chạy ngầm (background daemon).
- Theo dõi các thay đổi và cập nhật trên Amazon S3 bucket.
- Tải các bản build mới về thư mục chia sẻ cục bộ.
- Tự động dọn dẹp các bản build cũ không còn sử dụng để giải phóng dung lượng đĩa.
- Đảm bảo dữ liệu được tải xuống hoàn tất và toàn vẹn trước khi game server gọi thực thi.

Cả hai container này cùng gắn kết (mount) chung một thư mục lưu trữ để đảm bảo việc đọc ghi và thực thi các bản build được diễn ra trơn tru.

# Các Dịch Vụ AWS Được Tích Hợp
Giải pháp Multi-Build là sự kết hợp chặt chẽ của nhiều dịch vụ AWS:
- **Amazon GameLift Servers:** Đóng vai trò làm hạ tầng quản lý phiên chơi và điều phối máy chủ.
- **Amazon S3:** Nơi lưu trữ tập trung các bản build của game server.
- **Amazon ECR:** Quản lý mã nguồn và hình ảnh container cho các dịch vụ.
- **AWS IAM:** Cung cấp cơ chế phân quyền an toàn giữa các dịch vụ.
- **AWS CodeBuild:** Tự động hóa quy trình đóng gói và xây dựng container.
- **AWS CloudFormation:** Định nghĩa toàn bộ hạ tầng dưới dạng mã nguồn (IaC).
- **Amazon CloudWatch Logs:** Ghi nhận nhật ký hoạt động phục vụ giám sát và gỡ lỗi.

# Lợi Ích Của Giải Pháp Multi-Build
- **Đẩy nhanh tiến độ phát triển:** Giúp các nhóm kỹ thuật thử nghiệm song song nhiều tính năng hoặc bản sửa lỗi mà không cần tốn thời gian tạo fleet mới.
- **Tiết kiệm thời gian tối đa:** Quá trình cập nhật bản build mới chỉ diễn ra trong vài phút thay vì phải chờ đợi hàng giờ để triển khai hạ tầng.
- **Hỗ trợ đắc lực cho Alpha/Beta:** Cho phép chạy nhiều phiên bản game khác nhau để phục vụ các nhóm game thủ thử nghiệm riêng biệt.
- **Vận hành đơn giản:** Quản lý tập trung các bản build trên S3 và tự động hóa toàn bộ quy trình đồng bộ hóa xuống máy chủ.

# Kết Luận
Giải pháp Multi-Build trên Amazon GameLift Servers là công cụ vô cùng mạnh mẽ cho các nhà phát triển game muốn rút ngắn chu kỳ thử nghiệm và phát hành. Bằng cách gom nhiều bản build chạy chung trên một fleet duy nhất, AWS giúp giảm đáng kể chi phí hạ tầng và tối ưu hóa quy trình phát triển game. Đây chắc chắn là giải pháp rất đáng để các studio game ứng dụng trong giai đoạn thử nghiệm Alpha, Beta hoặc khi cần lặp lại tính năng nhanh chóng.

# Hình ảnh
![alt text](image-1.png)
![alt text](image-2.png)

# Link tài liệu tham khảo:
https://aws.amazon.com/vi/blogs/gametech/rapid-game-server-iteration-on-amazon-gamelift-servers/