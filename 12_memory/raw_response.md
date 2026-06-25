<!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8" /> <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover" /> <meta name="theme-color" content="#080b18" /> <title>Neon Memory</title> <style> :root { color-scheme: dark; --bg: #070913; --panel: rgba(18, 22, 45, 0.78); --panel-border: rgba(139, 150, 255, 0.18); --text: #f6f7ff; --muted: #9ba3c7; --cyan: #5cecff; --purple: #a875ff; --pink: #ff66c4; --green: #65ffbc; --danger: #ff6685; --gold: #ffd66b; --card-size: clamp(58px, 15vw, 118px); --gap: clamp(8px, 1.6vw, 15px); }
* {
  box-sizing: border-box;
  -webkit-tap-highlight-color: transparent;
}

html,
body {
  min-height: 100%;
  margin: 0;
}

body {
  overflow-x: hidden;
  background:
    radial-gradient(circle at 15% 15%, rgba(92, 236, 255, 0.12), transparent 28%),
    radial-gradient(circle at 85% 18%, rgba(168, 117, 255, 0.15), transparent 30%),
    radial-gradient(circle at 50% 100%, rgba(255, 102, 196, 0.1), transparent 36%),
    linear-gradient(155deg, #050711 0%, #0a0d20 48%, #070914 100%);
  color: var(--text);
  font-family:
    Inter, ui-rounded, "SF Pro Rounded", "Segoe UI", system-ui, -apple-system,
    BlinkMacSystemFont, sans-serif;
  user-select: none;
}

body::before,
body::after {
  position: fixed;
  inset: 0;
  z-index: -2;
  pointer-events: none;
  content: "";
}

body::before {
  opacity: 0.32;
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.025) 1px, transparent 1px);
  background-size: 42px 42px;
  mask-image: linear-gradient(to bottom, black, transparent 88%);
}

body::after {
  z-index: -1;
  background:
    radial-gradient(circle at 50% 30%, transparent 0 35%, rgba(0, 0, 0, 0.32) 85%),
    linear-gradient(to bottom, transparent 65%, rgba(0, 0, 0, 0.3));
}

button,
select {
  font: inherit;
}

button {
  color: inherit;
}

.app {
  display: flex;
  width: min(1180px, 100%);
  min-height: 100vh;
  margin: 0 auto;
  padding:
    max(18px, env(safe-area-inset-top))
    max(14px, env(safe-area-inset-right))
    max(24px, env(safe-area-inset-bottom))
    max(14px, env(safe-area-inset-left));
  align-items: center;
  justify-content: center;
}

.game-shell {
  position: relative;
  width: 100%;
  padding: clamp(16px, 3vw, 30px);
  overflow: hidden;
  border: 1px solid var(--panel-border);
  border-radius: 30px;
  background:
    linear-gradient(145deg, rgba(25, 30, 59, 0.82), rgba(10, 13, 30, 0.78));
  box-shadow:
    0 32px 90px rgba(0, 0, 0, 0.45),
    inset 0 1px 0 rgba(255, 255, 255, 0.06);
  backdrop-filter: blur(24px);
}

.game-shell::before {
  position: absolute;
  top: -100px;
  left: 50%;
  width: 560px;
  height: 240px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(92, 236, 255, 0.13), transparent 68%);
  content: "";
  pointer-events: none;
  transform: translateX(-50%);
}

.topbar {
  position: relative;
  z-index: 2;
  display: grid;
  grid-template-columns: minmax(190px, 1fr) auto;
  gap: 18px;
  align-items: center;
}

.brand {
  min-width: 0;
}

.eyebrow {
  margin: 0 0 5px;
  color: var(--cyan);
  font-size: 0.7rem;
  font-weight: 800;
  letter-spacing: 0.24em;
  text-transform: uppercase;
}

h1 {
  display: flex;
  margin: 0;
  align-items: center;
  gap: 10px;
  font-size: clamp(1.75rem, 4vw, 3rem);
  line-height: 1;
  letter-spacing: -0.055em;
}

h1 .glow {
  color: var(--cyan);
  text-shadow:
    0 0 12px rgba(92, 236, 255, 0.65),
    0 0 28px rgba(92, 236, 255, 0.26);
}

.subtitle {
  margin: 9px 0 0;
  color: var(--muted);
  font-size: clamp(0.78rem, 1.8vw, 0.95rem);
}

.controls {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: flex-end;
}

.select-wrap {
  position: relative;
}

.select-wrap::after {
  position: absolute;
  top: 50%;
  right: 14px;
  color: var(--muted);
  content: "▾";
  pointer-events: none;
  transform: translateY(-52%);
}

select,
.action-btn {
  min-height: 46px;
  border: 1px solid rgba(155, 163, 199, 0.2);
  border-radius: 14px;
  background: rgba(8, 11, 28, 0.65);
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, 0.05),
    0 8px 24px rgba(0, 0, 0, 0.18);
  color: var(--text);
  font-size: 0.86rem;
  font-weight: 750;
}

select {
  min-width: 142px;
  padding: 0 38px 0 14px;
  outline: 0;
  appearance: none;
  cursor: pointer;
}

select:focus-visible,
.action-btn:focus-visible,
.memory-card:focus-visible {
  outline: 2px solid var(--cyan);
  outline-offset: 3px;
}

.action-btn {
  display: inline-flex;
  padding: 0 17px;
  align-items: center;
  gap: 8px;
  justify-content: center;
  cursor: pointer;
  transition:
    transform 160ms ease,
    border-color 160ms ease,
    background 160ms ease,
    box-shadow 160ms ease;
}

.action-btn:hover {
  border-color: rgba(92, 236, 255, 0.5);
  background: rgba(18, 30, 55, 0.85);
  box-shadow:
    0 0 22px rgba(92, 236, 255, 0.1),
    inset 0 1px 0 rgba(255, 255, 255, 0.08);
  transform: translateY(-2px);
}

.action-btn:active {
  transform: translateY(0) scale(0.97);
}

.stats {
  position: relative;
  z-index: 2;
  display: grid;
  margin: clamp(18px, 3vw, 28px) 0;
  grid-template-columns: repeat(4, 1fr);
  gap: clamp(8px, 1.5vw, 13px);
}

.stat {
  position: relative;
  min-width: 0;
  padding: clamp(11px, 2vw, 16px);
  overflow: hidden;
  border: 1px solid rgba(159, 167, 220, 0.14);
  border-radius: 17px;
  background: rgba(7, 10, 26, 0.48);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.035);
}

.stat::after {
  position: absolute;
  right: -18px;
  bottom: -26px;
  width: 70px;
  height: 70px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(92, 236, 255, 0.1), transparent 70%);
  content: "";
}

.stat-label {
  display: block;
  margin-bottom: 5px;
  overflow: hidden;
  color: var(--muted);
  font-size: clamp(0.62rem, 1.6vw, 0.72rem);
  font-weight: 800;
  letter-spacing: 0.09em;
  text-overflow: ellipsis;
  text-transform: uppercase;
  white-space: nowrap;
}

.stat-value {
  position: relative;
  z-index: 1;
  display: block;
  overflow: hidden;
  font-variant-numeric: tabular-nums;
  font-size: clamp(1rem, 2.6vw, 1.35rem);
  font-weight: 850;
  letter-spacing: -0.025em;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.stat-value.accent {
  color: var(--cyan);
  text-shadow: 0 0 14px rgba(92, 236, 255, 0.35);
}

.board-wrap {
  position: relative;
  z-index: 2;
  display: flex;
  min-height: 260px;
  align-items: center;
  justify-content: center;
}

.board {
  --columns: 4;
  display: grid;
  width: min-content;
  max-width: 100%;
  grid-template-columns: repeat(var(--columns), var(--card-size));
  gap: var(--gap);
  perspective: 1400px;
  transition: opacity 180ms ease, transform 180ms ease;
}

.board.changing {
  opacity: 0;
  transform: scale(0.975);
}

.memory-card {
  position: relative;
  width: var(--card-size);
  height: var(--card-size);
  padding: 0;
  border: 0;
  border-radius: clamp(12px, 2vw, 20px);
  background: transparent;
  cursor: pointer;
  perspective: 950px;
  touch-action: manipulation;
}

.memory-card:disabled {
  cursor: default;
}

.card-inner {
  position: absolute;
  inset: 0;
  border-radius: inherit;
  transform-style: preserve-3d;
  transition:
    transform 620ms cubic-bezier(0.2, 0.8, 0.2, 1),
    filter 250ms ease;
}

.memory-card.flipped .card-inner,
.memory-card.matched .card-inner {
  transform: rotateY(180deg);
}

.card-face {
  position: absolute;
  inset: 0;
  display: grid;
  overflow: hidden;
  border-radius: inherit;
  backface-visibility: hidden;
  place-items: center;
  -webkit-backface-visibility: hidden;
}

.card-back {
  border: 1px solid rgba(130, 145, 255, 0.25);
  background:
    radial-gradient(circle at 28% 22%, rgba(255, 255, 255, 0.13), transparent 26%),
    linear-gradient(145deg, #202951 0%, #121735 52%, #161b3f 100%);
  box-shadow:
    0 10px 24px rgba(0, 0, 0, 0.3),
    inset 0 1px 0 rgba(255, 255, 255, 0.1),
    inset 0 -1px 0 rgba(0, 0, 0, 0.3),
    0 0 0 rgba(92, 236, 255, 0);
  transition:
    border-color 180ms ease,
    box-shadow 180ms ease,
    transform 180ms ease;
}

.memory-card:not(:disabled):hover .card-back {
  border-color: rgba(92, 236, 255, 0.58);
  box-shadow:
    0 12px 28px rgba(0, 0, 0, 0.34),
    0 0 24px rgba(92, 236, 255, 0.15),
    inset 0 1px 0 rgba(255, 255, 255, 0.12);
  transform: translateY(-3px);
}

.card-back::before,
.card-back::after {
  position: absolute;
  content: "";
}

.card-back::before {
  inset: 13%;
  border: 1px solid rgba(135, 156, 255, 0.26);
  border-radius: 30%;
  background:
    linear-gradient(45deg, transparent 43%, rgba(92, 236, 255, 0.12) 44% 56%, transparent 57%),
    linear-gradient(-45deg, transparent 43%, rgba(168, 117, 255, 0.14) 44% 56%, transparent 57%);
  transform: rotate(45deg);
}

.card-back::after {
  width: 24%;
  aspect-ratio: 1;
  border: 2px solid rgba(92, 236, 255, 0.75);
  border-radius: 50%;
  box-shadow:
    0 0 14px rgba(92, 236, 255, 0.5),
    inset 0 0 10px rgba(168, 117, 255, 0.35);
}

.card-front {
  border: 1px solid color-mix(in srgb, var(--card-color), white 20%);
  background:
    radial-gradient(circle at 34% 24%, rgba(255, 255, 255, 0.22), transparent 30%),
    linear-gradient(145deg,
      color-mix(in srgb, var(--card-color), #26325f 68%),
      color-mix(in srgb, var(--card-color), #0c1026 24%));
  box-shadow:
    0 12px 28px rgba(0, 0, 0, 0.34),
    0 0 24px color-mix(in srgb, var(--card-color), transparent 75%),
    inset 0 1px 0 rgba(255, 255, 255, 0.16);
  transform: rotateY(180deg);
}

.card-front::before {
  position: absolute;
  inset: 8%;
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 24%;
  content: "";
}

.symbol {
  position: relative;
  z-index: 2;
  font-size: calc(var(--card-size) * 0.43);
  filter:
    drop-shadow(0 4px 4px rgba(0, 0, 0, 0.28))
    drop-shadow(0 0 8px rgba(255, 255, 255, 0.16));
  line-height: 1;
  transform: translateZ(30px);
}

.memory-card.matched {
  pointer-events: none;
}

.memory-card.matched .card-front {
  animation: matchedPulse 800ms cubic-bezier(0.2, 0.8, 0.2, 1);
  border-color: var(--green);
  box-shadow:
    0 0 26px rgba(101, 255, 188, 0.45),
    0 12px 28px rgba(0, 0, 0, 0.3),
    inset 0 0 18px rgba(101, 255, 188, 0.15);
}

.memory-card.wrong .card-inner {
  animation: cardShake 430ms ease;
}

.footer {
  position: relative;
  z-index: 2;
  display: flex;
  margin-top: clamp(18px, 3vw, 28px);
  align-items: center;
  justify-content: center;
  color: var(--muted);
  font-size: 0.78rem;
  text-align: center;
}

.status-dot {
  width: 7px;
  height: 7px;
  margin-right: 8px;
  border-radius: 50%;
  background: var(--green);
  box-shadow: 0 0 12px rgba(101, 255, 188, 0.75);
}

.win-overlay {
  position: fixed;
  inset: 0;
  z-index: 50;
  display: grid;
  padding: 18px;
  opacity: 0;
  background: rgba(3, 5, 14, 0.68);
  backdrop-filter: blur(14px);
  pointer-events: none;
  place-items: center;
  transition: opacity 300ms ease;
}

.win-overlay.visible {
  opacity: 1;
  pointer-events: auto;
}

.win-panel {
  position: relative;
  width: min(450px, 100%);
  padding: 34px 28px 28px;
  overflow: hidden;
  border: 1px solid rgba(92, 236, 255, 0.32);
  border-radius: 28px;
  background:
    radial-gradient(circle at 50% 0%, rgba(92, 236, 255, 0.16), transparent 45%),
    linear-gradient(150deg, rgba(28, 34, 67, 0.98), rgba(10, 13, 31, 0.98));
  box-shadow:
    0 35px 100px rgba(0, 0, 0, 0.58),
    0 0 45px rgba(92, 236, 255, 0.12),
    inset 0 1px 0 rgba(255, 255, 255, 0.09);
  text-align: center;
  transform: translateY(22px) scale(0.92);
  transition: transform 480ms cubic-bezier(0.2, 1, 0.25, 1);
}

.win-overlay.visible .win-panel {
  transform: translateY(0) scale(1);
}

.trophy {
  display: grid;
  width: 84px;
  height: 84px;
  margin: 0 auto 18px;
  border: 1px solid rgba(255, 214, 107, 0.32);
  border-radius: 24px;
  background: rgba(255, 214, 107, 0.08);
  box-shadow:
    0 0 30px rgba(255, 214, 107, 0.2),
    inset 0 0 22px rgba(255, 214, 107, 0.08);
  font-size: 2.6rem;
  place-items: center;
  animation: trophyFloat 2.1s ease-in-out infinite;
}

.win-title {
  margin: 0;
  font-size: clamp(2rem, 7vw, 3rem);
  letter-spacing: -0.06em;
}

.win-subtitle {
  margin: 9px 0 22px;
  color: var(--muted);
  line-height: 1.55;
}

.win-stats {
  display: grid;
  margin-bottom: 22px;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
}

.win-stat {
  padding: 14px 10px;
  border: 1px solid rgba(155, 163, 199, 0.15);
  border-radius: 15px;
  background: rgba(4, 7, 20, 0.46);
}

.win-stat span {
  display: block;
}

.win-stat span:first-child {
  margin-bottom: 3px;
  color: var(--muted);
  font-size: 0.68rem;
  font-weight: 800;
  letter-spacing: 0.09em;
  text-transform: uppercase;
}

.win-stat span:last-child {
  color: var(--cyan);
  font-size: 1.25rem;
  font-weight: 850;
}

.play-again {
  width: 100%;
  min-height: 52px;
  border: 0;
  border-radius: 16px;
  background: linear-gradient(135deg, #52e9ff, #9473ff);
  box-shadow:
    0 13px 30px rgba(92, 236, 255, 0.22),
    inset 0 1px 0 rgba(255, 255, 255, 0.34);
  color: #07101d;
  cursor: pointer;
  font-weight: 900;
  transition:
    transform 160ms ease,
    filter 160ms ease;
}

.play-again:hover {
  filter: brightness(1.08);
  transform: translateY(-2px);
}

.play-again:active {
  transform: scale(0.98);
}

.new-record {
  display: none;
  margin: -10px 0 17px;
  color: var(--gold);
  font-size: 0.8rem;
  font-weight: 850;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  text-shadow: 0 0 12px rgba(255, 214, 107, 0.32);
}

.new-record.visible {
  display: block;
  animation: recordPop 550ms cubic-bezier(0.2, 1.3, 0.3, 1);
}

.particles {
  position: fixed;
  inset: 0;
  z-index: 49;
  overflow: hidden;
  pointer-events: none;
}

.particle {
  position: absolute;
  top: -20px;
  width: 10px;
  height: 16px;
  border-radius: 3px;
  background: var(--particle-color);
  box-shadow: 0 0 9px var(--particle-color);
  animation: confettiFall var(--duration) linear forwards;
  transform: translate3d(0, 0, 0) rotate(var(--rotation));
}

@keyframes matchedPulse {
  0% {
    filter: brightness(1);
    transform: rotateY(180deg) scale(1);
  }
  42% {
    filter: brightness(1.35);
    transform: rotateY(180deg) scale(1.09);
  }
  100% {
    filter: brightness(1);
    transform: rotateY(180deg) scale(1);
  }
}

@keyframes cardShake {
  0%,
  100% {
    transform: rotateY(180deg) translateX(0);
  }
  25% {
    transform: rotateY(180deg) translateX(-5px);
  }
  50% {
    transform: rotateY(180deg) translateX(5px);
  }
  75% {
    transform: rotateY(180deg) translateX(-3px);
  }
}

@keyframes trophyFloat {
  0%,
  100% {
    transform: translateY(0) rotate(-2deg);
  }
  50% {
    transform: translateY(-7px) rotate(2deg);
  }
}

@keyframes recordPop {
  from {
    opacity: 0;
    transform: scale(0.7);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

@keyframes confettiFall {
  0% {
    opacity: 1;
    transform: translate3d(0, -3vh, 0) rotate(0);
  }
  100% {
    opacity: 0.95;
    transform: translate3d(var(--drift), 108vh, 0) rotate(780deg);
  }
}

@media (max-width: 760px) {
  .app {
    align-items: flex-start;
  }

  .game-shell {
    border-radius: 23px;
  }

  .topbar {
    grid-template-columns: 1fr;
  }

  .controls {
    justify-content: stretch;
  }

  .select-wrap,
  select,
  .action-btn {
    flex: 1;
  }

  select,
  .action-btn {
    width: 100%;
  }

  .stats {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 420px) {
  .game-shell {
    padding: 14px;
  }

  .subtitle {
    max-width: 290px;
  }

  .controls {
    display: grid;
    grid-template-columns: 1fr 1fr;
  }

  .stats {
    margin: 15px 0 18px;
  }

  .stat {
    padding: 10px;
    border-radius: 14px;
  }

  .footer {
    font-size: 0.7rem;
  }
}

@media (orientation: landscape) and (max-height: 620px) {
  .app {
    align-items: flex-start;
  }

  .game-shell {
    padding: 14px 20px;
  }

  .topbar {
    grid-template-columns: minmax(180px, 1fr) auto;
  }

  .subtitle,
  .footer {
    display: none;
  }

  .stats {
    margin: 12px 0;
  }

  .stat {
    padding: 8px 12px;
  }
}

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
</style> </head> <body> <main class="app"> <section class="game-shell" aria-label="Memory card game"> <header class="topbar"> <div class="brand"> <p class="eyebrow">Premium Casual</p> <h1><span class="glow">Neon</span> Memory</h1> <p class="subtitle">Match every pair using the fewest moves possible.</p> </div>
    <div class="controls">
      <label class="select-wrap" aria-label="Difficulty">
        <select id="difficulty">
          <option value="4">Classic · 4×4</option>
          <option value="6">Expert · 6×6</option>
          <option value="8">Master · 8×8</option>
        </select>
      </label>
      <button class="action-btn" id="restartButton" type="button">
        <span aria-hidden="true">↻</span>
        Restart
      </button>
    </div>
  </header>

  <section class="stats" aria-label="Game statistics">
    <div class="stat">
      <span class="stat-label">Moves</span>
      <span class="stat-value accent" id="moves">0</span>
    </div>
    <div class="stat">
      <span class="stat-label">Time</span>
      <span class="stat-value" id="timer">00:00</span>
    </div>
    <div class="stat">
      <span class="stat-label">Pairs</span>
      <span class="stat-value" id="pairs">0 / 8</span>
    </div>
    <div class="stat">
      <span class="stat-label">Best</span>
      <span class="stat-value" id="best">—</span>
    </div>
  </section>

  <div class="board-wrap">
    <div class="board" id="board" role="grid" aria-label="Memory cards"></div>
  </div>

  <footer class="footer">
    <span class="status-dot"></span>
    <span id="status">Choose any two cards to begin</span>
  </footer>
</section>
</main> <div class="particles" id="particles" aria-hidden="true"></div> <div class="win-overlay" id="winOverlay" role="dialog" aria-modal="true" aria-labelledby="winTitle" > <div class="win-panel"> <div class="trophy" aria-hidden="true">🏆</div> <h2 class="win-title" id="winTitle">Perfect Match!</h2> <p class="win-subtitle">Every pair has been discovered. Excellent memory!</p> <div class="new-record" id="newRecord">New personal best</div> <div class="win-stats"> <div class="win-stat"> <span>Moves</span> <span id="finalMoves">0</span> </div> <div class="win-stat"> <span>Time</span> <span id="finalTime">00:00</span> </div> </div> <button class="play-again" id="playAgainButton" type="button">Play Again</button> </div> </div> <script> (() => { "use strict"; const symbols = [ "🚀", "🌙", "⚡", "💎", "🎮", "🪐", "👾", "🔥", "🌈", "🎧", "🦋", "🍀", "🧿", "🎯", "🧩", "🍒", "🐳", "🦄", "🍄", "🌻", "🦊", "🐙", "🍉", "🛸", "🎸", "🧠", "💫", "🍩", "🐉", "🪩", "🧸", "🔮" ]; const cardColors = [ "#5cecff", "#a875ff", "#ff66c4", "#65ffbc", "#ffd66b", "#ff7d73", "#72a7ff", "#c4ff61", "#ff9bea", "#64ffe6", "#ffa95c", "#a2a9ff" ]; const board = document.getElementById("board"); const difficultySelect = document.getElementById("difficulty"); const restartButton = document.getElementById("restartButton"); const playAgainButton = document.getElementById("playAgainButton"); const movesElement = document.getElementById("moves"); const timerElement = document.getElementById("timer"); const pairsElement = document.getElementById("pairs"); const bestElement = document.getElementById("best"); const statusElement = document.getElementById("status"); const winOverlay = document.getElementById("winOverlay"); const finalMovesElement = document.getElementById("finalMoves"); const finalTimeElement = document.getElementById("finalTime"); const newRecordElement = document.getElementById("newRecord"); const particles = document.getElementById("particles"); const state = { size: 4, cards: [], firstCard: null, secondCard: null, locked: false, moves: 0, matches: 0, totalPairs: 8, started: false, completed: false, startTime: 0, elapsedSeconds: 0, timerId: null, mismatchTimer: null, generation: 0 }; let audioContext = null; function initAudio() { if (!audioContext) { const AudioContextClass = window.AudioContext || window.webkitAudioContext; if (AudioContextClass) { audioContext = new AudioContextClass(); } } if (audioContext?.state === "suspended") { audioContext.resume().catch(() => {}); } } function playTone(frequency, duration, type = "sine", volume = 0.035, delay = 0) { if (!audioContext) return; const start = audioContext.currentTime + delay; const oscillator = audioContext.createOscillator(); const gain = audioContext.createGain(); oscillator.type = type; oscillator.frequency.setValueAtTime(frequency, start); gain.gain.setValueAtTime(0.0001, start); gain.gain.exponentialRampToValueAtTime(volume, start + 0.012); gain.gain.exponentialRampToValueAtTime(0.0001, start + duration); oscillator.connect(gain); gain.connect(audioContext.destination); oscillator.start(start); oscillator.stop(start + duration + 0.03); } function playFlipSound() { playTone(390, 0.08, "sine", 0.025); playTone(530, 0.07, "triangle", 0.018, 0.035); } function playMatchSound() { playTone(560, 0.12, "sine", 0.035); playTone(710, 0.14, "triangle", 0.03, 0.07); playTone(880, 0.18, "sine", 0.026, 0.14); } function playMismatchSound() { playTone(250, 0.16, "triangle", 0.025); playTone(185, 0.18, "sine", 0.02, 0.09); } function playWinSound() { [523, 659, 784, 1047].forEach((frequency, index) => { playTone(frequency, 0.28, index % 2 ? "triangle" : "sine", 0.035, index * 0.11); }); } function shuffle(items) { const array = [...items]; for (let index = array.length - 1; index > 0; index -= 1) { const randomIndex = Math.floor(Math.random() * (index + 1)); [array[index], array[randomIndex]] = [array[randomIndex], array[index]]; } return array; } function formatTime(seconds) { const minutes = Math.floor(seconds / 60); const remainingSeconds = seconds % 60; return `${String(minutes).padStart(2, "0")}:${String(remainingSeconds).padStart(2, "0")}`; } function getBestKey() { return `neon-memory-best-${state.size}`; } function getBestScore() { try { const rawValue = localStorage.getItem(getBestKey()); if (!rawValue) return null; const parsed = JSON.parse(rawValue); if ( typeof parsed.moves !== "number" || typeof parsed.time !== "number" ) { return null; } return parsed; } catch { return null; } } function isBetterScore(current, best) { if (!best) return true; if (current.moves < best.moves) return true; return current.moves === best.moves && current.time < best.time; } function saveBestScore(score) { try { localStorage.setItem(getBestKey(), JSON.stringify(score)); return true; } catch { return false; } } function updateBestDisplay() { const best = getBestScore(); bestElement.textContent = best ? `${best.moves} · ${formatTime(best.time)}` : "—"; bestElement.title = best ? `${best.moves} moves in ${formatTime(best.time)}` : "No personal best yet"; } function updateStats() { movesElement.textContent = String(state.moves); timerElement.textContent = formatTime(state.elapsedSeconds); pairsElement.textContent = `${state.matches} / ${state.totalPairs}`; } function fitBoard() { const availableWidth = Math.min( window.innerWidth - (window.innerWidth <= 420 ? 56 : 92), 1030 ); const availableHeight = window.innerHeight - ( window.innerWidth <= 760 ? 345 : 305 ); const gap = state.size === 8 ? Math.max(4, Math.min(9, availableWidth * 0.008)) : state.size === 6 ? Math.max(6, Math.min(12, availableWidth * 0.012)) : Math.max(8, Math.min(15, availableWidth * 0.016)); const widthBased = (availableWidth - gap * (state.size - 1)) / state.size; const heightBased = availableHeight > 200 ? (availableHeight - gap * (state.size - 1)) / state.size : widthBased; const maximum = state.size === 4 ? 118 : state.size === 6 ? 86 : 68; const minimum = state.size === 4 ? 50 : state.size === 6 ? 39 : 30; const cardSize = Math.max(minimum, Math.min(maximum, widthBased, heightBased)); document.documentElement.style.setProperty("--card-size", `${cardSize}px`); document.documentElement.style.setProperty("--gap", `${gap}px`); } function startTimer() { if (state.started || state.completed) return; state.started = true; state.startTime = Date.now() - state.elapsedSeconds * 1000; statusElement.textContent = "Find all matching pairs"; state.timerId = window.setInterval(() => { state.elapsedSeconds = Math.floor((Date.now() - state.startTime) / 1000); timerElement.textContent = formatTime(state.elapsedSeconds); }, 250); } function stopTimer() { if (state.timerId !== null) { clearInterval(state.timerId); state.timerId = null; } if (state.started) { state.elapsedSeconds = Math.floor((Date.now() - state.startTime) / 1000); } } function createCard(cardData, index) { const card = document.createElement("button"); card.className = "memory-card"; card.type = "button"; card.dataset.pairId = String(cardData.pairId); card.dataset.index = String(index); card.setAttribute("role", "gridcell"); card.setAttribute("aria-label", `Hidden card ${index + 1}`); card.style.setProperty( "--card-color", cardColors[cardData.pairId % cardColors.length] ); card.innerHTML = ` <span class="card-inner"> <span class="card-face card-back" aria-hidden="true"></span> <span class="card-face card-front"> <span class="symbol" aria-hidden="true">${cardData.symbol}</span> </span> </span> `; card.addEventListener("click", () => handleCardClick(card)); return card; } function resetSelections() { state.firstCard = null; state.secondCard = null; } function handleCardClick(card) { initAudio(); if ( state.locked || state.completed || card === state.firstCard || card.classList.contains("matched") || card.classList.contains("flipped") ) { return; } startTimer(); playFlipSound(); card.classList.add("flipped"); card.setAttribute( "aria-label", `Card showing ${state.cards[Number(card.dataset.index)].symbol}` ); if (!state.firstCard) { state.firstCard = card; statusElement.textContent = "Choose one more card"; return; } state.secondCard = card; state.moves += 1; updateStats(); const matched = state.firstCard.dataset.pairId === state.secondCard.dataset.pairId; if (matched) { resolveMatch(); } else { resolveMismatch(); } } function resolveMatch() { const first = state.firstCard; const second = state.secondCard; first.classList.add("matched"); second.classList.add("matched"); first.disabled = true; second.disabled = true; first.setAttribute("aria-label", "Matched card"); second.setAttribute("aria-label", "Matched card"); state.matches += 1; updateStats(); playMatchSound(); statusElement.textContent = "Great match!"; resetSelections(); if (state.matches === state.