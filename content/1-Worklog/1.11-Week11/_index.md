---
title: "Week 11 Worklog"
date: 2026-01-01
weight: 11
chapter: false
---

### Week 11 Objectives:

* Optimize the full-stack OCR pipeline to support high-volume parallel batch processing and reduce end-to-end latency.
* Implement robust infrastructure scaling and resilience mechanisms, specifically targeting AI API rate limits and memory-intensive fallback scenarios.
* Resolve critical synchronization and connectivity bugs within the concurrent upload and polling systems.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **Project - OCR Latency & Edge Cases:**<br>• Reduce latency from 45s to 18.8s by bypassing local OCR when Gemini is active<br>• Fix math discrepancies in C# logic and implement "Auto-interpolation" for missing tax data<br>• Implement "Read-then-Destroy" for Ghost Bug (404) and fix OcrReviewModal display | 23/03/2026 | 23/03/2026 |  |
| 3 | **Project - Batch Processing & Optimization:**<br>• Rewrite upload flow for concurrent uploads using Promise.all() and semaphores<br>• Implement Smart Polling with 15s initial delay and 5s intervals<br>• Refactor Worker Service to prevent "greediness" and local RAM pressure | 24/03/2026 | 24/03/2026 |  |
| 4 | **Project - Scaling & AI Resilience:**<br>• Reconfigure CloudWatch alarms for precise SQS-based Auto Scaling<br>• Resolve Gemini 429 rate limit issues and fix OOM failures during local AI fallback<br>• Upgrade ECS Fargate tasks to 2 vCPU / 8 GB RAM and perform zero-downtime rollout | 25/03/2026 | 25/03/2026 |  |
| 5 | **Project - Batch Upload Reliability:**<br>• Fix net::ERR_CONNECTION_REFUSED by tuning uploadSemaphore limits<br>• Refactor polling logic to be independent per invoice (removing blocking loops)<br>• Sync Worker timeouts (300s) with SQS Visibility Timeout for heavy AI tasks | 26/03/2026 | 26/03/2026 |  |
| 6 | **Project - Pipeline Performance:**<br>• Transition all frontend polling to parallel execution via Promise.all()<br>• Increase upload bandwidth utilization (max: 5 concurrent streams)<br>• Implement resumePollingForInvoice recovery mechanism for browser refreshes | 27/03/2026 | 27/03/2026 |  |
| 7 | **Project - Infrastructure & Local AI:**<br>• Configure Step Scaling Policies for ECS Fargate based on SQS queue depth<br>• Debug and fix LayoutLMv3 model loading paths within Docker containers<br>• Verify AI Fallback resilience during simulated 429 quota exhaustion | 28/03/2026 | 28/03/2026 |  |

### Week 11 Achievements:

* Successfully reduced average processing latency from 45s to 18.8s by optimizing the AI orchestration workflow.
* Stabilized the production environment with dynamic ECS scaling policies and enhanced worker resilience (5-minute keep-alive).
* Validated a zero-interruption AI fallback mechanism that handles Gemini API quota exhaustion by gracefully switching to local models.
