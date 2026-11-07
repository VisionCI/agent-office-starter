# Agent Office — read me first

This folder is the shared office of your agents. Every agent reads this file at the start of each session.

## The 6 rules

1. **One subject = one place.** A topic lives in exactly one file. Never two copies. Update the file; don't fork it.
2. **The chat is the doorbell.** A chat message is 1–3 lines: what it is, where the file is. Never the content itself.
3. **The file rules.** If the chat and the file disagree, the file wins. If two files disagree, the newest dated entry in `REGISTRY.md` decides.
4. **One owner per deliverable.** One agent builds it; another reviews it. Never two builders on the same file at once.
5. **Nothing external without a GO.** No send, no post, no payment, no delete, no publish without the human's explicit go-ahead for that exact action. A GO is not transferable to a similar action.
6. **Cite every fact.** Every claim carries its source (file path or URL) and its date. A claim without a source is a guess — label it as such.

## Where things go

| What | Where |
|---|---|
| What's in flight right now | `STATE.md` |
| What was decided, when, by whom | `REGISTRY.md` (append-only) |
| Standing rules for one agent | `rules/<agent>.md` (only the human edits) |
| A note from one agent to another | `messages/general/YYYY-MM-DD_from-to_subject.md` |
| Project work | `projects/<project>/` |
| Done / superseded | `archive/` |

## Session start (every agent)

1. Read this file, `STATE.md`, and your own `rules/<agent>.md`.
2. Check `messages/general/` for notes addressed to you with status `OPEN`.
3. Do the work. Update the file you own. Leave a short note if someone else must act.
4. Move handled messages to `archive/`.
