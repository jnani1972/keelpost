---
description: Handle a jump in search interest for a topic. The director checks it is real, the writer drafts, search-watch picks the owning page, and the director gates.
argument-hint: <topic or query that is surging, and the export file that shows it>
---

# /demand-surge

Event: search interest in a topic has jumped.

Event text: $ARGUMENTS

## 0. Checks before anything

1. Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /demand-surge | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner, and stop.
2. Read the four files in `settings/`. If any answer needed here contains `{{fill:`, tell the owner which file and question, log the stop, and stop.
3. If the event text is empty, ask the owner what is surging and where they saw it. Do nothing else.

## 1. Is this real?

Use the director agent on this event, as `kind: event`, `event: /demand-surge`. Ask it to test all four, citing the file for each:

| test | checked against |
| --- | --- |
| the jump passes the surge threshold | "surge in search interest" in `brand/search/thresholds.md` |
| the query is one of our keywords or close to one | clusters in `brand/search/keywords.md` |
| the data is dated and comes from a known feed | file name in `data/` matches a row in `brand/search/data-feeds.md` |
| the topic is one we own | "topics we own" in `settings/strategy.md` |

- Any test fails: the director logs "not an event: <test>" and stops. Nothing is drafted.
- A rule file has no answer (`{{fill:`): the director adds a pending item `Rule missing: <file>, <field>`, logs it, and stops. It never invents a threshold.

## 2. Steps

| step | agent | does | writes |
| --- | --- | --- | --- |
| 1 | director | writes a writer brief and a search-watch brief, and lists both hand-offs | `work/briefs/YYYY-MM-DD-writer-<slug>.md`, `work/briefs/YYYY-MM-DD-search-watch-<slug>.md` |
| 2 | writer | drafts the piece for the channel in the brief, sourced from project files only | `work/YYYY-MM-DD-<channel>-<slug>.md` |
| 3 | search-watch | names which page should own the keyword and flags any page already competing for it (cannibalisation) | `work/YYYY-MM-DD-search-<slug>.md` |
| 4 | director | applies the approval gate to the draft and the search advice | items in `approvals/pending.md` |

Run them in order:

1. "Use the director agent on this /demand-surge event: $ARGUMENTS"
2. "Use the writer agent on work/briefs/<writer brief>"
3. "Use the search-watch agent on work/briefs/<search-watch brief>" (give it the writer's draft path)
4. "Use the director agent to process returns for the /demand-surge event"

If search-watch says an existing page should own the keyword, the director turns the draft into a refresh brief for that page instead of a new URL.

## 3. What waits for the owner

- The new piece, because it is not on the calendar, unless `settings/approvals.md` explicitly lets surge pieces auto-ship.
- Anything the always-wait list in `CLAUDE.md` catches (prices, names, `[CHECK]`, competitor reactions).
- Any change to which page owns a keyword: it is a suggestion in the search report, never an edit.

## 4. Log example

```
2026-10-26 10:14 | director | event /demand-surge: "winter bike maintenance" passed 4 of 4 tests | work/briefs/2026-10-26-writer-winter-bike-maintenance.md
```

## 5. What the owner gets back

- Whether the surge was real, and which test failed if not.
- The draft path and its voice result.
- The page search-watch recommends as the owner, and any cannibalisation warning.
- The pending item ids to tick.

## 6. Never

- Never act on a surge from an undated or unknown export.
- Never invent or loosen a threshold to make the event count.
- Never publish a new page or change which page owns a keyword without the owner.
- Never skip the director: the writer and search-watch work only from its briefs.
