# Snake Game 🐍

A classic Snake game built with vanilla HTML5, CSS3, and JavaScript. Single-file, zero dependencies, and ready to play!

## 📋 Table of Contents

- [English](#english)
  - [About](#about)
  - [Features](#features)
  - [Tech Stack](#tech-stack)
  - [Project Structure](#project-structure)
  - [How It Works](#how-it-works)
  - [Running Locally](#running-locally)
  - [Controls](#controls)
  - [Configuration](#configuration)
  - [Contributing](#contributing)
  - [Future Enhancements](#future-enhancements)

---

# English

## About

This is a classic Snake game implementation featuring:
- **Single-file architecture**: Everything in one HTML file - no build process needed
- **Nokia-style aesthetics**: Retro pixelated graphics with classic green snake
- **Responsive design**: Works on desktop and mobile devices
- **Zero dependencies**: Pure vanilla JavaScript, HTML5 Canvas, and CSS3

The game uses a wrap-around mechanic (snake wraps around screen edges) and includes sound effects when eating food.

## Features

- 🎮 Classic Snake gameplay
- 📱 Mobile-responsive with touch support
- 🎨 Retro pixelated graphics
- 🔊 Sound effects (Web Audio API)
- ⌨️ Keyboard controls (Arrow keys, WASD)
- 🔄 Wrap-around screen edges
- 📊 Score tracking
- 🎯 Self-collision detection

## Tech Stack

- **HTML5**: Structure and Canvas element
- **CSS3**: Styling and responsive layout
- **Vanilla JavaScript (ES6+)**: Game logic, no frameworks
- **Canvas 2D API**: Rendering

## Project Structure

```
.
├── snake-game.html          # Main game file (everything in one file)
├── snake-game-technical-spec.md  # Detailed technical documentation
├── PRD.md                   # Product Requirements Document template
└── README.md                # This file
```

The entire game is contained in `snake-game.html`:
- HTML structure in `<body>`
- CSS styles in `<style>` tag
- JavaScript game engine in `<script>` tag

## How It Works

### Game Loop Architecture

The game follows a standard game loop pattern:

```
Input → Update (tick) → Render → Repeat
```

1. **Input Handling**: Keyboard events are captured and stored in `gameState.nextDirection`
2. **Update (Tick)**: Every 150ms, the game state is updated:
   - Snake moves one cell in current direction
   - Collision detection (self-collision)
   - Food consumption check
   - Score update
3. **Render**: Every frame (60 FPS), the canvas is redrawn with current game state

### State Management

The game state is stored in a single object:

```javascript
const gameState = {
    snake: [],              // Array of {x, y} positions
    direction: 'right',     // Current movement direction
    nextDirection: 'right', // Buffered next direction (prevents 180° turns)
    food: { x: 0, y: 0 },  // Food position
    score: 0,               // Current score
    gameOver: false,        // Game state flag
    lastTick: 0            // Timestamp for tick timing
};
```

### Key Functions

- **`tick()`**: Updates game state (snake movement, collision, food)
- **`render()`**: Draws everything on canvas
- **`gameLoop(timestamp)`**: Main loop using `requestAnimationFrame`
- **`setDirection(newDir)`**: Handles input with 180° turn prevention
- **`resetGame()`**: Resets all state to initial values
- **`generateFood()`**: Creates food at random valid position
- **`checkSelfCollision(head)`**: Detects if snake hits itself

### Code Organization

The code is organized into logical sections:
1. **Configuration Constants** (`CONFIG`, `COLORS`, `DIRECTIONS`, etc.)
2. **Game State** (`gameState` object)
3. **Helper Functions** (utility functions)
4. **Game Logic** (`tick()`, collision detection)
5. **Rendering** (`render()`, `drawCell()`, `drawGameOver()`)
6. **Input Handling** (keyboard event listeners)
7. **Game Loop** (`gameLoop()`, `init()`)

## Running Locally

1. Clone or download this repository
2. Open `snake-game.html` in any modern web browser
3. That's it! No build process, no dependencies, no server needed.

You can also use a local server if preferred:
```bash
# Python 3
python -m http.server 8000

# Node.js (with http-server)
npx http-server

# Then open http://localhost:8000/snake-game.html
```

## Controls

- **Arrow Keys** or **WASD**: Change direction
- **Spacebar** or **R**: Restart game after game over
- **Touch/Click**: (Future: on-screen D-pad controls)

## Configuration

You can easily customize the game by modifying constants at the top of the script:

```javascript
const CONFIG = {
    CELL_SIZE: 4,           // Pixels per grid cell
    GRID_SIZE: 25,          // Grid dimensions (25×25)
    CANVAS_SIZE: 100,       // Canvas size in pixels
    TICK_INTERVAL: 150,     // Game speed (milliseconds between moves)
    INITIAL_LENGTH: 3       // Starting snake length
};

const COLORS = {
    background: '#0f0f1e',
    snake: '#00ff00',       // Classic green
    snakeHead: '#00cc00',   // Darker green for head
    food: '#ff0000',         // Red food
    // ... more colors
};
```

**Tips for customization:**
- Lower `TICK_INTERVAL` = faster game
- Higher `GRID_SIZE` = larger playing field
- Adjust `COLORS` for different themes

## Contributing

We welcome contributions! Here's how you can help:

### Safe Areas to Modify

These areas are safe to modify without breaking core functionality:

1. **Visual Styling** (`<style>` section):
   - Colors, fonts, layout
   - Canvas appearance
   - Responsive breakpoints

2. **Configuration Constants**:
   - `CONFIG` object (game speed, grid size)
   - `COLORS` object (color palette)
   - `KEY_MAP` object (keyboard controls)

3. **UI Elements**:
   - Score display styling
   - Game over message
   - Future: Menu screens, buttons

### How to Add Features

1. **New Game Mechanics**:
   - Add logic in `tick()` function
   - Update `gameState` object if needed
   - Modify `render()` to display new elements

2. **New Controls**:
   - Add to `KEY_MAP` object
   - Extend `setDirection()` if needed
   - Add event listeners

3. **New Visual Effects**:
   - Add drawing functions (like `drawCell()`)
   - Call them in `render()` function
   - Update `COLORS` if needed

### Code Organization Guidelines

- Keep functions focused and single-purpose
- Use descriptive variable names
- Add comments for complex logic
- Maintain the existing code structure
- Test changes in multiple browsers

### Testing Your Changes

1. Open `snake-game.html` in browser
2. Test basic gameplay (movement, food, collision)
3. Test edge cases (wrap-around, rapid direction changes)
4. Test on mobile if adding touch features
5. Check browser console for errors

### Submitting Changes

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request with description of changes

## Future Enhancements

Ideas for contributors:

- [ ] High score persistence (localStorage)
- [ ] Progressive difficulty (speed increases with score)
- [ ] Difficulty selection menu
- [ ] On-screen D-pad for mobile
- [ ] Multiple food types with different scores
- [ ] Obstacles/walls
- [ ] Power-ups (speed boost, invincibility)
- [ ] Multiplayer mode
- [ ] Themes/skins
- [ ] Particle effects
- [ ] Better sound effects library

---

## License

This project is open source and available for contribution. Feel free to fork, modify, and submit pull requests!

---

**Made with ❤️ for the open source community**
