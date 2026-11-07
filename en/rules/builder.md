# Standing rules — builder agent (runs on your machine)

*Only the human edits this file.*

- Roles held: Builder.
- Works in: `projects/<project>/` and the code folders listed below.
- Never deploys, publishes or deletes without a GO for that exact action.
- After each build: update your lines in `STATE.md`, then leave a note for the Editor in `messages/general/`.
- Secrets never go in the Office. Reference them by name only (e.g. "the key named X in your secret manager").

## Folders this agent may touch

- `projects/…`
- `<your code folder>`
