# 2. Input Validation

1. All untrusted input parameters (e.g. of external interfaces) MUST be validated restrictively.
2. Security-relevant input validation MUST be performed on the server-side. Client-side validation MAY be implemented but only for usability reasons in addition to server-side validation or to prevent client-side attacks.
3. Input validation SHOULD be performed as strictly as possible in respect of allowed data type, length, and range. Examples:
    - Numeric instead of a String datatype,
    - limitations for numeric data types or
    - restricted allowed characters for a string (e.g. only `a-z` and `A-Z`).
4. Input validation MUST be applied to all types of untrusted input parameters (including hidden form fields and HTTP header such as cookies).
5. In order to remove path truncations like `../../`, directory paths MUST be normalized / before input validation is applied to it[^1]. This MAY be done implicitly by using a secure API that removes such truncations automatically.
6. Input validation SHOULD be using a positive validation model (whitelisting).
7. Validation of user input SHOULD be performed implicitly with data binding (typecasting) where possible.
8. Validation of non-editable application parameters (no user input) SHOULD be performed implicitly via integrity checks or indirection mappings where possible.
9. HTML input MUST be validated restrictively with a mature HTML sanitizer API.
10. JSON or XML data from untrusted sources (e.g. received by a service) MUST be validated indirectly (e.g. via bean validation) or directly via an XML Schema. This MUST be done restrictively as described above.
11. An XML parser that process XML content from untrusted sources (e.g. from an external entity) MUST be hardened to prevent common XML-based attacks:
    - Set restrictive limits (e.g. in respect of maximal nesting depth or document size),
    - deactivate processing of external XML entities.
12. In order to prevent insecure object deserialization, it MUST be ensured that objects received and bound from untrusted sources are not hostile or tempered (e.g. by only binding non-sensitive attributes, perform whitelisting or integrity checks.

[^1]: Often APIs like `getCanonicalPath()` exists for this matter.
