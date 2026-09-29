# justabdullah.com

stylized <small>just</small>Abdullah<small>.com</small>

Personal site and blog for Abdullah — PhD Researcher at Memorial University of Newfoundland. Built with [Hugo](https://gohugo.io) (no external theme — everything under `layouts/` is custom) and deployed to [Cloudflare Pages](https://pages.cloudflare.com/) from this private repo.

## Requirements

- Hugo **extended** v0.140+ (site was built/tested against v0.166.0)
- No Node/npm build step required — CSS is plain and processed via Hugo Pipes

## Local development

```bash
hugo server -D
```

Serves at `http://localhost:1313/` with drafts enabled and live reload.

## Creating content

New blog post:

```bash
hugo new posts/my-post-slug.md
```

This uses the `archetypes/posts.md` template, which pre-fills `date`, `categories`, `tags`, `images`, and `description` front matter. Fill those in — they drive the SEO meta tags, Open Graph/Twitter cards, and JSON-LD.

Front matter reference for posts:

```yaml
title: "Post title"
date: 2026-09-27T09:00:00-02:30
lastmod: 2026-09-27T09:00:00-02:30
draft: false
description: "One or two sentences used as the meta description / OG description."
summary: "Shown on post cards; falls back to auto summary if omitted."
categories: ["Research"]      # one primary category
tags: ["Synthetic Data"]      # as many as apply
images: ["images/og-default.svg"]  # replace with a real 1200x630 image per post if you have one
toc: true                     # set true to render a table of contents
```

Other content:

- `content/about.md` — About page (edit this to update bio/CV-style info)
- `content/_index.md` — landing page copy (front matter only; layout is `layouts/index.html`)
- `content/posts/_index.md` — blog index page, pinned to `/blog/` via `url:` front matter

## Site structure

```
hugo.toml              site config: SEO defaults, taxonomies, menus, params
archetypes/             front matter templates for `hugo new`
content/
  _index.md             landing page
  about.md              about page
  posts/                blog posts (section = "posts", URL = /blog/:filename/)
layouts/
  _default/             baseof, single, list, taxonomy, term
  posts/                blog-specific single/list templates (reading time, TOC, tags)
  partials/
    head.html            <head>, stylesheet, favicon, RSS link
    seo.html              meta description/robots, Open Graph, Twitter Cards, JSON-LD
    header.html / footer.html
    post-card.html
  robots.txt            custom robots.txt with sitemap reference
  404.html
assets/css/main.css     plain CSS (light mode only), CSS custom properties for theming
static/
  _headers              Cloudflare Pages security + cache headers
  favicon.svg
  images/og-default.svg fallback social share image — replace with a real PNG/JPG
```

## SEO features

- Per-page meta description, keywords, robots tags (`noindex` supported via front matter)
- Open Graph + Twitter Card tags (article vs website type, published/modified time, section, tags)
- JSON-LD structured data: `WebSite`/`Person` on the homepage, `BlogPosting` on posts, `WebPage` elsewhere
- Canonical URLs on every page
- `categories` and `tags` taxonomies with dedicated archive pages and RSS per term
- Sitemap (`/sitemap.xml`), RSS feeds (site-wide and per-section/taxonomy), `robots.txt`
- Reading time + breadcrumbs + optional table of contents on posts

## Design

No design tooling/build step — everything lives in [assets/css/main.css](assets/css/main.css) as plain CSS custom properties (`:root` in that file is the source of truth; the table below just documents it).

**Palette**

| Token | Value | Usage |
|---|---|---|
| `--color-accent` | `#004aad` (blue) | links, primary buttons, blockquote rule, skip-link |
| `--color-accent-secondary` | `#e2ae12` (gold) | eyebrow/kicker labels, tag-pill hover border |
| `--color-bg` | `#ffffff` | page background |
| `--color-bg-alt` | `#f6f7f9` | card/section backgrounds (post cards, pill list, TOC) |
| `--color-text` | `#1a1d23` | body copy |
| `--color-text-muted` | `#5c6470` | meta text, summaries, captions |
| `--color-border` | `#e4e7eb` | hairlines, card borders |

Light mode only, by design — `html { color-scheme: light; }` and there is no `prefers-color-scheme: dark` block. Don't reintroduce one without being asked.

**Typography**

- `--font-sans`: `"Avenir Next", Avenir, "Segoe UI", -apple-system, BlinkMacSystemFont, Roboto, Helvetica, Arial, sans-serif` — used for all UI and copy.
- `--font-mono`: system monospace stack — used for inline `code` and fenced code blocks.
- Avenir is a commercial Apple/Linotype font, not bundled with this repo. It renders natively on macOS/iOS and falls back to system sans-serif elsewhere. To force real Avenir on all platforms, license and self-host it (e.g. Adobe Fonts) and add `@font-face` rules — do not source Avenir font files from the web without a license.

**Layout & components**

- `--max-width: 780px` — single centered reading column (`.container`), no sidebar.
- `--radius: 10px` — shared corner radius for buttons, cards, pills, TOC box.
- Components (all in `main.css`, no CSS framework): `.btn` (`.btn-primary` filled blue / `.btn-ghost` outlined), `.post-card`, `.tag-pill` / `.category-pills`, `.pill-list` (research interests), `.toc`, `.breadcrumbs`, `.pagination` (styled Hugo `_internal/pagination.html` output).
- Code blocks (`.prose pre`) are intentionally always dark (`#1e1f26` background) regardless of the light-only site theme — this is a deliberate contrast choice, not a leftover from dark mode.
- Responsive breakpoint: single `@media (min-width: 640px)` bump for hero heading size; layout is mobile-first and single-column throughout (no multi-column grid at any width).

Before going live, update in `hugo.toml`:

- `baseURL` if the domain changes
- `params.social.*` (GitHub, LinkedIn, Google Scholar, ORCID, email)
- `params.authorTwitter` and `services.googleAnalytics.ID` / `params.plausibleDomain` if you want analytics
- Replace `static/images/og-default.svg` with a real raster image (SVG isn't reliably rendered by Twitter/Facebook crawlers for `og:image`)

## Deploying to Cloudflare Pages

This repo is private, so connect it via the Cloudflare dashboard (Workers & Pages → Create → Pages → Connect to Git) rather than a public webhook:

| Setting | Value |
|---|---|
| Build command | `hugo --minify` |
| Build output directory | `public` |
| Environment variable | `HUGO_VERSION=0.166.0` |

`static/_headers` is copied into `public/` automatically and sets security headers (CSP, HSTS, X-Frame-Options, etc.) plus long-lived caching for `css/` and `images/`.

## Language Instructions

1. Subject + verb + object/complement is the default structure.
2. Use parallel structures for direct contrasts.
3. Prefer "A, not B" over "not A, but rather B".
4. Use punctuation when it can replace an explicit connector.
5. Use em dashes sparingly.
6. Maximum 24 words per sentence.
7. Prefer two short sentences over one complex sentence.
8. Do not explain relationships the reader can infer.
9. Prefer verbs over nominalizations.
10. Avoid stacks of abstract nouns.
11. Use precise, familiar vocabulary.
12. Avoid unnecessarily advanced words.
13. Avoid excessive transition words.
14. Avoid symmetrical "AI" constructions.
15. Keep technical terms when they carry necessary meaning.
16. Do not simplify technical ideas merely to make them easier.
17. Let sentence structure carry some of the reasoning.

## Notes

- No theme is installed as a Hugo Module or git submodule — this avoids extra auth/config for Cloudflare Pages builds against a private repo.
- `public/` and Hugo's `resources/_gen` cache are git-ignored; only source files are committed.
- Bio/research content originally sourced here now lives in [content/about.md](content/about.md) and [content/posts/welcome-to-just-abdullah.md](content/posts/welcome-to-just-abdullah.md).
