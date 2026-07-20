# Proxy Buffer

A tiny, dependency-free web tool that adds a **1/8" black buffer border** to MTG
card images so they survive cutting when you print proxies. Drag images in,
download them as PNGs (individually or as a zip). Everything runs in the browser,
with no upload, no server, no tracking.

Live once you enable GitHub Pages (see below).

## What it does

- **Drag & drop / browse / paste** any number of MTG card images at once.
- Adds a solid **1/8" (0.125") buffer border** on all four sides, the standard
  proxy bleed. Sized as a *true* 1/8" relative to each image, so it stays 1/8"
  whether the source is 750px or 1500px wide (about 38px per side at 300 DPI).
- **Border color** (black by default; white or custom).
- The image itself is never altered. Only the border is added around it.
- **Checks each image** against the standard 2.5 × 3.5" MTG card and flags:
  - **Resolution**: effective DPI. Under ~200 DPI = blurry (red),
    200 to 299 = soft (amber), 300+ = good, 600+ = excellent.
  - **Card shape**: warns if the aspect ratio isn't ~2.5:3.5 (5:7), or if the
    image looks sideways.
- **Download** each card as a PNG, or **Download all as .zip** (zip is built
  in-browser with a hand-rolled store-only writer, no libraries).

## The numbers it uses

| Thing | Value |
|---|---|
| Card trim size | 2.5 × 3.5 in (63 × 88 mm), aspect 5:7 |
| Min crisp print | 750 × 1050 px (300 DPI) |
| Excellent | 1500 × 2100 px (600 DPI) |
| 1/8" border | 0.125" per side ≈ 37.5 px at 300 DPI |
| Card + 1/8" border | 2.75 × 3.75 in = 825 × 1125 px at 300 DPI |

**Why the border?** Cutters are never perfectly aligned. A solid border means a
slightly-off cut trims into the border instead of leaving a white sliver or slicing
the art. Real Magic cards are black-bordered, so a miscut into black is invisible.
This is the same idea as "bleed" in print shops and MakePlayingCards uploads.

## Host it on GitHub Pages

1. Create a new GitHub repo (e.g. `proxy-buffer`) and put `index.html` at its root.
   ```bash
   git init
   git add index.html README.md
   git commit -m "Proxy Buffer"
   git branch -M main
   git remote add origin https://github.com/<you>/proxy-buffer.git
   git push -u origin main
   ```
2. On GitHub: **Settings → Pages → Build and deployment**.
3. Set **Source: Deploy from a branch**, **Branch: `main`**, folder **`/ (root)`**, Save.
4. Wait ~1 minute. Your site is at `https://<you>.github.io/proxy-buffer/`.

That's it. A single static file, nothing else to configure.
