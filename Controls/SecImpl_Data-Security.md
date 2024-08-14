# B.10 - Data Security

## B.10.1 General

Only standard and mature cryptographic algorithms, operation modes, key lengths ciphers, and implementations MUST be used.

## B.10.2 Encryption at Transit

1. All external communication MUST only be possile via TLS/HTTPS.
3. In cases where access requires HTTPS, requests via HTTP MUST be redirected to HTTPS. This SHOULD be implemented with a permanent redirection (HTTP 301).
4. HTTPS servers MUST only support current secure ciphers and protocols. Insecure or deprecated ones (e.g. SSLv2, TLSv1.0, TLSv1.1 and RC4 cipher) MUST be deactivated [^1].
5. Effective TLS settings MUST be periodically tested using a suitable tool [^2].
6. Confidential data MUST only be sent within the HTTP request body (e.g. via HTTP POST) or header but not within URLs.
7. Transmission on untrusted channels (e.g. the Internet) MUST
    - only be possible with HTTPS using valid certificates.
    - using HTTP Strict Transport Security (HSTS) headers and
    - only be sent with anti-caching response headers (see [{{site.TITLE_MATERIAL_SECHEADER}}]({{site.URL_MATERIAL_SECHEADER}})).

## B.10.2 X.509 Certificates

1. External HTTPS connections MUST use valid X.509 certificates issued by a trusted certificate authority (CA).
2. X.509 certificates MUST use RSA with at least 3072 bit or ECDSA with at least 256 bit keys[^4].
3. External customer applications (UIs) SHOULD use Extended Validation (EV) certificates.
4. Wildcard certificated MUST not be used.

## B.10.4 Encryption at Rest

1. Confidential data MUST be encrypted before stored.
2. Access to encryption keys MUST be handles according to the requirements specified in [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}})
3. Only secure algorithms MUST be used for encryption[^3].
4. User passwords MUST be persisted according to requirements at [{{site.TITLE_IMPL_USERPASSWD}}]({{site.URL_IMPL_USERPASSWD}}).

## B.10.5 Cryptographic Integrity Checks

1. Security-sensitive integrity validation MUST be performed using either cryptographic hash functions (e.g. SHA256)[^5] or using public key cryptography[^4].

## B.10.6 Keys

1. Keys or tokens that are used for security purposes (e.g. as access tokens, passwords of technical users, or API keys) MUST be cryptographically random and created by an [PRNG](https://en.wikipedia.org/wiki/Pseudorandom_number_generator)[^6].

   
[^1]: See [SSL Best Practices by SSL.com](https://www.ssl.com/guide/ssl-best-practices/) or [OWASP TLS Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Transport_Layer_Security_Cheat_Sheet.html) for details.
[^2]: If you have an external endpoint you can use [SSL Test by Qualys](https://www.ssllabs.com/ssltest/) to test your settings.
[^3]: See [NIST 800-131A,R2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-131Ar2.pdf), Chap 1, Table 1, pg. 7
[^4]: See [NIST 800-131A,R2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-131Ar2.pdf), Chap 2, Table 2, pg. 9 
[^5]: See [NIST 800-131A,R2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-131Ar2.pdf), Chap 9, Table 9, pg. 18
[^6]: To archive this you may use an [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) or generate one directly using the OpenSSL CLI. Here is an example for creating a 256bit token encoded as Base64 `$ openssl rand -base64 32` 
