---
title: "Workshop"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

# SmartInvoice Shield — Triển Khai End-to-End trên AWS

#### Tổng quan

**SmartInvoice Shield** là nền tảng quản lý hóa đơn cấp production, được xây dựng trên AWS. Hệ thống sử dụng OCR (Nhận dạng ký tự quang học) kết hợp AI để tự động trích xuất dữ liệu từ ảnh và file PDF hóa đơn, sau đó cho phép người dùng xem xét, ghép nối và quản lý hóa đơn qua giao diện web bảo mật.

Trong workshop này, bạn sẽ tự tay triển khai toàn bộ kiến trúc SmartInvoice Shield trên AWS từ đầu, bao gồm mạng, bảo mật, compute, lưu trữ, CI/CD và giám sát.

#### Nhìn chung về Kiến trúc

Hệ thống được triển khai trên **2 Availability Zones** tại `ap-southeast-1` (Singapore) và bao gồm:
- **Frontend**: React + Vite chạy trên AWS Amplify
- **DNS & Tên miền tùy chỉnh**: Amazon Route 53
- **CDN / HTTPS Proxy**: CloudFront đặt trước Backend ALB
- **Backend API**: .NET 9 trên Elastic Beanstalk (EC2 private)
- **OCR AI Service**: Python (FastAPI + LayoutLMv3/Gemini) trên ECS Fargate
- **Cơ sở dữ liệu**: RDS PostgreSQL 16 (Multi-AZ)
- **Xác thực**: Amazon Cognito User Pool
- **Hàng đợi**: Amazon SQS (OCR queue + VietQR queue)
- **Lưu trữ**: Amazon S3 (private, truy cập qua Presigned URL)
- **Quản lý cấu hình**: SSM Parameter Store

#### Nội dung

1. [Tổng quan kiến trúc](5.1-Architecture/)
2. [Chuẩn bị](5.2-Prerequisite/)
3. [Mạng & Bảo mật](5.3-Networking-Security/)
4. [Lưu trữ, Xác thực & Cơ sở dữ liệu](5.4-Storage-Database/)
5. [Container Registry & Compute](5.5-Compute-Backend/)
6. [Frontend, Proxy & Route 53](5.6-Frontend-Proxy/)
7. [CI/CD & Giám sát](5.7-CICD-Monitoring/)
8. [Kiểm tra Tổng thể](5.8-Testing/)
9. [Dọn dẹp Tài nguyên](5.9-Cleanup/)