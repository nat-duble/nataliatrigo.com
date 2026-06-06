# nataliatrigo.com — internal context for Claude

## How to think in this repo

Think like a **frontend designer first, frontend engineer second**. Every decision should start from how it looks and feels, not from how it's implemented. The implementation follows the design — not the other way around.

**As a designer:**
- This site has a strong, intentional aesthetic: minimal, typographic, sparse. Protect it. When adding or changing anything visual, ask whether it *fits the existing language* — weight, spacing, case, color. When in doubt, do less.
- Think in whitespace, hierarchy, and proportion. The site uses letter-spacing and text-transform to carry visual weight instead of size or decoration. Lean into that.
- The audience is literary — readers, editors, publishers. The site should feel like a well-designed book, not a portfolio template.
- Natalia's voice is bilingual (Spanish primary). Any UI text you write or suggest should follow that — Spanish first, English alongside or secondary.

**As an engineer:**
- Prefer Sass over inline styles. Put new styles in the most specific relevant `_sass/_*.scss` file.
- Keep the Sass modular — `_variables.scss` for any new tokens, layout in the right section file.
- No JavaScript unless truly necessary. This is a static site; keep it that way.
- Mobile is a real use case. Always think about how something looks at `600px` and below.
- Don't introduce new dependencies. Font Awesome is already available for icons. Google Fonts is already loaded.

---

## What this is

Personal literary website for **Natalia Trigo** — Mexican writer, professor, writing coach. The site is her public presence: bio, books, writing accompaniment services, events, contact. It is primarily in **Spanish**, with English translations alongside most sections. The aesthetic is spare, minimal, typographic.

## Stack

- **Jekyll** static site generator (Ruby 3.3.6 — see `.ruby-version`)
- **Sass** with `@use`/`@forward` (NOT the old `@import` — already migrated)
- **GitHub Pages** for hosting — deploying to `gh-pages` branch auto-publishes
- Git remote: `git@github.com:nat-duble/nataliatrigo.com.git`
- Gems: jekyll-paginate, jekyll-sitemap, jekyll-feed, jekyll-seo-tag

## Layout and structure

```
sidebar (aside.sidebar)        main column (.main-column)
  .site-header                   .content-wrapper
    site title                     page content
    nav menu
```

- **Default layout** (`_layouts/default.html`): two-column — fixed left sidebar with header/nav, scrollable right content area.
- **Home layout** (`_layouts/home.html`): extends default. The `.content-wrapper` is `height: 100vh; overflow: hidden` — image + text statement fit within the viewport without scrolling.
- **Page layout** (`_layouts/page.html`): standard content pages with `.page-content` wrapper (max-width 600px, centered).

## Navigation

Driven entirely by `_data/settings.yml` → `menu` array. To add/remove/rename menu items, edit that file. Current menu order:
1. Bio → `/bio`
2. Libros → `/books`
3. Acompañamientos → `/acompanamientos`
4. Eventos → `/events`
5. Contacto → `/contact`

## Pages

| File | URL | Status |
|------|-----|--------|
| `index.html` | `/` | Home — image + bilingual statement |
| `pages/bio.md` | `/bio` | Full bilingual bio (Spanish then English) |
| `pages/books.md` | `/books` | Book listings with covers — *El fin del verano* (Almadía 2026) + *Daughters of Latin America* anthology |
| `pages/acompanamientos.md` | `/acompanamientos` | **Empty — placeholder, no content yet** |
| `pages/events.md` | `/events` | **Empty — placeholder, no content yet** |
| `pages/contact.md` | `/contact` | Email link + dachshund photo |
| `pages/about.md` | — | Legacy, not in menu |
| `pages/resources.md` | — | Legacy from theme, not in menu |

## Design system

- **Font**: Hanken Grotesk (200, 300, 400, 500 weights) — used for everything including headings/display. Loaded from Google Fonts.
- **Color**: `$brand-color: black`. Email link color: `#b5451b` (rust/terracotta). Social envelope icon: `#f39c12`.
- **Style aesthetic**: minimal, lots of letter-spacing (`0.18em–0.22em`), text-transform uppercase for nav/labels, lightweight font weights (200–300). No decorative elements.
- **Breakpoints**: tablet `600px`, phone `480px`.

## Sass file map

```
_sass/
  _variables.scss       — fonts, colors, breakpoints
  _base.scss            — reset, body, typography, links, tables
  _header.scss          — sidebar header + nav (responsive: horizontal on mobile)
  _home.scss            — home layout, home-statement, pagination
  _page.scss            — page-content, book layout, bio-photo, dog-photo, contact link style
  _footer.scss          — footer
  _post.scss            — blog post styles (not actively used)
  _code.scss            — code block styles
  _social-icons.scss    — font-awesome social icons
  _-sections-dir.scss   — @forward barrel for all partials
assets/css/main.scss    — entry point, @use _-sections-dir
```

## Slash commands (skills)

| Command | What it does |
|---------|-------------|
| `/start` | Starts Jekyll dev server with livereload + incremental on port 4000 |
| `/stop` | Kills the Jekyll server process |
| `/save` | `git add -A` + auto-generates commit message + commits (no Co-Authored-By) |
| `/publish` | Pushes `gh-pages` branch to origin → triggers GitHub Pages rebuild (~1–2 min) |

## Things to know

- **The `_posts/` directory** contains sample posts from the original Millennial theme — they are not real content. Natalia does not actively use the blog feature.
- **`millennial.gemspec`** — the site was bootstrapped from the open-source Millennial Jekyll theme. It has been heavily customized.
- **`site.github.url`** is used in templates for asset paths — this resolves correctly on GitHub Pages.
- **Disqus and Google Analytics** are both disabled (`disqus: false`, `google-ID: ''` in `_data/settings.yml`).
- **Social icons**: only email (`info@nataliatrigo.com`) is listed in the social section of settings.
- **`CNAME`** file: contains the custom domain (`nataliatrigo.com`) for GitHub Pages.
- **The `/contact` page** has a dachshund photo (`dog.jpg`) styled with `grayscale(40%)`.
- **Book covers** are in `assets/img/` — `el-fin-del-verano.jpg` and `daughters-of-latin-america.jpg`.
