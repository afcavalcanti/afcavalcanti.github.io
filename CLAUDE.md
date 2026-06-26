# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio website built with **Hugo** (static site generator, v0.157.0+). Bilingual (Portuguese default, English secondary). Deployed automatically to GitHub Pages via GitHub Actions on every push to `main`.

## Commands

```bash
# Start local development server
hugo server

# Production build (matches CI)
hugo --gc --minify --baseURL "https://afcavalcanti.github.io/"
```

No npm, Node.js, or other build tools — pure Hugo.

## Architecture

### Configuration-driven content

All portfolio content (experience, education, projects, achievements, skills, social links, section visibility) lives in **`hugo.yaml`** — not in markdown files. This is the primary file to edit for content changes.

### Multilingual structure

- **Portuguese (default):** `content/_index.md` + `[languages.pt]` section in `hugo.yaml`
- **English:** `content/en/_index.md` + `[languages.en]` section in `hugo.yaml`

Each language block in `hugo.yaml` has its own copy of all content sections. When updating content, update both language blocks.

### Theme

Uses [hugo-profile](https://github.com/gurusabarish/hugo-profile) as a Git submodule at `themes/hugo-profile/`. Custom overrides go in `layouts/partials/` (takes precedence over theme templates).

### Static assets

Images referenced in `hugo.yaml` are stored in `static/images/`. Resume PDF is at `static/resume.pdf`.

### Deployment

`.github/workflows/deploy.yml` — builds and publishes to GitHub Pages on every push to `main`. No manual deployment step needed.
