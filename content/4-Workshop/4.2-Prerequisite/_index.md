---
title: "Prerequisites"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

## 1. AWS Account

- An active **AWS Account** with administrative (or sufficiently broad) permissions.
- Log in to the **AWS Console**: https://console.aws.amazon.com
- In the top-right corner, select **Asia Pacific (Singapore)** `ap-southeast-1`.

> [!WARNING]
> All steps in this workshop must be performed in the **`ap-southeast-1`** region. Double-check the region selector before each step!

## 2. Required Tools (Local Machine)

Install the following tools on your local machine:

### AWS CLI v2

Download from: https://aws.amazon.com/cli/

After installation, verify:

```bash
aws --version   # Expected: aws-cli/2.x.x
```

Configure your credentials:

```bash
aws configure
```

Enter the following:

- **AWS Access Key ID**: (from your IAM User)
- **AWS Secret Access Key**: (from your IAM User)
- **Default region name**: `ap-southeast-1`
- **Default output format**: `json`

### Docker Desktop

Download from: https://www.docker.com/products/docker-desktop/

Ensure Docker is running (whale icon in taskbar):

```bash
docker --version
```

### Verify Setup

```bash
aws sts get-caller-identity
docker info
```

If both commands return output without errors, you are ready to proceed.

## 3. Source Code

You need access to the SmartInvoice Shield source code repository:

- **GitHub Repo**: `tuankiet18-dev/SMARTINVOICE-SHIELD`
- Ensure you have `git` installed and the repo cloned locally.

## 4. IAM User Permissions

Your IAM user needs the following permissions (or use an admin user for the lab):

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
