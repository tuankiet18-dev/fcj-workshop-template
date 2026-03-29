---
title: "Tuần 10 Báo cáo công việc"
date: 2026-01-01
weight: 10
chapter: false
---

### Tuần 10 Mục tiêu:

* Thực hiện đại tu UI/UX toàn diện sử dụng Tailwind CSS và Ant Design để hiện đại hóa giao diện ứng dụng.
* Tái cấu trúc quy trình xử lý AI OCR nhằm đạt khả năng tương thích cao với AWS Fargate Serverless (chuyển sang CPU-only).
* Nâng cao tính minh bạch của việc xác thực hóa đơn với component BusinessValidationSummary và tính năng theo dõi lịch sử phiên bản.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | **Dự án - Đại tu UI/UX & Luồng Auth:**<br>• Cập nhật UI/UX lớn trên toàn bộ ứng dụng<br>• Thiết kế lại Landing Page, Login và Register flows<br>• Tích hợp Tailwind CSS và Ant Design cho phong cách hiện đại | 16/03/2026 | 16/03/2026 |  |
| 3 | **Dự án - Tinh chỉnh Kiến trúc:**<br>• Tiếp tục tinh chỉnh kiến trúc backend cho hệ thống SmartInvoice Shield<br>• Tối ưu hóa phân phối tài nguyên cho các dịch vụ AWS | 17/03/2026 | 17/03/2026 |  |
| 4 | **Dự án - Xác thực Business & UX:**<br>• Xây dựng component BusinessValidationSummary hiển thị lỗi hóa đơn<br>• Tối ưu UI Chi tiết hóa đơn: Gộp tab "Kiểm tra" và "Rủi ro" thành tab "Kết quả kiểm tra"<br>• Tích hợp Quản lý Phiên bản và Banner cảnh báo hóa đơn bị thay thế<br>• Cải thiện UX: Ẩn ErrorCode kỹ thuật; Fix bug hiển thị trạng thái và casing JSON | 18/03/2026 | 18/03/2026 |  |
| 5 | **Dự án - Tối ưu Hạ tầng AWS:**<br>• Hoàn tất thiết kế Event-Driven Architecture tối ưu chi phí trên AWS<br>• Tích hợp Amazon SQS để xử lý OCR và VietQR bất đồng bộ<br>• Cấu hình bảo mật và monitoring: SSL/TLS (ACM), Route 53 và CloudWatch Alarms | 19/03/2026 | 19/03/2026 |  |
| 6 | **Dự án - Refactor AI Container (Fargate):**<br>• Xử lý lỗi thiếu thư viện CUDA (libcublas.so) trong container<br>• Chuyển đổi Dockerfile OCR từ GPU (8GB) sang CPU-only (1.5GB)<br>• Sử dụng paddlepaddle và torch bản CPU-only để tương thích 100% với AWS Fargate | 20/03/2026 | 20/03/2026 |  |
| 7 | **Dự án - Phân tách OCR & Đồng bộ Validation:**<br>• Fix lỗi Python OCR trả về dữ liệu bị lỗi định dạng cho C#<br>• Giải quyết bug "Thoát sớm" trong InvoiceProcessorService.cs để ghi nhận đầy đủ lỗi<br>• Sửa lỗi hiển thị "Tổng tiền 0 VND" trên frontend và thêm cảnh báo thiếu XML | 21/03/2026 | 21/03/2026 |  |

### Tuần 10 Kết quả đạt được:

* Giảm đáng kể kích thước container AI (từ 8GB xuống 1.5GB) giúp triển khai Fargate hiệu quả.
* Tích hợp thành công xử lý bất đồng bộ qua SQS cho các luồng OCR và VietQR để giải quyết nút thắt cổ chai về hiệu suất.
* Cải thiện độ chính xác dữ liệu bằng cách khắc phục các sai lệch trong phân tách OCR và tinh chỉnh logic xác thực backend.
