---
title : "Tạo mạng travel-vpc và Security Groups"
date : 2026-11-15 
weight : 1
chapter : false
pre : " <b> 5.3.1 </b> "
---

* Khởi tạo VPC travel-vpc (10.0.0.0/16) gồm 2 Public Subnets (bật Auto-assign public IPv4), 2 Private
* Subnets và 1 Internet Gateway.

![endpoint](/BC_AWS/images/PastedGraphic.png)

![endpoint](/BC_AWS/images/a-3.png)

Kéo xuống dưới cùng và bấm Create VPC. Đợi khoảng 10 giây cho đến khi hiện thông báo xanh lá cây thành công, bấm View VPC.
![endpoint](/BC_AWS/images/a-4.png)
![endpoint](/BC_AWS/images/a5.png)
![endpoint](/BC_AWS/images/a6.png)
![endpoint](/BC_AWS/images/a7.jpg)
![endpoint](/BC_AWS/images/a8.jpg)

Tạo nhóm bảo mật TL-Web mở cổng HTTP (80), HTTPS (443) cho mọi người dùng và cổng SSH (22) giới hạn theo IP cá nhân.
![endpoint](/BC_AWS/images/a9.png)
![endpoint](/BC_AWS/images/a11.png)

Tạo nhóm bảo mật TL-Database chỉ cho phép luồng kết nối nội bộ qua cổng MySQL/Aurora (3306) xuất phát từ TL-Web.
![endpoint](/BC_AWS/images/a10.png)

