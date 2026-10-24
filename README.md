# Modern Display Technologies — Quiz Trainer

A single-file practice/quiz app built from OCR of NPTEL *"Modern Display Technologies: Flat Panel Displays"* (IIT Guwahati) solution PDFs.

**Everything lives inside `index.html`** — questions data, styling and app logic are all inline (no external JS/CSS files), so it works on GitHub Pages under any base path.

## Features

- **Assignment-wise** — pick one of the 12 assignments (96 questions total).
- **Random Assignment Test** — shuffled mix of questions from all assignments, **50 by default** (adjustable 1–96).
- **Selected Assignment Test** — tick one or more assignments to test on; questions appear in assignment order and **every question carries a color-coded badge showing which assignment it came from**. Per-assignment accuracy breakdown at the end.
- **Complete Assignment Test** — every question, in order, with a per-assignment breakdown.
- **Instant grading** — the moment you click an option the question locks in: your pick turns red if wrong, the correct option turns green, plus the explanation where one exists in the source PDFs. Status icons sit in a fixed slot on the right, so option text never shifts or reflows when graded. In multi-assignment tests, a colored "Assignment N" pill next to the mode badge marks each question's source assignment.
- **Browser Back / Forward** — app screens (Home → Quiz → Results) are real history entries; pressing Back returns you to the previous screen exactly as you left it, and stepping further back/forward keeps working.
- **Skip**, **Mark for Review**, Previous/Next, and a question palette to jump anywhere.
- **Live stats panel** — Total / Attempted / Correct / Wrong / Accuracy with color-coded palette: green = attempted correct, red = attempted wrong, white = unattempted, yellow = marked for review.
- **Results screen** — accuracy donut and per-assignment accuracy table; "Retry Same Set" replays the exact same questions.
- Keyboard shortcuts: `1–4` answer, `←` / `→` navigate.

## Run locally

Open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8000
# http://localhost:8000
```

## Publish on GitHub Pages

The repo is already initialized and committed on branch `main`. You only need a GitHub remote:

1. Create an **empty** repository on github.com (no README license wizard — we already have the files).
2. Push:

```bash
git remote add origin https://github.com/<user>/<repo>.git
git push -u origin main
```

3. On GitHub: **Settings → Pages → Build and deployment → Source: "Deploy from a branch" → Branch: `main` / `/(root)` → Save.**

The site goes live at `https://<user>.github.io/<repo>/` after the first Pages/Actions run finishes (usually ~1 minute).

> **User site** (`https://<user>.github.io/`): name the repo `<user>.github.io` instead — it is hosted from `main`/root automatically, no Pages settings change needed.

## Editing questions

Questions live in the `window.QUESTIONS = [ ... ]` array inside `index.html`:

```js
{ id:"w1q1", a:1, name:"Assignment 1",   // id must be UNIQUE — it identifies the
                                          // question when Back/Forward restores a screen
  q:"question text",
  opts:["option A","option B","option C","option D"],
  correct:2,                   // 0-based index into opts
  exp:"explanation or null" }  // shown under the feedback if present
```

Edit entries and push again — Pages redeploys automatically.

> Note: `ans/` contains the source solution PDFs and is excluded via `.gitignore` (not needed for the site).
