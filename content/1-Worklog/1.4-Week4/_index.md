---
title: "Week 4 Worklog"
date: 2026-08-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---



### Week 4 Objectives:

* Understand network segmentation and routing mechanisms in the AWS cloud environment.
* Establish a multi-tier, secure virtual private network architecture (Public and Private Subnets) across multiple Availability Zones.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 7   | - Study Amazon VPC architecture, CIDR Blocks, Subnets, Internet Gateways, and Route Tables. <br> - Create a custom Virtual Private Cloud named travel-vpc (10.0.0.0/16) across 2 Availability Zones (ap-southeast-1a and 1b). <br> - Provision 2 Public Subnets and 2 Private Subnets. <br> - Enable auto-assign public IPv4 addresses for the Public Subnets. | 22/08/2026 | 22/08/2026      | <https://aws.amazon.com/> <br> <https://docs.aws.amazon.com/vpc/> <br> <https://docs.aws.amazon.com/security/> |

### Week 4 Achievements:

* Successfully deployed an isolated network infrastructure (travel-vpc) with clear separation between the public tier (hosting the Web Server) and the private tier (isolating the Database).

* Optimized networking costs by utilizing an Internet Gateway for Public Subnets and eliminating unnecessary NAT Gateways.
