# Nipun Aggarwal — Portfolio

Personal portfolio for Nipun Aggarwal, a Trust & Safety professional and AI Red Teaming Analyst with 6+ years of experience in content moderation, LLM evaluation, and community management.

**Live site:** [https://bynipun.com](https://bynipun.com)

---

## About

This portfolio presents Nipun's work across four professional domains: Trust & Safety, Content Moderation, Community Management, and LLM Training/Red Teaming. It is designed to serve as a detailed, domain-specific showcase for hiring managers and collaborators in AI Safety, AI Governance, and platform safety.

---

## Tech Stack

- **HTML5** — semantic markup, no frameworks
- **CSS3** — custom properties, Grid, Flexbox, animations, `backdrop-filter`
- **Vanilla JavaScript** — scroll-driven tab navigation, no dependencies
- **Google Fonts** — Bebas Neue, Crimson Pro, JetBrains Mono
- **Vercel** — hosting and deployment with Analytics and Speed Insights
- **No build step** — all files are static, shipped as-is

---

## File Structure

```
My-Portfolio/
├── index.html               # Homepage / main portfolio landing page
├── about.html               # Full biographical profile page
├── trust-safety.html        # Deep-dive: Trust & Safety domain work
├── content-moderation.html  # Deep-dive: Content Moderation domain work
├── community-management.html # Deep-dive: Community Management domain work
├── llm-training.html        # Deep-dive: LLM Training & Red Teaming work
├── nipun.jpg                # Profile photo (used on about.html)
├── og-image.png             # Open Graph / social share image (1200×630)
├── DESIGN.md                # Complete CSS design system reference
└── README.md                # This file
```

### What each file does

| File | Purpose |
|---|---|
| `index.html` | Hero section with animated orbs, skill cards, featured work grid, about snapshot, and contact form. Entry point for all visitors. |
| `about.html` | Full biographical deep-dive: intro with photo, career timeline, skills taxonomy, education & certifications, philosophy principles, and "beyond work" personal interests. |
| `trust-safety.html` | Domain page covering violation taxonomy (hate speech, harassment, NSFW, spam, etc.), enforcement actions, escalation workflows, self-harm protocols, and experience highlights. |
| `content-moderation.html` | Domain page covering moderation methodology, queue management, policy judgment, sensitive content handling, and tooling experience. |
| `community-management.html` | Domain page covering platform experience (Reddit, Discord, Khoros), community health metrics, crisis management, sentiment analysis, and weekly reporting. |
| `llm-training.html` | Domain page covering red teaming methodology, adversarial prompt techniques, output evaluation frameworks, RLHF data annotation, and VLA model training contributions. |

---

## Portfolio Sections

### Homepage (`index.html`)

- **Hero** — Name display, role tagline, status indicator ("Open to Work"), hero description with left-accent border, CTA buttons, and an animated info card with domain tags
- **Marquee strip** — Scrolling ticker of skill keywords
- **Skills** — Six domain cards (Trust & Safety, Content Moderation, Community Management, LLM Training, Red Teaming, AI Evaluation) with soft radial glow hover effects and inline arrow navigation
- **Featured Work** — Six project/domain cards with custom illustrated thumbnails (CSS-drawn code snippets, annotation frames, evaluation bar charts, moderation queues, community charts, T&S flow diagrams)
- **About snapshot** — Condensed bio with stats (6+ years, 5 companies, 2 degrees, 3 certs)
- **Contact** — Email link, LinkedIn, and a hire-me CTA

### About (`about.html`)

- Intro with profile photo and quick-facts sidebar
- Career timeline (2019–present) across 6 roles
- Skills taxonomy grouped by category
- Education cards + certifications list
- Philosophy / working principles (4 cards)
- Beyond work / personal interests

### Domain Deep-Dives (`trust-safety.html`, `content-moderation.html`, `community-management.html`, `llm-training.html`)

Each domain page follows the same structure:
- Page hero with breadcrumb, large title, intro text, and meta stats
- Sticky tab navigation for in-page sections
- Multiple content sections with eyebrow labels, display headings, and detailed breakdowns
- Domain-specific components (violation grids, enforcement flows, escalation steps, annotation examples, etc.)
- Footer with back-to-portfolio link

---

## Design System

The visual language is a **Premium Editorial Gallery** aesthetic — dark-first, glassmorphic, with editorial-scale typography and spring-curve motion. Full reference is in [`DESIGN.md`](./DESIGN.md), covering:

- Color palette (14 CSS custom properties, jewel-toned accents)
- Typography (Bebas Neue display, Crimson Pro body/nav, JetBrains Mono metadata)
- Glassmorphism implementation (card backgrounds, nav glass, directional borders)
- Layout system (section padding, open grid gutters)
- Interaction & motion (soft radial glow hover pattern, spring-curve easing)
- Background effects (atmospheric radial washes, grain texture, floating orbs)
- Responsive breakpoints

---

## Running Locally

No build tools required. Open any HTML file directly in a browser:

```bash
# Option 1: open directly
open index.html

# Option 2: use a local server (recommended to avoid CORS issues with fonts)
npx serve .
# or
python -m http.server 8080
```

Then visit `http://localhost:8080`.

---

## Deployment

Hosted on **Vercel** with automatic deployments from the `main` branch.

- Vercel Analytics: injected via `/_vercel/insights/script.js`
- Vercel Speed Insights: injected via `/_vercel/speed-insights/script.js`

To deploy your own fork:

1. Push to GitHub
2. Import the repository into [vercel.com](https://vercel.com)
3. Vercel auto-detects it as a static site — no configuration needed
4. Set your custom domain in the Vercel dashboard

---

## Open Graph / Social

Meta tags are set on `index.html` for Twitter Cards and Open Graph:

- **OG image:** `og-image.png` (1200×630)
- **Title:** Nipun Aggarwal · Trust & Safety & AI Governance Portfolio
- **Description:** 6+ years in Trust & Safety. Red Teaming LLMs, Content Moderation, Community Management & LLM Training. Open to remote roles.
