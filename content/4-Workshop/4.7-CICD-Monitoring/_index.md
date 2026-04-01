---
title: "CI/CD & Monitoring"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 4.7. </b> "
---

This section covers Steps 18–19: configuring GitHub Actions for automated CI/CD and setting up CloudWatch monitoring and alarms.

---

## Step 18: Configure GitHub Actions (CI/CD)

### 18.1 Configure GitHub Secrets

Go to your GitHub Repository → **Settings** → **Secrets and variables** → **Actions** → Add the following secrets:

| Secret | Value |
|---|---|
| `AWS_ACCESS_KEY_ID` | IAM Access Key |
| `AWS_SECRET_ACCESS_KEY` | IAM Secret Key |
| `AWS_REGION` | `ap-southeast-1` |
| `AWS_ACCOUNT_ID` | 12-digit Account ID |

### 18.2 Trigger Workflow

Push code to the `main` branch. GitHub Actions will automatically:

1. Build Docker images for Backend & OCR → Push to ECR.
2. Update Elastic Beanstalk (Backend) & ECS Service (OCR).

### 18.3 Backend Workflow (`deploy-backend.yml`)

The workflow builds the .NET 9 Docker image, pushes it to ECR, and deploys to Elastic Beanstalk:

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

## Step 19: CloudWatch Monitoring & Alarms

### 19.1 Set Up SNS Notifications

1. **Console**: SNS → **Create topic** → Name: `smartinvoice-alerts`
2. **Create subscription** → Protocol: `Email` → Enter your email address.
3. Confirm the subscription email you receive.

### 19.2 Create CloudWatch Alarms

**Console**: CloudWatch → **Alarms** → **Create alarm**

| Alarm Name | Condition | Action |
|---|---|---|
| **OCR Tasks Down** | `RunningTaskCount < 1` | Send email via SNS |
| **API 5xx Errors High** | `5xxError > 5 (1 min)` | Send email via SNS |
| **RDS Storage Low** | `FreeStorageSpace < 5GB` | Send email via SNS |

### 19.3 View Logs in CloudWatch

- **OCR Logs**: CloudWatch → Log groups → `/ecs/smartinvoice-ocr-task`
- **Backend Logs**: CloudWatch → Log groups → (Elastic Beanstalk auto-creates)

> [!TIP]
> Use **CloudWatch Log Insights** to query logs across time ranges — useful for debugging OCR processing errors.
