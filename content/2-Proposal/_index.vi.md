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

SmartInvoice Shield là một hệ thống SaaS (Software as a Service) được thiết kế chuyên biệt nhằm cung cấp giải pháp toàn diện cho các doanh nghiệp Việt Nam trong việc quản trị và rà soát rủi ro hóa đơn điện tử. Nền tảng tự động hóa quy trình trích xuất dữ liệu đa định dạng (XML, PDF, Ảnh) thông qua AI, đồng thời thực thi bộ quy tắc kiểm tra tuân thủ 3 lớp (Cấu trúc Lược đồ XML, Chữ ký số điện tử chuẩn W3C, Logic Nghiệp vụ & Dòng tiền) tối ưu hóa theo Nghị định 123/2020/NĐ-CP và Quyết định 78/QĐ-TCT.

Bằng việc tận dụng sức mạnh của các dịch vụ AWS Serverless và Managed Services (Elastic Beanstalk, ECS Fargate, S3, RDS, Cognito, SQS), SmartInvoice Shield chuyển đổi hệ thống lưu trữ thụ động thành một rào chắn kiểm duyệt chủ động (active firewall). Nó mang lại trải nghiệm xử lý tự động khối lượng dữ liệu khổng lồ với độ trễ thấp, đảm bảo tính khả dụng cao (Multi-AZ), tối ưu chi phí vận hành và bảo vệ hoàn hảo trước mạng lưới lây nhiễm rủi ro tài chính.

### 2. Đặt vấn đề

**_Vấn đề hiện tại_**

Tại nhiều doanh nghiệp, quy trình xử lý hóa đơn đầu vào vẫn phụ thuộc vào việc nhập liệu thủ công, tiêu tốn 5-10 phút cho mỗi hóa đơn với tỷ lệ sai sót lên đến 15-20%. Nghiêm trọng hơn, các doanh nghiệp đang đối mặt với hiệu ứng "lây nhiễm rủi ro" phi tập trung trong chuỗi cung ứng. Dựa theo bộ tiêu chí chấm điểm tại Quyết định 78/QĐ-TCT của Tổng cục Thuế với lưới lọc ma trận đa chiều (Rủi ro Tức thời, Rủi ro Định lượng, và Rủi ro Tham khảo), việc vô tình tiếp nhận và hạch toán hóa đơn từ danh sách đen (Blacklist) dẫn tới hệ lụy tàn liệt: bị loại trừ toàn bộ chi phí hợp lý khi tính thuế TNDN và bị từ chối khấu trừ thuế GTGT. Các giải pháp phần mềm hiện tại đa phần chỉ là nơi lưu trữ dữ liệu thô thụ động mà thiếu đi cơ chế cảnh báo sớm tại thời điểm tiền kiểm.

**_Giải pháp_**

SmartInvoice Shield kiến tạo lại chức năng kế toán bằng một hệ sinh thái kiểm soát dữ liệu tự động:

- **Động cơ Nhập liệu Trí tuệ Nhân tạo (AI-Driven Ingestion Engine):** Tự động bóc tách và chuyển đổi dữ liệu (ETL) các cấu trúc dạng cây phân cấp XML phức tạp chuẩn Quyết định 1450/1510/QĐ-TCT (các nhánh như TTChung, NBan, TToan) để ánh xạ vào SQL Database. Cùng với AI (AWS ECS Fargate), hệ thống đọc và số hóa các dữ liệu PDF/Ảnh trực quan.
- **Rà soát Rủi ro Đa Tầng (Multi-tier Risk Alerting):** (1) Kiểm định Lược đồ XSD nguyên bản; (2) Giải mã chứng thực toàn vẹn Chữ ký số (truy vết SigningTime và phân tích chứng thư X509Certificate) cùng hệ thống xác thực chuỗi Mã CQT; (3) Rà soát logic toán học cực kỳ chặt chẽ và tương tác trực tiếp API đối soát để lọc bỏ các Nhà cung cấp nằm trong danh sách đen cảnh báo rủi ro.
- **Lưu trữ Bất biến & Truy vết (Immutable Storage):** Lưu trữ gốc tệp blob XML vô hướng trên Amazon S3 mã hóa AES-256. Hệ thống vận hành Audit Trail bất biến không cho phép thao tác ghi đè theo yêu cầu thanh tra.
- **Giao diện Khám nghiệm Trực quan (Visual Diagnostic GUI):** Tự động phân tách cấu trúc XML khô khan thành bảng điều khiển mã hóa màu sắc, giúp Kế toán trưởng dễ dàng nhận diện mã lỗi kỹ thuật và ra quyết định phê duyệt nghiệp vụ thay vì phải trực tiếp phân tích mã lệnh.

**_Lợi ích cho doanh nghiệp & Mô hình kinh doanh_**

Hệ thống cam kết giúp doanh nghiệp cắt giảm 90% thời gian xử lý hóa đơn và ngăn chặn 100% rủi ro pháp lý trước khi khai thuế. Với mô hình SaaS, khách hàng không cần đầu tư bất kỳ chi phí phần cứng hay nhân sự IT nào để vận hành. Thay vào đó, doanh nghiệp chỉ cần linh hoạt đăng ký các **Gói dịch vụ (Subscription)** theo tháng/năm dựa trên lưu lượng hóa đơn thực tế. Điều này mang lại hiệu quả hoàn vốn (ROI) ngay lập tức nhờ việc loại bỏ hoàn toàn chi phí phạt vi phạm hành chính và tối ưu quỹ thời gian của bộ phận kế toán.

### 3. Kiến trúc giải pháp

Dự án áp dụng mô hình kiến trúc lai (Hybrid Architecture) kết hợp giữa Layered Monolith (cho hệ thống Backend lõi) và Microservices (cho dịch vụ AI OCR), giao tiếp bất đồng bộ qua hệ thống Message Queue.

_Dịch vụ AWS sử dụng_

- **AWS Elastic Beanstalk & ALB:** Cung cấp môi trường Auto Scaling Group cốt lõi cho Backend .NET 9 API, triển khai Multi-AZ đảm bảo High Availability.
- **AWS ECS Fargate:** Trái tim xử lý AI, chạy dưới dạng Serverless Container (Pay-As-You-Go), tự động tắt (Scale-to-Zero) khi không có hóa đơn để tiết kiệm 100% chi phí chạy ngầm.
- **Amazon RDS for PostgreSQL:** Lưu trữ cơ sở dữ liệu quan hệ (Multi-AZ) ẩn trong Private Subnet, với dữ liệu được mã hóa KMS.
- **Amazon S3:** Lưu trữ file hóa đơn (XML, PDF) với mã hóa SSE-S3. Tích hợp Lifecycle Policy chuyển dữ liệu cũ (>90 ngày) sang Glacier Deep Archive.
- **Amazon SQS:** Xử lý hàng đợi bất đồng bộ (Long-polling) cho các luồng công việc nặng như OCR và xác minh mã số thuế.
- **Amazon Route 53:** Quản lý phân giải DNS và tên miền tùy chỉnh, định tuyến an toàn lưu lượng truy cập internet đến ứng dụng web.
- **AWS Amplify & CloudFront:** Hosting, tự động CI/CD và cung cấp CDN biên cho ứng dụng Frontend React SPA.
- **AWS Cloud Map:** Cung cấp giải pháp Service Discovery nội bộ, hoạt động như một "danh bạ DNS". Tính năng này giúp Backend EC2 tra cứu và gọi trực tiếp các AI OCR Container (Direct API Call) mà không cần tốn chi phí duy trì Load Balancer trung gian.
- **Amazon Cognito:** Quản lý định danh (Identity Provider), cấp phát JWT Token và bảo mật người dùng chuẩn quốc tế.
- **AWS Systems Manager (Parameter Store):** Két sắt nội bộ quản lý bảo mật các thông tin nhạy cảm (Database Password, API Keys).

![alt text](image.png)

### 4. Triển khai kỹ thuật

_Các giai đoạn triển khai_

Hệ thống được thiết kế để triển khai end-to-end trên nền tảng AWS thông qua các giai đoạn:

1. **Thiết lập Networking & Security:** Tạo VPC với Public/Private Subnets trên 2 AZs. Áp dụng chiến lược tối ưu chi phí bằng cách loại bỏ NAT Gateway, khóa bảo mật hoàn toàn bằng Security Groups.
2. **Triển khai Database & Storage:** Khởi tạo RDS PostgreSQL trong mạng nội bộ, thiết lập các S3 Buckets và đăng ký Docker Images lên ECR.
3. **Triển khai Core & AI Services:** Khởi chạy ECS Fargate Spot cho dịch vụ OCR và cấu hình Elastic Beanstalk cho Backend .NET. Thiết lập AWS Cloud Map để định tuyến giao tiếp nội bộ.
4. **Triển khai Frontend & Domain:** Triển khai mã nguồn React lên AWS Amplify. Tích hợp Amazon Route 53 để cấu hình tên miền tùy chỉnh cho một giao diện web chuyên nghiệp.
5. **Giám sát & Quản trị:** Thiết lập CloudWatch Alarms (giám sát CPU, Queue depth, Storage) và SNS Topic để gửi cảnh báo tự động.

_Yêu cầu kỹ thuật_

- Nắm vững 5 trụ cột của kiến trúc AWS Well-Architected.
- Ứng dụng hiệu quả kỹ thuật Docker Containerization cho tiến trình Worker.
- Am hiểu sâu sắc về kiến trúc cây sơ đồ dữ liệu XML theo Quyết định 1450/1510/QĐ-TCT, tiêu chuẩn chữ ký số W3C (XML Signature Syntax), và kỹ thuật trích xuất ETL nhằm ánh xạ dữ liệu phân cấp phức tạp vào cơ sở dữ liệu quan hệ RDBMS.

### 5. Lộ trình & Mốc triển khai

Thời gian thực hiện dự kiến là 3 tháng (12 tuần) với đội ngũ 5 thành viên (Software Engineering, AI, Cybersecurity):

- **Tuần 1 - 4 (Nghiên cứu & Nền tảng):** Đội ngũ tập trung vào việc học tập chuyên sâu, làm chủ các dịch vụ cốt lõi của AWS. Đồng thời, nhóm tiến hành phân tích yêu cầu, thiết kế kiến trúc hệ thống (Architecture Design) và xây dựng cấu trúc cơ sở dữ liệu (Database Schema).
- **Tuần 5 - 9 (Phát triển Tính năng Cốt lõi):** Bắt tay vào lập trình các module phức tạp. Tích hợp mô hình AI OCR, xây dựng các API xử lý logic nghiệp vụ (3-layer validation), và thiết lập giao tiếp bất đồng bộ qua hàng đợi Amazon SQS.
- **Tuần 10 - 12 (Triển khai Đám mây & Hoàn thiện):** Chuyển đổi toàn bộ hệ thống từ môi trường local lên AWS Cloud (Production). Thiết lập quy trình CI/CD, thực hiện kiểm thử chịu tải (Load testing), rà soát bảo mật toàn diện và hoàn thiện các tài liệu báo cáo dự án.

### 6. Ước tính ngân sách

Hệ thống áp dụng chiến lược **Cost-Optimization Multi-AZ**, loại bỏ các thành phần hạ tầng dư thừa, giúp tiết kiệm tối đa ngân sách vận hành.

Dựa trên bảng giá AWS tại khu vực Singapore (ap-southeast-1), chi phí dự kiến như sau:

_Chi phí hạ tầng AWS (Dự kiến hàng tháng)_

- **Amazon RDS PostgreSQL (db.t3.micro Multi-AZ):** ~$40,00 USD _(Bao gồm cả node Primary và Standby dự phòng)_
- **AWS Elastic Beanstalk (2x EC2 t3.micro + 1 Application Load Balancer):** ~$42,00 USD
- **Amazon VPC (2x NAT Gateway cho 2 AZ):** ~$86,00 USD
- **ECS Fargate Spot (AI OCR):** Trả phí linh hoạt theo phần nghìn giây khi có hóa đơn (Pay-As-You-Go) (~$7,00 USD).
- **Amazon CloudFront, S3, SQS & Cloud Map:** ~$5,00 USD
- **AWS Amplify, Amazon Cognito & Route 53:** 0 USD _(Nằm trong Free Tier / Không đáng kể cho 1 Hosted Zone)_

_Tổng chi phí ước tính:_ **~180,00 USD/tháng** cho một môi trường Production bảo mật, chống chịu lỗi (Fault-Tolerant) và sẵn sàng phục vụ doanh nghiệp 24/7.

### 7. Đánh giá rủi ro

_Ma trận rủi ro_

- Nhận diện AI sai lệch (đối với ảnh mờ, rách): Ảnh hưởng trung bình, xác suất trung bình.
- Độ trễ từ API bên thứ 3 (VietQR API quá tải): Ảnh hưởng nhỏ, xác suất cao.
- Lưu lượng truy cập đột biến (Spike traffic cuối tháng khai thuế): Ảnh hưởng cao, xác suất thấp.

_Chiến lược giảm thiểu_

- **Đối với AI:** Cung cấp giao diện "Khám nghiệm Dữ liệu Trực quan" (Visual Diagnostic GUI) cho phép kế toán viên so sánh kết quả trích xuất và bản gốc để chỉnh sửa thủ công (Manual override).
- **Đối với API ngoại vi:** Áp dụng mẫu thiết kế Circuit Breaker và Retry Pattern với Exponential Backoff để chống lỗi dây chuyền.
- **Đối với Traffic:** Auto Scaling Group tự động tăng EC2 (Max 4 nodes) và ECS Task (Max 10 tasks) dựa trên số lượng tin nhắn tồn đọng trong SQS.

_Kế hoạch dự phòng:_
Sử dụng kiến trúc Multi-AZ giúp hệ thống tự động Failover (chuyển đổi dự phòng) khi một Availability Zone (AZ) gặp sự cố phần cứng. Dữ liệu RDS được backup tự động (Point-In-Time Recovery) kết hợp với CloudWatch Alarms theo dõi 24/7.

### 8. Kết quả kỳ vọng

_Cải tiến kỹ thuật:_ Hệ thống vận hành trơn tru theo hướng sự kiện (Event-Driven), đáp ứng độ trễ API P95 < 2s. Độ chính xác trích xuất AI (Textract/VietOCR) cam kết đạt trên 85% đối với các hóa đơn tiếng Việt phức tạp. Khả năng mở rộng ngang (Horizontal Scaling) chịu tải hàng nghìn hóa đơn đồng thời.

_Giá trị dài hạn:_ Cung cấp cho doanh nghiệp một "tấm khiên" (Shield) vững chắc để chuyển đổi số nghiệp vụ kế toán. Triệt tiêu hoàn toàn sai sót vật lý, minh bạch hóa quy trình phê duyệt, và xây dựng một kho lưu trữ dữ liệu hoàn hảo sẵn sàng cho mọi cuộc thanh tra kiểm toán thuế trong 10 năm tới.
