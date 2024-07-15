# 12. API Security

Please note: For reasons of simplification, some of the following requirements that refer to API apply to all techncial implementation variants such as XML WebServices, GraphQL or REST APIs.

## 1. General

1. External services SHOULD only be made available externally using a hardened Service/API Gateway.
2. Services SHOULD implement restrictive limits (max. requests per client or time interval).

## 2. Authentication

1. The strength of the authentication mechanism used MUST be adequate to the protection needs.
2. Shared secrets used for services authentication (e.g. API keys or OAuth 2.0 Client Secrets) MUST have the following characteristics:
    - Length min. 32 characters (= 256 bit)
    - Cryptographically random (consisting of alpha-numeric and special characters)
    - Stored securely according to the requirements specified in (11. Protection of Secrets)[B_Implementation_Requirements/11_Secrets.md])
    - Transmitted outside of URLs (e.g. via HTTP POST or HTTP header). 
3. For assurance class >= HIGH, external service-to-service communication SHOULD be authenticated using asymmetric cryptography (e.g. X.509 certificates or signed JWT access tokens).
4. Authentication credentials MUST be unique for different systems and environments (e.g. test, production).

## 3. Access Tokens

1. Services with assurance class >= HIGH SHOULD be protected using Access Tokens (OAuth 2.0 or SAML) 
2. Following requirements do apply to access tokens:
    - Short-lived
    - Restrictive scope
    - Transmitted only via HTTPS
    - Issued by a trusted and hardened  server (e.g. OIDC Identity Server or OAuth 2.0 Authorization Server)
    - created and validated using mature APIs

## 4. OAuth 2.0/OICD Requirements
1. Only 3-Legged: Authorization Code Grant with PKCE (or alternative authorization code binding technique, e.g. “state” binding or OICD Nounces) for both public clients (e.g. single-page applications (SPAs)[^1] SHOULD be used for both public and confidential clients (e.g. server-side web apps).[^2]
2. Only 3-Legged: For CSRF protection, Authorization Code Grant Flows MUST either use the “state” parameter, PKCE, or “OICD Nounces
3. Only 3-Legged: Clients MUST register (and be validated using) full redirect URI as described in RFC 6819 Section 5.2.3.5 (no pattern matching).
4. Service-to-service access SHOULD be protected using Client Credential Grant.
5. HTTPS MUST be used for all communication.

See requirements for Access Tokens above.

## 5. Web UI APIs

1. MUST implement the same security requirements for access to external resources as the corresponding web UI (authentication, validation, etc.).
2. MUST not contain script code (e.g. JavaScript) that is directly executable.
3. MUST contain CSRF protection if working in user context (see section https://secodis.atlassian.net/wiki/spaces/TSSWEB/pages/1179649/8.10+Hardening+of+Session+Management).

## 6. Cross-Domain Access

1. Cross-domain requests MUST be performed using secure mechanisms such as Cross-Origin Resource Sharing (CORS) and a restrictive policy (e.g. restricted so certain hosts or domains or with credential submission deactivated).
2. The origin header of cross-domain requests MUST be authorized on the server-side.

## 7. WebSockets
WebSockets MUST transfer all confidential data with wss:// schema and an additional server-side authorization of the source origin header.

[^1]: See https://tools.ietf.org/html/draft-ietf-oauth-browser-based-apps-00
[^2]: See https://tools.ietf.org/html/draft-ietf-oauth-security-topics-14
