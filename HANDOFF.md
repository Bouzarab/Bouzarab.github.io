# AnalyVa Website — Handoff Document

**Purpose:** enable a new AI model (or a new session) to continue exactly
where the previous conversation stopped. Read this file top-to-bottom
before making any changes.

**User:** Abdelouahd Bouzar (Moroccan, PhD in English Language and
Literature, developer of AnalyVa). Prefers concise/direct writing,
step-by-step work, and explicit approval before large batches of
changes. Second author on all validation papers: Khaoula El Idrissi.

---

## 1. Project overview

**AnalyVa** is a desktop statistical analysis app that combines PLS-SEM,
CB-SEM, general statistics, and qualitative text analysis in one app —
positioned as an alternative to SPSS + SmartPLS + NVivo.

The website (this repo) is:
- **Host:** GitHub Pages, custom domain `analyva.com`.
- **Repo:** `Bouzarab/Bouzarab.github.io`.
- **Local path:** `/Users/bouzarabdelouahd/Websites/Bouzarab.github.io`.
- **Framework:** Jekyll (plain, using `github-pages` plugin set).
- **Build:** GitHub Pages on `push`. A GitHub Action at
  `.github/workflows/daily-build.yml` also triggers a daily rebuild
  at 06:00 UTC so future-dated posts publish automatically.

---

## 2. What already exists on the site

Do **not** rebuild any of these. They are live and working:

**Static pages (root):**
- `index.html` — the homepage (long single-file hand-crafted HTML with
  its own inline CSS; do not restructure).
- `validation.html` → `/validation/` — lists all four Zenodo validation
  studies with DOIs.
- `cite.html` → `/cite/` — APA/MLA/Chicago/BibTeX/RIS for the software
  and for each of the four studies. Both authors credited.
- `blog/index.html` → `/blog/` — "The Applied Statistics Guide" — the
  main blog index. Uses a gallery/mosaic card layout defined in
  `assets/css/main.css`.
- `privacy.html`, `terms.html`, `coming-soon.html` — legal + legacy.
- `sitemap.xml` — hand-maintained static XML. Every new blog post URL
  needs to be added here manually.

**Jekyll infrastructure:**
- `_config.yml` — site config. Contains `brevo.form_action` (newsletter
  endpoint) and `permalink: /blog/:title/` (no dates in URLs).
- `_layouts/default.html`, `page.html`, `post.html` — layouts.
- `_includes/head.html`, `nav.html`, `footer.html`, `newsletter.html`.
- `assets/css/main.css` — shared design system + gallery card CSS.
- `Gemfile` — for local `bundle exec jekyll serve` if desired.

**Blog posts (`_posts/`), already published:**
- `2026-07-21-cronbachs-alpha-the-30-second-version.md` — 9-step
  reliability-analysis tutorial with screenshots.
- `2026-07-22-pearsons-r-the-right-way-to-read-a-correlation.md` —
  14-step Compute Variable + correlation tutorial.
- `2026-07-23-t-tests-when-to-use-which.md` — 8-step t-test tutorial
  (reuses P-value screenshots).
- `2026-07-24-htmt-above-0-85-what-to-do.md` — 17-step full PLS-SEM
  tutorial ending at HTMT.
- `2026-07-25-p-values-what-they-actually-mean.md` — 8-step t-test
  tutorial showing where p appears.

**Blog posts scheduled to auto-publish (already written, future-dated):**
- `2026-07-27-analyva-command-palette-keyboard-shortcuts.md`
- `2026-07-29-recoding-and-variable-types-in-analyva.md`
- `2026-08-02-qualitative-coding-in-analyva.md`

**Lead magnet:**
- `assets/downloads/analyva-pls-sem-reporting-checklist.pdf` — 2-page
  PDF built by `outputs/build_checklist.py` (Python reportlab script).
  Delivered via Brevo automation after DOI confirmation.

**Newsletter pipeline (fully working):**
- Provider: **Brevo** (formerly Sendinblue). Kit was tried first and
  blocked; Brevo works.
- Sender: `support@analyva.com` — forwarded to Gmail via **ImprovMX**
  (no dedicated mailbox; forwarding only).
- Sending domain: `analyva.com` — verified in Brevo (DKIM/SPF DNS
  records added at registrar).
- DOI email template #7 (`Default Template Double opt-in confirmation`)
  has been overwritten with a branded HTML email using the merge tag
  `{{ doubleoptin }}` for the confirm-button link. Post-confirm redirect
  goes directly to the PDF URL (no separate automation email).
- Unsubscribe template #6 also has branded HTML.
- Form embed action URL is stored in `_config.yml` → `brevo.form_action`.
  Do **not** rotate it unless a new form replaces the old one.
- The site's `_includes/newsletter.html` uses `fetch()` with
  `mode: 'no-cors'` + a native-POST fallback so ad-blockers can't kill
  signups.

**SEO:**
- Google Search Console set up + sitemap submitted (Discovered: 11).
- Bing Webmaster Tools setup was suggested but not confirmed.
- `_layouts/post.html` includes `BlogPosting` JSON-LD on every post.
- Every post has a `description:` front-matter field for meta.
- Every post has an auto-generated "Related reading" block at the
  bottom (tag-based match, falls back to 3 most recent).
- URLs are date-free: `/blog/post-slug/`.

**Cover art system:**
The homepage's 5 original posts (Alpha, Pearson, T-test, HTMT, P-value)
use professionally-designed editorial-collage JPGs at:
- `/blog/images/cover-alpha.jpg`
- `/blog/images/cover-p-value.jpg`
- `/blog/images/cover-pearson-r.jpg`
- `/blog/images/cover-t-test.jpg`
- `/blog/images/cover-htmt.jpg` (also .webp variant exists)

The **3 new posts (batch 1) use geometric SVG covers**, per user
request. Later they'll be swapped for illustrated JPGs the user
provides. Current placeholders:
- `/blog/images/cover-shortcuts.svg` — teal keys grid
- `/blog/images/cover-recoding.svg` — amber 1→5 reversal
- `/blog/images/cover-coding.svg` — purple highlighted lines

---

## 3. Where the conversation stopped

**Batch 1 of 4 blog posts was completed and pushed** (3 posts for
Jul 27, Jul 29, Aug 2).

**Batch 2 of 4 is now written and ready for review, but NOT yet
pushed** — 3 posts for Aug 4, Aug 6, Aug 8:
- `_posts/2026-08-04-pls-sem-with-indicator-cleaning.md`
- `_posts/2026-08-06-recode-variables-for-multi-group-analysis.md`
- `_posts/2026-08-08-moderation-analysis-in-pls-sem.md`

Covers created: `cover-pls-cleaning.svg`, `cover-mga.svg`,
`cover-moderation.svg` (same geometric cream/black/red style as batch 1).

All 12/13/17 screenshots per post are referenced and verified to exist.
`sitemap.xml` was also fixed — batch 1's three posts were missing from
it (a gap from the previous session), and all six batch 1 + batch 2
URLs have now been added.

**Still needed:** user review, then `git add . && git commit && git push`
per section 9 below.

---

## 4. The 13-post schedule

| # | Publish date (2026) | Screenshot folder (`Screenshots2/…`) | Suggested topic |
|---|---|---|---|
| 1 | Jul 27 ✅ | `ShortCuts` | AnalyVa command palette (DONE) |
| 2 | Jul 29 ✅ | `Reverse Coding; Recoding; Changing variable type` | Recoding + variable types (DONE) |
| 3 | Aug 2 ✅ | `Coding and analysis` | Qualitative coding tour (DONE) |
| 4 | Aug 4 ✅ | `PLS-SEM; Delete low loading indicators` | Running PLS-SEM + dropping weak indicators (DONE, unpushed) |
| 5 | Aug 6 ✅ | `Recode variables; MGA` | Recoding into groups + preparing MGA (DONE, unpushed) |
| 6 | Aug 8 ✅ | `Moderation; Significance appearance; ` | Moderation analysis + significance display (DONE, unpushed) |
| 7 | Aug 10 | (unassigned — see remaining folders) | — |
| 8 | Aug 12 | (unassigned) | — |
| 9 | Aug 18 | (unassigned) | — |
| 10 | Aug 24 | (unassigned) | — |
| 11 | Aug 28 | (unassigned) | — |
| 12 | Aug 29 | (unassigned) | — |
| 13 | Aug 30 | (unassigned) | — |

**Remaining unassigned folders** (assign these to posts 7–13, in any
order that makes pedagogical sense — mine roughly beginner→advanced):

- `Beysian` (7 files) — Bayesian estimation
- `CB-SEM` (14 files) — covariance-based SEM
- `Computational Analysis types` (34 files) — NLP / sentiment /
  topic modelling
- `Gaussian Copula; Path coefficients are movable; Indicators are hidable`
  (14 files) — endogeneity correction + UI tweaks
- `High Order CFA` (16 files) — second-order factor models
- `MGA` (13 files) — full multi-group analysis with results
- `Risidual Covariance; CB; Color Code; CB-SEM result components`
  (27 files) — CB-SEM results interpretation

The user said batches of **3+3+3+4** — so batches 3 and 4 will be
3 posts (Aug 10, 12, 18) then 4 posts (Aug 24, 28, 29, 30).

---

## 5. Conventions to follow when writing posts

**Filename:** `_posts/YYYY-MM-DD-slug-in-kebab-case.md`.

**Front matter template:**

```yaml
---
title: "Human-Readable Title with Colons if Needed"
description: "140-160 char SEO description with the keyword up front."
subtitle: >-
  Short reader-facing intro that appears under the H1. 1-2 sentences.
category: PLS-SEM              # or Statistics, Reliability, etc.
tier: Tier 3 · How-to          # Tier 1 = concept, Tier 3 = how-to
read_time: 8                   # minutes, rough estimate
tags: [analyva, pls-sem, htmt] # 2-4 tags
color: red                     # red|teal|purple|amber|green|blue|pink
size: large                    # small|wide|tall|large
image: /blog/images/cover-slug.svg
---
```

**Card colors already used** (avoid duplicating adjacent posts if
possible): red, teal, purple, amber, green, blue, pink.

**Sizes:** `large` = 2×2 grid cells (hero), `wide` = 2×1, `tall` = 1×2,
`small` = 1×1. Use `large` sparingly (max 1-2 in the gallery).

**Writing voice:** entity ("AnalyVa" / "we") for newsletter emails,
but personal-neutral for blog posts (no "I" — use "you" for the reader
and passive/neutral otherwise, like the existing posts).

**Tutorial section pattern** (used by every published post):

```markdown
## Doing this in AnalyVa

Optional one-paragraph intro framing the workflow.

**Step 1 — Action headline in bold.**
1-3 sentences of prose explaining what to do.

![Alt text describing the screenshot](/blog/images/analyva-slug-01-descriptor.png)

**Step 2 — Next headline.**
...
```

The bold **Step N — Headline.** with paragraph and image below is the
site's house style. Match it.

**Cover SVG pattern** (batch 1 uses these): 800×600 viewBox,
`preserveAspectRatio="xMidYMid slice"`, cream background `#efe6d0`,
black `#1a1a1a` + red `#d62828` shapes only, one accent per cover.

---

## 6. Batch 2 — what to actually write next

For each of the three, screenshots are already in `/blog/images/` with
the naming above. Sample a few screenshots via `Read` to see what
each shows, then write the tutorial in the standard step-by-step form.

### Post 4 — Aug 4 — PLS-SEM & Delete Low Loading Indicators
- Slug suggestion: `pls-sem-with-indicator-cleaning`
- Card color: `green`, size: `large`
- 12 screenshots (`analyva-plssem-01` through `12`)
- Shows: building a 4-construct model (CFT, PFT, WM, WA → WSE with 8
  hypothesis paths), running Run → PLS-SEM → Standard Algorithms →
  PLS-SEM algorithm, then reviewing outer loadings, selecting low
  loaders in the construct's Props panel (Delete Selected button),
  re-running.

### Post 5 — Aug 6 — Recoding a Continuous Variable into Groups for MGA
- Slug suggestion: `recode-variables-for-multi-group-analysis`
- Card color: `blue`, size: `wide`
- 13 screenshots (`analyva-mga-01` through `13`)
- Shows: running Descriptives, then Transform → Recode into Same
  Variables to build a Gender-based grouping variable, then opening
  the PLS-SEM algorithm dialog and enabling **Group data sets →
  Gender (2 groups)** to prep multi-group analysis. Note the
  Female/Male checkboxes and "Start calculation" button.

### Post 6 — Aug 8 — Moderation Analysis in PLS-SEM
- Slug suggestion: `moderation-analysis-in-pls-sem`
- Card color: `pink`, size: `wide`
- 17 screenshots (`analyva-moderation-01` through `17`)
- Shows: a model with a moderator variable (WP1, WP2, WP3 as
  moderator indicators), drawing the moderator construct, connecting
  it with interaction paths (purple dashed lines), running the
  algorithm with the Quadratic effect / SmartPLS-compatible centroid
  option in the PLS setup panel, then reading the significance
  display. Folder name also mentions "Significance appearance" — this
  post can also cover switching how significance is displayed on paths
  (Beta vs stars vs p-value in the bottom Path: dropdown).

### After writing each: create the geometric SVG cover
Same style as batch 1. See `/blog/images/cover-shortcuts.svg` etc.
for the pattern.

---

## 7. Batches 3 and 4 — future work

Once batch 2 is approved by the user, batch 3 = 3 posts for
**Aug 10, 12, 18** and batch 4 = 4 posts for **Aug 24, 28, 29, 30**.

Pick topics from the remaining folders in `Screenshots2/`:
- `Beysian` (Bayesian)
- `CB-SEM`
- `Computational Analysis types`
- `Gaussian Copula; Path coefficients are movable; Indicators are hidable`
- `High Order CFA`
- `MGA`
- `Risidual Covariance; CB; Color Code; CB-SEM result components`

Roughly ordering easier → harder for the schedule:
- Aug 10: `Gaussian Copula; …` (adds endogeneity, familiar territory)
- Aug 12: `High Order CFA` (second-order measurement)
- Aug 18: `MGA` (full MGA with results)
- Aug 24: `CB-SEM` (intro to CB-SEM)
- Aug 28: `Risidual Covariance; CB; …` (CB-SEM result interpretation)
- Aug 29: `Computational Analysis types` (NLP for qual side)
- Aug 30: `Beysian` (advanced closer)

But this ordering is a suggestion — the user may want a different
sequence.

---

## 8. Repeat this loop for each post

1. Look at what's in the screenshot folder (e.g. `ls Screenshots2/<folder>/`).
2. Sample 2-3 screenshots with the `Read` tool to understand the
   workflow.
3. Copy the screenshots to `/blog/images/` with a post-specific prefix:
   `analyva-<slug>-01.png`, `-02.png`, etc.
4. Create a geometric SVG cover in `/blog/images/cover-<slug>.svg`.
5. Write the `.md` post in `_posts/` with a future date, proper front
   matter, and the step-by-step tutorial format.
6. Add the new post URL to `sitemap.xml` manually.
7. Batch-approve with the user, then push.

---

## 9. Git workflow for the user

The user runs git themselves. Every completed batch, tell them:

```bash
cd ~/Websites/Bouzarab.github.io
git add .
git commit -m "Batch N of 4: new posts for <dates>"
git push
```

Wait ~90 seconds for GitHub Pages to build. Future-dated posts stay
hidden until the daily rebuild picks them up on their date.

---

## 10. Known live IDs (do not change unless the user asks)

- **Brevo form action:** stored in `_config.yml` under `brevo.form_action`.
- **Brevo DOI merge tag:** `{{ doubleoptin }}` (lowercase, no `params.`).
- **Google Analytics:** `G-0Y35NWRSZS` — hardcoded in
  `_includes/head.html` and inline in `index.html`.
- **Google Search Console:** verified via meta tag in
  `_includes/head.html`.
- **Author ORCID:** `0000-0002-6918-7817` (Bouzar); `0000-0001-8768-1889`
  (El Idrissi). Referenced in `cite.html` and post BlogPosting schema.

---

## 11. Things NOT to do

- Don't restructure `index.html` — user is attached to its design.
- Don't add `future: true` to `_config.yml` — it defeats the whole
  scheduled-publishing setup.
- Don't rebuild the newsletter pipeline — Brevo + ImprovMX + branded
  templates all work end-to-end.
- Don't rename existing post files — the URLs are permanent now.
- Don't touch the four Zenodo DOIs — they're published and citable.

---

## 12. Quick sanity command

To see what's on the site right now:

```bash
cd ~/Websites/Bouzarab.github.io
ls _posts/          # list all posts, dated (past + future)
ls blog/images/     # list all cover art and screenshots
cat _config.yml     # verify permalink and brevo IDs are still there
```

---

**End of handoff.** A new model reading this file has everything it
needs to continue writing posts 4-13 without re-discovering the
project. Start with **batch 2 (posts 4, 5, 6)** — the screenshots are
already in place, just need the SVG covers and markdown files.
