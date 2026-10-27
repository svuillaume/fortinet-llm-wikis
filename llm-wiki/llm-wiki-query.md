---
name: llm-wiki-query
description: Answer a question from an LLM wiki instead of re-reading raw documents. Use when the user asks "what does the wiki say about X", "answer from the wiki", or asks a documentation question in a project that has a wiki folder.
---

# LLM Wiki: Query

The goal is fast, grounded answers: read the compiled wiki, not the raw sources, and say where each fact came from.

## Steps

1. **Read `index.md` first.** Pick the few pages that match the question. Do not open the whole wiki.
2. **Read those pages** and follow links only where the answer needs them.
3. **Answer** concisely, citing the page and its source reference for each key fact, e.g. `(topics/waf/rate-limiting.md, src: admin-guide-7.4)`.
4. **Check status.** If a page is `needs-review` or `superseded`, say so plainly and name the newer source if one exists.
5. **Gaps:** if the wiki does not cover it, say "not in the wiki". Only then consult the raw source, and offer to ingest it (llm-wiki-ingest).
6. **Never guess** from memory when the wiki is silent. State what is unknown.

If the answer is new and reusable (a synthesis across pages), offer to file it back as a wiki page and log it in `log.md`.
