# World Cup 2026 — Simulation Site

[![Validate](https://github.com/alisarmusa/World-Cup-2026-Simulation/actions/workflows/validate.yml/badge.svg)](https://github.com/alisarmusa/World-Cup-2026-Simulation/actions/workflows/validate.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
![No build step](https://img.shields.io/badge/build-none-brightgreen)
![Single file](https://img.shields.io/badge/architecture-single--file-orange)

A single-file, data-driven fan site tracking the **2026 World Cup** — 48 teams, 12 groups, hosted across the United States, Canada, and Mexico — in near real time.

> The entire site is one self-contained HTML file. No build step, no dependencies, no backend, and **no third-party requests** — fonts are embedded, so nothing loads from an external server. Open it in a browser and it works.

## Contents

- [Features](#features)
- [Screenshots](#screenshots)
- [Running locally](#running-locally)
- [Project structure](#project-structure)
- [Data integrity](#data-integrity)
- [Deploying](#deploying)
- [Contributing](#contributing)
- [License](#license)

## Features

- **Live match data & standings** for all 12 groups, plus a **Knockout Bracket** from the Round of 32 through the Final, with penalty-shootout support.
- **Today's Matches** — a day-by-day schedule; all times shown in **Türkiye Standard Time (TRT, UTC+3)**.
- **Leaderboards** — Goals, Assists, Clean Sheets, Yellow Cards, Red Cards, and Average Ratings.
- **Breaking ticker** — a rolling strip of the latest results and fixtures.
- **Editorial** — Power Rankings (#1–48), Predictions, Favorites, Dark Horses, Tier Breakdown, Questions, Analysis, and an Executive Summary. Each carries flags, stat chips, and compact progress/meter visuals for fast scanning.
- **Current vs Before the Tournament** — Power Rankings, Simulation, Favorites, Predictions, Tier Breakdown, and Questions each have a two-way toggle: **Current** reflects the tournament as it stands, while **Before the Tournament** shows the same view driven by pre-tournament strength ratings.
- **Simulation** — a Poisson goal model plus a Monte Carlo run projecting the rest of the tournament, with real played results locked so they are never re-decided. A **Before the Tournament** mode re-simulates the whole event from scratch on pre-tournament ratings alone.
- **Team of the Week** — a rotating best XI.
- **Fantasy World Cup** — build an XI under a credit budget.
- **FC Game** — a self-contained HTML canvas arcade football mini-game (you vs. CPU) on desktop and mobile. Every nation carries a **5-star power rating**, and an **adaptive difficulty system** blends your chosen level (Easy / Medium / Hard) with the opponent's strength: a 5★ side like England plays markedly tougher than a 1★ side at the same setting. Each pairing resolves to a single **1–10 Match Difficulty** score (Stroll → Relaxed → Balanced → Tough → Brutal), shown on the match preview and in a full **Difficulty by Nation** list ranking all 48 teams.

## Screenshots

_Add a screenshot or GIF here once the site is deployed — e.g. `docs/preview.png`._

## Running locally

No tooling required:

```bash
# open directly
open index.html          # macOS
xdg-open index.html      # Linux

# …or serve it (recommended)
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Project structure

| File | Purpose |
|------|---------|
| `index.html` | The site — this is what a host serves. |
| `WC2026.html` | Byte-identical working copy of the site. |
| `vercel.json` / `.vercelignore` | Vercel deploy config (static, no build). |
| `.github/workflows/validate.yml` | CI: parity, JS parse, CSS balance, ticker, data checks. |

`index.html` and `WC2026.html` are kept **byte-identical** — edit one, mirror to the other. CI enforces this on every push.

The JavaScript is organised into self-contained IIFE modules (tournament data, simulation, leaderboards, knockout bracket, today's matches, fantasy, and the canvas game). No frameworks.

## Data integrity

Only **real, web-verified final scores** are entered, cross-checked against multiple reliable sources. Match referees stay `TBD` unless source-confirmed. Unplayed matches are only ever *projected* by the Simulation module — never hard-coded as results.

## Privacy & security

Built to be safe to publish as-is:

- **No tracking.** No analytics, no third-party scripts, no cookies, no `localStorage`/`sessionStorage`, no beacons — the site collects and transmits nothing about visitors.
- **No external requests.** Fonts (Inter and Bebas Neue, both under the SIL Open Font License) are embedded directly in the file, so the page makes zero calls to any outside server.
- **Content-Security-Policy.** A restrictive CSP is set via meta tag: only same-origin and inline resources are allowed; `object-src`, `frame-src`, and `form-action` are disabled.
- **No injection surface.** There are no text inputs or URL-parameter reads, so there is no user-supplied content that could reach the DOM.
- **Independent fan project.** A visible footer disclaims any affiliation with FIFA; all trademarks belong to their respective owners.

## Deploying

The site is a static single file, so any static host works.

**Vercel** — import the repo at [vercel.com/new](https://vercel.com/new). Framework preset **Other**; build command empty; output directory empty (root). Or run `vercel --prod` from the CLI.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). The most valuable contribution is often a **data correction** with a source link — no coding required.

## License

[MIT](LICENSE) © Malisar
