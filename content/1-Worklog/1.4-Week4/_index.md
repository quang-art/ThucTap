---
title: "Week 4 Worklog"
date: 2026-05-11
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Capability to migrate resources from on-premises to AWS cloud.
* Master the migration process ensuring high availability and zero data loss.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference |
|---|---|---|---|---|
| 2 | AWS VM Import/Export overview - Concepts, supported formats, key considerations | 11/05/2026 | 11/05/2026 | https://000014.awsstudygroup.com/vi/ |
| 3 | Practice VM migration: preparation, export VM from on-premises, import to EC2 | 12/05/2026 | 13/05/2026 | https://000014.awsstudygroup.com/vi/ |
| 4 | Introduction to AWS Database Migration Service (DMS) - Concepts, architecture, benefits | 14/05/2026 | 14/05/2026 | https://000043.awsstudygroup.com/vi/ |
| 5 | Learn AWS Schema Conversion Tool (SCT) - Schema conversion, data migration, compatibility checks | 15/05/2026 | 15/05/2026 | https://000043.awsstudygroup.com/vi/ |
| 6 | Practice database migration: configure DMS task, monitor progress, verify data | 16/05/2026 | 17/05/2026 | https://000043.awsstudygroup.com/vi/ |

**Implementation period:** 11/05/2026 - 17/05/2026

### Week 4 Achievements:

**About AWS VM Import/Export:**
- Understand the concepts and mechanisms of AWS VM Import/Export in infrastructure migration.
- Master supported formats (OVF, VHD, VMDK) and prerequisites for import/export operations.
- Proficient in VM preparation on on-premises including validation, sensitive data removal, and export.
- Successfully practiced exporting VM from VMware/Hyper-V and importing to EC2.
- Understand potential challenges (drivers, licensing, performance) and mitigation strategies.
- Know how to monitor and manage import/export tasks via AWS Console.

**About AWS Database Migration Service (DMS):**
- Fully understand DMS architecture: source database, target database, replication instance, tasks.
- Master migration types: Full Load, Change Data Capture (CDC), Full Load + CDC.
- Proficient in creating DMS endpoints for various source databases (On-premises SQL Server, MySQL, PostgreSQL, Oracle).
- Know how to configure DMS replication instance with appropriate parameters (instance class, allocated storage, network settings).
- Successfully created and executed DMS migration tasks with real-time monitoring.

**About AWS Schema Conversion Tool (SCT):**
- Fully understand SCT capabilities in automatically converting database schemas between different database engines.
- Proficient in schema conversion from SQL Server → RDS PostgreSQL/MySQL.
- Know how to handle conversion errors and tune database schema for performance optimization.
- Successfully practiced creating assessment reports to identify incompatible objects before migration.

**About Migration Process Management:**
- Understand best practices in database migration: planning, testing, validation, cutover strategy.
- Master DMS task monitoring: view data flow statistics, replicated objects, latency metrics.
- Know how to validate data after migration: compare row counts, check data consistency, validate business logic.
- Proficient in handling downtime: planned cutover, zero-downtime migration strategies.
- Have skills in rollback procedures and emergency handling during migration processes.

**Overall Experience Summary:**
- Achieved ability to plan and execute migration projects for both infrastructure (VM) and databases.
- Sufficient skills to handle complex scenarios in real-world migration implementations.
- Ready to participate in infrastructure and database migration projects from on-premises to AWS.

