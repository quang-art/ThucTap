---
title: "Week 9 Worklog"
date: 2026-06-15
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives - VPC Multi-AZ Networking Architecture Design:

* Design and implement a secure, multi-AZ network architecture on AWS to serve as the secure foundation for the High Availability Flash Sale Ticketing System.
* Configure isolation between layers (Public facing, private application backend, secure cache/database store).

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Design the VPC network layout, defining IP CIDR blocks (`10.0.0.0/16`), subnet distributions across AZs, and security zones. | 15/06/2026 | 15/06/2026 | [AWS VPC Docs](https://docs.aws.amazon.com/vpc/) |
| 3 | Create the main Amazon VPC and provision 2 Public Subnets (`10.0.1.0/24`, `10.0.2.0/24`) and 2 Private Subnets (`10.0.11.0/24`, `10.0.12.0/24`) across ap-southeast-1a and ap-southeast-1b. | 16/06/2026 | 16/06/2026 | [AWS Subnet Docs](https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html) |
| 4 | Deploy an Internet Gateway (IGW) and configure 2 redundant NAT Gateways (one in each Public Subnet) for secure internet access for private hosts. | 17/06/2026 | 17/06/2026 | [AWS NAT Gateway Docs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html) |
| 5 | Design and associate custom Route Tables to explicitly map public subnets to the IGW and private subnets to respective NAT Gateways. | 18/06/2026 | 18/06/2026 | [AWS Route Table Docs](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html) |
| 6 | Create and configure Security Groups for Application Load Balancers (ALB), EC2 worker instances, ElastiCache Redis, and RDS database proxy/instance. | 19/06/2026 | 19/06/2026 | [AWS SG Docs](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html) |
| 7 | Provision VPC Flow Logs to CloudWatch Log Group for auditing, and perform end-to-end connection tests to verify correct traffic routing. | 20/06/2026 | 20/06/2026 | [VPC Flow Logs Docs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html) |

### Week 9 Achievements:

* **Designed a Resilient Networking Schema:** Configured multi-AZ architecture (ap-southeast-1a & ap-southeast-1b) ensuring that any single AZ outage will not bring down the ticketing system.
* **Secured Layered Subnets:** 
  * Main VPC: `10.0.0.0/16`
  * Public subnets: `SubnetPublicA` (`10.0.1.0/24`) & `SubnetPublicB` (`10.0.2.0/24`) hosting public ALB and NAT Gateways.
  * Private subnets: `SubnetPrivateA` (`10.0.11.0/24`) & `SubnetPrivateB` (`10.0.12.0/24`) isolating core computing hosts (Elastic Beanstalk Backend/Worker instances) and RDS/Redis subnet groups.
* **Configured High Availability Outbound Access:** Established separate NAT Gateways in each AZ to eliminate cross-AZ traffic charges and ensure high availability for software updates/API calls from the private instances.
* **Enforced Network Security (Least Privilege chains):** 
  * Allowed HTTP/HTTPS traffic to `ticketing-alb-sg` from anywhere.
  * Locked down Beanstalk instances in `ticketing-ec2-worker-sg` to only accept port 80 traffic sourced from the `ticketing-alb-sg`.
  * Restrained `ticketing-redis-sg` to only accept port 6379 from Beanstalk instances via `ticketing-ec2-worker-sg`.
  * Isolated database access: `ticketing-rds-proxy-sg` allows port 5432 only from `ticketing-ec2-worker-sg`, and `ticketing-rds-instance-sg` allows port 5432 only from `ticketing-rds-proxy-sg`.
* **Established Traffic Auditing:** Active VPC Flow Logs logging to Amazon CloudWatch for live threat detection and debugging.
