# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Classic Asteroids arcade game clone — vanilla HTML5 Canvas, pure JavaScript (ES6+), zero dependencies, no build tools.

## Running

Open `index.html` directly in a browser, or serve with:

```
npx serve .
```

No build step, no package install, no compilation.

## Architecture

All game logic lives in `game.js` (single file, no modules). Key classes: `Ship`, `Asteroid`, `Bullet`, `Particle`. Each has `update(dt)` and `draw()` methods.

Game state machine: `'playing'` | `'dead'` | `'gameover'`

Canvas is fixed at 800×600px. Objects use toroidal wrapping (`wrap()` utility).

## Code Style

- `'use strict'` at the top of `game.js`
- Spanish comments and some Spanish variable names throughout — keep this consistent
- Utility functions (`wrap`, `dist`, `rand`, `randInt`) live at the top of `game.js`
- No linter or formatter configured — no need to run any format command

## Key Constants (game.js)

- Bullet speed: 520 px/s; shoot cooldown: 0.2s
- Ship thrust: 260 px/s²; drag: 0.987; rotation: 3.5 rad/s
- Invincibility on respawn: 3 seconds (blink effect)
- Asteroid sizes: 3 tiers, indexed 0–2 for radius/speed/points
- Delta-time clamped to 50ms max to prevent physics tunneling on tab focus

## No Tests

There is no test suite. Verify changes by running the game in a browser.
