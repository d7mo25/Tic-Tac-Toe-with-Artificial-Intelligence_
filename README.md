# Tic-Tac-Toe with Artificial Intelligence

A collection of Python Tic-Tac-Toe implementations, ranging from a two-player console game to a graphical Human-vs-AI version with a rule-based decision engine.

## Contents

| File | Description | Interface | Mode |
|---|---|---|---|
| [`Tic-Tac-Toe-AI_Animated.py`](#tic-tac-toe-ai_animatedpy) | GUI game against a scripted AI opponent | Tkinter | Human vs AI |
| [`tic_tac_toe_AI_Structural.py`](#tic_tac_toe_ai_structuralpy) | Console game against a random-move AI | Terminal | Human vs AI |
| [`multiplayer.py`](#multiplayerpy) | Console game for two human players | Terminal | Human vs Human |

## Requirements

- Python 3.x
- `tkinter` (only required for `Tic-Tac-Toe-AI_Animated.py` — included with most standard Python installs)

No third-party packages are needed; every script relies solely on the standard library (`tkinter`, `random`).

## Getting Started

Clone or download the repository, then run any script directly with Python:

```bash
python Tic-Tac-Toe-AI_Animated.py
python tic_tac_toe_AI_Structural.py
python multiplayer.py
```

---

## `Tic-Tac-Toe-AI_Animated.py`

A graphical Tic-Tac-Toe game built with `tkinter`, played against a computer opponent.

**Features**
- 3x3 grid of buttons rendered on a dark-themed canvas
- Choice of who plays first: **Machine vs Human** or **Human vs Machine**
- Reset button to start a new round without restarting the program
- Win/draw detection with a popup message box announcing the result

**How the AI works**

Rather than searching a game tree (e.g. minimax), the computer's moves are driven by a fixed set of response rules keyed to the move number and the opponent's move history (`surrounding_store`, `prob`, and `technique` track which strategy branch to follow). The AI recognizes common opening patterns — center, corner, and edge plays — and responds to block or set up a win accordingly, falling back to a random legal move when no rule applies.

**Run it**

```bash
python Tic-Tac-Toe-AI_Animated.py
```

Click **Human vs Machine** or **Machine vs Human** to start, then click any empty square to place your mark. Use **Reset** to play again.

---

## `tic_tac_toe_AI_Structural.py`

A lightweight, console-based Tic-Tac-Toe game against a computer opponent that plays random legal moves.

**Features**
- Text-rendered 3x3 board printed after every move
- Player always plays `X`; the computer plays `O`
- Detects rows, columns, diagonals, and ties
- Simple, readable structure — useful as a starting point for learning game logic in Python

**How the AI works**

The computer (`computer()` function) picks a random empty cell (`random.randint(0, 8)`) on its turn — there is no strategic evaluation, making this version a good baseline to compare against the rule-based AI in `Tic-Tac-Toe-AI_Animated.py`.

**Run it**

```bash
python tic_tac_toe_AI_Structural.py
```

Enter a number from 1–9 when prompted to place your mark in the corresponding board position:

```
 1 | 2 | 3
 4 | 5 | 6
 7 | 8 | 9
```

---

## `multiplayer.py`

A console-based, two-player Tic-Tac-Toe game — no AI involved.

**Features**
- Prompts for both players' names at the start
- Player 1 is assigned `X` and always goes first; Player 2 is assigned `O`
- Validates input (rejects out-of-range numbers and already-taken spots)
- Prints the board after every move
- Announces the winner by name, or declares a tie if all 9 spots fill without a winner

**Run it**

```bash
python multiplayer.py
```

Follow the prompts to enter both player names, then take turns entering a spot number (1–9) to place your sign.

---

## Notes

- The GUI script (`Tic-Tac-Toe-AI_Animated.py`) shares its underlying AI logic with the version documented in the accompanying project report and slide deck; it is a heuristic, pattern-matching opponent rather than a full minimax/alpha-beta search, despite the "Artificial Intelligence" naming across the project.
- `tic_tac_toe_AI_Structural.py` contains a couple of known quirks in its win-checking helpers (e.g. `checkRow` reports the wrong winner for the right-column case) — worth a look if you're using this file to practice debugging.
