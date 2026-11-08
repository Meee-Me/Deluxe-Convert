# Deluxe Convert

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

## Sharing and Deluxe Drive

Every converted file has **Share to Deluxe Drive** and **Share…** next to Download.

- **Share to Deluxe Drive** adds the file to a **Deluxe Convert** folder in your Deluxe Drive.
  **Share all to Deluxe Drive** does it for every converted file.
- **Share…** opens the share panel. From there you can share to Deluxe Drive, **copy a share link**
  (the file is saved to Deluxe Drive and you get a link anyone can open, with Email, WhatsApp and
  Telegram shortcuts), **send it with another app** (the device's share sheet, where the browser
  supports sharing files), or download it.

- **Open in Deluxe Docs** (in the share panel) saves the file to Deluxe Drive and opens it in Deluxe Docs.
- From Deluxe Drive, a file's menu has **Convert with Deluxe Convert**: Convert opens with that file
  already added (it reads the file's share link, `?url=…&name=…`).

Connecting works the same way as Deluxe Docs:

1. In Deluxe Drive, open the account menu (your avatar) → **Connect Deluxe Convert**.
2. Tap **Generate link ID**, then **Open Deluxe Convert**. Convert connects by itself.
   On another device, tap **Connect Deluxe Drive** at the top of Convert and type the code.
   The code works once, for 60 seconds.

The drive is https://deluxe-drive-xi.vercel.app (its server is a Vercel Function there). Files bigger
than 4 MB are sent in pieces, because a Vercel Function takes about 4.5 MB per request.

Convert gets a key that can **only add files** to that drive. It cannot list, open, change or delete
anything else. The key lasts 30 days and is kept in this browser; **Disconnect** in the Deluxe Drive
dialog ends it. Files are only uploaded when you choose to share one. A file can be up to 100 MB.

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
