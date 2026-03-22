# Asbrusn.art — Artist Portfolio Website Design Spec

## Overview

A portfolio website for Asbrusn.art, an illustrator specializing in drawings. The site showcases artwork in a visually polished, warm aesthetic while being easy for a non-technical artist to maintain. Built with Astro, deployed to GitHub Pages for free.

## Goals

1. **Showcase artwork** with a professional, gallery-quality presentation
2. **Zero-cost** — free hosting on GitHub Pages, no paid services
3. **Easy maintenance** — artist updates by dropping images into folders and pushing via GitHub Desktop
4. **Fast performance** — automatic image optimization for an image-heavy site
5. **Polished aesthetic** — warm, organic, handcrafted feel that complements illustration work

## Pages

### Home (`/`)
- Hero section with featured artwork (large, impactful)
- Brief artist introduction (2-3 sentences)
- "View Portfolio" call-to-action
- Subtle scroll indicator

### Portfolio (`/portfolio`)
- Category filter tabs at top (e.g., "All", "Portraits", "Nature", "Fantasy")
- Masonry grid layout via CSS `columns`
- Clicking artwork opens a lightbox with full-size image + title
- Lazy loading with blur-up placeholders
- Smooth filter transitions

### About (`/about`)
- Artist photo
- Bio / artist statement
- Skills and background info

### Contact (`/contact`)
- Email address
- Social media links (Instagram, etc.)
- Optional: commission information

## Tech Stack

| Layer | Choice | Rationale |
|-------|--------|-----------|
| Framework | Astro | Zero JS by default, built-in image optimization, static output |
| CSS | Vanilla CSS with custom properties | Full control over design polish, no framework overhead |
| Image optimization | Astro `<Image>` + sharp | Auto WebP/AVIF, multiple sizes, blur placeholders at build time |
| Masonry layout | CSS `columns` | No JS needed, performant, good browser support |
| Lightbox | Vanilla JS (~50 lines) | Minimal, no dependency needed |
| Hosting | GitHub Pages | Free, reliable, custom domain support |
| CI/CD | GitHub Actions | Auto-build and deploy on push |
| Fonts | Google Fonts (Cormorant Garamond + Inter) | Free, fast CDN delivery |

## Design System

### Color Palette — Warm Ivory

| Token | Hex | Usage |
|-------|-----|-------|
| `--bg` | `#faf7f2` | Page background |
| `--surface` | `#f0ebe3` | Cards, hover states, sections |
| `--text-primary` | `#2c2420` | Headings, body text |
| `--text-secondary` | `#9e8d7b` | Captions, metadata, nav links |
| `--accent` | `#b8956a` | Active filter tabs, links, hover highlights |
| `--divider` | `#e8e0d4` | Borders, separators |

### Typography

- **Headings:** Cormorant Garamond (serif) — elegant, gallery-like
- **Body:** Inter (sans-serif) — clean, highly readable
- **Brand "Asbrusn.art":** Cormorant Garamond, wide letter-spacing, uppercase

### Interactions

- **Gallery hover:** Gentle scale (1.02) + subtle shadow elevation
- **Filter tabs:** Active tab highlighted with accent underline, smooth content transitions
- **Lightbox:** Fade in/out, click outside or press Escape to close, keyboard arrow navigation
- **Page transitions:** Subtle fade between pages (Astro view transitions)

## Content Architecture

### Artwork folder structure:
```
src/content/artwork/
├── portraits/
│   ├── piece-name.jpg
│   └── ...
├── nature/
│   └── ...
└── fantasy/
    └── ...
```

- Each subdirectory = a category filter tab on the portfolio page
- Category names are derived from folder names (capitalized)
- Images are auto-discovered at build time via `Astro.glob()` or content collections
- No metadata file required — images just work when dropped in

### Optional metadata (artwork.json per folder):
```json
[
  { "file": "piece-name.jpg", "title": "Girl with Flowers", "year": "2025" }
]
```
If no metadata exists, the filename (cleaned up) is used as the title.

## Artist Maintenance Workflow

1. Artist opens the project folder on her computer
2. Drops new artwork images into the appropriate category folder (e.g., `src/content/artwork/portraits/`)
3. Opens GitHub Desktop, sees the new files
4. Clicks "Commit" then "Push"
5. GitHub Actions auto-builds with image optimization and deploys to GitHub Pages
6. Site is live with new artwork in ~2 minutes

## Image Optimization Pipeline

All handled automatically by Astro at build time:
- Source images converted to WebP (+ AVIF where supported)
- Multiple sizes generated: thumbnail (400w), medium (800w), full (1600w)
- Low-quality blur placeholder (LQIP) generated for each image
- `<picture>` elements with `srcset` for responsive loading
- Native `loading="lazy"` on all gallery images

## Responsive Design

- **Desktop:** 3-4 column masonry grid, full navigation
- **Tablet:** 2-3 column grid, navigation adapts
- **Mobile:** 1-2 column grid, hamburger menu
- Mobile-first CSS approach
- Touch-friendly lightbox with swipe gestures

## File Structure

```
gre-website/
├── src/
│   ├── components/
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   ├── MasonryGrid.astro
│   │   ├── FilterTabs.astro
│   │   ├── Lightbox.astro
│   │   ├── ArtworkCard.astro
│   │   └── HeroSection.astro
│   ├── layouts/
│   │   └── BaseLayout.astro
│   ├── pages/
│   │   ├── index.astro
│   │   ├── portfolio.astro
│   │   ├── about.astro
│   │   └── contact.astro
│   ├── styles/
│   │   ├── global.css          (reset, tokens, base styles)
│   │   └── components.css      (component-specific styles)
│   └── content/
│       └── artwork/
│           ├── portraits/
│           ├── nature/
│           └── fantasy/
├── public/
│   └── fonts/                   (if self-hosting)
├── astro.config.mjs
├── package.json
└── .github/
    └── workflows/
        └── deploy.yml           (GitHub Actions auto-deploy)
```
