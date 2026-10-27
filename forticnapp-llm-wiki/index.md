# FortiCNAPP LLM Wiki

Compiled wiki over **760** FortiCNAPP/Lacework source documents on this laptop.
- **Built:** 2026-10-14 (last ingest: 2026-10-22)
- **Source catalog:** [~/forticnapp-index/INDEX.md](../forticnapp-index/INDEX.md)
- **Changelog:** [log.md](log.md)

## Topics

- [`product-overview/`](topics/product-overview/index.md) — What FortiCNAPP is, modules, positioning. (188 sources)
- [`cspm/`](topics/cspm/index.md) — Cloud Security Posture Management: policies, suppressions, config checks. (9 sources)
- [`cwpp/`](topics/cwpp/index.md) — Workload protection: agent, AWLS (agentless), container, Kubernetes runtime. (52 sources)
- [`ciem/`](topics/ciem/index.md) — Cloud Identity & Entitlement Management: identities, permissions, attack chains. (17 sources)
- [`dspm/`](topics/dspm/index.md) — Data Security Posture Management across AWS and Azure. (38 sources)
- [`code-security/`](topics/code-security/index.md) — Shift-left: SCA, SAST, IaC, SBOM, VS Code extension, pipeline scanning. (37 sources)
- [`integrations/`](topics/integrations/index.md) — Cloud provider onboarding: AWS, Azure, GCP, OCI. (19 sources)
- [`terraform/`](topics/terraform/index.md) — Lacework/FortiCNAPP Terraform modules and provider auth. (82 sources)
- [`lql/`](topics/lql/index.md) — Lacework Query Language: syntax, datasources, query library. (46 sources)
- [`mcp-and-agents/`](topics/mcp-and-agents/index.md) — MCP server, LQL agent, AI integration patterns. (53 sources)
- [`skills/`](topics/skills/index.md) — Claude skills related to FortiCNAPP (what each does, how to invoke). (56 sources)
- [`rapid-cloud-assessment/`](topics/rapid-cloud-assessment/index.md) — RCA tool: UI, scoring, PDF reporting, deployment. (102 sources)
- [`operations/`](topics/operations/index.md) — Alerts, rules, channels, resource groups, admin guide operations. (8 sources)
- [`demos-blogs-field/`](topics/demos-blogs-field/index.md) — Blog posts, demo scripts, field notes, customer-facing materials. (48 sources)
- [`runbooks/`](topics/runbooks/index.md) — Troubleshooting, API, CLI, onboarding and remediation runbooks. (8 sources)

## How this wiki works

- `sources/<slug>.md` — one stub per raw document (frontmatter + first paragraph).
- `topics/<area>/index.md` — landing page listing every source routed there, plus synthesized content.
- Originals never modified. Stubs record `path` and `sha1` so staleness is detectable.

## Latest source addition

- [Wiz Security Graph, Defend and behavioral analytics](sources/wiz-security-graph-incident-response-2026-10-23.md) — incorporated into [Product Overview](topics/product-overview/index.md); Wiz claims only, no GNN mention found (2026-10-23).
- [Unified risk management and Risk Insights](sources/user-paste-unified-risk-management-risk-insights-2026-10-22.md) — incorporated into [Product Overview](topics/product-overview/index.md); preview feature, linked pages not supplied (2026-10-22).
- [Kubernetes cluster name discovery](sources/user-paste-kubernetes-cluster-name-2026-10-21.md) — incorporated into [CWPP](topics/cwpp/index.md); source command/example issues need review (2026-10-21).
