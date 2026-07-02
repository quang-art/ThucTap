---
title: "Worklog Tuần 9"
date: 2026-06-15
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9 - Thiết kế Kiến trúc Mạng VPC Multi-AZ:

* Thiết kế và triển khai mô hình mạng bảo mật cao Multi-AZ trên AWS nhằm làm nền tảng hạ tầng mạng an toàn cho Hệ thống đặt vé Flash Sale High Availability.
* Cấu hình phân tách độc lập giữa các lớp mạng (Public subnet tiếp nhận traffic, Private subnet chạy API/Worker, Private DB/Cache Subnet bảo mật).

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Thiết kế sơ đồ phân tách mạng VPC, hoạch định các dải CIDR block (`10.0.0.0/16`) cho subnet và phân vùng bảo mật. | 15/06/2026 | 15/06/2026 | [AWS VPC Docs](https://docs.aws.amazon.com/vpc/) |
| 3 | Khởi tạo Amazon VPC chính và thiết lập 2 Public Subnet (`10.0.1.0/24`, `10.0.2.0/24`), 2 Private Subnet (`10.0.11.0/24`, `10.0.12.0/24`) trên hai Availability Zone khác nhau (ap-southeast-1a và ap-southeast-1b). | 16/06/2026 | 16/06/2026 | [AWS Subnet Docs](https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html) |
| 4 | Cấu hình Internet Gateway (IGW) và triển khai 2 NAT Gateway độc lập (mỗi NAT Gateway nằm ở một Public Subnet của mỗi AZ) nhằm đảm bảo dự phòng. | 17/06/2026 | 17/06/2026 | [AWS NAT Gateway Docs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html) |
| 5 | Thiết lập Route Table: định tuyến Public Subnet trỏ ra IGW; định tuyến các Private Subnet trỏ ra NAT Gateway tương ứng trong cùng AZ để tối ưu đường truyền. | 18/06/2026 | 18/06/2026 | [AWS Route Table Docs](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html) |
| 6 | Xây dựng các nhóm bảo mật (Security Groups) riêng biệt cho Application Load Balancer (ALB), EC2 Worker instances, ElastiCache Redis và RDS Proxy/Instance. | 19/06/2026 | 19/06/2026 | [AWS SG Docs](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html) |
| 7 | Cấu hình VPC Flow Logs đẩy log về CloudWatch Log Group để phục vụ giám sát luồng mạng, đồng thời kiểm tra kết nối mạng nội bộ giữa các subnets. | 20/06/2026 | 20/06/2026 | [VPC Flow Logs Docs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html) |

### Kết quả đạt được tuần 9:

* **Thiết kế thành công hệ thống mạng Multi-AZ có tính sẵn sàng cao:** Triển khai hạ tầng trên 2 AZ (ap-southeast-1a và ap-southeast-1b) giúp loại bỏ điểm lỗi đơn (SPOF) ở cấp độ trung tâm dữ liệu.
* **Phân lớp mạng bảo mật chặt chẽ:**
  * Dải mạng VPC chính: `10.0.0.0/16`
  * Public Subnets: `SubnetPublicA` (`10.0.1.0/24`) & `SubnetPublicB` (`10.0.2.0/24`) chỉ chứa ALB công khai và NAT Gateways.
  * Private Subnets: `SubnetPrivateA` (`10.0.11.0/24`) & `SubnetPrivateB` (`10.0.12.0/24`) cô lập hoàn toàn máy chủ ứng dụng (Elastic Beanstalk Backend/Worker) và các subnet groups cho database RDS / cache Redis.
* **Đảm bảo dự phòng NAT Gateway:** Khởi tạo NAT Gateway riêng lẻ ở mỗi AZ giúp tránh mất kết nối Internet hướng đi ra từ Private Subnet nếu một AZ gặp sự cố, đồng thời giảm thiểu chi phí truyền tải dữ liệu chéo vùng (cross-AZ data charges).
* **Áp dụng Nguyên lý Đặc quyền Tối thiểu (Least Privilege) cho Security Groups:**
  * `ticketing-alb-sg`: Mở port 80/443 ra toàn bộ Internet.
  * `ticketing-ec2-worker-sg`: Chỉ cho phép nhận traffic ở cổng 80 từ `ticketing-alb-sg`.
  * `ticketing-redis-sg`: Chỉ chấp nhận kết nối inbound cổng 6379 xuất phát từ `ticketing-ec2-worker-sg`.
  * Cô lập lớp database: `ticketing-rds-proxy-sg` chỉ nhận cổng 5432 từ `ticketing-ec2-worker-sg`, và `ticketing-rds-instance-sg` chỉ nhận cổng 5432 từ `ticketing-rds-proxy-sg`.
* **Kích hoạt Giám sát Luồng mạng:** Thiết lập VPC Flow Logs gửi dữ liệu trực tiếp về Amazon CloudWatch, sẵn sàng cho việc giám sát an ninh mạng và phát hiện bất thường.


