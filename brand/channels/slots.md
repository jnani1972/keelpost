# Posting slots

When each channel posts. The director counts free slots to decide how many jobs make the week's cut; the scheduler books each item into the next free slot.
How to use: list days and times per channel in your local time zone. A slot is free when no `ready` or `scheduled` calendar row covers it.

Time zone: {{fill: e.g. Europe/London}}

## Slots per channel

| channel | posts per week | days | times | mix | scheduler role |
| --- | --- | --- | --- | --- | --- |
| instagram | {{fill: number}} | {{fill: e.g. Mon, Wed, Sat}} | {{fill: e.g. 07:30}} | {{fill: e.g. 2 tips, 1 workshop story}} | {{fill: scheduler, or none = [READY TO PASTE]}} |
| linkedin | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| facebook | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| tiktok | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| youtube | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| blog | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: blog}} |
| google-profile | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: local listing}} |
| email | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| instagram (example, Harbor Lane Bikes) | 3 | Mon, Wed, Sat | 07:30 | 2 tips, 1 workshop story | scheduler |

The posts-per-week numbers should match the cadence in `brand/content/calendar.md`.

## Minimum spacing

- Same channel: at least {{fill: e.g. 20 hours}} between posts.
- Any two channels: at least {{fill: e.g. 2 hours}} between posts.

## Blackout dates

No posts on these dates. Booked items move to the next free slot after the blackout.

| from | to | why |
| --- | --- | --- |
| {{fill: YYYY-MM-DD}} | {{fill: YYYY-MM-DD}} | {{fill: e.g. shop closed, holiday}} |
| 2026-12-25 | 2026-12-26 | shop closed (example, Harbor Lane Bikes) |

## Checks before anything is scheduled

The scheduler confirms, for each item:

1. `voice: pass` in the draft's front matter.
2. If the item has a visual: `spec: pass` in its `-visual.md` file.
3. No open `[CHECK]` or `[OWNER PICKS]` in the draft or visual.
4. It is inside `settings/approvals.md` and not on the always-wait list, or it has a yes tick in `approvals/pending.md`.
5. The slot is free, respects spacing and is not a blackout date.

Any failed check: the item goes to `approvals/pending.md` with the reason, and the scheduler moves to the next item.
