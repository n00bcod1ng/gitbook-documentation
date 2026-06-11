---
description: >-
  A Node.js CLI tool that renders text and pixel art onto the GitHub
  contribution graph using backdated commits, with a live terminal preview
  before anything is written.
---

# greenMachine

greenMachine turns the GitHub contribution graph into a canvas. Pass it any word and it renders that text as pixel art on the graph by generating backdated Git commits — one or more per "lit" pixel.

The standout feature is safety-first rendering: it **previews the pattern in the terminal and asks for confirmation before committing anything**, so misaligned letters are caught before hundreds of commits get pushed.

Source code: [github.com/n00bcod1ng/greenMachine](https://github.com/n00bcod1ng/greenMachine)

### How It Works

A GitHub contribution graph is a 7-row × ~52-column grid: 7 rows for the days of the week (Sunday at top) and 52 columns for the weeks of the year. Each cell's shade is driven by how many commits share that date — and GitHub counts contributions by a commit's **author date**, not its push date, which is the mechanism that makes backdated rendering possible.

The build breaks down into four parts:

1. **A pixel font** (`font.js`) — every character is hand-defined as a 7-row binary matrix. Letters are 5 cells wide, some glyphs (like `I`) are narrower, and the emoji-style glyphs (`<3`, `:)`) are 11 wide.
2. **A layout engine** (`pattern.js`) — tokenizes the input string (handling multi-character glyphs like `<3`), stitches the glyphs together with 1-column gaps, and produces a single combined grid.
3. **Date mapping** — each lit pixel at `(row, col)` maps to a real calendar date: `graphStart + (col × 7 days) + row days`, where `graphStart` is the Sunday that begins the target year's graph.
4. **The CLI** (`index.js`) — argument parsing, the preview/confirm flow, recursive async commits, and a history-wipe command.

### Key Features

* **Full CLI** — control everything with flags: `--word`, `--year`, `--intensity`, `--start`
* **Live terminal preview** — see the exact pattern and commit count before anything is written
* **Complete font** — full A–Z, 0–9, space, `!`, plus special glyphs `<3` (heart) and `:)` (smiley)
* **Auto-centering** — patterns are centered on the graph unless a start week is specified
* **Intensity control** — 1–5 commits per pixel to control the shade of green
* **Built-in wipe command** — `--clear <year>` resets the repo to a clean slate
* **Shuffled commits** — commits are randomized before pushing so history isn't written in pixel order

### Prerequisites

* Node.js v18+
* A new, empty repository dedicated to the tool
* Git configured with the email tied to your GitHub account

{% hint style="danger" %}
greenMachine rewrites commit history. Run it only against a throwaway repository — never a real project.
{% endhint %}

### Setup

```bash
git clone https://github.com/n00bcod1ng/greenMachine.git
cd greenMachine
npm install
```

### Usage

```bash
# Paint "HACK" across 2025
node index.js --word "HACK" --year 2025 --intensity 4

# Drop a smiley face on 2026 (auto-centered)
node index.js --word ":)" --year 2026

# Place a heart at a specific starting week
node index.js --word "<3" --year 2026 --start 20

# Wipe everything and start fresh
node index.js --clear 2025
```

Before writing any commits, the tool shows exactly what will land on the graph:

```
  Word:       "HACK"
  Year:       2025
  Intensity:  4 commits/pixel
  Width:      23 weeks  (starts at week 1)

■ · · · ■ · · ■ ■ ■ · · · ■ ■ ■ · · ■ · · · ■
■ · · · ■ · ■ · · · ■ · ■ · · · ■ · ■ · · ■ ·
■ · · · ■ · ■ · · · ■ · ■ · · · · · ■ · ■ · ·
■ ■ ■ ■ ■ · ■ ■ ■ ■ ■ · ■ · · · · · ■ ■ · · ·
■ · · · ■ · ■ · · · ■ · ■ · · · · · ■ · ■ · ·
■ · · · ■ · ■ · · · ■ · ■ · · · ■ · ■ · · ■ ·
■ · · · ■ · ■ · · · ■ · · ■ ■ ■ · · ■ · · · ■

  Total commits to create: 248

Proceed and write these commits? (y/n)
```

### CLI Options

* `--word` / `-w` — text to render (A–Z, 0–9, space, `!`, `<3`, `:)`)
* `--year` / `-y` — target year (default: current year)
* `--intensity` / `-i` — commits per pixel, 1–5, controls green shade (default: `4`)
* `--start` / `-s` — starting week column; omit to auto-center
* `--clear` — wipe all commit history for a clean slate
* `--yes` — skip the confirmation prompt
* `--help` / `-h` — show usage

{% hint style="info" %}
GitHub may take a few minutes to update the graph after pushing. If the pattern doesn't appear, toggle **Private contributions** in profile settings to force a re-sync.
{% endhint %}

### Lessons Learned

* GitHub counts contributions by a commit's author date, not its push date.
* `moment().day(n)` snaps to the *nearest* matching weekday and silently shifts pixels by a week. Switching to `.add(n, "days")` from a fixed Sunday anchor fixed alignment bugs that were impossible to spot until commits were already pushed — which is exactly why the preview step earns its keep.
* Each commit has to fully complete before the next begins, otherwise Git throws `index.lock` errors. Recursive async callbacks enforce that ordering.

### Tech Stack

* **Node.js (ES modules)** — runtime
* **simple-git** — programmatic Git commits and pushes
* **moment.js** — date calculation and contribution-graph alignment
* **jsonfile** — writing the commit payload to disk
* **readline (built-in)** — interactive confirmation prompt

### Credits

Inspired by [fenrir2608/goGreen](https://github.com/fenrir2608/goGreen) (the original backdated-commit concept) and [mattrltrent/github\_painter](https://github.com/mattrltrent/github_painter) (the idea of painting deliberate designs), reworked into a single text-driven CLI with a safety-first preview step.
