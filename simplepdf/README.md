# SimplePDF

A PDF tool that runs entirely in the browser or as a Windows desktop app. Files are processed on the user's device and are never uploaded.

## Layout
- `src/` the app (one HTML file plus `src/vendor/` libraries, no build step). Used by both the website and the desktop app.
- `main.js` Electron entry point for the desktop app.
- `licenses/` licenses of bundled third-party libraries. Keep these when distributing.

## Run the website locally
Open `src/index.html` in Chrome or Edge, or run `npx serve src`.

## Run and build the desktop app (Windows)
1. Install Node.js LTS.
2. `npm install`
3. `npm start` to test.
4. Open a terminal **as Administrator** and run `npm run dist`. The installer appears in `dist/`.
   Alternative to Administrator: turn on Developer Mode in Windows Settings.

If `npm start` says Electron failed to install, download `electron-v33.4.11-win32-x64.zip` from the Electron releases page, extract it into `node_modules/electron/dist`, then create `node_modules/electron/path.txt` containing `electron.exe`.

## Deploy the website (Vercel)
1. Push this repo to GitHub.
2. In Vercel choose Add New Project, import the repo, leave Framework Preset as Other, and Deploy. `vercel.json` already points Vercel at `src/` and skips install and build.

## Before each release
- Bump `version` in `package.json` and add a line to `CHANGELOG.md`.
- Test saved files in Adobe Acrobat and Microsoft Edge: merge, edits, signature, print.

## Known limits
- Original text under an edit or redaction box still exists in the saved PDF.
- Word and Excel output is approximate and works only on PDFs that contain real text, not scans.
- No OCR, no form-field filling, no password creation yet.
