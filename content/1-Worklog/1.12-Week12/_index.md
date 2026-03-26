---
title: "Week 12 Worklog"
date: 2026-01-01
weight: 12
chapter: false
---

### Week 12 Objectives:

* Asynchronous Processing: AWS SQS integration.
* Frontend UX for async flows and smart polling.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
|  | Worklog — 23/03/2026<br><br>Main goal: Run real-world tests for high-volume invoice batch processing and optimize the Frontend–Backend architecture.<br><br>- Frontend optimization (UploadInvoice.tsx) &amp; network bottleneck handling<br>	- Identified why Auto Scaling was not kicking in: the frontend was uploading files sequentially, so SQS could not build up a queue.<br>	- Rewrote the upload flow to run concurrent uploads using Promise.all() plus a semaphore-based chunking mechanism, limiting to a maximum of 4 parallel connections to avoid hitting the browser connection limit.<br>	- Implemented Smart Polling:<br>		- Added a 15-second delay before the first OCR status check.<br>		- Increased the polling interval to 5 seconds to reduce noisy SELECT queries against the database.<br><br>- Backend worker flow refactor (OcrWorkerService.cs)<br>	- Fixed the worker “greediness” by lowering MaxNumberOfMessages from 10 to 2 so messages are released back to SQS more fairly.<br>	- Controlled in-container parallelism with SemaphoreSlim(2, 2) to prevent local RAM pressure and reduce timeouts (over 180 seconds) on the first file during cold start. | 23/03/2026 | 23/03/2026 |  |
|  | Worklog — 24/03/2026<br><br>Main goal: Debug the OCR pipeline via AWS logs, address out-of-memory (OOM) issues during AI fallback, and upgrade AWS ECS Fargate configuration.<br><br>- CloudWatch alarms &amp; Auto Scaling adjustments<br>	- Investigated desynchronization between SQS depth and ECS Auto Scaling.<br>	- Reconfigured the CloudWatch alarm to trigger when ApproximateNumberOfMessagesVisible &gt;= 2 for 1 minute, so scaling matches the worker throughput and ECS spins up additional tasks at the right time.<br><br>- AI API incident (Gemini rate limit &amp; fallback OOM)<br>	- Traced logs in Elastic Beanstalk and ECS and confirmed the system hit the free quota limit for the Gemini API (HTTP 429 RESOURCE_EXHAUSTED).<br>	- Fixed the cascading failures (HTTP 500, 504 Gateway Timeout) when automatically falling back to the internal AI models (LayoutLMv3 + PaddleOCR).<br>		- Root cause: the internal model consumed too many resources and caused memory overflow (for example: PreconditionNotMetError: Tensor&#x27;s dimension is out of bound).<br><br>- AWS ECS Fargate infrastructure upgrade<br>	- Created a new revision of the task definition for smartinvoice-ocr-task.<br>	- Increased the task size from 1 vCPU / 2 GB RAM to 2 vCPU / 8 GB RAM to handle heavy image-matrix computation for the internal AI.<br>	- Removed container-level “virtual” limits (cleared Memory hard limit and Memory soft limit) to allow the OCR process to use the full allocated resources.<br>	- Rolled out the service update (rolling update) successfully without downtime. | 24/03/2026 | 24/03/2026 |  |

### Week 12 Achievements:

* Completed the planned tasks for the week.
* Gained deeper understanding of the integrated AWS services.
