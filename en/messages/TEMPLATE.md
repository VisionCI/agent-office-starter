# Message templates

File name: `messages/general/YYYY-MM-DD_<from>-to-<to>_<subject>.md`
Chat doorbell (1–3 lines): `New note for <to>: messages/general/<file>.md — <one-line why>.`

---

## 1. Request

```
FROM: <agent>   TO: <agent>   DATE: YYYY-MM-DD   STATUS: OPEN
SUBJECT: <short>

What: <the ask, 1–3 lines>
Why: <the goal>
Done when: <acceptance criteria>
Files: <paths>
Deadline: <date or "none">
```

## 2. Delivery (for review)

```
FROM: <builder>   TO: <editor>   DATE: YYYY-MM-DD   STATUS: OPEN
SUBJECT: <deliverable> ready for review

Deliverable: <path or URL>
What changed: <bullets>
How to verify: <steps — open the real thing>
Known limits: <or "none">
```

## 3. Review verdict

```
FROM: <editor>   TO: <builder>   DATE: YYYY-MM-DD   STATUS: OPEN
SUBJECT: Review — <deliverable> — PASS | FIX

Checked against: <the real page/file, with date>
Findings: <numbered, each with source>
Verdict: PASS (ready for human GO) | FIX (list above)
```

## 4. GO request (to the human)

```
TO: human   DATE: YYYY-MM-DD
Action: <exactly what will happen — send / post / pay / delete / publish>
Target: <where>
Verified by: <editor> on YYYY-MM-DD (messages/general/<review file>)
Reply GO to proceed with this exact action.
```

## 5. Watch report

```
FROM: <watcher>   DATE: YYYY-MM-DD
Source: <name/URL>
New since last report: <bullets, each with link + date>  — or "nothing new" (then don't send)
```

When handled: set `STATUS: DONE` and move the file to `archive/`.
