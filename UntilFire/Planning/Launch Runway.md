---
project: UntilFire
status: active
created_at: 2026-09-20
owner: John
---

# Launch Runway — to Product Hunt, 12 January 2027

Product Hunt was launched around June–July 2026. Six months puts the next
eligible window in December–January. **The date is Tuesday 12 January 2027**
— 16 weeks from 20 September 2026.

January over December deliberately: December kills launches (nobody is
reading Product Hunt between the 20th and New Year), and January is the one
month of the year when people actively go looking for a way to sort out
their money. For a product about financial freedom that is the best traffic
of the year, not a consolation.

## What the runway is actually for

The six-month wait is not the constraint. Having something worth launching
is. As of 20 September: 13 accounts, 4 of them in the last fortnight, 1
paying, and **one person used the app in the last seven days**.

Product Hunt gives one day of traffic. A product that does not retain turns
that day into a spike and nothing else. The runway exists to make sure that
by January the answer to "what happens to someone on day 8?" is not
"nothing".

So the goal for these 16 weeks is **proof the product retains**, not more
surface area. Features are not the bottleneck — the app already has a
household mode, a customisable home, bank sync, categories and scenarios,
serving one active user.

## Block 1 — Fix the two cliffs (now → 18 Oct, 4 weeks)

The onboarding gap audit in *Gentle Onboarding Principles* measured the
funnel: 225 landing views, and two drops that dwarf everything else.

| | People | Drop |
|---|---|---|
| Landing viewed | 225 | — |
| Reaches the calculator | 24 | **89%** |
| Reveal — freedom date shown | 16 | 33% over four steps |
| Signup started | 1 | **94%** |

The wizard itself is fine — 24 into it, 16 out the far end, no single step
bleeding. The problem is on both sides of it.

There is also more traffic than the account count suggests: ~7 visitors a
day are already arriving. Acquisition is not the bottleneck. Activation is.

- **Instrument the email capture first.** The reveal offers "or get it by
  email" through `/api/waitlist`, which is not in the funnel contract at
  all, so some of that 94% may be converting down an untracked path. Do not
  redesign anything against a number that is measuring the wrong door.
- **Cliff 1 — nine in ten never start.** They read the hero and leave. This
  is a landing problem, not a wizard problem.
- **Cliff 2 — they see their freedom date and stop.** Sixteen people got the
  answer and one wanted an account. Whatever the reveal is currently
  offering as a next step is not worth the signup.
- **The tonal break may be feeding both.** The hero got the v7 dark redesign
  and the wizard and reveal did not — click the polished dark hero, land on
  the older light calculator.

Two smaller ones, cheap and already known:

- **The reveal has no spending floor.** Savings equal to income yields
  "YOU'RE ALREADY FINANCIALLY FREE" on $4,000. A stranger who hits that on
  their first try does not come back.
- **The email sequence has never run end to end.** Campaign tagging landed
  17 September, after that day's cron, and nobody has been due since.

## Block 2 — Build the reason to come back (19 Oct → 29 Nov, 6 weeks)

The differentiator is "UntilFire does it with you". Today the product hands
over a date and waits. This block is the continuity.

- **One monthly move**, with impact, difficulty and confidence. Impact
  exists (`impactYears`); the other two do not.
- **A monthly progress moment** — email or card: "your freedom date moved
  two months closer, here's why."
- This is also the honest answer to "why is Pro worth $3?" Right now Pro is
  a pile of features. It should be continuity.

## Block 3 — Meet the beta gate (30 Nov → 20 Dec, 3 weeks)

Feature freeze. The gate is the one already written in *Beta Launch
Checklist*:

- 50 real visitors
- 20 completed freedom-date results
- 5 feedback replies
- 10 people who would comment on launch day
- zero critical flow issues

Fix only what the beta finds.

**If the gate is not met by 20 December, the launch moves — not the gate.**
Launching to an unproven funnel is what produces a spike and nothing else,
and it costs another six months to retry.

## Block 4 — Assets and launch (4 Jan → 12 Jan)

- 20–40s demo video: inputs → freedom date → plan
- 3–5 screenshots (they fall out of the same recording)
- tagline, short description, FAQ
- maker's first comment — John's story, not generated

Holidays 21 Dec – 3 Jan are not planned work.

## SEO — what the Search Console data actually said

Search Console now syncs daily into `seo_search_console`. The first full pull
(23 June – 18 September, the life of the property) settled the question that
had been guesswork: **3,261 impressions, 30 clicks.** The site is indexed and
does rank. It ranks for the wrong things.

Two opposite failures, and they point in opposite directions:

**The 229 city pages rank beautifully for terms nobody searches.**
`/fire-number/austin-tx` sits at position **1.7** and earned five impressions
in three months. `nyc` is 2.5, `atlanta` 3.7, the query "singapore fire
number" is **#1** on three impressions. That retires the programmatic city
strategy on evidence rather than opinion: it worked technically and the
demand is not there. Do not build more of them.

**The calculators rank for terms people do search — on page four.**
"coast fire calculator" 41, "apy to apr calculator" 37, "coast fire" 48,
compound interest 77. Impressions at position 41 only happen when real volume
exists, because almost nobody scrolls that far. Zero clicks, for the same
reason.

Across 79 queries: 5 in the top ten, 2 at 11–20, **51 at 21–50**, 21 below
50. That distribution is a site Google has understood and does not yet trust.

### Done — on-page pass (21 September)

Deepened `coast-fire` (506 → 892 words) and `apy` (447 → 679) with worked
examples, reference tables and FAQs written against the queries that actually
reach them. Fixed three titles rendering as `Calculator -Convert` with no
space, and a duplicate `<h1>` on the APY page.

Deliberately **not** done: migrating the `city_slug` underscores to hyphens.
Google prefers hyphens, but the only pages affected are the city pages we
just decided not to invest in, and they currently rank 1–7 for their terms.
Risking that for a marginal signal on pages that earn nothing is a bad trade.

### To do — 2. Lean into qualified and geo terms

Where the site is already competitive, it is competitive on qualified
variants, not generic ones:

| Query | Position |
|---|---|
| coast fire calculator | 41 |
| coast fire calculator singapore | 7.7 |
| singapore fire number | 1.0 |
| sg fire calculator | 10.3 |

Generic term, page four; qualified term, page one. Singapore is also the
single highest-impression page on the site. With 263 cities and an Expat FIRE
feature already built, there is a position here — *the FIRE calculator that
handles your country* — that the US personal-finance incumbents are not
contesting. This is choosing a fight that can be won rather than one that
cannot.

### To do — 3. Links, which are the actual unlock

On-page work moves a page from 40 to roughly 20–25. Top ten for a commercial
term needs authority, and the site has close to none. That means being cited
by FIRE creators, newsletters and communities — founder work, not engineering
work, and the only item on this list that cannot be delegated to a coding
session.

Worth being blunt in the plan: none of this pays out before January. Four
months old, 37 impressions a day. Done well it starts showing around March.
SEO is a parallel long game, not the answer to the launch-traffic question.

## The two numbers to watch

**Landing → calculator started.** It is 11%. Every visitor Product Hunt
sends lands on that same page, so this number multiplies the entire launch.

**Reveal → account.** It is 6% at best and possibly lower. This is the one
that turns a launch-day spike into users.

Weekly active users is the honest backstop: it is 1. If it is still in
single digits in December, nothing in Block 4 will save the launch, and the
date should move.
