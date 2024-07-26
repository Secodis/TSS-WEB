<title>{{site.TITLE_SSDLC_SECENV}}</title>
# {{site.TITLE_SSDLC_SECENV}}

## 1. Securing Access to Dev Environment

1. Access to development systems (including build and deployment systems) MUST be sufficiently protected.
2. Access to the development environment MUST be restricted.
3. Remote access to development systems MUST only be possible via a secure VPN connection and multi-factor authentication (MFA).

## 2. Protection of Source and Program Code

1. Every repository MUST have a clear ownership.
1. Access to sensitive source and program code MUST be restricted to authorized users only.
2. Access MUST be revoked as soon a user does not require it anymore (e.g. leaves the team or organization). 
3. Access SHOULD be granted based on role-based access control (RBAC)
4. Internal source and program code MUST NOT be made available to others outside of the organization (e.g. within internet forums) without explicit clearance of the relevant IT security function.
5. Code repositories SHOULD be periodically scanned for exposed secrets (e.g. X.509 private keys or API keys).

## 3. Use of 3rd Party Dependencies
see [{{site.TITLE_SSDLC_SDLC}}]({{site.URL_SSDLC_SDLC}})
