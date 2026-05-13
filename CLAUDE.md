# CLAUDE.md — AI Assistant Guide for aksaeri.com

## Project Overview

**Site:** https://aksaeri.com/ (also https://www.aksaeri.com/)
**Framework:** Astro 5 (static site generation)
**Hosting:** Vercel (auto-deploys from `main`)
**DNS:** Cloudflare proxied → Vercel
**Purpose:** Personal academic site for Alexander K. Saeri — AI governance, behavioural science, AI safety research.

The site was migrated from Hugo/Wowchemy to Astro in November 2025 (PRs #1–#3). The previous Hugo build is preserved in `hugo-backup/` for reference.

## Repository Structure

```
site-aksaeri-com/
├── astro.config.mjs       # Astro config (site URL, integrations)
├── vercel.json            # Vercel framework + URL redirects
├── package.json           # Astro 5, @astrojs/mdx, @astrojs/sitemap
├── src/
│   ├── assets/                  # Optimised images (imported into pages)
│   │   ├── avatar.jpg
│   │   ├── og-preview.png
│   │   └── projects/            # Per-project images
│   ├── layouts/
│   │   └── BaseLayout.astro     # Shared <head>, nav, footer, global CSS
│   └── pages/
│       ├── index.astro          # Home (/)
│       └── other-projects.astro # /other-projects
├── public/                # Static assets served as-is at literal path
│   ├── favicon.ico              # → /favicon.ico
│   └── uploads/                 # Static files (e.g. resume.pdf)
├── BACKLOG.md             # Tracked TODOs (e.g. image replacements)
└── hugo-backup/           # Archived Hugo site (do not edit)
```

## Tech Stack

- **Astro 5.0** — static site generator. Routes are files under `src/pages/`. `.astro` files mix component frontmatter (JS/TS) with HTML-like templates.
- **Integrations:** `@astrojs/mdx` (Markdown + JSX), `@astrojs/sitemap` (auto `/sitemap-index.xml`).
- **Styling:** plain `<style is:global>` blocks in `BaseLayout.astro`. No Tailwind, no CSS framework.
- **Output:** `output: 'static'` — pre-rendered HTML in `dist/`.

## Commands

```bash
npm install        # First time / after pulling
npm run dev        # Local dev server (http://localhost:4321)
npm run build      # Production build → dist/
npm run preview    # Serve the built site locally
```

## How Astro Decides vs How We Decide

**Astro decides:**
- Routing: every file in `src/pages/` becomes a route at its path. `src/pages/about.astro` → `/about`. No router config.
- Build pipeline: bundling, minification, asset hashing for imported assets.
- `<head>` injection of generated assets (when components or pages import CSS/JS).
- The `public/` vs `src/` distinction (see below).

**We decide:**
- Page content and layout (`src/pages/*.astro`, `src/layouts/BaseLayout.astro`).
- All visual styling — CSS lives inline in `.astro` files. There is no theme to swap; the look-and-feel is hand-rolled in `BaseLayout.astro`.
- Redirects and rewrites (in `vercel.json`).
- Whether images go in `public/` (served as-is) or `src/assets/` (optimised by Astro's `<Image>` component).

## Public vs src/assets

| Location | When to use | URL |
|---|---|---|
| `src/assets/foo.png` | Content images. Imported into a page/component and rendered with `<Image>` from `astro:assets`. Astro resizes, format-converts, hashes, and lazy-loads them. **Default.** | Hashed URL generated at build time. |
| `public/foo.png` | Files that must live at a fixed URL — `favicon.ico`, `robots.txt`, PDF downloads, OG images referenced from external services. | `/foo.png` (literal). |

The site currently uses `src/assets/` for content images and `public/` only for `favicon.ico` and `uploads/resume.pdf`.

### Adding an image

```astro
---
import { Image } from 'astro:assets';
import myImage from '../assets/projects/my-project.jpg';
---
<Image src={myImage} alt="…" widths={[400, 800]} sizes="(max-width: 600px) 100vw, 800px" />
```

The `widths` array tells Astro which sizes to generate; `sizes` tells the browser which one to pick. Astro converts to WebP/AVIF and serves a `<picture>` with the right `srcset` automatically.

## URL Redirects

Edit `vercel.json` — already has `/meet`, `/cv`, `/intro`, `/opportunities`, `/eoi` → Google links.

## Deployment

Push to `main` → Vercel rebuilds and deploys automatically. Preview deployments are generated for any branch.

The Vercel project is `site-aksaeri-com.vercel.app`; the primary domain `aksaeri.com` is proxied through Cloudflare.

## Conventions

- Internal links use absolute paths: `<a href="/other-projects">`.
- Hash anchors target IDs on the page: `<a href="#contact">` → element with `id="contact"`.
- External links open in the same tab unless there's a reason otherwise.
- Images use `<Image>` from `astro:assets` with files imported from `src/assets/`.
- Two pages exist (`index.astro`, `other-projects.astro`). Any new page is a new file under `src/pages/`.

## Things to Avoid

- Editing `hugo-backup/` — it's an archive, not a live site.
- Hardcoding the absolute domain in links — use relative paths so previews work.
- Adding a CSS framework without first deciding it's worth the complexity; the current site is intentionally lightweight.

## Useful Resources

- Astro docs: https://docs.astro.build/
- Astro Image component: https://docs.astro.build/en/guides/images/
- Vercel project: https://vercel.com/aksaeri/site-aksaeri-com (auth required)
