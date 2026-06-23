---
title: "Worklog Tuần 5"
date: 2026-05-18
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---


### Mục tiêu tuần 5 - Vận hành (Operations):

* Tạo các automation workflow cho việc quản lý và làm quen với AWS Lambda.
* Nắm vững cách quản lý tài nguyên, monitoring và automation.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|---|---|---|---|---|
| 2 | Bật tắt máy chủ tự động với AWS Lambda và gửi thông báo Slack | 18/05/2026 | 18/05/2026 | https://000022.awsstudygroup.com/vi/ |
| 3 | Tạo bảng theo dõi hệ thống với CloudWatch và Grafana | 19/05/2026 | 19/05/2026 | https://000029.awsstudygroup.com/vi/ |
| 4 | Quản lý tài nguyên theo nhóm bằng Tag và Resource Groups | 20/05/2026 | 20/05/2026 | https://000027.awsstudygroup.com/vi/ |
| 5 | Quản lý truy cập EC2 bằng Tag thông qua IAM | 21/05/2026 | 22/05/2026 | https://000028.awsstudygroup.com/vi/ |
| 6 | Quản lý dịch vụ và tự động hóa tác vụ với AWS Systems Manager | 23/05/2026 | 23/05/2026 | https://000031.awsstudygroup.com/vi/ |
| 7 | Sử dụng AWS Systems Manager - Session Manager | 24/05/2026 | 24/05/2026 | https://000058.awsstudygroup.com/vi/ |
| 8 | Khởi tạo Hạ tầng dưới dạng Code với AWS CloudFormation | 24/05/2026 | 24/05/2026 | https://000037.awsstudygroup.com/vi/ |

**Giai đoạn thực hiện:** 18/05/2026 - 24/05/2026

### Kết quả đạt được tuần 5:

**Về AWS Lambda và Automation:**
- Tạo và deploy Lambda function để tự động bật/tắt EC2 instance theo lịch biểu.
- Tích hợp Lambda với SNS để gửi thông báo Slack khi có sự kiện xảy ra.
- Hiểu rõ về IAM roles và permissions cho Lambda function.
- Xử lý các event triggers từ CloudWatch Events, SNS, API Gateway.

**Về CloudWatch và Grafana:**
- Cấu hình CloudWatch metrics và dashboards để giám sát các EC2 instances.
- Tạo CloudWatch alarms để thông báo khi có anomalies.
- Tích hợp Grafana với CloudWatch để trực quan hóa dữ liệu.
- Phân tích logs trợ với CloudWatch Logs Insights.

**Về Resource Tagging:**
- Tạo chính sách tagging đầu tiên (project, environment, owner, cost-center).
- Sử dụng Resource Groups để nhóm và quản lý tài nguyên dựa trên tags.
- Áp dụng resource-based IAM policies cho EC2 dựa trên tags.

**Về IAM Tag-based Access Control:**
- Cấp quyền truy cập EC2 dựa trên principal tags và resource tags.
- Tạo IAM policies với condition keys như aws:PrincipalTag và aws:ResourceTag.
- Quản lý team access đến các EC2 instances theo môi trường (dev, staging, prod).

**Về AWS Systems Manager:**
- Sử dụng Parameter Store để lưu trữ cấu hình ứng dụng.
- Tạo và chạy automation documents để thực hiện các tác vụ vận hành.
- Sử dụng Maintenance Windows để lên lịch bảo trì hệ thống.

**Về Session Manager:**
- Cấu hình Session Manager để kết nối remote đến EC2 instances mà không cần SSH keys.
- Giám sát và ghi lại session activities cho audit trails.

**Về AWS CloudFormation:**
- Viết Infrastructure as Code (IaC) templates bằng JSON/YAML.
- Tạo stacks để tự động deployment các AWS resources.
- Quản lý stack updates và deletion mà không ảnh hưởng đến production.
- Sử dụng nested stacks để tái sử dụng templates.


