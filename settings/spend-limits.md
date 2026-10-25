# Spend limits

The money rules. Agents read this before proposing any spend and never edit it.
Replace each placeholder (double curly braces starting with the word fill) with your answer. Lines starting with `> Example` are for a fictional shop, Harbor Lane Bikes; delete each one once your own answer is in. Agents ignore examples.

**Every spend waits for you, even inside these caps.** The caps decide whether an item is also marked `OVER LIMIT`; they never let an agent spend on its own.

## 1. Monthly cap

{{fill: The most you will spend on marketing in one calendar month, with currency.}}

> Example (Harbor Lane Bikes): 300 GBP per month.

## 2. Cap per single item

{{fill: The most any one ad, boost or purchase may cost, with currency.}}

> Example (Harbor Lane Bikes): 60 GBP per item.

## 3. Channels allowed to spend

{{fill: Which channels may ever carry paid spend? List them using the channel names in CLAUDE.md.}}

> Example (Harbor Lane Bikes): instagram, facebook.

## 4. Spend that is never allowed

{{fill: Kinds of spend you never want proposed at all.}}

> Example (Harbor Lane Bikes): paid followers, paid reviews, influencer fees, any tool subscription over 20 GBP a month.

## 5. When the cap gets close

{{fill: At what point should agents warn you, and what should they do then?}}

> Example (Harbor Lane Bikes): At 80% of the monthly cap, the analyst adds a pending item; no new spend is proposed until I reply.

## 6. Date last changed

{{fill: The date you last changed this file, as YYYY-MM-DD.}}

> Example (Harbor Lane Bikes): 2026-10-01.

## How agents use this file

- The director adds up the spend on items ticked yes in the Closed section of `approvals/pending.md` for this calendar month.
- If a new spend would take that total past the monthly cap, or is larger than the per-item cap, its approval title gets `OVER LIMIT`.
- Spend on a channel not listed in section 3, or of a kind in section 4, is not proposed. The agent notes it in its output instead.
