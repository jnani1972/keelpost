# Data feeds

Where each signal comes from and how fresh it must be. search-watch checks every expected export against this file before it reads a single number, and reports gaps instead of filling them.
How to use: one row per signal. File names follow `<role>-<what>-YYYY-MM-DD` with the role from `brand/stack.md`. The date is the day the data runs up to.

## Feeds

| signal | tool role | arrives via | file pattern | refresh | supplied by | read by |
| --- | --- | --- | --- | --- | --- | --- |
| search queries | search console | {{fill: export / mcp}} | search-console-queries-YYYY-MM-DD.csv | {{fill: weekly}} | {{fill: owner}} | search-watch, director |
| rankings | rank tracker | {{fill: ...}} | rank-tracker-positions-YYYY-MM-DD.csv | {{fill: ...}} | {{fill: ...}} | search-watch, rival-watch |
| competitor rankings | rank tracker | {{fill: ...}} | rank-tracker-competitors-YYYY-MM-DD.csv | {{fill: ...}} | {{fill: ...}} | rival-watch |
| sessions per page | analytics | {{fill: ...}} | analytics-sessions-YYYY-MM-DD.csv | {{fill: ...}} | {{fill: ...}} | search-watch, analyst |
| backlinks gained and lost | backlinks | {{fill: ...}} | backlinks-changes-YYYY-MM-DD.csv | {{fill: ...}} | {{fill: ...}} | search-watch |
| site crawl issues | site crawler | {{fill: ...}} | site-crawler-issues-YYYY-MM-DD.csv | {{fill: ...}} | {{fill: ...}} | search-watch |
| mentions | mentions monitor | {{fill: ...}} | mentions-monitor-mentions-YYYY-MM-DD.csv | {{fill: ...}} | {{fill: ...}} | rival-watch, reputation |
| saved alerts | alerts | {{fill: ...}} | alerts-saved-YYYY-MM-DD.md | {{fill: ...}} | {{fill: ...}} | rival-watch |
| audience habits | audience research | {{fill: ...}} | audience-research-topics-YYYY-MM-DD.csv | {{fill: ...}} | {{fill: ...}} | rival-watch |
| competitor traffic | traffic estimates | {{fill: ...}} | traffic-estimates-competitors-YYYY-MM-DD.csv | {{fill: ...}} | {{fill: ...}} | rival-watch |

Other folders use the same naming: reviews (`review-tool-reviews-`), messages (`shared-inbox-messages-`, `chat-bot-messages-`, `sms-messages-`), CRM (`crm-contacts-`), bookings (`booking-link-bookings-`), post results (`scheduler-posts-`), results, ads and spend (`reporting-tool-results-`, `reporting-tool-ads-`, `reporting-tool-spend-`).

## Freshness limits

An export older than its limit is **stale**. Agents still read it but label every number from it `stale` and say so at the top of their report. Missing exports are reported as gaps.

| signal | stale after |
| --- | --- |
| search queries | {{fill: e.g. 8 days}} |
| rankings | {{fill: e.g. 8 days}} |
| sessions per page | {{fill: e.g. 8 days}} |
| backlinks | {{fill: e.g. 35 days}} |
| site crawl | {{fill: e.g. 35 days}} |
| mentions and alerts | {{fill: e.g. 3 days}} |

> Example (Harbor Lane Bikes): queries, rankings and sessions stale after 8 days; crawl and backlinks after 35 days; mentions after 3 days.

## Moving a feed to a live connection

1. Add the MCP server and note it in `brand/stack.md` as `mcp: <server name>`.
2. Keep dropping the export for two weeks and compare the numbers.
3. When they match, change "how it arrives" above to `mcp`. Agents read the connection the same way as the file.
4. If the connection fails, agents log it and use the newest export.
