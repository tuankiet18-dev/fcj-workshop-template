---
title: "Tuần 13 Báo cáo công việc"
date: 2026-04-06
weight: 13
chapter: false
---

### Mục tiêu Tuần 13:

- **Toàn vẹn Dữ liệu**: Thực hiện xử lý lỗi nghiêm ngặt cho quy trình xử lý hóa đơn để ngăn chặn sai sót dữ liệu.
- **Bảo mật & Tuân thủ**: Hoàn tất quản lý thông tin xác thực Gemini API và đảm bảo lưu trữ an toàn các dữ liệu nhạy cảm.
- **Hoàn thiện Dự án**: Giải quyết các lỗi giao diện còn sót lại và tối ưu hóa luồng nạp hóa đơn đầu cuối.

### Các công việc được thực hiện trong tuần này:

| Ngày | Công việc                                                                                                                                                                                                                                     | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------ |
| 1    | **Dự án - Xử lý Lỗi Fatal:**<br>• Thực hiện xử lý lỗi Fatal nghiêm ngặt cho pipeline OCR/XML (lỗi trùng lặp, sai MST)<br>• Phát triển cơ chế "Hard Delete" cho các tệp S3 và bản ghi cơ sở dữ liệu không hợp lệ.                             | 06/04/2026   | 06/04/2026      |                    |
| 2    | **Dự án - Bảo toàn Nhật ký Audit:**<br>• Phi bình thường hóa CompanyId và InvoiceNumber vào bảng Log để bảo toàn dữ liệu khi xóa hóa đơn.<br>• Cập nhật AuditLogController để lọc Log theo CompanyId độc lập với bảng Invoice.<br>• Sửa giao diện hiển thị số hóa đơn vĩnh viễn và nhãn tiếng Việt (Xóa tạm, Khôi phục).<br>• Dọn dẹp repository (bin/obj/pycache) để khắc phục lỗi CI/CD LFS trên GitHub. | 07/04/2026   | 07/04/2026      |                    |


### Thành tựu Tuần 13:

- **Đầu vào Ổn định**: Thiết lập cơ chế fail-safe đảm bảo chỉ các hóa đơn hợp lệ và không trùng lặp mới được lưu trữ trong hệ thống.
- **Bảo toàn Audit**: Đảm bảo nhật ký vòng đời hóa đơn quan trọng được lưu giữ và có thể tra cứu ngay cả khi bản ghi hóa đơn liên quan đã bị xóa vĩnh viễn.
