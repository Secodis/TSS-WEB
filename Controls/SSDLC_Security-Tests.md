---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---
# A.3 - Security Tests

## {{site.TITLE_SSDLC_SECTESTS_GEN}}

1. **Verify Security Requirements:** The correct and complete implementation of security and security-relevant requirements and changes MUST be verified with suitable security tests.

2. **Automate and Continuously Test:** Where possible, security tests SHOULD be executed automatically and continuously (e.g. within CI and CD pipelines)

3. **Provide Immediate Feedback:** Tests SHOULD fail-fast and produce immediate feedback to developers where possible. 

4. **Enforce a Consistant Test Policy:** Test SHOULD be reproducible and executed against a consistent test policy in all stages.

5. **Allow Local Testability:** Developers SHOULD be able to run automated test locally against the respective testing policy (dry runs). 

6. **Restrict The Use of Production Data:** Test data MUST NOT contain confidential or personal (PII) data references.

7. **Segregate Test Execution:** The execution of security tests MUST NOT be affected by perimeter security systems (e.g. a web application firewall).

## {{site.TITLE_SSDLC_SECTESTS_DEFECTH}}

1. **Track Security Defects:** Security defects MUST be tracked in a defect tracking system and provide relevant meta information (e.g., criticality rating, CVSS score, etc.).

2. **Regular Revie Open Defects:** Open security defects SHOULD be regularly checked for relevance and possible quick wins.

3. **Remediate Defects:** Security defects identified during the development process MUST be handled according to requirements in [{{site.TITLE_SSDLC_SECDEV_VULMREM}}]({{site.URL_SSDLC_SECDEV_VULMREM}}). Defects identified in production systems MUST be managed according to requirements in [{{site.TITLE_SSDLC_SECOP_VULNREMED}}]({{site.URL_SSDLC_SECOPP_VULNREMED}}).

## {{site.TITLE_SSDLC_SECTESTS_SECSCANS}}

1. **Code Scanning:** Applications MUST be automatically analyzed with security code scanning tools (SAST or IAST) to identify implementation vulnerabilities in source or program code as early as possible.

2. **Dependency Scanning:** Applications MUST be automatically analyzed with SCA (Software Composition Analysis) tools for any known vulnerabilities in third-party dependencies. Repositories SHOULD be continuously scanned, even if the code has not changed, to identify new CVEs.
   
3. **Image Scanning:** Images used in the target production environment MUST be automatically scanned for security issues (see [{{site.TITLE_SSDLC_SECOP_CONTAINERSEC}}]({{site.URL_SSDLC_SECOPP_CONTAINERSEC}})).

4. **Configuration Scanning:** Security-relevant configurations (including IaC) MUST be automatically scanned for security issues.

5. **Secret Scanning:** Source code or configuration MUST be automatically scanned for disclosed secrets.

6. **API Scanning:** For *risk class >= [HIGH]*, exposed APIs SHOULD be automatically tested for security issues.

7. **Denial-of-Service Testing:** For *risk class [HIGH]* SHOULD be automatically tested for denial-of-service attackability, e.g. by testing enforced rate limits, throttling and executing fuzzing tests.

8. **Vulnerability Scans:** Systems MUST be scanned for vulnerabilities (see requirements for operational scans in  [{{site.TITLE_SSDLC_SECOP_SECSCANNING}}]({{site.URL_SSDLC_SECOPP_SECSCANNING}}))

9. **Pipeline Integration:** For *risk class >= [HIGH]*, security testing tools MUST be integrated in the build pipeline and enforce security requirements & security testing policies within the release process.

## {{site.TITLE_SSDLC_SECTESTS_CUSTOMTESTS}}

1. **Functional Security Tests:** Developer and system acceptance testing SHOULD test implemented functional security requirements (security controls) such as authentication, authorization, security validation, etc.

2. **Do Negative Tests:** Tests SHOULD be both positive and negative (e.g., can an user without proper role access a protected ressource).

3. **Test Abuse Cases:** For *risk class >= [HIGH]*, teams SHOULD test potential abuse cases and common attack vectors (e.g., privilege escalation or business logic abuse) identified through threat modeling, business requirements, or other means.

4. **Automate Test Execution:** Security tests of implemented security requirements and security controls (e.g., authentication or access controls) SHOULD be implemented and executed, preferably in an automatic and continuous way.

## {{site.TITLE_SSDLC_SECTESTS_PENTESTS}}

1. **Conduct Pentests:** Applications MUST be verified by penetration tests according to the pentesting policy below. Penetration tests SHOULD be carried out within environments that are close to production environments (e.g. on integration systems).

2. **Retests Findings:** After a severe vulnerability has been fixed that was found by a pentest, a retest should be executed, ideally by the same tester, in order to verify the correct implementation of the fix.
 
3. **Pentest Policy:** Pentests MUST be repeated according to follwing policy:
   
| Business Criticality | External Applications  | Internal Applications |
| ------------- | ------------- | ------------- |
| **>= [HIGH]** | Before initial go live but at least annually[^1]  | ASAP after initial go-live but at least every third year  |
| **< [HIGH]** | Before initial go live but at least every second year  | - | 

[^1]: In the case where it is ensured that no changes are made to an application, this interval MAY be extended by one additional year.
