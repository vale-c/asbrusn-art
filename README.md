# Asbrusn.art

Portfolio website for Greta, a visual artist working across watercolor, colored pencil, and handmade crafts.

**Live at [asbrusn.art](https://asbrusn.art)**

## Tech

- [Astro](https://astro.build/) static site generator
- Vanilla CSS with custom properties
- Auto image optimization (WebP, responsive srcset)
- GitHub Pages + GitHub Actions for free hosting and auto-deploy

## For the Artist

See **[HOW-TO-UPDATE.md](HOW-TO-UPDATE.md)** for a step-by-step guide on adding artwork, updating content, and publishing changes. No coding required.

## Development

```bash
npm install
npm run dev      # local dev server at localhost:4321
npm run build    # production build to dist/
npm run preview  # preview the build locally
```

## How It Works

Artwork images live in `src/content/artwork/` organized by category folders. The site auto-discovers them at build time:

```
src/content/artwork/
  drawings-and-paintings/   -> "Drawings & Paintings" tab
  crafts/                   -> "Crafts" tab
  photos/                   -> "Photos" tab
```

Drop an image into a folder, push to GitHub, and it appears on the site in ~2 minutes. Optional `artwork.json` files in each folder provide rich metadata (title, materials, theme, year, description).

## Deploy

Automatic via GitHub Actions on every push to `main`. See `.github/workflows/deploy.yml`.
