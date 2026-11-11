# Common

Pub quiz preparation for the NarrenCastl finale, theme **common** — the word the
host buried in his hint: *"Achieving a Bingo in the finales will be as common as
I can possibly make it."*

Single HTML file. No build step, no dependencies, no tracking, works offline.
Progress and best scores live in the browser via `localStorage`, so they stay on
each device.

## What's in it

- **Briefing** — nine sections walking the theme through every field it could
  land in, plus three habits worth more than any extra fact.
- **Cards** — 130 flashcards with Leitner boxes, in five categories: most common,
  the commons, common names, bingo, culture.
- **Pictures** — 34 photo cards: the "common"-named species, the people behind
  the commons, the places, and the objects of chance. Images load from Wikipedia
  at runtime and are cached, so the first run needs a connection.
- **Music** — 14 songs as clue cards. The app cannot play audio, so you get a
  description, the way the host's round works in reverse.
- **Lists** — eight timed "name as many as you can" challenges. These score per
  item on the night, which is why they are worth practising against a clock.
- **Rapid** — 90 seconds of typed recall across the whole deck.

Typed answers are matched generously: accents, articles, German or English
wording and single typos all pass. Short answers must be exact.

## Host it on GitHub Pages

1. Create a new repository on github.com — the green **New** button, or the plus
   at the top right. Name it `common`. Set it to **Public**; Pages needs that on
   a free account. Create it empty, without a README.
2. On the empty repository page, click **uploading an existing file**, drag in
   `index.html` and `README.md`, and commit. `index.html` has to sit in the root
   and keep that name, or the page will not open by itself.
3. Go to **Settings → Pages** in that repository.
4. Under **Build and deployment**, set Source to **Deploy from a branch**, branch
   `main`, folder `/ (root)`, and save.
5. After about a minute the address appears at the top of the Pages settings:
   `https://<your-username>.github.io/common/`

From the command line instead:

```bash
cd common
git init
git add index.html README.md
git commit -m "Common — pub quiz prep"
git branch -M main
git remote add origin https://github.com/<your-username>/common.git
git push -u origin main
```

Then enable Pages as in step 3.

### Afterwards

Open the address on your phone and add it to the home screen, and it behaves
like an app. To publish a new version, click `index.html` in the repository,
then the pencil icon, and replace the contents — or upload the file again. The
page redeploys itself within a minute. If you do not see the change, reload with
a hard refresh, because the browser caches it.

Anyone with the link can use it, and each person's progress stays on their own
device.

## Editing the content

Three arrays at the top of the `<script>` block hold everything. The last entry
of each card row is a list of accepted alternative answers, which is what makes
the typed drills forgiving:

- `CARDS` — `["Category", "Question", "Answer", ["alias", …]]`
- `PICS` — `["Answer", "note shown after", "Group", "Wikipedia title", ["alias", …]]`
- `SONGS` — `["Title", "Artist", "Year", "the clue"]`
- `LISTS` — `{t: "title", s: seconds, i: [["Item", ["alias", …]], …]}`
- `BRIEF` — `["Section heading", "<p>HTML body</p>"]`

A new category appears as a filter button by itself.
