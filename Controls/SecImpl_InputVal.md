# B.2 - Input Validation

## {{site.TITLE_IMPL_INPUTVAL_GENERAL}}

1. All untrusted input parameters (e.g. of external interfaces) MUST be validated restrictively where possible.
2. Validation policy SHOULD be defined by the data owner.
3. Input validation SHOULD be performed as strictly as possible with respect to allowed data type, length, and range. Examples:
    - Numeric instead of a String datatype,
    - limitations for numeric data types (e.g. range, length),
    - only allow lists or enums for a String datatype,
    - restricted allowed characters via RegExp for a string (e.g. only `a-z` and `A-Z`).
4. Input validation SHOULD be using a positive validation model (whitelisting).
5. In order to prevent deserialization attacks, untrusted data SHOULD generally not be deserialized.
6. Data with high integrity protection requirements SHOULD be validated using cryptographic integrity checks (see [{{site.TITLE_IMPL_CRYPTO}}]({{site.URL_IMPL_CRYPTO}})).
7. JSON or XML data from untrusted sources (e.g. received by a service) MUST be validated using schema validation (e.g. OpenAPI, XML, or JSON schema) or bean validation. Schemas SHOULD be restrrictive where possible (e.g. avoid using unrestricted String datatypes) (see [{{site.TITLE_IMPL_APISEC}}]({{site.URL_IMPL_APISEC}})).
8. An XML parser that processes XML content from untrusted sources (e.g. from an external entity) MUST be hardened to prevent common XML-based attacks:
    - Set restrictive limits (e.g. with respect to maximal nesting depth or document size),
    - deactivate processing of external XML entities.
9. In order to prevent insecure object deserialization, it MUST be ensured that objects received and bound from untrusted sources are not hostile or tempered (e.g. by only binding non-sensitive attributes, performing whitelisting or integrity checks.

## {{site.TITLE_IMPL_INPUTVAL_UIs}}

1. Security-relevant input validation MUST be performed on the server side. Client-side validation MAY be implemented but only for usability reasons in addition to server-side validation or to prevent client-side attacks.
2. Input validation MUST be applied to all types of untrusted input parameters (including hidden form fields and HTTP headers such as cookies).
3. Validation of user input SHOULD be performed implicitly with data binding (typecasting) where possible.
4. Validation of non-editable application parameters (no user input) SHOULD be performed implicitly via integrity checks or indirection mappings where possible.
5. In order to remove path truncations like `../../`, directory paths MUST be normalized before input validation is applied to them [^1]. This MAY be done implicitly by using a secure API that removes such truncations automatically.
6. HTML input MUST be validated restrictively with a mature HTML sanitizer API.
7. Redirects MUST be checked against a list of allowed URLs or hosts.

[^1]: Often APIs like `getCanonicalPath()` exists for this matter.
