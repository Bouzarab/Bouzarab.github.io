---
title: "HTMT Above 0.85: What to Do When Discriminant Validity Fails"
description: "HTMT crossed 0.85 in your PLS-SEM report? A step-by-step decision path: check the bootstrap CI, inspect indicator pairs, and defend or reshape the model."
subtitle: >-
  Your PLS-SEM report is due, HTMT crossed the threshold, and you're
  wondering whether to defend it or reshape the model. Here's a decision
  path that works whether you're in SmartPLS, R, or AnalyVa.
category: PLS-SEM
tier: Tier 1 · Problem query
read_time: 9
doi: 10.5281/zenodo.21536948
tags: [PLS-SEM, HTMT, discriminant validity]
color: red
size: large
image: /blog/images/cover-htmt.svg
---

You ran PLS-SEM, opened the report, and one HTMT value is 0.87. The
manuscript is due Friday. The reviewer you're most worried about wrote
their PhD on discriminant validity. What now?

This post gives you a concrete decision path — the same one used by
methodologists like [Henseler, Ringle, and Sarstedt (2015)][hrs2015] and
extended in later work. It applies whether you're running the analysis
in SmartPLS 4, in R with the `SEMinR` or `cSEM` packages, or in AnalyVa.

## What HTMT actually measures

The **Heterotrait-Monotrait ratio of correlations (HTMT)** compares the
average correlation of indicators *across* two constructs to the average
correlation of indicators *within* each construct. When HTMT approaches
1.0, the two constructs are effectively measuring the same thing.

There isn't one universally accepted cutoff. The three most commonly
cited thresholds are:

- **HTMT < 0.85** — strict. Recommended when your constructs are
  conceptually distinct (e.g., *trust* vs. *satisfaction*).
- **HTMT < 0.90** — liberal. Acceptable when constructs are
  conceptually close (e.g., *cognitive trust* vs. *affective trust*).
- **HTMT confidence interval excludes 1.0** — the inferential test,
  based on bootstrap resampling. Preferred by many editors today.

If your value sits between 0.85 and 0.90, don't panic yet — the
inferential HTMT test is what most journals now expect you to report
anyway.

## The six things to try, in order

### 1. Check the bootstrapped HTMT confidence interval

Run 5,000 bootstrap subsamples with the percentile method and report
the 97.5% upper bound. If the interval excludes 1.0, most reviewers
will accept the constructs as empirically distinct even when the point
estimate is above 0.85. This is the test that survives peer review.

### 2. Look at the offending indicator pair

HTMT is an *average* — it hides which specific pair is causing the
problem. Pull the raw cross-loadings matrix and find the two indicators
with the highest cross-construct correlation. That pair is usually
where the theoretical overlap is real.

### 3. Consider whether the constructs are actually distinct

Sometimes HTMT is telling you the truth: the two constructs *aren't*
distinct in your data. This is the moment to step back from the
statistics and ask a theoretical question. Are *perceived usefulness*
and *perceived value* really separate for your sample, or did your
respondents treat them as the same idea? If the constructs collapse
conceptually, merge them and reestimate.

### 4. Drop the weakest cross-loading indicator

If the pair problem is driven by one indicator with a weak outer
loading (< 0.70) and a strong cross-loading, drop it. Document the
decision in the methods section. Never drop indicators purely to
"fix" HTMT — you need a defensible measurement reason.

### 5. Reconsider the reflective/formative specification

If one of the constructs is actually formative (its indicators *cause*
the latent variable rather than reflect it), HTMT doesn't apply in the
first place. Formative constructs are assessed with VIF and indicator
weights, not with HTMT or AVE. Misspecification is a common hidden
cause of "failing" discriminant validity.

### 6. If all else fails, report and defend

If the theory supports two distinct constructs, the bootstrapped HTMT
interval excludes 1.0, and dropping indicators would harm construct
coverage, report the HTMT value honestly and defend it in the
Discussion. Editors generally accept a defended 0.87 more readily than
a suspiciously clean 0.84 that clearly came from indicator surgery.

## How this looks in SmartPLS 4

SmartPLS 4 reports the HTMT point estimate in the standard PLS
algorithm output, and the bootstrapped confidence intervals under the
"Discriminant Validity" tab after you run the bootstrap procedure. To
identify the offending indicator pair, open the "Cross Loadings"
report.

## Doing this in AnalyVa

AnalyVa reports HTMT alongside its bootstrap confidence interval in
the same table, so you don't have to run two procedures to see both.
The cross-loading heatmap highlights indicator pairs above your
chosen threshold in a single view.

> **Screenshot placeholder** — replace this note with a screenshot of
> the AnalyVa HTMT report + cross-loading heatmap. Filename suggestion:
> `analyva-htmt-with-bootstrap-ci.png`.

## Validation

AnalyVa's HTMT calculations were benchmarked against SmartPLS 4 on the
corporate reputation dataset (n = 344) as part of the second
validation study. Point estimates and bootstrapped confidence intervals
reproduce SmartPLS output to the reported precision. See the study on
Zenodo at [doi.org/10.5281/zenodo.21536948][study].

## Further reading

- Henseler, J., Ringle, C. M., & Sarstedt, M. (2015). A new criterion
  for assessing discriminant validity in variance-based structural
  equation modeling. *Journal of the Academy of Marketing Science*,
  43(1), 115–135. [DOI][hrs2015]
- Franke, G., & Sarstedt, M. (2019). Heuristics versus statistics in
  discriminant validity testing. *Internet Research*, 29(3), 430–447.

[hrs2015]: https://doi.org/10.1007/s11747-014-0403-8
[study]: https://doi.org/10.5281/zenodo.21536948
