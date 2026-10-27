---
name: llm-wiki-ingest
description: Add or refresh one or more source documents in an existing LLM wiki. Use when the user says "ingest this doc", "add this to the wiki", "update the wiki with the new version", or drops a new file/URL/transcript into a wiki project.
---

# LLM Wiki: Ingest

Prerequisite: a wiki folder following the llm-wiki layout (`index.md`, `log.md`, `sources/`, `topics/`). If none exists, use the llm-wiki skill first.

## Steps

1. **Fingerprint the source:** record title, path or URL, modified date and a content hash. If a stub with the same hash exists, stop and report "already ingested".
2. **New version of a known source?** Keep the old stub, set its status to `superseded`, link it to the new one, and mark every page citing it `needs-review`.
3. **Extract text** with the right skill for the file type. Note anything lost (images, tables, speaker notes, video without transcript).
4. **Decide placement:** update existing pages where the topic already exists; create a new page only for genuinely new topics. Prefer fewer, richer pages.
5. **Write changes** with source references on every sourced claim. Flag contradictions with existing pages instead of overwriting them.
6. **Update bookkeeping:** `sources/<stub>.md`, `index.md` entries, and one line in `log.md`: `YYYY-MM-DD | ingest | <source> | <pages touched>`.
7. **Report:** pages created, pages updated, conflicts found, content that could not be extracted.

Never modify the original document.
