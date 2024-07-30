<title>{{site.TITLE_IMPL_PRINCIPLES}}</title>

# {{site.TITLE_IMPL_PRINCIPLES}}

| # | Principle | Explanation |
| ------------- | ------------- | ------------- |
| 1 | Minimize Attack Surface | Interfaces, functionality, parameters, services, and protocols that are not required MUST be disabled on external and SHOULD be disabled on internal systems. |
| 2 | Don’t Trust User Input | Data that has been received from an untrusted source (e.g. a web browser) MUST generally be mistrusted and therefore strongly validated. |
| 3 | Defense-in-Depth | Security SHOULD be implemented based on multiple layers to compensate for ineffective security controls. |
| 4 | Keep Security Settings Adaptable | Security parameterization SHOULD be declarative where possible (= with configuration statements or annotations) instead of programmable (= with program code) where possible. |
| 5 | Externalize Security Functions | Security functions SHOULD be externalized (e.g. using an external authentication system) |
| 5 | Least Pricilege | Every program and user SHOULD operate using the least set of privileges necessary. |
| 6 | Keep Security Consistant | Identical security controls (e.g. one within the frontend and another within an REST interface) SHOULD be implemented with the same security function (= program code) and policy. |
| 7 | Use Mature Security Controls | Security relevant program code SHOULD only be implemented with mature and tested technologies, algorithms and implementations (APIs, frameworks etc.).  |
| 8 | Keep Security Testable | Before a new technology (protocol, framework, API, etc.) is being used in production, it SHOULD be ensured that proper testing procedures and tools exist for performing security tests on them. |
| 9 | Use Fail-Safe Defaults | Use secure / safe defaults (e.g. in frameworks) to prevent unintentional security problems.  |
