---
title: "Tuần 11 Báo cáo công việc"
date: 2026-01-01
weight: 11
chapter: false
---

### Tuần 11 Mục tiêu:

* Tối ưu hóa quy trình OCR full-stack để hỗ trợ xử lý hàng loạt song song khối lượng lớn và giảm độ trễ đầu-cuối.
* Triển khai cơ chế mở rộng hạ tầng và khả năng phục hồi mạnh mẽ, đặc biệt nhắm vào giới hạn rate limit của AI API và các kịch bản fallback tiêu tốn bộ nhớ.
* Giải quyết các lỗi kết nối và đồng bộ hóa nghiêm trọng trong hệ thống upload và polling đồng thời.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | **Dự án - Độ trễ OCR & Các trường hợp biên:**<br>• Giảm độ trễ từ 45 giây xuống còn 18,8 giây bằng cách bỏ qua local OCR khi Gemini hoạt động<br>• Sửa lỗi sai lệch tính toán trong C# và triển khai "Tự động nội suy" cho dữ liệu thuế thiếu<br>• Triển khai "Read-then-Destroy" cho Ghost Bug (404) và sửa lỗi hiển thị OcrReviewModal | 23/03/2026 | 23/03/2026 |  |
| 3 | **Dự án - Xử lý Hàng loạt & Tối ưu hóa:**<br>• Viết lại luồng upload để xử lý song song qua Promise.all() và semaphores<br>• Triển khai Smart Polling với trễ ban đầu 15 giây và chu kỳ 5 giây<br>• Refactor Worker Service để ngăn chặn sự "tham lam" và áp lực RAM tại local | 24/03/2026 | 24/03/2026 |  |
| 4 | **Dự án - Scaling & AI Resilience:**<br>• Cấu hình lại cảnh báo CloudWatch cho Auto Scaling dựa trên SQS chính xác<br>• Giải quyết lỗi giới hạn 429 của Gemini và fix lỗi OOM khi fallback về AI nội bộ<br>• Nâng cấp ECS Fargate lên 2 vCPU / 8 GB RAM và triển khai zero-downtime rollout | 25/03/2026 | 25/03/2026 |  |
| 5 | **Dự án - Tin cậy Upload Batch:**<br>• Sửa lỗi net::ERR_CONNECTION_REFUSED bằng cách tinh chỉnh giới hạn uploadSemaphore<br>• Refactor logic polling độc lập cho từng hóa đơn (loại bỏ vòng lặp chặn)<br>• Đồng bộ hóa timeout của Worker (300s) với SQS Visibility Timeout cho các tác vụ AI nặng | 26/03/2026 | 26/03/2026 |  |
| 6 | **Dự án - Hiệu năng Pipeline:**<br>• Chuyển toàn bộ polling frontend sang thực thi song song qua Promise.all()<br>• Tối đa hóa sử dụng băng thông upload (tối đa 5 luồng đồng thời)<br>• Triển khai cơ chế resumePollingForInvoice để khôi phục khi làm mới trình duyệt | 27/03/2026 | 27/03/2026 |  |
| 7 | **Dự án - Hạ tầng & AI Nội bộ:**<br>• Cấu hình Step Scaling Policies cho ECS Fargate dựa trên độ sâu hàng đợi SQS<br>• Debug và sửa đường dẫn tải mô hình LayoutLMv3 trong Docker containers<br>• Xác thực khả năng phục hồi fallback AI khi giả lập trạng thái cạn kiệt hạn ngạch 429 | 28/03/2026 | 28/03/2026 |  |

### Tuần 11 Kết quả đạt được:

* Giảm thành công độ trễ xử lý trung bình từ 45 giây xuống còn 18,8 giây bằng cách tối ưu hóa luồng điều phối AI.
* Ổn định môi trường sản xuất với các chính sách scaling ECS linh hoạt và tăng cường khả năng phục hồi của worker (timeout 5 phút).
* Xác thực thành công cơ chế fallback AI không gián đoạn, xử lý tình trạng cạn kiệt hạn ngạch Gemini API bằng cách chuyển sang các mô hình local một cách mượt mà.
