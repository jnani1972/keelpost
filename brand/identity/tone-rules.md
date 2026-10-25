# Tone rules

The checklist every draft is tested against before it can ship. Each rule must be checkable: someone reading the draft can say yes or no without guessing.
How to use: add rules as one line each. When a draft fails, the agent quotes the rule from this file in `approvals/voice-holds.md`, so write rules you are happy to see quoted.

## Always

| id | rule | how to check |
| --- | --- | --- |
| T-01 | {{fill: rule}} | {{fill: what to look for}} |
| T-02 | {{fill: rule}} | {{fill: what to look for}} |
| T-03 | {{fill: rule}} | {{fill: what to look for}} |
| T-ex | Every post gives one concrete next step. (example, Harbor Lane Bikes) | last two lines contain an action the reader can take |

## Banned words

| word or phrase | use instead |
| --- | --- |
| {{fill: word}} | {{fill: replacement}} |
| {{fill: word}} | {{fill: replacement}} |
| cheap (example, Harbor Lane Bikes) | "good value", or give the price with its FAQ source |

## Banned behaviours

These three are fixed. Add your own below them.

1. Inventing facts, numbers, quotes, reviews or results.
2. Mocking or belittling competitors.
3. Tagging or naming people or companies without their permission.
4. {{fill: your own, or "none"}}

## Off-limits topics

| topic | what to do instead |
| --- | --- |
| {{fill: topic}} | {{fill: alternative angle, or "skip the job"}} |
| Road-safety blame after a local accident (example, Harbor Lane Bikes) | post nothing about it; carry on with the calendar |

## Sensitive moments

{{fill: What changes when there is bad local news, a national tragedy, or a problem at your business? Who decides when to stop posting?}}

> Example (Harbor Lane Bikes): On a day of serious local news, scheduled posts are held and the owner decides when to restart. Nothing jokey for a week.

## Pass or fail

A draft **passes** when it breaks no rule in this file and none in `settings/voice.md`.
A draft **fails** on the first broken rule. The agent:

1. sets `voice: fail: <rule id or quoted rule>` in the draft's front matter,
2. adds a `V-YYYYMMDD-NN` item to `approvals/voice-holds.md` quoting the rule and the exact failing line,
3. stops work on that draft and logs the hold.

The agent does not quietly rewrite a failed line and pass it.
