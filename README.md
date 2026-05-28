# SimplifyIAM IAM Implementation Portfolio
**Cohort:** SimplifyIAM Live Cohort 1 &ensp;&ensp;&ensp;&ensp;**Name:** Jonathan Cacao &ensp;&ensp;&ensp;&ensp;**LinkedIn:** [LinkedIn URL] &ensp;&ensp;&ensp;&ensp;**Completed:** May 2026 - June 2026 (In-progress)

## Overview ##
SimplifyTech is 200-person technology company with a manual identity problem. 
HR updates a spreadsheet. IT manually creates accounts one by one. Nobody knows who has access to what.
The objective is to design and build their identity infrastructure from scratch over five consecutive Saturdays.

## What SimplifyTech Actually Needs 
After conversation with the CISO, the following requirements needs to addressed.
| Identity Source | Target Systems | Lifecycle Automation | Audit Trail |
|---|---|---|---|
| HR spreadsheet today. Need a system of record that the IGA platform can read automatically — no manual exports. | Active Directory (or equivalent) for all staff accounts. Every employee must have a directory account provisioned on **Day 1**. | Joiner, Mover, and Leaver events must be triggered automatically by **HR events** — not IT tickets. Zero manual provisioning. | SOC 2 requires evidence of: who had access, when it was granted, when it was removed, and who approved it. |

## What I Built
Over five live Saturday sessions I built a complete IAM environment from scratch using a simple HRIS web-based app, MidPoint, OpenLDAP, and Auth0. The environment runs on a dedicated cloud server and replicates how IAM provisioning works in a real enterprise engagement.

This repository documents my configuration, screenshots, and decisions for each session. It is intended as portfolio evidence for IAM implementation roles.

## Environment
| Component | Purpose |
| ----------- | --------|
| midPoint | IGA platform - identity lifecycle, provisioning, reconciliation |
| SimplifyHR (Flask) | HR source of truth - simulates enterprise HRIS |
| OpenLDAP | Target directory - user accounts provisioned here |
| Auth0 | Access management - OIDC and SAML federation |

## Session Deliverables
[Saturday 1 - Architecture and Environment](./week_1/saturday_1.md)<br> 
[Saturday 2 - Joiner Workflow](./week_2/saturday_2.md)<br> 
[Saturday 3 - Mover and Leaver Workflows](./week_3/saturday_3.md)<br> 
[Saturday 4 - Access Management](./week_4/saturday_4.md)<br> 
[Saturday 5 - Career Preparation](./week_5/saturday_5.md)<br> 





