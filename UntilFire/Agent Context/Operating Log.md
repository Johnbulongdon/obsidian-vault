---
project: UntilFire
purpose: durable operating trail for future agents
created_at: 2026-05-20
---

# UntilFire Operating Log

This note is the durable trail of how John wants UntilFire work handled. Use it before making product, docs, repo, or monitoring changes.

## Current operating conventions

- Obsidian is the UntilFire information layer.
- The UntilFire GitHub repo should stay focused on code, tests, package/config files, and minimal setup or agent safety pointers.
- Knowledge updates, product context, strategy, roadmap, decisions, user feedback, and agent context should be written to this vault and pushed to `Johnbulongdon/obsidian-vault`.
- Code behavior changes should happen in `Johnbulongdon/UntilFire`, using latest `origin/main` as the baseline.
- When updating either repo, commit and push rather than leaving important changes only on disk.
- Keep secrets out of both repos and vault notes. Redact credential-like values.

## Communication style for John

- Be concise by default.
- Use simple wording and plain human progress updates.
- Report final state as: what changed, whether anything is wrong, and the next useful action.
- Avoid noisy implementation detail unless John asks for it.

## UntilFire product direction

- Position UntilFire around emotional outcomes: work becoming optional, freedom date, and monthly moves.
- Do not lead social/community copy with “calculator” framing, except SEO pages where calculator wording matches search intent.
- Anchor copy: “Find your freedom date”, “work can become optional”, “monthly moves”, “Free, no login.”
- Beta priorities: mobile web UX, clear save confirmations, obvious navigation/copy, simplified dashboard IA.
- Dashboard IA: Home / Money / Freedom, with Profile as account/settings/assumptions area. FIRE/personality test belongs near Profile assumptions.

## Friends-and-family beta rules

- Current beta audience is family and friends, not random users yet.
- The beta goal is to learn whether this is what users want and what John should build next.
- Anything that causes user dropoff is a priority signal.
- Do not scare users at the start: keep the first experience calm, optional, and low-pressure.
- Users should reach their freedom-date result and one useful monthly move before feedback, login, payment, bank connection, or other commitment asks.
- Feedback should be hidden unless the user opens it.
- Feedback must only be available after the freedom-date result.
- Avoid star ratings during early beta.
- Preferred feedback entry copy: “Help us improve this for you.”
- Pro is currently $4.99/month, with the Stripe price ID set in Vercel. Keep actual price IDs out of notes/logs.
- Avoid visible Pro/paywall pressure during beta unless John explicitly changes this.
- See [[UntilFire/Product/Gentle Onboarding Principles]], [[UntilFire/Product/Feedback Prompt Spec]], [[UntilFire/Product/Beta Feedback]], [[UntilFire/Product/Pricing and Pro Packaging]], and [[UntilFire/Planning/Beta Launch Checklist]].

## Monitoring conventions

- Repo update watcher: Hermes cron job `41e1229663b3` alerts when `main` changes for UntilFire or obsidian-vault.
- Production deploy watcher should send concise alerts for successful UntilFire Production deployments.
- Keep alerts short and actionable.

## README boundary

- The UntilFire repo README should stay code/setup oriented.
- The README should include a visible pointer to `Johnbulongdon/obsidian-vault`, especially `UntilFire/UntilFire Knowledge Base.md` and this operating log, so other AI agents know where the durable project knowledge lives.
- Avoid re-growing the README into a product roadmap, changelog, or strategy document; put that content in Obsidian instead.

## Decision trail rules

When a future decision affects product direction, repo/vault boundaries, UX IA, monitoring, or agent behavior:

1. Add or update a note in this vault.
2. Link it from [[UntilFire/UntilFire Knowledge Base]] if it is broadly useful.
3. Commit and push the vault update.
4. Do not bury durable decisions only in chat history or code commits.
