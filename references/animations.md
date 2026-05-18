# Animation & motion — pattern library

Reference for **duration, easing, choreography**, and **reduced-motion** alternatives. Values are defaults; tune per brand in `design-systems/_base/DESIGN.md`.

## Tokens

| Token | Typical range | Usage |
|-------|----------------|--------|
| `duration-instant` | 0–50 ms | toggles that should feel immediate |
| `duration-fast` | 100–150 ms | micro-feedback (hover, press) |
| `duration-base` | 200–250 ms | small position/opacity changes |
| `duration-slow` | 300–400 ms | panels, drawers, page cross-fades |
| `duration-emphasis` | 450–600 ms | hero intros (use sparingly, once per session) |

### Easing

| Name | Curve (approx) | When |
|------|------------------|------|
| **Standard** | cubic-bezier(0.2, 0, 0, 1) | most UI enter/exit |
| **Decelerate** | cubic-bezier(0, 0, 0, 1) | elements entering frame |
| **Accelerate** | cubic-bezier(0.3, 0, 1, 1) | elements leaving frame |
| **Spring-like** | spring or custom bezier | playful consumer UI only; keep amplitude low |

Avoid linear easing for organic UI motion except **progress indicators** and **scrubbers**.

## Patterns

### 1. Hover / pressed (controls)

- Properties: background color, border, subtle scale **≤ 1.02** or none.
- Duration: `duration-fast`.
- Reduced motion: color/border only; no scale.

### 2. Focus ring

- Prefer **outline** or box-shadow ring; animate opacity **0 → 1** in ≤ 120 ms on focus-visible.
- Reduced motion: static ring, no pulse.

### 3. Toggle / switch

- Track slides with `duration-base`, standard easing.
- Knob shadow softens at end state.
- Reduced motion: crossfade track colors; knob position can jump or use 100 ms max.

### 4. Expand / collapse (accordion, inline details)

- Height: prefer **grid-template-rows** `0fr → 1fr` pattern or max-height with caution for performance.
- Opacity of children: 0.95 → 1 to reduce “pop.”
- Duration: `duration-slow` for >400 px height changes.
- Reduced motion: **instant expand** or opacity-only reveal; preserve state.

### 5. Modal / dialog

- Backdrop: opacity 0 → 1 in `duration-base`.
- Panel: translateY(8px) + opacity with decelerate; or scale 0.96 → 1 if brand allows.
- Focus trap and return focus on close are mandatory (document in handoff).
- Reduced motion: backdrop fade only; panel appears without slide.

### 6. Drawer (side panel)

- Panel: translateX with `duration-slow`, standard easing.
- Scrim: parallel backdrop fade.
- Reduced motion: panel **no slide**; scrim fade only.

### 7. Toast / snackbar

- Enter: translateY(12px) → 0 + opacity, `duration-base`.
- Exit: accelerate, slightly shorter than enter.
- Stack: stagger **40–60 ms** max; cap visible count.
- Reduced motion: opacity only; shorter durations.

### 8. List reorder (drag-drop)

- Item lift: scale **1.02**, elevation bump, `duration-fast`.
- Ghost placeholder: subtle opacity pulse **avoid**; prefer static tint.
- Drop settle: spring-like **only if** amplitude ≤ 2%; else standard easing.
- Reduced motion: no lift scale; highlight row border only.

### 9. Skeleton loading

- Shimmer: slow gradient sweep **1.2–1.8 s** linear infinite **only if** reduced motion off.
- Reduced motion: **static** skeleton blocks or pulse opacity **≤ 5%** once per 3 s (or no pulse).

### 10. Page transition (SPA)

- Outgoing: opacity or slight translate (4–8 px), `duration-base`.
- Incoming: decelerate, match distance for spatial continuity.
- Reduced motion: **opacity crossfade only**, ≤ 200 ms.

### 11. Chart draws

- Stagger series by **30–50 ms**; cap total staged time ≤ 600 ms.
- Reduced motion: show **end state** immediately or animate only numbers changing once.

### 12. Success / error micro-celebrations

- Success check: stroke-dashoffset draw, `duration-slow`, single play.
- Error shake: **avoid**; prefer icon color + inline message fade-in.
- Reduced motion: no draw effects; icon state change only.

## Choreography rules

- **One focal motion** per 200 ms window where possible; parallel motions should be related (e.g. backdrop + panel).
- **Spatial consistency**: motion axis matches origin of action (button opens menu downward if below, etc.).
- **Interruptible**: user input cancels decorative animations safely.

## Performance

- Prefer **transform** and **opacity**; avoid animating `top/left/width/height` when transform can do the job.
- Large blurs and shadows during motion are expensive; reduce blur mid-animation if needed.

## Checklist (handoff)

- [ ] Durations and easing named per pattern
- [ ] `prefers-reduced-motion` behavior specified
- [ ] Focus order preserved during transitions
- [ ] No seizure-inducing flashes (> 3 Hz general motion)
