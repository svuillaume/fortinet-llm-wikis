---
title: RCA Diagram: read-only access from cloud to report (user-uploaded HTML)
path: chat upload d3ce761b-rca-diagram.html, 2026-10-15 (original location on disk not stated)
inline: true
topic: rapid-cloud-assessment
tags: [rca, architecture, diagram, data-path]
updated: 2026-10-15
size: 32959
sha1: 03339007dafc
status: current
---

**Source:** self-contained HTML page (32,959 bytes, title "RCA Diagram", heading "FortiCNAPP Rapid Cloud Assessment") uploaded in chat and ingested with `llm-wiki-ingest`. Text extracted (about 1,160 characters); the diagram graphics and 1 embedded PNG were not read.

## Content
"How it works: read-only access, from cloud to report. The RCA reads findings from your FortiCNAPP tenant with a read-only API key. It never receives cloud credentials."

Flow: customer cloud in scope (AWS accounts, Azure subscriptions, GCP projects, workloads via agent or agentless scanning) -> READ-ONLY -> FortiCNAPP tenant (alerts, vulnerabilities, misconfigurations, identity risk, secrets) -> read-only API key -> RCA instance (private per customer; window 7 or 14 days; correlates four categories; builds score and report; expires 48 h, extend +48h) -> outputs at rca.fabriclab.ca (Risk Score and Maturity level, Security Report in 4 styles, correlated findings in 4 categories, optional sanitized copy). ONE-TIME: admin-level access to integrate, only if FortiCNAPP is not yet installed (AWS administrator; Azure Global Administrator + Owner; GCP Owner or Organization Administrator), never used for scanning. Secret handling: the API key secret is entered only in the New assessment form.

The same diagram appears in `user-upload-rca-scoping-checklist-documentation-2026-10-15` and `user-upload-rca-guided-setup-2026-10-15`.

## Related wiki pages

- [[rapid-cloud-assessment]]
