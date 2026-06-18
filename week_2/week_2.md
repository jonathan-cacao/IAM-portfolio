## Week 2 - Joiner Workflow
Session Date : May 16, 2026

### Phase 1: HRIS to Midpoint

**What I built:**
- configured the CSV connector (SimplifyHR resource)- to ingest data from CSV file to midpoint 
- configured inbound mappings -define how attribute values from the CSV file are transformed and written into MidPoint user properties
- configured synchronization settings- what action MidPoint should take when a resource account is found to be in a particular state — such as creating a new user when unmatched, or updating an existing one when linked. action taken is based on correlation result
- defined correlation rule - tells MidPoint how to match incoming resource accounts (e.g. from the CSV) to existing MidPoint users, preventing duplicates by linking records that belong to the same person rather than creating a new user. 
- Ran reconciliation to create focus objects in Midpoint<br><br>

**Screenshots:**

CSV Connector resource
![csv connector](<HR source connector configuration.png>)<br><br>

Inbound mappings
![inbound mappings](<seven inbound mappings.png>)<br><br>

Synchronization settings
![Synchronization](<synchronization.png>)<br><br>

Correlation Rule
![Correlation Rule](<correlation rule set.png>)<br><br>

Reconciliation to Create Focus Objects in Midpoint
![Reconciliation](<focus objects(users) in midpoint.png>)<br><br>

### Phase 2: MidPoint to OpenLDAP Account Provisioning

**What I built:**
- created an OpenLDAP connector - bridges MidPoint and the OpenLDAP directory server, allowing MidPoint to provision, update, and delete user accounts in LDAP based on role assignments and policy — in this case, triggered by the Employee role inducement.
- outbound mappings: givenName, sn, cn (script), DN (script), mail, departmentNumber, employeeNumber
- DN script that routes active users to ou=people and terminated users to ou=inactive
- defined Synchronization reactions and correlation rule on OpenLDAP resource
- updated Employee role with OpenLDAP construction inducement (the missing link) - will automatically provision a Default account on the OpenLDAP resource
- provisioned accounts to ou=people automatically via reconciliation<br><br>

**Screenshots:**

LDAP connector resource
![LDAP connector](<LDAP connector configuration.png>)<br><br>

Outbound mappings
![Outbound mappings](<outbound mappings.png>)<br><br>

OpenLDAP construction inducement
![OpenLDAP construction inducement](<role inducement.png>)<br><br>

New OpenLDAP accounts provisioned
![New OpenLDAP accounts provisioned](<7 Open LDAP accounts created.png>)






