---
title: Task 5/6/7 correction: rework around real FortiCNAPP endpoints
path: /Users/svuillaume/tmp/personal_project/rca_beta_initiative/.claude/worktrees/forticnapp-poc/.superpowers/sdd/task-5-6-7-real-endpoints-report.md
topic: rapid-cloud-assessment
updated: 2026-07-18
size: 6511
sha1: 4f25ef1f4e54
status: current
---

**Original path:** `/Users/svuillaume/tmp/personal_project/rca_beta_initiative/.claude/worktrees/forticnapp-poc/.superpowers/sdd/task-5-6-7-real-endpoints-report.md`

**Topic:** [[rapid-cloud-assessment]]

## Summary (first paragraph of source)

Live probing against a real FortiCNAPP tenant showed the 4 endpoints the master spec assumed (`ComplianceEvaluations`, `Vulnerabilities`, `CloudTrailExceptions`, `IAMEntities`) all return `403 Unrecognized url`. Two real endpoints were confirmed instead:
