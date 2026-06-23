---
title: "Worklog Tuần 8"
date: 2026-06-08
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8 - Hiệu năng & Tối ưu chi phí (Performance & Cost Optimization):

* Tối ưu hóa hiệu năng ứng dụng và quản lý chi phí.
* Triển khai advanced solutions cho data management và analytics.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|---|---|---|---|---|
| 2 | Tự động hóa triển khai ứng dụng với AWS CodePipeline | 08/06/2026 | 08/06/2026 | https://000023.awsstudygroup.com/vi/ |
| 3 | Lưu trữ dữ liệu không giới hạn với File Storage Gateway | 09/06/2026 | 09/06/2026 | https://000024.awsstudygroup.com/vi/ |
| 4 | Triển khai kho lưu trữ chung cho Windows sử dụng FSx | 10/06/2026 | 10/06/2026 | https://000025.awsstudygroup.com/vi/ |
| 5 | Xây dựng Data Lake trên AWS | 11/06/2026 | 12/06/2026 | https://000035.awsstudygroup.com/vi/ |
| 6 | Kiến trúc nâng cao với Amazon DynamoDB | 12/06/2026 | 12/06/2026 | https://000039.awsstudygroup.com/vi/ |
| 7 | Tối ưu chi phí với Savings Plans, Reserved Instances | 13/06/2026 | 13/06/2026 | https://000042.awsstudygroup.com/vi/ |
| 8 | Lựa chọn kích thước máy chủ với EC2 Optimization | 14/06/2026 | 14/06/2026 | https://000032.awsstudygroup.com/vi/ |
| 9 | Trực quan hóa chi phí và phân tích với Athena & Glue | 14/06/2026 | 14/06/2026 | https://000040.awsstudygroup.com/vi/ |

**Giai đoạn thực hiện:** 08/06/2026 - 14/06/2026

### Kết quả đạt được tuần 8:

**Về CodePipeline Automation:**
- Tạo multi-stage pipelines với automated testing và deployment.
- Tích hợp với GitHub, GitLab, hoặc on-premises repositories.
- Implement blue-green deployments và canary releases.
- Giám sát deployment metrics và rollback capabilities.

**Về File Storage Gateway:**
- Thiết lập File Storage Gateway để lưu trữ files trên S3 với local caching.
- Kết nối NFS/SMB clients đến gateway.
- Cấu hình lifecycle policies để lưu trữ dữ liệu tối ưu.

**Về Amazon FSx:**
- Tạo managed file systems cho Windows (FSx for Windows File Server).
- Kết nối với Active Directory và configure access controls.
- Giám sát file server performance và manage backups.

**Về Data Lake:**
- Thiết kế Data Lake architecture trên S3 (raw, processed, curated layers).
- Tạo data ingestion pipelines với AWS Glue.
- Implement data cataloging và governance.
- Query data với Athena và Redshift.

**Về Amazon DynamoDB:**
- Tạo bảng DynamoDB với optimal partition keys và sort keys.
- Thiết kế indexes (GSI, LSI) để query hiệu quả.
- Cấu hình auto-scaling capacity cho traffic spikes.
- Implement global tables để multi-region replication.

**Về Cost Optimization:**
- Phân tích compute usage và lựa chọn giữa On-Demand, Reserved Instances, Savings Plans.
- Implement Savings Plans để giảm chi phí Compute.
- Mua Reserved Instances cho RDS và durable workloads.

**Về EC2 Resource Optimization:**
- Sử dụng AWS Compute Optimizer để nhận recommendations.
- Upsize/downsize instances dựa trên utilization metrics.
- Thay thế underutilized instances với more cost-effective types.

**Về Chi phí Analytics:**
- Tạo Cost and Usage reports và lưu trữ trên S3.
- Sử dụng Athena để query cost data.
- Tạo Quicksight dashboards để visualize spending trends.
- Implement tags-based cost allocation và chargeback.


