---
title: "Week 5 Worklog"
date: 2026-08-29
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 5 Objectives:

* Master the operation of stateful firewalls on AWS.
* Configure strict inbound and outbound traffic control rules for each application tier.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 7   | - Study the working principles of Inbound and Outbound Rules in AWS Security Groups. <br> - Create the Web Server Security Group (TL-Web): open HTTP (80) and HTTPS (443) to public traffic, and restrict SSH (22) strictly to the personal IP address. <br> - Create the Database Security Group (TL-Database): allow MySQL (3306) traffic exclusively from TL-Web. <br> | 29/08/2026 | 29/08/2026      | <https://aws.amazon.com/> |

### Week 5 Achievements:

* Completed a two-tier network defense mechanism using TL-Web and TL-Database.

* Enforced the principle of least privilege, completely blocking unauthorized external Internet access to the database tier.
