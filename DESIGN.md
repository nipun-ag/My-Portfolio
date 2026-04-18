# Design System — Nipun Aggarwal Portfolio

Complete design reference for [bynipun.com](https://bynipun.com).

---

## Design Philosophy

The visual language is built around a **Premium Editorial Gallery** aesthetic — the kind of interface found in high-end SaaS products (Vercel, Linear, Stripe) and luxury editorial sites. Key principles:

- **Dark-first, high contrast** — near-black backgrounds with carefully layered surface levels
- **Luxury of space** — generous padding and gutters; content breathes rather than crowds
- **Glassmorphism depth** — semi-transparent card layers with backdrop-blur create a physical sense of depth without grain
- **Restrained motion** — soft radial glows replace mechanical sweeps; spring-curve easing over linear
- **Editorial scale** — display type is enormous (up to 13rem) with tightly negative tracking; metadata stays small and precise

---

## Color Palette

All colors are defined as CSS custom properties on `:root`. Values are slightly desaturated from their original forms for a more "jewel-toned" or expensive feel.

### Base / Backgrounds

| Variable | Hex | Usage |
|---|---|---|
| `--bg` | `#07080f` | Page background — the deepest layer |
| `--ink` | `#0c0d16` | Reference value (cards now use glass rgba) |
| `--surface` | `#10111c` | Elevated sections |
| `--surface2` | `#161724` | Deep hover states |

### Borders

| Variable | Hex | Usage |
|---|---|---|
| `--border` | `#1c1d2e` | Section dividers |
| `--border2` | `#252638` | Structural inner borders |

Glass cards use a three-property directional border in place of `--border2` (see Glassmorphism Implementation).

### Text

| Variable | Hex | Usage |
|---|---|---|
| `--white` | `#eceef8` | Headings, names, high-emphasis labels |
| `--text` | `#c8cce0` | Body copy |
| `--muted` | `#7e8199` | Metadata, nav links, secondary labels |
| `--dim` | `#52546e` | Decorative, tertiary, placeholders |

### Accent Colors (Desaturated / Jewel-Toned)

| Variable | Hex | Previous | Primary usage |
|---|---|---|---|
| `--accent` | `#4a6cf7` | `#4f7cff` | Blue — primary CTA, Trust & Safety, nav dot |
| `--accent2` | `#00b8e8` | `#00c8ff` | Cyan — LLM/AI domain, gradients |
| `--gold` | `#e8963e` | `#f0a050` | Amber — gaming, experience highlights |
| `--red` | `#e03050` | `#ff4455` | Jewel red — warnings, violations, red teaming |
| `--green` | `#27c47a` | `#30d980` | Muted green — Community Management, status |
| `--purple` | `#8862e0` | `#9b6ef3` | Muted purple — Cognizant, education |

### Gradient Pairs

- **Primary CTA:** `linear-gradient(135deg, #4a6cf7, #00b8e8)`
- **Hero name:** `linear-gradient(90deg, #4a6cf7, #00b8e8)` — gradient text via `-webkit-background-clip`
- **Stat numbers:** `linear-gradient(135deg, var(--accent), var(--accent2))` — gradient text

---

## Typography

Three typefaces, each with a strict role. The combination creates a deliberate tension: architectural condensed display, warm editorial serif, cold precision mono.

### 1. Bebas Neue — Display

```css
--font-display: 'Bebas Neue', sans-serif;
```

- **Role:** Hero names, section headings, card titles, timeline roles, stat numbers
- **Letter-spacing:** `-0.03em` on display-scale headings (high-fashion tightening), `-0.02em` on section headings
- **Sizes:** `clamp(5rem, 13vw, 13rem)` hero, `clamp(4rem, 10vw, 10rem)` page titles, `clamp(2.5rem, 5vw, 5.5rem)` sections

### 2. Crimson Pro — Body + Navigation

```css
--font-body: 'Crimson Pro', serif;
```

- **Role:** All body copy, descriptions, **and navigation links** (`font-weight: 300`, `letter-spacing: 0.04em`)
- **Nav links change from previous:** was JetBrains Mono uppercase — now Crimson Pro 300 weight for elegance
- **Body sizes:** `1.1rem` hero desc, `1rem` section desc, `0.95rem`–`0.88rem` card copy
- **Line height:** `1.6` base, `1.8`–`1.9` prose

### 3. JetBrains Mono — Metadata Only

```css
--font-mono: 'JetBrains Mono', monospace;
```

- **Role:** Status badges, eyebrow labels, data rows, navigation CTA, breadcrumbs, tags, year markers
- **Strictly limited** to small UI chrome — not used for navigation links or section labels where Crimson Pro now applies
- **Sizes:** `0.55rem`–`0.78rem`, always uppercase, letter-spacing `0.1em`–`0.3em`

---

## Layout System

### Page Padding

| Context | Desktop | Mobile |
|---|---|---|
| Homepage sections | `10rem 3rem` | `4rem 1.5rem` |
| Inner-page content sections | `8rem 3rem` | `X 1.5rem` |
| Page heroes | `11rem 3rem 7rem` | `X 1.5rem` |
| Contact / about sections | `8rem 2.5rem` | `3rem 1.5rem` |

### Grid Gaps

Cards are no longer flush-joined with 1px gaps. All card grids now use open gutters:

| Grid type | Old gap | New gap |
|---|---|---|
| Skills / work cards | `1px` (seamless) | `2rem` |
| Violation / action grids | `1px` (seamless) | `1.5rem` |
| Platform / abuse grids | `1.5rem` | `2rem` |
| Stat bars | `1px` (seamless) | `1rem` |
| Cert list | `1px` (seamless) | `0.75rem` |

The parent grid containers no longer carry `background: var(--border)` or `overflow: hidden` — the visual separation now comes from the card's own glass border.

---

## Text Rendering

All six files set these properties on `body` for maximum sharpness on retina and OLED displays:

```css
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
text-rendering: optimizeLegibility;
```

---

## Glassmorphism Implementation

All card and surface components use semi-transparent glass instead of solid ink backgrounds:

```css
background: rgba(12, 13, 22, 0.7);
border: 1px solid rgba(255, 255, 255, 0.1);
border-bottom-color: rgba(255, 255, 255, 0.03);
border-right-color: rgba(255, 255, 255, 0.03);
border-radius: 6px;
backdrop-filter: blur(20px);
-webkit-backdrop-filter: blur(20px);
```

The three-property border simulates a **top-left light source**: the top and left edges catch more light (`0.1` opacity) while the bottom and right fall into shadow (`0.03` opacity).

Applied to: `.skill-card`, `.work-card`, `.stack-card`, `.info-card`, `.hero-stat`, `.contact-item`, `.mf-input`, `.violation-item`, `.action-item`, `.esc-step`, `.case-card`, `.platform-card`, `.abuse-item`, `.tool-item`, `.attack-card`, `.edu-card`, `.cert-item`, `.principle-card`, `.beyond-card`, `.skill-item`, `.stat-item`, `.contact-strip`, `.photo-quick-facts`.

> **Note:** Nav borders use `border-bottom: 1px solid rgba(255,255,255,0.05)` (single edge, no directional override) to avoid simulating a light source on a full-width strip.

### Navigation Glass

Both the main nav and sticky tab nav use a higher-blur glass:

```css
/* Main nav */
background: rgba(7, 8, 15, 0.6);
backdrop-filter: blur(20px);
-webkit-backdrop-filter: blur(20px);
border-bottom: 1px solid rgba(255, 255, 255, 0.05);

/* Tab nav */
background: rgba(7, 8, 15, 0.7);
backdrop-filter: blur(24px);
-webkit-backdrop-filter: blur(24px);
border-bottom: 1px solid rgba(255, 255, 255, 0.05);
```

---

## Interaction & Motion

### Form Field Focus States

Contact form inputs (`.mf-input`) use a three-property spring transition and a visible but restrained focus ring:

```css
.mf-input {
  border: 1px solid rgba(255,255,255,0.07); /* softer than card borders — inputs read as recessed */
  transition: border-color 0.4s cubic-bezier(0.16,1,0.3,1),
              background   0.4s cubic-bezier(0.16,1,0.3,1),
              box-shadow   0.4s cubic-bezier(0.16,1,0.3,1);
}
.mf-input:focus {
  border-color: rgba(74,108,247,0.4);      /* --accent at low opacity */
  background: rgba(22,23,36,0.9);          /* slightly brighter than resting state */
  box-shadow: 0 0 0 3px rgba(74,108,247,0.06); /* accessibility glow ring */
  outline: none;
}
.mf-input::placeholder { color: rgba(200,204,224,0.5); } /* legible but clearly secondary */
```

The `0.07` resting border keeps inputs visually recessed relative to cards (`0.1`). Placeholder opacity is `0.5` — high enough to read the hint text, low enough to never be mistaken for filled content. The 3px glow ring provides a keyboard-accessible focus indicator without breaking the dark palette.

### Contact Item Layout

Contact rows (`.contact-item`) are flex rows with the icon+value pair aligned via `.ci-big-val`:

```css
.contact-item {
  display: flex; align-items: center; gap: 1.25rem;
  padding: 1.4rem 1.5rem;
}
.ci-big-val {
  display: flex; align-items: center; gap: 0.75rem; /* icon + text baseline */
  flex: 1;
}
```

The SVG icon inside `.ci-big-val` carries `flex-shrink: 0` so it never collapses in narrow viewports. Alignment is defined entirely in CSS — no inline styles on the markup.

### Status Indicator Pattern

Pulsing availability dots are CSS classes, not inline styles, so the animation cannot cause layout shifts:

```css
/* index.html — used inside .avatar-status */
.status-pulse {
  width: 6px; height: 6px; border-radius: 50%;
  background: var(--green);
  box-shadow: 0 0 6px var(--green);
  flex-shrink: 0; /* prevents dot from collapsing in tight flex rows */
  animation: pulse 1.5s infinite;
}

/* about.html — used inside .photo-status */
.status-dot {
  width: 6px; height: 6px; border-radius: 50%;
  background: var(--green);
  box-shadow: 0 0 6px var(--green);
  flex-shrink: 0;
  animation: pulse 1.5s infinite;
}
```

The `pulse` keyframe only modulates `opacity` (`1 → 0.3 → 1`) — no size, transform, or position changes — so adjacent text is guaranteed to remain stable. All parent containers use `display: flex; align-items: center` with an explicit `gap` rather than relying on margin.

### Transition Easing

All interactive elements use a premium spring curve:

```css
transition: [property] 0.6s cubic-bezier(0.16, 1, 0.3, 1);
/* hover glows use 0.8s for a softer arrival */
```

This replaces the previous `ease` and linear `0.2s`/`0.3s` timings. The cubic-bezier produces a fast-start, slow-settle "spring" characteristic.

### Hover Pattern: Soft Glow

Replaces the old "shimmer sweep" (translating gradient from left to right). Cards now use:

1. **Radial glow** — `::after` pseudo with a radial gradient that fades in via `opacity: 0 → 1`
2. **Border brightening** — `border-color: rgba(255,255,255,0.1)` on hover
3. **Box shadow lift** — `box-shadow: 0 8px 48px rgba([accent], 0.10–0.15)` on hover
4. **Top border fade** — `::before` at 1px height fades from `opacity: 0 → 1` (replaces scaleX sweep)

```css
/* Example: skill card */
.skill-card::after {
  content: '';
  position: absolute; inset: 0;
  background: radial-gradient(ellipse 150% 120% at 50% -5%, rgba(74,108,247,0.10) 0%, transparent 75%);
  opacity: 0;
  transition: opacity 0.8s cubic-bezier(0.16, 1, 0.3, 1);
}
.skill-card:hover::after { opacity: 1; }
.skill-card:hover {
  border-color: rgba(255,255,255,0.1);
  box-shadow: 0 8px 48px rgba(74,108,247,0.12);
}
```

The glow ellipse is `150% 120%` — wider and taller than the card — positioned at `50% -5%` so the brightest point sits just above the card's top edge. This creates an atmospheric bloom rather than a tight cone. Max opacity is `0.10` across all domains.

Domain-specific glow colors:
- Trust & Safety / default: `rgba(74,108,247,0.10)` blue
- Community Management: `rgba(39,196,122,0.10)` green
- Red Teaming / LLM: `rgba(224,48,80,0.10)` jewel red

### Button Interactions

```css
.btn-primary {
  box-shadow: 0 4px 24px rgba(74,108,247,0.25);
  transition: opacity 0.6s cubic-bezier(0.16, 1, 0.3, 1),
              transform 0.6s cubic-bezier(0.16, 1, 0.3, 1),
              box-shadow 0.6s cubic-bezier(0.16, 1, 0.3, 1);
}
.btn-primary:hover {
  opacity: 0.9;
  transform: translateY(-3px);
  box-shadow: 0 20px 40px rgba(74,108,247,0.2);
}
.btn-secondary:hover { border-color: var(--accent2); transform: translateY(-3px); }
```

Buttons lift `3px` on hover. The `box-shadow` is included in the transition curve so the shadow expands smoothly from a tight `4px 24px` ambient to a broad `20px 40px` bloom as the button rises. Applied to `index.html` and `about.html`.

---

## Animations (Unchanged from original)

```css
@keyframes pulse    { 0%,100%{opacity:1} 50%{opacity:0.3} }
@keyframes fadeUp   { from{opacity:0;transform:translateY(28px)} to{opacity:1;transform:none} }
@keyframes fadeLeft { from{opacity:0;transform:translateX(28px)} to{opacity:1;transform:none} }
@keyframes orbFloat { 0%,100%{transform:translateY(0) scale(1)} 50%{transform:translateY(-30px) scale(1.05)} }
@keyframes marqueeScroll { 0%{transform:translateX(0)} 100%{transform:translateX(-50%)} }
```

Hero entrance animations (fadeUp with staggered delays 0.1s–1.4s) are preserved.

---

## Background Effects

### Atmospheric Radial Washes (replaces grid lines)

Present on all pages via `.grid-bg`. Extremely low opacity — perceptible as depth, not pattern:

```css
.grid-bg {
  position: fixed; inset: 0;
  background:
    radial-gradient(ellipse 80% 60% at 15% 50%,  rgba(74,108,247,0.025) 0%, transparent 100%),
    radial-gradient(ellipse 60% 50% at 85% 20%,  rgba(0,184,232,0.02)   0%, transparent 100%),
    radial-gradient(ellipse 50% 40% at 50% 90%,  rgba(136,98,224,0.015) 0%, transparent 100%);
  pointer-events: none; z-index: 0;
}
```

Three overlapping washes — left blue, right-top cyan, bottom-center purple — create a gentle ambient light effect rather than a grid structure.

### Grain Texture (index.html only)

Preserved on `body::after`: SVG `feTurbulence` fractalNoise at `opacity: 0.025`, outer element at `opacity: 0.5`. Adds tactile depth over the atmospheric washes.

### Floating Orbs (homepage hero only)

Three blurred radial gradients (`filter: blur(80px)`) floating on 8–12s loops behind the hero copy. Unchanged from original.

### Page Hero Glows

Each domain page retains its `radial-gradient` glow in the hero, positioned at `ellipse at 60–70% 50%`. Colors use the domain accent at `0.05–0.06` opacity.

---

## Responsive Breakpoints

Single breakpoint at `900px`. On mobile:

- Horizontal padding: `3rem → 1.5rem` on all sections
- Layouts collapse to single column (`.intro-grid`, `.skills-grid-3`, `.edu-grid`, etc.)
- `.hero-right` hidden, `.hero-left` goes full width
- Nav links hidden (CTA remains)
- Skills and featured grids go single column

---

## Scrollbar

```css
::-webkit-scrollbar       { width: 3px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: var(--border2); }
```

Minimal 3px scrollbar matching the dark palette.
