---
project: UntilFire
created_at: 2026-05-28
source: chat-plan
source_session: 20260528_022254_50666c
phase_alias: Phase 4
status: Planned
module: Dashboard → Progress-Oriented Hierarchy
---

# Sprint 19 — Dashboard Around Progress, Not Noise

**Status:** 🔲 Planned  
**Module:** Dashboard → Progress-Oriented Hierarchy  
**Phase mapping:** Phase 4 — Reshape the dashboard around progress, not noise  
**Goal:** Make the logged-in product support the guidance loop.

## Problem

The dashboard already has many surfaces, but that breadth can dilute clarity. If the dashboard leads with equal-weight cards, raw data, or advanced views before clear guidance, the product can feel busy instead of helpful.

The dashboard should reinforce:

1. where I stand
2. what my plan is
3. whether I’m following it
4. whether I’m getting closer

## User story

As a logged-in user, I want the dashboard to start with my freedom path and current plan — so I immediately know what matters and do not feel buried in noise.

## Done when

- [ ] The dashboard hero leads with:
  - freedom date
  - current status
  - top move
- [ ] The first supporting row shows:
  - this month’s target
  - plan vs actual
  - consistency / streak
  - freedom progress
- [ ] Secondary surfaces are clearly lower priority, including:
  - portfolio overview
  - cash / debt / investments
  - reports
  - projections
  - connected accounts
- [ ] The dashboard de-emphasizes:
  - advanced modeling first
  - too many equal-weight cards
  - raw financial data without interpretation
- [ ] Guidance and progress remain visually primary on both mobile and desktop.
- [ ] A first-time logged-in user can tell what to focus on without exploring multiple tabs.

## Acceptance criteria

- The dashboard starts with guidance and progress.
- Raw tracking supports the plan rather than competing with it.
- A first-time user is not overwhelmed.
- The information hierarchy is obvious within a few seconds.
- The logged-in experience feels like continuity from the result screen, not a separate product.

## Out of scope

- Rebuilding every secondary dashboard tab
- Deep portfolio analytics redesign
- Expanding advanced modeling features
- Adding more dashboard widgets just because space exists

## Related notes

- [[UntilFire/Product/PRD|PRD]]
- [[UntilFire/Planning/Roadmap|Roadmap]]
- [[UntilFire/Strategy/Product Positioning|Product Positioning]]
- [[UntilFire/Planning/Sprints/sprint-17-result-screen-product-moment|Sprint 17 — Result Screen Product Moment]]
- [[UntilFire/Planning/Sprints/sprint-18-monthly-discipline-loop|Sprint 18 — Monthly Discipline Loop]]

## Implementation intent

This sprint turns the dashboard into a progress surface instead of a feature catalog:

**freedom date → current plan → current follow-through → supporting detail**
