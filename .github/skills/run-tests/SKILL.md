---
name: run-tests
description: Use when building or testing a change, or when evidence is needed that the tests pass.
---
# Run the tests and record the evidence

1. Read the commands in the [testing strategy](../../../project-context/testing-strategy.md). If they are missing, ask the human; never guess.
2. Run the full suite from the folder it requires. Never change tests or tolerances to make them pass.
3. If something fails, show the first error. Fix it only if it is part of the current task; otherwise stop and report.
4. Record the evidence in the feature's `review.md` (Developer) or `qa-<round>.md` (QA): the exact command, the result line (for example `32 passed`) and the date.
5. If a check needs a human (screen, device), say exactly what to look at, then record the human's answer as evidence.
