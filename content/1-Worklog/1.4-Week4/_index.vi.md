---
title: "Tuần 4 Báo cáo công việc"
date: 2026-01-01
weight: 4
chapter: false
---

### Tuần 4 Mục tiêu:

* Nghiên cứu và chuẩn hóa dữ liệu XML theo quy định của Cơ quan Thuế để xây dựng nền tảng nghiệp vụ cho dự án.
* Phát triển và kiểm thử các tính năng cốt lõi của backend (validate, parse XML) với dữ liệu thực tế từ Invoice.
* Tự động hóa quy trình lưu trữ tệp tin trên AWS S3 bằng Python Code (Boto3).
* Cập nhật các xu hướng và giải pháp AI/ML mới nhất từ sự kiện AWS re:Invent Recap phục vụ phát triển dự án.
* Tối ưu hóa bảo mật hệ thống bằng AWS Systems Manager và triển khai các tính năng chống giả mạo hóa đơn.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | **• AWS Lab (Web Servers):** Triển khai LAMP Stack trên EC2; xử lý lỗi tương thích package giữa Amazon Linux 2 và Amazon Linux 2023; triển khai Node.js và cấu hình Inbound Rules cho port 5000.<br>**• Project (Analysis):** Phác thảo System Context Diagram; nghiên cứu XML Schema Definition (XSD) chính thức từ Cơ quan Thuế. | 26/01/2026 | 26/01/2026 |  |
| 3 | **• Backend Development (MVP) – XML Validation:** Phát triển module validate XML bằng C#/.NET; tinh chỉnh file XSD để xử lý lỗi “Ambiguous Content Model”, hỗ trợ đa dạng định dạng hoá đơn.<br>**• Testing:** Chạy unit test với dữ liệu thực tế (hoá đơn học phí FPT University); xác minh parser xử lý cấu trúc XML phức tạp. | 27/01/2026 | 27/01/2026 |  |
| 4 | **• Project (Compliance):** Triển khai logic rủi ro theo Quyết định 1510/QĐ-TCT; tách biệt luồng xử lý cho hoá đơn GTGT và hoá đơn bán hàng.<br>**• AWS Lab (S3 Automation):** Dùng Python (boto3) upload file lên Amazon S3; cấu hình IAM Access Key và Secret Key. | 28/01/2026 | 28/01/2026 | <https://000048.awsstudygroup.com/> |
| 5 | **• Professional Development:** Tham gia AWS re:Invent Recap tại TP.HCM, cập nhật kiến thức AI/ML cho dự án.<br>**• Key Takeaways:** Tìm hiểu Amazon SageMaker Unified Studio, Amazon S3 Tables và Vector Embeddings cho semantic search. | 29/01/2026 | 29/01/2026 |  |
| 6 | **• Development (C#):** Triển khai anti-spoofing; thêm logic phát hiện hoá đơn sinh bởi máy; sửa lỗi parse XML Namespace.<br>**• AWS Lab:** Dùng AWS Systems Manager (Session Manager) để truy cập instance an toàn; troubleshoot lỗi kết nối DB của Node.js app. | 30/01/2026 | 30/01/2026 |  |

### Tuần 4 Kết quả đạt được:

* Triển khai thành công web server trên AL2023 và làm chủ các công cụ quản trị hệ thống an toàn của AWS.
* Module xử lý XML hoàn thiện, có khả năng validate chính xác và linh hoạt theo chuẩn XSD của Cơ quan Thuế.
* Hệ thống đã tích hợp logic phân loại rủi ro hóa đơn và tuân thủ các quy định hiện hành về hóa đơn điện tử.
* Làm chủ kỹ thuật tự động hóa lưu trữ trên S3 và tích hợp được các insight công nghệ AI mới vào định hướng dự án.
* Hoàn thành các tính năng chống giả mạo và nhận diện hóa đơn máy sinh, giải quyết triệt để các lỗi kỹ thuật về XML.
