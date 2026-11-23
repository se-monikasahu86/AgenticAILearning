# Feature lifecycle

## The files of a feature

Each feature has its own folder: `work/features/F###-<short-name>/`.

| File | Written by | Content |
|---|---|---|
| `story.md` | Developer | Status, user story, acceptance criteria, approvals |
| `plan.md` | Developer | Research notes, tasks, how each criterion will be verified |
| `review.md` | Developer | What changed and the evidence for each criterion |
| `baseline/` | Developer | Copies of existing files taken before their first edit |
| `qa-1.md`, `qa-2.md`… | QA | One report per QA round |

## Statuses

| Status | Who works | What happens | Moves on when |
|---|---|---|---|
| DRAFT | Developer | Writes the story and measurable acceptance criteria, asks questions | The human says "I approve the story." → PLANNING |
| PLANNING | Developer | Reads the context and the code, writes `plan.md` | The human says "I approve the plan." → IMPLEMENTING |
| IMPLEMENTING | Developer | Does all tasks without asking again, runs the tests, ticks criteria with evidence | All criteria ticked → QA |
| QA | QA | Re-runs the checks, reviews the code against the criteria and the coding rules | PASS → DONE, FAIL → REWORK |
| REWORK | Developer | Fixes the QA findings, refreshes the evidence | → QA |
| DONE | — | Set by QA only | — |

Any status can become BLOCKED: write the reason and what is needed. If the human asks to cancel a feature, QA sets it to CANCELLED and keeps the unfinished criteria visible.

## Developer rules

- Stop at the two approval points. Between them, do not ask for "go".
- If the story or the plan must change after approval, show the change and ask for approval again.
- Before the first edit of an existing file, copy it to `baseline/`, so that "unchanged" criteria can be checked.
- A check that needs a human (look at the screen, use a device): ask the human, then record their answer as evidence.
- When all criteria are ticked, set the status to QA and invoke the QA agent. If you cannot, tell the human: "Open a new chat with the QA agent and ask: Review the open feature."
- After two failed attempts at the same problem, stop and ask.

## QA rules

- Work only on a feature in QA status. Never create a feature, never change production code or tests.
- Re-run the tests yourself. Do not trust a tick without evidence.
- Check the code against the acceptance criteria and the coding rules. Compare with `baseline/` for "unchanged" criteria.
- Write `qa-<round>.md` from the template. Never overwrite an earlier round or the Developer's files.
- PASS: set DONE. FAIL: set REWORK and list exactly what must be fixed.
