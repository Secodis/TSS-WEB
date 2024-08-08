# B.12 - API Security

Please note: For reasons of simplification, some of the following requirements that refer to API apply to all techncial implementation variants such as XML WebServices, GraphQL or REST APIs.

## 1. General

1. APIs MUST be restricted validated using Open API Schema (see [{{site.TITLE_IMPL_INPUTVAL}}]({{site.URL_IMPL_INPUTVAL}}))
2. External APIs SHOULD only be made available externally using a hardened service/API gateway.
3. APIs SHOULD implement restrictive limits (aka rate limiting, max. requests per client or time interval).

## 2. Authentication

1. The strength of the authentication mechanism used MUST be adequate to the protection needs.
2. Shared secrets used for API authentication (e.g. API keys or OAuth 2.0 Client Secrets) MUST have the following characteristics:
    - Length min. 32 characters (= 256 bit)
    - Cryptographically random (see [{{site.TITLE_IMPL_CRYPTO}}]({{site.URL_IMPL_CRYPTO}}))
    - Stored securely according to the requirements specified in [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}}))
    - Transmitted outside of URLs (e.g. via HTTP POST or HTTP header). 
3. For *risk class >= [HIGH]*, external service-to-service communication SHOULD be authenticated using asymmetric cryptography (e.g. X.509 certificates or signed JWT access tokens).
4. Authentication credentials MUST be unique for different systems and environments (e.g. test, production).

## 3. Access Tokens

1. Services with *risk class >= HIGH* SHOULD be protected using Access Tokens (OAuth 2.0 or SAML) 
2. Following requirements do apply to access tokens:
    - Short-lived (minutes or hours)
    - Cryptographically random (see [{{site.TITLE_IMPL_CRYPTO}}]({{site.URL_IMPL_CRYPTO}}))
    - Restrictive scope & audiance
    - Transmitted only via HTTPS/TLS
    - Issued by a trusted and hardened  server (e.g. OIDC Identity Server or OAuth 2.0 Authorization Server)
    - created and validated using mature frameworks.
3. If the token is encoded as a JWT, the encryption method MUST be verified.

## 4. OAuth 2.0/OICD Requirements
1. For user authentication (3-legged):
    - Authorization Code Grant with PKCE (or alternative authorization code binding technique, e.g. “state” binding or OICD Nounces) for both public clients (e.g. single-page applications (SPAs)[^1] SHOULD be used for both public and confidential clients (e.g. server-side web apps).[^2]
    - For CSRF protection, Authorization Code Grant Flows MUST either use the “state” parameter, PKCE, or “OICD Nounces"
    - Clients MUST register (and be validated using) full redirect URI as described in [RFC 6819 Section 5.2.3.5](https://datatracker.ietf.org/doc/html/rfc6819#section-5.2.3.5) (no pattern matching).
    - Refresh tokens MUST be secured according to [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}})
2. Service-to-service access SHOULD be protected using Client Credential Grant.
3. HTTPS MUST be used for all communication.

See also requirements for Access Tokens above.

## 5. Frontend APIs 

1. MUST implement the same security requirements for access to external resources as the corresponding UI (authentication, validation, etc.)
2. MUST not contain script code (e.g. JavaScript) that is directly executable
3. MUST contain CSRF protection if working in user context (see [{{site.TITLE_IMPL_SESSIONMGMT}}]({{site.URL_IMPL_SESSIONMGMT}}))

## 6. Cross-Domain Access

1. Cross-domain requests MUST be performed using secure mechanisms such as Cross-Origin Resource Sharing (CORS) and a restrictive policy (e.g. restricted so certain hosts or domains or with credential submission deactivated).
2. The origin header of cross-domain requests MUST be authorized on the server-side.

## 7. WebSockets
WebSockets MUST transfer all confidential data with `wss://` schema and an additional server-side authorization of the source origin header.

[^1]: See [https://tools.ietf.org/html/draft-ietf-oauth-browser-based-apps-00](https://tools.ietf.org/html/draft-ietf-oauth-browser-based-apps-00)
[^2]: See [https://tools.ietf.org/html/draft-ietf-oauth-security-topics-14](https://tools.ietf.org/html/draft-ietf-oauth-security-topics-14)
