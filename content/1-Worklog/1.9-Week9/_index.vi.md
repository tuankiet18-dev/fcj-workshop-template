---
title: "Tuần 9 Báo cáo công việc"
date: 2026-01-01
weight: 9
chapter: false
---

### Tuần 9 Mục tiêu:

* Core Business Logic: XML structure analysis and data mapping.
* API Development: Company entity processing.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - FCJ Project - Backend &amp; API Development<br>	- Triển khai Invoice CRUD API và hệ thống Audit Logs ở backend.<br>	- Tối ưu hóa hiệu năng xử lý file XML cho hóa đơn.<br>	- Thiết lập và cấu hình các biến môi trường cho dự án.<br>	- Tổ chức quản lý Git branch (tạo branch mới từ dev để phát triển tính năng mới). | 02/03/2026 | 02/03/2026 |  |
| 3 | - FCJ Project - API &amp; UI Enhancement<br>	- Phát triển logic backend cho chức năng filtering, pagination và RBAC.<br>	- Cải thiện UI/UX ở frontend cho phần quản lý hóa đơn.<br>	- Xử lý conflict code và merge nhánh thành công.<br>- Completed AWS Lab: Database Essentials with Amazon RDS<br>	- Key Technical Activities:<br>		- DB Instance Creation: Khởi tạo thành công Amazon RDS instance (PostgreSQL/SQL Server) phù hợp với cấu hình backend .NET của dự án.<br>		- Connectivity &amp; Security: Cấu hình Security Groups để kiểm soát inbound traffic, chỉ cho phép kết nối từ dải IP cụ thể hoặc từ Application Tier (EC2/Elastic Beanstalk).<br>		- Database Management: Thực hành kết nối và quản lý database thông qua công cụ quản lý (như pgAdmin hoặc SQL Server Management Studio) từ môi trường local.<br>		- Backup &amp; Monitoring: Thiết lập chế độ Automated Backups và theo dõi các chỉ số hiệu năng (CPU, RAM, Storage) qua Amazon CloudWatch. | 03/03/2026 | 03/03/2026 |  |
| 4 | - FCJ Project - Cloud Infrastructure &amp; Security<br>	- Refactor hệ thống cấu hình: thay thế DotNetEnv bằng AWS Parameter Store để quản lý config bảo mật hơn.<br>	- Lên kế hoạch thiết kế Cloud Infrastructure trên AWS (VPC, RDS, S3, Cognito, ECS Fargate cho OCR, Elastic Beanstalk cho API, CloudWatch), đảm bảo tiêu chí Multi-AZ, tối ưu chi phí và bảo mật. | 04/03/2026 | 04/03/2026 |  |
| 5 | - FCJ Project - Core Business Logic<br>	- Nghiên cứu và thiết kế luồng Validation 2 bước cho hệ thống hóa đơn.<br>	- Phát triển logic xác thực quyền sở hữu hóa đơn (kiểm tra MST người mua khớp với MST công ty).<br>	- Xử lý logic check trùng lặp hóa đơn và ngăn chặn việc lưu các hóa đơn lỗi (Rejected) thành rác dữ liệu (junk data) trong DB. | 05/03/2026 | 05/03/2026 |  |
| 6 | - FCJ Project - Backend Implementation<br>	- Thực thi code cho phần logic Invoice Ownership Validation đã thiết kế.<br>	- Bổ sung các hành động quản lý bản nháp hóa đơn (draft management: submit/delete).<br>	- Review và merge feature validation này vào nhánh chính. | 06/03/2026 | 06/03/2026 |  |
| 7 | - FCJ Project - Codebase Maintenance &amp; Team Collaboration<br>	- Dọn dẹp repository (xóa các file lock thừa như bun).<br>	- Review code và merge các Pull Request quan trọng từ team member (liên quan đến Invoice CRUD API, Dashboard UI, UI/UX của Risk Check và Audit Logs). | 07/03/2026 | 07/03/2026 |  |

### Tuần 9 Kết quả đạt được:

* Hoàn thành các công việc đã đề ra trong tuần.
* Hiểu sâu hơn về các dịch vụ AWS đã thực hành.
