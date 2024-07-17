# 3. Secure Development Environment

## 3.1 Securing Access to Dev Environment

1. Access to development systems (incl. and build and deployment systems) MUST be sufficiently protected.
2. Access to development environment MUST be restricted.
3. Remote access to development systems MUST only be possible via a secure VPN connection and multi-factor authentication (MFA).

## 3.2 Protection of Cource and Program Code

1. Access to sensitive source and program code (code that is run in production, containing PII or other sensitive information or business logic) MUST be restricted to authorized users and revoked as soon as this user does not need it anymore (e.g. leaves the team). This includes authentication and authorization of access to cloud accounts, code repositories (e.g. Git), build systems (e.g. Jenkins or TFS), Wikis and other resources such as file systems.
2. Sensitive source and program code MUST NOT be made available to others outside of EXAMPLE INC. (e.g. within internet forums) without explicit clearance of the relevant IT security function.
3. The code repository SHOULD be periodically scanned for exposed secrets (e.g. X.509 private keys or API keys).
4. Source code repositories SHOULD be regularly scanned for disclosed secrets (e.g. X.509 private keys or API keys).

## 3.3 Use of 3rd Party Dependencies
see [4. Security within SDLC][A_SDLC]

[A_SDLC]: ../A_SSDLC_Requirements/04_Security-wthin-SDLC.md
