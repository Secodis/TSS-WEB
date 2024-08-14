# About

This is the official site of TSS-WEB, an open security requirement framework for web-based applications and services. All requirements here are based on common standards and best practices, including those from [OWASP, Microsoft, NIST, and ISO/IEC](#related-standards).

Note that this project and its content is provided "as-is" without any guarantees. The information and views expressed are subject to change without notice. You assume all risks associated with using this content.

# Purpose

The purpose of this framework is to offer a comprehensive, consistent, and practical set of technical and organizational AppSec controls that organizations can adopt and tailor to their own security standards, policies, or concepts.

The goal is to provide a foundation that works for most organizations. In many cases, you may want to adapt only some controls or add others that are more suitable to your specific organization or technology stack.

# General
1. [{{site.TITLE_GENERAL_REQUIREMENTS}}]({{site.URL_GENERAL_REQUIREMENTS}})
2. [{{site.TITLE_GENERAL_TERMS}}]({{site.URL_GENERAL_TERMS}})
3. [{{site.TITLE_GENERAL_ROLES}}]({{site.URL_GENERAL_ROLES}})
4. [{{site.TITLE_GENERAL_RISKCLASSES}}]({{site.URL_GENERAL_RISKCLASSES}})
5. [{{site.TITLE_GENERAL_FAQ}}]({{site.URL_GENERAL_FAQ}})
6. [{{site.TITLE_GENERAL_LICENSE}}]({{site.URL_GENERAL_LICENSE}})

# Part A: SSDLC Controls
* [{{site.TITLE_SSDLC_SECENV}}]({{site.URL_SSDLC_SECENV}})
* [{{site.TITLE_SSDLC_SECDEV}}]({{site.URL_SSDLC_SECDEV}})
* [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}})
* [{{site.TITLE_SSDLC_OUTDEV}}]({{site.URL_SSDLC_OUTDEV}})
* [{{site.TITLE_SSDLC_SECOP}}]({{site.URL_SSDLC_SECOP}})

# Part B: Secure Implementation Controls
* [{{site.TITLE_IMPL_PRINCIPLES}}]({{site.URL_IMPL_PRINCIPLES}})
* [{{site.TITLE_IMPL_INPUTVAL}}]({{site.URL_IMPL_INPUTVAL}})
* [{{site.TITLE_IMPL_FILEUPLOADS}}]({{site.URL_IMPL_FILEUPLOADS}})
* [{{site.TITLE_IMPL_OUTPUTVAL}}]({{site.URL_IMPL_OUTPUTVAL}})
* [{{site.TITLE_IMPL_USERAUTH}}]({{site.URL_IMPL_USERAUTH}})
* [{{site.TITLE_IMPL_USERPASSWD}}]({{site.URL_IMPL_USERPASSWD}})
* [{{site.TITLE_IMPL_SESSIONMGMT}}]({{site.URL_IMPL_SESSIONMGMT}})
* [{{site.TITLE_IMPL_AUTHZ}}]({{site.URL_IMPL_AUTHZ}})
* [{{site.TITLE_IMPL_ERRORLOG}}]({{site.URL_IMPL_ERRORLOG}})
* [{{site.TITLE_IMPL_CRYPTO}}]({{site.URL_IMPL_CRYPTO}})
* [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}})
* [{{site.TITLE_IMPL_APISEC}}]({{site.URL_IMPL_APISEC}})
* [{{site.TITLE_IMPL_CLIENTSEC}}]({{site.URL_IMPL_CLIENTSEC}})
* [{{site.TITLE_IMPL_HTTPHEADERSEC}}]({{site.URL_IMPL_HTTPHEADERSEC}})

# Additional Material
* [{{site.TITLE_MATERIAL_TOPTENMAPPING}}]({{site.URL_MATERIAL_TOPTENMAPPING}})
* [{{site.TITLE_MATERIAL_SAMMMAPPING}}]({{site.URL_MATERIAL_SAMMMAPPING}})
  
# Legacy Versions

You can find older versions of TSS-WEB in both English and German in PDF and MS Word format [here](https://secodis.atlassian.net/wiki/spaces/TSSWEB).

# Related Standards

Generally, TSS-WEB aims to incorporate requirements from existing standards and best practices in this field that are suitable to establish baseline security. However, that does not mean that every requirement is integrated, particularly those that address edge case or too specific scenarios.

The following table outlines the coverage of some important standards in this area.

| Standard  | Coverage |
| ------------- | ------------- |
| [Microsoft SDL](https://www.microsoft.com/en-us/securityengineering/sdl) | Full coverage by SSDLC controls. See [{{site.TITLE_MATERIAL_MSSDLMAPPING}}]({{site.URL_MATERIAL_MSSDLMAPPING}}). |
| [Microsoft S2CF](https://www.microsoft.com/en-us/securityengineering/sdl/s2c2f) | Microsofts S2CF is a new framework focussed on supply chain security. Although a critical topic, most of its requirements are more than what would be expected as baseline security. |
| [OWASP TOP Ten 2021](https://owasp.org/www-project-top-ten/) | Full coverage by implementation controls. See [{{site.TITLE_MATERIAL_TOPTENMAPPING}}]({{site.URL_MATERIAL_TOPTENMAPPING}}). |
| [OWASP SAMM 2.0](https://owaspsamm.org/model/) | OWASP SAMM has a different scope and goal but practices related to security requirements should generally be covered. See [{{site.TITLE_MATERIAL_SAMMMAPPING}}]({{site.URL_MATERIAL_SAMMMAPPING}}). |
| [ISO/IEC 27002:2022](https://www.iso.org/standard/27001)  | TSS-WEB meets 14.2.1 control ("Secure Development Policy") and covers controls 8.24 - 8.31. |
| [NIST SSDF 1.1](https://csrc.nist.gov/Projects/ssdf)  | The Secure Software Development Framework (SSDF
NIST Special Publication (SP) 800-218). Comming soon. |
| [OWASP Top 10 CI/CD Security Risks](https://owasp.org/www-project-top-10-ci-cd-security-risks/) | coming soon. |

Also, you may have a look at [OpenCRE](https://www.opencre.org/) which provides a general requirement mapping over many more standards.

# License
The document is licensed under [Creative Commons By 4.0](https://creativecommons.org/licenses/by/4.0/deed.en) and can therefore be used and changed to individual needs free of charge and without any other obligations than to name the document and author of the used template. Furthermore, any adapted version of this document does not have to be published under the same license.

# Author
This site is maintained by [Secodis GmbH](https://www.secodis.com). Responsible for the content is [Matthias Rohr](https://www.linkedin.com/in/matthias-rohr/).
# Thanks
Tanks a lot to Timo Pagel and Christian Schneider for their input!
