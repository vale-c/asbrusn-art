# How to Update Your Website

> **TL;DR** Drop images into folders, commit, push. Done. Site updates in 2 minutes.

---

## The 3-Step Loop (this is all you really need)

**Every time you want to add new artwork, it's the same 3 steps:**

1. **Drop** your image into the right folder
2. **Commit** in GitHub Desktop (write anything in the summary, e.g. "new art")
3. **Push** (click "Push origin")

That's it. The site rebuilds automatically. Go make tea, come back, it's live.

---

## Where to Drop Images

Open the project folder and go to:

```
src/content/artwork/
```

Pick the right subfolder:

| Folder | What goes in it |
|--------|-----------------|
| `drawings-and-paintings/` | Watercolor, colored pencil, digital art |
| `crafts/` | Clay, handmade, physical pieces |
| `photos/` | Photography |

**Just drag and drop.** That's literally it.

### Naming your file

Use **lowercase** and **dashes** instead of spaces:

> `sunset-over-sea.jpg` (not `Sunset Over Sea.jpg`)

The filename becomes the title on the site automatically.

---

## (Optional) Adding Details to a Piece

This step is **totally optional**. Skip it if you just want the image to show up.

If you want a piece to have a title, description, materials, etc., edit the `artwork.json` file inside the category folder.

Here's a copy-paste template. Just change the values:

```json
[
  {
    "file": "your-image-filename.jpg",
    "title": "Your Title Here",
    "materials": "Watercolor on paper",
    "theme": "Fantasy, Portrait",
    "year": "2025",
    "description": "A short sentence about the piece."
  }
]
```

**What each field does:**

| Field | Where it shows up | Required? |
|-------|-------------------|-----------|
| `"file"` | Connects the info to the image. **Must match the filename exactly.** | YES |
| `"title"` | Big heading in the detail view | no |
| `"materials"` | Small text with palette icon | no |
| `"theme"` | Colorful tag pills (separate with commas) | no |
| `"year"` | Next to the title | no |
| `"description"` | Body text below the title | no |

**Adding a second piece?** Put a comma between entries:

```json
[
  {
    "file": "first-piece.jpg",
    "title": "First Piece"
  },
  {
    "file": "second-piece.jpg",
    "title": "Second Piece"
  }
]
```

> **No comma after the last entry!** That's the #1 thing that breaks it.

---

## Publishing (GitHub Desktop)

Every time, same steps:

1. Open **GitHub Desktop**
2. Your changes appear on the left
3. Bottom-left: type *anything* in the Summary box (e.g. "added new painting")
4. Click **Commit to main**
5. Click **Push origin** (top bar)
6. Wait ~2 minutes. Check your site. Done.

---

## Other Things You Can Do

### Add a new category
Create a new folder in `src/content/artwork/`. For example: `src/content/artwork/digital/`. A new filter tab appears on the site automatically.

### Remove artwork
Delete the image file. If it has an entry in `artwork.json`, delete that entry too.

### Change the About page photo
Replace `src/assets/artist-photo.jpg` with your new photo. Keep the same filename. (The flip card back image is `src/assets/artist-photo-2.jpg`.)

### Edit the About page text
Open `src/pages/about.astro` in any text editor. Change the text between `<p>` and `</p>` tags. Don't touch anything else.

---

## Quick Reference

| I want to... | Do this |
|---|---|
| Add artwork | Drop image into the right folder in `src/content/artwork/` |
| Add details to a piece | Edit `artwork.json` in that folder |
| New category | New folder in `src/content/artwork/` |
| Remove artwork | Delete the image (and its `artwork.json` entry if any) |
| Change about photo | Replace `src/assets/artist-photo.jpg` |
| Publish anything | Commit + Push in GitHub Desktop |

---

## Something Broke?

**Site didn't update?**
- Did you **push**? Committing is not enough. You also need to click "Push origin."
- Wait 2-3 minutes. It's not instant.

**artwork.json not working?**
- Check for missing or extra commas
- All text must be in `"double quotes"` (not single quotes)
- The `"file"` name must match your image **exactly**, including `.jpg`
- Paste your JSON into [jsonlint.com](https://jsonlint.com) to find errors

**Totally stuck?**
- Don't worry about it. Message Valentina.
