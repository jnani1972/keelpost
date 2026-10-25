# Approval rules

Your rules for what ships on its own and what needs you. Agents read this before shipping anything and never edit it.
Replace each placeholder (double curly braces starting with the word fill) with your answer. Write "none" if you have nothing to add. Lines starting with `> Example` are for a fictional shop, Harbor Lane Bikes; delete each one once your own answer is in. Agents ignore examples.

## 1. May go out without me

These are already filled in. Delete any you do not want.

- Routine organic posts that are on the calendar, passed the voice check, and have no open `[CHECK]`, `[OWNER PICKS]` or other marker, booked into a normal slot.
- Replies to good reviews that only say thank you (no offer, no promise, no names).
- Inbox answers copied word for word from `brand/inbox/faq.md`.

Your additions:

{{fill: Anything else that may go out without you? Write "none" if nothing.}}

> Example (Harbor Lane Bikes): Google profile posts announcing our normal opening hours.

## 2. Always waits for me

These are fixed in `CLAUDE.md` and cannot be removed here:

- any spend: ads, boosts, paid placements, budget changes, new paid tools
- any reply to a negative review or a complaint
- anything naming a real person, customer or partner
- anything mentioning a price, discount, offer, giveaway or delivery date
- anything not on the content calendar
- anything still carrying a `[CHECK]` marker
- anything that reacts to a competitor
- any outbound message to someone who never contacted the brand

Your additions:

{{fill: Anything else that must always wait for you? Write "none" if nothing.}}

> Example (Harbor Lane Bikes): any post about e-bikes, until our e-bike servicing is fully launched.

## 3. What is urgent

Health, safety, legal threats, press enquiries and real leads that arrive out of hours are always urgent.

Your additions:

{{fill: What else should be marked URGENT and put at the top of the list? Write "none" if nothing.}}

> Example (Harbor Lane Bikes): any message from the landlord or the council.

## 4. Channels where nothing auto-ships

{{fill: Channels where every item waits for you, even routine posts. Use the channel names in CLAUDE.md, or write "none".}}

> Example (Harbor Lane Bikes): linkedin, email.

## 5. How often I review

{{fill: How often will you open approvals/pending.md? Agents use this to judge whether to mark something URGENT.}}

> Example (Harbor Lane Bikes): Every weekday at 9am, and Saturday lunchtime.
