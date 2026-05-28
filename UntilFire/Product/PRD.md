---
project: UntilFire
source_path: docs/PRD.md
migrated_from_repo: /home/adminuser/projects/UntilFire
migrated_at: 2026-05-20T09:16:16+00:00
updated_at: 2026-05-28
role: product-requirements
---

# UntilFire — Product Requirements Document (PRD)
Last updated: 2026-05-28

---

## Purpose of this note

This note owns **product requirements and feature behavior**.

It should describe what the product needs to do, how the main flows should behave, and what must be true for a good user experience.

It should not be the main home for product positioning, launch sequencing, or agent operating rules.

For those, use:
- [[UntilFire/Strategy/Product Positioning|Product Positioning]]
- [[UntilFire/Planning/Roadmap|Roadmap]]
- [[UntilFire/Agent Context/Operating Log|Operating Log]]

---

## Product summary

UntilFire is a **financial freedom app** that helps users:

1. see their freedom date quickly
2. understand where they stand
3. get a clear next move that can bring that date closer

The product should feel calm, trustworthy, beginner-friendly, and actionable.

---

## Problem statement

Most users do not need another finance app that only tracks spending or another calculator that only returns a number.

They need help answering:

- where do I stand?
- when could work become optional?
- what should I do next?
- should I focus on spending, income, or investing first?

The current market often fails in two directions:

- **Too complex** — dense simulators and planners require too much setup before value.
- **Too shallow** — dashboards and generic calculators do not tell the user what to do next.

UntilFire should bridge that gap.

---

## Product vision

> Give users a fast freedom-date answer, then help them move that date closer with a simple, practical plan.

The first value moment should be free, fast, and no-login.
The product should then create continuity into the dashboard and adviser layer.

---

## Target user

See [[UntilFire/Product/Personas|Personas]] for full detail.

At a high level, the product is for financially aware but under-guided users who want clarity without complexity.

Important early user clusters:
- investment-confidence seekers
- income climbers
- global / cross-border planners
- early-career stabilizers
- FIRE-curious planners

---

## Core product principles

- Lead with freedom from financial stress and work, not with calculator jargon.
- Deliver value before asking for login, payment, feedback, or bank connection.
- Make the result screen answer both **“where do I stand?”** and **“what should I do next?”**.
- Use city/tax/global logic as trust proof, not the main promise.
- Keep the experience simple on the surface even when the underlying logic is deeper.

---

## Core product flows

### 1. Anonymous calculator journey

This is the main acquisition and first-value flow.

#### Goal
A new visitor should be able to go from curiosity to a useful result in about 60 seconds.

#### Core steps
- Hero / landing
- City or custom expenses
- Income
- Savings
- Reveal / freedom-date result

#### Required output
The result should show:
- freedom date or timeline
- enough context to trust the answer
- at least one practical next move
- a low-pressure path to continue

### 2. Logged-in continuity journey

This is the retention and deepening layer.

#### Goal
Help the user keep track of progress, understand changes, and eventually use a stronger monthly adviser loop.

#### Core areas
- dashboard / home
- money / transactions / reports
- freedom / projections / scenario views
- account and assumptions

### 3. Pro / paid layer

This should deepen guidance, not interrupt first value.

#### Goal
Offer a better ongoing plan after trust has been earned.

#### Desired shape
- clearer monthly moves
- more continuity
- stronger personalized guidance
- better visibility into impact over time

---

## Feature requirements by product area

## A. Public landing and calculator

### Hero / landing
Must:
- make the product understandable quickly
- make the main CTA obvious
- avoid forcing login before value
- feel broader than a niche FIRE hobbyist tool

Should:
- communicate freedom date + path
- feel calm and trustworthy on mobile

### City / custom expenses step
Must:
- support search-as-you-type city selection
- support custom-city fallback
- let users continue without getting blocked by missing city data

Should:
- make assumptions understandable enough to trust

### Income step
Must:
- support direct annual income entry
- show tax-aware context
- work for both US and international assumptions

Should:
- explain take-home impact clearly without overwhelming users

### Savings step
Must:
- accept a simple savings input
- help users estimate if they do not know an exact number

Should:
- create useful motivation without shaming the user

### Reveal / result screen
Must:
- show the freedom date or equivalent timeline clearly
- explain the result enough to feel believable
- show at least one concrete next move
- provide a low-pressure continuation path

Should:
- make the moment feel emotionally meaningful
- encourage adjustment and exploration
- connect actions to time impact where possible

---

## B. Logged-in dashboard

Must:
- preserve continuity from the calculator result
- make it easy to understand where the user stands
- avoid overwhelming first-time users

Should:
- separate present money state from freedom-path state clearly
- support cashflow, tracking, reports, and projections
- show changes over time in a way that feels useful, not noisy

---

## C. Guidance / adviser layer

Must:
- focus on practical next moves
- explain why a recommendation matters
- connect guidance to freedom-date impact when possible

Should:
- help users choose between spending, income, and investing actions
- feel personalized without feeling magical or invasive

Future ideal:
- monthly adviser loop
- clear top move / next move surface
- confidence and tradeoff framing

---

## D. Payments / Pro

Must:
- stay out of the first-value path
- work cleanly once the user chooses to upgrade

Should:
- frame paid value around guidance and continuity, not access friction

---

## E. Bank connection / external data

Must:
- remain secondary until trust is earned
- not be required for the first useful experience

Should:
- only become more prominent if it clearly improves guidance quality

---

## Current priorities

The most important near-term requirements are:

1. smooth mobile no-login flow
2. clear result with one monthly move or equivalent next action
3. low-pressure first session
4. stronger trust in the result
5. verified Stripe / Plaid / categorisation infrastructure before wider launch

Use [[UntilFire/Planning/Roadmap|Roadmap]] for sequencing and launch readiness.

---

## Non-goals right now

- becoming a generic budgeting app
- making bank connection central to first value
- pushing a hard paywall before the guidance loop is strong
- building power-user depth before beginner clarity
- expanding into regulated-advice territory

---

## Success metrics

Product success should be judged by whether users can:

- understand the product quickly
- complete the calculator flow
- trust the result
- see a clear next move
- continue into saving, sharing, logging in, or coming back

See [[UntilFire/Planning/Roadmap|Roadmap]] for current metric targets and launch gates.

---

## Related notes

- [[UntilFire/Strategy/Product Positioning|Product Positioning]]
- [[UntilFire/Product/User Journey|User Journey]]
- [[UntilFire/Product/Personas|Personas]]
- [[UntilFire/Product/Survey - Friends Beta - 2026-05-20|Friends Beta Survey — 2026-05-20]]
- [[UntilFire/Planning/Roadmap|Roadmap]]
- [[UntilFire/Product/Gentle Onboarding Principles|Gentle Onboarding Principles]]
- [[UntilFire/Product/Feedback Prompt Spec|Feedback Prompt Spec]]
