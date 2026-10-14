# Browser Escape Games

Two self-contained HTML5 browser games — no install, no dependencies.

## Games

- **[Dash to Safety](game1.html)** — Horizontal runner. Dodge obstacles, survive to 2000m.
- **[Vertical Escape](game2.html)** — Falling-dodge. Slide left/right, survive 60 seconds.

## Controls

### Game 1 — Dash to Safety
| Input | Action |
|---|---|
| Arrow Up / W | Move up |
| Arrow Down / S | Move down |
| Space | Start / Restart |
| P | Pause |
| Tap top half | Move up (mobile) |
| Tap bottom half | Move down (mobile) |

### Game 2 — Vertical Escape
| Input | Action |
|---|---|
| Arrow Left / A | Move left |
| Arrow Right / D | Move right |
| Space | Start / Restart |
| P | Pause |
| Tap left half | Move left (mobile) |
| Tap right half | Move right (mobile) |

## Game Mechanics

### Dash to Safety
- Player is a green circle fixed at X=80, moving vertically
- Red rectangle obstacles scroll from right to left
- 3 lives — hit an obstacle, lose 1 life + 1 sec invincibility
- Speed and spawn rate increase every 400m
- Reach 2000m to win

### Vertical Escape
- Player is a blue rectangle at the bottom, moving horizontally
- Coloured circle obstacles fall from top
- 3 lives — collision costs 1 life + 1.5 sec invincibility
- Survive 60 seconds to win (progress bar fills)
- Difficulty ramps every 15 seconds

## Developer Notes

- Pure vanilla ES6, no external dependencies
- Each game is fully self-contained in a single HTML file
- Canvas: Game 1 = 800×400px | Game 2 = 480×640px
- State machine: `start | playing | win | lose | paused`
- AABB collision (Game 1), Circle-AABB collision (Game 2)
- Responsive canvas scaling via CSS (max-width 100%)

## Running Locally

Drop any of the HTML files into a browser — no server required.
Or serve the folder with any static host (GitHub Pages, Netlify, Vercel).
