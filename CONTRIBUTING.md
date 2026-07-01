# Contributing

Thanks for your interest in the World Cup 2026 fan site.

## The one rule that matters most

**Data integrity.** Only real, web-verified final scores are entered. Before changing any
result, cross-check it against at least two reliable sources (ESPN, FIFA, CBS, Sky Sports,
Al Jazeera). Referees stay `TBD` unless a source confirms them. Never hard-code a score for
a match that hasn't finished — unplayed matches are projected by the Simulation module only.

## Project shape

The entire site is one self-contained file. There is **no build step**.

- `index.html` is what gets served.
- `WC2026.html` is a byte-identical working copy.
- **Any change must be applied to both files so they stay identical.** CI enforces this.

## Before you open a pull request

Run the same checks CI runs (all pure Node, no dependencies):

- `cmp index.html WC2026.html` — the two files must match exactly.
- Every `<script>` block parses.
- CSS braces are balanced.
- The Breaking ticker has two identical halves.
- No finished match has a null score.

## Times

All match dates and times are displayed in **Türkiye Standard Time (TRT, UTC+3)**.

## Reporting instead of coding

Not a coder? Open an issue. A **Data correction** issue with a source link is one of the most
useful contributions you can make.
