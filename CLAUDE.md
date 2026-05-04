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
| `ai-engineering.html` | AI Engineering domain deep-dive (6 sections) |
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

- CSS variable names, font imports, OG meta tags, glassmorphism border pattern
- Vercel Analytics/Speed Insights script injections
- Grain texture (body::after on index) and floating orbs (hero)

## Reference

- **docs/ARCHITECTURE.md** — Tech details, deployment, local dev
- **DESIGN.md** — CSS design system and component specs
- **PROGRESS.md** — Change log and deferred features
- **README.md** — Public-facing description

## Common Tasks

- **New section:** Read file + DESIGN.md, use CSS classes, follow glassmorphism, test at 900px
- **New domain page:** Copy existing page structure, update breadcrumb/meta/links, update ARCHITECTURE.md
- **Copy updates:** Edit HTML only, commit with `content:` prefix

## Before Starting Any Task

- Read DESIGN.md first for any CSS or visual task
- Read the specific HTML file before editing it
- Check CSS variable names before adding new styles
- Task touches multiple pages → check all affected files first

## Never Do These Without Asking First

- Add new fonts or external dependencies
- Change CSS variable names
- Modify the glassmorphism border pattern
- Add JavaScript frameworks or libraries
- Change Vercel deployment configuration
- Rename any HTML files (breaks internal links)

## Self-Updating Meta Instruction

Trigger this automatically when:
- A feature is fully working and tested
- A bug is fixed and confirmed
- You are about to switch to a different task
- The user says "done", "ship it", "looks good", "push it", "that works", or any similar confirmation phrase

Do not wait for explicit wrap up or end session instructions.

After every session:
1. Update CLAUDE.md current state section (keep under 120 lines)
2. Add a dated entry to PROGRESS.md (what changed and why)
3. Update DESIGN.md if any visual or CSS changes were made
4. Update docs/ARCHITECTURE.md if any structural changes made
5. Never append session notes to README.md
6. Run git add . && git commit -m "[type]: description" && git push

## Git Commits

Format: `type: description`

- `feat:` new page or section
- `fix:` bug fix
- `style:` CSS or visual changes
- `content:` copy or text changes
- `docs:` documentation only

## Current Project State

- 7 pages live: index, about, and 5 domain deep-dives
- AI Engineering page: 6-tab structure (Philosophy, Stack & Tools, Projects, Automation, Architecture, Workflow)
- Premium Editorial Gallery dark theme with glassmorphism
- Soft radial glow hover pattern, spring-curve easing
- Atmospheric radial washes + grain texture (homepage only) + floating hero orbs
- Vercel auto-deploy on main branch with Analytics and Speed Insights
- Live at bynipun.com
