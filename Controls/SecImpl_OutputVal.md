# B.4 - Output Validation & Encoding

1. Every access to backend systems such as databases MUST be parameterized[^1], e.g. via prepared statements, OR mappers (e.g. Hibernate) when an API for this matter does exist.
2. All parameters, either internally or user-controlled, MUST be declared as parameters within a prepared statement (or similar API) call.
3. In case an API does not provide any methods for parameterized statements, parameters MUST be encoded with suitable APIs (e.g. SQL encoding) to prevent interpreter injection.
4. User-controlled parameters MUST be encoded with a suitable API and method related to its output context if written into a webpage:
    - HTML context: HTML entity encoding
    - JavaScript context: JavaScript escaping
    - CSS context: CSS escaping
5. Output encoding SHOULD only be implemented with mature APIs and frameworks.
6. Implicit validation (e.g. via ORM frameworks or template technologies) SHOULD be preferred to explicit validation (API calls).

[^1]: Each parameter needs to be defined explicitly as a parameter (e.g. with a `setParam()` statement) or indirectly by a framework.
