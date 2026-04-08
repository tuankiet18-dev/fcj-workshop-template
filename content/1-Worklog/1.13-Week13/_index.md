---
title: "Week 13 Worklog"
date: 2026-04-06
weight: 13
chapter: false
---

### Week 13 Objectives:

- **Data Integrity**: Implement robust error handling for invoice processing to prevent database corruption.
- **Security & Compliance**: Finalize Gemini API credential management and ensure secure storage of sensitive data.
- **Project Refinement**: Address remaining UI/UX glitches and streamline the end-to-end invoice ingestion flow.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                     | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ------------------ |
| 1   | **Project - Fatal Error Handling:**<br>• Implemented strict fatal error handling for OCR/XML pipelines (duplicates, MST mismatches)<br>• Developed "Hard Delete" mechanism for invalid S3 files and database records.       | 06/04/2026 | 06/04/2026      |                    |
| 2   | **Project - Audit Log Persistence:**<br>• Denormalized CompanyId and InvoiceNumber into InvoiceAuditLog for data integrity.<br>• Updated AuditLogController to filter by CompanyId independently of the Invoice table.<br>• Fixed UI to show persistent invoice numbers and friendly Vietnamese labels after deletion.<br>• Cleaned up repository (bin/obj/pycache) to resolve GitHub LFS CI/CD issues. | 07/04/2026 | 07/04/2026 |                    |


### Week 13 Achievements:

- **Robust Ingestion**: Established a fail-safe mechanism that ensures only valid, non-duplicate invoices are persisted in the system.
- **Audit Persistence**: Ensured critical invoice lifecycle logs are preserved and searchable even after hard deletion of the associated records.
