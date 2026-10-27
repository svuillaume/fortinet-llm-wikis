# my-llm-wikis

> LLM-compiled knowledge bases for Fortinet cloud-security products.

An **LLM wiki** is a markdown wiki built by an LLM agent over a corpus of raw
documents (admin guides, user guides, internal notes, blogs, Terraform docs…).
It is *not* a search index — every page is synthesized, cross-linked, and
source-attributed, so an LLM can answer questions from it with high fidelity
instead of guessing from unstructured dumps.

Each wiki is self-contained and portable: plain markdown, no database, no
build step. Point any agent (Claude Code, Codex, an OpenAI-compatible LLM
with file access) at the folder and start asking.

## Available wikis

| Wiki | Product | Coverage |
|---|---|---|
| [`forticnapp-llm-wiki/`](forticnapp-llm-wiki/index.md) | **FortiCNAPP** (ex-Lacework CNAPP) | ~760 source documents: product overview, CSPM, CWPP, CIEM, DSPM, code security, Terraform, LQL, MCP/agents, rapid cloud assessment, operations, runbooks. |
| [`forticasb-llm-wiki/`](forticasb-llm-wiki/index.md) | **FortiCASB / FortiCASB-SSPM** | 26 source documents: product & naming/rebrand, SSPM user guide (Feb 2026), legacy admin guide, competitive & market analysis. |

## Anatomy of a wiki

```
<product>-llm-wiki/
├── index.md    ← start here: full topic map with per-page summaries
├── log.md      ← ingest/changelog history
├── sources/    ← one stub per raw document (frontmatter + sha1 of original)
└── topics/     ← synthesized knowledge pages, organized by area
```

Conventions:

- **Start at `index.md`** — it maps every topic and what each page covers.
- Every claim is attributed to a source stub: `[src: <source>]`.
- Pages marked `needs-review` record places where sources disagree.
- Originals are never modified; stubs store path + sha1 so staleness is detectable.

## How to use it

### Claude Code (recommended)

1. Open the repo (or a wiki folder) in Claude Code.
2. Ask questions directly — e.g. *"How does FortiCASB-SSPM workflows work?"*
   or *"What CSPM policy types does FortiCNAPP support?"*. The agent starts
   at `index.md`, follows links to the relevant topic pages, and cites sources.
3. Optional: for repeated workflows, invoke the `llm-wiki` skills
   (`llm-wiki-query`, `llm-wiki-ingest`, `llm-wiki-lint`, `llm-wiki-stats`)
   — query, extend, health-check, and report on the wiki respectively.

Tips:

- For multi-part research, ask for answers with `[src:]` citations so you can
  verify against `sources/`.
- If a page says `needs-review`, treat the answer as disputed — the wiki will
  tell you which documents conflict.

### OpenAI / other LLMs

LLM wikis are just markdown, so any model with file access works:

1. Give the model the wiki folder (upload the files, or run an agent with a
   file-reading tool over the directory).
2. Instruct it:

   > "Use `<product>-llm-wiki/` as the knowledge base. Start from
   > `index.md`, follow links to the topic pages that answer the user's
   > question, and cite the `[src: ...]` stubs in your answer. If a page is
   > marked `needs-review`, mention the disagreement."

3. For a quick single-session setup, `index.md` + the specific topic pages it
   links to are usually all you need in context — load them first, then let
   the model pull in more pages as needed.

## Maintenance

| Task | What to do |
|---|---|
| Add new documents | Drop them in the corpus and ingest (see `llm-wiki-ingest` skill) |
| Check freshness | `log.md` records the last ingest; source stubs carry `sha1` of originals |
| Health check | `llm-wiki-lint` skill (broken links, orphaned sources, stale pages) |
| Stats | `llm-wiki-stats` skill (page counts, coverage, gaps) |

---

*Both wikis were compiled on this machine from local document corpora;
last ingest dates are in each wiki's `log.md`.*