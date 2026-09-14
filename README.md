# Weird Wrestling Organizer

A single-page, self-contained web app: a categorized archive of wrestling moves plus a
match-card generator for inspiration. No backend, no build step, no dependencies beyond
one Google Fonts stylesheet — it's just `index.html`. The app's UI and content are in German.

## Run it locally

Just open `index.html` in a browser. That's it — no server required.

## Host it on GitHub Pages

1. **Create a new repository** on GitHub (public repos get free Pages hosting).
2. **Add this file** to the repo, keeping the name `index.html` at the root
   (GitHub Pages serves `index.html` automatically).
   - Easiest way: on the repo's GitHub page, click **Add file → Upload files**,
     drag in `index.html`, and commit.
   - Or via git:
     ```bash
     git init
     git add index.html README.md
     git commit -m "Weird Wrestling Organizer"
     git branch -M main
     git remote add origin https://github.com/<your-username>/<your-repo>.git
     git push -u origin main
     ```
3. **Enable Pages**: in the repo, go to **Settings → Pages**. Under "Build and
   deployment", set **Source** to "Deploy from a branch", pick the **main** branch
   and the **/ (root)** folder, then **Save**.
4. Wait a minute or two — GitHub will show a URL like:
   `https://<your-username>.github.io/<your-repo>/`
   That's your live app.

Any time you edit `index.html` and push again, the live page updates automatically
within a minute or so.

## Editing the content

Everything lives in one file, `index.html`:

- **`CATEGORIES`** — the 5 move categories (Submission-Aktionen, Würfe & Slams,
  Schläge & Tritte, Sprung- & Flugtechniken, Double-Team-Moves), each with a label,
  accent color, and short blurb.
- **`MOVES`** — the archive. Each entry has an `id`, `name`, `category`, `tier`
  (`basic` / `signature` / `finisher`), `risk` (`low` / `moderate` / `high`), and
  a German `desc`. Add a new object to this array to add a move.
- **`ARCHETYPES`** — the 5 wrestler styles used by the Match-Generator, each with
  category weightings that bias which moves get picked.
- **`STIPULATIONS`** — the list of match types the generator can pick from.
- **`BEATS`** — the 5-beat match structure (Auftakt / Kontrolle / Wendepunkt /
  Highlight / Finish) and which move tiers fit each beat.

Favorites are saved in the visitor's browser via `localStorage` — nothing is sent
to a server, and each visitor only sees their own favorites.

## Source note

Categories and move names are based on the German Wikipedia overview
["Liste von Wrestling-Kampftechniken"](https://de.wikipedia.org/wiki/Liste_von_Wrestling-Kampftechniken).
All descriptions in the app were written fresh for this project, not copied from
that or any other source.
