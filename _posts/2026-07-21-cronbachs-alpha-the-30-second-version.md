---
title: "Cronbach's Alpha: The 30-Second Version + Common Mistakes"
description: "Cronbach's alpha explained in 30 seconds. What it measures, the accepted thresholds, and the three common mistakes that keep sneaking through peer review."
subtitle: >-
  If your paper uses a multi-item scale, you have probably reported α.
  And your reviewer has probably asked whether it is above 0.70.
  Here is what α actually measures, what it does not, and the three
  mistakes that keep sneaking through peer review.
category: Reliability
tier: Tier 1 · Concept explainer
read_time: 6
tags: [statistics, reliability, cronbach alpha]
color: blue
size: small
image: /blog/images/cover-alpha.svg
---

If your paper uses a multi-item scale — a five-question survey, a set
of Likert items, anything where multiple observations combine into one
construct — you have probably reported Cronbach's α. And your reviewer
has probably asked whether it is above 0.70.

Here is what α is, what it is not, and the three mistakes that keep
sneaking through peer review.

## What α measures

Formally, α estimates the average correlation between all possible
split-halves of your scale. In practice, it tells you how much the
items in your scale "agree" with each other — how internally consistent
they are.

An α of 0.85 means your scale items are highly correlated with each
other. An α of 0.30 means they are barely related. That is the whole
idea.

Notice what α does **not** measure:

- whether the items measure one thing (dimensionality);
- whether the items measure the *right* thing (validity);
- whether the scale is a good scale overall.

α is a reliability index, not a validity index. Necessary, not
sufficient.

## Thresholds (and why they are contested)

The most-cited benchmarks (Nunnally, 1978):

- **α ≥ 0.90** — excellent, but suspiciously so; often signals
  redundant items;
- **α ≥ 0.80** — good;
- **α ≥ 0.70** — acceptable for research scales;
- **α ≥ 0.60** — acceptable only for exploratory research.

Above **0.95**, the items are often near-duplicates and the scale is
padded. Below **0.60**, items do not hang together — either a poor
scale, or multiple constructs mixed in the same instrument.

## Three mistakes to avoid

**1. Confusing α with unidimensionality.**
α can be perfectly acceptable for a scale that measures two different
things. If items 1-3 correlate strongly with each other AND items 4-6
correlate strongly with each other AND the two groups do not correlate
at all, α can still exceed 0.70. Always run an EFA or CFA alongside α
to confirm the scale is unidimensional.

**2. Inflating α by adding items.**
The Spearman-Brown formula shows that α grows mechanically with the
number of items. You can raise α from 0.65 to 0.80 by adding items
alone, without improving the quality of the scale. Always report α
with `k` (the number of items) visible so readers can judge.

**3. Reporting α when its assumptions do not hold.**
α assumes tau-equivalence — that every item measures the underlying
construct with equal weight. Real scales rarely meet this. Modern
practice recommends reporting composite reliability (**ρ_C**) or
Dijkstra-Henseler's rho (**ρ_A**) alongside α. Both handle unequal
factor loadings and give more honest reliability estimates.

## What to report

For a modern applied paper:

- Cronbach's α, with the number of items, e.g. `α = 0.82, k = 6`.
- Composite reliability **ρ_C**.
- Optionally **ρ_A**, especially in PLS-SEM contexts.
- Optionally the "α if item deleted" for each item, so weak items are
  visible to reviewers.

## Doing this in AnalyVa

*A step-by-step tutorial with screenshots will be added here.*

> **Screenshot placeholder — Step 1: Import your data.**
> Suggested filename: `analyva-alpha-01-import.png`.

> **Screenshot placeholder — Step 2: Select the scale items.**
> Suggested filename: `analyva-alpha-02-select-items.png`.

> **Screenshot placeholder — Step 3: Run reliability analysis.**
> Suggested filename: `analyva-alpha-03-run.png`.

> **Screenshot placeholder — Step 4: Read the α, ρ_A, ρ_C, and
> item-total statistics.**
> Suggested filename: `analyva-alpha-04-results.png`.

## Further reading

- Cortina, J. M. (1993). What is coefficient alpha? An examination of
  theory and applications. *Journal of Applied Psychology*, 78(1),
  98–104.
- Sijtsma, K. (2009). On the use, the misuse, and the very limited
  usefulness of Cronbach's alpha. *Psychometrika*, 74(1), 107–120.
