# Token economy — keeping context creep out of the Office

*[Version française → economie-tokens.md](economie-tokens.md)*

Every file an agent reads costs tokens, and every token of old context dilutes the current task. An Office that grows without limits gets slower, costlier and less accurate. These rules keep it lean. Each one is written so you can **test** it.

## A. What an agent reads

| # | Rule | Test |
|---|---|---|
| A1 | **Read the minimum at session start:** `STATE.md` + `rules/<agent>.md` + **only the 2 most recent messages** of the project. Never the whole history. | The start prompt lists exactly these files. An agent that says it "read all messages" failed. |
| A2 | **Open older files only by name**, when a message or `STATE.md` points to them. No browsing. | Every older file an agent opens is cited by path in a recent message or in `STATE.md`. |
| A3 | **One subject = one file.** Update it; never duplicate it. | Searching the subject's name returns one working file (plus its archive). |
| A4 | **Logs, not screenshots.** Prefer text output (log, command result, page text) over images. Screenshot only when the visual layout *is* the question. | Review messages cite a log line or text excerpt, not an image, unless the check is visual. |

## B. What an agent writes

| # | Rule | Test |
|---|---|---|
| B1 | **The chat is the doorbell:** 1–3 lines + the file path. Never paste content into the chat. | No chat message over 3 lines; each one contains a path. |
| B2 | **`STATE.md` is capped** (e.g. 150 lines). Above the cap, compact: summarize what's done in one line each, move details to `archive/STATE-YYYY-MM-DD.md`. | `wc -l STATE.md` ≤ 150. |
| B3 | **Auto-archive messages older than 30 days** (move from `messages/` to `archive/`). | No file in `messages/` has a date older than 30 days. See the script below. |
| B4 | **Short handoff notes** (≤ 15 lines: done / not done / next step / files) instead of stretching a session. | Handoff file exists and is ≤ 15 lines. |

## C. How sessions run

| # | Rule | Test |
|---|---|---|
| C1 | **Fresh session per work item.** One deliverable = one new session that starts from A1. Don't carry a long conversation from task to task. | A new deliverable never starts in a session that already finished another one. |
| C2 | **End a session when it gets long** (e.g. it has summarized/compacted once, or it starts re-reading files it already read): write a handoff (B4), close, restart fresh. | Sessions that compacted twice are rare; each has a handoff note. |
| C3 | **Reusable scripts, not repeated AI work.** If an agent does the same mechanical task twice (rename, check links, archive, format), it writes a script once and runs it next time. | Recurring tasks point to a file in `scripts/` (or your tools folder). |

## D. Which model does what

| # | Rule | Test |
|---|---|---|
| D1 | **Route by task size:** a small/fast model for triage, sorting, watches, yes/no checks; a large model for drafting, architecture, hard reviews. | Each scheduled job states its model; watches never run on the largest model. |
| D2 | **Eco mode:** the chat agent executes routine steps; the code agent only arbitrates (reviews, decides, handles exceptions). Don't spend the expensive agent on mechanical work. | The code agent's session log is mostly reviews/decisions, not routine edits. |

## E. Budgets and brakes

| # | Rule | Test |
|---|---|---|
| E1 | **Every loop has a budget**: max iterations, max time, and/or max spend, written in the task. | No scheduled job or retry loop without a stated limit. |
| E2 | **Brakes:** stop and report when the budget is hit, when the same error repeats twice, or when nothing changed since the last run. Silence beats a repeated report. | Loop logs show a stop reason; no job ran past its limit. |

## Example: 30-day archive script

PowerShell:
```powershell
$office = "<OFFICE PATH>"
$cut = (Get-Date).AddDays(-30)
Get-ChildItem "$office\messages" -Recurse -File -Filter *.md |
  Where-Object { $_.LastWriteTime -lt $cut } |
  ForEach-Object { Move-Item $_.FullName "$office\archive\" }
```

Bash:
```bash
OFFICE="<OFFICE PATH>"
find "$OFFICE/messages" -name '*.md' -mtime +30 -exec mv {} "$OFFICE/archive/" \;
```

Run it on a schedule (weekly is enough), or ask your builder agent to run it at the start of the week.

## Add to the start prompt

```
Token economy: read only STATE.md, rules/<your-agent>.md and the 2 most recent messages. Open older files only when a message names them. Keep chat messages to 1-3 lines with a path. If STATE.md exceeds 150 lines, compact it. Prefer logs to screenshots. If you repeat a mechanical task, write a script. Every loop has a budget; stop when it's hit or nothing changed.
```
