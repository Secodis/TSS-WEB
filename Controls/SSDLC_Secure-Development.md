---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---
# A.2 - Secure Development

## 1. Roles & Training

1. **Team Responsibility:** Every development team IS responsible for the security of their own code.

2. **Security Champions:** Each development team CAN appoint a security champion as outlined in [{{site.TITLE_GENERAL_ROLES}}]({{site.URL_GENERAL_ROLES}}).

3. **Security Qualification:** It MUST be ensured that all team members possess sufficient security knowledge. This CAN be achieved by providing general awareness and role-specific security training to team members, including secure coding training and training in secure design principles for developers.

## 2. Secure By Design

1. **Security Considerations in Design:** Security MUST be strongly considered during the design phase. Wherever possible, security requirements SHOULD be addressed at the architectural level instead of the code layer.

2. **Documented Security Architecture:** For applications with an *assurance class >= [HIGH]*, a documented security architecture MUST describe relevant security aspects, security controls, and a threat model of the application.

3. **Functional Requirements:** High-level application security objectives MUST be mapped to functional requirements.

4. **Review of Security Decisions:** Decisions with severe security implications MUST be regularly questioned and discussed within the team.

## 3. Security within Change Management & Agile Development

1. **Use of SCM:** All changes of source code MUST be committed to a source code management system (SCM) such as Git.

2. **Peer Review:** For applications with *assurance class >= [HIGH]*, all commits to protected branches MUST be reviewed by a second developer of the responsible team (e.g. via pull/merge request approvals).

3. **Assessment of Functional Requirements:** The team MUST conduct an assessment of all functional requirements (e
g. User Stories) and changes regarding potential security risks/impact (termed "security relevance") before implementation..
   - This assessment MAY be conducted informally by a team if it gained sufficient experience.
   - Teams MAY define their own criteria for security relevance.
   - Agile development teams SHOULD integrate corresponding criteria in their Definition of Ready (DoR) discuss security relevance in refinement meetings and take security efforts (e.g. for verification) into account for the estimation of a story.
   - For *assurance class >= [HIGH]*: If such an assessment is not conducted, a deployed application increment MUST be considered to have a potential high-security risk.
   - Threat models and assurance class MUST be reviewed and updated if affected (e.g. in case of changes in security controls or architectural change in general).
   - A suitable acceptance criteria (e.g. review by security champion, update of security documentation) MUST be defined for all security-relevant requirements and changes. Agile development teams SHOULD integrate corresponding criteria in their Definition of Done (DoD).

## 4. Secure Implementation

The implementation MUST adhere to [{{site.TITLE_IMPL_CONTROLS}}]({{site.URL_IMPL_CONTROLS}}).

## 5. Secure Build & Deployment

1. **Formal Process Definition:** A formal definition of the build and deployment process MUST be created to ensure consistency, repeatability, and automation.

2. **Secured Access:** Access to build and deployment systems MUST be secured according to the requirements outlined in [{{site.TITLE_SSDLC_SECENV}}]({{site.URL_SSDLC_SECENV}}).

3. **Integrated Security Checks:** Automated security checks MUST be integrated into the build and deployment processes in accordance with the requirements specified in [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}}).

4. **Secret Management:** Secrets SHOULD be injected during the deployment process in accordance with the guidelines provided at [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}}).

5. **Pull-Based Deployment Model:** Deployment pipelines SHOULD implement a pull-based model[^3].

6. **SBOMs:** A Software Bill of Materials (SBOM) MUST be created for all build and release artifacts.

7. **Cryptographic Signing:** For *assurance class >= [HIGH]*, all deployed artifacts (including SBOMs) MUST be cryptographically signed.

## 6. Security of Third-Party Dependencies

This section is relevant for the target production environment:

1. **Approved Repositories:** Third-party dependencies SHOULD only be obtained via internal and approved repositories.

2. **Dependency Approval:** Before a new third-party dependency can be used in production applications or within the release build environment, it MUST be approved by the architecture board. This requirement does not affect new releases of a dependency that has already been approved.

3. **Regular Updates:** Third-party dependencies SHOULD be updated regularly, ideally through an automated process.

4. **Critical Updates:** Third-party dependencies MUST be updated in response to critical security vulnerabilities or when they reach end-of-life status.

5. **Testing Requirements:** Testing requirements for both custom and third-party code are defined in [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}}).

## 7. Security Approvals (Security Gates)

1. **Initial Project approval:** All new projects that are either implementing new applications or that plan to change existing ones MUST be approved by the relevant IT security function before they are allowed to be started. As part of this approval, the relevant IT security function will specify the assurance class with the project and may define security controls that have to be implemented or security activities that have to be conducted by the project.

2. **Architecture approval (conditional):** For all new applications with *assurance class >= [HIGH]*, or if explicitly requested by the IT security function during the project approval, the solution architecture (including security architecture that describes security controls & aspects and a threat model describing relevant threats and mitigations for them) MUST be approved by the relevant IT security function before initial implementation is allowed to begin. The IT security function MAY request this approval to be renewed for architectural changes when certain criteria are met.

3. **Go-Live approval (conditional):** Initial application releases for applications with *assurance class >= [HIGH]* MUST pass a security sign-off by the relevant IT security function before they are allowed to be used in the target production environment. The relevant IT security function MAY decide within the project approval as well that this approval is required for subsequent releases (e.g. based on certain criteria) or projects with a lower assurance class.

4. **Continuous Release Gates:** Releases SHOULD be automatically tested against a security policy before deployment to production to prevent the deployment of artifacts with severe security violations.

5. ***Documentation:** All security approvals and risk management decisions MUST be documented.

## 8. Remediation of Security Findings

Security findings with a criticality >= [HIGH] (or CVSS[^2] v3 Score >= 7.0) MUST be sufficiently mitigated before a new application release is allowed to go live:

1. **Risk Acceptance:** If mitigation is not possible, the relevant risk MUST be accepted by the respective management function (e.g., project lead). For applications with an *assurance class >= [HIGH]*, this risk acceptance MUST be formally documented (e.g., as a Jira ticket).

2. **Finding Verification:** Security findings with criticality ratings of [MEDIUM] or greater (or a CVSS v3 Score of 5.0 or higher) SHOULD not go live without proper verification.

3. **Reassessment of Tool Findings:** Teams may reassess tool findings. For example, they can refine a CVSS Base Score by evaluating its CVSS Environmental Score, taking aspects such as classification or accessibility into account. When a rating/score is refined, the rationale (e.g., CVSS vector) MUST be documented.

4. **Retesting After Remediation:** Identified vulnerabilities MUST be retested after remediation to verify that countermeasures have been implemented correctly.

5. **Approval of Exceptions:** For *assurance class >= [HIGH]*: exceptions (such as temporary workarounds) MUST be approved by the IT security function.

## 9. Security Documentation

1. A comprehensive security documentation MUST exist and formally be approved by the relevant IT security function for every application with *assurance class >= [HIGH]* before its implementation starts (relevant aspects) and it’s allowed to initially go live (complete documentation).

2. In case the relevant IT security function has not requested it differently, this document SHOULD cover the following aspects:
   - Data and application classification (assurance class),
   - known threats (or full threat model) and respective countermeasures to mitigate them,
   - list of relevant security requirements (e.g. security standards or business  security requirements),
   - security within the development & deployment process,
   - network/cloud security architecture,
   - application security architecture (relevant application components, services, interfaces, and relevant data flows and architectural security controls in the form of a diagram),
   - role and authorization concept (required for go-live),
   - operational security controls (required for go-live).

[^1]: SAFECode defines a good security indicator here, by describing security-relevant changes as “Any additions or changes in security controls and functionality”: (1) Authentication (Adding or changing an authentication method, or mechanism), (2) Authorization (Shifting the trust relationships between any components or actors in the system (change of user levels, change of data access permissions, etc or adding or changing an authorization method, or mechanism), (3) Logging, monitoring and alerting (Adding or changing application monitoring, business analytics and insight, auditing, and compliance requirements or forensics) or (3) Cryptography (Adding or changing cryptographic functionality: hashing algorithms, salt, encryption/decryption algorithms, SSL/TLS configuration, key management, etc). See SAFECode paper [Tactical Threat Modeling](https://safecode.org/wp-content/uploads/2017/05/SAFECode_TM_Whitepaper.pdf)

[^2]: The Common Vulnerability Scoring System (CVSS) is a framework for rating the severity of security vulnerabilities. See [Common Vulnerability Scoring System (CVSS) v3](https://www.first.org/cvss)

[^3]: A pull-based model refers to a deployment strategy where deployment systems pull updates from a central repository rather than having updates pushed to them. See  [https://www.weave.works/blog/why-is-a-pull-vs-a-push-pipeline-important](https://www.weave.works/blog/why-is-a-pull-vs-a-push-pipeline-important)
