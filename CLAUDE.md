# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-file browser-based Tic Tac Toe game — all HTML, CSS, and JS live in `tictactoe.html`. No build tools, no dependencies.

## Running the Game

Open `tictactoe.html` directly in any modern browser, or use the configured Claude Code command:

```
cmd.exe /c start "" "C:\Users\Nir\claude_test\tictactoe.html"
```

## Version Control

After completing any meaningful unit of work, commit and push to GitHub so progress is never lost:

- **Remote:** https://github.com/NirEllor/claude_test
- **Branch:** `master`

```bash
git add <specific-files>
git commit -m "short, descriptive message in imperative mood"
git push
```

Commit messages should describe *what* changed and *why* in plain English (e.g., `"add draw detection logic"`, `"fix win check not clearing on reset"`). Commit at logical checkpoints — after a feature is working, a bug is fixed, or a refactor is complete — not after every line edit.

## Architecture

Everything is in `tictactoe.html` as one self-contained file:

**State variables:**
- `board` — 9-cell array (`''`, `'X'`, or `'O'`)
- `current` — whose turn (`'X'` or `'O'`)
- `over` — boolean, game ended
- `scores` — `{ X, O, draw }` persisted across resets

**Key functions:**
- `init()` — resets board for a new game (scores persist)
- `checkWin()` — tests the 8 win combinations in `WINS` constant
- Cell click handlers — place mark, check win/draw, swap turn

**Win combinations** (`WINS`): rows `[0,1,2]`, `[3,4,5]`, `[6,7,8]`, columns `[0,3,6]`, `[1,4,7]`, `[2,5,8]`, diagonals `[0,4,8]`, `[2,4,6]`.

**Styling:** Dark theme (`#1a1a2e` background), X in red (`#e94560`), O in blue (`#a8dadc`). Winning cells get a CSS pulse animation.
