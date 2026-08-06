# sudoku-solver

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

## Run it

Just open `index.html` in a browser — everything is self-contained.

## Deploy to GitHub Pages

1. Create a new repo (e.g. `sudoku-solver`) and push `index.html` + `README.md` to it.
2. In the repo, go to **Settings → Pages**, set source to the `main` branch, root folder.
3. Your app will be live at `https://<username>.github.io/sudoku-solver/`.
