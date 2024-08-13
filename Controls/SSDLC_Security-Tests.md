---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---
# A.3 - Security Tests

## {{site.TITLE_SSDLC_SECTESTS_GEN}}

1. **Verification of Security Requirements:** The correct and complete implementation of security and security-relevant requirements and changes MUST be verified with suitable security tests.

2. **Automated and Continuous Testing:** Where possible, security tests SHOULD be executed automatically and continuously (e.g., within CI and CD pipelines) and as early as possible within the development process (following the fail-fast principle).

3. **Immediate Feedback:** Tests SHOULD fail-fast and produce immediate feedback to developers where possible. 

4. **Consistant Test Policy:** Test SHOULD be reproducible and executed against a consistent test policy in all stages.

5. **Local Testability:** Developers SHOULD be able to run automated test locally against the respective testing policy (dry runs). 

6. **Use of Production Data:** Test data MUST NOT contain confidential or personal (PII) data references.

7. **Segregated Test Execution:** The execution of security tests MUST NOT be affected by perimeter security systems (e.g., a web application firewall).

## {{site.TITLE_SSDLC_SECTESTS_DEFECTH}}

1. **Tracking of Security Defects:** Security defects MUST be tracked in a defect tracking system and provide relevant meta-information (e.g., criticality rating, CVSS score, etc.).

2. **Regular Review of Open Defects:** Open security defects SHOULD be regularly checked for relevance and possible quick wins.

3. **Defect Remediation:** Defects identified during the development process MUST be handled according to requirements in A.2 Secure Development Process. Defects identified in production systems MUST be managed according to requirements in A.5 Secure Operation.

## {{site.TITLE_SSDLC_SECTESTS_SECSCANS}}

1. **Code Scanning:** Applications MUST be automatically analyzed with security code scanning tools (SAST or IAST) to identify implementation vulnerabilities in source or program code as early as possible.

2. **Dependency Scanning:** Applications MUST be automatically analyzed with SCA (Software Composition Analysis) tools for any known vulnerabilities in third-party dependencies.

3. **Image Scanning:** Images used in the target production environment MUST be automatically scanned for security issues.

4. **Configuration Scanning:** Security-relevant configurations (including IaC) MUST be automatically scanned for security issues.

5. **Secret Scanning:** Source code or configuration MUST be automatically scanned for disclosed secrets.

6. **API Scanning:** For *risk class >= [HIGH]*, exposed APIs SHOULD be automatically tested for security issues.

7. **Denial-of-Service Testing:** Applications with an *risk class [HIGH]* SHOULD be automatically tested for denial-of-service attackability, e.g. by testing enforced rate limits, throttling and executing fuzzing tests.

8. **Pipeline Integration:** For *risk class >= [HIGH]*, security testing tools MUST be integrated in the build pipeline and enforce security requirements & security testing policies within the release process.

## {{site.TITLE_SSDLC_SECTESTS_CUSTOMTESTS}}

1. **Functional Security Tests:** Developer and system acceptance testing SHOULD test implemented functional security requirements (security controls).

2. **Negative Tests:** Tests SHOULD be both positive and negative (e.g. can an user without proper role access a protected ressource).

3. **Abuse Case Tests:** For *risk class >= [HIGH]*, teams SHOULD test possible abuse cases and common attack vectors (e.g Privilege Escalation, SQLi).

4. **Automated Execution:** Security tests of implemented security requirements and security controls (e.g., authentication or access controls) SHOULD be implemented and executed, preferably in an automatic and continuous way.

## {{site.TITLE_SSDLC_SECTESTS_PENTESTS}}

1. **Use of Pentests:** Applications MUST be verified by penetration tests according to the pentesting policy below. Penetration tests SHOULD be carried out within environments that are close to production environments (e.g. on integration systems).

2. **Retests of Findings:** After a severe vulnerability has been fixed that was found by a pentest, a retest should be executed, ideally by the same tester, in order to verify the correct implementation of the fix.
 
3. **Pentest Policy:** Pentests MUST be repeated according to follwing policy:
   
| Business Criticality | External Applications  | Internal Applications |
| ------------- | ------------- | ------------- |
| >= [HIGH] | Before initial go live but at least annually[^1]  | ASAP after initial go-live but at least every third year  |
| < [HIGH] | Before initial go live but at least every second year  | - | 

[^1]: In the case where it is ensured that no changes are made to an application, this interval MAY be extended by one additional year.
