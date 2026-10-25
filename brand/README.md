# Brand knowledge base

Everything the agents need to know about your business, written down once so every draft starts from the same facts. You write these files. Agents read them.

## Rules

1. **Agents read, the owner writes.** Agents never change a brand file, with two exceptions:
   - In a table whose heading says **(open to suggestions)**, an agent may add a new row with status `suggested`. It never edits or deletes an existing row. You change `suggested` to a real status or delete the row.
   - In `brand/content/calendar.md`, the director and scheduler may add rows and set statuses exactly as that file's status table allows.
2. **Settings win.** If a brand file disagrees with a file in `settings/`, the setting wins and the agent adds a pending item asking you to fix the conflict.
3. **An unanswered placeholder means unknown.** An agent that needs a field still holding a fill placeholder stops and asks. It never guesses.
4. **Examples are not facts.** Rows and lines marked as Harbor Lane Bikes examples are for a fictional shop. Delete them once your own rows are in. Agents ignore them.
5. **Exports go in `data/`, not here.** Brand files hold rules and facts that change slowly. Weekly numbers live in `data/`.
6. **No secrets.** No passwords, API keys, card numbers or private customer details in any file in this project.

## Folder map

| folder | files | what it holds |
| --- | --- | --- |
| `identity/` | voice.md, tone-rules.md, positioning.md, claims.md | how you sound, what you stand for, what you can prove |
| `search/` | keywords.md, thresholds.md, targets.md, data-feeds.md | keywords, alarm levels, ranking goals, where search data comes from |
| `content/` | calendar.md, brief-layouts.md, hooks.md, seo-checks.md | what gets posted when, and how drafts are shaped |
| `visuals/` | specs.md, assets.md, video-scripts.md | colours, sizes, approved assets, video layouts |
| `channels/` | channel-rules.md, slots.md, hashtags.md | rules per platform, posting times, tags |
| `reputation/` | reply-guide.md, review-process.md, mentions.md | how to answer reviews and mentions |
| `inbox/` | faq.md, lead-rules.md, reply-scripts.md | approved answers, what counts as a lead, message scripts |
| `metrics/` | kpis.md, cost-limits.md, credit-rules.md | what success means and how it is counted |
| `stack.md` | | which tool you use for each role and how it connects |

## Who reads what

| agent | reads |
| --- | --- |
| director | `content/calendar.md`, `channels/slots.md`, `search/thresholds.md`, `metrics/kpis.md`, `stack.md`, plus whatever an event needs |
| search-watch | `search/` (all four), `stack.md` |
| rival-watch | `identity/positioning.md`, `identity/claims.md`, `search/keywords.md`, `search/thresholds.md`, `reputation/mentions.md` |
| writer | `identity/` (all four), `content/` (all four), `channels/channel-rules.md`, `channels/hashtags.md` |
| designer | `identity/voice.md`, `identity/tone-rules.md`, `identity/positioning.md`, `visuals/` (all three), `stack.md` |
| scheduler | `channels/` (all three), `content/calendar.md`, `stack.md` |
| reputation | `identity/` (all four), `reputation/` (all three), `stack.md` |
| inbox | `identity/voice.md`, `identity/tone-rules.md`, `inbox/` (all three), `stack.md` |
| analyst | `metrics/` (all three), `content/hooks.md`, `stack.md` |
| setup-check | everything, read only |

## Minimum for a first run

Fill these before running `/weekly-run`. `/setup-check` checks them.

1. `identity/voice.md`
2. `identity/tone-rules.md`
3. `identity/positioning.md`
4. `identity/claims.md`
5. `content/calendar.md`, with at least one row marked `ready`

Plus the length rule for at least one channel in `channels/channel-rules.md`.

Everything else can wait. An agent that needs an empty file stops and tells you which one.

## Keeping it current

| when | what to do |
| --- | --- |
| weekly | review `suggested` rows; add ready rows to the calendar; drop new exports into `data/` |
| monthly | check claims and proof expiry dates; update `search/targets.md` positions; re-read `metrics/kpis.md` targets |
| on change | new price, product, opening hours or staff: update `inbox/faq.md`, `identity/claims.md` and `inbox/lead-rules.md` the same day; new tool: update `stack.md` |
