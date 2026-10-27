---
title: Introduction and Cloud Security Features
summary: Overview of the legacy FortiCASB platform (Admin Guide 24.4.b) and its visibility, data security, threat protection and compliance features.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Introduction and Cloud Security Features

**Scope note:** this guide (FortiCASB 24.4.b Admin Guide, dated Dec 30 2024) describes the LEGACY FortiCASB platform. For the legacy vs FortiCASB-SSPM naming see [naming and rebrand](../product/naming-and-rebrand.md). Screenshots were not extracted.

## Overview
FortiCASB is Fortinet's cloud-native Cloud Access Security Broker (CASB) service providing visibility, compliance, data security, and threat protection for cloud-based services. It uses direct API access for deep inspection and policy management of data stored in cloud application platforms, and provides user analytics and management tools. [src: forticasb-admin-guide-24-4-b, p.18]

## Four pillars
- **Visibility**: data scans and analytics answer who accessed information, what, when, and from where.
- **Compliance**: file content monitoring finds and reports regulated data in the cloud.
- **Data security**: scans for sensitive data (e.g. social security or credit card numbers), classifies it by sensitivity level, and alerts according to the sensitivity of the data accessed.
- **Threat protection**: User Entity Behavior Analytics watches for suspicious or irregular behavior; alerts on malicious behavior.

[src: forticasb-admin-guide-24-4-b, p.18]

## Features
### Visibility
- Automatic on-demand data scan: examines existing content in all folders to identify sensitive data subjects or security policies.
- Cloud usage analytics: key usage statistics, trends over time periods, drilldown, access count, usage over time.
- User entitlements review: privileged, dormant, and external users.
- File exposure: most shared files overall and per user.

[src: forticasb-admin-guide-24-4-b, p.18]

### Data security and threat protection
- Cloud data loss prevention: DLP policies based on data identifiers, keywords, and regular expressions for data at rest.
- Threat detection: out-of-the-box policies for account-centric threats.
- Malware detection: policy to detect malicious files.
- Geo-location analytics: global access patterns; flags unlikely cross-region access attempts.
- Shadow IT discovery: overview of unsanctioned cloud applications and control of application usage.
- Configuration assessment: out-of-the-box policies validating best security practices against the cloud storage account.

[src: forticasb-admin-guide-24-4-b, p.19]

### Compliance
- Predefined compliance policies for ISO 270001 (as printed), NIST 800-53 V4, and NIST 800-171.
- Compliance reports for audit purposes covering the same standards.

[src: forticasb-admin-guide-24-4-b, p.19]

## Related
- [Licensing](licensing.md)
- [Supported apps and scan scope](supported-apps-and-scan-scope.md)
- [Company and first-time setup](company-and-first-time-setup.md)
- [Release notes](release-notes.md)
- [FortiCASB naming and rebrand](../product/naming-and-rebrand.md)
