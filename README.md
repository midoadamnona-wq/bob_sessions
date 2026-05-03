# Trust 0 — KPI Integrity Platform

> A theatrical product demo for the IBM Bob Dev Day Hackathon · May 2026

## What this is

Trust 0 is a KPI integrity platform that maps the hidden authority chain behind every corporate KPI. It prevents employees from being held accountable for numbers they don't actually control, while giving executives real-time visibility into where accountability and authority diverge inside the organization.

This repository contains a single-file theatrical HTML demonstration that walks through:

1. A 1-minute story showing why the problem matters (a sales rep terminated for a number his Operations colleague controlled)
2. A 1-minute live product walkthrough of how Trust 0 ingests, chains, approves, and distributes KPI accountability

## How to run

The demo is a single self-contained HTML file. Open it in any modern browser:

```bash
open trust0_film.html
```

That's it. No build step. No dependencies. No server. The film auto-plays on load.

## Controls

The bottom bar lets you navigate during the 3:36 runtime:

- ↺ Restart
- ⏮ Previous scene
- ⏸ / ▶ Pause / Play
- ⏭ Next scene

## Structure

| Segment | Runtime |
|---|---|
| Opening title | 3 sec |
| Scene 1 — Adam Hossam, 12, planning London hackathon | 30 sec |
| Scene 2 — Hossam (his father) closing Q3 at the office | 47 sec |
| Scene 3 — Two universes split: termination vs Trust 0 evidence | 66 sec |
| Demo — Trust 0 product walkthrough (7 stages) | 60 sec |
| Final closing — KPI clause + Godfather quote + logo | 10 sec |

## How IBM Bob was used

See `bob_sessions/` folder for the exported task history and screenshots from the IBM Bob session that produced the bulk of this build. Bob acted as the development partner, scaffolding the HTML structure, generating CSS animations, and writing the scene state-machine logic. Iteration with Bob across multiple turns produced the final form, with Claude (Anthropic) used in parallel as a creative writing partner to shape the story arc.

## Architecture

Single HTML file with three layers:

1. **Stage layer.** Two side-by-side macOS-style laptop frames rendered with HTML/CSS, each with their own clock, battery, app indicator, and desktop content area. The pause-on-one-side, play-on-the-other technique is achieved by toggling a CSS class that applies opacity 0.55 + grayscale 0.6 + frozen clock indicator.

2. **Scene controller (vanilla JS).** Each scene is a function that sequences DOM mutations through `scheduleAt(ms, fn)` — a wrapper around setTimeout that tracks handles for global pause/cancel. State lives in module variables (currentScene, isPaused, timeoutHandles, pausedTimeouts).

3. **Demo stage.** Separate full-screen overlay that takes over for the product walkthrough. Each of the 7 stages renders its content into a single `#demo-content` container.

## Why Trust 0

Existing performance tools (Workday, BetterWorks, Lattice) ingest whatever KPIs the customer provides and visualize them. Garbage in, dashboard out. Trust 0 is structurally different: it interrogates the authority chain behind each KPI before accepting it. If Hossam in Sales is being measured on collection rate, Trust 0 traces the actual authority chain — Customer pays → Operations records → Operations reports → Sales credited — and surfaces that 75% of the authority sits with Operations, not Sales.

When Q3 underperforms, Trust 0 distributes the consequence to where the authority lived. Hossam loses 3 points for edge cases he could have followed up on. Michael in Operations loses 17 points for the structural failure he was hiding. Same data. Different accountability. That's the integrity layer.

## License

Source code: MIT.
Story, names, and creative content: © 2026 Mohamed Hossam Eldin Aboutaleb. Used here under the IBM Dev Day Hackathon submission terms.

## Contact

Mohamed Hossam Eldin Aboutaleb
Manama, Bahrain
