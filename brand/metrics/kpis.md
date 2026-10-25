# KPIs

What success means, how each number is defined, and what counts as normal. The analyst reports every KPI against this file; the director uses it to score jobs; `/post-breakout` uses the breakout threshold.
How to use: pick one main number first. Then define each KPI precisely enough that two people would get the same figure from the same export.

## The one main number

{{fill: The single number that tells you whether marketing is working, with its definition and source.}}

> Example (Harbor Lane Bikes): booked services per month, counted from the booking link role's export (data/booking-link-bookings-YYYY-MM-DD.csv).

## KPIs per agent

| agent | KPI | definition | source (export pattern) | target | review date |
| --- | --- | --- | --- | --- | --- |
| writer, scheduler | {{fill: e.g. saves per post}} | {{fill: ...}} | {{fill: e.g. scheduler-posts-YYYY-MM-DD.csv}} | {{fill: ...}} | {{fill: YYYY-MM-DD}} |
| search-watch | {{fill: e.g. organic sessions to top pages}} | {{fill: ...}} | {{fill: analytics-sessions-YYYY-MM-DD.csv}} | {{fill: ...}} | {{fill: ...}} |
| reputation | {{fill: e.g. average rating, reply time}} | {{fill: ...}} | {{fill: review-tool-reviews-YYYY-MM-DD.csv}} | {{fill: ...}} | {{fill: ...}} |
| inbox | {{fill: e.g. leads recorded, first reply time}} | {{fill: ...}} | {{fill: shared-inbox-messages-YYYY-MM-DD.csv}} | {{fill: ...}} | {{fill: ...}} |
| analyst | {{fill: e.g. cost per booked service}} | {{fill: ...}} | {{fill: reporting-tool-spend-YYYY-MM-DD.csv}} | {{fill: ...}} | {{fill: ...}} |

## Normal performance per channel

"Normal" is the median of the last {{fill: e.g. 12}} posts on that channel. A post **breaks out** when it beats the breakout threshold below.

| channel | main post metric | normal (median) | breakout threshold | audience check |
| --- | --- | --- | --- | --- |
| instagram | {{fill: e.g. reach}} | {{fill: ...}} | {{fill: e.g. 3x normal within 72 hours}} | {{fill: e.g. 60%+ of reach in our area}} |
| linkedin | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| facebook | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| tiktok | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| blog | {{fill: e.g. sessions in first 7 days}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| instagram (example, Harbor Lane Bikes) | reach | 900 | 3x normal within 72 hours | 60%+ of reach within 10 miles |

A post that beats the threshold but fails the audience check is noted, not treated as a breakout.

## Weekly report contents

The analyst's `work/YYYY-MM-DD-metrics-<period>.md` always has, in this order:

1. data sources and dates, with `[NO DATA]` and stale feeds listed
2. the main number: this period, last period, target
3. KPI table: this period, last period, target, status
4. cost per result per channel, with within / close / over
5. total spend against the caps in `settings/spend-limits.md`
6. best and worst content by the main post metric; repurpose candidates
7. pending items it raised
