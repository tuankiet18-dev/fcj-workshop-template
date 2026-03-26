---
title: "Week 5 Worklog"
date: 2026-01-01
weight: 5
chapter: false
---

### Week 5 Objectives:

- Configure and evaluate AWS Auto Scaling with Dynamic Scaling Policies.
- Design and implement S3 storage strategies using Access Points and Lifecycle Policies.
- Execute VM Import/Export operations and automated backup configurations.
- Design database schema and backend security (AWS Cognito) for the SmartInvoice Shield project.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Start Date | Completion Date | Reference Material                |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | --------------------------------- |
| 2   | AWS Lab:<br>- Configured an Auto Scaling Group (ASG) with Dynamic Scaling Policies based on CPU utilization.<br>- Performed Stress Tests using Apache Bench (ab) to trigger scaling events.<br>- Managed CloudFront distribution and handled cache invalidation.<br><br>Project Architecture:<br>- Designed an S3 strategy using Access Points for simplified permission management.<br>- Planned S3 Lifecycle Policies to move aged invoice data (&gt;3 months) to S3 Standard-IA for cost savings. | 02/02/2026 | 02/02/2026      |                                   |
| 3   | AWS Lab:<br>• Attempted VM Import/Export (VMware to AMI).<br>• Lesson Learned: Encountered and analyzed a CLIENT_ERROR: Unsupported kernel version issue due to OS incompatibility.<br>• Configured AWS Backup Plans for automated resource protection.Tools:<br>• Practiced using AWS CloudShell for executing CLI commands without local configuration                                                                                                                                             | 03/02/2026 | 03/02/2026      |                                   |
| 4   | FCJ Project - Database Design:<br>• Analyzed database schema requirements for the SmartInvoice Shield project.<br>• Configured DbContext, wrote Entity Framework Core migration scripts, and created tables in PostgreSQL.                                                                                                                                                                                                                                                                           | 04/02/2026 | 04/02/2026      |                                   |
| 5   | FCJ AWS Labs - Compute & Storage:<br>• Practiced provisioning and configuring Amazon EC2 instances and setting up Security Groups.<br>• Created and configured Amazon S3 buckets, wrote access control policies to prepare the storage infrastructure.                                                                                                                                                                                                                                               | 05/02/2026 | 05/02/2026      | https://000057.awsstudygroup.com/ |
| 6   | FCJ Project - Backend Security:<br>• Researched AWS Cognito API documentation and integration libraries for .NET 9.<br>• Set up middleware in Program.cs to receive and validate JWT tokens from AWS Cognito.                                                                                                                                                                                                                                                                                        | 06/02/2026 | 06/02/2026      |                                   |

### Week 5 Achievements:

- Successfully implemented ASG with dynamic scaling and stress tested using Apache Bench.
- Optimized S3 storage costs using Lifecycle Policies and simplified access with Access Points.
- Gained hands-on experience with VM migration tools and AWS CloudShell.
- Completed DB schema migration and integrated JWT validation with AWS Cognito.
