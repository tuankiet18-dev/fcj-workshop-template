---
title: "Tuần 12 Báo cáo công việc"
date: 2026-01-01
weight: 12
chapter: false
---

### Tuần 12 Mục tiêu:

* Xử lý Bất đồng bộ: Tích hợp AWS SQS.
* UI/UX Frontend cho luồng async và smart polling.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | **Dự án - Tối ưu Frontend & Mạng:**<br>• Tải lên đồng thời qua Promise.all và kiểm soát semaphore<br>• Triển khai Smart Polling với trễ 15s và chu kỳ 5s<br><br>**Dự án - Refactor Backend Worker:**<br>• Hạ MaxNumberOfMessages trong SQS để phân phối công bằng<br>• Giới hạn song song trong container bằng SemaphoreSlim(2, 2) | 23/03/2026 | 23/03/2026 |  |
| 3 | **Dự án - CloudWatch & ECS Scaling:**<br>• Đồng bộ hóa độ sâu SQS và cảnh báo ECS Auto Scaling<br>• Cấu hình cảnh báo CloudWatch cho VisibleMessages >= 2<br><br>**Dự án - AI Fallback & Nâng cấp ECS:**<br>• Theo dõi và xử lý giới hạn Gemini (HTTP 429) & lỗi OOM fallback<br>• Nâng cấp cấu hình ECS task lên 2 vCPU / 8 GB RAM<br>• Triển khai cập nhật dịch vụ zero-downtime thành công | 24/03/2026 | 24/03/2026 |  |

### Tuần 12 Kết quả đạt được:

* Hoàn thành các công việc đã đề ra trong tuần.
* Hiểu sâu hơn về các dịch vụ AWS đã thực hành.
