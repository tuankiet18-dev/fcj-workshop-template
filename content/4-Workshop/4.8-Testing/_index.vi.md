---
title: "Kiểm tra Tổng thể"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 4.8. </b> "
---

Sau khi hoàn thành tất cả các bước triển khai, thực hiện các bài kiểm tra sau để xác minh toàn bộ hệ thống hoạt động đúng.

---

## Bảng Kiểm tra

| STT | Kiểm tra | Kết quả mong đợi |
|---|---|---|
| 1 | Truy cập Frontend (Amplify URL) | Trang Login hiển thị đúng |
| 2 | Đăng ký tài khoản mới | Nhận email OTP; tạo tài khoản thành công |
| 3 | Đăng nhập | Vào được Dashboard |
| 4 | Upload hóa đơn (ảnh/PDF) | Status chuyển từ **Processing** → **Draft** |
| 5 | Xem chi tiết hóa đơn | Các trường (MST, Ngày, Tiền) được điền đúng |
| 6 | Kiểm tra RiskLevel | Hiển thị cảnh báo rủi ro (nếu có) |

---

## Các Bước Kiểm tra Chi tiết

### 1. Truy cập Frontend

- Mở URL Amplify app trên trình duyệt.
- Form đăng nhập phải hiển thị. Không có lỗi console.

### 2. Đăng ký & Đăng nhập

- Click **Đăng ký**, điền email và mật khẩu.
- Kiểm tra email để lấy mã OTP/xác thực.
- Hoàn thành đăng ký và đăng nhập.

### 3. Upload Hóa đơn

- Từ Dashboard, click **Tải lên Hóa đơn**.
- Chọn file PDF hoặc ảnh hóa đơn mẫu.
- Hóa đơn phải xuất hiện trong danh sách với status **Processing**.
- Sau khoảng 30–90 giây, status phải chuyển thành **Draft** với dữ liệu đã được trích xuất.

### 4. Chi tiết Hóa đơn

- Click vào hóa đơn để mở trang chi tiết.
- Kiểm tra các trường sau đã được điền:
  - Mã số thuế (Tax ID)
  - Ngày hóa đơn
  - Tổng tiền
  - Tên người bán/người mua

### 5. Xác nhận Hóa đơn

- Từ hóa đơn ở trạng thái `Draft`, click **Merge / Xác nhận**.
- Kiểm tra status hóa đơn chuyển sang `Confirmed` hoặc `Merged`.

---

## Kiểm tra Health của Backend

Bạn cũng có thể kiểm tra backend trực tiếp qua CloudFront:

```bash
curl https://<CLOUDFRONT_DOMAIN>/api/health
# Kết quả mong đợi: {"status":"Healthy"}
```

Và OCR internal health check (qua ECS Exec hoặc test từ Backend):

```bash
curl http://<ALB_OCR_DNS>/api/v1/health
# Kết quả mong đợi: {"status":"ok"}
```

---

## Xử lý Sự cố Thường gặp

| Vấn đề | Nguyên nhân có thể | Giải pháp |
|---|---|---|
| Hóa đơn bị kẹt ở `Processing` | ECS tasks OCR không chạy | Kiểm tra ECS service → Tasks; xem CloudWatch logs |
| 502 Bad Gateway từ CloudFront | Backend EB environment không khỏe | Kiểm tra trang health của EB environment |
| Đăng nhập thất bại | Cấu hình Cognito sai | Kiểm tra `COGNITO_CLIENT_ID` và `COGNITO_CLIENT_SECRET` trong SSM |
| Dữ liệu hóa đơn rỗng sau OCR | Lỗi model path hoặc thiếu env vars | Kiểm tra log `/ecs/smartinvoice-ocr-task` trên CloudWatch |
