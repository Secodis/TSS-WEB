---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---

# NIST SSDF Mapping 

TSS-WEB covers most controls of [NIST SSDF v1.1](https://csrc.nist.gov/Projects/ssdf), except those that either do not relate to a security requirement or are too specific for a baseline requirement. 

Additionally, the general scope of SSDF is slightly different since it addresses security requirements for suppliers of public US institutions, which can be more strict than what most companies can demand from their suppliers.

Therefore, from a customer perspective, the respective requirements in TSS-WEB (see [{{site.TITLE_SSDLC_OUTDEV}}]({{site.URL_SSDLC_OUTDEV}})) are a little less strict since they aim to provide a set of security requirements that should be commonly acceptable by software suppliers in general.

## Prepare the Organization (PO)

### Define Security Requirements for Software Development (PO.1)

This is what should be archived by applying TSS-WEB in general.

### Implement Roles and Responsibilities (PO.2)

See [{{site.TITLE_SSDLC_SECDEV_ROLES}}]({{site.URL_SSDLC_SECDEV_ROLES}}).

### Implement Supporting Toolchains (PO.3)

Covered from a requirement perspective mostly at [{{site.TITLE_SSDLC_SECDEV_BUILD}}]({{site.URL_SSDLC_SECDEV_BUILD}}). However, this SSDF requirements also focussed on the general process of selecting and implementing the right tooling which is not covered by TSS-WEB.

### Define and Use Criteria for Software Security Checks (PO.4)

Covered from a requirement perspective mostly at [{{site.TITLE_SSDLC_SECDEV_BUILD}}]({{site.URL_SSDLC_SECDEV_BUILD}}) as wel as [{{site.TITLE_SSDLC_SECDEV_3RDPARTY}}]({{site.URL_SSDLC_SECDEV_3RDPARTY}}).

### Implement and Maintain Secure Environments for Software Development (PO.5)

See [{{site.TITLE_SSDLC_SECENV}}]({{site.URL_SSDLC_SECENV}}).

## Protect the Software (PS)

### Protect All Forms of Code from Unauthorized Access and Tampering (PS.1)

Covered by various requirements, including:

* [{{site.TITLE_SSDLC_SECENV_ACCESS}}]({{site.URL_SSDLC_SECENV_ACCESS}})
* [{{site.TITLE_SSDLC_SECENV_CODEPROTECT}}]({{site.URL_SSDLC_SECENV_CODEPROTECT}})
* [{{site.TITLE_SSDLC_SECOP_SEPERATION}}]({{site.URL_SSDLC_SECOPP_SEPERATION}})
* [{{site.TITLE_SSDLC_SECOP_SECBACKEND}}]({{site.URL_SSDLC_SECOPP_SECBACKEND}})
* [{{site.TITLE_SSDLC_SECOP_ADMINACCESS}}]({{site.URL_SSDLC_SECOPP_ADMINACCESS}})

### Provide a Mechanism for Verifying Software Release Integrity (PS.2)

Code signature verification is required in release process (see [{{site.TITLE_SSDLC_SECDEV_BUILD}}]({{site.URL_SSDLC_SECDEV_BUILD}})).

Also, provisioning of code signing certificates Integrate code signing is a supplier requirement (see [{{site.TITLE_SSDLC_OUTDEV}}]({{site.URL_SSDLC_OUTDEV}})). 

### Archive and Protect Each Software Release (PS.3)

See requirements at [{{site.TITLE_SSDLC_SECDEV_BUILD}}]({{site.URL_SSDLC_SECDEV_BUILD}}).

Also covered from a customer perspective at [{{site.TITLE_SSDLC_OUTDEV}}]({{site.URL_SSDLC_OUTDEV}}).

## Produce Well-Secured Software (PW)

### Design Software to Meet Security Requirements and Mitigate Security Risks (PW.1)

Covered by [{{site.TITLE_SSDLC_SECDEV_SECDESIGN}}]({{site.URL_SSDLC_SECDEV_SECDESIGN}}).

### Review the Software Design to Verify Compliance with Security Requirements and Risk Information (PW.2)

Covered by [{{site.TITLE_SSDLC_SECDEV_SECDESIGN}}]({{site.URL_SSDLC_SECDEV_SECDESIGN}}) and [{{site.TITLE_SSDLC_SECDEV_SECGATES}}]({{site.URL_SSDLC_SECDEV_SECGATES}}).

### Reuse Existing, Well-Secured Software When Feasible Instead of Duplicating Functionality (PW.4)

Not covered directly at the moment. This would be usually be enforced in an architecture board that approves new architecture decisions like new technologies (see [{{site.TITLE_SSDLC_SECDEV_SECGATES}}]({{site.URL_SSDLC_SECDEV_SECGATES}})).

### Create Source Code by Adhering to Secure Coding Practices (PW.5)

Covered technology agnostic by [{{site.TITLE_SSDLC_SECDEV_SECIMP}}]({{site.URL_SSDLC_SECDEV_SECIMP}}); especially be te implementation requirements. In a next step you could derive technology-specific secure coding guidelines from them (e.g. secure coding guidelines for Java EE, python, etc.).

### Configure the Compilation, Interpreter, and Build Processes to Improve Executable Security (PW.6)

Security aspects of the build process are covered by [{{site.TITLE_SSDLC_SECDEV_BUILD}}]({{site.URL_SSDLC_SECDEV_BUILD}}).

Since the scope of TSS-WEB are web-based applications and services, security of executables are not covered here though.

### Review and/or Analyze Human-Readable Code to Identify Vulnerabilities and Verify Compliance with Security Requirements (PW.7)

Peer reviews are required in [{{site.TITLE_SSDLC_SECDEV_SECIMP}}]({{site.URL_SSDLC_SECDEV_SECIMP}}).

### Test Executable Code to Identify Vulnerabilities and Verify Compliance with Security Requirements (PW.8)

Not covered by TSS-WEB since its scope are web-based applicaions and services.

### Configure Software to Have Secure Settings by Default (PW.9)

Covered by [{{site.TITLE_SSDLC_SECOP_HARDENING}}]({{site.URL_SSDLC_SECOP_HARDENING}}).

## Respond to Vulnerabilities (RV)

### Identify and Confirm Vulnerabilities on an Ongoing Basis (RV.1)

Covered by [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}}).

### Assess, Prioritize, and Remediate Vulnerabilities (RV.2)

* For vulnerabilities identified within the development process: [{{site.TITLE_SSDLC_SECDEV_VULMREM}}]({{site.URL_SSDLC_SECDEV_VULMREM}})
* For vulnerabilities identified in production: [{{site.TITLE_SSDLC_SECOP_VULNREMED}}]({{site.URL_SSDLC_SECOP_VULNREMED}}).
  
### Analyze Vulnerabilities to Identify Their Root Causes (RV.3)

Covered by [{{site.TITLE_SSDLC_SECOP_VULNREMED}}]({{site.URL_SSDLC_SECOP_VULNREMED}}).
