# Your Life, In Receipts

A frontend-only interactive story built from the three provided datasets: Spotify listening history (2013-2024), a personal expense diary (2015-2018) and card transactions (2022-2024).

**Live demo:** _add your deployed URL here_

## What it does
- **Six chapters** split the life into eras, each with computed stats (plays, hours, top artist, spent, saved, earned).
- **The roll** charts plays per month, with diary spending (blue dots) and card receipts (pink squares).
- **Connections:** click any month to get a receipt joining music, purchases, events and notes, plus "echo" months sharing the same top artist.
- **Follow an artist:** highlight every month where an artist is in the top 3.
- **Search and filter** moments by type (music, event, note, card).
- **Six pattern cards** computed from the data (Beatles streak, the 2020 Killers year, the 1,816-play day, savings ratio and more).

## Tech
Vanilla JS and SVG in one self-contained `index.html`. No backend, no build step to run it. Keyboard accessible and responsive.

## Data notes
- Only music and purchases are literal categories; events, notes and entertainment are derived from diary fields.
- Spotify `skipped` is unreliable (79% in 2015, 0% for 2017-2021), so it is not used.
- Spotify timestamps are UTC, so no time-of-day claims are made.
- The card data spans about 1,330 card numbers with roughly half labelled fraud, so it is shown as a separate layer.

## Rebuilding the data
`tools/build.py` aggregates the raw CSVs into compact JSON and injects it into `tools/tpl.html`. Put the raw files in `tools/data/` (spotify/, household/, india/) and run `cd tools && python build.py`. Raw CSVs are not committed because of size.
