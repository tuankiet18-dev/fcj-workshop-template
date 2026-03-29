---
title: "Tuần 9 Báo cáo công việc"
date: 2026-01-01
weight: 9
chapter: false
---

### Tuần 9 Mục tiêu:

* Triển khai các lớp bảo mật bao gồm RBAC ở Frontend và Cô lập dữ liệu (Data Isolation) cho các thành viên dự án.
* Xây dựng và triển khai quy trình xử lý bất đồng bộ sử dụng AWS SQS để xử lý các tác vụ OCR và validate có độ trễ cao.
* Phát triển logic hợp nhất dữ liệu phức tạp ("Invoice Dossier Merge") để đồng bộ hóa dữ liệu XML và dữ liệu trích xuất từ AI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | **Dự án - Ủy quyền & UI/UX:**<br>• Triển khai Role-Based Access Control (RBAC) cho AppLayout và routing ở frontend<br>• Thực thi Data Isolation cho Member trên Dashboard và Validation<br>• Refactor thông báo lỗi validation từ backend<br>• Cải thiện giao diện UploadInvoice và tính năng chọn dòng | 09/03/2026 | 09/03/2026 |  |
| 3 | **Dự án - Cấu hình Hạ tầng & Sửa lỗi:**<br>• Cấu hình các thiết lập cho Super Admin panel<br>• Thiết lập môi trường cho AI, Validation, S3 và Security<br>• Xử lý lỗi khóa ngoại PostgreSQL trong cập nhật cấu hình | 10/03/2026 | 10/03/2026 |  |
| 4 | **Dự án - Tích hợp AI OCR & Xác thực Business:**<br>• Tích hợp kết quả JSON từ AI OCR vào hệ thống<br>• Phác thảo và triển khai luồng xử lý dữ liệu trích xuất<br>• Xác thực logic nghiệp vụ cho hóa đơn hình ảnh và PDF | 11/03/2026 | 11/03/2026 |  |
| 5 | **Dự án - Xử lý Bất đồng bộ (AWS SQS):**<br>• Thiết kế và triển khai luồng validate bất đồng bộ qua SQS<br>• Áp dụng pattern Producer-Consumer và Polly policies<br>• Sử dụng SemaphoreSlim để kiểm soát xử lý đồng thời | 12/03/2026 | 12/03/2026 |  |
| 6 | **Dự án - UI/UX cho Luồng Bất đồng bộ:**<br>• Phát triển Giai đoạn 1 của UI hỗ trợ quy trình bất đồng bộ<br>• Triển khai cơ chế smart polling để lấy kết quả hiệu quả<br>• Thêm các chỉ bảo trạng thái thời gian thực cho người dùng | 13/03/2026 | 13/03/2026 |  |
| 7 | **Dự án - Tái cấu trúc & Hợp nhất Dữ liệu:**<br>• Tái cấu trúc lớn các dịch vụ backend và dọn dẹp code<br>• Triển khai logic "Hợp nhất Hồ sơ Hóa đơn" (XML ghi đè OCR) | 14/03/2026 | 14/03/2026 |  |

### Tuần 9 Kết quả đạt được:

* Khắc phục thành công vấn đề timeout API bằng cách chuyển sang kiến trúc bất đồng bộ dựa trên SQS bền bỉ.
* Nâng cao trải nghiệm người dùng với các chỉ báo trạng thái thời gian thực và cơ chế polling thông minh cho xử lý hàng loạt.
* Củng cố bảo mật hệ thống và tính toàn vẹn dữ liệu thông qua RBAC, cô lập dữ liệu và xử lý lỗi chặt chẽ.
