# Deluxe Convert

A private, browser-based file converter. Static site, no build step, no server. Files never leave the user's device.

## Supported conversions

| Input | Output |
|---|---|
| Images (PNG, JPG, WebP, GIF, BMP, SVG, AVIF, ICO) | PNG, JPG, WebP, BMP, ICO, PDF |
| PDF | PNG / JPG (one file, or a ZIP of pages), TXT |
| Word (.docx) | HTML, TXT, Markdown, PDF |
| Excel (.xlsx, .xls, .ods), CSV, TSV, JSON, YAML | JSON, CSV, TSV, XLSX, YAML, XML, HTML, TXT |
| XML | JSON, YAML, TXT |
| TXT, Markdown, HTML | TXT, HTML, Markdown, PDF |
| Audio (MP3, WAV, OGG, M4A, AAC, FLAC, OPUS, WMA) | MP3, WAV, OGG, FLAC, M4A |
| Video (MP4, WebM, MOV, MKV, AVI, M4V, FLV) | MP4, WebM, GIF, MP3, WAV, M4A |
| Any other file | ZIP |

Notes:
- Spreadsheets: only the first sheet is converted.
- Text-to-PDF uses a standard Latin font, so non-Latin scripts will not render in PDFs.
- Video conversion runs in WebAssembly and is slow for large files. Very large files may run out of browser memory.
- Libraries (jsDelivr / unpkg) load on demand the first time they are needed, so an internet connection is required.

## Deploy: GitHub → Vercel

1. Create a new empty repository on GitHub (e.g. `deluxe-convert`).
2. In this folder:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/deluxe-convert.git
   git push -u origin main
   ```
3. Go to [vercel.com/new](https://vercel.com/new), import the repository.
4. Framework Preset: **Other**. Leave Build Command and Output Directory empty. Click **Deploy**.

Every `git push` to `main` redeploys automatically.

## Run locally

Open `index.html` in a browser, or run `npx serve .`.
