# SimplifyIAM IAM Implementation Portfolio
**Cohort:** SimplifyIAM Live Cohort 1 &ensp;&ensp;&ensp;&ensp;**Name:** Jonathan Cacao &ensp;&ensp;&ensp;&ensp;**LinkedIn:** [LinkedIn URL] &ensp;&ensp;&ensp;&ensp;**Completed:** May 2026 - June 2026 (In-progress)

## Overview ##
SimplifyTech is 200-person technology company with a manual identity problem. 
HR updates a spreadsheet. IT manually creates accounts one by one. Nobody knows who has access to what.
The objective is to design and build their identity infrastructure from scratch over five consecutive Saturdays.

## What SimplifyTech Actually Needs ##
After conversation with the CISO, the following requirements needs to addressed.
| Identity Source | Target Systems | Lifecycle Automation | Audit Trail |
|---|---|---|---|
| HR spreadsheet today. Need a system of record that the IGA platform can read automatically — no manual exports. | Active Directory (or equivalent) for all staff accounts. Every employee must have a directory account provisioned on **Day 1**. | Joiner, Mover, and Leaver events must be triggered automatically by **HR events** — not IT tickets. Zero manual provisioning. | SOC 2 requires evidence of: who had access, when it was granted, when it was removed, and who approved it. |

## What I Built
Over five live Saturday sessions I will build a complete IAM environment from scratch using a simple HRIS web-based app, MidPoint, OpenLDAP, and Auth0. The environment runs on a dedicated cloud server and replicates how IAM provisioning works in a real enterprise engagement.

This repository documents my configuration, screenshots, and decisions for each session. It is intended as portfolio evidence for IAM implementation roles.

## Environment
| Component | Purpose |
| ----------- | --------|
| midPoint | IGA platform - identity lifecycle, provisioning, reconciliation |
| SimplifyHR (Flask) | HR source of truth - simulates enterprise HRIS |
| OpenLDAP | Target directory - user accounts provisioned here |
| Auth0 | Access management - OIDC and SAML federation |

## Session Deliverables
### Saturday 1 - Architecture and Environment
Session date: May 9, 2026
- [ ] Architecture diagram or description committed
```mermaid
flowchart LR
    HRIS["SimplifyHR\nHR system of record"]
    
    subgraph MidPoint["SimplifyIAM"]
        direction TB
        Schema["Schema mapping"]
        Roles["Role assignment"]
        Policy["Policy enforcement"]
    end
    
    OpenLDAP["OpenLDAP\nAccount directory"]

    HRIS -->|"HR events\nHire · Transfer · Terminate\nCSV connector"| MidPoint
    MidPoint -->|"Provision / Deprovision\nCreate · Modify · Disable\nLDAP connector"| OpenLDAP
```
- **SimplifyHR** fires HR events (hire, transfer, terminate) through an HR connector into SimplifyIAM (Midpoint)
- **SimplifyIAM** is the brain which handles the schema mapping, role assignment, and policy enforcement
- **OpenLDAP** receives the provisioning instructions via an LDAP connector and creates, modifies, or disables accounts accordingly
  
- [ ] Screenshot: midPoint Screens<br>
![SimplifyHR dashboard](./images/Midpoint_users.png)<br><br><br>

- [ ] Screenshot: SimplifyHR dashboard running<br>
![SimplifyHR dashboard](./images/SimplifyHR%20dashboard.png)<br><br><br>

- [ ] Screenshot: OpenLDAP screens and OU structure<br>
![SimplifyHR dashboard](./images/OpenLDAP.png)<br><br><br>

**What I built:** 
- Provisioned a Linux VM in the cloud and installed all three components (HRIS application, MidPoint IGA, and OpenLDAP), each running on their designated ports
- Verified all services were operational via SSH, confirming connectivity and port availability before beginning design work
- Defined the overall IAM architecture covering the Joiner-Mover-Leaver (JML) lifecycle and the identity data flow from HR source (CSV) through MidPoint to the target OpenLDAP directory
- Specified the provisioning approach: CSV connector for HR data ingestion, outbound attribute mappings for account provisioning, and RBAC enforced via MidPoint roles and inducements

**What I Learned:**
- 
  
**Resume bullet:** Deployed a multi-component IAM environment including midPoint, an HR source simulator, and LDAP directory on a cloud server — verified end-to-end connectivity before first provisioning run<br><br>


### Saturday 2 - Joiner Workflow
Session date: May 16, 2026
- [ ] HR source connector configuration (screenshot or XML snippet)
- [ ] Correlation rule definition (screenshot or XML snippet)
- [ ] Inbound mapping table (screenshot)
- [ ] Screenshot: New Joiner account in OpenLDAP after reconciliation

**What I built:** [Fill in - 2 sentences max]

**Resume bullet:** [Your bullet here]


### Saturday 3 - Mover and Leaver Workflows
Session date: May 23, 2026
- [ ] Role definitions created (screenshot or XML snippet)
- [ ] Mover workflow configuration (screenshot)
- [ ] Screenshot: Robert Klein account disabled/deleted after leaver trigger
- [ ] Reconciliation results (screenshot)

**What I built:** [Fill in - 2 sentences max]

**Resume bullet:** [Your bullet here]


### Saturday 4 - Access Management
- [ ] Auth0 OIDC application configuration (screenshot)
- [ ] SAML integration SP and IdP config (screenshot)
- [ ] SAML assertion screenshot (redact any sensitive values)
- [ ] JWT claims screenshot

**What I built:** [Fill in - 2 sentences max]

**Resume bullet:** [Your bullet here]


### Saturday 5 - Career Preparation
- [ ] Final resume bullets section (5 bullets, one per session)
- [ ] LinkedIn before and after headline
- [ ] Mock interview reflection

**Resume bullets (copy these to your CV):**

1. [Saturday 1 bullet]
2. [Saturday 2 bullet]
3. [Saturday 3 bullet]
4. [Saturday 4 bullet]
5. [Saturday 5 bullet]


## My Transformation
**Where I started:** [Role, experience level, what you could not explain or do before the cohort]

**Where I am now:** [What you built, what you can demo, what you can now explain in an interview]

**Roles I am targeting:** [Job titles, geography, companies if relevant]



