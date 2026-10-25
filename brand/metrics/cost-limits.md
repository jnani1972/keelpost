# Cost limits

What each channel costs you, what a result is worth, and the line past which a channel is too expensive. The analyst runs the cost check against this file every period. It never changes a budget; it raises a pending item.
How to use: include tool fees and your own hours, not only ad spend, or cheap-looking channels will hide their real cost. The overall caps live in `settings/spend-limits.md` and win over this file.

## Monthly cost per channel

| channel | tools | ads | hours per month | hourly value | total |
| --- | --- | --- | --- | --- | --- |
| {{fill: channel}} | {{fill: amount}} | {{fill: amount}} | {{fill: ...}} | {{fill: ...}} | {{fill: ...}} |
| instagram (example, Harbor Lane Bikes) | 15 GBP | 120 GBP | 6 | 20 GBP | 255 GBP |

Currency: {{fill: must match settings/spend-limits.md}}

## Value of each result type

| result type | value | how you know |
| --- | --- | --- |
| {{fill: e.g. booked service}} | {{fill: amount}} | {{fill: e.g. average job value from the till report}} |
| {{fill: e.g. lead}} | {{fill: ...}} | {{fill: ...}} |

## Cost limit per result

| channel | result type | limit per result |
| --- | --- | --- |
| {{fill: ...}} | {{fill: ...}} | {{fill: amount}} |

## How the cost check works

1. Cost per result = channel total for the period divided by results credited to that channel by `brand/metrics/credit-rules.md`.
2. Compare it with the limit above.
3. If results are `[NO DATA]` or zero, the cost per result is `[NO DATA]`, not infinite and not estimated.

## Flag levels

| level | when | what happens |
| --- | --- | --- |
| within | at or under {{fill: e.g. 80%}} of the limit | reported only |
| close | between {{fill: e.g. 80%}} and 100% of the limit | reported; noted for the director |
| over | above the limit | pending item with one suggested option (pause, cut, or keep with a reason) |

## Never

- Never change a budget, bid, ad or campaign.
- Never estimate a missing cost or result.
- Never change this file's limits to make a channel look within limit.
