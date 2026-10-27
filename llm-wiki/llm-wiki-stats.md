---
name: llm-wiki-stats
description: "Show how large an LLM wiki has become: size, file counts per folder, growth since the first build, largest topic pages, consistency checks, and the most recently added references. Use when the user asks \"wiki stats\", \"how big is the wiki\", \"how large has the wiki become\", or \"what was added recently\"."
---

# LLM Wiki: Stats

Read-only report on the size and recent growth of an llm-wiki folder. Never modify the wiki.

## Steps

1. **Find the wiki root:** the folder that contains `index.md`, `log.md`, `sources/` and `topics/`. Use the path the user gives, otherwise the current folder, otherwise ask. If the wiki is on the user's computer, run the script there with the device shell; do not stage the whole wiki.
2. **Run the script below** with the root as its only argument. It only reads files.
3. **Show the report in the chat** in the layout under "Output", then save the same text as `wiki-stats-YYYY-MM-DD.md` and send it to the user (outside the wiki folder, so the wiki is not changed).
4. **Add one or two sentences of reading:** only what the numbers show (a page that dominates the rest, a count mismatch, a fast-growing topic). Offer a follow-up (split a large page, run llm-wiki-lint) but do not do it unasked.

## Script

```python
import os, re, sys, statistics, datetime
root = os.path.abspath(sys.argv[1] if len(sys.argv) > 1 else '.')
for need in ('index.md', 'log.md', 'sources', 'topics'):
    if not os.path.exists(os.path.join(root, need)):
        sys.exit('Not an llm-wiki root (missing %s): %s' % (need, root))

def walk(sub=''):
    base = os.path.join(root, sub)
    for d, dirs, files in os.walk(base):
        dirs[:] = [x for x in dirs if x != '.claude']
        for f in files:
            fp = os.path.join(d, f)
            if os.path.isfile(fp):  # skips dangling symlinks and special files
                yield fp

def human(n):
    if n == 0: return 'empty'
    for u in ('B', 'KB', 'MB', 'GB'):
        if n < 1024 or u == 'GB': return ('%d %s' % (n, u)) if u == 'B' else ('%.1f %s' % (n, u) if u == 'MB' else '%.0f %s' % (n, u))
        n /= 1024.0

def words(p):
    try: return len(open(p, encoding='utf-8', errors='replace').read().split())
    except OSError: return 0

all_files = list(walk())
total_bytes = sum(os.path.getsize(p) for p in all_files)
md_live = [p for p in all_files if p.endswith('.md') and '/_archived/' not in p and '/_to_delete/' not in p]
total_words = sum(words(p) for p in md_live)
out = []
out.append('The wiki is about %s across %d files, with roughly %s words of markdown.\n' % (human(total_bytes), len(all_files), format(int(round(total_words, -3)), ',')))

out.append('| Part | Files | Size |\n|---|---|---|')
labels = {'sources': 'sources/ (one stub per document)', 'topics': 'topics/ (%d topic pages)', 'skills': 'skills/ (verbatim skill copies)', '_archived': '_archived/', '_to_delete': '_to_delete/'}
for d in ('sources', 'topics', 'skills', '_archived', '_to_delete'):
    fs = list(walk(d)) if os.path.isdir(os.path.join(root, d)) else []
    label = labels[d]
    if d == 'topics': label = label % len([p for p in fs if p.endswith('/index.md')])
    out.append('| %s | %d | %s |' % (label, len(fs), human(sum(os.path.getsize(p) for p in fs))))

# ---- growth
log = open(os.path.join(root, 'log.md'), encoding='utf-8', errors='replace').read().splitlines()
entries = [l for l in log if re.match(r'^- 20\d\d-\d\d-\d\d', l)]
first = next((l for l in entries if re.search(r'(\d+) source stubs', l)), None)
m_idx = re.search(r'over \*\*(\d+)\*\*', open(os.path.join(root, 'index.md'), encoding='utf-8', errors='replace').read())
claimed = int(m_idx.group(1)) if m_idx else None
stubs = sorted(os.listdir(os.path.join(root, 'sources')))
out.append('')
if first and claimed:
    d0 = re.match(r'^- (20\d\d-\d\d-\d\d)', first).group(1)
    n0 = int(re.search(r'(\d+) source stubs', first).group(1))
    days = (datetime.date.today() - datetime.date.fromisoformat(d0)).days
    out.append('**Growth:** the initial build on %s had %d source stubs. Today the index claims %d, so about %d sources were added in %d day%s (the log has %d entries).' % (d0, n0, claimed, claimed - n0, days, '' if days == 1 else 's', len(entries)))
else:
    out.append('**Growth:** the log has %d entries; no initial stub count was found to compare against.' % len(entries))

# ---- topic pages
tp = []
for p in walk('topics'):
    if p.endswith('/index.md'):
        tp.append((os.path.getsize(p), words(p), os.path.basename(os.path.dirname(p))))
tp.sort(reverse=True)
out.append('\n**Largest topic pages:**\n')
for b, w, n in tp[:6]:
    out.append('- `%s`: %s, about %s words' % (n, human(b), format(int(round(w, -2)), ',')))
sm = tp[-3:]
out.append('\nSmallest: ' + ', '.join('`%s` (%s)' % (n, human(b)) for b, w, n in reversed(sm)) + '.')
if tp:
    med = statistics.median(b for b, w, n in tp)
    big = ['`%s`' % n for b, w, n in tp if b > 3 * med]
    if len(big) == 1:
        out.append('Watch: %s is more than 3x the median topic page (%s), so reading it in full costs the most per query.' % (big[0], human(med)))
    elif big:
        out.append('Watch: %s and %s are each more than 3x the median topic page (%s), so reading them in full costs the most per query.' % (', '.join(big[:-1]), big[-1], human(med)))

# ---- consistency
topic_text = ' '.join(open(p, encoding='utf-8', errors='replace').read() for p in walk('topics') if p.endswith('.md'))
unref = [s for s in stubs if s.endswith('.md') and s[:-3] not in topic_text]
out.append('\n**Consistency:**')
if claimed is not None and claimed != len(stubs):
    out.append('- The index header says %d sources, but `sources/` holds %d files.' % (claimed, len(stubs)))
else:
    out.append('- Index count matches `sources/` (%d).' % len(stubs))
out.append('- %d stub%s not referenced from any topic page%s' % (len(unref), ' is' if len(unref) == 1 else 's are', (': ' + ', '.join('`%s`' % s for s in unref[:8]) + (' ...' if len(unref) > 8 else '')) if unref else '.'))
broken = []
for d, dirs, files in os.walk(root):
    dirs[:] = [x for x in dirs if x != '.claude']
    for f in files + dirs:
        fp = os.path.join(d, f)
        if os.path.islink(fp) and not os.path.exists(fp): broken.append(os.path.relpath(fp, root))
if broken: out.append('- Dangling symlink%s (target missing): %s' % ('' if len(broken) == 1 else 's', ', '.join('`%s`' % b for b in broken[:5])))
out.append('- A lint pass (llm-wiki-lint) checks links, hashes and conflicts; this report does not.')

# ---- recently added
def meta(p):
    t = open(p, encoding='utf-8', errors='replace').read(2500)
    g = lambda k: (re.search(r'^%s:\s*(.+)$' % k, t, re.M) or [None, ''])[1].strip()
    return g('title'), g('topic'), g('updated'), g('sha1')
recent = sorted((os.path.join(root, 'sources', s) for s in stubs if s.endswith('.md') and os.path.isfile(os.path.join(root, 'sources', s))), key=os.path.getmtime, reverse=True)[:10]
out.append('\n**Recently added or updated references (newest first):**\n')
out.append('| Date | Topic | Reference | Stub |\n|---|---|---|---|')
for p in recent:
    t, tp_, up, sha = meta(p)
    date = up or datetime.date.fromtimestamp(os.path.getmtime(p)).isoformat()
    out.append('| %s | %s | %s | `%s` |' % (date, tp_ or '-', (t or os.path.basename(p))[:80], os.path.basename(p)[:-3][:60]))
out.append('\nLast log entries:\n')
for l in entries[-5:]:
    out.append('- ' + l[2:][:220])
print('\n'.join(out))
```

## Output

Keep this order: headline sentence, folder table, Growth, Largest topic pages, Consistency, Recently added references, last log entries. Round words to the nearest thousand (whole wiki) or hundred (one page). Use "about" only for rounded numbers. State any figure the script could not compute (for example no initial build count) as "not available", never an estimate.

## Notes

- Sizes are real file bytes, not disk usage (`du` rounds every small file up to a block and reports far larger totals for a wiki of many small stubs). Never quote a `du` figure in this report.
- "Recently added" is ordered by file modification time, so a stub that was only edited also appears; its `updated:` date is shown when present.
- Counts of sources and words exclude `.claude/`; word counts also exclude `_archived/` and `_to_delete/`. Dangling symlinks are not counted as files and are listed under Consistency.
- Never delete, move or edit wiki files from this skill. Suggestions (split a page, lint, ingest) are offered, not performed.
