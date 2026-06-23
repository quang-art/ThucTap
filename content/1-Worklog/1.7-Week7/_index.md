---
title: "Week 7 Worklog"
date: 2026-06-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives - Reliability & Performance:

* Build highly available infrastructure with disaster recovery capabilities.
* Deploy containerized applications and establish CI/CD pipelines.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference |
|---|---|---|---|---|
| 2 | Deploy system backup plan with AWS Backup | 01/06/2026 | 01/06/2026 | https://000013.awsstudygroup.com/vi/ |
| 3 | Link VPCs with VPC Peering | 02/06/2026 | 02/06/2026 | https://000019.awsstudygroup.com/vi/ |
| 4 | Manage connections centrally with AWS Transit Gateway | 03/06/2026 | 03/06/2026 | https://000020.awsstudygroup.com/vi/ |
| 5 | Deploy applications with Docker | 04/06/2026 | 04/06/2026 | https://000015.awsstudygroup.com/vi/ |
| 6 | Deploy applications to Amazon ECS | 05/06/2026 | 05/06/2026 | https://000016.awsstudygroup.com/vi/ |
| 7 | Deploy applications with AWS CodePipeline | 06/06/2026 | 07/06/2026 | https://000017.awsstudygroup.com/vi/ |

**Implementation period:** 01/06/2026 - 07/06/2026

### Week 7 Achievements:

**About AWS Backup:**
- Create backup plans for EC2, RDS, EBS volumes.
- Configure backup frequency, retention policy, encryption.
- Recover data from backups during emergency situations.
- Monitor backup jobs and verify backup integrity.

**About VPC Peering:**
- Create VPC peering connections between VPCs in same or different regions.
- Configure route tables to route traffic through peering connections.
- Manage peering connection states and troubleshoot connectivity issues.

**About AWS Transit Gateway:**
- Connect multiple VPCs and on-premises networks through Transit Gateway.
- Create route tables on Transit Gateway to control traffic flow.
- Manage attachments for VPCs and VPNs.

**About Docker:**
- Create Dockerfiles for containerizing applications.
- Build and test Docker images locally.
- Understand Docker registries and image repositories.

**About Amazon ECS:**
- Create ECS clusters and services.
- Deploy containers to ECS using Fargate or EC2 launch types.
- Configure load balancing and auto-scaling for container services.
- Monitor container performance and logs.

**About AWS CodePipeline:**
- Create CI/CD pipelines for automatic application deployment.
- Connect source (CodeCommit), build (CodeBuild), deploy (CodeDeploy) stages.
- Add approval steps before production deployment.
- Monitor pipeline execution and troubleshoot failures.
