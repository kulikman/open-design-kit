# Skill — Landing page design

Use when building or critiquing **marketing / landing** pages: hero, social proof, pricing, FAQs, signup flows.

**Related in this kit:** brand/tokens — `design-systems/<project>/DESIGN.md`; motion timing — `references/animations.md`; aesthetic directions — `references/design-styles.md`; full workflow — `SKILL.md` (repo root).

## Goals

- Communicate **value in seconds**: headline clarifies who it’s for and the outcome.
- Maintain **one primary CTA** per viewport; secondary actions are visually quieter.
- Support **scanning**: hierarchy, chunking, consistent spacing rhythm.

## Structure checklist

1. **Hero**: promise, supporting line, primary CTA, optional proof strip (logos, rating, metric).
2. **Problem → solution**: pain in user language; bridge to product mechanism without jargon walls.
3. **How it works**: 3–5 steps, verbs first, each step outcome-oriented.
4. **Proof**: testimonials (specific results), logos, compliance badges if relevant.
5. **Features / modules**: benefit-led headings; one idea per card; avoid duplicate CTAs.
6. **Pricing** (if applicable): default selection clear; annual/monthly toggle accessible; footnotes readable.
7. **FAQ**: real objections; link out for legal/security detail when needed.
8. **Final CTA**: repeat primary action with low-friction copy.

## Layout rules

- Max line length for body: **~65–75 characters** where possible.
- Use a **single spacing scale** from the design system; avoid one-off margins.
- Imagery: show product in context; alt text describes meaning, not decoration.

## Conversion hygiene

- Form friction: minimal fields above the fold; progressive profiling later.
- Loading states for CTAs; disabled styling distinct from idle.
- Error copy: what happened + next step (retry, contact, fix field).

## Responsive

- Collapse columns in **priority order**; never hide the primary CTA without a sticky alternative on long pages.
- Test **320px**, **768px**, **1280px+** mentally; check tap targets and line breaks in headlines.

## Output format

When asked for a page spec, deliver:

1. Section order with **H1/H2** text proposals.
2. CTA labels + destinations (URL or route).
3. Component list mapped to the design system.
4. **SEO**: title + meta description (optional if out of scope).
