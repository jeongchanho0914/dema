<!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"> <title>Maze Chaser</title> <style> :root { color-scheme: dark; }

{ box-sizing: border-box; }

html,
body {
width: 100%;
height: 100%;
margin: 0;
overflow: hidden;
background: radial-gradient(circle at center, #090923 0%, #020208 58%, #000 100%);
font-family: "Courier New", monospace;
}

body {
display: grid;
place-items: center;
touch-action: none;
user-select: none;
}

.game-shell {
width: min(96vw, 680px);
max-height: 98vh;
display: flex;
flex-direction: column;
align-items: center;
gap: 8px;
}

canvas {
display: block;
width: 100%;
height: auto;
max-height: 92vh;
object-fit: contain;
background: #000;
border: 2px solid #17175b;
border-radius: 12px;
box-shadow:
0 0 28px rgba(30, 60, 255, 0.38),
inset 0 0 30px rgba(0, 0, 0, 0.8);
}

.touch-controls {
display: none;
grid-template-columns: repeat(3, 48px);
grid-template-rows: repeat(2, 48px);
gap: 5px;
}

.touch-controls button {
border: 1px solid #334cff;
border-radius: 12px;
background: rgba(15, 17, 62, 0.92);
color: #fff;
font: 700 22px/1 monospace;
box-shadow: 0 0 12px rgba(45, 72, 255, 0.35);
}

.touch-controls button:active {
transform: scale(0.94);
background: #24329b;
}

.touch-controls .up {
grid-column: 2;
grid-row: 1;
}

.touch-controls .left {
grid-column: 1;
grid-row: 2;
}

.touch-controls .down {
grid-column: 2;
grid-row: 2;
}

.touch-controls .right {
grid-column: 3;
grid-row: 2;
}

@media (pointer: coarse), (max-width: 700px) {
.game-shell {
width: min(96vw, 610px);
}

.touch-controls {
  display: grid;
}

canvas {
  max-height: calc(98vh - 112px);
}

}
</style>

</head> <body> <div class="game-shell"> <canvas id="game" aria-label="Pac-Man inspired maze game"></canvas> <div class="touch-controls" aria-label="Touch controls"> <button class="up" data-dir="up" aria-label="Up">▲</button> <button class="left" data-dir="left" aria-label="Left">◀</button> <button class="down" data-dir="down" aria-label="Down">▼</button> <button class="right" data-dir="right" aria-label="Right">▶</button> </div> </div> <script> (() => { "use strict"; const canvas = document.getElementById("game"); const ctx = canvas.getContext("2d"); const TILE = 22; const HUD = 54; const FOOTER = 34; const TUNNEL_ROW = 14; const RAW_MAP = [ "#############################", "#o...........###...........o#", "#.#####.#####.###.#####.#####", "#.#####.#####.###.#####.#####", "#...........................#", "#.###.###.#########.###.###.#", "#.....###....###....###.....#", "#####.#####. ### .#####.#####", " #.#####. ### .#####.# ", "#####.###...........###.#####", "#.......#.###...###.#.......#", "#.#####.#.###...###.#.#####.#", "#.....#.................#...#", "#####.#.###.=====.###.#.#####", " ...# 1234 #... ", "#####.#.###.#####.###.#.#####", "#.....#..... P .....#.....#", "#.#####.###.#####.###.#####.#", "#...........###.............#", "#.###.#####.###.#####.###.#.#", "#o..#...................#..o#", "###.#.###.#########.###.#.###", "#.....###....###....###.....#", "#.##########.###.##########.#", "#...........................#", "#.#####.#####.###.#####.#####", "#.....#.......#.#.......#...#", "#####.#.###.###.###.###.#.###", "#.............#.............#", "#o###########...###########o#", "#############################" ]; const COLS = Math.max(...RAW_MAP.map(row => row.length)); const ROWS = RAW_MAP.length; const MAP_TEMPLATE = RAW_MAP.map(row => row.padEnd(COLS, " ").slice(0, COLS) ); const MAZE_HEIGHT = ROWS * TILE; canvas.width = COLS * TILE; canvas.height = HUD + MAZE_HEIGHT + FOOTER; const DIR = Object.freeze({ NONE: Object.freeze({ x: 0, y: 0, angle: 0, name: "none" }), RIGHT: Object.freeze({ x: 1, y: 0, angle: 0, name: "right" }), DOWN: Object.freeze({ x: 0, y: 1, angle: Math.PI / 2, name: "down" }), LEFT: Object.freeze({ x: -1, y: 0, angle: Math.PI, name: "left" }), UP: Object.freeze({ x: 0, y: -1, angle: -Math.PI / 2, name: "up" }) }); const TIE_ORDER = [ DIR.UP, DIR.LEFT, DIR.DOWN, DIR.RIGHT ]; const MODE_SCHEDULE = [ { mode: "scatter", duration: 7 }, { mode: "chase", duration: 20 }, { mode: "scatter", duration: 7 }, { mode: "chase", duration: 20 }, { mode: "scatter", duration: 5 }, { mode: "chase", duration: 20 }, { mode: "scatter", duration: 5 }, { mode: "chase", duration: Infinity } ]; const GHOST_DEFS = [ { name: "Blinky", color: "#ff3038", corner: { x: COLS - 2, y: 1 } }, { name: "Pinky", color: "#ff8fca", corner: { x: 1, y: 1 } }, { name: "Inky", color: "#25e6e8", corner: { x: COLS - 2, y: ROWS - 2 } }, { name: "Clyde", color: "#ff9d28", corner: { x: 1, y: ROWS - 2 } } ]; let pellets = []; let remainingPellets = 0; let pacman; let ghosts = []; let animationTime = 0; let lastTimestamp = performance.now(); let pointerStart = null; const game = { score: 0, highScore: loadHighScore(), lives: 3, level: 1, state: "ready", readyTimer: 1.45, stateTimer: 0, paused: false, globalMode: "scatter", modeIndex: 0, modeTimer: MODE_SCHEDULE[0].duration, frightTimer: 0, ghostCombo: 0, extraLifeAwarded: false, levelFlash: 0 }; function loadHighScore() { try { return Number(localStorage.getItem("mazeChaserHighScore")) || 0; } catch (_) { return 0; } } function saveHighScore() { try { localStorage.setItem( "mazeChaserHighScore", String(game.highScore) ); } catch (_) {} } function sameDirection(a, b) { return a.x === b.x && a.y === b.y; } function isReverse(a, b) { return ( a.x === -b.x && a.y === -b.y && (a.x !== 0 || a.y !== 0) ); } function centerOf(value) { return Math.round(value - 0.5) + 0.5; } function normalizeTunnelX(x) { let result = x; while (result < 0) { result += COLS; } while (result >= COLS) { result -= COLS; } return result; } function cellAt(tx, ty) { if (ty < 0 || ty >= ROWS) { return "#"; } if (tx < 0 || tx >= COLS) { return ty === TUNNEL_ROW ? " " : "#"; } return MAP_TEMPLATE[ty][tx]; } function canPacmanEnter(tx, ty) { const cell = cellAt(tx, ty); return cell !== "#" && cell !== "="; } function canGhostEnter(tx, ty, ghost) { const cell = cellAt(tx, ty); if (cell === "#") { return false; } if (cell === "=") { return ( ghost.state === "eaten" || ghost.state === "exiting" ); } return true; } function canMoveFrom(entity, direction, passableFn) { if ( !direction || (direction.x === 0 && direction.y === 0) ) { return false; } let tx = Math.floor(entity.x); const ty = Math.floor(entity.y); if ( ty === TUNNEL_ROW && (tx < 0 || tx >= COLS) ) { tx = normalizeTunnelX(tx); } return passableFn( tx + direction.x, ty + direction.y ); } function createPellets() { pellets = Array.from( { length: ROWS }, () => Array(COLS).fill(0) ); remainingPellets = 0; for (let y = 0; y < ROWS; y++) { for (let x = 0; x < COLS; x++) { const cell = MAP_TEMPLATE[y][x]; if (cell === ".") { pellets[y][x] = 1; remainingPellets++; } else if (cell === "o") { pellets[y][x] = 2; remainingPellets++; } } } } function makeGhost( index, x, y, direction, state, releaseDelay ) { return { index, name: GHOST_DEFS[index].name, color: GHOST_DEFS[index].color, corner: GHOST_DEFS[index].corner, x, y, dir: direction, state, releaseTimer: releaseDelay, houseDirection: index % 2 === 0 ? 1 : -1 }; } function createActors() { pacman = { x: 14.5, y: 16.5, dir: DIR.LEFT, desired: DIR.LEFT, lastDir: DIR.LEFT, baseSpeed: 5.15, mouthPhase: 0 }; ghosts = [ makeGhost( 0, 14.5, 12.5, DIR.LEFT, "normal", 0 ), makeGhost( 1, 13.5, 14.5, DIR.RIGHT, "house", 2.1 ), makeGhost( 2, 14.5, 14.5, DIR.LEFT, "house", 4.4 ), makeGhost( 3, 15.5, 14.5, DIR.RIGHT, "house", 6.8 ) ]; } function resetModeCycle() { game.globalMode = "scatter"; game.modeIndex = 0; game.modeTimer = MODE_SCHEDULE[0].duration; game.frightTimer = 0; game.ghostCombo = 0; } function loadLevel() { createPellets(); createActors(); resetModeCycle(); game.state = "ready"; game.readyTimer = 1.45; game.stateTimer = 0; game.levelFlash = 0; } function resetAfterDeath() { createActors(); resetModeCycle();