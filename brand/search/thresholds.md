# Search thresholds

The numbers that turn a wobble into an event. Without them, agents cannot tell a real drop from noise, so the event commands stop and ask until these are filled.
How to use: set each threshold as a number plus a time window. Tighten or loosen them after a month of reports.

## Ranking loss

A page counts as dropped when:

{{fill: e.g. "falls 3 or more positions for its assigned keyword, and stays down for 2 checks in a row"}}

> Example (Harbor Lane Bikes): down 3+ positions on two weekly checks in a row, or out of the top 10.

## Surge in search interest

A query counts as surging when:

{{fill: e.g. "impressions up 50% or more week on week, with at least 100 impressions this week"}}

> Example (Harbor Lane Bikes): impressions up 60%+ week on week and at least 80 impressions this week.

## Query movement worth reporting

{{fill: The smallest change in clicks, impressions or position search-watch should list in its weekly report.}}

> Example (Harbor Lane Bikes): clicks or impressions up or down 30%+, or position change of 2+.

## Competitor move in results

A competitor move counts when:

{{fill: e.g. "a watch-list competitor enters the top 5 for one of our main keywords, or gains 5+ positions"}}

## Result features wanted per page

| owning URL | feature wanted (map pack, FAQ, image, video, review stars, none) |
| --- | --- |
| {{fill: URL}} | {{fill: ...}} |

## Severity

| level | when | who hears | how fast |
| --- | --- | --- | --- |
| low | {{fill: e.g. one keyword moved, no sessions lost}} | weekly report only | next weekly run |
| medium | {{fill: e.g. a top page dropped}} | owner, via a pending item | {{fill: e.g. within 2 days}} |
| high | {{fill: e.g. a page lost most of its sessions, or is blocked from search}} | owner, `URGENT` pending item | {{fill: e.g. same day}} |

## Never

- Never treat a single check as a trend unless it crosses the high level.
- Never estimate a number that is missing from the exports: write `[NO DATA]`.
- Never change a threshold to make an event go away. Only the owner edits this file.
