---
name: commit-message-from-diff
description: Draft a complete, ready-to-use commit message from uncommitted Git changes. Use when Codex is asked to describe unstaged, staged, or untracked files; summarize what changed; propose a full conventional commit title and body; document validation or tests run; or prepare a commit message without necessarily creating the commit.
---

# Commit Message From Diff

## Workflow

Inspect the repository state before drafting text. Prefer these commands:

```bash
git status --short
git diff --stat
git diff --cached --stat
git diff --name-status
git diff --cached --name-status
```

For each changed file that matters, inspect the actual diff. Use `git diff -- <path>` for unstaged files and `git diff --cached -- <path>` for staged files. For untracked text files, read enough of the file to understand its purpose. Avoid reading generated, binary, dependency, or secret-looking files unless needed to avoid a wrong summary.

If the user asks only for commit text, do not modify files, stage files, or create a commit. If the user asks to commit, still produce or use the message only after verifying the final staged state.

## Reasoning Rules

- Summarize behavior and intent, not just filenames.
- Separate unrelated changes if the work appears to require multiple commits; say so and provide separate messages.
- Do not invent validation. Mention only tests, linters, type checks, or manual checks that were actually run in the current task or are clearly present in the conversation.
- If no validation was run, include `Not run:` with the concrete reason.
- Call out risky or unknown changes briefly if the diff is incomplete, binary-only, too large to inspect, or includes untracked files that were not read.
- Match the user's language. Use Russian when the request or repository communication is Russian.

## Commit Message Format

Return a complete commit message in this shape:

```text
type(scope): краткое действие в инфинитиве/повелительном стиле

  One concise paragraph explaining the main purpose and outcome.

  - Bullet describing a concrete changed behavior, file group, or requirement
  - Bullet describing another concrete part of the change
  - Bullet describing migration, config, tests, docs, or operational impact when relevant

  Validation:
  - <command/check>: <result or concise note>
  - Not run: <reason>
```

Use a conventional commit type:

- `feat` for user-visible capability
- `fix` for bug fixes
- `docs` for documentation or PRD/spec changes
- `test` for test-only changes
- `refactor` for restructuring without behavior change
- `perf` for performance work
- `build` for packaging, dependency, or build system changes
- `ci` for CI or workflow changes
- `chore` for maintenance that does not fit the above

Choose a narrow scope from the changed area, such as `bot`, `admin`, `bitrix`, `db`, `parser`, `security`, `prd`, `tests`, or a package/module name. Omit scope only when no meaningful scope exists.

Keep the title specific enough to stand alone. Prefer one strong verb and the user-facing outcome over vague titles like `update files` or `fix changes`.

## Example

```text
docs(prd): зафиксировать ТЗ на переход бота на PostgreSQL

  Добавить новый PRD с согласованными требованиями по устойчивости парсинга, покрытию ручного ввода городов и полному отказу от SQLite в
  пользу PostgreSQL без Docker.

  - Описать сценарий автовосстановления парсинга: детект зависания как 120 секунд без прироста записей и без перехода на следующую
  страницу, refresh в текущей Chrome-сессии и продолжение джоба по остальным URL при сбое одного URL
  - Зафиксировать требования к ручному вводу городов: статический каталог городов RU/KZ в репозитории как source of truth и отклонение
  неоднозначных алиасов с запросом на уточнение
  - Уточнить целевую архитектуру хранения данных: полный вывод SQLite из runtime и тестового контура, переход на PostgreSQL для
  production, local development и automated tests
  - Определить условия миграции данных: прямой полный перенос из SQLite в PostgreSQL без dual-run, без fallback на SQLite и без
  допустимости частичного успешного результата
  - Закрепить эксплуатационные рамки этапа: работа без Docker, headful Chrome для бота, сохранение автоприменения Alembic-миграций в
  PostgreSQL-контуре

  Validation:
  - Not run: сформирован только текст PRD, код и тесты не запускались
```
