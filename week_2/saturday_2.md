## Saturday 2 - Joiner Workflow
Session Date : May 16, 2026

### Phase 1: HRIS to Midpoint

**What I built:**
- configured the CSV connector (SimplifyHR resource)- to ingest data from CSV file to midpoint 
- configured inbound mappings -define how attribute values from the CSV file are transformed and written into MidPoint user properties
- configured synchronization settings- what action MidPoint should take when a resource account is found to be in a particular state — such as creating a new user when unmatched, or updating an existing one when linked. action taken is based on correlation result
- defined correlation rule - tells MidPoint how to match incoming resource accounts (e.g. from the CSV) to existing MidPoint users, preventing duplicates by linking records that belong to the same person rather than creating a new user. 
- Ran reconciliation to create focus objects in Midpoint<br><br>

**Screenshots:**

[CSV Connector resource](./images/HR%20source%20connector%20configuration.png)

[Inbound mappings](./images/seven%20inbound%20mappings.png)

[Synchronization settings](./images/synchronization.png)

[Correlation Rule](./images/correlation%20rule%20set.png)

[Reconciliation to Create Focus Objects in Midpoint](./images/focus%20objects(users)%20in%20midpoint.png)


### Phase 2: MidPoint to OpenLDAP Account Provisioning

**What I built:**
- created an OpenLDAP connector - bridges MidPoint and the OpenLDAP directory server, allowing MidPoint to provision, update, and delete user accounts in LDAP based on role assignments and policy — in this case, triggered by the Employee role inducement.
- outbound mappings: givenName, sn, cn (script), DN (script), mail, departmentNumber, employeeNumber
- DN script that routes active users to ou=people and terminated users to ou=inactive
- defined Synchronization reactions and correlation rule on OpenLDAP resource
- updated Employee role with OpenLDAP construction inducement (the missing link) - will automatically provision a Default account on the OpenLDAP resource
- provisioned accounts to ou=people automatically via reconciliation<br><br>

**Screenshots:**

[LDAP connector resource](./images/LDAP%20connector%20configuration.png)

[Outbound mappings](./images/outbound%20mappings.png)

[OpenLDAP construction inducement](./images/role%20inducement.png)

[New OpenLDAP accounts provisioned](./images/7%20Open%20LDAP%20accounts%20created.png)







