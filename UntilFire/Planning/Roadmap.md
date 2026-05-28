---
project: UntilFire
source_path: docs/ROADMAP.md
migrated_from_repo: /home/adminuser/projects/UntilFire
migrated_at: 2026-05-20T09:16:16+00:00
updated_at: 2026-05-28
---

# UntilFire — Product Roadmap
Last updated: 2026-05-28

---

## Product Direction

**Positioning:** Personal finance that sets you free.

UntilFire should be framed as a **financial freedom app**: start with your freedom date, reduce financial stress, and give a clear path that helps work become optional over time.

**Core differentiator:** UntilFire does it with you. Most money tools either track what already happened or give you a number and leave you alone. UntilFire should show the path, the next move, and the impact of that move.

**North star:** Turn financial independence from an abstract result into a clear, emotional, actionable path:

- where do I stand?
- when can work become optional?
- what should I do next?
- how does this move my freedom date?

**Product principles:**
- Lead with freedom from financial stress and work, not with calculator jargon.
- Keep the first value moment free, fast, calm, and no-login.
- Show a concrete next move after the result, not generic FIRE advice.
- Use city/tax logic and global coverage as trust proof, not the main headline.
- Keep global / cross-border strength as support for now, not the lead story.
- Protect the first session from pressure: no early login, paywall, bank prompt, or feedback interruption.
- Treat the dashboard and Pro tier as continuity after the first aha moment, not the product’s only value.

---

## Current Reality Snapshot

### Built and already real

**Public funnel / calculator**
- 5-screen landing calculator wizard
- 263 cities worldwide with search-as-you-type city selection
- Custom city fallback with manual monthly expenses
- US tax calculations and international effective tax assumptions
- FIRE number / freedom-date reveal
- Existing portfolio balance input
- Wizard → dashboard prefill handoff
- Public calculator hub at `/calculators`
- City SEO pages under `/fire-number/*`
- FIRE Type quiz and share page infrastructure

**Dashboard / logged-in product**
- Dashboard shell and tabs
- Cashflow tracking
- Assets / liabilities
- Projection chart
- Monte Carlo simulation
- Recurring planner
- Reports
- Profile settings
- Multi-currency display

**Growth / content**
- Learning Hub
- Public learn pages
- article pages
- basic SEO plumbing

### Built but still needs production verification

**Stripe / Pro**
- checkout route
- portal route
- webhook route
- subscription sync route
- upgrade modal and subscription schema

**Plaid / bank connection**
- link token, exchange, sync, disconnect, list items, accounts routes
- dashboard UI
- free vs Pro bank-limit logic
- balances and transactions feeding product views

**AI categorisation**
- server-side categorisation route
- env var moved server-side
- basic product wiring in place

**Distribution experiments**
- FIRE Type quiz
- share page
- OG image route
- analytics wiring for share-type flows

---

## Current Focus — Private Beta Readiness 🔥

*Goal: make the friends-and-family experience clear, calm, trustworthy, and useful before any broader push.*

### Must be true now

- [ ] Full no-login calculator flow works cleanly on mobile.
- [ ] Homepage CTA clearly starts the calculator with no dead feeling.
- [ ] Result clearly shows freedom date plus at least one concrete next move.
- [ ] The first session does not push login, payment, bank connection, or feedback too early.
- [ ] The result explains why the number is believable enough to trust.
- [ ] The copy feels broader than “retire early calculator” and closer to financial freedom / reduced stress.
- [ ] The public path feels useful for beginners, not only FIRE hobbyists.

### Beta instrumentation and learning

- [ ] Track hero CTA click, calculator start, step completion, reveal, save/share/login clicks.
- [ ] Confirm feedback path only appears after value and uses calm wording.
- [ ] Review dropoff points in the current anonymous funnel.
- [ ] Capture what users want next: investing help, spending help, or income help.

### Verification and hardening

- [ ] Verify production Stripe env vars and webhook signing secret on Vercel.
- [ ] Test full Stripe flow: checkout → return → sync → portal.
- [ ] Verify production Plaid credentials and mode.
- [ ] QA bank connect / sync / refresh / disconnect / duplicate handling.
- [ ] Verify server-side categorisation env vars and fallback behavior.
- [ ] Add visible fallback/error handling where categorisation fails.

### Documentation hygiene

- [ ] Resolve overlap between root overview, PRD, roadmap, and positioning docs.
- [ ] Decide canonical agent-context notes vs legacy context bundles.
- [ ] Archive or repurpose stale planning notes that are no longer active working docs.

### Private beta gate

Minimum gate before wider distribution:
- [ ] 50 real visitors
- [ ] 20 completed freedom-date results
- [ ] 5 feedback replies
- [ ] zero critical flow issues

Stronger gate:
- [ ] 100 visitors
- [ ] 50 completed results
- [ ] 10 people willing to support/comment on launch
- [ ] zero critical flow issues

---

## Next Focus — Soft Public Launch

*Goal: test whether the product story and funnel hold up outside friends-and-family before Product Hunt.*

### Channels
- [ ] soft Reddit launch in relevant communities / weekly promo threads
- [ ] X launch thread from @GetUntilFire
- [ ] lightweight founder-led content cadence around freedom date, stress reduction, and monthly moves
- [ ] limited outreach to warm communities before broad launch spikes

### Funnel quality goals
- [ ] A new visitor can understand the product in 5 seconds.
- [ ] A new visitor can start the calculator in 1 click.
- [ ] A new visitor can reach a useful result in about 60 seconds.
- [ ] The result explains the number, timeline, and at least one move.
- [ ] Mobile experience has no obvious blockers.
- [ ] No critical console, CTA, or layout issues in the public funnel.

### Conversion / retention setup
- [ ] add “save my result” or equivalent after reveal, not before
- [ ] refine share insight around freedom date or city insight, not sensitive finances
- [ ] improve dashboard handoff so users keep their result and first next move
- [ ] decide whether FIRE Type stays public, secondary, or hidden for the launch path

---

## Product Hunt Readiness — Only After Beta Gate ✅ Then Launch Prep

*Goal: package a proven funnel, not use Product Hunt to discover basic UX problems.*

### Launch assets
- [ ] Product Hunt tagline aligned to the broader financial freedom story
- [ ] short description centered on freedom date + guided path
- [ ] maker comment with personal story and “UntilFire does it with you” angle
- [ ] 20–40 second demo clip
- [ ] 3–5 screenshots: hero, calculator step, result, next move, dashboard continuity
- [ ] FAQ answers: assumptions, privacy, who it is for, why it is free

### Launch criteria
- [ ] beta gate met first
- [ ] soft public launch shows acceptable completion and no critical trust blockers
- [ ] messaging feels broader than a niche FIRE calculator
- [ ] share path is clear and non-sensitive

---

## Post-Launch Growth & Early Revenue

*Goal: turn launch attention into repeat usage, email capture, and first paying customers.*

### Growth
- [ ] city SEO expansion beyond the first set of pages
- [ ] FIRE / freedom topic pages linked from result flows
- [ ] creator / newsletter / podcast outreach once the funnel proves itself
- [ ] referral loop built around freedom-date insight, not private financial details

### Product
- [ ] improve adjust-inputs flow from result screen
- [ ] improve beginner explanation of assumptions and methodology
- [ ] email result summary with top move
- [ ] sync custom dashboard categories to Supabase across devices
- [ ] persist useful dashboard views in URL / state cleanly

### Monetisation
- [ ] finalize free vs Pro packaging around the current beta pricing approach
- [ ] keep paid asks after free value is delivered
- [ ] align pricing page around guidance / monthly moves, not generic dashboard access
- [ ] keep Stripe identifiers and secrets out of docs and notes

---

## Monthly Moves Adviser

*Goal: make UntilFire useful every month, not just once.*

### Core adviser layer
- [ ] personalized monthly action plan based on spending, income, city, savings rate, and timeline
- [ ] recommendations framed as clear moves with freedom-date impact
- [ ] explanation of tradeoffs: impact, difficulty, confidence, and why it matters
- [ ] editable assumptions so guidance feels understandable, not magical
- [ ] monthly progress card or email

### Supporting product depth
- [ ] spending reports tied directly to freedom-date impact
- [ ] recurring bills and income insights tied to monthly moves
- [ ] Coast FIRE / Barista FIRE scenarios
- [ ] stronger scenario comparison and confidence ranges
- [ ] optional deeper bank integration only if it clearly improves advice quality

---

## Later Depth

*Goal: deepen the product after the main funnel, guidance loop, and retention model are working.*

### Product depth
- [ ] partner / spouse mode
- [ ] advanced assumptions editor
- [ ] better international depth for priority regions once demand justifies it
- [ ] installable PWA or stronger mobile web shell

### Platform / trust
- [ ] public methodology page
- [ ] embeddable calculator for partners
- [ ] creator / partner integrations

---

## Priority Decisions Currently Set

1. **Category:** frame UntilFire broadly as a financial freedom app, not only a FIRE tool.
2. **Emotional center:** freedom from financial stress and work are the same core story.
3. **Global story:** keep international / cross-border depth as supporting proof for now, not the lead promise.
4. **Launch path:** private beta first, then soft public launch, then Product Hunt only after the beta gate is met.
5. **Plaid:** keep bank connection secondary until trust is earned; do not make it the hero path.
6. **Monetisation:** keep paid infrastructure ready, but avoid early paywall pressure before the adviser loop is stronger.
7. **Current roadmap emphasis:** harden the current funnel, verify built infrastructure, clean overlapping docs, and learn from beta behavior.

---

## Metrics Targets

| Metric | Private Beta Gate | Soft Public Goal | 90 Days After Public Launch |
|---|---|---|---|
| Homepage → calculator start | qualitative clear pass | 35%+ | 40%+ |
| Calculator completion rate | 20 completed results minimum | 45%+ | 55%+ |
| Result → save/share/login action | observe baseline | 10%+ | 18%+ |
| Monthly active users | — | 250+ | 1,000 |
| Registered users | — | 75+ | 300 |
| Paid subscribers | — | low / experimental | 50 |
| MRR | — | exploratory | $450+ |

---

## What We Are Deliberately NOT Building Yet

- native mobile app before the web funnel is proven
- heavy budgeting-app parity for its own sake
- login-first onboarding
- making Plaid a first-session dependency
- advanced advice that creates regulated-advice risk
- broad global expansion as the main public story before the core positioning wins
