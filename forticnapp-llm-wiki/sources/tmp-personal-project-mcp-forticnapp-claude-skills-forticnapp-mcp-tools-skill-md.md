---
title: FortiCNAPP MCP Tools
path: /Users/svuillaume/tmp/personal_project/mcp_forticnapp/.claude/skills/forticnapp-mcp-tools/SKILL.md
topic: skills
updated: 2026-07-07
size: 5511
sha1: 077b4a2a0d8c
status: current
---

**Original path:** `/Users/svuillaume/tmp/personal_project/mcp_forticnapp/.claude/skills/forticnapp-mcp-tools/SKILL.md`

**Topic:** [[skills]]

## Summary (first paragraph of source)

The `mcp__forticnapp__*` tools are generated from `lw.yaml` (FortiCNAPP/Lacework API 2.0) and are typically deferred — load a tool's schema with `ToolSearch` (`select:<tool_name>`, comma-join multiple) before calling it. Two things trip up first calls: (1) guessing `Inventory/search`'s `dataset` param as a resource-type selector, and (2) guessing filter operator names instead of using the real enu
