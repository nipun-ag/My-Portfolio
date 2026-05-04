# Change Log & Project Progress

## 2026-05-05 (Session 2)

Completed major content refinement pass on ai-engineering.html. Shifted all sections from tool-specific documentation to teachable principles and patterns.

- **#automation section** — Generalized messaging from Outreach-focused to broader automation pipeline patterns (5 card updates)
- **Browser Automation card** — Refined body text for clarity on browser interaction vs HTTP scraping
- **#architecture section** — Replaced ModEval-specific 6-layer system with "PRODUCTION VS TOY" 4-principle framework (Handles Failure, Configurable, Logs What It Does, Stays Live Without Babysitting)
- **#workflow section** — Removed all tool/model names, replaced with process categories (High-End Models, Cheaper Models, AI Design Tools, Automated Deployment)
- **Result** — Page now teaches how to build and think about systems, not how to use specific tools

## 2026-05-05

Refined #automation section messaging from tool-specific examples to generalized pipeline patterns.

- **Section description** — Changed from job-hunting context to broader automation pipeline philosophy
- **Card 1** — "Job Discovery Pipeline" → "Scheduled Scraping Pipelines" (generalized to any scheduled scraping task)
- **Card 2** — "Resume Tailoring via Claude" → "AI in the Pipeline" (abstracted to any reasoning-heavy step)
- **Card 3** — "Auto-Fill Automation" → "Browser Automation" (reframed around Playwright capabilities)
- **Card 4** — "Outreach Dashboard" → "Bringing It Together" (removed URL, focused on integration pattern)
- **Result** — Automation section now teaches patterns, not products. Visitors see how pipelines work, not how Outreach works.

---

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
