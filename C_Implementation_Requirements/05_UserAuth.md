# {{site.TITLE_IMPL_USERAUTH}}

1. User registration MUST be implemented with an identification method that is suitable for the assurance class of the application it is used for:
    - <= [STANDARD]: E-mail addresses MAY be used.
    - [HIGH]: An additional factor (e.g. mobile phone) SHOULD be used.
    - [VERY HIGH]: Personal identification is required.
2. Users MUST NOT be allowed to log into the application before their identification process has been completed.
3. Registration and authentication of external users MUST be implemented on external applications in a way that they prevent automated attacks (e.g. brute forcing). Examples are delays or CAPTCHAs.
4. User authentication MUST be implemented with suitable mechanisms in respect of the assurance class:
    - <= [STANDARD]: Password-based authentication with secure methods and protocols. Password must be compliant to the password policy (NIST Authenticator Assurance Level 1[^1]).
    - [HIGH]: Same requirements as for standard but with an additional authentication factor. This factor must be exchanged using a separate and secure channel or layer of communication. It may be stored on the same system where the password is entered through (soft crypto token). Examples are X.509 certificates, one-time tokens that are sent via SMS or e-mail, time-based tokens (e.g. via Google Authenticator App), or IP addresses. (NIST Authenticator Assurance Level 2).
    - [VERY HIGH]: Same as High but with the authentication factor required to be generated on a separate system (hard crypto token) that has been approved for this purpose. Examples are RSA SecureID tokens (NIST Authenticator Assurance Level 3).
5. HTTP Basic authentication SHOULD only be used as additional access protection and MUST always be used with HTTPS.
6. Usernames SHOULD be personalized.
7. In case a user login fails, the application MUST NOT disclose information on the cause of the error (e.g. “password is wrong”). Positive example: “Username or password was incorrect.”.
8. Autocomplete for all fields on login dialogs SHOULD be deactivated by using the following statement `autocomplete="off"`.


[^1]: See NIST SP 800-63b, NIST Special Publication 800-63B Digital Identity Guideline, [Authenticator Assurance Levels](https://pages.nist.gov/800-63-3/sp800-63b.html#sec4)
