---
title: "Event 4"
date: 2026-04-11
weight: 4
chapter: false
pre: " <b> 3.4. </b> "
---

# CLOUD MASTERY 3 - NETWORKING & SECURITY

### Mục Đích Của Sự Kiện

- **Nghiên cứu sâu về AWS Networking:** Nắm vững cấu hình VPC, chia subnet và các tùy chọn kết nối để xây dựng nền tảng mạng vững chắc.
- **Tăng cường Bảo mật và Bảo vệ Ứng dụng:** Hiểu cách bảo vệ ứng dụng bằng AWS WAF, Shield và Network Firewall.
- **Triển khai Quản lý Định danh Hiệu quả:** Học các best practices cho IAM, bao gồm SSO, Service Control Policies (SCPs) và Access Analyzer.

### Danh Sách Diễn Giả

- **Lâm An Thịnh** & **Nguyễn Phan Quốc Việt** (AWS Networking)
- **Lâm Tuấn Kiệt** - DevOps Engineer (Security & App Protection)
- **Huỳnh Hoàng Long** & **Đặng Thị Minh Thu** (IAM)

### Nội Dung Nổi Bật

#### Nền tảng AWS Networking

- **VPC & Subnetting:** Hiểu về dải CIDR, Subnet công khai (Public) vs riêng tư (Private), và cấu hình Route Table.
- **Kết nối:** Sử dụng chiến lược Internet Gateway (IGW) và NAT Gateway để truy cập bên ngoài an toàn.

#### Bảo mật & Bảo vệ Ứng dụng

- **AWS WAF (Web Application Firewall):** Bảo vệ chống lại các lỗ hổng web phổ biến và triển khai các quy tắc tùy chỉnh.
- **AWS Shield:** Dịch vụ bảo vệ DDoS được quản lý (lớp Standard và Advanced).
- **AWS Network Firewall & Firewall Manager:** Quản lý bảo mật tập trung trên nhiều VPC và tài khoản.

#### Quản lý định danh và truy cập (IAM)

- **IAM Best Practices:** Triển khai nguyên tắc đặc quyền tối thiểu (least privilege).
- **AWS IAM Identity Center (SSO):** Quản lý truy cập tập trung cho tất cả các tài khoản AWS và ứng dụng.
- **Quản trị:** Sử dụng Service Control Policies (SCPs) và Access Analyzer để đảm bảo tuân thủ và bảo mật.

### Những Gì Học Được

- **Bảo mật từ khâu thiết kế (Security by Design):** Bảo mật không nên là yếu tố bổ sung sau cùng; nó phải được tích hợp vào các lớp mạng và định danh ngay từ đầu.
- **Quản trị tập trung:** Các công cụ như Firewall Manager và IAM Identity Center là thiết yếu để quản lý bảo mật ở quy mô lớn.

### Ứng Dụng Vào Công Việc

- **Dự án SmartInvoice Shield:**
  - **Triển khai WAF:** Áp dụng AWS WAF với các Managed Rules (Core rule set, SQL injection) để bảo vệ API SmartInvoice khỏi lưu lượng độc hại.
  - **Bảo vệ DDoS:** Đảm bảo AWS Shield Standard đang hoạt động và đánh giá Shield Advanced cho các endpoint quan trọng.
  - **IAM Chi tiết:** Tinh chỉnh các role trong dự án để sử dụng quyền hạn chi tiết và tìm hiểu IAM Identity Center để quản lý truy cập cho nhóm.

---

> **Tổng kết:** Chuỗi bài học Cloud Mastery đã cung cấp một lộ trình toàn diện để xây dựng hạ tầng bảo mật, có khả năng mở rộng và được quản trị tốt trên AWS, có thể áp dụng trực tiếp để nâng cấp kiến trúc của SmartInvoice Shield.

### Một số hình ảnh khi tham gia sự kiện

<div style="display: flex; gap: 10px; justify-content: center; align-items: flex-start; flex-wrap: wrap; margin-top: 20px;">
  <div style="flex: 1; min-width: 250px; text-align: center;">
    <img src="/fcj-workshop-template/images/3-Events/3.4-Event4/DSC05114.jpg" alt="Session Networking & Security" style="width: 100%; height: 250px; object-fit: cover; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  </div>
  <div style="flex: 1; min-width: 250px; text-align: center;">
    <img src="/fcj-workshop-template/images/3-Events/3.4-Event4/DSC05373.jpg" alt="Cloud Mastery Series 3" style="width: 100%; height: 250px; object-fit: cover; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  </div>
</div>
