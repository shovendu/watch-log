# Watch Log

Single-file dashboard for `watch-log.json`. No build step: push to GitHub, enable Pages.

## Setup
1. Push `index.html`, `watch-log.json` (and optionally `sample-watch-log.json`) to the repo root.
2. Settings → Pages → deploy from branch `main` / root.
3. Open the site → **Settings** tab, on each device:
   - GitHub token (fine-grained, this repo only, Contents read/write) — only needed to add/edit/delete from the site
   - TMDB key → posters, year, "Auto-fill runtime"
   - OMDb key → IMDb rating
4. Preview with demo data: `https://<you>.github.io/<repo>/?demo`

Keys and token are stored in the browser only, never in the repo.

## Data format (Muse writes this)
`watch-log.json`: `{tracker, owner, entries[]}`. Each entry is one watching event:
`dateWatched, title, type (Movie|Series|Documentary|Other), season, episode, status (Watching|Finished|Plan to watch|Dropped), rating (1-10|null), durationMinutes, note`.

Rewatches are simply new entries with a new date. Posters/year/IMDb rating are fetched in the browser and cached per device; they are not written to the JSON.

## Privacy
GitHub Pages serves `watch-log.json` publicly if the repo is public. Use a private repo only if your plan supports private Pages; otherwise assume the log is readable by anyone with the URL.
