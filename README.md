# 🐱 CAT-MAN

A browser-based arcade game inspired by the classic Pac-Man, with a feline twist. You play as Cat-Man — an orange tabby on a mission to catch mice while dodging dogs through a neon-lit maze.

## 🎮 Gameplay

Navigate Cat-Man through a tile-based maze, gobbling up mice and collecting power pellets. Clear every dot on the board to advance to the next level.

- **Mice** are your enemies — avoid them or they'll cost you a life
- **Power Pellets** (large glowing orbs) flip the script: mice transform into scared **dogs**, and Cat-Man turns the hunter
- Eat a scared dog for **200 bonus points**
- Clear all dots to advance — levels get progressively faster

## 🕹️ Controls

| Key | Action |
|-----|--------|
| `Arrow Keys` or `WASD` | Move Cat-Man |
| `Enter` or `Space` | Start / Restart game |
| `P` | Pause / Resume |

## 🏆 Scoring

| Action | Points |
|--------|--------|
| Regular dot | 10 |
| Power pellet | 50 |
| Eating a scared dog | 200 |

Your high score is tracked for the session.

## ✨ Features

- Two unique maze layouts (Level 1 & 2); Level 3+ reuse Layout 2 with increasing speed
- Smooth tile-based movement with pixel interpolation
- Four enemies (Blinky, Pinky, Inky, Clyde), each with their own speed and chase probability
- Power pellet mode with animated progress bar, glowing canvas effect, and a countdown flash warning
- Web Audio API sound effects (dot collection, power-up, death sequence)
- Lives system — 3 lives per game
- Persistent high score display within the session

## 🚀 Getting Started

No build tools, no dependencies — just open the file in a browser.

```bash
# Clone the repo
git clone https://github.com/your-username/cat-man.git

# Open the game
open catman-game.html
```

Or simply download `catman-game.html` and double-click it.

**Browser support:** Any modern browser with HTML5 Canvas and Web Audio API support (Chrome, Firefox, Safari, Edge).

## 🗂️ Project Structure

The entire game is self-contained in a single HTML file:

```
catman-game.html
├── CSS          — Layout, HUD styling, power bar, animations
├── Game logic   — Tile map, movement, collision detection, scoring
├── Rendering    — Canvas drawing for Cat-Man, mice, dogs, and maze
└── Audio        — Procedural sound effects via Web Audio API
```

## 🛠️ Technical Notes

- Movement is fully **tile-based**: Cat-Man steps one cell at a time on a fixed timer, giving the crisp feel of the original arcade game
- Each ghost has an independent move timer and a unique `chaseP` (chase probability), making some enemies more aggressive than others
- Ghost AI chases Cat-Man within 10 tiles; beyond that range it wanders randomly
- The tunnel on row 10 wraps Cat-Man (and ghosts) from one side of the board to the other
- Power pellet duration: **15 seconds** (900 frames at 60 fps)

## 📄 License

MIT — free to use, modify, and distribute.
