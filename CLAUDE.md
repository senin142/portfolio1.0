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

- **Light, editorial theme** (changed 2026-09-14 from the original dark+terminal theme, per Shubhanshu's explicit choice after reviewing portfolio-design research): warm off-white `--bg:#faf8f4`, white card surfaces `--bg-elev:#ffffff`, ink text `--text:#20241f`, muted `--text-muted:#5c6259`, accent teal `--accent:#2f8f80` (darkened from the old `#4fd6c4` for AA contrast on a light background), amber `--amber:#b3691a` (status-only, never decoration).
- The hero terminal panel is kept as a **deliberate dark contrast element** — it does NOT use the page's light tokens; it has its own `--term-*` variables (`--term-bg:#171f1c` etc.) so it still reads as a "log/terminal" surface against the light page.
- Fonts: Fraunces (serif, headings — the "editorial" signal), Inter (body), JetBrains Mono (labels, tags, terminal UI).
- Signature element: a terminal-style hero panel showing real (non-sensitive) log lines representing actual work.
- Hero has a **single primary CTA**: "Contact me directly →" (mailto, `.btn-primary`). "View selected systems" is secondary/ghost. Don't add a second competing primary CTA in the hero — this was a deliberate research-backed choice (competing CTAs can hurt conversion).
- Hero eyebrow/lead explicitly states "Backend-leaning" and "Open to remote" — don't let this get implied-only again; keep it literal.
- Each of the 3 Selected Systems cards has a `.sys-reflect` block ("Challenge: ... Next time: ...") — keep these grounded strictly in already-verified facts below; if adding a new one, confirm with Shubhanshu first per the hard rule.
- Case study cards use a status dot + label: teal "Deployed" / amber "In staging" / teal "Ongoing" — never mark something deployed if it isn't.
- Single-file HTML (`index.html`), no build step, hosted via GitHub Pages at https://senin142.github.io/portfolio1.0/
- **Light/dark mode toggle** (added 2026-09-14): a circular sun/moon button in the nav's top-right, next to "Get in touch". Implementation: `data-theme="light"|"dark"` on `<html>`, dark palette overrides declared right after the light `:root` block (source order matters — same specificity, later wins), persisted to `localStorage['theme']`, defaulting to `prefers-color-scheme` on first visit. A tiny synchronous script is the very first thing in `<head>` (before the Google Fonts link and the `<style>` block) so the theme is set before first paint — don't move it later or a light-mode flash comes back on a stored dark preference. The hero terminal panel's `--term-*` tokens are deliberately NOT overridden per-theme — it stays dark in both.

## Portfolio projects (original, clean-room — not employer code)

1. **Content CMS** (renamed from "Bilingual Content CMS" — Arabic/RTL support was removed at Shubhanshu's request; the real bilingual work stays in "Selected Systems" since that's actual CNBC Arabia work, not this personal project). NestJS + PostgreSQL + Next.js, JWT auth, article CRUD with role-gated publishing, tags, a public reading site, and real-time (Socket.IO) publish notifications. Demo seed users are neutral names (Alex Morgan, Jordan Lee) — never re-add Arabic-sounding demo names to this project. Built at `d:\work\NextStep\backend` + `frontend`. **Split into two repos and pushed to GitHub: https://github.com/senin142/portfolio_backend and https://github.com/senin142/portfolio_frontend** (the old combined `content-cms` repo is orphaned/stale — Shubhanshu still needs to delete it manually via GitHub Settings, since the cached credential's OAuth scope lacks `delete_repo`). Not deployed live yet.
2. **Role Workflow Portal** — NestJS + PostgreSQL + Next.js, a case (requester → reviewer → admin) moving through a server-enforced pipeline (submitted → assigned → in_review → resolved/rejected). Inspired generically by multi-role workflow platforms (not copied — no real role names, no payment/video features). Built at `d:\work\role-workflow-portal`. **Pushed to GitHub: https://github.com/senin142/role-workflow-portal** (not deployed live yet).
3. **Video player access-control demo** (`streaming-demo.html`, its own page, linked from the homepage's "Also built" line) — practices geography + time-window blocking patterns from real broadcast video work: a live-stream player with a simulated always-on India geo-block plus a real recurring 5-minute scheduled-break window at the top of every hour, both overridable via an "Unblock" button; a VOD player with a custom Video.js control-bar "Playlist" button and a persistent playlist below it. Uses Video.js. Sources are deliberately chosen for reliable cross-origin playback (verified by hand, not guessed) — test-streams.mux.dev for live HLS, MDN's/W3Schools' CC0 clips for VOD. **If asked to touch this page again: verify any new video URL actually resolves with `curl -I` before using it** — several "well-known free stream" URLs (NASA TV's old Akamai endpoint, the old commondatastorage/shaka-demo-assets Google buckets) are now dead or blocked by the browser (ORB) despite being widely cited online; don't reintroduce them. Lives inside the portfolio repo itself, not a separate GitHub repo.
4. **Intentionally de-emphasized in the portfolio**: all three of the above are personal side projects, not the main point. `index.html` no longer gives them their own numbered section or full case-study cards — they're a single low-key "Also built" line right after "Selected Systems" (real employer work stays the centerpiece of the homepage), now with real "View code" links for #1 and #2. Keep it that way; don't re-inflate this into a full section unless Shubhanshu asks.
5. The CV's "PERSONAL PROJECTS" entries are in sync with #1 and #2 (Content CMS description updated, no Arabic wording); the streaming demo (#3) has not been added to the CV — ask before adding it there.
6. None of the repos (portfolio_backend, portfolio_frontend, role-workflow-portal, portfolio1.0) are deployed to a live URL yet — GitHub only. Don't mark anything "Deployed" until that changes.
7. **Content CMS has an image-upload feature** (`MediaModule`, `backend/src/media/`): one image per article, an optional server-side resize toggle (sharp, max 1600px/JPEG), and a shared 150MB storage cap across all articles — the oldest images are auto-evicted past the cap. Don't advertise the underlying DB vendor (Supabase) on the public portfolio page — Shubhanshu asked for that not to be shown there, even though it's fine to use internally and mention in the repos' own READMEs/CLAUDE.md.
8. **Content CMS's Postgres now runs on a hosted Supabase project** (free tier, project ref `dargpbknmjfhhfdyoajj`, region Seoul/ap-northeast-2), replacing the local initdb instance on port 5434 for this project. `backend/.env` points at Supabase's **session pooler** (`aws-0-ap-northeast-2.pooler.supabase.com:5432`, username `postgres.dargpbknmjfhhfdyoajj`) — NOT the direct-connection host (`db.dargpbknmjfhhfdyoajj.supabase.co`), which is IPv6-only and unreachable from this network. The DB password contains a `#`, so it's quoted in `.env` (`DB_PASSWORD="..."`) — dotenv otherwise treats `#` as a comment marker and silently truncates the value. This only moves the database; the NestJS backend and Next.js frontend still run locally — this does NOT make the project "Deployed" per rule #6 above.
9. **Row Level Security must stay enabled on every table in this Supabase project.** Found during a 2026-09-14 red-team pass: creating tables via raw Sequelize migrations (rather than Supabase's own UI) skips the usual RLS nudge, and Supabase's auto-generated PostgREST API defaults to exposing any table without RLS to anyone holding the public "publishable" key — this briefly exposed the full `users` table including password hashes. Fixed via `ALTER TABLE ... ENABLE ROW LEVEL SECURITY` (no policies — this app's own connection uses the `postgres` superuser, which bypasses RLS, so nothing else had to change). **If a new migration ever adds a table to this Supabase project, enable RLS on it in the same migration** — it will not happen by default.

## When adding a new project or case study

1. Confirm with Shubhanshu (via the chat, not assumed) that any new claim is something he actually did and can defend.
2. Update `index.html`, the CV (separate file, ask if unsure where it lives), and `README.md` together — keep all three in sync.
3. Keep the CV to one page; keep the portfolio's case-study grid to a clean 2-column layout.
4. Never mark a project "Deployed" until it has a real, working live URL.
