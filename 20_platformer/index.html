<!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8"> <meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover"> <meta name="theme-color" content="#060914"> <title>Echoes of the Abyss</title> <style> :root{ --bg:#060914; --cyan:#4dfcff; --violet:#a875ff; --pink:#ff69c9; --gold:#ffd36b; --danger:#ff5277; --glass:rgba(8,12,28,.72); }

*{
box-sizing:border-box;
-webkit-tap-highlight-color:transparent;
}

html,body{
width:100%;
height:100%;
margin:0;
overflow:hidden;
background:
radial-gradient(circle at 50% 15%,#151b3b 0,#080b18 42%,#03050c 100%);
color:#fff;
font-family:Inter,ui-sans-serif,system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
touch-action:none;
user-select:none;
}

#gameShell{
position:relative;
width:100%;
height:100%;
overflow:hidden;
}

canvas{
position:absolute;
inset:0;
display:block;
width:100%;
height:100%;
}

#hud{
position:absolute;
inset:0;
pointer-events:none;
padding:max(14px,env(safe-area-inset-top)) max(14px,env(safe-area-inset-right))
max(14px,env(safe-area-inset-bottom)) max(14px,env(safe-area-inset-left));
display:flex;
flex-direction:column;
justify-content:space-between;
}

.hudTop{
display:flex;
justify-content:space-between;
align-items:flex-start;
gap:12px;
}

.panel{
border:1px solid rgba(125,226,255,.18);
background:linear-gradient(135deg,rgba(13,18,43,.85),rgba(5,8,20,.64));
box-shadow:
0 14px 40px rgba(0,0,0,.28),
inset 0 1px rgba(255,255,255,.05),
0 0 24px rgba(77,252,255,.05);
backdrop-filter:blur(10px);
border-radius:16px;
}

#stats{
min-width:255px;
padding:12px 15px;
}

#hearts{
display:flex;
gap:7px;
margin-bottom:8px;
}

.heart{
width:24px;
height:22px;
filter:drop-shadow(0 0 8px rgba(255,82,119,.75));
opacity:.18;
transition:.2s;
}

.heart.active{
opacity:1;
}

.heart svg{
display:block;
width:100%;
height:100%;
}

.statsRow{
display:grid;
grid-template-columns:repeat(3,auto);
gap:13px;
align-items:center;
font-size:12px;
text-transform:uppercase;
letter-spacing:.12em;
color:#aeb9d9;
}

.statsRow strong{
display:block;
margin-top:2px;
color:#fff;
font-size:16px;
letter-spacing:.02em;
font-variant-numeric:tabular-nums;
}

#rightPanel{
padding:11px 14px;
text-align:right;
}

#areaName{
color:#b8f7ff;
font-size:13px;
font-weight:800;
letter-spacing:.18em;
text-transform:uppercase;
}

#progress{
width:min(250px,32vw);
height:6px;
border-radius:999px;
margin-top:8px;
background:rgba(255,255,255,.08);
overflow:hidden;
}

#progressFill{
width:0%;
height:100%;
border-radius:inherit;
background:linear-gradient(90deg,var(--violet),var(--cyan));
box-shadow:0 0 12px var(--cyan);
}

#message{
position:absolute;
left:50%;
top:20%;
transform:translate(-50%,-15px);
min-width:min(460px,80vw);
padding:12px 20px;
border-radius:999px;
text-align:center;
font-weight:800;
letter-spacing:.1em;
text-transform:uppercase;
color:#eaffff;
background:rgba(5,9,24,.8);
border:1px solid rgba(77,252,255,.24);
box-shadow:0 0 35px rgba(77,252,255,.12);
opacity:0;
transition:opacity .25s,transform .25s;
}

#message.show{
opacity:1;
transform:translate(-50%,0);
}

#bossHint{
align-self:center;
margin-bottom:10px;
padding:8px 14px;
color:#dce4ff;
font-size:12px;
letter-spacing:.1em;
opacity:.72;
}

#overlay{
position:absolute;
inset:0;
display:flex;
align-items:center;
justify-content:center;
padding:24px;
background:
radial-gradient(circle at 50% 35%,rgba(62,71,149,.16),transparent 45%),
rgba(2,4,12,.5);
backdrop-filter:blur(5px);
transition:opacity .3s;
}

#overlay.hidden{
opacity:0;
pointer-events:none;
}

.menu{
width:min(670px,100%);
padding:34px;
text-align:center;
border:1px solid rgba(145,214,255,.2);
border-radius:26px;
background:
linear-gradient(150deg,rgba(17,23,55,.93),rgba(5,8,22,.9));
box-shadow:
0 30px 90px rgba(0,0,0,.52),
inset 0 1px rgba(255,255,255,.06),
0 0 60px rgba(87,91,255,.09);
}

.eyebrow{
color:#7ffaff;
font-size:12px;
font-weight:900;
letter-spacing:.28em;
text-transform:uppercase;
}

h1{
margin:8px 0 5px;
font-size:clamp(39px,7vw,78px);
line-height:.9;
letter-spacing:-.06em;
background:linear-gradient(180deg,#fff 12%,#bcd4ff 52%,#9f76ff 100%);
-webkit-background-clip:text;
color:transparent;
filter:drop-shadow(0 0 20px rgba(144,121,255,.25));
}

#subtitle{
color:#9faaca;
font-size:clamp(13px,2vw,17px);
margin:14px auto 24px;
max-width:520px;
line-height:1.55;
}

.controlsGrid{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:10px;
margin:20px 0 24px;
}

.controlCard{
padding:13px 8px;
border-radius:14px;
background:rgba(255,255,255,.035);
border:1px solid rgba(255,255,255,.07);
color:#aab4d2;
font-size:12px;
}

.controlCard b{
display:block;
margin-bottom:4px;
color:#fff;
font-size:14px;
}

button{
appearance:none;
border:0;
color:#07101b;
font:inherit;
font-weight:900;
letter-spacing:.1em;
text-transform:uppercase;
padding:14px 28px;
border-radius:999px;
cursor:pointer;
background:linear-gradient(90deg,#80fbff,#aa83ff);
box-shadow:
0 10px 30px rgba(84,217,255,.22),
0 0 20px rgba(128,251,255,.15);
transition:transform .15s,filter .15s;
}

button:hover{
transform:translateY(-2px);
filter:brightness(1.08);
}

button:active{
transform:translateY(1px) scale(.98);
}

#secondaryButton{
display:none;
margin-left:8px;
color:#dce9ff;
background:rgba(255,255,255,.08);
box-shadow:none;
border:1px solid rgba(255,255,255,.12);
}

#touchControls{
position:absolute;
left:0;
right:0;
bottom:max(16px,env(safe-area-inset-bottom));
display:none;
justify-content:space-between;
align-items:flex-end;
padding:0 max(16px,env(safe-area-inset-right)) 0 max(16px,env(safe-area-inset-left));
pointer-events:none;
}

.touchGroup{
display:flex;
gap:12px;
pointer-events:auto;
}

.touchBtn{
width:66px;
height:66px;
padding:0;
display:grid;
place-items:center;
border-radius:50%;
color:#dfffff;
font-size:25px;
background:rgba(10,15,38,.62);
border:1px solid rgba(130,230,255,.25);
box-shadow:
inset 0 1px rgba(255,255,255,.08),
0 7px 24px rgba(0,0,0,.25);
backdrop-filter:blur(9px);
}

.touchBtn.jump{
width:78px;
height:78px;
font-size:13px;
letter-spacing:.08em;
background:rgba(71,54,132,.62);
}

.touchBtn:active,
.touchBtn.active{
transform:scale(.92);
background:rgba(77,252,255,.23);
}

@media (pointer:coarse),(max-width:800px){
#touchControls{display:flex}
#bossHint{display:none}
#stats{min-width:0}
.statsRow{gap:9px}
#rightPanel{display:none}
.controlsGrid{grid-template-columns:1fr}
.controlCard{padding:9px}
.menu{padding:26px 20px}
}

@media (max-width:520px){
#hud{padding:10px}
#stats{padding:10px 12px}
.statsRow{font-size:9px}
.statsRow strong{font-size:13px}
.heart{width:20px;height:18px}
#message{font-size:11px}
}
</style>

</head> <body> <div id="gameShell"> <canvas id="game"></canvas> <div id="hud"> <div class="hudTop"> <div id="stats" class="panel"> <div id="hearts"></div> <div class="statsRow"> <span>Score<strong id="scoreValue">000000</strong></span> <span>Relics<strong id="coinValue">0 / 0</strong></span> <span>Time<strong id="timeValue">00:00.0</strong></span> </div> </div> <div id="rightPanel" class="panel"> <div id="areaName">The Hollow Reach</div> <div id="progress"><div id="progressFill"></div></div> </div> </div> <div id="bossHint" class="panel">Move: Arrow Keys / A D &nbsp; • &nbsp; Jump: Space / W / ↑ &nbsp; • &nbsp; Pause: P</div> </div> <div id="message"></div> <div id="touchControls"> <div class="touchGroup"> <button class="touchBtn" id="touchLeft" aria-label="Move left">◀</button> <button class="touchBtn" id="touchRight" aria-label="Move right">▶</button> </div> <div class="touchGroup"> <button class="touchBtn jump" id="touchJump" aria-label="Jump">Jump</button> </div> </div> <div id="overlay"> <div class="menu"> <div class="eyebrow">An original atmospheric platformer</div> <h1 id="menuTitle">Echoes of<br>the Abyss</h1> <div id="subtitle"> Cross the forgotten caverns, master aerial movement, awaken ancient checkpoints, and reach the radiant gate beyond the Hollow Reach. </div> <div class="controlsGrid"> <div class="controlCard"><b>Run</b>Arrow Keys or A / D</div> <div class="controlCard"><b>Leap</b>Space, W, or Up</div> <div class="controlCard"><b>Advanced</b>Double jump and wall jump</div> </div> <button id="startButton">Begin Descent</button> <button id="secondaryButton">Restart</button> </div> </div> </div> <script> (() => { "use strict"; const canvas = document.getElementById("game"); const ctx = canvas.getContext("2d", { alpha: false }); const overlay = document.getElementById("overlay"); const startButton = document.getElementById("startButton"); const secondaryButton = document.getElementById("secondaryButton"); const menuTitle = document.getElementById("menuTitle"); const subtitle = document.getElementById("subtitle"); const scoreValue = document.getElementById("scoreValue"); const coinValue = document.getElementById("coinValue"); const timeValue = document.getElementById("timeValue"); const heartsEl = document.getElementById("hearts"); const messageEl = document.getElementById("message"); const progressFill = document.getElementById("progressFill"); const TAU = Math.PI * 2; const FIXED_STEP = 1 / 120; const WORLD_WIDTH = 8100; const WORLD_HEIGHT = 1100; const GROUND_Y = 820; let viewW = innerWidth; let viewH = innerHeight; let dpr = Math.min(devicePixelRatio || 1, 2); let accumulator = 0; let previousTime = performance.now(); let gameState = "menu"; let elapsed = 0; let displayElapsed = 0; let screenShake = 0; let flashAmount = 0; let totalCollectibles = 0; let messageTimer = 0; let ambientTime = 0; let pausedByVisibility = false; const keys = Object.create(null); const pressed = Object.create(null); function resize() { viewW = innerWidth; viewH = innerHeight; dpr = Math.min(devicePixelRatio || 1, 2); canvas.width = Math.floor(viewW * dpr); canvas.height = Math.floor(viewH * dpr); canvas.style.width = viewW + "px"; canvas.style.height = viewH + "px"; ctx.setTransform(dpr, 0, 0, dpr, 0, 0); camera.zoom = Math.max(.77, Math.min(1.08, viewH / 900)); } addEventListener("resize", resize, { passive: true }); const audio = { ctx: null, master: null, musicGain: null, sfxGain: null, nextNote: 0, noteIndex: 0, enabled: false, init() { if (this.ctx) { this.ctx.resume(); return; } const AudioCtx = window.AudioContext || window.webkitAudioContext; if (!AudioCtx) return; this.ctx = new AudioCtx(); this.master = this.ctx.createGain(); this.musicGain = this.ctx.createGain(); this.sfxGain = this.ctx.createGain(); this.master.gain.value = .55; this.musicGain.gain.value = .11; this.sfxGain.gain.value = .35; this.musicGain.connect(this.master); this.sfxGain.connect(this.master); this.master.connect(this.ctx.destination); this.nextNote = this.ctx.currentTime; this.enabled = true; }, tone(freq, duration, type = "sine", volume = .2, slide = 1, delay = 0) { if (!this.enabled || !this.ctx) return; const now = this.ctx.currentTime + delay; const osc = this.ctx.createOscillator(); const gain = this.ctx.createGain(); osc.type = type; osc.frequency.setValueAtTime(freq, now); osc.frequency.exponentialRampToValueAtTime(Math.max(30, freq * slide), now + duration); gain.gain.setValueAtTime(.0001, now); gain.gain.exponentialRampToValueAtTime(Math.max(.0001, volume), now + .008); gain.gain.exponentialRampToValueAtTime(.0001, now + duration); osc.connect(gain); gain.connect(this.sfxGain); osc.start(now); osc.stop(now + duration + .03); }, noise(duration = .12, volume = .12, cutoff = 1100) { if (!this.enabled || !this.ctx) return; const frames = Math.floor(this.ctx.sampleRate * duration); const buffer = this.ctx.createBuffer(1, frames, this.ctx.sampleRate); const data = buffer.getChannelData(0); for (let i = 0; i < frames; i++) { data[i] = (Math.random() * 2 - 1) * (1 - i / frames); } const source = this.ctx.createBufferSource(); const filter = this.ctx.createBiquadFilter(); const gain = this.ctx.createGain(); filter.type = "lowpass"; filter.frequency.value = cutoff; gain.gain.value = volume; source.buffer = buffer; source.connect(filter); filter.connect(gain); gain.connect(this.sfxGain); source.start(); }, jump(doubleJump = false) { this.tone(doubleJump ? 520 : 350, .13, "triangle", .22, 1.7); if (doubleJump) this.tone(780, .16, "sine", .1, 1.2, .025); }, wallJump() { this.tone(290, .16, "square", .15, 1.8); this.noise(.08, .07, 1800); }, coin(gem = false) { const base = gem ? 690 : 880; this.tone(base, .1, "sine", .18, 1.38); this.tone(base * 1.5, .15, "triangle", .11, 1.18, .06); }, stomp() { this.tone(145, .16, "square", .21, .6); this.noise(.11, .11, 900); }, hurt() { this.tone(230, .28, "sawtooth", .24, .35); this.noise(.2, .15, 700); }, bounce() { this.tone(180, .18, "sine", .24, 3.1); }, checkpoint() { [0, .1, .2, .32].forEach((d, i) => this.tone([440, 554, 659, 880][i], .34, "sine", .12, 1.02, d)); }, crumble() { this.noise(.28, .18, 500); this.tone(120, .25, "square", .08, .5); }, win() { [0, .13, .26, .42, .62].forEach((d, i) => this.tone([392, 494, 587, 784, 988][i], .5, "triangle", .16, 1.03, d)); }, scheduleMusic() { if (!this.enabled || !this.ctx || gameState !== "playing") return; const scale = [110, 146.83, 164.81, 196, 220, 246.94, 293.66, 329.63]; const pattern = [0, 2, 5, 3, 1, 4, 6, 3, 0, 5, 2, 7, 4, 1, 3, 6]; while (this.nextNote < this.ctx.currentTime + .15) { const beat = .36; const index = pattern[this.noteIndex % pattern.length]; const freq = scale[index]; const osc = this.ctx.createOscillator(); const gain = this.ctx.createGain(); const filter = this.ctx.createBiquadFilter(); osc.type = this.noteIndex % 4 === 0 ? "triangle" : "sine"; osc.frequency.value = freq; filter.type = "lowpass"; filter.frequency.value = 800; gain.gain.setValueAtTime(.0001, this.nextNote); gain.gain.exponentialRampToValueAtTime(.12, this.nextNote + .025); gain.gain.exponentialRampToValueAtTime(.0001, this.nextNote + beat * .82); osc.connect(filter); filter.connect(gain); gain.connect(this.musicGain); osc.start(this.nextNote); osc.stop(this.nextNote + beat); if (this.noteIndex % 4 === 0) { const bass = this.ctx.createOscillator(); const bassGain = this.ctx.createGain(); bass.type = "sine"; bass.frequency.value = freq / 2; bassGain.gain.setValueAtTime(.0001, this.nextNote); bassGain.gain.exponentialRampToValueAtTime(.11, this.nextNote + .03); bassGain.gain.exponentialRampToValueAtTime(.0001, this.nextNote + beat * 3.5); bass.connect(bassGain); bassGain.connect(this.musicGain); bass.start(this.nextNote); bass.stop(this.nextNote + beat * 3.8); } this.nextNote += beat; this.noteIndex++; } } }; const camera = { x: 0, y: 260, zoom: 1, lookX: 0, reset() { this.x = 0; this.y = 260; this.lookX = 0; }, update(dt) { const speedLook = clamp(player.vx * .28, -90, 130); this.lookX = lerp(this.lookX, speedLook, 1 - Math.pow(.001, dt)); const targetX = clamp(player.x + player.w * .5 - viewW / (2 * this.zoom) + this.lookX, 0, Math.max(0, WORLD_WIDTH - viewW / this.zoom)); const targetY = clamp(player.y + player.h * .5 - viewH / (2 * this.zoom) + 50, 0, Math.max(0, WORLD_HEIGHT - viewH / this.zoom)); this.x = lerp(this.x, targetX, 1 - Math.pow(.00008, dt)); this.y = lerp(this.y, targetY, 1 - Math.pow(.00008, dt)); } }; class Particle { constructor(x, y, options = {}) { this.x = x; this.y = y; this.vx = options.vx ?? rand(-90, 90); this.vy = options.vy ?? rand(-140, -30); this.life = options.life ?? rand(.3, .65); this.maxLife = this.life; this.size = options.size ?? rand(2, 6); this.color = options.color ?? "#8dfaff"; this.gravity = options.gravity ?? 500; this.drag = options.drag ?? .98; this.glow = options.glow ?? 8; this.shape = options.shape ?? "circle"; this.rotation = rand(0, TAU); this.spin = rand(-8, 8); } update(dt) { this.life -= dt; this.vx *= Math.pow(this.drag, dt * 60); this.vy += this.gravity * dt; this.x += this.vx * dt; this.y += this.vy * dt; this.rotation += this.spin * dt; } draw() { if (this.life <= 0) return; const alpha = clamp(this.life / this.maxLife, 0, 1); ctx.save(); ctx.globalAlpha = alpha; ctx.translate(this.x, this.y); ctx.rotate(this.rotation); ctx.shadowColor = this.color; ctx.shadowBlur = this.glow; ctx.fillStyle = this.color; if (this.shape === "diamond") { ctx.rotate(Math.PI / 4); ctx.fillRect(-this.size / 2, -this.size / 2, this.size, this.size); } else if (this.shape === "spark") { ctx.fillRect(-this.size * 1.8, -this.size / 3, this.size * 3.6, this.size * .66); ctx.fillRect(-this.size / 3, -this.size * 1.8, this.size * .66, this.size * 3.6); } else { ctx.beginPath(); ctx.arc(0, 0, this.size, 0, TAU); ctx.fill(); } ctx.restore(); } } class FloatingText { constructor(x, y, text, color = "#fff") { this.x = x; this.y = y; this.text = text; this.color = color; this.life = .9; this.maxLife = .9; } update(dt) { this.life -= dt; this.y -= 45 * dt; } draw() { const alpha = clamp(this.life / this.maxLife, 0, 1); ctx.save(); ctx.globalAlpha = alpha; ctx.font = "900 18px system-ui"; ctx.textAlign = "center"; ctx.fillStyle = this.color; ctx.shadowColor = this.color; ctx.shadowBlur = 10; ctx.fillText(this.text, this.x, this.y); ctx.restore(); } } class Platform { constructor(x, y, w, h, type = "normal", options = {}) { this.x = x; this.y = y; this.baseX = x; this.baseY = y; this.w = w; this.h = h; this.type = type; this.rangeX = options.rangeX || 0; this.rangeY = options.rangeY || 0; this.speed = options.speed || 1; this.phase = options.phase || 0; this.prevX = x; this.prevY = y; this.dx = 0; this.dy = 0; this.triggered = false; this.crumbleTimer = 0; this.respawnTimer = 0; this.active = true; this.glow = options.glow ?? true; } update(dt) { this.prevX = this.x; this.prevY = this.y; if (this.type === "moving") { const t = elapsed * this.speed + this.phase; this.x = this.baseX + Math.sin(t) * this.rangeX; this.y = this.baseY + Math.cos(t * .82) * this.rangeY; } if (this.type === "crumbling") { if (this.triggered && this.active) { this.crumbleTimer -= dt; if (this.crumbleTimer <= 0) { this.active = false; this.respawnTimer = 4.2; audio.crumble(); screenShake = Math.max(screenShake, 6); burst(this.x + this.w / 2, this.y + this.h / 2, 24, "#ad8cff", { speed: 180, gravity: 650, size: [2, 8] }); } } else if (!this.active) { this.respawnTimer -= dt; if (this.respawnTimer <= 0) { this.active = true; this.triggered = false; } } } this.dx = this.x - this.prevX; this.dy = this.y - this.prevY; } touch() { if (this.type === "crumbling" && !this.triggered) { this.triggered = true; this.crumbleTimer = .62; } } draw() { if (!this.active) { const alpha = clamp(1 - this.respawnTimer / 4.2, 0, .28); ctx.save(); ctx.globalAlpha = alpha; ctx.strokeStyle = "#a886ff"; ctx.lineWidth = 2; roundRect(ctx, this.x, this.y, this.w, this.h, 7); ctx.stroke(); ctx.restore(); return; } const shake = this.type === "crumbling" && this.triggered ? Math.sin(this.crumbleTimer * 90) * 2.5 : 0; ctx.save(); ctx.translate(shake, 0); const palettes = { normal: ["#202847", "#11172e", "#4dfcff"], moving: ["#29345c", "#141c3b", "#7ea3ff"], crumbling: ["#392b54", "#1c1734", "#b982ff"], bouncy: ["#17485a", "#0a2635", "#6dfff3"] }; const p = palettes[this.type]; const grad = ctx.createLinearGradient(0, this.y, 0, this.y + this.h); grad.addColorStop(0, p[0]); grad.addColorStop(1, p[1]); ctx.shadowColor = p[2]; ctx.shadowBlur = this.glow ? 11 : 0; ctx.fillStyle = grad; roundRect(ctx, this.x, this.y, this.w, this.h, 7); ctx.fill(); ctx.shadowBlur = 0; ctx.strokeStyle = hexAlpha(p[2], .55); ctx.lineWidth = 1.4; roundRect(ctx, this.x, this.y, this.w, this.h, 7); ctx.stroke(); ctx.fillStyle = hexAlpha(p[2], .28); roundRect(ctx, this.x + 5, this.y + 4, Math.max(0, this.w - 10), 3, 2); ctx.fill(); if (this.type === "moving") { ctx.fillStyle = hexAlpha(p[2], .42); for (let x = this.x + 14; x < this.x + this.w - 8; x += 24) { ctx.beginPath(); ctx.moveTo(x, this.y + this.h / 2); ctx.lineTo(x + 7, this.y + this.h / 2 - 4); ctx.lineTo(x + 7, this.y + this.h / 2 + 4); ctx.closePath(); ctx.fill(); } } if (this.type === "crumbling") { ctx.strokeStyle = hexAlpha(p[2], .5); ctx.lineWidth = 1.2; const cracks = [ [this.x + this.w * .2, this.y + 3, this.x + this.w * .3, this.y + this.h - 3], [this.x + this.w * .53, this.y + 3, this.x + this.w * .47, this.y + this.h - 3], [this.x + this.w * .76, this.y + 3, this.x + this.w * .68, this.y + this.h - 3] ]; cracks.forEach(c => { ctx.beginPath(); ctx.moveTo(c[0], c[1]); ctx.lineTo((c[0] + c[2]) / 2 + 4, (c[1] + c[3]) / 2); ctx.lineTo(c[2], c[3]); ctx.stroke(); }); } if (this.type === "bouncy") { ctx.strokeStyle = "#8dfff8"; ctx.lineWidth = 2; for (let x = this.x + 10; x < this.x + this.w - 8; x += 18) { ctx.beginPath(); ctx.moveTo(x, this.y + this.h - 5); ctx.lineTo(x + 4, this.y + 6); ctx.lineTo(x + 8, this.y + this.h - 5); ctx.stroke(); } } ctx.restore(); } } class Collectible { constructor(x, y, type = "coin") { this.x = x; this.y = y; this.type = type; this.collected = false; this.t = rand(0, TAU); this.radius = type === "gem" ? 14 : 11; } update(dt) { this.t += dt * (this.type === "gem" ? 2.1 : 3); if (this.collected) return; const bobY = Math.sin(this.t) * 5; const box = { x: this.x - this.radius, y: this.y + bobY - this.radius, w: this.radius * 2, h: this.radius * 2 }; if (overlap(player, box)) { this.collected = true; const value = this.type === "gem" ? 250 : 100; player.coins++; player.score += value; audio.coin(this.type === "gem"); floatingTexts.push(new FloatingText(this.x, this.y - 10, "+" + value, this.type === "gem" ? "#ef8cff" : "#ffd66b")); burst(this.x, this.y + bobY, this.type === "gem" ? 18 : 12, this.type === "gem" ? "#d575ff" : "#ffe577", { speed: this.type === "gem" ? 180 : 130, gravity: 120, shape: "spark" }); } } draw() { if (this.collected) return; const bob = Math.sin(this.t) * 5; const squeeze = .65 + Math.abs(Math.cos(this.t * 1.7)) * .35; ctx.save(); ctx.translate(this.x, this.y + bob); ctx.scale(squeeze, 1); if (this.type === "gem") { ctx.rotate(Math.sin(this.t * .8) * .18); ctx.shadowColor = "#d679ff"; ctx.shadowBlur = 22; const g = ctx.createLinearGradient(0, -15, 0, 15); g.addColorStop(0, "#fff"); g.addColorStop(.2, "#f0afff"); g.addColorStop(.65, "#ad52ff"); g.addColorStop(1, "#582ea8"); ctx.fillStyle = g; ctx.beginPath(); ctx.moveTo(0, -16); ctx.lineTo(12, -5); ctx.lineTo(8, 12); ctx.lineTo(0, 18); ctx.lineTo(-8, 12); ctx.lineTo(-12, -5); ctx.closePath(); ctx.fill(); ctx.strokeStyle = "rgba(255,255,255,.6)"; ctx.lineWidth = 1.2; ctx.beginPath(); ctx.moveTo(0, -14); ctx.lineTo(0, 15); ctx.moveTo(-10, -4); ctx.lineTo(10, -4); ctx.stroke(); } else { ctx.shadowColor = "#ffd45d"; ctx.shadowBlur = 18; const g = ctx.createRadialGradient(-4, -5, 1, 0, 0, 14); g.addColorStop(0, "#fff9c2"); g.addColorStop(.35, "#ffe06d"); g.addColorStop(1, "#d58b21"); ctx.fillStyle = g; ctx.beginPath(); ctx.arc(0, 0, 11, 0, TAU); ctx.fill(); ctx.strokeStyle = "#fff4a9"; ctx.lineWidth = 2; ctx.beginPath(); ctx.arc(0, 0, 7, 0, TAU); ctx.stroke(); } ctx.restore(); if (Math.random() < .025) { particles.push(new Particle(this.x + rand(-12, 12), this.y + bob + rand(-12, 12), { vx: rand(-8, 8), vy: rand(-22, -5), life: rand(.25, .55), size: rand(1, 2.6), gravity: 0, color: this.type === "gem" ? "#df8cff" : "#ffe985", shape: "spark" })); } } } class Enemy { constructor(x, y, options = {}) { this.x = x; this.y = y; this.w = 42; this.h = 36; this.vx = options.direction === -1 ? -55 : 55; this.vy = 0; this.speed = options.speed || 55; this.minX = options.minX ?? x - 100; this.maxX = options.maxX ?? x + 100; this.alive = true; this.deadTimer = 0; this.t = rand(0, TAU); this.grounded = false; } update(dt) { this.t += dt; if (!this.alive) { this.deadTimer -= dt; this.y += 220 * dt; return; } if (this.x <= this.minX) this.vx = Math.abs(this.speed); if (this.x + this.w >= this.maxX) this.vx = -Math.abs(this.speed); this.vy += 1650 * dt; const oldX = this.x; const oldY = this.y; this.x += this.vx * dt; for (const p of platforms) { if (!p.active || !overlap(this, p)) continue; if (this.vx > 0) this.x = p.x - this.w; else this.x = p.x + p.w; this.vx *= -1; } this.y += this.vy * dt; this.grounded = false; for (const p of platforms) { if (!p.active || !overlap(this, p)) continue; if (this.vy > 0 && oldY + this.h <= p.y + 8) { this.y = p.y - this.h; this.vy = 0; this.grounded = true; this.x += p.dx; this.y += p.dy; } else if (this.vy < 0 && oldY >= p.y + p.h - 8) { this.y = p.y + p.h; this.vy = 0; } } if (this.grounded) { const probeX = this.vx > 0 ? this.x + this.w + 4 : this.x - 4; const probeY = this.y + this.h + 5; if (!pointOnSolid(probeX, probeY)) this.vx *= -1; } if (this.y > WORLD_HEIGHT + 100) this.alive = false; if (player.invulnerability <= 0 && overlap(player, this)) { const playerBottomBefore = player.prevY + player.h; const stomp = player.vy > 80 && playerBottomBefore <= this.y + 12; if (stomp) { this.alive = false; this.deadTimer = .8; player.vy = -570; player.score += 350; player.combo++; audio.stomp(); screenShake = Math.max(screenShake, 5); floatingTexts.push(new FloatingText(this.x + this.w / 2, this.y, "+" + (350 * player.combo), "#8ffcff")); player.score += 350 * (player.combo - 1); burst(this.x + this.w / 2, this.y + this.h / 2, 18, "#7cfbff", { speed: 170, gravity: 420, size: [2, 7] }); } else { damagePlayer(this.x + this.w / 2); } } } draw() { if (!this.alive && this.deadTimer <= 0) return; const squash = !this.alive ? clamp(this.deadTimer / .2, .12, 1) : 1 + Math.sin(this.t * 7) * .04; ctx.save(); ctx.translate(this.x + this.w / 2, this.y + this.h); ctx.scale(1, squash); ctx.shadowColor = "#ed6cff"; ctx.shadowBlur = 15; const g = ctx.createLinearGradient(0, -this.h, 0, 0); g.addColorStop(0, "#9a5cff"); g.addColorStop(.55, "#472781"); g.addColorStop(1, "#1a1634"); ctx.fillStyle = g; ctx.beginPath(); ctx.moveTo(-20, 0); ctx.quadraticCurveTo(-24, -22, -10, -33); ctx.quadraticCurveTo(0, -43, 10, -33); ctx.quadraticCurveTo(24, -22, 20, 0); ctx.closePath(); ctx.fill(); ctx.shadowBlur = 8; ctx.fillStyle = "#ddffff"; const look = Math.sign(player.x - this.x) * 2; ctx.beginPath(); ctx.ellipse(-7 + look, -19, 3.2, 4.2, 0, 0, TAU); ctx.ellipse(7 + look, -19, 3.2, 4.2, 0, 0, TAU); ctx.fill(); ctx.fillStyle = "#07101c"; ctx.beginPath(); ctx.arc(-7 + look, -18, 1.4, 0, TAU); ctx.arc(7 + look, -18, 1.4, 0, TAU); ctx.fill(); ctx.restore(); } } class Checkpoint { constructor(x, y) { this.x = x; this.y = y; this.w = 34; this.h = 92; this.active = false; this.t = 0; } update(dt) { this.t += dt; const box = { x: this.x - 18, y: this.y - this.h, w: 60, h: this.h + 20 }; if (!this.active && overlap(player, box)) { checkpoints.forEach(c => c.active = false); this.active = true; player.respawnX = this.x - 12; player.respawnY = this.y - 130; player.score += 500; player.health = 3; audio.checkpoint(); showMessage("Checkpoint awakened", 2); burst(this.x + 10, this.y - 62, 34, "#72fbff", { speed: 210, gravity: -20, shape: "spark" }); updateHearts(); } } draw() { ctx.save(); ctx.strokeStyle = this.active ? "#83ffff" : "#53628d"; ctx.lineWidth = 5; ctx.shadowColor = this.active ? "#5effff" : "#5969ab"; ctx.shadowBlur = this.active ? 25 : 8; ctx.beginPath(); ctx.moveTo(this.x, this.y); ctx.lineTo(this.x, this.y - this.h); ctx.stroke(); ctx.fillStyle = this.active ? "#adffff" : "#56628c"; ctx.beginPath(); ctx.moveTo(this.x, this.y - this.h); ctx.quadraticCurveTo(this.x + 33, this.y - this.h + 11, this.x + 12, this.y - this.h + 34); ctx.lineTo(this.x, this.y - this.h + 28); ctx.closePath(); ctx.fill(); const glowAlpha = this.active ? .18 + Math.sin(this.t * 4) * .06 : .05; ctx.fillStyle = `rgba(100,255,255,${glowAlpha})`; ctx.beginPath(); ctx.arc(this.x, this.y - this.h + 10, this.active ? 42 : 20, 0, TAU); ctx.fill(); ctx.restore(); } } const player = { x: 100, y: 650, prevX: 100, prevY: 650, w: 34, h: 52, vx: 0, vy: 0, facing: 1, grounded: false, wasGrounded: false, wallDir: 0, wallSliding: false, coyote: 0, jumpBuffer: 0, jumpsUsed: 0, health: 3, score: 0, coins: 0, combo: 0, invulnerability: 0, respawnX: 100, respawnY: 650, dead: false, deathTimer: 0, animationTime: 0, trailTimer: 0, onPlatform: null, reset(full = true) { this.x = 100; this.y = 650; this.prevX = this.x; this.prevY = this.y; this.vx = 0; this.vy = 0; this.facing = 1; this.grounded = false; this.wasGrounded = false; this.wallDir = 0; this.wallSliding = false; this.coyote = 0; this.jumpBuffer = 0; this.jumpsUsed = 0; this.health = 3; this.invulnerability = 0; this.respawnX = 100; this.respawnY = 650; this.dead = false; this.deathTimer = 0; this.combo = 0; if (full) { this.score = 0; this.coins = 0; } }, respawn() { this.x = this.respawnX; this.y = this.respawnY; this.prevX = this.x; this.prevY = this.y; this.vx = 0; this.vy = 0; this.dead = false; this.deathTimer = 0; this.invulnerability = 1.5; this.health = Math.max(1, this.health); camera.x = clamp(this.x - viewW / (2 * camera.zoom), 0, WORLD_WIDTH); camera.y = clamp(this.y - viewH / (2 * camera.zoom), 0, WORLD_HEIGHT); flashAmount = .55; updateHearts(); }, update(dt) { this.animationTime += dt; this.prevX = this.x; this.prevY = this.y; this.wasGrounded = this.grounded; if (this.invulnerability > 0) this.invulnerability -= dt; if (this.dead) { this.deathTimer -= dt; this.vy += 850 * dt; this.y += this.vy * dt; if (this.deathTimer <= 0) this.respawn(); return; } const move = (keys.ArrowRight || keys.KeyD ? 1 : 0) - (keys.ArrowLeft || keys.KeyA ? 1 : 0); const jumpHeld = keys.Space || keys.ArrowUp || keys.KeyW; const jumpPressed = pressed.Space || pressed.ArrowUp || pressed.KeyW; if (jumpPressed) this.jumpBuffer = .13; else this.jumpBuffer = Math.max(0, this.jumpBuffer - dt); if (this.grounded) { this.coyote = .11; this.jumpsUsed = 0; this.combo = 0; } else { this.coyote = Math.max(0, this.coyote - dt); } const acceleration = this.grounded ? 2500 : 1550; const maxSpeed = 330; const friction = this.grounded ? 2200 : 500; if (move !== 0) { this.vx = approach(this.vx, move * maxSpeed, acceleration * dt); this.facing = move; } else { this.vx = approach(this.vx, 0, friction * dt); } this.wallDir = 0; const wallProbeTop = this.y + 8; const wallProbeBottom = this.y + this.h - 5; if (isSolidAt(this.x - 3, wallProbeTop) || isSolidAt(this.x - 3, wallProbeBottom)) this.wallDir = -1; if (isSolidAt(this.x + this.w + 3, wallProbeTop) || isSolidAt(this.x + this.w + 3, wallProbeBottom)) this.wallDir = 1; this.wallSliding = !this.grounded && this.wallDir !== 0 && this.vy > 20 && move === this.wallDir; if (this.wallSliding) { this.vy = Math.min(this.vy, 135); if (Math.random() < .22) { particles.push(new Particle( this.wallDir < 0 ? this.x : this.x + this.w, this.y + rand(12, this.h), { vx: -this.wallDir * rand(20, 60), vy: rand(-20, 55), life: rand(.2, .5), size: rand(1, 3), gravity: 180, color: "#7acfff" } )); } } if (this.jumpBuffer > 0) { if (this.wallDir !== 0 && !this.grounded) { this.vx = -this.wallDir * 430; this.vy = -650; this.facing = -this.wallDir; this.jumpBuffer = 0; this.jumpsUsed = 1; audio.wallJump(); jumpDust(this.wallDir < 0 ? this.x : this.x + this.w, this.y + this.h * .6, -this.wallDir); } else if (this.coyote > 0) { this.vy = -640; this.coyote = 0; this.jumpBuffer = 0; this.jumpsUsed = 1; audio.jump(false); jumpDust(this.x + this.w / 2, this.y + this.h, 0); } else if (this.jumpsUsed < 2) { this.vy = -590; this.jumpBuffer = 0; this.jumpsUsed = 2; audio.jump(true); burst(this.x + this.w / 2, this.y + this.h / 2, 16, "#a785ff", { speed: 130, gravity: 90, shape: "spark" }); } } if (!jumpHeld && this.vy < -180) this.vy += 1850 * dt; this.vy += (this.wallSliding ? 900 : 1780) * dt; this.vy = Math.min(this.vy, 980); this.x += this.vx * dt; this.resolveHorizontal(); this.grounded = false; this.onPlatform = null; this.y += this.vy * dt; this.resolveVertical(); if (!this.wasGrounded && this.grounded && this.vy >= 0) { landingDust(this.x + this.w / 2, this.y + this.h); audio.tone(90, .07, "sine", .06, .7); } if (this.onPlatform) { this.x += this.onPlatform.dx; this.y += this.onPlatform.dy; } this.x = clamp(this.x, 0, WORLD_WIDTH - this.w); this.trailTimer -= dt; if (!this.grounded && Math.abs(this.vx) > 250 && this.trailTimer <= 0) { this.trailTimer = .045; particles.push(new Particle(this.x + this.w / 2 - this.facing * 10, this.y + this.h * .55, { vx: -this.vx * .08 + rand(-12, 12), vy: rand(-10, 10), life: .22, size: rand(2, 4), gravity: 0, drag: .91, color: "#6fdcff" })); } if (this.y > WORLD_HEIGHT + 100) { damagePlayer(this.x, true); } }, resolveHorizontal() { for (const p of platforms) { if (!p.active || !overlap(this, p)) continue; if (this.vx > 0 && this.prevX + this.w <= p.x + 9) { this.x = p.x - this.w; this.vx = 0; } else if (this.vx < 0 && this.prevX >= p.x + p.w - 9) { this.x = p.x + p.w; this.vx = 0; } } }, resolveVertical() { for (const p of platforms) { if (!p.active || !overlap(this, p)) continue; if (this.vy >= 0 && this.prevY + this.h <= p.y + 12) { this.y = p.y - this.h; this.grounded = true; this.onPlatform = p; p.touch(); if (p.type === "bouncy") { this.grounded = false; this.onPlatform = null; this.vy = -860; this.jumpsUsed = 0; audio.bounce(); screenShake = Math.max(screenShake, 5); burst(this.x + this.w / 2, p.y, 20, "#6efff0", { speed: 200, gravity: 250, shape: "spark" }); } else { this.vy = 0; } } else if (this.vy < 0 && this.prevY >= p.y + p.h - 10) { this.y = p.y + p.h; this.vy = 25; } } }, draw() { if (this.invulnerability > 0 && Math.floor(this.invulnerability * 14) % 2 === 0) return; const speedRatio = clamp(Math.abs(this.vx) / 330, 0, 1); const runBob = this.grounded ? Math.sin(this.animationTime * (8 + speedRatio * 10)) * speedRatio * 2 : 0; const squashX = this.grounded ? 1 + Math.abs(Math.sin(this.animationTime * 10)) * speedRatio * .04 : 1; const squashY = this.vy < -100 ? 1.07 : this.vy > 220 ? .95 : 1; const lean = clamp(this.vx / 1400, -.17, .17); ctx.save(); ctx.translate(this.x + this.w / 2, this.y + this.h / 2 + runBob); ctx.rotate(lean); ctx.scale(this.facing * squashX, squashY); ctx.shadowColor = "#54e8ff"; ctx.shadowBlur = 18; ctx.fillStyle = "rgba(86,221,255,.18)"; ctx.beginPath(); ctx.ellipse(-4, 20, 20, 8, 0, 0, TAU); ctx.fill(); const cloak = ctx.createLinearGradient(0, -24, 0, 28); cloak.addColorStop(0, "#235a8a"); cloak.addColorStop(.48, "#173757"); cloak.addColorStop(1, "#0b162b"); ctx.fillStyle = cloak; ctx.beginPath(); ctx.moveTo(-13, -10); ctx.quadraticCurveTo(-20, 7, -18, 25); ctx.quadraticCurveTo(-5, 31, 12, 24); ctx.quadraticCurveTo(17, 8, 11, -12); ctx.closePath(); ctx.fill(); ctx.fillStyle = "#101a31"; ctx.beginPath(); ctx.ellipse(0, -15, 14, 16, 0, 0, TAU); ctx.fill(); ctx.shadowBlur = 8; ctx.fillStyle = "#d9ffff"; ctx.beginPath(); ctx.ellipse(4, -16, 4.8, 3, 0, 0, TAU); ctx.fill(); ctx.fillStyle = "#5ff7ff"; ctx.beginPath(); ctx.ellipse(5.5, -16, 1.6, 1.6, 0, 0, TAU); ctx.fill(); ctx.strokeStyle = "#58d8f2"; ctx.lineWidth = 3; ctx.lineCap = "round"; const leg = this.grounded ? Math.sin(this.animationTime * (8 + speedRatio * 10)) * speedRatio * 6 : 0; ctx.beginPath(); ctx.moveTo(-7, 20); ctx.lineTo(-8 + leg, 28); ctx.moveTo(6, 20); ctx.lineTo(7 - leg, 28); ctx.stroke(); ctx.strokeStyle = "rgba(106,243,255,.55)"; ctx.lineWidth = 1.2; ctx.beginPath(); ctx.moveTo(-12, -4); ctx.quadraticCurveTo(-3, 3, 10, -1); ctx.stroke(); ctx.restore(); } }; let platforms = []; let collectibles = []; let enemies = []; let checkpoints = []; let particles = []; let floatingTexts = []; let goal = null; function addPlatform(x, y, w, h = 32, type = "normal", options = {}) { platforms.push(new Platform(x, y, w, h, type, options)); } function coinLine(x, y, count, spacing = 46, type = "coin") { for (let i = 0; i < count; i++) { collectibles.push(new Collectible(x + i * spacing, y, type)); } } function coinArc(x, y, count, spacing = 42, height = 80) { for (let i = 0; i < count; i++) { const t = count === 1 ? .5 : i / (count - 1); collectibles.push(new Collectible(x + i * spacing, y - Math.sin(t * Math.PI) * height)); } } function buildLevel() { platforms = []; collectibles = []; enemies = []; checkpoints = []; particles = []; floatingTexts = []; addPlatform(0, GROUND_Y, 720, 90); addPlatform(780, 790, 250, 40); addPlatform(1090, 735, 210, 36); addPlatform(1360, 665, 180, 34, "moving", { rangeY: 75, speed: 1.1 }); addPlatform(1605, 785, 340, 50); addPlatform(2000, 720, 130, 30, "crumbling"); addPlatform(2180, 655, 130, 30, "crumbling"); addPlatform(2360, 585, 150, 30, "crumbling"); addPlatform(2550, 780, 300, 45); addPlatform(2880, 745, 130, 30, "bouncy"); addPlatform(3080, 560, 210, 34); addPlatform(3340, 650, 180, 34, "moving", { rangeX: 105, speed: .85 }); addPlatform(3600, 760, 520, 56); addPlatform(4170, 700, 120, 32, "crumbling"); addPlatform(4340, 625, 120, 32, "crumbling"); addPlatform(4510, 550, 120, 32, "crumbling"); addPlatform(4680, 475, 150, 32); addPlatform(4910, 640, 150, 34, "moving", { rangeY: 130, speed: .8, phase: 1 }); addPlatform(5160, 770, 340, 50); addPlatform(5535, 720, 170, 34); addPlatform(5790, 660, 160, 34, "moving", { rangeX: 110, speed: 1.05, phase: 2 }); addPlatform(6070, 760, 240, 46); addPlatform(6350, 700, 135, 30, "bouncy"); addPlatform(6560, 505, 220, 36); addPlatform(6860, 625, 150, 34, "crumbling"); addPlatform(7060, 700, 150, 34, "crumbling"); addPlatform(7260, 760, 840, 80); addPlatform(920, 540, 145, 30); addPlatform(1180, 455, 150, 30); addPlatform(1810, 500, 170, 30); addPlatform(2740, 485, 145, 30); addPlatform(3810, 505, 170, 30); addPlatform(5330, 485, 175, 30); addPlatform(6150, 430, 145, 30); coinLine(120, 750, 7, 48); coinArc(790, 720, 6, 48, 78); coinLine(930, 490, 3, 44); coinArc(1100, 650, 6, 47, 120); collectibles.push(new Collectible(1250, 405, "gem")); coinArc(1610, 710, 7, 46, 70); coinLine(2000, 650, 3, 180); collectibles.push(new Collectible(2420, 525, "gem")); coinLine(2580, 720, 5, 48); coinArc(2885, 670, 7, 45, 155); collectibles.push(new Collectible(3180, 500, "gem")); coinLine(3630, 690, 8, 50); coinLine(3830, 455, 4, 45); coinArc(4180, 630, 5, 85, 125); collectibles.push(new Collectible(4745, 420, "gem")); coinArc(4910, 570, 6, 55, 110); coinLine(5200, 705, 5, 50); collectibles.push(new Collectible(5415, 435, "gem")); coinArc(5540, 650, 8, 55, 120); coinLine(6090, 700, 4, 46); collectibles.push(new Collectible(6220, 375, "gem")); coinArc(6370, 620, 8, 51, 160); coinLine(7280, 700, 10, 58); collectibles.push(new Collectible(7750, 660, "gem")); enemies.push(new Enemy(470, 760, { minX: 350, maxX: 680, speed: 62 })); enemies.push(new Enemy(1650, 745, { minX: 1610, maxX: 1920, speed: 70, direction: -1 })); enemies.push(new Enemy(2640, 740, { minX: 2560, maxX: 2820, speed: 75 })); enemies.push(new Enemy(3670, 720, { minX: 3605, maxX: 4100, speed: 80, direction: -1 })); enemies.push(new Enemy(5210, 730, { minX: 5170, maxX: 5480, speed: 80 })); enemies.push(new Enemy(6100, 720, { minX: 6075, maxX: 6300, speed: 88, direction: -1 })); enemies.push(new Enemy(7350, 720, { minX: 7280, maxX: 7740, speed: 92 })); enemies.push(new Enemy(7800, 720, { minX: 7700, maxX: 8050, speed: 98, direction: -1 })); checkpoints.push(new Checkpoint(1710, 785)); checkpoints.push(new Checkpoint(3730, 760)); checkpoints.push(new Checkpoint(5290, 770)); checkpoints.push(new Checkpoint(7310, 760)); goal = { x: 7970, y: 760, w: 55, h: 150, t: 0, reached: false }; totalCollectibles = collectibles.length; } function drawBackground() { const gradient = ctx.createLinearGradient(0, 0, 0, viewH); gradient.addColorStop(0, "#080c1f"); gradient.addColorStop(.48, "#111832"); gradient.addColorStop(1, "#060914"); ctx.fillStyle = gradient; ctx.fillRect(0, 0, viewW, viewH); const glowX = viewW * .68 - camera.x * .012; const glowY = viewH * .22; const moonGlow = ctx.createRadialGradient(glowX, glowY, 4, glowX, glowY, 230); moonGlow.addColorStop(0, "rgba(175,220,255,.22)"); moonGlow.addColorStop(.25, "rgba(103,134,255,.11)"); moonGlow.addColorStop(1, "rgba(30,40,90,0)"); ctx.fillStyle = moonGlow; ctx.fillRect(0, 0, viewW, viewH); drawStars(.04, 55, 1.4, .45); drawCavernLayer(.08, viewH * .45, 170, "#101733", .38, 220); drawCavernLayer(.16, viewH * .57, 210, "#0c132b", .72, 160); drawCavernLayer(.28, viewH * .72, 250, "#080e22", 1, 115); ctx.save(); ctx.globalAlpha = .18; ctx.strokeStyle = "#5571bb"; ctx.lineWidth = 1; for (let x = -((camera.x * .16) % 180); x < viewW + 180; x += 180) { const length = 45 + ((x * 13) % 70 + 70) % 70; ctx.beginPath(); ctx.moveTo(x, 0); ctx.lineTo(x + 9, length); ctx.lineTo(x - 8, length + 20); ctx.stroke(); } ctx.restore(); const fog = ctx.createLinearGradient(0, viewH * .45, 0, viewH); fog.addColorStop(0, "rgba(18,27,58,0)"); fog.addColorStop(1, "rgba(6,9,20,.72)"); ctx.fillStyle = fog; ctx.fillRect(0, viewH * .4, viewW, viewH * .6); } function drawStars(parallax, count, size, alpha) { ctx.save(); ctx.fillStyle = "#c8ecff"; for (let i = 0; i < count; i++) { const seed = i * 9283.17; const worldX = ((seed * 43.7) % (WORLD_WIDTH + viewW)); const x = ((worldX - camera.x * parallax) % (viewW + 120) + viewW + 120) % (viewW + 120) - 60; const y = ((seed * 1.37) % (viewH * .65)); const twinkle = .45 + Math.sin(ambientTime * 1.7 + i) * .3; ctx.globalAlpha = alpha * twinkle; ctx.beginPath(); ctx.arc(x, y, size * (.5 + (i % 4) / 5), 0, TAU); ctx.fill(); } ctx.restore(); } function drawCavernLayer(parallax, baseline, amplitude, color, alpha, frequency) { ctx.save(); ctx.globalAlpha = alpha; ctx.fillStyle = color; ctx.beginPath(); ctx.moveTo(-20, viewH + 20); const offset = camera.x * parallax; for (let x = -40; x <= viewW + 50; x += 35) { const wx = x + offset; const noise = Math.sin(wx / frequency) * amplitude * .42 + Math.sin(wx / (frequency * .47) + 1.8) * amplitude * .23 + Math.sin(wx / (frequency * 1.83) + .4) * amplitude * .17; ctx.lineTo(x, baseline - Math.abs(noise)); } ctx.lineTo(viewW + 20, viewH + 20); ctx.closePath(); ctx.fill(); ctx.restore(); } function drawWorld() { ctx.save(); let shakeX = 0; let shakeY = 0; if (screenShake > .1) { shakeX = rand(-screenShake, screenShake); shakeY = rand(-screenShake, screenShake); } ctx.translate(viewW / 2, viewH / 2); ctx.scale(camera.zoom, camera.zoom); ctx.translate(-viewW / (2 * camera.zoom) - camera.x + shakeX, -viewH / (2 * camera.zoom) - camera.y + shakeY); drawWorldAtmosphere(); for (const p of platforms) p.draw(); for (const checkpoint of checkpoints) checkpoint.draw(); drawGoal(); for (const collectible of collectibles) collectible.draw(); for (const enemy of enemies) enemy.draw(); player.draw(); for (const particle of particles) particle.draw(); for (const text of floatingTexts) text.draw(); ctx.restore(); } function drawWorldAtmosphere() { ctx.save(); for (let x = 180; x < WORLD_WIDTH; x += 620) { const y = 300 + Math.sin(x * .007) * 170; ctx.fillStyle = "rgba(77,252,255,.04)"; ctx.beginPath(); ctx.arc(x, y, 130, 0, TAU); ctx.fill(); ctx.strokeStyle = "rgba(111,194,255,.08)"; ctx.lineWidth = 3; ctx.beginPath(); ctx.moveTo(x, y - 170); ctx.quadraticCurveTo(x + 20, y - 60, x - 10, y + 20); ctx.stroke(); } ctx.fillStyle = "#040711"; ctx.fillRect(-200, 900, WORLD_WIDTH + 400, 400); const abyssGlow = ctx.createLinearGradient(0, 790, 0, 1050); abyssGlow.addColorStop(0, "rgba(85,72,190,.04)"); abyssGlow.addColorStop(1, "rgba(14,4,35,.7)"); ctx.fillStyle = abyssGlow; ctx.fillRect(-100, 770, WORLD_WIDTH + 200, 320); ctx.restore(); } function drawGoal() { if (!goal) return; goal.t += 1 / 60; ctx.save(); ctx.translate(goal.x, goal.y); const pulse = .72 + Math.sin(goal.t * 3) * .14; ctx.shadowColor = "#bca0ff"; ctx.shadowBlur = 28; ctx.strokeStyle = "#d5c2ff"; ctx.lineWidth = 6; ctx.beginPath(); ctx.moveTo(0, 0); ctx.lineTo(0, -goal.h); ctx.stroke(); ctx.fillStyle = "#9f7bff"; ctx.beginPath(); ctx.moveTo(2, -goal.h + 5); ctx.quadraticCurveTo(55, -goal.h + 15, 30, -goal.h + 58); ctx.lineTo(2, -goal.h + 47); ctx.closePath(); ctx.fill(); const g = ctx.createRadialGradient(0, -goal.h + 36, 2, 0, -goal.h + 36, 80); g.addColorStop(0, `rgba(230,220,255,${.55 * pulse})`); g.addColorStop(1, "rgba(140,90,255,0)"); ctx.fillStyle = g; ctx.beginPath(); ctx.arc(0, -goal.h + 36, 80, 0, TAU); ctx.fill(); ctx.restore(); if (!goal.reached && overlap(player, { x: goal.x - 20, y: goal.y - goal.h, w: 80, h: goal.h + 20 })) { winGame(); } } function update(dt) { ambientTime += dt; if (gameState !== "playing") return; elapsed += dt; displayElapsed += dt; screenShake = approach(screenShake, 0, 22 * dt); flashAmount = approach(flashAmount, 0, 2.5 * dt); for (const p of platforms) p.update(dt); player.update(dt); for (const c of collectibles) c.update(dt); for (const e of enemies) e.update(dt); for (const checkpoint of checkpoints) checkpoint.update(dt); for (const p of particles) p.update(dt); particles = particles.filter(p => p.life > 0); for (const text of floatingTexts) text.update(dt); floatingTexts = floatingTexts.filter(t => t.life > 0); enemies = enemies.filter(e => e.alive || e.deadTimer > 0); camera.update(dt); audio.scheduleMusic(); if (messageTimer > 0) { messageTimer -= dt; if (messageTimer <= 0) messageEl.classList.remove("show"); } updateHud(); for (const code in pressed) delete pressed[code]; } function render() { ctx.setTransform(dpr, 0, 0, dpr, 0, 0); drawBackground(); drawWorld(); if (flashAmount > 0) { ctx.save(); ctx.globalAlpha = flashAmount; ctx.fillStyle = "#d5faff"; ctx.fillRect(0, 0, viewW, viewH); ctx.restore(); } if (gameState === "paused") { ctx.fillStyle = "rgba(2,4,12,.6)"; ctx.fillRect(0, 0, viewW, viewH); ctx.fillStyle = "#fff"; ctx.textAlign = "center"; ctx.font = "900 34px system-ui"; ctx.shadowColor = "#7ffaff"; ctx.shadowBlur = 18; ctx.fillText("PAUSED", viewW / 2, viewH / 2); ctx.shadowBlur = 0; ctx.font = "500 14px system-ui"; ctx.fillStyle = "#aeb9d9"; ctx.fillText("Press P to continue", viewW / 2, viewH / 2 + 32); } } function frame(now) { const delta = Math.min(.05, (now - previousTime) / 1000); previousTime = now; accumulator += delta; while (accumulator >= FIXED_STEP) { update(FIXED_STEP); accumulator -= FIXED_STEP; } render(); requestAnimationFrame(frame); } function startGame() { audio.init(); audio.ctx?.resume(); buildLevel(); player.reset(true); camera.reset(); elapsed = 0; displayElapsed = 0; gameState = "playing"; overlay.classList.add("hidden"); menuTitle.innerHTML = "Echoes of<br>the Abyss"; subtitle.textContent = "Cross the forgotten caverns, master aerial movement, awaken ancient checkpoints, and reach the radiant gate beyond the Hollow Reach."; startButton.textContent = "Begin Descent"; secondaryButton.style.display = "none"; updateHearts(); updateHud(); showMessage("Reach the radiant gate", 2.5); } function winGame() { if (goal.reached) return; goal.reached = true; gameState = "won"; player.score += Math.max(0, Math.floor(12000 - displayElapsed * 18)); updateHud(); audio.win(); burst(goal.x, goal.y - goal.h / 2, 80, "#c99dff", { speed: 330, gravity: 100, shape: "spark", size: [2, 7] }); setTimeout(() => { menuTitle.innerHTML = "Radiance<br>Restored"; subtitle.innerHTML = `Final score: <strong>${player.score.toLocaleString()}</strong><br>` + `Relics: <strong>${player.coins} / ${totalCollectibles}</strong> &nbsp; • &nbsp; ` + `Time: <strong>${formatTime(displayElapsed)}</strong>`; startButton.textContent = "Play Again"; secondaryButton.style.display = "none"; overlay.classList.remove("hidden"); }, 900); } function damagePlayer(sourceX, instantFall = false) { if (player.dead || player.invulnerability > 0 || gameState !== "playing") return; player.health--; player.invulnerability = 1.25; player.combo = 0; audio.hurt(); screenShake = 15; flashAmount = .3; updateHearts(); burst(player.x + player.w / 2, player.y + player.h / 2, 22, "#ff6589", { speed: 220, gravity: 350, shape: "diamond" }); if (player.health <= 0 || instantFall) { player.dead = true; player.deathTimer = .9; player.vx = 0; player.vy = -350; player.health = Math.max(1, player.health); showMessage("The abyss claims you...", 1.3); } else { const direction = player.x + player.w / 2 < sourceX ? -1 : 1; player.vx = direction * 380; player.vy = -460; } } function updateHud() { scoreValue.textContent = String(Math.floor(player.score)).padStart(6, "0"); coinValue.textContent = `${player.coins} / ${totalCollectibles}`; timeValue.textContent = formatTime(displayElapsed); progressFill.style.width = `${clamp((player.x / (WORLD_WIDTH - 150)) * 100, 0, 100)}%`; } function updateHearts() { heartsEl.innerHTML = ""; for (let i = 0; i < 3; i++) { const el = document.createElement("div"); el.className = "heart" + (i < player.health ? " active" : ""); el.innerHTML = ` <svg viewBox="0 0 32 28" aria-hidden="true"> <path fill="#ff5277" d="M16 27C14.2 24.7 2 17.6 2 8.8 2 3.8 5.5 1 9.7 1c2.8 0 5.2 1.5 6.3 3.8C17.2 2.5 19.6 1 22.4 1 26.6 1 30 3.8 30 8.8 30 17.6 17.8 24.7 16 27Z"/> <path fill="rgba(255,255,255,.45)" d="M8.3 4.2c-2.1.5-3.5 2.1-3.6 4.2-.1.9.6 1.5 1.3 1 .7-2.2 2-3.4 4-4 .8-.4.1-1.5-1.7-1.2Z"/> </svg>`; heartsEl.appendChild(el); } } function showMessage(text, du