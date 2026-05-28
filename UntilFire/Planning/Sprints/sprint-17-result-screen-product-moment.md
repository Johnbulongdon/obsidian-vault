---
project: UntilFire
created_at: 2026-05-28
source: chat-plan
source_session: 20260528_022254_50666c
phase_alias: Phase 2
status: Planned
module: Landing & Wizard → Result Screen
---

# Sprint 17 — Result Screen Product Moment

**Status:** 🔲 Planned  
**Module:** Landing & Wizard → Result Screen  
**Phase mapping:** Phase 2 — Upgrade the result screen into the real product moment  
**Goal:** Turn the reveal from “interesting result” into “useful guidance.”

## Problem

The freedom-date reveal is the hook, but it may still stop too early. A user can get a result without getting enough help to answer:

- where do I stand?
- what should I do next?
- why that move?

If the result feels like just a calculator output, the new UntilFire positioning is not yet real.

## User story

As someone who has just seen my freedom date, I want the result screen to tell me what to do next and why it matters — so the product feels like a guide, not only a calculator.

## Done when

- [ ] Freedom date / timeline remains the hero of the page.
- [ ] A **Top next move** card appears directly below the result.
- [ ] The top move is concrete and stage-appropriate, for example:
  - invest more each month
  - reduce spending by a specific amount
  - build an emergency fund first
  - capture employer match first
- [ ] A short **Why this matters** explanation appears under or beside the top move.
- [ ] The result includes a lightweight compare view for **what would change my date fastest?**
- [ ] Compare view includes simple options such as:
  - save more
  - invest more
  - lower expenses
  - increase income
- [ ] The compare view is simple and confidence-building, not a giant simulator.
- [ ] The result provides a low-pressure continuation path only after value, such as:
  - save result
  - create account
  - track progress
  - get monthly plan
- [ ] The result clearly answers:
  - where do I stand?
  - what should I do next?
  - why that move?
- [ ] The screen feels more like a guide than a calculator on mobile and desktop.

## Acceptance criteria

- The main result remains emotionally clear and not visually buried.
- The user can understand at least one recommended next step without reading a long explanation.
- The page links actions to time impact where possible.
- The continuation path is present but does not pressure the user before value.
- The result is calm, believable, and beginner-friendly.

## Out of scope

- Building the full monthly adviser system
- Deep scenario modeling with many controls
- Aggressive login, paywall, or bank prompts
- Reworking the entire dashboard in this sprint

## Related notes

- [[UntilFire/Product/PRD|PRD]]
- [[UntilFire/Planning/Roadmap|Roadmap]]
- [[UntilFire/Product/Survey - Friends Beta - 2026-05-20|Friends Beta Survey — 2026-05-20]]
- [[UntilFire/Planning/Sprints/sprint-05-reveal-screen-cleanup|Sprint 05 — Reveal Screen Cleanup]]

## Implementation intent

This sprint makes the positioning real at the exact moment of first value:

**freedom date → next move → why it matters → continue if you want**
