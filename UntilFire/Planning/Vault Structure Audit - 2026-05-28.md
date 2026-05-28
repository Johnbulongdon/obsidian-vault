---
project: UntilFire
status: active
created_at: 2026-05-28
updated_at: 2026-05-28
author: Hermes Agent
---

# UntilFire Vault Structure Audit — 2026-05-28

## Goal

Check whether the UntilFire Obsidian vault has overlapping folders or notes, and recommend a cleaner “one owner per topic” structure.

## High-level finding

Yes — there is overlap.

The main problem is not that the folder tree is completely wrong. It is that several notes are trying to do the same job at different levels of detail, and a few older migrated docs still describe an older version of the product.

The biggest overlaps are:

1. **top-level product definition**
2. **launch / roadmap / checklist ownership**
3. **agent-context ownership**
4. **stale operational notes that overlap with newer logs**

The current folders are still usable, but a few notes need clearer ownership so future updates do not drift.

---

## Folder-by-folder audit

## 1) Root-level notes

Current root notes:
- `00 - Start Here.md`
- `UntilFire Knowledge Base.md`
- `Repo and Vault Boundary.md`
- `Repo Cleanup Plan.md`

### What overlaps

`00 - Start Here.md` currently behaves like a product overview, README mirror, current-state note, and partial positioning doc all at once.

That overlaps with:
- `Strategy/Product Positioning.md`
- `Product/PRD.md`
- `Planning/Roadmap.md`

### Recommendation

Keep root-level notes only for navigation and boundaries:

- `UntilFire Knowledge Base.md` = index
- `Repo and Vault Boundary.md` = ownership rule
- `00 - Start Here.md` = short project overview / current snapshot only

`00 - Start Here.md` should stop being a second PRD or second positioning doc.

### Canonical owner recommendation

- **Project overview / snapshot:** `00 - Start Here.md`
- **Positioning / message:** `Strategy/Product Positioning.md`
- **Requirements / product spec:** `Product/PRD.md`
- **Execution priorities:** `Planning/Roadmap.md`

---

## 2) Strategy vs Product overlap

### What overlaps

These notes all touch product definition:
- `Strategy/Product Positioning.md`
- `Product/PRD.md`
- `00 - Start Here.md`
- parts of `Strategy/Decision Log.md`

### What is happening

- `Product Positioning.md` is now the best home for the message and category.
- `PRD.md` still contains older framing where city/cost-of-living accuracy is closer to the core value story.
- `00 - Start Here.md` still says “The personal finance app built for FIRE,” which is narrower than the newer positioning.

### Recommendation

Separate them by job:

- `Strategy/Product Positioning.md` → why the product matters, category, emotional promise, messaging guardrails
- `Product/PRD.md` → product requirements and feature behavior only
- `Strategy/Decision Log.md` → durable “why we chose this” decisions
- `00 - Start Here.md` → short orientation for someone new

### Canonical owner recommendation

- **Positioning:** `Strategy/Product Positioning.md`
- **Spec:** `Product/PRD.md`
- **Decision trail:** `Strategy/Decision Log.md`

---

## 3) Planning overlap

Current planning notes include:
- `Planning/Roadmap.md`
- `Planning/Beta Launch Checklist.md`
- `Planning/Todos.md`
- many sprint notes under `Planning/Sprints/`

### What overlaps

`Roadmap.md` and `Beta Launch Checklist.md` both talk about launch readiness and gates.

`Planning/Todos.md` is not really an active todo list anymore. It is a historical resolved-issues note, which overlaps more with:
- `Engineering/Changelog.md`
- `Engineering/Development Log.md`

### Recommendation

- `Roadmap.md` should own **current priorities, phases, and decision sequencing**.
- `Beta Launch Checklist.md` should own only the **go / no-go launch gate** and beta-readiness checklist.
- `Planning/Todos.md` should either be:
  - archived, or
  - renamed/reframed as a historical fixes log if you still want it.

Sprint docs are fine in `Planning/Sprints/`, but they should be treated as implementation slices, not current truth for priorities.

### Canonical owner recommendation

- **What matters now:** `Planning/Roadmap.md`
- **Beta gate:** `Planning/Beta Launch Checklist.md`
- **Historical fix notes:** move out of “Todos” framing

---

## 4) Agent Context overlap

Current notes:
- `Agent Context/Operating Log.md`
- `Agent Context/Agent Rules.md`
- `Agent Context/AI Context.md`
- `Agent Context/Claude Context.md`
- `Agent Context/Instructions Bundle - Agents.md`

### What overlaps

This is the most obvious overlap area.

`Operating Log.md`, `AI Context.md`, and `Claude Context.md` all try to explain what UntilFire is and how agents should work on it.

`AI Context.md` and `Claude Context.md` also look stale relative to the newer product direction and product state.

`Instructions Bundle - Agents.md` is very lightweight and does not seem to add much unique current value.

### Recommendation

Use a tighter split:

- `Operating Log.md` = durable current operating truth for future agents
- `Agent Rules.md` = repo workflow and baseline rules
- `AI Context.md` / `Claude Context.md` = either archive them, or replace them with one single lightweight current execution context note
- `Instructions Bundle - Agents.md` = archive unless it still drives a real workflow elsewhere

### Canonical owner recommendation

- **How John wants the project run:** `Agent Context/Operating Log.md`
- **Implementation safety / repo rules:** `Agent Context/Agent Rules.md`
- **Legacy migrated agent bundles:** candidate archive

---

## 5) Engineering overlap

Current notes:
- `Engineering/Development Log.md`
- `Engineering/Changelog.md`
- `Engineering/Auth Setup.md`

### What overlaps

`Development Log.md` and `Changelog.md` are adjacent but still understandable:

- `Development Log.md` = narrative recent paper trail + next actions
- `Changelog.md` = release-style technical change log

This overlap is acceptable if both stay disciplined.

### Recommendation

Keep both, but do not let them absorb planning or product-direction content that belongs elsewhere.

---

## 6) Product vs Strategy evidence notes

Current notes include:
- `Product/Survey - Friends Beta - 2026-05-20.md`
- `Strategy/Market Research.md`
- `Product/Personas.md`

### What overlaps

These do overlap slightly, but this is mostly healthy overlap:

- survey note = source evidence
- market research = synthesis and external context
- personas = translated user models

### Recommendation

Keep all three, but maintain the hierarchy:

- **raw / direct evidence:** survey note
- **market synthesis:** market research
- **user models:** personas

This area does **not** need major structural cleanup right now.

---

## Main structural problems to fix first

### Priority 1 — clarify the single source of truth for messaging

Right now the positioning is split across:
- `00 - Start Here.md`
- `Product/PRD.md`
- `Strategy/Product Positioning.md`

This is the highest-value cleanup because it affects every future agent and every product/marketing decision.

### Priority 2 — clarify the single source of truth for launch priorities

Right now launch logic is spread across:
- `Planning/Roadmap.md`
- `Planning/Beta Launch Checklist.md`
- some older sprint notes

This is manageable, but easy to drift.

### Priority 3 — clean up agent-context duplication

Future agents do not need 4–5 overlapping context notes. They need:
- one current operating context
- one rules/baseline note
- optionally one short execution quickstart

### Priority 4 — retire stale note names

`Planning/Todos.md` is the clearest example. It no longer behaves like a todo list.

---

## Suggested target structure

### Root
- `UntilFire Knowledge Base.md` — index
- `00 - Start Here.md` — short overview/current snapshot
- `Repo and Vault Boundary.md` — repo vs vault rule

### Strategy
- `Product Positioning.md` — canonical messaging and category
- `Market Research.md` — external and synthesized market context
- `Decision Log.md` — durable decisions

### Product
- `PRD.md` — requirements only
- `User Journey.md` — flow, emotional journey, dropoff
- `Personas.md` — user models
- evidence / onboarding / pricing notes as they are now

### Planning
- `Roadmap.md` — current priorities and sequence
- `Beta Launch Checklist.md` — explicit gate only
- `Sprints/` — implementation slices
- archive or rename `Todos.md`

### Agent Context
- `Operating Log.md` — current durable guidance
- `Agent Rules.md` — repo workflow rules
- archive or consolidate the rest

---

## Recommended next cleanup actions

1. Update `00 - Start Here.md` so it becomes a short overview, not a second positioning/PRD hybrid.
2. Refresh `Product/PRD.md` so it matches the newer broader financial freedom positioning.
3. Decide whether to archive `Agent Context/AI Context.md`, `Claude Context.md`, and `Instructions Bundle - Agents.md`.
4. Rename or archive `Planning/Todos.md`.
5. Keep `Roadmap.md` as the single owner of current execution priorities.

---

## Bottom line

The vault structure is mostly fine.

The real issue is **note ownership drift**, not folder chaos.

If you want the smallest useful cleanup:
- keep the current folders
- make `Product Positioning`, `Roadmap`, `Operating Log`, and `PRD` each own one job
- demote or archive older overlapping context notes
- shorten `00 - Start Here` into a true overview
