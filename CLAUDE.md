# CLAUDE.md — Nipun Aggarwal Portfolio

## What This App Is

Personal portfolio for Nipun Aggarwal — Trust & Safety professional and AI Red Teaming Analyst. Five domain pages covering Trust & Safety, Content Moderation, Community Management, LLM Training/Red Teaming, and AI Engineering. Pure static site, no backend. Live at [bynipun.com](https://bynipun.com).

## Tech Stack

- Pure HTML5, CSS3, Vanilla JavaScript — no frameworks
- Google Fonts: Bebas Neue, Crimson Pro, JetBrains Mono
- Hosting: Vercel (auto-deploy on push to main)
- Analytics: Vercel Analytics + Speed Insights
- No build step — static files shipped as-is

## File Structure

| File | Purpose |
|---|---|
| `index.html` | Homepage, hero, skills, featured work |
| `about.html` | Full bio, timeline, education, certs |
| `trust-safety.html` | Trust & Safety domain deep-dive |
| `content-moderation.html` | Content Moderation domain deep-dive |
| `community-management.html` | Community Management domain deep-dive |
| `llm-training.html` | LLM Training & Red Teaming deep-dive |
| `css/ or inline styles` | All styling via CSS custom properties |
| `DESIGN.md` | Complete design system reference |

## Coding Conventions

- Semantic HTML5 only — no frameworks, no build tools
- All colors via CSS custom properties — never hardcode hex values
- Three fonts only: Bebas Neue (display), Crimson Pro (body/nav), JetBrains Mono (metadata) — never mix roles
- All card hover effects via `::after` pseudo and opacity transitions
- Spring curve easing: `cubic-bezier(0.16, 1, 0.3, 1)` on all interactive elements
- Glassmorphism pattern must match DESIGN.md spec exactly
- No inline styles — all layout defined in CSS classes
- JavaScript: vanilla only, scroll-driven tab navigation only
- No external dependencies, CDNs, or package managers

## What NOT to Touch

- CSS variable names — used across all 6 HTML files
- Font imports — Bebas Neue, Crimson Pro, JetBrains Mono
- Vercel Analytics and Speed Insights script injections
- OG meta tags on index.html — configured for social sharing
- The glassmorphism border pattern (three-property directional border) — visually critical, easy to break
- Grain texture on body::after (index.html only)
- Floating orb animations in homepage hero

## Where to Find Things

- Technical structure, deployment, local dev → `docs/ARCHITECTURE.md`
- Visual design system → `DESIGN.md`
- Change log → `PROGRESS.md`
- Public description → `README.md`

## Common Task Patterns

### Adding a new section to an existing page
1. Read the full HTML file first
2. Read DESIGN.md for relevant component specs
3. Use existing CSS classes where possible
4. Follow glassmorphism pattern for any new cards
5. Test responsive at 900px breakpoint

### Adding a new domain page
1. Copy structure from an existing domain page
2. Update breadcrumb, hero title, meta tags
3. Add link in index.html and about.html navigation
4. Update docs/ARCHITECTURE.md file structure

### Updating copy or content
1. Edit only the relevant HTML file
2. No CSS changes needed for copy updates
3. Commit with "content: description of change"

## Before Starting Any Task

- Read DESIGN.md first for any CSS or visual task
- Read the specific HTML file before editing it
- Check CSS variable names before adding new styles
- Task touches multiple pages → check all affected files first

## Git Commits

Format: `type: description`

- `feat:` new page or section
- `fix:` bug fix
- `style:` CSS or visual changes
- `content:` copy or text changes
- `docs:` documentation only

## Current Project State

- 7 pages live: index, about, and 5 domain deep-dives
- Premium Editorial Gallery dark theme
- Glassmorphism cards with directional light-source borders
- Soft radial glow hover pattern
- Spring-curve easing on all interactions
- Atmospheric radial background washes on all pages
- Grain texture on homepage only
- Floating orbs in homepage hero
- Vercel Analytics and Speed Insights active
- Deployed at bynipun.com
