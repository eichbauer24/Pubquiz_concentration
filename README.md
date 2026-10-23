# Bridge Trainer

Pub quiz trainer for NarrenCastl Season 9, Quiz 5 (theme: **bridges**), built in the
real format of the evening: four rounds, 20 points each, 80 in total, answers
written down and marked in the break.

Single file, no build step, no dependencies, no tracking. Scores and flashcard
progress live in the browser via `localStorage`, so they stay on each device.
Photos are fetched from Wikipedia at runtime and cached, so the first run needs
an internet connection.

## The two modes

**Quiz night** — a full simulated quiz:

1. *Photos Frenzy* — 20 pictures to name, one point each.
2. *Trivia Blitz* — 20 questions across all categories.
3. *Music Mania* — 10 songs, two points each for title and artist. Since the app
   cannot play the audio, you get a clue and the year instead.
4. *Build a Bridge* — the themed round: 12 word bridges and 8 bridges to name
   from a description.

After each round you hand in, the answers are matched automatically (generous
about spelling, accents and German or English wording) and you can override every
verdict with the *point* / *no point* buttons, exactly as the host would. Round
scores, the total out of 80 and your past attempts are kept.

**Drill** — flashcards with Leitner boxes for pictures, trivia, outside-the-box
readings, word bridges and the songs. Use it on whichever round the scoreboard
shows as your weakest.

## Host it on GitHub Pages

1. Create a public repository, for example `bridge-trainer`.
2. Upload `index.html` to the root (the name must stay `index.html`).
3. Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`, Save.
4. After about a minute: `https://<your-username>.github.io/bridge-trainer/`.

```bash
git init
git add index.html README.md
git commit -m "Bridge Trainer"
git branch -M main
git remote add origin https://github.com/<your-username>/bridge-trainer.git
git push -u origin main
```

## Editing the content

Five arrays at the top of the `<script>` block hold everything. The last entry of
the picture and question rows is a list of accepted alternative answers, which is
what makes the automatic marking forgiving:

- `PICS` — `["Name", "what it is", "Group", "Wikipedia title", ["alias", …]]`
- `TOPIC` — `["Category", "Question", "Answer", ["alias", …]]`
- `LATERAL` — same shape, for the off-beat readings of the theme
- `WORDS` — `["Language", "left", "bridging word", "right"]`
- `SONGS` — `["Title", "Artist", "Year", "clue"]`

New categories appear as filter buttons in the drill automatically.
