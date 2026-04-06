---
title: "Event 3"
date: 2026-04-04
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# CLOUD MASTERY 2 - DEVOPS FOR FRESHER

### MỤC ĐÍCH CỦA SỰ KIỆN

- Khám phá các xu hướng công nghệ Cloud Native và AI trong hệ sinh thái AWS.
- Tìm hiểu cách quản lý hạ tầng hiện đại bằng Infrastructure as Code (IaC) và Container Orchestration.
- Nghiên cứu các giải pháp lập trình đồng thời và chịu lỗi cao cho hạ tầng DevOps với Elixir.
- Thảo luận về việc tối ưu hóa chi phí và hiệu suất khi triển khai các hệ thống lớn.

### DANH SÁCH DIỄN GIẢ

- **Thịnh Nguyễn** – Cloud Engineer Trainee at FCAJ, Swinburne Vietnam.
- **Bảo Huỳnh** – Junior Cloud Native Developer at Endava, Founder of iTea Lab.
- **Nguyễn Tạ Minh Triết** – R&D Member at iTea Lab, SAP Developer Intern at Bosch GSV.

### NỘI DUNG NỔI BẬT

#### Infrastructure as Code (IaC) với Terraform trên AWS

- So sánh giữa IaC và "ClickOps", nhấn mạnh lợi ích của việc tự động hóa và quản lý hạ tầng bằng mã nguồn.
- Giới thiệu các công cụ IaC trên AWS: CloudFormation, CDK và đi sâu vào Terraform.
- Quy trình làm việc thực tế với Terraform: **Write -> Plan -> Apply** và cơ chế quản lý State.

#### Kiến trúc Cloud Native với Kubernetes

- Giải quyết các thách thức trong việc điều phối container (container orchestration).
- Đi sâu vào kiến trúc Kubernetes: Control Plane, Worker Nodes, và các đối tượng cốt lõi (Pods, Services, Deployments).
- Giới thiệu các công cụ hỗ trợ vận hành K8s hiệu quả: **Helm** và **K9S**.

#### Elixir - Giải pháp hợp nhất cho hạ tầng DevOps hiệu năng cao

- Giới thiệu ngôn ngữ Elixir và máy ảo BEAM với khả năng xử lý hàng triệu tiến trình đồng thời.
- Cơ chế chịu lỗi (Fault-tolerance) với OTP (Open Telecom Platform).
- Case study ấn tượng: Chuyển đổi từ kiến trúc Serverless (Lambda/API Gateway) sang Elixir giúp giảm chi phí từ $30,000 xuống còn $400 mỗi tháng.
- Ứng dụng Elixir trong hệ sinh thái AI/ML với Numerical Elixir (NX) và Livebook.

### BÀI HỌC RÚT RA

- **Tư duy hạ tầng:** Việc sử dụng Terraform là bắt buộc để đảm bảo tính nhất quán và khả năng tái sử dụng hạ tầng trên AWS.
- **Kỹ năng điều phối:** Kubernetes không chỉ là công cụ chạy container mà là một hệ điều hành cho Cloud, đòi hỏi sự am hiểu về kiến trúc mạng và lưu trữ.
- **Tối ưu hóa chi phí:** Serverless không phải lúc nào cũng rẻ nhất. Việc lựa chọn ngôn ngữ phù hợp như Elixir có thể mang lại hiệu quả kinh tế cực lớn cho các hệ thống có lưu lượng truy cập cao.

### ỨNG DỤNG VÀO CÔNG VIỆC

#### Nâng cấp dự án SmartInvoice Shield

- **Triển khai Terraform:** Sử dụng Terraform để quản lý toàn bộ các resource AWS của SmartInvoice (S3, SQS, RDS, Elastic Beanstalk), thay thế cho việc cấu hình thủ công.
- **Container hóa OCR Worker:** Cân nhắc đưa OCR worker lên Kubernetes để tận dụng khả năng auto-scaling và tự phục hồi (self-healing) khi xử lý khối lượng lớn hóa đơn.
- **Nghiên cứu Elixir cho Ingestion Layer:** Đánh giá việc sử dụng Elixir/Phoenix để xây dựng handler nhận hóa đơn từ email/webhook nhằm đáp ứng khả năng chịu tải cực lớn với chi phí thấp.

---

> **Tổng kết:** Sự kiện FCJ AI đã mang lại cái nhìn chuyên sâu về cách kết hợp giữa quản lý hạ tầng hiện đại và các giải pháp ngôn ngữ lập trình tối ưu để xây dựng hệ thống Cloud bền vững.
