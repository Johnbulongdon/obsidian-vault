---
project: UntilFire
status: active
created_at: 2026-05-20
owner: John
---

# Gentle Onboarding Principles

UntilFire is in a friends-and-family beta. The first experience should feel calm, useful, and optional. Anything that causes confusion, pressure, or dropoff is a product risk.

## Core rule

Do not scare users at the start.

Users should reach the first value moment — their freedom date and one useful monthly move — before UntilFire asks for feedback, login, payment, bank connection, or extra commitment.

## What early users should feel

- “This helps me understand what I want next.”
- “I can try this without committing.”
- “I am not being judged for my finances.”
- “I can leave, adjust, or give feedback without pressure.”

## Early beta audience

The first beta is for family and friends, not random users yet.

The beta goal is to learn:

1. Whether this is what users want.
2. What direction UntilFire should build next.
3. What causes dropoff or confusion.

## Avoid during early beta

- Auto-opening feedback prompts.
- Star ratings.
- Popups or modals that feel like interruptions.
- Login prompts before the result.
- Payment or Pro pressure.
- Bank/Plaid prompts as a central launch path.
- Asking for too much financial detail too soon.
- Copy that makes the FIRE timeline feel hopeless or personally judgmental.

## Preferred product posture

- Free first value.
- No login before the aha moment.
- Hidden or user-initiated feedback.
- Soft founder-led language.
- Simple reassurance around privacy and assumptions.
- Treat every early dropoff signal as important.

## Onboarding Guide Gap Audit — 2026-07-16

Prompted by an external research summary (~1,000 onboarding flows / ~3,000 paywalls studied). Question asked: is the orphaned `GoalsScreen` component the only onboarding gap? Answer: no. The biggest gaps are upstream and downstream of the wizard itself, not inside it. Findings are from direct code inspection (`app/HomeClient.tsx`, `app/components/landing/*`) plus a real PostHog funnel query (last 30 days, `funnel_landing_viewed` → `funnel_signup_completed`).

### Real funnel data (last 30 days, n=225 landing views)

| Step | People | Conversion from start | Drop from previous step |
|---|---|---|---|
| Landing viewed | 225 | 100% | — |
| Reaches city step | 24 | 10.7% | 89.3% |
| Reaches income step | 19 | 8.4% | 21% |
| Reaches savings step | 16 | 7.1% | 16% |
| Reaches portfolio step | 16 | 7.1% | 0% |
| Reveal (freedom date shown) | 16 | 7.1% | 0% |
| Signup started | 1 | 0.4% | 93.75% |
| Signup completed | 1 | 0.4% | 0% |

Two cliffs dwarf everything else:

1. **Landing → city (89% drop).** 9 out of 10 visitors never click past the hero into the calculator. This is a hero/landing conversion problem, not a wizard-quality problem — GoalsScreen or wizard polish can only affect the ~11% who get past this point.
2. **Reveal → signup started (93.75% drop).** Once someone sees their actual freedom date, almost nobody continues into an account. This is the single highest-leverage number for the $3k MRR conversion lever. Caveat: the reveal screen also offers a parallel "or get it by email" waitlist capture (`/api/waitlist`) that is **not instrumented** in the funnel contract at all — some of that 93.75% may be converting through the untracked email path instead of the tracked `/login` path, so the true reveal→convert rate is probably better than 6.25%, but likely still poor. Worth adding a `funnel_email_capture_submitted` event before trusting this number further.

Once someone actually starts the wizard, it holds up fine: 24 → 16 through to reveal is a 67% completion rate with no single-step cliff (savings → portfolio → reveal is 0% drop). This part is not the problem.

### Is GoalsScreen the only gap? No — three code-level findings

1. **`GoalsScreen.tsx` is fully orphaned.** Not in the `Screen` type union (`app/HomeClient.tsx:2227`), not imported anywhere live, zero related state. Only referenced from an old audit doc and a paperclip JSON — never wired into `origin/main`. If revived, the research favors multi-select goal pickers over the current single-select radio-card design (Headspace saw +10% trial conversion from multi-select).
2. **A second orphaned screen: the "currency" step is dead code.** `CityScreen`'s `onNext` and `onSkip` both route straight to `"income"` (`HomeClient.tsx:4315`, `:4320`), auto-deriving currency via `stateToCurrency(c.stateKey)`. Nothing anywhere calls `setScreen("currency")`. The `screen === "currency"` branch at `HomeClient.tsx:4350` still renders (a second copy of `IncomeScreen`) but is unreachable. `docs/analytics/EVENTS.md`'s canonical funnel contract still documents `city → currency → income → savings → portfolio` as 5 steps — that doc is stale; the live flow is 4 steps with currency folded into the income screen. Confirmed independently: `step_id=currency` has never once appeared in PostHog's recorded property values for `funnel_calculator_step_viewed`.
3. **Visual/tonal discontinuity: the wizard and reveal screens never got the v7 dark redesign.** `LandingPage.tsx`'s hero is the new dark "born twice" treatment (`#08080e` background, orange/teal accents), but the actual input screens (`.uf-screen` and related classes) and reveal card still use the old light theme (`#FFF7ED`, `#F8FAFC`, white cards). A visitor who clicks past the polished dark hero lands on a lighter, older-feeling calculator — exactly the kind of tonal break the research guide flags (calm, consistent tone through the full flow, not just the marketing surface).

### What the guide says we're doing right already

- No login/payment/survey before the aha moment — matches "let users try the core experience before signup."
- Reveal screen already uses outcome-first framing (freedom date + FIRE number), not a bare calculator output.
- Reveal CTA copy ("Save plan and track monthly" / "Save my plan →") already uses the guide's praised low-friction pattern, plus a genuine no-account fallback (email capture) — a rarer, good pattern.

### Recommended next actions, in order of leverage

1. Instrument the email-capture path (`/api/waitlist` submit) as a funnel event, so the reveal→convert number reflects reality before changing anything else about the paywall or wizard.
2. Investigate the landing/hero itself — 89% of visitors never reach city. This is the biggest number in the whole funnel and sits upstream of everything else in this audit.
3. Delete the dead `"currency"` screen branch and fix `docs/analytics/EVENTS.md` to match the real 4-step flow (or intentionally decide currency deserves its own step again).
4. Decide GoalsScreen's fate: wire it in as a real first step (multi-select, per the guide) or delete it — an unreferenced component with no type-union entry misleads future readers of the codebase.
5. Bring the wizard/reveal screens' visual theme in line with the v7 dark hero so the experience doesn't visually reset partway through.

No code changes made yet — this is an analysis pass only, logged before starting the paywall-side review.

## Related notes

- [[UntilFire/Product/Feedback Prompt Spec]]
- [[UntilFire/Product/Beta Feedback]]
- [[UntilFire/Planning/Beta Launch Checklist]]
- [[UntilFire/Agent Context/Operating Log]]
