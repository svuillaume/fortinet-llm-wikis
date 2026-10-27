---
title: LQL agent project instructions
path: /Users/svuillaume/Downloads/CLAUDE.md
topic: lql
updated: 2026-10-05
size: 1550
sha1: 794cdfe83555
status: current
---

**Original path:** `/Users/svuillaume/Downloads/CLAUDE.md`

**Topic:** [[lql]]

## Summary (first paragraph of source)

For any request to write, fix or test FortiCNAPP LQL in this folder, use ONLY these (not `lql-tester`, `lql-builder` or other LQL skills): - One datasource: the `lql-agent` sub-agent. - Two or more resource types (for example EC2 -> instance profile -> IAM role -> policy): the `lql-orchestrator` skill. It runs in this conversation, launches `lql-datasource-specialist` agents in parallel, composes 
