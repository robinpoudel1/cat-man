# 🐱 CAT-MAN

A browser-based arcade game inspired by the classic Pac-Man, with a full feline twist. You play as **Cat-Man** — an orange tabby navigating a neon-lit maze, chasing mice and fleeing angry dogs.

🔴 **Live Demo:** [robinpoudel1.github.io/cat-man](https://robinpoudel1.github.io/cat-man)

---

## 🎮 How It Works

You are a cat. The maze is full of **angry dogs** that chase you. Collect all the fish pellets to clear the level — but avoid the dogs or you'll lose a life.

Eat a **power pellet** (glowing gold orb) and the whole dynamic flips:

- Dogs transform into **colourful scared mice** 🐭
- The **revival zone lights up** with a danger warning — mice eaten there revive instantly as dogs!
- You have **15 seconds** to hunt them down before they turn back

---

## 🕹️ Controls

| Key | Action |
|-----|--------|
| `Arrow Keys` / `WASD` | Move Cat-Man |
| `Enter` / `Space` | Start / Restart |
| `P` | Pause / Resume |

---

## 🏆 Scoring

| Action | Points |
|--------|--------|
| Fish pellet (dot) | 10 |
| Power pellet | 50 |
| Eating a scared mouse | 200 |

High score is tracked for the session.

---

## ⚡ Power Pellet Mode

When Cat-Man eats a power pellet, the following happen simultaneously:

1. **Screen flashes** orange → gold → white burst on the canvas
2. **Canvas border** glows bright gold
3. **Progress bar** appears below the HUD showing time remaining
4. **"🐭 POWER MODE — MICE APPEAR! EAT THEM!"** indicator blinks
5. All dogs on the map **transform into colourful scared mice** with X eyes and sparkles ✦
6. The **revival zone** (ghost house) shows a pulsing red dashed border with ⚠ warning and 💀 skull icons
7. In the **last 3 seconds**, the bar and border flash yellow as a warning
8. When power expires, mice snap back to angry dogs 🐶

> ⚠️ **Revival Zone rule:** Even if you eat a mouse inside the marked revival zone, it respawns immediately as a dog at that same spot. Stay out!

---

## 👾 The Dogs (Enemies)

| Name | Colour | Chase % | Speed |
|------|--------|---------|-------|
| Blinky | 🔴 Red | 40% | Fastest |
| Pinky | 🩷 Pink | 30% | Fast |
| Inky | 🩵 Cyan | 25% | Medium |
| Clyde | 🟠 Orange | 20% | Medium |

- Dogs only **actively chase** within 10 tiles — beyond that they wander randomly
- Each dog has its own **independent move timer** so they never move in sync
- Cat-Man is always **~2× faster** than the fastest dog

---

## 🗺️ Levels

| Level | Maze | Speed |
|-------|------|-------|
| 1 | Classic layout | Base |
| 2 | New layout — tighter corridors | +1 |
| 3+ | Level 2 layout repeats | Increases every 2 levels |

---

## 🚀 Getting Started

No build tools or dependencies — one HTML file, runs entirely in the browser.

```bash
# Clone the repo
git clone https://github.com/robinpoudel1/cat-man.git

# Open the game
open index.html
```

Or visit the live demo: **[robinpoudel1.github.io/cat-man](https://robinpoudel1.github.io/cat-man)**

**Browser support:** Chrome, Firefox, Safari, Edge (any modern browser with HTML5 Canvas + Web Audio API)

---

## 🗂️ Project Structure

```
index.html          # Entire game — self-contained, no dependencies
README.md           # This file
```

### Inside `index.html`

| Section | Description |
|---------|-------------|
| `<style>` | Dark arcade UI, HUD, power bar, animations |
| `MAPS[]` | Two 21×21 tile maps (0=open, 1=wall, 2=dot, 3=power pellet, 4=revival zone) |
| `initGame()` | Resets all state for a fresh game |
| `stepPac()` | Tile-based movement with queued input — one tile per timer tick |
| `stepGhost(g)` | Per-dog AI: chase within 10 tiles or wander randomly |
| `checkDots()` | Pellet collection, power mode trigger, level-clear detection |
| `checkCollisions()` | Dog/mouse-Cat-Man hit detection (tile-exact) |
| `activatePowerUI()` | Canvas flash, progress bar, indicator, sound burst |
| `loop(timestamp)` | Fixed-timestep RAF loop — runs at 60fps logic on any display Hz |
| `draw()` | Full canvas render including revival zone caution overlay |
| Audio | Procedural Web Audio API — zero audio files |

---

## ⚙️ Technical Notes

- **Fixed timestep loop** — game logic always runs at exactly 60fps regardless of display refresh rate (60Hz, 120Hz, 144Hz). Uses an accumulator pattern to prevent speed variation across devices.
- **Tile-based movement** — Cat-Man and dogs each move one tile per timer step. Input is queued so turns register at the next valid junction.
- **Revival zone** — tile type `4` (empty, no dot). During power mode these tiles pulse red and the zone is outlined with a dashed danger border.
- **Per-ghost timers** — each dog has its own `moveTimer` and `spd` so they never clump or synchronise.
- **Power duration** — 15 seconds (900 ticks at 60fps). Warning kicks in at 180 ticks (~3s) remaining.
- **Zero dependencies** — no npm, no frameworks, no CDN calls except Google Fonts.

---

## 📋 Changelog

| Version | Changes |
|---------|---------|
| v6 | Revival zone caution overlay — pulsing border, ⚠ label, 💀 skulls during power mode |
| v5 | Swapped enemies: dogs are now normal, colourful mice appear during power mode |
| v4 | Fixed-timestep loop — consistent speed on all devices and GitHub Pages |
| v3 | Power pellet UI — canvas flash, progress bar, blinking indicator, sound burst |
| v3 | Full Cat-Man reskin — cat face with ears/whiskers, dog/mouse characters |
| v2 | Per-ghost independent timers, 65/35 chase/random AI, 10-tile chase range |
| v2 | Ghost speeds fixed — all dogs 2× slower than Cat-Man |
| v1 | Tile-based movement rebuild — fixed arrow key controls |
| v0 | Initial Pac-Man build |

---

## 🛠️ Vibe Coding Workflow

Built iteratively with **Claude AI** (Perplexity) using natural language prompts — no manual coding:

1. *"Build a Pac-Man game as a single HTML file"*
2. *"Arrow keys aren't moving Pac-Man"*
3. *"Make it Cat-Man — cat, mice, dogs"*
4. *"Swap mice and dogs so dogs are the normal enemies"*
5. *"Show a revival zone caution area during power mode"*
6. *"The game runs too fast on GitHub Pages"* → fixed with timestep loop

> **Tip for vibe coding:** Describe behaviour, not code. One feature at a time. The README and changelog are your spec — keep them updated as you go.

---

## 📄 License

MIT — free to use, modify, and distribute.
