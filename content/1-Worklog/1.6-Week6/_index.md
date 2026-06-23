---
title: "Week 6 Worklog"
date: 2026-05-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives - Security:

* Strengthen infrastructure and application security.
* Manage access control and data encryption.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference |
|---|---|---|---|---|
| 2 | Setup Single Sign-On for Organization with Amazon SSO | 25/05/2026 | 25/05/2026 | https://000012.awsstudygroup.com/vi/ |
| 3 | Limit User permissions with IAM Permission Boundary | 26/05/2026 | 26/05/2026 | https://000030.awsstudygroup.com/vi/ |
| 4 | Limit role switching by Conditions | 27/05/2026 | 27/05/2026 | https://000044.awsstudygroup.com/vi/ |
| 5 | Check security standards with AWS Security Hub | 28/05/2026 | 29/05/2026 | https://000018.awsstudygroup.com/vi/ |
| 6 | Secure applications and APIs with AWS WAF | 29/05/2026 | 29/05/2026 | https://000026.awsstudygroup.com/vi/ |
| 7 | Manage encryption keys with AWS KMS | 30/05/2026 | 31/05/2026 | https://000033.awsstudygroup.com/vi/ |

**Implementation period:** 25/05/2026 - 31/05/2026

### Week 6 Achievements:

**About Amazon SSO:**
- Setup AWS Single Sign-On for multi-account environments.
- Integrate with Active Directory or Okta for user authentication.
- Manage access to AWS accounts through SSO portal.

**About IAM Permission Boundaries:**
- Create permission boundaries to limit max permissions for IAM users/roles.
- Combine permission boundaries with role-based policies.
- Prevent privilege escalation using permission boundaries.

**About Conditional Role Assumption:**
- Setup AssumeRole policies with conditions (IP address, MFA, time-based).
- Restrict role assumption based on source IP and MFA requirements.
- Enhance security for cross-account role access.

**About AWS Security Hub:**
- Integrate Security Hub across AWS accounts and regions.
- Review findings from AWS Config, GuardDuty, Macie, IAM Access Analyzer.
- Create custom insights for security posture analysis.

**About AWS WAF:**
- Configure WAF rules to protect against SQL injection, XSS, DDoS attacks.
- Apply WAF to CloudFront, ALB, API Gateway.
- Monitor WAF logs and adjust rules based on traffic patterns.

**About AWS KMS:**
- Create and manage Customer Master Keys (CMK) for encryption.
- Encrypt EBS volumes, S3 objects, RDS databases using KMS keys.
- Manage key rotation and audit key usage.
- Understand key policies and cross-account key access.
