# Open Design Kit — Agent Skill (Main)

Use this skill when the user asks for **end-to-end design work**: product UX, visual systems, landing pages, component libraries, motion specs, or design-to-dev handoff.

## Operating principles

- Prefer **constraints over decoration**: audience, platform, accessibility (WCAG 2.2 AA default), performance, and brand rules first.
- Every deliverable should be **inspectable**: named sections, acceptance criteria, and measurable outcomes.
- Reuse tokens and patterns from `design-systems/` before inventing new ones.

## Phase 1 — Discover

- Clarify goal, audience, primary user jobs, and success metrics.
- Inventory constraints: tech stack, design system in use, locales, dark mode, legal/compliance.
- Output: problem statement, assumptions, open questions (max 5), and a **research checklist** (competitive, heuristic, content).

## Phase 2 — Define

- Translate discovery into **information architecture**: key screens, navigation model, content hierarchy.
- Define **key flows** (happy path + edge cases) in plain language or bullet steps.
- Output: sitemap or screen list, prioritized flows, empty/error/loading states policy.

## Phase 3 — Design system alignment

- Open `design-systems/_base/DESIGN.md` and map brand + tokens to the product (or note gaps).
- When the brief names an aesthetic direction (or you need a coherent visual vocabulary), use `references/design-styles.md` and commit to one direction only.
- Specify typography scale, spacing rhythm, color roles (semantic), elevation, radius, and icon style.
- Output: token table or delta list, “do / don’t” for brand usage.

## Phase 4 — UI & layout

- For marketing surfaces, follow `skills/landing-page/SKILL.md`.
- For app chrome and components, follow `skills/ui-components/SKILL.md`.
- For **clickable, multi-screen prototypes** (HTML/JSX state machine, device frames), follow `skills/prototype/SKILL.md`.
- Output: section-by-section layout notes, responsive behavior (breakpoints), and component inventory.

## Phase 5 — Motion & feedback

- Use `references/animations.md` for durations, easing, and pattern names.
- Tie motion to **intent**: orientation, causality, continuity; avoid gratuitous animation.
- Output: per-pattern triggers, durations, reduced-motion behavior.

## Phase 6 — Handoff & quality

- Produce **implementation-ready notes**: spacing in the design grid, token names, interaction states, and copy deck where needed.
- Run an accessibility pass: focus order, labels, contrast, touch targets, keyboard paths.
- Optional quality gate: self-review using `references/critique-guide.md` (5D) when the brief calls for a high bar before delivery.
- Output: acceptance criteria checklist, open risks, and next iteration hypotheses.

## Escalation

- If requirements are ambiguous, propose **two** concrete directions with trade-offs instead of blocking.
- If brand/system docs are missing, scaffold minimal defaults in `DESIGN.md` and mark them explicitly as provisional.
