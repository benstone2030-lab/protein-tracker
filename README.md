# Protein

A single-page protein tracker. Open it, type a number, hit enter.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app — markup, styles, logic |
| `manifest.webmanifest` | Name, icon, and standalone display for the home screen |
| `sw.js` | Service worker; caches the app so it opens offline |
| `icon-*.png` | Home screen icons |

All of these must sit in the same folder. Paths are relative, so it works from a
repo subpath like `username.github.io/protein/`.

## Put it on GitHub Pages

1. Create a new repository — `protein` is a fine name. Public.
2. Upload all seven files to the root of the repo (drag them into the "Add file →
   Upload files" screen).
3. Settings → Pages. Under "Build and deployment", set Source to **Deploy from a
   branch**, branch **main**, folder **/ (root)**. Save.
4. Wait a minute or two, then open `https://YOUR-USERNAME.github.io/protein/`.

HTTPS comes free with Pages, which the service worker requires.

## Add it to your iPhone

Open the URL in **Safari** (not Chrome — only Safari can install to the home
screen on iOS). Tap Share → **Add to Home Screen**. It launches full screen with
no browser chrome.

## Data

Entries live in the browser's local storage on that device. Nothing is uploaded
anywhere. That means:

- Data does not sync between your phone and your laptop.
- Deleting the app from your home screen may clear it, and "Clear History and
  Website Data" in Safari settings definitely will.

Use **EXPORT DATA** now and then for a backup file, and **IMPORT DATA** to merge
it back or move it to another device. Import merges by entry ID, so importing
the same backup twice will not duplicate anything.

## Changing it

Edit `index.html` directly. If you change it after the app has been installed,
bump the `CACHE` constant at the top of `sw.js` (`protein-v1` → `protein-v2`) or
the old cached copy will keep loading.

Things you might want to adjust, all near the top of the `<script>`:

- `SEG` — number of segments in the progress bar.
- The `> 500` check in `add()` — the typo guard on a single entry.
- Colors live in the `:root` block in the `<style>` tag.
