# B.9 - Error Handling and Logging

1. It MUST be ensured that in the event of any error (expected or unexpected), the application stays in a secure state in which that no internal information (such as stack traces) is disclosed to users.
2. Security exceptions SHOULD be thrown in case of security failures.
3. Security-relevant events (e.g. user log-ins, unauthorized access to sensitive data, sensitive actions on a user profile, potential misuse or attacks) MUST be logged.
4. The following information SHOULD be logged as part of a security event:
    - Security tag (`[SEC]`)
    - Timestamp
    - Subject (e.g. user ID, source IP)
    - Event description (e.g. sensitive access / change to object)
    - Relevant component
    - Result
5. Technical logs MUST not contain Personal Identifiable Information (PII).
