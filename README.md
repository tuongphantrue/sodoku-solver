# sudoku-solver

**📱 Open the app: https://tuongphantrue.github.io/sodoku-solver/**

*(link goes live once GitHub Pages is turned on for this repo — see below)*

A single-page Sudoku web app — generate a puzzle, play it, or let the solver finish it for you.

Built as one static `index.html` (no build step, no dependencies) so it runs directly or deploys straight to GitHub Pages.

## Features

- Puzzle generator with unique-solution guarantee (Easy / Medium / Hard / Expert)
- Click-or-keyboard entry, arrow-key navigation
- Pencil-mark notes mode
- Check for conflicts, get a hint, or auto-solve the whole board
- Backtracking solver + generator, both in plain JS
- **Import a puzzle** three ways:
  - **Text / file** — paste 81 digits (0 or `.` for blanks) or upload a `.txt`/`.csv`
  - **Photo** — upload a picture of a Sudoku grid, drag the four corner handles onto its border, and it's read automatically via [Tesseract.js](https://github.com/naptha/tesseract.js) OCR after a perspective-correcting warp
  - **Live camera** — on a phone, open the camera, fill the on-screen box with the grid, and hold steady; the app repeatedly reads the grid (every ~1s) and overlays the missing numbers directly on the video feed in green once it locks on. Needs HTTPS (GitHub Pages qualifies) and camera permission — it won't work opened as a local `file://`.
  - Either the photo or camera path can also be sent to the review screen (misreads shown in orange) so you can fix mistakes and play it on the board

## Open it on your phone (enable GitHub Pages once)

The files are already in this repo — Pages just needs to be switched on:

1. On GitHub, go to this repo's **Settings** tab.
2. In the left sidebar, click **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Under **Branch**, pick **main** and folder **/ (root)**, then **Save**.
5. Wait a minute or two, then reload the Pages settings page — it'll show *"Your site is live at `https://tuongphantrue.github.io/sodoku-solver/`"*. Open that link on your phone (or scan it as a QR code) — camera scanning needs this `https://` URL specifically, it won't work opened from a `file://` link.

## Run it locally

Just open `index.html` in a browser — everything works except camera scanning, which needs HTTPS (see above).
