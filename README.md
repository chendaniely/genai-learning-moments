# genai-learning-moments

Capturing examples of me correcting GenAI output.

**Read them at <https://chendaniely.github.io/genai-learning-moments/>.**

Each moment lives in [`posts/`](posts/) as a Quarto document.
The site is built with [Quarto](https://quarto.org) and published to GitHub Pages by
[a GitHub Actions workflow](.github/workflows/publish.yml) on every push to `main`.

To build it locally:

```bash
quarto preview
```

New moments are written with the
[`capture-learning-moment`](https://github.com/chendaniely/skills/tree/main/capture-learning-moment)
Claude Code skill. See [`CLAUDE.md`](CLAUDE.md) for where they go and how they're formatted.
