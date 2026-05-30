# 🐱 CAT-MAN

A browser-based arcade game inspired by the classic Pac-Man, with a feline twist. You play as Cat-Man — an orange tabby on a mission to catch mice while dodging dogs through a neon-lit maze. Fully playable on desktop and mobile.

## 🎮 Gameplay

Navigate Cat-Man through a tile-based maze, gobbling up dots and collecting power pellets. Clear every dot on the board to advance to the next level.

- **Dogs** are your enemies — avoid them or they'll cost you a life
- **Power Pellets** (large glowing orbs) flip the script: dogs turn into scared **mice**, and Cat-Man becomes the hunter
- **Bonus Fish 🐟** are hidden in the ghost house — grab one for a big point bonus
- Eat a scared mouse for **200 bonus points**, shown as a floating score popup
- Clear all dots to advance — levels get progressively faster

## 🕹️ Controls

| Input | Action |
|-------|--------|
| `Arrow Keys` or `WASD` | Move Cat-Man |
| Swipe (mobile) | Move Cat-Man |
| `Enter` or `Space` | Start / Restart game |
| `P` | Pause / Resume |
| 🔊 Button | Toggle mute |

## 🏆 Scoring

| Action | Points |
|--------|--------|
| Regular dot | 10 |
| Power pellet | 50 |
| Bonus fish 🐟 | 500 |
| Eating a scared mouse | 200 |

Your high score is saved to **localStorage** and persists between sessions.

## ✨ Features

- **3 unique maze layouts** — Level 1, 2, and 3 each have a distinct design; Level 4+ reuse Layout 3 with increasing speed
- **Mobile support** — swipe controls, viewport meta tag, and touch-action handling prevent scroll interference
- **Mute button** — toggle sound on/off at any time
- **Bonus fish tiles** — hidden collectibles worth 500 points per level
- **Floating score popups** — points animate and fade out at the point of collection
- **FM synthesis audio** — all sound effects are procedurally generated cat-like meows using the Web Audio API
- **Persistent high score** — saved to localStorage across sessions
- **Power pellet mode** — animated progress bar, glowing canvas border, and a flashing low-power warning
- **Frame-rate independent game loop** — uses a fixed timestep accumulator for consistent speed across devices
- Four enemies with unique speeds and chase probabilities, each with direction-aware eye animations

## 🚀 Getting Started

No build tools, no dependencies — just open the file in a browser.

```bash
# Clone the repo
git clone https://github.com/your-username/cat-man.git

# Open the game
open catman-game.html
```

Or simply download `catman-game.html` and double-click it. Works on any modern browser — Chrome, Firefox, Safari, Edge.

## 🗂️ Project Structure

The entire game is self-contained in a single HTML file:

```
catman-game.html
├── CSS          — Layout, HUD, power bar, Press Start 2P font, mobile styles
├── Game logic   — Tile maps (3 levels), movement, collision, scoring, localStorage
├── Rendering    — Canvas drawing for Cat-Man, dogs, mice, fish, floating texts
└── Audio        — FM synthesis sound effects via Web Audio API
```

## 🛠️ Technical Notes

- Movement is fully **tile-based**: Cat-Man steps one cell at a time on a fixed timer for crisp arcade-style control
- The game loop uses a **fixed timestep accumulator** (`MS_PER_TICK = 1000/60`) so speed stays consistent regardless of display refresh rate
- Each of the four enemies has an independent move timer, unique `chaseP` (chase probability), and a 12-tile activation range before switching to random wandering
- The left/right tunnel on row 10 wraps both Cat-Man and enemies across the board
- **Power pellet duration:** 15 seconds (900 ticks); the bar flashes red in the final 3 seconds
- **High score** is read from and written to `localStorage` under the key `catman_hiscore`
- All audio is generated with FM synthesis (carrier + modulator oscillators) — no audio files required

## 📄 License

MIT — free to use, modify, and distribute.
