# Framework rules

This repository uses the agentic framework described in [workflow.md](../workflow.md). Read it before working on a feature.

Before planning or changing code, read [architecture](../project-context/architecture.md), [testing strategy](../project-context/testing-strategy.md) and [coding rules](instructions/coding-rules.instructions.md). The coding rules are also attached automatically when files matching their `applyTo` pattern are edited.

- Features live in `work/features/F###-<short-name>/`. The `Status:` line in `story.md` is the single source of truth.
- Only one feature may be open (any status other than DONE or CANCELLED).
- Approvals must be explicit: "I approve the story." and "I approve the plan." "continue", "ok", "go" or silence are not approvals. Record the exact message and the date in `story.md`.
- Never fabricate test results, evidence or approvals.
- Never weaken an acceptance criterion or a test to make it pass.
- No global installs, pushes, deletions outside the feature folder or external actions without the human's agreement.
