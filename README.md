# treena

> mobile is the dev machine. no laptop.

treena is the environment for developers who build entirely from their phone.
real terminal, real editor, real workflow — no desk required.

---

## what this repo is

a minimal, static landing page for treena. no frameworks, no build step, no
dependencies. just `index.html` and `style.css`. loads instantly on mobile data.

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
├── index.html   # page markup — header, hero, features, manifesto, footer
├── style.css    # all styles — tokens, layout, components, one breakpoint at 600px
└── README.md    # this file
```

---

## design decisions

- **color palette** — near-black `#0d0d0d` background, warm off-white `#f0ede8`
  text, acid-green `#c8f04d` accent. high contrast, readable on any screen.
- **typography** — system font stack. `clamp()` for fluid headline sizing.
  no external font requests.
- **layout** — single centered column, `max-width: 760px`. feature cards stack
  vertically on mobile and shift to a three-column grid at 600px+.
- **no javascript** — except one line to stamp the current year in the footer.
- **no images** — zero network requests beyond the two local files.

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
