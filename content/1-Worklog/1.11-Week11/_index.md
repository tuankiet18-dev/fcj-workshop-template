---
title: "Week 11 Worklog"
date: 2026-01-01
weight: 11
chapter: false
---

### Week 11 Objectives:

* UI/UX Overhaul: Landing Page, Login, Register flows.
* Integration of Tailwind CSS and Ant Design.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - FCJ Project - UI/UX Overhaul &amp; Authentication Flows<br>	- Committed major UI/UX updates across the application.<br>	- Redesigned and implemented the Landing Page, Login, and Register flows.<br>	- Integrated Tailwind CSS and Ant Design for modern styling and component rendering. | 16/03/2026 | 16/03/2026 |  |
| 3 | - FCJ Project - Architecture Refinement &amp; AWS Optimization<br>	- Continued refinement of the backend architecture for the SmartInvoice Shield. | 17/03/2026 | 17/03/2026 |  |
| 4 | • Xây dựng component BusinessValidationSummary hiển thị lỗi hóa đơn<br>• Tối ưu UI Chi tiết hóa đơn: Gộp tab &quot;Kiểm tra&quot; và &quot;Rủi ro&quot; thành tab &quot;Kết quả kiểm tra&quot;.<br>• Tích hợp tính năng Quản lý Phiên bản (Version History Dropdown) và Banner cảnh báo hóa đơn bị thay thế.<br>• Cải thiện UX: Ẩn các mã lỗi kỹ thuật thô (ErrorCode) khỏi giao diện người dùng.<br>• Fix bug Frontend: Xử lý lỗi hiển thị sai trạng thái (Xanh toàn bộ) do bất đồng Casing JSON và thiếu logic quét ValidationLayers.<br>• Tách tiêu chí kiểm tra &quot;Trùng lặp hóa đơn&quot; thành một rule độc lập trên UI.<br>• Fix bug Backend: Gỡ bỏ logic &quot;Thoát sớm&quot; (Early Return) để hệ thống bắt trọn vẹn tất cả lỗi (bao gồm lỗi lệch tiền dung sai).<br>• Viết API mới GET /api/invoices/{id}/versions phục vụ truy xuất lịch sử hóa đơn. | 18/03/2026 | 18/03/2026 |  |
| 5 | - FCJ Project - AWS Architecture &amp; Infrastructure Optimization<br>	- Finalized the cost-optimized AWS architecture design (Event-Driven Architecture).<br>	- Integrated Amazon SQS for asynchronous queue processing (OCR and VietQR) to resolve bottlenecks during heavy invoice upload loads.<br>	- Configured security and monitoring layers: SSL/TLS via ACM, Route 53, and established CloudWatch Alarms alongside AWS Budgets. | 19/03/2026 | 19/03/2026 |  |
| 6 | - FCJ Project - AI Container Refactoring for AWS Fargate<br>	- Resolved the missing CUDA dynamic library (libcublas.so) error in the container environment.<br>	- Refactored the OCR module&#x27;s Dockerfile: Migrated from a heavy GPU base image (nvidia/cuda ~8GB) to a lightweight CPU base image (python:3.10-slim ~1.5GB) to ensure 100% compatibility with the AWS Fargate Serverless environment.<br>	- Switched paddlepaddle and torch packages to their CPU-only versions and configured the web server to run gunicorn instead of the default Flask dev server. | 20/03/2026 | 20/03/2026 |  |
| 7 | - FCJ Project - OCR Data Parsing &amp; Validation Sync<br>	- Fixed the Python OCR issue returning corrupted stringified dictionaries for text fields, standardizing the JSON response format for C#.<br>	- Backend: Resolved the early exit (return false;) bug in InvoiceProcessorService.cs to ensure the system scans and records all validation errors for an invoice.<br>	- Frontend: Fixed the &quot;Total amount 0 VND&quot; display error on the BusinessValidationSummary.tsx component by correctly mapping the nested JSON object paths from the OCR flow. Added a &quot;Missing original XML file&quot; warning for OCR results. | 21/03/2026 | 21/03/2026 |  |
| 2 | - FCJ Project - OCR Pipeline Latency Tuning &amp; Edge Case Handling<br>	- AI Optimization: Improved the run_full_pipeline workflow in Python: Bypassed the local PaddleOCR/VietOCR execution when Gemini Vision is active, significantly reducing invoice processing latency from ~45s down to ~18.8s.<br>	- Backend: Fixed the math discrepancy False Positive error caused by C# reading Raw data instead of the cleaned ExtractedData.<br>	- Backend: Added &quot;Auto-interpolation&quot; logic to calculate Line Tax if the AI returns 0 VND but provides a tax rate percentage and the total line amount.<br>	- Fullstack: Addressed the &quot;Ghost Bug&quot; (404 Not Found) when uploading duplicate files. Implemented the &quot;Read-then-Destroy&quot; technique (Backend retains Failed/Draft status -&gt; Frontend displays the error -&gt; Frontend implicitly calls the API to hard-delete the garbage invoice).<br>	- Frontend: Fixed the issue where image/PDF files failed to display on OcrReviewModal.tsx by implementing fallback logic for GetVisualFileUrlAsync in C# and optimizing the iframe/img rendering in React. | 22/03/2026 | 22/03/2026 |  |

### Week 11 Achievements:

* Completed the planned tasks for the week.
* Gained deeper understanding of the integrated AWS services.
