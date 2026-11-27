---
title: "Worklog Tuần 4"
date: 2026-08-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---



### Mục tiêu tuần 4:

* Hiểu rõ cơ chế phân chia mạng và định tuyến trên môi trường đám mây AWS.
* Thiết lập kiến trúc mạng riêng ảo phân tầng bảo mật (Public và Private Subnets) trên nhiều vùng sẵn sàng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 7   | - Tìm hiểu kiến trúc Amazon VPC, CIDR Block, Subnet, Internet Gateway và Route Table. <br> - Thực hành khởi tạo mạng riêng ảo travel-vpc (10.0.0.0/16) trên 2 Availability Zones (ap-southeast-1a và 1b). <br> - Tạo 2 Public Subnets và 2 Private Subnets. <br> - Cấu hình tự động cấp IPv4 công cộng cho các Public Subnets. <br> | 22/08/2026   | 22/08/2026      | <https://aws.amazon.com/> <br> <https://docs.aws.amazon.com/vpc/> <br> <https://docs.aws.amazon.com/security/> |

### Kết quả đạt được tuần 4:

* Khởi tạo thành công hạ tầng mạng độc lập travel-vpc với sơ đồ phân tầng rõ ràng giữa khu vực công khai (đặt Web Server) và khu vực riêng tư (cô lập Database).

* Tối ưu hóa chi phí mạng bằng cách sử dụng Internet Gateway cho Public Subnet và loại bỏ hoàn toàn NAT Gateway không cần thiết.
