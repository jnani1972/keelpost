# Reply scripts

Fixed messages the inbox agent sends around the FAQ answers: the greeting, the holding reply, the booking-link reply. It never improvises between them.
How to use: write each message exactly as it should be sent. Keep `{name}` out of scripts; the agent fills only `{faq answer}`, `{booking link}` and `{opening time}` from project files.

## How the bot introduces itself

{{fill: One line, e.g. "Hi, this is the Harbor Lane Bikes assistant. A person reads every message."}}

Rule: the bot never pretends to be a person.

## Scripts

| id | trigger | message | next step |
| --- | --- | --- | --- |
| SC-01 | question with an FAQ answer | {{fill: e.g. "Thanks for asking. {faq answer}"}} | none |
| SC-02 | out of hours, holding reply | {{fill: e.g. "Thanks for your message. We're closed right now and will reply after we open at {opening time}."}} | owner or inbox agent replies in hours |
| SC-03 | in hours, holding reply (no FAQ answer, problem, complaint) | {{fill: e.g. "Thanks for getting in touch. Someone from the team will reply today."}} | owner replies |
| SC-04 | lead ready to book | {{fill: e.g. "You can pick a time here: {booking link}"}} | lead noted in CRM role |
| SC-05 | {{fill: your own}} | {{fill: ...}} | {{fill: ...}} |

> Example (Harbor Lane Bikes): SC-02 reads "Thanks for your message. The workshop is closed now; we'll reply after we open at 09:00."

## Rules

1. Send one script per message, plus the FAQ answer when SC-01 applies.
2. A message is not changed except for the three fill-ins above.
3. If the reply fails the voice check, send SC-02 or SC-03 instead and note the failure.
4. Spam gets no reply.
5. Never put a price, discount or date into a script unless it is copied from `brand/inbox/faq.md`.
