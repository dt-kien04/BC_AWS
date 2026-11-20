---
title: "Workshop"
date: 2026-11-15
weight: 5
chapter: false
pre: " <b> 5. </b> "
---


# DEPLOYING A HIGH-AVAILABILITY AND AUTO-SCALING WEB TRAVEL APPLICATION ON AWS

#### Overview

Modern cloud architecture resolves the overloading and Single Point of Failure (SPOF) challenges of traditional physical servers by clearly decoupling the networking, application, and database tiers.

In this lab, we will learn how to design, configure, and operate a complete infrastructure on AWS for the Web Travel online tour booking application (PHP/MySQL). The system is deployed within an isolated multi-Availability Zone (Multi-AZ) environment, ensuring robust data security and seamless auto-scaling capabilities when user traffic surges.

We will build and integrate three core service layers to operate an enterprise-standard web application:
+ **Virtual Private Cloud & Security (Amazon VPC & Security Groups)** - Provision the travel-vpc network infrastructure separating Public Subnets and Private Subnets, strictly controlling traffic via two firewall layers: TL-Web and TL-Database.
+ **Managed Database Service (Amazon RDS)** - Deploy a MySQL database (travel-database) completely isolated inside a Private Subnet to safeguard business data and communicate internally with the application server.
+ **Application Server & Auto Scaling (EC2, AMI & Auto Scaling)** – Host the source code on an Ubuntu EC2 instance (Web-travel-sv), package it into a golden image (Web-Travel-AMI), and configure Travel-auto-scaling-group to dynamically orchestrate compute resources.

#### Nội dung

1. [Introduction](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequiste/)
3. [Setting up VPC Networking and Amazon RDS](5.3-S3-vpc/)
4. [Deploying the Web Server on EC2 and Testing the Application](5.4-S3-onprem/)
5. [Packaging AMI and Configuring Auto Scaling Group](5.5-Policy/)
6. [Resource Cleanup](5.6-Cleanup/)