# B.13 - Client-Side Security

1. Client-side UIs SHOULD be completely build using mature JavaScript or Typescript frameworks such as React, Angular, or Vue (no ActiveX or Java):
    - JSON code MUST only be parsed with a secure API such as `JSON.parse()` (not `eval()`).
    - Instead of unsafe JavaScript APIs that inject HTML code directly (e.g. `.innerHTML`), safe APIs SHOULD be used that only output text (e.g. `.innerText` or `.textContent`). This requirement also extends to any other web frameworks or API that offer similar functionality.
3. HTTP header of web-based UIs MUST be implemented according to [{{site.TITLE_IMPL_HTTPHEADERSEC}}]({{site.URL_IMPL_HTTPHEADERSEC}})
4. User states or other meta-information MUST only be stored with sufficient integrity protection (e.g. as a signed JWT token).
5. Only confidential user data MAY be stored on the client-side but this SHOULD only be be in an encrypted way.
6. Secrets MUST be protected if their use is not avoidable:
    - ephemeral storage like the `SessionStorage` (e.g. for access tokens) MUST be used OR
    - secrets (e.g. refresh tokens) MUST be stored encrypted (e.g. in the Keystore) on mobile devices
