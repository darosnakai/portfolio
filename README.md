# Daros Nakai — Portfolio Website

A clean, modern dark-theme personal portfolio built in pure HTML, CSS, and JavaScript. No frameworks or build tools required.

---

## File Structure

```
portfolio/
├── index.html          ← Root redirect (sends visitors to /f/ by default)
├── README.md           ← This file
├── CNAME               ← Custom domain (darosnakai.com)
├── cv-en.pdf           ← English CV
├── cv-pt.pdf           ← Portuguese CV
│
├── f/                  ← Finance portfolio
│   ├── index.html      ← Homepage (hero + projects grid + about)
│   ├── favicon_dn.png
│   └── projects-t/
│       ├── factor-investing.html
│       ├── brazilian-inflation-prediction.html
│       └── capm-risk-return.html
│
└── t/                  ← Tech portfolio
    ├── index.html      ← Homepage (hero + projects grid + about)
    ├── favicon_dn.png
    └── projects-t/
        ├── factor-investing.html
        ├── brazilian-inflation-prediction.html
        └── capm-risk-return.html
```

---

## Routing

`darosnakai.com` resolves via the root `index.html`, which immediately redirects to `/f/` (the finance portfolio). To change the default:

```html
<!-- portfolio/index.html -->
<!DOCTYPE html>
<meta http-equiv="refresh" content="0; url=f/">
```

Change `f/` to `t/` to make the tech portfolio the default landing page.

---

## CV Files

`cv-en.pdf` and `cv-pt.pdf` live in the repo root. Both portfolio index files reference them with a relative path going up one level:

```js
const CV_URLS = {
  en: '../cv-en.pdf',
  pt: '../cv-pt.pdf',
};
```

The CV button `href` should also match:

```html
<a href="../cv-en.pdf" ... id="cv-btn">CV</a>
```

---

## Design System

All pages share the same CSS design tokens defined in `:root`:

| Token    | Value     | Usage                         |
|----------|-----------|-------------------------------|
| `--bg`   | `#0a0a0f` | Page background               |
| `--bg2`  | `#10101a` | Card / panel background       |
| `--bg3`  | `#16162a` | Input / tab background        |
| `--a1`   | `#5cf0b0` | Primary accent (mint green)   |
| `--a3`   | `#6eb5ff` | Secondary accent (sky blue)   |
| `--a5`   | `#ffb347` | Tertiary accent (amber)       |
| `--mono` | DM Mono   | Monospace font (labels, code) |
| `--sans` | Syne      | Display font (headings, body) |

---

## How to Add a New Project

### Step 1 — Create the project page

Copy an existing project page as a starting point:

```bash
cp f/projects-t/brazilian-inflation-prediction.html f/projects-t/your-project-slug.html
```

Then edit the `<title>`, eyebrow tags, title, description, and chart/data logic.

### Step 2 — Add a card on the homepage

Open `f/index.html` (or `t/index.html`) and add a new card in the projects grid:

```html
<a href="projects-t/your-project-slug.html" class="project-card" style="--card-accent:#6eb5ff;">
  <div class="card__tag-row">
    <span class="card__tag card__tag--accent">Your Category</span>
    <span class="card__tag">Another Tag</span>
  </div>
  <h3 class="card__title">Your Project Title</h3>
  <p class="card__desc">
    One or two sentences describing what the project does and why it matters.
  </p>
  <div class="card__footer">
    <div class="card__tech">
      <span class="card__tech-item">Python</span>
    </div>
    <span class="card__arrow">↗</span>
  </div>
</a>
```

**Accent colour suggestions:**

| Colour   | Hex       | Suggested use     |
|----------|-----------|-------------------|
| Mint     | `#5cf0b0` | ML / Forecasting  |
| Sky blue | `#6eb5ff` | Quant Finance     |
| Violet   | `#c97bff` | NLP / Text        |
| Amber    | `#ffb347` | Data Engineering  |
| Coral    | `#ff6b6b` | Risk / Macro      |
| Pink     | `#f06fff` | Deep Learning     |

---

## Deployment

The site is entirely static — no build step needed. It is deployed via **GitHub Pages**:

- Repo: `darosnakai/portfolio`
- Branch: `main`
- Custom domain: `darosnakai.com` (configured via `CNAME`)

To deploy changes, commit and push to `main`:

```bash
git add .
git commit -m "your message"
git push origin main
```

GitHub Pages will rebuild automatically within ~1 minute.
