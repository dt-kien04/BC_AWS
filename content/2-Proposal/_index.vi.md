---
title: "Bản đề xuất"
date: 2026-11-15
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


Tại phần này, tôi tóm tắt các nội dung trong workshop mà tôi **dự tính** sẽ làm.

# WEB TRAVEL PLATFORM ON CLOUD  
## Giải pháp kiến trúc AWS sẵn sàng cao và tự động mở rộng cho hệ thống đặt tour trực tuyến  

### 1. Tóm tắt điều hành  
Web Travel Platform được thiết kế và triển khai nhằm hiện đại hóa hệ thống quản lý, tìm kiếm và đặt tour du lịch trực tuyến trên nền tảng điện toán đám mây Amazon Web Services (AWS). Hệ thống hỗ trợ vận hành ổn định trên môi trường thực tế với khả năng tự động mở rộng linh hoạt từ 0 lên tối đa 3 máy chủ ứng dụng tùy theo lưu lượng truy cập. Nền tảng tận dụng các dịch vụ cốt lõi của AWS (VPC, EC2, RDS, Auto Scaling) để đảm bảo tính sẵn sàng cao, cô lập bảo mật dữ liệu tuyệt đối và tối ưu hóa chi phí vận hành trong phạm vi ngân sách 100 USD AWS Promotional Credits.  

### 2. Tuyên bố vấn đề  
*Vấn đề hiện tại*  
Các ứng dụng web truyền thống triển khai trên một máy chủ vật lý hoặc môi trường cục bộ (như XAMPP) thường gặp tình trạng quá tải khi lượng người dùng tăng đột biến vào mùa cao điểm du lịch. Việc lưu trữ chung mã nguồn web và cơ sở dữ liệu trên cùng một máy chủ làm tăng nguy cơ lộ lọt dữ liệu, khó sao lưu phục hồi và tồn tại điểm lỗi đơn lẻ (Single Point of Failure).  

*Giải pháp*  
Nền tảng sử dụng Amazon VPC để phân tách hạ tầng mạng thành hai tầng công khai và riêng tư trên 2 vùng sẵn sàng (Availability Zones). Tầng ứng dụng sử dụng Amazon EC2 (Ubuntu 24.04 LTS) chạy mã nguồn PHP, kết hợp với Auto Scaling Group và khuôn mẫu AMI để tự động nhân bản máy chủ khi cần thiết. Tầng dữ liệu được chuyển dịch lên dịch vụ quản trị Amazon RDS (MySQL) đặt ẩn hoàn toàn trong Private Subnet và bảo vệ bởi hai lớp tường lửa Security Groups.  

*Lợi ích và hoàn vốn đầu tư (ROI)*  
Giải pháp giúp loại bỏ hoàn toàn chi phí đầu tư và bảo trì phần cứng máy chủ vật lý ban đầu, đồng thời nâng cao độ tin cậy và bảo mật dữ liệu khách hàng. Chi phí vận hành thực tế được kiểm soát ở mức cực thấp (gần như 0 USD khi ở chế độ chờ và khoảng 0,025 USD/giờ khi bật cả EC2 và RDS), hoàn toàn nằm gọn trong gói 100 USD Credits tài trợ học tập. Hệ thống giúp giảm thiểu thời gian quản trị hạ tầng thủ công và sẵn sàng mở rộng quy mô doanh nghiệp ngay lập tức.  

### 3. Kiến trúc giải pháp  
Nền tảng áp dụng kiến trúc đám mây phân tầng tiêu chuẩn của AWS tại khu vực Singapore (ap-southeast-1). Toàn bộ hệ thống nằm trong mạng riêng ảo travel-vpc trải dài qua 2 Availability Zones (ap-southeast-1a và ap-southeast-1b). Máy chủ web Web-travel-sv đặt tại Public Subnet tiếp nhận lưu lượng người dùng thông qua Internet Gateway và tường lửa TL-Web. Dữ liệu nghiệp vụ được truy vấn nội bộ tới travel-database (Amazon RDS MySQL) đặt trong Private Subnet thông qua tường lửa TL-Database. Cụm Travel-auto-scaling-group kết hợp cùng Web-Travel-AMI và Travel-target đảm bảo khả năng tự động mở rộng và duy trì phiên đăng nhập người dùng liên tục.  

![WEB TRAVEL PLATFORM ON CLOUD](/BC_AWS/images/Sodo.drawio.png)

### 4. Triển khai kỹ thuật  
*Các giai đoạn triển khai*  
Dự án được thực hiện xuyên suốt trong 10 tuần (triển khai định kỳ vào thứ 7 hàng tuần) trải qua 4 giai đoạn chính:
1. Khảo sát và chuẩn hóa mã nguồn (Tuần 1 – 2): Kiểm thử ứng dụng Web Travel trên XAMPP, xuất cơ sở dữ liệu travel_test.sql và quản lý mã nguồn tập trung trên GitHub (dt-kien04/du-an-01).
2. Thiết lập mạng và bảo mật (Tuần 3 – 4): Khởi tạo travel-vpc, phân chia 2 Public Subnets, 2 Private Subnets và cấu hình tường lửa TL-Web, TL-Database.
3. Triển khai Database và Web Server (Tuần 5 – 7): Khởi tạo Amazon RDS (travel-database), tạo máy chủ EC2 Ubuntu (Web-travel-sv), cài đặt LAMP stack, kéo code từ GitHub và kết nối cơ sở dữ liệu.
4. Cấu hình mở rộng tự động và tối ưu vận hành (Tuần 8 – 10): Đóng gói Web-Travel-AMI, thiết lập Target Group (Travel-target), Launch Template (Travel-template), Auto Scaling Group và hoàn thiện báo cáo khóa luận.  

*Yêu cầu kỹ thuật*  
* Tầng ứng dụng (Web Tier): Máy chủ ảo EC2 loại t3.micro chạy hệ điều hành Ubuntu Server 24.04 LTS, cài đặt Apache2, PHP 8.x, MySQL Client và Git. Xác thực truy cập quản trị từ xa qua SSH Key Pair (khoa-travel.pem).
* Tầng dữ liệu (Database Tier): Dịch vụ Amazon RDS chạy MySQL Community trên cấu hình db.t4g.micro với 20 GiB ổ cứng SSD (gp2), tắt truy cập công cộng (Public access = No) và sao lưu tự động 1 ngày.  

### 5. Lộ trình & Mốc triển khai  
* Giai đoạn chuẩn bị (Tuần 1 – 2): Nghiên cứu lý thuyết AWS, kích hoạt tài khoản 100 Credits, chuẩn hóa mã nguồn PHP và đẩy dự án lên GitHub.
* Giai đoạn xây dựng hạ tầng (Tuần 3 – 6): Thiết lập hoàn chỉnh mạng travel-vpc, các nhóm bảo mật Security Groups, khởi tạo thành công cơ sở dữ liệu Amazon RDS và máy chủ ảo EC2.
* Giai đoạn tích hợp & mở rộng (Tuần 7 – 9): Đưa website Web Travel lên chạy trực tuyến, cấu hình cụm Auto Scaling Group, kiểm thử khắc phục sự cố kết nối và tối ưu chi phí vận hành.
* Giai đoạn hoàn thiện (Tuần 10): Tổng hợp số liệu thực nghiệm, vẽ sơ đồ kiến trúc chuẩn AWS, hoàn chỉnh cuốn báo cáo khóa luận và chuẩn bị bảo vệ trước hội đồng.  


### 6. Kết quả kỳ vọng  
* Cải tiến kỹ thuật: Xây dựng thành công hệ thống đặt tour du lịch trực tuyến vận hành ổn định trên đám mây AWS với kiến trúc phân tầng bảo mật cao, loại bỏ điểm lỗi đơn lẻ và sẵn sàng tự động mở rộng khi lưu lượng truy cập tăng cao.
* Giá trị dài hạn: Tạo nền tảng kiến trúc chuẩn mực để tiếp tục nâng cấp trong tương lai như tách biệt lưu trữ hình ảnh sang Amazon S3 + CloudFront, tích hợp tên miền Route 53 kèm chứng chỉ bảo mật HTTPS (ACM) và tự động hóa quy trình triển khai CI/CD.