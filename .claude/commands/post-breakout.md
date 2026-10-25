---
description: Handle a post performing far above normal. The scheduler writes versions for other channels and prepares a boost with a blank amount, the analyst checks cost and caps, and the director gates. The boost always waits for the owner.
argument-hint: <the post (draft path or link), channel, and the export that shows its numbers>
---

# /post-breakout

Event: a post is doing far better than usual.

Event text: $ARGUMENTS

## 0. Checks before anything

1. Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /post-breakout | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner, and stop.
2. Read the four files in `settings/`. If any answer needed here contains `{{fill:`, tell the owner which file and question, log the stop, and stop.
3. If the event text does not name the post and its export, ask the owner. Do nothing else.

## 1. Is this real?

Both must hold, from a dated export in `data/`:

| test | checked against |
| --- | --- |
| it passes the breakout threshold for its channel | "normal performance per channel" in `brand/metrics/kpis.md` |
| its reach is mainly our target audience | the audience check column in the same table, and `settings/strategy.md` |

- Fails either test: the director logs "not an event: <test>". The analyst may still list the post as notable.
- The breakout threshold or audience check for that channel is `{{fill:`: the director adds a pending item `Rule missing: brand/metrics/kpis.md, breakout threshold for <channel>`, logs it, and stops.

## 2. Steps

| step | agent | does | writes |
| --- | --- | --- | --- |
| 1 | director | confirms the tests; briefs the scheduler | `work/briefs/YYYY-MM-DD-scheduler-<slug>.md` |
| 2 | scheduler | writes a version for each other channel in `brand/channels/channel-rules.md` that fits, re-checks each one, and prepares a boost with the amount left blank | `work/YYYY-MM-DD-<channel>-<slug>.md` per version, `work/YYYY-MM-DD-schedule-<slug>.md` |
| 3 | director | briefs the analyst | `work/briefs/YYYY-MM-DD-analyst-<slug>.md` |
| 4 | analyst | cost per result for the channel against `brand/metrics/cost-limits.md`, and month-to-date spend against `settings/spend-limits.md` caps | `work/YYYY-MM-DD-metrics-<period>.md` |
| 5 | director | gates the versions and the boost | items in `approvals/pending.md` |

Run in order:

1. "Use the director agent on this /post-breakout event: $ARGUMENTS"
2. "Use the scheduler agent on work/briefs/<scheduler brief>"
3. "Use the director agent to process returns for the /post-breakout event"
4. "Use the analyst agent on work/briefs/<analyst brief>"
5. "Use the director agent to process returns for the /post-breakout event"

## 3. What waits for the owner

- The boost, always. The amount is blank; the owner writes it in the comment line. If the owner's amount would pass a cap, the director marks it `OVER LIMIT`.
- The new channel versions, because they are not yet on the calendar.
- Anything the always-wait list in `CLAUDE.md` catches.

## 4. Log example

```
2026-10-29 12:40 | analyst | breakout cost check: instagram within limit, 62% of monthly cap used | work/2026-10-29-metrics-2026-w44.md
```

## 5. What the owner gets back

- The post's numbers against normal and the threshold.
- The channel versions with their voice results.
- The boost item (amount blank), the cost check, and how much of the monthly cap is left.

## 6. Never

- Never boost, or fill in a boost amount.
- Never treat a post as a breakout on reach from outside the target audience.
- Never change the post's message in the channel versions.
- Never estimate missing numbers: `[NO DATA]`.
