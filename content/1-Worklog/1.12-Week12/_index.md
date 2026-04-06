---
title: "Week 12 Worklog"
date: 2026-03-29
weight: 12
chapter: false
---

### Week 12 Objectives:

- **Infrastructure Optimization**: Migrate OCR service communication to AWS Cloud Map (Service Discovery) and improve ECS reliability.
- **System Documentation**: Develop a professional Software Requirements Specification (SRS) for the SmartInvoice Shield project.
- **Site Management**: Standardize and renumber the Hugo-based internship portfolio for better organization.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                     | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ------------------ |
| 1   | **Project - OCR Pipeline Stability:**<br>• Configure LayoutLMv3 fallback for Gemini API rate limits (429 errors)<br>• Optimize ECS Task definition with safetensors and increased memory                                 | 30/03/2026 | 30/03/2026      |                    |
| 2   | **Project - AWS Architecture & Sync:**<br>• Migrate OCR communication from Internal ALB to AWS Cloud Map (Service Discovery)<br>• Resolve OcrWorkerService sync issue where deleted drafts caused UI errors              | 31/03/2026 | 31/03/2026      |                    |
| 3   | **Documentation - Portfolio & Events:**<br>• Refactor internship site (removed BlogsTranslated, renumbered sections)<br>• Finalized "AWS re:Invent Recap HCMC 2026" event report<br>• Drafted Internship Self-Evaluation | 01/04/2026 | 01/04/2026      |                    |
| 4   | **Documentation - SRS Authoring:**<br>• Authored comprehensive IEEE 830-1998 SRS for SmartInvoice Shield<br>• Integrated Vietnamese legal requirements (Circular 78/2021/TT-BTC)                                         | 02/04/2026 | 02/04/2026      |                    |
| 5   | **Project - Docker & Proposal:**<br>• Optimized Docker Compose for local development; Fixed Cognito auth and network issues<br>• Updated SmartInvoice proposal with e-invoice regulations (Circular 78) and XML structure.      | 03/04/2026 | 03/04/2026      |                    |
| 6   | **Deployment - AWS Infrastructure:**<br>• Deployed backend to AWS Elastic Beanstalk; Configured RDS security groups and SSM Parameter Store<br>• Integrated and tested SQS OCR pipeline in local Docker.                         | 04/04/2026 | 04/04/2026      |                    |
| 7   | **Research - Security & Optimization:**<br>• Researched centralized authentication and AWS Free Tier cost optimization<br>• Prepared fatal error handling strategies for OCR data.                                               | 05/04/2026 | 05/04/2026      |                    |

### Week 12 Achievements:

- **Deployment Ready**: Successfully finalized local Docker configuration and AWS Beanstalk deployment, establishing a robust serverless foundation.
- **Regulatory Compliance**: Proposal and SRS documentation fully updated with Circular 78/2021/TT-BTC requirements for Vietnamese e-invoices.
- **Streamlined Portfolio**: Improved the readability and professional look of the internship documentation.
