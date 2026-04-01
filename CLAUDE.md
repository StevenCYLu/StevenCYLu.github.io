# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Academic personal website for Chen-yi Lu (PhD student, Purdue University) built with Jekyll and the [Minimal Light](https://github.com/yaoyao-liu/minimal-light) remote theme. Hosted on GitHub Pages.

## Build & Development

```bash
bundle install              # Install dependencies
bundle exec jekyll serve    # Local dev server at http://localhost:4000
```

Requires Ruby and Bundler. The `webrick` gem is included for Ruby 3+ compatibility.

## Architecture

**Theme:** Uses `remote_theme: yaoyao-liu/minimal-light` — the theme's layouts, includes, and Sass are fetched remotely. Local files override the remote theme when present.

**Content flow:**
- `index.md` (front matter: `layout: homepage`) → rendered inside `_layouts/homepage.html`
- Publications are included via `{% include_relative _includes/publications.md %}` — this is **manually written HTML**, not auto-generated from `_data/publications.yml`
- `_data/publications.yml` exists as structured data but is not currently used by the template

**Key content files to edit:**
- `index.md` — About Me bio
- `_includes/publications.md` — Publication list (raw HTML with image teasers, links, badges)
- `_includes/services.md` — Service/reviewing section (currently empty)
- `_config.yml` — Personal info, social links, site settings (title, affiliation, email, avatar, Google Scholar, GitHub, LinkedIn)

**Styling:**
- `_sass/minimal-light.scss` — Main stylesheet (596 lines), includes dark mode via `@media (prefers-color-scheme: dark)`
- `assets/css/publications.css` — Publication card styles
- Font choice configured in `_config.yml` (`font: "Serif"` or `"Sans Serif"`)
- Two-column layout: 232px fixed left sidebar (header) + 650px content area, collapses to single column at 480px

**Assets:**
- `assets/img/` — Avatar, favicons (light/dark), publication teaser images
- `assets/files/` — CV PDF
- `assets/js/` — Favicon dark-mode switcher, mobile viewport scaling

**`html_source_file/`** — Pre-compiled static HTML version for non-Jekyll deployment. Excluded from Jekyll build via `_config.yml`.

## Adding a Publication

1. Add teaser image to `assets/img/`
2. Add the HTML entry to `_includes/publications.md` following the existing pattern (Bootstrap-style grid: 3-col image + 9-col text)
3. Optionally add structured data to `_data/publications.yml`

## Deployment

Push to `main` branch — GitHub Pages builds and deploys automatically. No CI config needed; GitHub Pages handles Jekyll builds natively.
