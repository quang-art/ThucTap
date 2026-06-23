---
title: "Worklog Tuần 6"
date: 2026-05-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6 - Bảo mật (Security):

* Tăng cường bảo mật hạ tầng và ứng dụng.
* Quản lý truy cập và mã hóa dữ liệu.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|---|---|---|---|---|
| 2 | Thiết lập Single Sign-On cho Organization với Amazon SSO | 25/05/2026 | 25/05/2026 | https://000012.awsstudygroup.com/vi/ |
| 3 | Giới hạn quyền của User với IAM Permission Boundary | 26/05/2026 | 26/05/2026 | https://000030.awsstudygroup.com/vi/ |
| 4 | Giới hạn chuyển Role theo Condition | 27/05/2026 | 27/05/2026 | https://000044.awsstudygroup.com/vi/ |
| 5 | Kiểm tra đánh giá tiêu chuẩn bảo mật với AWS Security Hub | 28/05/2026 | 29/05/2026 | https://000018.awsstudygroup.com/vi/ |
| 6 | Bảo mật Ứng dụng và API với AWS WAF | 29/05/2026 | 29/05/2026 | https://000026.awsstudygroup.com/vi/ |
| 7 | Quản lý khóa với AWS KMS | 30/05/2026 | 31/05/2026 | https://000033.awsstudygroup.com/vi/ |

**Giai đoạn thực hiện:** 25/05/2026 - 31/05/2026

### Kết quả đạt được tuần 6:

**Về Amazon SSO:**
- Thiết lập AWS Single Sign-On cho môi trường multi-account.
- Tích hợp với Active Directory hoặc Okta để xác thực users.
- Quản lý quyền truy cập các AWS accounts thông qua SSO portal.

**Về IAM Permission Boundaries:**
- Tạo permission boundaries để giới hạn max permissions cho IAM users/roles.
- Phối hợp permission boundaries với role-based policies.
- Tránh privilege escalation bằng cách sử dụng permission boundaries.

**Về Conditional Role Assumption:**
- Thiết lập AssumeRole policies với conditions (IP address, MFA, time-based).
- Giới hạn role assumption dựa trên source IP và MFA requirement.
- Tăng bảo mật cho cross-account role access.

**Về AWS Security Hub:**
- Kết nối Security Hub với các AWS accounts và regions.
- Kiểm tra findings dựa trên AWS Config, GuardDuty, Macie, AWS IAM Access Analyzer.
- Tạo custom insights để phân tích security posture.

**Về AWS WAF:**
- Cấu hình WAF rules để bảo vệ khỏi SQL injection, XSS, DDoS attacks.
- Áp dụng WAF về CloudFront, ALB, API Gateway.
- Giám sát WAF logs và điều chỉnh rules dựa trên traffic patterns.

**Về AWS KMS:**
- Tạo và quản lý Customer Master Keys (CMK) cho mã hóa.
- Mã hóa EBS volumes, S3 objects, RDS databases sử dụng KMS keys.
- Quản lý key rotation và auditing key usage.
- Hiểu về key policies và cross-account key access.


