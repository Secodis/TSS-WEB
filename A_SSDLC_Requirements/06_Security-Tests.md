# 6. Security Tests

## 6.1 General Requirements

1. Correct and complete implementation of security & security-relevant requirements and changes MUST be verified with suitable security tests.
2. Where possible, security tests SHOULD be executed automatically and continuously (e.g. within CI and CD pipelines) and as early as possible within the development process (fail fast principle).
3. Test data MUST not contain confidential or personal (PII data) references.
4. The execution of security tests MUST NOT be affected by perimetric security systems (e.g. a web application firewall).

## 6.2 Defect Tracking

1. Security defects MUST be tracked in defect tracking system and provide relevant meta information (e.g. criticality rating, CVSS score etc.).
2. Open security defects SHOULD be regularly checked for relevance and possible quick wins.
3. For applications with assurance class >= [HIGH], security risks MUST also tracked in defect tracking system.

## 6.3 Automated Security Testing

1. Applications MUST be automatically analyzed with security code scanning tools (SAST or IAST) in order to identify implementation vulnerabilities in source and program code as early as possible.
2. Applications MUST be automatically analyzed with SCA (Software Composition Analysis) tools for any known vulnerabilities in 3rd party dependencies.
3. Docker images used in the target production environment MUST be automatically scanned for security issues.
4. Security-relevant configuration MUST be automatically scanned for security issues.
5. For applications with assurance class >= [HIGH] Security testing tools MUST automatically enforce security requirements and security testing policies within the build process as specified at 5. Security within Software Development Process.
6. Applications with assurance class [VERY HIGH] SHOULD be periodically tested for denial-of-service attackability.

## 6.4 Developer Tests

1. Security tests of implemented security requirements and security controls (e.g. authentication or access controls) SHOULD be implemented, executed, preferably in an automatically and continuously way.
2. Developer and system acceptance testing SHOULD include testing for functional (security controls) and non-functional [^1] security requirements.
3. Abuse cases SHOULD be created & tested for critical business security aspects in applications with assurance class >= [HIGH].

## 6.5 Pentests
1. Applications MUST be verified by penetration tests according to the pentesting policy bellow. Penetration tests SHOULD be carried out within environments that are close to production environments (e.g. on integration systems).
2. After an severe vulnerability has been fixed, a retest should be executed, ideally by the same tester, in order to verify the correct implementation of the fix. 

| | External Applications  | Internal Applications |
| ------------- | ------------- | ------------- |
| Criticality >= [HIGH] | Before initial go live but at least annually[^2]  | ASAP after initial go-live but at least every third year  |
| Criticality < [HIGH] | Before initial go live but at least every second year  | - |


[^1]: E.g. using predefined tests for common injection vulnerabilities (XSS, SQLi), access controls (trying to access sensitive objects with no/insufficient privileges) and fuzz testing.

[^2]: In the case where it is ensured that no changes are made to an application, this interval MAY be extended by one additional year.
