# Deep Planning Skill for Claude Code

Система глубокой декомпозиции задач с поддержкой параллельных планов.

## Что умеет

- Селектор сложности для новых задач
- Глубокая декомпозиция на задачи, подзадачи и шаги
- Параллельные планы в отдельных папках
- Проверка конфликтов по `Affected Files`
- Пошаговое выполнение через `dp-next`
- Мониторинг прогресса через `dp-status`
- Завершение с отчётом в `journal/YYYY-MM-DD/`

## Где лежит исходник Claude

- Папка: `/Users/ilgiz/Documents/code/ skills/deep plan skill`
- Основные файлы: `commands/deep-plan.md`, `commands/dp-next.md`, `commands/dp-status.md`

## Codex version

Для Codex этот workflow теперь является дефолтным skill:

- Skill name: `deep-planning`
- Установлен в: `/Users/ilgiz/.codex/skills/deep-planning`
- Хранение планов: `deep-planning-skill/<plan-id>/`
- `doc/plans` больше не используется этим skill

## Source of truth для Codex

При запуске новой сессии поведение задают сразу несколько мест. Важно держать их синхронными:

- `~/.codex/skills/deep-planning/SKILL.md` — основная логика deep planning
- `~/.codex/skills/deep-planning/references/tree-rules.md` — правила структуры плана
- `~/.codex/skills/deep-planning/agents/openai.yaml` — UI-метаданные и default prompt
- `~/.codex/AGENTS.md` — глобальные инструкции Codex

Если `SKILL.md` уже переведён на `deep-planning-skill/<plan-id>/`, а в `~/.codex/AGENTS.md` всё ещё написано `doc/plans/...`, новая сессия снова начнёт создавать `doc/plans`. Это главный подводный камень.

## Установка в Codex с нуля

1. Установить или обновить skill `deep-planning` в `~/.codex/skills/deep-planning`.
2. Проверить, что в `~/.codex/skills/deep-planning/SKILL.md` указано хранение в `deep-planning-skill/<plan-id>/`.
3. Проверить, что в `~/.codex/AGENTS.md` блок про глубокое планирование тоже ссылается на `deep-planning-skill/<plan-id>/STATUS.md`, а не на `doc/plans/...`.
4. Если в проекте есть локальный `AGENTS.md`, убедиться, что он не переопределяет deep planning обратно на `doc/plans`.
5. Убедиться, что нет второго конкурирующего skill с другой схемой хранения, например `deep-plan-claude`.

## Быстрая проверка после установки

Запусти:

```bash
rg -n "doc/plans|deep-planning-skill" ~/.codex/AGENTS.md ~/.codex/skills/deep-planning
```

Ожидаемый результат:

- в `~/.codex/AGENTS.md` должен быть `deep-planning-skill/<plan-id>/STATUS.md`
- в `~/.codex/skills/deep-planning/` должен использоваться `deep-planning-skill/`
- упоминаний `doc/plans` в этих рабочих файлах быть не должно

## Что делать, если снова появился `doc/plans`

1. Сначала проверить `~/.codex/AGENTS.md`.
2. Потом проверить `~/.codex/skills/deep-planning/SKILL.md`.
3. Потом проверить локальный `AGENTS.md` конкретного проекта.
4. После исправления удалить ошибочно созданный `doc/plans`, если он не нужен.

## Как работает

1. Пользователь описывает задачу.
2. Создаётся plan id вида `XXXX-kebab-name`.
3. План раскладывается в `STATUS.md`, `TASK.md` и `PLAN.md`.
4. Выполнение идёт depth-first через следующий незавершённый leaf.
5. После завершения пишется отчёт в `journal/YYYY-MM-DD/`, затем папка плана удаляется.
