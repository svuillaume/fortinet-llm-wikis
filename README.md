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

### Prerequisites

| Requirement | Needed for | How |
|---|---|---|
| [Git](https://git-scm.com/) + access to the repo | Everyone | `git clone` (step 1) |
| [Claude Code](https://claude.com/claude-code) | Claude workflow | Install via `npm install -g @anthropic-ai/claude-code` or the native installer |
| **llm-wiki skills** | `/llm-wiki-query` etc. | Not on a public marketplace — copy the `llm-wiki*` skill folders into `~/.claude/skills/` (see below) |
| Any other LLM agent with file access (Codex, OpenAI-compatible, …) | Generic workflow | No extra install — just a system prompt (see step 4) |

**Install the llm-wiki skills (Claude Code only)**

The skills (`llm-wiki`, `llm-wiki-query`, `llm-wiki-ingest`, `llm-wiki-lint`,
`llm-wiki-logs`, `llm-wiki-stats`, `llm-wiki-review`) are distributed as plain
folders. On a machine that doesn't have them:

```bash
# from a machine that already has them, or any copy of the skill folders:
mkdir -p ~/.claude/skills
cp -R <path-to>/llm-wiki* ~/.claude/skills/
```

Restart Claude Code. Verify with `/help` — the `llm-wiki-*` commands should be
listed. (Without the skills the wiki still works: just ask questions directly
and the agent will read the markdown — skills just standardize the workflow.)

### Step 1 — Clone the repo

```bash
git clone https://github.com/svuillaume/fortinet-llm-wikis.git
cd fortinet-llm-wikis
```

### Step 2 — Open it in your AI assistant

Open the repo folder in your agent of choice:

- **Claude Code**: `claude` from inside the repo (or open the folder in
  Claude Code desktop/IDE).
- **Codex or any other agent**: point it at the repo directory and give it
  file-reading access.

### Step 3 — Ask your question

In Claude Code, use the wiki query skill:

```
/llm-wiki-query What is FortiCNAPP for non-technical audiences?
/llm-wiki-query How does FortiCASB-SSPM revoke third-party app access?
/llm-wiki-query What are the FortiCASB SKUs and list prices?
```

Or just ask naturally — the agent will start at the relevant wiki's
`index.md`, follow links to topic pages, and cite sources with
`[src: <stub>]` so you can verify.

**Tips**

- Name the product so the agent picks the right wiki: FortiCNAPP →
  `forticnapp-llm-wiki/`, FortiCASB → `forticasb-llm-wiki/`.
- If a page says `needs-review`, the wiki tells you which documents
  disagree — treat the answer as disputed.
- For other workflows: `/llm-wiki-ingest` (add documents),
  `/llm-wiki-lint` (health check), `/llm-wiki-stats` (coverage report).

### Step 4 — Using with OpenAI or other LLMs

LLM wikis are just markdown, so any model with file access works — no skills
needed:

1. Upload the wiki folder (or give the agent file access to it).
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