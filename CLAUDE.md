# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal/archival site for p5lab.net, built with **Markpub** — a Python-based static site generator that converts Markdown files into a wiki-style website. It is deployed on Netlify.

## Architecture

### Content and Build

- **Content**: Markdown files at the repo root (e.g., `README.md`, `Sidebar.md`) plus subdirectories
- **Sidebar navigation**: `Sidebar.md`
- **Build config**: `.markpub/markpub.yaml` — sets site title, author, theme, sidebar, edit URLs, etc.
- **Theme**: `p5_forte` (a customized fork of the `forte` theme), located at `.markpub/themes/p5_forte/`
- **Build output**: `.markpub/output/` (Markpub copies and converts the entire repo)
- **Search**: Lunr.js index built via Node.js; `.markpub/package.json` lists `lunr` as a dependency

### Build Process

Netlify runs the build from the `.markpub/` directory:
```
markpub build -i .. -o ./output --lunr --commits
```
(`-i ..` points to the repo root as input; `--lunr` builds the search index; `--commits` adds git commit metadata)

To build locally, activate the Python venv and run from `.markpub/`:
```bash
cd .markpub
source .venv/bin/activate
markpub build -i .. -o ./output --lunr --commits
```

### Theme Customization

The active theme lives at `.markpub/themes/p5_forte/`. It inherits from the `forte` base theme (`.markpub/themes/forte/`). Theme templates use Jinja2-style HTML partials:
- `_header.html`, `_footer.html`, `_body-header.html`, `_javascript.html`
- `page.html`, `all-pages.html`, `recent-pages.html`, `search.html`
- CSS: `.markpub/themes/p5_forte/static/markpub_static/css/`

### Legacy Static Assets

The repo also contains legacy static HTML that predates Markpub. Markpub copies it into the output as-is:
- `public/` — historical Praxis101 landing page with its own CSS/JS copies
- `docs/` — another static HTML section with its own CSS/JS copies
- `js/site.js`, `css/` — Skeleton CSS framework assets used by legacy pages
- `previous-index.html` — archived version of the old landing page

These legacy files use the Skeleton CSS framework (v2.0.4) with jQuery loaded from CDN.

### Netlify Config

`netlify.toml` sets `base = ".markpub"`, `publish = "./output"`, `PYTHON_VERSION = "3.12"`, and `ignore = "/bin/false"` (always rebuilds).

## Editing

- Add or edit Markdown files at the repo root to create/update wiki pages
- Update `Sidebar.md` to change navigation links
- Customize theme appearance in `.markpub/themes/p5_forte/static/markpub_static/css/`
- Site metadata (title, author, edit URLs) is in `.markpub/markpub.yaml`
