---
title: "Tự đánh giá"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

Trong suốt thời gian thực tập tại dự án **SmartInvoice Shield** từ tháng 01/2026 đến tháng 04/2026, tôi đã có cơ hội học hỏi và áp dụng các dịch vụ Cloud hàng đầu của AWS vào giải pháp quản lý hóa đơn thực tế.  
Tôi đã trực tiếp tham gia xây dựng kiến trúc hạ tầng (VPC, ASG, RDS), tích hợp pipeline AI OCR và tối ưu hóa hệ thống để sẵn sàng cho môi trường sản xuất (Production).

### Các Đóng Góp Nổi Bật & Dấu Ấn Kỹ Thuật

**1. Thiết kế Kiến trúc Hạ tầng & Cloud Native**

- Trực tiếp tham gia thiết kế và xây dựng kiến trúc hạ tầng cốt lõi trên AWS, bao gồm việc thiết lập VPC, Auto Scaling Groups (ASG) và cơ sở dữ liệu Amazon RDS để đảm bảo hệ thống sẵn sàng cho môi trường Production.
- Thiết kế hệ thống theo mô hình Event-Driven Architecture, sử dụng kết hợp Amazon SQS, Amazon ECS Fargate Spot và RDS để tối ưu hóa hiệu suất và chi phí vận hành.
- Làm chủ và ứng dụng linh hoạt hệ sinh thái các dịch vụ của AWS như IAM, S3 và Cognito để đáp ứng các tiêu chuẩn bảo mật khắt khe.

**2. Phát triển Backend (.NET 9) & Logic Nghiệp vụ**

- Đảm nhận vai trò Backend Lead, trực tiếp thiết kế và triển khai các logic nghiệp vụ cốt lõi của hệ thống.
- Tích hợp thành công toàn bộ các dịch vụ hạ tầng AWS với hệ thống backend được phát triển bằng .NET 9.
- Xây dựng hệ thống phân quyền Role-Based Access Control (RBAC), thiết lập các lớp kiểm tra chống giả mạo (anti-spoofing) và xác thực đa tầng (multi-layer validation) để đảm bảo tính toàn vẹn của luồng dữ liệu.
- Ứng dụng thư viện Boto3 của Python để tự động hóa các tác vụ quản lý hạ tầng.

**3. Tối ưu hóa Hệ thống & Xử lý sự cố (Troubleshooting)**

- Thực hiện thành công việc tích hợp và tối ưu hóa pipeline AI OCR vào dự án.
- Giải quyết triệt để các vấn đề phức tạp liên quan đến độ trễ của OCR, tích hợp SQS và khắc phục các lỗi triển khai trên môi trường Elastic Beanstalk.
- Chủ động đề xuất và xây dựng logic AI Fallback để xử lý các lỗi tràn bộ nhớ (memory errors), qua đó nâng cao đáng kể độ tin cậy của hệ thống.
- Tái cấu trúc logic tải lên (upload) của Frontend bằng kỹ thuật parallel polling, đồng thời điều chỉnh SemaphoreSlim của Worker để xử lý hàng loạt (batch processing) mượt mà hơn nhằm tối ưu hóa luồng xử lý bất đồng bộ.
- Chủ động đề xuất giải pháp sử dụng AWS Cloud Map để tối ưu hóa chi phí hệ thống và đảm bảo việc di chuyển cơ sở dữ liệu (database migration) diễn ra an toàn.

### Tự Đánh Giá

Để phản ánh một cách khách quan quá trình thực tập, tôi xin tự đánh giá bản thân dựa trên các tiêu chí dưới đây:

| STT | Tiêu chí                 | Đánh giá | Nhận xét                                                                                                               |
| --- | ------------------------ | -------- | ---------------------------------------------------------------------------------------------------------------------- |
| 1   | **Kiến thức chuyên môn** | ✅ Tốt   | Nắm vững hệ sinh thái AWS (IAM, VPC, S3, SQS, RDS, Cognito) và tích hợp thành công với backend .NET 9.                 |
| 2   | **Khả năng học hỏi**     | ✅ Tốt   | Tiếp thu nhanh các công nghệ mới về Cloud Native, tối ưu hóa pipeline AI và tự động hóa hạ tầng bằng Boto3.            |
| 3   | **Tính chủ động**        | ✅ Tốt   | Chủ động đề xuất giải pháp tối ưu hóa chi phí (Cloud Map) và nâng cao độ tin cậy của hệ thống (AI Fallback logic).     |
| 4   | **Kỷ luật**              | ✅ Khá   | Tuân thủ tốt lịch trình làm việc và quy trình triển khai, duy trì nhật ký công việc (worklog) đầy đủ hàng tuần.        |
| 5   | **Giao tiếp**            | ✅ Khá   | Trình bày giải pháp kỹ thuật rõ ràng, báo cáo tiến độ kịp thời và phối hợp tốt với các thành viên trong dự án.         |
| 6   | **Teamwork**             | ✅ Tốt   | Hợp tác hiệu quả giữa các mảng Backend, AI và Cloud để đảm bảo hệ thống vận hành trơn tru và đồng bộ.                  |
| 7   | **Giải quyết vấn đề**    | ✅ Tốt   | Xử lý triệt để các lỗi triển khai trên Elastic Beanstalk, tối ưu hóa độ trễ OCR và quản lý di chuyển database an toàn. |
| 8   | **Đóng góp cho dự án**   | ✅ Tốt   | Xây dựng thành công hệ thống SmartInvoice Shield ổn định, bảo mật cao và có khả năng mở rộng tốt trên môi trường AWS.  |

### Cần cải thiện

- Nâng cao tính kỷ luật trong việc cập nhật tài liệu kỹ thuật ngay khi có thay đổi nhỏ trong hệ thống.
- Cải thiện kỹ năng thuyết trình các mô hình kiến trúc phức tạp một cách trực quan và dễ hiểu hơn.
- Tiếp tục học hỏi các dịch vụ Serverless nâng cao để tối ưu hóa hơn nữa kiến trúc ứng dụng trong tương lai.
