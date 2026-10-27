---
title: Skills
summary: Claude skills related to FortiCNAPP (what each does, how to invoke).
sources: [skill-forticnapp, skill-forticnapp-integration, skill-forticnapp-azure-integration, skill-forticnapp-terraform, skill-forticnapp-lql-agent, tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-skill-md, tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-cloud-security-md, tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-detection-engineering-md, tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-operations-md, tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-updates-md, tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-vendors-md, claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-references-aws-md, tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-references-aws-md, claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-references-azure-md, tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-references-azure-md, downloads-cnapp-skill-skill-md, tmp-personal-project-newsletter-cnapp-skills-skill-md, claude-skills-engineering-blog-skill-md, downloads-forticnapp-terraform-skill-md, claude-skills-forticnapp-references-azure-permissions-md, claude-skills-forticnapp-references-azure-terraform-md, claude-skills-forticnapp-references-azure-troubleshooting-md, downloads-forticnapp-azure-onboarding-agent-skill-md, tmp-personal-project-new-wiki-cnapp-aiassist-integration-forticnapp-azure-onboarding-agent-skill-md, claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-skill-md, tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-skill-md, tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-index-md, claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-index-md, tmp-personal-project-forticnapp-inventory-claude-skills-forticnapp-exposure-report-skill-md, tmp-personal-project-forticnapp-aiagent-plugin-skills-lql-agent-skill-md, claude-skills-forticnapp-mcp-tools-skill-md, tmp-personal-project-mcp-forticnapp-claude-skills-forticnapp-mcp-tools-skill-md, claude-skills-forticnapp-skill-md, documents-claude-projects-forticnapp-azure-onboarding-skill-md, tmp-personal-project-forticnapp-inventory-claude-skills-forticnapp-inventory-skill-md, tmp-personal-project-forticnapp-inventory-claude-skills-forticnapp-inventory-catalog-attack-paths-md, claude-plugins-cache-fortinet-plugins-code-security-1-7-1-skills-fortinet-code-review-skill-md, claude-plugins-marketplaces-fortinet-plugins-plugins-code-security-skills-fortinet-code-review-skill-md, claude-plugins-cache-fortinet-plugins-code-security-1-7-1-skills-fortinet-settings-skill-md, claude-plugins-marketplaces-fortinet-plugins-plugins-code-security-skills-fortinet-settings-skill-md, claude-plugins-cache-fortinet-plugins-code-security-1-7-1-skills-fortinet-cli-setup-skill-md, claude-plugins-marketplaces-fortinet-plugins-plugins-code-security-skills-fortinet-cli-setup-skill-md, tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-references-gcp-md, claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-references-gcp-md, tmp-personal-project-forticnapp-aiagent-plugin-skills-lql-agent-references-lql-rules-md, claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-references-oci-md, tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-references-oci-md, tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-contribute-catalogs-md, claude-skills-forticnapp-references-session1-cnapp-md, claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-skill-yaml, documents-claude-scheduled-cnapp-market-intel-biweekly-skill-md, tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-skill-yaml, documents-claude-scheduled-fortiai-and-cloud-security-bites-skill-md, documents-claude-scheduled-casb-sspm-newsletter-skill-md, tmp-personal-project-new-wiki-skill-md]
updated: 2026-10-14
status: needs-review
---

# Skills

Claude skills related to FortiCNAPP (what each does, how to invoke).

## Scope

This page indexes **56** source documents routed to this topic.

## Overview

The FortiCNAPP skill ecosystem on this laptop clusters into six functional
groups, each triggered by a different kind of request.

**Master reference.** The `forticnapp` skill is the single entry point for
anything FortiCNAPP or FortiCASB-SSPM — "cloud integrations (Azure, AWS, GCP),
CSPM/CWPP/CIEM/DSPM, CLI, Terraform, troubleshooting, activity logs, agentless
workload scanning" as well as field work and content creation, all mode-switched
automatically from the request [src: forticnapp]. It carries the full Azure
onboarding runbook, LQL syntax rules (`sec_to_timestamp` for time arithmetic,
`RESOURCE_CONFIG:field` aliasing on `LW_CFG_*` sources, the `RLIKE`-on-region
trap that silently returns zero rows), and the Fortinet "Shift Left, Shield
Right" session framework [src: forticnapp]. Reach for it first on any
FortiCNAPP question before pulling in a narrower skill.

**MCP and LQL agents.** `forticnapp-mcp-tools` is the thin but critical
companion loaded "when calling any `mcp__forticnapp__*` tool"; it covers
deferred-schema loading via `ToolSearch`, the real filter-expression enum
(`eq, ne, in, not_in, like, ilike, rlike, gt, ge, lt, le, between` — negation
is `ne`, never `not_eq`), the `resourceType` vs `dataset` trap on
`Inventory/search`, and the auto-chunked `next_page_url` pagination used when a
response would exceed byte limits [src: forticnapp-mcp-tools]. The
`forticnapp-lql-agent:lql-agent` sub-agent turns a natural-language security
question into "a validated, executed, scored LQL query" by iterating against
the `forticnapp-lql` MCP server — it is the only agent granted the LQL tools.

**Integration and onboarding.** `forticnapp-cloud-integration:forticnapp-integration`
guides users through AWS, Azure, GCP, and OCI integrations, choosing between
Guided Configuration and Terraform. The `forticnapp-azure-onboarding-agent` is
a conversational chatbot that walks a user from "I want FortiCNAPP to monitor
my Azure tenant" to a verified Cloud Account — enforcing read-before-write,
keeping client secrets out of the chat (Key Vault only), and gating on
preflight PASS before any App Registration, SP, RBAC assignment, or
CloudAccount is created [src: forticnapp-azure-onboarding-agent].
`forticnapp-terraform` is the registry reference for the `lacework/lacework`
provider and modules (`iam-role/aws`, `cloudtrail/aws`, `config/azure`,
`agentless-scanning/aws`, `dspm/aws`, `agent/kubernetes`, …), with a module
picker, provider-authentication order (CLI profile → env vars → static), and
multi-account patterns using aliased providers [src: forticnapp-terraform].

**Code security.** The `code-security` plugin ships three task-scoped skills:
`fortinet:cli-setup` installs the Lacework CLI with IaC and SCA components,
`fortinet:code-review` runs IaC and SCA scans on the current directory, and
`fortinet:settings` enables or disables scanning globally or per repo.

**Assessment and reporting.** `forticnapp-exposure-report` builds the
attack-path and internet-exposure wiki pages (Critical/High/Medium chains and
how internet-exposed hosts with Critical vulnerabilities are reached), and
`forticnapp-inventory` answers questions from the resulting wiki.
`cnapp-report-design` generates self-contained HTML competitive-analysis
reports comparing FortiCNAPP against Wiz, Palo Alto, and other CNAPP vendors.
The scheduled briefings — `cnapp-market-intel-biweekly`,
`casb-sspm-newsletter`, `fortiai-and-cloud-security-bites` — run on cron to
refresh market intelligence.

**Blog and content generation.** `engineering-blog` produces single-file HTML
blog posts in the Fortinet 2026 wiki design system; Template D is the default
(light mode, navy nav + navy footer, system sans-serif, `border-left: 3px
solid var(--accent)` h2s in Fortinet red `#EE3124`, 860px article width, the
9-section structure from Executive Summary through Glossary), and invoked with
no arguments the skill auto-converts unmatched `.md` files into Template D
HTML [src: engineering-blog]. `forticnapp-cloud-security-content` is the
longer-form writing persona for blogs, whitepapers, battlecards, demo
narratives, how-to guides, and competitive teardowns, with explicit minimalism,
citation (`[web:N]`), and black-and-white visual standards aimed at CISO and
engineering audiences [src: forticnapp-cloud-security-content].

## Synthesized catalog

FortiCNAPP-related Claude skills on this laptop. Each row: skill name, one-line purpose, source location.

| Skill | Purpose | Source |
|---|---|---|
| [Skill: forticnapp](../../sources/skill-forticnapp.md) | All-in-one FortiCNAPP (Lacework) assistant - organization enrollment, cloud integrations for AWS/Azure/GCP/OCI (CSPM, activity/audit logs, agentless, DSPM), Terraform pro | `skills/forticnapp/SKILL.md` |
| [Skill: forticnapp-integration](../../sources/skill-forticnapp-integration.md) | Guides users through FortiCNAPP cloud integrations for AWS, Azure, GCP, and OCI. Use when the user asks about setting up CSPM, activity/audit log monitoring, or agentless | `skills/forticnapp/_retired/forticnapp-integration/SKILL.md` |
| [Skill: forticnapp-azure-integration](../../sources/skill-forticnapp-azure-integration.md) | Expert support assistant for integrating FortiCNAPP with Microsoft Azure. Use whenever a user needs to onboard, extend, verify, fix or understand a FortiCNAPP Azure integ | `skills/forticnapp/_retired/forticnapp-azure-integration/SKILL.md` |
| [Skill: forticnapp-terraform](../../sources/skill-forticnapp-terraform.md) | Use when writing, reviewing or troubleshooting Terraform for FortiCNAPP (Lacework) - the lacework provider, authentication, cloud integration modules (AWS, Azure, GCP, OC | `skills/forticnapp/_retired/forticnapp-terraform/SKILL.md` |
| [Skill: forticnapp-lql-agent](../../sources/skill-forticnapp-lql-agent.md) | Generate the most accurate FortiCNAPP LQL query from a natural-language security intent, testing it against the forticnapp MCP server and refining it until it scores 95/1 | `skills/forticnapp/_retired/forticnapp-lql-agent/skills/lql-agent/SKILL.md` |
| `1-doc` | "Answer FortiCNAPP and cloud security questions (product, licensing, RiskWatch, CNAPP, CSPM, CWPP, CIEM, DSPM, Kubernetes hardening, LQL detection rules, Terraform integrations, alert investigation, what is new) from … | `~/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/SKILL.md` |
| `1-doc-contribute` | _(no description)_ | `~/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc-contribute/catalogs.md` |
| `1-doc-contribute` | _(no description)_ | `~/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc-contribute/watch.md` |
| `casb-sspm-newsletter` | CASB-SSPM Market insights | `~/Documents/Claude/Scheduled/casb-sspm-newsletter/SKILL.md` |
| `catalog` | _(no description)_ | `~/tmp/personal_project/forticnapp-inventory/.claude/skills/forticnapp-inventory/catalog/attack-paths.md` |
| `catalog` | _(no description)_ | `~/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/updates.md` |
| `catalog` | _(no description)_ | `~/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/vendors.md` |
| `catalog` | _(no description)_ | `~/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/cloud-security.md` |
| `catalog` | _(no description)_ | `~/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/detection-engineering.md` |
| `catalog` | _(no description)_ | `~/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/operations.md` |
| `cnapp-market-intel-biweekly` | CNAPP Market insights | `~/Documents/Claude/Scheduled/cnapp-market-intel-biweekly/SKILL.md` |
| `cnapp-report-design` | "Generate or update a self-contained HTML competitive-analysis report comparing cloud-native application protection platform vendors — CSPM, CWPP, CIEM, CDR, DSPM, Code Security (e.g. Fortinet FortiCNAPP vs. Wiz, Palo… | `~/tmp/personal_project/newsletter/cnapp/skills/SKILL.md` |
| `engineering-blog` | > | `~/.claude/skills/engineering-blog/SKILL.md` |
| `fortiai-and-cloud-security-bites` | AI and Cloud Security Market trends | `~/Documents/Claude/Scheduled/fortiai-and-cloud-security-bites/SKILL.md` |
| `forticnapp` | > | `~/.claude/skills/forticnapp/SKILL.md` |
| `forticnapp-azure-integration` | Expert support assistant for integrating FortiCNAPP with Microsoft Azure. Use whenever a user needs to onboard, extend, verify, fix or understand a FortiCNAPP Azure integration (subscription or tenant, Configuration/C… | `~/Documents/Claude/Projects/FortiCNAPP/Azure-Onboarding/SKILL.md` |
| `forticnapp-azure-onboarding-agent` | Interactive chatbot that guides a user through a new FortiCNAPP Azure integration: preflight roles, app/SP creation, and CloudAccount creation via FortiCNAPP MCP/API. | `~/Downloads/forticnapp-azure-onboarding-agent/SKILL.md` |
| `forticnapp-azure-onboarding-agent` | Interactive chatbot that guides a user through a new FortiCNAPP Azure integration: preflight roles, app/SP creation, and CloudAccount creation via FortiCNAPP MCP/API. | `~/tmp/personal_project/new_wiki/cnapp_aiassist_integration/forticnapp-azure-onboarding-agent/SKILL.md` |
| `forticnapp-cloud-security-content` | > | `~/Downloads/cnapp_skill/SKILL.md` |
| `forticnapp-exposure-report` | Use when the user asks to build or refresh the FortiCNAPP attack path and internet exposure wiki - Critical/High/Medium attack paths and how internet-exposed hosts with Critical vulnerabilities are reached. Read-only,… | `~/tmp/personal_project/forticnapp-inventory/.claude/skills/forticnapp-exposure-report/SKILL.md` |
| `forticnapp-integration` | _(no description)_ | `~/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/SKILL.yaml` |
| `forticnapp-integration` | Guides users through FortiCNAPP cloud integrations for AWS, Azure, GCP, and OCI. Use when the user asks about setting up CSPM, activity/audit log monitoring, or agentless scanning; choosing Guided Configuration vs Ter… | `~/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp/_retired/forticnapp-integration/SKILL.md` |
| `forticnapp-integration` | _(no description)_ | `~/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/SKILL.yaml` |
| `forticnapp-integration` | Guides users through FortiCNAPP cloud integrations for AWS, Azure, GCP, and OCI. Use when the user asks about setting up CSPM, activity/audit log monitoring, or agentless scanning; choosing Guided Configuration vs Ter… | `~/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp/_retired/forticnapp-integration/SKILL.md` |
| `forticnapp-integration` | _(no description)_ | `~/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/index.md` |
| `forticnapp-integration` | _(no description)_ | `~/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/index.md` |
| `forticnapp-inventory` | "Answer FortiCNAPP attack path and internet exposure questions (attack paths by severity, how exposed hosts are reached from the internet) from the forticnapp-inventory wiki, naming the pages used." | `~/tmp/personal_project/forticnapp-inventory/.claude/skills/forticnapp-inventory/SKILL.md` |
| `forticnapp-mcp-tools` | Use when calling any mcp__forticnapp__* tool (FortiCNAPP/Lacework API) — covers loading deferred tool schemas, building filters/search bodies, dataset vs resourceType confusion on Inventory search, and avoiding oversi… | `~/.claude/skills/forticnapp-mcp-tools/SKILL.md` |
| `forticnapp-mcp-tools` | Use when calling any mcp__forticnapp__* tool (FortiCNAPP/Lacework API) — covers loading deferred tool schemas, building filters/search bodies, dataset vs resourceType confusion on Inventory search, and avoiding oversi… | `~/tmp/personal_project/mcp_forticnapp/.claude/skills/forticnapp-mcp-tools/SKILL.md` |
| `forticnapp-terraform` | Use when writing, reviewing or troubleshooting Terraform for FortiCNAPP (Lacework) - the lacework provider, authentication, cloud integration modules (AWS, Azure, GCP, OCI, Kubernetes), alert channels/profiles/rules, … | `~/Downloads/forticnapp-terraform/SKILL.md` |
| `fortinet:cli-setup` | Install and configure the Lacework CLI with IaC and SCA scanning components | `~/.claude/plugins/cache/fortinet-plugins/code-security/1.7.1/skills/fortinet:cli-setup/SKILL.md` |
| `fortinet:cli-setup` | Install and configure the Lacework CLI with IaC and SCA scanning components | `~/.claude/plugins/marketplaces/fortinet-plugins/plugins/code-security/skills/fortinet:cli-setup/SKILL.md` |
| `fortinet:code-review` | Run Fortinet Code Security IaC and SCA scans on the current directory | `~/.claude/plugins/cache/fortinet-plugins/code-security/1.7.1/skills/fortinet:code-review/SKILL.md` |
| `fortinet:code-review` | Run Fortinet Code Security IaC and SCA scans on the current directory | `~/.claude/plugins/marketplaces/fortinet-plugins/plugins/code-security/skills/fortinet:code-review/SKILL.md` |
| `fortinet:settings` | Configure Fortinet Code Security plugin settings (enable/disable scanning globally or per repo) | `~/.claude/plugins/cache/fortinet-plugins/code-security/1.7.1/skills/fortinet:settings/SKILL.md` |
| `fortinet:settings` | Configure Fortinet Code Security plugin settings (enable/disable scanning globally or per repo) | `~/.claude/plugins/marketplaces/fortinet-plugins/plugins/code-security/skills/fortinet:settings/SKILL.md` |
| `lql-agent` | Generate, fix or test FortiCNAPP LQL queries. Turns a natural-language cloud security question into a validated, executed, scored LQL query using the forticnapp-lql MCP tools. Use when the user says "write an LQL quer… | `~/tmp/personal_project/forticnapp-aiagent/plugin/skills/lql-agent/SKILL.md` |
| `new_wiki` | _(no description)_ | `~/tmp/personal_project/new_wiki/SKILL.md` |
| `references` | _(no description)_ | `~/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/references/aws.md` |
| `references` | _(no description)_ | `~/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/references/aws.md` |
| `references` | _(no description)_ | `~/.claude/skills/forticnapp/references/session1-cnapp.md` |
| `references` | _(no description)_ | `~/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/references/oci.md` |
| `references` | _(no description)_ | `~/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/references/oci.md` |
| `references` | _(no description)_ | `~/.claude/skills/forticnapp/references/azure-troubleshooting.md` |
| `references` | _(no description)_ | `~/tmp/personal_project/forticnapp-aiagent/plugin/skills/lql-agent/references/lql-rules.md` |
| `references` | _(no description)_ | `~/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/references/gcp.md` |
| `references` | _(no description)_ | `~/.claude/skills/forticnapp/references/azure-terraform.md` |
| `references` | _(no description)_ | `~/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/references/gcp.md` |
| `references` | _(no description)_ | `~/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/references/azure.md` |
| `references` | _(no description)_ | `~/.claude/skills/forticnapp/references/azure-permissions.md` |
| `references` | _(no description)_ | `~/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/references/azure.md` |


### Consolidated core FortiCNAPP skills (2026-10-14)

Five core skills were copied verbatim into `skills/` and mapped in `skills/README.md`: `forticnapp` (master, keep), `forticnapp-integration` (redundant), `forticnapp-azure-integration` (redundant after copy, with one unresolved reference conflict), `forticnapp-terraform` (redundant after copy) and the `forticnapp-lql-agent` plugin (optional retire) [src: skill-forticnapp][src: skill-forticnapp-integration][src: skill-forticnapp-azure-integration][src: skill-forticnapp-terraform][src: skill-forticnapp-lql-agent]. The knowledge now sits in topics/lql, topics/integrations, topics/terraform and topics/product-overview.

## Sources

- [1-doc](../../sources/tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-skill-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/SKILL.md`
- [1-doc: cloud-security (17 pages)](../../sources/tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-cloud-security-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/cloud-security.md`
- [1-doc: detection-engineering (5 pages)](../../sources/tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-detection-engineering-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/detection-engineering.md`
- [1-doc: operations (10 pages)](../../sources/tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-operations-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/operations.md`
- [1-doc: updates (3 pages)](../../sources/tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-updates-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/updates.md`
- [1-doc: vendors (5 pages)](../../sources/tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-catalog-vendors-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc/catalog/vendors.md`
- [AWS Integration with FortiCNAPP](../../sources/claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-references-aws-md.md) — `/Users/svuillaume/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/references/aws.md`
- [AWS Integration with FortiCNAPP](../../sources/tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-references-aws-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/references/aws.md`
- [Azure Integration with FortiCNAPP](../../sources/claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-references-azure-md.md) — `/Users/svuillaume/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/references/azure.md`
- [Azure Integration with FortiCNAPP](../../sources/tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-references-azure-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/references/azure.md`
- [Cloud Security & FortiCNAPP Content Expertise](../../sources/downloads-cnapp-skill-skill-md.md) — `/Users/svuillaume/Downloads/cnapp_skill/SKILL.md`
- [CNAPP competitive-report design](../../sources/tmp-personal-project-newsletter-cnapp-skills-skill-md.md) — `/Users/svuillaume/tmp/personal_project/newsletter/cnapp/skills/SKILL.md`
- [Engineering Blog — Design System & Generation Guide](../../sources/claude-skills-engineering-blog-skill-md.md) — `/Users/svuillaume/.claude/skills/engineering-blog/SKILL.md`
- [FortiCNAPP (Lacework) Terraform](../../sources/downloads-forticnapp-terraform-skill-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/SKILL.md`
- [FortiCNAPP Azure Integration — Permissions Reference](../../sources/claude-skills-forticnapp-references-azure-permissions-md.md) — `/Users/svuillaume/.claude/skills/forticnapp/references/azure-permissions.md`
- [FortiCNAPP Azure Integration — Terraform Reference](../../sources/claude-skills-forticnapp-references-azure-terraform-md.md) — `/Users/svuillaume/.claude/skills/forticnapp/references/azure-terraform.md`
- [FortiCNAPP Azure Integration — Troubleshooting Runbook](../../sources/claude-skills-forticnapp-references-azure-troubleshooting-md.md) — `/Users/svuillaume/.claude/skills/forticnapp/references/azure-troubleshooting.md`
- [FortiCNAPP Azure Onboarding Agent](../../sources/downloads-forticnapp-azure-onboarding-agent-skill-md.md) — `/Users/svuillaume/Downloads/forticnapp-azure-onboarding-agent/SKILL.md`
- [FortiCNAPP Azure Onboarding Agent](../../sources/tmp-personal-project-new-wiki-cnapp-aiassist-integration-forticnapp-azure-onboarding-agent-skill-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/cnapp_aiassist_integration/forticnapp-azure-onboarding-agent/SKILL.md`
- [FortiCNAPP Cloud Integration](../../sources/claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-skill-md.md) — `/Users/svuillaume/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp/_retired/forticnapp-integration/SKILL.md`
- [FortiCNAPP Cloud Integration](../../sources/tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-skill-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp/_retired/forticnapp-integration/SKILL.md`
- [FortiCNAPP Cloud Integration](../../sources/tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-index-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/index.md`
- [FortiCNAPP Cloud Integration](../../sources/claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-index-md.md) — `/Users/svuillaume/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/index.md`
- [FortiCNAPP Exposure Report](../../sources/tmp-personal-project-forticnapp-inventory-claude-skills-forticnapp-exposure-report-skill-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-inventory/.claude/skills/forticnapp-exposure-report/SKILL.md`
- [FortiCNAPP LQL authoring](../../sources/tmp-personal-project-forticnapp-aiagent-plugin-skills-lql-agent-skill-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/plugin/skills/lql-agent/SKILL.md`
- [FortiCNAPP MCP Tools](../../sources/claude-skills-forticnapp-mcp-tools-skill-md.md) — `/Users/svuillaume/.claude/skills/forticnapp-mcp-tools/SKILL.md`
- [FortiCNAPP MCP Tools](../../sources/tmp-personal-project-mcp-forticnapp-claude-skills-forticnapp-mcp-tools-skill-md.md) — `/Users/svuillaume/tmp/personal_project/mcp_forticnapp/.claude/skills/forticnapp-mcp-tools/SKILL.md`
- [FortiCNAPP — Master Reference](../../sources/claude-skills-forticnapp-skill-md.md) — `/Users/svuillaume/.claude/skills/forticnapp/SKILL.md`
- [FortiCNAPP ↔ Azure Integration — Expert Support Assistant](../../sources/documents-claude-projects-forticnapp-azure-onboarding-skill-md.md) — `/Users/svuillaume/Documents/Claude/Projects/FortiCNAPP/Azure-Onboarding/SKILL.md`
- [forticnapp-inventory](../../sources/tmp-personal-project-forticnapp-inventory-claude-skills-forticnapp-inventory-skill-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-inventory/.claude/skills/forticnapp-inventory/SKILL.md`
- [forticnapp-inventory: attack-paths (2 pages)](../../sources/tmp-personal-project-forticnapp-inventory-claude-skills-forticnapp-inventory-catalog-attack-paths-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-inventory/.claude/skills/forticnapp-inventory/catalog/attack-paths.md`
- [Fortinet Code Security Review](../../sources/claude-plugins-cache-fortinet-plugins-code-security-1-7-1-skills-fortinet-code-review-skill-md.md) — `/Users/svuillaume/.claude/plugins/cache/fortinet-plugins/code-security/1.7.1/skills/fortinet:code-review/SKILL.md`
- [Fortinet Code Security Review](../../sources/claude-plugins-marketplaces-fortinet-plugins-plugins-code-security-skills-fortinet-code-review-skill-md.md) — `/Users/svuillaume/.claude/plugins/marketplaces/fortinet-plugins/plugins/code-security/skills/fortinet:code-review/SKILL.md`
- [Fortinet Code Security Settings](../../sources/claude-plugins-cache-fortinet-plugins-code-security-1-7-1-skills-fortinet-settings-skill-md.md) — `/Users/svuillaume/.claude/plugins/cache/fortinet-plugins/code-security/1.7.1/skills/fortinet:settings/SKILL.md`
- [Fortinet Code Security Settings](../../sources/claude-plugins-marketplaces-fortinet-plugins-plugins-code-security-skills-fortinet-settings-skill-md.md) — `/Users/svuillaume/.claude/plugins/marketplaces/fortinet-plugins/plugins/code-security/skills/fortinet:settings/SKILL.md`
- [Fortinet Code Security Setup](../../sources/claude-plugins-cache-fortinet-plugins-code-security-1-7-1-skills-fortinet-cli-setup-skill-md.md) — `/Users/svuillaume/.claude/plugins/cache/fortinet-plugins/code-security/1.7.1/skills/fortinet:cli-setup/SKILL.md`
- [Fortinet Code Security Setup](../../sources/claude-plugins-marketplaces-fortinet-plugins-plugins-code-security-skills-fortinet-cli-setup-skill-md.md) — `/Users/svuillaume/.claude/plugins/marketplaces/fortinet-plugins/plugins/code-security/skills/fortinet:cli-setup/SKILL.md`
- [Google Cloud Platform (GCP) Integration with FortiCNAPP](../../sources/tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-references-gcp-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/references/gcp.md`
- [Google Cloud Platform (GCP) Integration with FortiCNAPP](../../sources/claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-references-gcp-md.md) — `/Users/svuillaume/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/references/gcp.md`
- [LQL rules from the FortiCNAPP LQL Reference Guide](../../sources/tmp-personal-project-forticnapp-aiagent-plugin-skills-lql-agent-references-lql-rules-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/plugin/skills/lql-agent/references/lql-rules.md`
- [Oracle Cloud Infrastructure (OCI) Integration with FortiCNAPP](../../sources/claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-references-oci-md.md) — `/Users/svuillaume/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/references/oci.md`
- [Oracle Cloud Infrastructure (OCI) Integration with FortiCNAPP](../../sources/tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-references-oci-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/references/oci.md`
- [Rebuild the /1-doc catalogs and wiki/graph.md](../../sources/tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-contribute-catalogs-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc-contribute/catalogs.md`
- [Session 1 — FortiCNAPP](../../sources/claude-skills-forticnapp-references-session1-cnapp-md.md) — `/Users/svuillaume/.claude/skills/forticnapp/references/session1-cnapp.md`
- [Skill](../../sources/claude-plugins-cache-forticnapp-ai-forticnapp-cloud-integration-1-0-0-skills-forticnapp-integration-skill-yaml.md) — `/Users/svuillaume/.claude/plugins/cache/forticnapp-ai/forticnapp-cloud-integration/1.0.0/skills/forticnapp-integration/SKILL.yaml`
- [Skill](../../sources/documents-claude-scheduled-cnapp-market-intel-biweekly-skill-md.md) — `/Users/svuillaume/Documents/Claude/Scheduled/cnapp-market-intel-biweekly/SKILL.md`
- [Skill](../../sources/tmp-personal-project-forticnapp-aiagent-forticnapp-integration-skills-forticnapp-integration-skill-yaml.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/forticnapp-integration/skills/forticnapp-integration/SKILL.yaml`
- [Skill](../../sources/documents-claude-scheduled-fortiai-and-cloud-security-bites-skill-md.md) — `/Users/svuillaume/Documents/Claude/Scheduled/fortiai-and-cloud-security-bites/SKILL.md`
- [Skill](../../sources/documents-claude-scheduled-casb-sspm-newsletter-skill-md.md) — `/Users/svuillaume/Documents/Claude/Scheduled/casb-sspm-newsletter/SKILL.md`
- [Skill](../../sources/tmp-personal-project-new-wiki-skill-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/SKILL.md`
- [Watched sources](../../sources/tmp-personal-project-new-wiki-llm-wiki-claude-skills-1-doc-contribute-watch-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/.claude/skills/1-doc-contribute/watch.md`
