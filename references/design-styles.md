# Design Styles — Aesthetic Direction Reference

Each direction has: signature, palette logic, typography rules, motion character, and when to use.
Agent reads this when choosing or applying an aesthetic direction.

Never blend two directions in one build. Commit fully to one.

---

## 1. Cinematic Dark

**Signature:** Deep space atmosphere. Like a film poster designed by someone who codes.

**When to use:** SaaS products, developer tools, AI products, anything that needs to feel powerful or serious.

**Palette logic:**
- BG: near-black with slight warm or cool tint (`#0a0a0f` or `#0d0b00`)
- Surface: `#111` — `#1a1a1a`
- Accent: one saturated color that glows (electric blue `#3b82f6`, violet `#8b5cf6`, green `#10b981`)
- Glow: accent at 20–30% opacity as box-shadow spread
- Text: near-white `#f0f0f0`, muted `#666`

**Typography:**
- Display: Syne, Unbounded, or Archivo Black — wide, bold, commanding
- Body: IBM Plex Sans or Manrope — technical, precise

**Motion character:**
- Slow, deliberate entrance animations (0.8s+)
- Glow pulses on key elements (2–4s infinite)
- Particle or aurora background that breathes
- Hover: glow intensifies, slight scale

**Rules:**
- Every card has a subtle border (`1px solid rgba(255,255,255,0.06)`)
- Gradients go from accent to transparent, never accent-to-accent
- No pure white anywhere — always slightly off-white
- Shadows are colored (accent-tinted), never pure black

---

## 2. Luxury Minimal

**Signature:** Nothing unnecessary. Every element earns its place. Feels expensive without trying.

**When to use:** Premium products, consulting/agency sites, high-ticket B2B, anything where trust = conversion.

**Palette logic:**
- BG: pure white `#ffffff` or warm cream `#faf8f4`
- Surface: `#f5f5f0`
- Accent: one muted sophisticated color (deep navy `#1a2744`, forest `#2d4a3e`, burgundy `#5c1f2e`)
- Text: near-black `#0f0f0f`, muted `#6b6b6b`
- No gradients. No glows.

**Typography:**
- Display: Cormorant Garamond, Fraunces, or Playfair Display — editorial, refined
- Body: Source Serif 4 or Crimson Pro — readable, classic
- Spacing: generous. Line-height 1.6–1.8 body, 1.1 display

**Motion character:**
- Subtle and slow (0.6–1.2s eases)
- Fade + tiny Y offset (12px, not 32px)
- No bounces, no springs — pure ease-out
- Hover: color shift, underline extension, nothing dramatic

**Rules:**
- Whitespace IS the design. Never fill it.
- One accent color maximum, used sparingly
- Typography does the visual work — not decoration
- Mobile: same generous spacing, no cramming
- Images: high contrast, editorial photography style

---

## 3. Glassmorphism

**Signature:** Layered frosted glass floating over a rich gradient. Depth through translucency.

**When to use:** Consumer apps, fintech dashboards, lifestyle products, anything needing modern-but-approachable.

**Palette logic:**
- BG: rich gradient (purple-to-blue, blue-to-teal, rose-to-orange)
- Glass: `rgba(255,255,255,0.08)` — `rgba(255,255,255,0.15)`
- Border: `1px solid rgba(255,255,255,0.15)`
- Blur: `backdrop-filter: blur(20px)`
- Text: white or near-white throughout

**Typography:**
- Display: Outfit, Figtree, or Onest — friendly, geometric
- Body: same family, lighter weight

**Motion character:**
- Glass panels slide in from bottom (mobile) or fade in (desktop)
- Background gradient slowly shifts hue (10–15s infinite)
- Hover: glass opacity increases, border brightens
- Cards float with subtle shadow change on hover

**Rules:**
```css
.glass {
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 16px;
}
```
- Always test: glass must be readable against the background it floats over
- Blur radius 16–24px sweet spot — below looks cheap, above is too heavy
- Background gradient must be colorful enough for glass to read

---

## 4. Neo-Brutalist

**Signature:** Raw, bold, unapologetic. Heavy borders, flat colors, intentional visual tension.

**When to use:** Creative agencies, portfolios, startups that want to stand out, cultural products.

**Palette logic:**
- Base: white `#ffffff` or black `#000000`
- Accent: one flat saturated color (yellow `#FFE500`, red `#FF3B00`, electric green `#00FF85`)
- Borders: `2px–4px solid #000` (on light) or `2px–4px solid #fff` (on dark)
- Shadows: hard offset, no blur — `4px 4px 0 #000` or `6px 6px 0 #000`

**Typography:**
- Display: Bebas Neue, Archivo Black, or Syne Extra Bold — maximum weight
- Body: IBM Plex Mono or Work Sans — functional, no frills
- Sizes: extreme scale contrast (hero 120px vs body 16px)

**Motion character:**
- Fast and snappy (0.15–0.25s)
- Hard easing (linear or ease-in-out, no spring)
- Hover: shadow shifts position (element appears to press down)
- Scroll reveals: instant appear, no fade

```css
.brutal-card {
  border: 3px solid #000;
  box-shadow: 6px 6px 0 #000;
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}
.brutal-card:hover {
  transform: translate(-3px, -3px);
  box-shadow: 9px 9px 0 #000;
}
```

**Rules:**
- No border-radius unless intentional as contrast element
- No gradients — flat fills only
- Layout breaks the grid intentionally (overlapping elements, diagonal text)
- Whitespace used as contrast, not comfort

---

## 5. Organic Flow

**Signature:** Soft, alive, natural. Like a living thing breathing. Calm energy.

**When to use:** Health, wellness, meditation, family products, B2C with emotional register.

**Palette logic:**
- BG: warm off-white `#fef9f4` or sage `#f0f4f0`
- Surfaces: soft greens, warm peaches, dusty lavender
- Accent: earthen tones (terracotta `#c17a5e`, sage `#6b8f71`, warm sand `#d4a96a`)
- No pure black — use `#2d2418` (warm dark) for text

**Typography:**
- Display: Fraunces (optical size large), Instrument Serif — organic letterforms
- Body: Karla or Lexend — legible, warm

**Motion character:**
- Everything feels like it breathes (scale 1.0 → 1.02 → 1.0, infinite)
- Scroll reveals float up slowly (0.9s, custom ease)
- SVG blob backgrounds morph slowly (8–12s)
- Hover: gentle scale, warm shadow

```css
@keyframes breathe {
  0%, 100% { transform: scale(1) rotate(0deg); }
  50%       { transform: scale(1.04) rotate(1deg); }
}
.blob { animation: breathe 6s ease-in-out infinite; }
```

**Rules:**
- Blob shapes for backgrounds and decorative elements (SVG, border-radius 40–60%)
- Curves everywhere — sections divided by wave SVGs, not straight lines
- Images: warm-toned, natural light, human presence
- No sharp corners unless structural

---

## 6. Retro-Future

**Signature:** The future as imagined in 1982. Synthwave meets brutalism. Nostalgic but digital.

**When to use:** Gaming, crypto, music, creative tools, anything with a cult following.

**Palette logic:**
- BG: deep dark `#0d0015` or `#000814`
- Accents: neon pink `#ff006e`, electric cyan `#00f5ff`, laser yellow `#ffe600`
- Grid lines: faint `rgba(0,245,255,0.1)` on dark bg (perspective grid effect)
- Glow: multiple accents can coexist (unlike other directions)

**Typography:**
- Display: Bebas Neue or custom pixel-adjacent fonts — retro tech feel
- Body: IBM Plex Mono — terminal aesthetic
- Mix case intentionally (ALL CAPS headers, lowercase body)

**Motion character:**
- Glitch effect on hover or load
- Scanline overlay (CSS)
- CRT flicker (subtle opacity pulse)
- Neon glow pulses

```css
/* Scanlines */
.scanlines::after {
  content: '';
  position: absolute; inset: 0;
  background: repeating-linear-gradient(
    0deg, transparent, transparent 2px,
    rgba(0,0,0,0.15) 2px, rgba(0,0,0,0.15) 4px
  );
  pointer-events: none;
}

/* Glitch */
@keyframes glitch {
  0%, 100% { clip-path: inset(0 0 100% 0); transform: translate(0); }
  20%       { clip-path: inset(20% 0 60% 0); transform: translate(-4px, 2px); }
  40%       { clip-path: inset(50% 0 30% 0); transform: translate(4px, -2px); }
  60%       { clip-path: inset(70% 0 10% 0); transform: translate(-2px, 4px); }
  80%       { clip-path: inset(10% 0 80% 0); transform: translate(2px, -4px); }
}
```

**Rules:**
- Perspective grid on hero background (CSS transform)
- Neon text-shadow on accented elements
- Chrome/metallic text effect for hero headlines
- Pixel-perfect borders (1px exact, no blur)

---

## 7. Editorial

**Signature:** Magazine meets product. Typography as visual design. Grid tension as aesthetic.

**When to use:** Media products, content platforms, agencies, newsletters, anything text-primary.

**Palette logic:**
- BG: white `#ffffff` or newsprint `#f7f5f0`
- Accent: one bold color used sparingly (deep red `#c0392b`, royal blue `#1a3a8f`)
- Text: black `#111111` as primary design element
- Photography: black-and-white or duotone

**Typography:**
- Display: Playfair Display (italic for pull quotes), Libre Baskerville
- Body: Source Serif 4 — long-form readable
- Mono: for dates, labels, metadata
- Size range: extreme — 96px headlines to 12px captions

**Motion character:**
- Text-driven: words animate, not backgrounds
- Column reveals on scroll
- Image parallax (subtle, 20–30% offset)
- Hover: accent color wash on cards

**Rules:**
- Grid: strict 12-column, intentional breaks for tension
- Pull quotes: oversized, centered, italic, full-width
- Running numbers / indices as decorative elements
- Photography crops: unexpected (faces cropped, extreme close-up)
- Drop caps on feature content

---

## 8. Soft Aurora

**Signature:** Dreamy, weightless, pastel. Like a sunset through frosted glass.

**When to use:** Consumer apps, lifestyle brands, anything targeting a soft emotional register.

**Palette logic:**
- BG: very light, almost white with a faint tint (`#fafaff`, `#fff5fa`)
- Orbs: soft pastels (lavender `#c4b5fd`, rose `#fca5a5`, sky `#7dd3fc`, mint `#6ee7b7`)
- Text: dark but not black (`#1e1b2e`)
- Surface: white with soft shadow

**Typography:**
- Display: Fraunces or Instrument Serif — dreamy, literary
- Body: Figtree or Onest — clean, modern, friendly

**Motion character:**
- Aurora orbs drift slowly (8–12s, ease-in-out infinite)
- Everything fades in softly (opacity only, no Y offset needed)
- Hover: gentle glow, scale 1.02
- No sudden movements

```css
.aurora-bg {
  position: fixed; inset: 0; z-index: -1;
  background: var(--bg);
  overflow: hidden;
}
.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.5;
  animation: drift 10s ease-in-out infinite;
}
@keyframes drift {
  0%, 100% { transform: translate(0, 0); }
  33%       { transform: translate(40px, -30px); }
  66%       { transform: translate(-20px, 20px); }
}
```

**Rules:**
- Never full-bleed dark sections — maintain the light, airy feel throughout
- Shadows: extremely soft (`0 4px 24px rgba(0,0,0,0.06)`)
- Icons: rounded, friendly (Phosphor Regular or Lucide)
- CTAs: filled with a pastel-to-slightly-deeper gradient

---

## 9. Industrial

**Signature:** Functional beauty. Precision grid. Information as aesthetic. Zero decoration.

**When to use:** Developer tools, dashboards, data products, technical documentation sites.

**Palette logic:**
- BG: `#0f0f0f` (dark) or `#f8f8f8` (light)
- Surface: subtle step (`#161616` / `#efefef`)
- Accent: one functional color (green `#00ff41` terminal, or blue `#0066ff`)
- Text: high contrast, monospaced for data
- Borders: `1px solid #222` or `#ddd`

**Typography:**
- Display: Geist Mono or IBM Plex Mono — everything monospaced
- Body: IBM Plex Sans — functional
- Data: tabular numbers, monospaced always

**Motion character:**
- Minimal — function over form
- Terminal-style text reveals (typewriter, left-to-right)
- No decorative animations — only functional (loading states, transitions)
- Hover: border color shift, background step

**Rules:**
- Grid: strict, aligned, no overlap
- Every element has a clear functional purpose
- Data density acceptable — this audience expects it
- No imagery unless data visualization
- Borders do visual work instead of shadows
