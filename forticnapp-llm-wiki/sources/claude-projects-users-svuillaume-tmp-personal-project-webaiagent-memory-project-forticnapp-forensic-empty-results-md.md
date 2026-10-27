---
title: Project Forticnapp Forensic Empty Results
path: /Users/svuillaume/.claude/projects/-Users-svuillaume-tmp-personal-project-webaiagent/memory/project_forticnapp_forensic_empty_results.md
topic: mcp-and-agents
updated: 2026-09-11
size: 2408
sha1: 829c594e0055
status: current
---

**Original path:** `/Users/svuillaume/.claude/projects/-Users-svuillaume-tmp-personal-project-webaiagent/memory/project_forticnapp_forensic_empty_results.md`

**Topic:** [[mcp-and-agents]]

## Summary (first paragraph of source)

RESOLVED. `/mcp/forensic`'s `forticnapp_inventory_search` tool call was returning 0 results for real data (e.g. "list s3 in ca-central-1" against tenant `partner-demo`) because of two compounding FortiCNAPP `/api/v2/Inventory/search` gotchas the agent-loop system prompt didn't warn about:
