---
name: llm-wiki
description: Build or extend an LLM wiki, a persistent folder of linked markdown pages compiled from source documents (docx, pptx, pdf, md, txt, web pages, transcripts). Use when the user says "build a wiki", "llm-wiki", "collect docs into a knowledge base", or wants documentation consolidated so AI answers stop starting from scratch. For adding one source use llm-wiki-ingest, for answering use llm-wiki-query, for audits use llm-wiki-lint.
---

# LLM Wiki

An LLM wiki is a curated, compiled layer between raw documents and the AI. Raw sources stay untouched; the wiki holds distilled, linked, source-traced pages that the AI reads first.

## Layout

```
wiki/
├── index.md          # catalog: every page, one line each, grouped by topic
├── log.md            # append-only: date, action, source, pages touched
├── sources/          # one stub per raw document (title, path/URL, date, hash, status)
└── topics/<area>/<page>.md
```

## Page format

Every topic page starts with frontmatter:

```
---
title: <short title>
summary: <one sentence>
sources: [<source stub names>]
updated: <YYYY-MM-DD>
status: current | needs-review | superseded
---
```

Body rules:
- State facts, procedures and decisions. No filler.
- Every claim that comes from a document ends with a source reference, e.g. `[src: install-guide-v3]`.
- Link related pages with relative markdown links. Never leave an orphan page.
- If two sources disagree, record both, name the newer one, and set `status: needs-review`. Never silently pick one.
- Never invent facts. Unknown means "not found in sources".

## Workflow (collect first)

1. **Scope:** confirm which folders or files are in scope and any to exclude. Work on copies; never edit originals.
2. **Inventory:** list candidate files with type, size and modified date. Extract text per type (use the docx, pptx, pdf skills where available).
3. **Propose structure:** draft `index.md` and the topic tree, and show it to the user before bulk writing unless they asked you to proceed.
4. **Compile:** write source stubs first, then topic pages, then `index.md` and `log.md`.
5. **Check:** run the llm-wiki-lint checks and report counts: pages, sources, conflicts, orphans.
6. **Deliver:** hand over the wiki folder (zip if remote) with a short summary of what was covered and what was skipped.

Technical content should stay neutral and engineering-focused: architecture, behavior, procedures, outcomes.
