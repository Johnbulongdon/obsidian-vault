---
project: UntilFire
created_at: 2026-05-29
source: chat-plan
phase_alias: Phase 7
status: Planned
module: Public Funnel → Beta Trust + Learning Signals
---

# Sprint 22 — Beta Trust and Learning Signals

**Status:** 🔲 Planned  
**Module:** Public Funnel → Beta Trust + Learning Signals  
**Phase mapping:** Phase 7 — Make beta learning safe, calm, and measurable  
**Goal:** Learn from beta users without hurting the first value moment.

## Why this should be next

The roadmap’s current focus is still **private beta readiness**, not broader feature depth.

Sprints 18–21 define the longer-term continuity path:
- monthly guidance loop
- dashboard hierarchy
- useful tracking
- guidance-led Pro

But before those layers matter, UntilFire still needs a safer and more measurable beta funnel.

Right now there are two important gaps:
1. **Trust gap:** feedback behavior has drifted from the product rules and can feel too visible or too early.
2. **Learning gap:** current analytics cover big funnel steps, but not enough of the post-result and feedback actions needed to understand dropoff and next intent.

This sprint should close those gaps before deeper dashboard or monetisation work.

## Problem

UntilFire is in friends-and-family beta. The first session should feel calm and useful:
- user reaches their freedom date
- user gets one useful next move
- only then may UntilFire ask for anything extra

If feedback appears too visibly, opens too eagerly, or feels like something happened without intent, beta trust drops.

If analytics only show broad funnel movement but miss key post-result actions, John cannot clearly answer:
- where users hesitate
- whether the result creates action
- whether users want to save, share, sign up, or give feedback
- what should be improved next

## User stories

### Beta user
As a beta user, I want to reach my freedom-date result and see one useful next move before UntilFire asks for feedback or commitment — so the product feels calm and trustworthy.

### Founder/operator
As John, I want clear, privacy-safe signals for the first-value funnel and post-result actions — so I can see where users drop off and what they want next without guessing.

## Done when

- [ ] Feedback is only available **after the result**.
- [ ] Feedback is **hidden by default** and only opens after explicit user action.
- [ ] No stars are shown.
- [ ] No feedback UI auto-opens.
- [ ] No feedback UI auto-submits.
- [ ] If dismissed, feedback stays quiet for the session.
- [ ] The feedback entry copy is aligned to beta guidance, e.g. **“Help us improve this for you.”**
- [ ] Post-result actions are measurable with privacy-safe analytics, including the most important current actions such as:
  - primary CTA after result
  - share opened / share completed / copy fallback if applicable
  - login or signup start / complete
  - feedback opened / submitted / dismissed
- [ ] If a “save result” action exists, it is instrumented; if not, this sprint does **not** invent a new save system just to satisfy analytics.
- [ ] Analytics payloads do **not** include raw financial values, personal text, email, or sensitive details.
- [ ] The event contract is documented and typed.
- [ ] John has one simple verification/query checklist to review beta dropoff and next-step behavior in PostHog.

## Acceptance criteria

- The first experience still feels like **free value first**.
- Feedback feels optional and founder-led, not interruptive.
- Users are not pressured toward Pro, login, or feedback before understanding their result.
- Beta learning is materially clearer after this sprint.
- Event coverage is enough to answer:
  - where users stop
  - whether they reach value
  - what they try next after the result
- Mobile result screens stay calm and uncluttered.

## Out of scope

- Full in-app survey system
- Long-form onboarding questionnaires
- Major dashboard redesign
- Pro/paywall redesign
- Retention emails or notifications
- Inventing new core product surfaces only for analytics
- Deep data warehousing or complex BI work

## Recommended implementation slices

### Slice 1 — Fix feedback behavior to match beta rules
Scope:
- Gate feedback behind the result / post-value state.
- Replace any always-visible or overly prominent feedback surface that violates beta posture.
- Make feedback opt-in, dismissible, and quiet.

Likely touch points:
- `app/dashboard/FeedbackWidget.tsx`
- `app/page.tsx`
- any result-screen surface that should own the optional feedback entry point

### Slice 2 — Expand the analytics contract for beta learning
Scope:
- Add typed events for missing post-result actions.
- Keep payloads coarse and privacy-safe.
- Ensure each event has one clear emit site.

Likely touch points:
- `lib/analytics-events.ts`
- `lib/analytics.ts`
- `docs/analytics/EVENTS.md`
- `app/page.tsx`
- `app/login/page.tsx`
- feedback open/submit/dismiss surface

### Slice 3 — Add a founder-facing verification checklist
Scope:
- Document exactly which events should fire and from where.
- Add a short smoke-test list for beta QA.
- Make it obvious how to inspect post-result behavior in PostHog.

Likely touch points:
- `docs/analytics/EVENTS.md`
- Obsidian beta notes if a short query/checklist is better stored there

## Safe event design rules

- Track **intent and transitions**, not sensitive values.
- Prefer booleans, enum labels, route/source labels, and coarse buckets.
- Never send:
  - raw FIRE number
  - raw income / savings / portfolio values
  - free-text feedback body to analytics
  - email / name / city string if it can identify the user too precisely
- If feedback text needs storage, keep it in the existing feedback backend only — not in analytics properties.

## Verification

### Product behavior QA
- [ ] Fresh visitor on homepage: no feedback visible.
- [ ] User starts calculator: no feedback visible.
- [ ] User completes calculator: result is visible before any feedback ask.
- [ ] Optional feedback entry appears only after result.
- [ ] Feedback opens only after click.
- [ ] Dismiss keeps it quiet for the session.
- [ ] Mobile result still keeps the main next action obvious.

### Analytics QA
- [ ] Hero entry event path still works.
- [ ] Calculator start and step events still work.
- [ ] Reveal event still works.
- [ ] Post-result CTA events fire exactly once from the expected action.
- [ ] Feedback open / submit / dismiss events fire only on user action.
- [ ] No new event includes sensitive financial values.
- [ ] Event docs and runtime contract stay in sync.

## Suggested success readout after deploy

Within the first beta batch, John should be able to answer:
- How many people reached the result?
- Of those, how many clicked a next action?
- Which next action was most common: share, login, feedback, or leave?
- Did anyone interact with feedback before value? (should be no)
- Are there obvious mobile or result-stage dropoff points?

## Related notes

- [[UntilFire/Planning/Roadmap|Roadmap]]
- [[UntilFire/Planning/Beta Launch Checklist|Beta Launch Checklist]]
- [[UntilFire/Product/Beta Feedback|Beta Feedback]]
- [[UntilFire/Product/Feedback Prompt Spec|Feedback Prompt Spec]]
- [[UntilFire/Product/Gentle Onboarding Principles|Gentle Onboarding Principles]]
- [[UntilFire/Planning/Sprints/sprint-17-result-screen-product-moment|Sprint 17 — Result Screen Product Moment]]
- [[UntilFire/Planning/Sprints/sprint-18-monthly-discipline-loop|Sprint 18 — Monthly Discipline Loop]]

## Implementation intent

This sprint protects the first-value moment while making beta learning sharper:

**free value → clear result → optional feedback → measurable next action → better product decisions**
