# Bridge Trainer

Single-file pub quiz trainer for the theme **bridges** (NarrenCastl, Season 9, Quiz 5).
Four chapters, all flashcard style: pictures, topic questions, lateral readings
and word bridges.
No build step, no dependencies, no tracking. Progress is kept in the browser
with `localStorage`, so it stays on each person's own device.

Photos are fetched at runtime from Wikipedia and cached in the browser, so an
internet connection is needed the first time through.

## Host it on GitHub Pages

1. Create a public repository, for example `bridge-trainer`.
2. Upload `index.html` to the root of the repository (the name must stay `index.html`).
3. Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`, Save.
4. After about a minute the app is live at `https://<your-username>.github.io/bridge-trainer/`.

Command line instead:

```bash
git init
git add index.html README.md
git commit -m "Bridge Trainer"
git branch -M main
git remote add origin https://github.com/<your-username>/bridge-trainer.git
git push -u origin main
```

## Editing the content

Four arrays at the top of the `<script>` block hold everything:

- `PICS` — `["Name", "what it is", "Group", "Wikipedia title"]`. The Wikipedia
  title decides which photo is loaded; English is tried first, then German.
- `TOPIC` — `["Category", "Question", "Answer"]`.
- `LATERAL` — same shape, for the off-beat readings of the theme.
- `WORDS` — `["Language", "left", "bridging word", "right"]`, so
  `["English","day","light","house"]` becomes daylight · lighthouse.

A new group or category automatically gets its own filter button.
