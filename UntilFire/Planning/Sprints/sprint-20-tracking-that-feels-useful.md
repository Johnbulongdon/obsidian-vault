---
project: UntilFire
created_at: 2026-05-28
source: chat-plan
source_session: 20260528_022254_50666c
phase_alias: Phase 5
status: Planned
module: Tracking → Plan vs Actual + Trust
---

# Sprint 20 — Tracking That Feels Useful

**Status:** 🔲 Planned  
**Module:** Tracking → Plan vs Actual + Trust  
**Phase mapping:** Phase 5 — Make tracking useful, not just available  
**Goal:** Better answer “tracking investments” without becoming a spreadsheet clone.

## Problem

UntilFire can expose tracking data, but data alone does not reduce stress. Users need tracking that explains whether they are improving, where the gap is, and whether the numbers are trustworthy enough to act on.

## User story

As a user checking my money progress, I want tracking that tells me what I planned, what actually happened, and what changed — so I can act without feeling buried in spreadsheets.

## Done when

- [ ] Users can see **plan vs actual contributions** clearly.
- [ ] The product shows:
  - what I planned
  - what I actually did
  - the gap
- [ ] The product includes a useful portfolio summary with:
  - investments
  - cash
  - debt
  - net worth
  - major changes
- [ ] The product surfaces simple interpretive nudges, such as:
  - contributions dropped this month
  - idle cash is building up
  - portfolio concentration may be high
- [ ] The product includes trust-building explanations for:
  - what counts where
  - why a number changed
  - what to do if data looks off
- [ ] Tracking helps users tell whether they are improving without forcing them through multiple report views.

## Acceptance criteria

- Users can tell if they are improving.
- Tracking reduces stress instead of adding confusion.
- Data feels trustworthy enough to act on.
- The main tracking surfaces explain changes, not just display values.
- The experience stays aligned with the broader freedom-path product story.

## Out of scope

- Becoming a spreadsheet-style finance tracker
- Deep trading/investment tooling
- Overbuilt analytics dashboards for power users first
- Expanding bank-sync complexity before the explanation layer is useful

## Related notes

- [[UntilFire/Product/PRD|PRD]]
- [[UntilFire/Planning/Roadmap|Roadmap]]
- [[UntilFire/Strategy/Product Positioning|Product Positioning]]
- [[UntilFire/Planning/Sprints/sprint-18-monthly-discipline-loop|Sprint 18 — Monthly Discipline Loop]]
- [[UntilFire/Planning/Sprints/sprint-19-dashboard-progress-not-noise|Sprint 19 — Dashboard Around Progress, Not Noise]]

## Implementation intent

This sprint makes tracking support decisions instead of just reporting state:

**plan → actual → gap → explanation → next action**
