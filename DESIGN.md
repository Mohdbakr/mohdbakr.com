---
name: Mohamed Bakr Portfolio
description: Forged precision — a data scientist's portfolio where rigorous craft meets human warmth.
colors:
  anvil-teal: "#0F766E"
  anvil-teal-light: "#2DD4BF"
  hammered-gold: "#A16207"
  hammered-gold-light: "#FBBF24"
  molten-crimson: "#991B1B"
  iron-slate: "#475569"
  copper-green: "#065F46"
  surface-light: "#FAFAF9"
  surface-dark: "#333333"
  ink-warm: "#352A26"
  parchment: "#D6C8B8"
typography:
  display:
    fontFamily: "Lora, Georgia, serif"
    fontSize: "3rem"
    fontWeight: 700
    lineHeight: 1.1
    letterSpacing: "normal"
  headline:
    fontFamily: "Lora, Georgia, serif"
    fontSize: "2.2rem"
    fontWeight: 700
    lineHeight: 1.15
  title:
    fontFamily: "Lora, Georgia, serif"
    fontSize: "1.5rem"
    fontWeight: 600
    lineHeight: 1.3
  body:
    fontFamily: "Poppins, system-ui, sans-serif"
    fontSize: "1rem"
    fontWeight: 400
    lineHeight: 1.6
  label:
    fontFamily: "Poppins, system-ui, sans-serif"
    fontSize: "0.875rem"
    fontWeight: 700
    letterSpacing: "0.1em"
  mono:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "0.875rem"
    fontWeight: 400
  arabic-body:
    fontFamily: "Tajawal, sans-serif"
    fontSize: "1rem"
    fontWeight: 400
    lineHeight: 1.6
  arabic-title:
    fontFamily: "Readex Pro, sans-serif"
    fontSize: "inherit"
    fontWeight: 600
rounded:
  sm: "4px"
  md: "8px"
  lg: "12px"
  full: "50%"
spacing:
  xs: "0.25rem"
  sm: "0.5rem"
  md: "1rem"
  lg: "1.5rem"
  xl: "2rem"
components:
  button-ghost:
    backgroundColor: "transparent"
    textColor: "var(--bs-body-color)"
    rounded: "{rounded.md}"
    padding: "0.5rem 1rem"
  button-ghost-hover:
    backgroundColor: "rgba(var(--bs-body-color-rgb), 0.06)"
    textColor: "var(--mb-primary)"
    rounded: "{rounded.md}"
    padding: "0.5rem 1rem"
  social-link:
    backgroundColor: "rgba(var(--bs-body-color-rgb), 0.08)"
    textColor: "rgba(var(--bs-body-color-rgb), 0.85)"
    rounded: "{rounded.md}"
    size: "2.75rem"
  social-link-hover:
    backgroundColor: "rgba(var(--bs-body-color-rgb), 0.12)"
    textColor: "var(--bs-body-color)"
    rounded: "{rounded.md}"
    size: "2.75rem"
  project-card:
    backgroundColor: "transparent"
    rounded: "{rounded.md}"
    padding: "{spacing.md}"
  project-card-hover:
    backgroundColor: "transparent"
    rounded: "{rounded.md}"
    padding: "{spacing.md}"
  category-pill:
    backgroundColor: "transparent"
    textColor: "var(--bs-body-color)"
    rounded: "{rounded.sm}"
    padding: "0.2rem 0.6rem"
  category-pill-hover:
    backgroundColor: "color-mix(in srgb, var(--mb-primary) 10%, transparent)"
    textColor: "var(--mb-primary)"
    rounded: "{rounded.sm}"
    padding: "0.2rem 0.6rem"
---

# Design System: Mohamed Bakr Portfolio

## 1. Overview

**Creative North Star: "The Forged Portfolio"**

This is a portfolio built the way a precision instrument is made: not designed to impress at a glance, but to reward close attention. The metalwork palette (Anvil Teal, Hammered Gold, Molten Crimson, Iron Slate, Copper Green) is not decorative naming — it encodes a philosophy. Real craft takes time, pressure, and iteration. The result is refined through process, not ornamented in a rush.

The typographic pairing of Lora (an editorial serif with ink-trap origins) and Poppins (a clean geometric sans) encodes the same duality: depth and rigour alongside clarity and approachability. Hierarchy is established through scale and weight contrast, never by relying on color alone. Body text is capped at 65–75ch to preserve reading comfort at every viewport width.

Surfaces carry ambient elevation from rest. Cards and containers are slightly lifted even at default state — they don't need to be hovered to register as objects with weight and presence. Hover states amplify that presence: a lift, deeper shadow, and a warm hammered-gold glow. The bilingual nature of the site (EN/AR) is a structural constraint, not an afterthought: RTL layout, Arabic-specific typefaces, and accessible contrast are woven into every component decision.

This system explicitly rejects: gradient blobs and glassmorphism used decoratively, LinkedIn corporate energy, generic Bootstrap portfolio layouts, and any visual pattern that could belong to anyone.

**Key Characteristics:**
- Serif/sans pairing: Lora for authority, Poppins for clarity
- Metalwork palette: named for material qualities, not hex codes
- Ambient elevation at rest: surfaces have presence before interaction
- Two-role color discipline: teal for function, gold for decoration
- Full bilingual EN/AR support with dedicated Arabic typefaces (Tajawal body, Readex Pro headings)
- All color in code flows through Quarto's `_brand.yml` exports and Bootstrap/Quarto variables — never hardcoded

## 2. Colors: The Forged Palette

Two accent roles with strict purpose separation. Neither competes for the same surface.

### Primary
- **Anvil Teal** (light: `$primary` / dark: `$primary`, resolved via `--mb-primary`): Functional UI feedback only. Link hover, form focus rings, active nav states, contact icon hover. The color of precision and reliability. Used wherever the interface confirms user intent.

### Secondary
- **Hammered Gold** (light: `$secondary` / dark: `$secondary`, resolved via `--mb-accent`): Decorative emphasis only. Profile image glows, card hover accent rings, ambient warmth. Never used for functional feedback. Its rarity makes it feel earned.

### Tertiary
- **Molten Crimson** (`$danger`): Error and danger states exclusively.
- **Copper Green** (`$success`): Success states only.

### Neutral
- **Surface Light / Surface Dark** (`$body-bg`): Page background per mode. Slightly warm — not clinical white, not pure black.
- **Ink Warm / Parchment** (`$body-color`): Body text per mode. A warm near-black in light mode, warm cream in dark mode.
- **Iron Slate** (`$gray-600` range): Supporting text, dividers, secondary metadata.

### Color in Code

All color values in SCSS and CSS must come from Quarto/Bootstrap exported variables. `_brand.yml` values are automatically exported by Quarto through:

- `$body-color`, `$body-bg` — resolve to the correct palette value per mode
- `$navbar-fg`, `$navbar-bg`, `$footer-fg`, `$footer-bg` — surface-scoped aliases
- `$link-color` — resolves to `$primary` (anvil-teal per mode)
- `--mb-primary` — aliased from `--quarto-scss-export-primary` (anvil-teal)
- `--mb-accent` — aliased from `--quarto-scss-export-secondary` (hammered-gold)
- `--mb-accent-light` — aliased from `--quarto-scss-export-navbar-hl` (scrolled navbar accent)
- `color-mix(in srgb, var(--mb-accent) X%, transparent)` — for tinted surfaces and glows
- `rgba($body-color, X)` — for tinted borders, dividers, and shadows

Never reference palette hex values directly in SCSS or CSS. If a new semantic role is needed, add it to `_brand.yml` and alias it in `:root`.

### Named Rules

**The Two-Role Rule.** Anvil Teal (`--mb-primary`) signals function; Hammered Gold (`--mb-accent`) signals decoration. They never swap roles. A teal card glow or a gold focus ring is a system violation.

**The Warm Neutral Rule.** Never use `#fff` or `#000`. `$body-bg` and `$body-color` always resolve to warmth-tinted values as defined in `_brand.yml`. This holds in both light and dark modes.

## 3. Typography

**Display/Heading Font:** Lora (Georgia, serif fallback)
**Body Font:** Poppins (system-ui, sans-serif fallback)
**Monospace:** JetBrains Mono
**Arabic Body:** Tajawal (sans-serif fallback) — applied via `[dir="rtl"] body { font-family: "Tajawal", sans-serif }`
**Arabic Headings (H1–H6 in RTL):** Readex Pro (sans-serif fallback) — applied via `[dir="rtl"] h1, h2, ... { font-family: "Readex Pro", sans-serif }`

**Character:** Lora brings editorial authority to headings — its ink-trap details add visual texture at large sizes without veering into academic stiffness. Poppins is geometric but warm, legible at any weight. The pairing reads: rigorous thinker, clearly explained. In Arabic, Tajawal and Readex Pro mirror the same logic — Readex Pro's geometric structure for headings, Tajawal's warmth for prose.

### Hierarchy
- **Display** (Lora, 700, 3rem, line-height 1.1): Hero name on the index page only. Never reused for section headings.
- **Headline** (Lora, 700, 2.2rem, line-height 1.15): Page-level H1 headings, about page title.
- **Title** (Lora, 600, 1.5rem, line-height 1.3): Subsection H2 headings, project card titles on detail pages.
- **Body** (Poppins 400 / Tajawal 400 in RTL, 1rem, line-height 1.6, max 65–75ch): All prose. Never narrower than 45ch on wide viewports.
- **Label** (Poppins, 700, 0.875rem, letter-spacing 0.1em, uppercase): Navbar items, category pills, hero subtitle, metadata labels. Uppercase is reserved for structural UI — never applied to content prose.
- **Mono** (JetBrains Mono, 400, 0.875rem): Code blocks, language toggle badge, any UI element signaling precision.

### Named Rules

**The Serif Headings Rule.** H1–H3 in content areas are always Lora (or Readex Pro in RTL). Poppins is for UI labels and subtitles only. The serif/sans split is the primary hierarchy signal.

**The Arabic Type Rule.** In `[dir="rtl"]` contexts, body text renders in Tajawal and headings in Readex Pro. These are not fallbacks — they are the intentional typefaces for Arabic content. Never allow Poppins or Lora to render Arabic script.

## 4. Elevation

This system uses ambient elevation. Surfaces carry visible depth even at rest. Work has weight and presence before you touch it.

**Rest state:** Cards and interactive containers render with a diffuse ambient shadow (`0 2px 4px rgba($body-color, 0.08)`). Barely visible, but present. It registers as material substance, not a literal drop shadow.

**Hover state:** Shadow deepens (`0 4px 12px rgba($body-color, 0.10)`), element lifts `translateY(-4px)`, and a hammered-gold accent ring appears (`color-mix(in srgb, var(--mb-accent) 35%, transparent)`). The compound effect — lift + deepen + warm glow — is the system's signature interaction.

**Non-surface elements:** Navbar, footer, and body background are fully flat. Elevation belongs to content objects, not the page frame.

### Shadow Vocabulary
- **Ambient** (`0 2px 4px rgba($body-color, 0.08)`): Rest state for cards and containers.
- **Elevated** (`0 4px 12px rgba($body-color, 0.10)`): Hover state — the interaction signal.
- **Deep** (`0 8px 24px rgba($body-color, 0.15)`): Profile image and hero portrait. Communicates singular importance.

### Named Rules

**The Weight-Before-Touch Rule.** Content objects carry ambient shadow at rest. Shadow reflects the intrinsic weight of real work — it doesn't have to be earned by hovering. Only its depth changes on interaction.

**The Frame-Is-Flat Rule.** Navbar, footer, and page background never receive elevation. Depth belongs to content, not chrome.

## 5. Components

### Buttons
Ghost-first. The primary button is transparent with a border, reinforcing that content is the point.

- **Shape:** Gently curved corners (8px radius, `$_radius-md`)
- **Ghost (default):** `transparent` background, `rgba($body-color, 0.25)` border, `$body-color` text
- **Hover:** `rgba($body-color, 0.06)` background, border and text shift to `var(--mb-primary)`, `translateY(-2px)` + ambient shadow, 0.2s ease
- **Active:** `translateY(0)`, no shadow
- **Never:** Solid-filled primary buttons in content areas. Ghost is the default; solid fill is only for form submission actions.

### Social / Icon Links (Hero)
44×44px touch targets, icon-only, used in the index hero and about pages.

- **Shape:** 8px radius
- **Default:** `rgba($body-color, 0.08)` fill, `rgba($body-color, 0.15)` border, `rgba($body-color, 0.85)` icon color
- **Hover:** Fill deepens to `rgba($body-color, 0.12)`, border to `rgba($body-color, 0.30)`, icon to `$body-color`, `translateY(-2px)` + ambient shadow, 0.3s `$_easing-standard`
- **Sponsor variant:** Tinted with `$brand-sponsor-color` throughout, never `$body-color`

### Project Cards (Listing)
- **Corner style:** Gently curved (8px radius)
- **Background:** `transparent` — inherits page background. Never an explicit white card on a light page.
- **Shadow at rest:** `$_shadow-sm` (ambient elevation)
- **Shadow on hover:** `$_shadow-md` + `0 0 0 1px color-mix(in srgb, var(--mb-accent) 35%, transparent)` accent ring
- **Border at rest:** `1px solid rgba($body-color, 0.08)`
- **Border on hover:** `color-mix(in srgb, var(--mb-accent) 35%, transparent)`
- **Internal padding:** `$_space-md` (1rem)
- **Image:** `scale(1.04)` on card hover over `$_anim-slow` (0.6s). Height fixed at 200px, `object-fit: cover`.

### Category Pills
Clickable filters on listing pages; metadata labels on project detail pages.

- **Default:** No background, `$body-color` text, 4px radius
- **Hover (listing):** `color-mix(in srgb, var(--mb-primary) 10%, transparent)` background, `var(--mb-primary)` text and border, `translateY(-1px)`, 0.2s ease
- **Hover (project detail):** `color-mix(in srgb, var(--mb-accent) 12%, transparent)` background, `var(--mb-accent)` text and border — decorative context applies on detail pages

### Navigation
- **Style:** Transparent at page top; `rgba($navbar-bg, 0.85)` when scrolled
- **Typography:** Poppins 700, uppercase, `letter-spacing: 0.1em`
- **Default:** `opacity: 0.65`
- **Hover / Active:** `opacity: 1` + underline expands from center (`scaleX(0)` → `scaleX(0.8)`, 0.3s `$_easing-standard`). Active state: `border-bottom-width: 0.2em`.
- **Color at top:** `$body-color` (dark text on transparent background)
- **Color when scrolled:** `$navbar-fg` (light text on dark background); active/hover accent shifts to `var(--mb-accent-light)`
- **Mobile (≤992px):** Underline animations suppressed via `scaleX(0) !important`.

### Language Toggle Badge
A signature component: the EN/AR switcher is a standalone monospace pill in the navbar, no icon.

- **Style at top:** `$body-bg` text on `$body-color` background, 4px radius, `$font-family-monospace` at 0.68em, weight 900
- **Style when scrolled:** `$navbar-bg` text on `$navbar-fg` background
- **Hover:** Both states invert to ~50% opacity with reduced background

### Profile Image
- **About page (trestles template):** 12px radius, `2px solid color-mix(in srgb, var(--mb-accent) 20%, transparent)` border, `$_shadow-md` at rest. Hover: `$_shadow-lg`, `translateY(-5px)`, border deepens to `var(--mb-accent)`.
- **Index page (solana template):** Circular crop. `drop-shadow` with `color-mix(in srgb, var(--mb-accent) 40%, transparent)` tint (not `box-shadow` — follows PNG contour). Hover deepens glow and lifts `translateY(-4px)`.

## 6. Do's and Don'ts

### Do:
- **Do** use `var(--mb-primary)` for every functional feedback moment: link hover, focus rings, active nav, form focus, contact icon hover.
- **Do** use `var(--mb-accent)` for decorative glow only: image borders, card hover rings, ambient warmth that signals quality without implying action.
- **Do** give cards `$_shadow-sm` at rest. Ambient elevation is the system's signature — never flatten surfaces back to border-only.
- **Do** cap body prose at 65–75ch. Reading comfort is non-negotiable.
- **Do** use Lora (Readex Pro in RTL) for H1–H3 in content areas. The serif/sans split carries the hierarchy signal.
- **Do** use uppercase + letter-spacing for Poppins label-weight UI elements only (navbar, pills, subtitles). Never apply uppercase to heading or body prose.
- **Do** use Tajawal for Arabic body text and Readex Pro for Arabic headings in all `[dir="rtl"]` contexts.
- **Do** source all colors from Quarto/Bootstrap variables (`$body-color`, `$navbar-bg`, `--mb-primary`, `--mb-accent`, `color-mix()` patterns). `_brand.yml` is the single source of truth; its values are exported automatically.
- **Do** ensure every interactive element has a visible `focus-visible` indicator: `2px solid $body-color`, `outline-offset: 2px`.
- **Do** test every component in both light and dark mode and with `prefers-reduced-motion` active.

### Don't:
- **Don't** use gradient text (`background-clip: text` with a gradient). Emphasis comes from weight and size, not gradient decoration.
- **Don't** use glassmorphism decoratively. Blur effects are prohibited except where structurally justified (scrolled navbar readability).
- **Don't** use gradient blobs, ambient background gradients, or decorative hero glows. This is PRODUCT.md's first anti-reference and the most visible AI-generated design signal.
- **Don't** use `border-left` greater than 1px as a colored accent stripe on cards, callouts, or list items. Rewrite with background tints, full borders, or leading icons.
- **Don't** build identical card grids. The listing should have visual rhythm, not uniformity.
- **Don't** render LinkedIn blue (#0A66C2 or similar) anywhere. LinkedIn icon links render in `$body-color`.
- **Don't** use `#000`, `#fff`, or any hardcoded hex value in SCSS or CSS. `$body-bg` and `$body-color` from `_brand.yml` are the warmth-tinted extremes.
- **Don't** apply `var(--mb-accent)` (Hammered Gold) to interactive/functional states. Teal (`--mb-primary`) for function, gold (`--mb-accent`) for decoration — never reversed.
- **Don't** override Quarto/Bootstrap color variables with literal values. If a semantic role is missing, add it to `_brand.yml` and alias it in `:root` via `--mb-*`.
- **Don't** remove `focus-visible` indicators without a replacement. Accessibility is a design principle, not a checklist item.
