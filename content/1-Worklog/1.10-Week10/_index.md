---
title: "Week 10 Worklog"
date: 2026-10-03
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 10 Objectives:

* Verify system stability and troubleshoot runtime connection errors after server restarts.
* Implement cost-control routines to preserve the allocated AWS Credit budget.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 7   | - Test system recovery after stopping and restarting the EC2 and RDS instances. <br> - Inspect Apache error logs (/var/log/apache2/error.log) and resolve HTTP ERROR 500 database connection issues in php/ket_noi.php. <br> - Verify live table structures inside Amazon RDS using MySQL CLI commands (SHOW TABLES). <br> - Establish a routine to temporarily stop EC2 and RDS instances when idle to conserve the 100 Credits budget. <br> | 03/10/2026   | 03/10/2026      | <https://aws.amazon.com/> |

### Week 10 Achievements:

* Resolved runtime configuration errors and ensured reliable database connectivity upon system restarts.

* Minimized cloud operational expenses and compiled complete visual evidence from the AWS Console for thesis documentation.
