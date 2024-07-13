# 2. Remediation of Vulnerabilities in Production

Identified vulnerabilities in applications MUST generally be remediated quickly and causative. In case root case remediation should require a significant amount of time and the risk posed by the vulnerability is also significant, temporary measures (e.g. workarounds) SHOULD be implemented to reduce the exploitability as soon as possible until the actual root cause is fixed. Such remediation MUST always be considered as a temporary measure.

In respect of external (e.g. Internet-facing) applications, the following requirements define the point of time until a vulnerability MUST be corrected, or its exploitability prevented latest:

|| **Critical Vulnerability** | **High Vulnerability**  | **Moderate Vulnerability**  |
| ------------- | ------------- | ------------- | ------------- |
| **Critical Application** | At the end of the **next working day**|  Within **7 days**  | Within the next release, but after **6 months** at the latest. |
| **Non-Critical Application** | Within **7 days**  | Within **21 days**  | - |

In respect of internal applications, the following requirements define the point of time until a vulnerability MUST be remediated if possible or at least its exploitability prevented:

| | **Critical Vulnerability**  | **High Vulnerability** | **Moderate Vulnerability** |
| -------------| ------------- | ------------- | ------------- |
| **Critical Application** | Within **7 days**  | Within **30 days**  | Within the next release, but after **12 months** at the latest. |
| **Non-Critical Application**| Within **21 days**  | Within **60 days**  | - |