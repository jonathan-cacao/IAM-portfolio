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







