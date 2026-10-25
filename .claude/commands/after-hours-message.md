---
description: Handle a direct message or enquiry that arrived while the business is closed. The inbox agent replies with an FAQ answer, holding reply, booking link or nothing, records leads in the CRM role, and the director alerts the owner only for real leads and problems.
argument-hint: <the message text, channel, sender contact if given, and arrival time>
---

# /after-hours-message

Event: a message or enquiry came in while the business is closed.

Event text: $ARGUMENTS

## 0. Checks before anything

1. Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /after-hours-message | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner, and stop.
2. Read the four files in `settings/`. If any answer needed here contains `{{fill:`, tell the owner which file and question, log the stop, and stop.
3. If the event text has no message, ask the owner for it. Do nothing else.

## 1. Is this real?

Every message is answered or deliberately left (spam). The inbox agent sorts it:

| kind | means | reply |
| --- | --- | --- |
| real lead | passes the lead tests in `brand/inbox/lead-rules.md` | FAQ answer if there is one, plus booking link if the rules say so, else holding reply |
| problem | support problem or complaint | holding reply only |
| question | a question, not a lead | FAQ answer copied exactly, else holding reply and an FAQ gap |
| spam | sales pitch, links, nonsense | no reply |

- Opening hours or lead tests in `brand/inbox/lead-rules.md` are `{{fill:`: treat the message as a real lead and out of hours, and the director adds a pending item asking the owner to fill those rules. Log it. Do not invent hours.
- No arrival time given: treat it as out of hours.

## 2. Steps

| step | agent | does | writes |
| --- | --- | --- | --- |
| 1 | director | writes one inbox brief | `work/briefs/YYYY-MM-DD-inbox-<slug>.md` |
| 2 | inbox | sorts, replies with approved scripts only, looks up or records the lead in the CRM role, voice-checks the reply | `work/YYYY-MM-DD-inbox-<slug>.md` |
| 3 | director | adds an `URGENT` pending item for a real lead or a problem; passes complaints on as a reputation brief | `approvals/pending.md`, `work/briefs/YYYY-MM-DD-reputation-<slug>.md` |

Run in order:

1. "Use the director agent on this /after-hours-message event: $ARGUMENTS"
2. "Use the inbox agent on work/briefs/<inbox brief>"
3. "Use the director agent to process returns for the /after-hours-message event"
4. If the director wrote a reputation brief: "Use the reputation agent on work/briefs/<reputation brief>", then the director again.

## 3. What waits for the owner

- Any wording beyond the FAQ answers and reply scripts.
- Anything about money: prices, refunds, discounts, compensation, or dates not in the FAQ.
- A complaint that needs a public reply.
- Until a message role is connected, replies are written as `[READY TO PASTE]` for the owner to send.

## 4. Log example

```
2026-11-01 22:47 | inbox | after-hours lead, holding reply + booking link, CRM note ready to paste, URGENT A-20261101-01 | work/2026-11-01-inbox-saturday-service-request.md
```

## 5. What the owner gets back

- The message, its kind, and the reply that was sent or is ready to paste.
- The CRM note or new contact.
- An `URGENT` pending item for a real lead or a problem; nothing for questions or spam.

## 6. Never

- Never write an answer that is not in `brand/inbox/faq.md` or `brand/inbox/reply-scripts.md`.
- Never mention a price, refund, discount or date that is not copied from the FAQ.
- Never pretend the reply comes from a person.
- Never create a second CRM record for someone already there.
- Never alert the owner for spam or a plain question.
