---
title: "Workshop"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

# SmartInvoice Shield — End-to-End Deployment on AWS

#### Overview

**SmartInvoice Shield** is a production-grade, cloud-native invoice management platform built on AWS. It uses AI-powered OCR to automatically extract key data from invoice images and PDFs, validates the results, and provides a secure web interface for users to review, merge, and manage invoices.

In this workshop, you will deploy the complete SmartInvoice Shield architecture on AWS from scratch, covering networking, security, compute, storage, CI/CD, and monitoring.

#### Architecture at a Glance

The system is deployed across **2 Availability Zones** in `ap-southeast-1` (Singapore) and consists of:
- **Frontend**: React + Vite hosted on AWS Amplify
- **DNS & Custom Domain**: Amazon Route 53
- **CDN / HTTPS Proxy**: CloudFront in front of the Backend ALB
- **Backend API**: .NET 9 running on Elastic Beanstalk (private EC2 instances)
- **OCR AI Service**: Python (FastAPI + LayoutLMv3/Gemini) on ECS Fargate
- **Database**: RDS PostgreSQL 16 (Multi-AZ)
- **Authentication**: Amazon Cognito User Pool
- **Queuing**: Amazon SQS (OCR queue + VietQR queue)
- **Storage**: Amazon S3 (private, Presigned URL access)
- **Secrets**: SSM Parameter Store

#### Content

1. [Architecture Overview](5.1-Architecture/)
2. [Prerequisites](5.2-Prerequisite/)
3. [Networking & Security](5.3-Networking-Security/)
4. [Storage, Auth & Database](5.4-Storage-Database/)
5. [Container Registry & Compute](5.5-Compute-Backend/)
6. [Frontend, Proxy & Route 53](5.6-Frontend-Proxy/)
7. [CI/CD & Monitoring](5.7-CICD-Monitoring/)
8. [End-to-End Testing](5.8-Testing/)
9. [Clean Up](5.9-Cleanup/)