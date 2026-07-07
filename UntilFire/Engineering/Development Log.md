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
2. Mobile QA: full no-login homepage → calculator/onboarding → freedom-date result → monthly move flow, now against the born-twice redesign.
3. Verify the friends/family beta path on a real phone: clear copy, save confirmations, obvious nav, no surprise prompts.
4. Confirm production Stripe/Plaid/PostHog environment only when needed; never write secret values into this vault.
5. Keep updating this log after meaningful development so future agents start with current state instead of stale chat history.
