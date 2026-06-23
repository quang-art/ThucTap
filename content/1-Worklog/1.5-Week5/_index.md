---
title: "Week 5 Worklog"
date: 2026-05-18
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---


### Week 5 Objectives - Operations:

* Create automation workflows for management and learn AWS Lambda.
* Master resource management, monitoring, and automation techniques.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference |
|---|---|---|---|---|
| 2 | Auto start/stop servers with AWS Lambda and send Slack notifications | 18/05/2026 | 18/05/2026 | https://000022.awsstudygroup.com/vi/ |
| 3 | Create system monitoring dashboard with CloudWatch and Grafana | 19/05/2026 | 19/05/2026 | https://000029.awsstudygroup.com/vi/ |
| 4 | Manage resources by groups using Tags and Resource Groups | 20/05/2026 | 20/05/2026 | https://000027.awsstudygroup.com/vi/ |
| 5 | Manage EC2 access using Tags through IAM | 21/05/2026 | 22/05/2026 | https://000028.awsstudygroup.com/vi/ |
| 6 | Manage services and automate tasks using AWS Systems Manager | 23/05/2026 | 23/05/2026 | https://000031.awsstudygroup.com/vi/ |
| 7 | Work with AWS Systems Manager - Session Manager | 24/05/2026 | 24/05/2026 | https://000058.awsstudygroup.com/vi/ |
| 8 | Initialize Infrastructure as Code with AWS CloudFormation | 24/05/2026 | 24/05/2026 | https://000037.awsstudygroup.com/vi/ |

**Implementation period:** 18/05/2026 - 24/05/2026

### Week 5 Achievements:

**About AWS Lambda and Automation:**
- Deploy Lambda functions to automatically start/stop EC2 instances on schedule.
- Integrate Lambda with SNS to send Slack notifications for events.
- Understand IAM roles and permissions for Lambda functions.
- Handle event triggers from CloudWatch Events, SNS, API Gateway.

**About CloudWatch and Grafana:**
- Configure CloudWatch metrics and dashboards for monitoring EC2 instances.
- Create CloudWatch alarms for anomaly detection and notifications.
- Integrate Grafana with CloudWatch for data visualization.
- Analyze logs using CloudWatch Logs Insights.

**About Resource Tagging:**
- Create tagging policies (project, environment, owner, cost-center).
- Use Resource Groups to organize and manage resources by tags.
- Apply resource-based IAM policies for EC2 based on tags.

**About IAM Tag-based Access Control:**
- Grant EC2 access based on principal tags and resource tags.
- Create IAM policies with condition keys like aws:PrincipalTag and aws:ResourceTag.
- Manage team access to EC2 instances by environment (dev, staging, prod).

**About AWS Systems Manager:**
- Use Parameter Store for application configuration storage.
- Create and execute automation documents for operational tasks.
- Use Maintenance Windows for scheduling system maintenance.

**About Session Manager:**
- Configure Session Manager for remote EC2 access without SSH keys.
- Monitor and audit session activities for compliance.

**About AWS CloudFormation:**
- Write Infrastructure as Code (IaC) templates in JSON/YAML.
- Create stacks for automatic AWS resource deployment.
- Manage stack updates and deletion without affecting production.
- Use nested stacks for template reuse.
