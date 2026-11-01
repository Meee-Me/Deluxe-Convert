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

## Deploy: GitHub → Netlify

1. Push this repository to GitHub.
2. Go to [app.netlify.com](https://app.netlify.com) → **Add new site → Import an existing project** → GitHub, and pick this repo.
3. Leave Build command empty. Set Publish directory to `.` (already set in `netlify.toml`). Click **Deploy**.

Every push to `main` redeploys automatically. (A `vercel.json` is also included if you prefer Vercel.)

## Run locally

Open `index.html` in a browser, or run `npx serve .`.
