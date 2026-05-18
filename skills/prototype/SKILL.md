# Skill: Prototype

Use when: user wants a clickable, multi-screen interactive prototype.
Not for static mockups — for things you can actually tap through.

---

## When to use this skill vs others

| Need | Skill |
|---|---|
| Marketing page | landing-page |
| Reusable React component | ui-components |
| Clickable app flow to test or demo | **prototype** ← this |

---

## Output format

Default: **HTML standalone** — single self-contained file, zero dependencies.
Everything inline: CSS, JS, all screens. Opens in any browser, no server needed.

If user specifies React: JSX artifact with screen state machine.

---

## Core Architecture

Every prototype is a **screen state machine**:

```js
const screens = {
  home:     { component: renderHome,    transitions: { 'cta-click': 'signup' } },
  signup:   { component: renderSignup,  transitions: { 'submit': 'dashboard', 'back': 'home' } },
  dashboard:{ component: renderDash,    transitions: { 'logout': 'home' } },
};

let current = 'home';

function navigate(to) {
  current = to;
  document.getElementById('app').innerHTML = '';
  screens[to].component(document.getElementById('app'));
  // entrance animation
  gsap.from('#app > *', { opacity: 0, y: 20, stagger: 0.08, duration: 0.4, ease: 'power2.out' });
}
```

**Rule:** Never use `<a href>` for screen transitions. Always JS `navigate()`.

---

## Device Frames

Always render inside a device frame unless user says "no frame".

### Mobile (default for app prototypes)

```html
<div class="device-frame iphone">
  <div class="device-notch"></div>
  <div class="device-screen" id="app"></div>
  <div class="device-home-bar"></div>
</div>
```

```css
.device-frame.iphone {
  width: 390px;
  height: 844px;
  background: #1a1a1a;
  border-radius: 54px;
  padding: 20px 8px;
  box-shadow:
    0 0 0 2px #3a3a3a,
    0 0 0 4px #1a1a1a,
    0 40px 80px rgba(0,0,0,0.5);
  position: relative;
  overflow: hidden;
}
.device-notch {
  width: 120px; height: 34px;
  background: #1a1a1a;
  border-radius: 0 0 20px 20px;
  position: absolute;
  top: 0; left: 50%;
  transform: translateX(-50%);
  z-index: 10;
}
.device-screen {
  width: 100%; height: 100%;
  border-radius: 46px;
  overflow: hidden;
  overflow-y: auto;
  background: var(--bg);
}
.device-home-bar {
  width: 120px; height: 5px;
  background: rgba(255,255,255,0.3);
  border-radius: 3px;
  position: absolute;
  bottom: 12px; left: 50%;
  transform: translateX(-50%);
}
```

### Browser (for web app prototypes)

```html
<div class="device-frame browser">
  <div class="browser-bar">
    <div class="browser-dots">
      <span></span><span></span><span></span>
    </div>
    <div class="browser-url">app.example.com</div>
  </div>
  <div class="browser-content" id="app"></div>
</div>
```

```css
.device-frame.browser {
  width: 900px;
  border-radius: 12px;
  box-shadow: 0 40px 80px rgba(0,0,0,0.4);
  overflow: hidden;
}
.browser-bar {
  height: 44px;
  background: #2a2a2a;
  display: flex;
  align-items: center;
  padding: 0 16px;
  gap: 12px;
}
.browser-dots {
  display: flex; gap: 6px;
}
.browser-dots span {
  width: 12px; height: 12px;
  border-radius: 50%;
  background: #555;
}
.browser-dots span:nth-child(1) { background: #ff5f57; }
.browser-dots span:nth-child(2) { background: #febc2e; }
.browser-dots span:nth-child(3) { background: #28c840; }
.browser-url {
  flex: 1;
  background: #1a1a1a;
  border-radius: 6px;
  height: 28px;
  display: flex;
  align-items: center;
  padding: 0 12px;
  font-size: 12px;
  color: #888;
  font-family: monospace;
}
.browser-content {
  height: 600px;
  overflow-y: auto;
  background: var(--bg);
}
```

---

## Screen Transitions

### Slide (mobile-native feel)
```js
function slideTransition(fromEl, toEl, direction = 'left') {
  const x = direction === 'left' ? '100%' : '-100%';
  gsap.fromTo(toEl, { x }, { x: '0%', duration: 0.35, ease: 'power2.out' });
  gsap.to(fromEl, { x: direction === 'left' ? '-30%' : '30%', duration: 0.35, ease: 'power2.out' });
}
```

### Fade (universal)
```js
function fadeTransition(app) {
  gsap.from(app.children, { opacity: 0, y: 16, stagger: 0.06, duration: 0.3, ease: 'power2.out' });
}
```

### Scale up (modal / detail)
```js
gsap.from(newScreen, { scale: 0.95, opacity: 0, duration: 0.25, ease: 'back.out(1.4)' });
```

---

## Navigation Patterns

### Bottom tab bar (mobile)
```html
<nav class="tab-bar">
  <button onclick="navigate('home')"    class="tab" data-screen="home">
    <svg><!-- home icon --></svg><span>Home</span>
  </button>
  <button onclick="navigate('explore')" class="tab" data-screen="explore">
    <svg><!-- search icon --></svg><span>Explore</span>
  </button>
  <button onclick="navigate('profile')" class="tab" data-screen="profile">
    <svg><!-- user icon --></svg><span>Profile</span>
  </button>
</nav>
```

```js
// Highlight active tab
function updateTabs(screen) {
  document.querySelectorAll('.tab').forEach(t => {
    t.classList.toggle('active', t.dataset.screen === screen);
  });
}
```

### Back button (mobile)
```html
<button class="back-btn" onclick="navigate('prev-screen')">
  <svg><!-- chevron-left --></svg>
  Back
</button>
```

---

## Required screens minimum

Never deliver a single-screen prototype. Minimum:

- **App prototype:** 3 screens (entry → core flow → success/result)
- **Onboarding:** 4 screens (welcome → step 1 → step 2 → done)
- **Dashboard:** 2 screens (list/overview → detail)
- **E-commerce:** 3 screens (listing → product → cart/checkout)

---

## Hotspot overlay (optional)

For presenting to stakeholders — show clickable zones on hover:

```css
.hotspot {
  position: absolute;
  border: 2px dashed rgba(99, 102, 241, 0.6);
  border-radius: 8px;
  background: rgba(99, 102, 241, 0.08);
  cursor: pointer;
  opacity: 0;
  transition: opacity 0.2s;
}
.show-hotspots .hotspot { opacity: 1; }
```

```html
<button onclick="document.body.classList.toggle('show-hotspots')"
        style="position:fixed;bottom:20px;right:20px;z-index:999">
  Toggle hotspots
</button>
```

---

## Prototype-specific rules

1. **Every button does something.** No dead interactions.
2. **Real copy only.** No "Lorem ipsum", no "Button text".
3. **Show the full flow.** Entry state AND success state.
4. **Scrollable screens.** Content must overflow naturally, not truncate.
5. **Loading states.** If there's a form submit — show a 1s loading state before next screen.
6. **Error states.** At least one screen must show an error/empty state.
7. **Keyboard navigation.** Enter submits forms, Escape closes modals.
8. **No broken frames.** Device frame always perfectly contains content.
