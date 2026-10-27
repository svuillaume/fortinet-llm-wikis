---
title: Feedback Env Only Credentials
path: /Users/svuillaume/.claude/projects/-Users-svuillaume-tmp-personal-project-mcp-forticnapp/memory/feedback_env_only_credentials.md
topic: mcp-and-agents
updated: 2026-07-07
size: 1387
sha1: d37306668f3f
status: current
---

**Original path:** `/Users/svuillaume/.claude/projects/-Users-svuillaume-tmp-personal-project-mcp-forticnapp/memory/feedback_env_only_credentials.md`

**Topic:** [[mcp-and-agents]]

## Summary (first paragraph of source)

`.env` is the only source of truth for FortiCNAPP API keys/credentials in this project. Never document or add an inline `env` block with `FORTICNAPP_KEY_ID`/`FORTICNAPP_API_SECRET`/etc. in a client config file (`claude_desktop_config.json`, `.mcp.json`, or similar), even as a documented "fallback" option.
