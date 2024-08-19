---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---

# A.2 - Secure Development Process

## {{site.TITLE_SSDLC_SECDEV_ROLES}}

1. **Team Responsibility:** Every development team MUST be responsible for the security of their own code (see [{{site.TITLE_GENERAL_ROLES}}]({{site.URL_GENERAL_ROLES}}).

2. **Security Champions:** Each development team CAN appoint a security champion as outlined in [{{site.TITLE_GENERAL_ROLES}}]({{site.URL_GENERAL_ROLES}}).

3. **Security Know-How:**
    - It MUST be ensured that everyone involved in the development process  posess sufficient security knowledge for their particular role.
    - This SHOULD be achieved by providing general awareness and role-specific security training or coaching of team members, including   
         - secure coding training and training of secure design principles for developers, and
         - SSDLC training for project management role such as Product Owners.

## {{site.TITLE_SSDLC_SECDEV_INITIALIZATION}}

1. **Security Kick-Off:** New projects and dev teams MUST receive a security kick-off by their *IT security function*.

## {{site.TITLE_SSDLC_SECDEV_SECDESIGN}}

1. **Secure Design Considerations:** Security MUST be strongly considered during the design phase. Wherever possible, security requirements SHOULD be addressed at the architectural level instead of the code layer and according to [{{site.TITLE_IMPL_PRINCIPLES}}]({{site.URL_IMPL_PRINCIPLES}}).

2. **Use of Mature Technologies:** Applications and services SHOULD prioritize and utilize established security features, languages, and frameworks.

3. **Conduct Threat Modeling:** For applications and services with *risk class >= [HIGH]*:
    - A threat modeling session MUST be conducted prior to the start of implementation.
    - The threat model MUST be documented with mitigations and be incorporated into, or referenced from, the security architecture concept. 
    - The identified mitigation measures MUST be incorporated into the planning process (e.g.,the product backlog) and prioritized accordingly.
    - The threat model MUST be reviewed with every architectural change.

4. **Define Security Architecture:** For applications and services with *risk class >= [HIGH]*, a documented security architecture MUST describe relevant (technical & business) security requirements, invariants, threats and controls of the respective business application.

5. **Security Evaluation of New Features:**
Dev teams MUST assess every new feature regarding their potential security impact (= their security relevance) before they are allocated for development (e.g.assigned to a sprint).
   - This assessment MAY be conducted informally by a team if it gained sufficient experience.
   - Teams MAY define their own criteria for security relevance.
   - Agile teams SHOULD integrate corresponding criteria in their Definition of Ready (DoR) discuss security relevance in refinement meetings and take security efforts (e.g. for verification) into account for the estimation of a story.
   - Threat models and risk class MUST be reviewed and updated if affected (e.g. in case of changes in security controls or architectural change in general).
   - A suitable acceptance criteria (e.g. review by security champion, update of security documentation) MUST be defined for all security-relevant requirements and changes. Agile teams SHOULD integrate corresponding criteria in their Definition of Done (DoD).

6. **Review of Security Decisions:** Decisions with severe security implications MUST be regularly questioned and discussed within the team.

## {{site.TITLE_SSDLC_SECDEV_SECIMP}}

1. **Use of SCM:** All changes of source code MUST be committed to a source code management system (SCM) such as Git.

2. **Enforce Branch Protection:** For master/main branches, protected branch rules MUST be enforced.

3. **Perform Peer Reviews:** For applications and services with *risk class >= [HIGH]*, all commits to protected branches MUST be reviewed by a second developer of the responsible team (e.g. via pull/merge request approvals) for security aspects.

4. **Signed Commits:** Business critical applications SHOULD use signed commmits for protected branches.[^6]

5. **Implementation Requirements:** The implementation MUST adhere to [{{site.TITLE_IMPL_CONTROLS}}]({{site.URL_IMPL_CONTROLS}}).

6. **Security Verification:** Correct implementation of security requirements MUST be verified according to requirements specified in [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}}).

## {{site.TITLE_SSDLC_SECDEV_BUILD}}

1. **Formal Process Definition:** A formal definition of the build and deployment process MUST be defined to ensure consistency, repeatability, and automation.

2. **Secured Access:** Access to build and deployment systems MUST be secured according to the requirements outlined in [{{site.TITLE_SSDLC_SECENV}}]({{site.URL_SSDLC_SECENV}}).

3. **Securing Execution Nodes:** Pipeline jobs MUST be executed on nodes (or runners) with restricted permissions and network access, that are at least seperated for each environment. Shared nodes MUST NOT be used for applications or services with different security classifications.

4. **Automated Security Checks:** Automated security checks MUST be integrated into the build and deployment processes in accordance with the requirements specified in [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}}).

5. **Secret Management:** Secrets SHOULD be injected during the deployment process in accordance with the guidelines provided at [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}}).

6. **Pull-Based Deployment Model:** Deployment pipelines SHOULD implement a pull-based model[^3].

7. **SBOMs:** A Software Bill of Materials (SBOM) MUST be created for all build and release artifacts.

8. **Artefact Signing:** For *risk class >= [HIGH]*, all deployed artifacts (including SBOMs) MUST be cryptographically signed[^7]. Signatures SHOULD be automatically verified.

9. **Provenence Verification:** For *risk class >= [VERY HIGH]*, provenance and signatures of deployed artifacts MUST be automatically verified.

## {{site.TITLE_SSDLC_SECDEV_3RDPARTY}}

This section is relevant for the target production environment:

1. **Approved Repositories:** Third-party dependencies MUST only be obtained via internal or approved[^8] repositories. This MAY include proxy repositories. Exceptions are permitted only for isolated test environments

2. **Dependency Approval:** Before a new 3rd-party dependency can be used in prod, it MUST be approved by the architecture board or respective community of practice. This requirement does not affect new releases of a dependency that has already been approved.

3. **Automated Updates:** 3rd-party dependencies SHOULD be updated regularly, ideally through an automated process.[^5]

4. **Critical Updates:** 3rd-party dependencies MUST be updated in response to critical security vulnerabilities or when they reach end-of-life.

5. **Software Composition Analysis (SCA):** 3rd-party dependencies must be continuously tested according requirements at [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}}).

6. **End-of-Life Scans:** Automated scans for end of life of dependencies SHOULD be implemented.[^4]

7. **Dependency Pinning:** "Latest" releases MUST generally not be used. For business critical applications or services, 3rd-party dependencies MUST be pinned using checksums or cryptographic signatures.

## {{site.TITLE_SSDLC_SECDEV_SECGATES}}

1. **Initial Project Approval:**
   - All new projects that are either implementing new applications or that plan to change existing ones MUST be approved by the *IT security function* before they are allowed to be started.
   - As part of this approval, the *IT security function* CAN specify the risk class with the project and may define security controls that have to be implemented or security activities that have to be conducted by the project.

2. **Architecture Approval (Conditional):** For all new applications with *risk class >= [HIGH]*, or if explicitly requested by the *IT security function* during the project approval:
   - The security architecture (see [{{sute.TITLE_SSDLC_SECDEV_SECDESIGN}}]({{site.URL_SSDLC_SECDEV_SECDESIGN}}) MUST be approved by the *IT security function* before initial implementation is allowed to begin.
   - The *IT security function* MAY request this approval to be renewed for architectural changes when certain criteria are met.

4. **Go-Live Approval (Conditional):** Initial application releases for applications with *risk class >= [HIGH]*
   - MUST pass a security sign-off by the *IT security function* before they are allowed to be used in the target production environment.
   - The *IT security function* MAY decide within the project approval as well that this approval is required for subsequent releases (e.g. based on certain criteria) or projects with a lower risk class.

5. **Continuous Release Gates:** Releases SHOULD be automatically tested against a security policy before deployment to production to prevent the deployment of artifacts with severe security violations.

6. **Documentation:** Gate decisions MUST be documented.

## {{site.TITLE_SSDLC_SECDEV_VULMREM}}

Security findings with a *criticality >= [HIGH]* (or CVSS[^2] v3 Score >= 7.0) MUST be sufficiently mitigated before a new application release is allowed to go live:

1. **Risk Acceptance:** If mitigation is not possible, the relevant risk MUST be accepted by the respective management function (e.g., project lead). For applications with an *risk class >= [HIGH]*, this risk acceptance MUST be formally documented (e.g., as a Jira ticket).

2. **Finding Verification:** Security findings with criticality ratings of *[MEDIUM]* or greater (or a CVSS v3 Score of 5.0 or higher) SHOULD not go live without proper verification.

3. **Reassessment of Tool Findings:** Teams may reassess tool findings. For example, they can refine a CVSS Base Score by evaluating its CVSS Environmental Score, taking aspects such as classification or accessibility into account. When a rating/score is refined, the rationale (e.g. CVSS vector) MUST be documented.

4. **Retesting After Remediation:** Identified vulnerabilities MUST be retested after remediation to verify that countermeasures have been implemented correctly.

5. **Approval of Exceptions:** For *risk class >= [HIGH]*: exceptions (such as temporary workarounds) MUST be approved by the *IT security function*.

6. **Remediation for Production:** If a vulnerability may already exist in production, the requirements outlined in [{{site.TITLE_SSDLC_SECOP_VULNREMED}}]({{site.URL_SSDLC_SECOP_VULNREMED}}) MUST be followed.

[^1]: [SAFECode](https://safecode.org/wp-content/uploads/2017/05/SAFECode_TM_Whitepaper.pdf) provides a good security indicator. It defines security-relevant changes as “any additions or changes in security controls and functionality”. Examples are (1) Authentication (adding or changing an authentication method, or mechanism), (2) Authorization (Shifting the trust relationships between any components or actors in the system (change of user levels, change of data access permissions, etc or adding or changing an authorization method, or mechanism), (3) logging, monitoring and alerting (adding or changing application monitoring, business analytics and insight, auditing, and compliance requirements or forensics), and (4) cryptography (adding or changing cryptographic functionality: hashing algorithms, salt, encryption/decryption algorithms, SSL/TLS configuration, key management, etc).

[^2]: The Common Vulnerability Scoring System (CVSS) is a framework for rating the severity of security vulnerabilities. See [Common Vulnerability Scoring System (CVSS) v3](https://www.first.org/cvss)

[^3]: A pull-based model refers to a deployment strategy where deployment systems pull updates from a central repository rather than having updates pushed to them. See [https://itnext.io/gitops-pull-based-vs-push-based-959c50feca78](https://itnext.io/gitops-pull-based-vs-push-based-959c50feca78)

[^4]: One tool to accomplish this is [xeol](https://github.com/xeol-io/xeol).

[^5]: E.g. using [Renovate](https://github.com/renovatebot/renovate) or [Dependabot](https://github.com/dependabot)

[^6]: Commits made through the UI are typically signed using a technical user, which is acceptable because the UI itself enforces secure authentication for the developer.

[^7]: e.g. using [sigstore](https://www.sigstore.dev) cosign

[^8]: Approval by the *IT security function* or Architecture COP. Approval should be based on vetting criteria like [OpenSSF Scorecard](https://scorecard.dev/).
