<!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8" /> <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover" /> <meta name="theme-color" content="#0b0e17" /> <title>Sudoku</title> <style> :root { color-scheme: dark; --bg: #080a11; --surface: #111520; --surface-2: #171c29; --surface-3: #1d2433; --border: rgba(255, 255, 255, 0.08); --border-strong: rgba(255, 255, 255, 0.28); --text: #f4f6fb; --muted: #9099ad; --accent: #7c8cff; --accent-strong: #98a4ff; --accent-soft: rgba(124, 140, 255, 0.15); --accent-softer: rgba(124, 140, 255, 0.08); --success: #6ee7b7; --danger: #ff6b7a; --warning: #f8c76a; --cell-peer: rgba(124, 140, 255, 0.07); --cell-same: rgba(124, 140, 255, 0.18); --cell-selected: rgba(124, 140, 255, 0.32); --radius: 18px; --shadow: 0 30px 80px rgba(0, 0, 0, 0.38); }
* {
  box-sizing: border-box;
  -webkit-tap-highlight-color: transparent;
}

html {
  min-height: 100%;
  background: var(--bg);
}

body {
  min-height: 100vh;
  min-height: 100dvh;
  margin: 0;
  overflow-x: hidden;
  font-family:
    Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", sans-serif;
  color: var(--text);
  background:
    radial-gradient(circle at 15% 10%, rgba(124, 140, 255, 0.12), transparent 32rem),
    radial-gradient(circle at 90% 90%, rgba(88, 203, 255, 0.07), transparent 28rem),
    var(--bg);
}

button,
select {
  font: inherit;
}

button {
  color: inherit;
}

.app {
  width: min(1180px, 100%);
  min-height: 100vh;
  min-height: 100dvh;
  margin: 0 auto;
  padding:
    max(22px, env(safe-area-inset-top))
    max(20px, env(safe-area-inset-right))
    max(24px, env(safe-area-inset-bottom))
    max(20px, env(safe-area-inset-left));
  display: flex;
  flex-direction: column;
}

.topbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 18px;
  margin-bottom: 24px;
}

.brand {
  display: flex;
  align-items: center;
  gap: 13px;
  min-width: 0;
}

.brand-mark {
  width: 44px;
  height: 44px;
  flex: 0 0 auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 3px;
  padding: 8px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 13px;
  background:
    linear-gradient(145deg, rgba(124, 140, 255, 0.3), rgba(124, 140, 255, 0.08)),
    var(--surface);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.3);
}

.brand-mark span {
  border-radius: 2px;
  background: rgba(255, 255, 255, 0.38);
}

.brand-mark span:nth-child(1),
.brand-mark span:nth-child(5),
.brand-mark span:nth-child(9) {
  background: var(--accent-strong);
  box-shadow: 0 0 10px rgba(124, 140, 255, 0.5);
}

.brand-copy {
  min-width: 0;
}

.brand-copy h1 {
  margin: 0;
  font-size: clamp(1.35rem, 3vw, 1.75rem);
  line-height: 1;
  letter-spacing: -0.045em;
}

.brand-copy p {
  margin: 6px 0 0;
  color: var(--muted);
  font-size: 0.78rem;
  letter-spacing: 0.07em;
  text-transform: uppercase;
}

.top-actions {
  display: flex;
  align-items: center;
  gap: 10px;
}

.select-wrap {
  position: relative;
}

.select-wrap::after {
  content: "";
  position: absolute;
  top: 50%;
  right: 14px;
  width: 7px;
  height: 7px;
  border-right: 2px solid var(--muted);
  border-bottom: 2px solid var(--muted);
  transform: translateY(-65%) rotate(45deg);
  pointer-events: none;
}

select {
  height: 43px;
  min-width: 126px;
  appearance: none;
  border: 1px solid var(--border);
  border-radius: 12px;
  outline: none;
  padding: 0 36px 0 14px;
  color: var(--text);
  background: var(--surface);
  cursor: pointer;
  transition:
    border-color 160ms ease,
    background 160ms ease;
}

select:hover,
select:focus-visible {
  border-color: rgba(124, 140, 255, 0.55);
  background: var(--surface-2);
}

.primary-button,
.icon-button,
.tool-button,
.numpad-button,
.modal-button {
  border: 0;
  outline: 0;
  cursor: pointer;
  user-select: none;
  touch-action: manipulation;
  transition:
    transform 120ms ease,
    background 160ms ease,
    border-color 160ms ease,
    opacity 160ms ease,
    box-shadow 160ms ease;
}

.primary-button {
  height: 43px;
  padding: 0 17px;
  border-radius: 12px;
  color: #fff;
  font-weight: 750;
  background: linear-gradient(135deg, #7c8cff, #6575e8);
  box-shadow: 0 10px 25px rgba(91, 107, 224, 0.26);
}

.primary-button:hover {
  transform: translateY(-1px);
  box-shadow: 0 14px 28px rgba(91, 107, 224, 0.34);
}

.primary-button:active,
.icon-button:active,
.tool-button:active,
.numpad-button:active,
.modal-button:active {
  transform: scale(0.97);
}

.game-layout {
  flex: 1;
  display: grid;
  grid-template-columns: minmax(360px, 610px) minmax(270px, 340px);
  align-items: center;
  justify-content: center;
  gap: clamp(28px, 5vw, 68px);
}

.board-column {
  width: 100%;
  min-width: 0;
}

.status-panel {
  min-height: 66px;
  margin-bottom: 13px;
  padding: 12px 15px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  align-items: center;
  border: 1px solid var(--border);
  border-radius: 15px;
  background: rgba(17, 21, 32, 0.78);
  box-shadow: 0 14px 38px rgba(0, 0, 0, 0.18);
  backdrop-filter: blur(14px);
}

.status-item {
  min-width: 0;
  text-align: center;
}

.status-item + .status-item {
  border-left: 1px solid var(--border);
}

.status-label {
  margin-bottom: 4px;
  color: var(--muted);
  font-size: 0.69rem;
  font-weight: 700;
  letter-spacing: 0.09em;
  text-transform: uppercase;
}

.status-value {
  overflow: hidden;
  color: var(--text);
  font-size: 1rem;
  font-weight: 750;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.timer-value {
  font-variant-numeric: tabular-nums;
  letter-spacing: 0.04em;
}

.board-shell {
  position: relative;
  width: 100%;
  aspect-ratio: 1;
  overflow: hidden;
  border: 1px solid var(--border-strong);
  border-radius: var(--radius);
  background: var(--surface);
  box-shadow: var(--shadow);
}

.sudoku-board {
  width: 100%;
  height: 100%;
  display: grid;
  grid-template-columns: repeat(9, 1fr);
  grid-template-rows: repeat(9, 1fr);
  background: rgba(255, 255, 255, 0.08);
  gap: 1px;
}

.cell {
  position: relative;
  min-width: 0;
  min-height: 0;
  display: grid;
  place-items: center;
  padding: 0;
  border: 0;
  border-radius: 0;
  outline: none;
  color: #c8ceff;
  background: #111621;
  cursor: pointer;
  isolation: isolate;
  font-size: clamp(1.35rem, 4.2vw, 2.15rem);
  font-weight: 620;
  font-variant-numeric: tabular-nums;
  transition:
    background 100ms ease,
    color 100ms ease,
    transform 100ms ease;
}

.cell::after {
  content: "";
  position: absolute;
  inset: 0;
  z-index: -1;
  opacity: 0;
  background: rgba(255, 255, 255, 0.05);
  transition: opacity 120ms ease;
}

.cell:hover::after {
  opacity: 1;
}

.cell:nth-child(3n):not(:nth-child(9n)) {
  box-shadow: 2px 0 0 rgba(255, 255, 255, 0.29);
}

.cell:nth-child(n + 19):nth-child(-n + 27),
.cell:nth-child(n + 46):nth-child(-n + 54) {
  box-shadow: inset 0 -2px 0 rgba(255, 255, 255, 0.29);
}

.cell:nth-child(21),
.cell:nth-child(24),
.cell:nth-child(48),
.cell:nth-child(51) {
  box-shadow:
    2px 0 0 rgba(255, 255, 255, 0.29),
    inset 0 -2px 0 rgba(255, 255, 255, 0.29);
}

.cell.peer {
  background: color-mix(in srgb, #111621 92%, var(--accent) 8%);
}

.cell.same {
  background: color-mix(in srgb, #111621 78%, var(--accent) 22%);
}

.cell.selected {
  color: #fff;
  background: color-mix(in srgb, #111621 59%, var(--accent) 41%);
  box-shadow: inset 0 0 0 2px rgba(151, 162, 255, 0.82);
}

.cell.selected:nth-child(3n):not(:nth-child(9n)) {
  box-shadow:
    2px 0 0 rgba(255, 255, 255, 0.29),
    inset 0 0 0 2px rgba(151, 162, 255, 0.82);
}

.cell.given {
  color: #f8f9ff;
  font-weight: 790;
}

.cell.hinted {
  color: var(--success);
  font-weight: 760;
}

.cell.wrong {
  color: var(--danger);
  background: rgba(255, 74, 95, 0.11);
}

.cell.conflict {
  color: var(--danger);
  background: rgba(255, 74, 95, 0.16);
}

.cell.wrong.selected,
.cell.conflict.selected {
  background: rgba(255, 74, 95, 0.23);
  box-shadow: inset 0 0 0 2px rgba(255, 107, 122, 0.9);
}

.cell.pop .cell-value {
  animation: valuePop 170ms ease-out;
}

.cell-value {
  position: relative;
  z-index: 2;
  line-height: 1;
}

.notes {
  position: absolute;
  inset: 8%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  align-items: center;
  justify-items: center;
  color: #9ba5c2;
  font-size: clamp(0.46rem, 1.35vw, 0.72rem);
  font-weight: 650;
  line-height: 1;
  pointer-events: none;
}

.cell.peer .notes {
  color: #aab3d2;
}

.cell.selected .notes {
  color: #e2e5ff;
}

.pause-overlay,
.generation-overlay {
  position: absolute;
  inset: 0;
  z-index: 20;
  display: grid;
  place-items: center;
  padding: 24px;
  text-align: center;
  background: rgba(8, 10, 17, 0.91);
  backdrop-filter: blur(15px);
  opacity: 0;
  visibility: hidden;
  transition:
    opacity 180ms ease,
    visibility 180ms ease;
}

.pause-overlay.visible,
.generation-overlay.visible {
  opacity: 1;
  visibility: visible;
}

.overlay-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
}

.overlay-icon {
  width: 62px;
  height: 62px;
  display: grid;
  place-items: center;
  border: 1px solid rgba(124, 140, 255, 0.28);
  border-radius: 20px;
  color: var(--accent-strong);
  background: var(--accent-soft);
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.22);
}

.overlay-content h2 {
  margin: 0;
  font-size: 1.5rem;
  letter-spacing: -0.035em;
}

.overlay-content p {
  max-width: 280px;
  margin: -5px 0 0;
  color: var(--muted);
  line-height: 1.55;
}

.spinner {
  width: 48px;
  height: 48px;
  border: 4px solid rgba(124, 140, 255, 0.16);
  border-top-color: var(--accent);
  border-radius: 50%;
  animation: spin 700ms linear infinite;
}

.control-panel {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 18px;
}

.tool-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 9px;
}

.tool-button {
  position: relative;
  min-height: 74px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 7px;
  padding: 9px 6px;
  border: 1px solid var(--border);
  border-radius: 14px;
  color: var(--muted);
  background: rgba(17, 21, 32, 0.9);
}

.tool-button:hover:not(:disabled) {
  color: var(--text);
  border-color: rgba(124, 140, 255, 0.38);
  background: var(--surface-2);
  transform: translateY(-1px);
}

.tool-button.active {
  color: var(--accent-strong);
  border-color: rgba(124, 140, 255, 0.48);
  background: var(--accent-soft);
  box-shadow: inset 0 0 0 1px rgba(124, 140, 255, 0.1);
}

.tool-button:disabled {
  cursor: default;
  opacity: 0.35;
}

.tool-icon {
  width: 23px;
  height: 23px;
  display: grid;
  place-items: center;
}

.tool-icon svg {
  width: 100%;
  height: 100%;
  fill: none;
  stroke: currentColor;
  stroke-width: 1.8;
  stroke-linecap: round;
  stroke-linejoin: round;
}

.tool-label {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.01em;
}

.mode-dot {
  position: absolute;
  top: 9px;
  right: 9px;
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: var(--accent);
  box-shadow: 0 0 12px var(--accent);
  opacity: 0;
  transform: scale(0.5);
  transition:
    opacity 150ms ease,
    transform 150ms ease;
}

.tool-button.active .mode-dot {
  opacity: 1;
  transform: scale(1);
}

.numpad {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}

.numpad-button {
  position: relative;
  min-height: 66px;
  overflow: hidden;
  border: 1px solid var(--border);
  border-radius: 15px;
  color: #eef0ff;
  background: linear-gradient(145deg, #181e2c, #121722);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
  font-size: 1.35rem;
  font-weight: 720;
}

.numpad-button::before {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(145deg, rgba(124, 140, 255, 0.13), transparent);
  opacity: 0;
  transition: opacity 150ms ease;
}

.numpad-button:hover:not(:disabled) {
  border-color: rgba(124, 140, 255, 0.48);
  transform: translateY(-1px);
}

.numpad-button:hover:not(:disabled)::before {
  opacity: 1;
}

.numpad-button:disabled {
  cursor: default;
  opacity: 0.28;
}

.numpad-button.complete-number {
  color: var(--muted);
  opacity: 0.43;
}

.numpad-button .remaining {
  position: absolute;
  top: 7px;
  right: 9px;
  color: var(--muted);
  font-size: 0.62rem;
  font-weight: 750;
}

.secondary-actions {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}

.icon-button {
  min-height: 46px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  border: 1px solid var(--border);
  border-radius: 13px;
  color: var(--muted);
  background: var(--surface);
  font-size: 0.82rem;
  font-weight: 720;
}

.icon-button:hover {
  color: var(--text);
  border-color: rgba(124, 140, 255, 0.36);
  background: var(--surface-2);
}

.icon-button svg {
  width: 18px;
  height: 18px;
  fill: none;
  stroke: currentColor;
  stroke-width: 1.9;
  stroke-linecap: round;
  stroke-linejoin: round;
}

.keyboard-help {
  color: var(--muted);
  font-size: 0.72rem;
  line-height: 1.65;
  text-align: center;
}

kbd {
  display: inline-grid;
  min-width: 24px;
  height: 22px;
  place-items: center;
  margin: 0 2px;
  padding: 0 5px;
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-bottom-color: rgba(255, 255, 255, 0.2);
  border-radius: 5px;
  color: #bbc2d5;
  background: rgba(255, 255, 255, 0.04);
  font-family: inherit;
  font-size: 0.63rem;
  font-weight: 700;
}

.modal-backdrop {
  position: fixed;
  inset: 0;
  z-index: 100;
  display: grid;
  place-items: center;
  padding: 22px;
  background: rgba(4, 5, 10, 0.75);
  backdrop-filter: blur(13px);
  opacity: 0;
  visibility: hidden;
  transition:
    opacity 220ms ease,
    visibility 220ms ease;
}

.modal-backdrop.visible {
  opacity: 1;
  visibility: visible;
}

.completion-modal {
  width: min(420px, 100%);
  padding: 31px;
  border: 1px solid rgba(255, 255, 255, 0.11);
  border-radius: 24px;
  text-align: center;
  background:
    radial-gradient(circle at 50% 0%, rgba(124, 140, 255, 0.17), transparent 16rem),
    #121722;
  box-shadow: 0 35px 100px rgba(0, 0, 0, 0.52);
  transform: translateY(20px) scale(0.96);
  transition: transform 260ms cubic-bezier(0.2, 0.85, 0.25, 1.15);
}

.modal-backdrop.visible .completion-modal {
  transform: translateY(0) scale(1);
}

.trophy {
  width: 76px;
  height: 76px;
  margin: 0 auto 18px;
  display: grid;
  place-items: center;
  border: 1px solid rgba(248, 199, 106, 0.28);
  border-radius: 24px;
  color: var(--warning);
  background: rgba(248, 199, 106, 0.11);
  box-shadow: 0 18px 45px rgba(248, 199, 106, 0.08);
}

.trophy svg {
  width: 40px;
  height: 40px;
  fill: none;
  stroke: currentColor;
  stroke-width: 1.65;
  stroke-linecap: round;
  stroke-linejoin: round;
}

.completion-modal h2 {
  margin: 0;
  font-size: 1.75rem;
  letter-spacing: -0.045em;
}

.completion-modal > p {
  margin: 9px 0 23px;
  color: var(--muted);
  line-height: 1.55;
}

.completion-stats {
  margin-bottom: 24px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  overflow: hidden;
  border: 1px solid var(--border);
  border-radius: 15px;
  background: rgba(255, 255, 255, 0.025);
}

.completion-stat {
  padding: 13px 7px;
}

.completion-stat + .completion-stat {
  border-left: 1px solid var(--border);
}

.completion-stat small {
  display: block;
  margin-bottom: 4px;
  color: var(--muted);
  font-size: 0.62rem;
  font-weight: 720;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.completion-stat strong {
  display: block;
  font-size: 0.92rem;
  font-variant-numeric: tabular-nums;
}

.modal-button {
  width: 100%;
  min-height: 48px;
  border-radius: 13px;
  color: #fff;
  background: linear-gradient(135deg, #7c8cff, #6575e8);
  box-shadow: 0 12px 28px rgba(91, 107, 224, 0.28);
  font-weight: 780;
}

.toast-container {
  position: fixed;
  right: max(20px, env(safe-area-inset-right));
  bottom: max(20px, env(safe-area-inset-bottom));
  z-index: 150;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 9px;
  pointer-events: none;
}

.toast {
  max-width: min(360px, calc(100vw - 40px));
  padding: 11px 15px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 11px;
  color: #e9ecf5;
  background: rgba(24, 29, 42, 0.95);
  box-shadow: 0 14px 35px rgba(0, 0, 0, 0.3);
  backdrop-filter: blur(12px);
  font-size: 0.8rem;
  font-weight: 620;
  animation: toastIn 220ms ease-out;
}

.toast.success {
  border-color: rgba(110, 231, 183, 0.28);
}

.toast.error {
  border-color: rgba(255, 107, 122, 0.3);
}

.toast.leaving {
  animation: toastOut 190ms ease-in forwards;
}

#confettiCanvas {
  position: fixed;
  inset: 0;
  z-index: 110;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

@keyframes valuePop {
  0% {
    opacity: 0.35;
    transform: scale(0.62);
  }
  75% {
    transform: scale(1.13);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

@keyframes toastIn {
  from {
    opacity: 0;
    transform: translateY(9px) scale(0.97);
  }
}

@keyframes toastOut {
  to {
    opacity: 0;
    transform: translateY(8px) scale(0.97);
  }
}

@media (max-width: 900px) {
  .app {
    width: min(680px, 100%);
  }

  .game-layout {
    grid-template-columns: 1fr;
    align-items: start;
    gap: 20px;
  }

  .control-panel {
    gap: 14px;
  }

  .tool-grid {
    order: 2;
  }

  .numpad {
    order: 1;
    grid-template-columns: repeat(9, 1fr);
    gap: 7px;
  }

  .numpad-button {
    min-height: 54px;
    border-radius: 12px;
    font-size: 1.1rem;
  }

  .numpad-button .remaining {
    display: none;
  }

  .secondary-actions {
    order: 3;
  }

  .keyboard-help {
    order: 4;
  }
}

@media (max-width: 620px) {
  .app {
    padding-left: 12px;
    padding-right: 12px;
  }

  .topbar {
    align-items: flex-start;
    margin-bottom: 17px;
  }

  .brand-copy p {
    display: none;
  }

  .brand-mark {
    width: 40px;
    height: 40px;
    border-radius: 12px;
  }

  .top-actions {
    gap: 7px;
  }

  select {
    width: 106px;
    min-width: 106px;
    height: 40px;
    padding-left: 11px;
    font-size: 0.78rem;
  }

  .primary-button {
    height: 40px;
    padding: 0 13px;
    font-size: 0.78rem;
  }

  .status-panel {
    min-height: 58px;
    margin-bottom: 9px;
    padding: 9px 8px;
    border-radius: 12px;
  }

  .status-label {
    font-size: 0.59rem;
  }

  .status-value {
    font-size: 0.87rem;
  }

  .board-shell {
    border-radius: 12px;
  }

  .cell {
    font-size: clamp(1.08rem, 6.3vw, 1.7rem);
  }

  .notes {
    inset: 5%;
    font-size: clamp(0.4rem, 2.25vw, 0.61rem);
  }

  .numpad {
    gap: 4px;
  }

  .numpad-button {
    min-height: 46px;
    border-radius: 9px;
    font-size: 1rem;
  }

  .tool-grid {
    gap: 5px;
  }

  .tool-button {
    min-height: 62px;
    gap: 5px;
    padding: 7px 3px;
    border-radius: 11px;
  }

  .tool-icon {
    width: 20px;
    height: 20px;
  }

  .tool-label {
    font-size: 0.61rem;
  }

  .mode-dot {
    top: 7px;
    right: 7px;
    width: 6px;
    height: 6px;
  }

  .secondary-actions {
    gap: 7px;
  }

  .icon-button {
    min-height: 43px;
    border-radius: 11px;
  }

  .keyboard-help {
    display: none;
  }
}

@media (max-width: 390px) {
  .brand-copy h1 {
    font-size: 1.22rem;
  }

  .brand-mark {
    display: none;
  }

  select {
    width: 94px;
    min-width: 94px;
  }

  .primary-button {
    padding: 0 10px;
  }

  .tool-label {
    font-size: 0.56rem;
  }
}

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    animation-duration: 1ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 1ms !important;
  }
}
</style> </head> <body> <main class="app"> <header class="topbar"> <div class="brand"> <div class="brand-mark" aria-hidden="true"> <span></span><span></span><span></span> <span></span><span></span><span></span> <span></span><span></span><span></span> </div> <div class="brand-copy"> <h1>Sudoku</h1> <p>Focus · Logic · Precision</p> </div> </div>
  <div class="top-actions">
    <div class="select-wrap">
      <select id="difficultySelect" aria-label="Difficulty">
        <option value="easy">Easy</option>
        <option value="medium" selected>Medium</option>
        <option value="hard">Hard</option>
      </select>
    </div>
    <button class="primary-button" id="newGameButton" type="button">
      New Game
    </button>
  </div>
</header>

<section class="game-layout">
  <div class="board-column">
    <div class="status-panel" aria-label="Game status">
      <div class="status-item">
        <div class="status-label">Difficulty</div>
        <div class="status-value" id="difficultyLabel">Medium</div>
      </div>
      <div class="status-item">
        <div class="status-label">Time</div>
        <div class="status-value timer-value" id="timer">00:00</div>
      </div>
      <div class="status-item">
        <div class="status-label">Mistakes</div>
        <div class="status-value" id="mistakes">0</div>
      </div>
    </div>

    <div class="board-shell">
      <div
        class="sudoku-board"
        id="board"
        role="grid"
        aria-label="Sudoku board"
      ></div>

      <div class="pause-overlay" id="pauseOverlay">
        <div class="overlay-content">
          <div class="overlay-icon" aria-hidden="true">
            <svg width="28" height="28" viewBox="0 0 24 24">
              <path
                d="M8 5v14M16 5v14"
                fill="none"
                stroke="currentColor"
                stroke-width="2.2"
                stroke-linecap="round"
              />
            </svg>
          </div>
          <h2>Game Paused</h2>
          <p>Your board is hidden. Resume when you are ready.</p>
          <button class="primary-button" id="overlayResumeButton" type="button">
            Resume Game
          </button>
        </div>
      </div>

      <div class="generation-overlay visible" id="generationOverlay">
        <div class="overlay-content">
          <div class="spinner" aria-hidden="true"></div>
          <h2>Creating Puzzle</h2>
          <p>Building a unique Sudoku board for you.</p>
        </div>
      </div>
    </div>
  </div>

  <aside class="control-panel" aria-label="Game controls">
    <div class="tool-grid">
      <button
        class="tool-button"
        id="undoButton"
        type="button"
        aria-label="Undo"
        title="Undo (Ctrl+Z)"
      >
        <span class="tool-icon">
          <svg viewBox="0 0 24 24">
            <path d="M9 7 4 12l5 5" />
            <path d="M5 12h8a6 6 0 1 1 0 12" transform="translate(0 -6)" />
          </svg>
        </span>
        <span class="tool-label">Undo</span>
      </button>

      <button
        class="tool-button"
        id="redoButton"
        type="button"
        aria-label="Redo"
        title="Redo (Ctrl+Y)"
      >
        <span class="tool-icon">
          <svg viewBox="0 0 24 24">
            <path d="m15 7 5 5-5 5" />
            <path d="M19 12h-8a6 6 0 1 0 0 12" transform="translate(0 -6)" />
          </svg>
        </span>
        <span class="tool-label">Redo</span>
      </button>

      <button
        class="tool-button"
        id="pencilButton"
        type="button"
        aria-pressed="false"
        aria-label="Toggle pencil marks"
        title="Pencil Marks (P)"
      >
        <span class="mode-dot"></span>
        <span class="tool-icon">
          <svg viewBox="0 0 24 24">
            <path d="m4 20 4.2-1 10.9-10.9a2.1 2.1 0 0 0-3-3L5.2 16Z" />
            <path d="m14.6 6.6 3 3" />
            <path d="M4 20h5" />
          </svg>
        </span>
        <span class="tool-label">Notes</span>
      </button>

      <button
        class="tool-button"
        id="hintButton"
        type="button"
        aria-label="Reveal a cell"
        title="Reveal one cell"
      >
        <span class="tool-icon">
          <svg viewBox="0 0 24 24">
            <path d="M9 18h6" />
            <path d="M10 22h4" />
            <path d="M8.5 14.5A7 7 0 1 1 15.6 14c-1 .8-1.6 1.8-1.6 3h-4c0-1.1-.5-1.9-1.5-2.5Z" />
          </svg>
        </span>
        <span class="tool-label">Hint</span>
      </button>

      <button
        class="tool-button"
        id="eraseButton"
        type="button"
        aria-label="Erase selected cell"
        title="Erase (Backspace)"
      >
        <span class="tool-icon">
          <svg viewBox="0 0 24 24">
            <path d="m3 15 8.5-9a2 2 0 0 1 2.9 0l5.1 5.2a2 2 0 0 1 0 2.8l-5.7 6H8Z" />
            <path d="m11 9 7 7" />
            <path d="M13.8 20H21" />
          </svg>
        </span>
        <span class="tool-label">Erase</span>
      </button>
    </div>

    <div class="numpad" id="numpad" aria-label="Number pad"></div>

    <div class="secondary-actions">
      <button class="icon-button" id="pauseButton" type="button">
        <svg id="pauseIcon" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M8 5v14M16 5v14" />
        </svg>
        <span id="pauseButtonLabel">Pause</span>
      </button>

      <button class="icon-button" id="restartButton" type="button">
        <svg viewBox="0 0 24 24" aria-hidden="true">
          <path d="M4 4v6h6" />
          <path d="M5.5 15a8 8 0 1 0 .9-7.8L4 10" />
        </svg>
        <span>Restart</span>
      </button>
    </div>

    <div class="keyboard-help">
      Select a cell, then press <kbd>1</kbd>–<kbd>9</kbd>.
      Use <kbd>P</kbd> for notes and arrow keys to navigate.
    </div>
  </aside>
</section>
</main> <div class="modal-backdrop" id="completionBackdrop" aria-hidden="true"> <div class="completion-modal" role="dialog" aria-modal="true" aria-labelledby="completionTitle" > <div class="trophy" aria-hidden="true"> <svg viewBox="0 0 24 24"> <path d="M8 4h8v4a4 4 0 0 1-8 0Z" /> <path d="M8 6H4v1a4 4 0 0 0 4 4" /> <path d="M16 6h4v1a4 4 0 0 1-4 4" /> <path d="M12 12v5" /> <path d="M8 21h8" /> <path d="M9 17h6v4H9z" /> </svg> </div> <h2 id="completionTitle">Puzzle Complete!</h2> <p>Excellent focus. Every number is exactly where it belongs.</p>
  <div class="completion-stats">
    <div class="completion-stat">
      <small>Level</small>
      <strong id="completionDifficulty">Medium</strong>
    </div>
    <div class="completion-stat">
      <small>Time</small>
      <strong id="completionTime">00:00</strong>
    </div>
    <div class="completion-stat">
      <small>Mistakes</small>
      <strong id="completionMistakes">0</strong>
    </div>
  </div>

  <button class="modal-button" id="playAgainButton" type="button">
    Play Another Puzzle
  </button>
</div>
</div>

<canvas id="confettiCanvas" aria-hidden="true"></canvas>

<div class="toast-container" id="toastContainer" aria-live="polite"></div> <script> (() => { "use strict"; const STORAGE_KEY = "ultimate-sudoku-state-v1"; const DIFFICULTY_CONFIG = { easy: { label: "Easy", clues: 44 }, medium: { label: "Medium", clues: 34 }, hard: { label: "Hard", clues: 28 } }; const boardElement = document.getElementById("board"); const numpadElement = document.getElementById("numpad"); const timerElement = document.getElementById("timer"); const mistakesElement = document.getElementById("mistakes"); const difficultyLabelElement = document.getElementById("difficultyLabel"); const difficultySelect = document.getElementById("difficultySelect"); const generationOverlay = document.getElementById("generationOverlay"); const pauseOverlay = document.getElementById("pauseOverlay"); const completionBackdrop = document.getElementById("completionBackdrop"); const completionDifficulty = document.getElementById("completionDifficulty"); const completionTime = document.getElementById("completionTime"); const completionMistakes = document.getElementById("completionMistakes"); const pauseButtonLabel = document.getElementById("pauseButtonLabel"); const pauseIcon = document.getElementById("pauseIcon"); const newGameButton = document.getElementById("newGameButton"); const restartButton = document.getElementById("restartButton"); const pauseButton = document.getElementById("pauseButton"); const overlayResumeButton = document.getElementById("overlayResumeButton"); const pencilButton = document.getElementById("pencilButton"); const eraseButton = document.getElementById("eraseButton"); const hintButton = document.getElementById("hintButton"); const undoButton = document.getElementById("undoButton"); const redoButton = document.getElementById("redoButton"); const playAgainButton = document.getElementById("playAgainButton"); const toastContainer = document.getElementById("toastContainer"); const confettiCanvas = document.getElementById("confettiCanvas"); const confettiContext = confettiCanvas.getContext("2d"); const cells = []; const numberButtons = []; let state = createEmptyState(); let timerInterval = null; let saveCounter = 0; let generating = false; let confettiFrame = null; let confettiParticles = []; function createEmptyState() { return { difficulty: "medium", puzzle: Array(81).fill(0), solution: Array(81).fill(0), board: Array(81).fill(0), notes: Array.from({ length: 81 }, () => []), locked: Array(81).fill(false), hinted: Array(81).fill(false), selected: -1, pencilMode: false, mistakes: 0, hintsUsed: 0, elapsed: 0, paused: false, completed: false, history: [], redo: [] }; } function buildBoard() { const fragment = document.createDocumentFragment(); for (let index = 0; index < 81; index++) { const cell = document.createElement("button"); cell.type = "button"; cell.className = "cell"; cell.dataset.index = String(index); cell.setAttribute("role", "gridcell"); cell.setAttribute("aria-label", getCellLabel(index, 0)); const value = document.createElement("span"); value.className = "cell-value"; const notes = document.createElement("span"); notes.className = "notes"; notes.setAttribute("aria-hidden", "true"); for (let number = 1; number <= 9; number++) { const note = document.createElement("span"); note.dataset.note = String(number); notes.appendChild(note); } cell.append(value, notes); cell.addEventListener("click", () => selectCell(index)); cells.push({ button: cell, value, notes: [...notes.children] }); fragment.appendChild(cell); } boardElement.appendChild(fragment); } function buildNumpad() { const fragment = document.createDocumentFragment(); for (let number = 1; number <= 9; number++) { const button = document.createElement("button"); button.type = "button"; button.className = "numpad-button"; button.dataset.number = String(number); button.setAttribute("aria-label", `Enter ${number}`); button.innerHTML = ` <span>${number}</span> <span class="remaining" aria-hidden="true">9</span> `; button.addEventListener("click", () => enterNumber(number)); numberButtons.push(button); fragment.appendChild(button); } numpadElement.appendChild(fragment); } function getCellLabel(index, value) { const row = Math.floor(index / 9) + 1; const column = (index % 9) + 1; return value ? `Row ${row}, column ${column}, value ${value}` : `Row ${row}, column ${column}, empty`; } function shuffle(array) { for (let index = array.length - 1; index > 0; index--) { const randomIndex = Math.floor(Math.random() * (index + 1)); [array[index], array[randomIndex]] = [ array[randomIndex], array[index] ]; } return array; } function generateSolvedGrid() { const base = 3; const side = 9; const pattern = (row, column) => (base * (row % base) + Math.floor(row / base) + column) % side; const rowGroups = shuffle([0, 1, 2]); const columnGroups = shuffle([0, 1, 2]); const rows = rowGroups.flatMap(group => shuffle([0, 1, 2]).map(row => group * base + row) ); const columns = columnGroups.flatMap(group => shuffle([0, 1, 2]).map(column => group * base + column) ); const numbers = shuffle([1, 2, 3, 4, 5, 6, 7, 8, 9]); return rows.flatMap(row => columns.map(column => numbers[pattern(row, column)]) ); } function candidatesMask(board, index) { const row = Math.floor(index / 9); const column = index % 9; let used = 0; for (let i = 0; i < 9; i++) { const rowValue = board[row * 9 + i]; const columnValue = board[i * 9 + column]; if (rowValue) used |= 1 << rowValue; if (columnValue) used |= 1 << columnValue; } const boxRow = Math.floor(row / 3) * 3; const boxColumn = Math.floor(column / 3) * 3; for (let r = boxRow; r < boxRow + 3; r++) { for (let c = boxColumn; c < boxColumn + 3; c++) { const value = board[r * 9 + c]; if (value) used |= 1 << value; } } return 0x3fe & ~used; } function countBits(mask) { let count = 0; while (mask) { mask &= mask - 1; count++; } return count; } function countSolutions(board, limit = 2) { let solutions = 0; function solve() { if (solutions >= limit) return; let bestIndex = -1; let bestMask = 0; let smallestCount = 10; for (let index = 0; index < 81; index++) { if (board[index] !== 0) continue; const mask = candidatesMask(board, index); const count = countBits(mask); if (count === 0) return; if (count < smallestCount) { smallestCount = count; bestIndex = index; bestMask = mask; if (count === 1) break; } } if (bestIndex === -1) { solutions++; return; } for (let number = 1; number <= 9; number++) { if (!(bestMask & (1 << number))) continue; board[bestIndex] = number; solve(); board[bestIndex] = 0; if (solutions >= limit) return; } } solve(); return solutions; } function generatePuzzle(difficulty) { const solution = generateSolvedGrid(); const puzzle = solution.slice(); const targetClues = DIFFICULTY_CONFIG[difficulty].clues; let clues = 81; let passes = 0; while (clues > targetClues && passes < 4) { const indexes = shuffle( Array.from({ length: 81 }, (_, index) => index) .filter(index => puzzle[index] !== 0) ); let changed = false; for (const index of indexes) { if (clues <= targetClues) break; const previous = puzzle[index]; puzzle[index] = 0; const testBoard = puzzle.slice(); if (countSolutions(testBoard, 2) === 1) { clues--; changed = true; } else { puzzle[index] = previous; } } if (!changed) break; passes++; } return { puzzle, solution }; } function createSnapshot(index) { return { index, value: state.board[index], notes: [...state.notes[index]], locked: state.locked[index], hinted: state.hinted[index] }; } function applySnapshot(snapshot) { state.board[snapshot.index] = snapshot.value; state.notes[snapshot.index] = [...snapshot.notes]; state.locked[snapshot.index] = snapshot.locked; state.hinted[snapshot.index] = snapshot.hinted; } function snapshotsEqual(first, second) { return ( first.value === second.value && first.locked === second.locked && first.hinted === second.hinted && first.notes.length === second.notes.length && first.notes.every((number, index) => number === second.notes[index]) ); } function commitAction(index, before, after, type = "edit") { if (snapshotsEqual(before, after)) return false; state.history.push({ index, before, after, type }); if (state.history.length > 400) state.history.shift(); state.redo = []; updateUndoRedoButtons(); saveState(); return true; } function selectCell(index) { if (generating || state.paused || state.completed) return; state.selected = index; renderBoard(); saveState(); } function enterNumber(number) { if ( generating || state.paused || state.completed || state.selected < 0 ) { return; } const index = state.selected; if (state.locked[index]) { pulseCell(index); return; } const before = createSnapshot(index); if (state.pencilMode) { if (state.board[index] !== 0) return; const notes = new Set(state.notes[index]); if (notes.has(number)) { notes.delete(number); } else { notes.add(number); } state.notes[index] = [...notes].sort((a, b) => a - b); } else { if (state.board[index] === number) { state.board[index] = 0; } else { state.board[index] = number; state.notes[index] = []; if (number !== state.solution[index]) { state.mistakes++; showToast("That number does not belong in this cell.", "error"); } } } const after = createSnapshot(index); if (commitAction(index, before, after, state.pencilMode ? "note" : "number")) { pulseCell(index); renderAll(); checkCompletion(); } } function eraseSelected() { if ( generating || state.paused || state.completed || state.selected < 0 ) { return; } const index = state.selected; if (state.locked[index]) return; const before = createSnapshot(index); state.board[index] = 0; state.notes[index] = []; const after = createSnapshot(index); if (commitAction(index, before, after, "erase")) { renderAll(); } } function togglePencilMode() { if (generating || state.completed) return; state.pencilMode = !state.pencilMode; updatePencilButton(); saveState(); } function useHint() { if (generating || state.paused || state.completed) return; let index = state.selected; if ( index < 0 || state.locked[index] || state.board[index] === state.solution[index] ) { const incorrect = []; const empty = []; for (let cellIndex = 0; cellIndex < 81; cellIndex++) { if (state.locked[cellIndex]) continue; if ( state.board[cellIndex] !== 0 && state.board[cellIndex] !== state.solution[cellIndex] ) { incorrect.push(cellIndex); } else if (state.board[cellIndex] === 0) { empty.push(cellIndex); } } const pool = incorrect.length ? incorrect : empty; if (!pool.length) return; index = pool[Math.floor(Math.random() * pool.length)]; } const before = createSnapshot(index); state.board[index] = state.solution[index]; state.notes[index] = []; state.locked[index] = true; state.hinted[index] = true; state.hintsUsed++; state.selected = index; const after = createSnapshot(index); if (commitAction(index, before, after, "hint")) { renderAll(); pulseCell(index); showToast("One cell has been revealed.", "success"); checkCompletion(); } } function undo() { if ( generating || state.paused || state.completed || !state.history.length ) { return; } const action = state.history.pop(); applySnapshot(action.before); state.redo.push(action); state.selected = action.index; renderAll(); updateUndoRedoButtons(); saveState(); } function redo() { if ( generating || state.paused || state.completed || !state.redo.length ) { return; } const action = state.redo.pop(); applySnapshot(action.after); state.history.push(action); state.selected = action.index; renderAll(); pulseCell(action.index); updateUndoRedoButtons(); saveState(); checkCompletion(); } function restartPuzzle() { if (generating) return; const hasProgress = state.board.some( (value, index) => !state.locked[index] && value !== 0 ) || state.notes.some(notes => notes.length > 0); if ( hasProgress && !window.confirm("Restart this puzzle and clear all progress?") ) { return; } state.board = state.puzzle.slice(); state.notes = Array.from({ length: 81 }, () => []); state.locked = state.puzzle.map(value => value !== 0); state.hinted = Array(81).fill(false); state.selected = -1; state.pencilMode = false; state.mistakes = 0; state.hintsUsed = 0; state.elapsed = 0; state.paused = false; state.completed = false; state.history = []; state.redo = []; hideCompletion(); updatePauseUI(); renderAll(); saveState(); startTimer(); showToast("Puzzle restarted."); } function startNewGame(difficulty = difficultySelect.value, force = false) { if (generating) return; const hasProgress = !state.completed && state.board.some( (value, index) => !state.locked[index] && (value !== 0 || state.notes[index].length > 0) ); if ( !force && hasProgress && !window.confirm("Start a new puzzle and discard current progress?") ) { difficultySelect.value = state.difficulty; return; } generating = true; generationOverlay.classList.add("visible"); hideCompletion(); stopConfetti(); stopTimer(); window.setTimeout(() => { try { const generated = generatePuzzle(difficulty); state = createEmptyState(); state.difficulty = difficulty; state.puzzle = generated.puzzle; state.solution = generated.solution; state.board = generated.puzzle.slice(); state.locked = generated.puzzle.map(value => value !== 0); difficultySelect.value = difficulty; renderAll(); updatePauseUI(); saveState(); startTimer(); } catch (error) { console.error(error); showToast("Puzzle generation failed. Trying again.", "error"); const generated = generatePuzzle("medium"); state = createEmptyState(); state.difficulty = "medium"; state.puzzle = generated.puzzle; state.solution = generated.solution; state.board = generated.puzzle.slice(); state.locked = generated.puzzle.map(value => value !== 0); difficultySelect.value = "medium"; renderAll(); saveState(); startTimer(); } finally { generating = false; generationOverlay.classList.remove("visible"); } }, 60); } function togglePause(forceResume = false) { if (generating || state.completed) return; state.paused = forceResume ? false : !state.paused; updatePauseUI(); saveState(); } function updatePauseUI() { pauseOverlay.classList.toggle("visible", state.paused); pauseButtonLabel.textContent = state.paused ? "Resume" : "Pause"; pauseIcon.innerHTML = state.paused ? '<path d="m8 5 11 7-11 7Z" />' : '<path d="M8 5v14M16 5v14" />'; boardElement.setAttribute("aria-hidden", state.paused ? "true" : "false"); } function getPeerSet(index) { const peers = new Set(); const row = Math.floor(index / 9); const column = index % 9; const boxRow = Math.floor(row / 3) * 3; const boxColumn = Math.floor(column / 3) * 3; for (let i = 0; i < 9; i++) { peers.add(row * 9 + i); peers.add(i * 9 + column); } for (let r = boxRow; r < boxRow + 3; r++) { for (let c = boxColumn; c < boxColumn + 3; c++) { peers.add(r * 9 + c); } } peers.delete(index); return peers; } function findConflicts() { const conflicts = new Set(); function markGroup(indexes) { const positionsByValue = new Map(); for (const index of indexes) { const value = state.board[index]; if (!value) continue; if (!positionsByValue.has(value)) { positionsByValue.set(value, []); } positionsByValue.get(value).push(index); } for (const indexesForValue of positionsByValue.values()) { if (indexesForValue.length > 1) { indexesForValue.forEach(index => conflicts.add(index)); } } } for (let row = 0; row < 9; row++) { markGroup( Array.from({ length: 9 }, (_, column) => row * 9 + column) ); } for (let column = 0; column < 9; column++) { markGroup( Array.from({ length: 9 }, (_, row) => row * 9 + column) ); } for (let boxRow = 0; boxRow < 3; boxRow++) { for (let boxColumn = 0; boxColumn < 3; boxColumn++) { const indexes = []; for (let row = boxRow * 3; row < boxRow * 3 + 3; row++) { for ( let column = boxColumn * 3; column < boxColumn * 3 + 3; column++ ) { indexes.push(row * 9 + column); } } markGroup(indexes); } } return conflicts; } function renderBoard() { const selectedValue = state.selected >= 0 ? state.board[state.selected] : 0; const peers = state.selected >= 0 ? getPeerSet(state.selected) : new Set(); const conflicts = findConflicts(); for (let index = 0; index < 81; index++) { const cell = cells[index]; const value = state.board[index]; const isGiven = state.puzzle[index] !== 0; const isHinted = state.hinted[index]; const isWrong = value !== 0 && !isGiven && !isHinted && value !== state.solution[index]; cell.button.classList.toggle("selected", index === state.selected); cell.button.classList.toggle("peer", peers.has(index)); cell.button.classList.toggle( "same", selectedValue !== 0 && value === selectedValue && index !== state.selected ); cell.button.classList.toggle("given", isGiven); cell.button.classList.toggle("hinted", isHinted); cell.button.classList.toggle("wrong", isWrong); cell.button.classList.toggle("conflict", conflicts.has(index)); cell.value.textContent = value ? String(value) : ""; cell.notes.forEach((noteElement, noteIndex) => { const number = noteIndex + 1; noteElement.textContent = !value && state.notes[index].includes(number) ? String(number) : ""; }); cell.button.setAttribute("aria-label", getCellLabel(index, value)); cell.button.setAttribute( "aria-selected", index === state.selected ? "true" : "false" ); cell.button.disabled = generating; } } function renderNumpad() { const counts = Array(10).fill(0); for (const value of state.board) { if (value) counts[value]++; } for (let number = 1; number <= 9; number++) { const button = numberButtons[number - 1]; const remaining = Math.max(0, 9 - counts[number]); button.querySelector(".remaining").textContent = String(remaining); button.classList.toggle("complete-number", remaining === 0); button.disabled = generating || state.paused || state.completed || remaining === 0; } } function renderStatus() { const difficulty = DIFFICULTY_CONFIG[state.difficulty]; difficultyLabelElement.textContent = difficulty.label; difficultySelect.value = state.difficulty; timerElement.textContent = formatTime(state.elapsed); mistakesElement.textContent = String(state.mistakes); } function renderAll() { renderBoard(); renderNumpad(); renderStatus(); updatePencilButton(); updateUndoRedoButtons(); updateActionButtons(); } function updatePencilButton() { pencilButton.classList.toggle("active", state.pencilMode); pencilButton.setAttribute( "aria-pressed", state.pencilMode ? "true" : "false" ); } function updateUndoRedoButtons() { undoButton.disabled = generating || state.paused || state.completed || state.history.length === 0; redoButton.disabled = generating || state.paused || state.completed || state.redo.length === 0; } function updateActionButtons() { const selectedEditable = state.selected >= 0 && !state.locked[state.selected]; eraseButton.disabled = generating || state.paused || state.completed || !selectedEditable; hintButton.disabled = generating || state.paused || state.completed; pencilButton.disabled = generating || state.completed; pauseButton.disabled = generating || state.completed; } function pulseCell(index) { const button = cells[index]?.button; if (!button) return; button.classList.remove("pop"); void button.offsetWidth; button.classList.add("pop"); window.setTimeout(() => button.classList.remove("pop"), 190); } function checkCompletion() { if (state.completed) return; const complete = state.board.every( (value, index) => value === state.solution[index] ); if (!complete) return; state.completed = true; state.paused = false; saveState(); renderAll(); updatePauseUI(); showCompletion(); } function showCompletion() { completionDifficulty.textContent = DIFFICULTY_CONFIG[state.difficulty].label; completionTime.textContent = formatTime(state.elapsed); completionMistakes.textContent = String(state.mistakes); completionBackdrop.classList.add("visible"); completionBackdrop.setAttribute("aria-hidden", "false"); startConfetti(); } function hideCompletion() { completionBackdrop.classList.remove("visible"); completionBackdrop.setAttribute("aria-hidden", "true"); } function formatTime(totalSeconds) { const safeSeconds = Math.max(0, Math.floor(totalSeconds)); const hours = Math.floor(safeSeconds / 3600); const minutes = Math.floor((safeSeconds % 3600) / 60); const seconds = safeSeconds % 60; if (hours > 0) { return [hours, minutes, seconds] .map(number => String(number).padStart(2, "0")) .join(":"); } return [minutes, seconds] .map(number => String(number).padStart(2, "0")) .join(":"); } function startTimer() { if (timerInterval) return; timerInterval = window.setInterval(() => { if ( generating || state.paused || state.completed || document.hidden ) { return; } state.elapsed++; timerElement.textContent = formatTime(state.elapsed); saveCounter++; if (saveCounter >= 5) { saveCounter = 0; saveState(); } }, 1000); } function stopTimer() { if (!timerInterval) return; window.clearInterval(timerInterval); timerInterval = null; } function serializeAction(action) { return { index: action.index, type: action.type, before: { ...action.before, notes: [...action.before.notes] }, after: { ...action.after, notes: [...action.after.notes] } }; } function saveState() { if (generating || !state.solution.some(Boolean)) return; const savedState = { difficulty: state.difficulty, puzzle: state.puzzle, solution: state.solution, board: state.board, notes: state.notes, locked: state.locked, hinted: state.hinted, selected: state.selected, pencilMode: state.pencilMode, mistakes: state.mistakes, hintsUsed: state.hintsUsed, elapsed: state.elapsed, paused: state.paused, completed: state.completed, history: state.history.slice(-150).map(serializeAction), redo: state.redo.slice(-150).map(serializeAction), savedAt: Date.now() }; try { localStorage.setItem(STORAGE_KEY, JSON.stringify(savedState)); } catch (error) { console.warn("Could not save Sudoku state.", error); } } function isValidNumberArray(array, allowZero = true) { return ( Array.isArray(array) && array.length === 81 && array.every( value => Number.isInteger(value) && value >= (allowZero ? 0 : 1) && value <= 9 ) ); } function validateSnapshot(snapshot) { return ( snapshot && Number.isInteger(snapshot.index) && snapshot.index >= 0 && snapshot.index < 81 && Number.isInteger(snapshot.value) && snapshot.value >= 0 && snapshot.value <= 9 && Array.isArray(snapshot.notes) && snapshot.notes.every( number => Number.isInteger(number) && number >= 1 && number <= 9 ) && typeof snapshot.locked === "boolean" && typeof snapshot.hinted === "boolean" ); } function normalizeActions(actions) { if (!Array.isArray(actions)) return []; return actions .filter( action => action && Number.isInteger(action.index) && validateSnapshot(action.before) && validateSnapshot(action.after) ) .slice(-150) .map(action => ({ index: action.index, type: String(action.type || "edit"), before: { ...action.before, notes: [...new Set(action.before.notes)].sort((a, b) => a - b) }, after: { ...action.after, notes: [...new Set(action.after.notes)].sort((a, b) => a - b) } })); } function loadState() { try { const raw = localStorage.getItem(STORAGE_KEY); if (!raw) return false; const saved = JSON.parse(raw); if ( !saved || !DIFFICULTY_CONFIG[saved.difficulty] || !isValidNumberArray(saved.puzzle) || !isValidNumberArray(saved.solution, false) || !isValidNumberArray(saved.board) || !Array.isArray(saved.notes) || saved.notes.length !== 81 || !Array.isArray(saved.locked) || saved.locked.length !== 81 || !Array.isArray(saved.hinted) || saved.hinted.length !== 81 ) { return false; } state = createEmptyState(); state.difficulty = saved.difficulty; state.puzzle = [...saved.puzzle]; state.solution = [...saved.solution]; state.board = [...saved.board]; state.notes = saved.notes.map(notes => Array.isArray(notes) ? [...new Set(notes)] .filter( number => Number.isInteger(number) && number >= 1 && number <= 9 ) .sort((a, b) => a - b) : [] ); state.locked = saved.locked.map(Boolean); state.hinted = saved.hinted.map(Boolean); state.selected = Number.isInteger(saved.selected) && saved.selected >= -1 && saved.selected < 81 ? saved.selected : -1; state.pencilMode = Boolean(saved.pencilMode); state.mistakes = Math.max(0, Number(saved.mistakes) || 0); state.hintsUsed = Math.max(0, Number(saved.hintsUsed) || 0); state.elapsed = Math.max(0, Number(saved.elapsed) || 0); state.paused = Boolean(saved.paused); state.completed = Boolean(saved.completed); state.history = normalizeActions(saved.history); state.redo = normalizeActions(saved.redo); return true; } catch (error) { console.warn("Could not load Sudoku state.", error); return false; } } function moveSelection(deltaRow, deltaColumn) { if (generating || state.paused || state.completed) return; let index = state.selected; if (index < 0) index = 0; const row = Math.floor(index / 9); const column = index % 9; const nextRow = Math.min(8, Math.max(0, row + deltaRow)); const nextColumn = Math.min(8, Math.max(0, column + deltaColumn)); state.selected = nextRow * 9 + nextColumn; renderBoard(); cells[state.selected].button.focus({ preventScroll: true }); saveState(); } function handleKeyboard(event) { if ( event.target instanceof HTMLSelectElement || event.target instanceof HTMLInputElement || event.target instanceof HTMLTextAreaElement ) { return; } const key = event.key.toLowerCase(); const hasControl = event.ctrlKey || event.metaKey; if (hasControl && key === "z") { event.preventDefault(); event.shiftKey ? redo() : undo(); return; } if (hasControl && key === "y") { event.preventDefault(); redo(); return; } if (key >= "1" && key <= "9") { event.preventDefault(); enterNumber(Number(key)); return; } if (key === "backspace" || key === "delete" || key === "0") { event.preventDefault(); eraseSelected(); return; } if (key === "p" || key === "n") { event.preventDefault(); togglePencilMode(); return; } if (key === "arrowup") { event.preventDefault(); moveSelection(-1, 0); } else if (key === "arrowdown") { event.preventDefault(); moveSelection(1, 0); } else if (key === "arrowleft") { event.preventDefault(); moveSelection(0, -1); } else if (key === "arrowright") { event.preventDefault(); moveSelection(0, 1); } else if (key === "escape" && !state.completed) { event.preventDefault(); togglePause(); } } function showToast(message, type = "") { const toast = document.createElement("div"); toast.className = `toast ${type}`.trim(); toast.textContent = message; toastContainer.appendChild(toast); window.setTimeout(() => { toast.classList.add("leaving"); window.setTimeout(() => toast.remove(), 200); }, 2300); } function resizeConfettiCanvas() { const ratio = Math.min(window.devicePixelRatio || 1, 2); confettiCanvas.width = Math.floor(window.innerWidth * ratio); confettiCanvas.height = Math.floor(window.innerHeight * ratio); confettiCanvas.style.width = `${window.innerWidth}px`; confettiCanvas.style.height = `${window.innerHeight}px`; confettiContext.setTransform(ratio, 0, 0, ratio, 0, 0); } function startConfetti() { stopConfetti(); resizeConfettiCanvas(); const colors = [ "#7c8cff", "#98a4ff", "#6ee7b7", "#f8c76a", "#ff7d91", "#7dd3fc" ]; const particleCount = Math.min( 180, Math.max(90, Math.floor(window.innerWidth / 7)) ); confettiParticles = Array.from({ length: particleCount }, () => ({ x: Math.random() * window.innerWidth, y: -20 - Math.random() * window.innerHeight * 0.7, width: 5 + Math.random() * 6, height: 8 + Math.random() * 9, speedX: -1.8 + Math.random() * 3.6, speedY: 2.2 + Math.random() * 3.8, rotation: Math.random() * Math.PI * 2, rotationSpeed: -0.13 + Math.random() * 0.26, color: colors[Math.floor(Math.random() * colors.length)], wave: Math.random() * Math.PI * 2, opacity: 0.75 + Math.random() * 0.25 })); const startTime = performance.now(); function animate(now) { const elapsed = now - startTime; confettiContext.clearRect( 0, 0, window.innerWidth, window.innerHeight ); for (const particle of confettiParticles) { particle.wave += 0.04; particle.x += particle.speedX + Math.sin(particle.wave) * 0.45; particle.y += particle.speedY; particle.rotation += particle.rotationSpeed; confettiContext.save(); confettiContext.globalAlpha = elapsed > 3500 ? Math.max(0, particle.opacity * (1 - (elapsed - 3500) / 1200)) : particle.opacity; confettiContext.translate(particle.x, particle.y); confettiContext.rotate(particle.rotation); confettiContext.fillStyle = particle.color; confettiContext.fillRect( -particle.width / 2, -particle.height / 2, particle.width, particle.height ); confettiContext.restore(); } confettiParticles = confettiParticles.filter( particle => particle.y < window.innerHeight + 40 ); if (elapsed < 4700 && confettiParticles.length) { confettiFrame = requestAnimationFrame(animate); } else { stopConfetti(); } } confettiFrame = requestAnimationFrame(animate); } function stopConfetti() { if (confettiFrame) { cancelAnimationFrame(confettiFrame); confettiFrame = null; } confettiParticles = []; confettiContext.clearRect( 0, 0, window.innerWidth, window.innerHeight ); } function attachEvents() { newGameButton.addEventListener("click", () => startNewGame(difficultySelect.value) ); restartButton.addEventListener("click", restartPuzzle); pauseButton.addEventListener("click", () => togglePause()); overlayResumeButton.addEventListener("click", () => togglePause(true)); pencilButton.addEventListener("click", togglePencilMode); eraseButton.addEventListener("click", eraseSelected); hintButton.addEventListener("click", useHint); undoButton.addEventListener("click", undo); redoButton.addEventListener("click", redo); playAgainButton.addEventListener("click", () => { hideCompletion(); stopConfetti(); startNewGame(state.difficulty, true); }); completionBackdrop.addEventListener("click", event => { if (event.target === completionBackdrop) { hideCompletion(); stopConfetti(); } }); document.addEventListener("keydown", handleKeyboard); document.addEventListener("visibilitychange", () => { if (document.hidden) saveState(); }); window.addEventListener("beforeunload", saveS