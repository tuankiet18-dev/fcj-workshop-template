---
title: "Bản đề xuất"
date: 2026-03-30
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
# SmartInvoice Shield
<h2 align="center">Hệ thống Quản trị & Rà soát Rủi ro Hóa đơn Điện tử trên nền tảng AWS</h2>

### 1. Tổng quan dự án
SmartInvoice Shield là một hệ thống SaaS (Software as a Service) được thiết kế chuyên biệt nhằm cung cấp giải pháp toàn diện cho các doanh nghiệp Việt Nam trong việc quản trị và rà soát rủi ro hóa đơn điện tử. Nền tảng tự động hóa quá trình trích xuất dữ liệu từ các định dạng hóa đơn (XML, PDF, Ảnh) thông qua AI, đồng thời thực thi bộ quy tắc kiểm tra tuân thủ 3 lớp (Cấu trúc, Chữ ký số, Nghiệp vụ) dựa trên Nghị định 123/2020/NĐ-CP.

Bằng việc tận dụng sức mạnh của các dịch vụ AWS Serverless và Managed Services (Elastic Beanstalk, ECS Fargate, S3, RDS, Cognito, SQS), SmartInvoice Shield mang lại trải nghiệm xử lý tự động khối lượng dữ liệu lớn với độ trễ thấp, đảm bảo tính khả dụng cao (Multi-AZ), tối ưu chi phí vận hành và bảo mật tuyệt đối.

### 2. Đặt vấn đề
***Vấn đề hiện tại***

Tại nhiều doanh nghiệp, quy trình xử lý hóa đơn đầu vào vẫn phụ thuộc 100% vào việc nhập liệu thủ công, tiêu tốn 5-10 phút cho mỗi hóa đơn với tỷ lệ sai sót lên đến 15-20%. Nghiêm trọng hơn, các doanh nghiệp gặp rủi ro cực kỳ lớn trong việc hạch toán nhầm hóa đơn từ doanh nghiệp thuộc "danh sách đen" (Blacklist), hóa đơn giả, hoặc sai lệch toán học. Theo Quyết định 78/QĐ-TCT, việc này mang lại hậu quả pháp lý nặng nề (bị loại trừ chi phí hợp lý, truy thu thuế). Các giải pháp phần mềm hiện tại đa phần chỉ lưu trữ thụ động mà thiếu đi cơ chế rà soát tự động (active firewall) và cảnh báo sớm.

***Giải pháp***

SmartInvoice Shield chuyển đổi quy trình thủ công thành quy trình tự động hóa hoàn toàn với các tính năng cốt lõi:
- **Thu thập & Số hóa:** Tự động trích xuất dữ liệu từ hóa đơn gốc XML và sử dụng Động cơ AI (AWS ECS Fargate chạy PaddleOCR/VietOCR) để đọc và số hóa file PDF/Ảnh.
- **Rà soát rủi ro 3 lớp (3-Layer Validation):** (1) Kiểm tra tính hợp lệ của cấu trúc XSD; (2) Xác thực Chữ ký số và chống giả mạo (Anti-Spoofing); (3) Kiểm tra logic nghiệp vụ (toán học, ngày tháng, và gọi API VietQR để xác minh trạng thái Mã số thuế).
- **Lưu trữ bảo mật & Truy vết:** Lưu trữ vô hạn trên Amazon S3 với mã hóa AES-256. Dữ liệu được bảo vệ bằng hệ thống Audit Trail bất biến (không thể xóa) nhằm truy vết mọi thay đổi của người dùng.
- **Minh bạch & Cảnh báo:** Hệ thống đánh giá rủi ro theo 3 cấp độ trực quan (Xanh/Vàng/Đỏ), giúp kế toán trưởng đưa ra quyết định phê duyệt nhanh chóng.

***Lợi ích cho doanh nghiệp & Mô hình kinh doanh***

Hệ thống cam kết giúp doanh nghiệp cắt giảm 90% thời gian xử lý hóa đơn và ngăn chặn 100% rủi ro pháp lý trước khi khai thuế. Với mô hình SaaS, khách hàng không cần đầu tư bất kỳ chi phí phần cứng hay nhân sự IT nào để vận hành. Thay vào đó, doanh nghiệp chỉ cần linh hoạt đăng ký các **Gói dịch vụ (Subscription)** theo tháng/năm dựa trên lưu lượng hóa đơn thực tế. Điều này mang lại hiệu quả hoàn vốn (ROI) ngay lập tức nhờ việc loại bỏ hoàn toàn chi phí phạt vi phạm hành chính và tối ưu quỹ thời gian của bộ phận kế toán.

### 3. Kiến trúc giải pháp
Dự án áp dụng mô hình kiến trúc lai (Hybrid Architecture) kết hợp giữa Layered Monolith (cho hệ thống Backend lõi) và Microservices (cho dịch vụ AI OCR), giao tiếp bất đồng bộ qua hệ thống Message Queue.

*Dịch vụ AWS sử dụng*
- **AWS Elastic Beanstalk & ALB:** Cung cấp môi trường Auto Scaling Group cốt lõi cho Backend .NET 9 API, triển khai Multi-AZ đảm bảo High Availability.
- **AWS ECS Fargate:** Trái tim xử lý AI, chạy dưới dạng Serverless Container (Pay-As-You-Go), tự động tắt (Scale-to-Zero) khi không có hóa đơn để tiết kiệm 100% chi phí chạy ngầm.
- **Amazon RDS for PostgreSQL:** Lưu trữ cơ sở dữ liệu quan hệ (Multi-AZ) ẩn trong Private Subnet, với dữ liệu được mã hóa KMS.
- **Amazon S3:** Lưu trữ file hóa đơn (XML, PDF) với mã hóa SSE-S3. Tích hợp Lifecycle Policy chuyển dữ liệu cũ (>90 ngày) sang Glacier Deep Archive.
- **Amazon SQS:** Xử lý hàng đợi bất đồng bộ (Long-polling) cho các luồng công việc nặng như OCR và xác minh mã số thuế.
- **AWS Amplify & CloudFront:** Hosting, tự động CI/CD và cung cấp CDN biên cho ứng dụng Frontend React SPA.
- **Amazon Cognito:** Quản lý định danh (Identity Provider), cấp phát JWT Token và bảo mật người dùng chuẩn quốc tế.
- **AWS Systems Manager (Parameter Store):** Két sắt nội bộ quản lý bảo mật các thông tin nhạy cảm (Database Password, API Keys).

### 4. Triển khai kỹ thuật
*Các giai đoạn triển khai*

Hệ thống được thiết kế để triển khai end-to-end trên nền tảng AWS thông qua các giai đoạn:
1. **Thiết lập Networking & Security:** Tạo VPC với Public/Private Subnets trên 2 AZs. Áp dụng chiến lược tối ưu chi phí bằng cách loại bỏ NAT Gateway, khóa bảo mật hoàn toàn bằng Security Groups.
2. **Triển khai Database & Storage:** Khởi tạo RDS PostgreSQL trong mạng nội bộ, thiết lập các S3 Buckets và đăng ký Docker Images lên ECR.
3. **Triển khai Core & AI Services:** Khởi chạy ECS Fargate Spot cho dịch vụ OCR và cấu hình Elastic Beanstalk cho Backend .NET. Tích hợp Application Load Balancer.
4. **Triển khai Frontend & Domain:** Triển khai mã nguồn React lên AWS Amplify.
5. **Giám sát & Quản trị:** Thiết lập CloudWatch Alarms (giám sát CPU, Queue depth, Storage) và SNS Topic để gửi cảnh báo tự động.

*Yêu cầu kỹ thuật*
- Nắm vững 5 trụ cột của kiến trúc AWS Well-Architected.
- Ứng dụng hiệu quả Docker Containerization.
- Am hiểu cấu trúc cây dữ liệu định dạng XML theo Quyết định 1450/1510/QĐ-TCT và thuật toán băm chữ ký số.

### 5. Lộ trình & Mốc triển khai
Thời gian thực hiện dự kiến là 3 tháng (12 tuần) với đội ngũ 5 thành viên (Software Engineering, AI, Cybersecurity):
- **Tuần 1 - 4 (Nghiên cứu & Nền tảng):** Đội ngũ tập trung vào việc học tập chuyên sâu, làm chủ các dịch vụ cốt lõi của AWS. Đồng thời, nhóm tiến hành phân tích yêu cầu, thiết kế kiến trúc hệ thống (Architecture Design) và xây dựng cấu trúc cơ sở dữ liệu (Database Schema).
- **Tuần 5 - 9 (Phát triển Tính năng Cốt lõi):** Bắt tay vào lập trình các module phức tạp. Tích hợp mô hình AI OCR, xây dựng các API xử lý logic nghiệp vụ (3-layer validation), và thiết lập giao tiếp bất đồng bộ qua hàng đợi Amazon SQS.
- **Tuần 10 - 12 (Triển khai Đám mây & Hoàn thiện):** Chuyển đổi toàn bộ hệ thống từ môi trường local lên AWS Cloud (Production). Thiết lập quy trình CI/CD, thực hiện kiểm thử chịu tải (Load testing), rà soát bảo mật toàn diện và hoàn thiện các tài liệu báo cáo dự án.

### 6. Ước tính ngân sách
Hệ thống áp dụng chiến lược **Cost-Optimization Multi-AZ**, loại bỏ các thành phần hạ tầng dư thừa, giúp tiết kiệm tối đa ngân sách vận hành:

*Chi phí hạ tầng AWS (Dự kiến hàng tháng)*
- Amazon RDS PostgreSQL (APS1-InstanceUsage:db.t3.micro): ~23,20 USD
- Amazon CloudFront: ~2,34 USD
- AWS Elastic Beanstalk (EC2 & Application Load Balancer): ~42,10 USD
- Amazon S3, SQS & Các dịch vụ mạng khác: ~2,00 USD
- AWS Amplify & Amazon Cognito: 0 USD (Nằm trong Free Tier)
- ECS Fargate Spot (AI OCR): Trả phí linh hoạt theo phần nghìn giây khi có hóa đơn (Pay-As-You-Go) (~7,00 USD).

*Tổng chi phí ước tính:* **~76,55 USD/tháng** cho môi trường Production sẵn sàng phục vụ doanh nghiệp.

### 7. Đánh giá rủi ro
*Ma trận rủi ro*
- Nhận diện AI sai lệch (đối với ảnh mờ, rách): Ảnh hưởng trung bình, xác suất trung bình.
- Độ trễ từ API bên thứ 3 (VietQR API quá tải): Ảnh hưởng nhỏ, xác suất cao.
- Lưu lượng truy cập đột biến (Spike traffic cuối tháng khai thuế): Ảnh hưởng cao, xác suất thấp.

*Chiến lược giảm thiểu*
- **Đối với AI:** Cung cấp giao diện "Khám nghiệm Dữ liệu Trực quan" (Visual Diagnostic GUI) cho phép kế toán viên so sánh kết quả trích xuất và bản gốc để chỉnh sửa thủ công (Manual override).
- **Đối với API ngoại vi:** Áp dụng mẫu thiết kế Circuit Breaker và Retry Pattern với Exponential Backoff để chống lỗi dây chuyền.
- **Đối với Traffic:** Auto Scaling Group tự động tăng EC2 (Max 4 nodes) và ECS Task (Max 10 tasks) dựa trên số lượng tin nhắn tồn đọng trong SQS.

*Kế hoạch dự phòng:*
Sử dụng kiến trúc Multi-AZ giúp hệ thống tự động Failover (chuyển đổi dự phòng) khi một Availability Zone (AZ) gặp sự cố phần cứng. Dữ liệu RDS được backup tự động (Point-In-Time Recovery) kết hợp với CloudWatch Alarms theo dõi 24/7.

### 8. Kết quả kỳ vọng
*Cải tiến kỹ thuật:* Hệ thống vận hành trơn tru theo hướng sự kiện (Event-Driven), đáp ứng độ trễ API P95 < 2s. Độ chính xác trích xuất AI (Textract/VietOCR) cam kết đạt trên 85% đối với các hóa đơn tiếng Việt phức tạp. Khả năng mở rộng ngang (Horizontal Scaling) chịu tải hàng nghìn hóa đơn đồng thời.

*Giá trị dài hạn:* Cung cấp cho doanh nghiệp một "tấm khiên" (Shield) vững chắc để chuyển đổi số nghiệp vụ kế toán. Triệt tiêu hoàn toàn sai sót vật lý, minh bạch hóa quy trình phê duyệt, và xây dựng một kho lưu trữ dữ liệu hoàn hảo sẵn sàng cho mọi cuộc thanh tra kiểm toán thuế trong 10 năm tới.