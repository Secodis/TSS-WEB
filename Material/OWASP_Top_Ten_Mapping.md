# OWASP Top Ten 2021 Mapping

OWASP TOP Ten is a ranking of critical threats to common Web applications that are published and periodically updated by the Open Source Web Application Security Project (OWASP). The following table shows a mapping of the requirements specified in this standard to the [2021 version of the OWASP Top 10](https://owasp.org/www-project-top-ten/).

| OWASP Top Ten Control  | Relevant TSS-WEB Requirement |
| ------------- | ------------- |
| A01:2021-Broken Access Control  | Verification of every sensitive object access (on both functional and object layer) as well as the implementation of indirections (see section [8. Access Controls][B_AUTHZ].  |
| A02:2021-Cryptographic Failures | Covered in [10. Data Security][B_CRYPTO] |
| A03:2021-Injection  | Primary: (1) Parametrization / ORM frameworks (SQL Injection) and (2) use of encoding APIs (see ​[4. Output Validation][B_OUTPUTVAL]). Secondary: restrictive input validation (see [2. Input Validation][B_INPUTVAL]) |
| A04:2021-Insecure Design | Covered within [4. Security in SDLC][A_SDLC] and [1. Secure Design Principles][B_PRINCIPLES] |
| A05:2021-Security Misconfiguration | Perform server hardening (see [2. Secure Operation][A_SECOP]) |
| A06:2021-Vulnerable and Outdated Components  | Keep your 3rd party components updates and perform SCA assessments in build pipeline (see ​[4. Security in SDLC][A_SDLC]). |
| A07:2021-Identification and Authentication Failures | Covered in [5. Secure User Authentication][B_USERAUTH] and [​13. API Security][B_APISEC]  |
| A08:2021-Software and Data Integrity Failures | Covered in [4. Security in SDLC][A_SDLC] |
| A09:2021-Security Logging and Monitoring Failures  | Covered in [2. Secure Operation][A_SECOP]  |
| A10:2021-Server-Side Request Forgery | Covered in ​[4. Output Validation][B_OUTPUTVAL] |


[B_AUTHZ]: B_Implementation_Requirements/08_Access-Control.md
[B_CRYPTO]: B_Implementation_Requirements/10_Data-Security.md
[B_OUTPUTVAL]: B_Implementation_Requirements/04_OutputVal.md
[B_INPUTVAL]: B_Implementation_Requirements/02_InputVal.md
[A_SECOP]: A_SSDLC_Requirements/02_Secure-Operation.md
[A_SDLC]: A_SSDLC_Requirements/04_Security-wthin-SDLC.md
[B_USERAUTH]: B_Implementation_Requirements/05_UserAuth.md
[A_SECENV]: A_SSDLC_Requirements/03_Secure-Dev-Environment.md
[A_SECTESTS]: A_SSDLC_Requirements/05_Security-Tests.md
[B_APISEC]: B_Implementation_Requirements/13_API-Security.md
[B_PRINCIPLES]: B_Implementation_Requirements/01_Secure-Design-Principles.md
