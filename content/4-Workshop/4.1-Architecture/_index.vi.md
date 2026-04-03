---
title: "Tổng quan Kiến trúc"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

## Sơ Đồ Kiến Trúc Hệ Thống

![alt text](image.png)

## Bảng Subnet

| Subnet                    | CIDR          | AZ  | Loại    | Chứa                             |
| ------------------------- | ------------- | --- | ------- | -------------------------------- |
| `smartinvoice-public-1a`  | `10.0.1.0/24` | 1a  | Public  | ALB Public, NAT GW               |
| `smartinvoice-public-1b`  | `10.0.2.0/24` | 1b  | Public  | ALB Public                       |
| `smartinvoice-private-1a` | `10.0.3.0/24` | 1a  | Private | EC2, RDS, ECS Fargate, Cloud Map |
| `smartinvoice-private-1b` | `10.0.4.0/24` | 1b  | Private | EC2 Backend, RDS Standby         |

## Tổng quan các Bước Triển khai (~4 giờ)

| Bước | Nội dung                                 | ⏱️  |
| ---- | ---------------------------------------- | --- |
| 1    | Chọn Region & Chuẩn bị                   | 5'  |
| 2    | Tạo VPC & Subnets                        | 15' |
| 3    | Tạo Internet Gateway                     | 5'  |
| 4    | Tạo NAT Gateway                          | 10' |
| 5    | Tạo Route Tables                         | 10' |
| 6    | Tạo Security Groups                      | 15' |
| 7    | Tạo IAM Roles                            | 15' |
| 8    | Tạo S3 Bucket                            | 5'  |
| 9    | Tạo Amazon Cognito                       | 15' |
| 10   | Tạo SQS Queues                           | 10' |
| 11   | Tạo SSM Parameter Store                  | 15' |
| 12   | Tạo RDS PostgreSQL                       | 15' |
| 13   | Tạo ECR & Push Docker Images             | 20' |
| 14   | Triển khai OCR (ECS Fargate + Cloud Map) | 20' |
| 15   | Triển khai Backend (Elastic Beanstalk)   | 20' |
| 16   | Cấu hình HTTPS (CloudFront)              | 15' |
| 17   | Triển khai Frontend (Amplify)            | 10' |
| 18   | Cấu hình Tên miền tùy chỉnh (Route 53)   | 10' |
| 19   | CI/CD (GitHub Actions)                   | 10' |
| 20   | CloudWatch Monitoring                    | 15' |
| 21   | Kiểm tra End-to-End                      | 15' |

## Chi Phí Ước Tính (Monthly)

| Dịch vụ        | Cấu hình dự kiến     | Chi phí (USD/tháng) |
| -------------- | -------------------- | ------------------- |
| EC2 (EBS)      | 2x t3.micro          | ~$15                |
| RDS PostgreSQL | db.t3.micro Multi-AZ | ~$28                |
| ECS Fargate    | 2 tasks (0.25 vCPU)  | ~$20                |
| NAT Gateway    | 1 zone + data        | ~$35                |
| ALB (Backend)  | 1 ALB                | ~$18                |
| **TỔNG CỘNG**  |                      | **~$116**           |
