---
title: Task 5 correction: FortiCNAPP auth fix report
path: /Users/svuillaume/tmp/personal_project/rca_beta_initiative/.claude/worktrees/forticnapp-poc/.superpowers/sdd/task-5-auth-fix-report.md
topic: rapid-cloud-assessment
updated: 2026-07-18
size: 6322
sha1: 79683686b0c7
status: current
---

**Original path:** `/Users/svuillaume/tmp/personal_project/rca_beta_initiative/.claude/worktrees/forticnapp-poc/.superpowers/sdd/task-5-auth-fix-report.md`

**Topic:** [[rapid-cloud-assessment]]

## Summary (first paragraph of source)

The original `client.ts` assumed a single static header, `X-LW-TOKEN: <apiKey>`, sent on every request. This was based on an illustrative example in a planning doc, not the real API. Per Fortinet's official "Lacework FortiCNAPP 26.2.0 API Reference," the real flow is:
