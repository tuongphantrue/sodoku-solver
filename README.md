# sudoku-solver

**📱 Open the app: https://tuongphantrue.github.io/sodoku-solver/**

*(link goes live once GitHub Pages is turned on for this repo — see below)*

A Sudoku **solver**, not a game — no puzzle generator, no play mode, no timer. Feed it a puzzle by camera, photo, or text, and it hands back the solved grid.

Built as one static `index.html` (no build step, no dependencies) so it runs directly or deploys straight to GitHub Pages.

## How it works

Three ways to give it a puzzle:

- **Camera (live)** — open your rear camera, fill the on-screen box with the grid, hold steady. The app rescans roughly every second and overlays the missing numbers directly on the video feed in green once it locks on. Needs HTTPS (GitHub Pages qualifies) and camera permission — it won't work opened as a local `file://`.
- **Photo** — upload a picture of a grid, drag four corner handles onto its border, and it's read automatically via [Tesseract.js](https://github.com/naptha/tesseract.js) OCR after a perspective-correcting warp.
- **Text** — paste 81 digits (0 or `.` for blanks) or upload a `.txt`/`.csv`.

Whichever way you go in, you land on a **correction screen** — digits read automatically show in orange, so you can tap and fix any OCR misread — then **Solve**. The result screen shows the finished grid: your original numbers in navy, the ones the solver filled in shown in green. Backtracking constraint solver, runs entirely in your browser.

## Open it on your phone (enable GitHub Pages once)

The files are already in this repo — Pages just needs to be switched on:

1. On GitHub, go to this repo's **Settings** tab.
2. In the left sidebar, click **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Under **Branch**, pick **main** and folder **/ (root)**, then **Save**.
5. Wait a minute or two, then reload the Pages settings page — it'll show *"Your site is live at `https://tuongphantrue.github.io/sodoku-solver/`"*. Open that link on your phone — camera scanning needs this `https://` URL specifically, it won't work opened from a `file://` link.

## Run it locally

Just open `index.html` in a browser — everything works except camera scanning, which needs HTTPS (see above).
