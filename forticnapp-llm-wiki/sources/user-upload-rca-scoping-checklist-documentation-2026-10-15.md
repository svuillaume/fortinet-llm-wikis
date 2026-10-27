---
title: RCA Scoping Checklist / RCA Documentation (user-uploaded HTML)
path: chat upload 7868923c-rca-documentation.html, 2026-10-15 (original location on disk not stated)
inline: true
topic: rapid-cloud-assessment
tags: [rca, scoping-checklist, hosted-service, read-only-api-key, rca-fabriclab-ca]
updated: 2026-10-15
size: 192113
sha1: a2fd57d59984
status: current
---

**Source:** self-contained HTML page (192,113 bytes, title "RCA Scoping Checklist", heading "RCA Documentation") uploaded in chat and ingested with `llm-wiki-ingest`. Text extracted (about 2,270 characters). The 6 embedded PNG images and the page's edit/move/font/save-HTML controls were not extracted. The page links to a 1-pager at https://tec.myfortinet.com/ask/decks/p/1-pagerca/ (not opened).

## Content

- **Purpose:** "Scope your cloud environment, connect read-only access and generate the Cloud Security Report, in two guided steps." Two entry cards: **Prepare for RCA** (scope, access, report options, contacts, Share) and **Start guided RCA setup** (create the assessment, open it, generate the report).
- **Flow shown:** customer cloud in scope (AWS accounts, Azure subscriptions, GCP projects, workloads with agent or agentless scanning) -> read-only -> FortiCNAPP tenant (alerts, vulnerabilities, misconfigurations, identity risk, secrets) -> read-only API key -> **RCA instance** (private per customer; window 7 or 14 days; correlates four categories; builds score and report; **expires 48 h, extend +48h**) -> outputs at `rca.fabriclab.ca`: Risk Score with Maturity level, Security Report in 4 styles, correlated findings in 4 categories, optional sanitized copy.
- **One-time admin access** (only if FortiCNAPP is not yet installed): AWS administrator; Azure Global Administrator + Owner; GCP Owner or Organization Administrator. "Never used for scanning." Ongoing access is read-only.
- **Hand-off:** share the account list, cloud connection (or confirmation it exists) and API access with the Cloud Specialist or CSE in SMART; "most assessments are ready within a few business days".
- **Saving answers:** answers are kept on the device and restored; Save as JSON, Download text summary, Clear answers. API key secrets are never collected or saved.
- Document label: "FortiCNAPP Rapid Cloud Assessment - Scoping Checklist, Companion to the Technical RCA Report".

## Related wiki pages

- [[rapid-cloud-assessment]]
