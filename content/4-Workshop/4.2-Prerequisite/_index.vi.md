---
title: "Chuẩn bị"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

## 1. Tài khoản AWS

- Một **Tài khoản AWS** đang hoạt động với quyền quản trị (hoặc đủ rộng).
- Đăng nhập vào **AWS Console**: https://console.aws.amazon.com
- Góc trên phải → chọn **Asia Pacific (Singapore)** `ap-southeast-1`.

> [!WARNING]
> Tất cả các bước trong workshop này phải thực hiện ở **Region `ap-southeast-1`**. Hãy kiểm tra lại region trước mỗi bước!

## 2. Công cụ Cần Thiết (Máy tính local)

Cài đặt các công cụ sau lên máy tính của bạn:

### AWS CLI v2

Tải về tại: https://aws.amazon.com/cli/

Sau khi cài đặt, kiểm tra:

```bash
aws --version   # Kết quả mong đợi: aws-cli/2.x.x
```

Cấu hình thông tin đăng nhập:

```bash
aws configure
```

Nhập các thông tin:

- **AWS Access Key ID**: (Lấy từ IAM User của bạn)
- **AWS Secret Access Key**: (Lấy từ IAM User của bạn)
- **Default region name**: `ap-southeast-1`
- **Default output format**: `json`

### Docker Desktop

Tải về tại: https://www.docker.com/products/docker-desktop/

Đảm bảo Docker đang chạy (biểu tượng cá voi ở taskbar):
```bash
docker --version
```

### Xác minh Thiết lập

```bash
aws sts get-caller-identity
docker info
```

Nếu cả hai lệnh trả về kết quả mà không có lỗi, bạn đã sẵn sàng tiếp tục.

## 3. Mã nguồn (Source Code)

Bạn cần có quyền truy cập vào kho mã nguồn SmartInvoice Shield:

- **GitHub Repo**: `tuankiet18-dev/SMARTINVOICE-SHIELD`
- Đảm bảo bạn đã cài `git` và clone repo về máy.

## 4. Quyền IAM User

IAM User của bạn cần có các quyền sau (hoặc dùng tài khoản admin cho bài lab):
- `AmazonEC2FullAccess`
- `AmazonECS_FullAccess`
- `AmazonRDSFullAccess`
- `AmazonS3FullAccess`
- `AmazonCognitoPowerUser`
- `AmazonSQSFullAccess`
- `AWSElasticBeanstalkFullAccess`
- `AmazonEC2ContainerRegistryFullAccess`
- `AmazonSSMFullAccess`
- `CloudFrontFullAccess`
- `IAMFullAccess`
