# Architecture & Technical Reference

## File Structure

```
My-Portfolio/
├── index.html                # Homepage / portfolio landing page
├── about.html                # Full biographical profile page
├── trust-safety.html         # Trust & Safety domain deep-dive
├── content-moderation.html   # Content Moderation domain deep-dive
├── community-management.html # Community Management domain deep-dive
├── llm-training.html         # LLM Training & Red Teaming domain deep-dive
├── ai-engineering.html       # AI Engineering domain deep-dive
├── nipun.jpg                 # Profile photo (used on about.html)
├── og-image.png              # Open Graph / social share image (1200×630)
├── DESIGN.md                 # Complete CSS design system reference
├── CLAUDE.md                 # Codebase documentation & conventions
├── PROGRESS.md               # Change log and deferred features
└── docs/
    └── ARCHITECTURE.md       # This file — technical details & deployment
```

---

## Homepage (index.html)

Entry point for all visitors. Contains:
- **Hero** — Name display, role tagline, "Open to Work" status indicator, hero description with left-accent border, CTA buttons, animated info card with domain tags
- **Marquee strip** — Scrolling ticker of skill keywords
- **Skills grid** — Six domain cards (Trust & Safety, Content Moderation, Community Management, LLM Training, Red Teaming, AI Evaluation) with soft radial glow hover effects
- **Featured Work grid** — Six project/domain cards with CSS-drawn thumbnails (code snippets, annotation frames, evaluation charts, moderation queues, community charts, T&S flow diagrams)
- **About snapshot** — Condensed bio with stats (6+ years, 5 companies, 2 degrees, 3 certs)
- **Contact section** — Email link, LinkedIn, hire-me CTA

---

## About Page (about.html)

Full biographical deep-dive. Contains:
- **Intro section** — Profile photo and quick-facts sidebar (status, roles, domains)
- **Career timeline** — 2019–present across 6 roles
- **Skills taxonomy** — Grouped by category
- **Education cards** — Plus certifications list
- **Philosophy section** — 4 principle cards (work values)
- **Beyond work** — Personal interests

---

## Domain Pages (trust-safety.html, content-moderation.html, community-management.html, llm-training.html, ai-engineering.html)

Each domain page follows identical structure:
- **Page hero** — Breadcrumb, large title, intro text, meta stats
- **Sticky tab navigation** — In-page section jump links
- **Multiple content sections** — Eyebrow labels, display headings, detailed breakdowns with domain-specific components (violation grids, enforcement flows, escalation steps, annotation examples, etc.)
- **Footer** — Back-to-portfolio link

---

## Tech Stack Details

- **HTML5** — Semantic markup, no frameworks
- **CSS3** — Custom properties, Grid, Flexbox, animations, `backdrop-filter`
- **Vanilla JavaScript** — Scroll-driven tab navigation, no dependencies
- **Google Fonts** — Bebas Neue (display), Crimson Pro (body/nav), JetBrains Mono (metadata)
- **Vercel hosting** — Auto-deploys from main branch
- **Vercel Analytics** — Injected via `/_vercel/insights/script.js`
- **Vercel Speed Insights** — Injected via `/_vercel/speed-insights/script.js`

---

## Running Locally

No build tools required. All files are static and shipped as-is.

```bash
# Option 1: Open directly (may have CORS issues with fonts)
open index.html

# Option 2: Use a local server (recommended)
npx serve .
# or
python -m http.server 8080
```

Then visit `http://localhost:8080`.

**Note:** CORS with fonts locally — Firefox and Safari may block Google Fonts if serving from `file://`. Use a local server to avoid this.

---

## Deployment

Hosted on **Vercel** with automatic deployments from the `main` branch.

To deploy your own fork:

1. Push to GitHub
2. Import the repository into [vercel.com](https://vercel.com)
3. Vercel auto-detects it as a static site — no configuration needed
4. Set your custom domain in the Vercel dashboard

**Auto-deploy:** Any push to `main` triggers a new production deployment.

---

## Open Graph / Social Meta Tags

All social sharing meta tags are set on `index.html`:

```html
<meta property="og:image" content="https://bynipun.com/og-image.png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:image:type" content="image/png">
<meta property="og:title" content="Nipun Aggarwal · Trust & Safety & AI Governance Portfolio">
<meta property="og:description" content="6+ years in Trust & Safety. Red Teaming LLMs, Content Moderation, Community Management & LLM Training. Open to remote roles.">
<meta property="og:url" content="https://bynipun.com/">
<meta property="og:type" content="website">
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:image" content="https://bynipun.com/og-image.png">
<meta name="twitter:title" content="Nipun Aggarwal · Trust & Safety & AI Governance Portfolio">
<meta name="twitter:description" content="6+ years in Trust & Safety. Red Teaming LLMs, Content Moderation, Community Management & LLM Training. Open to remote roles.">
```

**Image:** `og-image.png` is 1200×630px and serves both Twitter Cards and Open Graph.

---

## Environment & Dependencies

**No environment variables needed.** This is a pure static site.

**No external dependencies.** All fonts, styling, and JavaScript are either:
- Google Fonts (via CDN, preconnected in head)
- Inline CSS in `<style>` tags
- Vanilla JavaScript in `<script>` tags

No package.json, no build step, no NODE_MODULES.

---

## Known Considerations

### CORS with Fonts (Local Development)

When running locally via `file://` protocol, some browsers block Google Fonts imports. **Workaround:** Use a local server (`npx serve .` or `python -m http.server`).

### No Build Step

All CSS and JavaScript are inline. Changes made directly to HTML files are live — no compilation or transpilation. This means:
- No tree-shaking or code-splitting
- All CSS is loaded upfront
- All JavaScript files are small and vanilla-only

### Static Site Limitations

No server-side processing means:
- No form submission handling (contact form is visible but non-functional without backend)
- No dynamic content generation
- All pages are pre-built HTML files

---

## CSS Custom Properties (Color Palette)

All colors are defined as CSS variables in `:root`. Never hardcode hex values — always use the variable.

```css
:root {
  --bg: #07080f;              /* Page background */
  --ink: #0c0d16;             /* Reference (cards now use glass rgba) */
  --surface: #10111c;         /* Elevated sections */
  --surface2: #161724;        /* Deep hover states */
  --border: #1c1d2e;          /* Section dividers */
  --border2: #252638;         /* Inner borders */
  --text: #c8cce0;            /* Body copy */
  --muted: #7e8199;           /* Metadata, nav links */
  --dim: #52546e;             /* Decorative, tertiary */
  --white: #eceef8;           /* Headings, high-emphasis */
  --accent: #4a6cf7;          /* Blue — primary, T&S, nav */
  --accent2: #00b8e8;         /* Cyan — LLM/AI domains */
  --gold: #e8963e;            /* Amber — experience highlights */
  --red: #e03050;             /* Jewel red — violations, red teaming */
  --green: #27c47a;           /* Muted green — Community Mgmt, status */
  --purple: #8862e0;          /* Muted purple — education, Cognizant */
}
```

---

## Typography Reference

Three fonts, strict roles:

| Font | Role | Sizes |
|---|---|---|
| **Bebas Neue** | Display headings, titles, numbers | `clamp(5rem, 13vw, 13rem)` hero; `clamp(4rem, 10vw, 10rem)` page titles |
| **Crimson Pro** | Body copy, nav links (300 weight) | `1rem` body; `0.95rem`–`0.88rem` card copy |
| **JetBrains Mono** | Metadata, badges, breadcrumbs, tags | `0.55rem`–`0.78rem`, uppercase, `letter-spacing: 0.1em`–`0.3em` |

---

## Glassmorphism Pattern (Critical)

All cards use a three-property directional border simulating a top-left light source:

```css
background: rgba(12, 13, 22, 0.7);
border: 1px solid rgba(255, 255, 255, 0.1);
border-bottom-color: rgba(255, 255, 255, 0.03);
border-right-color: rgba(255, 255, 255, 0.03);
border-radius: 6px;
backdrop-filter: blur(20px);
-webkit-backdrop-filter: blur(20px);
```

Applied to: `.skill-card`, `.work-card`, `.stack-card`, `.info-card`, `.hero-stat`, `.contact-item`, `.mf-input`, `.violation-item`, `.action-item`, `.esc-step`, `.case-card`, `.platform-card`, `.abuse-item`, `.tool-item`, `.attack-card`, `.edu-card`, `.cert-item`, `.principle-card`, `.beyond-card`, `.skill-item`, `.stat-item`, `.contact-strip`, `.photo-quick-facts`.

---

## Spring Curve Easing

All interactive elements use the same premium cubic-bezier:

```css
transition: [property] 0.6s cubic-bezier(0.16, 1, 0.3, 1);
/* Hover glows use 0.8s for softer arrival */
```

---

## Hover Effect Pattern

Cards use a soft radial glow via `::after` pseudo-element, not mechanical sweeps:

```css
.card::after {
  content: '';
  position: absolute; inset: 0;
  background: radial-gradient(ellipse 150% 120% at 50% -5%, rgba(74,108,247,0.10) 0%, transparent 75%);
  opacity: 0;
  transition: opacity 0.8s cubic-bezier(0.16, 1, 0.3, 1);
}
.card:hover::after { opacity: 1; }
```

---

## Responsive Design

Single breakpoint at **900px**. On mobile:

- Horizontal padding: `3rem → 1.5rem`
- Grids collapse to single column
- Nav links hidden (CTA remains)
- `.hero-right` hidden, `.hero-left` full width
- Featured and skills grids go single column

---

## Status Indicator Pattern

Pulsing dots use CSS classes (not inline styles) to prevent layout shifts:

```css
.status-pulse {
  width: 6px; height: 6px; border-radius: 50%;
  background: var(--green);
  box-shadow: 0 0 6px var(--green);
  flex-shrink: 0;
  animation: pulse 1.5s infinite;
}

@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }
```

The animation only modulates `opacity` — no size, transform, or position changes — so adjacent text stays stable.

---

## Background Effects

### Atmospheric Radial Washes (all pages)

Extremely low opacity — perceptible as depth, not pattern:

```css
.grid-bg {
  position: fixed; inset: 0;
  background:
    radial-gradient(ellipse 80% 60% at 15% 50%, rgba(74,108,247,0.025) 0%, transparent 100%),
    radial-gradient(ellipse 60% 50% at 85% 20%, rgba(0,184,232,0.02) 0%, transparent 100%),
    radial-gradient(ellipse 50% 40% at 50% 90%, rgba(136,98,224,0.015) 0%, transparent 100%);
  pointer-events: none; z-index: 0;
}
```

### Grain Texture (index.html only)

SVG `feTurbulence` fractalNoise at `opacity: 0.025`, outer element at `opacity: 0.5`. Adds tactile depth.

### Floating Orbs (homepage hero only)

Three blurred radial gradients (`filter: blur(80px)`) floating on 8–12s loops. Unchanged from original.

### Page Hero Glows (domain pages)

Each domain page retains a radial gradient glow in the hero at `0.05–0.06` opacity with domain-specific accent color.

---

## Form Field Focus States

Contact form inputs use a three-property spring transition:

```css
.mf-input {
  border: 1px solid rgba(255,255,255,0.07);
  transition: border-color 0.4s cubic-bezier(0.16,1,0.3,1),
              background 0.4s cubic-bezier(0.16,1,0.3,1),
              box-shadow 0.4s cubic-bezier(0.16,1,0.3,1);
}
.mf-input:focus {
  border-color: rgba(74,108,247,0.4);
  background: rgba(22,23,36,0.9);
  box-shadow: 0 0 0 3px rgba(74,108,247,0.06);
  outline: none;
}
.mf-input::placeholder { color: rgba(200,204,224,0.5); }
```

---

## Scrollbar Styling

```css
::-webkit-scrollbar { width: 3px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: var(--border2); }
```

Minimal 3px scrollbar matching the dark palette.
