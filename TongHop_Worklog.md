TUẦN 1 (20/4 - 26/4)
- Tạo mới tài khoản AWS Free Tier và kiểm tra quyền truy cập
- Tìm hiểu dịch vụ AWS cơ bản: Compute, Storage, Networking, Database và chi phí
- Thực hành trên AWS Console và cài đặt, cấu hình AWS CLI
- Quản lý quyền truy cập với AWS IAM: tạo user, group, policy và kiểm soát quyền
- Thiết lập hạ tầng mạng cơ bản với Amazon VPC và kiểm tra kết nối

TUẦN 2 (27/4 - 03/5)
- Bắt đầu và triển khai ứng dụng trên Amazon EC2 - Khởi tạo instance, cấu hình environment
- Cấp quyền cho ứng dụng truy cập dịch vụ AWS thông qua IAM Role - Tạo role, attach policy
- Sử dụng Cloud IDE trên trình duyệt với AWS Cloud9 - Tạo environment, viết và test code
- Hosting static website với Amazon S3 - Upload file, cấu hình bucket, setup CDN
- Tạo cơ sở dữ liệu trên Amazon RDS - Khởi tạo DB instance, backup, restore
- Tối ưu chi phí tính toán với Amazon Lightsail - So sánh với EC2, tạo Lightsail instance

TUẦN 3 (04/5 - 10/5)
- Tự động mở rộng qui mô ứng dụng với Amazon EC2 Autoscaling - Tạo Auto Scaling Group, Load Balancer
- Tạo bảng theo dõi hệ thống với Amazon CloudWatch - Setup metrics, alarms, logs
- Thiết lập hệ thống DNS hybrid tích hợp giữa môi trường Local và Amazon VPC với Amazon Route53 - Setup hosted zone, DNS records
- Sử dụng AWS CLI trên các Amazon EC2 (Windows/Ubuntu) - Cài đặt CLI, chạy lệnh quản lý resource
- Highly Available Web Application Workshop - Lab thực hành, triển khai ứng dụng high availability

TUẦN 4 (11/5 - 17/5)
- Thế giới của AWS VM Import/Export - Khái niệm, các định dạng cũ, những lưu ý quan trọng
- Thực hành di chuyển VM: chuẩn bị, export VM từ on-premises, import vào EC2
- Giới thiệu AWS Database Migration Service (DMS) - Khái niệm, kiến trúc, ưu điểm
- Tìm hiểu AWS Schema Conversion Tool (SCT) - Chuyển đổi schema, di chuyển dữ liệu, kiểm tra tương thích
- Thực hành di chuyển CSDL: cấu hình DMS task, giám sát tiến độ, xác minh dữ liệu

TUẦN 5 (18/5 - 24/5)
- Bật tắt máy chủ tự động với AWS Lambda và gửi thông báo Slack
- Tạo bảng theo dõi hệ thống với CloudWatch và Grafana
- Quản lý tài nguyên theo nhóm bằng Tag và Resource Groups
- Quản lý truy cập EC2 bằng Tag thông qua IAM
- Quản lý dịch vụ và tự động hóa tác vụ với AWS Systems Manager
- Sử dụng AWS Systems Manager - Session Manager
- Khởi tạo Hạ tầng dưới dạng Code với AWS CloudFormation

TUẦN 6 (25/5 - 31/5)
- Thiết lập Single Sign-On cho Organization với Amazon SSO
- Giới hạn quyền của User với IAM Permission Boundary
- Giới hạn chuyển Role theo Condition
- Kiểm tra đánh giá tiêu chuẩn bảo mật với AWS Security Hub
- Bảo mật Ứng dụng và API với AWS WAF
- Quản lý khóa với AWS KMS

TUẦN 7 (01/6 - 07/6)
- Triển khai kế hoạch sao lưu hệ thống với AWS Backup
- Liên kết VPCs với VPC Peering
- Quản lý kết nối tập trung với AWS Transit Gateway
- Triển khai ứng dụng với Docker
- Triển khai ứng dụng lên Amazon ECS
- Triển khai ứng dụng với AWS CodePipeline

TUẦN 8 (08/6 - 14/6)
- Tự động hóa triển khai ứng dụng với AWS CodePipeline
- Lưu trữ dữ liệu không giới hạn với File Storage Gateway
- Triển khai kho lưu trữ chung cho Windows sử dụng FSx
- Xây dựng Data Lake trên AWS
- Kiến trúc nâng cao với Amazon DynamoDB
- Tối ưu chi phí với Savings Plans, Reserved Instances
- Lựa chọn kích thước máy chủ với EC2 Optimization
- Trực quan hóa chi phí và phân tích với Athena & Glue

TUẦN 9 (15/6 - 21/6)
- Thiết kế sơ đồ phân tách mạng VPC, hoạch định các dải CIDR block (10.0.0.0/16) cho subnet và phân vùng bảo mật
- Khởi tạo Amazon VPC chính và thiết lập 2 Public Subnet, 2 Private Subnet trên hai Availability Zone khác nhau (ap-southeast-1a và ap-southeast-1b)
- Cấu hình Internet Gateway (IGW) và triển khai 2 NAT Gateway độc lập nhằm đảm bảo dự phòng
- Thiết lập Route Table: định tuyến Public Subnet trỏ ra IGW; định tuyến các Private Subnet trỏ ra NAT Gateway tương ứng trong cùng AZ
- Xây dựng các nhóm bảo mật (Security Groups) riêng biệt cho ALB, EC2 Worker instances, ElastiCache Redis và RDS Proxy/Instance
- Cấu hình VPC Flow Logs đẩy log về CloudWatch Log Group để phục vụ giám sát luồng mạng

TUẦN 10 (22/6 - 28/6)
- Soạn thảo các tệp tin cấu hình môi trường ứng dụng  để cấu hình cổng chạy ứng dụng và tối ưu Reverse Proxy
- Khởi tạo ứng dụng Elastic Beanstalk và triển khai BeanstalkBackendEnvironment  trong các Private Subnets
- Cấu hình ALB trong Public Subnet tiếp nhận lưu lượng công khai, thiết lập kiểm tra sức khỏe  và kích hoạt Connection Draining
- Thiết lập quy mô dung lượng Auto Scaling Group  và xây dựng chính sách scaling dựa trên CPU 
- Khởi tạo cấu hình môi trường BeanstalkWorkerEnvironment  kết nối nhận thông số hàng đợi  (Amazon SQS) và SMTP
- Cài đặt các biến môi trường  và triển khai bản build đầu tiên lên Beanstalk

TUẦN 11 (29/6 - 05/7)
- Thiết kế cấu trúc phân phối lưu trữ Cache, xác định các cấu trúc Cache keys, chính sách giải phóng bộ nhớ  và khóa phân tán 
- Tạo nhóm nhân bản Amazon ElastiCache for Redis  chạy Engine 7.0, loại node cache.t3.micro với tính năng Multi-AZ
- Cấu hình nhóm mạng con cho Cache  liên kết với Private Subnets và cấu hình Security Group
- Tích hợp thư viện Redis client vào backend API, trỏ các kết nối qua biến môi trường
- Viết kịch bản Lua Script chạy trực tiếp trên Redis để xử lý trừ tồn kho vé nguyên tử (atomic decrement) và rate limiter sliding-window
- Kết nối hoàn chỉnh API từ Beanstalk sang Redis Cluster và chạy thử nghiệm kịch bản failover tự động

TUẦN 12 (06/7 - 12/7)
- Triển khai và hoàn thiện báo cáo thực tập
- Tổng hợp và đánh giá kết quả đạt được trong suốt quá trình thực tập
