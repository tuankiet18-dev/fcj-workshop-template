---
title: "Tuần 5 Báo cáo công việc"
date: 2026-01-01
weight: 5
chapter: false
---

### Tuần 5 Mục tiêu:

- Cấu hình và đánh giá AWS Auto Scaling với các Dynamic Scaling Policy.
- Thiết kế và triển khai chiến lược lưu trữ S3 dùng Access Points và Lifecycle Policies.
- Thực hiện các thao tác VM Import/Export và cấu hình sao lưu tự động.
- Thiết kế schema database và bảo mật backend (AWS Cognito) cho dự án SmartInvoice Shield.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                    |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------- |
| 2   | AWS Lab: Cấu hình Auto Scaling Group (ASG) với Dynamic Scaling Policies dựa trên mức sử dụng CPU; thực hiện stress test bằng Apache Bench (ab) để kích hoạt scaling events; quản lý CloudFront distribution và xử lý cache invalidation.<br><br>Project Architecture: Thiết kế chiến lược lưu trữ S3 dùng Access Points để đơn giản hoá quản lý phân quyền; lập kế hoạch S3 Lifecycle Policies để chuyển dữ liệu hoá đơn cũ (> 3 tháng) sang S3 Standard-IA nhằm tiết kiệm chi phí. | 02/02/2026   | 02/02/2026      |                                   |
| 3   | AWS Lab: Thử nghiệm VM Import/Export (VMware to AMI); ghi nhận bài học khi gặp lỗi CLIENT_ERROR: Unsupported kernel version do OS không tương thích và phân tích nguyên nhân; cấu hình AWS Backup Plans để tự động bảo vệ tài nguyên.<br><br>Tools: Thực hành AWS CloudShell để chạy lệnh AWS CLI mà không cần cấu hình local.                                                                                                                                                      | 03/02/2026   | 03/02/2026      |                                   |
| 4   | FCJ Project (Database Design): Phân tích yêu cầu schema database cho dự án SmartInvoice Shield; cấu hình DbContext; viết migration scripts bằng Entity Framework Core; tạo các table trong PostgreSQL.                                                                                                                                                                                                                                                                              | 04/02/2026   | 04/02/2026      |                                   |
| 5   | FCJ AWS Labs (Compute & Storage): Thực hành provision và cấu hình Amazon EC2 instances, thiết lập Security Groups; tạo và cấu hình Amazon S3 buckets, viết access control policies để chuẩn bị hạ tầng lưu trữ.                                                                                                                                                                                                                                                                     | 05/02/2026   | 05/02/2026      | https://000057.awsstudygroup.com/ |
| 6   | FCJ Project (Backend Security): Nghiên cứu tài liệu AWS Cognito API và các thư viện tích hợp cho .NET 9; thiết lập middleware trong Program.cs để nhận và validate JWT tokens từ AWS Cognito.                                                                                                                                                                                                                                                                                       | 06/02/2026   | 06/02/2026      |                                   |

### Tuần 5 Kết quả đạt được:

- Triển khai thành công ASG có cơ chế dynamic scaling và kiểm thử bằng Apache Bench.
- Tối ưu hóa chi phí lưu trữ S3 bằng Lifecycle Policies và quản lý quyền truy cập qua Access Points.
- Có kinh nghiệm thực hành công cụ di chuyển VM và AWS CloudShell.
- Hoàn tất migration database và tích hợp xác thực JWT với AWS Cognito.
