# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A bilingual (English / Arabic) educational website covering practical data science and ML topics — statistics for business problems, probability, machine learning foundations, and related applied topics. Built with **Quarto** (`type: website`) and deployed to GitHub Pages via GitHub Actions.

## Commands

**Setup:**
```bash
uv sync
```

**Local preview (hot-reloads on save, does not execute notebooks):**
```bash
quarto preview
```

**Full build (execute notebooks + generate static HTML):**
```bash
quarto render
```

**Build a single page (faster iteration):**
```bash
quarto render content/en/week-01-conditioning.qmd
```

**Build without executing** (layout/style changes only):
```bash
quarto render --no-execute
```

Output goes to `_site/` (not `_build/`).

## Architecture

- **`_quarto.yml`** — primary site config: project type, navbar, sidebar, footer, light/dark theme pair, brand reference.
- **`_brand.yml`** — single source of truth for all colours and typography. All CSS uses `--brand-*` custom properties; never hardcode hex values in SCSS.
- **`pyproject.toml`** — dependency management via `uv`. Add new dependencies here and run `uv sync`.
- **`styles/custom.scss`** — site-wide styles. Sections: semantic colour bridge (`:root`), hero, components, dark mode (`[data-bs-theme=dark]`), RTL corrections (`[dir="rtl"]`).
- **`index.qmd`** — English landing page.
- **`about.qmd`** — English about page.
- **`ar/`** — Arabic section (`/ar/`). Each page sets `lang: ar; dir: rtl` via `ar/_metadata.yml`.
- **`content/en/`** — English lesson pages (`.qmd` files).
- **`content/ar/`** — Arabic lesson pages.
- **`.github/workflows/deploy.yml`** — CI pipeline: `quarto render` on push to `main`, deploys `_site/` to GitHub Pages.
- **`_site/`** — generated output, not committed.

## Styling rules

- All colours must reference `--brand-*` CSS variables (generated from `_brand.yml`) or the semantic bridge variables (`--color-primary`, `--color-accent`, etc. defined in `custom.scss`).
- Dark mode overrides live in the `[data-bs-theme=dark]` block in `custom.scss`.
- RTL fixes live in the `[dir="rtl"]` block in `custom.scss`.
- Theme pair: `light: [flatly, styles/custom.scss]` / `dark: [darkly, styles/custom.scss]`.

## Adding content

1. Create `content/en/<slug>.qmd` (and optionally `content/ar/<slug>.qmd` for Arabic).
2. Add the page to the `sidebar` section in `_quarto.yml`.
3. Run `quarto render content/en/<slug>.qmd` to test before a full build.
