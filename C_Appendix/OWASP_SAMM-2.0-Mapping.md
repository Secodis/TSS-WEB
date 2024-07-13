# OWASP SAMM 2.0 Mapping

TSS-WEB 2.0 generally covers a large number of OWASP SAMM 2.0 security practices, especially from maturity level 1 & 2. We’ve added additional requirements to TSS-WEB where this was possible. However, the scope of TSS-WEB is another as OWASP SAMM. 

Whereas TSS-WEB describes a security dev standard for particular development units, OWASP SAMM focuses on the entire organization. Therefore, organization-wide tasks that have to be done by the IT security government function and that are therefore mostly within business function Governance are not covered in TSS-WEB. Also, whereas TSS-WEB describes a robust enterprise standard, OWASP SAMM provides three level of maturity for all objectives.

TSS-WEB can be helpful for implementing a large number of requirements (= those that affect the dev organization) of OWASP SAMM.

## Detailed Coverage

| Business Function | Security Practices | Stream | Mat. Level | Requirement | TSS-WEB Coverage |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | 
| Governance | Strategy & Metrics | All | All | All | No. Not scope of this standard, task for IT security function. |
| Governance | Policy & Compliance | Stream A Policy & Standards | 1 | Determine a security baseline representing organization’s policies and standards. | No. But you can use TSS-WEB as a basis to describe your organization-specific baseline.  |
| Governance | Policy & Compliance | Stream A Policy & Standards | 2 | Develop security requirements applicable to all applications. | Yes. TSS-WEB covers this for Web-based applications. |
| Governance | Policy & Compliance | Stream A Policy & Standards | 3 | Measure and report on the status of individual application’s adherence to policies and standards. | No. Not scope of this standard, task for IT security function. | 
| Governance | Policy & Compliance | Stream B Compliance Management | 1 | Identify 3rd-party compliance drivers and requirements and map to existing policies and standards | This cannot be covered by TSS-WEB, since we don’t know your specific compliance drivers. But you can use TSS-WEB and integrate yours into it. |
| Governance | Policy & Compliance | Stream B Compliance Management | 2 | Publish compliance-specific application requirements and test guidance | No. This cannot be covered by TSS-WEB, since we don’t know your specific compliance drivers. But you can use TSS-WEB and integrate yours into it. |
| Governance | Policy & Compliance | Stream B Compliance Management | 3 | Measure and report on individual application’s compliance with 3rd party requirements | No. This cannot be covered by TSS-WEB, since we don’t know your specific compliance drivers. But you can use TSS-WEB and integrate yours into it. |
| Governance | Education & Guidance | Stream A Training and Awareness | 1 | Provide security awareness training for all personnel involved in software development | Yes. See “General Requirements” athttps://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338|
| Governance | Education & Guidance | Stream A Training and Awareness | 2 | Offer technology and role-specific guidance, including security nuances of each language and platform | Yes. See “General Requirements” athttps://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Governance | Education & Guidance | Stream A Training and Awareness | 3 | Standardized in-house guidance around the organization’s secure software development standards. | No. This cannot be covered by TSS-WEB, since we don’t know your specific compliance drivers. But you can use TSS-WEB and integrate yours into it. |
| Governance | Education & Guidance |Stream A Training and Awareness | 1 | Yes. See “General Requirements” athttps://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Governance | Education & Guidance |Stream A Training and Awareness | 2 | Partially. Although establishing such a community is a task for a IT security function, participation at it is described as role duties for a “security champion” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/335675582  |
| Governance | Education & Guidance |Stream A Training and Awareness | 3 | Partially. Although establishing such a community is a task for a IT security function, participation at it is described as role duties for a “security champion” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/335675582  |
| Design | Threat Assessment | Stream A Application Risk Profile | 1 | A basic assessment of the application risk is performed to understand likelihood and impact of an attack. | Yes. See “Security within change management & agile development” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Design | Threat Assessment | Stream A Application Risk Profile | 2 | Understand the risk for all applications in the organization by centralizing the risk profile inventory for stakeholders. | No. Not covered since not scope of a standard but local risk management procedures in development are defined at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Design | Threat Assessment | Stream A Application Risk Profile | 3 | Periodically review application risk profiles at regular intervals to ensure accuracy and reflect current state. | This is defined as a team responsible in https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Design | Threat Assessment | Stream B Threat Modeling | 1 | Perform best-effort, risk-based threat modeling using brainstorming and existing diagrams with simple threat checklists. | See “Security within change management & agile development” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 
| Design | Threat Assessment | Stream B Threat Modeling | 2 | Standardize threat modeling training, processes, and tools to scale across the organization. | No. Not in scope of TSS-WEB. Should be described separately and linked into your own standard. |
| Design | Threat Assessment | Stream B Threat Modeling | 3 Continuously optimization and automation of your threat modeling methodology.  | No. Not in scope of TSS-WEB. Should be described 
