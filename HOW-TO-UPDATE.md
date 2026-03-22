# How to Update Your Website

Hi! This guide explains how to add new artwork, edit info, and keep your site up to date. You don't need to know how to code — just follow these steps.

---

## What You Need

- **GitHub Desktop** (free app) — [download here](https://desktop.github.com/)
- A file explorer (Finder on Mac, File Explorer on Windows)
- Your artwork images (`.jpg`, `.jpeg`, `.png`, or `.webp`)

---

## Adding New Artwork

### Step 1: Find the artwork folder

Open the project folder on your computer and navigate to:

```
src/content/artwork/
```

Inside you'll see category folders:

```
artwork/
├── drawings-and-paintings/  ← pencil, watercolor, digital art
├── crafts/        ← clay, handmade, physical pieces
└── photos/        ← photography
```

### Step 2: Drop your image in

Drag your image file into the right category folder. For example:

- A new watercolor painting → drop it into `drawings-and-paintings/`
- A photo of a clay sculpture → drop it into `crafts/`
- A photograph you took → drop it into `photos/`

**Naming tips:**

- Use lowercase with dashes: `sunset-over-sea.jpg` (not `Sunset Over Sea.jpg`)
- The filename becomes the title on the site: `sunset-over-sea.jpg` → "Sunset Over Sea"
- Avoid spaces and special characters in filenames

### Step 3: (Optional) Add details about the piece

When someone clicks on an artwork, a detail view opens showing the image alongside a caption with all the info you provide. To add this info, edit the `artwork.json` file inside the category folder. If one doesn't exist yet, create it.

Example `artwork.json`:

```json
[
  {
    "file": "sunset-over-sea.jpg",
    "title": "Sunset Over the Sea",
    "materials": "Watercolor on cold-pressed paper",
    "theme": "Landscape, Nature",
    "year": "2025",
    "description": "A warm sunset reflected on calm waters."
  }
]
```

Here's what each field does:

| Field           | What it shows                                                         | Required? |
| --------------- | --------------------------------------------------------------------- | --------- |
| `"file"`        | Must match the image filename exactly                                 | Yes       |
| `"title"`       | The artwork name (shown as the heading in the detail view)            | No\*      |
| `"materials"`   | Media/tools used, e.g. "Colored pencil on paper" (shown with icon)    | No        |
| `"theme"`       | Comma-separated tags, e.g. "Fantasy, Portrait" (shown as pill badges) | No        |
| `"year"`        | Year created (shown next to the title)                                | No        |
| `"description"` | A short caption about the piece (shown as body text)                  | No        |

\*If no title is provided, the filename is used (e.g. `sunset-over-sea.jpg` → "Sunset Over Sea")

**Important:**

- The `"file"` must match your image filename exactly (including `.jpg` / `.png` etc.)
- All fields except `"file"` are optional — skip any you don't need
- Make sure to put a comma between entries (but NOT after the last one)
- `"theme"` supports multiple values separated by commas — each one becomes its own tag
- If you don't create an `artwork.json` at all, the site still works — it just uses the filename as the title and the detail view won't show extra info

### Step 4: Publish your changes

1. Open **GitHub Desktop**
2. You'll see your new files listed as changes
3. Type a short message in the "Summary" box (e.g., "Added new watercolor")
4. Click **"Commit to main"**
5. Click **"Push origin"**
6. Wait ~2 minutes — the site rebuilds automatically!

---

## Creating a New Category

Just create a new folder inside `src/content/artwork/`. For example:

```
src/content/artwork/digital/
```

Drop images in, and a new filter tab ("Digital") will appear on the portfolio page automatically. No code changes needed.

---

## Removing Artwork

Simply delete the image file from its folder. If there's an entry for it in `artwork.json`, remove that entry too.

---

## Editing the About Page Text

Open `src/pages/about.astro` in any text editor. Look for the text between `<p>` tags and change it. Don't touch anything else in the file.

---

## Changing the About Page Photo

Replace the file at `src/assets/artist-photo.jpg` with your new photo (keep the same filename).

For the flip card back image, replace `src/assets/artist-photo-2.jpg`.

---

## Quick Reference

| I want to...          | Do this                                              |
| --------------------- | ---------------------------------------------------- |
| Add artwork           | Drop image in `src/content/artwork/<category>/`      |
| Add artwork details   | Edit or create `artwork.json` in the category folder |
| Create a new category | Create a new folder in `src/content/artwork/`        |
| Remove artwork        | Delete the image file (and its `artwork.json` entry) |
| Change about photo    | Replace `src/assets/artist-photo.jpg`                |
| Publish changes       | Commit & push in GitHub Desktop                      |

---

## Troubleshooting

**"My new artwork isn't showing"**

- Make sure you pushed the changes (not just committed)
- Wait 2-3 minutes for the site to rebuild
- Check that the image is in the right folder and has a supported extension (`.jpg`, `.png`, `.webp`)

**"The artwork.json isn't working"**

- Make sure it's valid JSON (no trailing commas, all quotes are `"double quotes"`)
- The `"file"` field must match the image filename exactly, including the extension
- You can validate your JSON at [jsonlint.com](https://jsonlint.com)

**"I see an error on the site"**

- Don't panic! Check the Actions tab on GitHub — it will show what went wrong
- Usually it's a typo in `artwork.json`
- If stuck, ask Valentina for help :)
