---
title: RCA Guided Setup (user-uploaded HTML slide deck)
path: chat upload c196864b-rca-guided-setup.html, 2026-10-15 (original location on disk not stated)
inline: true
topic: rapid-cloud-assessment
tags: [rca, guided-setup, hosted-service, api-key, assessment-lifecycle, report-styles, maturity-score]
updated: 2026-10-15
size: 307707
sha1: 4fa0fbb74f96
status: current
---

**Source:** self-contained HTML slide deck (307,707 bytes, title "RCA Guided Setup", marked "Fortinet Internal") uploaded in chat and ingested with `llm-wiki-ingest`. Text extracted (about 8,300 characters). The 6 embedded images (2 PNG, 4 JPEG; assessments-list and report screenshots) were not extracted or read. The deck cites "FortiRCA pre-flight check" and "rca.fabriclab.ca assessment screens" as its sources.

## Part I - Prepare

- **A. Scope:** list every account, subscription or project with regions and owners; anything left off will not appear. Window **7 days** (standard, faster) or **14 days** (broader trend). Optional **sanitized copy** (hostnames, IPs, account IDs replaced by consistent fake values). Findings are correlated into **four categories**: high-permissive identities; internet-exposed resources with a critical vulnerability; critical alerts; secrets exposure.
- **Report styles:** Standard Technical (alerts, vulnerabilities, misconfigurations, identity risk, exposed secrets); Wider-Scope Beta (per-cloud risk scoring, exploit-path simulation, per-host attack diagrams); Executive Overview (condensed, chart-first); Narrative Beta (scope, methodology, findings, evidence, recommended actions).
- **B. Connect FortiCNAPP:** already installed -> only generate a key; not installed -> Option 1 CSP console guided setup from the FortiCNAPP integration wizard, or Option 2 IaC template (CloudFormation for AWS, ARM for Azure, Terraform for GCP) applied through the customer's pipeline. Elevated access is needed once; day-to-day access is read-only.
- **One-time access to integrate:** AWS administrative privileges on every account; Azure Global Administrator on the tenant directory plus Owner on every monitored subscription; Google Cloud Owner on the project, or Organization Administrator plus Logging Config Writer at organization level (billing must be enabled on the project used to provision FortiCNAPP resources); FortiCNAPP account with Administrator privileges. The deck says to **re-check this list against current integration guides** and to **confirm supported template types per cloud**.
- **C. Data path:** the RCA reads findings from the FortiCNAPP tenant with a read-only API key and "never receives cloud credentials". The API key secret is entered only in the New assessment form, not in a checklist or email.

## Part II - Run (48 h default lifetime)

1. In FortiCNAPP, **Settings > API Keys**: create a key under a read-only user or role; download the key file (Key ID and Secret). The deck asks to verify that key permissions follow the user or role rather than a per-key scope.
2. Open `https://rca.fabriclab.ca/` (lands on New assessment form). Fields: customer name; FortiCNAPP account (tenant address, e.g. tenant.lacework.net); Key ID and Secret; Sub-account only for multi-team organizations. Click **Create assessment**: stands up a private report instance for one customer.
3. Status **Starting** goes through six stages: Creating resources, Provisioning storage, Pulling image, Starting container, Waiting for health, Loading FortiCNAPP data. If stuck, re-check Key ID, Secret and tenant address.
4. When **Ready**, click **Open**; the report can take up to 20 s to populate. Row actions: Open, **+48h** (extend expiry), **Destroy** (remove when finished).
5. The report opens on the **Cloud Security Risk Score** gauge. Four maturity levels: Foundational, Managed, Advanced, Optimized. "The higher the score, the more mature the cloud security posture. Despite the name, it is a maturity score." Sample tenant shown: score 37, Managed.
6. Left panel **Generate Cloud Security Report**; form fields Requester, Company Logo, Specialist Conclusion (field meanings inferred from labels; the deck says to check them against the live form).

## FAQ in the deck
Secret goes only in the Secret field of the form; stuck on Starting -> re-check credentials and tenant address; empty report after Open -> wait up to 20 s; availability 48 h by default, extend with +48h.

## Related wiki pages

- [[rapid-cloud-assessment]]
