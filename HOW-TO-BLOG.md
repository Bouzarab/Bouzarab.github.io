# How to publish a new blog post

The blog is powered by Jekyll, which GitHub Pages builds automatically
every time you `git push`. You don't run anything locally unless you
want to preview.

## Writing a new post — the 5-minute version

1. Create a new file in the `_posts/` folder.
2. Name it `YYYY-MM-DD-your-slug-here.md` — the date at the start is
   required, and the slug becomes part of the URL.
3. Copy the front matter from any existing post and edit the fields.
4. Write the body in Markdown.
5. `git add`, `git commit`, `git push`. The post is live within about
   a minute.

## Filename rules

- Must start with `YYYY-MM-DD-`
- Use lowercase and hyphens for the slug — no spaces, no capitals.
- Good: `2026-08-01-pls-sem-minimum-sample-size.md`
- Bad: `2026-8-1 PLS-SEM Sample Size.md`

## Front matter cheatsheet

Every post starts with a block between two `---` lines:

```yaml
---
title: "Your post title in quotes"
subtitle: >-
  One or two sentences that appear under the title and in
  the blog index card.
category: PLS-SEM          # or "Statistics", "Textual Analysis", etc.
tier: Tier 1 · Problem query
read_time: 9               # minutes, your best estimate
doi: 10.5281/zenodo.21536948   # optional; adds a validation link at the bottom
tags: [PLS-SEM, HTMT, discriminant validity]
---
```

Only `title` and `date` (from the filename) are strictly required.
Everything else is optional but helpful.

## Writing in Markdown

- `## Heading` for section headings.
- `**bold**` and `*italic*`.
- `[link text](https://example.com)` for links.
- Reference-style links (cleaner for many links):

  ```markdown
  See [Henseler et al.][hrs2015] for the original definition.

  [hrs2015]: https://doi.org/10.1007/s11747-014-0403-8
  ```

- Inline code with backticks: `` `HTMT` ``.
- Fenced code blocks:

  ````markdown
  ```r
  library(seminr)
  ```
  ````

- Blockquotes with `>`:

  ```markdown
  > This is a callout or a quote.
  ```

- Images:

  ```markdown
  ![Descriptive alt text](/screenshots/analyva-htmt-report.png)
  ```

  Put the file in `/screenshots/` or a dedicated `/blog/images/` folder.
  Always give real alt text — image search sends real traffic in
  academic niches.

## The post structure that works

From the SEO strategy brief:

1. Answer the reader's question completely and generously, including
   how it's done in SPSS, SmartPLS, or NVivo. **Never gate the answer.**
2. End with a short "Doing this in AnalyVa" section — 3–4 annotated
   screenshots showing the equivalent workflow.
3. Link to the relevant validation study DOI where the underlying claim
   is benchmarked (use the `doi:` front matter field to auto-generate
   the footer link).
4. Internal-link to 2–3 related posts.

## Previewing locally (optional)

If you want to preview posts on your Mac before pushing:

```bash
# One-time setup
gem install bundler jekyll
bundle install

# Every time you want to preview
bundle exec jekyll serve
# Open http://localhost:4000
```

Otherwise, just push to git and check `https://analyva.com/blog/`.

## Tagging cadence

Two posts a week is the cadence to aim for. If you slip, don't burn
yourself out catching up — consistency beats bursts, but slowness beats
silence. Even one post a week keeps the compounding-returns clock
running.
