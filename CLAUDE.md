# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## Overview

Pure static site — no build system, no package manager, no bundler. All dependencies are loaded from CDN. To preview locally, open any `.html` file directly in a browser or serve the folder with any static server:

```bash
# Python (from PersonalWebsite/)
python -m http.server 8080

# Node
npx serve .
```

---

## Architecture

### Two coexisting design systems

**Homepage** (`index.html`):
- Based on Start Bootstrap Grayscale v7.0.6
- Uses `css/styles.css` and `js/scripts.js`
- Bootstrap 5.2.3 via CDN; FontAwesome 6.3.0 via CDN
- Dark hero + light projects section layout

**Blog index + blog posts** (`Blogs.html`, `BlogPosts/*.html`):
- Custom dark design (purple gradient, `#0f0f0f` background)
- Blog posts link to `../css/stylesblog.css` (shared post layout)
- Bootstrap 5.3.0 via CDN; Inter font; inline CSS for page-specific styles
- `Blogs.html` is a **manually maintained** HTML file — there is no CMS or generator. Adding a new blog post requires updating the grid in `Blogs.html` and creating the post file in `BlogPosts/`.

### Special pages

| Page | Purpose |
|------|---------|
| `Fix.html` | Placeholder "Pipeline Under Maintenance" — intended future home for BIST hourly data table |
| `SMGrafana.html` | Embeds a Grafana snapshot via `<iframe>` |
| `RealUserAgent/RealUserAgent.html` | DataTables viewer that reads `RealUserAgent/FingerPrintAuth.csv` via PapaParse |

### Blog posts

- Published posts: `BlogPosts/*.html`
- Draft / todo posts: `BlogPosts/To-do's/` — unfinished, not linked from `Blogs.html`
- All published posts use `../css/stylesblog.css` for styling

---

## Adding a new blog post

1. Create `BlogPosts/<PostName>.html` — link `../css/stylesblog.css` in `<head>`
2. Add the card in `Blogs.html` inside `#blogGrid`, following the existing `.blog-item` pattern with `data-category` set to one of: `business`, `sales`, `marketing`, `philosophy`, `psychology`, `productivity`
3. Add the corresponding image to `assets/img/`
