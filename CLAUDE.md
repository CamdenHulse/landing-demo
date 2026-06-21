# CLAUDE.md

Guidance for AI assistants working in this repository.

## what this is

A single-page static **landing page for "treena"** — a (fictional) product
whose pitch is "mobile is the dev machine. no laptop." The site is the entire
deliverable; there is no application behind it.

**No frameworks. No build step. No dependencies. No external network requests.**
The page is hand-written HTML, CSS, and a small block of vanilla JavaScript. It
must keep loading instantly on mobile data, so this constraint is a hard rule,
not a preference.

## files

The whole project is three files at the repo root:

```
landing-demo/
├── index.html   # all markup + an inline <script> at the end of <body>
├── style.css    # all styles
├── README.md    # human-facing project readme
└── CLAUDE.md    # this file
```

- `index.html` — page structure in order: header/nav → hero (copy + css
  terminal mockup) → features → how it works → social proof (band) → manifesto
  → faq → signup (band) → footer. The `<script>` lives inline at the bottom of
  `<body>`; there is no separate JS file.
- `style.css` — organized top-to-bottom as: reset → `:root` design tokens →
  base → layout wrapper → then one section per component, in the same order as
  the markup → motion block → media queries.

## running it

No install, no compile. Either:

- open `index.html` directly in a browser (fine for a quick visual check), or
- serve statically: `python3 -m http.server 8080` then visit
  `http://localhost:8080` (recommended — closer to production behavior).

There is no test suite, linter, or CI build to run. "Verifying" a change means
loading the page in a browser and checking it at mobile and desktop widths.

## conventions — follow these

- **No build tooling and no dependencies.** Don't add a framework, bundler,
  package.json, npm packages, or a JS file. Keep the page to plain HTML/CSS/JS.
- **Zero external requests.** No web fonts, no CDN scripts, no remote images.
  The favicon is an inline `data:` SVG; the product shot in the hero is a
  **css-only terminal mockup** (markup + CSS, no image file). Keep it that way.
- **Lowercase copy and class names.** All visible text and CSS class names are
  intentionally lowercase. Match it.
- **Mobile-first.** Base styles target mobile; widen with `min-width` media
  queries. Breakpoints in use: **600px** (features/steps/stats become 3-column,
  waitlist row goes horizontal) and **760px** (two-column hero). A
  **max-width: 599px** block handles the JS mobile-nav collapse.
- **Design tokens.** Colors, spacing, radius, fonts, and easing are CSS custom
  properties in `:root`. Use existing tokens (e.g. `--accent`, `--bg-card`,
  `--ease`) instead of hardcoding values. Current palette is a dark theme:
  near-black backgrounds with a purple (`--accent #a855f7`) → cyan
  (`--accent-2 #22d3ee`) gradient accent. The only non-brand hues
  (`--term-green`, `--term-cyan`) are reserved for inside the fake terminal.
- **System fonts only.** `--font` is the system sans stack; `--mono` is the
  system mono stack (used in the terminal). No font downloads.
- **Accessibility & progressive enhancement.** Everything must work with
  JavaScript disabled — the JS only enhances. The root `<html>` gets a `js`
  class early (inline script in `<head>`) so CSS can gate JS-only behavior
  (`.js .reveal`, `.js .nav-toggle`). Keep `aria-*` attributes, the
  `.visually-hidden` labels, `:focus-visible` styles, and the
  `prefers-reduced-motion` handling intact when editing.
- **Motion is opt-in.** All animation lives under
  `@media (prefers-reduced-motion: no-preference)`. Scroll-reveal degrades to
  "everything visible" when motion is reduced or `IntersectionObserver` is
  unavailable.

## the inline JavaScript

A single IIFE at the bottom of `index.html` does four small things, all
progressive enhancement:

1. stamps the current year into the footer (`#year`),
2. toggles the mobile nav (hamburger → `.is-open`, with aria + Escape/close),
3. handles the demo waitlist form (`preventDefault`, validates, swaps in a
   success message — **nothing is actually sent or stored**),
4. scroll-reveals `.reveal` elements via `IntersectionObserver`.

If you add behavior, keep it vanilla, dependency-free, and gated so the page
still works without it.

## git workflow

- Active development branch for this work: `claude/claude-md-docs-t0un4a`.
- Do not push to `main` without explicit permission. Do not open a pull request
  unless explicitly asked.
- Keep commits small with descriptive messages. History shows the typical
  change here is a focused tweak (e.g. color-scheme adjustments, a section
  improvement).
