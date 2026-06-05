---
name: create-prd
description: Turn a user's rough app idea into a clear product requirements document. Use when the user says they want to make/build/create an app, service, SaaS, MVP, website, tool, game, or product and wants Codex to ask questions with answer options, accept "ok" as confirmation, let the user correct individual answers, and save the final development specification to PRD.md with no reasoning, ambiguity, or open questions.
---

# Create PRD

Use this skill to run a structured product discovery interview and produce a clean `PRD.md` for development.

## Workflow

1. Extract the initial app idea from the user's message.
2. Ask concise questions with answer options. Prefer 3-5 options per question. Include a brief "recommended" option only when there is an obvious pragmatic default.
3. Ask questions in small batches. Start with the highest-impact unknowns: target user, core workflow, platform, monetization, data/auth needs, integrations, admin/backoffice, and launch scope.
4. After each batch, summarize the answers as numbered decisions and ask the user to reply `ok` if correct or correct any individual answers.
5. Treat `ok`, `ок`, `okay`, and equivalent confirmation as approval of the current decisions.
6. If the user corrects individual answers, update only those decisions and continue. Do not restart the interview unless the product direction materially changes.
7. Continue until there is enough information to write a development-ready PRD with no open questions.
8. Save the final specification to `PRD.md` in the current workspace unless the user explicitly gives another path.

## Interview Rules

- Use the user's language.
- Keep questions concrete and answerable.
- Provide options instead of open-ended questions whenever practical.
- Allow free-form corrections even when options are provided.
- Do not over-interview. Stop once uncertainty no longer blocks a clear MVP specification.
- If a necessary detail is missing and the user has approved defaults, choose a conservative MVP default and include it as a decided requirement.

## PRD.md Requirements

Write `PRD.md` as a clear development specification in free-form text.

The file must contain:

- Product overview and goal
- Target users and main use cases
- MVP scope
- Feature requirements, with each feature described separately from a product perspective
- Main user flows
- Data/entities the app must store or manage
- Roles and permissions, if relevant
- Integrations and external services, if relevant
- Non-functional requirements, if relevant
- Explicit out-of-scope items for the first version

The file must not contain:

- Reasoning process
- Open questions
- Maybe/possibly language
- Chat transcript
- A list of unresolved assumptions
- Implementation code

## Final Response

After saving `PRD.md`, briefly state where it was saved and mention that it contains the finalized product specification. Do not paste the full PRD unless the user asks.
