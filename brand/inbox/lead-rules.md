# Lead rules

What counts as a lead, who handles each kind of message, and when the owner is alerted. If these rules are empty, `/after-hours-message` treats every message as a lead and asks you to fill this file.
How to use: fill opening hours first, since "out of hours" depends on them. Then decide which intents get the booking link and which wake you up.

## Opening hours

Time zone: {{fill: e.g. Europe/London}}

| day | open | close |
| --- | --- | --- |
| Monday | {{fill: ...}} | {{fill: ...}} |
| Tuesday | {{fill: ...}} | {{fill: ...}} |
| Wednesday | {{fill: ...}} | {{fill: ...}} |
| Thursday | {{fill: ...}} | {{fill: ...}} |
| Friday | {{fill: ...}} | {{fill: ...}} |
| Saturday | {{fill: ...}} | {{fill: ...}} |
| Sunday | {{fill: or closed}} | {{fill: ...}} |
| Harbor Lane Bikes example (delete) | Tue to Sat 09:00 | 18:00, Thu 20:00 |

## Intents

| intent | example | handler | channel for the reply | response time |
| --- | --- | --- | --- | --- |
| question | "Do you sell kids' helmets?" | inbox agent, FAQ answer only | same as received | {{fill: ...}} |
| lead | "Can you service my bike this week?" | inbox agent + owner | same as received | {{fill: ...}} |
| support problem | "My gears are slipping since the service." | owner | same as received, holding reply first | {{fill: ...}} |
| complaint | "Nobody called me back." | director, then reputation | holding reply only | {{fill: ...}} |
| spam | sales pitches, links, nonsense | none | no reply | - |

The examples are for Harbor Lane Bikes, a fictional shop. Unclear messages are treated as leads.

## Tests for a real lead

A message is a real lead when it passes {{fill: e.g. "at least 2"}} of these:

1. Asks about a service or product we sell.
2. Mentions a time frame ("this week", "before Saturday").
3. Gives a way to reach them (phone, email, or the channel itself allows replies).
4. {{fill: your own test}}

## Booking link

Offer the booking link from `brand/stack.md` when: {{fill: e.g. "the lead names a service and a time frame"}}. Use the booking-link script in `brand/inbox/reply-scripts.md`.

## Alerting the owner

| when | how |
| --- | --- |
| real lead, in hours | {{fill: e.g. pending item}} |
| real lead, out of hours | `URGENT` pending item |
| support problem | {{fill: e.g. pending item; URGENT if out of hours}} |
| question or spam | no alert |

## CRM rules

1. Look up the person in the CRM role by email, then phone.
2. Found: add a note with the date, channel and their first message.
3. Not found: create one contact with only what they told us, plus source channel and first message.
4. One contact per person. Never duplicate, merge or delete records.
5. If the CRM role is `none` in `brand/stack.md`, write the note or new contact as `[READY TO PASTE]` in the inbox report.

## Never

- Never quote a price, discount, refund or date that is not in `brand/inbox/faq.md`.
- Never add anyone to a mailing list.
- Never message someone who has not contacted us.
- {{fill: your own, or "none"}}
