# World Cup 2026 — Live Fan Site & Simulation

A single-file, self-contained web app tracking the **2026 FIFA World Cup** (USA · Canada · Mexico, June 11 – July 19) in near real time. All 48 teams across 12 groups: real results, standings, a live knockout bracket, player leaderboards, editorial analysis, a Monte-Carlo simulation engine, a playable canvas mini-game, and a Fantasy World Cup team builder — all in one HTML file, no build step, no backend.

**Live:** https://world-cup-2026-simulation-malisar.vercel.app/

---

## What's inside

- **Knockout Bracket** — the real bracket, updated as results come in (Groups → R32 → R16 → QF → SF → Final, plus a Third-Place play-off), with connector lines and a progress rail. Undecided ties (final/third place) show matchup placeholders like "FRA/ESP" that resolve automatically as rounds are played.
- **Today's Matches** — a day-by-day fixture modal covering every round through the Final and Third-Place match; all kickoff times shown in Türkiye Standard Time (TRT), with live / FT / upcoming states.
- **Leaderboards** — Goals, Assists, Clean Sheets, Red/Yellow Cards, and Average Ratings, each with proportional value bars.
- **Simulation** — a Poisson goal model + power ratings run through a Monte-Carlo simulation; projects every unplayed match, group tables, the bracket, and a champion. Real results are never overwritten. "Before the Tournament" mode re-runs from pre-tournament ratings.
- **Editorial** — Power Rankings (all 48), Predictions, Favorites, Dark Horses, Tier Breakdown, Questions, and a methodology Analysis. Eliminated teams are visually dimmed so live sides stand out.
- **The Best XI** — a Team of the Week laid out on a football pitch, rebuilt each completed round.
- **Fantasy World Cup** — build a 4-3-3 within a credit budget, guided position-by-position, scored on projected points; each player shows their specific position (LB/CB/CDM/CAM/RW/ST …).
- **The Game** — a canvas arcade match: pick a nation, choose difficulty, beat the CPU. Mobile-first with touch controls and fullscreen.
- **Breaking ticker** — a scrolling headline feed plus a full Breaking News list, newest first.

## Tech

- **One file.** `index.html` (deployed) and `WC2026.html` are byte-identical copies; everything — HTML, CSS, JS, fonts — is inline. Fonts (Inter, Bebas Neue) are embedded as base64 woff2 (OFL 1.1).
- **No framework, no build.** Vanilla JS modules in closures (Tournament, Simulation, Today's Matches, Leaderboard, Bracket, Fantasy, Game).
- **Data integrity first.** Only web-verified, multi-source-confirmed final scores are entered; the simulation is the only thing that projects unplayed matches.

## Repo layout

| File | Purpose |
|------|---------|
| `index.html` | Deployed app (served by Vercel) |
| `WC2026.html` | Byte-identical twin of `index.html` |
| `vercel.json` | Deploy config |
| `README.md` | This file |

## Development

The app is a single static file — open `index.html` in any modern browser to run it. No install, no server, no dependencies.

Deployment is handled via the Vercel CLI. Vercel is the only deployment domain.

## Credits

Fonts: Inter and Bebas Neue (SIL Open Font License 1.1). Match data compiled from public reporting. This is an independent fan project and is not affiliated with FIFA.
