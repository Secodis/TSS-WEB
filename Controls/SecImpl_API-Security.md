# B.12 - API Security

Please note: For reasons of simplification, some of the following requirements that refer to API apply to all techncial implementation variants such as XML WebServices, GraphQL or REST APIs.

## {{site.TITLE_IMPL_APISEC_GENERAL}}

1. APIs MUST be restricted validated using Open API Schema (see [{{site.TITLE_IMPL_INPUTVAL}}]({{site.URL_IMPL_INPUTVAL}})).
2. External APIs SHOULD only be made available externally using a hardened service or API gateway.
3. APIs SHOULD implement restrictive limits based on business requirements (aka rate limiting, e.g. max. requests per client within time interval)[^1].

## {{site.TITLE_IMPL_APISEC_AUTH}}

1. The strength of the authentication mechanism used MUST be adequate to the protection needs.
2. Shared secrets used for API authentication (e.g. API keys or OAuth 2.0 Client Secrets) MUST have the following characteristics:
    - Implemented according to [{{site.TITLE_IMPL_DATASEC_TOKENS}}]({{site.URL_IMPL_DATASEC_TOKENS}}))
    - Stored securely according to the requirements specified in [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}}))
    - Transmitted outside of URLs (e.g. via HTTP POST or HTTP header). 
3. For *risk class >= [HIGH]*, external service-to-service communication SHOULD be authenticated using asymmetric cryptography (e.g. X.509 certificates or signed JWT access tokens).
4. Authentication credentials MUST be unique for each service/system and environment (e.g. serviceX in dev, serviceX test, sericeX in production).

## {{site.TITLE_IMPL_APISEC_ACCESS-TOKENS}}

1. Services with *risk class >= [HIGH]* SHOULD be protected using Access Tokens (OAuth 2.0 or SAML) 
2. Following requirements do apply to access tokens:
    - Short-lived (minutes or hours)
    - Implemented arrocrind to [{{site.TITLE_IMPL_DATASEC_TOKENS}}]({{site.URL_IMPL_DATASEC_TOKENS}})
    - Restrictive scope & audiance
    - Transmitted only via HTTPS/TLS
    - Issued by a trusted and hardened access server (e.g. OIDC Identity Server or OAuth 2.0 Authorization Server)
    - created and validated using mature frameworks.
3. If the token is encoded as a JSON Web Token (JWT), the encryption method MUST be verified.

## {{site.TITLE_IMPL_APISEC_OAUTH2}}

1. For user authentication (3-legged):
    - Authorization Code Grant with PKCE (or alternative authorization code binding technique, e.g. “state” binding or OICD Nounces) for both public clients (e.g. single-page applications (SPAs)[^2] SHOULD be used for both public and confidential clients (e.g. server-side web apps).[^3]
    - For CSRF protection, Authorization Code Grant Flows MUST either use the “state” parameter, PKCE, or “OICD Nounces"
    - Clients MUST register (and be validated using) full redirect URI as described in [RFC 6819 Section 5.2.3.5](https://datatracker.ietf.org/doc/html/rfc6819#section-5.2.3.5) (no pattern matching).
    - Refresh tokens MUST be secured according to [{{site.TITLE_IMPL_SECRETS}}]({{site.URL_IMPL_SECRETS}})
2. Service-to-service access SHOULD be protected using Client Credential Grant.
3. HTTPS MUST be used for all communication.

See also requirements [{{site.TITLE_IMPL_APISEC_ACCESS-TOKENS}}]({{site.URL_IMPL_APISEC_ACCESS-TOKENS}}).

## {{site.TITLE_IMPL_APISEC_FRONTEND-APIS}}

APIs that are used as a backend for client-side frontend (e.g. SPAs):

1. MUST implement the same security requirements for access to external resources as the corresponding UI (authentication, validation, etc.)
2. MUST not contain script code (e.g. JavaScript) that is directly executable
3. MUST contain CSRF protection if working in user context (see [{{site.TITLE_IMPL_SESSIONMGMT}}]({{site.URL_IMPL_SESSIONMGMT}}))

## {{site.TITLE_IMPL_APISEC_X-DOMAIN-ACCESS}}

1. Cross-domain requests MUST be performed using secure mechanisms such as Cross-Origin Resource Sharing (CORS) and a restrictive policy (e.g. restricted so certain hosts or domains or with credential submission deactivated).
2. The origin header of cross-domain requests MUST be authorized on the server-side.

## {{site.TITLE_IMPL_APISEC_WEBSOCKETS}}

WebSockets MUST transfer all confidential data with `wss://` schema and an additional server-side authorization of the source origin header.

[^1]: This control aims to prevent denial-of-service (DoS) conditions, which can occur both deliberately and accidentally, such as those triggered by a client malfunction.
[^2]: See [https://tools.ietf.org/html/draft-ietf-oauth-browser-based-apps-00](https://tools.ietf.org/html/draft-ietf-oauth-browser-based-apps-00)
[^3]: See [https://tools.ietf.org/html/draft-ietf-oauth-security-topics-14](https://tools.ietf.org/html/draft-ietf-oauth-security-topics-14)
