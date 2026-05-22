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

1. Mobile QA: full no-login homepage → calculator/onboarding → freedom-date result → monthly move flow.
2. Verify the friends/family beta path on a real phone: clear copy, save confirmations, obvious nav, no surprise prompts.
3. Confirm production Stripe/Plaid/PostHog environment only when needed; never write secret values into this vault.
4. Keep updating this log after meaningful development so future agents start with current state instead of stale chat history.
