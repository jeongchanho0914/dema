<!doctype html> <html lang="en"> <head> <meta charset="UTF-8" /> <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" /> <meta name="theme-color" content="#0b0f0d" /> <title>Ironfront: Tank Battle</title> <style> :root { color-scheme: dark; --bg: #080b09; --panel: rgba(17, 23, 19, 0.92); --border: rgba(174, 196, 160, 0.2); --text: #e8eee3; --muted: #8d9b8a; --p1: #57e6c2; --p2: #ff765f; }
* {
  box-sizing: border-box;
  -webkit-tap-highlight-color: transparent;
}

html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
  overflow: hidden;
  background:
    radial-gradient(circle at 50% 0%, #1c271f 0%, transparent 50%),
    linear-gradient(135deg, #080b09 0%, #0d120f 50%, #050706 100%);
  color: var(--text);
  font-family:
    Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", sans-serif;
}

body {
  display: grid;
  place-items: center;
  padding: 14px;
}

.game-shell {
  width: min(100%, 1180px);
  display: flex;
  flex-direction: column;
  gap: 10px;
  user-select: none;
}

.topbar {
  min-height: 58px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 18px;
  padding: 10px 15px;
  border: 1px solid var(--border);
  border-radius: 12px;
  background:
    linear-gradient(180deg, rgba(28, 37, 30, 0.96), rgba(12, 17, 14, 0.96)),
    repeating-linear-gradient(
      90deg,
      transparent 0,
      transparent 14px,
      rgba(255, 255, 255, 0.012) 15px
    );
  box-shadow:
    0 18px 60px rgba(0, 0, 0, 0.42),
    inset 0 1px rgba(255, 255, 255, 0.04);
}

.brand {
  display: flex;
  align-items: center;
  gap: 12px;
  min-width: 0;
}

.emblem {
  width: 38px;
  height: 38px;
  position: relative;
  flex: 0 0 auto;
  border: 1px solid #6e7c69;
  border-radius: 8px;
  background:
    linear-gradient(135deg, #404d3e, #1b231d 55%, #596754);
  box-shadow:
    inset 0 0 0 3px #131a15,
    inset 0 1px rgba(255, 255, 255, 0.18),
    0 5px 14px rgba(0, 0, 0, 0.35);
}

.emblem::before,
.emblem::after {
  content: "";
  position: absolute;
  background: #cbd6c5;
  border-radius: 2px;
  opacity: 0.85;
}

.emblem::before {
  width: 20px;
  height: 7px;
  left: 8px;
  top: 17px;
}

.emblem::after {
  width: 5px;
  height: 21px;
  left: 16px;
  top: 7px;
}

.brand-text {
  min-width: 0;
}

.brand h1 {
  margin: 0;
  font-size: clamp(15px, 2vw, 21px);
  line-height: 1;
  letter-spacing: 0.13em;
  white-space: nowrap;
}

.brand p {
  margin: 6px 0 0;
  color: var(--muted);
  font-size: 10px;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  white-space: nowrap;
}

.control-summary {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 12px;
  color: var(--muted);
  font-size: 11px;
  white-space: nowrap;
}

.control-group {
  display: flex;
  align-items: center;
  gap: 6px;
  padding-left: 12px;
  border-left: 1px solid rgba(255, 255, 255, 0.08);
}

.player-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  box-shadow: 0 0 9px currentColor;
}

.p1-dot {
  color: var(--p1);
  background: currentColor;
}

.p2-dot {
  color: var(--p2);
  background: currentColor;
}

kbd {
  min-width: 22px;
  height: 21px;
  display: inline-grid;
  place-items: center;
  padding: 0 6px;
  border: 1px solid #3e493e;
  border-bottom-width: 3px;
  border-radius: 5px;
  color: #dfe8da;
  background: #1b221d;
  font: inherit;
  font-weight: 700;
  box-shadow: inset 0 1px rgba(255, 255, 255, 0.04);
}

.canvas-frame {
  position: relative;
  width: 100%;
  border: 1px solid var(--border);
  border-radius: 14px;
  overflow: hidden;
  background: #080b09;
  box-shadow:
    0 24px 80px rgba(0, 0, 0, 0.58),
    inset 0 1px rgba(255, 255, 255, 0.035);
}

.canvas-frame::before {
  content: "";
  position: absolute;
  inset: 0;
  z-index: 2;
  pointer-events: none;
  background:
    linear-gradient(rgba(255, 255, 255, 0.018) 50%, transparent 50%);
  background-size: 100% 4px;
  mix-blend-mode: overlay;
  opacity: 0.26;
}

.canvas-frame::after {
  content: "";
  position: absolute;
  inset: 0;
  z-index: 3;
  pointer-events: none;
  box-shadow:
    inset 0 0 90px rgba(0, 0, 0, 0.46),
    inset 0 0 0 1px rgba(255, 255, 255, 0.025);
}

canvas {
  display: block;
  width: 100%;
  height: auto;
  aspect-ratio: 1080 / 720;
  background: #0a0e0b;
  outline: none;
  cursor: crosshair;
}

.status-strip {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  color: #738073;
  font-size: 10px;
  letter-spacing: 0.09em;
  text-transform: uppercase;
  padding: 0 4px;
}

.status-strip span:last-child {
  text-align: right;
}

@media (max-width: 750px) {
  body {
    padding: 6px;
  }

  .game-shell {
    gap: 6px;
  }

  .topbar {
    min-height: 48px;
    padding: 8px 10px;
  }

  .emblem {
    width: 32px;
    height: 32px;
  }

  .emblem::before {
    width: 16px;
    left: 7px;
    top: 14px;
  }

  .emblem::after {
    height: 17px;
    left: 14px;
    top: 6px;
  }

  .brand p,
  .control-summary,
  .status-strip {
    display: none;
  }

  .canvas-frame {
    border-radius: 9px;
  }
}
</style> </head> <body> <main class="game-shell"> <header class="topbar"> <div class="brand"> <div class="emblem" aria-hidden="true"></div> <div class="brand-text"> <h1>IRONFRONT: TANK BATTLE</h1> <p>Local two-player armored combat</p> </div> </div>
  <div class="control-summary" aria-label="Controls">
    <div class="control-group">
      <span class="player-dot p1-dot"></span>
      <strong>P1</strong>
      <kbd>WASD</kbd>
      <kbd>SPACE</kbd>
    </div>
    <div class="control-group">
      <span class="player-dot p2-dot"></span>
      <strong>P2</strong>
      <kbd>ARROWS</kbd>
      <kbd>ENTER</kbd>
    </div>
  </div>
</header>

<section class="canvas-frame">
  <canvas
    id="game"
    width="1080"
    height="720"
    tabindex="0"
    aria-label="Two-player tank battle game"
  ></canvas>
</section>

<footer class="status-strip">
  <span>Brick walls can be destroyed · Steel walls reflect shells</span>
  <span>First tank to eliminate all enemy lives wins</span>
</footer>
</main> <script> (() => { "use strict"; const canvas = document.getElementById("game"); const ctx = canvas.getContext("2d", { alpha: false }); const WIDTH = canvas.width; const HEIGHT = canvas.height; const TILE = 40; const COLS = 20; const ROWS = 15; const ARENA_X = 24; const ARENA_Y = 60; const ARENA_W = COLS * TILE; const ARENA_H = ROWS * TILE; const PANEL_X = 850; const PANEL_W = 206; const EMPTY = 0; const BRICK = 1; const STEEL = 2; const TAU = Math.PI * 2; const keys = new Set(); const keyOrder = new Map(); let keyCounter = 0; let lastTime = performance.now(); let audioContext = null; let noiseBuffer = null; let map = []; let tanks = []; let bullets = []; let particles = []; let powerups = []; let floatingTexts = []; let debris = []; let powerSpawnTimer = 7; let gameTime = 0; let gameOver = false; let winner = null; let screenShake = 0; let impactFlash = 0; let matchStarted = false; const spawnPoints = [ { col: 2, row: 12, dir: 0 }, { col: 17, row: 2, dir: Math.PI } ]; const palette = { floor: "#111712", floorAlt: "#151d17", grid: "rgba(165, 184, 155, 0.055)", brick: "#7b4030", brickDark: "#3e241e", brickLight: "#9e5944", steel: "#677067", steelDark: "#262d29", steelLight: "#a7afa4", panel: "#111712", panelBorder: "#354137", p1: "#57e6c2", p1Dark: "#167c69", p1Light: "#b8fff0", p2: "#ff765f", p2Dark: "#9e2f25", p2Light: "#ffd0c7", text: "#e6eee2", muted: "#899687", speed: "#ffd45a", shield: "#70b9ff", double: "#d983ff" }; class Tank { constructor(id, spawn) { this.id = id; this.name = id === 0 ? "PLAYER 1" : "PLAYER 2"; this.color = id === 0 ? palette.p1 : palette.p2; this.dark = id === 0 ? palette.p1Dark : palette.p2Dark; this.light = id === 0 ? palette.p1Light : palette.p2Light; this.controls = id === 0 ? { up: "KeyW", down: "KeyS", left: "KeyA", right: "KeyD", fire: "Space" } : { up: "ArrowUp", down: "ArrowDown", left: "ArrowLeft", right: "ArrowRight", fire: "Enter" }; this.spawn = { ...spawn }; this.x = tileCenterX(spawn.col); this.y = tileCenterY(spawn.row); this.angle = spawn.dir; this.radius = 15; this.baseSpeed = 115; this.active = true; this.lives = 3; this.score = 0; this.respawnTimer = 0; this.reload = 0; this.speedTimer = 0; this.shieldTimer = 0; this.doubleTimer = 0; this.spawnProtection = 1.65; this.trackPhase = 0; this.moving = false; this.hitPulse = 0; } resetForMatch() { this.x = tileCenterX(this.spawn.col); this.y = tileCenterY(this.spawn.row); this.angle = this.spawn.dir; this.active = true; this.lives = 3; this.score = 0; this.respawnTimer = 0; this.reload = 0; this.speedTimer = 0; this.shieldTimer = 0; this.doubleTimer = 0; this.spawnProtection = 1.65; this.trackPhase = 0; this.moving = false; this.hitPulse = 0; } update(dt) { this.reload = Math.max(0, this.reload - dt); this.speedTimer = Math.max(0, this.speedTimer - dt); this.shieldTimer = Math.max(0, this.shieldTimer - dt); this.doubleTimer = Math.max(0, this.doubleTimer - dt); this.spawnProtection = Math.max(0, this.spawnProtection - dt); this.hitPulse = Math.max(0, this.hitPulse - dt * 3.5); if (!this.active) { if (this.lives > 0 && !gameOver) { this.respawnTimer -= dt; if (this.respawnTimer <= 0) { this.respawn(); } } return; } const direction = this.getMovementDirection(); this.moving = direction !== null; if (direction !== null) { this.angle = direction.angle; const speed = this.baseSpeed * (this.speedTimer > 0 ? 1.52 : 1) * (direction.reverse ? 0.86 : 1); const dx = direction.dx * speed * dt; const dy = direction.dy * speed * dt; this.tryMove(dx, dy); this.trackPhase += dt * speed * 0.12; } } getMovementDirection() { const choices = [ { code: this.controls.up, dx: 0, dy: -1, angle: -Math.PI / 2 }, { code: this.controls.down, dx: 0, dy: 1, angle: Math.PI / 2 }, { code: this.controls.left, dx: -1, dy: 0, angle: Math.PI }, { code: this.controls.right, dx: 1, dy: 0, angle: 0 } ].filter((entry) => keys.has(entry.code)); if (choices.length === 0) return null; choices.sort( (a, b) => (keyOrder.get(b.code) || 0) - (keyOrder.get(a.code) || 0) ); const selected = choices[0]; const facingDelta = angleDifference(this.angle, selected.angle); selected.reverse = Math.abs(facingDelta) > Math.PI * 0.75; return selected; } tryMove(dx, dy) { const oldX = this.x; const oldY = this.y; if (dx !== 0) { this.x += dx; if (tankBlocked(this, this.x, this.y)) { this.x = oldX; } } if (dy !== 0) { this.y += dy; if (tankBlocked(this, this.x, this.y)) { this.y = oldY; } } } fire() { if (!this.active || gameOver || this.reload > 0) return; const maxBullets = this.doubleTimer > 0 ? 2 : 1; const currentBullets = bullets.reduce( (count, bullet) => count + (bullet.active && bullet.owner === this ? 1 : 0), 0 ); if (currentBullets >= maxBullets) return; const barrelLength = 24; const spawnX = this.x + Math.cos(this.angle) * barrelLength; const spawnY = this.y + Math.sin(this.angle) * barrelLength; bullets.push(new Bullet(this, spawnX, spawnY, this.angle)); this.reload = this.doubleTimer > 0 ? 0.17 : 0.25; createMuzzleFlash(spawnX, spawnY, this.angle, this.color); playShootSound(this.id); } destroy(attacker) { if (!this.active || gameOver) return; if (this.spawnProtection > 0) { createShieldImpact(this.x, this.y, this.color); playShieldSound(); return; } if (this.shieldTimer > 0) { this.shieldTimer = 0; this.hitPulse = 1; createShieldImpact(this.x, this.y, palette.shield); addFloatingText(this.x, this.y - 24, "SHIELD BLOCK", palette.shield); playShieldSound(); return; } this.active = false; this.lives = Math.max(0, this.lives - 1); this.speedTimer = 0; this.shieldTimer = 0; this.doubleTimer = 0; this.respawnTimer = 3; attacker.score += 1; createTankExplosion(this.x, this.y, this.color); addFloatingText( attacker.x, attacker.y - 32, "+1", attacker.color, 1.2 ); screenShake = Math.max(screenShake, 12); impactFlash = 0.45; playExplosionSound(); if (this.lives <= 0) { gameOver = true; winner = attacker; setTimeout(() => playVictorySound(), 180); } } respawn() { const point = findRespawnPoint(this); this.x = point.x; this.y = point.y; this.angle = this.spawn.dir; this.active = true; this.respawnTimer = 0; this.spawnProtection = 1.85; this.hitPulse = 0; createRespawnEffect(this.x, this.y, this.color); playRespawnSound(); } draw() { if (!this.active) return; const blink = this.spawnProtection > 0 && Math.floor(this.spawnProtection * 10) % 2 === 0; ctx.save(); ctx.translate(this.x, this.y); ctx.rotate(this.angle); if (blink) { ctx.globalAlpha = 0.58; } if (this.speedTimer > 0 && this.moving) { drawSpeedTrail(this); } ctx.shadowColor = "rgba(0,0,0,0.6)"; ctx.shadowBlur = 8; ctx.shadowOffsetY = 4; drawTankTracks(this); drawTankHull(this); drawTankTurret(this); ctx.shadowBlur = 0; ctx.shadowOffsetY = 0; if (this.hitPulse > 0) { ctx.globalCompositeOperation = "screen"; ctx.globalAlpha = this.hitPulse * 0.7; ctx.fillStyle = "#ffffff"; roundedRect(-17, -15, 34, 30, 6); ctx.fill(); } ctx.restore(); if (this.shieldTimer > 0 || this.spawnProtection > 0) { drawTankShield(this); } if (this.doubleTimer > 0) { drawDoubleIndicator(this); } } } class Bullet { constructor(owner, x, y, angle) { this.owner = owner; this.x = x; this.y = y; this.prevX = x; this.prevY = y; this.radius = 4; this.speed = 360; this.vx = Math.cos(angle) * this.speed; this.vy = Math.sin(angle) * this.speed; this.active = true; this.age = 0; this.bounces = 0; this.trail = []; } update(dt) { if (!this.active) return; this.age += dt; if (this.age > 8 || this.bounces > 8) { this.active = false; return; } this.trail.unshift({ x: this.x, y: this.y }); if (this.trail.length > 8) this.trail.pop(); const distance = Math.hypot(this.vx, this.vy) * dt; const steps = Math.max(1, Math.ceil(distance / 5)); const stepDt = dt / steps; for (let i = 0; i < steps && this.active; i++) { this.prevX = this.x; this.prevY = this.y; const nextX = this.x + this.vx * stepDt; const nextY = this.y + this.vy * stepDt; const collision = getBulletWallCollision( nextX, nextY, this.radius ); if (collision) { if (collision.type === BRICK) { destroyBrick(collision.col, collision.row, this); this.active = false; break; } if (collision.type === STEEL) { const hitX = bulletTouchesWall( nextX, this.y, this.radius, collision.col, collision.row ); const hitY = bulletTouchesWall( this.x, nextY, this.radius, collision.col, collision.row ); if (hitX && !hitY) { this.vx *= -1; } else if (hitY && !hitX) { this.vy *= -1; } else { const wallCenterX = ARENA_X + collision.col * TILE + TILE / 2; const wallCenterY = ARENA_Y + collision.row * TILE + TILE / 2; const localX = this.x - wallCenterX; const localY = this.y - wallCenterY; if (Math.abs(localX) > Math.abs(localY)) { this.vx *= -1; } else if (Math.abs(localY) > Math.abs(localX)) { this.vy *= -1; } else { this.vx *= -1; this.vy *= -1; } } this.bounces += 1; createRicochet( this.x, this.y, Math.atan2(this.vy, this.vx) ); playRicochetSound(); this.x += Math.sign(this.vx) * 1.8; this.y += Math.sign(this.vy) * 1.8; continue; } } this.x = nextX; this.y = nextY; for (const tank of tanks) { if ( tank !== this.owner && tank.active && circleCollision( this.x, this.y, this.radius, tank.x, tank.y, tank.radius ) ) { tank.destroy(this.owner); this.active = false; break; } } } } draw() { if (!this.active) return; ctx.save(); for (let i = this.trail.length - 1; i >= 0; i--) { const point = this.trail[i]; const alpha = (1 - i / this.trail.length) * 0.14; const size = 1.2 + (1 - i / this.trail.length) * 2.2; ctx.globalAlpha = alpha; ctx.fillStyle = this.owner.color; ctx.beginPath(); ctx.arc(point.x, point.y, size, 0, TAU); ctx.fill(); } ctx.globalAlpha = 1; ctx.shadowColor = "#ffe19d"; ctx.shadowBlur = 12; ctx.fillStyle = "#fff3bd"; ctx.beginPath(); ctx.arc(this.x, this.y, this.radius, 0, TAU); ctx.fill(); ctx.fillStyle = "#ffffff"; ctx.beginPath(); ctx.arc(this.x - 1, this.y - 1, 1.4, 0, TAU); ctx.fill(); ctx.restore(); } } class Particle { constructor(options) { this.x = options.x; this.y = options.y; this.vx = options.vx || 0; this.vy = options.vy || 0; this.life = options.life || 1; this.maxLife = this.life; this.size = options.size || 3; this.color = options.color || "#ffffff"; this.gravity = options.gravity || 0; this.drag = options.drag ?? 0.98; this.rotation = options.rotation || 0; this.rotationSpeed = options.rotationSpeed || 0; this.shape = options.shape || "circle"; this.glow = options.glow || 0; this.shrink = options.shrink ?? true; } update(dt) { this.life -= dt; this.vx *= Math.pow(this.drag, dt * 60); this.vy *= Math.pow(this.drag, dt * 60); this.vy += this.gravity * dt; this.x += this.vx * dt; this.y += this.vy * dt; this.rotation += this.rotationSpeed * dt; } draw() { if (this.life <= 0) return; const progress = Math.max(0, this.life / this.maxLife); const size = this.shrink ? this.size * progress : this.size; ctx.save(); ctx.translate(this.x, this.y); ctx.rotate(this.rotation); ctx.globalAlpha = Math.min(1, progress * 1.4); ctx.fillStyle = this.color; if (this.glow > 0) { ctx.shadowColor = this.color; ctx.shadowBlur = this.glow; } if (this.shape === "rect") { ctx.fillRect(-size / 2, -size / 2, size, size); } else if (this.shape === "line") { ctx.fillRect(-size * 1.6, -size / 3, size * 3.2, size / 1.5); } else { ctx.beginPath(); ctx.arc(0, 0, Math.max(0.1, size), 0, TAU); ctx.fill(); } ctx.restore(); } } class PowerUp { constructor(type, col, row) { this.type = type; this.col = col; this.row = row; this.x = tileCenterX(col); this.y = tileCenterY(row); this.age = 0; this.life = 13; this.active = true; } update(dt) { this.age += dt; this.life -= dt; if (this.life <= 0) { this.active = false; return; } for (const tank of tanks) { if ( tank.active && circleCollision( this.x, this.y, 14, tank.x, tank.y, tank.radius ) ) { this.collect(tank); break; } } } collect(tank) { if (!this.active) return; this.active = false; if (this.type === "speed") { tank.speedTimer = 8; addFloatingText(this.x, this.y - 22, "SPEED BOOST", palette.speed); } else if (this.type === "shield") { tank.shieldTimer = 12; addFloatingText(this.x, this.y - 22, "SHIELD", palette.shield); } else { tank.doubleTimer = 10; addFloatingText( this.x, this.y - 22, "DOUBLE SHELL", palette.double ); } createPowerPickup(this.x, this.y, powerColor(this.type)); playPowerupSound(); } draw() { if (!this.active) return; const pulse = 1 + Math.sin(this.age * 5) * 0.08; const color = powerColor(this.type); ctx.save(); ctx.translate(this.x, this.y); ctx.scale(pulse, pulse); ctx.shadowColor = color; ctx.shadowBlur = 18; ctx.fillStyle = "rgba(12,17,14,0.9)"; ctx.strokeStyle = color; ctx.lineWidth = 2; ctx.beginPath(); ctx.arc(0, 0, 14, 0, TAU); ctx.fill(); ctx.stroke(); ctx.shadowBlur = 7; ctx.fillStyle = color; if (this.type === "speed") { ctx.beginPath(); ctx.moveTo(2, -10); ctx.lineTo(-6, 1); ctx.lineTo(-1, 1); ctx.lineTo(-4, 10); ctx.lineTo(7, -3); ctx.lineTo(2, -3); ctx.closePath(); ctx.fill(); } else if (this.type === "shield") { ctx.beginPath(); ctx.moveTo(0, -10); ctx.lineTo(9, -6); ctx.lineTo(7, 4); ctx.quadraticCurveTo(5, 9, 0, 11); ctx.quadraticCurveTo(-5, 9, -7, 4); ctx.lineTo(-9, -6); ctx.closePath(); ctx.fill(); } else { ctx.font = "900 13px system-ui"; ctx.textAlign = "center"; ctx.textBaseline = "middle"; ctx.fillText("Ⅱ", 0, 1); } ctx.restore(); } } function tileCenterX(col) { return ARENA_X + col * TILE + TILE / 2; } function tileCenterY(row) { return ARENA_Y + row * TILE + TILE / 2; } function angleDifference(a, b) { let diff = (b - a + Math.PI) % TAU; if (diff < 0) diff += TAU; return diff - Math.PI; } function createMap() { const nextMap = Array.from({ length: ROWS }, () => Array(COLS).fill(EMPTY) ); for (let row = 0; row < ROWS; row++) { for (let col = 0; col < COLS; col++) { if ( row === 0 || row === ROWS - 1 || col === 0 || col === COLS - 1 ) { nextMap[row][col] = STEEL; } } } const steelPositions = [ [3, 2], [4, 2], [8, 2], [11, 2], [15, 2], [16, 2], [6, 3], [13, 3], [2, 4], [3, 4], [8, 4], [9, 4], [10, 4], [11, 4], [16, 4], [17, 4], [5, 6], [6, 6], [13, 6], [14, 6], [2, 7], [9, 7], [10, 7], [17, 7], [5, 8], [6, 8], [13, 8], [14, 8], [2, 10], [3, 10], [8, 10], [9, 10], [10, 10], [11, 10], [16, 10], [17, 10], [6, 11], [13, 11], [3, 12], [4, 12], [8, 12], [11, 12], [15, 12], [16, 12] ]; const brickPositions = [ [6, 1], [7, 1], [12, 1], [13, 1], [2, 2], [5, 2], [6, 2], [7, 2], [12, 2], [13, 2], [14, 2], [17, 2], [3, 3], [4, 3], [8, 3], [9, 3], [10, 3], [11, 3], [15, 3], [16, 3], [5, 4], [6, 4], [13, 4], [14, 4], [2, 5], [3, 5], [4, 5], [7, 5], [8, 5], [11, 5], [12, 5], [15, 5], [16, 5], [17, 5], [8, 6], [9, 6], [10, 6], [11, 6], [4, 7], [5, 7], [7, 7], [12, 7], [14, 7], [15, 7], [8, 8], [9, 8], [10, 8], [11, 8], [2, 9], [3, 9], [4, 9], [7, 9], [8, 9], [11, 9], [12, 9], [15, 9], [16, 9], [17, 9], [5, 10], [6, 10], [13, 10], [14, 10], [3, 11], [4, 11], [8, 11], [9, 11], [10, 11], [11, 11], [15, 11], [16, 11], [2, 12], [5, 12], [6, 12], [7, 12], [12, 12], [13, 12], [14, 12], [17, 12], [6, 13], [7, 13], [12, 13], [13, 13] ]; for (const [col, row] of steelPositions) { if (isInterior(col, row)) nextMap[row][col] = STEEL; } for (const [col, row] of brickPositions) { if (isInterior(col, row) && nextMap[row][col] === EMPTY) { nextMap[row][col] = BRICK; } } clearSpawnArea(nextMap, spawnPoints[0].col, spawnPoints[0].row); clearSpawnArea(nextMap, spawnPoints[1].col, spawnPoints[1].row); return nextMap; } function isInterior(col, row) { return col > 0 && col < COLS - 1 && row > 0 && row < ROWS - 1; } function clearSpawnArea(targetMap, col, row) { const clearTiles = [ [0, 0], [-1, 0], [1, 0], [0, -1], [0, 1] ]; for (const [dx, dy] of clearTiles) { const x = col + dx; const y = row + dy; if (isInterior(x, y)) targetMap[y][x] = EMPTY; } } function resetGame() { map = createMap(); bullets = []; particles = []; powerups = []; floatingTexts = []; debris = []; gameTime = 0; powerSpawnTimer = 5.5; gameOver = false; winner = null; screenShake = 0; impactFlash = 0; if (tanks.length === 0) { tanks = [ new Tank(0, spawnPoints[0]), new Tank(1, spawnPoints[1]) ]; } else { tanks.forEach((tank) => tank.resetForMatch()); } createRespawnEffect(tanks[0].x, tanks[0].y, tanks[0].color); createRespawnEffect(tanks[1].x, tanks[1].y, tanks[1].color); } function tankBlocked(tank, x, y) { const half = tank.radius; const minCol = Math.max( 0, Math.floor((x - half - ARENA_X) / TILE) ); const maxCol = Math.min( COLS - 1, Math.floor((x + half - ARENA_X) / TILE) ); const minRow = Math.max( 0, Math.floor((y - half - ARENA_Y) / TILE) ); const maxRow = Math.min( ROWS - 1, Math.floor((y + half - ARENA_Y) / TILE) ); for (let row = minRow; row <= maxRow; row++) { for (let col = minCol; col <= maxCol; col++) { if (map[row][col] === EMPTY) continue; const wallX = ARENA_X + col * TILE; const wallY = ARENA_Y + row * TILE; if ( rectsOverlap( x - half, y - half, half * 2, half * 2, wallX + 1, wallY + 1, TILE - 2, TILE - 2 ) ) { return true; } } } for (const other of tanks) { if (other === tank || !other.active) continue; if ( circleCollision( x, y, tank.radius + 1, other.x, other.y, other.radius + 1 ) ) { return true; } } return false; } function getBulletWallCollision(x, y, radius) { const minCol = Math.max( 0, Math.floor((x - radius - ARENA_X) / TILE) ); const maxCol = Math.min( COLS - 1, Math.floor((x + radius - ARENA_X) / TILE) ); const minRow = Math.max( 0, Math.floor((y - radius - ARENA_Y) / TILE) ); const maxRow = Math.min( ROWS - 1, Math.floor((y + radius - ARENA_Y) / TILE) ); for (let row = minRow; row <= maxRow; row++) { for (let col = minCol; col <= maxCol; col++) { const type = map[row][col]; if (type === EMPTY) continue; if (bulletTouchesWall(x, y, radius, col, row)) { return { type, col, row }; } } } return null; } function bulletTouchesWall(x, y, radius, col, row) { const rx = ARENA_X + col * TILE; const ry = ARENA_Y + row * TILE; return circleRectCollision(x, y, radius, rx, ry, TILE, TILE); } function destroyBrick(col, row, bullet) { if (map[row][col] !== BRICK) return; map[row][col] = EMPTY; const centerX = tileCenterX(col); const centerY = tileCenterY(row); const impactAngle = Math.atan2(bullet.vy, bullet.vx); for (let i = 0; i < 16; i++) { const angle = impactAngle + randomRange(-1.25, 1.25); const speed = randomRange(45, 150); particles.push( new Particle({ x: centerX + randomRange(-12, 12), y: centerY + randomRange(-12, 12), vx: Math.cos(angle) * speed, vy: Math.sin(angle) * speed, life: randomRange(0.35, 0.8), size: randomRange(3, 7), color: Math.random() < 0.5 ? "#9e5944" : "#512b23", gravity: 100, drag: 0.95, rotation: Math.random() * TAU, rotationSpeed: randomRange(-8, 8), shape: "rect" }) ); } for (let i = 0; i < 7; i++) { particles.push( new Particle({ x: centerX + randomRange(-8, 8), y: centerY + randomRange(-8, 8), vx: randomRange(-30, 30), vy: randomRange(-45, -5), life: randomRange(0.45, 0.85), size: randomRange(5, 10), color: "rgba(65,54,44,0.75)", gravity: -8, drag: 0.93, shrink: false }) ); } screenShake = Math.max(screenShake, 3); playBrickSound(); } function rectsOverlap(ax, ay, aw, ah, bx, by, bw, bh) { return ( ax < bx + bw && ax + aw > bx && ay < by + bh && ay + ah > by ); } function circleCollision(ax, ay, ar, bx, by, br) { const dx = ax - bx; const dy = ay - by; const radius = ar + br; return dx * dx + dy * dy < radius * radius; } function circleRectCollision(cx, cy, radius, rx, ry, rw, rh) { const nearestX = Math.max(rx, Math.min(cx, rx + rw)); const nearestY = Math.max(ry, Math.min(cy, ry + rh)); const dx = cx - nearestX; const dy = cy - nearestY; return dx * dx + dy * dy <= radius * radius; } function findRespawnPoint(tank) { const preferred = { x: tileCenterX(tank.spawn.col), y: tileCenterY(tank.spawn.row) }; if (!tankBlocked(tank, preferred.x, preferred.y)) { return preferred; } const candidates = []; for (let row = 1; row < ROWS - 1; row++) { for (let col = 1; col < COLS - 1; col++) { if (map[row][col] !== EMPTY) continue; const x = tileCenterX(col); const y = tileCenterY(row); const distance = Math.hypot( x - preferred.x, y - preferred.y ); candidates.push({ x, y, distance }); } } candidates.sort((a, b) => a.distance - b.distance); for (const candidate of candidates) { if (!tankBlocked(tank, candidate.x, candidate.y)) { return candidate; } } return preferred; } function spawnPowerUp() { if (powerups.filter((power) => power.active).length >= 3) return; const candidates = []; for (let row = 1; row < ROWS - 1; row++) { for (let col = 1; col < COLS - 1; col++) { if (map[row][col] !== EMPTY) continue; const x = tileCenterX(col); const y = tileCenterY(row); const nearTank = tanks.some( (tank) => tank.active && Math.hypot(tank.x - x, tank.y - y) < TILE * 2 ); const occupied = powerups.some( (power) => power.active && power.col === col && power.row === row ); if (!nearTank && !occupied) { candidates.push({ col, row }); } } } if (candidates.length === 0) return; const location = candidates[Math.floor(Math.random() * candidates.length)]; const random = Math.random(); const type = random < 0.34 ? "speed" : random < 0.67 ? "shield" : "double"; powerups.push(new PowerUp(type, location.col, location.row)); createPowerSpawn( tileCenterX(location.col), tileCenterY(location.row), powerColor(type) ); } function powerColor(type) { if (type === "speed") return palette.speed; if (type === "shield") return palette.shield; return palette.double; } function update(dt) { if (!matchStarted) { updateParticles(dt); return; } gameTime += dt; screenShake = Math.max(0, screenShake - dt * 22); impactFlash = Math.max(0, impactFlash - dt * 2.2); for (const tank of tanks) tank.update(dt); for (const bullet of bullets) bullet.update(dt); for (const power of powerups) power.update(dt); resolveBulletCollisions(); updateParticles(dt); bullets = bullets.filter((bullet) => bullet.active); powerups = powerups.filter((power) => power.active); particles = particles.filter((particle) => particle.life > 0); floatingTexts = floatingTexts.filter((text) => text.life > 0); debris = debris.filter((item) => item.life > 0); if (!gameOver) { powerSpawnTimer -= dt; if (powerSpawnTimer <= 0) { spawnPowerUp(); powerSpawnTimer = randomRange(7, 11.5); } } } function resolveBulletCollisions() { for (let i = 0; i < bullets.length; i++) { const a = bullets[i]; if (!a.active) continue; for (let j = i + 1; j < bullets.length; j++) { const b = bullets[j]; if (!b.active || a.owner === b.owner) continue; if ( circleCollision( a.x, a.y, a.radius + 1, b.x, b.y, b.radius + 1 ) ) { a.active = false; b.active = false; createBulletClash((a.x + b.x) / 2, (a.y + b.y) / 2); playRicochetSound(); } } } } function updateParticles(dt) { for (const particle of particles) particle.update(dt); for (const text of floatingTexts) { text.life -= dt; text.y -= dt * 22; } for (const item of debris) { item.life -= dt; item.rotation += item.rotationSpeed * dt; item.vx *= Math.pow(0.96, dt * 60); item.vy *= Math.pow(0.96, dt * 60); item.x += item.vx * dt; item.y += item.vy * dt; } } function draw() { ctx.save(); const shakeX = screenShake > 0 ? randomRange(-screenShake, screenShake) : 0; const shakeY = screenShake > 0 ? randomRange(-screenShake, screenShake) : 0; ctx.translate(shakeX, shakeY); drawBackground(); drawHeader(); drawArena(); drawPowerups(); drawBullets(); drawTanks(); drawParticles(); drawSidebar(); drawFloatingTexts(); if (!matchStarted) { drawStartOverlay(); } else if (gameOver) { drawGameOverOverlay(); } ctx.restore(); if (impactFlash > 0) { ctx.save(); ctx.globalAlpha = impactFlash * 0.18; ctx.fillStyle = "#ffffff"; ctx.fillRect(0, 0, WIDTH, HEIGHT); ctx.restore(); } } function drawBackground() { const gradient = ctx.createLinearGradient(0, 0, WIDTH, HEIGHT); gradient.addColorStop(0, "#0a0e0b"); gradient.addColorStop(0.55, "#111712"); gradient.addColorStop(1, "#070a08"); ctx.fillStyle = gradient; ctx.fillRect(0, 0, WIDTH, HEIGHT); ctx.save(); ctx.globalAlpha = 0.12; for (let i = 0; i < 80; i++) { const x = hashNoise(i * 31.17) * WIDTH; const y = hashNoise(i * 87.91) * HEIGHT; const size = 1 + hashNoise(i * 12.3) * 2; ctx.fillStyle = i % 3 === 0 ? "#9eaa95" : "#243027"; ctx.fillRect(x, y, size, size); } ctx.restore(); } function drawHeader() { ctx.fillStyle = "rgba(9,13,10,0.96)"; ctx.fillRect(0, 0, WIDTH, 48); const headerGradient = ctx.createLinearGradient(0, 0, WIDTH, 0); headerGradient.addColorStop(0, "rgba(87,230,194,0.5)"); headerGradient.addColorStop(0.5, "rgba(140,157,135,0.08)"); headerGradient.addColorStop(1, "rgba(255,118,95,0.5)"); ctx.fillStyle = headerGradient; ctx.fillRect(0, 47, WIDTH, 1); ctx.font = "800 11px system-ui"; ctx.textBaseline = "middle"; ctx.letterSpacing = "1px"; ctx.fillStyle = palette.muted; ctx.textAlign = "left"; ctx.fillText("P1 WASD + SPACE", 24, 24); ctx.textAlign = "center"; ctx.fillStyle = "#b8c4b4"; ctx.font = "900 14px system-ui"; ctx.fillText("ARMORED COMBAT ZONE // SECTOR 07", WIDTH / 2, 24); ctx.textAlign = "right"; ctx.font = "800 11px system-ui"; ctx.fillStyle = palette.muted; ctx.fillText("P2 ARROWS + ENTER", WIDTH - 24, 24); } function drawArena() { ctx.save(); ctx.fillStyle = "#080c09"; ctx.fillRect(ARENA_X - 5, ARENA_Y - 5, ARENA_W + 10, ARENA_H + 10); ctx.strokeStyle = "#455146"; ctx.lineWidth = 2; ctx.strokeRect( ARENA_X - 3, ARENA_Y - 3, ARENA_W + 6, ARENA_H + 6 ); const floorGradient = ctx.createLinearGradient( ARENA_X, ARENA_Y, ARENA_X, ARENA_Y + ARENA_H ); floorGradient.addColorStop(0, "#151c16"); floorGradient.addColorStop(1, "#0f150f"); ctx.fillStyle = floorGradient; ctx.fillRect(ARENA_X, ARENA_Y, ARENA_W, ARENA_H); for (let row = 0; row < ROWS; row++) { for (let col = 0; col < COLS; col++) { const x = ARENA_X + col * TILE; const y = ARENA_Y + row * TILE; if ((row + col) % 2 === 0) { ctx.fillStyle = "rgba(255,255,255,0.012)"; ctx.fillRect(x, y, TILE, TILE); } const noise = hashNoise(row * 87 + col * 19); if (noise > 0.72 && map[row][col] === EMPTY) { ctx.fillStyle = "rgba(91,111,83,0.12)"; ctx.beginPath(); ctx.arc( x + 8 + noise * 20, y + 10 + hashNoise(noise * 91) * 22, 1.1 + noise, 0, TAU ); ctx.fill(); } } } ctx.strokeStyle = palette.grid; ctx.lineWidth = 1; for (let col = 0; col <= COLS; col++) { const x = ARENA_X + col * TILE + 0.5; ctx.beginPath(); ctx.moveTo(x, ARENA_Y); ctx.lineTo(x, ARENA_Y + ARENA_H); ctx.stroke(); } for (let row = 0; row <= ROWS; row++) { const y = ARENA_Y + row * TILE + 0.5; ctx.beginPath(); ctx.moveTo(ARENA_X, y); ctx.lineTo(ARENA_X + ARENA_W, y); ctx.stroke(); } for (let row = 0; row < ROWS; row++) { for (let col = 0; col < COLS; col++) { const type = map[row][col]; if (type === BRICK) { drawBrickWall(col, row); } else if (type === STEEL) { drawSteelWall(col, row); } } } drawSpawnMark(spawnPoints[0], palette.p1); drawSpawnMark(spawnPoints[1], palette.p2); ctx.restore(); } function drawBrickWall(col, row) { const x = ARENA_X + col * TILE; const y = ARENA_Y + row * TILE; const gradient = ctx.createLinearGradient(x, y, x, y + TILE); gradient.addColorStop(0, palette.brickLight); gradient.addColorStop(0.5, palette.brick); gradient.addColorStop(1, palette.brickDark); ctx.fillStyle = "#241815"; ctx.fillRect(x + 1, y + 1, TILE - 2, TILE - 2); ctx.fillStyle = gradient; const mortar = 2; const brickH = 11; for (let line = 0; line < 3; line++) { const by = y + 3 + line * 12; const offset = line % 2 === 0 ? 0 : 9; const widths = [17, 18, 17]; let bx = x + 3 - offset; for (let i = 0; i < 4; i++) { const width = widths[i % widths.length]; ctx.fillRect( Math.max(x + 3, bx), by, Math.min(width, x + TILE - 3 - Math.max(x + 3, bx)), brickH ); ctx.fillStyle = "rgba(255,255,255,0.08)"; ctx.fillRect( Math.max(x + 3, bx), by, Math.max( 0, Math.min(width, x + TILE - 3 - Math.max(x + 3, bx)) ), 1 ); ctx.fillStyle = gradient; bx += width + mortar; } } ctx.strokeStyle = "rgba(0,0,0,0.45)"; ctx.strokeRect(x + 1.5, y + 1.5, TILE - 3, TILE - 3); } function drawSteelWall(col, row) { const x = ARENA_X + col * TILE; const y = ARENA_Y + row * TILE; const gradient = ctx.createLinearGradient(x, y, x + TILE, y + TILE); gradient.addColorStop(0, "#343d37"); gradient.addColorStop(0.25, palette.steelLight); gradient.addColorStop(0.5, palette.steel); gradient.addColorStop(0.78, "#3c4540"); gradient.addColorStop(1, palette.steelDark); ctx.fillStyle = "#131915"; ctx.fillRect(x, y, TILE, TILE); ctx.fillStyle = gradient; ctx.fillRect(x + 3, y + 3, TILE - 6, TILE - 6); ctx.strokeStyle = "rgba(230,240,228,0.22)"; ctx.lineWidth = 1; ctx.strokeRect(x + 4.5, y + 4.5, TILE - 9, TILE - 9); ctx.strokeStyle = "rgba(0,0,0,0.35)"; ctx.beginPath(); ctx.moveTo(x + 5, y + TILE - 5); ctx.lineTo(x + TILE - 5, y + 5); ctx.stroke(); for (const [dx, dy] of [ [8, 8], [TILE - 8, 8], [8, TILE - 8], [TILE - 8, TILE - 8] ]) { const rivet = ctx.createRadialGradient( x + dx - 1, y + dy - 1, 0, x + dx, y + dy, 3 ); rivet.addColorStop(0, "#e0e6dc"); rivet.addColorStop(0.35, "#7f8a80"); rivet.addColorStop(1, "#252c28"); ctx.fillStyle = rivet; ctx.beginPath(); ctx.arc(x + dx, y + dy, 2.7, 0, TAU); ctx.fill(); } } function drawSpawnMark(spawn, color) { const x = tileCenterX(spawn.col); const y = tileCenterY(spawn.row); ctx.save(); ctx.globalAlpha = 0.12; ctx.strokeStyle = color; ctx.lineWidth = 1.5; ctx.setLineDash([5, 5]); ctx.beginPath(); ctx.arc(x, y, 17, 0, TAU); ctx.stroke(); ctx.setLineDash([]); ctx.fillStyle = color; ctx.beginPath(); ctx.arc(x, y, 2, 0, TAU); ctx.fill(); ctx.restore(); } function drawTankTracks(tank) { ctx.fillStyle = "#131815"; roundedRect(-17, -15, 34, 8, 3); ctx.fill(); roundedRect(-17, 7, 34, 8, 3); ctx.fill(); ctx.fillStyle = "#3e4940"; for (let i = -13; i <= 13; i += 6) { const offset = ((tank.trackPhase % 6) + 6) % 6; ctx.fillRect(i + offset - 3, -13, 3, 4); ctx.fillRect(i + offset - 3, 9, 3, 4); } ctx.strokeStyle = "rgba(216,229,210,0.14)"; ctx.lineWidth = 1; ctx.strokeRect(-15.5, -13.5, 31, 5); ctx.strokeRect(-15.5, 8.5, 31, 5); } function drawTankHull(tank) { const bodyGradient = ctx.createLinearGradient(-15, -13, 16, 13); bodyGradient.addColorStop(0, tank.light); bodyGradient.addColorStop(0.15, tank.color); bodyGradient.addColorStop(0.7, tank.dark); bodyGradient.addColorStop(1, "#17211c"); ctx.fillStyle = bodyGradient; roundedRect(-15, -11, 30, 22, 5); ctx.fill(); ctx.strokeStyle = "rgba(255,255,255,0.23)"; ctx.lineWidth = 1; roundedRect(-14.5, -10.5, 29, 21, 4.5); ctx.stroke(); ctx.fillStyle = "rgba(0,0,0,0.24)"; ctx.fillRect(-8, -8, 16, 16); ctx.fillStyle = tank.dark; ctx.fillRect(-13, -7, 4, 14); ctx.fillRect(9, -7, 4, 14); ctx.fillStyle = "rgba(255,255,255,0.14)"; ctx.fillRect(-12, -9, 19, 2); } function drawTankTurret(tank) { const turretGradient = ctx.createRadialGradient( -4, -5, 1, 0, 0, 14 ); turretGradient.addColorStop(0, tank.light); turretGradient.addColorStop(0.25, tank.color); turretGradient.addColorStop(1, tank.dark); ctx.fillStyle = "#151b17"; roundedRect(5, -3.8, 23, 7.6, 3); ctx.fill(); const barrelGradient = ctx.createLinearGradient(5, -4, 5, 4); barrelGradient.addColorStop(0, tank.light); barrelGradient.addColorStop(0.35, tank.color); barrelGradient.addColorStop(1, tank.dark); ctx.fillStyle = barrelGradient; roundedRect(4, -3, 25, 6, 2.5); ctx.fill(); ctx.fillStyle = turretGradient; ctx.beginPath(); ctx.arc(0, 0, 10.5, 0, TAU); ctx.fill(); ctx.strokeStyle = "rgba(255,255,255,0.25)"; ctx.lineWidth = 1; ctx.beginPath(); ctx.arc(0, 0, 9.5, 0, TAU); ctx.stroke(); ctx.fillStyle = "#25302a"; ctx.beginPath(); ctx.arc(-2, 0, 4.5, 0, TAU); ctx.fill(); ctx.fillStyle = tank.light; ctx.globalAlpha = 0.5; ctx.beginPath(); ctx.arc(-3, -2, 1.6, 0, TAU); ctx.fill(); ctx.globalAlpha = 1; } function drawTankShield(tank) { const time = tank.shieldTimer > 0 ? tank.shieldTimer : tank.spawnProtection; const color = tank.shieldTimer > 0 ? palette.shield : tank.color; const pulse = 1 + Math.sin(gameTime * 7 + tank.id) * 0.04; ctx.save(); ctx.translate(tank.x, tank.y); ctx.scale(pulse, pulse); ctx.globalAlpha = 0.26 + Math.sin(gameTime * 6) * 0.06; ctx.strokeStyle = color; ctx.lineWidth = 2; ctx.shadowColor = color; ctx.shadowBlur = 14; ctx.beginPath(); ctx.arc(0, 0, 23, 0, TAU); ctx.stroke(); ctx.globalAlpha = 0.11; ctx.fillStyle = color; ctx.beginPath(); ctx.arc(0, 0, 22, 0, TAU); ctx.fill(); if (time < 2) { ctx.globalAlpha = 0.2 + Math.sin(gameTime * 18) * 0.12; ctx.beginPath(); ctx.arc(0, 0, 26, 0, TAU); ctx.stroke(); } ctx.restore(); } function drawDoubleIndicator(tank) { ctx.save(); ctx.translate(tank.x, tank.y - 27); ctx.globalAlpha = 0.7 + Math.sin(gameTime * 6) * 0.2; ctx.fillStyle = palette.double; ctx.shadowColor = palette.double; ctx.shadowBlur = 8; ctx.font = "900 9px system-ui"; ctx.textAlign = "center"; ctx.fillText("Ⅱ", 0, 0); ctx.restore(); } function drawSpeedTrail(tank) { ctx.save(); ctx.globalAlpha = 0.4; ctx.fillStyle = palette.speed; ctx.shadowColor = palette.speed; ctx.shadowBlur = 9; for (let side of [-1, 1]) { ctx.beginPath(); ctx.moveTo(-14, side * 8); ctx.lineTo(-25 - Math.random() * 9, side * 8); ctx.lineTo(-16, side * 4.5); ctx.closePath(); ctx.fill(); } ctx.restore(); } function drawPowerups() { for (const power of powerups) power.draw(); } function drawBullets() { for (const bullet of bullets) bullet.draw(); } function drawTanks() { for (const tank of tanks) tank.draw(); } function drawParticles() { for (const item of debris) { const alpha = Math.min(1, item.life / item.maxLife); ctx.save(); ctx.translate(item.x, item.y); ctx.rotate(item.rotation); ctx.globalAlpha = alpha; ctx.fillStyle = item.color; ctx.fillRect(-item.w / 2, -item.h / 2, item.w, item.h); ctx.restore(); } for (const particle of particles) particle.draw(); } function drawFloatingTexts() { for (const text of floatingTexts) { const alpha = Math.min(1, text.life * 1.8); ctx.save(); ctx.globalAlpha = alpha; ctx.font = `900 ${text.size}px system-ui`; ctx.textAlign = "center"; ctx.textBaseline = "middle"; ctx.fillStyle = text.color; ctx.shadowColor = "#000000"; ctx.shadowBlur = 4; ctx.fillText(text.value, text.x, text.y); ctx.restore(); } } function drawSidebar() { const x = PANEL_X; const y = ARENA_Y; const w = PANEL_W; const h = ARENA_H; ctx.save(); const panelGradient = ctx.createLinearGradient(x, y, x + w, y + h); panelGradient.addColorStop(0, "rgba(24,32,26,0.97)"); panelGradient.addColorStop(1, "rgba(10,15,12,0.98)"); ctx.fillStyle = panelGradient; roundedRect(x, y, w, h, 8); ctx.fill(); ctx.strokeStyle = palette.panelBorder; ctx.lineWidth = 1; roundedRect(x + 0.5, y + 0.5, w - 1, h - 1, 8); ctx.stroke(); drawPlayerPanel(tanks[0], x + 12, y + 12, w - 24, 142); drawPlayerPanel(tanks[1], x + 12, y + 164, w - 24, 142); drawMinimap(x + 12, y + 318, w - 24, 144); drawPowerLegend(x + 12, y + 474, w - 24, 112); ctx.restore(); } function drawPlayerPanel(tank, x, y, w, h) { ctx.fillStyle = "rgba(4,7,5,0.43)"; roundedRect(x, y, w, h, 7); ctx.fill(); ctx.strokeStyle = "rgba(193,209,188,0.11)"; roundedRect(x + 0.5, y + 0.5, w - 1, h - 1, 7); ctx.stroke(); ctx.fillStyle = tank.color; ctx.fillRect(x, y, 4, h); ctx.textBaseline = "middle"; ctx.textAlign = "left"; ctx.fillStyle = tank.color; ctx.font = "900 13px system-ui"; ctx.fillText(tank.name, x + 13, y + 18); ctx.fillStyle = palette.muted; ctx.font = "700 9px system-ui"; ctx.textAlign = "right"; ctx.fillText(`SCORE ${tank.score}`, x + w - 11, y + 18); ctx.textAlign = "left"; ctx.fillStyle = palette.muted; ctx.font = "700 9px system-ui"; ctx.fillText("LIVES", x + 13, y + 45); for (let i = 0; i < 3; i++) { const alive = i < tank.lives; drawLifeTankIcon( x + 54 + i * 25, y + 45, alive ? tank.color : "#39413a", alive ? 1 : 0.45 ); } if (!tank.active && tank.lives > 0 && !gameOver) { ctx.fillStyle = "#f0d89a"; ctx.font = "900 13px system-ui"; ctx.fillText( `RESPAWN ${Ma