# Neon Hangman

A polished, cyberpunk-neon-themed Hangman game built with Python and
Tkinter (standard library only — no extra installs needed beyond a
Python that includes Tkinter).

## Running it

```
python main.py
```

Requires Python 3.8+ with Tkinter available (Tkinter ships by default
with the python.org installers for Windows/macOS; on Linux you may need
`sudo apt-get install python3-tk` or the equivalent for your distro).

The first run creates a `data/` folder next to the source files to store
your settings, statistics, and unlocked achievements as JSON — delete it
any time to start fresh, or use Settings → "Reset all saved data".

## What's included

- **Neon cyberpunk UI** — glowing rounded buttons, a pulsing animated
  title, a drifting particle background, and a neon on-screen keyboard
  with hover/press/correct/wrong states.
- **Custom-drawn hangman** — a progressively revealed neon stick figure
  on a proper gallows (not a plain ASCII stick figure), with a shake +
  red flash on loss and a confetti celebration on the win screen.
- **Four difficulty modes** — Easy / Medium / Hard, plus a fully
  configurable Custom Challenge (lives, hints, timer, preferred word
  length).
- **9 word categories** (Food, Places, Things, Animals, Movies, Sports,
  Technology, Countries, Science) plus Random, each word paired with a
  short definition used by the hint system.
- **Hint system** — definition, category clue, first letter, and a
  random revealed letter, each with its own score penalty and a
  difficulty-based hint budget.
- **Scoring, streaks, and a live progress/lives bar.**
- **Persistent statistics** (games played/won/lost, win %, high score,
  longest streak, favorite category/difficulty, perfect games, etc.)
  stored in `data/stats.json`.
- **10 achievements** with an in-app gallery screen and a toast popup
  the moment one is unlocked.
- **Settings screen** — sound on/off, music toggle, animation speed,
  font size, fullscreen, default hint/timer behavior, 3 selectable
  color themes (including a high-contrast/colorblind-friendly theme),
  and a full data reset.
- Keyboard shortcuts: just type A-Z during a round, no need to click.

## Project layout

```
main.py                 entry point
app.py                  App window + screen-switching controller
theme.py                color palettes / fonts
storage.py              JSON-backed settings / stats / achievements
word_database.py        categories, words, hint definitions
game.py                 core game rules & scoring (no UI code)
achievements.py         achievement catalogue + unlock checks
canvas_draw.py          neon gallows/figure drawing + confetti/shake
widgets.py              NeonButton, LetterKey, ProgressBar, Toggle
animations.py           color pulsing, particle field, toast popups
sounds.py               safe cross-platform beep-based sound effects
screens/                one file per screen (home, difficulty, category,
                         game, win, lose, settings, stats, achievements)
```

## Notes on scope

This build focuses on making the core game modes, visuals, hints,
scoring, persistence, and achievements genuinely solid and bug-free
rather than stubbing out every bonus idea in the original brief (daily
challenge, two-player mode, etc. are not included). The architecture is
modular, so those are straightforward to add later — `game.py` and
`word_database.py` in particular were kept UI-free specifically to make
extensions like that easy.
