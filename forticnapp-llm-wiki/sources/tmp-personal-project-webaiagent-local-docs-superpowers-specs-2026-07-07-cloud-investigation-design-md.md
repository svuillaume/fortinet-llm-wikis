---
title: Cloud Investigation (FortiCNAPP MCP integration) — Design
path: /Users/svuillaume/tmp/personal_project/webaiagent_local/docs/superpowers/specs/2026-07-07-cloud-investigation-design.md
topic: mcp-and-agents
updated: 2026-08-12
size: 12375
sha1: 45d889603369
status: current
---

**Original path:** `/Users/svuillaume/tmp/personal_project/webaiagent_local/docs/superpowers/specs/2026-07-07-cloud-investigation-design.md`

**Topic:** [[mcp-and-agents]]

## Summary (first paragraph of source)

Add a "Cloud Investigation" tab to the existing Risk Hunting drawer in the Chrome extension. The user types a free-text investigation objective (e.g. "find EC2 instances with public S3 buckets attached"); `serve.py` runs a server-side, multi-step LLM agent loop that calls read-only FortiCNAPP tools exposed by the `mcp_forticnapp` MCP server (a separate, already-working project at `~/tmp/personal_p
