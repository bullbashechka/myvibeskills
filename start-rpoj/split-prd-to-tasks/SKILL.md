---
name: split-prd-to-tasks
description: Split an existing PRD.md into implementation phases and development tasks. Use when the user asks Codex to divide PRD.md into stages, milestones, tasks, a TASKS.md plan, a tasks folder, or separate Markdown files for each task.
---

# Split PRD To Tasks

Use this skill to convert `PRD.md` into a practical implementation plan with a master `TASKS.md` and one Markdown file per task.

## Workflow

1. Locate and read `PRD.md` in the current workspace unless the user gives another path.
2. Extract product scope, features, user flows, roles, data entities, integrations, non-functional requirements, and out-of-scope items.
3. Divide the work into implementation phases ordered by dependency and delivery value.
4. Break each phase into concrete development tasks. Prefer tasks that are independently understandable and small enough for a coding agent to complete.
5. Save the master plan to `TASKS.md` in the current workspace.
6. Create a task-files folder named `tasks/` in the current workspace unless that name already conflicts with an existing file. If it conflicts, use `prd-tasks/`.
7. Create one Markdown file per task inside the task-files folder.
8. Link every task file from `TASKS.md`.

## Phase Guidelines

Use phases that fit the PRD, but prefer this order when applicable:

1. Project setup and foundation
2. Data model and backend foundations
3. Authentication, roles, and permissions
4. Core user workflows
5. Admin or backoffice workflows
6. Integrations, notifications, payments, or external services
7. Quality, edge cases, analytics, deployment, and release readiness

Do not create artificial phases that contain only one trivial task unless the PRD is very small.

## TASKS.md Format

Write `TASKS.md` as a readable implementation index:

- Title
- Short source reference to `PRD.md`
- Phase list in execution order
- For each phase:
  - Goal
  - Task checklist with links to the per-task Markdown files
  - Dependencies or sequencing notes when relevant
- A final "Definition of Done" section for the full PRD scope

Keep `TASKS.md` concise. Put detailed acceptance criteria in the individual task files.

## Task File Format

Name files with stable numeric prefixes and short slugs:

```text
tasks/
  001-project-setup.md
  002-user-auth.md
  003-create-main-entity.md
```

Each task file must include:

- Task title
- Phase
- Goal
- Product context from the PRD
- Scope
- Out of scope
- Requirements
- Acceptance criteria
- Dependencies
- Implementation notes, only when the PRD implies constraints the developer must preserve

Acceptance criteria must be concrete and testable. Avoid vague criteria like "works well" or "nice UX".

## Splitting Rules

- Keep tasks product-driven, not arbitrary code chores.
- Separate backend, frontend, data, and integration work only when separation makes implementation clearer.
- Keep shared setup or infrastructure tasks early.
- Preserve PRD decisions. Do not invent new product scope.
- If the PRD is ambiguous, choose conservative MVP defaults only for task decomposition. Do not add unresolved questions to `TASKS.md`.
- Put later-version or explicitly out-of-scope PRD items into a separate future-work note only if useful; do not turn them into current tasks.

## Final Response

After writing the files, briefly state that `TASKS.md` and the task-files folder were created. Include the folder path and the number of task files. Do not paste all task contents unless the user asks.
