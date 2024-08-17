---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---
# A.5 - Secure Operation

The following requirements apply to systems (infrastructure, platforms, or other runtime environments) on which applications in the target production environment are executed:

## {{site.TITLE_SSDLC_SECOP_SEPERATION}}

Systems in production MUST be strictly separated from development and test systems:

1. **Segregation of Stages:** Production, test, and development stages MUST be separated using different environments (e.g., separate clusters or cloud environments using separate accounts/subscriptions).

2. **Restricted Connections:** Connections to different environments MUST be restricted.

3. **Resource Isolation:** Resources MUST NOT be shared between production and other environments, especially no secret storage.

4. **Separate Authorization:** Users and processes MUST be authorized separately for each environment.

5. **Access Server Separation:** Access server SHOULD be separate instances for every environment but MUST at least use separate realms for each environment. For *risk class >= [HIGH]*: At least the prod environment MUST be a seperate and isolated instance. 

6. **Restricted Production Access:** Access to the production environment MUST be granted strictly on a need-to-know and least-privilege basis (see [{{site.TITLE_SSDLC_SECOP_ADMINACCESS}}]({{site.URL_SSDLC_SECOPP_ADMINACCESS}})) and SHOULD be automated where possible.
   
## {{site.TITLE_SSDLC_SECOP_HARDENING}}
1. **Pre-Deployment Hardening:** Systems (e.g., web servers, application servers, container platforms, content management systems, cloud platforms, or other runtime environments) MUST be hardened according to common best practices before being used in a production stage.

2. **Hardening Verification:** Systems in production MUST be periodically and automatically tested for insufficient hardening.

This includes:
- A hardened OS (e.g. using a hardened base image, see below)
- Deactivation of all services, plugins, and other functionality that is not needed, especially if they are exposed (executable from remote)
- Hardened SSL/TLS stack (see  [{{site.TITLE_IMPL_DATASEC_ENCRYPT-TANSIT}}](site.URL_IMPL_DATASEC_ENCRYPT-TANSIT))
- Activated security headers according to [{{site.TITLE_IMPL_HTTPHEADERSEC}}]({{site.URL_IMPL_HTTPHEADERSEC}}).
- Removal of samples and other default content
- Execution of network services (e.g. web or application servers) with only minimal privileges and isolated from other processes if possible (e.g. as an isolated container or dedicated server instance, VM or host)
- Network services bound to localhost if access is only required from the same system.
- Network services should only be accessible from certain IPs if possible.
- Deactivation of file handlers that are not required (e.g. `.php` for a Java application).
- Deactivation of insecure HTTP methods (e.g. `TRACE` and `TRACK`)
- Web and application servers must not disclose details on the server-side software stack (e.g. version numbers). Related HTTP response headers such as `Server` or `X-Powered-By` are to be deactivated or filtered.

## {{site.TITLE_SSDLC_SECOP_CONTAINERSEC}}
1. **Secure Build:** Containers MUST be executed only if they are built using trusted repositories, hardened base images, minimal dependencies, and updated OS packages.

2. **Security Scans:** Containers MUST be periodically scanned for insecure third-party components and misconfigurations.

3. **Minimal Privileges:** Containers MUST be executed with the least privileges necessary to function.

4. **Prohibit use of Remote Shells:** Containers MUST NOT include remote shells such as sshd or telnet.

5. **Lifecycle Management:** Containers MUST have a defined maximum lifetime, after which they need to be rebuild with updated OS packages.

6. **Labeling:**  
   Containers MUST have labels that indicate the application or service they belong to and the responsible team.

## {{site.TITLE_SSDLC_SECOP_SECBACKEND}}

1. **Least Privilege:** Processes MUST only have the required permissions to resources, such as on the file system or database. For example, "no root permission on databases."

2. **Access Requirements:** Access to backend systems MUST be authenticated and authorized according to requirements of [{{site.TITLE_IMPL_APISEC}}]({{site.URL_IMPL_APISEC}}).

3. **Dedicated Service Accounts:** Access to backend systems MUST use dedicated service accounts for each system.

4. **Secure Secrets Management:** Secrets must be securely stored and managed (see [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}})).

## {{site.TITLE_SSDLC_SECOP_ISOLATION}}

1. **Dedicated Environments:** Applications MUST be deployed in dedicated isolated production environments.

2. **Encrypted Communication:** All network communication MUST be encrypted using TLS (see [{{site.TITLE_IMPL_DATASEC_ENCRYPT-TANSIT}}])({{site.URL_IMPL_DATASEC_ENCRYPT-TANSIT}}.

3. **External Access Approval:** All external access to internal network zones MUST be approved.

4. **Restricted Outgoing Communication:** Outgoing communication (egress) to the Internet MUST be restricted (whitelisted) and SHOULD be handled by proxies (e.g., HTTP proxies or SMTP proxies).

5. **Restricted Incoming Communication:** Incoming communication (ingress) from untrusted networks MUST be restricted and handled by reverse proxies (e.g., API gateways, web gateways).

6. **Web Application Firewall (WAF):** A web application firewall MAY be used as an additional layer of protection for web UIs.

## {{site.TITLE_SSDLC_SECOP_ADMINACCESS}}

Administrative access MUST be as strongly restricted:

1. **Limited Access:** Access MUST be limited to required persons only and restricted to permissions necessary to fullfill task.

2. **Personalized Admin Accounts:** Access MUST be via personalized accounts (e.g., usernames like “admin” should not be used). This SHOULD be a different account as the standard user account of that particular person. 

3. **Network Restrictions:** Access MUST be limited to internal network zones or authorized IPs if possible. System access MUST only be possible via a jump host


4. **Two-Factor Authentication:** Access MUST use a mandatory second authentication factor (such as hardware tokens, authenticator apps, X.509 client certificates) in combination with a strong user password.

5. **Logging:** All administrative access SHOULD be logged in a tamper-proof way.

6. **Revocation:** Access MUST be immediately revoked after it is no longer required (e.g., user changes organizational role).

7. **Automation:** Admin tasks SHOULD be automated when possible to replace direct human access.

## {{site.TITLE_SSDLC_SECOP_SECSCANNING}}

Productive systems MUST be periodically scanned for potential security problems. 

For instance:
- Insecure configurations
- Missing security patches
- Validity of X.509 certificates (see [{{site.TITLE_IMPL_DATASEC_ENCRYPT-TANSIT}}]({{site.URL_IMPL_DATASEC_ENCRYPT-TANSIT}})
- Exposed development artifacts (e.g. SVN files)
- Potential malware infection
- Vendor of product specific hardening guidelines
- Drifts of productive configuration (drift detection)

## {{site.TITLE_SSDLC_SECOP_MONITORING}}
For *risk class >= [HIGH]*: 

1. **Monitoring:** Possible security incidents MUST be continuously monitored. For instance:
- Potential account abuse or system compromise
- Failures in security controls or tests
- Use or assignment of critical security permissions
- Potential Denial of Service (DoS) conditions 
- Critical security findings on production systems.

2. **Alerting:** Alerting procedures for potential critical security events SHOULD be implemented.

3. **SIEM Integration:** Logs MUST be shipped to a SIEM system.

## {{site.TITLE_SSDLC_SECOP_MAINTANENCE}}

1. **System Updates:** Systems MUST be kept up-to-date, especially in terms of security patches.

2. **Decommissioning:** Unused applications or services MUST be decommissioned.

## {{site.TITLE_SSDLC_SECOP_VULNREMED}}

1. Identified vulnerabilities in productive applications MUST generally be remediated quickly and effectively.

2. In cases where root cause remediation requires a significant amount of time and the risk posed by the vulnerability is also significant, temporary measures (e.g., workarounds) SHOULD be implemented to reduce exploitability as soon as possible until the actual root cause is fixed.

3. Vulnerabilities in productive applications and services MUST be remediated or have their exploitability prevented within the following SLA (Service Level Agreement):

Internet-facing applications or services:

| | **Critical Vulnerability** | **High Vulnerability**  | **Moderate Vulnerability**  |
| ------------- | ------------- | ------------- | ------------- |
| **Critical Application** | At the end of the **next working day** |  Within **7 days** | Within the next release, but after **6 months** at the latest. |
| **Non-Critical Application** | Within **7 days**  | Within **21 days** | - |

Internal applications or services:

| | **Critical Vulnerability**  | **High Vulnerability** | **Moderate Vulnerability** |
| -------------| ------------- | ------------- | ------------- |
| **Critical Application** | Within **7 days**  | Within **30 days**  | Within the next release, but after **12 months** at the latest. |
| **Non-Critical Application**| Within **21 days**  | Within **60 days**  | - |

4. The *IT security function* MAY extend this SLA if justified from an individual risk evaluation. SLA extensions MUST be documented along with their justification.
   
## {{site.TITLE_SSDLC_SECOP_INCIDENTMGMT}}

A consistent incident management process (including roles, responsibilities escalation procedures) MUST be implemented and followed.

