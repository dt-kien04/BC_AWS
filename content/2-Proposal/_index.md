---
title: "Proposal"
date: 2026-11-15
weight: 2
chapter: false
pre: " <b> 2. </b> "
---



# WEB TRAVEL PLATFORM ON CLOUD
## High-Availability and Auto-Scaling AWS Architecture Solution for Online Tour Booking Systems

### 1. Executive Summary
Web Travel Platform is designed and deployed to modernize online tour management, searching, and booking systems on the Amazon Web Services (AWS) cloud platform. The system operates reliably in a live cloud environment with flexible auto-scaling capabilities ranging from 0 to a maximum of 3 application servers depending on incoming traffic. The platform leverages core AWS services (VPC, EC2, RDS, Auto Scaling) to ensure high availability, strict data isolation, and operational cost optimization within the 100 USD AWS Promotional Credits budget.

### 2. Problem Statement
### What’s the Problem?
Traditional web applications deployed on a single physical server or local environment (such as XAMPP) frequently experience overloading during peak tourism seasons when user traffic surges. Hosting both web source code and the database on the same server increases the risk of data breaches, complicates backup and recovery procedures, and introduces a Single Point of Failure (SPOF).

### The Solution
The platform utilizes Amazon VPC to segment the network infrastructure into public and private tiers across two Availability Zones. The application tier runs on Amazon EC2 (Ubuntu 24.04 LTS) hosting PHP source code, integrated with an Auto Scaling Group and a custom AMI template to automatically replicate servers when needed. The data tier is migrated to the managed Amazon RDS (MySQL) service, completely isolated inside a Private Subnet and protected by two layers of Security Groups.

### Benefits and Return on Investment
The solution completely eliminates upfront physical server hardware investment and maintenance costs while enhancing system reliability and customer data security. Actual operational costs are kept minimal (nearly 0 USD when stopped in standby mode and approximately 0.025 USD/hour when both EC2 and RDS are active), fitting comfortably within the 100 USD Credits academic grant. The system significantly reduces manual infrastructure administration overhead and is ready for immediate enterprise-scale expansion.

### 3. Solution Architecture
The platform adopts a standard multi-tier AWS cloud architecture in the Singapore Region (ap-southeast-1). The entire infrastructure resides within a custom Virtual Private Cloud named travel-vpc, spanning two Availability Zones (ap-southeast-1a and ap-southeast-1b). The web server Web-travel-sv is placed inside a Public Subnet, receiving user traffic through an Internet Gateway and the TL-Web security group. Business data is queried internally from travel-database (Amazon RDS MySQL) located in a Private Subnet protected by the TL-Database security group. The Travel-auto-scaling-group, combined with Web-Travel-AMI and Travel-target, guarantees elastic scalability and continuous user session persistence.

![WEB TRAVEL PLATFORM ON CLOUD](/BC_AWS/images/Sodo.drawio.png)
![WEB TRAVEL PLATFORM ON CLOUD](/BC_AWS/images/Sodo2.drawio.png)

### 4. Technical Implementation
**Implementation Phases**
The project was executed over 10 weeks (conducted regularly every Saturday) across four primary phases:
1. Survey and Source Code Standardization (Weeks 1 – 2): Tested the Web Travel application locally on XAMPP, exported the travel_test.sql database dump, and established centralized version control on GitHub (dt-kien04/du-an-01).
2. Network and Security Setup (Weeks 3 – 4): Provisioned travel-vpc, segmented 2 Public Subnets and 2 Private Subnets, and configured the TL-Web and TL-Database security groups.
3. Database and Web Server Deployment (Weeks 5 – 7): Launched Amazon RDS (travel-database), provisioned the Ubuntu EC2 instance (Web-travel-sv), installed the LAMP stack, cloned source code from GitHub, and established database connectivity.
4. Auto-Scaling Configuration and Operational Optimization (Weeks 8 – 10): Packaged Web-Travel-AMI, configured the Target Group (Travel-target), Launch Template (Travel-template), and Auto Scaling Group, and finalized the graduation thesis documentation.

**Technical Requirements**
Application Tier (Web Tier): Amazon EC2 t3.micro virtual instance running Ubuntu Server 24.04 LTS, configured with Apache2, PHP 8.x, MySQL Client, and Git. Remote administrative access is authenticated via an SSH Key Pair (khoa-travel.pem).
Data Tier (Database Tier): Amazon RDS running MySQL Community Edition on a db.t4g.micro instance with 20 GiB SSD (gp2) storage, public access disabled (Public access = No), and a 1-day automated backup retention period.


### 5. Timeline & Milestones
**Project Timeline**
Preparation Phase (Weeks 1 – 2): Studied AWS cloud fundamentals, activated the 100 Credits account, standardized PHP source code, and pushed the repository to GitHub.

### 8. Expected Outcomes
#### Technical Improvements: 
Successfully deliver a stable, live online tour booking platform on the AWS cloud featuring a highly secure multi-tier network architecture, eliminating single points of failure and enabling seamless auto-scaling under high traffic loads.
#### Long-term Value
Establish a standardized cloud architecture foundation ready for future enterprise upgrades, including offloading static image assets to Amazon S3 + CloudFront, integrating a custom domain via Amazon Route 53 with HTTPS (ACM) encryption, and automating deployments via CI/CD pipelines.