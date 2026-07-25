---
title: "T-Tests: When to Use Which"
description: "One-sample, independent, or paired t-test — which do you need? The decision framework, the assumptions to check first, and the three mistakes to avoid."
subtitle: >-
  The t-test is the workhorse of comparing means — but "the t-test" is
  really three related tests, and picking the wrong one is one of the
  most common mistakes in student and early-career research. Here is
  the decision framework.
category: Statistics
tier: Tier 1 · Problem query
read_time: 8
tags: [statistics, t-test, hypothesis testing]
color: purple
size: wide
image: /blog/images/cover-t-test.svg
---

The t-test is the workhorse of comparing means. But "the t-test" is
really *three* related tests, and picking the wrong one is one of the
most common mistakes in student and early-career research.

Here is the decision framework and the reporting standards.

## The three t-tests

**One-sample t-test.**
Compares one group's mean to a known reference value.
*Example: are the students in this sample scoring above the national
average of 100?*

**Independent-samples t-test.**
Compares the means of two *different* groups.
*Example: do men and women differ in exam scores?*

**Paired-samples t-test.**
Compares two measurements from the *same* subjects (or matched pairs).
*Example: did the students' scores change from pre-test to post-test?*

Using the wrong one inflates or deflates the Type I error rate. An
independent test on paired data throws away statistical power; a paired
test on independent data is simply invalid.

## Decision tree

- Comparing **one group** to a fixed number? → **one-sample.**
- Comparing **two independent groups**? → **independent.**
- Comparing **two measurements from the same subjects** (or matched
  pairs)? → **paired.**
- Comparing **three or more groups**? → not a t-test. Use ANOVA.

## Assumptions

All t-tests assume:

- the dependent variable is continuous (interval or ratio);
- observations are independent within each group;
- the dependent variable is approximately normally distributed within
  each group.

The independent-samples t-test additionally assumes equal variances
between groups (homogeneity). When that is violated, use **Welch's
t-test** — most modern statistical software defaults to Welch's for
exactly this reason. It costs nothing when variances are equal and
works correctly when they are not.

## Effect size — report it, always

A p-value tells you whether a difference exists. Cohen's *d* tells you
how big it is.

- **d = 0.20** → small
- **d = 0.50** → medium
- **d = 0.80** → large

A study with n = 1,000 might return `p < .001` for `d = 0.05` —
statistically significant, practically meaningless. Always report d
alongside its 95% confidence interval.

## Three common mistakes

**1. Running pairwise t-tests on three or more groups.**
Three groups A, B, C tested with three t-tests (A vs B, A vs C, B vs C),
each at α = 0.05, gives a family-wise error rate of roughly 14%. Use
ANOVA followed by a post-hoc test (Tukey's HSD, Bonferroni) instead.

**2. Ignoring Welch's t-test.**
When group variances differ notably (Levene's test p < 0.05), the
classical Student's t-test is biased. Welch's has no such assumption.
Modern journals expect Welch's by default when variances are unequal.

**3. One-tailed tests without prior justification.**
A one-tailed test doubles statistical power on one side, but requires
you to have committed to a direction *before* looking at the data.
Post-hoc one-tailed tests are a form of p-hacking. Report two-tailed by
default unless you have a preregistered directional hypothesis.

## What to report

For an independent-samples t-test, a defensible modern report:

> "The intervention group scored significantly higher than the control
> group, t(48) = 3.21, p = .002, d = 0.91, 95% CI for d [0.34, 1.48]."

Components:

- **t(df) = value** — the statistic and its degrees of freedom.
- **exact p** — not just "< .05".
- **Cohen's d** plus its 95% CI.
- **The mean difference** plus its 95% CI where journal style allows.

## Doing this in AnalyVa

*A step-by-step tutorial with screenshots will be added here.*

> **Screenshot placeholder — Step 1: Import your data (dependent
> variable plus a grouping variable for independent tests, or two
> paired variables for paired tests).**
> Suggested filename: `analyva-ttest-01-import.png`.

> **Screenshot placeholder — Step 2: Choose the test type
> (one-sample / independent / paired).**
> Suggested filename: `analyva-ttest-02-choose-test.png`.

> **Screenshot placeholder — Step 3: Configure the test and enable
> Welch's correction if variances differ.**
> Suggested filename: `analyva-ttest-03-configure.png`.

> **Screenshot placeholder — Step 4: Read the output — t, df, p, mean
> difference with its CI, and Cohen's d with its CI.**
> Suggested filename: `analyva-ttest-04-results.png`.

## Further reading

- Lakens, D. (2013). Calculating and reporting effect sizes to
  facilitate cumulative science: A practical primer for t-tests and
  ANOVAs. *Frontiers in Psychology*, 4, 863.
- Delacre, M., Lakens, D., & Leys, C. (2017). Why psychologists should
  by default use Welch's t-test instead of Student's t-test.
  *International Review of Social Psychology*, 30(1), 92–101.
