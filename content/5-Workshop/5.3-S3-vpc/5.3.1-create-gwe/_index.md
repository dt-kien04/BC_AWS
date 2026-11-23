---
title : "Create a travel-vpc network and Security Groups."
date : 2026-11-15 
weight : 1
chapter : false
pre : " <b> 5.3.1 </b> "
---

* Initialize the travel-vpc (10.0.0.0/16) VPC with 2 public subnets (auto-assign public IPv4 enabled) and 2 private subnets.
* Subnets and 1 Internet Gateway.

![endpoint](/BC_AWS/images/PastedGraphic.png)

![endpoint](/BC_AWS/images/a-3.png)

Scroll to the bottom and click Create VPC. Wait about 10 seconds until a green success message appears, then click View VPC.
![endpoint](/BC_AWS/images/a-4.png)
![endpoint](/BC_AWS/images/a5.png)
![endpoint](/BC_AWS/images/a6.png)
![endpoint](/BC_AWS/images/a7.jpg)
![endpoint](/BC_AWS/images/a8.jpg)

Create a TL-Web security group that opens HTTP (80) and HTTPS (443) ports for all users and SSH (22) ports restricted by individual IP addresses.
![endpoint](/BC_AWS/images/a9.png)
![endpoint](/BC_AWS/images/a11.png)

Create a TL-Database security group that only allows internal connection streams through MySQL/Aurora port (3306) originating from TL-Web.
![endpoint](/BC_AWS/images/a10.png)

