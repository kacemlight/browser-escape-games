# Browser Escape Games

Two self-contained browser-based obstacle dodge games built with vanilla HTML5 Canvas and JavaScript. No install, no server, no dependencies.

**[Play index.html](index.html)** to access both games from the landing page.

---

## Games

### Game 1 — Dash to Safety
> Horizontal side-scrolling runner. Dodge red obstacles rushing from the right. Survive to 2000m.

| Property | Value |
|---|---|
| Canvas | 800 × 400 px |
| Player | Green circle, 30px diameter (`#00E676`) |
| Win condition | Reach 2000m distance |
| Lives | 3 |
| Obstacles | Red rectangles, scroll left |
| Invincibility | 1 second after hit |

### Game 2 — Vertical Escape
> Top-down falling obstacle dodge. Avoid debris raining from the top. Survive 60 seconds.

| Property | Value |
|---|---|
| Canvas | 480 × 640 px |
| Player | Blue rectangle, 40×20 px (`#2979FF`) |
| Win condition | Survive 60 seconds (progress bar fills) |
| Lives | 3 |
| Obstacles | Coloured circles, fall from top |
| Invincibility | 1.5 seconds after hit |

---

## Controls

### Game 1 — Dash to Safety
| Input | Action |
|---|---|
| Arrow Up / W | Move up |
| Arrow Down / S | Move down |
| Space / Enter | Start or restart |
| P | Pause / resume |
| Tap top half (mobile) | Move up |
| Tap bottom half (mobile) | Move down |

### Game 2 — Vertical Escape
| Input | Action |
|---|---|
| Arrow Left / A | Move left |
| Arrow Right / D | Move right |
| Space / Enter | Start or restart |
| P | Pause / resume |
| Tap left half (mobile) | Move left |
| Tap right half (mobile) | Move right |

---

## Difficulty Scaling

Both games ramp difficulty over time. New speed/spawn levels unlock automatically:

**Game 1 — Dash to Safety**
| Distance Band | Scroll Speed | Spawn Interval |
|---|---|---|
| 0–399m | 3 | 80 frames |
| 400–799m | 4 | 70 frames |
| 800–1199m | 5 | 60 frames |
| 1200–1599m | 6 | 50 frames |
| 1600–2000m | 7 | 45 frames |

**Game 2 — Vertical Escape**
| Time Band | Fall Speed | Spawn Interval |
|---|---|---|
| 0–14s | 2.5 | 50 frames |
| 15–29s | 3.5 | 40 frames |
| 30–44s | 4.5 | 32 frames |
| 45–59s | 5.5 | 26 frames |
| 60s+ | 6.5 | 22 frames |

---

## Technical Architecture

- **Language:** Vanilla ES6 JavaScript (no frameworks, no CDN imports)
- **Rendering:** HTML5 Canvas 2D API
- **State machine:** `start | playing | win | lose | paused` — both games use identical flow
- **Collision detection:**
  - Game 1: AABB (axis-aligned bounding box) with 4px forgiveness border
  - Game 2: Circle vs. AABB closest-point algorithm
- **Timing:** Game 2 uses `requestAnimationFrame` timestamps for accurate delta-time survival tracking
- **Mobile:** Touch events map to half-screen taps for directional input

---

## File Structure

```
browser-escape-games/
├── index.html    # Landing page — links to both games
├── game1.html    # Dash to Safety (horizontal runner)
├── game2.html    # Vertical Escape (falling-dodge)
└── README.md     # This file
```

---

## Running the Games

**Locally:** Open any `.html` file directly in a browser. No web server required.

**Static host (GitHub Pages, Netlify, Vercel etc.):**
1. Upload the folder contents to your host root
2. Point the domain to `index.html`
3. All three games work immediately — no build step

---

## Developer Notes

- All game files are fully self-contained — no external assets loaded
- Each file is under 20 KB for fast loading
- Colours follow a consistent palette: `#1A1A2E` bg, `#FFD600` accent, `#00E676` G1 player, `#2979FF` G2 player
- To modify difficulty: edit the `BANDS` array at the top of each file
- To change canvas dimensions: update the `W`/`H` constants and adjust the CSS `max-width`/`max-height` as needed
- Adding sound effects: hook into collision events (`player.inv` transitions from 0 to 60) and call `AudioContext.play()`
