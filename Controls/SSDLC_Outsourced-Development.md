---
toc: false
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---
# A.5 Outsourced Development 

The following requirements apply to contractors implementing applications on behalf of EXAMPLE INC. These requirements are specifically relevant to the services and deliverables provided by the supplier. Additionally, all other applicable security requirements MUST be adhered to, as they pertain to the supplier's work.

1. **Due Diligence:** Implement all measures and common best practices within development, operation, and quality assurance required to prevent the occurrence of new security defects.

2. **Provision of Evidence:** For applications with *risk class >= [HIGH]:*  
   - Provide evidence[^1] that security has been considered throughout the development process.
   - Develop a security concept that complies with the security documentation requirements specified in [{{site.TITLE_SSDLC_SECDEV}}]({{site.URL_SSDLC_SECDEV}}).
   - Provide updated and signed SBOM and SLSA provenance for every shipped release artifact.
   - Provide means to verify signed artifacts (e.g. the respective X.509 certificate).

3. **Implementation of Security Measures:** Implement all necessary and requested security measures to achieve a suitable level of protection, including implementation requirements listed in [{{site.TITLE_IMPL_CONTROLS}}]({{site.URL_IMPL_CONTROLS}}).

4. **Internal Security Contact:** Appoint an internal contact person for security-relevant questions.

5. **Access Control to Source Code:** Ensure that only authorized persons who are required to have access (need-to-know principle) can access the source code created on behalf of EXAMPLE INC.

6. **Right to Audit:** Example Inc. is allowed to conduct security assessments of applications and source code created on its behalf at its own discretion. The supplier will provide the required support if needed.

7. **Provision of Source Code:** The supplier MUST provide all relevant source code of artifacts created on behalf of Example Inc.

8. **Remediation of Security Vulnerabilities:** Remediate security vulnerabilities as soon as possible without extra costs when requested by EXAMPLE INC. (see respective SLAs at [{{site.TITLE_SSDLC_SECOP_VULNREMED}}]({{site.URL_SSDLC_SECOP_VULNREMED}})).

9. **Inclusion of Security in Supplier Agreements:** Security should be built into supplier agreements to ensure compliance with organizational security requirements and that contracted developers possess the necessary skill set.


[^1]: e.g., via a ISO 27001 certification
