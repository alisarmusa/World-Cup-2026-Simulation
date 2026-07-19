# World Cup 2026 — Live Fan Site & Simulation

A single-file, self-contained web app covering the **2026 FIFA World Cup** (USA · Canada · Mexico, June 11 – July 19). All 48 teams across 12 groups: real results, standings, the full knockout bracket, player leaderboards, editorial analysis, a Monte-Carlo simulation engine, a playable canvas mini-game, and a Fantasy World Cup team builder — all in one HTML file, no build step, no backend.

**Live:** https://world-cup-2026-simulation-malisar.vercel.app/

**Tournament state: COMPLETE.** 🏆 **Spain are world champions** — beating Argentina **1–0 after extra time** at MetLife Stadium on July 19, Ferran Torres scoring 39 seconds into the second period off a Nico Williams header, against ten men after Enzo Fernández was sent off in stoppage time. England took bronze 6–4 over France in the highest-scoring third-place play-off in World Cup history.

**Awards:** Golden Ball **Rodri** · Golden Boot **Kylian Mbappé** (10 goals, first back-to-back winner) · Golden Glove **Unai Simón** (one goal conceded all tournament, a record 650 consecutive minutes) · Best Young Player **Pau Cubarsí**.

---

## What's inside

- **Language switch — English / Türkçe.** A toggle in the top bar translates the whole site, editorial prose included. English is the default; the choice is not stored, so it resets on reload. Player names and venue names deliberately stay in their original form.
- **Knockout Bracket** — the complete real bracket (Groups → R32 → R16 → QF → SF → Final, plus the Third-Place play-off), with connector lines, a progress rail and the champion capsule.
- **Today's Matches** — a day-by-day fixture modal covering every round, all kickoff times in Türkiye Standard Time (TRT). It opens on the closing slate (July 19) and is bounded at both ends of the tournament.
- **Leaderboards** — Goals, Assists, Clean Sheets, Red/Yellow Cards and Average Ratings, each with proportional value bars and a **Current / Pre-Tournament** toggle (final numbers vs. the model's pre-tournament projection).
- **Simulation** — a Poisson goal model plus power ratings run through a 4,000-run Monte-Carlo simulation. With every match now played, **Current** simply replays the real result; **Pre-Tournament** re-sims the whole thing from opening ratings, which is where the interest now lies — the real bracket repeats far less often than you'd expect.
- **Editorial** — Power Rankings (all 48, now a final verdict rather than a projection), Predictions scored against what actually happened, Favorites, Dark Horses, Tier Breakdown, Questions and a methodology Analysis. Eliminated teams are visually dimmed so the champions stand out.
- **The Best XI** — the Team of the Tournament laid out on a pitch, with a Player of the Tournament spotlight and selector's notes.
- **Fantasy World Cup** — build a 4-3-3 within a credit budget, guided position by position, scored on full-tournament points.
- **The Game** — a canvas arcade match: pick a nation, pick an opponent, choose difficulty, beat the CPU. Nations can be ordered by Power Rankings or alphabetically. A per-nation difficulty panel rates all 48 sides 0–100 against your chosen team. Mobile-first with touch controls and fullscreen.
- **Breaking ticker** — a scrolling headline feed plus a full Breaking News list, newest first, closing with the final and the awards.

## Tech

- **One file.** `index.html` (deployed) and `WC2026.html` are byte-identical copies; everything — HTML, CSS, JS, fonts — is inline. Fonts (Inter, Bebas Neue) are embedded as base64 woff2 (OFL 1.1).
- **No framework, no build.** Vanilla JS modules in closures (Tournament, Simulation, Today's Matches, Leaderboard, Bracket, Fantasy, Game, I18N).
- **Translation without markup churn.** The language switch is a text-node dictionary swap with a reverse map, plus a guarded `MutationObserver` so content rendered after a switch is translated too. No `data-i18n` attributes were added to the markup.
- **Locked down.** A strict `Content-Security-Policy` meta, no external requests, no analytics, no cookies, no storage, and no user text input anywhere.
- **Data integrity first.** Only web-verified, multi-source-confirmed final scores are entered; the simulation is the only thing that projects unplayed matches. Stats that aren't in a published match feed are left out rather than estimated — the yellow-card table is deliberately incomplete for the final because sources disagreed on who was booked.

## Repo layout

| File | Purpose |
|------|---------|
| `index.html` | Deployed app (served by Vercel) |
| `WC2026.html` | Byte-identical twin of `index.html` |
| `vercel.json` | Deploy config |
| `README.md` | This file |

`CLAUDE.md` (working instructions) and `memory.md` (session log) live alongside the project but are intentionally **not** part of the repo.

## Development

The app is a single static file — open `index.html` in any modern browser to run it. No install, no server, no dependencies.

Deployment is handled via the Vercel CLI. Vercel is the only deployment domain.

## Credits

Fonts: Inter and Bebas Neue (SIL Open Font License 1.1). Match data compiled from public reporting. This is an independent fan project and is not affiliated with FIFA.
