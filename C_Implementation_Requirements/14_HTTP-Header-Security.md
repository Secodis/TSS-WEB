# {{site.TITLE_IMPL_HTTPHEADERSEC}}

Modern web browsers support several additional client-side protection mechanisms that can be activated using HTTP response headers. The table below describes related requirements and recommendations for external Web UIs and services in production:

**Headers that can be centrally included:**

| Response Header  | Value |
| ------------- | ------------- | 
| Content-Type  | `...; charset=utf-8`  |  
| Strict-Transport-Security[^1]  | `max-age=10886400; includeSubDomains; preload`  | 
| X-Frame-Options  | `SAMEORIGIN`  | 
| Referrer Policy | `same-origin` |
| X-Content-Type-Options[^2] | `nosniff` |

**Headers that must be set within a Web application:**

| Response Header  | Value | When? |
| ------------- | ------------- | ------------- |
| Set-Cookie  | `… ;httpOnly; secure; SameSite=Lax`  | When the transfer of confidential data in cookies |
| Cache-Control  | `no-cache, no-store`  | Whenever confidential data is transmitted.  |
| Pragma  | `no-cache`  | Whenever confidential data is transmitted.  | 
| Expires  | `-1`  | Whenever confidential data is transmitted.  | 
| Content-Security-Policy[^3] | `object-src 'none'; script-src ‘self’ [URL1] [URL2]; style-src ‘self’ unsafe-inline; object-src ‘self‘;base-uri 'none';` | General recommendation for new for all Web UIs. Not required for APIs.|
| Content-Security-Policy[^3] | `object-src 'none'; script-src 'nonce-{random}' 'unsafe-inline' 'unsafe-eval' 'strict-dynamic' https: http:; base-uri 'none';report-uri https://your-report-collector.example.com/` | Recommendation for new Web UIs that must use inline script blocks (e.g., if integrated by a JS framework): Avoid using this setting unless necessary, as it disables CSP protection for older browsers. |
| Content-Disposition | `attachment; filename=<filename>` | Web pages at which users can potentially download untrusted files. |
| X-Download-Options | `noopen` | Web UIs at which users can potentially download untrusted files. |

**Caution: Settings these headers may have implications on the proper functionality of a web application. Therefore, activating a new header SHOULD always be combined with comprehensive functional tests.**

[^1]: HTTP Strict Transport Security (HSTS) forces users of a website to exclusively access it via HTTPS for a defined amount of time. Before using this header, you should ensure that all requests to this host (and to all subdomains when using `includeSubDomains` attribute) can be executed using HTTPS. This header prevents certain man-in-the-middle attacks.
[^2]: Deactivation of MIME sniffing in browsers that are used to identify MIME types but also to execute certain Cross-site Scripting attacks.
[^3]: A Content Security Policy (CSP) provides additional but very effective client-side protection against many common client-site attacks such as Cross-site Scripting (XSS). Applications must explicitly support it which often requires a CSP-compliant MVC framework. For more practical CSP recommendations have a look at [https://web.dev/articles/strict-csp](https://web.dev/articles/strict-csp).
