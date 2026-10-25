# Keelpost

Keelpost is a set of Claude Code agents and commands that does the routine marketing work of a small business: it plans the week's posts, drafts them in your voice, keeps an eye on search and competitors, drafts review and inbox replies, and reports what worked. It runs entirely on Markdown files in this folder. You set the rules once in `settings/`, drop your tool exports into `data/`, and run one command a week. Anything that costs money, answers an unhappy customer, names a real person or mentions a price lands in `approvals/pending.md` for you to tick. Nothing is posted, spent or sent that your rules do not allow.

## What is in the folder

| path | what it is |
| --- | --- |
| `CLAUDE.md` | the rules every agent follows |
| `.claude/agents/` | ten agents: director (lead), search-watch, rival-watch, writer, designer, scheduler, reputation, inbox, analyst, setup-check |
| `.claude/commands/` | `/weekly-run`, `/setup-check` and eight event commands |
| `settings/` | your four rule files: voice, spend limits, approvals, strategy |
| `brand/` | the knowledge base the agents read (see `brand/README.md`) |
| `brand/stack.md` | which real tool you use for each job, and how it connects |
| `data/` | where you drop exports from your tools |
| `work/` | briefs, drafts and reports the agents write |
| `approvals/` | what waits for you, and what failed a voice check |
| `logs/actions.md` | a dated entry for each thing an agent did |

## Getting going

1. Start Claude Code inside this folder.
2. Fill in the four files in `settings/`. Replace every `{{fill: ...}}` with your answer and delete the Harbor Lane Bikes examples as you go.
3. Fill the first-run brand files: `brand/identity/voice.md`, `brand/identity/tone-rules.md`, `brand/identity/positioning.md`, `brand/identity/claims.md`, and `brand/content/calendar.md` with at least one row marked `ready`. Also fill the length rule for at least one channel in `brand/channels/channel-rules.md`.
4. Fill `brand/stack.md` with the tools you use. Leave a role as `none` if you do not have it.
5. Run `/setup-check`. Fix whatever it lists.
6. Drop your exports into `data/`, named `<role>-<what>-YYYY-MM-DD.csv` (for example `search-console-queries-2026-10-19.csv`).
7. Run `/weekly-run`. It prints a list of hand-offs; run them one at a time as it tells you.
8. Open `approvals/pending.md` and `approvals/voice-holds.md`. Tick yes or no on each item and add a comment if you want.
9. Ask: "Use the director agent to process approvals." It acts on your ticks and moves them to Closed.

When something happens mid-week, use an event command, for example `/bad-review` followed by the review text, or `/after-hours-message` followed by the message.

## How to pause

Create an empty file called `settings/PAUSE`. Every agent and command will stop, write one log line, and tell you it is paused. Delete the file to resume. No agent can create or remove it.

## Connecting REA (optional)

REA lets the rival-watch agent look at a competitor's public page and compare screenshots over time. `.mcp.json` already registers it for Windows:

```json
{"mcpServers":{"rea":{"command":"cmd","args":["/c","npx","-y","rea-agents@6.3.0","mcp"]}}}
```

On macOS or Linux, change the entry to `"command": "npx", "args": ["-y", "rea-agents@6.3.0", "mcp"]`.

Before using it, start a separate Chrome profile that is signed in to nothing, with `--remote-debugging-port=9222`. REA is only for public pages: no logins, no scripts, no code. If REA is not running, rival-watch logs that and carries on without it.

## License

Free for noncommercial use under the PolyForm Noncommercial License 1.0.0 (`LICENSE.md`).
Commercial use, including running it for a business, needs a separate license. See `NOTICE.md`.

A walkthrough of a demo week is at https://jnani1972.github.io/keelpost/.
