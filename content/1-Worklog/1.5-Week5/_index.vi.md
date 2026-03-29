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
| 2 | **AWS Lab:**<br>• Cấu hình ASG với Dynamic Scaling Policies<br>• Thực hiện Stress Tests bằng Apache Bench (ab)<br>• Quản lý CloudFront và cache invalidation<br><br>**Kiến trúc Dự án:**<br>• Thiết kế chiến lược S3 dùng Access Points<br>• Lập kế hoạch S3 Lifecycle Policies để tiết kiệm chi phí | 02/02/2026 | 02/02/2026 |  |
| 3 | **AWS Lab:**<br>• Thử nghiệm VM Import/Export (VMware to AMI)<br>• Phân tích lỗi CLIENT_ERROR: Unsupported kernel version<br>• Cấu hình AWS Backup Plans<br><br>**Công cụ:**<br>• Thực hành AWS CloudShell cho các lệnh CLI | 03/02/2026 | 03/02/2026 |  |
| 4 | **Dự án - Thiết kế Database:**<br>• Phân tích schema database cho SmartInvoice Shield<br>• Cấu hình DbContext và EF Core migrations<br>• Tạo các bảng trong PostgreSQL | 04/02/2026 | 04/02/2026 |  |
| 5 | **AWS Labs - Tính toán & Lưu trữ:**<br>• Provision và cấu hình EC2 instances và Security Groups<br>• Tạo S3 buckets và access control policies | 05/02/2026 | 05/02/2026 | https://000057.awsstudygroup.com/ |
| 6 | **Dự án - Bảo mật Backend:**<br>• Nghiên cứu thư viện tích hợp AWS Cognito cho .NET 9<br>• Thiết lập middleware xác thực JWT trong Program.cs | 06/02/2026 | 06/02/2026 |  |

### Tuần 5 Kết quả đạt được:

- Triển khai thành công ASG có cơ chế dynamic scaling và kiểm thử bằng Apache Bench.
- Tối ưu hóa chi phí lưu trữ S3 bằng Lifecycle Policies và quản lý quyền truy cập qua Access Points.
- Có kinh nghiệm thực hành công cụ di chuyển VM và AWS CloudShell.
- Hoàn tất migration database và tích hợp xác thực JWT với AWS Cognito.
