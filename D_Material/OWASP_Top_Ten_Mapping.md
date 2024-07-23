# OWASP Top Ten 2021 Mapping

OWASP TOP Ten is a ranking of critical threats to common Web applications that are published and periodically updated by the Open Source Web Application Security Project (OWASP). The following table shows a mapping of the requirements specified in this standard to the [2021 version of the OWASP Top 10](https://owasp.org/www-project-top-ten/).

| OWASP Top Ten Control  | Relevant TSS-WEB Requirement |
| ------------- | ------------- |
| A01:2021-Broken Access Control  | Verification of every sensitive object access (on both functional and object layer) as well as the implementation of indirections (see section [{{site.TITLE_IMPL_AUTHZ}}]({{site.URL_IMPL_AUTHZ}}).  |
| A02:2021-Cryptographic Failures | Covered in section [{{site.TITLE_IMPL_CRYPTO}}]({{site.URL_IMPL_CRYPTO}}) |
| A03:2021-Injection  | Primary: (1) Parametrization / ORM frameworks (SQL Injection) and (2) use of encoding APIs (see ​[4. Output Validation][B_OUTPUTVAL]). Secondary: restrictive input validation (see [{{site.TITLE_IMPL_INPUTVAL}}]({{site.URL_IMPL_INPUTVAL}})|
| A04:2021-Insecure Design | Covered in sections [{{site.TITLE_SSDLC_SDLC}}]({{site.URL_SSDLC_SDLC}}) and [{{site.TITLE_IMPL_PRINCIPLES}}]({{site.URL_IMPL_PRINCIPLES}}) |
| A05:2021-Security Misconfiguration | Perform server hardening (see [{{site.TITLE_SSDLC_SECOP}}]({{site.URL_SSDLC_SECOP}}) |
| A06:2021-Vulnerable and Outdated Components  | Keep your 3rd party components updates and perform SCA assessments in build pipeline (see ​[{{site.TITLE_SSDLC_SDLC}}]({{site.URL_SSDLC_SDLC}}). |
| A07:2021-Identification and Authentication Failures | Covered in [{{site.TITLE_IMPL_USERAUTH}}]({{site.URL_IMPL_USERAUTH}}) and [{{site.TITLE_IMPL_APISEC}}]({{site.URL_IMPL_APISEC}}) |
| A08:2021-Software and Data Integrity Failures | Covered in [{{site.TITLE_SSDLC_SECOP}}]({{site.URL_SSDLC_SECOP}}) |
| A09:2021-Security Logging and Monitoring Failures  | Covered in [{{site.TITLE_SSDLC_SECOP}}]({{site.URL_SSDLC_SECOP}} |
| A10:2021-Server-Side Request Forgery | Covered in [{{site.TITLE_IMPL_OUTPUTVAL}}]({{site.URL_IMPL_OUTPUTVAL}})|
