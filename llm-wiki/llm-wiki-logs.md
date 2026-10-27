---
name: llm-wiki-logs
description: "List the references added to an LLM wiki in the last 30 days (or N days): when each was added, how it arrived, where and when it was indexed, and by whom if recorded. Use when the user asks \"wiki logs\", \"what was added in the last 30 days\", \"recent ingests\", or \"who added what to the wiki\"."
---

# LLM Wiki: Logs

Read-only report of recent additions to an llm-wiki folder. Never modify the wiki.

## Steps

1. **Find the wiki root:** the folder that contains `index.md`, `log.md`, `sources/` and `topics/`. Use the path the user gives, otherwise the current folder, otherwise ask. If the wiki is on the user's computer, run the script there with the device shell; do not stage the whole wiki.
2. **Choose the window:** 30 days unless the user names another ("last 7 days" -> 7). Choose the row limit for the newest-references table: 40 unless the user asks for more or all.
3. **Run the script below:** `python3 wikilogs.py <root> <days> <limit>`. It only reads files.
4. **Show the report in the chat** in the order the script prints, then save the same text as `wiki-logs-YYYY-MM-DD.md` and send it to the user (outside the wiki folder, so the wiki is not changed).
5. **Add one or two sentences of reading:** only what the numbers show (a bulk build that dominates the window, references not indexed, entries with no dated log line). Offer follow-ups (run llm-wiki-lint, add the missing index entry) but do not do them unasked.

## What each column means

- **Added:** the date the stub file was created (file creation time where the system records it, otherwise last modified). This is when the reference entered the wiki, not the date of the source document.
- **Via:** how it arrived, from the stub: `chat upload` (file attached in chat), `chat paste` (text pasted or stated in chat), `local file`, `web`, or `other`.
- **Indexed in:** the topic pages whose text links or cites the stub. `NOT INDEXED` means no topic page mentions it.
- **Indexed when:** the date of the first `log.md` line that names the stub (a `sources/prefix-*` pattern also matches). `no dated log entry` means it is indexed in a topic page but no log line names it (typical of the initial bulk build or of a batch covered by one log line).
- **By:** the author of the git commit that added the stub if the wiki is a git repository, or an `author:` field in the stub. Otherwise `not recorded`. Never guess a name from the file owner or the channel.

## Script

```python
import os, re, sys, datetime, subprocess, fnmatch
root = os.path.abspath(sys.argv[1] if len(sys.argv) > 1 else '.')
days = int(sys.argv[2]) if len(sys.argv) > 2 else 30
limit = int(sys.argv[3]) if len(sys.argv) > 3 else 40
for need in ('index.md', 'log.md', 'sources', 'topics'):
    if not os.path.exists(os.path.join(root, need)):
        sys.exit('Not an llm-wiki root (missing %s): %s' % (need, root))
today = datetime.date.today(); cutoff = today - datetime.timedelta(days=days)
rd = lambda p: open(p, encoding='utf-8', errors='replace').read()
cut = lambda s, n: s if len(s) <= n else s[:n - 1].rstrip() + '...'

# ---- log entries
entries = []
for l in rd(os.path.join(root, 'log.md')).splitlines():
    m = re.match(r'^- (\d{4}-\d{2}-\d{2})\s*(?:\||\u2014|-)\s*(.*)$', l)
    if not m: continue
    d = datetime.date.fromisoformat(m.group(1)); text = m.group(2)
    parts = [x.strip() for x in text.split(' | ')]
    am = re.search(r'(ingest-update|ingest|lint-fix|lint|consolidate|restructure|archive|synthesis|initial build)', parts[0].lower() if len(parts) > 1 else text.lower())
    action = am.group(1) if am else 'other'
    subject = parts[1] if len(parts) > 1 else text
    pages = parts[2] if len(parts) > 2 else ''
    low = text.lower()
    via = ('chat upload' if 'upload' in low else 'chat paste' if ('pasted' in low or 'inline' in low or 'user-pasted' in low or 'user clarification' in low or 'user statement' in low)
           else 'local files' if 'local repo' in low else 'wiki build' if action in ('initial build', 'synthesis', 'lint') else '-')
    entries.append((d, action, subject, pages, via, text))
win_entries = [e for e in entries if e[0] >= cutoff]

# ---- stubs
topic_text = {}
for d, _, fs in os.walk(os.path.join(root, 'topics')):
    for f in fs:
        if f.endswith('.md'):
            topic_text[os.path.basename(d) if f == 'index.md' else os.path.join(os.path.basename(d), f)] = rd(os.path.join(d, f))
has_git = os.path.isdir(os.path.join(root, '.git'))
def git_author(rel):
    try:
        r = subprocess.run(['git', '-C', root, 'log', '--diff-filter=A', '--format=%an', '--', rel], capture_output=True, text=True, timeout=10)
        a = [x for x in r.stdout.split('\n') if x.strip()]
        return a[-1] if a else None
    except Exception: return None
rows = []
for s in sorted(os.listdir(os.path.join(root, 'sources'))):
    p = os.path.join(root, 'sources', s)
    if not (s.endswith('.md') and os.path.isfile(p)): continue
    t = rd(p)[:2500]
    g = lambda k: (re.search(r'^%s:\s*(.+)$' % k, t, re.M) or [None, ''])[1].strip()
    st = os.stat(p)
    d = datetime.date.fromtimestamp(getattr(st, 'st_birthtime', st.st_mtime))
    path = g('path'); inline = g('inline').lower() == 'true'
    ch = ('chat upload' if inline and 'upload' in path.lower() else 'chat paste' if inline else 'web' if path.startswith('http') else
          'local file' if path.startswith(('/', '~')) else 'other')
    slug = s[:-3]
    topics = [k.split('/')[0] for k, v in topic_text.items() if slug in v]
    def hit(e):
        if slug in e[5]: return True
        return any(fnmatch.fnmatch('sources/' + slug + '.md', t) for t in re.findall(r'sources/[\w*.-]+', e[5]))
    logd = next((e[0] for e in sorted(entries) if hit(e)), None)
    by = g('author') or (git_author('sources/' + s) if has_git else None) or 'not recorded'
    rows.append(dict(d=d, slug=slug, title=g('title') or slug, ch=ch, topics=sorted(set(topics)), logd=logd, by=by))
win = sorted([r for r in rows if r['d'] >= cutoff], key=lambda r: (r['d'], r['slug']), reverse=True)

out = []
out.append('**References added in the last %d days** (%s to %s): %d of %d stubs, %d log entries.\n' % (days, cutoff, today, len(win), len(rows), len(win_entries)))
out.append('**Log timeline**\n\n| Date | Action | What | Pages touched | Via |\n|---|---|---|---|---|')
for e in sorted(win_entries, key=lambda e: e[0], reverse=True):
    out.append('| %s | %s | %s | %s | %s |' % (e[0], e[1], cut(e[2], 90).replace('|', '/'), cut(e[3], 70).replace('|', '/') or '-', e[4]))
chans = sorted(set(r['ch'] for r in win))
out.append('\n**Added per day and channel**\n\n| Date | ' + ' | '.join(chans) + ' | Total |\n|---|' + '---|' * (len(chans) + 1))
for d in sorted(set(r['d'] for r in win), reverse=True):
    c = [sum(1 for r in win if r['d'] == d and r['ch'] == x) for x in chans]
    out.append('| %s | %s | %d |' % (d, ' | '.join(map(str, c)), sum(c)))
out.append('\n**Newest %d references**\n\n| Added | Reference | Via | Indexed in | Indexed when | By |\n|---|---|---|---|---|---|' % min(limit, len(win)))
for r in win[:limit]:
    ix = ', '.join(r['topics'][:2]) if r['topics'] else 'NOT INDEXED'
    when = str(r['logd']) if r['logd'] else ('no dated log entry' if r['topics'] else '-')
    out.append('| %s | %s | %s | %s | %s | %s |' % (r['d'], cut(r['title'], 70).replace('|', '/'), r['ch'], ix, when, r['by']))
if len(win) > limit: out.append('\n%d more not shown (see the per-day table above).' % (len(win) - limit))
noidx = [r for r in win if not r['topics']]
out.append('\n**Gaps**\n')
out.append('- %d reference(s) in the window are not linked from any topic page%s' % (len(noidx), (': ' + ', '.join('`%s`' % r['slug'] for r in noidx[:6])) if noidx else '.'))
out.append('- "By" is %s.' % ('taken from git history (author of the commit that added the stub)' if has_git else 'not recorded: this wiki has no git history or author field, so only the channel (Via) is known'))
print('\n'.join(out))
```

## Notes

- If the initial bulk build falls inside the window, it dominates the per-day table; say so rather than listing it reference by reference.
- Log lines that name no stub (lint passes, archive moves, restructures) appear in the timeline but never in the reference table.
- Do not fill in "By" from the conversation or the user's name unless the stub or git history says so. To make it recordable in future, suggest that ingest log lines end with `by: <name>`; offer it, do not change the ingest skill unasked.
- Never delete, move or edit wiki files from this skill.
