# Critique Guide — 5D Quality Review

Agent runs this review on every output before delivery.
Score each dimension 1–10. Minimum passing score: 7 per dimension, 38 total.
If any dimension scores below 7 — fix before delivering.

---

## How to run the review

After generating output, evaluate it against all 5 dimensions.
Write the scores as a brief block before the final code:

```
── Critique ──────────────────────────
D1 Visual Impact:     8/10
D2 Technical Quality: 9/10
D3 Motion Design:     7/10
D4 Functional UX:     8/10
D5 Originality:       9/10
Total: 41/50 ✓
──────────────────────────────────────
```

If score < 38 or any dimension < 7: state what you're fixing, then fix it.

---

## D1 — Visual Impact (Does it stop the scroll?)

**The test:** Would a designer screenshot this?

| Score | What it means |
|---|---|
| 9–10 | Immediately striking. Distinctive. Memorable. |
| 7–8  | Looks good, has a clear aesthetic point of view |
| 5–6  | Competent but forgettable. Generic AI output. |
| 1–4  | No aesthetic direction. Placeholder-level. |

**Check:**
- Is there a clear, committed aesthetic direction?
- Does the hero section create immediate impact?
- Is typography doing visual work (not just holding text)?
- Is the color system cohesive — not random?
- Does it look like it was designed, not generated?

**Common failures:**
- Purple gradient on white (instant -3)
- Inter or Roboto anywhere (instant -2)
- Card grid that looks like every other SaaS site (-2)
- Equal visual weight everywhere, no hierarchy (-2)

---

## D2 — Technical Quality (Does it work perfectly?)

**The test:** Ship it right now — would anything break?

| Score | What it means |
|---|---|
| 9–10 | Zero issues. Production-ready. |
| 7–8  | Works fully, minor polish opportunities |
| 5–6  | Works mostly, has one or more broken elements |
| 1–4  | Broken interactions, missing styles, or errors |

**Check:**
- [ ] No broken imports or missing CDN links
- [ ] All buttons and interactions functional
- [ ] Responsive — tested mentally at 375px, 768px, 1280px
- [ ] No overflow issues (horizontal scroll on mobile)
- [ ] Fonts load correctly (Google Fonts link present)
- [ ] CSS custom properties defined before use
- [ ] No `undefined` or `null` in rendered output
- [ ] Forms have proper input types and labels
- [ ] Images have alt text
- [ ] `prefers-reduced-motion` respected

**Common failures:**
- GSAP used but CDN link missing (-3)
- Mobile nav broken or overflowing (-2)
- Hover states defined but touch devices get stuck (-1)
- Font reference without import (-2)

---

## D3 — Motion Design (Does it feel alive?)

**The test:** Remove all animations — does the page feel dead? Good. Put them back.

| Score | What it means |
|---|---|
| 9–10 | Animation adds meaning. Purposeful, timed perfectly. |
| 7–8  | Solid animations, enhance the experience |
| 5–6  | Animations present but generic or poorly timed |
| 1–4  | Static or distracting. No motion or wrong motion. |

**Check:**
- [ ] Page load has orchestrated entrance (not everything at once)
- [ ] Scroll reveals present on all major sections
- [ ] Hover states on all interactive elements
- [ ] Background has ambient animation (if aesthetic calls for it)
- [ ] Easing curves match the aesthetic character
- [ ] Duration appropriate — not too fast (< 150ms feels broken) or slow (> 1200ms feels laggy)
- [ ] Animations only use `transform` and `opacity` (GPU-composited)
- [ ] Stagger delays feel natural (80–150ms between children)

**Easing reference:**
```
Luxury Minimal  → cubic-bezier(0.16, 1, 0.3, 1)   // slow out
Neo-Brutalist   → linear or ease-in-out             // mechanical
Organic Flow    → cubic-bezier(0.34, 1.56, 0.64, 1) // slight spring
Cinematic Dark  → cubic-bezier(0.25, 0.46, 0.45, 0.94) // film ease
```

**Common failures:**
- All elements animate simultaneously (-3)
- `ease-in` used anywhere (always feels wrong for entrances) (-2)
- Animation on `height` or `width` instead of `transform` (-2)
- Hover on cards but not on buttons (-1)

---

## D4 — Functional UX (Does it serve the user?)

**The test:** Give it to someone unfamiliar — can they complete the primary action?

| Score | What it means |
|---|---|
| 9–10 | Flow is obvious. No friction. Every state handled. |
| 7–8  | Clear primary action, minor UX gaps |
| 5–6  | Works but user needs to think too much |
| 1–4  | Confusing hierarchy, broken flows, missing states |

**Check:**
- [ ] Primary CTA is immediately visible above the fold
- [ ] Navigation is clear — user knows where they are
- [ ] Forms have visible labels (not just placeholder text)
- [ ] Error states exist (not just happy path)
- [ ] Empty states defined (for dashboards, lists)
- [ ] Loading states present (for any async action)
- [ ] Mobile touch targets ≥ 44px
- [ ] Focus states visible (keyboard navigation)
- [ ] Information hierarchy: what's most important is most prominent

**For prototypes specifically:**
- [ ] Every screen has a clear next action
- [ ] Back navigation always available
- [ ] Dead-end screens don't exist

**Common failures:**
- CTA below the fold on mobile (-2)
- Placeholder text as only label (disappears on focus) (-2)
- No error state on forms (-2)
- Touch targets too small on mobile (-2)

---

## D5 — Originality (Is it memorable?)

**The test:** After seeing 100 AI-generated sites today, does this one stand out?

| Score | What it means |
|---|---|
| 9–10 | Unmistakable. Would be discussed. Portfolio-worthy. |
| 7–8  | Distinctive — clearly has a point of view |
| 5–6  | Fine but forgettable. Could be from any AI tool. |
| 1–4  | Generic. Template-feeling. No personality. |

**Check:**
- Is there one unexpected detail the user didn't ask for but will notice?
- Does the typography choice feel intentional for this context?
- Is the layout doing something non-obvious?
- Does the color palette feel chosen, not defaulted to?
- Would a designer recognize this as having a point of view?

**Unexpected detail ideas (use one per build):**
- Oversized single letter as decorative element
- Number counter that animates on scroll into view
- Cursor that changes shape over interactive elements
- Section divider that's a diagonal or wave, not a line
- Stat cards with animated counting numbers
- Navigation with an unusual hover effect
- Hero text that splits into words on load
- Accent line that draws itself on page load (SVG stroke)
- Background that subtly reacts to mouse position

**Common failures:**
- Same layout as every SaaS landing page (-3)
- Hero: big headline + subtext + two buttons + hero image (-2, too predictable)
- Feature section: 3x2 icon grid with title and description (-2)
- Footer: 4 columns, copyright, social icons (-1, at least animate it)

---

## Quick fixes by score

**D1 < 7 (Visual Impact):**
→ Change the font — pick something from the approved list
→ Commit harder to the aesthetic direction — don't hedge
→ Add one bold typographic moment (oversized, unexpected)

**D2 < 7 (Technical Quality):**
→ Check all CDN links exist and are correct
→ Test each breakpoint mentally: 375 / 768 / 1280
→ Verify every button has an action

**D3 < 7 (Motion Design):**
→ Add scroll reveals to every section that lacks them
→ Add stagger to any list or grid
→ Check easing curves match aesthetic

**D4 < 7 (Functional UX):**
→ Move primary CTA higher
→ Add labels to all form inputs
→ Add at least one error state

**D5 < 7 (Originality):**
→ Add the unexpected detail
→ Break the predictable layout in one section
→ Choose a bolder font combination
