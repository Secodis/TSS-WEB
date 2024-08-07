# 1. Types of Requirements

By [RFC2119](https://datatracker.ietf.org/doc/html/rfc2119), two types of requirements are specified in this standard in terms of their rigorness:

- **Mandatory Requirements**: Identified by terms like “MUST“, “MUST NOT”, or “HAVE TO”
- **Recommendations**: Identified by a term like “SHOULD“ or “CAN” In case a requirement has a recommendation like nature, it does not need to be implemented if justifiable reasons exist. Recommendations that are specified with “CAN” are focused on applications of increased protection requirements or risk profile. Exceptions to not complying with mandatory requirements must be approved by the relevant IT security function.

Furthermore, requirements are also specified based on their [risk class]({{site.URL_GENERAL_RISKCLASSES}}):

- **Baseline Requirements**: Suitable for all applications and services
- **High-Assurance Requirements**: Required only for applications with a higher risk class (usually >= [HIGH])
