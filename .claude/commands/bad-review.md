---
description: Handle a 1-star or other negative review. The reputation agent drafts a calm reply (or a private note for false claims) and checks for repeats; the director queues it. Every reply waits for the owner.
argument-hint: <the review text, stars, where it was posted, date, and link>
---

# /bad-review

Event: a negative review has arrived.

Event text: $ARGUMENTS

## 0. Checks before anything

1. Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /bad-review | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner, and stop.
2. Read the four files in `settings/`. If any answer needed here contains `{{fill:`, tell the owner which file and question, log the stop, and stop.
3. If the event text has no review text or no link, ask the owner for them. Do nothing else.

## 1. Is this real?

A negative review is always handled. The director sorts it before briefing:

| kind | means | handling |
| --- | --- | --- |
| complaint | a real customer describes a real problem | calm public reply draft, waits |
| mix-up | wrong business, wrong branch, or a misunderstanding | short, polite public reply draft that clears it up, waits |
| false or abusive | not a customer, made-up claims, abuse | nothing public; private note for the owner; `URGENT` |

It is also `URGENT` whenever the review raises a health or safety issue, threatens legal action, or names someone on staff, or when `settings/approvals.md` lists it as urgent.

- The "next step for complaints" in `brand/reputation/reply-guide.md` is `{{fill:`: the reputation agent records and routes the review but drafts no reply, and the director adds a pending item `Rule missing: brand/reputation/reply-guide.md, next step for complaints`. Log it and stop there.

## 2. Steps

| step | agent | does | writes |
| --- | --- | --- | --- |
| 1 | director | sorts the review, sets urgency, writes one reputation brief | `work/briefs/YYYY-MM-DD-reputation-<slug>.md` |
| 2 | reputation | records it, checks earlier review reports for the same complaint, drafts the reply by the reply guide, voice-checks it | `work/YYYY-MM-DD-reviews-<slug>.md` |
| 3 | director | queues the reply (or the private note) for the owner | item in `approvals/pending.md` |

Run in order:

1. "Use the director agent on this /bad-review event: $ARGUMENTS"
2. "Use the reputation agent on work/briefs/<reputation brief>"
3. "Use the director agent to process returns for the /bad-review event"

After the owner ticks yes, the director briefs the scheduler, which posts the reply through the review tool role or writes it as `[READY TO PASTE]`.

## 3. What waits for the owner

- Every reply to this review. No exceptions, whatever `settings/approvals.md` says.
- The private note for a false or abusive review, as an `URGENT` item.
- A reply that failed the voice check sits in `approvals/voice-holds.md` and is never quietly fixed.

## 4. Log example

```
2026-10-26 18:22 | reputation | drafted reply to 2-star review, seen before x2, added A-20261026-03 | work/2026-10-26-reviews-slow-puncture-repair.md
```

## 5. What the owner gets back

- The review, its kind, and whether it is urgent.
- Earlier reviews with the same complaint, if any.
- The draft reply (or private note) and the pending item id to tick.

## 6. Never

- Never post any reply without the owner's tick.
- Never admit fault, promise a refund or fix, or argue.
- Never mention order details, other customers or staff names.
- Never pressure a reviewer to edit or delete what they wrote.
- Never draft a public reply to a false or abusive review.
