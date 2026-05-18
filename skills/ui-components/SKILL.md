# Skill — UI components (app surfaces)

Use when designing **application UI**: dashboards, settings, forms, tables, navigation, empty states.

## Principles

- **Predictability**: same control = same behavior everywhere.
- **Density with dignity**: prefer progressive disclosure to cramming.
- **State completeness**: default, hover, focus, active, disabled, read-only, loading, empty, error.

## Core patterns

### Navigation

- Choose **one primary model**: top nav, sidebar, or hybrid; document where utilities live (profile, help).
- Keep **wayfinding**: current location visible; provide escape hatches from deep flows.

### Forms

- Labels visible (not placeholder-only); describe **why** when asking for sensitive data.
- Validate on blur for long fields; on submit for short flows; inline errors tied to fields with `aria-describedby` analog in notes.
- Destructive actions require **confirmation** with explicit consequences.

### Data display

- Tables: sticky header optional; column priorities for small screens (collapse to **row cards**).
- Charts: declare **default range** and units; empty chart states explained.

### Feedback

- Toasts for **async confirmation**; banners for page-level issues; inline for field-level.
- Do not stack competing modals; prefer single surface with clear hierarchy.

## Component specs (what to output)

For each component, specify:

- Anatomy (slots): e.g. `leadingIcon`, `label`, `hint`, `trailingAction`
- Variants and when to use them
- Keyboard interaction
- Tokens used: color roles, spacing, type roles, radius, elevation

## Accessibility

- Color is never the only signal; pair with icon/text/pattern.
- `prefers-reduced-motion`: replace slide with crossfade where possible.
- Skip links for keyboard users on chrome-heavy layouts.

## Handoff

- Redline spacing relative to **8px grid** (or your declared rhythm).
- Note truncation rules for dynamic text (email, file names, titles).
