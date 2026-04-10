# Breeze Labs Docs

Public technical documentation for Breeze Labs, published at **<https://quarto.breezelabs.app>**.

Built with [Quarto](https://quarto.org), hosted on GitHub Pages, auto-deployed via GitHub Actions.

## Current docs

| File | Title | Audience |
|---|---|---|
| `voice-stack.qmd` | Breeze Buddy Voice Stack | Founders and technical leadership |

## How to update a doc

1. Edit the relevant `.qmd` file directly on `main` (or via a PR if you prefer review).
2. Commit and push.
3. GitHub Actions renders and publishes to <https://quarto.breezelabs.app> within ~90 seconds.
4. Refresh the page. Done.

No local rendering required. No manual upload.

## How to add a new doc

1. Create a new `your-doc.qmd` at the repo root.
2. Add it to the render list in `_quarto.yml` under `project.render`.
3. Add a navbar entry in `_quarto.yml` under `website.navbar.left`.
4. Link it from `index.qmd` so it appears on the landing page.
5. Commit and push.

## Local preview (optional)

```bash
brew install quarto    # one-time
cd quarto-docs
quarto preview         # live-reloading preview at http://localhost:<port>
```

To render once without previewing:

```bash
quarto render
```

The output goes into `_site/` which is gitignored.

## Project layout

```
quarto-docs/
├── _quarto.yml                         # project config (theme, navbar, render list)
├── index.qmd                           # landing page
├── voice-stack.qmd                     # the voice stack brief
├── CNAME                               # custom domain for GitHub Pages
├── README.md                           # you are here
├── .gitignore
└── .github/workflows/publish.yml       # auto-render + deploy to GitHub Pages
```

## How the auto-publish works

The `.github/workflows/publish.yml` workflow runs on every push to `main`:

1. Checks out the repo
2. Installs Quarto (via `quarto-dev/quarto-actions/setup@v2`)
3. Runs `quarto render` — produces `_site/`
4. Uploads `_site/` as a GitHub Pages artifact
5. Deploys it to GitHub Pages

The first successful run maps `<org>.github.io/quarto-docs` to the site. Once the custom domain is configured (see `CNAME`), all requests land on <https://quarto.breezelabs.app>.

## One-time setup (when first creating this repo)

If you are setting this repo up for the first time, see the setup checklist at the bottom of `.github/workflows/publish.yml` — or ask an engineer who set up the GitHub Pages + Cloudflare DNS binding the first time.
