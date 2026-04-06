---
title: "Event 3"
date: 2026-04-04
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS First Cloud Journey (FCJ) AI

### EVENT PURPOSE

- Explore Cloud Native and AI technology trends within the AWS ecosystem.
- Learn about modern infrastructure management using Infrastructure as Code (IaC) and Container Orchestration.
- Study high-concurrency and fault-tolerant programming solutions for DevOps infrastructure with Elixir.
- Discuss cost and performance optimization when deploying large-scale systems.

### SPEAKER LIST

- **Thịnh Nguyễn** – Cloud Engineer Trainee at FCAJ, Swinburne Vietnam.
- **Bảo Huỳnh** – Junior Cloud Native Developer at Endava, Founder of iTea Lab.
- **Nguyễn Tạ Minh Triết** – R&D Member at iTea Lab, SAP Developer Intern at Bosch GSV.

### HIGHLIGHTS

#### Infrastructure as Code (IaC) with Terraform on AWS

- Comparison between IaC and "ClickOps", emphasizing automation and configuration-based management.
- Introduction to IaC tools on AWS: CloudFormation, CDK, and deep dive into Terraform.
- Real-world Terraform workflow: **Write -> Plan -> Apply** and State management mechanism.

#### Cloud Native Architecture with Kubernetes

- Addressing challenges in container orchestration.
- Deep dive into Kubernetes architecture: Control Plane, Worker Nodes, and core objects (Pods, Services, Deployments).
- Introduction to effective K8s operation tools: **Helm** and **K9S**.

#### Elixir - A Unified Solution for High-Performance DevOps Infrastructure

- Introduction to the Elixir language and the BEAM VM with its capability to handle millions of concurrent processes.
- Fault-tolerance mechanism with OTP (Open Telecom Platform).
- Impressive case study: Migrating from a Serverless architecture (Lambda/API Gateway) to Elixir reduced costs from $30,000 to approximately $400 per month.
- Elixir's application in the AI/ML ecosystem with Numerical Elixir (NX) and Livebook.

### LESSONS LEARNED

- **Infrastructure Mindset:** Using Terraform is essential to ensure consistency and reusability of AWS infrastructure.
- **Orchestration Skills:** Kubernetes is more than just a tool to run containers; it's an operating system for the Cloud, requiring a deep understanding of network and storage architectures.
- **Cost Optimization:** Serverless is not always the most cost-effective solution. Choosing the right language, like Elixir, can bring huge economic benefits to high-traffic systems.

### APPLICATION TO WORK

#### Upgrading SmartInvoice Shield

- **Terraform Implementation:** Use Terraform to manage all AWS resources for SmartInvoice (S3, SQS, RDS, Elastic Beanstalk), replacing manual configuration.
- **Containerize OCR Worker:** Consider moving the OCR worker to Kubernetes to leverage auto-scaling and self-healing for high-volume invoice processing.
- **Research Elixir for Ingestion Layer:** Evaluate using Elixir/Phoenix to build the invoice ingestion handler for emails/webhooks to handle extreme loads at low costs.

---

> **Summary:** The FCJ AI event provided deep insights into combining modern infrastructure management with optimal programming solutions to build robust Cloud systems.
