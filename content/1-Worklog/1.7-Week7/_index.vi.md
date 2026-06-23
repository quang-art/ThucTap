---
title: "Worklog Tuần 7"
date: 2026-06-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7 - Độ tin cậy & Hiệu năng (Reliability & Performance):

* Xây dựng hạ tầng có tính sẵn sàng cao và phục hồi sau sự cố.
* Triển khai ứng dụng container và CI/CD pipelines.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|---|---|---|---|---|
| 2 | Triển khai kế hoạch sao lưu hệ thống với AWS Backup | 01/06/2026 | 01/06/2026 | https://000013.awsstudygroup.com/vi/ |
| 3 | Liên kết VPCs với VPC Peering | 02/06/2026 | 02/06/2026 | https://000019.awsstudygroup.com/vi/ |
| 4 | Quản lý kết nối tập trung với AWS Transit Gateway | 03/06/2026 | 03/06/2026 | https://000020.awsstudygroup.com/vi/ |
| 5 | Triển khai ứng dụng với Docker | 04/06/2026 | 04/06/2026 | https://000015.awsstudygroup.com/vi/ |
| 6 | Triển khai ứng dụng lên Amazon ECS | 05/06/2026 | 05/06/2026 | https://000016.awsstudygroup.com/vi/ |
| 7 | Triển khai ứng dụng với AWS CodePipeline | 06/06/2026 | 07/06/2026 | https://000017.awsstudygroup.com/vi/ |

**Giai đoạn thực hiện:** 01/06/2026 - 07/06/2026

### Kết quả đạt được tuần 7:

**Về AWS Backup:**
- Tạo backup plans cho EC2, RDS, EBS volumes.
- Cấu hình backup frequency, retention policy, encryption.
- Phục hồi dữ liệu từ backups trong tình huống khẩn cấp.
- Giám sát backup jobs và xác minh backup integrity.

**Về VPC Peering:**
- Tạo VPC peering connections giữa các VPCs trong cùng hoặc khác region.
- Cấu hình route tables để lưu lượng traffic qua peering connection.
- Quản lý peering connection states và troubleshoot connectivity issues.

**Về AWS Transit Gateway:**
- Kết nối môi trường VPCs và on-premises networks thông qua Transit Gateway.
- Tạo route tables trên Transit Gateway để kiểm soát traffic.
- Quản lý attachments cho VPCs và VPNs.

**Về Docker:**
- Tạo Dockerfiles để container hóa ứng dụng.
- Build và test Docker images trên máy tính local.
- Hiểu về Docker registries và image repositories.

**Về Amazon ECS:**
- Tạo ECS clusters và services.
- Deploy containers lên ECS using Fargate hoặc EC2 launch types.
- Cấu hình load balancing và auto-scaling cho container services.
- Giám sát container performance và logs.

**Về AWS CodePipeline:**
- Tạo CI/CD pipelines để tự động deploy ứng dụng.
- Kết nối source (CodeCommit), build (CodeBuild), deploy (CodeDeploy) stages.
- Thêm approval steps trước khi deploy vào production.
- Giám sát pipeline execution và troubleshoot failures.


