# B.11 - Protection of Secrets

The following requirements are relevant for technical secrets (e.g. passwords of technical users, API keys, credentials or private keys) used either in production or that are generally used to protect access to sensitive systems or data:

1. Secrets MUST be encrypted when stored with the source code (otherwise they need to be stored separately).
2. Access to secrets and their encryption keys MUST be restricted.
3. Own secrets MUST be automatically and securely generated according to [{{site.TITLE_IMPL_DATASEC_TOKENS}}]({{site.URL_IMPL_DATASEC_TOKENS}})) if possible.
4. Secrets SHOULD have a label (or other metadata) indicating the application or service and responsible team they belong to.
5. For *risk class >= [HIGH]*:
    - Secrets MUST be stored in a secure secret store (vault) or protected keystore
    - Secrets MUST be stored encrypted
    - Secrets SHOULD be rotated at least once per year
    - Developers or admins MUST not have direct access to the secret 
