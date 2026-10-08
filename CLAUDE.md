# genai-learning-moments

A Quarto website of learning moments, published at <https://chendaniely.github.io/genai-learning-moments/>.
New moments come from the `capture-learning-moment` skill, whose `template.qmd` is the structure of every post.
This file holds what is specific to this repository; where it differs from the skill's defaults, this file wins.

## Layout

- `posts/YYYY-MM-DD-<slug>.qmd`: one file per moment. The home page lists everything in `posts/`.
- `index.qmd`: the listing (newest first, category filter, RSS feed at `index.xml`).
- `about.qmd`: what a moment is and how to read one.
- `_quarto.yml`: site config. Its `render:` list is what becomes a page, so `README.md` and this file stay repo-only.
- `.github/workflows/publish.yml`: renders on every pull request; renders and publishes to the `gh-pages` branch on every push to `main`.
  Actions are pinned to commit SHAs; `.github/dependabot.yml` opens a monthly PR to bump them.

## Adding a moment

- **Put it in `posts/`**, named `YYYY-MM-DD-<slug>.qmd`. A file at the repo root is not rendered.
- **Front matter:** `title` ("Learning Moment: …"), `date` and `categories`, as in the template.
  The listing sorts by `date` and filters by `categories`, so keep all three.
  Start `categories` with `[claude, learning, ai-collaboration]`, then add every topic tag that fits:
  the tools in play (`quarto`, `python`, `git`, `shell`), the kind of lesson (`over-engineering`, `debugging`, `testing`, `security`), and the material (`teaching`, `writing`, `documentation`).
  Reuse tags already in use (`grep -h '^categories:' posts/*.qmd`); add a new one only when none fits.
- **Companion files** (a repro page, an image) go in `posts/` beside the post, named after it (`<post-name>-repro.html`), and are linked by relative path.
  Quarto copies linked files into the site.
- **Link other moments by relative `.qmd` path**, for example `[venv is a module](2026-08-26-venv-is-a-module.qmd)`.
  Quarto rewrites these to `.html`. Never link to a moment's GitHub blob or raw URL.
- **Render before committing:** `quarto render posts/<file>.qmd` for one post, or `quarto render` for the whole site.
  It should finish with no warnings. `quarto preview` serves it locally.
- **The published URL** is `https://chendaniely.github.io/genai-learning-moments/posts/<file>.html`. Use it when linking from elsewhere.

## Publishing

- **Pushing to `main` publishes.** The repo was already public; the site makes every moment one search away.
  Redaction (hostnames, IPs, usernames, paths) happens before the commit, not after: git history is permanent.
- Don't commit `_site/` or `.quarto/` (both are ignored). The workflow builds the site itself.
- Commit messages for a new moment: `Add learning moment: <short title>`.
