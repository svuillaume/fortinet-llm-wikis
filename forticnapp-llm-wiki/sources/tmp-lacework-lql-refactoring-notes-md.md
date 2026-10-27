---
title: Lacework LQL Script - Refactoring Notes
path: /Users/svuillaume/tmp/lacework_lql/REFACTORING_NOTES.md
topic: lql
updated: 2026-01-14
size: 4393
sha1: 7e4d2b5c2074
status: current
---

**Original path:** `/Users/svuillaume/tmp/lacework_lql/REFACTORING_NOTES.md`

**Topic:** [[lql]]

## Summary (first paragraph of source)

- **Removed hardcoded credentials**: API keys now use environment variables - **Prevents accidental commits**: Credentials won't be leaked in version control - **Required validation**: Script fails fast if credentials are missing
