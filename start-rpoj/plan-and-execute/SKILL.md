---
name: plan-and-execute
description: >-
  Use when the user says exactly or effectively: "ну все супер, решили.
  теперь давай план реализации напишем и будем по нему работать". Create an
  implementation plan from already agreed decisions, confirm it, then execute
  the work step by step. Do not launch or depend on Plan mode; the user will
  start Plan mode themselves if needed.
---

# Plan And Execute

Trigger phrase:

```text
ну все супер, решили. теперь давай план реализации напишем и будем по нему работать
```

Use this skill after product decisions and edge cases have already been discussed and the user wants to move from discussion to implementation.

## Workflow

1. Collect the agreed context from the current conversation and any referenced files.
2. If a task file, `TASKS.md`, or `PRD.md` is relevant, read it before planning.
3. Write a concrete implementation plan in execution order.
4. Keep the plan practical: each step should be small enough to implement and verify.
5. Call out dependencies, risky steps, and verification points.
6. Ask for confirmation before starting implementation unless the user explicitly says to proceed immediately.
7. After confirmation, work through the plan step by step.
8. Report progress as steps are completed.
9. Update the plan if implementation reveals a necessary change, and explain the reason briefly.

## Plan Rules

- Do not restart product discovery.
- Do not ask broad open-ended questions unless a missing decision blocks implementation.
- Do not switch modes or ask the user to switch modes.
- Do not use Plan mode as a requirement. The user will launch Plan mode themselves.
- Keep technical detail useful for implementation, not educational filler.
- Prefer existing project conventions and nearby code patterns.

## Plan Format

Use this structure:

```markdown
**План реализации**

1. Step name - what will be changed and how it will be verified.
2. Step name - what will be changed and how it will be verified.
3. Step name - what will be changed and how it will be verified.

Риски:
- Short risk and mitigation.

Проверка:
- Commands or manual checks to run.
```

## Execution Rules

When implementation starts:

- Read the relevant code before editing.
- Keep edits scoped to the approved task.
- Preserve user changes in the worktree.
- Verify with tests, type checks, build commands, or focused manual checks when available.
- If verification cannot run, state why and provide the closest useful check performed.

## Final Response

At the end, summarize:

- What was implemented
- What files changed
- What verification was run
- Any remaining risks or follow-up tasks
