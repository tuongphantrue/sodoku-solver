# sudoku-solver

**📱 Open the app: https://tuongphantrue.github.io/sodoku-solver/**

*(link goes live once GitHub Pages is turned on for this repo — see below)*

A Sudoku **solver**, not a game — no puzzle generator, no play mode, no timer. Feed it a puzzle by camera, photo, or text, and it hands back the solved grid.

Two files, no build step, no server: `index.html` (the app) and `digit_model.json` (a small trained neural network — see below). Both need to sit in the same folder for it to work.

## How it works

Three ways to give it a puzzle:

- **Camera (live)** — open your rear camera, fill the on-screen box with the grid, hold steady. The app rescans roughly every second and overlays the missing numbers directly on the video feed in green once it locks on. Needs HTTPS (GitHub Pages qualifies) and camera permission — it won't work opened as a local `file://`.
- **Photo** — upload a picture of a grid, drag four corner handles onto its border, and it's read automatically after a perspective-correcting warp. You can also just **paste an image** (Ctrl+V / Cmd+V) after copying one — no need to save it as a file first.
- **Text** — paste 81 digits (0 or `.` for blanks) or upload a `.txt`/`.csv`.

Whichever way you go in, you land on a **correction screen** — digits read automatically show in orange, so you can tap and fix anything wrong — then **Solve**. The result screen shows the finished grid: your original numbers in navy, the ones the solver filled in shown in green. The Sudoku solving itself is a backtracking constraint solver, runs entirely in your browser.

## How digit recognition works

Reading digits out of a photo or screenshot is the hard part, so it's worth explaining honestly:

- A small neural network (`digit_model.json`, ~230 KB) was trained offline on ~20,000 synthetic digit images — 185 real fonts, each digit rendered with random rotation, blur, noise, and stroke-thickness variation to imitate photographed or screenshotted puzzles. It runs entirely client-side with about 20 lines of plain JavaScript (matrix multiply + ReLU + softmax) — no TensorFlow.js or any ML library needed in the browser.
- [Tesseract.js](https://github.com/naptha/tesseract.js) (general-purpose OCR) runs as a second, independent check.
- A digit only gets filled in automatically when the trained model is confident on its own. If Tesseract actively disagrees with a confident model prediction, the cell is left blank instead of guessing — correctness over completeness. Cells left blank get called out on the correction screen so you know to fill them in by hand.

On held-out synthetic test data this setup reads digits at ~97% accuracy with well under 1% wrong-when-confident. Real-world accuracy on an actual photo or screenshot may differ from that synthetic benchmark — some fonts and imaging conditions weren't in training data.

## Open it on your phone (enable GitHub Pages once)

The files are already in this repo — Pages just needs to be switched on:

1. On GitHub, go to this repo's **Settings** tab.
2. In the left sidebar, click **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Under **Branch**, pick **main** and folder **/ (root)**, then **Save**.
5. Wait a minute or two, then reload the Pages settings page — it'll show *"Your site is live at `https://tuongphantrue.github.io/sodoku-solver/`"*. Open that link on your phone — camera scanning needs this `https://` URL specifically, it won't work opened from a `file://` link.

## Run it locally

Open `index.html` in a browser with `digit_model.json` in the same folder — everything works except camera scanning, which needs HTTPS (see above).
