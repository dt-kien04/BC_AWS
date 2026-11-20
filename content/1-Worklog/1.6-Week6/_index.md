---
title: "Week 6 Worklog"
date: 026-09-05
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 6 Objectives:

* Understand the advantages of managed database services over manual database installations.
* Provision and secure a MySQL database inside the private network tier.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 7   | - Study Amazon RDS features, storage options, and backup configurations. <br> - Create a DB Subnet Group comprising the 2 Private Subnets of travel-vpc. <br> - Launch a MySQL database instance (travel-database, db.t4g.micro) with public access disabled (Public access = No). <br> - Attach the TL-Database security group and retrieve the database connection Endpoint. <br> | 05/09/2026   | 05/09/2026      | <https://aws.amazon.com/> |

### Week 6 Achievements:
* Successfully provisioned the travel-database instance in an Available state inside the Private Subnet.

* Obtained the internal RDS Endpoint and initialized an empty travel_test database ready for data migration.
