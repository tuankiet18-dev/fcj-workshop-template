---
title: "Tuần 12 Báo cáo công việc"
date: 2026-03-29
weight: 12
chapter: false
---

### Mục tiêu Tuần 12:

- **Tối ưu hóa cơ sở hạ tầng**: Di chuyển các giao tiếp dịch vụ OCR sang AWS Cloud Map (Service Discovery) và cải thiện độ tin cậy của ECS.
- **Xây dựng tài liệu hệ thống**: Phát triển Đặc tả yêu cầu phần mềm (SRS) chuyên nghiệp cho dự án SmartInvoice Shield.
- **Quản lý danh mục thực tập**: Chuẩn hóa và đánh số lại danh mục thực tập dựa trên Hugo để tổ chức nội dung tốt hơn.

### Các công việc được thực hiện trong tuần này:

| Ngày | Công việc                                                                                                                                                                                                                                     | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------ |
| 1    | **Dự án - Ổn định OCR Pipeline:**<br>• Cấu hình dự phòng LayoutLMv3 cho giới hạn Gemini API (lỗi 429)<br>• Tối ưu hóa tệp định nghĩa ECS (ECS Task definition) với safetensors và tăng dung lượng bộ nhớ.                                     | 30/03/2026   | 30/03/2026      |                    |
| 2    | **Dự án - Kiến trúc AWS & Đồng bộ hóa:**<br>• Di chuyển giao tiếp OCR từ Internal ALB sang AWS Cloud Map (Service Discovery)<br>• Giải quyết vấn đề đồng bộ OcrWorkerService, khắc phục lỗi xóa draft gây lỗi giao diện người dùng.           | 31/03/2026   | 31/03/2026      |                    |
| 3    | **Tài liệu - Danh mục & Sự kiện:**<br>• Tái cấu trúc trang web thực tập (loại bỏ BlogsTranslated, đánh số lại các phần nội dung)<br>• Hoàn thành báo cáo sự kiện "AWS re:Invent Recap HCMC 2026"<br>• Bản thảo tài liệu Tự đánh giá thực tập. | 01/04/2026   | 01/04/2026      |                    |
| 4    | **Tài liệu - Soạn thảo SRS:**<br>• Soạn thảo SRS toàn diện theo tiêu chuẩn IEEE 830-1998 cho SmartInvoice Shield<br>• Tích hợp các yêu cầu pháp lý của Việt Nam (Thông tư 78/2021/TT-BTC)                                                     | 02/04/2026   | 02/04/2026      |                    |
| 5    | **Dự án - Docker & Đề án:**<br>• Tối ưu hóa Docker Compose cho môi trường local; Khắc phục lỗi Cognito và cấu hình mạng<br>• Cập nhật đề án SmartInvoice với quy định hóa đơn điện tử (Thông tư 78) và cấu trúc XML.                | 03/04/2026   | 03/04/2026      |                    |
| 6    | **Triển khai - AWS Deployment:**<br>• Triển khai backend lên AWS Elastic Beanstalk; Cấu hình RDS Security Groups và SSM Parameter Store<br>• Tích hợp và kiểm thử SQS OCR pipeline trong môi trường Docker local.                   | 04/04/2026   | 04/04/2026      |                    |
| 7    | **Nghiên cứu - Bảo mật & Tối ưu hóa:**<br>• Nghiên cứu cơ chế xác thực tập trung và tối ưu hóa chi phí vận hành AWS Free Tier<br>• Chuẩn bị kế hoạch xử lý lỗi nghiêm trọng cho dữ liệu OCR.                                       | 05/04/2026   | 05/04/2026      |                    |

### Thành tựu Tuần 12:

- **Sẵn sàng triển khai**: Hoàn tất cấu hình Docker local và triển khai thành công lên AWS Beanstalk, thiết lập nền tảng serverless ổn định.
- **Tuân thủ pháp lý**: Đề án và tài liệu SRS được cập nhật đầy đủ các yêu cầu từ Thông tư 78/2021/TT-BTC về hóa đơn điện tử.
- **Tài liệu hợp lý**: Cải thiện khả năng đọc và giao diện chuyên nghiệp của tài liệu báo cáo thực tập.
