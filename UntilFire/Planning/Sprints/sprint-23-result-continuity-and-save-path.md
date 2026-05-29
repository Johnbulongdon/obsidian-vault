---
project: UntilFire
created_at: 2026-05-29
source: chat-plan
phase_alias: Phase 8
status: Planned
module: Public Funnel → Result Continuity + Save Path
---

# Sprint 23 — Result Continuity and Save Path

**Status:** 🔲 Planned  
**Module:** Public Funnel → Result Continuity + Save Path  
**Phase mapping:** Phase 8 — Keep the aha moment alive after the result  
**Goal:** Make the first post-result next step obvious, calm, and worth taking.

## Why this should follow Sprint 22

Sprint 22 focuses on **beta trust and learning signals**:
- feedback only after value
- optional and quiet feedback behavior
- better post-result instrumentation

Once that is in place, the next highest-leverage question is not just **what users do after the result**, but whether UntilFire gives them a continuation path that feels worth taking.

The roadmap already points to this gap:
- add **save my result** or equivalent after reveal
- refine **share insight** around freedom date or a safe public angle
- improve **dashboard handoff** so users keep their result and first next move
- avoid losing the emotional value of the first result screen

This sprint should make the post-result path feel like the start of a relationship, not the end of a calculator.

## Problem

A user can reach their freedom date result, feel a moment of interest, and still leave because the next step is not clear enough or feels too heavy.

If the continuation path is weak, UntilFire risks three bad outcomes:
1. The result feels disposable instead of memorable.
2. The user does not know whether to save, share, sign up, or come back.
3. The product loses the emotional momentum created by the freedom-date reveal.

The post-result step should preserve the calm, low-pressure beta posture while helping the user keep or act on what they just learned.

## User stories

### Beta user
As a user who has just seen my freedom date, I want one clear way to keep this result or continue from it — so I do not feel like I have to start over later.

### Returning user
As someone interested in my result but not ready for a big commitment, I want a lightweight way to save or revisit it — so the product feels useful before asking for more.

### Founder/operator
As John, I want the post-result continuation path to be clear and measurable — so I can tell whether users want to save, share, sign up, or simply leave.

## Done when

- [ ] The result screen presents **one primary next step** after value is delivered.
- [ ] That next step feels like continuation, not pressure.
- [ ] A lightweight **save result** or equivalent continuity action exists after reveal, or a clearly defined substitute path is chosen and implemented.
- [ ] If sign-up is used as the save mechanism, the copy makes the value explicit: keep my result, keep my plan, or continue later.
- [ ] The result and top next move are preserved through the handoff into the next state where possible.
- [ ] Share remains secondary and framed around a safe, non-sensitive insight.
- [ ] The continuation path works cleanly on mobile.
- [ ] The experience avoids surprise login, paywall, or bank prompts before the user understands the result.
- [ ] Post-result actions are easy to measure using the Sprint 22 analytics foundation.

## Acceptance criteria

- The user can tell what to do next within a few seconds of seeing the result.
- The continuation path feels consistent with UntilFire’s promise: *personal finance that sets you free*.
- The product does not force commitment before first value.
- If a user leaves and returns through the chosen continuation path, the experience feels remembered rather than reset.
- The post-result screen stays emotionally clear and uncluttered.
- The primary CTA copy is calm, beginner-friendly, and benefit-led.

## Out of scope

- Full account-system redesign
- Deep lifecycle messaging or email automation
- Major dashboard redesign beyond the continuity handoff
- New monetisation experiments
- Expanding public social features beyond a safer share path
- Reworking the core calculator itself

## Recommended implementation slices

### Slice 1 — Choose the continuation mechanic
Scope:
- Decide the smallest good next step after reveal:
  - save result
  - continue later
  - create account to keep my plan
- Prefer one primary action, not several equal-weight actions.
- Ensure the action is clearly downstream of first value.

Likely touch points:
- `app/page.tsx`
- result-screen CTA components
- any auth/signup handoff copy

### Slice 2 — Preserve result continuity through handoff
Scope:
- Keep the freedom date, top next move, and enough context to make continuation feel seamless.
- Avoid making users feel they lost what they just unlocked.
- Make the first logged-in or saved state clearly connected to the original result.

Likely touch points:
- `app/page.tsx`
- auth/signup handoff logic
- dashboard prefill / onboarding state
- any result persistence helper already in the app

### Slice 3 — Make share supportive, not dominant
Scope:
- Keep share available but secondary.
- Frame sharing around safe insight such as freedom date progress, city angle, or a motivational public framing — not raw private numbers.
- Ensure share does not steal emphasis from the save/continue path.

Likely touch points:
- result CTA cluster
- `/share` flow and related copy
- analytics emit sites for share actions

### Slice 4 — Add founder QA and readout
Scope:
- Document the intended post-result decision tree.
- Add a concise QA checklist for mobile and desktop.
- Define the 2–3 key success signals John should review after release.

Likely touch points:
- `docs/analytics/EVENTS.md`
- Obsidian planning or beta notes if the decision tree is easier to keep there

## Product rules for this sprint

- First value comes before any ask.
- The result should still feel like the hero.
- Continuation should sound like help, not obligation.
- Prefer one strong next step over many competing buttons.
- Avoid language that sounds like signup for signup’s sake.
- Do not introduce sensitive-data sharing patterns.

## Verification

### Product behavior QA
- [ ] User reaches result without login.
- [ ] Result screen clearly shows freedom date and top next move first.
- [ ] One primary continuation action is visually obvious.
- [ ] Secondary actions do not compete with the main continuation path.
- [ ] If the user chooses the continuation action, the next screen preserves context.
- [ ] If the user does nothing, the page still feels complete and useful.
- [ ] Mobile layout stays calm and the CTA cluster is not crowded.

### Analytics QA
- [ ] The primary continuation CTA fires exactly once.
- [ ] Share open / share complete still work if present.
- [ ] Signup/login handoff events remain consistent with the typed event contract.
- [ ] No event includes raw financial values or other sensitive details.
- [ ] John can distinguish result viewers from continuation-takers in PostHog.

## Suggested success readout after deploy

Within the first beta cohort after release, John should be able to answer:
- Of users who saw the result, how many took the primary continuation action?
- Which path performed better: save/continue, share, or leave?
- Are users hesitating because the CTA is unclear, too committal, or too easy to ignore?
- Does the result-to-dashboard or result-to-signup path feel connected enough to preserve the aha moment?

## Related notes

- [[UntilFire/Planning/Roadmap|Roadmap]]
- [[UntilFire/Planning/Beta Launch Checklist|Beta Launch Checklist]]
- [[UntilFire/Product/Gentle Onboarding Principles|Gentle Onboarding Principles]]
- [[UntilFire/Product/Feedback Prompt Spec|Feedback Prompt Spec]]
- [[UntilFire/Planning/Sprints/sprint-17-result-screen-product-moment|Sprint 17 — Result Screen Product Moment]]
- [[UntilFire/Planning/Sprints/sprint-22-beta-trust-and-learning-signals|Sprint 22 — Beta Trust and Learning Signals]]
- [[UntilFire/Planning/Sprints/sprint-21-pro-around-continuity-and-guidance|Sprint 21 — Pro Around Continuity and Guidance]]

## Implementation intent

This sprint makes the next step after the result feel calm and worth taking:

**freedom date → clear next step → saved continuity → easier return**
