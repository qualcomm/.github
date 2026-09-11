# Qualcomm Open Source Security Policy

## 1. Purpose

Qualcomm is committed to supporting secure development and responsible vulnerability handling for Qualcomm-managed open source projects. This policy describes Qualcomm's approach to vulnerability reporting, assessment, remediation, disclosure, and related security practices.

## 2. Scope

This policy applies to Qualcomm-managed open source repositories and software components that Qualcomm maintains, contributes to, distributes, or otherwise supports through its open source development activities. Project-specific guidance may supplement this policy through `SECURITY.md` files, `CONTRIBUTING.md` files, project documentation, security advisories, and related repository resources.

## 3. Security Principles

* Coordinated Vulnerability Disclosure
* Secure Development
* Defense in Depth
* Risk-Based Prioritization
* Transparency and Responsible Disclosure
* Regulatory and Industry Alignment

## 4. Reporting Security Vulnerabilities

Security researchers and contributors should follow the vulnerability reporting instructions provided in the applicable repository `SECURITY.md` file or other Qualcomm-designated security reporting channels. Vulnerabilities should not be reported through public issues, pull requests, discussions, or other public forums unless explicitly directed otherwise.

Reports should include relevant technical information such as affected component, version, impact, reproduction steps, proof-of-concept details where available, and any known exploitability information.

## 5. Vulnerability Handling Lifecycle

Qualcomm generally follows a coordinated vulnerability handling lifecycle:

* Report or Detection
* Triage
* Risk Assessment
* Remediation
* Validation
* Disclosure

### Remediation Objectives

Qualcomm strives to address applicable security vulnerabilities in a timely and risk-based manner. When regulatory or legal requirements impose stricter timelines, including cybersecurity reporting or remediation expectations under applicable regulations such as the EU Cyber Resilience Act, those requirements take precedence.

| Vulnerability Category | Target Objective |
| --- | --- |
| Actively exploited or elevated-risk vulnerabilities | Expedited assessment and remediation as soon as practicable, or as required by applicable regulatory timelines. |
| Critical vulnerabilities | Target remediation within approximately 21 calendar days where feasible |
| High-severity vulnerabilities | Target remediation within approximately 21 calendar days where feasible |
| Moderate and low-severity vulnerabilities | Risk-based remediation based on impact and applicability |

Contributors, maintainers, and other project participants are encouraged to support these remediation objectives and to prioritize applicable security issues accordingly. These objectives are guidance rather than guarantees and may vary based on technical complexity, validation requirements, upstream dependencies, availability of mitigations, and other relevant factors.

## 6. Security Practices

Qualcomm-managed open source projects may employ security practices appropriate to the project type and risk profile, including:

* Automated security analysis
* Dependency and vulnerability monitoring
* CI/CD security safeguards
* Release integrity controls
* Software supply chain security practices
* Repository and access management controls

All identified issues and vulnerabilities that affect a proposed contribution must be addressed before the contribution is accepted into the project.

## 7. Security Compliance Alignment

Qualcomm continuously evaluates and enhances its open source security practices to align with applicable security compliance and industry best practices relevant to Qualcomm products, services, and open source development activities.

## 8. Additional Information

Additional security information is available through repository `SECURITY.md` files, `CONTRIBUTING.md` files, project documentation, security advisories, and other Qualcomm security resources.
