# Design system — base schema (template)

Copy this file to your product folder (for example `design-systems/<product>/DESIGN.md`) and replace placeholders. Keep tables scannable; agents and humans should parse this quickly.

## Brand

| Field | Value |
|--------|--------|
| Product name | `<name>` |
| One-line promise | `<what we help users achieve>` |
| Voice | `<e.g. direct, warm, expert>` |
| Tone guardrails | `<avoid / prefer>` |
| Primary locales | `<e.g. en-US, de-DE>` |

## Foundations

### Typography

| Role | Family | Weights | Size scale notes |
|------|--------|-----------|------------------|
| Display | `<font>` | `<400–700>` | `<usage>` |
| UI / body | `<font>` | `<400–600>` | `<usage>` |
| Mono (optional) | `<font>` | `<400>` | `<code, data>` |

### Color roles (semantic)

Define **roles**, not arbitrary hex unless legacy requires it.

| Role | Purpose | Light | Dark (if applicable) |
|------|---------|-------|------------------------|
| `background` | App canvas | `<token or hex>` | `<>` |
| `surface` | Cards, panels | `<>` | `<>` |
| `surface-elevated` | Modals, popovers | `<>` | `<>` |
| `border` | Hairlines, dividers | `<>` | `<>` |
| `text-primary` | Main copy | `<>` | `<>` |
| `text-secondary` | Supporting copy | `<>` | `<>` |
| `text-muted` | Placeholder, hints | `<>` | `<>` |
| `accent` | Primary actions | `<>` | `<>` |
| `accent-contrast` | Text on accent | `<>` | `<>` |
| `success` / `warning` / `danger` | System feedback | `<>` | `<>` |

### Spacing & layout

| Token | Value | Usage |
|-------|-------|--------|
| `space-1` … `space-n` | `<4px grid or scale>` | `<padding, gap>` |
| `page-max-width` | `<px>` | `<marketing vs app>` |
| `radius-sm` / `radius-md` / `radius-lg` | `<values>` | `<controls, cards>` |

### Elevation

| Level | Shadow / border | Usage |
|-------|-----------------|--------|
| `0` | none | flat lists |
| `1` | `<spec>` | cards |
| `2` | `<spec>` | sticky bars, popovers |

### Iconography

- Style: `<outline / filled / rounded>`
- Stroke / optical size: `<rules>`
- Metaphor consistency: `<e.g. use “trash” not mixed delete icons>`

## Components (inventory)

List only what exists or is planned; link to specs or Storybook when available.

| Component | States | Notes |
|-----------|--------|--------|
| Button | default, hover, active, disabled, loading | `<primary/secondary/ghost>` |
| Input | default, focus, invalid, disabled | `<masking, autocomplete>` |
| … | … | … |

## Motion defaults

| Pattern | Duration | Easing | Reduced motion |
|---------|-----------|--------|------------------|
| Micro-interaction | `<ms>` | `<curve>` | `<instant / opacity-only>` |
| Panel / drawer | `<ms>` | `<curve>` | `<crossfade>` |

See `references/animations.md` for a fuller pattern library.

## Accessibility baseline

- Text contrast: **WCAG 2.2 AA** minimum for normal text; AAA where brand allows.
- Focus: visible ring on all interactive elements; order follows reading order.
- Targets: minimum **44×44 CSS px** for primary touch targets where applicable.
- Motion: respect `prefers-reduced-motion`; provide non-motion equivalents.

## Open decisions

- `<decision 1>`
- `<decision 2>`
