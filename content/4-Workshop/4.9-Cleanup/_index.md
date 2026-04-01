---
title: "Clean Up"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 4.9. </b> "
---

After finishing the workshop, delete all created resources to avoid unnecessary AWS charges.

> [!CAUTION]
> **Delete resources in the correct order!** Some services depend on others (e.g. you must remove NAT Gateway before its EIP can be released). Follow the steps below carefully.

---

## Estimated Cost if NOT Cleaned Up

| Service | Approx. Monthly Cost |
|---|---|
| NAT Gateway | ~$35 |
| RDS Multi-AZ | ~$28 |
| ECS Fargate (2 tasks) | ~$20 |
| ALB | ~$18 |
| EC2 (2x t3.micro) | ~$15 |
| **Total** | **~$116/month** |

---

## Cleanup Order

### 1. AWS Amplify

**Console**: Amplify → Your app → **Actions** → **Delete app**

### 2. CloudFront Distribution

**Console**: CloudFront → Distributions → Select distribution → **Disable** (wait ~5 min) → **Delete**

### 3. Elastic Beanstalk Environment

**Console**: Elastic Beanstalk → Applications → `Smartinvoice-api` → Environments → `Smartinvoice-api-env` → **Actions** → **Terminate environment**

Wait for environment to terminate fully before proceeding.

### 4. ECS Fargate Service & Cluster

**Console**: ECS → Clusters → `smartinvoice-cluster`

1. Select **Services** → `smartinvoice-ocr-task-service` → **Delete service** (set desired tasks to 0 first)
2. Delete the **Cluster**

### 5. Internal ALB for OCR

**Console**: EC2 → Load Balancers → Select `alb-smartinvoice-ocr` → **Actions** → **Delete**

Delete the target group `tg-ocr-ai` as well.

### 6. RDS Database

**Console**: RDS → Databases → `smartinvoice-db` → **Actions** → **Delete**
- Uncheck "Create final snapshot" for the lab
- Confirm deletion by typing the instance identifier

### 7. ECR Repositories

**Console**: ECR → Repositories → Delete `smartinvoice-backend` and `smartinvoice-ocr`

### 8. NAT Gateway & Elastic IP

Wait for status **Deleted**, then:

**Console**: VPC → Elastic IPs → Select the allocated EIP → **Release Elastic IP address**

### 9. VPC & Networking Resources

**Console**: VPC → Your VPCs → `smartinvoice-vpc` → **Actions** → **Delete VPC**

This will also delete associated subnets, route tables, internet gateway, and security groups.

### 10. SSM Parameters

**Console**: Systems Manager → Parameter Store → Select all `/SmartInvoice/prod/*` parameters → **Delete**

### 11. SQS Queues

**Console**: SQS → Select `smartinvoice-ocr-queue` and `smartinvoice-vietqr-queue` → **Delete**

### 12. Amazon Cognito User Pool

**Console**: Cognito → User Pools → `smart-invoice` pool → **Delete**

### 13. IAM Roles

**Console**: IAM → Roles → Delete:
- `aws-elasticbeanstalk-ec2-role`
- `aws-elasticbeanstalk-service-role`
- `ecsTaskExecutionRole`
- `smartinvoice-ecs-task-role`

### 14. S3 Bucket

**Console**: S3 → Select `smart-invoice-shield-storage` → **Empty** (delete all objects first) → **Delete bucket**

### 15. CloudWatch Log Groups

**Console**: CloudWatch → Log groups → Delete `/ecs/smartinvoice-ocr-task` and any other log groups created.

---

## Verify No Running Resources

After cleanup, verify in the AWS Console:
- EC2 Instances: none running
- RDS: no databases
- ECS: no running tasks
- NAT Gateways: none
- Load Balancers: none (except any pre-existing)

---

> [!TIP]
> Use **AWS Cost Explorer** (Billing → Cost Explorer) to monitor any lingering charges from the lab for the next 24–48 hours.
