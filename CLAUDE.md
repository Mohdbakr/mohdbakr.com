# CLAUDE.md

## Project

Personal portfolio and blog for Mohamed Bakr — bilingual English/Arabic. Built with **Quarto** (`type: website`), deployed to GitHub Pages via GitHub Actions.

## Commands

```bash
uv sync                              # install dependencies
quarto preview                       # hot-reload dev server (no execution)
quarto render                        # full build → _site/
quarto render about.qmd              # single page (faster iteration)
quarto render --no-execute           # layout/style changes only
```

## File Map

| File | Purpose |
| --- | --- |
| `_quarto.yml` | Site config: navbar, footer, theme pair, brand ref |
| `_brand.yml` | Single source of truth for colours and typography |
| `assets/styles/theme.scss` | All custom styles — only SCSS file |
| `ar/_metadata.yml` | RTL config + JS that translates nav text and remaps hrefs to `/ar/*`, then restores `.active` class |
| `_includes/_fix-nav.html` | Injects language badge (EN/AR) into navbar |
| `_includes/_mode-toggle.html` | Floating dark/light mode toggle |

**Pages (English):** `index.qmd` · `about.qmd` · `projects.qmd` · `contact.qmd` · `accessibility.qmd` · `license.qmd`

**Pages (Arabic):** `ar/index.qmd` · `ar/about.qmd` · `ar/contact.qmd` — RTL via `lang: ar; dir: rtl` in `ar/_metadata.yml`

## Styling Rules

- All colours come from `_brand.yml` palette via Quarto's `--quarto-scss-export-*` variables, aliased in `theme.scss` as `--mb-*`. Never hardcode hex values.
- Dark mode: Quarto handles light/dark theme switching (`flatly`/`darkly`). Use `$body-color`, `$body-bg`, `$navbar-fg`, `$navbar-bg`, `$footer-fg`, `$footer-bg` — they resolve correctly in both modes.
- RTL overrides live in the `[dir="rtl"]` block at the bottom of `theme.scss`.

### Design Token Semantics

| Token | Colour | Use for |
| --- | --- | --- |
| `--mb-primary` | anvil-teal | Functional UI feedback: form focus, link/tab hover, contact icons |
| `--mb-accent` | hammered-gold | Decorative emphasis: image glows, borders, card accents |
| `--mb-accent-light` | navbar-hl | Scrolled navbar active/hover (light-on-dark contrast) |

### Link Styling Patterns

**Pattern A — Content links** (`$_link-underline-*` variables): Animated underline thickness + colour. Applied to `p a`, `li a`, `blockquote a` inside `main`. Not for nav or buttons.

**Pattern B — Metadata links**: Toggle `text-decoration` on hover only. For author names, dates, meta labels.

**Pattern C — Navigation** (`::after` pseudo-element): Animated underline expanding from centre. Applied to `.navbar-nav a.nav-link`.

**Pattern D — Interactive UI** (`transform`): `translateY`/`scale` motion on social links, cert badges, hero image.

## RTL Notes

- Arabic pages at `/ar/` share the same navbar config as English. Quarto's server-side `.active` detection uses English hrefs and won't match `/ar/*` URLs — `ar/_metadata.yml` JS handles this by stripping and re-applying `.active` after remapping hrefs.
- Contact form RTL separator flip is in the `[dir="rtl"] #contact` block in `theme.scss`.
- Footer is forced `direction: ltr` to keep icon layout consistent.
