---
title: Task 5 Report: FortiCNAPP API client with retry logic
path: /Users/svuillaume/tmp/personal_project/rca_beta_initiative/.claude/worktrees/forticnapp-poc/.superpowers/sdd/task-5-report.md
topic: rapid-cloud-assessment
updated: 2026-07-18
size: 6728
sha1: e33ab396c984
status: current
---

**Original path:** `/Users/svuillaume/tmp/personal_project/rca_beta_initiative/.claude/worktrees/forticnapp-poc/.superpowers/sdd/task-5-report.md`

**Topic:** [[rapid-cloud-assessment]]

## Summary (first paragraph of source)

- `server/src/forticnapp/client.ts` — `FortiCNAPPClient` class wrapping an axios instance: - Constructor takes `{ tenantUrl, apiKey }`, creates an axios instance with `baseURL` = `${tenantUrl}/api/v2`, a 30s timeout, and the `X-LW-TOKEN` header set to the API key. - A response interceptor implements retry-on-429/5xx: up to 3 retries, with a `100 * retryCount` ms backoff delay (deliberately fast fo
