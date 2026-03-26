---
title: "Tuần 3 Báo cáo công việc"
date: 2026-01-01
weight: 3
chapter: false
---

### Tuần 3 Mục tiêu:

* Nắm vững kiến thức nâng cao về VPN và Transit Gateway trên AWS để thiết lập kết nối mạng phức hợp.
* Hiểu rõ các thành phần cơ bản của Amazon EC2 trên cả hai hệ điều hành Linux và Windows.
* Thành thạo các kỹ năng quản lý EC2: chỉnh sửa instance, quản lý EBS snapshots và tạo AMI tùy chỉnh.
* Thực hành triển khai ứng dụng web thực thực tế (LAMP/XAMPP) trên cả môi trường Linux và Windows Server.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Học và thực hành VPN Connection dùng Strongswan với Transit Gateway, sau đó dọn dẹp tài nguyên (clean up resources):<br>- Tạo Customer Gateway (CGW), tạo Transit Gateway, tạo VPN Connection, tạo Transit Gateway attachment, cấu hình route table, cấu hình CGW | 19/01/2026 | 19/01/2026 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.3-vpnsitetosite-optional/> |
| 3 | Học compute essentials với Amazon EC2:<br>- Tạo VPC cho Linux instance và VPC cho Windows instance<br>- Tạo Security Group cho Linux và Windows<br>- Tạo EC2 Amazon Linux instance và thực hiện kết nối vào instance Amazon Linux | 20/01/2026 | 20/01/2026 | <https://000004.awsstudygroup.com/2-prerequiste/> |
| 4 | Học Amazon EC2 cơ bản và thực hành:<br>- Chỉnh sửa (modify) EC2 instance<br>- Tạo và quản lý EBS snapshots<br>- Tạo Custom AMI<br>- Launch instance từ Custom AMI<br>- Remote desktop vào EC2 Ubuntu | 21/01/2026 | 21/01/2026 | <https://000004.awsstudygroup.com/5-amazonec2basic/> |
| 5 | Triển khai AWS User Management Application trên Amazon Linux:<br>- Cài LAMP web server trên Amazon Linux<br>- Cài Node.js<br>- Deploy application | 22/01/2026 | 22/01/2026 | <https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/> |
| 6 | Triển khai AWS User Management Application trên Amazon EC2 Windows:<br>- Cài XAMPP trên Amazon Windows<br>- Cài Node.js<br>- Deploy application | 23/01/2026 | 23/01/2026 | <https://000004.awsstudygroup.com/7-awsfcjmanagement-windows/> |

### Tuần 3 Kết quả đạt được:

* Thiết lập thành công VPN Connection sử dụng Strongswan và Transit Gateway, hiểu rõ luồng đi của traffic.
* Khởi tạo và kết nối thành công các instance EC2 trên nền tảng Linux và Windows trong các VPC riêng biệt.
* Có khả năng triển khai các giải pháp sao lưu và phục hồi hệ thống thông qua Snapshots và AMI tùy chỉnh.
* Triển khai thành công ứng dụng AWS User Management, nắm vững quy trình setup web server trên đa nền tảng.
