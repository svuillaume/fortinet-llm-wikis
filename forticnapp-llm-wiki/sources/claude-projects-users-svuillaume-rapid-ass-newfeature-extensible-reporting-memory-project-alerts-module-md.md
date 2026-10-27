---
title: Project Alerts Module
path: /Users/svuillaume/.claude/projects/-Users-svuillaume-rapid-ass-newfeature-extensible-reporting/memory/project_alerts_module.md
topic: operations
updated: 2026-04-19
size: 1433
sha1: f98ccca0e4e0
status: current
---

**Original path:** `/Users/svuillaume/.claude/projects/-Users-svuillaume-rapid-ass-newfeature-extensible-reporting/memory/project_alerts_module.md`

**Topic:** [[operations]]

## Summary (first paragraph of source)

**Bad host extraction** (in `modules/alerts.py`): 1. Primary source: `alertInfo.get('subject')` — FortiCNAPP populates this for network alerts 2. Regex fallback on description: `_HOST_RE` matches `bad host <X> at`, `_ON_HOST_RE` matches `running on host <X>`, `_IP_RE` matches bare IPs 3. Port extracted separately with `_PORT_RE` and appended as `host:port`
