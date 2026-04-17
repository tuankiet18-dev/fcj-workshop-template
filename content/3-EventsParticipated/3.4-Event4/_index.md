---
title: "Event 4"
date: 2026-04-11
weight: 4
chapter: false
pre: " <b> 3.4. </b> "
---

# CLOUD MASTERY 3 - NETWORKING & SECURITY

### Event Objectives

- **Deep Dive into AWS Networking:** Master VPC configuration, subnetting, and connectivity options to build a robust network foundation.
- **Enhance Security and Application Protection:** Understand how to safeguard applications using AWS WAF, Shield, and Network Firewall.
- **Implement Robust Identity Management:** Learn best practices for IAM, including SSO, Service Control Policies (SCPs), and Access Analyzer.

### Speakers

- **Lâm An Thịnh** & **Nguyễn Phan Quốc Việt** (AWS Networking)
- **Lâm Tuấn Kiệt** - DevOps Engineer (Security & App Protection)
- **Huỳnh Hoàng Long** & **Đặng Thị Minh Thu** (IAM)

### Key Highlights

#### AWS Networking Fundamentals

- **VPC & Subnetting:** Understanding CIDR blocks, Public vs Private subnets, and Route Table configurations.
- **Connectivity:** Strategic use of Internet Gateway (IGW) and NAT Gateway for secure external access.

#### Security & Application Protection

- **AWS WAF (Web Application Firewall):** Protecting against common web exploits and custom rule implementation.
- **AWS Shield:** Managed DDoS protection service (Standard and Advanced layers).
- **AWS Network Firewall & Firewall Manager:** Centralized security management across multiple VPCs and accounts.

#### Identity and Access Management (IAM)

- **IAM Best Practices:** Implementing the principle of least privilege.
- **AWS IAM Identity Center (SSO):** Centralized access management for all AWS accounts and applications.
- **Governance:** Using Service Control Policies (SCPs) and Access Analyzer to ensure compliance and security.

### Key Takeaways

- **Security by Design:** Security shouldn't be an afterthought; it must be integrated into the networking and identity layers from the start.
- **Centralized Governance:** Tools like Firewall Manager and IAM Identity Center are essential for managing security at scale.

### Applying to Work

- **SmartInvoice Shield Project:**
  - **WAF Implementation:** Deploy AWS WAF with Managed Rules (Core rule set, SQL injection) to protect the SmartInvoice API from malicious traffic.
  - **DDoS Protection:** Ensure AWS Shield Standard is active and evaluate Shield Advanced for mission-critical endpoints.
  - **Granular IAM:** Refactor project roles to use fine-grained permissions and explore IAM Identity Center for team access.

---

> **Summary:** The Cloud Mastery Series provided a comprehensive roadmap for building secure, scalable, and well-governed infrastructure on AWS, directly applicable to enhancing the SmartInvoice Shield architecture.

### Some event photos

<div style="display: flex; gap: 10px; justify-content: center; align-items: flex-start; flex-wrap: wrap; margin-top: 20px;">
  <div style="flex: 1; min-width: 250px; text-align: center;">
    <img src="/fcj-workshop-template/images/3-Events/3.4-Event4/DSC05114.jpg" alt="Networking & Security Session" style="width: 100%; height: 250px; object-fit: cover; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  </div>
  <div style="flex: 1; min-width: 250px; text-align: center;">
    <img src="/fcj-workshop-template/images/3-Events/3.4-Event4/DSC05373.jpg" alt="Cloud Mastery Series 3" style="width: 100%; height: 250px; object-fit: cover; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  </div>
</div>
