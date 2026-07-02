---
title: "Week 11 Worklog"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives - Amazon ElastiCache for Redis Cluster:

* Deploy and integrate Amazon ElastiCache for Redis Replication Group with Multi-AZ replication.
* Implement session state, rate limiting, and ticket inventory caching to prevent race conditions and DB bottlenecks under extreme high load.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Design the caching architecture, defining cache keys, volatile-lru eviction policy, and distributed locking strategy. | 29/06/2026 | 29/06/2026 | [Redis Cache Strategies](https://aws.amazon.com/caching/caching-best-practices/) |
| 3 | Provision an Amazon ElastiCache for Redis Replication Group (`ticketing-redis` with Engine version `7.0`, node type `cache.t3.micro`) with Multi-AZ and Auto-Failover enabled. | 30/06/2026 | 30/06/2026 | [ElastiCache Multi-AZ Docs](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/AutoFailover.html) |
| 4 | Define custom Cache Subnet Group `ticketing-redis-subnet-group` and link it to private subnets. Attach `ticketing-redis-sg` to restrict port 6379 ingress to Beanstalk instances. | 01/07/2026 | 01/07/2026 | [ElastiCache Network Docs](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/VPCs.html) |
| 5 | Integrate Redis client into backend code, targeting environment variables `REDIS_HOST`, `REDIS_PRIMARY_HOST` and `REDIS_READER_HOST` with connection pool parameters. | 02/07/2026 | 02/07/2026 | [Redis Client Best Practices](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/BestPractices.Clients.html) |
| 6 | Program Lua scripts on Redis for atomic ticket inventory decrementing, and deploy a sliding-window rate limiter for public API endpoints. | 03/07/2026 | 03/07/2026 | [Redis Lua Scripting Docs](https://redis.io/docs/manual/programmability/eval-intro/) |
| 7 | Connect the Beanstalk API to the Redis cluster, trigger a manual failover in AWS Console, and verify that connection recovery happens automatically. | 04/07/2026 | 04/07/2026 | [ElastiCache Failover Test](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/AutoFailover.html#AutoFailover.Test) |

### Week 11 Achievements:

* **Deployed Redundant Cache Cluster:** Established an Amazon ElastiCache for Redis Replication Group spanning two Availability Zones (Primary in `SubnetPrivateA` AZ-A, Replica in `SubnetPrivateB` AZ-B) using a 1-shard, 1-replica configuration (`NumNodeGroups: 1`, `ReplicasPerNodeGroup: 1`).
* **Isolated Caching Network:** Confined ElastiCache within a Private Cache Subnet Group (`ticketing-redis-subnet-group`). Port 6379 is locked down in `ticketing-redis-sg` to block all public internet access.
* **Eliminated Ticket Overselling (Race Conditions):** 
  * Wrote highly optimized Redis Lua scripts to execute "check-and-decrement" operations for remaining tickets atomically.
  * This guarantees that even when thousands of users order concurrently, ticket sales are exact and double-booking is physically impossible.
* **Implemented High-Speed Rate Limiting:** Built a sliding-window rate limiter on Redis to track IP addresses. It blocks scrapers and ticketing bots making more than 60 requests per minute.
* **Achieved Rapid Failover Recovery:** Executed a manual promotion simulation. The application connection pool recovered session states instantly using the primary endpoint address (`RedisReplicationGroup.PrimaryEndPoint.Address`), completing node migration in under 10 seconds.
