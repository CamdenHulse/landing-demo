# treena

> mobile is the dev machine. no laptop.

treena is the environment for developers who build entirely from their phone.
real terminal, real editor, real workflow — no desk required.

---

## what this repo is

a static landing page for treena. no frameworks, no build step, no
dependencies — just `index.html` and `style.css`. zero external network
requests (system fonts, a css-only product visual, an inline-svg favicon), so
it still loads instantly on mobile data.

---

## run locally

**option 1 — open directly**

drag `index.html` into any browser. works fine for visual review.

**option 2 — static server (recommended)**

if you have python 3:

```bash
python3 -m http.server 8080
```

then open `http://localhost:8080` in your browser.

if you have node / npx:

```bash
npx serve .
```

then open the url printed in the terminal (usually `http://localhost:3000`).

---

## project structure

```
landing-demo/
├── index.html   # page markup — header/nav, hero + terminal, features, how it
│                #   works, social proof, manifesto, faq, signup, footer
├── style.css    # all styles — tokens, layout, components, breakpoints at
│                #   600px and 760px, motion + reduced-motion blocks
└── README.md    # this file
```

---

## design decisions

- **color palette** — deep navy background (`--bg #04111f`), blue-black cards
  (`--bg-card #0a2038`), ice-white text (`--text #f5fbff`, muted
  `--text-muted #a9bfd3`), and a fading blue accent system (`--border
  #38bdf8`, `--accent #38bdf8`, `--accent-2 #818cf8`). derived tokens add
  depth — an ambient `--bg-grad`, an `--accent-glow`, and soft hairline borders
  (`--border-soft`). terminal colors stay in the same cool blue family with a
  teal status color for successful commands.
- **typography** — system font stack (system monospace inside the terminal).
  `clamp()` for fluid sizing. no external font requests.
- **layout** — centered column, `max-width: 760px`, with full-bleed `.band`
  sections that widen to `960px`. the hero is single-column on mobile and a
  two-column copy + terminal grid at 760px+. features / steps / stats stack on
  mobile and become three-column grids at 600px+.
- **product visual** — a css-only "mobile terminal" mockup (markup + css, no
  image) shows a `git push` → build → deploy flow right in the hero.
- **minimal javascript** — vanilla, dependency-free: stamps the footer year,
  toggles the mobile nav, runs the demo waitlist form, and reveals sections on
  scroll. all progressive-enhancement — every link, the faq, and all content
  work with javascript disabled — and it respects `prefers-reduced-motion`.
- **no images** — zero raster images and zero external requests; the favicon is
  an inline data-uri svg and the product shot is pure css.

---

## making changes

1. edit `index.html` or `style.css` directly — no compile step needed.
2. refresh the browser to see changes immediately.
3. commit and push:

```bash
git add index.html style.css README.md
git commit -m "describe your change here"
git push origin main
```

---

## contributing

open an issue or pull request on github. keep changes minimal and mobile-first.
all copy and class names stay lowercase — that's intentional.

---

## license

mit
