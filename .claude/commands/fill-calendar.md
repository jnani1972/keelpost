---
description: Fill gaps in the content calendar for a date range. The scheduler lists empty slots, the director briefs one job per gap, the writer drafts, the director adds them as ready, and the scheduler books what may ship.
argument-hint: <date range, e.g. 2026-11-02 to 2026-11-15, optionally channels>
---

# /fill-calendar

Event: the calendar has gaps in a date range.

Event text: $ARGUMENTS

## 0. Checks before anything

1. Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /fill-calendar | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner, and stop.
2. Read the four files in `settings/`. If any answer needed here contains `{{fill:`, tell the owner which file and question, log the stop, and stop.
3. If the event text has no date range, ask the owner for one. Do nothing else.

## 1. Is this real?

A gap is real when both hold:

| test | checked against |
| --- | --- |
| a slot exists for that channel, day and time | `brand/channels/slots.md` |
| no `ready` or `scheduled` calendar row covers that slot | `brand/content/calendar.md` |

- A channel with no cadence in `brand/content/calendar.md` is skipped. The director adds one pending item asking the owner whether that channel should have one.
- Slots, spacing or blackout dates are `{{fill:`: the director adds a pending item `Rule missing: brand/channels/slots.md, <field>`, logs it, and stops. It never makes up a cadence.

## 2. Steps

| step | agent | does | writes |
| --- | --- | --- | --- |
| 1 | director | briefs the scheduler to list gaps in the range | `work/briefs/YYYY-MM-DD-scheduler-<slug>.md` |
| 2 | scheduler | lists every free slot; notes skipped channels | `work/YYYY-MM-DD-schedule-<slug>.md` |
| 3 | director | one writer brief per gap. Topic source, in this order: `idea` rows in the calendar; then proof in `brand/identity/claims.md` not used in the last 30 days; then a pattern from `brand/content/hooks.md` applied to a topic we own | `work/briefs/YYYY-MM-DD-writer-<slug>.md` per gap |
| 4 | writer | drafts each filler | `work/YYYY-MM-DD-<channel>-<slug>.md` |
| 5 | director | adds a calendar row with status `ready` for each draft that passed the voice check, and gates it | `brand/content/calendar.md`, `approvals/pending.md` |
| 6 | scheduler | books what may ship; writes `[READY TO PASTE]` where no tool is connected | `work/YYYY-MM-DD-schedule-<slug>.md` |

Run in order:

1. "Use the director agent on this /fill-calendar event: $ARGUMENTS"
2. "Use the scheduler agent on work/briefs/<scheduler gaps brief>"
3. "Use the director agent to process returns for the /fill-calendar event"
4. "Use the writer agent on work/briefs/<writer brief>" (once per gap)
5. "Use the director agent to process returns for the /fill-calendar event"
6. "Use the scheduler agent on work/briefs/<scheduler booking brief>"

## 3. What waits for the owner

- Fillers on channels listed under "nothing auto-ships" in `settings/approvals.md`.
- Anything the always-wait list in `CLAUDE.md` catches: prices, names, `[CHECK]`, competitor reactions.
- Drafts that failed the voice check (in `approvals/voice-holds.md`).

## 4. Log example

```
2026-10-28 09:05 | scheduler | 5 free slots found 2026-11-02 to 2026-11-15, tiktok skipped (no cadence) | work/2026-10-28-schedule-november-gaps.md
```

## 5. What the owner gets back

- How many gaps were found, and which channels were skipped.
- One line per filler: date, channel, topic, draft path, scheduled / ready to paste / waiting.
- Pending item ids to tick.

## 6. Never

- Never fill a slot that does not exist in `brand/channels/slots.md`.
- Never book anything into a blackout date or closer than the minimum spacing.
- Never change a row the owner wrote; only add rows and set statuses the calendar allows.
- Never use a topic outside "topics we own" in `settings/strategy.md`.
