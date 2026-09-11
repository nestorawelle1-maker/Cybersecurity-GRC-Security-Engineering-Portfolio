# Data Security Governance Framework Implementation

## Project Overview

In this project, I worked through the implementation of a Data Security Governance program for an organization that processes employee, customer, financial, and other sensitive information.

My goal was to understand what data the organization had, where it was stored, how it moved, who had access to it, and whether the appropriate controls were in place.

I then used those findings to improve data classification, PII protection, access control, data lifecycle management, third-party risk, SOC 2 readiness, AI data governance, and ongoing monitoring.

The project follows this process:

**Discover → Inventory → Classify → Map → Assess → Remediate → Validate → Monitor**

# 1. Data Discovery

I started by meeting with IT and business owners because I first needed to understand the environment.

I asked questions such as:

* What systems are we using?
* What type of data do we collect?
* Where is the data stored?
* Who owns the data?
* Who has access?
* Which vendors receive the data?
* How does data move between systems?
* How long is it retained?
* Is any of the data being used for analytics or AI?

I documented systems such as cloud platforms, SaaS applications, databases, shared drives, employee endpoints, data platforms, and third-party applications.

### Tools Used

* Microsoft Purview – data discovery, classification, and sensitive-information identification
* Microsoft Excel – initial data inventory and tracking
* Jira – findings, remediation ownership, and tracking
* Vanta – control monitoring and compliance evidence

### What I Identified

There was no centralized inventory showing all sensitive data, its owner, location, classification, and lifecycle.

### What I Did

I created a centralized data inventory and worked with IT and business owners to identify the systems processing sensitive information.

I documented:

**Data → Owner → System → Location → Access → Third Party → Retention → Classification**

This inventory became the foundation for the rest of the assessment.

---

# 2. Data Classification

After discovering the data, I needed to determine its sensitivity.

I established four classification levels:

**Public → Internal → Confidential → Restricted**

Examples:

* Public: Marketing information
* Internal: Internal procedures
* Confidential: Customer contact information and contracts
* Restricted: SSNs, financial information, credentials, API keys, and certain sensitive PII

### Tool Used

**Microsoft Purview**

I used Purview's data classification and sensitive-information capabilities to help identify sensitive data across supported data sources.

### What I Identified

Sensitive information was not consistently classified, meaning employees did not always know what information required stronger protection.

### What I Did

I established classification requirements and worked with data owners to classify information based on sensitivity, business impact, privacy requirements, and regulatory obligations.

I then connected each classification level to specific handling requirements.

---

# 3. Data Flow Mapping

After identifying and classifying the data, I mapped how sensitive information moved.

For example:

**Student/User → Application → Database/Data Platform → Analytics → Authorized Business User**

Another flow could be:

**Employee → HR System → Payroll Provider → Financial Institution**

I looked at:

* Data entering the organization
* Internal transfers
* APIs
* ETL pipelines
* Data warehouses
* Third-party transfers
* Analytics environments
* Backups
* Data deletion

### Tools Used

* Lucidchart – data-flow diagrams
* Microsoft Purview – data discovery and lineage where supported

### What I Identified

Some sensitive information was being copied or transferred between systems without clear ownership or documented handling requirements.

### What I Did

I documented the flows and identified the systems, owners, third parties, and controls involved at each stage.

This allowed me to identify where stronger encryption, access restrictions, monitoring, or retention controls were required.

---

# 4. Access Control Assessment

Next, I reviewed who could access sensitive information.

I compared current access against:

* Job responsibilities
* Business need
* Least privilege
* Role-Based Access Control
* Segregation of duties

### What I Identified

Some users had access beyond what was required for their role.

For example, a Finance user had access to sensitive HR information that was not necessary for their job.

### What I Did

I worked with the data owner and IT to validate whether the access was required.

Where access was unnecessary:

1. The access was removed.
2. The reason for the excessive access was investigated.
3. RBAC rules were reviewed.
4. Similar accounts were checked.
5. The remediation was documented in Jira.
6. The control was retested.

### Tools Used

* Microsoft Entra ID – identity and access management
* Jira – remediation tracking
* Vanta – control/evidence monitoring

### Evidence

* Access reports
* Manager approvals
* Access-review records
* Jira remediation tickets
* Screenshots/configuration evidence

---

# 5. PII Protection Assessment

Because the organization processes sensitive personal information, I specifically assessed how PII was handled.

I reviewed:

* Storage
* Encryption
* Access
* Sharing
* Downloads
* Retention
* Third-party access
* Logging
* Disposal

### What I Identified

Sensitive PII existed in locations where protection was inconsistent.

### What I Did

I worked with the appropriate technical and business teams to move sensitive information toward approved storage locations and establish stronger handling requirements.

Depending on the data classification, controls included:

* Encryption
* MFA
* RBAC
* Least privilege
* DLP
* Logging
* Retention controls

### Tools Used

* Microsoft Purview – sensitive-information discovery/classification and DLP
* Microsoft Entra ID – identity controls
* Vanta – compliance/control monitoring

---

# 6. Data Retention and Lifecycle Management

I reviewed how long sensitive information was being retained.

### What I Identified

Some departments were retaining information without clearly documented retention requirements.

### What I Did

I worked with Legal, Privacy, Compliance, and business owners to establish retention requirements based on:

* Legal requirements
* Regulatory requirements
* Contractual obligations
* Privacy requirements
* Business requirements

The lifecycle became:

**Collect → Use → Store → Share → Archive → Delete**

### Tool Used

Microsoft Purview – retention and data lifecycle capabilities where applicable.

---

# 7. Third-Party Data Risk

I also reviewed vendors that received or processed organizational information.

For each vendor, I asked:

* What data are they receiving?
* Why do they need it?
* Where is it stored?
* Is it encrypted?
* Who can access it?
* Are subprocessors involved?
* How long is it retained?
* What happens when the contract ends?

### Tools Used

* BitSight – external security posture monitoring
* Security questionnaires – vendor control assessment
* Jira – remediation tracking

### What I Identified

Some vendors had access to sensitive information without consistent security evidence or clearly documented data-handling requirements.

### What I Did

I risk-tiered vendors based on the sensitivity of the data and service.

For higher-risk vendors, I reviewed evidence such as:

* SOC 2 Type II
* ISO 27001
* Penetration-test summaries
* Encryption controls
* Incident response
* Business continuity
* Data Processing Agreements
* Security addenda

Any gaps were documented, assigned to an owner, remediated or formally accepted, and tracked to closure.

---

# 8. SOC 2, OHIP and Hi-Trust Readiness

Another part of the project was ensuring that governance controls could be demonstrated through evidence.

I mapped relevant controls to SOC 2, OHIP and Hi-Trust requirements and reviewed whether the organization could prove that controls were operating.

### Tools Used

* Vanta – SOC 2 control monitoring and evidence collection
* Jira – remediation tracking
* Vanta – policies and supporting documentation

### Example

If the organization says:

**"Access to sensitive information is reviewed periodically."**

I should be able to provide:

**Policy → Access Review → Manager Approval → Access Change → Evidence**

If evidence was missing, I documented the gap and worked with the control owner to remediate it.

---

# 9. AI and Advanced Analytics Data Governance

I also included AI because sensitive data can now move into AI and analytics workflows.

Before sensitive organizational data could be used with an AI system, I reviewed:

* What data is being provided?
* Does it contain PII?
* Why is the data needed?
* Is the AI tool approved?
* Will the provider retain the data?
* Can the data be used for model training?
* Who can access prompts and outputs?
* Are prompts or outputs logged?
* Can sensitive information be masked or removed?
* Are third parties involved?

### What I Identified

The organization needed clearer governance around what information employees could submit to AI systems.

### What I Did

I established an AI data-use review process.

Sensitive data required additional review before being used in AI workflows.

Where possible, I required:

* Data minimization
* Masking/redaction
* Approved AI platforms
* Access restrictions
* Logging
* Vendor review
* Human oversight

I aligned the governance approach with the organization's broader privacy and security requirements.

---

# 10. Data Platforms and Analytics

I also considered how governance applied inside data platforms such as data warehouses, ETL pipelines, and environments such as Databricks.

The flow could look like:

**Source System → ETL Pipeline → Data Warehouse/Lakehouse → Analytics/AI → Tableau or Power BI**

At each stage, I reviewed:

* Data classification
* Access
* Encryption
* PII exposure
* Data transformations
* Logging
* Retention
* Data sharing

The purpose was to make sure governance followed the data instead of stopping at the source system.

---

# 11. Governance Metrics and Reporting

I created metrics to help leadership understand whether the program was improving.

Examples included:

### Data Protection Metrics

* Percentage of sensitive data classified
* Percentage of systems included in the data inventory
* Encryption coverage
* DLP findings

### Access Metrics

* Access-review completion
* Excessive-access findings
* MFA adoption
* Privileged-access findings

### Governance Metrics

* Policy adoption
* Outstanding exceptions
* Remediation completion
* Data-owner participation

### Incident Metrics

* Data-handling incidents
* Time to identify an issue
* Time to remediate
* Repeat findings

### Tools Used

* Power BI – governance dashboards and reporting
* Vanta – compliance metrics
* Jira – remediation metrics

---

# 12. Continuous Monitoring

The project did not end after implementation.

I established ongoing monitoring through:

**Monthly reviews**

* Findings
* Security alerts
* Remediation
* Exceptions

**Quarterly reviews**

* Access certification
* Governance metrics
* High-risk vendors
* Data protection issues

**Annual reviews**

* Data inventory
* Classification
* Policies
* Control testing
* Vendor reassessment
* Training
* Audit evidence

---

# 13. Final Outcome

The organization moved from limited visibility into its data toward a structured Data Security Governance program.

The program connected:

**Data Discovery → Classification → Data Flow → Risk Assessment → Remediation → Control Implementation → Evidence → Monitoring**

The project produced:

* Data Inventory
* Data Classification Framework
* Data Flow Diagrams
* PII Handling Requirements
* Access Control Framework
* Data Retention Requirements
* Third-Party Data Assessments
* AI Data Governance Requirements
* SOC 2 Control Evidence
* Governance Metrics
* Remediation Tracking
* Continuous Monitoring Process

The most important lesson from this project was that data governance is not just about creating policies.

It is about understanding where the data is, identifying the risk, translating policy into practical requirements, working with technical teams to implement the appropriate controls, collecting evidence, and continuously verifying that those controls are working.
