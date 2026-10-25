# Content calendar

What goes out, where and when. A piece that is not on this calendar always waits for the owner. The writer drafts the next `ready` row; the scheduler books rows whose draft has passed every check.
How to use: add one row per planned piece with a date, a channel and a status. Keep at least two weeks of `ready` rows so the calendar never runs thin.

## Status values

| status | meaning | who may set it |
| --- | --- | --- |
| idea | worth doing, not yet agreed | owner; director when it spots a job that is not on the calendar |
| ready | agreed for that date and channel; may be drafted and booked | owner; director only while running `/fill-calendar` |
| scheduled | booked in the scheduler role, with confirmation | scheduler, after the tool or the owner confirms |
| posted | went out | scheduler, from the scheduler role's confirmation or export |
| held | its draft is waiting in `approvals/pending.md` or `approvals/voice-holds.md` | director |
| dropped | will not run | owner; director after the owner ticks no or discard |

Agents may add rows and change the status, brief and draft columns as allowed above. They never change the date, channel or subject of a row the owner wrote.

## Calendar

| id | date | channel | subject | pillar | aim | keyword | status | brief | draft | notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| C-001 | {{fill: YYYY-MM-DD}} | {{fill: channel}} | {{fill: what the piece is about}} | {{fill: pillar from claims.md}} | {{fill: what it should achieve}} | {{fill: keyword or none}} | {{fill: status}} | | | |
| C-ex | 2026-11-04 | instagram | winter tune-up checklist (example, Harbor Lane Bikes) | Repair first | bookings for November tune-ups | none | ready | | | delete this row |

Channel names: linkedin, instagram, facebook, tiktok, youtube, blog, google-profile, email, chat.
Brief and draft columns hold paths, for example `work/briefs/2026-11-01-writer-winter-tune-up-checklist.md`.

## When the calendar counts as thin

{{fill: e.g. "fewer than 2 ready or scheduled rows in the next 14 days on any channel with a cadence"}}

> Example (Harbor Lane Bikes): any channel with a cadence has fewer than one ready or scheduled row per planned post in the next 10 days.

When thin, the director suggests `/fill-calendar` for the gap in its end-of-run summary.

## Cadence per channel

The number of pieces per week. Posting days and times live in `brand/channels/slots.md`. A channel with no cadence is skipped by `/fill-calendar`.

| channel | pieces per week |
| --- | --- |
| linkedin | {{fill: number or none}} |
| instagram | {{fill: ...}} |
| facebook | {{fill: ...}} |
| tiktok | {{fill: ...}} |
| youtube | {{fill: ...}} |
| blog | {{fill: ...}} |
| google-profile | {{fill: ...}} |
| email | {{fill: ...}} |
