---
title: "Week 10 Worklog"
date: 2026-01-01
weight: 10
chapter: false
---

### Week 10 Objectives:

* Perform a major UI/UX overhaul using Tailwind CSS and Ant Design to modernize the application's interface.
* Refactor the AI OCR processing pipeline for high compatibility with AWS Fargate Serverless (CPU-only migration).
* Enhance invoice validation transparency with the BusinessValidationSummary component and version history tracking.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **Project - UI/UX Overhaul & Auth Flows:**<br>• Execute major UI/UX updates across the entire application<br>• Redesign and implement Landing Page, Login, and Register flows<br>• Integrate Tailwind CSS and Ant Design for modern styling | 16/03/2026 | 16/03/2026 |  |
| 3 | **Project - Architecture Refinement:**<br>• Refine backend architecture for SmartInvoice Shield<br>• Optimize resource allocation for AWS services | 17/03/2026 | 17/03/2026 |  |
| 4 | **Project - Business Validation & UX:**<br>• Build BusinessValidationSummary component for detailed error display<br>• Merge "Check" and "Risk" tabs into a unified "Validation Results" tab<br>• Integrate Version History and warning banners for replaced invoices<br>• Hide raw ErrorCodes and fix JSON casing discrepancies in frontend | 18/03/2026 | 18/03/2026 |  |
| 5 | **Project - AWS Infra Optimization:**<br>• Finalize cost-optimized Event-Driven Architecture<br>• Integrate Amazon SQS for asynchronous OCR and VietQR processing<br>• Configure SSL/TLS (ACM), Route 53, and CloudWatch Alarms | 19/03/2026 | 19/03/2026 |  |
| 6 | **Project - AI Container Refactoring (Fargate):**<br>• Resolve libcublas.so missing library errors in container<br>• Migrate OCR Dockerfile from GPU (8GB) to CPU-only base image (1.5GB)<br>• Switch to CPU-only paddlepaddle/torch for 100% Fargate compatibility | 20/03/2026 | 20/03/2026 |  |
| 7 | **Project - OCR Parsing & Validation Sync:**<br>• Fix corrupted stringified dictionaries in Python OCR output<br>• Resolve early-exit bug in InvoiceProcessorService.cs to ensure full reporting<br>• Fix "Total amount 0 VND" display error and add missing XML warnings | 21/03/2026 | 21/03/2026 |  |

### Week 10 Achievements:

* Dramatically reduced AI container size (from 8GB to 1.5GB) ensuring efficient Fargate deployment.
* Successfully integrated asynchronous SQS processing for OCR and VietQR flows to resolve performance bottlenecks.
* Improved data accuracy by resolving OCR parsing discrepancies and refining backend validation logic.
