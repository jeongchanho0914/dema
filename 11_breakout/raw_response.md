<!doctype html> <html lang="en"> <head> <meta charset="UTF-8" /> <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover, user-scalable=no" /> <meta name="theme-color" content="#050712" /> <title>Neon Breakout</title> <style> :root { color-scheme: dark; --cyan: #50f7ff; --blue: #4b7cff; --purple: #b55cff; --pink: #ff4fd8; --red: #ff4f6d; --orange: #ff9f43; --yellow: #ffe66d; --green: #55ff9a; --panel: rgba(9, 13, 30, 0.9); --border: rgba(109, 236, 255, 0.35); }
* {
  box-sizing: border-box;
  -webkit-tap-highlight-color: transparent;
  user-select: none;
}

html,
body {
  width: 100%;
  min-height: 100%;
  margin: 0;
  overflow: hidden;
  background:
    radial-gradient(circle at 50% -20%, #252163 0%, transparent 45%),
    radial-gradient(circle at 15% 80%, rgba(0, 229, 255, 0.13), transparent 38%),
    radial-gradient(circle at 85% 75%, rgba(255, 39, 193, 0.13), transparent 38%),
    #03050d;
  font-family:
    "Trebuchet MS",
    "Segoe UI",
    system-ui,
    sans-serif;
}

body {
  display: grid;
  place-items: center;
  padding:
    max(12px, env(safe-area-inset-top))
    max(12px, env(safe-area-inset-right))
    max(12px, env(safe-area-inset-bottom))
    max(12px, env(safe-area-inset-left));
}

body::before {
  content: "";
  position: fixed;
  inset: 0;
  pointer-events: none;
  opacity: 0.17;
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.025) 1px, transparent 1px);
  background-size: 34px 34px;
  mask-image: radial-gradient(circle at center, black 15%, transparent 85%);
}

.cabinet {
  position: relative;
  width: min(1100px, 100%);
  max-height: calc(100vh - 24px);
  padding: clamp(10px, 1.5vw, 18px);
  border: 1px solid rgba(103, 229, 255, 0.4);
  border-radius: 28px;
  background:
    linear-gradient(145deg, rgba(16, 23, 50, 0.96), rgba(4, 7, 18, 0.98));
  box-shadow:
    0 0 0 2px rgba(255, 255, 255, 0.025) inset,
    0 0 36px rgba(42, 222, 255, 0.17),
    0 25px 90px rgba(0, 0, 0, 0.65);
}

.cabinet::before,
.cabinet::after {
  content: "";
  position: absolute;
  pointer-events: none;
  border-radius: inherit;
}

.cabinet::before {
  inset: -2px;
  z-index: -1;
  background: linear-gradient(
    110deg,
    rgba(55, 238, 255, 0.7),
    transparent 30%,
    transparent 65%,
    rgba(255, 57, 207, 0.7)
  );
  filter: blur(16px);
  opacity: 0.35;
}

.cabinet::after {
  inset: 7px;
  border: 1px solid rgba(255, 255, 255, 0.04);
}

.title-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  min-height: 62px;
  padding: 4px 10px 12px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 12px;
  white-space: nowrap;
}

.logo-mark {
  width: 42px;
  height: 42px;
  position: relative;
  border: 2px solid var(--cyan);
  border-radius: 10px;
  transform: rotate(45deg);
  box-shadow:
    0 0 14px var(--cyan),
    0 0 25px rgba(79, 246, 255, 0.45) inset;
}

.logo-mark::before,
.logo-mark::after {
  content: "";
  position: absolute;
  background: #fff;
  box-shadow: 0 0 10px #fff;
}

.logo-mark::before {
  width: 8px;
  height: 8px;
  left: 7px;
  top: 7px;
  border-radius: 50%;
}

.logo-mark::after {
  width: 16px;
  height: 4px;
  right: 5px;
  bottom: 7px;
  border-radius: 999px;
}

.logo-text {
  line-height: 0.9;
  font-weight: 900;
  letter-spacing: 0.08em;
  font-size: clamp(20px, 3vw, 34px);
  text-transform: uppercase;
  color: #eefeff;
  text-shadow:
    0 0 8px rgba(255, 255, 255, 0.7),
    0 0 18px var(--cyan);
}

.logo-text span {
  display: block;
  margin-top: 6px;
  font-size: 0.38em;
  letter-spacing: 0.42em;
  color: #8beeff;
  text-shadow: 0 0 10px var(--cyan);
}

.status-strip {
  display: flex;
  justify-content: flex-end;
  gap: clamp(7px, 1vw, 14px);
  flex-wrap: wrap;
}

.status-card {
  min-width: 86px;
  padding: 8px 11px;
  border: 1px solid rgba(109, 235, 255, 0.22);
  border-radius: 11px;
  background: rgba(5, 9, 22, 0.75);
  box-shadow:
    0 0 18px rgba(46, 216, 255, 0.06) inset,
    0 7px 22px rgba(0, 0, 0, 0.32);
  text-align: center;
}

.status-label {
  display: block;
  margin-bottom: 2px;
  color: #6e8fa7;
  font-size: 10px;
  font-weight: 800;
  letter-spacing: 0.16em;
  text-transform: uppercase;
}

.status-value {
  display: block;
  min-height: 20px;
  color: #f1fdff;
  font-size: clamp(14px, 2vw, 20px);
  font-weight: 900;
  letter-spacing: 0.05em;
  text-shadow: 0 0 8px rgba(110, 238, 255, 0.55);
}

.screen-wrap {
  position: relative;
  width: 100%;
  aspect-ratio: 3 / 2;
  max-height: calc(100vh - 122px);
  overflow: hidden;
  border: 2px solid rgba(117, 232, 255, 0.4);
  border-radius: 18px;
  background: #02040c;
  box-shadow:
    0 0 0 1px rgba(255, 255, 255, 0.035) inset,
    0 0 30px rgba(0, 229, 255, 0.12),
    0 14px 40px rgba(0, 0, 0, 0.5) inset;
  touch-action: none;
  cursor: crosshair;
}

.screen-wrap::before {
  content: "";
  position: absolute;
  inset: 0;
  z-index: 3;
  pointer-events: none;
  background:
    linear-gradient(
      rgba(255, 255, 255, 0.025) 50%,
      rgba(0, 0, 0, 0.045) 50%
    );
  background-size: 100% 4px;
  mix-blend-mode: overlay;
  opacity: 0.7;
}

.screen-wrap::after {
  content: "";
  position: absolute;
  inset: 0;
  z-index: 4;
  pointer-events: none;
  border-radius: inherit;
  box-shadow:
    0 0 70px rgba(0, 0, 0, 0.62) inset,
    0 0 15px rgba(91, 241, 255, 0.17) inset;
}

canvas {
  display: block;
  width: 100%;
  height: 100%;
}

.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 18px;
  padding: 11px 9px 0;
  color: #55778c;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.key {
  display: inline-grid;
  place-items: center;
  min-width: 25px;
  height: 23px;
  margin: 0 3px;
  padding: 0 6px;
  border: 1px solid rgba(105, 225, 255, 0.35);
  border-bottom-width: 3px;
  border-radius: 5px;
  background: rgba(5, 12, 27, 0.88);
  color: #9ff6ff;
  box-shadow: 0 0 8px rgba(75, 227, 255, 0.13);
  font-size: 10px;
}

@media (max-width: 720px) {
  body {
    padding: 6px;
  }

  .cabinet {
    max-height: calc(100vh - 12px);
    padding: 7px;
    border-radius: 18px;
  }

  .title-bar {
    min-height: 53px;
    padding: 2px 5px 7px;
  }

  .logo-mark {
    width: 30px;
    height: 30px;
    border-radius: 8px;
  }

  .logo-text span {
    display: none;
  }

  .status-strip {
    gap: 5px;
  }

  .status-card {
    min-width: 59px;
    padding: 5px 6px;
    border-radius: 8px;
  }

  .status-label {
    font-size: 7px;
  }

  .status-value {
    font-size: 13px;
  }

  .screen-wrap {
    max-height: calc(100vh - 93px);
    border-radius: 12px;
  }

  .footer {
    display: none;
  }
}

@media (max-width: 430px) {
  .logo-mark {
    display: none;
  }

  .logo-text {
    font-size: 18px;
  }

  .status-card {
    min-width: 52px;
  }

  .status-card:nth-child(3) {
    display: none;
  }
}
</style> </head> <body> <main class="cabinet"> <header class="title-bar"> <div class="logo"> <div class="logo-mark" aria-hidden="true"></div> <div class="logo-text"> Neon Breakout <span>Arcade System</span> </div> </div>
  <div class="status-strip" aria-label="Game status">
    <div class="status-card">
      <span class="status-label">Score</span>
      <span class="status-value" id="score">000000</span>
    </div>
    <div class="status-card">
      <span class="status-label">High</span>
      <span class="status-value" id="highScore">000000</span>
    </div>
    <div class="status-card">
      <span class="status-label">Level</span>
      <span class="status-value" id="level">01</span>
    </div>
    <div class="status-card">
      <span class="status-label">Lives</span>
      <span class="status-value" id="lives">● ● ●</span>
    </div>
  </div>
</header>

<section class="screen-wrap" id="screen">
  <canvas id="game" aria-label="Neon Breakout game"></canvas>
</section>

<footer class="footer">
  <div>
    Move <span class="key">Mouse</span>
    <span class="key">Touch</span>
    <span class="key">←</span><span class="key">→</span>
  </div>
  <div>
    Launch / Fire <span class="key">Click</span>
    <span class="key">Space</span>
    &nbsp; Pause <span class="key">P</span>
  </div>
</footer>
</main> <script> (() => { "use strict"; const canvas = document.getElementById("game"); const ctx = canvas.getContext("2d", { alpha: false }); const screen = document.getElementById("screen"); const scoreEl = document.getElementById("score"); const highScoreEl = document.getElementById("highScore"); const levelEl = document.getElementById("level"); const livesEl = document.getElementById("lives"); const WORLD = Object.freeze({ width: 960, height: 640, wall: 26, ceiling: 64 }); const COLORS = Object.freeze([ "#ff4f6d", "#ff9f43", "#ffe66d", "#55ff9a", "#49dbff", "#7c76ff", "#d65cff" ]); const POWER_TYPES = Object.freeze({ MULTI: "multi", WIDE: "wide", LASER: "laser", SLOW: "slow", LIFE: "life" }); const POWER_INFO = Object.freeze({ [POWER_TYPES.MULTI]: { symbol: "M", label: "MULTI BALL", color: "#b966ff" }, [POWER_TYPES.WIDE]: { symbol: "W", label: "WIDE PADDLE", color: "#48e8ff" }, [POWER_TYPES.LASER]: { symbol: "L", label: "LASER", color: "#ff4b8b" }, [POWER_TYPES.SLOW]: { symbol: "S", label: "SLOW BALL", color: "#55ffb3" }, [POWER_TYPES.LIFE]: { symbol: "+", label: "EXTRA LIFE", color: "#ffe65c" } }); let dpr = 1; let renderScaleX = 1; let renderScaleY = 1; let animationFrame = 0; let lastTime = 0; let elapsed = 0; let audioUnlocked = false; let audioCtx = null; let masterGain = null; const input = { pointerX: WORLD.width / 2, pointerActive: false, left: false, right: false }; const game = { state: "title", score: 0, highScore: Number(localStorage.getItem("neon-breakout-high-score") || 0), level: 1, lives: 3, combo: 0, maxCombo: 0, bricks: [], balls: [], particles: [], powerUps: [], lasers: [], floaters: [], stars: [], paddle: null, levelIntroTimer: 0, message: "", messageTimer: 0, shakeTime: 0, shakeMagnitude: 0, flash: 0, laserCooldown: 0, gameTime: 0, pausedFrom: null, lastBrickHitAt: 0 }; class Paddle { constructor() { this.baseWidth = 136; this.width = this.baseWidth; this.height = 18; this.x = WORLD.width / 2; this.y = WORLD.height - 60; this.targetX = this.x; this.velocityX = 0; this.wideTimer = 0; this.laserTimer = 0; this.glowPulse = 0; } update(dt) { this.glowPulse += dt * 4; if (input.left) this.targetX -= 610 * dt; if (input.right) this.targetX += 610 * dt; const half = this.width / 2; this.targetX = clamp( this.targetX, WORLD.wall + half, WORLD.width - WORLD.wall - half ); const previousX = this.x; const follow = 1 - Math.pow(0.0005, dt); this.x += (this.targetX - this.x) * follow; this.velocityX = (this.x - previousX) / Math.max(dt, 0.001); if (this.wideTimer > 0) { this.wideTimer -= dt; this.width += (210 - this.width) * Math.min(1, dt * 9); } else { this.width += (this.baseWidth - this.width) * Math.min(1, dt * 9); } if (this.laserTimer > 0) { this.laserTimer -= dt; } } draw() { const left = this.x - this.width / 2; const top = this.y - this.height / 2; const laserActive = this.laserTimer > 0; const glow = 10 + Math.sin(this.glowPulse) * 3; ctx.save(); ctx.shadowBlur = glow + (laserActive ? 9 : 0); ctx.shadowColor = laserActive ? "#ff4d94" : "#48eaff"; const gradient = ctx.createLinearGradient(left, top, left, top + this.height); gradient.addColorStop(0, "#f4ffff"); gradient.addColorStop(0.23, laserActive ? "#ff8fbe" : "#85f6ff"); gradient.addColorStop(0.7, laserActive ? "#df286c" : "#168cc8"); gradient.addColorStop(1, "#0a2b56"); roundedRect(left, top, this.width, this.height, 9); ctx.fillStyle = gradient; ctx.fill(); ctx.lineWidth = 2; ctx.strokeStyle = laserActive ? "rgba(255, 175, 212, 0.95)" : "rgba(183, 250, 255, 0.95)"; ctx.stroke(); ctx.shadowBlur = 0; roundedRect(left + 12, top + 3, this.width - 24, 4, 3); ctx.fillStyle = "rgba(255,255,255,0.55)"; ctx.fill(); if (laserActive) { drawLaserCannon(left + 11, this.y - 13); drawLaserCannon(left + this.width - 11, this.y - 13); } ctx.restore(); } catchPower(power) { const info = POWER_INFO[power.type]; switch (power.type) { case POWER_TYPES.MULTI: activateMultiBall(); break; case POWER_TYPES.WIDE: this.wideTimer = Math.max(this.wideTimer, 14); break; case POWER_TYPES.LASER: this.laserTimer = Math.max(this.laserTimer, 14); game.laserCooldown = 0; break; case POWER_TYPES.SLOW: activateSlowBall(); break; case POWER_TYPES.LIFE: game.lives = Math.min(9, game.lives + 1); updateHUD(); break; } game.floaters.push( new FloatingText(this.x, this.y - 30, info.label, info.color, 18) ); spawnBurst(power.x, power.y, info.color, 22, 80, 260); playPowerUpSound(); } } class Ball { constructor(x, y, vx, vy, stuck = false) { this.x = x; this.y = y; this.prevX = x; this.prevY = y; this.radius = 8; this.vx = vx; this.vy = vy; this.stuck = stuck; this.dead = false; this.trail = []; this.speedMultiplier = 1; this.slowTimer = 0; this.spawnProtection = 0.15; } launch() { if (!this.stuck) return; const direction = Math.random() < 0.5 ? -1 : 1; const speed = getBaseBallSpeed() * 0.95; this.vx = direction * speed * 0.36; this.vy = -Math.sqrt(speed * speed - this.vx * this.vx); this.stuck = false; playTone(300, 0.06, "square", 0.08, 540); } update(dt) { if (this.dead) return; if (this.stuck) { this.x = game.paddle.x; this.y = game.paddle.y - game.paddle.height / 2 - this.radius - 2; this.trail.length = 0; return; } if (this.spawnProtection > 0) this.spawnProtection -= dt; if (this.slowTimer > 0) { this.slowTimer -= dt; this.speedMultiplier += (0.68 - this.speedMultiplier) * Math.min(1, dt * 8); } else { this.speedMultiplier += (1 - this.speedMultiplier) * Math.min(1, dt * 2.6); } this.prevX = this.x; this.prevY = this.y; const travelX = this.vx * this.speedMultiplier * dt; const travelY = this.vy * this.speedMultiplier * dt; const distance = Math.hypot(travelX, travelY); const steps = Math.max(1, Math.ceil(distance / 5)); const stepDt = dt / steps; for (let i = 0; i < steps && !this.dead; i++) { this.x += this.vx * this.speedMultiplier * stepDt; this.y += this.vy * this.speedMultiplier * stepDt; this.handleWalls(); this.handlePaddle(); this.handleBricks(); if (this.y - this.radius > WORLD.height + 30) { this.dead = true; } } this.trail.unshift({ x: this.x, y: this.y, life: 1 }); if (this.trail.length > 10) this.trail.pop(); for (const point of this.trail) { point.life -= dt * 4; } } handleWalls() { const left = WORLD.wall; const right = WORLD.width - WORLD.wall; const top = WORLD.ceiling; if (this.x - this.radius < left && this.vx < 0) { this.x = left + this.radius; this.vx = Math.abs(this.vx); playWallSound(); } if (this.x + this.radius > right && this.vx > 0) { this.x = right - this.radius; this.vx = -Math.abs(this.vx); playWallSound(); } if (this.y - this.radius < top && this.vy < 0) { this.y = top + this.radius; this.vy = Math.abs(this.vy); playWallSound(); } } handlePaddle() { if (this.vy <= 0) return; const paddle = game.paddle; const left = paddle.x - paddle.width / 2; const right = paddle.x + paddle.width / 2; const top = paddle.y - paddle.height / 2; const bottom = paddle.y + paddle.height / 2; if ( this.x + this.radius >= left && this.x - this.radius <= right && this.y + this.radius >= top && this.y - this.radius <= bottom && this.prevY + this.radius <= top + 6 ) { this.y = top - this.radius - 0.5; const hitPosition = clamp( (this.x - paddle.x) / (paddle.width / 2), -1, 1 ); const maxAngle = Math.PI * 0.39; const angle = hitPosition * maxAngle; const currentSpeed = clamp( Math.hypot(this.vx, this.vy) * 1.015, getBaseBallSpeed() * 0.9, getBaseBallSpeed() * 1.42 ); this.vx = Math.sin(angle) * currentSpeed + clamp(paddle.velocityX * 0.06, -90, 90); this.vy = -Math.abs(Math.cos(angle) * currentSpeed); enforceBallSpeed(this); game.combo = 0; playPaddleSound(hitPosition); spawnSparkLine(this.x, top, "#76f7ff", 9); } } handleBricks() { const nearby = game.bricks; for (let i = 0; i < nearby.length; i++) { const brick = nearby[i]; if (!brick.alive) continue; if ( this.x + this.radius < brick.x || this.x - this.radius > brick.x + brick.width || this.y + this.radius < brick.y || this.y - this.radius > brick.y + brick.height ) { continue; } const closestX = clamp(this.x, brick.x, brick.x + brick.width); const closestY = clamp(this.y, brick.y, brick.y + brick.height); const dx = this.x - closestX; const dy = this.y - closestY; if (dx * dx + dy * dy > this.radius * this.radius) continue; const fromLeft = Math.abs(this.prevX + this.radius - brick.x); const fromRight = Math.abs(this.prevX - this.radius - (brick.x + brick.width)); const fromTop = Math.abs(this.prevY + this.radius - brick.y); const fromBottom = Math.abs(this.prevY - this.radius - (brick.y + brick.height)); const min = Math.min(fromLeft, fromRight, fromTop, fromBottom); if (min === fromLeft && this.vx > 0) { this.vx = -Math.abs(this.vx); this.x = brick.x - this.radius - 0.2; } else if (min === fromRight && this.vx < 0) { this.vx = Math.abs(this.vx); this.x = brick.x + brick.width + this.radius + 0.2; } else if (min === fromTop && this.vy > 0) { this.vy = -Math.abs(this.vy); this.y = brick.y - this.radius - 0.2; } else { this.vy = Math.abs(this.vy); this.y = brick.y + brick.height + this.radius + 0.2; } damageBrick(brick, this.x, this.y); break; } } draw() { if (this.dead) return; for (let i = this.trail.length - 1; i >= 0; i--) { const point = this.trail[i]; if (point.life <= 0) continue; const ratio = (this.trail.length - i) / this.trail.length; ctx.beginPath(); ctx.arc( point.x, point.y, this.radius * ratio * 0.72, 0, Math.PI * 2 ); ctx.fillStyle = `rgba(69, 224, 255, ${point.life * 0.18})`; ctx.fill(); } ctx.save(); ctx.shadowBlur = 20; ctx.shadowColor = "#5cecff"; const gradient = ctx.createRadialGradient( this.x - 2.5, this.y - 3, 1, this.x, this.y, this.radius ); gradient.addColorStop(0, "#ffffff"); gradient.addColorStop(0.32, "#c9fbff"); gradient.addColorStop(0.67, "#47dfff"); gradient.addColorStop(1, "#2670ff"); ctx.beginPath(); ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2); ctx.fillStyle = gradient; ctx.fill(); ctx.lineWidth = 1.2; ctx.strokeStyle = "rgba(255,255,255,0.8)"; ctx.stroke(); ctx.restore(); } } class Brick { constructor(x, y, width, height, row, col, hp, points, color, special = false) { this.x = x; this.y = y; this.width = width; this.height = height; this.row = row; this.col = col; this.hp = hp; this.maxHp = hp; this.points = points; this.color = color; this.alive = true; this.hitFlash = 0; this.scale = 1; this.special = special; this.phase = Math.random() * Math.PI * 2; } update(dt) { this.hitFlash = Math.max(0, this.hitFlash - dt * 5); this.scale += (1 - this.scale) * Math.min(1, dt * 16); this.phase += dt * 3; } draw() { if (!this.alive) return; const cx = this.x + this.width / 2; const cy = this.y + this.height / 2; const w = this.width * this.scale; const h = this.height * this.scale; const x = cx - w / 2; const y = cy - h / 2; ctx.save(); ctx.shadowBlur = 10 + this.hitFlash * 12; ctx.shadowColor = this.color; const gradient = ctx.createLinearGradient(x, y, x, y + h); gradient.addColorStop(0, lighten(this.color, 0.47)); gradient.addColorStop(0.16, lighten(this.color, 0.2)); gradient.addColorStop(0.58, this.color); gradient.addColorStop(1, darken(this.color, 0.45)); roundedRect(x, y, w, h, 6); ctx.fillStyle = gradient; ctx.fill(); ctx.lineWidth = 1.5; ctx.strokeStyle = this.hitFlash > 0 ? `rgba(255,255,255,${0.55 + this.hitFlash * 0.45})` : colorAlpha(lighten(this.color, 0.65), 0.72); ctx.stroke(); ctx.shadowBlur = 0; roundedRect(x + 5, y + 3, Math.max(0, w - 10), Math.max(2, h * 0.2), 3); ctx.fillStyle = "rgba(255,255,255,0.28)"; ctx.fill(); if (this.hp > 1) { for (let i = 0; i < this.hp - 1; i++) { const size = 4; const dotX = cx + (i - (this.hp - 2) / 2) * 9; ctx.beginPath(); ctx.arc(dotX, cy + 3, size, 0, Math.PI * 2); ctx.fillStyle = "rgba(4,8,20,0.62)"; ctx.fill(); ctx.strokeStyle = "rgba(255,255,255,0.3)"; ctx.stroke(); } } if (this.special) { const pulse = 0.68 + Math.sin(this.phase) * 0.25; ctx.beginPath(); ctx.arc(cx, cy + 1, 5, 0, Math.PI * 2); ctx.fillStyle = `rgba(255,255,255,${pulse})`; ctx.shadowBlur = 13; ctx.shadowColor = "#fff"; ctx.fill(); } ctx.restore(); } } class PowerUp { constructor(x, y, type) { this.x = x; this.y = y; this.type = type; this.vy = 118; this.width = 34; this.height = 20; this.rotation = 0; this.alive = true; this.life = 0; } update(dt) { this.life += dt; this.y += this.vy * dt; this.rotation += dt * 3.8; const paddle = game.paddle; const left = paddle.x - paddle.width / 2; const right = paddle.x + paddle.width / 2; const top = paddle.y - paddle.height / 2; if ( this.x + this.width / 2 >= left && this.x - this.width / 2 <= right && this.y + this.height / 2 >= top && this.y - this.height / 2 <= paddle.y + paddle.height / 2 ) { this.alive = false; paddle.catchPower(this); } if (this.y > WORLD.height + 30) this.alive = false; } draw() { const info = POWER_INFO[this.type]; const squash = 0.78 + Math.abs(Math.cos(this.rotation)) * 0.22; const w = this.width * squash; const h = this.height; ctx.save(); ctx.translate(this.x, this.y); ctx.shadowBlur = 18; ctx.shadowColor = info.color; const gradient = ctx.createLinearGradient(0, -h / 2, 0, h / 2); gradient.addColorStop(0, "#ffffff"); gradient.addColorStop(0.25, lighten(info.color, 0.3)); gradient.addColorStop(1, darken(info.color, 0.36)); roundedRect(-w / 2, -h / 2, w, h, 8); ctx.fillStyle = gradient; ctx.fill(); ctx.lineWidth = 1.5; ctx.strokeStyle = colorAlpha(info.color, 0.95); ctx.stroke(); ctx.shadowBlur = 8; ctx.fillStyle = "#07101c"; ctx.textAlign = "center"; ctx.textBaseline = "middle"; ctx.font = "900 13px Trebuchet MS"; ctx.fillText(info.symbol, 0, 0.5); ctx.restore(); } } class Particle { constructor(x, y, color, speedMin = 40, speedMax = 220) { const angle = Math.random() * Math.PI * 2; const speed = random(speedMin, speedMax); this.x = x; this.y = y; this.vx = Math.cos(angle) * speed; this.vy = Math.sin(angle) * speed; this.gravity = random(80, 240); this.drag = random(0.9, 2.4); this.life = random(0.35, 0.9); this.maxLife = this.life; this.size = random(1.8, 5.8); this.color = color; this.rotation = Math.random() * Math.PI; this.spin = random(-8, 8); this.shape = Math.random() < 0.72 ? "rect" : "circle"; } update(dt) { this.life -= dt; this.vx *= Math.exp(-this.drag * dt); this.vy *= Math.exp(-this.drag * dt); this.vy += this.gravity * dt; this.x += this.vx * dt; this.y += this.vy * dt; this.rotation += this.spin * dt; } draw() { if (this.life <= 0) return; const alpha = Math.max(0, this.life / this.maxLife); ctx.save(); ctx.globalAlpha = alpha; ctx.translate(this.x, this.y); ctx.rotate(this.rotation); ctx.shadowBlur = 7; ctx.shadowColor = this.color; ctx.fillStyle = this.color; if (this.shape === "circle") { ctx.beginPath(); ctx.arc(0, 0, this.size * alpha, 0, Math.PI * 2); ctx.fill(); } else { ctx.fillRect( -this.size * alpha, -this.size * alpha * 0.45, this.size * 2 * alpha, this.size * 0.9 * alpha ); } ctx.restore(); } } class FloatingText { constructor(x, y, text, color = "#fff", size = 16) { this.x = x; this.y = y; this.text = text; this.color = color; this.size = size; this.life = 1; this.maxLife = 1; this.vy = -40; } update(dt) { this.life -= dt; this.y += this.vy * dt; this.vy *= Math.exp(-1.7 * dt); } draw() { if (this.life <= 0) return; const alpha = clamp(this.life / this.maxLife, 0, 1); ctx.save(); ctx.globalAlpha = alpha; ctx.textAlign = "center"; ctx.textBaseline = "middle"; ctx.font = `900 ${this.size}px Trebuchet MS`; ctx.fillStyle = this.color; ctx.shadowBlur = 11; ctx.shadowColor = this.color; ctx.fillText(this.text, this.x, this.y); ctx.restore(); } } class Laser { constructor(x, y) { this.x = x; this.y = y; this.prevY = y; this.vy = -790; this.width = 4; this.height = 17; this.alive = true; } update(dt) { this.prevY = this.y; this.y += this.vy * dt; for (const brick of game.bricks) { if (!brick.alive) continue; if ( this.x + this.width / 2 >= brick.x && this.x - this.width / 2 <= brick.x + brick.width && this.y - this.height / 2 <= brick.y + brick.height && this.prevY + this.height / 2 >= brick.y ) { this.alive = false; damageBrick(brick, this.x, this.y, true); break; } } if (this.y < WORLD.ceiling - 30) this.alive = false; } draw() { ctx.save(); ctx.shadowBlur = 13; ctx.shadowColor = "#ff3b87"; const gradient = ctx.createLinearGradient( this.x, this.y - this.height / 2, this.x, this.y + this.height / 2 ); gradient.addColorStop(0, "rgba(255,255,255,0)"); gradient.addColorStop(0.35, "#ffffff"); gradient.addColorStop(1, "#ff287a"); roundedRect( this.x - this.width / 2, this.y - this.height / 2, this.width, this.height, 3 ); ctx.fillStyle = gradient; ctx.fill(); ctx.restore(); } } function initialize() { resize(); createStars(); resetGame(); game.state = "title"; updateHUD(); animationFrame = requestAnimationFrame(loop); } function resetGame() { game.score = 0; game.level = 1; game.lives = 3; game.combo = 0; game.maxCombo = 0; game.particles.length = 0; game.powerUps.length = 0; game.lasers.length = 0; game.floaters.length = 0; game.paddle = new Paddle(); buildLevel(game.level); createServeBall(); updateHUD(); } function startGame() { resetGame(); game.state = "levelIntro"; game.levelIntroTimer = 1.65; game.message = "LEVEL 01"; game.messageTimer = 1.65; unlockAudio(); playStartSound(); } function buildLevel(level) { game.bricks.length = 0; game.powerUps.length = 0; game.lasers.length = 0; const rows = 5; const cols = 11; const gap = 8; const sideMargin = 62; const brickWidth = (WORLD.width - sideMargin * 2 - gap * (cols - 1)) / cols; const brickHeight = 29; const top = 104; for (let row = 0; row < rows; row++) { for (let col = 0; col < cols; col++) { if (!shouldPlaceBrick(level, row, col, rows, cols)) continue; const x = sideMargin + col * (brickWidth + gap); const y = top + row * (brickHeight + gap); const color = COLORS[(row + Math.floor((level - 1) / 2)) % COLORS.length]; const hp = getBrickHP(level, row, col); const points = (rows - row) * 20 + (hp - 1) * 35; const specialChance = level === 1 ? 0.15 : 0.18; const special = Math.random() < specialChance; game.bricks.push( new Brick( x, y, brickWidth, brickHeight, row, col, hp, points, color, special ) ); } } } function shouldPlaceBrick(level, row, col, rows, cols) { const pattern = (level - 1) % 7; switch (pattern) { case 0: return true; case 1: return !(row === 1 && col % 3 === 1) && !(row === 3 && col % 3 === 0); case 2: { const center = (cols - 1) / 2; return Math.abs(col - center) <= row + 1 || row === rows - 1; } case 3: return (row + col) % 2 === 0 || row === 0 || row === rows - 1; case 4: return col === 0 || col === cols - 1 || row === 0 || row === rows - 1 || (row === 2 && col >= 3 && col <= 7); case 5: { const center = (cols - 1) / 2; return Math.abs(col - center) + Math.abs(row - 2) <= 5; } case 6: return !( (row === 1 || row === 3) && (col === 2 || col === 5 || col === 8) ); default: return true; } } function getBrickHP(level, row, col) { if (level < 2) return 1; let hp = 1; const difficulty = Math.min(4, Math.floor((level - 1) / 2)); if ((row + col + level) % 5 === 0) hp += 1; if (difficulty >= 2 && row === 0 && col % 2 === 0) hp += 1; if (difficulty >= 3 && (col === 0 || col === 10)) hp += 1; return Math.min(4, hp); } function createServeBall() { game.balls = [ new Ball( game.paddle.x, game.paddle.y - 24, 0, -getBaseBallSpeed(), true ) ]; } function launchBalls() { let launched = false; for (const ball of game.balls) { if (ball.stuck) { ball.launch(); launched = true; } } return launched; } function update(dt) { elapsed += dt; if (game.state === "paused" || game.state === "title" || game.state === "gameover") { updateAmbient(dt); return; } game.gameTime += dt; if (game.state === "levelIntro") { game.levelIntroTimer -= dt; updateAmbient(dt); if (game.levelIntroTimer <= 0) { game.state = "playing"; } return; } if (game.state === "levelClear") { game.levelIntroTimer -= dt; updateEffects(dt); if (game.levelIntroTimer <= 0) { game.level += 1; buildLevel(game.level); game.paddle = new Paddle(); createServeBall(); game.combo = 0; game.state = "levelIntro"; game.levelIntroTimer = 1.55; game.message = `LEVEL ${String(game.level).padStart(2, "0")}`; game.messageTimer = 1.55; updateHUD(); playStartSound(); } return; } game.paddle.update(dt); for (const brick of game.bricks) brick.update(dt); for (const ball of game.balls) ball.update(dt); for (const power of game.powerUps) power.update(dt); for (const laser of game.lasers) laser.update(dt); updateEffects(dt); handleLaserSystem(dt); game.balls = game.balls.filter((ball) => !ball.dead); game.powerUps = game.powerUps.filter((power) => power.alive); game.lasers = game.lasers.filter((laser) => laser.alive); if (game.balls.length === 0) { loseLife(); } if ( game.state === "playing" && game.bricks.length > 0 && game.bricks.every((brick) => !brick.alive) ) { clearLevel(); } if (game.messageTimer > 0) game.messageTimer -= dt; } function updateAmbient(dt) { for (const star of game.stars) { star.twinkle += dt * star.speed; } updateEffects(dt, true); if (game.messageTimer > 0) game.messageTimer -= dt; } function updateEffects(dt, ambientOnly = false) { for (const particle of game.particles) particle.update(dt); for (const floater of game.floaters) floater.update(dt); game.particles = game.particles.filter((particle) => particle.life > 0); game.floaters = game.floaters.filter((floater) => floater.life > 0); if (!ambientOnly) { for (const star of game.stars) { star.twinkle += dt * star.speed; } } game.shakeTime = Math.max(0, game.shakeTime - dt); game.flash = Math.max(0, game.flash - dt * 2.5); } function handleLaserSystem(dt) { if (game.paddle.laserTimer <= 0) return; game.laserCooldown -= dt; if (game.laserCooldown <= 0) { game.laserCooldown = 0.36; const half = game.paddle.width / 2; game.lasers.push( new Laser(game.paddle.x - half + 12, game.paddle.y - 18), new Laser(game.paddle.x + half - 12, game.paddle.y - 18) ); playLaserSound(); } } function loseLife() { if (game.state !== "playing") return; game.lives -= 1; game.combo = 0; game.powerUps.length = 0; game.lasers.length = 0; game.paddle.wideTimer = 0; game.paddle.laserTimer = 0; game.shakeTime = 0.55; game.shakeMagnitude = 18; game.flash = 0.45; updateHUD(); playLoseSound(); spawnBurst( game.paddle.x, WORLD.height - 16, "#ff4a72", 34, 120, 360 ); if (game.lives <= 0) { game.state = "gameover"; game.message = "GAME OVER"; game.messageTimer = 999; commitHighScore(); playGameOverSound(); } else { game.state = "levelIntro"; game.levelIntroTimer = 1.25; game.message = "BALL LOST"; game.messageTimer = 1.25; createServeBall(); } } function clearLevel() { game.state = "levelClear"; game.levelIntroTimer = 2.1; game.message = "SECTOR CLEARED"; game.messageTimer = 2.1; const clearBonus = game.level * 1000 + game.lives * 250; addScore(clearBonus); game.floaters.push( new FloatingText( WORLD.width / 2, WORLD.height / 2 + 55, `BONUS +${clearBonus}`, "#ffe65e", 23 ) ); for (let i = 0; i < 9; i++) { setTimeout(() => { if (game.state !== "levelClear") return; spawnBurst( random(150, WORLD.width - 150), random(120, 360), COLORS[i % COLORS.length], 24, 100, 360 ); }, i * 90); } playLevelClearSound(); } function damageBrick(brick, hitX, hitY, fromLaser = false) { if (!brick.alive) return; brick.hp -= 1; brick.hitFlash = 1; brick.scale = 0.92; spawnBurst( clamp(hitX, brick.x, brick.x + brick.width), clamp(hitY, brick.y, brick.y + brick.height), brick.color, brick.hp <= 0 ? 16 : 7, 50, brick.hp <= 0 ? 260 : 150 ); if (brick.hp > 0) { addScore(10); playBrickHitSound(brick.row, false); return; } brick.alive = false; game.combo += 1; game.maxCombo = Math.max(game.maxCombo, game.combo); const multiplier = Math.min(8, 1 + Math.floor((game.combo - 1) / 3)); const earned = brick.points * multiplier; addScore(earned); game.floaters.push( new FloatingText( brick.x + brick.width / 2, brick.y + brick.height / 2, multiplier > 1 ? `+${earned} x${multiplier}` : `+${earned}`, multiplier >= 4 ? "#ffe66d" : "#ffffff", multiplier >= 4 ? 18 : 15 ) ); if (brick.special || Math.random() < 0.11) { dropPowerUp( brick.x + brick.width / 2, brick.y + brick.height / 2 ); } if (game.combo > 0 && game.combo % 5 === 0) { game.floaters.push( new FloatingText( WORLD.width / 2, 80, `${game.combo} HIT COMBO`, "#ff72df", 23 ) ); playComboSound(game.combo); } game.shakeTime = Math.max(game.shakeTime, fromLaser ? 0.04 : 0.075); game.shakeMagnitude = Math.max(game.shakeMagnitude, 2.5); playBrickHitSound(brick.row, true); } function dropPowerUp(x, y) { const roll = Math.random(); let type; if (roll < 0.23) type = POWER_TYPES.MULTI; else if (roll < 0.46) type = POWER_TYPES.WIDE; else if (roll < 0.67) type = POWER_TYPES.LASER; else if (roll < 0.88) type = POWER_TYPES.SLOW; else type = POWER_TYPES.LIFE; game.powerUps.push(new PowerUp(x, y, type)); } function activateMultiBall() { const active = game.balls.filter((ball) => !ball.dead); if (active.length === 0) return; const sourceBalls = active.slice(0, 3); const newBalls = []; for (const source of sourceBalls) { const speed = Math.max( getBaseBallSpeed(), Math.hypot(source.vx, source.vy) ); const baseAngle = Math.atan2(source.vy, source.vx); for (const offset of [-0.42, 0.42]) { if (game.balls.length + newBalls.length >= 8) break; const angle = baseAngle + offset; newBalls.push( new Ball( source.x, source.y, Math.cos(angle) * speed, Math.sin(angle) * speed, false ) ); } } game.balls.push(...newBalls); } function activateSlowBall() { for (const ball of game.balls) { ball.slowTimer = Math.max(ball.slowTimer, 10); } } function enforceBallSpeed(ball) { const speed = Math.hypot(ball.vx, ball.vy); const minSpeed = getBaseBallSpeed() * 0.88; const maxSpeed = getBaseBallSpeed() * 1.45; const target = clamp(speed, minSpeed, maxSpeed); if (speed > 0.001) { ball.vx = (ball.vx / speed) * target; ball.vy = (ball.vy / speed) * target; } const minimumHorizontal = 105; if (Math.abs(ball.vx) < minimumHorizontal) { ball.vx = Math.sign(ball.vx || (Math.random() - 0.5)) * minimumHorizontal; const verticalSign = Math.sign(ball.vy || -1); ball.vy = verticalSign * Math.sqrt(Math.max(100, target * target - ball.vx * ball.vx)); } } function getBaseBallSpeed() { return Math.min(610, 370 + (game.level - 1) * 24); } function addScore(amount) { game.score += Math.round(amount); if (game.score > game.highScore) { game.highScore = game.score; } updateHUD(); } function commitHighScore() { if (game.highScore < game.score) { game.highScore = game.score; } localStorage.setItem( "neon-breakout-high-score", String(game.highScore) ); updateHUD(); } function updateHUD() { scoreEl.textContent = String(game.score).padStart(6, "0"); highScoreEl.textContent = String( Math.max(game.highScore, game.score) ).padStart(6, "0"); levelEl.textContent = String(game.level).padStart(2, "0"); livesEl.textContent = game.lives <= 5 ? Array(Math.max(0, game.lives)).fill("●").join(" ") : `● × ${game.lives}`; } function render() { ctx.setTransform(dpr * renderScaleX, 0, 0, dpr * renderScaleY, 0, 0); drawBackground(); let shakeX = 0; let shakeY = 0; if (game.shakeTime > 0) { const normalized = clamp(game.shakeTime / 0.55, 0, 1); const magnitude = game.shakeMagnitude * normalized; shakeX = random(-magnitude, magnitude); shakeY = random(-magnitude, magnitude); } ctx.save(); ctx.translate(shakeX, shakeY); drawArena(); for (const brick of game.bricks) brick.draw(); for (const power of game.powerUps) power.draw(); for (const laser of game.lasers) laser.draw(); for (const ball of game.balls) ball.draw(); if (game.paddle) game.paddle.draw(); for (const particle of game.particles) particle.draw(); for (const floater of game.floaters) floater.draw(); drawComboIndicator(); drawPowerTimers(); ctx.restore(); drawOverlay(); if (game.flash > 0) { ctx.fillStyle = `rgba(255,55,100,${game.flash * 0.38})`; ctx.fillRect(0, 0, WORLD.width, WORLD.height); } } function drawBackground() { ctx.fillStyle = "#02040d"; ctx.fillRect(0, 0, WORLD.width, WORLD.height); const bg = ctx.createRadialGradient( WORLD.width / 2, WORLD.height * 0.25, 20, WORLD.width / 2, WORLD.height * 0.4, WORLD.width * 0.75 ); bg.addColorStop(0, "rgba(25, 29, 77, 0.88)"); bg.addColorStop(0.48, "rgba(8, 13, 35, 0.72)"); bg.addColorStop(1, "rgba(2, 4, 13, 0)"); ctx.fillStyle = bg; ctx.fillRect(0, 0, WORLD.width, WORLD.height); for (const star of game.stars) { const alpha = star.alpha * (0.62 + Math.sin(star.twinkle) * 0.38); ctx.fillStyle = `rgba(${star.tint},${alpha})`; ctx.fillRect(star.x, star.y, star.size, star.size); } ctx.save(); ctx.globalAlpha = 0.09; ctx.strokeStyle = "#4beaff"; ctx.lineWidth = 1; const horizon = 378; for (let y = horizon; y < WORLD.height; y += 31) { const perspective = (y - horizon) / (WORLD.height - horizon); const curvedY = horizon + perspective * perspective * (WORLD.height - horizon); ctx.beginPath(); ctx.moveTo(0, curvedY); ctx.lineTo(WORLD.width, curvedY); ctx.stroke(); } for (let x = -WORLD.width; x <= WORLD.width * 2; x += 90) { ctx.beginPath(); ctx.moveTo(WORLD.width / 2, horizon); ctx.lineTo(x, WORLD.height); ctx.stroke(); } ctx.restore(); const horizonGlow = ctx.createLinearGradient(0, 340, 0, 460); horizonGlow.addColorStop(0, "rgba(58, 218, 255, 0)"); horizonGlow.addColorStop(0.46, "rgba(58, 218, 255, 0.07)"); horizonGlow.addColorStop(1, "rgba(58, 218, 255, 0)"); ctx.fillStyle = horizonGlow; ctx.fillRect(0, 330, WORLD.width, 150); } function drawArena() { ctx.save(); const wallGradient = ctx.createLinearGradient(0, 0, WORLD.wall, 0); wallGradient.addColorStop(0, "#081126"); wallGradient.addColorStop(0.45, "#153d67"); wallGradient.addColorStop(0.8, "#45dffc"); wallGradient.addColorStop(1, "#d9ffff"); ctx.shadowBlur = 16; ctx.shadowColor = "#38dfff"; ctx.fillStyle = wallGradient; ctx.fillRect(11, WORLD.ceiling - 8, WORLD.wall - 11, WORLD.height - WORLD.ceiling + 8); const rightWallGradient = ctx.createLinearGradient( WORLD.width - WORLD.wall, 0, WORLD.width, 0 ); rightWallGradient.addColorStop(0, "#d9ffff"); rightWallGradient.addColorStop(0.2, "#45dffc"); rightWallGradient.addColorStop(0.55, "#153d67"); rightWallGradient.addColorStop(1, "#081126"); ctx.fillStyle = rightWallGradient; ctx.fillRect( WORLD.width - WORLD.wall, WORLD.ceiling - 8, WORLD.wall - 11, WORLD.height - WORLD.ceiling + 8 ); const topGradient = ctx.createLinearGradient(0, WORLD.ceiling - 18, 0, WORLD.ceiling); topGradient.addColorStop(0, "#081126"); topGradient.addColorStop(0.45, "#1b4b7b"); topGradient.addColorStop(0.82, "#50eaff"); topGradient.addColorStop(1, "#e5ffff"); ctx.fillStyle = topGradient; ctx.fillRect( WORLD.wall, WORLD.ceiling - 18, WORLD.width - WORLD.wall * 2, 18 ); ctx.shadowBlur = 0; ctx.fillStyle = "rgba(255,255,255,0.55)"; ctx.fillRect(WORLD.wall, WORLD.ceiling, WORLD.width - WORLD.wall * 2, 1); ctx.restore(); } function drawComboIndicator() { if (game.combo < 2 || game.state !== "playing") return; const multiplier = Math.min( 8, 1 + Math.floor((game.combo - 1) / 3) ); ctx.save(); ctx.textAlign = "right"; ctx.textBaseline = "top"; ctx.font = "900 15px Trebuchet MS"; ctx.fillStyle = "#ff8ce7"; ctx.shadowBlur = 12; ctx.shadowColor = "#ff4fd8"; ctx.fillText(`${game.combo} HIT`, WORLD.width - 48, 79); ctx.font = "900 26px Trebuchet MS"; ctx.fillStyle = multiplier >= 4 ? "#ffe66d" : "#ffffff"; ctx.fillText(`x${multiplier}`, WORLD.width - 48, 97); ctx.restore(); } function drawPowerTimers() { if (!game.paddle || game.state !== "playing") return; const active = []; if (game.paddle.wideTimer > 0) { active.push({ label: "WIDE", time: game.paddle.wideTimer, max: 14, color: POWER_INFO[POWER_TYPES.WIDE].color }); } if (game.paddle.laserTimer > 0) { active.push({ label: "LASER", time: game.paddle.laserTimer, max: 14, color: POWER_INFO[POWER_TYPES.LASER].color }); } let slowTime = 0; for (const ball of game.balls) { slowTime = Math.max(slowTime, ball.slowTimer); } if (slowTime > 0) { active.push({ label: "SLOW", time: slowTime, max: 10, color: POWER_INFO[POWER_TYPES.SLOW].color }); } if (active.length === 0) return; const barWidth = 116; const barHeight = 8; const startX = 44; const startY = WORLD.height - 30 - active.length * 23; ctx.save(); ctx.font = "800 10px Trebuchet MS"; ctx.textBaseline = "middle"; active.forEach((item, index) => { const y = startY + index * 23; const ratio = clamp(item.time / item.max, 0, 1); ctx.fillStyle = "#7991aa"; ctx.textAlign = "left"; ctx.fillText(item.label, startX, y + 3); roundedRect(startX + 42, y, barWidth, barHeight, 4); ctx.fillStyle = "rgba(0,0,0,0.6)"; ctx.fill(); if (ratio > 0) { roundedRect(startX + 42, y, barWidth * ratio, barHeight, 4); ctx.fillStyle = item.color; ctx.shadowBlur = 8; ctx.shadowColor = item.color; ctx.fill(); ctx.shadowBlur = 0; } }); ctx.restore(); } function drawOverlay() { if (game.state === "playing") return; if (game.state === "title") { drawTitleScreen(); return; } if (game.state === "paused") { drawDimmer(0.64); drawCenteredTitle("PAUSED", "#7df4ff", 56); drawCenteredSubtitle("PRESS P OR TAP TO RESUME", 340); return; } if (game.state === "gameover") { drawDimmer(0.72); drawCenteredTitle("GAME OVER", "#ff557e", 60); ctx.save(); ctx.textAlign = "center"; ctx.fillStyle = "#b9dbe8"; ctx.font = "800 18px Trebuchet MS"; ctx.fillText( `SCORE ${String(game.score).padStart(6, "0")}`, WORLD.width / 2, 342 ); ctx.fillText( `MAX COMBO ${game.maxCombo}`, WORLD.width / 2, 373 ); const pulse = 0.65 + Math.sin(elapsed * 4) * 0.35; ctx.globalAlpha = pulse; ctx.fillStyle = "#ffffff"; ctx.shadowBlur = 12; ctx.shadowColor = "#57eaff"; ctx.font = "900 16px Trebuchet MS"; ctx.fillText( "CLICK / TAP / SPACE TO PLAY AGAIN", WORLD.width / 2, 430 ); ctx.restore(); return; } if ( game.state === "levelIntro" || game.state === "levelClear" ) { drawDimmer(game.state === "levelClear" ? 0.33 : 0.26); const color = game.state === "levelClear" ? "#ffe66d" : "#69f2ff"; drawCenteredTitle(game.message, color, game.state === "levelClear" ? 47 : 52); if ( game.state === "levelIntro" && game.message.startsWith("LEVEL") ) { drawCenteredSubtitle("GET READY", 352); } } } function drawTitleScreen() { drawDimmer(0.2); ctx.save(); ctx.textAlign = "center"; ctx.textBaseline = "middle"; const glow = 22 + Math.sin(elapsed * 2.4) * 5; ctx.shadowBlur = glow; ctx.shadowColor = "#4deaff"; const gradient = ctx.createLinearGradient(0, 205, 0, 330); gradient.addColorStop(0, "#ffffff"); gradient.addColorStop(0.34, "#79f4ff"); gradient.addColorStop(0.66, "#617eff"); gradient.addColorStop(1, "#d54eff"); ctx.fillStyle = gradient; ctx.font = "900 75px Trebuchet MS"; ctx.fillText("BREAKOUT", WORLD.width / 2, 248); ctx.shadowBlur = 14; ctx.shadowColor = "#ff42c6"; ctx.fillStyle = "#ff75db"; ctx.font = "900 24px Trebuchet MS"; ctx.letterSpacing = "8px"; ctx.fillText("NEON OVERDRIVE", WORLD.width / 2, 305); ctx.shadowBlur = 0; ctx.font = "800 15px Trebuchet MS"; ctx.fillStyle = "#7797ac"; ctx.fillText( "SMASH BRICKS • CATCH POWER-UPS • CHAIN COMBOS", WORLD.width / 2, 357 ); const pulse = 0.62 + Math.sin(elapsed * 4) * 0.38; ctx.globalAlpha = pulse; ctx.shadowBlur = 13; ctx.shadowColor = "#55eaff"; ctx.fillStyle = "#efffff"; ctx.font = "900 18px Trebuchet MS"; ctx.fillText( "CLICK / TAP / SPACE TO START", WORLD.width / 2, 433 ); ctx.globalAlpha = 1; ctx.shadowBlur = 0; ctx.fillStyle = "#527185"; ctx.font = "700 12px Trebuchet MS"; ctx.fillText( "MOVE WITH MOUSE, TOUCH OR ARROW KEYS", WORLD.width / 2, 474 ); ctx.restore(); } function drawDimmer(alpha) { ctx.fillStyle = `rgba(2,4,14,${alpha})`; ctx.fillRect(0, 0, WORLD.width, WORLD.height); const vignette = ctx.createRadialGradient( WORLD.width / 2, WORLD.height / 2, 90, WORLD.width / 2, WORLD.height / 2, 520 ); vignette.addColorStop(0, "rgba(14,34,67,0.1)"); vignette.addColorStop(1, "rgba(0,0,0,0.75)"); ctx.fillStyle = vignette; ctx.fillRect(0, 0, WORLD.width, WORLD.height); } function drawCenteredTitle(text, color, size) { ctx.save(); ctx.textAlign = "center"; ctx.textBaseline = "middle"; ctx.font = `900 ${size}px Trebuchet MS`; ctx.fillStyle = color; ctx.shadowBlur = 24; ctx.shadowColor = color; ctx.fillText(text, WORLD.width / 2, 282); ctx.restore(); } function drawCenteredSubtitle(text, y) { ctx.save(); ctx.textAlign = "center"; ctx.textBaseline = "middle"; ctx.font = "900 16px Trebuchet MS"; ctx.fillStyle = "#e8fdff"; ctx.shadowBlur = 10; ctx.shadowColor = "#59eaff"; ctx.fillText(text, WORLD.width / 2, y); ctx.restore(); } function createStars() { game.stars.length = 0; for (let i = 0; i < 100; i++) { const tone = Math.random(); game.stars.push({ x: Math.random() * WORLD.width, y: WORLD.ceiling + Math.random() * (WORLD.height - WORLD.ceiling), size: random(0.7, 2), alpha: random(0.1, 0.65), speed: random(0.8, 3.3), twinkle: Math.random() * Math.PI * 2, tint: tone < 0.7 ? "174,232,255" : tone < 0.88 ? "255,176,237" : "184,174,255" }); } } function spawnBurst(x, y, color, count, speedMin, speedMax) { for (let i = 0; i < count; i++) { game.particles.push( new Particle(x, y, color, speedMin, speedMax) ); } if (game.particles.length > 600) { game.particles.splice(0, game.particles.length - 600); } } function spawnSparkLine(x, y, color, count) { for (let i = 0; i < count; i++) { const particle = new Particle(x, y, color, 60, 180); particle.vx = random(-170, 170); particle.vy = random(-110, -20); particle.gravity = 240; particle.life = random(0.18, 0.42); particle.maxLife = particle.life; game.particles.push(particle); } } function resize() { const rect = screen.getBoundingClientRect(); dpr = Math.min(2, window.devicePixelRatio || 1); canvas.width = Math.max(1, Math.round(rect.width * dpr)); canvas.height = Math.max(1, Math.round(rect.height * dpr)); renderScaleX = rect.width / WORLD.width; renderScaleY = rect.height / WORLD.height; ctx.imageSmoothingEnabled = true; } function pointerToWorld(event) { const rect = canvas.getBoundingClientRect(); const clientX = event.touches?.[0]?.clientX ?? event.changedTouches?.[0]?.clientX ?? event.clientX; const clientY = event.touches?.[0]?.clientY ?? event.changedTouches?.[0]?.clientY ?? event.clientY; return { x: ((clientX - rect.left) / rect.width) * WORLD.width, y: ((clientY - rect.top) / rect.height) * WORLD.height }; } function movePointer(event) { const point = pointerToWorld(event); input.pointerX = point.x; input.pointerActive = true; if (game.paddle) { game.paddle.targetX = point.x; } } function primaryAction(event) { if (event) event.preventDefault(); unlockAudio(); if (game.state === "title" || game.state === "gameover") { startGame(); return; } if (game.state === "paused") { game.state = game.pausedFrom || "playing"; return; } if (game.state === "playing") { launchBalls(); } } function togglePause() { if ( game.state === "title" || game.state === "gameover" || game.state === "levelClear" ) { return; } if (game.state === "paused") { game.state = game.pausedFrom || "playing"; } else { game.pausedFrom = game.state; game.state = "paused"; } } function loop(timestamp) { const rawDt = (timestamp - lastTime) / 1000; lastTime = timestamp; const dt = Math.min(0.033, Math.max(0, rawDt || 0)); update(dt); render(); animationFrame = requestAnimationFrame(loop); } function unlockAudio() { if (!audioCtx) { const AudioContextClass = window.AudioContext || window.webkitAudioContext; if (!AudioContextClass) return; audioCtx = new AudioContextClass(); masterGain = audioCtx.createGain(); masterGain.gain.value = 0.38; masterGain.connect(audioCtx.destination); } if (audioCtx.state === "suspended") { audioCtx.resume(); } audioUnlocked = true; } function playTone( frequency, duration, type = "sine", volume = 0.08, endFrequency = null, delay = 0 ) { if (!audioUnlocked || !audioCtx || !masterGain) return; const now = audioCtx.currentTime + delay; const osc = audioCtx.createOscillator(); const gain = audioCtx.createGain(); osc.type = type; osc.frequency.setValueAtTime(Math.max(30, frequency), now); if (endFrequency !== null) { osc.frequency.exponentialRampToValueAtTime( Math.max(30, endFrequency), now + duration ); } gain.gain.setValueAtTime(0.0001, now); gain.gain.exponentialRampToValueAtTime( Math.max(0.0002, volume), now + 0.008 ); gain.gain.exponentialRampToValueAtTime( 0.0001, now + duration ); osc.connect(gain); gain.connect(masterGain); osc.start(now); osc.stop(now + duration + 0.03); } function playNoise(duration = 0.1, volume = 0.04, cutoff = 1400) { if (!audioUnlocked || !audioCtx || !masterGain) return; const frameCount = Math.max( 1, Math.floor(audioCtx.sampleRate * duration) ); const buffer = audioCtx.createBuffer( 1, frameCount, audioCtx.sampleRate ); const data = buffer.getChannelData(0); for (let i = 0; i < frameCount; i++) { data[i] = Math.random() * 2 - 1; } const source = audioCtx.createBufferSource(); const filter = audioCtx.createBiquadFilter(); const gain = audioCtx.createGain(); const now = audioCtx.currentTime; filter.type = "lowpass"; filter.frequency.value = cutoff; gain.gain.setValueAtTime(volume, now); gain.gain.exponentialRampToValueAtTime( 0.0001, now + duration ); source.buffer = buffer; source.connect(filter); filter.connect(gain); gain.connect(masterGain); source.start(now); } function playWallSound() { playTone(210, 0.035, "square", 0.025, 180); } function playPaddleSound(hitPosition) { const frequency = 280 + (hitPosition + 1) * 75; playTone(frequency, 0.075, "triangle", 0.07, frequency * 1.45); } function playBrickHitSound(row, destroyed) { const base = 420 + (4 - row) * 58; if (destroyed) { playTone(base, 0.07, "square", 0.052, base * 1.35); playTone(base * 1.5, 0.065, "triangle", 0.036, base * 2, 0.012); } else { playTone(base * 0.75, 0.045, "square", 0.032, base * 0.62); } } function playPowerUpSound() { [520, 660, 820, 1040].forEach((frequency, index) => { playTone( frequency, 0.12, "triangle", 0.052, frequency * 1.08, index * 0.055 ); }); } function playLaserSound() { playTone(920, 0.055, "sawtooth", 0.025, 380); } function playComboSound(combo) { const base = 600 + Math.min(600, combo * 20); playTone(base, 0.09, "square", 0.045, base * 1.25); playTone(base * 1.5, 0.12, "triangle", 0.035, base * 2, 0.055); } function playLoseSound() { playNoise(0.16, 0.07, 600); playTone(210, 0.28, "sawtooth", 0.08, 70); } function playStartSound() { [220, 330, 440, 660].forEach((frequency, index) => { playTone( frequency, 0.12, "square", 0.038, frequency * 1.08, index * 0.07 ); }); } function playLevelClearSound() { const notes = [440, 554, 659, 880, 1108]; notes.forEach((frequency, index) => { playTone( frequency, 0.22, index < 3 ? "triangle" : "square", 0.05, frequency * 1.03, index * 0.085 ); }); } function playGameOverSound() { [360, 310, 250, 180, 100].forEach((frequency, index) => { playTone( frequency, 0.24, "sawtooth", 0.052, frequency * 0.75, index * 0.13 ); }); } function drawLaserCannon(x, y) { ctx.save(); ctx.shadowBlur = 10; ctx.shadowColor = "#ff4b90"; ctx.fillStyle = "#ff599a"; roundedRect(x - 4, y - 7, 8, 13, 3); ctx.fill(); ctx.fillStyle = "#fff"; ctx.fillRect(x - 1.5, y - 10, 3, 6); ctx.restore(); } function roundedRect(x, y, width, height, radius) { const r = Math.max( 0, Math.min(radius, Math.abs(width) / 2, Math.abs(height) / 2) ); ctx.beginPath(); ctx.moveTo(x + r, y); ctx.arcTo(x + width, y, x + width, y + height, r); ctx.arcTo( x + width, y + height, x,