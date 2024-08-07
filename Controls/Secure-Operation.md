# A.4 - Secure Operation

The following requirements apply to systems (infrastructure, platforms, or other runtime environments) on which applications in the target production environment are executed:

## 1. Environment Separation
Systems in production MUST be strictly separated from development and test systems:
1. Production, test, and development stages MUST be separated using different environments (e.g. in separate clusters, cloud environments using separate accounts/subscriptions).
2. Connections between different environments MUST not be possible.
3. Ressources MUST not be shared between production and other environments (especially no secret storages).
4. Users and systems MUST be authorized separately for each environment.
5. Access servers SHOULD be separated instances for all environments but MUST at least use separate realms.
6. Access to the production environment MUST be granted strictly on a need-to-know & least-privilege basis (see "Administrative Access" below) and SHOULD be automated where possible.
7. Production data SHOULD not be used on non-production systems (exceptions see [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}})).
   
## 2. System Hardening
1. Systems (e.g. web servers, application servers, container platforms or content management systems, cloud platforms, or other runtime environments) MUST be hardened according to common best practices before used in a production stage.
2. Systems in production MUST be periodically and automatically tested for insufficient hardening.

This includes:
- A hardened OS (e.g. using a hardened base image, see below)
- Deactivation of all services, plugins, and other functionality that is not needed, especially if they are exposed (executable from remote)
- Hardened SSL/TLS stack (see [{{site.TITLE_IMPL_CRYPTO}}]({{site.URL_IMPL_CRYPTO}}))
- Activated security headers according to Appendix A: Requirements for HTTP Security Header
- Removal of samples and other default content
- Execution of network services (e.g. web or application servers) with only minimal privileges and isolated from other processes if possible (e.g. as an isolated container or dedicated server instance, VM or host)
- Network services bound to localhost if access is only required from the same system.
- Network services should only be accessible from certain IPs if possible.
- Deactivation of file handlers that are not required (e.g. `.php` for a Java application).
- Deactivation of insecure HTTP methods (e.g. `TRACE` and `TRACK`)
- Web and application servers must not disclose details on the server-side software stack (e.g. version numbers). Related HTTP response headers such as `Server` or `X-Powered-By` are to be deactivated or filtered.

## 3. Container Security
1. Only containers MUST be used that where built using trusted repositories, using hardened base images, and updated OS packages.
2. Containers MUST be periodically scanned for insecure 3rd party components and insecure configuration.
3. Containers MUST not consist of a remote shell like SSH or telnet.
4. Containers MUST have a maximal lifetime after which they have to be rebuilt with updated OS dependencies. 
5. Containers MUST have a label indicating the application/service and responsible team they belong to.

## 4. Securing Access to Backend Resources
1. Processes MUST only have the required permissions to resources such as on the file system or database (least privilege principle). Example: “no root permission on databases”.
2. Access to backend systems MUST be authenticated and authorized by the requirements of [{{site.TITLE_IMPL_APISEC}}]({{site.URL_IMPL_APISEC}}).
3. Access to backend systems MUST use dedicated service accounts for each system.
4. Secrets MUST be securely stored and managed (see [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}}))

## 5. Isolation of External Systems
1. Applications MUST be deployed in dedicated isolated production environments.
2. All network communication MUST be encrypted using TLS.
3. All external access to internal network zones MUST be approved.
4. Outgoing communication (egress) to the Internet MUST be restricted (whitelisted) and SHOULD be handled by proxies (e.g. HTTP proxies or SMTP proxies).
5. Incoming communication (ingress) from untrusted networks MUST be restricted and handled by reverse proxies (e.g. API gateways, Web gateways).
6. A web application firewall (WAF) MAY be used as an additional layer of protection for web UIs.

## 6. Administrative Access
Administrative access MUST be as restricted as possible:
1. Limited to required persons only.
2. Access only via personalized accounts (e.g. usernames like “admin” should not be used).
3. Limited to internal network zones or authorized IPs if possible.
4. Using a mandatory 2nd authentication factor (such as hardware tokens, authenticator apps, X.509 client certificates) in combination with a strong user password.
5. All administrative access should be logged in a tamper proof way.
6. Immediately revoked after they are not required anymore (e.g. user changes organizational role).

## 7. System Maintenance
1. Systems MUST be kept up-to-date, especially in terms of security patches.
2. Unused applications MUST be decommissioned.

## 8. Security Scanning
Productive systems MUST be periodically scanned for potential security problems. 

For instance:
- Insecure configurations
- Missing security patches
- Validity and X.509 certificates
- Exposed development artifacts (e.g. SVN files)
- Potential malware infection

## 9. Security Monitoring
For applications with ***assurance class >= [HIGH]***: Possible security incidents MUST be continuously monitored. 

For instance:
- Potential account abuse or system compromise
- Failures in security controls or tests
- Use or assignment of critical security permissions
- DoS (or other) attacks
- Critical security findings from security scans (see above).

## 10. Incident Management

A consistent incident management process (including roles, responsibilities escalation procedures) MUST be implemented and followed.
