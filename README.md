# 道地南蠻 Tainan Barbarians (Pygame)

A tiny Pixel-Art Shoot-’em-Up born from a **vibe-coding** assignment.
You play as a drifting mouth that switches between **Salty** and **Sweet** moods to eat matching foods.
Eat the wrong thing and you get nauseous. Eat enough right things and you feel spiritually validated.

## Controls

* Arrows or WASD: Move
* Space: Toggle Salty/Sweet, also Start/Restart
* Esc: Retreat from the culinary battlefield

## Rules

Match the flavor or suffer the consequences.

**Salty (Pale Blue #A7D3FF)**

* Doritos (triangle)
* Burgers (rounder, slightly clingy)
* Fries (skinny rectangles)

**Sweet (Pink #FF9ECF)**

* Ice cream (circle)
* Soda (tall rectangle)
* Cake (trapezoid, also mildly clingy)

Mechanics:

* Wrong eat: +20 nausea
* Nausea slowly fades at 2 per second
* Hit 100 nausea and it’s game over
* +1 score per correct eat
* Level clears at 20 correct eats
* Every run uses RNG seed 42, because chaos should at least be consistent

## Tech

* Python 3.10+
* pygame (latest stable)
* 600x900 portrait gameplay
* 60 FPS of pure dietary regret

## Run

```
pip install -r requirements.txt
python main.py
```

### Headless smoke test (for CI or quiet suffering)

```
# Windows PowerShell
set SDL_VIDEODRIVER=dummy; python main.py --headless 2
```

## Notes

* All sprites are geometric shapes pretending to be pixel art.
* The neck is a decorative polyline with a tiny sinusoidal wiggle because animation is expensive but vibes are free.

## Display scaling, DPI, and letterboxing

* Game renders at 600x900, then scales with aspect-preserving letterboxing.
* Integer scaling by default for crisp pixels.
  Enable smooth scaling with:

  ```
  python main.py --smooth-scale
  ```
* Window size adapts to your display (margin 0.95) and is fully resizable.
* DPI awareness on Windows is attempted but not guaranteed.

### Minimal usage example

```python
from nanmon.display_manager import DisplayManager

dm = DisplayManager(margin=0.95, use_integer_scale=True, caption="Game")
frame = dm.get_logical_surface()

frame.fill((0,0,0,0))
# draw your masterpiece here...

dm.present()
```
