---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---

# A.2 - Secure Development Process

## {{site.TITLE_SSDLC_SECDEV_ROLES}}

1. **Establish Team Responsibility:** Dev teams MUST be responsible for the security of their own code and applications (see [{{site.TITLE_GENERAL_ROLES}}]({{site.URL_GENERAL_ROLES}})).

2. **Ensure Adequate Prioritization:** Product Owners are responsible for prioritizing security measures for their products based on risk assessment and compliance obligations.
   
3. **Implement Guardrails:** Dev teams SHOULD manage their own security within predefined boundaries.

4. **Appoint Security Champions:** Dev teams CAN appoint a security champion (see [{{site.TITLE_GENERAL_ROLES}}]({{site.URL_GENERAL_ROLES}})).

5. **Ensure Security Know-How:** It MUST be ensured that everyone involved in the development process posess sufficient security knowledge for their particular role:
    - **Security Onboarding:** New developers &  teams MUST receive a security onboarding.
    - **Security Training:** Role-specific security training or coaching SHOULD be provided to team members, including secure coding training for developers.
 
## {{site.TITLE_SSDLC_SECDEV_SECDESIGN}}

1. **Embrace Security Principles:** Wherever possible, security requirements SHOULD be addressed at the architectural level instead of the code layer and according to [{{site.TITLE_IMPL_PRINCIPLES}}]({{site.URL_IMPL_PRINCIPLES}}).

2. **Use Mature Technologies:** Applications and services SHOULD prioritize and utilize established security features, languages, and frameworks.

3. **Implement Secure Defaults:** Use secure defaults where possible to foster the use of secure settings.

4. **Conduct Threat Modeling:** For applications and services with *risk class >= [HIGH]*:
    - A threat modeling session MUST be conducted prior to the start of implementation.
    - The threat model MUST be documented with mitigations and be incorporated into, or referenced from, the security architecture concept (see below). 
    - The identified mitigation measures MUST be incorporated into the planning process (e.g.,the product backlog) and prioritized accordingly.
    - The threat model MUST be reviewed with every architectural change.

5. **Define the Security Architecture:** For *risk class >= [HIGH]*, a documented security architecture MUST describe relevant (technical & business) security requirements, invariants, threats and controls of the respective business application and subject of the architecture gate (see [{{site.TITLE_SSDLC_SECDEV_SECGATES}}]({{site.URL_SSDLC_SECDEV_SECGATES}})).

6. **Assess Security of New Features:**
Dev teams MUST assess every new feature regarding their potential security impact (= their security relevance[^1)) before they are allocated for development (e.g.assigned to a sprint).
   - This assessment MAY be conducted informally by a team if it gained sufficient expertise.
   - Teams MAY define their own criteria for security relevance.
   - Agile teams SHOULD integrate corresponding criteria in their Definition of Ready (DoR) discuss security relevance in refinement meetings and take necessary security efforts (e.g. for verification) into account for the estimation of a story.
   - Threat models and risk classes MUST be reviewed and updated if affected by a feature (e.g. in case of changes in security controls or architectural change in general).
   - A suitable acceptance criteria (e.g. review by security champion, update of security documentation) MUST be defined for all security-relevant requirements and changes. Agile teams SHOULD integrate corresponding criteria into their Definition of Done (DoD).

7. **Review Security Decisions:** Decisions with severe security implications MUST be regularly questioned and discussed within the team.

## {{site.TITLE_SSDLC_SECDEV_SECIMP}}

1. **Utilize Source Control:** All source code changes MUST be committed to a source code management (SCM) system, such as Git.

2. **Enforce Branch Protection:** For master/main branches, protected branch rules MUST be enforced.

3. **Perform Peer Reviews:** For applications and services with *risk class >= [HIGH]*, every commit to a protected branch MUST be reviewed by a second developer of the responsible team (e.g. via pull/merge request approvals) and include an assessment of security aspects.

4. **Sign Commits:** Business critical applications SHOULD sign commmits to protected branches.[^6]

5. **Implement Security Controls:** The implementation MUST adhere to [{{site.TITLE_IMPL_CONTROLS}}]({{site.URL_IMPL_CONTROLS}}).

6. **Verify Secure Implementation:** Correct implementation of security requirements MUST be verified and defects managed according to requirements specified in [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}})).

## {{site.TITLE_SSDLC_SECDEV_BUILD}}

1. **Define a Formal Process:** A formal definition of the build and deployment process MUST be defined to ensure consistency, repeatability, and automation.

2. **Secure Pipelines:** Access to build and deployment systems and security of pipelines MUST be secured according to the requirements at [{{site.TITLE_SSDLC_SECENV_PIPELINESEC}}]({{site.URL_SSDLC_SECENV_PIPELINESEC}}).

3. **Automate Security Checks:** Automated security checks MUST be integrated into the build and deployment processes in accordance with the requirements specified in [{{site.TITLE_SSDLC_SECTESTS_SECSCANS}}]({{site.URL_SSDLC_SECTESTS_SECSCANS}}).

4. **Enforce Security Policy:** A security policy MUST be enforced at a release gate according to [{{site.TITLE_SSDLC_SECDEV_SECGATES}}]({{site.URL_SSDLC_SECDEV_SECGATES}}).

5. **Protect Secrets:** Secrets SHOULD be injected during the deployment process in accordance with the requirements at [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}}).

6. **Implement a Pull-Based Deployment Model:** Deployment pipelines SHOULD implement a pull-based model[^3].

7. **Create SBOMs:** A Software Bill of Materials (SBOM) MUST be created for all build and release artifacts.

8. **Sign Artefacts:** For *risk class >= [HIGH]*, all deployed artifacts (including SBOMs) MUST be cryptographically signed[^7]. Signatures SHOULD be automatically verified.

9. **Verify Provenence:** For *risk class >= [VERY HIGH]*, provenance and signatures of deployed artifacts MUST be automatically verified.

## {{site.TITLE_SSDLC_SECDEV_3RDPARTY}}

This section applies to third-party dependencies, both backend and frontend, intended for use in the production environment.

1. **Use Approved Repositories:** Third-party dependencies MUST only be obtained via internal or approved[^8] repositories. This MAY include proxy repositories. Exceptions are permitted only for isolated test environments

2. **Use Approved Dependencies:** Before a new 3rd-party dependency can be used in prod, it MUST be approved by the architecture board or respective community of practice. This requirement does not affect new releases of a dependency that has already been approved.

3. **Update Dependencies:** Dependencies SHOULD be updated regularly, ideally through an automated process and before end-of-life.[^5]

4. **Use Software Composition Analysis (SCA):** 3rd-party dependencies must be continuously tested according requirements at [{{site.TITLE_SSDLC_SECTESTS_SECSCANS}}]({{site.URL_SSDLC_SECTESTS_SECSCANS}}).

5. **Perform End-of-Life Scans:** Automated scans for end of life of dependencies SHOULD be implemented.[^4]

6. **Pin Dependencies:** "Latest" releases MUST generally be avoided. For business critical applications or services, 3rd-party dependencies MUST be pinned using checksums or cryptographic signatures.

## {{site.TITLE_SSDLC_SECDEV_SECGATES}}

1. **Initial Project Kick-Off:**
   - New projects that are either implementing new applications or services, or that plan to change existing ones MUST conduct a security kick-off from the *IT security function* before they are allowed to be started.
   - As part of this kick-off, the *IT security function* CAN specify the risk class with the project and may define security controls that have to be implemented or security activities that have to be conducted by the project.

2. **Architecture Approval:** 
    - New architectures, or substantial changes to existing ones, MUST be approved by the *IT security function* and respective architecture function before initial implementation is allowed to begin.

3. **Release Gate:**
    - Initial releases (go live) for *risk class >= [HIGH]*, MUST pass a security sign-off by the *IT security function* before they are allowed to deployed in the prod environment.
    - Releases SHOULD be automatically tested against a security policy before deployment in prod environment to prevent deployment of artifacts with severe security violations.
    - Security findings MUST be mitigated or managed before a new application release is allowed to be deployed in a prod or pre-prod:
        - For  *risk class >= [HIGH]*, findings with *criticality >= [MEDIUM]* (or CVSS[^2] v3 score >= 5.0)
        - For  *risk class < [HIGH]*, findings with a *criticality >= [HIGH]* (or CVSS[^2] v3 score >= 7.0)
    - Violation of release requirements MUST necessitate approval (e.g., risk acceptance) to be overruled.
    - Gate policies should be transparent, enabling dev teams to continuously assess their code against it to avoid impediments in the realease process.
      
[^1]: [SAFECode](https://safecode.org/wp-content/uploads/2017/05/SAFECode_TM_Whitepaper.pdf) provides a good security indicator. It defines security-relevant changes as “any additions or changes in security controls and functionality”. Examples are (1) Authentication (adding or changing an authentication method, or mechanism), (2) Authorization (Shifting the trust relationships between any components or actors in the system (change of user levels, change of data access permissions, etc or adding or changing an authorization method, or mechanism), (3) logging, monitoring and alerting (adding or changing application monitoring, business analytics and insight, auditing, and compliance requirements or forensics), and (4) cryptography (adding or changing cryptographic functionality: hashing algorithms, salt, encryption/decryption algorithms, SSL/TLS configuration, key management, etc).

[^2]: The Common Vulnerability Scoring System (CVSS) is a framework for rating the severity of security vulnerabilities. See [Common Vulnerability Scoring System (CVSS) v3](https://www.first.org/cvss)

[^3]: A pull-based model refers to a deployment strategy where deployment systems pull updates from a central repository rather than having updates pushed to them. See [https://itnext.io/gitops-pull-based-vs-push-based-959c50feca78](https://itnext.io/gitops-pull-based-vs-push-based-959c50feca78)

[^4]: One tool to accomplish this is [xeol](https://github.com/xeol-io/xeol).

[^5]: E.g. using [Renovate](https://github.com/renovatebot/renovate) or [Dependabot](https://github.com/dependabot)

[^6]: Commits made through the UI are typically signed using a technical user, which is acceptable because the UI itself enforces secure authentication for the developer.

[^7]: e.g. using [sigstore](https://www.sigstore.dev) cosign

[^8]: Approval by the *IT security function* or Architecture COP. Approval should be based on vetting criteria like [OpenSSF Scorecard](https://scorecard.dev/).
