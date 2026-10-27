---
title: FortiCNAPP News and Release Announcements, Jul–Oct 2026 (user-uploaded compilation)
path: chat upload a78a1ab4-attachment.txt, 2026-10-15 (original location on disk not stated)
inline: true
topic: product-overview
tags: [release-notes, polygraph-v2, code-security, claude-code-plugin, vulnerability-assessment, llmjacking, threat-landscape, events]
updated: 2026-10-15
size: 7084
sha1: 4647b150c38d
status: current
---

**Source:** a user-compiled Markdown file dated 2026-10-15, uploaded in chat and ingested with `llm-wiki-ingest`. It covers FortiCNAPP release notes, blogs and events from about 15 Jul 2026 to 15 Oct 2026. The file states each item was read directly from Fortinet documentation, blog, events and newsroom pages; those pages were not re-opened during ingest.

## Items in the window

| # | Date | Type | Title | What it says |
|---|---|---|---|---|
| 1 | Jul 2026 | Release notes | July 2026 Platform Releases | Polygraph v2 graph-based anomaly alerts (a graph neural network maps identities, actions, resources and source IPs); click-to-filter alerts by category and sub-category; cloud account rollback and deployment history for integrations. All GA. |
| 2 | Aug 2026 | Release notes | August 2026 Platform Releases | Code Security plug-in for Claude Code (IaC and SCA scans from the CLI); unified Code Security CI/CD integrations (IaC, SCA, SAST and PR comments for GitHub, GitLab, Bitbucket and Azure DevOps; Atlantis and Jenkins support IaC only); redesigned Automated Configuration onboarding workflow; new FortiCNAPP.com customer portal; agentless dashboard; console navigation reorganized into Threat Center and Risk Center; docs: Integration Permissions Reference. All GA. |
| 3 | Sep 2026 | Release notes | September 2026 Platform Releases | Risk score adjustment when a FortiGate or other NGFW is detected inline; vulnerability assessment for Google Container-Optimized OS (agent 8.4.0+ and Agentless); Ubuntu 25.04 to 26.10 host vulnerability assessment (may cause a spike in findings after the first feed update); docs update on tag-based enforcement using EventBridge and Lambda (tag key corrected to `fcnappalert`). |
| 4 | Aug 26, 2026 | Event | Fortinet in Action: Technical Demo Series, FortiCNAPP | Guided demo on AWS, Azure, GCP and Kubernetes, including a live credential-compromise detection and response scenario and DevOps integration. |
| 5 | Sep 3, 2026 | Blog (FortiGuard Labs) | Someone Else Is Using Your AI | AWS LLMjacking incident: leaked admin IAM key, new IAM user, Bedrock subscription through Marketplace, then inference abuse. FortiCNAPP detections that fire: lacework-global-12, 13, 2037, 2038, 2906, 2907. Recommends Bedrock invocation logging and short-lived credentials. |
| 6 | Sep 23, 2026 | Blog (Industry Trends) | Cloud Intrusions Now Move at Machine Speed | 2026 Cloud-Native Threat Landscape Report, built on FortiCNAPP intelligence: 150M recon events, 2.3B brute-force attempts, 1.7B exploitation attempts; identity abuse is the dominant intrusion path; FortiDAST integrates with FortiCNAPP and FortiAppSec Cloud for GenAI app testing. |
| 7 | Nov 10, 2026 (upcoming) | Event | November FortiCNAPP Quarterly Webinar | 1:00 to 2:00 PM ET, live Q&A; presenters Adam Larson and Tareq Alkhatib; no agenda published. |

## Just outside the window (context only, per the source)

- Jun 10: Skills Scanning in FortiCNAPP Code Security (community blog)
- Jun 26: Shai Hulud CI/CD to Redshift breach, detected by FortiCNAPP (blog)
- May 12: Fortinet and NVIDIA enterprise AI integration (press release; full text not opened by the compiler)
- Apr 21: Google Cloud Partner of the Year for Workload Security (press release)
- Jan 27: Network, Data and Unified Risk Context press release

## Gaps and caveats stated by the source

- No FortiCNAPP press release in the window; the Sep 29 Gemini Enterprise blog does not mention FortiCNAPP and is excluded.
- No October 2026 release notes page published yet.
- Release notes carry month-level dates only.
- Two September release-notes URLs exist (`922189` with 2 items, `959740` with 4); the file uses `959740`.
- Blog search returned 34 results, only 2 in the window; "Load More" was not clicked.
- Fortinet Community and Tech Tips were not searched beyond the one post in the out-of-window list; more in-window posts may exist.
- Third-party coverage (SecurityBrief, ITBrief and similar) excluded.

Source URLs (docs.fortinet.com release-notes pages 163169, 499403, 959740; fortinet.com blog posts for items 5 and 6; events.fortinet.com pages for items 4 and 7) are listed in the original file.

## Related wiki pages

- [[product-overview]] — platform release timeline for Jul–Oct 2026
- [[code-security]] — Claude Code plug-in and unified CI/CD integrations (Aug 2026)
- [[cwpp]] — Polygraph v2, agentless dashboard, Container-Optimized OS and Ubuntu host vulnerability assessment
- [[integrations]] — Automated Configuration redesign, cloud account rollback, Integration Permissions Reference
- [[demos-blogs-field]] — demo series, LLMjacking and machine-speed blogs, November webinar
- Source stub `forticnapp-wiki-forticnapp-techtip-june2026-release-html` — the previous monthly release stubs (Apr, May, Jun 2026)
- Source stub `tmp-personal-project-new-wiki-llm-wiki-raw-forticnapp-release-notes-fc03a1-txt` — FortiCNAPP 26.3 release notes PDF (collected 2026-10-11)
- Source stub `tmp-personal-project-new-wiki-llm-wiki-wiki-threats-polygraph-v2-graph-neural-network-detection-md` — Polygraph v2 description

## Conflict / Note

No hard conflict with existing pages. Three items to reconcile later:
- The 26.3 release notes PDF stub may already contain the July to September items. Its text was not re-read, so overlap is unverified.
- The August navigation change (Threat Center and Risk Center) may make console paths quoted elsewhere in the wiki stale.
- The July "cloud account rollback and deployment history" and August "Automated Configuration" redesign may change the Automated Configuration description in `integrations` (all-or-nothing rollback, console path). Not reconciled.
