---
description: Handle an ad whose creative is wearing out. The designer builds variants that change one element each, the scheduler writes a rotation plan as a draft only, and the director queues the swap. Nothing goes live until the owner says yes.
argument-hint: <the ad (name or id), channel, and the reporting export that shows the decline>
---

# /ad-fatigue

Event: an ad's creative is wearing out.

Event text: $ARGUMENTS

## 0. Checks before anything

1. Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /ad-fatigue | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner, and stop.
2. Read the four files in `settings/`. If any answer needed here contains `{{fill:`, tell the owner which file and question, log the stop, and stop.
3. If the event text does not name the ad and its export, ask the owner. Do nothing else.

## 1. Is this real?

Both must hold:

| test | checked against |
| --- | --- |
| the ad passes the worn-out rule | "when an ad creative counts as worn out" in `brand/visuals/specs.md`, using the newest `data/reporting-tool-ads-*` export |
| nothing else about the ad changed in that window: budget, audience, offer or landing page | `logs/actions.md` and the ad rotation history in `brand/visuals/assets.md` |

- If something else changed, the decline may not be the creative. The director logs "not an event: ad also changed <what>" and stops.
- The worn-out rule is `{{fill:`: the director adds a pending item `Rule missing: brand/visuals/specs.md, when an ad creative counts as worn out`, logs it, and stops.

## 2. Steps

| step | agent | does | writes |
| --- | --- | --- | --- |
| 1 | director | confirms the tests; briefs the designer with the number of variants (default 3) | `work/briefs/YYYY-MM-DD-designer-<slug>.md` |
| 2 | designer | builds variants, each changing exactly one element (headline, image, colour, or opening line), same offer and message; spec-checks each | `work/YYYY-MM-DD-<channel>-<slug>-visual.md` |
| 3 | director | briefs the scheduler for a rotation plan | `work/briefs/YYYY-MM-DD-scheduler-<slug>.md` |
| 4 | scheduler | writes the rotation plan (which variant, from when, what is retired) as a draft only; nothing is booked or changed | `work/YYYY-MM-DD-schedule-<slug>.md` |
| 5 | director | queues the swap | item in `approvals/pending.md` |

Run in order:

1. "Use the director agent on this /ad-fatigue event: $ARGUMENTS"
2. "Use the designer agent on work/briefs/<designer brief>"
3. "Use the director agent to process returns for the /ad-fatigue event"
4. "Use the scheduler agent on work/briefs/<scheduler brief>"
5. "Use the director agent to process returns for the /ad-fatigue event"

## 3. What waits for the owner

- The swap, always. It changes a paid ad, so it is spend-related even if the budget stays the same.
- Any variant that failed the spec check (in `approvals/voice-holds.md`).
- After a yes, the scheduler writes the swap as `[READY TO PASTE]` and the owner makes it in the ad tool.

## 4. Log example

```
2026-10-31 11:10 | designer | 3 variants for winter service ad: headline, image, colour | work/2026-10-31-facebook-winter-service-ad-visual.md
```

## 5. What the owner gets back

- The decline against the worn-out rule, and confirmation that nothing else changed.
- Each variant with the one element it changes.
- The rotation plan and the pending item id for the swap.

## 6. Never

- Never change the ad, its budget, audience, offer or landing page.
- Never change more than one element per variant.
- Never use an unregistered asset in a variant.
- Never book or launch the rotation.
