---
title: "Pearson's r: The Right Way to Read a Correlation"
description: "How to read Pearson's correlation coefficient responsibly. What r actually measures, Cohen's benchmarks, and four things r does not tell you (including causation)."
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
image: /blog/images/cover-pearson-r.jpg
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

A realistic workflow: many correlations in applied research are not
between two raw variables but between two *composite scale scores*
(e.g. the mean of six items measuring a construct). This tutorial
covers the whole path — data import → build two composites via
*Transform → Compute Variable* → run *Correlate → Bivariate* → read
the result and the heatmap.

**Step 1 — Click *Import*.**
Launch AnalyVa on an empty canvas. Click the **Import** button in the
top toolbar.

![The Import button in the top toolbar](/blog/images/analyva-pearson-01-import-button.png)

**Step 2 — The import dialog opens.**
An overlay appears asking for a file (`.xlsx`, `.csv`, or `.tsv`).

![The Import Tabular Data dialog waiting for a file](/blog/images/analyva-pearson-02-import-dialog.png)

**Step 3 — Load and preview.**
Drop your file. AnalyVa parses it and reports the shape (here: 361
rows × 53 columns, 49 numeric, 0 missing). Click **Import**.

![The Import dialog showing a preview of 361 rows × 53 columns](/blog/images/analyva-pearson-03-import-preview.png)

**Step 4 — Open *Transform → Compute Variable*.**
Every variable now appears in the sidebar. Before correlating, build
the two composite scores. Open the **Transform** menu → **Compute
Variable…**.

![The Transform menu with Compute Variable highlighted](/blog/images/analyva-pearson-04-transform-menu.png)

**Step 5 — Name the first composite.**
The **Compute Variable** dialog opens. In *Target Variable*, type a
short, meaningful name — here `Variable1` — this becomes a new column
in your dataset.

![Compute Variable dialog with cursor on the Target Variable field](/blog/images/analyva-pearson-05-compute-target.png)

**Step 6 — Move to the Expression field.**
Click into the *Expression* field. Below it, AnalyVa shows every
available variable as a clickable chip and the full list of supported
functions and operators.

![Compute Variable dialog with the Expression field highlighted](/blog/images/analyva-pearson-06-compute-expression-field.png)

**Step 7 — Enter the composite formula and click *OK*.**
Type or click-to-insert the arithmetic that produces the composite —
here the mean of six items:
`(GP_1+GP_2+GP_3+GP_4+GP_5+GP_6)/6`. Click **OK**. The header confirms
*"Computed 'Variable1' for 361 cases"*.

![Compute Variable dialog with the mean formula filled in](/blog/images/analyva-pearson-07-compute-v1-done.png)

**Step 8 — Repeat for the second composite.**
Open **Transform → Compute Variable…** again to build the second
composite. Same dialog, same flow.

![The Transform menu opened again for the second composite](/blog/images/analyva-pearson-08-transform-menu-again.png)

**Step 9 — Name Variable2.**
In the new dialog, type `Variable2` in *Target Variable*.

![Compute Variable dialog for the second composite](/blog/images/analyva-pearson-09-v2-target.png)

**Step 10 — Build the expression by clicking chips.**
Instead of typing, click the variable chips (`PA_1`, `PA_2`, …) below
the expression box — AnalyVa inserts them at the cursor. Add the `+`
between each and wrap in parentheses.

![Clicking a variable chip to insert PA_1 into the expression](/blog/images/analyva-pearson-10-click-pa1.png)

**Step 11 — Confirm the second composite.**
The full formula: `(PA_1+PA_2+PA_3+PA_4+PA_5+PA_6)/6`. Click **OK**.
The header confirms *"Computed 'Variable2' for 361 cases"*.

![Compute Variable dialog with the second composite formula ready](/blog/images/analyva-pearson-11-compute-v2-done.png)

**Step 12 — Open *Analyze → Correlate → Bivariate*.**
With both composites in the dataset, open the **Analyze** menu →
**Correlate** → **Bivariate…**.

![The Analyze menu with Correlate → Bivariate highlighted](/blog/images/analyva-pearson-12-correlate-menu.png)

**Step 13 — Select the two composites and choose Pearson.**
The **Bivariate Correlations** dialog opens with every numeric
variable listed. Ctrl/Cmd-click **Variable1** and **Variable2** to
select just the two composites. Leave *Method* on **Pearson**. Click
**OK**.

![Bivariate Correlations dialog with Variable1 and Variable2 selected](/blog/images/analyva-pearson-13-bivariate-dialog.png)

**Step 14 — Read the results.**
The right pane switches to **Results** and shows a **Bivariate
Correlations (Pearson)** table:

- **Variable1 ↔ Variable2 = -0.332 \*\*\***

Below the table, a **Correlation Heatmap** visualises the magnitude
and direction (red = negative, blue = positive). Significance stars
follow the convention `* p < .05, ** p < .01, *** p < .001`.

In plain reporting: the two composites correlate **r = -0.33, p <
.001** — a small-to-moderate negative association. To also inspect
whether the relationship is linear (Cohen's caveat #2 above), open the
scatterplot from the same panel before writing up.

![The results panel showing r = -0.332 *** and the correlation heatmap](/blog/images/analyva-pearson-14-results.png)

## Further reading

- Rodgers, J. L., & Nicewander, W. A. (1988). Thirteen ways to look at
  the correlation coefficient. *The American Statistician*, 42(1),
  59–66.
- Cohen, J. (1988). *Statistical power analysis for the behavioral
  sciences* (2nd ed.). Erlbaum.
