# Math-Flow (30s Mental Maths)

A small, static **mental-math chain game** in a single HTML file. You start from a number, swipe through a sequence of operations (add, subtract, multiply, divide, fractions, percentages, roots, and more), keep a running total in your head, then type the final answer. A **30-second** bar runs while you play; finish in time for a “spot on” result.

**Live demo:** [mercedessm.github.io/Math-Flow](https://mercedessm.github.io/Math-Flow/) (if this repo is published there).

## How to run locally

No build step or dependencies. Open `index.html` in a browser, or serve the folder with any static server (e.g. `npx serve .`) for a more realistic mobile experience.

## How to play

1. Read the **first card** (your starting number).
2. **Swipe left** to reveal each next step; the timer starts when you begin swiping.
3. Apply every operation to your **running total** (nothing is written on the cards).
4. On the last card, **enter the final number** and submit. You get a few wrong tries before the run ends.
5. Use **Show answer** to reveal the full step-by-step breakdown.

## Modes

| Mode | Description |
|------|-------------|
| **Daily Challenge** | The puzzle is **deterministic for a given calendar day** (seeded from the date). **Everyone gets the same daily** on that day. Before building the chain, a **difficulty tier** is rolled with the same seed: roughly **~18%** Beginner, **~77%** Medium, **~5%** Hard (tweak `DAILY_EASY_CUTOFF` / `DAILY_MEDIUM_CUTOFF` in `index.html` if you want a different mix). |
| **Practice** | You pick **Easy (Beginner)**, **Medium**, or **Hard**. Each run uses normal randomness (not the date seed), so every round is different. |

Difficulty changes **how large and how varied the numbers and operations** can be—not how long the run is: every run uses the same number of **10** operation steps after the start (see `MENTAL_ROUNDS` in the script). Operations are designed so answers stay in a sensible range; only steps that keep the running value as a **positive integer under 1000** are applied.

## Project structure

- **`index.html`** — All UI, styles, and game logic. The `MathEngine` object defines a large set of **operations** and which **pools** exist for `easy` / `medium` / `hard` / daily tier.

## Sharing results

The result screen can copy a short text summary (including the daily tier on daily runs) to the clipboard, using the public URL in the app.
