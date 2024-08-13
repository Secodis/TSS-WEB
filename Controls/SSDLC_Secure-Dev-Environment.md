---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---
# A.1 - Secure Development Environment

## {{site.TITLE_SSDLC_SECENV_ACCESS}}

1. **Protection of Access**: Access to development systems, including build and deployment systems, MUST be sufficiently protected and restricte.

2. **Secure Remote Access**: Remote access to development systems MUST only be possible via a secure VPN connection and multi-factor authentication (MFA).

3. **Revocation of Access**: Access to code MUST be revoked as soon as a user no longer requires it (e.g., when leaving the team or organization).

## {{site.TITLE_SSDLC_SECENV_CODEPROTECT}}

1. **Ownership of Repositories**: Every repository MUST have a clear ownership.

2. **Restricted Access to Code**: Access to sensitive source and program code MUST be restricted to authorized users/groups only. Access rules MUST be periodically reviewed and recovated if not required anymore. 

3. **Role-Based Access Control (RBAC)**: Access SHOULD be granted based on role-based access control (RBAC).

4. **Code Disclosure**: Source and program code MUST NOT be made available to individuals outside the organization (e.g., within internet forums) without explicit clearance from the relevant IT security function.

5. **Periodic Scanning for Exposed Secrets**: Code repositories SHOULD be periodically scanned for exposed secrets (e.g., X.509 private keys or API keys).
