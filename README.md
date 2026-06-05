# My Vibe Skills

Локальная коллекция Codex skills.

Каждый skill должен лежать в отдельной папке и содержать файл `SKILL.md`:

```text
myvibeskills/
  commit-message-from-diff/
    SKILL.md
    agents/
```

## Глобальная Установка В Codex

Codex загружает пользовательские skills из папки:

```powershell
$env:USERPROFILE\.codex\skills
```

Если задана переменная `CODEX_HOME`, Codex использует:

```powershell
$env:CODEX_HOME\skills
```

Создать глобальную папку для skills:

```powershell
$dest = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME "skills" } else { Join-Path $env:USERPROFILE ".codex\skills" }
New-Item -ItemType Directory -Force -Path $dest
```

Установить все skill-папки из этого репозитория:

```powershell
$dest = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME "skills" } else { Join-Path $env:USERPROFILE ".codex\skills" }
Get-ChildItem -Directory | Where-Object {
  Test-Path (Join-Path $_.FullName "SKILL.md")
} | ForEach-Object {
  Copy-Item -Recurse -Force -Path $_.FullName -Destination $dest
}
```

Установить только один skill:

```powershell
$dest = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME "skills" } else { Join-Path $env:USERPROFILE ".codex\skills" }
Copy-Item -Recurse -Force .\commit-message-from-diff $dest
```

После установки или обновления skills перезапусти Codex.

## Проверка Установленных Skills

```powershell
$dest = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME "skills" } else { Join-Path $env:USERPROFILE ".codex\skills" }
Get-ChildItem -Directory $dest
```

## Обновление Skill

Повторно выполни копирование с `-Force`, затем перезапусти Codex:

```powershell
$dest = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME "skills" } else { Join-Path $env:USERPROFILE ".codex\skills" }
Copy-Item -Recurse -Force .\commit-message-from-diff $dest
```
