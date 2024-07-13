# 12. Client-Side Security

1. Client-side code SHOULD be completely build using mature JavaScript APIs (not ActiveX or Java):
    - JSON code MUST only be parsed with a secure JavaScript API such as `JSON.parse()` (not `eval()`).
    - Instead of unsafe JavaScript APIs that do allow to write HTML code directly (e.g. `.innerHTML`), safe APIs SHOULD be used that only write text output (e.g. `.innerText` or `.textContent`). The same requirement applies to web frameworks that provide such functionality.
3. HTTP header of Web UIs MUST be implemented according to Appendix A: Requirements for HTTP Security Header.
4. Only confidential user data MAY be stored on the client-side but this SHOULD only be be in an encrypted way.
5. User states or other meta-information MUST only be stored with sufficient integrity protection (e.g. as a signed JWT token).
