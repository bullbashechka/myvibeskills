---
name: review-prd
description: Review and improve an existing PRD.md product requirements document. Use when the user asks Codex to review PRD.md, find open questions, ask missing product decisions with answer options, accept "ok" or corrections for individual answers, and then update PRD.md in the same format without adding reasoning or unresolved questions.
---

# Review PRD

Use this skill to turn an existing `PRD.md` into a more complete, development-ready product specification.

## Workflow

1. Locate and read `PRD.md` in the current workspace unless the user gives another path.
2. Review the document for missing product decisions, ambiguous requirements, contradictions, incomplete feature descriptions, unclear MVP scope, data gaps, user-flow gaps, permissions gaps, integration gaps, and launch-scope risks.
3. If the PRD is already sufficiently clear, say that there are no blocking open questions and ask the user whether to proceed with minor cleanup if needed.
4. If there are open questions, ask concise questions with answer options. Prefer 3-5 options per question. Include a recommended option only when there is an obvious conservative MVP default.
5. Ask questions in small batches, ordered by development impact.
6. After each batch, summarize the proposed decisions and ask the user to reply `ok` if correct or correct individual answers.
7. Treat `ok`, `ок`, `okay`, and equivalent confirmation as approval of the current decisions.
8. If the user corrects individual answers, update only those decisions and continue.
9. When all blocking questions are resolved, update `PRD.md` in place.

## Review Focus

Check for:

- Unclear target users or use cases
- Features described only as ideas instead of concrete product behavior
- Missing happy paths, empty states, error states, or edge cases
- Undefined roles, permissions, onboarding, authentication, or account model
- Missing data/entities the app must store or manage
- Vague admin/backoffice needs
- Undefined integrations, notifications, payments, analytics, or external APIs
- MVP scope that mixes first-version requirements with later ideas
- Non-functional requirements that affect implementation, such as privacy, performance, localization, audit logs, or device support

Ask only questions that materially improve the PRD for development. Do not ask questions for trivia, preferences, or details that can be safely defaulted.

## Update Rules

- Preserve the existing PRD structure and tone when it is coherent.
- Add missing details into the relevant existing sections.
- Create a new section only when the existing format has no natural place for important information.
- Keep each feature described separately from a product perspective.
- Convert approved answers into firm requirements.
- Remove or rewrite ambiguous language if the new decisions resolve it.
- Keep explicit out-of-scope items separate from MVP requirements.
- Do not add chat history, reasoning, unresolved assumptions, or open questions to `PRD.md`.

## Final Response

After updating `PRD.md`, briefly state that the PRD was reviewed and updated, and mention the path. Summarize the main categories of additions in 1-3 bullets. Do not paste the full PRD unless the user asks.
