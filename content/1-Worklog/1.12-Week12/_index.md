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
| 2 | **Project - Frontend Optimization & Network:**<br>• Concurrent uploads via Promise.all and semaphore control<br>• Implement Smart Polling with 5s delay and 5s intervals<br><br>**Project - Backend Worker Refactor:**<br>• Lower MaxNumberOfMessages in SQS for fair distribution<br>• Limit in-container parallelism using SemaphoreSlim(2, 2) | 23/03/2026 | 23/03/2026 |  |
| 3 | **Project - CloudWatch & ECS Scaling:**<br>• Desynchronize SQS depth and ECS Auto Scaling alarms<br>• Reconfigure CloudWatch alarm to trigger for VisbileMessages >= 2<br><br>**Project - AI Fallback & ECS Upgrade:**<br>• Trace and fix Gemini rate limit (HTTP 429) & OOM fallback issues<br>• Upgrade ECS task size to 2 vCPU / 8 GB RAM<br>• Roll out zero-downtime service update | 24/03/2026 | 24/03/2026 |  |

### Week 12 Achievements:

* Completed the planned tasks for the week.
* Gained deeper understanding of the integrated AWS services.
