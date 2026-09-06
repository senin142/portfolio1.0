# Project Context — Shubhanshu Pandey Portfolio

This file gives Claude Code persistent context for this repo. Read this before making any changes.

## Who this is for

Shubhanshu Pandey — Full-Stack Engineer, 4+ years experience, MultiTV Solution (CNBC Arabia platform). Recently promoted (last ~2 months) to lead a team of 5–6 engineers, including a new TV app (Android TV / smart TV) initiative. Backend-leaning: NestJS, PostgreSQL, Google Cloud. Also does React/Next.js front-end work. Based in Lucknow, Uttar Pradesh, India; open to remote roles and Lucknow-based roles.

Job search target: Full-Stack Engineer / Senior Full-Stack Engineer roles, primarily remote (₹18L–₹28L+ target), Lucknow-local as fallback (₹12L–₹20L).

## Hard rule: only defensible claims

Every claim in the portfolio, CV, and README must be something Shubhanshu can explain in detail under interview pressure. Before adding or keeping any claim, ask: "could he defend this for 5 minutes if challenged?" If not, cut it or mark it clearly as staging/in-progress/aspirational.

**Do not re-add anything related to Cloud Armor, WAF, or GA4 traffic anomaly investigation** — this was removed deliberately because he couldn't back it up in an interview. If asked to work on security/traffic topics, do not resurrect this framing.

**Do not fabricate metrics.** Only use numbers he's explicitly confirmed:
- 40+ PostgreSQL tables migrated, one exceeding 50,000 records
- 100+ bugs resolved (backend + frontend, no exact ticket count available)
- Team of 5–6 engineers, promoted to lead ~2 months ago
- 4+ years total experience (joined MultiTV Solution as a fresher, April 29, 2022)
- Meta/YouTube ingestion pipeline: 1 account per platform (Facebook, Instagram, YouTube), currently in STAGING, not production — do not claim it's deployed/live until he confirms otherwise.

## Real technical background (verified, safe to reference)

- Designed the platform's core NestJS microservices architecture: a dual-controller-per-domain pattern (admin vs. public endpoints sharing one service layer), plus shared libraries for auth (dual RBAC + subscriber models), DTOs/entities, and error handling, reused across independently-deployable services in an Nx monorepo.
- Factored ingestion monitoring (run-tracking, rate-limiting) out of platform-specific integration code for the Meta/YouTube analytics pipeline.
- Designed and migrated 40+ PostgreSQL tables (bilingual Arabic/English content) via Sequelize-TypeScript, including a 50,000+ row table.
- Resolved 100+ production/pre-production bugs: notable ones include a BT.601/BT.709 colorspace mismatch on livestream video, a GCS upload race condition, and an Elasticsearch sort-query bug.
- Front-end: React, Next.js, SEO work (XML sitemaps, RSS feeds) for CNBC Arabia, World Climate Institute, Mazars.
- Stack: JavaScript/TypeScript, Node.js, NestJS, React, Next.js, PostgreSQL, Sequelize-TypeScript, Elasticsearch, Google Cloud (Cloud Run, GCS, Cloud Scheduler, Cloud Tasks, Secret Manager).

**Never reproduce or reference actual proprietary code, real client/business logic, internal codenames, or anything from his employer's real codebase — even structurally.** Portfolio projects must be original, clean-room implementations only inspired by generic architectural patterns (see below), never copied.

## Portfolio design system (for consistency in future edits)

- Dark theme: `--bg:#0c1218`, `--bg-elev:#131b23`, `--text:#e7edf2`, `--text-muted:#8b9aac`, accent teal `--accent:#4fd6c4`, amber `--amber:#e8a33d` (used only for "in progress/staging" status, not decoration).
- Fonts: Space Grotesk (headings), Inter (body), JetBrains Mono (labels, tags, terminal UI).
- Signature element: a terminal-style hero panel showing real (non-sensitive) log lines representing actual work.
- Case study cards use a status dot + label: teal "Deployed" / amber "In staging" / teal "Ongoing" — never mark something deployed if it isn't.
- Single-file HTML (`index.html`), no build step, hosted via GitHub Pages at https://senin142.github.io/portfolio1.0/

## Portfolio projects (original, clean-room — not employer code)

1. **Content CMS** (renamed from "Bilingual Content CMS" — Arabic/RTL support was removed at Shubhanshu's request; the real bilingual work stays in "Selected Systems" since that's actual CNBC Arabia work, not this personal project). NestJS + PostgreSQL + Next.js, JWT auth, article CRUD with role-gated publishing. Demo seed users are neutral names (Alex Morgan, Jordan Lee) — never re-add Arabic-sounding demo names to this project, since it no longer has any Arabic/bilingual framing. Built at `d:\work\NextStep\backend` + `frontend`, committed locally, not yet pushed to GitHub or deployed.
2. **Role Workflow Portal** — NestJS + PostgreSQL + Next.js, a case (requester → reviewer → admin) moving through a server-enforced pipeline (submitted → assigned → in_review → resolved/rejected). Inspired generically by multi-role workflow platforms (not copied — no real role names, no payment/video features). Built at `d:\work\role-workflow-portal`, committed locally, not yet pushed to GitHub or deployed.
3. **Intentionally de-emphasized in the portfolio**: these are personal side projects, not the main point. `index.html` no longer gives them their own numbered section or full case-study cards — they're a single low-key "Also built" line right after "Selected Systems" (real employer work stays the centerpiece of the homepage). Keep it that way; don't re-inflate this into a full section unless Shubhanshu asks.
4. The CV's "PERSONAL PROJECTS" entries are already in sync with this (Content CMS description updated, no Arabic wording). Both projects should get real "View code" links once pushed to GitHub.

## When adding a new project or case study

1. Confirm with Shubhanshu (via the chat, not assumed) that any new claim is something he actually did and can defend.
2. Update `index.html`, the CV (separate file, ask if unsure where it lives), and `README.md` together — keep all three in sync.
3. Keep the CV to one page; keep the portfolio's case-study grid to a clean 2-column layout.
4. Never mark a project "Deployed" until it has a real, working live URL.
