---
title: Running forticnapp-mcp against a local Ollama model
path: /Users/svuillaume/tmp/personal_project/webaiagent/vendor/mcp_forticnapp/mcp_ollama.md
topic: mcp-and-agents
updated: 2026-08-14
size: 10199
sha1: 8d36c012f026
status: current
---

**Original path:** `/Users/svuillaume/tmp/personal_project/webaiagent/vendor/mcp_forticnapp/mcp_ollama.md`

**Topic:** [[mcp-and-agents]]

## Summary (first paragraph of source)

Standalone setup that connects this vendored FortiCNAPP MCP server to a local Ollama model instead of Claude, using [mcphost](https://github.com/mark3labs/mcphost) as the bridge. Lives entirely under `vendor/mcp_forticnapp/` and does not touch `serve.py` or the extension — the main project's Cloud Investigation feature (`POST /mcp/investigate`) is separate and Claude-only (hardcoded gate at `serve
