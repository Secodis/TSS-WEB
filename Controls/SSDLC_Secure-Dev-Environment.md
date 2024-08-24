---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---
# A.1 - Secure Development Environment

## {{site.TITLE_SSDLC_SECENV_ACCESS}}

1. **Protect Access:** Access to development systems, including build and deployment systems, MUST be sufficiently protected and restricted based on least privilege and using seperate access realms.

2. **Protect Secrets:** Secrets used for accessing development systems MUST be secured according to requirements at [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}}).[^1]

3. **Implement Role-Based Access Control (RBAC):** Access SHOULD be granted based on role-based access control (RBAC).

4. **Avoid Local Identities:** Local user identities SHOULD not be used. Instead, use a centralized identity provider (IdP).

5. **Secure Remote Access:** Remote access to development systems MUST only be possible via a secure VPN connection and multi-factor authentication (MFA).

6. **Revocate Access:** Access to code MUST be revoked as soon as a user no longer requires it (e.g., when leaving the team or organization).

## {{site.TITLE_SSDLC_SECENV_CODEPROTECT}}

1. **Enforce Ownership:** Every repository MUST have a clear ownership.

2. **Restrict Code Access:** Access to sensitive source and program code MUST be restricted to authorized users/groups only. Access rules MUST be periodically reviewed and recovated if not required anymore. 

3. **Avoid Code Disclosure:** Source and program code MUST NOT be made available to individuals outside the organization (e.g., within internet forums) without explicit clearance from the *IT security function*.

4. **Periodic Scan for Exposed Secrets:** Code repositories MUST be periodically scanned for exposed secrets (e.g., X.509 private keys or API keys) as defined in [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}}).

## {{site.TITLE_SSDLC_SECENV_PIPELINESEC}}

1. **Secure Execution Nodes:** Pipeline jobs MUST be executed on nodes (or runners) with restricted permissions and network access, that are at least seperated for each environment.

2. **Limit Use of Shared Nodes:** Shared nodes MUST NOT be used for applications or services with different security classifications.

3. **Isolate Untrusted Pipelines:** Pipelines that execute untrusted code SHOULD be isolated with no access to sensitive ressources (e.g. secrets).

4. **Protect Pipeline Configuration:** Write access to sensitive pipeline (e.g. release pipelines) configuration files MUST be restricted and SHOULD implement a manual approval (e.g. push/merge request approval).

5. **Restrict Pipeline Execution:** Sensitive pipelines SHOULD not be triggered from external sources or untrusted actors and implement manual execution approval.


[^1]: Development systems would be normally not assessed as *risk class [HIGH]* and secrets protecting these systems usually not applicable to respective requirements.
