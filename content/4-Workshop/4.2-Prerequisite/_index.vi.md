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

## 5. Chuẩn Bị Môi Trường Local (Development)

Dự án sử dụng **tách môi trường Dev/Prod**. Cấu hình production nằm trên AWS Parameter Store và không bao giờ xuất hiện trong source code.

### Cấu trúc file cấu hình

| File | Git | Mục đích |
|------|:---:|----------|
| `SmartInvoice.API/appsettings.json` | ✅ Push | Config chung (không chứa secrets) |
| `SmartInvoice.API/appsettings.Development.json` | 🔒 Ignore | Config dev local (Cognito, DB, VnPay) |
| `SmartInvoice.API/.env` | 🔒 Ignore | AWS credentials cho local dev |
| `SmartInvoice.API/.env.example` | ✅ Push | Template cho developer mới |
| `SmartInvoice.Frontend/.env.development` | 🔒 Ignore | API URL localhost |
| `SmartInvoice.Frontend/.env.production` | ✅ Push | API URL production |
| `SmartInvoice.Frontend/.env.example` | ✅ Push | Template cho developer mới |

### Cách khởi tạo

```bash
# 1. Copy templates
cp SmartInvoice.API/.env.example SmartInvoice.API/.env
cp SmartInvoice.Frontend/.env.example SmartInvoice.Frontend/.env.development

# 2. Tạo file appsettings.Development.json theo mẫu
```

Nội dung mẫu `appsettings.Development.json`:

```json
{
  "Logging": { "LogLevel": { "Default": "Debug" } },
  "COGNITO_USER_POOL_ID": "<your-pool-id>",
  "COGNITO_CLIENT_ID": "<your-client-id>",
  "COGNITO_CLIENT_SECRET": "<your-client-secret>",
  "POSTGRES_HOST": "localhost",
  "POSTGRES_PORT": "5433",
  "POSTGRES_DB": "SmartInvoiceDb",
  "POSTGRES_USER": "postgres",
  "POSTGRES_PASSWORD": "<your-password>",
  "OCR_API_ENDPOINT": "http://localhost:5000",
  "ALLOWED_ORIGINS": "http://localhost:3000",
  "VnPay": {
    "TmnCode": "<your-vnpay-tmncode>",
    "HashSecret": "<your-vnpay-hashsecret>",
    "ReturnUrl": "http://localhost:3000/app/payment/result"
  }
}
```

> [!IMPORTANT]
> Khi chạy `dotnet run` ở Development mode, ứng dụng **tự động** load `appsettings.Development.json` và **KHÔNG** kết nối AWS Parameter Store. Khi deploy lên Production (Elastic Beanstalk), ứng dụng **tự động** load từ Parameter Store.

