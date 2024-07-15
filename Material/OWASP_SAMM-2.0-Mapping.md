# OWASP SAMM 2.0 Mapping

TSS-WEB 2.0 generally covers a large number of OWASP SAMM 2.0 security practices, especially from maturity level 1 & 2. We’ve added additional requirements to TSS-WEB where this was possible. However, the scope of TSS-WEB is another as OWASP SAMM. 

Whereas TSS-WEB describes a security dev standard for particular development units, OWASP SAMM focuses on the entire organization. Therefore, organization-wide tasks that have to be done by the IT security government function and that are therefore mostly within business function Governance are not covered in TSS-WEB. Also, whereas TSS-WEB describes a robust enterprise standard, OWASP SAMM provides three level of maturity for all objectives.

TSS-WEB can be helpful for implementing a large number of requirements (= those that affect the dev organization) of OWASP SAMM.

* [Governance](#governance-business-function)
* [Design](#design-business-function)
* [Implemnentation](#implementation-business-function)
* [Verification](#verification-business-function)
* [Operation](#operation-business-function)

## Governance Business Function

| Security Practices | Stream | Mat. Level | Requirement | TSS-WEB Coverage |
| ------------- | ------------- | ------------- | ------------- | ------------- | 
| Strategy & Metrics | All | All | All | No. Not scope of TSS-WEB task for IT security function. |
| Policy & Compliance | Stream A Policy & Standards | 1 | Determine a security baseline representing organization’s policies and standards. | No. But you can use TSS-WEB as a basis to describe your organization-specific baseline.  |
| Policy & Compliance | Stream A Policy & Standards | 2 | Develop security requirements applicable to all applications. | Yes. TSS-WEB covers this for Web-based applications. |
| Policy & Compliance | Stream A Policy & Standards | 3 | Measure and report on the status of individual application’s adherence to policies and standards. | No. Not scope of TSS-WEB, task for IT security function. | 
| Policy & Compliance | Stream B Compliance Management | 1 | Identify 3rd-party compliance drivers and requirements and map to existing policies and standards | This cannot be covered by TSS-WEB, since we don’t know your specific compliance drivers. But you can use TSS-WEB and integrate yours into it. |
| Policy & Compliance | Stream B Compliance Management | 2 | Publish compliance-specific application requirements and test guidance | No. This cannot be covered by TSS-WEB, since we don’t know your specific compliance drivers. But you can use TSS-WEB and integrate yours into it. |
| Policy & Compliance | Stream B Compliance Management | 3 | Measure and report on individual application’s compliance with 3rd party requirements | No. This cannot be covered by TSS-WEB, since we don’t know your specific compliance drivers. But you can use TSS-WEB and integrate yours into it. |
| Education & Guidance | Stream A Training and Awareness | 1 | Provide security awareness training for all personnel involved in software development | Yes. See “General Requirements” athttps://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338|
| Education & Guidance | Stream A Training and Awareness | 2 | Offer technology and role-specific guidance, including security nuances of each language and platform | Yes. See “General Requirements” athttps://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Education & Guidance | Stream A Training and Awareness | 3 | Standardized in-house guidance around the organization’s secure software development standards. | No. This cannot be covered by TSS-WEB, since we don’t know your specific compliance drivers. But you can use TSS-WEB and integrate yours into it. |
| Education & Guidance |Stream A Training and Awareness | 1 | Identify a “Security Champion” within each development team. | Yes. See “General Requirements” athttps://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Education & Guidance |Stream A Training and Awareness | 2 | Develop a secure software center of excellence promoting thought leadership among developers and architects. | Partially. Although establishing such a community is a task for a IT security function, participation at it is described as role duties for a “security champion” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/335675582  |
| Education & Guidance |Stream A Training and Awareness | 3 | Build a secure software community including all organization people involved in software security. | Partially. Although establishing such a community is a task for a IT security function, participation at it is described as role duties for a “security champion” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/335675582  |

##  Design Business Function

| Security Practices | Stream | Mat. Level | Requirement | TSS-WEB Coverage |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| Threat Assessment | Stream A Application Risk Profile | 1 | A basic assessment of the application risk is performed to understand likelihood and impact of an attack. | Yes. See “Security within change management & agile development” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Threat Assessment | Stream A Application Risk Profile | 2 | Understand the risk for all applications in the organization by centralizing the risk profile inventory for stakeholders. | No. Not covered since not scope of a standard but local risk management procedures in development are defined at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Threat Assessment | Stream A Application Risk Profile | 3 | Periodically review application risk profiles at regular intervals to ensure accuracy and reflect current state. | This is defined as a team responsible in https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Threat Assessment | Stream B Threat Modeling | 1 | Perform best-effort, risk-based threat modeling using brainstorming and existing diagrams with simple threat checklists. | See “Security within change management & agile development” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 
| Threat Assessment | Stream B Threat Modeling | 2 | Standardize threat modeling training, processes, and tools to scale across the organization. | No. Not in scope of TSS-WEB. Should be described separately and linked into your own standard. |
| Threat Assessment | Stream B Threat Modeling | 3 | Continuously optimization and automation of your threat modeling methodology.  | No. Not in scope of TSS-WEB. Should be described | 
| Security Requirements | Stream A Software Requirements | 1 | High-level application security objectives are mapped to functional requirements. | Yes. See “General Requirements” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 | 
| Security Requirements | Stream A Software Requirements | 2 | Structured security requirements are available and utilized by developer teams. | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/360467 |
| Security Requirements | Stream A Software Requirements | 3 | Build a requirements framework for product teams to utilize. | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/360467 |
| Security Requirements | Stream B Compliance Management | 1 | Evaluate the supplier based on organizational security requirements. | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/294930 |
| Security Requirements | Stream B Compliance Management | 2 | Build security into supplier agreements in order to ensure compliance with organizational requirements. | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/294930 |
| Security Requirements | Stream B Compliance Management | 3 | Ensure proper security coverage for external suppliers by providing clear objectives. | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/294930 |
| Security Architecture | Stream Architecture  | 1 | Teams are trained on the use of basic security principles during design. | Yes. See “General Requirements” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Security Architecture | Stream Architecture  | 2 | Establish common design patterns and security solutions for adoption. | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/327729/8.1+General+Principles |
| Security Architecture | Stream Architecture  | 3 | Reference architectures are utilized and continuously evaluated for adoption and appropriateness. | No. Not scope of TSS-WEB. This is a responsibility  of architectural board. |
| Security Architecture | Stream B Technology Management | 1 | Elicit technologies, frameworks and integrations within the overall solution to identify risk. | No. Not scope of TSS-WEB. This is a responsibility  of 
| Security Architecture | Stream B Technology Management | 2 | Standardize technologies and frameworks to be used throughout the different applications | No. Not scope of TSS-WEB. This is a responsibility  of 
| Security Architecture | Stream B Technology Management | 3 | Impose the use of standard technologies on all software development. | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/65878. Also a responsibility of an architectural board. |

##  Implementation Business Function

| Security Practices | Stream | Mat. Level | Requirement | TSS-WEB Coverage |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| Secure Build | Stream A Build Process | 1 | Yes. Create a formal definition of the build process so that it becomes consistent and repeatable. | See “Secure build & deployment” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Secure Build | Stream A Build Process | 2 | Yes. Automate your build pipeline and secure the used tooling. Add security checks in the build pipeline. | Yes. See “Secure build & deployment” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 | 
| Secure Build | Stream A Build Process | 3 | Define mandatory security checks in the build process and ensure that building non-compliant artifacts fails. | Yes. See “Secure build & deployment” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Secure Build | Stream B Software Dependencies | 1 | Create records with Bill of Materials of your applications and opportunistically analyze these. | Yes. See “Security of 3rd party dependencies” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Secure Build | Stream B Software Dependencies | 2 | Evaluate used dependencies and ensure timely reaction to situations posing risk to your applications. | Yes. See “Security of 3rd party dependencies” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Secure Build | Stream B Software Dependencies | 3 | Analyze used dependencies for security issues in a comparable way to your own code. | Yes. See “Security of 3rd party dependencies” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 , and reference to metrics in https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 |
| Seure Deployment | Stream A Deployment Process | 1 | Formalize the deployment process and secure the used tooling and processes | Yes, see “Secure build & deployment” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Seure Deployment | Stream A Deployment Process | 2 | Automate the deployment process over all stages and introduce sensible security verification tests. | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368, “Utilize automated security testing tools” |
| Seure Deployment | Stream A Deployment Process | 3 | Automatically verify integrity of all deployed software, indenendently on whether it's internally or externally developed. | Yes, see “Secure build & deployment” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Seure Deployment | Stream B Secret Management | 1 | Introduce basic protection measures to limit access to your production secrets. | See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/341016854 |
| Seure Deployment | Stream B Secret Management | 2 | Inject secrets dynamically during deployment process from hardened storages and audit all human access to them | Yes, see “Secure build & deployment” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 | 
| Seure Deployment | Stream B Secret Management | 3 | Improve the lifecycle of application secrets by regularly generating them and by ensuring proper use. | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/341016854 |
| Defect Management | Stream A Defect Tracking | 1 | Introduce a structured tracking of security defects and make knowledgeable decisions based on this information. | See “Defect tracking” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 |
| Defect Management | Stream A Defect Tracking | 2 | Rate all security defects over the whole organization consistently and define SLAs for particular severity classes. | Not scope of TSS-WEB, task for IT security function. |
| Defect Management | Stream A Defect Tracking | 3 | Enforce the predefined SLAs and integrate your defect management system with other relevant tooling. | No. Not in scope of TSS-WEB; task for IT security function. |
| Defect Management | Stream B Metrics and Feedback | 1 | Regularly go over previously recorded security defects and derive quick wins from basic metrics. | Yes. See “Defect tracking” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 | 
| Defect Management | Stream B Metrics and Feedback | 2 | Collect standardized defect management metrics and use these also for prioritization of centrally driven initiatives. | Not scope of TSS-WEB, task for IT security function. |
| Defect Management | Stream B Metrics and Feedback | 3 | Continuously improve your security defect management metrics and correlate it with other sources |  Not scope of TSS-WEB, task for IT security function. |

##  Verification Business Function
| Security Practices | Stream | Mat. Level | Requirement | TSS-WEB Coverage |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| Architecture Assessment | Stream A Architecture Validation | 1 | Identify application and infrastructure architecture components and review for basic security provisioning | Yes. See, “Security within change management & agile development” and “Architectural approval” and “Security documentation” in https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 | 
| Architecture Assessment | Stream A Architecture Validation | 2 | Validate the architecture security mechanisms | Yes. See, “Security within change management & agile development” and “Architectural approval” and “Security documentation” in https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Architecture Assessment | Stream A Architecture Validation | 3 | Review the architecture effectiveness and feedback results to improve the security architecture. | No. Not in scope of TSS-WEB; could be task for IT security function or architecture board |
| Architecture Assessment | Stream B Architecture Migitigation | 1 | Ad-hoc review of the architecture for unmitigated security threats. | Yes. See, “Security within change management & agile development” and “Architectural approval” and “Security documentation” in https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Architecture Assessment | Stream B Architecture Migitigation | 2 | Analyze the architecture for known threats. | Yes. See, “Security within change management & agile development” and “Architectural approval” and “Security documentation” in https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Architecture Assessment | Stream B Architecture Migitigation | 3 | Feed the architecture review results back into the enterprise architecture, organization design principles & patterns, security solutions and reference architectures. | No. Not in scope of TSS-WEB; could be a task of an architecture board | 
| Requirements-driven Testing | Stream A Control Verification | 1 | Test for software security controls | Yes. See “Custom security tests & developer tests” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 | 
| Requirements-driven Testing | Stream A Control Verification | 2 | Derive test cases from known security requirements | Yes. See “Complete and correct implementation” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Requirements-driven Testing | Stream A Control Verification | 3 | Perform regression testing (with security unit tests) | No |
| Requirements-driven Testing | Stream B Misuse / Abuse Testing | 1 | Perform security fuzzing testing | Yes. See “Custom security tests & developer tests” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 |
| Requirements-driven Testing | Stream B Misuse / Abuse Testing | 2 | Create and test abuse cases and business logic flaw test | Yes. See “Custom security tests & developer tests” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 | 
| Requirements-driven Testing | Stream B Misuse / Abuse Testing | 3 |  Denial of service and security stress testing | Yes. See “Custom security tests & developer tests” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368
| Security Testing | Stream A Scalable Baseline | 1 | Utilize automated security testing tools | Yes. See See “Utilize automated security testing tools” athttps://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 | 
| Security Testing | Stream A Scalable Baseline | 2 | Employ application-specific security testing automation | Yes. See “Secure build & deployment” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 | 
| Security Testing | Stream A Scalable Baseline | 3 | Integrate automated security testing into the build and deploy process | Yes. See “Secure build & deployment” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Security Testing | Stream B Deep Understanding | 1 | Perform manual security testing of high-risk components | Yes. See “Custom security tests & developer tests” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 |
| Security Testing | Stream B Deep Understanding | 2 | Conduct manual penetration testing  | Yes. See “Custom security tests & developer tests” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 |
| Security Testing | Stream B Deep Understanding | 3 | Integrate security testing into development process  | Yes. See “Custom security tests & developer tests” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98368 |

##  Operation Business Function

| Security Practices | Stream | Mat. Level | Requirement | TSS-WEB Coverage |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| Incident Management | Stream A Incident Detection | 1 | Use available log data to perform best-effort detection of possible security incidents. | See See requirements on “Possible security incidents monitoring” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 and https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/1179658  |
| Incident Management | Stream A Incident Detection | 2 | Follow an established, well-documented process for incident detection, with emphasis on automated log evaluation. | See See requirements on “Incident management” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 |
| Incident Management | Stream A Incident Detection | 3 | Use a proactively managed process for detection of incidents.	| No. Not scope of TSS-WEB; task for IT security function |
| Incident Management | Stream B Incident Detection Incident Response | 1 | Identify roles and responsibilities for incident response. | Yes. See requirements on “Incident management” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 | 
| Incident Management | Stream B Incident Detection Incident Response | 2 | Establish a formal incident response process and ensure staff are properly trained in performing their roles. | Yes. See requirements on “System hardening” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 |
| Incident Management | Stream B Incident Detection Incident Response | 3 | Employ a dedicated, well-trained incident response team. | No. Not scope of TSS-WEB; task for IT security function |
| Environment Management | Stream A Configuration Hardening | 1 | Perform best-effort hardening of configurations, based on readily available information. | Yes. See requirements on “System hardening” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 |
| Environment Management | Stream A Configuration Hardening | 2 | Perform consistent hardening of configurations, following established baselines and guidance. | Yes. See requirements on “System hardening” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 |
| Environment Management | Stream A Configuration Hardening | 3 | Actively monitor configurations for non-conformance to baselines, and handle detected occurrences as security defects. | Yes. See requirements on “Security monitoring” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 |
| Environment Management | Stream B Patching and Updating | 1 | Perform best-effort patching of system and application components | Yes. See requirements on “System updating / patching” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 and “Security of 3rd party dependencies” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Environment Management | Stream B Patching and Updating | 2 | Perform regular patching of system and application components, across the full stack. Ensure timely delivery of patches to customers. | See requirements on “System updating / patching” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 and “Security of 3rd party dependencies” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Environment Management | Stream B Patching and Updating | 3 | Actively monitor update status and manage missing patches as security defects. Proactively obtain vulnerability and update information for components. | YES. TBD |
| Operational Management | Stream A Data Protection | 1 | Implement basic data protection practices | Yes. See https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/1015823, https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/1179658 and https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 |
| Operational Management | Stream A Data Protection | 2 | Develop data catalog and establish data protection policy. | Yes. See “Security Documentation” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98338 |
| Operational Management | Stream A Data Protection | 3 | Automate detection of policy non-compliance, and audit compliance periodically. Regularly review and update to data catalog and data protection policy. | Yes. See TBD |
| Operational Management | Stream B Systgem Decomissioning / Legacy Management | 1 | Decomission unused applications and services as identified. Manage customer upgrades/migrations individually. | Yes. See requirement on “Decomission” at https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305 |
| Operational Management | Stream B Systgem Decomissioning / Legacy Ma nagement | 2 | Develop repeatable decommissioning processes for unused systems/services, and for migration from legacy dependencies. Manage legacy migration roadmaps for customers. | No. Not scope of TSS-WEB |
| Operational Management | Stream B Systgem Decomissioning / Legacy Management | 3 | Proactively manage migration roadmaps, for both unsupported end-of-life dependencies, and legacy versions of delivered software. | No. Not scope of TSS-WEB |