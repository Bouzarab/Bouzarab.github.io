---
title: "Pearson's r: The Right Way to Read a Correlation"
subtitle: >-
  It is bounded between -1 and +1, everyone reports it, and almost
  nobody interprets it responsibly. Here is what r actually measures
  and the four things it does not.
category: Statistics
tier: Tier 1 · Concept explainer
read_time: 6
tags: [statistics, correlation, pearson]
color: green
size: small
image: /blog/images/cover-pearson-r.svg
---

If two variables move together, we say they are correlated. If they
move in the same direction, we call it positive; opposite direction,
negative. The number that summarises all of this — how strongly, and in
which direction — is Pearson's r.

r is bounded between -1 and +1. But knowing that is not enough to
interpret it responsibly.

## What r actually measures

r is a scaled version of covariance. It measures the **linear**
relationship between two continuous variables. Its full name — the
Pearson product-moment correlation coefficient — is worth remembering
because every word matters.

- **Linear.** r only detects straight-line relationships. A perfectly
  curved relationship (U-shape, quadratic) can produce r ≈ 0.
- **Product-moment.** it is built from the joint deviations of both
  variables from their means.
- **Coefficient.** it is a one-number summary — not a full picture.
  Always plot the data.

## Interpreting r's magnitude

Cohen's benchmarks (1988) are the most widely cited:

- **|r| ≥ 0.10** → small
- **|r| ≥ 0.30** → medium
- **|r| ≥ 0.50** → large

These are field-specific. In physics, r = 0.90 is common. In social
psychology, r = 0.30 might be the strongest effect you will ever see.
Compare to your field's typical effect sizes, not to the benchmarks
alone.

## Four things r does not tell you

**1. Causation.**
Perhaps the most-repeated caveat in statistics. A high r between ice
cream sales and drowning deaths does not mean ice cream causes
drowning — a third variable (summer weather) drives both.

**2. Non-linear relationships.**
A dataset with a perfect U-shape can have r = 0. Always inspect a
scatterplot before trusting r. If the relationship is non-linear,
transform the variable (log, square root, quadratic term) or use a
non-parametric measure like Spearman's ρ.

**3. The magnitude of change.**
r = 0.80 means the variables move together strongly, but it does not
say by *how much* y changes when x changes by one unit. For that,
you need the slope of a regression (β), not r.

**4. Robustness to outliers.**
A single extreme point can pull r from 0.10 to 0.60. Always compute r
with and without any influential outlier, and report both — or use a
robust correlation (Spearman, Kendall's τ) if outliers are theoretically
meaningful and should stay in.

## What to report

- The value of r to two decimal places, e.g. `r = 0.42`.
- The exact p-value, e.g. `p = .003` — but read the
  [P-values post](/blog/2026/07/25/p-values-what-they-actually-mean/)
  first.
- The 95 % confidence interval for r (via bootstrap or Fisher's
  z-transformation).
- The sample size `n`.
- A scatterplot showing the actual data.

## Doing this in AnalyVa

*A step-by-step tutorial with screenshots will be added here.*

> **Screenshot placeholder — Step 1: Import your two continuous
> variables.**
> Suggested filename: `analyva-pearson-01-import.png`.

> **Screenshot placeholder — Step 2: Run the correlation analysis and
> select the variables.**
> Suggested filename: `analyva-pearson-02-configure.png`.

> **Screenshot placeholder — Step 3: Read r, the confidence interval,
> and the scatterplot.**
> Suggested filename: `analyva-pearson-03-results.png`.

## Further reading

- Rodgers, J. L., & Nicewander, W. A. (1988). Thirteen ways to look at
  the correlation coefficient. *The American Statistician*, 42(1),
  59–66.
- Cohen, J. (1988). *Statistical power analysis for the behavioral
  sciences* (2nd ed.). Erlbaum.
