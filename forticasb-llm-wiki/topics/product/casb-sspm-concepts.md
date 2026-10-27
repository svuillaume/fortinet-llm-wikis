---
title: CASB, SSPM, SSDR, SASE and CNAPP: how the categories relate
summary: Definitions and scope boundaries used in the FortiCASB enablement material, including the SSPM vs CASB vs CSPM comparison.
sources: [deck-techtalk-forticasb-sspm-v1-1, deck-saas-security-sspm-final, deck-tdm-presentation-casb]
updated: 2026-10-26
status: current
---

# CASB, SSPM, SSDR, SASE and CNAPP: how the categories relate

## Definitions as used in the decks
- **CASB** (Cloud Access Security Broker): sits between users and cloud applications to enforce security policies and protect data. Functions listed: monitor cloud app usage (shadow IT detection), enforce access control, DLP for cloud files, detect risky behavior and insider threats, encrypt/protect sensitive data. API CASB covers data at rest; inline CASB (in a SASE architecture) covers data in motion. `[src: deck-techtalk-forticasb-sspm-v1-1, slides 10, 13 notes]`
- **SSPM** (SaaS Security Posture Management): ensures SaaS apps are configured securely according to best practices and compliance frameworks. Functions: SaaS application discovery, audit of SaaS configuration (sharing, permissions, MFA), detection of misconfigurations (over-permissioned users, public data), remediation recommendations, compliance reports (SOC 2, HIPAA, GDPR). In the TechTalk deck's speaker notes, "SSPM is API CASB". `[src: deck-techtalk-forticasb-sspm-v1-1, slide 12]`
- **SSDR** (SaaS Security Detection and Response): detects abnormal and suspicious actions within SaaS services and suggests a plan. SSPM + SSDR "continuously assesses security risk and manages SaaS application security posture". `[src: deck-saas-security-sspm-final, slide 13]`

## SSPM core components (SSPM deck)
Continuous monitoring (misconfigurations, shadow SaaS, identity exposures), risk and compliance assessment (benchmarks such as CIS controls, HIPAA, GDPR, PCI, MITRE ATT&CK), policy enforcement, automated remediation (configuration correction, permission revocation, user access control, vulnerability mitigation). Typical detections: public file sharing, inactive accounts, shadow IT, missing MFA and weak password policy. `[src: deck-saas-security-sspm-final, slides 15-32]`

## How SSPM fits with SASE and CNAPP

| Capability | Fortinet product / feature | SASE? | Role |
|---|---|---|---|
| Cloud access control (inline CASB) and identity-centric access | FortiSASE | Yes | Identity-based access; central Zero Trust enforcement |
| SaaS posture and data protection | FortiCASB (API CASB) | Yes (via SASE) | Visibility, compliance, data protection |
| SaaS posture management | FortiCASB-SSPM | No | SaaS visibility and secure configuration |
| Infrastructure posture | CSPM via FortiCNAPP | No | Cloud misconfiguration tracking |
| Workload protection | FortiCNAPP (CWPP/runtime) | No | Protects apps/infrastructure |

The deck's summary line: "SSPM doesn't replace CASB or CSPM; it complements them." `[src: deck-saas-security-sspm-final, slides 43-45]`

## Scope comparison (SSPM vs SASE/CASB vs CSPM)

| | SSPM | SASE / CASB | CSPM |
|---|---|---|---|
| Focus | SaaS applications (Microsoft 365, Salesforce, Okta) | Cloud access and data flows (SaaS, IaaS, PaaS) | Cloud infrastructure (AWS, Azure, GCP) |
| Primary function | Continuous monitoring of configurations, permissions, compliance | Enforcing security policies between hybrid users and cloud services | Infrastructure configuration checks |
| Typical features | Centralized visibility, workflow remediation, identity-centric risk, risk drift | DLP, shadow IT discovery, UTM and threat detection | Infrastructure misconfiguration detection, compliance mapping, storage bucket security |

`[src: deck-saas-security-sspm-final, slide 45]`

## Related
- [Inline vs API CASB](inline-vs-api-casb.md)
- [Product overview](overview-and-use-cases.md)
- [SaaS OAuth attack-path example](saas-oauth-attack-path-example.md)
