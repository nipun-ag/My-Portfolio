# Change Log & Project Progress

## Deferred Features

- **Did You Know tab equivalent for portfolio** — Planned tab section showing interesting facts or recent work snippets
- **Dark/light mode toggle** — Theme switcher for light-theme variant (currently dark-only)
- **Blog or writing section** — Dedicated page for articles, essays, or thought leadership
- **Case study PDFs for download** — PDF versions of domain deep-dives for offline sharing
- **Animation performance audit for low-power devices** — Optimization pass for reduced-motion and mobile devices

---

## 2026-05-04

Rebuilt ai-engineering.html from thin 3-section project page into dense 6-section domain page.

- **New sections** — Added Stack & Tools, Automation, Workflow (total 6 sections with proper scroll tracking)
- **Hero meta stats** — Updated to Focus, Stack, Tools Live, Philosophy (4 items instead of 3)
- **Philosophy section** — Added 5th card (AI-Assisted Development), changed grid from 2x2 to 3-column layout with eyebrow label
- **Stack & Tools section** — 9 tool cards in 3-column glassmorphism grid with category labels and cyan hover glows
- **Projects section** — Changed to single-column layout (.projects-list flex class), kept ModEval, removed Reddit Sentiment Analyzer, added Outreach job automation tool with full details
- **Automation section** — 4 pipeline stage cards (Job Discovery, Resume Tailoring, Auto-Fill, Dashboard) in 2-column grid
- **Workflow section** — 4-step horizontal flow with → arrows between cards at desktop, stacking vertically at 900px with hidden arrows
- **Architecture section** — Added "SYSTEM DESIGN" eyebrow label, kept all 6 existing layers unchanged
- **Duplicate script removed** — Removed duplicate /_vercel/insights/script.js (line 287), kept single instance
- **Responsive design** — Stack grid 3→2 cols at 900px, philosophy/automation 3/2→1 col, workflow flex→column with hidden arrows
- **No breaking changes** — All CSS variable names preserved, fonts used correctly, all tabs track scroll position

---

## 2026-04-29

Created full documentation system: CLAUDE.md, docs/ARCHITECTURE.md, PROGRESS.md. Trimmed README.md to public-facing essentials.

- **CLAUDE.md** — Codebase reference with conventions, common patterns, file structure, and current project state (105 lines, under 120-line limit)
- **docs/ARCHITECTURE.md** — Complete technical reference: file structure, local dev, deployment, CSS custom properties, glassmorphism pattern, form field focus states, responsive design
- **README.md** — Trimmed to intro, About, Tech Stack, and Design System summary (removed detailed sections moved to ARCHITECTURE.md and CLAUDE.md)
- **.gitignore** — Created with .claude/, .DS_Store, Thumbs.db
- Updated references throughout to reflect 5 domain pages (added ai-engineering.html)
