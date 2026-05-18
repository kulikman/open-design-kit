# How to Use open-design-kit

Практический гайд: от установки до готового сайта.

---

## Установка (один раз)

```bash
# Клонируй репо в папку инструментов
git clone https://github.com/kulikman/open-design-kit.git ~/tools/open-design-kit

# Или если используешь /Users/DEV/TEMLATES
git clone https://github.com/kulikman/open-design-kit.git /Users/DEV/TEMLATES/Open-design-kit
```

Всё. Никакого `npm install`. Никакого сервера. Это просто файлы.

---

## Подключение к проекту

### Вариант A — Claude Code (рекомендуется)

В корне твоего проекта создай `.cursorrules` или добавь в существующий:

```
# Design skill
Read /Users/DEV/TEMLATES/Open-design-kit/SKILL.md before any UI/design task.
For brand context read /Users/DEV/TEMLATES/Open-design-kit/design-systems/<project>/DESIGN.md
For animation patterns read /Users/DEV/TEMLATES/Open-design-kit/references/animations.md
For design styles read /Users/DEV/TEMLATES/Open-design-kit/references/design-styles.md
```

### Вариант B — Cursor

Те же строки в `.cursorrules` в корне проекта.

### Вариант C — Прямо в чате Claude

Просто напиши в начале задачи:
```
Use open-design-kit SKILL.md rules for this task.
Aesthetic direction: Cinematic Dark.
Output: HTML standalone.
```

---

## Создать новый сайт — пошагово

### Шаг 1 — Создай DESIGN.md для проекта (5 минут)

```bash
cp /Users/DEV/TEMLATES/Open-design-kit/design-systems/_base/DESIGN.md \
   /Users/DEV/TEMLATES/Open-design-kit/design-systems/my-project/DESIGN.md
```

Открой файл, заполни:
- Название и позиционирование
- Шрифты (или оставь пустым — агент выберет)
- Палитру (или оставь пустым)
- Эстетическое направление (выбери из `references/design-styles.md`)

**Если не знаешь что заполнить — оставь пустым.** Агент спросит при первом запуске.

### Шаг 2 — Дай задачу агенту

В Claude Code или чате:

```
Build a landing page for [project name].
Skill: /Users/DEV/TEMLATES/Open-design-kit/SKILL.md
Brand: /Users/DEV/TEMLATES/Open-design-kit/design-systems/my-project/DESIGN.md

[описание продукта, аудитория, главный CTA]
```

### Шаг 3 — Агент выдаст код

Получишь один HTML-файл. Открой в браузере — готово.

### Шаг 4 — Итерации

```
Change the hero aesthetic to Luxury Minimal.
Keep the same content and structure.
```

```
Add a pricing section after features.
Three tiers: Free / Pro $29 / Enterprise.
```

```
Make it responsive — the mobile nav is broken.
```

---

## Рецепты для частых задач

### Лендинг с нуля

```
Landing page for [product].
Target: [audience].
Main CTA: [action].
Aesthetic: [direction from design-styles.md or leave blank].
Output: HTML standalone.
Sections: hero, how it works, pricing, CTA.
```

### UI компонент для Next.js

```
Build a [component name] React component.
Stack: Next.js TSX + Tailwind.
Variants: [list variants needed].
Include TypeScript props interface.
Match aesthetic from design-systems/[project]/DESIGN.md
```

### Кликабельный прототип

```
Interactive prototype for [app name].
Screens: [list screens].
Device frame: iPhone / Browser.
Flow: [screen A] → [screen B] → [screen C].
Output: HTML standalone.
```

### Отдельная секция

```
Add a testimonials section to this existing page.
[вставь текущий HTML]
Match the existing aesthetic.
Use real placeholder names and quotes.
```

---

## Обновление kit'а

```bash
cd /Users/DEV/TEMLATES/Open-design-kit
git pull origin main
```

Все проекты автоматически получают обновления — kit один, проектов много.

---

## Добавить бренд нового проекта

```bash
# Скопировать шаблон
cp design-systems/_base/DESIGN.md design-systems/new-project/DESIGN.md

# Заполнить
open design-systems/new-project/DESIGN.md

# Закоммитить
git add design-systems/new-project/DESIGN.md
git commit -m "feat: add new-project design system"
git push
```

---

## Структура репо (справка)

```
open-design-kit/
│
├── SKILL.md                        ← Главный файл. Агент читает это первым.
│                                     6 фаз: Detect → Brief → Decide → Format → Animate → QA
│
├── design-systems/
│   ├── _base/DESIGN.md             ← Шаблон. Копируй под каждый проект.
│   └── <project>/DESIGN.md         ← Бренд проекта. Агент читает если есть.
│
├── skills/
│   ├── landing-page/SKILL.md       ← Правила для лендингов
│   ├── ui-components/SKILL.md      ← Правила для компонентов
│   └── prototype/SKILL.md          ← Правила для прототипов
│
└── references/
    ├── animations.md               ← Библиотека анимаций (copy-paste паттерны)
    ├── design-styles.md            ← 9 эстетических направлений с полным спеком
    └── critique-guide.md           ← 5D ревью: агент оценивает перед выдачей
```

---

## Что делает агент автоматически

1. **Читает DESIGN.md** — не переспрашивает про бренд если файл есть
2. **Выбирает формат** — HTML для прототипов, TSX для production
3. **Анимирует каждую секцию** — статичный output запрещён правилами
4. **Запускает 5D ревью** — оценивает и фиксит до выдачи
5. **Добавляет unexpected detail** — одна деталь которую не просили

---

## Частые вопросы

**Токены кончаются быстро?**
Заполни DESIGN.md — агент не будет переспрашивать про бренд. Это главная экономия.

**Как сказать агенту какой стиль хочу?**
Укажи направление из `design-styles.md` в задаче: `Aesthetic: Neo-Brutalist`

**Хочу Next.js компонент, не HTML?**
Укажи в задаче: `Output: Next.js TSX`

**Как добавить свой skill?**
Создай папку `skills/my-skill/SKILL.md` по образцу существующих. Закоммить в репо.

**Хочу обновить kit под новый проект:**
Просто добавь `design-systems/<project>/DESIGN.md` — ничего другого менять не нужно.
