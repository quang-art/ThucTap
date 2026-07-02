---
title: "Worklog Tuần 11"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11 - Triển khai Amazon ElastiCache for Redis Cluster:

* Triển khai cấu trúc bộ nhớ đệm phân tán Amazon ElastiCache for Redis Replication Group Multi-AZ.
* Cấu hình đồng bộ hóa phiên người dùng (session state), thiết lập giới hạn tần suất yêu cầu (rate limiting), và bộ nhớ đệm hàng tồn kho (ticket inventory) nhằm tối ưu tốc độ và ngăn chặn nghẽn cơ sở dữ liệu khi hệ thống quá tải.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Thiết kế cấu trúc phân phối lưu trữ Cache, xác định các cấu trúc Cache keys, chính sách giải phóng bộ nhớ (eviction policy: volatile-lru), và chiến thuật khóa phân tán (Distributed Locks). | 29/06/2026 | 29/06/2026 | [Redis Cache Strategies](https://aws.amazon.com/caching/caching-best-practices/) |
| 3 | Tạo nhóm nhân bản Amazon ElastiCache for Redis (`ticketing-redis` chạy phiên bản Engine `7.0`, loại node `cache.t3.micro`) với tính năng Multi-AZ tự động failover. | 30/06/2026 | 30/06/2026 | [ElastiCache Multi-AZ Docs](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/AutoFailover.html) |
| 4 | Cấu hình nhóm mạng con cho Cache (`ticketing-redis-subnet-group`) liên kết với các Private Subnets. Áp dụng nhóm bảo mật `ticketing-redis-sg` chỉ cho phép cổng 6379 đi vào từ môi trường Beanstalk. | 01/07/2026 | 01/07/2026 | [ElastiCache Network Docs](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/VPCs.html) |
| 5 | Tích hợp thư viện Redis client vào backend API, trỏ các kết nối qua biến môi trường `REDIS_HOST`, `REDIS_PRIMARY_HOST` và `REDIS_READER_HOST` cùng cấu hình tối ưu connection pool. | 02/07/2026 | 02/07/2026 | [Redis Client Best Practices](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/BestPractices.Clients.html) |
| 6 | Viết kịch bản Lua Script chạy trực tiếp trên Redis để xử lý trừ số lượng vé khả dụng một cách nguyên tử (atomic decrement), đồng thời xây dựng bộ rate limiter dạng sliding-window. | 03/07/2026 | 03/07/2026 | [Redis Lua Scripting Docs](https://redis.io/docs/manual/programmability/eval-intro/) |
| 7 | Kết nối hoàn chỉnh API từ Elastic Beanstalk sang Redis Cluster, chạy thử nghiệm kịch bản giả lập ngắt kết nối (failover) từ console AWS và kiểm tra thời gian phục hồi tự động. | 04/07/2026 | 04/07/2026 | [ElastiCache Failover Test](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/AutoFailover.html#AutoFailover.Test) |

### Kết quả đạt được tuần 11:

* **Triển khai thành công cụm lưu trữ dự phòng Multi-AZ:** Cấu hình thành công ElastiCache Redis Replication Group trên hai phân vùng độc lập (`SubnetPrivateA` vùng AZ-A làm Primary, `SubnetPrivateB` vùng AZ-B làm Replica) với cấu hình 1 shard và 1 replica (`NumNodeGroups: 1`, `ReplicasPerNodeGroup: 1`).
* **Bảo mật tối đa mạng lưới Cache:** Cô lập thành công Redis Cluster trong dải Private Cache Subnets (`ticketing-redis-subnet-group`). Cổng 6379 bị chặn hoàn toàn từ ngoài Internet thông qua `ticketing-redis-sg` và chỉ chấp nhận kết nối nội bộ từ máy chủ Beanstalk.
* **Xử lý triệt để tranh chấp dữ liệu (Race Conditions) khi mua vé:**
  * Áp dụng kịch bản Lua Script thực thi nguyên tử (atomic) việc kiểm tra kho vé và trừ số lượng trực tiếp trong bộ nhớ đệm Redis.
  * Đảm bảo rằng dù hàng chục nghìn luồng request đổ bộ cùng lúc, hệ thống vẫn phản hồi chính xác số vé còn lại và tuyệt đối không xảy ra tình trạng bán quá số lượng (double-booking).
* **Tích hợp giới hạn tần suất yêu cầu (Rate Limiting):** Sử dụng thuật toán Sliding-Window lưu trữ trên Redis giúp nhận dạng và ngăn chặn các IP spam/crawling có tần suất gọi API vượt quá 60 req/phút.
* **Khôi phục kết nối tự động khi gặp sự cố:** Giả lập sự cố sập node Primary trên AWS, node Replica tự động được thăng cấp (promote) thành Primary trong 8 giây; bể kết nối của ứng dụng tự động chuyển hướng thông qua Primary Endpoint Address (`RedisReplicationGroup.PrimaryEndPoint.Address`) mà không gây gián đoạn dịch vụ.


