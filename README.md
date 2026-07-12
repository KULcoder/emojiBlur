# Emoji Mask

**Hide faces with emojis before you post — entirely in your browser.**

Emoji Mask is a single-file web app that detects faces in photos and covers them with emojis. Photos never leave your device. Exported images are re-encoded, so EXIF metadata (including GPS location) is stripped automatically.

## Features

- **Automatic face detection** — powered by [face-api.js](https://github.com/justadudewhohacks/face-api.js) (SSD MobileNet v1), with a tiled second pass on large images
- **Privacy-first** — all processing runs locally; no uploads, no server
- **Works offline** — model weights are embedded in `index.html`
- **Emoji themes** — smiles, cats, animals, fruits, space, sweets, ocean, spooky, hearts, or one emoji for every face
- **Manual editor** — move, resize, add, or delete emoji overlays; swipe or use arrow keys to move between photos
- **Batch export** — download individual images or everything as a `.zip`

## Quick start

No install or build step required.

### Option 1: Open the file

Download or clone this repo, then open `index.html` in a modern browser (Chrome, Edge, Firefox, or Safari).

> The file is ~8 MB because it bundles the face detector and model weights for offline use. Make sure it finishes downloading before opening.

### Option 2: Local server (recommended for development)

```bash
git clone https://github.com/KULcoder/emojiBlur.git
cd emojiBlur
python3 -m http.server 8080
```

Then visit [http://localhost:8080](http://localhost:8080).

## Deploy to GitHub Pages

This repo includes a GitHub Actions workflow that publishes the site on every push to `main`.

1. Push this repository to GitHub.
2. Go to **Settings → Pages → Build and deployment**.
3. Set **Source** to **GitHub Actions**.
4. After the workflow runs, the site will be live at:

   `https://KULcoder.github.io/emojiBlur/`

You can also deploy manually: enable Pages with the `main` branch and `/ (root)` as the source — `index.html` at the repo root is all you need.

## How it works

1. Drop or select one or more photos (JPEG, PNG, WebP).
2. The detector finds faces and places emoji overlays sized to each face box.
3. Tap **Edit** on any photo to fine-tune placements, change emojis, or add masks manually.
4. Save individual images or **Download all (.zip)**.

If automatic detection is unavailable (blocked CDN, ad blocker, etc.), you can still add photos and place emojis manually.

## Browser support

| Browser | Support |
|---------|---------|
| Chrome / Edge | ✅ Full |
| Firefox | ✅ Full |
| Safari | ✅ Full (iOS 15+) |

HEIC/HEIF images may not decode in all browsers — export as JPEG first if needed.

## Project structure

```
emojiBlur/
├── index.html          # Entire app (UI, logic, face-api.js, JSZip, model weights)
├── README.md
├── LICENSE
└── .github/workflows/  # GitHub Pages deployment
```

There is no build pipeline. Everything lives in one self-contained HTML file.

## Credits

- [face-api.js](https://github.com/justadudewhohacks/face-api.js) — face detection (MIT)
- [JSZip](https://stuk.github.io/jszip/) — ZIP export (MIT/GPL dual license)
- [Nunito](https://fonts.google.com/specimen/Nunito) — UI font (Google Fonts)

## License

MIT — see [LICENSE](LICENSE).
