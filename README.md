# Bridge Public Schools Website

A Hugo-based, fully bilingual (English/Spanish) website for Bridge Public Schools, deployed via GitHub Pages to [bridgepublicschools.org](https://bridgepublicschools.org).

## Quick reference: where things live

If you're here to update the site, this is the short version:

| I want to change... | Look in... |
|---|---|
| **Most page text** (headlines, buttons, section copy, FAQs) | `i18n/en.toml` (English) and `i18n/es.toml` (Spanish) |
| **News posts** and long-form page prose | `content/` (Markdown files) |
| **Logos and images** | `static/assets/` and `static/images/` |
| **Colors, fonts, spacing** (the overall look) | `static/assets/site.css` |
| **Page structure / design** (how a page is laid out) | `layouts/` |
| **Navigation menus** | `config/_default/menus/` |
| **Site-wide settings** | `config/_default/` |

> **Important:** because the site is bilingual, most text appears **twice** — once in English and once in Spanish. When you change a piece of text, update **both** language versions so the two stay in sync (the English file and its Spanish counterpart, e.g. `en.toml` / `es.toml`, or `mission.md` / `mission.es.md`).

## Where the website's text lives

Text is split across two places:

1. **`i18n/` — most of the visible text.** Headlines, buttons, section copy, the FAQ, the footer, and so on live in `i18n/en.toml` (English) and `i18n/es.toml` (Spanish). The two files mirror each other: each entry has a matching one in the other language. To change a headline, find its entry in **both** files and edit the text after `other =`.

2. **`content/` — news posts and page prose.** Longer written content is stored as Markdown. Spanish versions use a `.es.md` extension alongside the English `.md`:

   ```
   content/
   ├── _index.md / _index.es.md          Homepage metadata
   ├── about/
   │   ├── mission.md / .es.md           About page
   │   ├── educational-model.md / .es.md Educational Model page
   │   └── board.md / .es.md             Board of Directors page
   ├── contact.md / .es.md               Contact page
   ├── thanks.md / .es.md                Post-form "thank you" page
   └── news/
       ├── _index.md / .es.md            News section
       └── welcome-post.md / .es.md      A news post
   ```

## Logos and images

- `static/assets/` — site logos and the main stylesheet (`bison.png`, `logo-transparent.png`, `site.css`).
- `static/images/`, `static/logos/`, `static/icons/` — other image assets.

Anything in `static/` is copied to the site as-is. To reference an image in content or a layout, point to its path under `static/` (for example, `static/assets/bison.png` is available at `/assets/bison.png`).

## Page design and layout

The look and structure of each page is defined in `layouts/`. These are HTML templates that pull in text from `i18n/` and `content/`:

- `layouts/_default/baseof.html` — the shared shell (top bar, header, footer) used by every page.
- `layouts/index.html` — the homepage.
- `layouts/about/`, `layouts/_default/board.html`, `layouts/_default/model.html`, `layouts/_default/contact.html`, `layouts/news/`, `layouts/_default/thanks.html` — individual pages.
- `layouts/partials/` — reusable pieces shared across pages (e.g. the "join the interest list" call-to-action).

You usually only need to touch `layouts/` for design or structural changes. For wording, use `i18n/` or `content/` instead.

## Forms

The sign-up and contact forms submit through [Formspree](https://formspree.io). After submitting, visitors are redirected to the site's own thank-you page (`/thanks/`). The recipient email and submission limits are managed in the Formspree account, not in this repo.

## Local Development

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.142.0 or later)

### Running Locally

1. Clone the repository with submodules (the theme is a submodule):
   ```bash
   git clone --recurse-submodules https://github.com/tefirman/bridgeps.git
   cd bridgeps
   ```

2. Start the development server:
   ```bash
   hugo server
   ```

3. Open http://localhost:1313 in your browser. The Spanish site is at http://localhost:1313/es/.

### Adding a News Post

Create a new Markdown file in `content/news/` (and a `.es.md` companion for the Spanish version):

```bash
hugo new news/my-new-post.md
```

### Building for Production

```bash
hugo --gc --minify
```

The built site lands in the `public/` directory.

## Deployment

The site automatically deploys to GitHub Pages whenever changes are pushed to the `main` branch (via GitHub Actions). The production address is set by the custom domain in `static/CNAME`.

## Theme

This site is built on the [Hugo Clarity](https://github.com/chipzoller/hugo-clarity) theme (included as a Git submodule), with custom layouts and styling in `layouts/` and `static/assets/` that define the current design.
