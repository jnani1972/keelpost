---
description: Handle a competitor launching a promotion. rival-watch confirms it, the writer proposes keep / reframe / add for each calendar item, the designer rebuilds affected visuals, and the director gates. Everything waits for the owner.
argument-hint: <competitor name, what the promotion is, and where you saw it (link)>
---

# /rival-promo

Event: a competitor has launched a promotion that might pull customers away.

Event text: $ARGUMENTS

## 0. Checks before anything

1. Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /rival-promo | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner, and stop.
2. Read the four files in `settings/`. If any answer needed here contains `{{fill:`, tell the owner which file and question, log the stop, and stop.
3. If the event text names no competitor or no source, ask the owner for both. Do nothing else.

## 1. Is this real?

All three must hold. The director checks the first; rival-watch checks the other two.

| test | checked against |
| --- | --- |
| the competitor is on our watch list | competitor watch list in `brand/identity/positioning.md` |
| it is confirmed by the mention plus a second, linked source | "when a competitor promotion counts" in `brand/reputation/mentions.md` |
| it reaches our audience or topics | the same section, plus `settings/strategy.md` audience and topics |

- Any test fails: log "not an event: <test>" and stop. Nothing else is written.
- The promotion rule in `brand/reputation/mentions.md` is `{{fill:`: the director adds a pending item `Rule missing: brand/reputation/mentions.md, when a competitor promotion counts`, logs it, and stops.

## 2. Steps

| step | agent | does | writes |
| --- | --- | --- | --- |
| 1 | director | tests the watch list; briefs rival-watch to confirm | `work/briefs/YYYY-MM-DD-rival-watch-<slug>.md` |
| 2 | rival-watch | confirms with a second source, fills "Promotions spotted", optional page look with REA if the brief names a public page | `work/YYYY-MM-DD-rivals-<slug>.md` |
| 3 | director | if confirmed, briefs the writer with the next 14 days of calendar rows | `work/briefs/YYYY-MM-DD-writer-<slug>.md` |
| 4 | writer | for each calendar item proposes **keep**, **reframe** or **add**, using our proof ids, never the competitor's angle or wording | `work/YYYY-MM-DD-<channel>-<slug>.md` per reframe or addition |
| 5 | director | briefs the designer for each item whose visual must change | `work/briefs/YYYY-MM-DD-designer-<slug>.md` |
| 6 | designer | rebuilds the affected visuals from the new drafts | `work/YYYY-MM-DD-<channel>-<slug>-visual.md` |
| 7 | director | gates everything | items in `approvals/pending.md` |

Run in order, giving each return to the director before the next step:

1. "Use the director agent on this /rival-promo event: $ARGUMENTS"
2. "Use the rival-watch agent on work/briefs/<rival-watch brief>"
3. "Use the director agent to process returns for the /rival-promo event"
4. "Use the writer agent on work/briefs/<writer brief>"
5. "Use the director agent to process returns for the /rival-promo event"
6. "Use the designer agent on work/briefs/<designer brief>" (one per visual)
7. "Use the director agent to process returns for the /rival-promo event"

## 3. What waits for the owner

- Every reframe and addition, because it reacts to a competitor.
- Any price, discount, offer or giveaway, including a counter-offer.
- Any spend, such as boosting a reply post. Over a cap: `OVER LIMIT`.
- "Keep" items stay on the calendar as they were and are not re-gated.

## 4. Log example

```
2026-10-27 08:50 | rival-watch | promotion confirmed: Example Cycle Depot winter service, 2 sources | work/2026-10-27-rivals-winter-service-promo.md
```

## 5. What the owner gets back

- Whether the promotion was confirmed, with both links.
- A keep / reframe / add list for the next 14 days of calendar rows.
- The new drafts and visuals, and the pending item ids to tick.

## 6. Never

- Never reply to, mention, tag or comment on the competitor.
- Never copy or answer their wording, price or angle directly.
- Never propose a price match or discount as decided; it is always the owner's call.
- Never guess the competitor's prices, budget or results.
- Never log in to, click through or submit anything on the competitor's site.
