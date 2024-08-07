---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---
# A.3 - Security Tests

## 1. General Requirements

1. **Verification of Security Requirements:** The correct and complete implementation of security and security-relevant requirements and changes MUST be verified with suitable security tests.

2. **Automated and Continuous Testing:** Where possible, security tests SHOULD be executed automatically and continuously (e.g., within CI and CD pipelines) and as early as possible within the development process (following the fail-fast principle).

3. **Test Data:** Test data MUST NOT contain confidential or personal (PII) data references.

4. **Unrestricted Test Execution:** The execution of security tests MUST NOT be affected by perimeter security systems (e.g., a web application firewall).

## 2. Defect Tracking

1. **Tracking Security Defects:** Security defects MUST be tracked in a defect tracking system and provide relevant meta-information (e.g., criticality rating, CVSS score, etc.).

2. **Regular Review of Open Defects:** Open security defects SHOULD be regularly checked for relevance and possible quick wins.

3. **High Assurance Class Security Risks:** For applications with an *Assurance Class >= [HIGH]*, security risks MUST also be tracked in a defect tracking system.

## 3. Automated Security Testing

1. **Code Scanning for Vulnerabilities:** Applications MUST be automatically analyzed with security code scanning tools (SAST or IAST) to identify implementation vulnerabilities in source and program code as early as possible.

2. **Dependency Vulnerability Analysis:** Applications MUST be automatically analyzed with SCA (Software Composition Analysis) tools for any known vulnerabilities in third-party dependencies.

3. **Image Scanning:** Images used in the target production environment MUST be automatically scanned for security issues.

4. **Configuration Security Scanning:** Security-relevant configurations MUST be automatically scanned for security issues.

5. **Enforcement of Security Requirements:** For applications with an *Assurance Class >= [HIGH]*, security testing tools MUST automatically enforce security requirements and security testing policies within the build process as specified in [{{site.TITLE_SSDLC_SDLC}}]({{site.URL_SSDLC_SDLC}}).

6. **Denial-of-Service Testing:** Applications with an *Assurance Class [VERY HIGH]* SHOULD be periodically tested for denial-of-service attackability.

## 4. Developer Tests

1. **Automated Security Tests:** Security tests of implemented security requirements and security controls (e.g., authentication or access controls) SHOULD be implemented and executed, preferably in an automatic and continuous way.

2. **Inclusion in Acceptance Testing:** Developer and system acceptance testing SHOULD include testing for functional (security controls) and non-functional[^1] security requirements.

3. **Tests of Abuse Cases:** Abuse cases SHOULD be created and tested for critical business security aspects

## 5. Pentests
1. **Use of Pentests:** Applications MUST be verified by penetration tests according to the pentesting policy below. Penetration tests SHOULD be carried out within environments that are close to production environments (e.g. on integration systems).
2. **Retests of Findings:** After a severe vulnerability has been fixed that was found by a pentest, a retest should be executed, ideally by the same tester, in order to verify the correct implementation of the fix. 
3. **Pentest Policy:** Pentests MUST be repeated according to follwing policy:
| Business Criticality | External Applications  | Internal Applications |
| ------------- | ------------- | ------------- |
| >= [HIGH] | Before initial go live but at least annually[^2]  | ASAP after initial go-live but at least every third year  |
| < [HIGH] | Before initial go live but at least every second year  | - |


[^1]: E.g. using predefined tests for common injection vulnerabilities (XSS, SQLi), access controls (trying to access sensitive objects with no/insufficient privileges), and fuzz testing.

[^2]: In the case where it is ensured that no changes are made to an application, this interval MAY be extended by one additional year.
