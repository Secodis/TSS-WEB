---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---
# A.3 - Security Tests

## {{site.TITLE_SSDLC_SECTESTS_GEN}}

1. **Verify Security Requirements:** The correct and complete implementation of security requirements and changes MUST be verified with suitable security tests.

2. **Automate Tests:** Where possible, security tests SHOULD be executed automatically and continuously (e.g. within CI and CD pipelines). For *risk class >= [HIGH]*, security testing tools MUST be integrated in the build pipeline and enforce security requirements & security testing.

3. **Provide Immediate Feedback:** Tests SHOULD fail fast and produce immediate feedback to developers where possible. 

4. **Enforce a Consistent Test Policy:** Test SHOULD be reproducible and executed against a consistent test policy in all stages.

5. **Allow Local Testability:** Developers SHOULD be able to run automated tests locally against the applicable test policy (dry runs). 

6. **Restrict The Use of Production Data:** Test data MUST NOT contain confidential or personal (PII) data references.

7. **Segregate Test Execution:** The execution of security tests MUST NOT be affected by perimeter security systems such as web application firewalls.

## {{site.TITLE_SSDLC_SECTESTS_DEFECTH}}

1. **Review:** Security findings SHOULD always be reviewed by the team to verify their validity.

2. **Refine:** Teams CAN refine the severity of a security finding[^2], and rate it as a false positive or not applicable (requires explanation).

3. **Track:** Verified security findings MUST be tracked as defects in a defect tracking system and SHOULD include relevant metadata (e.g. SLA, criticality rating, CVSS score, source, etc).

4. **Mitigate**
    - Vulnerabilities MUST be mitigated within the development process according to release gate requirements defined in [{{site.TITLE_SSDLC_SECDEV_SECGATES}}]({{site.URL_SSDLC_SECDEV_SECGATES}}).
    - If a vulnerability exists in prod or pre-prod, the requirements outlined in [{{site.TITLE_SSDLC_SECOP_VULNREMED}}]({{site.URL_SSDLC_SECOP_VULNREMED}}) MUST be followed.

5. **Retest After Mitigation:** Identified vulnerabilities MUST be retested after remediation to verify that countermeasures have been implemented correctly.

6. **Approve Exceptions:** For *risk class >= [HIGH]*: exceptions (such as temporary workarounds) MUST be approved by the *IT security function*.

7. **Regular Review:** Open security defects SHOULD be regularly reviewed for relevance and possible quick wins.

## {{site.TITLE_SSDLC_SECTESTS_SECSCANS}}

1. **Code Scanning:** Applications MUST be automatically analyzed with security code scanning tools (SAST or IAST) to identify implementation vulnerabilities in source or program code as early as possible.

2. **Dependency Scanning:** Applications MUST be automatically analyzed with SCA (Software Composition Analysis) tools for any known vulnerabilities in third-party dependencies. Scand SHOULD be continuously triggered, even if the code has not changed, to identify new CVEs.
   
3. **Image Scanning:** Container images assigned for the target production environment MUST be automatically scanned for security issues (see also [{{site.TITLE_SSDLC_SECOP_CONTAINERSEC}}]({{site.URL_SSDLC_SECOPP_CONTAINERSEC}}) for container scanning requirements).

4. **Configuration Scanning:** Security-relevant configurations (including IaC) SHOULD be automatically statically scanned for security issues such as missing hardening settings (see
 [{{site.TITLE_SSDLC_SECOP_HARDENING}}]({{site.URL_SSDLC_SECOP_HARDENING}})) if possible.

5. **Secret Scanning:** Repositories MUST be automatically scanned for disclosed secrets.

6. **API Scanning:** For *risk class >= [HIGH]*, exposed APIs SHOULD be automatically tested for security issues.

7. **Denial-of-Service Testing:** For *risk class [HIGH]* SHOULD be automatically tested for denial-of-service attackability, e.g. by testing enforced rate limits and fuzzing.

8. **Vulnerability Scanning:** Systems MUST be periodically scanned for vulnerabilities such as missing security patches and CVEs according to [{{site.TITLE_SSDLC_SECOP_SECSCANNING}}]({{site.URL_SSDLC_SECOP_SECSCANNING}}).

## {{site.TITLE_SSDLC_SECTESTS_CUSTOMTESTS}}

1. **Test Functional Security:** Developer and system acceptance testing SHOULD test implemented functional security requirements (security controls) such as authentication, authorization, security validation, etc.

2. **Perform Negative Tests:** Tests SHOULD be both positive and negative (e.g., can a user without proper role access a protected resource).

3. **Test Abuse Cases:** For *risk class >= [HIGH]*, teams SHOULD test potential abuse cases and common attack vectors (e.g., privilege escalation or business logic abuse) identified through threat modeling, business requirements, or other means.

4. **Automate Test Execution:** Security tests of implemented security requirements and security controls (e.g., authentication or access controls) SHOULD be implemented and executed, preferably in an automatic and continuous way.

## {{site.TITLE_SSDLC_SECTESTS_PENTESTS}}

1. **Pentest Environment:** Penetration tests SHOULD be carried out within a pre-production environment  (e.g. the acceptance environment).

2. **Retests Findings:** After a severe vulnerability has been fixed that was identified by a pentest, a retest should be executed, ideally by the same tester, in order to verify the correct implementation of the fix.

3. **Pentest Policy:** Applications and services MUST be verified by penetration tests according to the following policy:

| Business Criticality | External Applications  | Internal Applications |
| ------------- | ------------- | ------------- |
| **>= [HIGH]** | Before initial go live but at least annually[^1]  | ASAP after initial go-live but at least every third year  |
| **< [HIGH]** | Before initial go live but at least every second year  | - | 
   

[^1]: In the case where it is ensured that no changes are made to an application, this interval MAY be extended by one additional year.

[^2]: For example, they can refine a CVSS Base Score by  evaluating its CVSS Environmental Score, taking aspects such as classification or accessibility into account.
