---
title: Lql
summary: Lacework Query Language: syntax, datasources, query library.
sources: [tmp-personal-project-new-wiki-llm-wiki-raw-forticnapp-lql-reference-guide-1-67512d-txt, tmp-personal-project-forticnapp-aiops-mcp-demo-prompts-act2-lql-generation-txt, tmp-lacework-lql-lacework-api-query-docs-api-md, tmp-lacework-lql-lacework-api-query-lacework-api-query-docs-api-md, tmp-personal-project-forticnapp-ctf-challenges-readme-md, tmp-personal-project-nlp-lql-claude-md, claude-cnapp-lql-claude-md, tmp-lacework-lql-lacework-api-query-lacework-api-query-scripts-csa-ccm-v4-0-5-policies-table-txt, tmp-personal-project-forticnapp-aiops-readme-md, tmp-samv-test-forticnapp-ai-readme-md, downloads-forticnapp-lql-agent-readme-md, tmp-personal-project-forticnapp-aiagent-readme-md, tmp-personal-project-lql-agent-docs-superpowers-plans-2026-08-02-forticnapp-lql-agent-md, tmp-personal-project-lql-agent-docs-superpowers-specs-2026-08-02-forticnapp-lql-agent-design-md, claude-cnapp-lql-readme-md, downloads-mcp-detection-lql-queries-md, tmp-personal-project-webaiagent-forticnapp-lql-reference-guide-txt, tmp-personal-project-forticnapp-aiops-forticnapp-lql-reference-guide-txt, tmp-personal-project-webaiagent-local-forticnapp-lql-reference-guide-txt, tmp-personal-project-forticnapp-aiagent-plugin-readme-md, tmp-personal-project-nlp-lql-forticnapp-lql-reference-guide-md, tmp-lacework-lql-lacework-api-query-lacework-api-query-readme-md, tmp-lacework-lql-lacework-api-query-readme-md, tmp-lacework-lql-refactoring-notes-md, tmp-personal-project-converters-docs-superpowers-specs-2026-07-17-lacework-cli-grounded-lql-design-md, tmp-personal-project-new-wiki-llm-wiki-wiki-detection-engineering-lql-language-reference-md, tmp-samv-test-forticnapp-ai-claude-agents-lql-agent-md, claude-agents-lql-agent-md, downloads-forticnapp-lql-agent-claude-agents-lql-agent-md, tmp-personal-project-forticnapp-aiagent-claude-agents-lql-agent-md, claude-plugins-cache-forticnapp-ai-forticnapp-lql-0-1-0-agents-lql-agent-md, downloads-claude-md, tmp-personal-project-lql-agent-docs-superpowers-plans-2026-08-04-lql-agent-tui-completion-md, tmp-personal-project-lql-agent-docs-superpowers-specs-2026-08-04-lql-agent-tui-design-md, tmp-personal-project-converters-readme-md, tmp-personal-project-new-wiki-llm-wiki-wiki-detection-engineering-lql-datasources-md, tmp-personal-project-new-wiki-llm-wiki-wiki-detection-engineering-lql-example-queries-md, tmp-personal-project-converters-docs-superpowers-specs-2026-07-17-lql-vector-db-design-md, tmp-personal-project-lql-agent-readme-md, claude-projects-users-svuillaume-tmp-personal-project-aiagent-memory-memory-md, claude-projects-users-svuillaume-claude-cnapp-lql-memory-memory-md, tmp-personal-project-nlp-lql-nlq2lql-readme-md, tmp-lacework-lql-pdf-generation-md, claude-projects-users-svuillaume-tmp-personal-project-aiagent-memory-reference-lql-guide-md, claude-projects-users-svuillaume-claude-cnapp-lql-memory-reference-lql-syntax-md, claude-plans-sunny-toasting-wind-md]
updated: 2026-10-14
status: needs-review
---

# Lql

Lacework Query Language: syntax, datasources, query library.

## Scope

This page indexes **46** source documents routed to this topic.

## Synthesized content

LQL (Lacework Query Language) is a SQL-like language used in FortiCNAPP to select, filter, and shape data from curated cloud and workload datasources. Queries can be executed interactively or associated with policies that carry reporting metadata [src: forticnapp-lql-reference-guide-1-67512d.txt]. The 26.2 reference describes a 72,000-character maximum per query, with case-insensitive keywords, case-sensitive identifiers, and an eleven-word reserved list including `JOIN`, `LIMIT`, `OUTER`, `SELECT`, `WHERE`, and `TYPE` that must be double-quoted when they appear as JSON keys [src: forticnapp-lql-reference-guide-1-67512d.txt].

### Query structure

Every query is delimited by `{ }` and contains three clauses — `source`, `filter`, and `return` [src: forticnapp-lql-reference-guide-1-67512d.txt]:

```lql
{
    source {
        LW_CFG_AWS_EC2_EBS_ENCRYPTION_BY_DEFAULT
    }
    filter {
        RESOURCE_CONFIG:EbsEncryptionByDefault = 'false'
    }
    return distinct {
        ACCOUNT_ALIAS,
        ACCOUNT_ID as RESOURCE_KEY,
        RESOURCE_REGION,
        RESOURCE_TYPE,
        SERVICE,
        'EbsEncryptionNotEnabledByDefault' as COMPLIANCE_FAILURE_REASON
    }
}
```

`source` names the datasource(s) and may alias them (`LW_CFG_... a`); the alias then qualifies field references (`a.ACCOUNT_ID`) [src: forticnapp-lql-reference-guide-1-67512d.txt]. `filter` is any boolean expression over source rows; `return` lists the columns (optionally `return distinct` for de-duplication, or `source.*` for every column) [src: forticnapp-lql-reference-guide-1-67512d.txt]. Expressions that are not plain column references must be aliased with `AS`.

### Data types, JSON, and casting

Supported types are String, Timestamp, Number, Json, Boolean, and Null; the Boolean type cannot be returned from a datasource [src: forticnapp-lql-reference-guide-1-67512d.txt]. JSON fields are navigated with `:` plus a dot-separated path (`EVENT:requestParameters.ipPermissions`), using double-quoted segments for non-identifier keys like `"aws:cloudformation:stack-name"` [src: forticnapp-lql-reference-guide-1-67512d.txt]. The `::` cast operator forces a type, e.g. `EVENT:eval_guid::String` [src: forticnapp-lql-reference-guide-1-67512d.txt]. Working with JSON arrays inline is not supported — instead, expand them with `array_to_rows(expr) alias` (or `array_to_rows_non_empty` to drop null arrays, mimicking an inner join) in the `source` clause [src: forticnapp-lql-reference-guide-1-67512d.txt]. Standard SQL null semantics apply (`IS NULL`, `IS NOT NULL`); JSON null is distinct and tested with `IS JSON NULL` / `IS NOT JSON NULL` [src: forticnapp-lql-reference-guide-1-67512d.txt].

### Datasource model, joins, and cardinality

Datasources are grouped by domain: `LW_CFG_*` (cloud configuration — AWS, Azure, GCP), `LW_HA_*` (host agent activity), `LW_HE_*` (host entities), `LW_APA_*` (attack-path analysis), `LW_CE_*` (cloud entitlements), plus `CloudTrailRawEvents` [src: forticnapp-lql-reference-guide-1-67512d.txt]. Multi-source queries use `WITH ... ON` to connect datasources along a path the platform publishes in its metadata; this behaves like a SQL left outer join (unmatched right-side fields are NULL) [src: forticnapp-lql-reference-guide-1-67512d.txt]:

```lql
source {
    LW_HE_FILES files with LW_HE_MACHINES machines on '(default)'
}
```

Connections have names (`'(default)'` when there is only one) and a published cardinality of `ONE` or `MANY`. Chains always nest right-to-left: `A with (B with C)` is valid; `(A with B) with C` is rejected because the left side of `WITH` must be a single datasource [src: forticnapp-lql-reference-guide-1-67512d.txt]. Branches combine multiple right-side sources: `A with (B, C)` yields the cartesian product of matches per `A` row [src: forticnapp-lql-reference-guide-1-67512d.txt].

### Operators, functions, and set operations

Comparison operators follow SQL (`<`, `<=`, `>`, `>=`, `=`, `<>`), with `IN`/`NOT IN`, `BETWEEN low AND high`, `LIKE`/`ILIKE` (`%`, `_` wildcards), POSIX-extended `RLIKE`, and multi-pattern variants `LIKE ANY`, `ILIKE ANY`, `RLIKE ANY` [src: forticnapp-lql-reference-guide-1-67512d.txt]. Logical operators `AND OR NOT` follow SQL precedence, and any null input to arithmetic, comparison, or logic produces null [src: forticnapp-lql-reference-guide-1-67512d.txt]. `CASE WHEN ... THEN ... ELSE ... END` and `COALESCE` cover conditional logic [src: forticnapp-lql-reference-guide-1-67512d.txt]. The function library spans timestamp math (`ADD_DAYS`, `DIFF_HOURS`, `SEC_TO_TIMESTAMP`, `CURRENT_TIMESTAMP_SEC`), string handling (`STARTS_WITH`, `ENDS_WITH`, `CONTAINS`, `LOWER`, `SUBSTRING`), JSON helpers (`KEY_EXISTS`, `VALUE_EXISTS`, `IS_ARRAY`, `IS_OBJECT`, `ARRAY_SIZE`, `ANY_IN_ARRAY`), and IP helpers (`IP_CONTAINS`, `IP_FAMILY`, `IP_HIGH_NETMASK_BITS`) [src: forticnapp-lql-reference-guide-1-67512d.txt]. `UNION` and `UNION ALL` combine multiple inner `{ source / filter / return }` blocks, which must have identical result shapes [src: forticnapp-lql-reference-guide-1-67512d.txt].

### Policy evaluation and time windows

When an LQL query is attached to a policy, the first (root) datasource defines the resource the policy is about. If the query only uses `ONE`-cardinality joins and no `ARRAY_TO_ROWS`, any column from any source may be returned. As soon as any `MANY` join or array expansion appears, the query **must** use `return distinct`, and returned columns are restricted to the root datasource plus `ONE`-connected sources — fields from `MANY`-connected sources or from `ARRAY_TO_ROWS` outputs may be used in `filter` but not in `return` [src: forticnapp-lql-reference-guide-1-67512d.txt]. Interactive execution via the Lacework CLI uses a YAML envelope (`queryId:` + `queryText: |-`) submitted with `lacework query validate --file ...` and, for actual results, `lacework query run --file ... --start <t> --end <t>`; a time range is mandatory for `run`, which is why automation gates it behind an explicit flag [src: 2026-08-02-forticnapp-lql-agent.md].

### Common pitfalls

Confusing JSON null with standard null (`= null` never works — use `IS NULL` or `IS JSON NULL`) [src: forticnapp-lql-reference-guide-1-67512d.txt]; writing `(A with B) with C` instead of right-nested joins [src: forticnapp-lql-reference-guide-1-67512d.txt]; forgetting `return distinct` after array expansion or `MANY` joins in a policy query, which yields duplicate violations or an outright rejection [src: forticnapp-lql-reference-guide-1-67512d.txt]; omitting the `AS` alias on expression-based return columns, which the engine will not auto-name [src: forticnapp-lql-reference-guide-1-67512d.txt]; and inventing field or datasource names rather than discovering them via `lacework query list-sources` / `show-source` — real errors surface on stderr as `Source named 'X' is not found on line N position M` and should be fed back into a validate/fix loop [src: 2026-08-02-forticnapp-lql-agent.md].

### Query-writing method: the scored generate, validate, execute loop

The FortiCNAPP MCP server is the ground truth for schema, fields, data and execution; if it contradicts prior knowledge, MCP wins [src: skill-forticnapp][src: skill-forticnapp-lql-agent]. Rules: discover the MCP tools first, never invent tool names, fields, tables, operators or relationships, add only the conditions the intent requires, and treat a query as unproven until it has executed through MCP; with no execution tool, say so and stop [src: skill-forticnapp-lql-agent].

The loop runs at most **20 iterations** and stops at a score of **95 or more** with valid syntax, schema, execution and intent match. Scoring (out of 100): syntax 20, schema 20, successful execution 20, intent match 30, result relevance 10; zero rows on an intent that should match suggests an over-filter. Refine the previous best candidate from the MCP error, and never return a later, worse candidate [src: skill-forticnapp-lql-agent][src: skill-forticnapp].

**Output.** The chat shows the final LQL as an unnamed `{ source { ... } filter { ... } return distinct { ... } }` block, a results table, then `Accuracy Score: NN/100` and `Confidence: NN%` (lower when few rows were inspected). Compliance and config datasources use the standard return columns (ACCOUNT_ALIAS, ACCOUNT_ID, key as RESOURCE_KEY, RESOURCE_REGION, RESOURCE_TYPE, SERVICE, a literal COMPLIANCE_FAILURE_REASON); host datasources return what the intent needs. Iteration history goes in a .md file, not the chat [src: skill-forticnapp]. *Conflict:* the `lql-agent` skill describes a named query (`Name { source ... }`) and returns LQL plus score only [src: skill-forticnapp-lql-agent]; see `skills/README.md`.

**Host and workload pattern (confirm every field through MCP).** (1) containers: `LW_HE_IMAGES` filter REPO, returning MID, REPO, IMAGE_ID; (2) VMs: `LW_HE_PROCESSES` filter CMDLINE or EXE_PATH, returning MID, CMDLINE; (3) resolve MIDs through `LW_HE_MACHINES` for hostname, account, region, public IP; (4) enumerate instances through `LW_HE_CONTAINERS` filtered on MID [src: skill-forticnapp]. **MCP-server detection:** containers match REPO against `^docker.io/mcp/`, `%/mcp-%`, `%-mcp%`, `%mcp-server%`, `%mcp-gateway%`, `%modelcontextprotocol%`, `%anthropic%`, `%/claude-%` (image-based beats name-based); VMs match CMDLINE for `modelcontextprotocol`, `mcp-server`, `mcp-gateway`, `mcp.server`, `docker mcp gateway`, and `npx`, `uvx` or `python` combined with `mcp` [src: skill-forticnapp].

## Sources

- [#https://docs.lacework.net/lql/restricted/lql- query-examples#iam- users-with-two-active-access-](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-forticnapp-lql-reference-guide-1-67512d-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/forticnapp-lql-reference-guide-1-67512d.txt`
- [Act2 Lql Generation](../../sources/tmp-personal-project-forticnapp-aiops-mcp-demo-prompts-act2-lql-generation-txt.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiops/mcp_demo/prompts/act2_lql_generation.txt`
- [API Documentation for Lacework API Query Script](../../sources/tmp-lacework-lql-lacework-api-query-docs-api-md.md) — `/Users/svuillaume/tmp/lacework_lql/lacework-api-query/docs/API.md`
- [API Documentation for Lacework API Query Script](../../sources/tmp-lacework-lql-lacework-api-query-lacework-api-query-docs-api-md.md) — `/Users/svuillaume/tmp/lacework_lql/lacework-api-query/lacework-api-query/docs/API.md`
- [Bonus / hand-authored challenges](../../sources/tmp-personal-project-forticnapp-ctf-challenges-readme-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-ctf/challenges/README.md`
- [CLAUDE.md](../../sources/tmp-personal-project-nlp-lql-claude-md.md) — `/Users/svuillaume/tmp/personal_project/nlp-lql/CLAUDE.md`
- [CLAUDE.md](../../sources/claude-cnapp-lql-claude-md.md) — `/Users/svuillaume/claude_cnapp/lql/CLAUDE.md`
- [Csa Ccm V4 0 5 Policies Table](../../sources/tmp-lacework-lql-lacework-api-query-lacework-api-query-scripts-csa-ccm-v4-0-5-policies-table-txt.md) — `/Users/svuillaume/tmp/lacework_lql/lacework-api-query/lacework-api-query/scripts/CSA_CCM_v4_0_5_policies_table.txt`
- [FortiCNAPP AIOps Assistant — Claude Desktop MCP](../../sources/tmp-personal-project-forticnapp-aiops-readme-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiops/README.md`
- [FortiCNAPP LQL Agent](../../sources/tmp-samv-test-forticnapp-ai-readme-md.md) — `/Users/svuillaume/tmp/samv_test/forticnapp-ai/README.md`
- [FortiCNAPP LQL Agent](../../sources/downloads-forticnapp-lql-agent-readme-md.md) — `/Users/svuillaume/Downloads/forticnapp-lql-agent/README.md`
- [FortiCNAPP LQL Agent](../../sources/tmp-personal-project-forticnapp-aiagent-readme-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/README.md`
- [FortiCNAPP LQL Agent Implementation Plan](../../sources/tmp-personal-project-lql-agent-docs-superpowers-plans-2026-08-02-forticnapp-lql-agent-md.md) — `/Users/svuillaume/tmp/personal_project/lql_agent/docs/superpowers/plans/2026-08-02-forticnapp-lql-agent.md`
- [FortiCNAPP LQL Agent — Design](../../sources/tmp-personal-project-lql-agent-docs-superpowers-specs-2026-08-02-forticnapp-lql-agent-design-md.md) — `/Users/svuillaume/tmp/personal_project/lql_agent/docs/superpowers/specs/2026-08-02-forticnapp-lql-agent-design.md`
- [FortiCNAPP LQL MCP Server + Chat](../../sources/claude-cnapp-lql-readme-md.md) — `/Users/svuillaume/claude_cnapp/lql/README.md`
- [FortiCNAPP LQL Queries — MCP Server Detection](../../sources/downloads-mcp-detection-lql-queries-md.md) — `/Users/svuillaume/Downloads/mcp_detection_lql_queries.md`
- [Forticnapp Lql Reference Guide](../../sources/tmp-personal-project-webaiagent-forticnapp-lql-reference-guide-txt.md) — `/Users/svuillaume/tmp/personal_project/webaiagent/FortiCNAPP-LQL_Reference_Guide.txt`
- [Forticnapp Lql Reference Guide](../../sources/tmp-personal-project-forticnapp-aiops-forticnapp-lql-reference-guide-txt.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiops/FortiCNAPP-LQL_Reference_Guide.txt`
- [Forticnapp Lql Reference Guide](../../sources/tmp-personal-project-webaiagent-local-forticnapp-lql-reference-guide-txt.md) — `/Users/svuillaume/tmp/personal_project/webaiagent_local/FortiCNAPP-LQL_Reference_Guide.txt`
- [forticnapp-lql plugin](../../sources/tmp-personal-project-forticnapp-aiagent-plugin-readme-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/plugin/README.md`
- [FortiCNAPP-LQL_Reference_Guide](../../sources/tmp-personal-project-nlp-lql-forticnapp-lql-reference-guide-md.md) — `/Users/svuillaume/tmp/personal_project/nlp-lql/FortiCNAPP-LQL_Reference_Guide.md`
- [Lacework API Query](../../sources/tmp-lacework-lql-lacework-api-query-lacework-api-query-readme-md.md) — `/Users/svuillaume/tmp/lacework_lql/lacework-api-query/lacework-api-query/README.md`
- [Lacework API Query](../../sources/tmp-lacework-lql-lacework-api-query-readme-md.md) — `/Users/svuillaume/tmp/lacework_lql/lacework-api-query/README.md`
- [Lacework LQL Script - Refactoring Notes](../../sources/tmp-lacework-lql-refactoring-notes-md.md) — `/Users/svuillaume/tmp/lacework_lql/REFACTORING_NOTES.md`
- [Lacework-CLI-Grounded LQL Builder — Design](../../sources/tmp-personal-project-converters-docs-superpowers-specs-2026-07-17-lacework-cli-grounded-lql-design-md.md) — `/Users/svuillaume/tmp/personal_project/converters/docs/superpowers/specs/2026-07-17-lacework-cli-grounded-lql-design.md`
- [LQL (Lacework Query Language) Reference](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-detection-engineering-lql-language-reference-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/detection-engineering/lql-language-reference.md`
- [Lql Agent](../../sources/tmp-samv-test-forticnapp-ai-claude-agents-lql-agent-md.md) — `/Users/svuillaume/tmp/samv_test/forticnapp-ai/.claude/agents/lql-agent.md`
- [Lql Agent](../../sources/claude-agents-lql-agent-md.md) — `/Users/svuillaume/.claude/agents/lql-agent.md`
- [Lql Agent](../../sources/downloads-forticnapp-lql-agent-claude-agents-lql-agent-md.md) — `/Users/svuillaume/Downloads/forticnapp-lql-agent/.claude/agents/lql-agent.md`
- [Lql Agent](../../sources/tmp-personal-project-forticnapp-aiagent-claude-agents-lql-agent-md.md) — `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/.claude/agents/lql-agent.md`
- [Lql Agent](../../sources/claude-plugins-cache-forticnapp-ai-forticnapp-lql-0-1-0-agents-lql-agent-md.md) — `/Users/svuillaume/.claude/plugins/cache/forticnapp-ai/forticnapp-lql/0.1.0/agents/lql-agent.md`
- [LQL agent project instructions](../../sources/downloads-claude-md.md) — `/Users/svuillaume/Downloads/CLAUDE.md`
- [LQL Agent TUI Completion Implementation Plan](../../sources/tmp-personal-project-lql-agent-docs-superpowers-plans-2026-08-04-lql-agent-tui-completion-md.md) — `/Users/svuillaume/tmp/personal_project/lql_agent/docs/superpowers/plans/2026-08-04-lql-agent-tui-completion.md`
- [LQL Agent TUI — Completion Design](../../sources/tmp-personal-project-lql-agent-docs-superpowers-specs-2026-08-04-lql-agent-tui-design-md.md) — `/Users/svuillaume/tmp/personal_project/lql_agent/docs/superpowers/specs/2026-08-04-lql-agent-tui-design.md`
- [LQL Builder](../../sources/tmp-personal-project-converters-readme-md.md) — `/Users/svuillaume/tmp/personal_project/converters/README.md`
- [LQL Datasources Catalog](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-detection-engineering-lql-datasources-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/detection-engineering/lql-datasources.md`
- [LQL Example Queries (Policy Patterns)](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-detection-engineering-lql-example-queries-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/detection-engineering/lql-example-queries.md`
- [LQL Vector DB — Design](../../sources/tmp-personal-project-converters-docs-superpowers-specs-2026-07-17-lql-vector-db-design-md.md) — `/Users/svuillaume/tmp/personal_project/converters/docs/superpowers/specs/2026-07-17-lql-vector-db-design.md`
- [lql-agent](../../sources/tmp-personal-project-lql-agent-readme-md.md) — `/Users/svuillaume/tmp/personal_project/lql_agent/README.md`
- [Memory](../../sources/claude-projects-users-svuillaume-tmp-personal-project-aiagent-memory-memory-md.md) — `/Users/svuillaume/.claude/projects/-Users-svuillaume-tmp-personal-project-aiagent/memory/MEMORY.md`
- [Memory Index](../../sources/claude-projects-users-svuillaume-claude-cnapp-lql-memory-memory-md.md) — `/Users/svuillaume/.claude/projects/-Users-svuillaume-claude-cnapp-lql/memory/MEMORY.md`
- [NL LQL](../../sources/tmp-personal-project-nlp-lql-nlq2lql-readme-md.md) — `/Users/svuillaume/tmp/personal_project/nlp-lql/nlq2lql/README.md`
- [PDF Generation Guide](../../sources/tmp-lacework-lql-pdf-generation-md.md) — `/Users/svuillaume/tmp/lacework_lql/PDF_GENERATION.md`
- [Reference Lql Guide](../../sources/claude-projects-users-svuillaume-tmp-personal-project-aiagent-memory-reference-lql-guide-md.md) — `/Users/svuillaume/.claude/projects/-Users-svuillaume-tmp-personal-project-aiagent/memory/reference_lql_guide.md`
- [Reference Lql Syntax](../../sources/claude-projects-users-svuillaume-claude-cnapp-lql-memory-reference-lql-syntax-md.md) — `/Users/svuillaume/.claude/projects/-Users-svuillaume-claude-cnapp-lql/memory/reference_lql_syntax.md`
- [Route Risk Hunting through on-device WebGPU](../../sources/claude-plans-sunny-toasting-wind-md.md) — `/Users/svuillaume/.claude/plans/sunny-toasting-wind.md`
