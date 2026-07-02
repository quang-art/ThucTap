---
title: "Week 10 Worklog"
date: 2026-06-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives - AWS Elastic Beanstalk Deployment & High-Scale Auto Scaling:

* Set up and deploy the core Node.js Web API and background worker application using AWS Elastic Beanstalk.
* Configure Elastic Load Balancing (ALB) and Auto Scaling Policies to dynamically absorb traffic spikes during Flash Sale events.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Write custom configuration scripts (`Procfile`, `.ebextensions/`, `.platform/` hooks) to customize Node.js application process port (`8080`) and reverse proxy settings. | 22/06/2026 | 22/06/2026 | [Elastic Beanstalk Config Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html) |
| 3 | Initialize Elastic Beanstalk applications and deploy BeanstalkBackendEnvironment (`ticketing-Backend-env`) running on Platform `Node.js 20 running on 64bit Amazon Linux 2023` in Private Subnets. | 23/06/2026 | 23/06/2026 | [VPC with Beanstalk Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/vpc.html) |
| 4 | Configure the public-facing ALB with health checks pointing to `/health` and connection draining triggers to evict unhealthy instances smoothly. | 24/06/2026 | 24/06/2026 | [ELB with Beanstalk Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-alb.html) |
| 5 | Setup Auto Scaling Group (ASG) capacity boundaries (MinSize: 2, MaxSize: 4) and configure target tracking rules based on CPU utilization (Upper: 70%, Lower: 30%). | 25/06/2026 | 25/06/2026 | [ASG Beanstalk Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-autoscaling.html) |
| 6 | Provision BeanstalkWorkerEnvironment (`ticketing-Worker-env` running as a WebServer Tier environment) configured with environment variables to poll `BookingQueue` (SQS) and handle SMTP email delivery. | 26/06/2026 | 26/06/2026 | [Beanstalk Worker Tier Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features-managing-env-tiers.html) |
| 7 | Configure Env Properties (RDS database proxy strings, SQS variables, Redis endpoints) and deploy initial app code; inspect logs for errors. | 27/06/2026 | 27/06/2026 | [Beanstalk Env Properties Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-envvars.html) |

### Week 10 Achievements:

* **Deployed Isolated Application Tier:** Successfully launched WebServer Tiers containing our Web API and Worker application in the Private Subnets (`SubnetPrivateA` and `SubnetPrivateB`), inaccessible directly from the Internet.
* **Optimized Load Balancing:** Configured ALB in the Public Subnets to securely route incoming client requests to backend instances, establishing enhanced health check monitoring and custom `/health` endpoint checks.
* **Implemented Auto Scaling for Spiky Traffic:** 
  * Configured ASG instance boundaries: Min: 2, Max: 4.
  * Added scaling trigger policies: Scale-out triggers when average CPU load exceeds 70% and scale-in triggers when CPU drops below 30%.
* **Decoupled Asynchronous Tasks:** Deployed a secondary WebServer Tier environment (`ticketing-Worker-env`) integrated with `BookingQueue` (Amazon SQS) and SMTP configuration (AWS SES) to pull transactional ticket orders from SQS and execute resource-intensive ticket PDF emailing concurrently.
* **Established Safe Deployments:** Configured `Rolling` deployment strategy with a batch size of `50%` inside Beanstalk configuration to ensure zero-downtime updates during live user traffic.
