---
title: "Week 10 Worklog"
date: 2026-01-01
weight: 10
chapter: false
---

### Week 10 Objectives:

* AWS S3 Integration in .NET.
* Backend Refactoring and Dependency Injection.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - FCJ Project - Authorization &amp; UI/UX<br>	- Triển khai Role-Based Access Control (RBAC) cho AppLayout và hệ thống routing ở frontend.<br>	- Thực thi Data Isolation (cô lập dữ liệu) cho các thành viên (Member) trên trang Dashboard và Validation.<br>	- Refactor lại các message báo lỗi validation từ backend để rõ ràng hơn.<br>	- Cải thiện giao diện trang UploadInvoice và tính năng row selection. | 09/03/2026 | 09/03/2026 |  |
| 3 | - FCJ Project - System Architecture Configuration &amp; Bug Fixing<br>	- Configured system settings for the Super Admin panel.<br>	- Set up environment configurations for AI/OCR, Validation, AWS/Storage, and Security modules.<br>	- Investigated and resolved a PostgreSQL foreign key constraint error related to system configuration updates. | 10/03/2026 | 10/03/2026 |  |
| 4 | - FCJ Project - AI OCR Integration &amp; Business Logic Validation<br>	- Integrated AI OCR JSON output into the system.<br>	- Defined and mapped out the data processing plan for extracted information.<br>	- Implemented data extraction and validated business logic specifically for image and PDF invoice uploads. | 11/03/2026 | 11/03/2026 |  |
| 5 | - FCJ Project - Asynchronous Processing Implementation (AWS SQS)<br>	- Designed and implemented an asynchronous validation flow using AWS SQS to mitigate API timeout issues.<br>	- Applied the SQS Producer-Consumer pattern for message queuing.<br>	- Configured Polly policies for resilience and fault tolerance.<br>	- Implemented SemaphoreSlim to manage and control concurrent processing. | 12/03/2026 | 12/03/2026 |  |
| 6 | - FCJ Project - Frontend UX for Asynchronous Flow (Phase 1)<br>	- Developed Phase 1 of the Frontend UX supporting the new asynchronous validation processes.<br>	- Implemented smart polling mechanisms to fetch validation results efficiently.<br>	- Added dynamic visual indicators to display real-time validation status to the end-user. | 13/03/2026 | 13/03/2026 |  |
| 7 | - FCJ Project - Codebase Refactoring &amp; Data Merging Logic<br>	- Conducted major code refactoring across the backend services.<br>	- Implemented the complex logic for &quot;Invoice Dossier Merge&quot;, ensuring XML data accurately overrides OCR data when conflicts arise.<br>	- Performed general code cleanup to improve overall maintainability. | 14/03/2026 | 14/03/2026 |  |

### Week 10 Achievements:

* Completed the planned tasks for the week.
* Gained deeper understanding of the integrated AWS services.
