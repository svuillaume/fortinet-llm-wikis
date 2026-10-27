# Wiki log

- 2026-10-14 — initial build. 714 source stubs across 15 topics. Sources inventoried from `~/forticnapp-index/` (noise paths excluded: paste-cache, tool-results, .terraform/modules, .vscode/extensions, .copilot/session-state, node_modules, truncated Library/Application paths).

- 2026-10-14 — synthesis pass: 8 topic pages compiled with inline `[src: ...]` citations (cspm, cwpp, ciem, dspm, code-security, lql, integrations, terraform). 6 topics (product-overview, mcp-and-agents, rapid-cloud-assessment, operations, demos-blogs-field, runbooks) rendered as source catalogs. `skills/` built as a 51-row catalog from each SKILL.md's `description:`.

- 2026-10-14 — lint pass: 713 source stubs, 15 topic pages. **0 broken links, 0 missing originals, 0 hash drift, 0 orphans, 0 pages still pending.** 119 `[src: basename]` citations use the human-readable basename form instead of stub slugs — they still resolve to real files on disk via grep, but are not clickable from topic pages. Acceptable as-is for LLM consumption.

- 2026-10-14 — second synthesis pass: remaining 7 topics (product-overview, mcp-and-agents, rapid-cloud-assessment, operations, demos-blogs-field, runbooks, skills) now have a prose `## Overview` section with `[src: ...]` citations inserted above their existing catalog tables. All 15 topics are now synthesized.

- 2026-10-14 | ingest | FortiCloud Organizations overview text (pasted in chat; sha1 ae4ef40f732e) | sources/pasted-forticloud-organizations-overview.md (new), topics/product-overview/index.md (overview paragraph, catalog row, sources list, count 178→179), index.md (counts 713→714, 178→179). No conflicts. Original page URL not provided.

- 2026-10-14 | ingest-update | FortiCloud Organizations (sha1 ae4ef40f732e) | source URL added and verified against the live page (https://docs.fortinet.com/document/forticnapp/latest/administration-guide/096943/navigating-forticloud-services): stub, product-overview catalog row, sources list. Other sections of that page (FortiCare ticketing services, User types) not ingested.

- 2026-10-14 | ingest | FortiCNAPP Organization overview (pasted text; sha1 ca955708369f; URL https://docs.fortinet.com/document/forticnapp/latest/administration-guide/068366/organization-overview probable, page body not verifiable) | sources/forticnapp-docs-organization-overview.md (new), sources/pasted-forticloud-organizations-overview.md (related link), topics/product-overview/index.md (organization enrollment paragraph with open items, catalog row, sources list, count 179→180), index.md (counts 714→715, 179→180). No contradiction with existing pages; reconciliation of enrollment model vs FortiCloud OU model flagged as open.

- 2026-10-14 | consolidate | core FortiCNAPP/LQL skills (forticnapp, forticnapp-integration, forticnapp-azure-integration, forticnapp-terraform, forticnapp-lql-agent plugin) | skills/ (58 files copied verbatim, hashes verified, MANIFEST.sha256, README.md, _archive tarball), sources/skill-*.md (5 new), topics/lql, topics/integrations, topics/terraform, topics/skills, topics/product-overview (sections added), index.md (counts 715→720, skills 51→56). Conflicts flagged: Azure Security Reader/admin consent (references vs SKILL.md), LQL output format (named vs unnamed). Skills themselves not deleted.

- 2026-10-14 | restructure | single FortiCNAPP skill | skills/forticnapp/ now holds SKILL.md (v1 verbatim), references/{terraform,azure}, _retired/ (integration, azure-integration, terraform, lql-agent). Manifest remapped, 58/58 hashes OK. v2 SKILL.md (absorbs Terraform triggers, wiki-first lookup, single-agent LQL, Azure-reference caveat) submitted as a propose_skills improvement for `forticnapp`; skill removals are done by the user.

- 2026-10-14 — ingest: inline note "FortiCloud Organizations" (hash ae4ef40f732e) → `sources/user-chat-forticloud-organizations-2026-10-14.md`. Related pages flagged for later cross-linking: product-overview, integrations.
- 2026-10-14 — archive: moved `~/.claude/skills/forticnapp/` (SKILL.md + references/) → `~/forticnapp-wiki-llm/_archived/forticnapp-skill/`. Skill is now disabled in Claude Code; content preserved for wiki reference. Reverse with `mv ~/forticnapp-wiki-llm/_archived/forticnapp-skill ~/.claude/skills/forticnapp`.

- 2026-10-14 — archive: moved `~/.claude/skills/forticnapp-exposure-report/` and `~/.claude/skills/forticnapp-mcp-tools/` into `~/forticnapp-wiki-llm/_archived/`. Both now disabled in Claude Code; content preserved. Reverse with `mv` back.

- 2026-10-14 | ingest | Automated configuration (FortiCNAPP admin doc excerpt, user-pasted) | sources/user-chat-automated-configuration-2026-10-14.md, topics/integrations/index.md

- 2026-10-14 | lint-fix | 7 archived-skill stubs repointed to ~/forticnapp-wiki-llm/_archived/ paths; 2 inline-ingest / URL stubs marked `inline: true`. All 15 L-sev "missing original" findings cleared.

- 2026-10-14 | ingest | FortiCare→FortiCloud→FortiCNAPP org mapping & SKU split (user-pasted) | sources/user-chat-forticare-forticnapp-org-mapping-2026-10-14.md, topics/product-overview/index.md

- 2026-10-15 | ingest | local repo `/Users/svuillaume/forticnapp-wiki` (27 new sources; CLAUDE.md, .claude/, .git/, .test.html.swp excluded; README.md skipped as 16-byte heading only). Added: 8→code-security, 4→product-overview, 2→cwpp, 1→cspm, 1→operations, 10→demos-blogs-field, 1→mcp-and-agents. Same-basename pairs (root vs `html/`, distinct hashes) kept as separate stubs cross-linked in a Related section; whether they are alternate builds or revisions is unverified. index.md totals 720→747. Hash diff against existing stubs matched none of the 27.

- 2026-10-15 | ingest | FortiCNAPP multi-tenant / sub-account support and legacy SAML (user-pasted; tag: FortiCNAPP Multi Tenant or Sub Account) | sources/user-chat-forticnapp-multitenant-legacy-saml-2026-10-15.md, topics/product-overview/index.md

- 2026-10-15 | ingest | FortiCNAPP News and Release Announcements, Jul–Oct 2026 (user-uploaded file a78a1ab4-attachment.txt, 7084 bytes, sha1 4647b150c38d) | sources/user-upload-forticnapp-news-releases-jul-oct-2026-2026-10-15.md, topics/product-overview/index.md, topics/code-security/index.md, topics/cwpp/index.md, topics/integrations/index.md, topics/demos-blogs-field/index.md

- 2026-10-15 | ingest | RCA hosted-service docs, 4 user-uploaded HTML files (FortiRCA.html wrapper d6214f035332; rca-documentation a2fd57d59984; rca-guided-setup 4fa0fbb74f96; rca-diagram 03339007dafc) | sources/user-upload-rca-*-2026-10-15.md (4 new), topics/rapid-cloud-assessment/index.md (new Hosted RCA service section, catalog rows, sources list, count 96->100), index.md (747->751, 96->100). Embedded images not extracted. Conflicts flagged, not reconciled: hosted rca.fabriclab.ca vs Docker/Vercel descriptions, score naming, report formats.

- 2026-10-15 | ingest | user clarification: RCA Cloud Security Risk Score = posture score (higher = fewer risk findings) | sources/user-chat-rca-score-naming-2026-10-15.md (new), topics/rapid-cloud-assessment/index.md (open item 2 resolved, score bullet updated). Stub count not changed in index.md totals (751 -> 752, RCA 100 -> 101).

- 2026-10-15 | ingest | user statement: rca.fabriclab.ca is a new service the user created and is launching | sources/user-chat-rca-hosted-service-launch-2026-10-15.md (new), topics/rapid-cloud-assessment/index.md (open item 1 partly resolved, intro line, sources list, count 101->102), index.md (752->753, 101->102). Codebase lineage still not stated.

- 2026-10-16 | ingest | Fortinet blog "How Feedback Loops and Machine Learning Power High-Precision Intrusion Detection in Lacework FortiCNAPP" (user-uploaded clipping 781cf743-attachment.txt, 10153 bytes, sha1 61c1a95eafc9) | sources/user-upload-fortinet-blog-feedback-loops-intrusion-detection-2026-10-16.md (new), topics/demos-blogs-field/index.md (new section, catalog row, sources list, count 47->48), topics/cwpp/index.md (new Composite Alerts section, sources list, count 48->49), index.md (753->754, cwpp 48->49, demos 47->48). Bad `published: 2001-08-01` in clipping noted, real date unknown. Figures 1-3 not extracted. No conflicts with existing pages.

- 2026-10-16 | ingest | user chat text: Azure CLI resource provider registration quick guide (inline, no file, no hash; ~2426 bytes) | sources/user-chat-azure-resource-provider-registration-quick-guide-2026-10-16.md (new), topics/integrations/index.md (new Azure resource provider registration section, sources list, count 18->19), index.md (754->755, integrations 18->19). Microsoft doc link was text only. No conflicts; FortiCNAPP relevance not stated in source.

- 2026-10-21 | ingest | Wiz Academy "What is SaaS Security Posture Management (SSPM)?" (https://www.wiz.io/academy/application-security/saas-security-posture-management-sspm; WebFetch summary, no raw hash; vendor claim) | sources/wiz-academy-sspm-guide-2026-08-04.md (new), topics/product-overview/index.md (new Wiz/SSPM subsection, catalog row, sources, count 184->185), index.md (755->756, 184->185)

- 2026-10-21 | ingest | FortiCNAPP Kubernetes compliance integration: core concepts and Kubernetes compliance docs (user-pasted chat text, no file, no hash, no URL; pasted twice, ingested once) | sources/user-chat-kubernetes-compliance-integration-2026-10-21.md (new), topics/cwpp/index.md (new Kubernetes compliance integration section, sources list, count 49->50), index.md (756->757, cwpp 49->50). No conflicts with existing pages. Stated EKS/GKE support limits and collector schedules are new to the wiki.

- 2026-10-21 | ingest | Install Linux Agent on Kubernetes: Helm, DaemonSet, Terraform, gVisor (user-pasted chat text, no file, no hash, no URL; pasted twice, ingested once) | sources/user-chat-linux-agent-kubernetes-install-2026-10-21.md (new), topics/cwpp/index.md (new Installing the agent on Kubernetes section, sources list, count 50->51), index.md (757->758, cwpp 50->51). Conflicts flagged, not reconciled: Terraform module ~> 1.0 here vs 2.x in kubernetes-agent stub; Kubernetes version ranges inconsistent within doc.

- 2026-10-21 | ingest | How FortiCNAPP derives the K8s cluster name (/Users/svuillaume/.codex/attachments/c333a896-994b-4ae8-92e1-ff31f952b2a8/Pasted text.txt; sha1 d41072d44c0ed1a03103dac27cf3902a081ed37f) | sources/user-paste-kubernetes-cluster-name-2026-10-21.md (new), topics/cwpp/index.md (cluster-name section, sources 51->52), index.md (758->759, CWPP 51->52). No new cross-source conflicts; malformed JSON, incomplete Helm command and Terraform refresh-only instruction flagged. Referenced machine-tag example absent from paste.

- 2026-10-22 | ingest | FortiCNAPP 26.3.0 admin guide: Unified risk management, Explorer policies, Risk Insights (user-pasted text, 12109 bytes, sha1 f20ab20aa46e; linked pages not fetched) | sources/user-paste-unified-risk-management-risk-insights-2026-10-22.md (new), topics/product-overview/index.md (new section, catalog row, sources list, count 185->186), index.md (759->760, 185->186). No conflicts; flagged 24h vs 6h evaluation wording. Complements existing video-based Risk Insights stub.

- 2026-10-23 | ingest | Wiz Security Graph blog, Wiz Defend GA post, Wiz Academy behavioral analytics (3 URLs, summarizing fetch, no raw files, sha1 of extracted text) | sources/wiz-security-graph-incident-response-2026-10-23.md (new), sources/wiz-defend-ga-2026-10-23.md (new), sources/wiz-academy-ai-behavioral-analytics-2026-10-23.md (new), topics/product-overview/index.md (new Polygraph v2 vs Wiz section, status stays needs-review)
2026-10-27 | delete | sources/tmp-personal-project-new-wiki-sailboat-wiki-1-doc-bundle-md.md | topics/product-overview/index.md, index.md | none (no src citations)
