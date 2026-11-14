# INROU — технический экспорт БЕЗ ДИЗАЙНА

**Дата:** 14.11.2026. **Источник:** [woorldmun-commits/inrou](https://github.com/woorldmun-commits/inrou), `main` @ `344fee7a6d342ca677f957c684873ccbb95b8869`. **Назначение:** безопасный снимок исходников и технической документации без визуального дизайна.

Вторая, не автоматически синхронизированная кодовая линия. Содержит Chief Analyst runtime/worker и миграцию 0018.

## Включено
- `backend/`: FastAPI, OAuth/auth, tenancy/RLS, Yandex Direct & Metrika adapters, audit rules, immutable snapshots, workers, billing, intelligence, SQL migrations, tests and synthetic golden evals.
- `docs/` (отбор): product canon, API contracts, data/architecture/economics/AI governance, legal and privacy review, migration/pilot/release plans, non-visual specialist roles.
- `designe 1.0/lib/`, `designe 1.0/app/api/`, `designe 1.0/proxy.ts`: **только серверная/интеграционная часть Next**, контракты и прокси; необходимые технические package manifests.
- `deploy/`, `.github/workflows/` и конфигурация: для анализа действующей инфраструктуры и релизных процедур (не гарантируется запуск без UI).

## Исключено
- Визуальные `design-inrou/`, `brand/`, `INROU_*reference/visual*`, `designe 1.0/app/` страницы JSX/TSX, `components/`, изображения, стили, шрифты, анимации, скриншоты, коллажи и дизайн/визуальный QA.
- Исторические тяжёлые отчёты визуального тестирования, результаты локальных браузерных прогонов, промежуточные дизайн-пакеты.
- Файлы секретов и локального окружения не переносились; `backend/.env.example` содержит только структуру переменных.

## ВАЖНО
1. **Это НЕ готовый развёртываемый сайт**: оригинальные `Dockerfile`, `compose.yaml`, `render.yaml` и CI могут ссылаться на удалённый UI и не будут работать в исходном виде. Экспорт нужен для архитектурного аудита, переноса ядра и дальнейшей разработки. Для запуска всего приложения использовать оригинальный репозиторий.
2. **Тесты в рамках экспорта не запускались.** CI старых SHA не доказывает готовность этой усечённой ветки.
3. **Реальный доступ к Яндексу, платежи, юридический допуск и хранение ПДн в РФ не подтверждены созданием ветки.** Не включать live-флаги из этого экспорта автоматически.
4. Другой репозиторий [woorldmun-commits/inrou-deploy](https://github.com/woorldmun-commits/inrou-deploy) содержит отличающуюся кодовую линию; не объединять миграции/главные ветки без diff, SQL compatibility review и тестов.
5. `docs/INROU_MASTER_SPEC_V3.md` (если есть в этой линии) — целевой scope, не описание доказанно работающих фич. Соотносить с реализационной матрицей и кодом.

## Проверка backend на отдельном тестовом PostgreSQL
```bash
cd backend
python -m pip install -r requirements-dev.txt
ruff check .
python -m pytest -q
```
Предварительно изучить `backend/.env.example`, `backend/tests/conftest.py` и `backend/migrations/README.md`; не указывать production DSN. Команды приведены как план, не результат проверки.

## Первоисточники и контроль изменений
Original commit: `344fee7a6d342ca677f957c684873ccbb95b8869`.
Это отдельная **экспортная ветка**, `main` не изменялся, PR не открывался, существующие файлы и БД не удалялись.
