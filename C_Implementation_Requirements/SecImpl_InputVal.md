# {{site.TITLE_IMPL_INPUTVAL}}

## 1. General Requirements
1. All untrusted input parameters (e.g. of external interfaces) MUST be validated restrictively.
2. Input validation SHOULD be performed as strictly as possible in respect of allowed data type, length, and range. Examples:
    - Numeric instead of a String datatype,
    - limitations for numeric data types,
    - only allow lists or enums for a String datatype,
    - restricted allowed characters via RegExp for a string (e.g. only `a-z` and `A-Z`).
3. Input validation SHOULD be using a positive validation model (whitelisting).
4. Transmitted data with high integrity protection requirement SHOULD be validated using hash, HMAC or public key encryption.
5. JSON or XML data from untrusted sources (e.g. received by a service) MUST be validated using OpenAPI, bean validation or schema validation (e.g. XML or JSON schema). Schemas SHOULD be restricte where possible (e.g. avoid using unrestricted String datatypes) (see [{{site.TITLE_IMPL_APISEC}}]({{site.URL_IMPL_APISEC}})).
6. An XML parser that process XML content from untrusted sources (e.g. from an external entity) MUST be hardened to prevent common XML-based attacks:
    - Set restrictive limits (e.g. in respect of maximal nesting depth or document size),
    - deactivate processing of external XML entities.
7. In order to prevent insecure object deserialization, it MUST be ensured that objects received and bound from untrusted sources are not hostile or tempered (e.g. by only binding non-sensitive attributes, perform whitelisting or integrity checks.

## 2. Additional Requirements for Web-based UIs
1. Security-relevant input validation MUST be performed on the server-side. Client-side validation MAY be implemented but only for usability reasons in addition to server-side validation or to prevent client-side attacks.
2. Input validation MUST be applied to all types of untrusted input parameters (including hidden form fields and HTTP header such as cookies).
3. Validation of user input SHOULD be performed implicitly with data binding (typecasting) where possible.
4. Validation of non-editable application parameters (no user input) SHOULD be performed implicitly via integrity checks or indirection mappings where possible.
5. In order to remove path truncations like `../../`, directory paths MUST be normalized before input validation is applied to it[^1]. This MAY be done implicitly by using a secure API that removes such truncations automatically.
6. 10. HTML input MUST be validated restrictively with a mature HTML sanitizer API.


[^1]: Often APIs like `getCanonicalPath()` exists for this matter.
