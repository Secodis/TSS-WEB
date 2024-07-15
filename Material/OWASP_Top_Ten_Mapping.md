# OWASP Top Ten 2021 Mapping

OWASP TOP Ten is a ranking of critical threats to common Web applications that are published and periodically updated by the Open Source Web Application Security Project (OWASP). The following table shows a mapping of the requirements specified in this standard to the [https://owasp.org/www-project-top-ten/](2021 version of OWASP Top 10).

| OWASP Top Ten Control  | Relevant TSS-WEB Requirement |
| ------------- | ------------- |
| A01:2021-Broken Access Control  | Verification of every sensitive object access (on both functional and object layer) as well as the implementation of indirections (see section ​https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/983054).   |
| A02:2021-Cryptographic Failures | Covered in ​https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/1015823 |
| A03:2021-Injection  | Primary: (1) Parametrization / ORM frameworks (SQL Injection) and (2) use of encoding APIs (see ​https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/360490). Secondary: restrictive input validation (see https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/262199) |
| A04:2021-Insecure Design | Covered within SSDLC requirements and Secure Design Practices |
| A05:2021-Security Misconfiguration | Perform server hardening (see ​https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98305) |
| A06:2021-Vulnerable and Outdated Components  | Keep your 3rd party components updates and perform SCA assessments in build pipeline (see ​https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/65878). |
| A07:2021-Identification and Authentication Failures | Covered in https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/327745​  |
| A08:2021-Software and Data Integrity Failures | Covered in ​https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/65878 |
| A09:2021-Security Logging and Monitoring Failures  | Covered in ​https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/1179658  |
| A10:2021-Server-Side Request Forgery | Covered in ​https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/262199 |
