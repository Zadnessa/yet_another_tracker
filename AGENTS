# AGENTS.md

Правила для AI-агентов (Codex, Claude Code, Cursor agents), работающих с этим репозиторием.

> ⚠️ Этот файл — стартовая заглушка. Финальная структура будет проработана в задаче research-эпика из `PLAN.md`. До тех пор соблюдаются минимальные правила ниже.

## 1. Stack & versions

- **Next.js 15** (App Router, async `cookies`/`headers`/`params`)
- **TypeScript** strict mode
- **Prisma** + **PostgreSQL**
- **Tailwind CSS** + **shadcn/ui**
- **Apache ECharts** через `echarts-for-react`
- **NextAuth.js** для авторизации

**Запреты:**
- ❌ `pages/api/` — только Route Handlers в `app/api/`
- ❌ Raw SQL — только через Prisma
- ❌ `float` / JavaScript `number` для денежных сумм — только `Decimal`
- ❌ Destructive миграции БД в v1 — только аддитивные
- ❌ Изменение Prisma schema без отдельного файла "migration rationale"

## 2. Security must-haves

- ✅ Zod-валидация на каждом серверном входе (Route Handlers, server actions)
- ✅ Проверка `userId` в каждом методе сервисного слоя
- ✅ Авторизация в Route Handlers, не только в middleware
- ✅ Эскейпинг пользовательских строк (Next.js делает это по умолчанию — не отключать)

## 3. Architecture rules

- **Service Layer обязателен.** Бизнес-логика — в сервисах (`src/services/`), не в Route Handlers.
- **Route Handlers** только парсят вход (Zod), вызывают сервис, форматируют ответ.
- **Запись данных** — через изолированный input-слой с интеграционными тестами.
- **Schema constraints в БД** — на критичных полях (положительные суммы, неpustyе ссылки, и т.д.).

## 4. Code style

- Импорты: external → internal → relative.
- Файлы компонентов: PascalCase (`ExpenseCard.tsx`).
- Файлы утилит/хуков: camelCase (`useTransactions.ts`).
- Ветки: `feature/<short-name>`, `fix/<short-name>`.
- Коммиты: Conventional Commits (`feat:`, `fix:`, `refactor:`).

## 5. Tier разметка

Каждая UI-фича имеет атрибут `tier: 'common' | 'pro'`. В v1 атрибут проставляется, но не используется (всё видно автору как pro-юзеру). Полноценный Common UI — отдельный эпик v2+.

## 6. Pull requests

- Один PR = одна фича или один логический блок изменений.
- Описание PR содержит: что сделано, как тестировалось, ссылка на issue/story.
- Перед мержем — ручной тест-план в локальном или PR-инстансе.

## 7. Что НЕ делает агент без явного запроса

- Не меняет схему БД.
- Не пишет деструктивные миграции.
- Не трогает `.env`, секреты, ключи деплоя.
- Не подключается к prod-БД.
- Не делает большие архитектурные рефакторинги без обсуждения.

## 8. References

- `README.md` — обзор проекта и стек.
- `PLAN.md` — текущий бэклог.
- `docs/PROJECT_SUMMARY.md` — видение и принципы.
- `docs/DECISIONS_LOG.md` — почему сделано именно так.
- `docs/OPEN_QUESTIONS.md` — открытые вопросы.
