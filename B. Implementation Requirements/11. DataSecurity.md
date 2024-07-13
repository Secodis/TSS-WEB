# 10. Data Security & Cryptography

## 1. General

Only standard and mature cryptographic algorithms, operation modes, key lengths ciphers, and implementations MUST be used.

## 2. Encryption at Transit

1. Transmission of sensitive data SHOULD generally only be possible via TLS/HTTPS.
2. In cases where access requires HTTPS, requests via HTTP MUST be redirected to HTTPS. This SHOULD be implemented with a permanent redirection (HTTP 301).
3. HTTPS servers MUST only support current secure ciphers and protocols. Insecure ones (e.g. SSLv2 and RC4 cipher) MUST be deactivated.
4. Confidential data MUST only be sent within the HTTP Request Body (e.g. via HTTP POST) but not within URLs (exception: object IDs).
5. Transmission on untrusted channels (e.g. the Internet) MUST
    - only be possible with HTTPS using valid certificates.
    - using HTTP Strict Transport Security (HSTS) headers  https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/950292 and
    - only be sent with anti-caching response headers (see https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/1015832).

## 3. Encryption at Rest
1. Confidential data MUST be encrypted before stored.
2. User passwords MUST be persisted with suitable methods (see section https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/98391).

## 4. X.509 Certificates
1. External HTTPS connections MUST use valid X.509 certificates issued by a trusted authority (CA).
2. X.509 certificates MUST use RSA with >= 2048 bit or ECC with >= 256 bit.
3. External customer applications (UIs) SHOULD use EV certificates.
