---
title: "Week 9 Worklog"
date: 2026-01-01
weight: 9
chapter: false
---

### Week 9 Objectives:

* Implement security layers including Frontend RBAC and Data Isolation for project members.
* Architect and deploy an asynchronous processing pipeline using AWS SQS to handle high-latency OCR and validation tasks.
* Develop complex data merging logic ("Invoice Dossier Merge") to synchronize XML and AI-extracted invoice data.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **Project - Authorization & UI/UX:**<br>• Implement Role-Based Access Control (RBAC) for AppLayout and frontend routing<br>• Enforce Data Isolation for members on Dashboard and Validation pages<br>• Refactor backend validation error messages for clarity<br>• Improve UploadInvoice UI and row selection features | 09/03/2026 | 09/03/2026 |  |
| 3 | **Project - Architecture & Bug Fixing:**<br>• Configure system settings for the Super Admin panel<br>• Set up environment configs for AI/OCR, Validation, S3, and Security<br>• Investigate and resolve PostgreSQL foreign key constraint errors | 10/03/2026 | 10/03/2026 |  |
| 4 | **Project - AI OCR & Validation:**<br>• Integrate AI OCR JSON output into the system<br>• Map out data processing plan for extracted information<br>• Implement data extraction and validate business logic for image/PDF uploads | 11/03/2026 | 11/03/2026 |  |
| 5 | **Project - Async Processing (AWS SQS):**<br>• Design and implement async validation flow using AWS SQS to mitigate timeouts<br>• Apply SQS Producer-Consumer pattern and Polly policies for resilience<br>• Use SemaphoreSlim to manage concurrent processing | 12/03/2026 | 12/03/2026 |  |
| 6 | **Project - Frontend Async UX:**<br>• Develop Phase 1 of Frontend UX for asynchronous validation<br>• Implement smart polling mechanisms and real-time status indicators | 13/03/2026 | 13/03/2026 |  |
| 7 | **Project - Refactoring & Data Merge:**<br>• Major backend service refactoring and code cleanup<br>• Implement "Invoice Dossier Merge" (XML accurately overrides OCR data) | 14/03/2026 | 14/03/2026 |  |

### Week 9 Achievements:

* Successfully mitigated API timeout issues by transitioning to a resilient SQS-based asynchronous architecture.
* Enhanced the user experience with real-time status indicators and smart polling mechanisms for batch processing.
* Strengthened system security and data integrity through RBAC, isolation, and robust error handling.
