# TSS-WEB (an Open Framework of Security Requirements for Web-based Applications & Services)

This is the official site of TSS-WEB, an open requirement framework consisting more than 200 general AppSec requirements. All these requirements are based on common best practices (including those from OWASP, SAFECode, ISO/IEC 27002, and NIST), along with our own experiences in this field.

For instance, implementing TSS-WEB also meets 14.2.1 control ("Secure Development Policy") of ISO/IEC 27002. Detailed compliance mappings are detailed below.

## Purpose

The purpose of this framework is to provide a comprehensive collection of technical and organizational AppSec controls for creating your own security standards, policies, or security concepts. You can use all of them or just select the ones you need. In many cases, you might need to adapt some of them or add others that are more relevant to your specific organization or technology stack.

## Types of Requirements

The requirements in this framework are primarily baseline requirements, suitable for all applications and services. Additionally, there are a few requirements specifically for more critical applications. These requirements often demand more effort to implement and address risks that may not be significant for all applications. To differentiate these, we use the term [assurance class][A_AC].

## General

[Definitions (Roles & Terms)][A_DEFINITIONS]

## SSDLC Requirements

1. [Remediation of Vulnerabilities in Production][A_REMEDIATION]
2. [Secure Operation][A_SECOP]
3. [Secure Development Environment][A_SECENV]
4. [Security within the SDLC][A_SDLC]
5. [Security Tests][A_SECTESTS]
5. [Outsourced Development][A_OUTDEV]

## Implementation Requirements

1. [Secure Design Principles][B_PRINCIPLES]
2. [Input Validation][B_INPUTVAL]
3. [File Uploads & Downloads][B_FILEUPLOADS]
4. [Output Validation (Encoding & Escaping)][B_OUTPUTVAL]
5. [User Authentication and Registration][B_USERAUTH]
6. [User Passwords][B_USERPASSWD]
7. [Hardening of Session Management][B_SESSIONMGMT]
8. [Access Control][B_AUTHZ]
9. [Error Handling & Logging][B_ERRORLOG]
10. [Data Security & Cryptography][B_CRYPTO]
11. [Protection of Secrets][B_SECRETS]
12. [Client-Side Security][B_CLIENTSEC]
13. [API Security][B_APISEC]

## Material
- [Requirements for HTTP Security Header][SECHEADER]

## Legacy Versions

You can find older versions of TSS-WEB in both English and German in PDF and Word format at the [here][TSSWEBOLD].

## Related Standards

Generally, we aim to integrate all useful requirements from existing standards and best practices into TSS-WEB that we find helpful for baseline security in that field. This does not mean that every requirement is or should be integrated, especially when they are more advanced or very specific.

The following table outlines coverage of the most important standards and best pratices in this field.

| Standard  | Coverage |
| ------------- | ------------- |
| [OWASP TOP Ten 2021][OWASPTOPTEN] | Full coverage withing implementation controls. See [OWASP Top Ten Mapping][TOPTENMAPPING). |
| [OWASP SAMM 2.0][OWASPSAMM} | OWASP SAMM has a different scope and goal but many of its practices are covered. See detailed [OWASP SAMM Mapping][SAMMMAPPING] |
| [ISO/IEC 27002:2022][27002]  | TSS-WEB meets 14.2.1 control ("Secure Development Policy") and covers controls 8.24 - 8.31 |
| [NIST SSSDF][SSDF]  | TBD  |
| [SAFECode Fundamental Practices for Secure Development][SAFECODE] | TBD |

Also, you may have a look at [OpenCRE][OPENCRE] which provides a general requirement mapping over many more standards.

## License
The document is licensed under Creative Commons By 4.0 and can therefore be used and changed to individual needs free of charge and without any other obligations than to name the document and author of the used template. Furthermore, any adapted version of this document does not have to be published under the same license.

## Author
This site is maintained by Secodis GmbH. Responsible for the content is Matthias Rohr. 

## Feedback 
Feedback about this content is very much welcome. Please post it in the TSS-WEB Google Group or send it directly to tss-web@googlegroups.com.

[A_REMEDIATION]: A_SSDLC_Requirements/01_Vulnerability-Remediation.md
[A_SECOP]: A_SSDLC_Requirements/02_Secure-Operation.md
[A_SECENV]: A_SSDLC_Requirements/03_Secure-Dev-Environment.md
[A_SDLC]: A_SSDLC_Requirements/04_Security-wthin-SDLC.md
[A_SECTESTS]: A_SSDLC_Requirements/05_Security-Tests.md
[A_OUTDEV]: A_SSDLC_Requirements/06_Outsourced-Development.md

[A_DEFINITIONS]: Definitions.md
[A_AC]: Definitions.md#assurance-classes
[A_TERMS]: Definitions.md#terms
[A_ROLES]: Definitions.md#roles

[B_PRINCIPLES]: B_Implementation_Requirements/01_Secure-Design-Principles.md
[B_INPUTVAL]: B_Implementation_Requirements/02_InputVal.md
[B_FILEUPLOADS]: B_Implementation_Requirements/03_FileUploads.md
[B_OUTPUTVAL]: B_Implementation_Requirements/04_OutputVal.md
[B_USERAUTH]: B_Implementation_Requirements/05_UserAuth.md
[B_USERPASSWD]: B_Implementation_Requirements/06_User-Passwords.md
[B_SESSIONMGMT]: B_Implementation_Requirements/07_Session-Mgmt.md
[B_AUTHZ]: B_Implementation_Requirements/08_Access-Control.md
[B_ERRORLOG]: B_Implementation_Requirements/09_Error-Handling-And-Logging.md
[B_CRYPTO]: B_Implementation_Requirements/10_Data-Security.md
[B_SECRETS]: B_Implementation_Requirements/11_Secrets.md
[B_CLIENTSEC]: B_Implementation_Requirements/12_Client-Side-Security.md
[B_APISEC]: B_Implementation_Requirements/13_API-Security.md

[SECHEADER]: Material/Requirements_for_HTTP_Header_Security.md
[TOPTENMAPPING]: Material/OWASP_Top_Ten_Mapping.md
[SAMMMAPPING]: Material/OWASP_SAMM-2.0-Mapping.md
[OWASPTOPTEN]: https://owasp.org/www-project-top-ten/
[TSSWEBOLD]: https://secodis.atlassian.net/wiki/spaces/TSSWEB

[OWASPSAMM]: https://owaspsamm.org/model/
[IEC27002]: https://www.iso.org/standard/2700
[NISTSSDF]: https://csrc.nist.gov/Projects/ssdf
[SAFECODE]: https://safecode.org/uncategorized/fundamental-practices-secure-software-development/
[OPENCRE]: https://www.opencre.org/
