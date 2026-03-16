# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

WeSeW — multi-page static site for a tailoring atelier in Kharkiv, Ukraine. Deployed to Cloudflare Pages.

## Tech Stack

- **Astro** (SSG) + **Tailwind CSS**
- Deploy target: **Cloudflare Pages**
- Language: Ukrainian (all UI content)

## Commands

```bash
npm run dev       # Local dev server
npm run build     # Production build (static output)
npm run preview   # Preview production build locally
```

## Architecture

Multi-page site with shared layout (Header + Footer).

Pages: `/` (Home), `/services`, `/services/<slug>`, `/contacts`

- All pages/components are Astro components (`.astro`) — zero client JS unless explicitly needed
- Shared layout: `src/layouts/` — header with nav + footer with contacts on every page
- Images must be in WebP format, optimized for performance
- Lighthouse target: 95+ across all categories

## SEO Requirements

- Semantic HTML5 elements (`<header>`, `<main>`, `<section>`, `<footer>`)
- Open Graph meta tags on every page
- JSON-LD structured data: `LocalBusiness` schema
- Ukrainian-language meta descriptions with keywords: ательє Харків, пошив одягу, весільні сукні, ремонт одягу

## Design Principles

- Light color scheme, mobile-first
- Minimal, fast-loading — no heavy frameworks or unnecessary JS
- CTA actions: phone call (`tel:+380963061920`) and Telegram (`https://t.me/+380963061920`)

## Image Generation

Service photos are generated via **Nano Banana 2 API** (skill: `kie-nano-banana-2`).

- **Style:** JSON-structured prompts for consistency (see `presets/wesew.json` in skill directory)
- **Resolution:** 1K (keeps files under 2MB)
- **Format:** PNG, aspect ratio 3:4 for people, 4:3 for products
- **Image-to-image:** Upload source to Google Drive → get public URL → pass as `--source`
- **Photo style:** Editorial fashion photography, soft studio lighting, light grey backdrop
- All service images live in `public/images/services/`

## Business Data

All contact info, services, and working hours are in README.md — use it as the single source of truth for content.
