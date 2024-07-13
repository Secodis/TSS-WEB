# 11. Protection of Secrets

The following requirements are relevant for technical secrets (e.g. passwords of technical users, API keys, credentials or private keys) used either in production or that are generally used to protect access to sensitive systems or data:

1. Secrets MUST be encrypted when stored with the source code (otherwise they need to be separated from it)
2. Access to secrets MUST be restricted.
3. For assurance class >= [HIGH]
    - Secrets MUST be stored in a secure secret store (vault) or keystore)
    - Secrets MUST be stored encrypted
    - Secrets SHOULD be rotated at least one per year.
