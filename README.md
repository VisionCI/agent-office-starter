# Agent Office — starter kit

*[Version française → README.fr.md](README.fr.md)*

A shared-folder pattern for running two (or more) AI agents together — typically one in your chat app and one on your machine (e.g. Claude Code). They can't talk to each other directly, so they share a folder: **the Office**. Each task is a file; the chat is only the doorbell; the file is the truth. Nothing goes out without your GO.

Generic on purpose: no private data, no real names — just the pattern.

## Quick start

```bash
git clone https://github.com/VisionCI/agent-office-starter.git
cp -r agent-office-starter/en "Agent Office"     # or fr/ -> "Bureau des Agents"
```

Then paste [`en/START-PROMPT.md`](en/START-PROMPT.md) into each agent, once.

## The 6 rules

1. **One subject = one place.** A topic lives in exactly one file. Never two copies.
2. **The chat is the doorbell.** A message is 1–3 lines: what it is, where the file is. Never the content itself.
3. **The file rules.** If the chat and the file disagree, the file wins.
4. **One owner per deliverable.** One agent builds it; the other reviews it. Never two builders.
5. **Nothing external without a GO.** No send, no post, no payment, no delete without your explicit go-ahead for that exact action.
6. **Cite every fact.** Every claim carries its source file and date. A claim without a source is a guess.

## What's in the box

```
en/                          fr/
  00_READ-ME.md                00_LISEZ-MOI.md        <- the rules, in full
  STATE.md                     ETAT.md                <- what's in flight right now
  REGISTRY.md                  REGISTRE.md            <- decisions log (append-only)
  START-PROMPT.md              AMORCE.md              <- paste into each agent once
  rules/                       regles/
    roles.md                     roles.md             <- the 4 roles
    builder.md                   constructeur.md      <- standing rules per agent (only you edit)
    operator.md                  operateur.md
  messages/                    messages/
    TEMPLATE.md                  GABARIT.md           <- message templates
    general/                     general/             <- the doorbell notes
  projects/<project>/          projets/<projet>/      <- one folder per project
  archive/                     archive/               <- done messages, old states
```

## Token economy

An Office that keeps growing gets slow and expensive ("context creep"). [`docs/token-economy.md`](docs/token-economy.md) has 15 testable rules: read only STATE + your rules + the 2 latest messages, cap STATE, auto-archive after 30 days, fresh session per work item, logs over screenshots, scripts over repeated AI work, model routing, budgets and brakes on every loop.

## The 4 roles

| Role | Job | Usually lives in |
|---|---|---|
| Strategist | Decides what to do, in what order. Owns the plan. | Chat agent |
| Builder | Makes it — code, pages, files. | Machine agent |
| Watcher | Checks sources on a schedule, reports only what's new. Silence otherwise. | Chat agent (scheduled) |
| Editor | Verifies before anything goes out. Reads the real thing, never the summary. | Chat agent |

## The daily loop

Morning: the Watcher reports what's new. Day: the Strategist picks the work, the Builder builds, the Editor verifies. Evening: one short debrief — what shipped, what's blocked, what needs your GO.

## Start tonight

1. Copy the folder.
2. Paste the start prompt into each agent.
3. Pick ONE watch — the smallest useful one.
4. Publish nothing until the Editor rule has caught one mistake. It will.

---

Made by [Vision CI](https://visionci.ca) — Québec. Videos: [@visionaivideo](https://www.instagram.com/visionaivideo/).
Licensed [CC BY 4.0](LICENSE): reuse and adapt freely, keep the credit.
