# Modern Display Technologies — Quiz Trainer

A single-file practice/quiz app built from OCR of NPTEL *"Modern Display Technologies: Flat Panel Displays"* (IIT Guwahati) solution PDFs.

**Everything is baked into `index.html`** — questions data, styling, and app logic are all inline. No build step, no external files, so it works on GitHub Pages under any base path.

## Features

- **Assignment-wise** — pick one of the 12 assignments (96 questions total).
- **Random Assignment Test** — shuffled mix of questions from all assignments.
- **Complete Assignment Test** — every question, in order, with a per-assignment breakdown.
- **Instant grading** — the answer is revealed the moment you click an option (your pick turns red if wrong, the correct option turns green), plus the explanation where one exists in the source PDFs.
- **Skip** button, **Mark for Review**, Previous/Next, palette to jump between questions.
- **Live stats panel** — Total / Attempted / Correct / Wrong / Accuracy with a color-coded question palette: green = attempted correct, red = attempted wrong, white = unattempted, yellow = marked for review.
- Results screen with an accuracy donut and per-assignment accuracy table.
- Keyboard shortcuts: `1–4` answer, `←` / `→` navigate.

## Run locally

Just open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8000
# http://localhost:8000
```

## Publish on GitHub Pages

**Project site** (`https://<user>.github.io/<repo>/`) — most common:

```bash
git init
git add .
git commit -m "Quiz app"
# create an empty repo on github.com, then:
git remote add origin https://github.com/<user>/<repo>.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Build and deployment → Source: "Deploy from a branch" → Branch: `main` / `/(root)` → Save.**

The site goes live at `https://<user>.github.io/<repo>/` after the first Actions run finishes (~1 min).

**User site** (`https://<user>.github.io/`): name the repo `<user>.github.io` instead — no Pages settings change needed (already hosted from `main`/root).

## Editing questions

Questions live in the `window.QUESTIONS = [ ... ]` array at the top of `index.html`:

```js
{ id:"w1q1", a:1, name:"Assignment 1",
  q:"question text",
  opts:["option A","option B","option C","option D"],
  correct:2,                  // 0-based index of the right option
  exp:"explanation or null" } // shown after answering if present
```

Add or edit entries and push again — Pages redeploys automatically.

> Note: `ans/` contains the source solution PDFs and is excluded via `.gitignore` (not needed for the site).
