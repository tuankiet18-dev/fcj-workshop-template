---
title: "Tuần 13 Báo cáo công việc"
date: 2026-04-06
weight: 13
chapter: false
---

### Mục tiêu Tuần 13:

- **Toàn vẹn Dữ liệu**: Thực hiện xử lý lỗi nghiêm ngặt cho quy trình xử lý hóa đơn để ngăn chặn sai sót dữ liệu.
- **Bảo mật & Tuân thủ**: Hoàn tất quản lý thông tin xác thực Gemini API và đảm bảo lưu trữ an toàn các dữ liệu nhạy cảm.
- **Phản biện Kiến trúc**: Chuẩn bị các kịch bản và kịch bản kỹ thuật phục vụ cho buổi thuyết trình bảo vệ kiến trúc dự án SmartInvoice Shield.

### Các công việc được thực hiện trong tuần này:

| Ngày | Công việc                                                                                                                                                                                                                                     | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------ |
| 2    | **Dự án - Xử lý Lỗi Fatal:**<br>• Thực hiện xử lý lỗi Fatal nghiêm ngặt cho pipeline OCR/XML (lỗi trùng lặp, sai MST)<br>• Phát triển cơ chế "Hard Delete" cho các tệp S3 và bản ghi cơ sở dữ liệu không hợp lệ.                             | 06/04/2026   | 06/04/2026      |                    |
| 3    | **Dự án - Bảo toàn Nhật ký Audit:**<br>• Phi bình thường hóa CompanyId và InvoiceNumber vào bảng Log để bảo toàn dữ liệu khi xóa hóa đơn.<br>• Cập nhật AuditLogController để lọc Log theo CompanyId độc lập với bảng Invoice.<br>• Sửa giao diện hiển thị số hóa đơn vĩnh viễn và nhãn tiếng Việt. | 07/04/2026   | 07/04/2026      |                    |
| 5    | **Dự án - Kịch bản Thuyết trình:**<br>• Viết kịch bản thuyết trình kỹ thuật dài 10 phút tập trung vào tương tác giữa các dịch vụ backend (Cognito, S3, SQS, RDS). | 09/04/2026 | 09/04/2026 | |
| 6    | **Dự án - Tương tác Thành phần:**<br>• Hoàn thiện logic xử lý hóa đơn nhiều mức thuế suất trong bộ phân giải XML và xác minh tính nhất quán với giao diện người dùng. | 10/04/2026 | 10/04/2026 | |

### Thành tựu Tuần 13:

- **Đầu vào Ổn định**: Thiết lập cơ chế fail-safe đảm bảo chỉ các hóa đơn hợp lệ và không trùng lặp mới được lưu trữ trong hệ thống.
- **Lộ trình Kỹ thuật**: Chốt xong nội dung thuyết trình tập trung vào khả năng mở rộng của hệ thống và các lựa chọn thiết kế kiến trúc.
