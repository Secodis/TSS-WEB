# {{site.TITLE_IMPL_AUTHZ}}

Are standard components used for authenticating users (policy decision point) or retrieving user roles and permissions (policy information point)? Then they should be described here.

1. Every sensitive object access (e.g. access to a sensitive object within the database) MUST be authorized on the server-side (complete mediation).
2. Access controls SHOULD be applied on different layers if possible (e.g. URL, file, method and object layer) or via an indirection layer to reduce the risk of insecure object references.
3. Access controls MUST not only verify if the requesting entity has all required roles for specific access but also if this particular entity has the required permission to access a specific data object.
4. Every process and role SHOULD be implemented as restrictive as possible according to its particular business requirement.
5. For technical APIs access see requirements at [{{site.TITLE_IMPL_APISEC}}]({{site.URL_IMPL_APISEC}}).
