---
title: "Week 4 Worklog"
date: 2026-01-01
weight: 4
chapter: false
---

### Week 4 Objectives:

* Research and standardize XML data according to Tax Authority regulations to build the project's business foundation.
* Develop and test core backend features (XML validation and parsing) using real-world invoice data.
* Automate file storage processes on AWS S3 using Python Code (Boto3).
* Stay updated with the latest AI/ML trends and solutions from the AWS re:Invent Recap event to support project development.
* Optimize system security using AWS Systems Manager and implement invoice anti-spoofing features.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **• AWS Lab (Web Servers):** Deployed a LAMP Stack on EC2; resolved package compatibility issues between AL2 and AL2023; deployed a Node.js application and configured Inbound Rules for port 5000.<br>**• Project (Analysis):** Drafted the System Context Diagram; researched official XML Schema Definition (XSD) from the Tax Authority. | 26/01/2026 | 26/01/2026 |  |
| 3 | **• Backend Development (MVP) – XML Validation:** Developed the XML validation module using C#/.NET; refined the XSD file to handle “Ambiguous Content Model” errors, supporting diverse invoice formats.<br>**• Testing:** Ran unit tests with real-world data (FPT University tuition invoices); verified parser for complex XML structures. | 27/01/2026 | 27/01/2026 |  |
| 4 | **• Project (Compliance):** Implemented risk logic based on Decision 1510/QĐ-TCT; separated processing flows for VAT and Sales invoices.<br>**• AWS Lab (S3 Automation):** Used Python (boto3) for programmatic S3 uploads; configured IAM Access and Secret Keys. | 28/01/2026 | 28/01/2026 | <https://000048.awsstudygroup.com/> |
| 5 | **• Professional Development:** Attended AWS re:Invent Recap in HCMC to gather AI/ML insights for the project.<br>**• Key Takeaways:** Explored Amazon SageMaker Unified Studio, Amazon S3 Tables, and Vector Embeddings for semantic search. | 29/01/2026 | 29/01/2026 |  |
| 6 | **• Development (C#):** Implemented anti-spoofing; added machine-generated invoice detection; fixed XML Namespace parsing errors.<br>**• AWS Lab:** Used AWS Systems Manager (Session Manager) for secure instance access; troubleshot Node.js DB connection issues. | 30/01/2026 | 30/01/2026 |  |

### Week 4 Achievements:

* Successfully deployed web servers on AL2023 and mastered AWS secure system administration tools.
* Finalized the XML processing module with accurate validation and flexibility based on Tax Authority XSD standards.
* Integrated invoice risk classification logic into the system, ensuring compliance with current electronic invoice regulations.
* Mastered S3 storage automation using Python/Boto3 and integrated new AI technology insights into the project roadmap.
* Completed anti-spoofing and machine-generated invoice detection features, fully resolving technical XML issues.
