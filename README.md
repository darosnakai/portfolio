# Daros Nakai — Portfolio Website

A clean, modern dark-theme personal portfolio built in pure HTML, CSS, and JavaScript. No frameworks or build tools required — just open `index.html` in a browser.

---

## File Structure

```
portfolio/
├── index.html                          ← Homepage (hero + projects grid + about)
├── README.md                           ← This file
└── projects/
    ├── brazilian-inflation-prediction.html   ← Project 1
    └── (your-next-project.html)              ← Add future projects here
```

---

## Design System

All pages share the same CSS design tokens defined in `:root`. The key values are:

| Token         | Value       | Usage                        |
|---------------|-------------|------------------------------|
| `--bg`        | `#0a0a0f`   | Page background              |
| `--bg2`       | `#10101a`   | Card / panel background      |
| `--bg3`       | `#16162a`   | Input / tab background       |
| `--a1`        | `#5cf0b0`   | Primary accent (mint green)  |
| `--a3`        | `#6eb5ff`   | Secondary accent (sky blue)  |
| `--mono`      | DM Mono     | Monospace font (labels, code)|
| `--sans`      | Syne        | Display font (headings, body)|

---

## How to Add a New Project

### Step 1 — Create the project page

Copy the existing project page as a starting point:

```bash
cp projects/brazilian-inflation-prediction.html projects/your-project-slug.html
```

Then edit:
- `<title>` — update to your project name
- `.header__eyebrow` — category tags (e.g. "Deep Learning · Finance")
- `.header__title` — project title
- `.header__desc` — short description
- The methodology / about section
- The JavaScript data-loading and chart logic

The nav bar (`../index.html` links) works automatically for any file inside `projects/`.

### Step 2 — Add a card on the homepage

Open `index.html` and find the comment:

```html
<!-- ══ PLACEHOLDER — add future projects below this comment ══ -->
```

Copy the existing project card block and update:

```html
<a href="projects/your-project-slug.html" class="project-card" style="--card-accent: #6eb5ff;">
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
      <span class="card__tech-item">Your Stack</span>
    </div>
    <span class="card__arrow">↗</span>
  </div>
</a>
```

**Accent colour suggestions** (pick one per project to keep visual variety):

| Colour    | Hex       | Suggested use          |
|-----------|-----------|------------------------|
| Mint      | `#5cf0b0` | ML / Forecasting       |
| Sky blue  | `#6eb5ff` | Quant Finance          |
| Violet    | `#c97bff` | NLP / Text             |
| Amber     | `#ffb347` | Data Engineering       |
| Coral     | `#ff6b6b` | Risk / Macro           |
| Pink      | `#f06fff` | Deep Learning          |

### Step 3 — Remove the "Coming Soon" placeholder (optional)

When you have at least two real projects, delete or hide the placeholder card:

```html
<!-- Delete this entire block when no longer needed -->
<div class="project-card project-card--soon" ...>
  ...
</div>
```

---

## Deployment

The site is entirely static — no server or build step needed. You can host it on:

- **GitHub Pages** — push to a repo, enable Pages in Settings → Pages → Deploy from branch
- **Netlify** — drag and drop the `portfolio/` folder at [netlify.com/drop](https://netlify.com/drop)
- **Vercel** — `vercel --prod` from the `portfolio/` directory

> **Note:** The Brazilian Inflation Prediction project page fetches data from a GitHub raw URL (`DATA_URL` in the script). Make sure the JSON file is publicly accessible at that path before deploying.
