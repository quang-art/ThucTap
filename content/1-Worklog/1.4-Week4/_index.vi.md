---
title: "Worklog Tuần 4"
date: 2026-05-11
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Khả năng di chuyển (migration) các tài nguyên từ on-premises vào AWS cloud.
* Nắm vững quá trình di chuyển đậm bảo tính khẳ dụng cao và không mất dữ liệu.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|---|---|---|---|---|
| 2 | Thế giới của AWS VM Import/Export - Khái niệm, các định dạng cũ, những lưu ý quan trọng | 11/05/2026 | 11/05/2026 | https://000014.awsstudygroup.com/vi/ |
| 3 | Thực hành di chuyển VM: chuẩn bị, export VM từ on-premises, import vào EC2 | 12/05/2026 | 13/05/2026 | https://000014.awsstudygroup.com/vi/ |
| 4 | Giới thiệu AWS Database Migration Service (DMS) - Khái niệm, kiến trúc, ưu điểm | 14/05/2026 | 14/05/2026 | https://000043.awsstudygroup.com/vi/ |
| 5 | Tìm hiểu AWS Schema Conversion Tool (SCT) - Chuyển đổi schema, di chuyển dữ liệu, kiểm tra tương thích | 15/05/2026 | 15/05/2026 | https://000043.awsstudygroup.com/vi/ |
| 6 | Thực hành di chuyển CSDL: cấu hình DMS task, giám sát tiến độ, xác minh dữ liệu | 16/05/2026 | 17/05/2026 | https://000043.awsstudygroup.com/vi/ |

**Giai đoạn thực hiện:** 11/05/2026 - 17/05/2026

### Kết quả đạt được tuần 4:

**Về AWS VM Import/Export:**
- Hiểu rõ khái niệm và cơ chế hoạt động của AWS VM Import/Export trong quá trình di chuyển hạ tầng.
- Nắm được các định dạng hỗ trợ (OVF, VHD, VMDK) và điều kiện tiên quyết để import/export VM.
- Thành thạo quy trình chuẩn bị VM trên on-premises bao gồm kiểm tra, xóa dữ liệu nhạy cảm, và export.
- Đã thực hành export VM từ VMware/Hyper-V và import vào AWS EC2 thành công.
- Hiểu rõ các vấn đề có thể gặp phải (driver, license, performance) và cách xử lý.
- Biết cách giám sát và quản lý các import/export task thông qua AWS Console.

**Về AWS Database Migration Service (DMS):**
- Hiểu đầy đủ về kiến trúc DMS: source database, target database, replication instance, tasks.
- Nắm vững các loại migration: Full Load, Change Data Capture (CDC), Full Load + CDC.
- Thành thạo trong việc tạo DMS endpoints cho các database source (On-premises SQL Server, MySQL, PostgreSQL, Oracle).
- Biết cách cấu hình DMS replication instance với các thông số phù hợp (instance class, allocated storage, network settings).
- Đã tạo và chạy DMS migration task thành công với monitoring thời gian thực.

**Về AWS Schema Conversion Tool (SCT):**
- Hiểu rõ tính năng SCT trong việc tự động chuyển đổi database schema giữa các database engine khác nhau.
- Thành thạo trong việc chuyển đổi schema từ SQL Server → RDS PostgreSQL/MySQL.
- Biết cách xử lý các lỗi conversion và tuning database schema để tối ưu hóa hiệu suất.
- Đã thực hành tạo assessment report để xác định các object không tương thích trước khi migration.

**Về quản lý quá trình Migration:**
- Hiểu rõ best practices trong di chuyển database: planning, testing, validation, cutover strategy.
- Nắm vững cách giám sát DMS task: xem thống kê dòng dữ liệu, replicated objects, latency.
- Biết cách xác minh dữ liệu sau migration: compare row counts, check data consistency, validate business logic.
- Thành thạo trong handling downtime: planned cutover, zero-downtime migration strategies.
- Có kỹ năng rollback nếu cần thiết và các tình huống emergency trong quá trình migration.

**Tổng kết kinh nghiệm:**
- Đạt được khả năng lên kế hoạch và thực thi migration project cho cả infrastructure (VM) và database.
- Có đủ kỹ năng để xử lý các tình huống phức tạp trong migration thực tế.
- Sẵn sàng để tham gia các project di chuyển hạ tầng và database từ on-premises lên AWS.



