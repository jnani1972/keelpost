---
description: Check the install. Runs the setup-check agent and prints what is missing, broken or still unfilled. Changes nothing.
argument-hint: (none needed)
---

# /setup-check

Check that Keelpost is installed and filled in enough to run.

Note from the owner (optional): $ARGUMENTS

## 0. Pause check

Glob `settings/PAUSE`. When it is there, add the line `YYYY-MM-DD HH:MM | /setup-check | stopped: settings/PAUSE is present | -` to `logs/actions.md`, tell the owner that Keelpost is paused, and stop. This is the only file this command may write.

## 1. Run the check

"Use the setup-check agent to check this project."

The agent only reads. It checks:

1. every file and folder in the layout in `CLAUDE.md`;
2. front matter of the ten agent files and ten command files;
3. every `{{fill:` left in `settings/`;
4. every `{{fill:` left in the first-run brand files: `brand/identity/voice.md`, `brand/identity/tone-rules.md`, `brand/identity/positioning.md`, `brand/identity/claims.md`, `brand/content/calendar.md`; plus one ready calendar row and one channel length in `brand/channels/channel-rules.md`;
5. leftover sample items and example rows;
6. undated files in `data/`.

## 2. Print the findings

Print the agent's report as it is, in its order:

1. status line (`ready for first run` or `not ready: <n> blocking items`)
2. missing files
3. broken agent or command files
4. unfilled settings, as `file:line question`
5. unfilled first-run brand fields
6. leftover samples and examples
7. undated data files
8. next step

Do not fix anything. Do not fill any `{{fill:` for the owner, even if asked in the same message; say which file to open instead.

## 3. What waits for the owner

Nothing is queued. The owner fixes what is listed and runs `/setup-check` again.

## 4. Log example

This command does not log a normal run, because it changes nothing. The only line it can write is the pause stop:

```
2026-10-25 17:30 | /setup-check | stopped: settings/PAUSE is present | -
```

## 5. What the owner gets back

- One status line saying whether the first run can start.
- A short list of exact files and questions to fill.
- When ready: "Run /weekly-run."

## 6. Never

- Never create, edit or delete any file, other than the pause log line above.
- Never answer a `{{fill:` question for the owner.
- Never run the director or any other agent from this command.
