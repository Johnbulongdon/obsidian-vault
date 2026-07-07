---
project: UntilFire
purpose: durable paper trail of recent code/docs updates, current state, and next plans for future agents
created_at: 2026-05-21
---

# Development Log

Use this as the short operational paper trail before changing code. It complements [[UntilFire/Engineering/Changelog]], [[UntilFire/Planning/Roadmap]], and [[UntilFire/Agent Context/Operating Log]].

## How to update this note

After meaningful UntilFire work:

1. Add a dated entry with the user-facing change, why it mattered, verification run, and commit if available.
2. Keep it brief; do not paste secrets, raw logs, or long diffs.
3. Link out to product/strategy notes when the change reflects a durable decision.
4. Keep future plans as bounded next actions, not a giant backlog.

## Current state — 2026-05-21

- Active goal: reach **$3k MRR** by improving activation, trust, conversion, retention, and founder-led beta learning.
- Repo: `Johnbulongdon/UntilFire`, code-focused.
- Vault: `Johnbulongdon/obsidian-vault`, product/strategy/roadmap/decision paper trail.
- Current product direction: emotional/outcome-led — freedom date, work optionality, and monthly moves. Avoid framing UntilFire as only a calculator outside SEO contexts.
- Beta stance: friends/family beta first; keep first session calm and low-pressure. Users should reach freedom date + one monthly move before feedback/login/paywall/bank prompts.
- Engineering habit: make the smallest safe change, add focused regression checks when possible, then run relevant checks plus lint/typecheck before pushing.

## Recent development trail

### 2026-07-07 — Production reverted after manual promotion of an unrelated branch; fixed by merging PR #115 to `main`

- Incident: `www.untilfire.com` / `untilfire.com` briefly served the pre-redesign landing page again after John manually promoted `codex/backlinks-2026-07-03` (commit `e9158a4`, an unrelated backlink/badge-logging branch) to production from the Vercel dashboard, overwriting the live "born twice" redesign.
- Root cause: production was being pointed at whichever branch preview was last manually promoted in Vercel, not tracking `main`. Several branches (`claude/untilfire-next-steps-uabyk5`, `codex/backlinks-2026-07-03`) each had their previews promoted to prod at different points, so prod could flip between them depending on who last clicked "Promote to Production."
- Fix: merged PR #115 into `main` (merge commit `1eff2d8`). `main`'s auto-deploy then became the new production deployment and picked up the `www.untilfire.com` / `untilfire.com` aliases automatically — no manual promotion needed.
- Residual risk: `codex/backlinks-2026-07-03` is still an open, unmerged branch. If it (or any other branch preview) gets manually promoted again, the same revert can recur. Should be merged to `main` or closed before it's promoted again.
- Recommendation going forward: treat `main` as the only source of truth for `www.untilfire.com` — merge to ship, avoid promoting arbitrary preview branches to production from the Vercel dashboard.

### 2026-07-02 — Landing page redesigned around "you are born twice"; reveal-screen conversion leak fixed (PR #115)

- Why: PostHog funnel (trailing 30 days) showed 136 visitors → 25 calculator starts (18%) → 15 freedom-date reveals → **1 signup**. Two leaks targeted: the landing decision moment, and reveal→signup where OAuth login was the only save path.
- Reveal screen: resurrected the already-built "get it by email" capture (posts to `/api/waitlist`, sends a Resend plan email) that was sitting dead in a `display:none` block, into the visible Save Plan sidebar; added a closing "Don't lose this plan" save block at the end of the reveal scroll so it no longer dead-ends at Share/Adjust.
- Landing page: full redesign of `app/components/landing/LandingPage.tsx` around a "born twice" narrative — literal birth into the grind, second birth when work becomes optional. Live countdown to the user's own freedom date (falls back to an example date), rotating dotted-globe (via `cobe`), an interactive "try it" slider using the same compounding math as the real calculator, a real per-city FIRE-readiness table, editorial pricing/quote/FAQ sections. Bank-connection trust band (logos) restored below the primary CTA rather than being the first message under it, matching the "no bank prompts before value" rule.
- Verification: `tsc --noEmit`, `next build`, ESLint clean on changed files, `npm run test:calm-startup`, Playwright browser QA (desktop + mobile) through the full wizard → reveal → email capture flow.
- Commits: `c747cf0` (redesign), `266401c` (ticker → trust band swap), `ef8da5f` (mask-fade trust strip, drop inaccurate trust cues).
- Related: acquisition work shifted from Reddit/X/HN launch posts to guest-post outreach for backlinks — see [[UntilFire/Marketing/Guest Post Outreach]].

> **Backfill note (added 2026-07-07):** the entries below from 2026-06-30 down to 2026-05-27 were missing from this log — five weeks of shipped work had no paper trail here. They are reconstructed from `git log` on `main` and the repo's `CHANGELOG.md`, not from live session notes, so verification/testing detail is thinner than usual. Treat dates/commit shas as accurate; treat "why" framing as best-effort reconstruction.

### 2026-06-30 — Free trial pricing shipped: 30 days, then extended to 3 months (PR #113, #114)

- Checkout now passes `trial_period_days` for first-time subscribers (detected by absence of a prior `stripe_subscription_id`); webhook handles `customer.subscription.trial_will_end` to send a Resend reminder email 3 days before the trial ends, idempotent via `profiles.trial_reminder_sent_at`.
- Shipped first as a 30-day trial with a prominent "we'll email you before it ends" callout on pricing/upgrade-modal/landing Pro card, then same-day extended to 90 days (3 months) across all the same surfaces.
- Commits: `5ede19f`, `691f573`.

### 2026-06-29 — Android distribution track opened: PWA manifest + Android Studio TWA project for Play Store

- Phase 1: PWA manifest, service worker, and icon set added so the app is installable as a PWA.
- Phase 2 (Option B): a full Android Studio Trusted Web Activity (TWA) project scaffolded to wrap the PWA for Play Store submission.
- Not yet reflected in `docs/ROADMAP.md`'s phase list — worth adding so future agents know this track exists and isn't still "later depth."
- Commits: `9fe27fc`, `dcc3395` (merged via PR #111).

### 2026-06-28 — Emergency fund guidance switched to a needs-only base with a six-month target

- Emergency fund target changed from whatever base was previously used to a needs-only spending base, with the target raised to six months of needs.
- Dashboard home now shows the needs-only emergency fund number directly.
- Commits: `0606e9e`, `ceaba53`, `73d9f72`.

### 2026-06-25 to 2026-06-27 — Reveal page motion polish (pre-"born twice")

- Polish pass on the reveal/result page experience with added motion, ahead of the later full "born twice" landing redesign (2026-07-02).
- Commits: `fbb2978`, `d3e876d`.

### 2026-06-22 to 2026-06-25 — Backlink / directory badge acquisition push

- Large batch of directory submissions and footer badges added as part of the backlink acquisition effort (the same lever behind the guest-post outreach plan): Stack Directory, Startup Fame, Tool Dynamo, Startup Fast (+ later "winner" badge), Wired Business, StartupBase, Fazier, MarketingDB, FirstLook, Startup Project, StartupLibrary, KittyLaunch, Noonlaunch, plus a shared backlink/directory ledger and repeated submission-status logging commits.
- This activity continued on a separate branch (`codex/backlinks-2026-07-03`) into July — see the 2026-07-07 incident entry above; that branch is still open/unmerged.
- Representative commits: `2d67739` (shared ledger), `f8fb0b2` (badge batch + submission log), `199c82a`, `0ed552a`, `f43e6d3`, `e95bdbe`.

### 2026-06-18 to 2026-06-19 — "Rate My Portfolio" checkup shipped; Scenarios tab redesigned as comparison view

- New portfolio checkup feature: Phase 1 rules-based checkup with a shareable report, Phase 2 adds a backtested performance chart vs. the S&P 500 (PR #106).
- Scenarios tab redesigned as a side-by-side comparison view (PR #107), then refined same-week with select-to-compare, removable scenarios, and a fuller ticker list.
- Neither feature appears in `docs/ROADMAP.md`'s phase checklists yet.
- Commits: `2d097f2`, `8299a8a` (PR #106), `2524c64` (PR #107), `e2ea85f`.

### 2026-06-17 — SEO expansion: state/region hubs, OG images at scale, 9 new education guides

- New SEO surfaces: state hub pages, ranking hub pages, and 6 regional hub pages (Northeast, Southeast, Midwest, Southwest, Mountain West, West Coast), all with schema markup and dashboard nav links.
- Dynamic OG images added across all 227 city pages plus all ranking/state pages.
- `/learn` expanded with 9 new guides — 5 core investing guides and 4 saving/behavioral-finance guides (PR #65, #66).
- Commits: `2a397b3`, `602509a`, `b69a604`, `ceac933`, `07e30f1`, `7fa9929`.

### 2026-06-15 to 2026-06-16 — Expat FIRE calculator + geo-arbitrage globe; Goals redesign; agent startup checklist now requires ROADMAP/CHANGELOG

- New public calculator at `/calculators/expat-fire` and a native "Expat FIRE" dashboard tab, seeded from the user's own data; ships with a full-bleed, theme-aware geo-arbitrage globe (dark ocean/white continents in light mode and inverse in dark mode) with zoom, hover popups showing FIRE-timing delta per city, and click-to-compare.
- Goals page redesigned as a personal savings-goal tracker.
- Dashboard onboarding `SetupChecklist` wired into the DashTab overview.
- Cashflow UX and nav restructure alongside these.
- Repo agent context updated to require reading `docs/ROADMAP.md` and `CHANGELOG.md` at the start of every task, and both docs synced to June 2026 state — this is the origin of the "Agent Startup Checklist" now in `CLAUDE.md`.
- Commits: `3b05554`, `d922237`, `8983d82`, `8a83de8`, `8bacbd3` / `f896740` (theme-aware iterations), `b652750` (Goals), `e3d51b6`/`91186f3` (onboarding checklist), `7f65dc3` + `b314698` (ROADMAP/CHANGELOG sync + startup checklist rule), `65d60b5` (cashflow/nav restructure).

### 2026-06-11 to 2026-06-13 — Demo video overhaul (v8 rebuild through v26)

- Roughly 15 iterations rebuilding the 43-second product demo video: real product UI in motion (not onboarding screens), horizontal renderer, brand fonts, real bank logos in a marquee, a phone-notification "swipe away spending leaks" scene, beat-synced transitions locked to the soundtrack, and final color/axis polish for a white background.
- Final render script: `demo video v26: render script for UntilFire 43s motion-graphics video`.
- Commits: `e12a81e` … `f1f02c9` (v16) … `851615c` (v26 final); ~15 commits total, not individually itemized here.

### 2026-06-09 to 2026-06-10 — Animated logo reveal + FIRE number landing glow (PR #56)

- Animated UntilFire logo reveal assets added; FIRE number on the result screen gets a landing "pop" and glow effect when it appears.
- CSV import's duplicate-detection review step finalized in the same window.
- Commits: `eb6aa8f` (PR #56), `364f357`, `71bee3b`, `4c7ec96`.

### 2026-06-05 to 2026-06-09 — FIRE Type result page fully redesigned: illustrated avatars, Trading Card, flat share poster

- FIRE Type reveal replaced the generic emoji with 16 custom illustrated meme-archetype characters (one per FIRE type), extended to full-body bold-flat-art compositions after an initial broken pass was fixed.
- Result page redesigned as a Trading Card layout on a dark background with a light-reveal animation.
- Share card replaced with a clean white "Poster" design, simplified and flattened (drop shadows removed, avatar crop tightened) after a couple of framing iterations.
- Wordmark bug fixed: orange accidentally applied to "Fire" text on the FIRE Type page.
- Commits: `6bf9670`, `0ef070d`, `f7bb679`, `38b69b2`, `3572349`, `b40600a`, `55e2054`, `784e74d`, `83f4e58`/`dc3ab5f`, `cec56c5`, `b2bd962`, `e87c425`, `cf22b8b`, `0dc7854`, `2b7ad46`, `caa4b8c`, `16af871`.

### 2026-06-05 — Category/emoji expansion; nav moved to sidebar sub-nav; Purchase Impact Calculator; recurring Plaid streams

- Expense categories and sub-categories expanded for common budgeting patterns, including a new Utilities category; emoji palette for category customisation expanded from ~30 to ~90 options; category picker added inline on transaction rows and inside the AI review modal.
- Money and Freedom sections moved from the dashboard's top bar into a collapsible sidebar sub-nav; Cashflow sub-tabs (Transactions, Categories, Recurring, Budgets) moved the same way.
- New Purchase Impact Calculator, linked from the calculators hub and the Freedom Date tab.
- Recurring tab gained a Plaid bank-streams section and a Monthly Net KPI; a subscription/investment panel and shareable FIRE Type card were added.
- Commits: `1ebfe0d`, `0495ca0`, `5386702`, `cda5f2a`, `aa331c2`, `4119ffb`, `f35c3da`, `674f79e`, `da98900`, `c2e0cac`, `f428969`.

### 2026-06-04 — Large SEO enrichment pass; welcome/retention emails via Resend; progress-chart accuracy fixes

- SEO: Organization + FAQ schema added to the calculators hub and fire-number hub, server-rendered h1s/content added to homepage/calculator/learn pages via a server/client split, article bodies enriched with structured content, generic city pages deepened with FIRE-variant/savings content, sitemap freshness signals added for deepened pages.
- Welcome email and Day-7 retention email shipped via Resend, rewritten twice same-day into a founder-voice tone with logo/branding polish; plan-recap email redesigned to match brand style (white background, brand colors, milestone graph).
- Achievements: milestones moved off a standalone card and onto the progress chart as pin bubbles; milestone naming updated (added "2 Comma Club"), join date shown.
- Progress chart accuracy: several fixes so the contributions-vs-market-gain breakdown uses actual Plaid cost-basis and portfolio snapshots instead of an overestimating cost-basis ratio, fixing a visible "V-dip" in the chart; chart defaulted to the breakdown view with the S&P 500 benchmark line eventually removed as redundant.
- Also: refund support on expenses (full and partial), a month-over-month cashflow chart at the top of the Cashflow view.
- Commits: `15d5a49`, `0ca2a7c`, `6380615`, `c92179a`, `9f8f45e`, `7f71c86`, `e0b6470`, `9780593`, `aeec2dc`, `df8d41f`, `bc01c96`, `19df1a5`, `646bf2c`/`50a78f4`, `619d975`, `4a1a493`, `e9aeb80`, `6b09998`, `ed30537`, `c25442f`, `37b5f43`, `99b7202`, `457e25e`.

### 2026-06-03 — AI classification review step + need/want rules; dark mode persistence fixed; 10-bug code review pass

- AI transaction classification got a review step (approve/skip per row) before applying, plus a per-sub-category need/want rule with mismatch detection when the rule conflicts with an existing transaction.
- Dark mode now persists across page loads (this is the fix later referenced as PR #54 in `CHANGELOG.md`).
- A 10-bug code-review pass landed covering AI classification correctness, stale mismatch detection, dead code, and performance; resolved via a same-day merge-conflict cleanup to make sure all 10 fixes survived onto `main`.
- Commits: `cb1866c`, `6d33bad`, `c3899d7`, `757f4fc`, `36ad87a`, `2ee7928`, `9c83dbd`.

### 2026-06-01 to 2026-06-02 — Dashboard Overview redesigned; full dark-mode rollout; CSV import hardened; categorise route moved to OpenRouter

- Dashboard Overview tab redesigned to a dark-themed card layout matching a mockup; dark/light mode toggle added to the dashboard and mobile topbar, with a full pass converting hardcoded card/table/chart colors to CSS variables across TransactionsTab, RecurringTab, ReportsTab, ProfileTab, categories, and the donut chart.
- CSV import hardened: WeChat Pay support (GBK encoding, Chinese headers, datetime parsing), a `transfer` transaction type, a notes field carried through import, currency-aware imports, and a fix for import dropdowns being invisible in dark mode.
- AI categorisation route switched to OpenRouter; OG image redesigned to match current positioning (logo mark recreation, fixed an edge-route crash from an SVG logo fetch).
- Budget mode toggle added (manual vs. predicted from history) with needs/wants classification.
- Commits: `4ee7c48`, `a395ff5`, `c5f9b5e`, `d821eb0`, `9dd2e04`, `7cf694f`, `9c22a5d`, `78d8349`, `dcfc7be`, `173d352`, `5369bdf`, `13a7475`, `18d1bbb`, `f2cccd9`, `563b2b5`.

### 2026-05-27 to 2026-05-30 — CSV import launched; dashboard/landing "sprint 17–22" overhaul; bank-logo trust strip; pricing copy fix

- CSV import for transactions shipped for the first time, with duplicate detection, wired into the Transactions tab.
- A run of dashboard/result-screen sprints (labeled Sprint 17 through 22 in commit messages) landed: result screen reframed as "a product moment," a monthly discipline loop on the dashboard, dashboard hero leading with freedom date + status + top move, top-spending-category insight tied to freedom-date impact, a freedom-date share card, email capture directly on the result screen, and beta trust/learning analytics events.
- Trust strip switched from text bank-name labels to real bank/brokerage logo images (Chase, Vanguard, Citi, Robinhood, US Bank, etc.).
- Pricing copy fixed to correctly state free tier = 1 bank + 1 brokerage, Pro = unlimited connections.
- Commits: `ff8385d`, `22f4883`, `1837437`, `86ac447`, `f0822ae`, `25747c1`, `727da67`, `0a6ee2f`, `4befcee`, `e25c386`.

### 2026-05-26 — Emergency fund now excludes brokerage DCA cash; Google login uses canonical UntilFire URL

- Repo update: dashboard emergency-fund logic now keeps brokerage cash in total cash/assets but excludes it from the emergency-fund "Current Savings" number when that cash is sitting in a brokerage account for scheduled investing.
- Product reason: this avoids double-assigning DCA cash as both emergency reserve and investable cash, while still showing it honestly in total assets.
- Auth update: Google sign-in now uses the canonical UntilFire production callback from `lib/site.ts` for live traffic, while localhost still uses the local origin for development.
- Setup note: Supabase **Site URL** should be the real UntilFire domain so Google shows UntilFire instead of the raw Supabase project URL on the consent screen.
- Verification target: `npm run build` before push.
- Related notes: [[UntilFire/Engineering/Auth Setup]], [[UntilFire/Engineering/Changelog]].

### 2026-05-22 — Landing positioning shifted from city/tax to guided plan

- Repo update: pulled latest `origin/main`, then cleaned the new landing page copy so the hero, how-it-works steps, comparison callout, feature cards, pricing bullets, and repo context docs emphasize UntilFire as a guided plan.
- Product reason: supports activation/conversion by making the core promise emotional and outcome-led — UntilFire does it with you — while leaving city/tax accuracy as a supporting trust feature.
- Verification: `npm run lint` and `npm run build` passed with existing warnings only after the plan hero update.
- Punchline update: added John's freedom-led punchlines to the decision layer and changed the hero to “Personal finance that sets you free.”
- Next useful action: mobile QA the public homepage to make sure the new “plan, not calculator” story scans well above the fold.

### 2026-05-21 — Marketing/social paper trail clarified

- Vault-only update: keep `UntilFire/Agent Context/Operating Log.md` and `UntilFire/Marketing/X Content Calendar.md`.
- What they are: the Operating Log tells future agents how John wants UntilFire work handled; the X Content Calendar is the reusable social/content plan for @GetUntilFire.
- Changed: added a default daily build-in-public format and linked that rule from the Operating Log so agents writing posts use the same structure, tone, and hashtags.
- Recommendation: commit and push these notes because they are durable marketing/agent-context decisions, not temporary drafts.
- Verification: reviewed file diffs and scanned edited vault markdown for secret-looking values.

### 2026-05-21 — Manual category icons now sync into transactions

- Commit: `0538750 fix: sync manual category icons in transactions`
- User issue: a transaction assigned to manual category `Dog` showed the generic `Other` box icon.
- Root cause: transaction rows looked up category metadata only from built-in categories, so manual categories fell back to default color/emoji.
- Changed: transaction list now receives the merged category list, so manual category label/color/emoji are used in transaction rows and search. Monthly summary category breakdown also includes custom category metadata.
- Verification: `npm run test:manual-category-icons`, `npm run test:categories-management`, `npm run lint`, `npm run typecheck`.
- Follow-up: if category customizations are later moved from localStorage to Supabase-first storage, keep transaction row/category summary lookup on the same merged source.

### 2026-05-21 — Category management list restored

- Commit: `07892e5 fix: restore category management list`
- User issue: manual/custom categories could disappear from the category page when they had no transactions, so users could not review/delete them there.
- Changed: category page shows all categories, including zero-spend custom categories; custom category delete now requires an explicit second confirmation and preserves historical transaction category keys.
- Verification: `npm run test:categories-management`, `npm run lint`, `npm run typecheck`.

### 2026-05-21 — Agent context aligned around $3k MRR

- Commit: `540f976 docs: align agents around $3k MRR`
- Changed: repo agent context now tells AI agents to work from latest `origin/main`, inspect existing patterns, keep changes bounded, and judge work by activation/conversion/retention/trust/acquisition toward $3k MRR.
- Related note: [[UntilFire/Agent Context/Operating Log]].

### 2026-05-21 — Public funnel and onboarding hardening

- Commits: `c12cf92`, `38cb5a9`, `75968e9`, `cce519f`, `11ebe9a`, `ed260b9`, `0bb467a`
- Theme: reduce first-session friction and protect the value moment.
- Examples: route quiz CTA into onboarding, support yearly savings input, simplify required onboarding inputs, improve achieved-FIRE chart handling, default income toward take-home pay, improve city capture coverage.
- Product rule reinforced: no early surprise surveys, feedback prompts, bank prompts, paywalls, or login before users see the freedom-date value.
- Related notes: [[UntilFire/Product/Gentle Onboarding Principles]], [[UntilFire/Product/Feedback Prompt Spec]], [[UntilFire/Planning/Roadmap]].

## Current useful next actions

1. Merge or close `codex/backlinks-2026-07-03` so it can't be manually re-promoted over the current redesign; going forward, ship to production only via merges to `main`.
2. Sync `UntilFire/Planning/Roadmap.md` (vault, stale since 2026-05-28) against `docs/ROADMAP.md` (repo, June 2026) — the repo version is more current but neither mentions Expat FIRE, Rate My Portfolio, Scenarios comparison view, or the Android/PWA track, all of which have already shipped.
3. Repo `CHANGELOG.md` hasn't had a new dated entry since the "Unreleased - 2026-06-15" section — everything from 2026-06-16 onward (Expat FIRE, SEO expansion, Rate My Portfolio, Scenarios redesign, Android/PWA, trial pricing, emergency fund change, born-twice redesign) is undocumented there too.
4. Mobile QA: full no-login homepage → calculator/onboarding → freedom-date result → monthly move flow, now against the born-twice redesign.
5. Verify the friends/family beta path on a real phone: clear copy, save confirmations, obvious nav, no surprise prompts.
6. Confirm production Stripe/Plaid/PostHog environment only when needed; never write secret values into this vault.
7. Keep updating this log after meaningful development so future agents start with current state instead of stale chat history.
