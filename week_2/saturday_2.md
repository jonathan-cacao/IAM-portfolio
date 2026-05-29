## Saturday 2 - Joiner Workflow
Session Date : May 16, 2026

### Phase 1: HR Source to Midpoint Identity Feed
Establishes the HR system as an authoritative identity source within MidPoint. This phase configures the CSV connector resource object, defines inbound attribute mappings, and sets up correlation and synchronization policies. Employee records from the HRIS are imported into MidPoint as focus (user) objects, with attributes such as name, employee number, and status reflected in the MidPoint Users page. No target provisioning is performed in this phase.

**Attribute Mapping:**

| CSV Attribute | Expression | midPoint Focus Object | 
| ---------------| -----------| ----------------------|
| empid | as is | name (direct - empid becomes the username) | 
| empid | script | [emailAddress](./scripts/emailAddress) |
| firstname | as is | givenName | 
| lastname | as is | familyName | 
| department | as is | organizationalUnit | 
| costcenter | as is | costCenter | 
| status | script | [activation/administrativeStatus](./scripts/status) |
<br>

**What I built:**
- configured the CSV connector resource and test connectivity 
- configured and saved seven inbound mappings
- configured three synchronization mappings
- defined correlation rule set - Item=name, Exact match 
- Ran reconciliation to create focus objects in Midpoint
- Display all employees as LINKED using Data Preview<br><br>

**Screenshots:**

[CSV Connector resource](./images/HR%20source%20connector%20configuration.png)

[Seven Inbound mappings](./images/seven%20inbound%20mappings.png)

[Three Synchronization mappings](./images/synchronization.png)

[Correlation Rule Set](./images/correlation%20rule%20set.png)

[Reconciliation to Create Focus Objects in Midpoint](./images/focus%20objects(users)%20in%20midpoint.png)

[Data preview for LINKED employees](./images/Data%20preview.png)


### Phase 2: MidPoint to OpenLDAP Account Provisioning
Configures OpenLDAP as a target resource within MidPoint. This phase establishes the LDAP connector resource, outbound attribute mappings, and synchronization reactions. Central to this phase is the Employee role and its inducement — the critical link that indirectly assigns an OpenLDAP account construction to every user holding that role. Without inducement, no provisioning occurs. Correlation maps existing LDAP accounts to their MidPoint owners via employee number. Reconciliation then enforces full alignment, ensuring every MidPoint focus object has a corresponding, correctly attributed OpenLDAP directory account.

**Attribute Mapping:**
| Midpoint Focus Object attribute | Expression | OpenLDAP |
|----------------------------------| ----------- | -------- |
| givenName | as is | givenName |
| familyName | as is | sn |
| familyName, givenName | script | cn |
| name | script | dn |
|emailAddress | as is | mail |
|costCenter | as is | departmentNumber |
| employeeNumber | as is | employeeNumber | 
<br>

**What I built:**
- created an OpenLDAP resource using Ldap connector
- configured Object type: inetOrgPerson with nsAccount auxiliary class
- Seven outbound mappings: givenName, sn, cn (script), DN (script), mail, departmentNumber, employeeNumber
- DN script that routes active users to ou=people and terminated users to ou=inactive
- defined Synchronization reactions and correlation rule on OpenLDAP resource
- updated Employee role with OpenLDAP construction inducement
- provisioned accounts to ou=people automatically via reconciliation


