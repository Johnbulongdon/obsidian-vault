---
project: UntilFire
status: active
created_at: 2026-05-20
owner: John
---

# Feedback Prompt Spec

This note defines how feedback collection should work during friends-and-family beta.

## Intent

Feedback exists to help John learn whether UntilFire is what early users want and what direction to build next.

Feedback should not interrupt the first value moment or make users feel like they accidentally submitted something.

## Current decision

Feedback should be hidden unless the user chooses to open it.

## Trigger rules

Feedback must only be available after the user reaches their freedom-date result.

Do not show feedback before the result.
Do not auto-open feedback.
Do not auto-submit feedback.
Do not show anything that looks like submitted feedback without explicit user action.

## Interaction model

Preferred beta behavior:

1. User completes the calculator and sees their result.
2. A small optional link or button is available after the result, such as “Help us improve this for you.”
3. The feedback form opens only after the user clicks that control.
4. The user may submit or dismiss without consequence.
5. If dismissed, do not keep nagging them in the same session.

## Copy

Preferred prompt language:

> Help us improve this for you

Tone:

- Calm.
- Optional.
- Founder-led.
- Low pressure.
- No guilt.
- No urgency.

## Avoid

- Star ratings during early beta.
- Popups at the start.
- “Rate your experience” language.
- Anything that implies a feedback submission happened without input.
- Full-screen modals.
- Feedback prompts before users understand the product.

## Suggested questions

Use one or two lightweight questions, not a long survey.

Good options:

- “Was this useful?”
- “What did you want to do next after seeing your result?”
- “What felt confusing or missing?”
- “What would make this worth coming back to?”

Avoid asking for sensitive financial details in feedback.

## Acceptance criteria for implementation

- Feedback UI is not visible before the result.
- Feedback UI does not open automatically.
- Feedback cannot submit unless the user intentionally clicks submit.
- No stars are shown during early beta.
- The entry point says “Help us improve this for you.”
- Dismissal is respected for the session.
- Mobile layout does not block the result or primary next action.
- Analytics, if added, should track feedback-opened and feedback-submitted without capturing sensitive financial values.

## Related notes

- [[UntilFire/Product/Gentle Onboarding Principles]]
- [[UntilFire/Product/Beta Feedback]]
- [[UntilFire/Planning/Beta Launch Checklist]]
