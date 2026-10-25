# Credit rules

How a result (a booking, a lead, a sale) gets credited to a post or a channel. The analyst follows these rules exactly; anything they do not cover is reported as unattributed rather than guessed.
How to use: choose one model and stick with it for at least a quarter, so periods can be compared. List your blind spots honestly; they explain the unattributed line.

## Model

{{fill: Which model you use: last click, first click, or "source the customer told us". One line on why.}}

| model | fits when |
| --- | --- |
| last click | most customers book soon after one visit |
| first click | you care most about how people first found you |
| told us | you ask every customer "how did you hear about us?" and record it |

> Example (Harbor Lane Bikes): "told us", because most bookings happen at the counter and staff ask every customer.

## Where each result is counted

| result type | counted in | export pattern |
| --- | --- | --- |
| {{fill: e.g. booked service}} | {{fill: e.g. booking link role}} | {{fill: booking-link-bookings-YYYY-MM-DD.csv}} |
| {{fill: e.g. lead}} | {{fill: e.g. CRM role}} | {{fill: crm-contacts-YYYY-MM-DD.csv}} |

## Link tags

Every link in a post carries tags so the analytics role can credit it.

- source = the channel name from `CLAUDE.md` (instagram, facebook, ...)
- medium = {{fill: e.g. social, email, listing}}
- campaign = the calendar row id, for example `C-014`

> Example (Harbor Lane Bikes): `https://example.com/book?utm_source=instagram&utm_medium=social&utm_campaign=C-014`

## Known blind spots

{{fill: Results you cannot trace: walk-ins, phone calls, word of mouth, people who screenshot a post.}}

## Never

- Never credit a result to a post without a rule above that supports it.
- Never move results from unattributed to a channel to make it look better.
- Never change these rules mid-quarter without noting the date in the metrics report.
