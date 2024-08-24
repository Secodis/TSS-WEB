---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true
---

# Mapping of SAFECode Practices for Secure Software Development (Draft)

[Fundamental Practices for Secure Software Development](https://safecode.org/wp-content/uploads/2018/03/SAFECode_Fundamental_Practices_for_Secure_Software_Development_March_2018.pdf)

## Application Security Control Definition

Covered as definition of application security architecture (see [{{site.TITLE_SSDLC_SECDEV_SECDESIGN}}]({{site.URL_SSDLC_SECDEV_SECDESIGN}})).

### Actively Manage Application Security Controls

Not covered that explicitely in the sense of a full Application Development Lifecycle Management (ADLM) as SAFEcode defines it yet.

- Definition of application security architecture (see [{{site.TITLE_SSDLC_SECDEV_SECDESIGN}}]({{site.URL_SSDLC_SECDEV_SECDESIGN}}))
- its approval in the architecture gate (see [{{site.TITLE_SSDLC_SECDEV_SECGATES}}]({{site.URL_SSDLC_SECDEV_SECGATES}}))
- Assess Security of New Features (see [{{site.TITLE_SSDLC_SECDEV_SECDESIGN}}]({{site.URL_SSDLC_SECDEV_SECDESIGN}}))

(TODO)

## Design

### Secure Design Principles

See [{{site.TITLE_IMPL_PRINCIPLES}}]({{site.URL_IMPL_PRINCIPLES}}).

### Threat Modeling

See [{{site.TITLE_SSDLC_SECDEV_SECDESIGN}}]({{site.URL_SSDLC_SECDEV_SECDESIGN}}).

### Develop an Encryption Strategy

Requriements are covered in [{{site.TITLE_IMPL_DATASEC}}]({{site.URL_IMPL_DATASEC}}). 

A full encryption strategy would be outside of the scope of TSS-WEB though.

### Standardize Identity and Access Management

Implicitly covered:

* As implementation requirements: [{{site.TITLE_IMPL_AUTHZ}}]({{site.URL_IMPL_AUTHZ}})
* As to use standardized technologies in general: [{{site.TITLE_SSDLC_SECDEV_SECDESIGN}}]({{site.URL_SSDLC_SECDEV_SECDESIGN}}).

### Establish Log Requirements and Audit Practices

* Log Requirements: [{{site.TITLE_IMPL_ERRORLOG}}]({{site.URL_IMPL_ERRORLOG}})
* Audit Practices: [{{site.TITLE_SSDLC_SECOP_MONITORING}}]({{site.URL_SSDLC_SECOP_MONITORING}})

## Secure Coding Practices 

### Establish Coding Standards and Conventions

Not covered.

TSS-WEB only coveres implementation requirements in [{{site.TITLE_IMPL_CONTROLS}}]({{site.URL_IMPL_CONTROLS}}).

### Use Safe Functions Only

Covered in [{{site.TITLE_SSDLC_SECDEV_SECDESIGN}}]({{site.URL_SSDLC_SECDEV_SECDESIGN}}).

### Use Code Analysis Tools to Find Security Issues Early

Covered in [{{site.TITLE_SSDLC_SECTESTS_SECSCANS}}]({{site.URL_SSDLC_SECTESTS_SECSCANS}}).

### Handle Data Safely

Covered in [{{site.TITLE_IMPL_DATASEC}}]({{site.URL_IMPL_DATASEC}}).

### Handle Errors

Covered in [{{site.TITLE_IMPL_ERRORLOG}}]({{site.URL_IMPL_ERRORLOG}}).

## Manage Security Risk Inherent in the Use of Third-party Components 

## Testing and Validation

Covered in [{{site.TITLE_SSDLC_SECTESTS}}]({{site.URL_SSDLC_SECTESTS}}).

### Automated Testing

Covered in [{{site.TITLE_SSDLC_SECTESTS_SECSCANS}}]({{site.URL_SSDLC_SECTESTS_SECSCANS}}).

### Manual Testing

Abuse case testing is covered in [{{site.TITLE_SSDLC_SECTESTS_CUSTOMTESTS}}]({{site.URL_SSDLC_SECTESTS_CUSTOMTESTS}}).

## Manage Security Findings

Covered in [{{site.TITLE_SSDLC_SECTESTS_DEFECTH}}]({{site.URL_SSDLC_SECTESTS_DEFECTH}}).

### Define Severity

Dfined in release gate [{{site.TITLE_SSDLC_SECDEV_SECGATES}}]({{site.URL_SSDLC_SECDEV_SECGATES}}).

### Risk Acceptance Process

Risk acceptance is references in [{{site.TITLE_SSDLC_SECTESTS_DEFECTH}}]({{site.URL_SSDLC_SECTESTS_DEFECTH}}) but not explicitely defined in TSS-WEB. This would have to be done outside of TSS-WEB.

## Vulnerability Response and Disclosure

### Define Internal and External Policies

Should be covered within a seperate vulnerability management standard / process.

### Define Roles and Responsibilities

Covered in [{{site.TITLE_GENERAL_ROLES}}]({{site.URL_GENERAL_ROLES}}).

### Ensure that Vulnerability Reporters Know Whom to Contact

Should be covered within a seperate vulnerability management standard / process.

### Manage Vulnerability Reporters

Should be covered within a seperate vulnerability management standard / process.

Should be covered within a seperate vulnerability management standard / process.

### Monitor and Manage Third-party Component Vulnerabilities

Covered in [{{site.TITLE_SSDLC_SECDEV_3RDPARTY}}]({{site.URL_SSDLC_SECDEV_3RDPARTY}}).

### Fix the Vulnerability

Covered in [{{site.TITLE_SSDLC_SECOP_VULNREMED}}]({{site.URL_SSDLC_SECOP_VULNREMED}}) and [{{site.TITLE_SSDLC_SECTESTS_DEFECTH}}]({{site.URL_SSDLC_SECTESTS_DEFECTH}}).

### Vulnerability Disclosure

TBD

### Secure Development Lifecycle Feedback

## Planning the Implementation and Deployment of Secure Development Practices

Covered in [{{site.TITLE_SSDLC_SECDEV_SECIMP}}]({{site.URL_SSDLC_SECDEV_SECIMP}}).

### Culture of the Organization

Not in scope.

### Expertise and Skill Level of the Organization

Not in scope.

### Product Development Model and Lifecycle

Covered in [{{site.TITLE_SSDLC_SECDEV}}]({{site.URL_SSDLC_SECDEV}}).

### Scope of Initial Deployment

Not in scope.

### Stakeholder Management and Communications

Not in scope.

### Compliance Measurement

Not in scope.

### SDL Process Health

Not in scope.

### Value Proposition

Not in scope.
