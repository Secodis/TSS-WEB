# 2. Secure Operation

The following requirements apply to systems (infrastructure, platforms or other runtime environments) on which applications in target production environment are executed:

## 2.1. Environment Separation
Systems in production MUST be strictly separated from development and test systems:
1. Production and development MUST be separated using different environments (e.g. in cloud environments using separate accounts/subscriptions).
2.  Connections between different environments MUST not be possible
3.  Production data SHOULD not be used on non-production systems (exceptions see 6. Security Tests).
4.  Users and systems MUST be authorized separately for each environment.
5.  Access servers SHOULD be separated instances for all environments but MUST be at least use separate realms.

## 2.2. System Hardening
Systems (e.g. web servers, application servers, container platforms or content management systems, cloud platforms or other runtime environments) MUST be hardened according to common best practices. 

This includes:
- A hardened OS (e.g. using a hardened base image, see below)
- Deactivation of all services, plugins and other functionality that is not needed, especially if they are exposed (executable from remote)
- Hardened SSL/TLS stack (see 8.10 Data Security & Cryptography)
- Activated security headers according to Appendix A: Requirements for HTTP Security Header
- Removal of samples and other default content
- Execution of network services (e.g. web or application servers) with only minimal privileges and isolated from other processes if possible (e.g. as an isolated container or dedicated server instance, VM or host)
- Network services bound to localhost if access only required from same system.
- Network services should only be accessible from certain IPs if possible.
- Deactivation of file handlers that are not required (e.g. “.php” for a Java application).
- Deactivation of insecure HTTP methods (e.g. TRACE and TRACK)
- Web and application servers must not disclose details on the server-side software stack (e.g. version numbers). Related HTTP response headers such as “Server” or “X-Powered-By” are to be deactivated or filtered.

## 2.3. Docker Security
1. Docker images MUST only be build using trusted repositories.
2. Docker images MUST only use selected base images.
3. Docker images MUST be updating OS packages at build.
4. Docker images MUST be scanned for insecure 3rd party components and insecure configuration.
5. Docker images MUST not consists of a remote shell like SSH or telnet.
6. Docker container MUST have a maximal lifetime after which they have to be rebuild with updated OS dependencies. 

## 2.4. Securing Access to Backend Resources
1. Every process MUST only have the required permissions to resources such as on the file system or database (least privilege principle). Example: “no root permission on databases”.
2. Access to backend systems MUST be authenticated and authorized in accordance to requirements of 8.13 Service & API Security
3. Access to backend systems MUST use dedicated credentials for each system.
4. Secrets MUST be securely stored and managed (see 8.11 Protection of Secrets)

## 2.5. Isolation of External Systems:
1. Applications that are directly accessible from the Internet (or other untrusted networks) MUST be deployed in an isolated network zone.
2. All external communication MUST be encrypted using TLS/HTTPS.
3. All external access to internal network zones MUST be approved.
4. Outgoing communication (egress) to the Internet MUST be restricted and SHOULD be handled by proxies (e.g. HTTP proxies or SMTP proxies).
5. Incoming communication (ingress) SHOULD be handled by reverse proxies (e.g. API gateways, Web gateways).
6. A web application firewall (WAF) MAY be used here, e.g. as an additional layer of protection, for virtual patching or as an application IDS. 

## 2.6. Administrative Access
Administrative access MUST be as restricted as possible:
1. Limited to required persons only, if possible using dedicated personal accounts.
2. Username “admin” should not be used.
3. Limited to internal network zones or authorized IPs if possible.
4. Using a mandatory 2nd authentication factor (such as hardware tokens, authenticator apps, X.509 client certificates) in combination with a strong user password.
5. All administrative access should be logged in a tamperproof way.
6. Immediately revoked after they are not required anymore (e.g. user changes organizational role).

## 2.7. System Maintenance
1. Systems MUST be kept up-to-date, especially in terms of security patches.
2. Unused applications MUST be decommissioned.

# 2.8. Security Scanning
Productive systems MUST be periodically scanned for potential security problems. 

For instance:
- Insecure configurations
- Missing security patches
- Validitiy and X.509 certificates
- Exposed development artifacts (e.g. SVN files)
- Potential malware infection

# 2.9. Security Monitoring
For applications with assurance class >= [HIGH] Possible security incidents MUST be continuously monitored. 

For instance:
- Potential account abuse or system compromise
- Failures in security controls or tests
- Use or assignment of critical security permissions
- DoS (or other) attacks
- Critical security findings from security scans (see above).

# 2.10. Incident Management

A consistent incident management process (including roles, responsibilities escalation procedures) MUST be implemented and followed.
