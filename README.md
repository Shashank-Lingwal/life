# Your Life, In Receipts

A frontend-only interactive story built from the three provided datasets: Spotify listening history (2013-2024), a personal expense diary (2015-2018) and card transactions (2022-2024).

**Live demo:** https://shashank-lingwal.github.io/life/

## What it does
- **Six chapters** split the life into eras, each with computed stats (plays, hours, top artist, spent, saved, earned).
- **The roll** charts plays per month, with diary spending (blue dots) and card receipts (pink squares).
- **Connections:** click any month to get a receipt joining music, purchases, events and notes, plus "echo" months sharing the same top artist.
- **Follow an artist:** highlight every month where an artist is in the top 3.
- **Search and filter** moments by type (music, event, note, card).
- **Six pattern cards** computed from the data (Beatles streak, the 2020 Killers year, the 1,816-play day, savings ratio and more).

## Project structure
```
index.html          page markup
src/main.js         state, chart rendering, receipts, search, interactions
src/styles.css      thermal-paper theme and responsive layout
src/data.js         aggregated data (generated)
tools/build.py      regenerates src/data.js from the raw CSVs
package.json        Vite scripts for local dev and build
```

## Run locally
```
npm install
npm run dev
```
Deployed as static files on GitHub Pages. No backend.

## Data notes
- Only music and purchases are literal categories; events, notes and entertainment are derived from diary fields.
- Spotify `skipped` is unreliable (79% in 2015, 0% for 2017-2021), so it is not used.
- Spotify timestamps are UTC, so no time-of-day claims are made.
- The card data spans about 1,330 card numbers with roughly half labelled fraud, so it is shown as a separate layer.

## Rebuilding the data
Put the raw files in `tools/data/` (spotify/, household/, india/) and run `cd tools && python build.py`.
