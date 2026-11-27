---
title: "Product Description"
date: 2026-11-15
weight: 8
chapter: false
pre: " <b> 8. </b> "
---

# Web Travel Platform on AWS Cloud

**Project Title:** Design and Deployment of a High-Availability, Auto-Scaling Online Tour Booking System on AWS  
**Region:** Asia Pacific (Singapore) — `ap-southeast-1`  
**Source Code Repository:** `https://github.com/dt-kien04/du-an-01`  

---

## 1. Problem Statement

Traditional web applications hosted on a single on-premises physical server or local development environment (such as XAMPP) face critical operational, security, and scalability challenges:

* **Traffic Spikes & Server Overloading:** During peak holiday and tourism seasons, sudden surges in concurrent users overwhelm single-server architectures, causing slow response times or complete service downtime.
* **Single Point of Failure (SPOF):** Hosting both the web application (Apache/PHP) and the relational database (MySQL) on the same server means any hardware failure, OS crash, or resource exhaustion brings down the entire platform.
* **Security & Data Exposure Risks:** Exposing a server directly without strict network segmentation puts sensitive customer records, user credentials, and tour booking data at risk. Additionally, default development settings (such as displaying verbose PHP error traces) can leak internal directory structures.
* **High Upfront Capital Expenditure & Rigid Scaling:** Purchasing physical server hardware requires significant upfront investment and manual provisioning, making it inefficient to scale resources up during busy periods or down during quiet periods.

---

## 2. Proposed Solution

To overcome these limitations, the **Web Travel Platform** is migrated and re-architected onto **Amazon Web Services (AWS)** using a decoupled, multi-tier, and auto-scaling cloud architecture:

* **Isolated Multi-AZ Virtual Private Cloud (`travel-vpc`):**
  * Configured a custom VPC (`10.0.0.0/16`) spanning two Availability Zones (`ap-southeast-1a` and `ap-southeast-1b`).
  * Segmented into **2 Public Subnets** (for outward-facing web servers) and **2 Private Subnets** (to completely isolate the database from direct Internet access), connected via an **Internet Gateway** (omitting expensive NAT Gateways to optimize budget).
* **Two-Tier Stateful Firewall Security (`Security Groups`):**
  * **`TL-Web`:** Allows public web traffic on `HTTP (Port 80)` and `HTTPS (Port 443)`, while restricting administrative `SSH (Port 22)` access strictly to the administrator's personal IP address.
  * **`TL-Database`:** Enforces the principle of least privilege by permitting inbound `MySQL/Aurora (Port 3306)` connections exclusively from instances associated with `TL-Web`.
* **Managed Relational Database (`Amazon RDS`):**
  * Deployed **`travel-database`** (MySQL Community Edition on `db.t4g.micro` with 20 GiB gp2 SSD) inside a Private Subnet Group (`travel-data-subnet-group`) with `Public access = No` and automated daily backups.
* **Elastic Compute & Auto Scaling (`EC2`, `AMI`, `Target Group`, `Auto Scaling Group`):**
  * Hosted the PHP/Apache application on **`Web-travel-sv`** (`t3.micro`, Ubuntu Server 24.04 LTS).
  * Captured the production-ready server into a golden image (**`Web-Travel-AMI`**).
  * Configured a Target Group (**`Travel-target`**) with **Stickiness (Sticky Sessions)** enabled to preserve user login states, paired with a Launch Template (**`Travel-template`**) and an Auto Scaling Group (**`Travel-auto-scaling-group`**) capable of scaling between **0 and 3 instances**.

---

## 3. End-to-End Workflow

### Phase 1: Source Code Preparation & Version Control
1. Tested and validated the **Web Travel** application (`index.php`, `css/`, `html/`, `photo/`, `php/`, `view/`) locally on XAMPP.
2. Exported the standardized relational database schema and initial records (`users`, `tours`, `dat_cho`) into `travel_test.sql`.
3. Pushed the entire codebase and SQL dump to the centralized GitHub repository (`dt-kien04/du-an-01`).

### Phase 2: Network & Security Infrastructure Provisioning
1. Created **`travel-vpc`** (`10.0.0.0/16`) across `ap-southeast-1a` and `ap-southeast-1b` with 2 Public Subnets (auto-assign public IPv4 enabled), 2 Private Subnets, Route Tables, and an Internet Gateway.
2. Configured **`TL-Web`** and **`TL-Database`** Security Groups to isolate database traffic from external networks.

### Phase 3: Database & Application Server Deployment
1. Provisioned **`travel-database`** on Amazon RDS (`db.t4g.micro`) inside the Private Subnets and retrieved its internal connection Endpoint (`travel-database.c7o8imgka428.ap-southeast-1.rds.amazonaws.com`).
2. Generated the SSH key pair (`khoa-travel.pem`, `chmod 400`) and launched **`Web-travel-sv`** (`t3.micro`, Ubuntu 24.04 LTS) inside Public Subnet 1.
3. Connected via SSH from VS Code Terminal, installed the LAMP stack (`apache2`, `php`, `libapache2-mod-php`, `php-mysql`, `mysql-client`, `git`), cleared `/var/www/html/`, cloned the code from GitHub, and set ownership (`www-data`) for the `photo/` directory.
4. Imported `travel_test.sql` into Amazon RDS via the MySQL CLI and updated `/var/www/html/php/ket_noi.php` with the RDS Endpoint and credentials.

### Phase 4: High Availability, Auto Scaling & Operational Hardening
1. Verified live end-to-end user workflows (tour browsing, registration/login, tour booking, and admin dashboard) via the public IPv4 address.
2. Hardened production reliability by troubleshooting runtime connection logs (`/var/log/apache2/error.log`), disabling public error display (`display_errors = Off`), and configuring SSH keep-alive settings.
3. Packaged the verified server into **`Web-Travel-AMI`**, created **`Travel-target`** (with Stickiness enabled), built **`Travel-template`**, and launched **`Travel-auto-scaling-group`** (`Min: 0`, `Desired: 0`, `Max: 3`).
4. Implemented a cost-control routine to temporarily **Stop** EC2 and RDS instances when idle.

### Runtime Request Flow
* **Customer Request:** `User Browser` $
ightarrow$ `HTTP (Port 80)` $
ightarrow$ `Internet Gateway` $
ightarrow$ `TL-Web` $
ightarrow$ `EC2 Web Server (Apache/PHP)` $
ightarrow$ `MySQL (Port 3306) via TL-Database` $
ightarrow$ `Amazon RDS (Private Subnet)`.
* **Admin & Deployment Flow:** `Admin Workstation (MacBook)` $
ightarrow$ `SSH (Port 22) + khoa-travel.pem` $
ightarrow$ `EC2 Instance` $\leftarrow$ `git clone/pull` $\leftarrow$ `GitHub Repository`.

---

## 4. Additional (Optional Enhancements)

To evolve this architecture into a full enterprise-grade production platform in future iterations, the following optional enhancements are recommended:

* **Application Load Balancer (ALB):** Attach an internet-facing ALB across both Public Subnets in front of `Travel-target` to evenly distribute incoming HTTP/HTTPS traffic and perform automated health checks across scaled EC2 instances.
* **Custom Domain & HTTPS Encryption (`Route 53` / `DuckDNS` + `ACM` / `Certbot`):** Map a friendly domain name to the platform and provision free SSL/TLS certificates to enforce `HTTPS (Port 443)` encryption and eliminate browser security warnings.
* **Stateless Media Storage (`Amazon S3` + `CloudFront`):** Offload tour images from the local EC2 `/var/www/html/photo/` directory to an **Amazon S3** bucket served via **Amazon CloudFront (CDN)** so dynamically scaled EC2 instances remain completely stateless.
* **Automated CI/CD Pipeline (`GitHub Actions` / `AWS CodePipeline`):** Automate code deployment so every `git push` to the `main` branch automatically updates the web servers without manual SSH intervention.
* **Performance Load Testing (`Apache JMeter`):** Conduct simulated concurrent user stress tests to benchmark response times and trigger automated CloudWatch alarm scaling policies.

---

## 5. Cost Estimation & Optimization

The architecture was designed to operate within a **100 USD AWS Promotional Credits** academic budget in the **Singapore (`ap-southeast-1`)** Region.

### Monthly On-Demand Cost Breakdown (Assuming 24/7 Continuous Operation)

| AWS Service | Specification / Configuration | Monthly Usage | Estimated Cost (USD) |
| :--- | :--- | :--- | :--- |
| **Amazon EC2** | `t3.micro` (2 vCPU, 1 GiB RAM, Ubuntu 24.04) | 730 hours (24/7) | ~$8.47 *(Free Tier eligible)* |
| **Amazon EBS & AMI** | 8 GiB gp3 Root Volume + 8 GiB AMI Snapshot | 16 GiB total | ~$1.16 |
| **Amazon RDS** | `db.t4g.micro` (Single-AZ, MySQL) | 730 hours (24/7) | ~$11.68 |
| **Amazon RDS Storage** | General Purpose SSD (`gp2`) | 20 GiB | ~$2.76 |
| **Networking & Scaling** | VPC, Subnets, IGW, Security Groups, Target Group, ASG | Always active | $0.00 *(Free management)* |
| **Data Transfer Out** | Outbound Internet traffic | ~1 GB/month | $0.00 *(First 100 GB free)* |
| **Total (24/7 Baseline)** | **Continuous full-time operation** | **Full Month** | **~$24.07 / month** |

### Actual Optimized Project Cost
* **Active Hourly Rate:** ~$0.025/hour when both `Web-travel-sv` and `travel-database` are running simultaneously.
* **Cost-Saving Measures Applied:**
  1. Avoided **NAT Gateway** (~$32+/month) by placing web servers in Public Subnets and utilizing an Internet Gateway.
  2. Configured **`Travel-auto-scaling-group`** with `Desired capacity = 0` during idle periods to prevent unintended EC2 launches.
  3. Enforced a strict **Stop / Stop temporarily** routine for EC2 and RDS immediately after development and testing sessions.
* **Net Credit Consumption:** Under **$5.00 USD** across the entire 10-week project lifecycle, preserving over **95% of the 100 USD Credits** budget.
