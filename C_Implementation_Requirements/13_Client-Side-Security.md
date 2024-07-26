# {{site.TITLE_IMPL_CLIENTSEC}}

1. Client-side code SHOULD be completely build using mature JavaScript APIs (not ActiveX or Java):
    - JSON code MUST only be parsed with a secure JavaScript API such as `JSON.parse()` (not `eval()`).
    - Instead of unsafe JavaScript APIs that do allow to write HTML code directly (e.g. `.innerHTML`), safe APIs SHOULD be used that only write text output (e.g. `.innerText` or `.textContent`). The same requirement applies to web frameworks that provide such functionality.
3. HTTP header of web-based UIs MUST be implemented according to [{{site.TITLE_IMPL_HTTPHEADERSEC}}]({{site.URL_IMPL_HTTPHEADERSEC}})
4. User states or other meta-information MUST only be stored with sufficient integrity protection (e.g. as a signed JWT token).
5. Only confidential user data MAY be stored on the client-side but this SHOULD only be be in an encrypted way.
6. Secrets MUST be protected
    - ephemeral storage like the SessionStorage (e.g. for access tokens) MUST be used OR
    - secrets (e.g. refresh tokens) MUST be stored encrypted (e.g. in the Keystore) on mobile devices
