# Deluxe Convert

A private, browser-based file converter. Static site, no build step, no server. Files never leave the user's device.

Typed output formats: after adding files, type a format (e.g. `pdf`, `mp3`) to apply it to every file that supports it.

## Deluxe account

Tap **Sign in with Deluxe Main** (top right) to use your Deluxe account from
[Deluxe Main](https://deluxe-drive.deluxelordd.workers.dev/main). Files still never leave your device: only
your last typed format and a list of recent conversions (file name, format, size, date) are saved to
your account, under the `convert` website in Deluxe Main. The page loads `deluxe.js` from Deluxe Main;
if it cannot load, the converter works exactly as before.

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

## Deploy: GitHub → Cloudflare Pages

1. Push this repository to GitHub (already done if you're reading this).
2. Go to [dash.cloudflare.com](https://dash.cloudflare.com) → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
3. Select this repository.
4. Build settings:
   - **Framework preset**: None
   - **Build command**: (leave empty)
   - **Build output directory**: `/` (or `.`)
5. Click **Save and Deploy**.

Every push to `main` redeploys automatically. Security headers are set via the `_headers` file.

## Run locally

Open `index.html` in a browser, or run `npx serve .`.
