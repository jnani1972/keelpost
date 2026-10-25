---
description: Handle a page dropping in search. search-watch finds the likely cause; a technical cause goes to the owner, a content cause gets a section-by-section refresh from the writer; the director gates.
argument-hint: <page URL, its keyword, and the rank tracker export that shows the drop>
---

# /rank-loss

Event: a page has dropped in search results.

Event text: $ARGUMENTS

## 0. Checks before anything

1. Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /rank-loss | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner, and stop.
2. Read the four files in `settings/`. If any answer needed here contains `{{fill:`, tell the owner which file and question, log the stop, and stop.
3. If the event text does not name the page, ask the owner. Do nothing else.

## 1. Is this real?

All three must hold:

| test | checked against |
| --- | --- |
| the change counts as a drop | "ranking loss" in `brand/search/thresholds.md` |
| the page sits under the position it was aiming for | the page's row in `brand/search/targets.md` |
| the keyword is the one assigned to that page | owning URL in `brand/search/keywords.md` |

- Any test fails: the director logs "not an event: <test>" and stops.
- The ranking-loss definition or the page's target is `{{fill:`: the director adds a pending item `Rule missing: <file>, <field>`, logs it, and stops.

## 2. Steps

| step | agent | does | writes |
| --- | --- | --- | --- |
| 1 | director | confirms the tests; briefs search-watch | `work/briefs/YYYY-MM-DD-search-watch-<slug>.md` |
| 2 | search-watch | finds the likely cause, checking in turn: competitors that moved up, query changes, sessions lost, links lost, crawl problems | `work/YYYY-MM-DD-search-<slug>.md` |
| 3 | director | technical cause: one pending item for the owner's web person. Content cause: briefs the writer | `approvals/pending.md` or `work/briefs/YYYY-MM-DD-writer-<slug>.md` |
| 4 | writer | content cause only: section-by-section refresh (current text, proposed text, reason) that keeps the URL and keyword | `work/YYYY-MM-DD-blog-<slug>.md` |
| 5 | director | gates the refresh | `approvals/pending.md` |

Run in order:

1. "Use the director agent on this /rank-loss event: $ARGUMENTS"
2. "Use the search-watch agent on work/briefs/<search-watch brief>"
3. "Use the director agent to process returns for the /rank-loss event"
4. "Use the writer agent on work/briefs/<writer brief>" (content cause only)
5. "Use the director agent to process returns for the /rank-loss event"

## 3. What waits for the owner

- Every technical fix (broken links, titles, redirects, blocked pages). Agents never touch the site.
- A refresh that alters any claim, promise or price on the page.
- Anything else the always-wait list in `CLAUDE.md` catches. A refresh that only reorders or expands existing, sourced content may go out if `settings/approvals.md` allows it.

## 4. Log example

```
2026-10-30 09:30 | search-watch | rank loss cause: lost 2 backlinks and title missing on page | work/2026-10-30-search-services-page-drop.md
```

## 5. What the owner gets back

- The drop against the threshold and the target.
- The likely cause with the evidence for each check.
- Either the technical fix list for the web person, or the refresh draft, with pending item ids.

## 6. Never

- Keep the page's address and its assigned keyword exactly as they are.
- Never edit the site, its redirects or settings.
- Never guess a cause the exports do not support; say "cause not found" instead.
- Never report a number that is not in an export: `[NO DATA]`.
