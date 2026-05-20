---
project: UntilFire
status: active
created_at: 2026-05-20
owner: John
---

# Beta Feedback

This note captures feedback, bugs, and product-learning signals from the friends-and-family beta.

## Beta goal

Learn whether UntilFire is what early users want and what direction John should build next.

The beta is currently for family and friends, not random public users.

## Feedback principles

- Capture anything that causes dropoff.
- Treat confusion as a product bug, not a user problem.
- Prioritize user comfort before conversion.
- Keep feedback collection hidden or user-initiated.
- Avoid star ratings during early beta.
- Do not push Pro/paywall during beta unless John explicitly changes this.

## Active issues

### Feedback box appeared without user input

**Status:** needs implementation fix / QA confirmation  
**Severity:** high for beta trust  
**User impact:** The UI appeared to collect or submit stars/questions without the user intentionally giving feedback. This can feel surprising or scary at the start.

**Desired behavior:**

- Feedback must only be available after the user reaches their freedom-date result.
- Feedback must be hidden unless the user clicks to open it.
- No star ratings during early beta.
- Entry copy should be: “Help us improve this for you.”
- Nothing should appear submitted without explicit user action.

**Related spec:** [[UntilFire/Product/Feedback Prompt Spec]]

**QA checklist:**

- [ ] Fresh visitor lands on homepage: no feedback box visible.
- [ ] User starts calculator: no feedback box visible.
- [ ] User fills city/income/savings/portfolio: no feedback box visible.
- [ ] User reaches result: only a small optional feedback entry point may appear.
- [ ] Feedback form opens only after clicking the entry point.
- [ ] No stars appear.
- [ ] Submit is impossible without typed or selected feedback.
- [ ] Dismissal is respected for the session.
- [ ] Mobile result screen remains calm and uncluttered.

## Open beta questions to keep learning

- Do users understand the freedom date result?
- Does one monthly move make the result feel actionable?
- What do users want to do next after the result?
- What feels confusing, too intense, or unnecessary?
- What causes dropoff?
- What would make users come back monthly?

## Related notes

- [[UntilFire/Product/Gentle Onboarding Principles]]
- [[UntilFire/Product/Feedback Prompt Spec]]
- [[UntilFire/Planning/Beta Launch Checklist]]
