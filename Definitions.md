# Definitions

## Types of Requirements

In accordance with RFC2119, two types of requirements are specified in this standard:

- **Mandatory Requirements**: Identified by terms like “MUST“, “MUST NOT”, or “HAVE TO”
- **Recommendations**: Identified by a term like “SHOULD“ or “CAN” In case a requirement has a recommendation like nature, it does not need to be implemented if justifiable reasons exist. Recommendations that are specified with “CAN” are focused on applications of increased protection requirements or risk profile. Exceptions to not complying with mandatory requirements must be approved by the relevant IT security function.

## Terms

The following definitions are used here:

- **3rd Party Dependency**: Here: 3rd party software artifacts, used by an application (e.g. libraries, Maven artifacts).
- **API**: Here: Web-based interface (e.g. a RESTful service)
- **Application**: Here: Synonym for -> web-based application or service.
- **Change**: Change to an application in production.
- **Confidential Data**: Data, which consists of
      - confidential information (e.g. trademarks, sensible business logic, passwords or personal data),
      - is explicitly declared as those or
      - is only accessible by a restricted number of people.
- **Confidential Code**: Source or program code which may consist -> confidential data.
- **Criticality**: Here: Mostly synonym for business criticality
- **Critical Application**: Here: Business critical application
- **Dependency Repository**: System that manages 3rd party dependencies (e.g. libraries, Maven artifacts). A dependency repository is often part of a general software repository system such as Nexus or Artifactory.
- **External Application**: A web-based application that is accessible from the outside of the organization (e.g. via the Internet).
- **Internal Code**: Source or program code which is not confidential and not public (standard).
- **Internal Application**: A web-based application that is only accessible from the inside of the organization (e.g. intranet application).
- **Service**: Here: Synonym for (business) application that can contain one or more ->APIs
- **Source Code Repository**: System where custom code is stored (e.g. SVN, Git).
- **Web Application**: Here: A software program (UI, service or API or combination of them) that is accessible via HTTP(s) protocol and fulfills a particular business case.

## Roles
The following roles are referred here:

- **(IT) Security Function**: Organizational entity or person that is responsible for establishing and maintaining IT security requirements and checking compliance with them - e.g. by conducting security sign-offs with projects and teams. The relevant IT security function may be a security officer dedicated for a particular project or team.
- **Security Champion**[^1]: Team internal technical expert (e.g. developer), contact and coordinator for security within a team (e.g. a development team). The responsibilities of this role include:
     - Security contact and enabler for a specific team.
     - Understands relevant security requirements and implementation/assurance of compliance to them within a team.
     - Identifies and manages of security risks.
     - Verifies correct implementation of security-relevant requirements.
     - Continuously verifies and improves of the effectiveness of implemented security checks and controls, it's automation and periodic assessment of security findings from tools.
     - Participates at internal security discussions (e.g. security Jour Fixe) or security communities).

- **Developer**: (Software) developers have the following responsibilities: 
     - Has general security know-how of technologies he/she is working with and keeps it up-to-date continuously.
     - Capable to avoid, find and fix vulnerabilities.
- **(Development) Team**: Responsible for the security of software artifacts it develops, maintains or operates. Continuously verifies and improves the effectiveness of implemented security checks and controls, it's automation and periodic assessment of security findings from tools.

## Assurance Classes
Certain requirements specified in this standard depend upon two aspects of an application.

The first is the accessibility, e.g. is an application accessible from the Internet, the second is the business criticality:

| Criticality| Internal Application | External Application |
| ------------- | ------------- | ------------- |
| Low-Medium | Standard | Standard |
| High | Standard | High |
| Very High | High | Very High |

[^1]: See SAFECode “Software Security Takes a Champion”, http://safecode.org/wp-content/uploads/2019/02/Security-Champions-2019-.pdf
