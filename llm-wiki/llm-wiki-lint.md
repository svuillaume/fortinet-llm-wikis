---
name: llm-wiki-lint
description: Audit an LLM wiki for staleness, broken links, orphan pages, conflicts and missing source references. Use when the user says "lint the wiki", "is the wiki current", "health check the wiki", or before sharing a wiki with others.
---

# LLM Wiki: Lint

Read-only audit. Report findings; fix only what the user approves.

## Checks

| Check | How |
|---|---|
| Broken links | Every relative link and `[src: ...]` reference resolves to a file |
| Orphans | Every page appears in `index.md` and has at least one inbound link |
| Missing sources | Every topic page lists `sources:` and cites them in the body |
| Stale pages | `updated` older than the newest linked source, or source file changed (hash differs) |
| Superseded | Pages still citing a `superseded` source |
| Conflicts | Pages with `status: needs-review`, or the same fact stated differently across pages |
| Index drift | `index.md` entries with no page, or pages with no entry |
| Frontmatter | `title`, `summary`, `sources`, `updated`, `status` all present |

## Output

A short report: counts per check, then a table of findings (page, issue, suggested fix), ordered by severity (conflicts and broken links first). Offer to apply the fixes and log them in `log.md`.
