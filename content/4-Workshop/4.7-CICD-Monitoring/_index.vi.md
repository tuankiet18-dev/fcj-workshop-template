---
title: "CI/CD & Giám sát"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 4.7. </b> "
---

Phần này bao gồm Bước 18–19: cấu hình GitHub Actions để tự động hóa CI/CD và thiết lập CloudWatch Monitoring & Alarms.

---

## Bước 18: Cấu hình GitHub Actions (CI/CD)

### 18.1 Cấu hình GitHub Secrets

Vào GitHub Repository → **Settings** → **Secrets and variables** → **Actions** → Thêm các secret sau:

| Secret | Value |
|---|---|
| `AWS_ACCESS_KEY_ID` | IAM Access Key |
| `AWS_SECRET_ACCESS_KEY` | IAM Secret Key |
| `AWS_REGION` | `ap-southeast-1` |
| `AWS_ACCOUNT_ID` | 12-digit Account ID |

### 18.2 Kích hoạt Workflow

Đẩy code lên branch `main`, GitHub Actions sẽ tự động:

1. Build Docker image Backend & OCR → Đẩy lên ECR.
2. Cập nhật Elastic Beanstalk (Backend) & ECS Service (OCR).

### 18.3 Backend Workflow (`deploy-backend.yml`)

Workflow build .NET 9 Docker image, push lên ECR và deploy lên Elastic Beanstalk:

```yaml
name: Deploy Backend to EB

on:
  push:
    branches: [main]
    paths: ['SmartInvoice.API/**']

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v4
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: ${{ secrets.AWS_REGION }}

      - name: Login to ECR
        uses: aws-actions/amazon-ecr-login@v2

      - name: Build, tag and push image
        run: |
          docker build -t smartinvoice-backend ./SmartInvoice.API
          docker tag smartinvoice-backend:latest \
            ${{ secrets.AWS_ACCOUNT_ID }}.dkr.ecr.ap-southeast-1.amazonaws.com/smartinvoice-backend:latest
          docker push \
            ${{ secrets.AWS_ACCOUNT_ID }}.dkr.ecr.ap-southeast-1.amazonaws.com/smartinvoice-backend:latest

      - name: Deploy to Elastic Beanstalk
        uses: einaregilsson/beanstalk-deploy@v22
        with:
          aws_access_key: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws_secret_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          application_name: Smartinvoice-api
          environment_name: Smartinvoice-api-env
          region: ap-southeast-1
          deployment_package: Dockerrun.aws.json
```

---

## Bước 19: CloudWatch Monitoring & Alarms

### 19.1 Thiết lập SNS Notification

1. **Console**: SNS → **Create topic** → Name: `smartinvoice-alerts`
2. **Create subscription** → Protocol: `Email` → Nhập email của bạn.
3. Xác nhận email đăng ký nhận thông báo.

### 19.2 Tạo CloudWatch Alarms

**Console**: CloudWatch → **Alarms** → **Create alarm**

| Tên Alarm | Điều kiện | Hành động |
|---|---|---|
| **OCR Tasks Down** | `RunningTaskCount < 1` | Gửi mail qua SNS |
| **API 5xx Errors High** | `5xxError > 5 (1 phút)` | Gửi mail qua SNS |
| **RDS Storage Low** | `FreeStorageSpace < 5GB` | Gửi mail qua SNS |

### 19.3 Xem Logs trên CloudWatch

- **OCR Logs**: CloudWatch → Log groups → `/ecs/smartinvoice-ocr-task`
- **Backend Logs**: CloudWatch → Log groups → (Elastic Beanstalk tự tạo)

> [!TIP]
> Dùng **CloudWatch Log Insights** để truy vấn logs theo khoảng thời gian — rất hữu ích để debug lỗi xử lý OCR.
