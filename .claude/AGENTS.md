# 🤖 Агенты и скилы проекта Maldives Fishing

Здесь — субагенты и скилы Claude Code, которые делают рутину пресейла **за тебя**.

## Кастомные субагенты (папка `agents/`)
Запускаются командой Claude Code: `@<имя>` или «запусти агента <имя> …». Их можно вызывать пачкой (параллельно).

| Агент | Что делает | Когда звать |
|---|---|---|
| `competitor-analyst` | Разбирает сайт конкурента/референса (оффер, цены, модель, языки, дефицит, UX, дыры) → секция для [02](../docs/02-competitors.md) | Добавить/обновить конкурента |
| `kp-writer` | Собирает черновик КП из брифа + стратегии + цен под клиента | Готовим/правим [05](../docs/05-proposal.md) |
| `content-strategist` | Контент-план, темы catch-reports/блога/гайда, видео-идеи | Контент-пак, контент-хаб |
| `site-architect` | Сайтмап, воронка, ТЗ на страницы/компоненты | Концепция/спека сайта [06](../docs/06-concept-sitemap.md) |
| `seo-strategist` | Ключи EN/RU+ по регионам, кластеры, как обойти агрегаторы | SEO-стратегия, посадки |

> Так уже был собран [02 — Анализ конкурентов](../docs/02-competitors.md): 5 параллельных `competitor-analyst` разобрали Blue Safari, Alphonse, FlyCastaway, Boombastic и мальдивских игроков.

## Готовые скилы Claude Code (ставятся как плагины)
Это «надстройки», которые приходят из маркетплейсов плагинов на GitHub (`anthropics/skills` и др.). Полезные под этот проект:

- **`deep-research`** — глубокий многоисточниковый ресёрч с проверкой фактов (рынки, спрос, регуляторика оплаты по странам).
- **`product-management:competitive-brief`** — battle cards / конкурентный бриф (усилить [02](../docs/02-competitors.md)).
- **`product-management:write-spec`** — PRD/спека сайта из концепции ([06](../docs/06-concept-sitemap.md)).
- **`docx` / `pdf` / `pptx`** — превратить [05 — КП](../docs/05-proposal.md) в красивый клиентский документ/презентацию.
- **`design:user-research` / `design:design-critique`** — UX-логика и критика макетов сайта.

### Как ставить/смотреть скилы
- В Claude Code: `/plugin` — открыть маркетплейс плагинов и поставить нужные скилы.
- Репозиторий скилов Anthropic: <https://github.com/anthropics/skills>.
- Вызов скила: `/<имя-скила>` (напр. `/deep-research`).

## Идея пайплайна «агенты работают за меня»
1. `competitor-analyst` ×N (параллельно) → [02](../docs/02-competitors.md)
2. `seo-strategist` + `content-strategist` → ключи и контент-план
3. `site-architect` → [06](../docs/06-concept-sitemap.md) → спека сайта
4. `kp-writer` → [05](../docs/05-proposal.md) → затем `docx`/`pptx` для клиента
5. Демо-сайт (Next.js) → деплой Vercel → ссылка на телефон
