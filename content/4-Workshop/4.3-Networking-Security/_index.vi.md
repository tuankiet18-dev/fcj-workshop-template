---
title: "Mạng & Bảo mật"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

Phần này bao gồm các Bước 2–7: tạo VPC, subnets, internet gateway, NAT gateway, route tables, security groups, và IAM roles.

---

## Bước 2: Tạo VPC & Subnets

### 2.1 Tạo VPC

**Console**: VPC Dashboard → **Your VPCs** → **Create VPC**

| Trường              | Giá trị            |
| ------------------- | ------------------ |
| Resources to create | **VPC and more**   |
| Name tag            | `smartinvoice-vpc` |
| IPv4 CIDR           | `10.0.0.0/16`      |
| Tenancy             | Default            |

![alt text](image.png)

### 2.2 Tạo 4 Subnets

**Console**: VPC → **Subnets** → **Create subnet** (nhấn **Add new subnet** để tạo cùng lúc)

| #   | Tên                       | AZ                | CIDR          |
| --- | ------------------------- | ----------------- | ------------- |
| 1   | `smartinvoice-public-1a`  | `ap-southeast-1a` | `10.0.1.0/24` |
| 2   | `smartinvoice-public-1b`  | `ap-southeast-1b` | `10.0.2.0/24` |
| 3   | `smartinvoice-private-1a` | `ap-southeast-1a` | `10.0.3.0/24` |
| 4   | `smartinvoice-private-1b` | `ap-southeast-1b` | `10.0.4.0/24` |

### 2.3 Bật Auto-assign Public IP

Cho **mỗi public subnet**: Actions → Edit subnet settings → ✅ Enable auto-assign public IPv4

---

## Bước 3: Tạo Internet Gateway

**Console**: VPC → **Internet Gateways** → **Create internet gateway**

| Name tag | `smartinvoice-igw` |
| -------- | ------------------ |

→ **Actions** → **Attach to VPC** → `smartinvoice-vpc` → **Attach** ✅

---

## Bước 4: Tạo NAT Gateway

> NAT Gateway cho phép Private Subnet truy cập Internet (outbound). Chi phí ~$32/tháng.

**Console**: VPC → **NAT Gateways** → **Create NAT gateway**

| Trường       | Giá trị                                             |
| ------------ | --------------------------------------------------- |
| Name         | `smartinvoice-nat-gw`                               |
| Subnet       | `smartinvoice-public-1a` ⚠️ (phải ở Public Subnet!) |
| Connectivity | Public                                              |
| Elastic IP   | Click **Allocate Elastic IP**                       |

Chờ status `Available` (2–3 phút).

---

## Bước 5: Tạo Route Tables

### 5.1 Public Route Table

**Console**: VPC → **Route Tables** → **Create route table**

| Tên                      | VPC                |
| ------------------------ | ------------------ |
| `smartinvoice-public-rt` | `smartinvoice-vpc` |

**Routes** → Edit → Add: `0.0.0.0/0` → Target: `smartinvoice-igw`

**Subnet associations**: tick `smartinvoice-public-1a` + `smartinvoice-public-1b`

### 5.2 Private Route Table

| Tên                       | VPC                |
| ------------------------- | ------------------ |
| `smartinvoice-private-rt` | `smartinvoice-vpc` |

**Routes** → Add: `0.0.0.0/0` → Target: `smartinvoice-nat-gw`

**Subnet associations**: tick `smartinvoice-private-1a` + `smartinvoice-private-1b`

---

## Bước 6: Tạo Security Groups

**Console**: VPC → **Security Groups** → **Create security group** (VPC: `smartinvoice-vpc`)

### SG 1: ALB (`smartinvoice-alb-sg`)

| Inbound | Port | Source      |
| ------- | ---- | ----------- |
| HTTP    | 80   | `0.0.0.0/0` |
| HTTPS   | 443  | `0.0.0.0/0` |

![alt text](image-2.png)

### SG 2: Backend (`smartinvoice-backend-sg`)

| Inbound    | Port | Source                |
| ---------- | ---- | --------------------- |
| HTTP       | 80   | `smartinvoice-alb-sg` |
| Custom TCP | 8080 | `smartinvoice-alb-sg` |

![alt text](image-3.png)

### SG 3: RDS (`smartinvoice-rds-sg`)

| Inbound    | Port | Source                    |
| ---------- | ---- | ------------------------- |
| PostgreSQL | 5432 | `smartinvoice-backend-sg` |
| PostgreSQL | 5432 | `smartinvoice-ocr-sg`     |

### SG 4: OCR (`smartinvoice-ocr-sg`)

| Inbound    | Port | Source                                    |
| ---------- | ---- | ----------------------------------------- |
| Custom TCP | 5000 | `smartinvoice-backend-sg` (Gọi trực tiếp) |

> Tất cả SG: **Outbound** = All traffic → `0.0.0.0/0`

---

## Bước 7: Tạo IAM Roles

Bạn cần tạo **4 IAM Roles**. Quy trình chung cho mỗi Role:

**Quy trình chung tạo Role**:

1. Truy cập **IAM Console** → Sidebar → **Roles** → **Create role**.
2. **Bước 1**: Trusted entity type: `AWS service`. Chọn dịch vụ tương ứng. Nhấn **Next**.
3. **Bước 2**: Tìm kiếm và tick các policy cần thiết. Nhấn **Next**.
4. **Bước 3**: Nhập **Role name** chính xác. Nhấn **Create role** ✅.

### 7.1 Role cho Elastic Beanstalk (**aws-elasticbeanstalk-ec2-role**)

Cấp quyền cho EC2 trong Backend để truy cập các tài nguyên AWS khác.

- **Trusted entity**: **AWS service** → **Elastic Beanstalk** → Use case: **Elastic Beanstalk - Compute**
- **Policies**:
  - `AmazonS3FullAccess`
  - `AmazonSQSFullAccess`
  - `AmazonCognitoPowerUser`
  - `AmazonSSMReadOnlyAccess`
  - `AmazonEC2ContainerRegistryReadOnly`
  - `CloudWatchLogsFullAccess`

![alt text](image-6.png)

### 7.2 Service Role cho EB (**aws-elasticbeanstalk-service-role**)

Cho phép Elastic Beanstalk thay mặt bạn gọi các dịch vụ AWS.

- **Trusted entity**: **AWS service** → **Elastic Beanstalk** → Use case: **Elastic Beanstalk - Environment**
- **Policies** (AWS tự động gắn):
  - `AWSElasticBeanstalkEnhancedHealth`
  - `AWSElasticBeanstalkManagedUpdatesCustomerRolePolicy`

![alt text](image-7.png)

### 7.3 ECS Execution Role (**ecsTaskExecutionRole**)

Dùng để ECS Fargate có quyền kéo image từ ECR và ghi log lên CloudWatch.

- **Trusted entity**: **AWS service** → **Elastic Container Service** → **Elastic Container Service Task**
- **Policies**:
  - `AmazonECSTaskExecutionRolePolicy`
  - `CloudWatchLogsFullAccess`

### 7.4 ECS Task Role cho OCR (**smartinvoice-ecs-task-role**)

Cấp quyền trực tiếp cho ứng dụng OCR chạy trong Container.

- **Trusted entity**: **AWS service** → **Elastic Container Service** → **Elastic Container Service Task**
- **Policies**:
  - `AmazonS3FullAccess`
  - `AmazonSQSFullAccess`
  - `AmazonSSMReadOnlyAccess`
