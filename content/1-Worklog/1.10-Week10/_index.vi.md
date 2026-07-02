---
title: "Worklog Tuần 10"
date: 2026-06-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10 - Triển khai AWS Elastic Beanstalk & Cấu hình Auto Scaling tải cao:

* Khởi tạo và triển khai ứng dụng Web API chạy Node.js cùng với ứng dụng Worker xử lý ngầm (background worker) sử dụng dịch vụ AWS Elastic Beanstalk.
* Cấu hình cân bằng tải Elastic Load Balancing (ALB) và chính sách tự động mở rộng Auto Scaling để phản hồi linh hoạt với lượng truy cập đột biến trong các đợt mở bán vé Flash Sale.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Soạn thảo các tệp tin cấu hình môi trường ứng dụng (`Procfile`, `.ebextensions/`, `.platform/` hooks) nhằm cấu hình cổng chạy ứng dụng (`8080`) và tối ưu Reverse Proxy. | 22/06/2026 | 22/06/2026 | [Elastic Beanstalk Config Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html) |
| 3 | Khởi tạo ứng dụng Elastic Beanstalk và triển khai BeanstalkBackendEnvironment (`ticketing-Backend-env`) chạy trên nền tảng `Node.js 20 running on 64bit Amazon Linux 2023` trong các Private Subnets. | 23/06/2026 | 23/06/2026 | [VPC với Beanstalk Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/vpc.html) |
| 4 | Cấu hình Application Load Balancer (ALB) trong Public Subnet tiếp nhận lưu lượng công khai, thiết lập kiểm tra sức khỏe ứng dụng qua đường dẫn `/health` và kích hoạt Connection Draining. | 24/06/2026 | 24/06/2026 | [ELB với Beanstalk Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-alb.html) |
| 5 | Thiết lập quy mô dung lượng Auto Scaling Group (ASG) với giới hạn MinSize: 2 và MaxSize: 4 máy chủ, xây dựng các chính sách scaling dựa trên CPU (Upper: 70%, Lower: 30%). | 25/06/2026 | 25/06/2026 | [ASG Beanstalk Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-autoscaling.html) |
| 6 | Khởi tạo cấu hình môi trường BeanstalkWorkerEnvironment (`ticketing-Worker-env` vận hành như một WebServer Tier thông thường) kết nối nhận thông số hàng đợi `BookingQueue` (Amazon SQS) và SMTP gửi mail. | 26/06/2026 | 26/06/2026 | [Beanstalk Worker Tier Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features-managing-env-tiers.html) |
| 7 | Cài đặt các biến môi trường (RDS database proxy strings, SQS URL, Redis primary/reader endpoints) và triển khai bản build đầu tiên lên Beanstalk, giám sát log lỗi trực tiếp. | 27/06/2026 | 27/06/2026 | [Beanstalk Env Properties Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-envvars.html) |

### Kết quả đạt được tuần 10:

* **Triển khai thành công phân tầng ứng dụng biệt lập:** Đưa cả hai môi trường Backend API và Worker chạy Node.js vận hành an toàn trong các Private Subnet (`SubnetPrivateA` và `SubnetPrivateB`) cách ly khỏi Internet trực tiếp.
* **Tối ưu hóa khả năng cân bằng tải:** Cấu hình thành công ALB nằm ở Public Subnets tiếp nhận yêu cầu từ client và điều phối đều sang các instance máy chủ backend, thiết lập endpoint kiểm tra sức khỏe tại đường dẫn `/health`.
* **Xây dựng cơ chế Auto Scaling tự động chống sập:**
  * Giới hạn quy mô ASG: Tối thiểu 2 máy chủ, tối đa 4 máy chủ (t3.micro).
  * Thiết lập ngưỡng Scale-out: Tự động scale thêm máy chủ khi CPU trung bình vượt quá 70% và Scale-in thu hồi máy chủ khi CPU trung bình hạ dưới 30%.
* **Phân tách và xử lý tác vụ tải nặng bất đồng bộ:** Vận hành môi trường worker chuyên trách (`ticketing-Worker-env`) liên kết lấy jobs từ hàng đợi `BookingQueue` (Amazon SQS) và cấu hình SMTP (AWS SES) để xử lý bất đồng bộ các tác vụ nặng như tạo file PDF vé và gửi mail xác nhận cho người dùng.
* **Áp dụng Deploy an toàn:** Thiết lập cơ chế cập nhật phiên bản theo dạng `Rolling` với quy mô Batch Size đạt `50%` trên Elastic Beanstalk cấu hình nhằm đảm bảo không có downtime của hệ thống khi cập nhật mã nguồn mới.


