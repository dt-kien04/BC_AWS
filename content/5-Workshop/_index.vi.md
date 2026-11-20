---
title: "Workshop"
date: 2026-11-15
weight: 5
chapter: false
pre: " <b> 5. </b> "
---




# TRIỂN KHAI ỨNG DỤNG WEB TRAVEL SẴN SÀNG CAO VÀ TỰ ĐỘNG MỞ RỘNG TRÊN AWS

#### Tổng quan

Kiến trúc điện toán đám mây hiện đại giúp giải quyết triệt để bài toán quá tải và điểm lỗi đơn lẻ (Single Point of Failure) của các máy chủ vật lý truyền thống bằng cách phân tách rõ ràng tầng mạng, tầng ứng dụng và tầng cơ sở dữ liệu.

Trong bài lab này, chúng ta sẽ học cách thiết kế, cấu hình và vận hành một hạ tầng hoàn chỉnh trên AWS cho ứng dụng đặt tour trực tuyến Web Travel (PHP/MySQL). Hệ thống được triển khai trong môi trường mạng cô lập nhiều vùng sẵn sàng (Multi-AZ), đảm bảo an toàn dữ liệu và sẵn sàng tự động mở rộng khi lưu lượng truy cập tăng cao.

Chúng ta sẽ xây dựng và kết nối ba lớp dịch vụ cốt lõi để vận hành ứng dụng web chuẩn doanh nghiệp:
+ **Mạng riêng ảo và Bảo mật (Amazon VPC & Security Groups)** - Thiết lập hạ tầng mạng travel-vpc phân tách Public Subnets và Private Subnets, kiểm soát lưu lượng chặt chẽ qua hai lớp tường lửa TL-Web và TL-Database.
+ **Cơ sở dữ liệu quản trị (Amazon RDS)** - Triển khai cơ sở dữ liệu MySQL (travel-database) ẩn hoàn toàn trong Private Subnet để bảo vệ dữ liệu nghiệp vụ và kết nối nội bộ với máy chủ ứng dụng.
+ **Máy chủ ứng dụng và Tự động mở rộng (EC2, AMI & Auto Scaling)** - Vận hành mã nguồn trên EC2 Ubuntu (Web-travel-sv), đóng gói thành khuôn mẫu Web-Travel-AMI và thiết lập cụm Travel-auto-scaling-group tự động điều phối tài nguyên.

#### Nội dung

1. [Giới thiệu](5.1-Workshop-overview/)
2. [Các bước chuẩn bị](5.2-Prerequiste/)
3. [Thiết lập hạ tầng mạng VPC và Cơ sở dữ liệu RDS](5.3-S3-vpc/)
4. [Triển khai Web Server trên EC2 và Kiểm thử ứng dụng](5.4-S3-onprem/)
5. [Đóng gói AMI và Cấu hình Auto Scaling Group)](5.5-Policy/)
6. [Dọn dẹp tài nguyên](5.6-Cleanup/)