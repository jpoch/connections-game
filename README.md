# Connections — a birthday puzzle

A single-page, dependency-free clone of the NYT Connections game, made as a birthday gift.
Everything lives in one file: `index.html`.

## Playing

Open `index.html` in any modern browser, or serve the folder:

```sh
python3 -m http.server 8765
# then visit http://localhost:8765/
```

## Editing the puzzle

All game content is in the `PUZZLE` object at the top of the `<script>` block in `index.html`:

```js
const PUZZLE = {
  number: 112,                  // shown as "Puzzle #112"
  date: "November 7, 2026",
  categories: [
    { name: "DENVER DATES", color: "yellow", words: ["GARDEN", "ART MUSEUM", "SYMPHONY", "CO HISTORY MUSEUM"] },
    // ...
  ],
  winMessage: "...",             // shown on the final screen
  loseMessage: "...",
  dedication: "..."              // small line at the bottom; set "" to hide
};
```

Rules of thumb:

- Four categories, four words each, 16 unique words.
- Order matters: the first entry is yellow (easiest) and the last is purple (hardest).
- `color` must be one of `yellow`, `green`, `blue`, `purple`.
- Tiles auto-shrink and wrap at spaces, so multi-word entries work.
- A literal `²` (or `¹`/`³`) renders as a styled exponent, e.g. `JE²`.

## Features

- 4×4 word grid with select/deselect, shuffle, and deselect-all
- Four-mistake limit with NYT-style mistake dots
- "One away…", "Incorrect" and "Next time…" toasts
- Solved categories collapse into color-coded rows in the order solved
- Win/lose results screen with an emoji grid and a share button that copies it to the clipboard
- Responsive layout, keyboard-accessible tiles, reduced-motion support

## Deploying to GitHub Pages

```sh
git add .
git commit -m "Connections birthday puzzle"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

Then in the repository: **Settings → Pages → Build and deployment**
→ Source: **Deploy from a branch** → Branch: **main**, folder: **/ (root)** → **Save**.

The game will be live at `https://<your-username>.github.io/<repo-name>/` in a minute or two.

## Note

A personal fan project inspired by NYT Connections. Not affiliated with The New York Times.
