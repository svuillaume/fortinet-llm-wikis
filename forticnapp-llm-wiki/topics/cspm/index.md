---
title: Cspm
summary: Cloud Security Posture Management: policies, suppressions, config checks.
sources: [downloads-forticnapp-cspm-beyond-misconfiguration-md, downloads-forticnapp-cspm-beyond-misconfiguration-1-md, test-container-forticnapp-cspm-beyond-misconfiguration-md, tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-cspm-md, tmp-personal-project-new-wiki-blog-cspm-md, downloads-forticnapp-azure-cspm-terraform-md, downloads-forticnapp-azure-cspm-terraform-1-md, scriptsv2-0-lw-suppressions-migration-readme-md, forticnapp-wiki-blog-cspm-html]
updated: 2026-10-15
status: needs-review
---

# Cspm

Cloud Security Posture Management: policies, suppressions, config checks.

## Scope

This page indexes **9** source documents routed to this topic.

## Synthesized content

### What it is

FortiCNAPP CSPM continuously discovers cloud resources across AWS, Azure, GCP, and OCI and evaluates their configuration against a policy library and compliance frameworks [src: cspm][src: forticnapp-cspm-beyond-misconfiguration]. It "deploys in minutes, with or without agents" and ships pre-built frameworks for SOC 2, ISO 27001, HIPAA, HITRUST, PCI, NIST, FISMA, PII, and CIS Benchmarks [src: forticnapp-cspm-beyond-misconfiguration][src: blog-cspm]. Posture is not a static rule engine — the Polygraph Data Platform learns environment baselines and flags deviations [src: blog-cspm][src: forticnapp-cspm-beyond-misconfiguration].

Fortinet positions CSPM as the second layer of a five-layer stack — Inventory → CSPM → CIEM → Exposure → Vulnerabilities — correlated by Attack Path Analysis so misconfiguration findings carry reachability, identity, and exploitability context rather than being surfaced as isolated signals [src: blog-cspm][src: forticnapp-cspm-beyond-misconfiguration].

### How it works

- **Resource Inventory** gives multi-cloud visibility with no result limit; every resource rolls up its vulnerability, misconfiguration, alert, and attack-path counts [src: blog-cspm][src: forticnapp-cspm-beyond-misconfiguration].
- **Configuration History** takes regular snapshots; the console exposes side-by-side diffs between any two snapshots [src: blog-cspm][src: forticnapp-cspm-beyond-misconfiguration].
- **Who/when attribution** comes from first-class integrations with AWS CloudTrail, Azure Activity Log, and Google Cloud Audit Log, so a misconfiguration pivots to the IAM principal, source IP, and API call that caused it [src: blog-cspm][src: forticnapp-cspm-beyond-misconfiguration].
- **Daily configuration audit** runs continuously and alerts on concerning changes; reports export to PDF/CSV and route to Jira/Slack for remediation [src: cspm][src: forticnapp-cspm-beyond-misconfiguration].
- **Network-aware scoring** factors firewall protection along internet-accessible paths into the finding's score, feeding the Exposure Polygraph and overall Risk Score [src: cspm][src: blog-cspm].
- **KSPM** extends the same model to Kubernetes with CIS Kubernetes and managed-service benchmarks [src: cspm].

### Policies, exceptions, and suppressions

Policies evaluate resource configuration against a baseline (e.g. `lacework-global-141` for an IAM check mapped from the legacy `LW_AWS_IAM_13`) [src: README]. Legacy **Suppressions (v1)** have been superseded by **Policy Exceptions (v2)**; the AWS CIS 1.1 rule set was replaced by CIS 1.4 policies, and legacy-to-current rule mappings are documented in the FortiCNAPP docs [src: README].

Policy Exceptions are created via the API `POST /Exceptions?policyId=<policyId>` with a description and a `constraints` array. Supported constraint fields vary per policy and include `accountIds`, `regionNames`, `resourceNames`, and `resourceTags` [src: README]. Not every legacy constraint maps cleanly — e.g. `lacework-global-41` rejects `regionNames` — so migrations must be reviewed against each policy's accepted constraint set before applying [src: README]. Running the migration helper twice creates duplicate exceptions [src: README].

### Configuration in practice

CSPM needs a read-only identity per cloud: AWS cross-account role, Azure service principal with Reader, GCP service account with viewer roles [src: cspm]. Fortinet publishes Terraform modules at `github.com/lacework/*` to create these [src: cspm][src: forticnapp-azure-cspm-terraform].

For Azure CSPM-only, use two pinned modules [src: forticnapp-azure-cspm-terraform]:

- `lacework/ad-application/azure` v2.0.1 — app registration, service principal, client secret, optional Directory Reader (`enable_directory_reader`, default `true`).
- `lacework/config/azure` v3.0.3 — assigns **Reader** + **Key Vault Reader** at subscription(s) or management group and registers `lacework_integration_azure_cfg`.

Scope is controlled by `all_subscriptions = true`, an explicit `subscription_ids` list, or `use_management_group = true` with `management_group_id` [src: forticnapp-azure-cspm-terraform]. A one-command alternative generates and applies the same modules: `lacework generate cloud-account azure --configuration --all_subscriptions --apply` [src: forticnapp-azure-cspm-terraform]. The deployer needs Azure Owner or User Access Administrator on the target scope, and Entra ID app-registration rights (plus Privileged Role Administrator if Directory Reader is enabled) [src: forticnapp-azure-cspm-terraform].

Caveats: without Directory Reader, Entra LQL datasources and IAM compliance policies are not assessed; Key Vault policies return "Could Not Assess" if Key Vault Reader is missing or vaults use access policies without List/List permissions [src: forticnapp-azure-cspm-terraform]. Activity log ingestion and agentless workload scanning are separate modules (`activity-log/azure`, `agentless-scanning/azure`) added on top of the CSPM baseline [src: forticnapp-azure-cspm-terraform].

## Sources

- [Beyond Misconfiguration: Why Modern CSPM Needs Inventory, CIEM, Exposure, Vulnerabilities — and the Auto-Correlation Tha](../../sources/downloads-forticnapp-cspm-beyond-misconfiguration-md.md) — `/Users/svuillaume/Downloads/forticnapp-cspm-beyond-misconfiguration.md`
- [Beyond Misconfiguration: Why Modern CSPM Needs Inventory, CIEM, Exposure, Vulnerabilities — and the Auto-Correlation Tha](../../sources/downloads-forticnapp-cspm-beyond-misconfiguration-1-md.md) — `/Users/svuillaume/Downloads/forticnapp-cspm-beyond-misconfiguration_1.md`
- [Beyond Misconfiguration: Why Modern CSPM Needs Inventory, CIEM, Exposure, Vulnerabilities — and the Auto-Correlation Tha](../../sources/test-container-forticnapp-cspm-beyond-misconfiguration-md.md) — `/Users/svuillaume/test_container/forticnapp-cspm-beyond-misconfiguration.md`
- [CSPM (Cloud Security Posture Management)](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-cspm-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/cloud-security/cspm.md`
- [FortiCNAPP - Risk Based Prioritized CSPM](../../sources/tmp-personal-project-new-wiki-blog-cspm-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/blog-cspm.md`
- [FortiCNAPP → Azure CSPM (Configuration integration) — Terraform](../../sources/downloads-forticnapp-azure-cspm-terraform-md.md) — `/Users/svuillaume/Downloads/forticnapp-azure-cspm-terraform.md`
- [FortiCNAPP → Azure CSPM (Configuration integration) — Terraform](../../sources/downloads-forticnapp-azure-cspm-terraform-1-md.md) — `/Users/svuillaume/Downloads/forticnapp-azure-cspm-terraform_1.md`
- [Suppressions (v1) to Policy Exceptions (v2) Migration Helper for Lacework CSPM Policies](../../sources/scriptsv2-0-lw-suppressions-migration-readme-md.md) — `/Users/svuillaume/scriptsv2.0/lw-suppressions-migration/README.md`
- [FortiCNAPP - Risk Based Prioritized CSPM — Fortinet Blog](../../sources/forticnapp-wiki-blog-cspm-html.md) — `/Users/svuillaume/forticnapp-wiki/blog-cspm.html`

## Synthesized catalog

| Document | Summary | Source |
|---|---|---|
| [FortiCNAPP - Risk Based Prioritized CSPM — Fortinet Blog](../../sources/forticnapp-wiki-blog-cspm-html.md) | **Summary:** Let's have a deeper look at Cloud Security Posture Management | `/Users/svuillaume/forticnapp-wiki/blog-cspm.html` |
