# Deluxe Convert

**Live:** https://deluxe-convert.netlify.app

A private, browser-based file converter. Static site, no build step, no server. Files never leave the user's device.

Typed output formats: after adding files, type a format (e.g. `pdf`, `mp3`) to apply it to every file that supports it.

## Supported conversions

| Input | Output |
|---|---|
| Images (PNG, JPG, WebP, GIF, BMP, SVG, AVIF, ICO, HEIC/HEIF, TIFF, PSD) | PNG, JPG, WebP, BMP, ICO, TIFF, PDF |
| PDF, Word (.docx), PowerPoint (.pptx), OpenDocument (.odt, .odp), RTF, TXT, Markdown, HTML | TXT, HTML, Markdown, PDF, DOCX, ODT, PPTX, RTF, JSON, XML, PNG, JPG (text only: layout, fonts and images are not preserved) |
| Excel (.xlsx, .xls, .ods), CSV, TSV, JSON, YAML | JSON, CSV, TSV, XLSX, YAML, XML, HTML, TXT |
| XML | JSON, YAML, TXT |
| Audio (MP3, WAV, OGG, M4A, AAC, FLAC, OPUS, WMA) | MP3, WAV, OGG, FLAC, M4A, AAC, Opus |
| Video (MP4, WebM, MOV, MKV, AVI, M4V, FLV) | MP4, WebM, MKV, MOV, AVI, GIF, or any audio format above |
| Any other file | ZIP |

Notes:
- Not supported: legacy binary Office files (.doc, .ppt) and camera RAW. Re-save them as .docx / .pptx first. PSD uses the flattened preview; RTF input is basic.
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
