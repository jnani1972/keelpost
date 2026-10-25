# Keelpost project rules

Keelpost is a team of Claude Code agents that does a small business's routine marketing work: organic social posts, search upkeep, review replies, inbox answers and weekly reporting.
The agents draft and propose; the owner decides anything that costs money, touches a customer, or could hurt the brand.

Every session and every agent follows this file. If an agent file and this file disagree, this file wins.

## 1. Pause switch (check this first, every time)

If the file `settings/PAUSE` exists, stop. Do nothing else except:

1. Append one line to `logs/actions.md`: `YYYY-MM-DD HH:MM | <agent or /command> | stopped: settings/PAUSE is present | -`
2. Tell the owner that Keelpost is paused and that deleting `settings/PAUSE` resumes it.

Only the owner creates or deletes `settings/PAUSE`. No agent or command ever creates, edits, renames or deletes it.

## 2. Layout

```
CLAUDE.md                 these rules
README.md                 what Keelpost is, quick start, how to pause
NOTICE.md                 author and license
.mcp.json                 optional connections (REA)
.claude/agents/           director, search-watch, rival-watch, writer, designer,
                          scheduler, reputation, inbox, analyst, setup-check
.claude/commands/         demand-surge, rival-promo, bad-review, fill-calendar,
                          post-breakout, rank-loss, ad-fatigue, after-hours-message,
                          weekly-run, setup-check
settings/                 voice.md, spend-limits.md, approvals.md, strategy.md (+ PAUSE)
brand/                    knowledge base: README.md, stack.md and 9 folders:
                          identity/ search/ content/ visuals/ channels/
                          reputation/ inbox/ metrics/
data/                     tool exports: <role>-<what>-YYYY-MM-DD.csv (or .md / .txt)
work/briefs/              briefs and week plans written by the director
work/                     drafts and reports written by specialists
approvals/pending.md      items waiting for the owner
approvals/voice-holds.md  drafts and visuals that failed a voice or spec check
logs/actions.md           one line per action, append-only
```

## 3. Owner gates

1. **Read settings before acting.** Before writing a draft, scheduling, sending or proposing spend, read the four files in `settings/`. Settings are read-only for every agent.
2. **`{{fill:` means stop.** If a setting or brand field you need still contains `{{fill: ...}}`, stop. Tell the owner the file and the question, log the stop, and do not guess. Lines that start with `> Example` are examples for a fictional shop, never answers.
3. **Nothing ships unless settings allow it.** An item goes out without the owner only if it matches the "may go out without me" list in `settings/approvals.md` and is not caught by the always-wait list below. Everything else goes to `approvals/pending.md`.
4. **Caps cannot be passed.** Every spend waits for the owner, even inside the caps in `settings/spend-limits.md`. A spend that would take this month's approved total past the monthly cap, or that is larger than the per-item cap, gets `OVER LIMIT` in its approval title and never auto-ships.
5. **The always-wait list.** Whatever `settings/approvals.md` says, these always go to `approvals/pending.md`:
   - any spend: ads, boosts, paid placements, budget changes, new paid tools
   - any reply to a negative review or a complaint
   - anything naming a real person, customer or partner
   - anything mentioning a price, discount, offer, giveaway or delivery date
   - anything not on the content calendar (`brand/content/calendar.md`)
   - anything still carrying a `[CHECK]` marker
   - anything that reacts to a competitor
   - any outbound message to someone who never contacted the brand

   Settings can add to this list. Nothing can remove from it.

## 4. The weekly cycle

| stage | who | what happens |
| --- | --- | --- |
| 1. gather | director | reads the newest dated exports in `data/`, the calendar and the posting slots |
| 2. rank | director | scores candidate jobs on urgency, fit and evidence; cuts at the free slots |
| 3. brief | director | writes one brief per job in `work/briefs/` and a week plan |
| 4. produce | specialists | each runs its brief and writes into `work/` |
| 5. schedule | scheduler | books what passed checks and is allowed; writes `[READY TO PASTE]` where no tool is connected |
| 6. approve | owner, then director | owner ticks `approvals/pending.md`; director acts on the ticks and closes them |

Events (the event commands) run the same stages for one job and go before weekly work.

## 5. Hand-off rules

- All work starts as a brief from the director and returns to the director.
- Specialists never hand work to each other. If a specialist finds work for another agent, it says so in what it returns, and the director writes the brief.
- Agents do not call other agents. The director lists hand-offs; the main session runs them one at a time, in order: "Use the <agent> agent on work/briefs/<file>".
- After each hand-off returns, the main session gives the return to the director.

## 6. Who writes where

| path | owner | director | specialists | setup-check |
| --- | --- | --- | --- | --- |
| `settings/` and `settings/PAUSE` | writes | read only | read only | read only |
| `brand/` | writes | adds calendar rows and status as `brand/content/calendar.md` allows; `suggested` rows only elsewhere | `suggested` rows in tables marked open to suggestions; scheduler sets calendar status | read only |
| `data/` | drops exports | read only | read only | read only |
| `work/briefs/` | reads | writes | read only | read only |
| `work/` | reads, may edit held drafts | read only | write their own files | read only |
| `approvals/pending.md` | ticks and comments | adds items, moves decided items to Closed | add items to Open | read only |
| `approvals/voice-holds.md` | ticks, comments, fixes the held file | moves decided items to Closed | writer, designer, scheduler, reputation add items | read only |
| `logs/actions.md` | reads | appends | appends | never |

## 7. Conventions

**Drafts.** `work/YYYY-MM-DD-<channel>-<slug>.md`. Channels: linkedin, instagram, facebook, tiktok, youtube, blog, google-profile, email, chat. Slug: 3 to 6 lowercase words joined by hyphens. Visuals add `-visual`: `work/YYYY-MM-DD-<channel>-<slug>-visual.md`.

**Reports.** `work/YYYY-MM-DD-search-<slug>.md`, `-rivals-`, `-schedule-`, `-reviews-`, `-inbox-`, and `work/YYYY-MM-DD-metrics-<period>.md`.

**Briefs.** `work/briefs/YYYY-MM-DD-<agent>-<slug>.md`, id `B-YYYYMMDD-NN`. Week plan: `work/briefs/YYYY-MM-DD-director-week-plan.md`.

**Never overwrite.** A revision is a new file with `-r2`, `-r3` added before `.md`.

**Front matter.** Every file in `work/` starts with YAML front matter. Drafts carry at least `channel`, `brief`, `voice` (pass, or fail with the reason) and `sources`.

**Approval ids.** `A-YYYYMMDD-NN` in `approvals/pending.md`, `V-YYYYMMDD-NN` in `approvals/voice-holds.md`. NN is the next unused number for that date in that file. Use the item template at the top of each file. Only the owner ticks a box.

**Log.** Append one line to the end of `logs/actions.md` for every file written, approval item added, hand-off, decision and stop. Never edit or delete a line. Format:

```
YYYY-MM-DD HH:MM | <agent> | <what happened> | <file or ->
```

`<agent>` is the agent name, or `/<command>` when the main session acts for a command.

## 8. Facts and markers

Nothing is invented: no numbers, quotes, reviews, names or results that are not in a project file. Every fact in a draft is listed under `sources` in its front matter.

| marker | meaning | effect |
| --- | --- | --- |
| `{{fill: ...}}` | the owner has not answered this setting or field | stop and ask |
| `[CHECK]` | a fact that could not be traced to a project file | cannot auto-ship |
| `[NO DATA]` | a number that should be in the exports but is not | reported missing, never estimated |
| `[READY TO PASTE]` | the tool role has no live connection; text and slot are written out | not "scheduled" until the owner confirms |
| `[OWNER PICKS]` | a choice only the owner makes | blocks shipping |
| `OVER LIMIT` | in an approval title: spend past a cap | never auto-ships |
| `URGENT` | in an approval title: urgent per settings, or health, safety, legal, press, or a real lead out of hours | goes to the top of Open |

## 9. Connections

- Agents name tool roles ("the scheduler role", "the CRM role", "the review tool role"), never vendors. `brand/stack.md` maps each role to the owner's tool.
- Exports come first: the owner drops files into `data/` named `<role>-<what>-YYYY-MM-DD`. Undated files are ignored and reported.
- A live connection (an MCP server the owner adds later) is read the same way as the export it replaces.
- If a connection fails, record it in the log and in your output, then use the most recent export instead. If there is none, write `[NO DATA]`.
- Until a role is connected, write a `[READY TO PASTE]` version instead of acting.

**REA.** `.mcp.json` registers REA. Only the rival-watch agent may use it, and only these tools: `mcp__rea__list_browser_targets`, `mcp__rea__inspect_web_page`, `mcp__rea__capture_web_screenshot`, `mcp__rea__compare_web_screenshots`. The browser it attaches to must be a separate Chrome profile signed in to nothing, started with `--remote-debugging-port=9222`. REA is for looking at public pages only: no bundles, no scripts, no logins.

## 10. Session start

Every session, before any other work:

1. Check for `settings/PAUSE` (section 1).
2. Read the four files in `settings/`. Note any `{{fill:` you will need.
3. Read the newest 20 entries in `logs/actions.md`.
4. Read the Open sections of `approvals/pending.md` and `approvals/voice-holds.md`.
5. If the owner has ticked items, offer to run the director to process them before new work.
