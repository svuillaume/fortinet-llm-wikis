---
title: Reference Lql Syntax
path: /Users/svuillaume/.claude/projects/-Users-svuillaume-claude-cnapp-lql/memory/reference_lql_syntax.md
topic: lql
updated: 2026-06-22
size: 3709
sha1: e601f5b1dde9
status: current
---

**Original path:** `/Users/svuillaume/.claude/projects/-Users-svuillaume-claude-cnapp-lql/memory/reference_lql_syntax.md`

**Topic:** [[lql]]

## Summary (first paragraph of source)

- **Case-sensitive identifiers**: `ACCOUNT_ID` ≠ `account_id` - **JSON path**: `FIELD:json.key` — cast with `::String`, `::Number`, `::Timestamp` - **`RLIKE`** is keyword form only: `FIELD RLIKE 'pattern'` (POSIX extended regex) — NOT `RLIKE(field, pattern)` - **Strings**: prefer s-strings `s'literal'` or double-quoted `"string"`. Single-quoted strings are legacy/discouraged. - **`CONTAINS`** is N
