---
title: "Dọn dẹp Tài nguyên"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 4.9. </b> "
---

Sau khi hoàn thành workshop, hãy xóa toàn bộ tài nguyên đã tạo để tránh phát sinh chi phí AWS không cần thiết.

> [!CAUTION]
> **Xóa tài nguyên theo đúng thứ tự!** Một số dịch vụ phụ thuộc vào nhau (ví dụ: phải xóa NAT Gateway trước khi giải phóng EIP). Hãy làm theo các bước dưới đây cẩn thận.

---

## Chi phí Ước tính nếu KHÔNG Dọn dẹp

| Dịch vụ | Chi phí xấp xỉ/tháng |
|---|---|
| NAT Gateway | ~$35 |
| RDS Multi-AZ | ~$28 |
| ECS Fargate (2 tasks) | ~$20 |
| ALB | ~$18 |
| EC2 (2x t3.micro) | ~$15 |
| **Tổng cộng** | **~$116/tháng** |

---

## Thứ tự Dọn dẹp

### 1. AWS Amplify

**Console**: Amplify → Ứng dụng của bạn → **Actions** → **Delete app**

### 2. CloudFront Distribution

**Console**: CloudFront → Distributions → Chọn distribution → **Disable** (chờ ~5 phút) → **Delete**

### 3. Elastic Beanstalk Environment

**Console**: Elastic Beanstalk → Applications → `Smartinvoice-api` → Environments → `Smartinvoice-api-env` → **Actions** → **Terminate environment**

Chờ môi trường terminate hoàn toàn trước khi tiếp tục.

### 4. ECS Fargate Service & Cluster

**Console**: ECS → Clusters → `smartinvoice-cluster`

1. Chọn **Services** → `smartinvoice-ocr-task-service` → **Delete service** (đặt desired tasks = 0 trước)
2. Xóa **Cluster**

### 5. Internal ALB cho OCR

**Console**: EC2 → Load Balancers → Chọn `alb-smartinvoice-ocr` → **Actions** → **Delete**

Xóa cả target group `tg-ocr-ai`.

### 6. RDS Database

**Console**: RDS → Databases → `smartinvoice-db` → **Actions** → **Delete**
- Bỏ chọn "Create final snapshot" cho bài lab
- Xác nhận xóa bằng cách gõ tên instance

### 7. ECR Repositories

**Console**: ECR → Repositories → Xóa **smartinvoice-backend** và **smartinvoice-ocr**

### 8. NAT Gateway & Elastic IP

**Console**: VPC → NAT Gateways → **smartinvoice-nat-gw** → **Delete**

Chờ status **Deleted**, sau đó:

**Console**: VPC → Elastic IPs → Chọn EIP đã cấp → **Release Elastic IP address**

### 9. VPC & Networking

**Console**: VPC → Your VPCs → **smartinvoice-vpc** → **Actions** → **Delete VPC**

Thao tác này cũng sẽ xóa các subnets, route tables, internet gateway, và security groups liên quan.

### 10. SSM Parameters

**Console**: Systems Manager → Parameter Store → Chọn tất cả tham số `/SmartInvoice/prod/*` → **Delete**

### 11. SQS Queues

**Console**: SQS → Chọn `smartinvoice-ocr-queue` và `smartinvoice-vietqr-queue` → **Delete**

### 12. Amazon Cognito User Pool

**Console**: Cognito → User Pools → pool `smart-invoice` → **Delete**

### 13. IAM Roles

**Console**: IAM → Roles → Xóa:
- `aws-elasticbeanstalk-ec2-role`
- `aws-elasticbeanstalk-service-role`
- `ecsTaskExecutionRole`
- `smartinvoice-ecs-task-role`

### 14. S3 Bucket

**Console**: S3 → Chọn `smart-invoice-shield-storage` → **Empty** (xóa tất cả objects trước) → **Delete bucket**

### 15. CloudWatch Log Groups

**Console**: CloudWatch → Log groups → Xóa `/ecs/smartinvoice-ocr-task` và các log groups khác đã tạo.

---

## Xác minh Không còn Tài nguyên Chạy

Sau khi dọn dẹp, kiểm tra lại trên AWS Console:
- EC2 Instances: không có
- RDS: không có database
- ECS: không có tasks đang chạy
- NAT Gateways: không có
- Load Balancers: không có (trừ các ALB có từ trước)

---

> [!TIP]
> Dùng **AWS Cost Explorer** (Billing → Cost Explorer) để theo dõi chi phí còn sót lại từ bài lab trong vòng 24–48 giờ tiếp theo.
