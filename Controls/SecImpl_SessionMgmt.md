<title>{{site.TITLE_IMPL_SESSIONMGMT}</title>

# {{site.TITLE_IMPL_SESSIONMGMT}}

## 1. General
1. The session management MUST be based on the standard implementation of the application server or web container.
2. Session IDs MUST be
    - at least 120 bit strong,
    - generated with a cryptographically secure pseudorandom number generator (CSPRNG) and be completely random,
    - transferred encrypted (via TLS/HTTPS) on insecure networks
    - renewed after every successful user authentication,
    - NOT be transmitted in URLs.
  
## 2. Session Cookies   
Session cookies MUST be restricted in respect of their validity:
1. Set both security attributes `httpOnly`, `secure` and `SameSite`
2. Avoid persistent cookies (don’t set expire attribute)
3. Set a path attribute to the base URL in case multiple applications are operated on the same system.

## 3. Authenticated Sessions
Authenticated server-side sessions
1. MUST be invalidated after a user has been logged-in successfully,
2. MUST be invalidated after an authenticated user has been idle for more than 30 minutes (idle or soft logout),
3. SHOULD be invalidated after a user session has been active more than 24 hours, and
4. SHOULD only exist once per user. When a user logs on, all existing session object of this user SHOULD be invalidated.

## 4. CSRF Protection
All state-changing operations (create, update, delete) on an authenticated user session MUST be protected against session replay and Cross-site Request Forgery (CSRF).
1. State-changing operations MUST be protected with a cryptographic random replay token (e.g. as an additional Hidden Fields or as X-header) that is unique for the user session or a specific request and for instance.
2. State-changing operations MUST be denied if a CSRF token is invalid or missing.
3. If a web framework provides an own CSRF protection mechanism, then this SHOULD be used.
4. State-changing operations MUST NOT be possible via HTTP GET.
