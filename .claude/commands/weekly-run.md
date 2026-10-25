---
description: Start the week. Runs the session-start checks, the director's weekly loop (gather, rank, brief), then walks through the hand-offs one by one and finishes with the approval gate.
argument-hint: [week start date YYYY-MM-DD or a note for the director]
---

# /weekly-run

Start the week's work.

Note from the owner (optional): $ARGUMENTS

## 0. Session-start checks

Do these yourself, in order, before calling any agent:

1. Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /weekly-run | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner, and stop.
2. Read the four files in `settings/`. If any contains `{{fill:`, list each file and question, log `stopped: unfilled settings`, and stop. Suggest `/setup-check`.
3. Read the newest 20 entries in `logs/actions.md`.
4. Read the Open sections of `approvals/pending.md` and `approvals/voice-holds.md`. If the owner has ticked items, run step 1 below in **approvals** mode first: "Use the director agent to process approvals."
5. Glob `data/`. If no dated export is inside its freshness limit in `brand/search/data-feeds.md` (or those limits are still `{{fill:`), tell the owner and ask whether to carry on with the calendar only.

## 1. Plan the week

"Use the director agent in weekly mode. Week start: <date from the note, or the coming Monday>. Owner note: $ARGUMENTS"

The director:

1. gathers the newest dated exports, the calendar and the posting slots;
2. scores every candidate job on urgency, fit and evidence (0 to 3 each) and cuts at the free slots;
3. writes one brief per job in `work/briefs/`;
4. writes the week plan `work/briefs/YYYY-MM-DD-director-week-plan.md` with the hand-off list.

## 2. Print the hand-off list

Show the owner the hand-off list from the week plan as a numbered list, for example:

```
1. Use the writer agent on work/briefs/2026-10-26-writer-winter-tune-up-checklist.md
2. Use the designer agent on work/briefs/2026-10-26-designer-winter-tune-up-checklist.md
3. Use the search-watch agent on work/briefs/2026-10-26-search-watch-weekly-check.md
4. Use the analyst agent on work/briefs/2026-10-26-analyst-week-43.md
```

Then run them one at a time, in order. After each one returns:

- give its return to the director: "Use the director agent to process returns for <brief id>";
- if the director writes a follow-up brief (for example a designer brief after a draft), add it to the end of the list.

Stop and ask the owner before continuing if any hand-off fails, a `{{fill:` stops an agent, or an `URGENT` item appears.

## 3. Schedule

When every hand-off has returned, the director will have written scheduler briefs for items that passed the gate. Run each: "Use the scheduler agent on work/briefs/<scheduler brief>".

## 4. What waits for the owner

Everything the gate held: items in `approvals/pending.md` and `approvals/voice-holds.md`. Nothing on the always-wait list in `CLAUDE.md` goes out this run.

## 5. Log example

```
2026-10-26 09:00 | director | week plan: 9 jobs scored, 5 kept, 5 briefs, 2 waiting | work/briefs/2026-10-26-director-week-plan.md
```

## 6. What the owner gets back

- The week plan path and the cut line.
- What was scheduled, what is `[READY TO PASTE]`, and what waits, with item ids.
- Anything held or not done, and whether the calendar is thin (suggesting `/fill-calendar`).
- Reminder: tick `approvals/pending.md`, then ask "Use the director agent to process approvals."

## 7. Never

- Never skip the director: specialists run only on its briefs.
- Never run two hand-offs at once or out of order.
- Never tick an approval box for the owner.
- Never continue past a pause or a stopped agent without telling the owner.
