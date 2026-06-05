---
name: steps-edge-cases
description: Discuss implementation risks, edge cases, and solution options for a specific task referenced by the user, especially with @task-file references. Use when the user wants Codex to take a task, explain technical pitfalls, work step by step through edge cases and possible approaches, and let a non-programmer decide from a product or user-experience perspective while Codex owns the technical solution.
---

# Steps Edge Cases

Use this skill to turn a referenced task into a structured implementation discussion before coding.

## Workflow

1. Identify the task the user referenced with `@`. If it points to a local file, read that task file and any directly linked context such as `TASKS.md` or `PRD.md` when needed.
2. Restate the task in plain product language, not implementation jargon.
3. List the main implementation areas that could contain hidden complexity.
4. Work through the task sequentially by edge-case groups. Do not dump every possible issue at once.
5. For each edge-case group, explain:
   - What can go wrong
   - Why it matters for users or product behavior
   - 2-4 possible solution options
   - The technical tradeoff of each option
   - The product/UX consequence of each option
   - A pragmatic recommended option when there is a clear default
6. Ask the user to choose between options or approve the recommendation. The user can answer from a product perspective only.
7. Treat `ok`, `ок`, `okay`, and equivalent confirmation as approval of the recommended option or current decisions.
8. If the user corrects individual decisions, update only those decisions and continue.
9. Continue until the task has a clear implementation approach, agreed edge-case handling, and no blocking product decisions.

## Discussion Style

- Use the user's language.
- Assume the user is not a programmer.
- Keep technical explanations clear, but do not hide important implementation consequences.
- Prefer concrete user-facing examples over abstract architecture talk.
- Separate technical feasibility from product preference.
- Ask one small decision set at a time.
- Do not start coding during this discussion unless the user explicitly asks.

## Edge-Case Checklist

Consider these categories when relevant:

- Empty states
- Error states
- Partial or failed saves
- Duplicate actions and double clicks
- Slow loading, retries, and timeouts
- Permission and role boundaries
- Authentication and session expiry
- Invalid, missing, or stale data
- Concurrent edits or race conditions
- Mobile, desktop, and responsive behavior
- Notifications and user feedback
- Payment, billing, and irreversible actions
- External API failures
- Data privacy, auditability, and deletion
- Admin override and support workflows

Only discuss categories that materially affect the referenced task.

## Output Shape

During the discussion, structure responses like this:

```markdown
**Step N: Short Topic**

What can go wrong:
...

Options:
1. Option A - product result and technical tradeoff
2. Option B - product result and technical tradeoff

Recommendation:
...

Decision needed:
...
```

When the discussion is complete, summarize:

- Final technical approach
- Agreed edge-case decisions
- Product behavior users will see
- Remaining non-blocking implementation notes, if any

Do not create or modify files unless the user asks to save the decisions or update a task file.
