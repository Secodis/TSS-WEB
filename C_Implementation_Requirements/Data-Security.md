# {{site.TITLE_IMPL_CRYPTO}}

## 1. General

Only standard and mature cryptographic algorithms, operation modes, key lengths ciphers, and implementations MUST be used.

## 2. Encryption at Transit

1. Transmission of sensitive data SHOULD generally only be possible via TLS/HTTPS.
2. In cases where access requires HTTPS, requests via HTTP MUST be redirected to HTTPS. This SHOULD be implemented with a permanent redirection (HTTP 301).
3. HTTPS servers MUST only support current secure ciphers and protocols. Insecure ones (e.g. SSLv2, TLSv1.0, TLSv1.1 and RC4 cipher) MUST be deactivated.
4. Confidential data MUST only be sent within the HTTP request body (e.g. via HTTP POST) or header but not within URLs.
5. Transmission on untrusted channels (e.g. the Internet) MUST
    - only be possible with HTTPS using valid certificates.
    - using HTTP Strict Transport Security (HSTS) headers and
    - only be sent with anti-caching response headers (see [{{site.TITLE_MATERIAL_SECHEADER}}]({{site.URL_MATERIAL_SECHEADER}})).

## 3. Encryption at Rest
1. Confidential data MUST be encrypted before stored.
2. Access to encryption keys MUST be as restricted as possible.
3. User passwords MUST be persisted with suitable methods (see [{{site.TITLE_IMPL_USERPASSWD}}]({{site.URL_IMPL_USERPASSWD}})).
4. Secrets MUST be stored securely according to the requirements specified in [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}})

## 4. X.509 Certificates
1. External HTTPS connections MUST use valid X.509 certificates issued by a trusted authority (CA).
2. X.509 certificates MUST use RSA with >= 3072 bit or ECC with >= 256 bit.
3. External customer applications (UIs) SHOULD use EV certificates.
4. Wildcard certificated MUST not be used.

## 5. Tokens
1. Tokens that are used for security purposes (e.g. as access tokens) MUST be cryptographically random and created by an [PRNG](https://en.wikipedia.org/wiki/Pseudorandom_number_generator).[^1]


[^1]: To archive this you may use an [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) or generate one directly using the OpenSSL CLI. Here is an example for creating a 256bit token encoded as Base64 `$ openssl rand -base64 32` 
