# {{site.TITLE_GENERAL_TERMS}}

The following requirements apply to systems (infrastructure, platforms, or other runtime environments) on which applications in the target production environment are executed:

## 1. Environment Separation
Systems in production MUST be strictly separated from development and test systems:
1. Production, test, and development systems MUST be separated using different environments (e.g. in separate clusters, cloud environments using separate accounts/subscriptions).
2. Connections between different environments MUST not be possible.
3. Ressources MUST not be shared between production and other environments (especially no secret storages).
4. Users and systems MUST be authorized separately for each environment.
5. Access servers SHOULD be separated instances for all environments but MUST at least use separate realms.
6. Access to the production environment MUST be granted strictly on a need-to-know & least-privilege basis (see 2.6 Administrative Access below) and SHOULD be automated where possible.
7. Production data SHOULD not be used on non-production systems (exceptions see [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}})).
   
## 2. System Hardening
Systems (e.g. web servers, application servers, container platforms or content management systems, cloud platforms, or other runtime environments) MUST be hardened according to common best practices. 

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

## 3. Docker Security
1. Docker images MUST only be built using trusted repositories.
2. Docker images MUST only use selected base images.
3. Docker images MUST be updating OS packages at build.
4. Docker images MUST be scanned for insecure 3rd party components and insecure configuration.
5. Docker images MUST not consist of a remote shell like SSH or telnet.
6. Docker containers MUST have a maximal lifetime after which they have to be rebuilt with updated OS dependencies. 

## 4. Securing Access to Backend Resources
1. Every process MUST only have the required permissions to resources such as on the file system or database (least privilege principle). Example: “no root permission on databases”.
2. Access to backend systems MUST be authenticated and authorized by the requirements of [{{site.TITLE_IMPL_APISEC}}]({{site.URL_IMPL_APISEC}}).
3. Access to backend systems MUST use dedicated service accounts for each system.
4. Secrets MUST be securely stored and managed (see [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}}))

## 5. Isolation of External Systems
1. Applications MUST be deployed in a dedicated isolated production environment that can be shared with other applications.
2. Application with assurance class >= [HIGH] MUST be completely isolated in terms of security realm, namespace, etc.
3. All network communication MUST be encrypted using TLS
4. All external access to internal network zones MUST be approved.
5. Outgoing communication (egress) to the Internet MUST be restricted and SHOULD be handled by proxies (e.g. HTTP proxies or SMTP proxies).
6. Incoming communication (ingress) SHOULD be restricted and handled by reverse proxies (e.g. API gateways, Web gateways).
7. A web application firewall (WAF) MAY be used here, e.g. as an additional layer of protection, for virtual patching, or as an application IDS. 

## 6. Administrative Access
Administrative access MUST be as restricted as possible:
1. Limited to required persons only, if possible using dedicated personal accounts.
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
For applications with assurance class >= [HIGH]: Possible security incidents MUST be continuously monitored. 

For instance:
- Potential account abuse or system compromise
- Failures in security controls or tests
- Use or assignment of critical security permissions
- DoS (or other) attacks
- Critical security findings from security scans (see above).

## 10. Incident Management

A consistent incident management process (including roles, responsibilities escalation procedures) MUST be implemented and followed.
