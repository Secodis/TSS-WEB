# B.11 - Protection of Secrets

The following requirements are relevant for technical secrets (e.g. passwords of technical users, API keys, credentials or private keys) used either in production or that are generally used to protect access to sensitive systems or data:

1. Secrets MUST be encrypted when stored with the source code (otherwise they need to be stored separately)
2. Access to secrets and their encryption keys MUST be restricted.
3. Secrets SHOULD have a label indicating the application or service and responsible team they belong to.
4. For ***assurance class >= [HIGH]***:
    - Secrets MUST be stored in a secure secret store (vault) or protected keystore
    - Secrets MUST be stored encrypted
    - Secrets SHOULD be rotated at least once per year
