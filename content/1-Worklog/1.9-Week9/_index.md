---
title: "Week 9 Worklog"
date: 2026-09-26
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 9 Objectives:

* Architect a High Availability (HA) and automatically scalable web system.
* Eliminate single points of failure inherent in traditional single-server setups.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 7   | - Package the configured Web-travel-sv instance into a golden image (Web-Travel-AMI). <br> - Create a Target Group (Travel-target) and enable Sticky Sessions to preserve user login states. <br> - Create a Launch Template (Travel-template) utilizing the custom AMI. <br> - Configure an Auto Scaling Group (Travel-auto-scaling-group) spanning 2 Public Subnets. <br> | 26/09/2026   | 26/09/2026      | <https://aws.amazon.com/> |

### Week 9 Achievements:

* Completed an elastic auto-scaling architecture capable of scaling between 0 and 3 instances based on demand.

* Ensured uninterrupted user session persistence across distributed server instances.
