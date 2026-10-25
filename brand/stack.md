# Tool stack

Agents name a role ("the CRM role"), never a product. This file says which real tool fills each role and how its data reaches Keelpost.
Fill one row per role you use. Write `none` in the tool column for roles you do not have; agents then skip that work or write `[READY TO PASTE]` text for you.

**How it connects** is one of:
- `export: <file pattern>`: you drop a file into `data/` with that name, for example `rank-tracker-positions-YYYY-MM-DD.csv`.
- `mcp: <server name>`: a live connection you have added. Agents read it the same way as the export it replaces.
- `none`: nothing arrives automatically. Agents that would act through this role write `[READY TO PASTE]` instead.

If a live connection fails, the agent logs it and falls back to the newest export.

## Publishing and messages

| role | tool | how it connects | refresh |
| --- | --- | --- | --- |
| scheduler | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| blog | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| local listing | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| CRM | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| chat bot | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| SMS | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| shared inbox | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| review tool | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| booking link | {{fill: tool and the link itself}} | {{fill: export / mcp / none}} | {{fill: how often}} |

## Search and market

| role | tool | how it connects | refresh |
| --- | --- | --- | --- |
| search console | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| rank tracker | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| analytics | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| backlinks | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| site crawler | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| mentions monitor | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| audience research | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| traffic estimates | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| alerts | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |

## Visuals and video

| role | tool | how it connects | refresh |
| --- | --- | --- | --- |
| template graphics | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| image generator | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| layout tool | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| code-built video | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| voice-over | {{fill: tool, and the voice you chose or [OWNER PICKS]}} | {{fill: export / mcp / none}} | {{fill: how often}} |

## Reporting

| role | tool | how it connects | refresh |
| --- | --- | --- | --- |
| dashboards | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| data warehouse | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| reporting tool | {{fill: tool (also the source for ad results and spend)}} | {{fill: export / mcp / none}} | {{fill: how often}} |
| content optimiser | {{fill: tool}} | {{fill: export / mcp / none}} | {{fill: how often}} |

## Example (Harbor Lane Bikes, delete when done)

| role | tool | how it connects | refresh |
| --- | --- | --- | --- |
| rank tracker | the shop's rank-tracking service | export: rank-tracker-positions-YYYY-MM-DD.csv | weekly, Monday |
| review tool | the shop's review dashboard | export: review-tool-reviews-YYYY-MM-DD.csv | daily |
| CRM | none | none | - |
