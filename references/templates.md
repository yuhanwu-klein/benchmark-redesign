# Templates

These are the shapes of the documents the loop produces. Adapt the headings to the topic, but keep the parts that make each one checkable: sources, the split between facts and inference, reasons, and status. Write each document in the language the user works in.

Use only what the request's size needs (see "Size the work to the request" in SKILL.md):

- **Medium (the default):** the report (2), with its adopt / adapt / reject table (3), and a standard (4) if the task is a quality judgment, all in one file.
- **Large:** add the research notes (1).
- **Any size:** the decision log (5) and the verification table (6) only when the project already keeps them.

## Contents

1. Research note (one per track)
2. Report
3. Adopt / adapt / reject table
4. Standard and audit
5. Decision log
6. Verification table
7. Credits list
8. Hand-back message

---

## 1. Research note

File: `research_notes/<topic>/<track>.md`

```markdown
# <Track>: <the question this track answers>

Scope: <which products and sources, and what is deliberately left out>. Research date: <YYYY-MM-DD>.

Source quality:
- No tag = page read directly.
- "(search summary)" = taken from a search snippet; the page was not read. Lower confidence.
- [unverified] = could not be confirmed.

## 1. <Sub-question>

### Takeaway
<Two or three sentences: what the sources show, in plain words.>

### Cited findings
**<Product or source>**
- <Fact, with numbers and dates where they exist> — [<Source title>](<url>)
- <Fact> (search summary) — [<Source>](<url>)

## Gaps
- <What could not be found or read, and why>
```

## 2. Report

File: `reports/<topic>.md`. Lead with the conclusion. The title states the finding, not the topic.

```markdown
# <The finding in one line>

<Why this research was done, the date, and a one-line note on the kind of evidence (e.g. "sources rarely describe films frame by frame, so each case separates confirmed traits from my reading").>

## Cases
| # | Company / product | What the source confirms | Source |
| --- | --- | --- | --- |

## Shared patterns (my synthesis)
1. **<Pattern>.** <One or two sentences.> (cases 2, 3, 10)

## What this means for <product>
<Adopt / adapt / reject table, then the concrete design consequences.>

## Not doing
- <Rejected idea>: <why, with evidence>

## Sources
Research date <YYYY-MM-DD>. No tag = read directly; "(search summary)" = from a search snippet; [unverified] = not confirmed.
1. [<Title>](<url>): <what it was used for>
```

At Medium size this Sources list replaces the research notes, so every claim in the cases table should trace to an entry in it.

## 3. Adopt / adapt / reject table

| Source structure | Where it came from | What <product> does | Why |
| --- | --- | --- | --- |
| Time-boxed container, archived per edition | Flickr 'Roid Week | Adopt: a weekly edition; past editions frozen | No endless feed; the archive pages by date |
| Peer nomination threads | 'Roid Week Favourites | Adapt: nominations private, uncounted, sent to editors | Keeps speaking up for others, drops the ranking |
| Algorithmic explore, top charts | Flickr Explore | Reject | Gamed, breeds comment trading, reads as fake points |

## 4. Standard and audit

```markdown
### Standard
A <photo / asset / clip> enters the product only if it passes all <n> rules:

1. **<Rule as a short claim>.** <Pass test.> <What fails, with concrete examples.> (Source: <official page>)
...
n. **No generation or stock tells.** <Tells.> If two of three reviewers say "AI" or "stock", it fails.

### Audit (<date>)
| Set | Pass | Close | Fail |
| --- | --- | --- | --- |
| <Set, count, file> | 0 | 2 | 17 |

- **Close:** <item>: fails only rule <n> because <reason>.
- **Fail:** <item, item>: rules <n, m>.
```

## 5. Decision log

File: `design-decisions.md`, newest last.

| Problem | Decision | Why | Source | Verified by |
| --- | --- | --- | --- | --- |
| Users could not see what a correction changed | A compare stage with the original left, the correction right and a draggable divider; strength 0 shows the original exactly | None of the six competitor apps shows the original beside the correction | PRD 1, 11; competitor audit | Divider, zoom and strength 0 checked in the browser |

## 6. Verification table

File: `flow-verification.md`. Start with what was checked and what was not.

```markdown
Checked in <browser/tool> on <date>, at <1440 × 900> and <375 × 812>. This verifies the <prototype/page>, not <user research, hardware, ...>.

| Scenario | Expected result | Status |
| --- | --- | --- |
| <First visit> | <What the user sees> | Pass |
| <Edge case, e.g. ?state=offline> | <Expected> | Fail: <what happened> |
```

## 7. Credits list

One line per asset, in the README and wherever the product shows the asset:

```markdown
- "<Title>" by <Author>, <License> — <url> (used in: <screen / file>)
```

## 8. Hand-back message

Keep it short and lead with the result.

```markdown
<One sentence: what is done and where.>

**Changed**
- <change>: <the evidence it rests on>

**Your edits kept**
- <anything the user changed that you left alone>

**Check before you ship**
1. <A contradiction or risk you found and did not decide alone>
2. <What could not be verified, and why>

<Unpublished, uncommitted or pending items, in one line.>
```
