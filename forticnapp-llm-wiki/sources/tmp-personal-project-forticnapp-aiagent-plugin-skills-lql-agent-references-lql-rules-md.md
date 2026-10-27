---
title: LQL rules from the FortiCNAPP LQL Reference Guide
path: /Users/svuillaume/tmp/personal_project/forticnapp-aiagent/plugin/skills/lql-agent/references/lql-rules.md
topic: skills
updated: 2026-10-06
size: 3060
sha1: fd7d346b742d
status: current
---

**Original path:** `/Users/svuillaume/tmp/personal_project/forticnapp-aiagent/plugin/skills/lql-agent/references/lql-rules.md`

**Topic:** [[skills]]

## Summary (first paragraph of source)

- Use `return distinct` with `array_to_rows` or MANY joins, and return only root or ONE-connected columns (policy-evaluation limit). - `(A with B) with C` is rejected; fork with `A with (B, C)`. `with` is a left outer join. - Missing attribute: `not value_exists(x.RESOURCE_CONFIG:Field)`. Null tests: `IS NULL`, never `= null`. - JSON booleans in `RESOURCE_CONFIG` are compared as strings (`= 'true'
