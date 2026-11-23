# Agentic framework (training edition, v3)

A small, instruction-based workflow for GitHub Copilot in VS Code. One feature at a time goes from **story → plan → code → independent QA**, with **two human approvals**.

## What is in the box

| Path | What it is |
|---|---|
| `.github/copilot-instructions.md` | The framework rules, read on every request |
| `.github/instructions/coding-rules.instructions.md` | Your coding rules, attached automatically when source files are edited (`applyTo`) |
| `.github/skills/run-tests/SKILL.md` | A skill: how to run your tests and record the evidence; loaded when a task needs it |
| `.github/agents/developer.agent.md` | **Developer**: writes the story and the plan, implements, records evidence |
| `.github/agents/qa.agent.md` | **QA**: checks the work independently; the only role that can set DONE |
| `.github/agents/teach-me.agent.md` | **Teach Me**: read-only guide that explains the framework |
| `project-context/` | Architecture and testing strategy of your project |
| `templates/` | Story, plan, review and QA report |
| `work/features/` | One folder per feature, created by the Developer |
| `workflow.md` | The one-page lifecycle |
| `exercises.md` | Things to try, including trying to break the rules |

## Install it in your project (10 min)

1. Copy `.github/`, `project-context/`, `templates/`, `work/`, `workflow.md` and `exercises.md` to the **root** of your repository. If you already have a `.github/copilot-instructions.md`, merge the two files by hand.
2. Fill in `project-context/architecture.md` and `project-context/testing-strategy.md`, with your real build and test commands.
3. Fill in `.github/instructions/coding-rules.instructions.md` and set `applyTo` to your source folder.
4. Open the repository root in VS Code. Check that **Developer**, **QA** and **Teach Me** appear in the agent picker.

## Run a feature

1. New chat, agent **Developer**: `New feature: <your idea>.` Give only the idea: the agent already knows it must draft the story and the acceptance criteria, then stop for your approval.
2. Review `story.md`, answer the questions, then reply **`I approve the story.`**
3. The Developer reads the context and the code and writes `plan.md`. Review it, then reply **`I approve the plan.`**
4. The Developer implements all tasks, runs the tests, records evidence in `review.md`, then hands over to QA.
5. QA re-checks everything itself. FAIL → the Developer fixes it and QA checks again. PASS → QA sets the feature to DONE.

If QA does not start on its own: new chat, agent **QA**: `Review the open feature.`

## Rules that matter

- Only an explicit approval counts: "continue", "ok" or "go" are not approvals.
- One open feature at a time.
- An acceptance criterion is ticked only with evidence: a command and its result, or a check done by the human.
- Only QA can set DONE. QA never changes production code.
- One agent per chat. Never ask the same chat to switch between Developer and QA.

These rules are Markdown instructions: the model follows them, nothing enforces them. Put whatever must never be skipped in tests, hooks or CI.
