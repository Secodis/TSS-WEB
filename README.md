This is the official site of TSS-WEB, an **open requirement framework for web-based applications & services**. All these requirements are based on common best practices (including those from OWASP, SAFECode, ISO/IEC 27002, and NIST) and our own experiences in this field.

For instance, implementing TSS-WEB also meets 14.2.1 control ("Secure Development Policy") of ISO/IEC 27002. Detailed compliance mappings are shared below.

## Purpose

The purpose of this framework is to provide a comprehensive and consistent collection of technical and organizational AppSec controls for creating your own security standards, policies, or security concepts. The idea is not to have various variants of requirements that cover every possible scenario, but one that works for most organizations, at least as a baseline. You can use all of them or just select the ones you need. In many cases, you might need to adapt some or add others more relevant to your specific organization or technology stack.


## A. General
 
 * [{{site.TITLE_GENERAL_REQUIREMENTS}}]({{site.URL_GENERAL_REQUIREMENTS}})
 * [{{site.TITLE_GENERAL_TERMS}}]({{site.URL_GENERAL_TERMS}})
 * [{{site.TITLE_GENERAL_ROLES}}]({{site.URL_GENERAL_ROLES}})
 * [{{site.TITLE_GENERAL_ASSURANCECLASSES}}]({{site.URL_GENERAL_ASSURANCECLASSES}})

## B. SSDLC Requirements

* [{{site.TITLE_SSDLC_REMEDIATION}}]({{site.URL_SSDLC_REMEDIATION}})
* [{{site.TITLE_SSDLC_SECOP}}]({{site.URL_SSDLC_SECOP}})
* [{{site.TITLE_SSDLC_SECENV}}]({{site.URL_SSDLC_SECENV}})
* [{{site.TITLE_SSDLC_SDLC}}]({{site.URL_SSDLC_SDLC}})
* [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}})
* [{{site.TITLE_SSDLC_OUTDEV}}]({{site.URL_SSDLC_OUTDEV}})

## C. Implementation Requirements

1. [Secure Design Principles]({{site.URL_IMPL_PRINCIPLES}})
2. [Input Validation]({{site.URL_IMPL_INPUTVAL}})
3. [File Uploads & Downloads]({{site.URL_SSDLC_REMEDIATION}})
4. [Output Validation (Encoding & Escaping)]({{site.URL_IMPL_OUTPUTVAL}})
5. [User Authentication and Registration]({{site.URL_IMPL_USERAUTH}})
6. [User Passwords]({{site.URL_IMPL_USERPASSWD}})
7. [Hardening of Session Management]({{site.URL_IMPL_SESSIONMGMT}})
8. [Access Control]({{site.URL_IMPL_AUTHZ}})
9. [Error Handling & Logging]({{site.URL_IMPL_ERRORLOG}})
10. [Data Security & Cryptography]({{site.URL_IMPL_CRYPTO}})
11. [Protection of Secrets]({{site.URL_IMPL_SECRETS}})
12. [Client-Side Security]({{site.URL_IMPL_CLIENTSEC}})
13. [API Security]({{site.URL_IMPL_APISEC}})

## D. Additional Material
- [Requirements for HTTP Security Header]({{site.URL_MATERIAL_SECHEADER}})
- [OWASP Top Ten 2021 Mapping]({{site.URL_MATERIAL_TOPTENMAPPING}})
- [OWASP SAMM 2.0 Mapping]({{site.URL_MATERIAL_SAMMMAPPING}})
  
## Legacy Versions

You can find older versions of TSS-WEB in both English and German in PDF and Word format at the [here](https://secodis.atlassian.net/wiki/spaces/TSSWEB).

## Related Standards

Generally, we aim to integrate all useful requirements from existing standards and best practices into TSS-WEB that we find helpful for baseline security in that field. This does not mean that every requirement is or should be integrated, especially when they are more advanced or very specific.

The following table outlines coverage of the most important standards and best practices in this field.

| Standard  | Coverage |
| ------------- | ------------- |
| [OWASP TOP Ten 2021](https://owasp.org/www-project-top-ten/) | Full coverage withing implementation controls. See [OWASP Top Ten Mapping]({{site.URL_MATERIAL_TOPTENMAPPING}}). |
| [OWASP SAMM 2.0][https://owaspsamm.org/model/) | OWASP SAMM has a different scope and goal but many of its practices are covered. See detailed [OWASP SAMM Mapping]({{site.URL_MATERIAL_SAMMMAPPING}}). |
| [ISO/IEC 27002:2022](https://www.iso.org/standard/27001)  | TSS-WEB meets 14.2.1 control ("Secure Development Policy") and covers controls 8.24 - 8.31 |
| [NIST SSSDF]( https://csrc.nist.gov/Projects/ssdf)  | TBD  |
| [SAFECode Fundamental Practices for Secure Development](https://safecode.org/resource-secure-development-practices/fundamental-practices-secure-software-development-2/) | TBD |

Also, you may have a look at [OpenCRE](https://www.opencre.org/) which provides a general requirement mapping over many more standards.

## License
The document is licensed under Creative Commons By 4.0 and can therefore be used and changed to individual needs free of charge and without any other obligations than to name the document and author of the used template. Furthermore, any adapted version of this document does not have to be published under the same license.

## Author
This site is maintained by [Secodis GmbH](https://www.secodis.com). Responsible for the content is [Matthias Rohr](https://www.linkedin.com/in/matthias-rohr/). 
