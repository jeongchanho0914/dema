# Prompt
Create the ULTIMATE, ARCADE-QUALITY Whack-a-Mole game in a SINGLE HTML file with inline CSS and JavaScript. PROFESSIONAL GRADE. Requirements: 3x3 grid of holes, moles pop up randomly with random duration, click/tap to whack, score per hit (faster mole = more points), miss penalty, 30-second timer, level progression (faster moles, shorter display time), mole with cute animation (pop up, look around, hide), hammer cursor on game area, hit animation with stars, miss animation, combo system for consecutive hits, high score in localStorage, dark theme with wooden board feel, smooth animations, sound effects (Web Audio: bonk, miss). Fun arcade feel. Output ONLY the complete HTML code.

# Answer
<!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8" /> <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" /> <meta name="theme-color" content="#160e0b" /> <title>Whack-a-Mole Arcade</title> <style> :root { --bg-1: #0d0908; --bg-2: #1b100c; --wood-dark: #3b1f14; --wood: #6b3821; --wood-light: #9c5a32; --gold: #ffd45a; --orange: #ff8f3f; --red: #ff4d52; --green: #65e692; --cream: #fff1c9; --ink: #20130d; --panel: rgba(20, 12, 9, 0.9); --shadow: rgba(0, 0, 0, 0.55); } * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; user-select: none; } html, body { width: 100%; min-height: 100%; margin: 0; overflow-x: hidden; } body { display: flex; align-items: center; justify-content: center; padding: 18px; color: var(--cream); font-family: Inter, ui-rounded, "Trebuchet MS", Arial, sans-serif; background: radial-gradient(circle at 50% 15%, rgba(255, 137, 61, 0.13), transparent 34%), radial-gradient(circle at 15% 70%, rgba(164, 75, 36, 0.12), transparent 30%), linear-gradient(145deg, var(--bg-2), var(--bg-1) 65%); } body::before { position: fixed; inset: 0; z-index: -1; content: ""; pointer-events: none; opacity: 0.12; background-image: repeating-linear-gradient( 0deg, transparent 0, transparent 4px, rgba(255, 255, 255, 0.05) 5px ); } button { font: inherit; } .game-shell { position: relative; width: min(100%, 900px); padding: 14px; border: 2px solid rgba(255, 205, 113, 0.2); border-radius: 30px; background: linear-gradient(145deg, rgba(69, 32, 19, 0.95), rgba(31, 17, 12, 0.98)); box-shadow: 0 28px 70px rgba(0, 0, 0, 0.55), inset 0 1px 0 rgba(255, 255, 255, 0.12); } .inner-frame { position: relative; overflow: hidden; padding: clamp(14px, 3vw, 28px); border: 3px solid #2b160f; border-radius: 20px; background: repeating-linear-gradient( 3deg, transparent 0, transparent 15px, rgba(49, 19, 8, 0.12) 16px, rgba(255, 215, 143, 0.04) 18px ), linear-gradient(110deg, #7a3e23, #985833 45%, #6b331e); box-shadow: inset 0 0 0 2px rgba(255, 209, 125, 0.15), inset 0 0 35px rgba(30, 8, 2, 0.55); } .wood-knot { position: absolute; width: 110px; height: 30px; border: 4px solid rgba(44, 17, 7, 0.15); border-radius: 50%; pointer-events: none; transform: rotate(-8deg); } .wood-knot.one { top: 15%; left: -30px; } .wood-knot.two { right: -40px; bottom: 17%; transform: rotate(13deg); } .title-row { position: relative; z-index: 5; display: flex; align-items: center; justify-content: space-between; gap: 18px; margin-bottom: 18px; } .title { margin: 0; color: var(--gold); font-size: clamp(1.65rem, 5vw, 3.2rem); font-weight: 1000; line-height: 0.92; letter-spacing: -0.055em; text-transform: uppercase; text-shadow: 0 4px 0 #8b341d, 0 7px 10px rgba(0, 0, 0, 0.4); } .title span { display: block; margin-top: 8px; color: #fff4c9; font-size: 0.45em; letter-spacing: 0.18em; text-shadow: 0 3px 0 #5b2818; } .sound-button { display: grid; flex: 0 0 auto; width: 48px; height: 48px; place-items: center; border: 2px solid rgba(255, 213, 119, 0.4); border-radius: 15px; color: var(--gold); font-size: 1.25rem; cursor: pointer; background: rgba(33, 17, 11, 0.78); box-shadow: 0 6px 0 #2d140d, inset 0 1px 0 rgba(255, 255, 255, 0.12); transition: transform 100ms ease, filter 100ms ease; } .sound-button:hover { filter: brightness(1.15); transform: translateY(-1px); } .sound-button:active { box-shadow: 0 2px 0 #2d140d; transform: translateY(4px); } .hud { position: relative; z-index: 5; display: grid; grid-template-columns: repeat(5, minmax(0, 1fr)); gap: 10px; margin-bottom: 18px; } .hud-card { min-width: 0; padding: 9px 8px 10px; border: 2px solid rgba(255, 210, 124, 0.2); border-radius: 15px; text-align: center; background: linear-gradient(180deg, rgba(39, 20, 13, 0.93), rgba(23, 12, 9, 0.93)); box-shadow: 0 6px 13px rgba(0, 0, 0, 0.25), inset 0 1px 0 rgba(255, 255, 255, 0.08); } .hud-label { display: block; overflow: hidden; margin-bottom: 3px; color: #d9b58e; font-size: clamp(0.55rem, 1.8vw, 0.72rem); font-weight: 900; letter-spacing: 0.08em; text-overflow: ellipsis; text-transform: uppercase; white-space: nowrap; } .hud-value { display: block; color: white; font-size: clamp(1rem, 3.2vw, 1.55rem); font-variant-numeric: tabular-nums; font-weight: 1000; line-height: 1; text-shadow: 0 2px 0 rgba(0, 0, 0, 0.4); } .hud-card.timer-card .hud-value { color: var(--gold); } .hud-card.combo-card.active { animation: comboPulse 380ms ease; border-color: rgba(255, 215, 94, 0.75); box-shadow: 0 0 18px rgba(255, 194, 67, 0.32), inset 0 1px 0 rgba(255, 255, 255, 0.14); } .progress-wrap { position: relative; z-index: 5; overflow: hidden; height: 12px; margin: -5px 0 18px; border: 2px solid rgba(35, 15, 9, 0.8); border-radius: 999px; background: rgba(24, 11, 7, 0.65); box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.45); } .progress-bar { width: 0; height: 100%; border-radius: inherit; background: linear-gradient(90deg, #ff743f, #ffd657 65%, #fff0a4); box-shadow: 0 0 12px rgba(255, 201, 69, 0.5); transition: width 250ms ease; } .board { position: relative; z-index: 3; display: grid; grid-template-columns: repeat(3, 1fr); gap: clamp(10px, 2.2vw, 20px); width: min(100%, 650px); margin: 0 auto; padding: clamp(12px, 2.5vw, 24px); border: 3px solid rgba(50, 20, 9, 0.88); border-radius: 25px; cursor: none; touch-action: manipulation; background: repeating-linear-gradient( 90deg, transparent 0, transparent 90px, rgba(50, 18, 6, 0.12) 92px, rgba(255, 228, 174, 0.04) 94px ), linear-gradient(145deg, #8d4b29, #5a2918); box-shadow: 0 16px 24px rgba(0, 0, 0, 0.34), inset 0 2px 0 rgba(255, 229, 178, 0.14), inset 0 -10px 25px rgba(42, 13, 5, 0.3); } .board.disabled { pointer-events: none; } .hole { position: relative; overflow: hidden; aspect-ratio: 1.18 / 1; border-radius: 45% 45% 48% 48%; isolation: isolate; } .hole::before { position: absolute; right: 5%; bottom: 3%; left: 5%; z-index: 2; height: 40%; content: ""; border-radius: 50%; background: radial-gradient(ellipse at 50% 38%, #050302 0 35%, #120906 54%, #35180f 72%, #9e5b36 75%); box-shadow: 0 10px 12px rgba(0, 0, 0, 0.45), inset 0 8px 10px rgba(0, 0, 0, 0.85); } .hole::after { position: absolute; right: 2%; bottom: 1%; left: 2%; z-index: 8; height: 22%; content: ""; border-radius: 48% 48% 52% 52%; background: linear-gradient( 180deg, #a9623a 0%, #7d3f25 28%, #512515 74%, #2d140d 100% ); box-shadow: inset 0 2px 1px rgba(255, 223, 165, 0.22), 0 -2px 0 rgba(53, 22, 12, 0.85); } .mole-wrap { position: absolute; right: 13%; bottom: -72%; left: 13%; z-index: 6; height: 90%; pointer-events: none; transform-origin: bottom center; } .hole.active .mole-wrap { pointer-events: auto; animation: popUp 190ms cubic-bezier(0.15, 0.85, 0.2, 1.16) forwards; } .hole.hiding .mole-wrap { animation: hideDown 170ms ease-in forwards; } .hole.hit .mole-wrap { animation: bonked 300ms ease forwards; } .mole { position: relative; width: 100%; height: 100%; border: 3px solid #3b1b10; border-radius: 48% 48% 38% 38%; background: radial-gradient(circle at 32% 22%, rgba(255, 255, 255, 0.2), transparent 12%), linear-gradient(145deg, #c77a42, #8b4829 60%, #63301f); box-shadow: inset 0 3px 0 rgba(255, 230, 190, 0.18), 0 8px 10px rgba(0, 0, 0, 0.3); } .mole::before, .mole::after { position: absolute; top: 11%; z-index: -1; width: 31%; aspect-ratio: 1; content: ""; border: 3px solid #3b1b10; border-radius: 50%; background: radial-gradient(circle, #d58a50 0 45%, #874425 48%); } .mole::before { left: -8%; } .mole::after { right: -8%; } .mole-face { position: absolute; inset: 0; } .eye { position: absolute; top: 32%; width: 14%; aspect-ratio: 0.75; overflow: hidden; border-radius: 50%; background: #f9f1d9; box-shadow: inset 0 -2px 0 rgba(0, 0, 0, 0.15); } .eye.left { left: 25%; } .eye.right { right: 25%; } .pupil { position: absolute; top: 30%; left: 34%; width: 42%; aspect-ratio: 1; border-radius: 50%; background: #20110b; transition: transform 100ms ease; } .hole.active:not(.hit) .pupil { animation: lookAround 1s ease-in-out infinite alternate; } .muzzle { position: absolute; top: 48%; left: 50%; width: 53%; height: 36%; border-radius: 50%; background: #e7a66c; box-shadow: inset 0 -4px 0 rgba(126, 55, 27, 0.14), 0 1px 0 rgba(255, 244, 217, 0.25); transform: translateX(-50%); } .nose { position: absolute; top: 47%; left: 50%; width: 19%; aspect-ratio: 1.15; border-radius: 50% 50% 45% 45%; background: #482118; box-shadow: inset 0 2px 0 rgba(255, 255, 255, 0.13); transform: translateX(-50%); } .mouth { position: absolute; top: 65%; left: 50%; width: 23%; height: 10%; border-bottom: 3px solid #6d3020; border-radius: 50%; transform: translateX(-50%); } .tooth { position: absolute; top: 73%; left: 50%; width: 12%; height: 12%; border: 1px solid #c9b998; border-radius: 1px 1px 4px 4px; background: #fff9e7; transform: translateX(-50%); } .hole.hit .mole { filter: saturate(0.75) brightness(1.1); } .hole.hit .eye { height: 3px; margin-top: 7px; background: #3e1c11; transform: rotate(10deg); } .hole.hit .eye.right { transform: rotate(-10deg); } .hole.hit .pupil { display: none; } .hole.hit .mouth { top: 69%; width: 20%; height: 13%; border: 0; border-radius: 50%; background: #542218; } .hit-stars { position: absolute; top: 0; left: 50%; z-index: 20; width: 1px; height: 1px; pointer-events: none; } .star { position: absolute; opacity: 0; color: #ffe05e; font-size: clamp(16px, 4vw, 28px); font-weight: 1000; text-shadow: 0 2px 0 #9e4c18, 0 0 10px rgba(255, 221, 81, 0.8); } .hole.hit .star { animation: starBurst 430ms ease-out forwards; } .star:nth-child(1) { --x: -65px; --y: -28px; animation-delay: 0ms !important; } .star:nth-child(2) { --x: -22px; --y: -62px; animation-delay: 30ms !important; } .star:nth-child(3) { --x: 25px; --y: -58px; animation-delay: 55ms !important; } .star:nth-child(4) { --x: 62px; --y: -25px; animation-delay: 80ms !important; } .point-popup { position: absolute; top: 25%; left: 50%; z-index: 30; color: white; font-size: clamp(1rem, 4vw, 1.65rem); font-weight: 1000; pointer-events: none; text-shadow: 0 3px 0 #893619, 0 0 12px rgba(255, 213, 92, 0.85); transform: translateX(-50%); animation: pointFloat 650ms ease-out forwards; } .miss-mark { position: absolute; z-index: 50; color: var(--red); font-size: clamp(1rem, 4vw, 1.7rem); font-weight: 1000; pointer-events: none; text-shadow: 0 3px 0 #6e1719, 0 0 12px rgba(255, 54, 70, 0.5); transform: translate(-50%, -50%); animation: missBurst 600ms ease-out forwards; } .hammer { position: fixed; z-index: 999; width: 78px; height: 78px; pointer-events: none; opacity: 0; filter: drop-shadow(0 8px 4px rgba(0, 0, 0, 0.42)); transform: translate(-20%, -75%) rotate(-38deg); transform-origin: 28% 72%; transition: opacity 120ms ease; } .hammer.visible { opacity: 1; } .hammer.swing { animation: hammerSwing 180ms cubic-bezier(0.4, 0, 0.7, 1); } .hammer-head { position: absolute; top: 10px; left: 12px; width: 49px; height: 29px; border: 3px solid #321910; border-radius: 8px; background: linear-gradient(180deg, #f0b05f, #b86732 58%, #8c4528); box-shadow: inset 0 3px 0 rgba(255, 236, 198, 0.34), inset 0 -4px 0 rgba(74, 29, 15, 0.25); } .hammer-head::before { position: absolute; top: 3px; left: -12px; width: 16px; height: 17px; content: ""; border: 3px solid #321910; border-right: 0; border-radius: 8px 0 0 8px; background: #d38645; } .hammer-handle { position: absolute; top: 33px; left: 34px; width: 13px; height: 48px; border: 3px solid #321910; border-radius: 5px 5px 9px 9px; background: linear-gradient(90deg, #71371e, #d37b3e 45%, #7c3c21); transform: rotate(-6deg); transform-origin: top; } .start-overlay, .game-over-overlay { position: absolute; inset: 0; z-index: 200; display: flex; align-items: center; justify-content: center; padding: 18px; border-radius: 18px; background: radial-gradient(circle at 50% 30%, rgba(130, 55, 27, 0.32), transparent 42%), rgba(12, 7, 5, 0.82); backdrop-filter: blur(5px); transition: opacity 250ms ease, visibility 250ms ease; } .start-overlay.hidden, .game-over-overlay.hidden { visibility: hidden; opacity: 0; pointer-events: none; } .modal { width: min(100%, 480px); padding: clamp(22px, 5vw, 38px); border: 3px solid #522615; border-radius: 25px; text-align: center; background: repeating-linear-gradient( 4deg, transparent 0 14px, rgba(83, 33, 13, 0.08) 15px 17px ), linear-gradient(145deg, #8c4a29, #512515); box-shadow: 0 24px 55px rgba(0, 0, 0, 0.55), inset 0 2px 0 rgba(255, 229, 180, 0.18); } .modal-icon { display: inline-grid; width: 86px; height: 86px; margin-bottom: 14px; place-items: center; border: 3px solid #502413; border-radius: 50%; font-size: 3.5rem; background: #d48043; box-shadow: 0 7px 0 #3d1b10, inset 0 3px 0 rgba(255, 255, 255, 0.2); } .modal h2 { margin: 0 0 10px; color: var(--gold); font-size: clamp(2rem, 8vw, 3.4rem); font-weight: 1000; letter-spacing: -0.055em; line-height: 0.95; text-shadow: 0 4px 0 #682717; } .modal p { margin: 10px auto 20px; max-width: 370px; color: #f8dcb9; font-weight: 700; line-height: 1.5; } .tips { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin: 18px 0 23px; } .tip { padding: 10px 5px; border: 1px solid rgba(255, 222, 157, 0.18); border-radius: 11px; color: #f6cfa3; font-size: 0.72rem; font-weight: 900; background: rgba(36, 15, 9, 0.4); } .tip b { display: block; margin-bottom: 3px; color: white; font-size: 1rem; } .arcade-button { min-width: 200px; padding: 14px 28px; border: 3px solid #5e2917; border-radius: 15px; color: #44200f; font-size: 1rem; font-weight: 1000; letter-spacing: 0.06em; text-transform: uppercase; cursor: pointer; background: linear-gradient(180deg, #ffe97d, #ffbe3e); box-shadow: 0 7px 0 #8d371b, 0 11px 18px rgba(0, 0, 0, 0.3), inset 0 2px 0 rgba(255, 255, 255, 0.55); transition: transform 100ms ease, filter 100ms ease; } .arcade-button:hover { filter: brightness(1.07); transform: translateY(-2px); } .arcade-button:active { box-shadow: 0 2px 0 #8d371b, 0 5px 10px rgba(0, 0, 0, 0.25); transform: translateY(5px); } .results { display: grid; grid-template-columns: repeat(2, 1fr); gap: 9px; margin: 20px 0 23px; } .result-item { padding: 12px; border: 2px solid rgba(255, 216, 138, 0.16); border-radius: 12px; background: rgba(31, 13, 8, 0.45); } .result-item span { display: block; color: #d3a478; font-size: 0.67rem; font-weight: 900; letter-spacing: 0.08em; text-transform: uppercase; } .result-item strong { display: block; margin-top: 4px; color: white; font-size: 1.45rem; } .new-record { display: none; margin: -8px 0 14px; color: #fff0a4; font-weight: 1000; animation: recordGlow 700ms ease-in-out infinite alternate; } .new-record.show { display: block; } .countdown { position: absolute; inset: 0; z-index: 150; display: grid; visibility: hidden; place-items: center; color: white; font-size: clamp(5rem, 22vw, 10rem); font-weight: 1000; pointer-events: none; opacity: 0; text-shadow: 0 8px 0 #7b2e18, 0 0 40px rgba(255, 197, 75, 0.7); } .countdown.show { visibility: visible; opacity: 1; animation: countdownPop 700ms ease; } .level-banner { position: absolute; top: 42%; left: 50%; z-index: 120; visibility: hidden; padding: 10px 26px; border: 3px solid #602b17; border-radius: 15px; color: #4d2311; font-size: clamp(1.3rem, 6vw, 2.3rem); font-weight: 1000; pointer-events: none; opacity: 0; white-space: nowrap; background: linear-gradient(180deg, #ffed8b, #ffad32); box-shadow: 0 7px 0 #7b3018, 0 12px 22px rgba(0, 0, 0, 0.3); transform: translate(-50%, -50%) scale(0.55) rotate(-4deg); } .level-banner.show { visibility: visible; animation: levelBanner 1000ms ease forwards; } .screen-shake { animation: screenShake 240ms linear; } .timer-danger { color: var(--red) !important; animation: timerDanger 500ms ease-in-out infinite alternate; } @keyframes popUp { 0% { bottom: -72%; transform: scaleY(0.86); } 70% { bottom: 12%; transform: scaleY(1.04); } 100% { bottom: 8%; transform: scaleY(1); } } @keyframes hideDown { from { bottom: 8%; transform: scaleY(1); } to { bottom: -75%; transform: scaleY(0.86); } } @keyframes bonked { 0% { bottom: 8%; transform: scale(1); } 30% { bottom: 2%; transform: scale(1.12, 0.76) rotate(-4deg); } 100% { bottom: -75%; transform: scale(0.85, 0.68) rotate(5deg); } } @keyframes lookAround { 0%, 20% { transform: translateX(-35%); } 45%, 60% { transform: translateX(0); } 80%, 100% { transform: translateX(35%); } } @keyframes starBurst { 0% { opacity: 0; transform: translate(-50%, 25px) scale(0) rotate(0deg); } 28% { opacity: 1; } 100% { opacity: 0; transform: translate(calc(-50% + var(--x)), var(--y)) scale(1.2) rotate(145deg); } } @keyframes pointFloat { 0% { opacity: 0; transform: translate(-50%, 8px) scale(0.6); } 25% { opacity: 1; transform: translate(-50%, 0) scale(1.18); } 100% { opacity: 0; transform: translate(-50%, -48px) scale(0.9); } } @keyframes missBurst { 0% { opacity: 0; transform: translate(-50%, -50%) scale(0.4) rotate(-12deg); } 25% { opacity: 1; transform: translate(-50%, -50%) scale(1.25) rotate(4deg); } 100% { opacity: 0; transform: translate(-50%, -90%) scale(0.9) rotate(-4deg); } } @keyframes hammerSwing { 0% { transform: translate(-20%, -75%) rotate(-38deg); } 48% { transform: translate(-20%, -75%) rotate(20deg) scale(0.95); } 100% { transform: translate(-20%, -75%) rotate(-38deg); } } @keyframes comboPulse { 0% { transform: scale(1); } 45% { transform: scale(1.12) rotate(-2deg); } 100% { transform: scale(1); } } @keyframes screenShake { 0%, 100% { transform: translate(0); } 20% { transform: translate(-6px, 2px); } 40% { transform: translate(5px, -3px); } 60% { transform: translate(-3px, 4px); } 80% { transform: translate(4px, -1px); } } @keyframes countdownPop { 0% { opacity: 0; transform: scale(1.7); } 30% { opacity: 1; transform: scale(0.88); } 60% { transform: scale(1); } 100% { opacity: 0; transform: scale(0.7); } } @keyframes levelBanner { 0% { visibility: visible; opacity: 0; transform: translate(-50%, -50%) scale(0.55) rotate(-8deg); } 18% { opacity: 1; transform: translate(-50%, -50%) scale(1.12) rotate(2deg); } 30%, 72% { opacity: 1; transform: translate(-50%, -50%) scale(1) rotate(-1deg); } 100% { visibility: hidden; opacity: 0; transform: translate(-50%, -65%) scale(0.9); } } @keyframes timerDanger { from { text-shadow: 0 0 4px rgba(255, 62, 75, 0.2); } to { text-shadow: 0 0 15px rgba(255, 62, 75, 0.8); } } @keyframes recordGlow { from { text-shadow: 0 0 4px rgba(255, 232, 130, 0.4); } to { text-shadow: 0 0 17px rgba(255, 232, 130, 1); } } @media (max-width: 640px) { body { align-items: flex-start; padding: 8px; } .game-shell { padding: 7px; border-radius: 21px; } .inner-frame { border-radius: 15px; } .title-row { margin-bottom: 13px; } .hud { gap: 5px; margin-bottom: 13px; } .hud-card { padding: 7px 3px 8px; border-radius: 10px; } .progress-wrap { margin-bottom: 12px; } .board { gap: 7px; padding: 9px; border-radius: 18px; } .tips { gap: 5px; } .tip { font-size: 0.61rem; } .hammer { display: none; } } @media (max-height: 720px) and (min-width: 650px) { body { align-items: flex-start; padding: 8px; } .game-shell { max-width: 760px; } .inner-frame { padding: 12px 18px; } .title { font-size: 2rem; } .title-row, .hud, .progress-wrap { margin-bottom: 9px; } .board { width: min(100%, 500px); padding: 10px; gap: 8px; } } </style> </head> <body> <main class="game-shell" id="gameShell"> <section class="inner-frame"> <div class="wood-knot one"></div> <div class="wood-knot two"></div>
  <header class="title-row">
    <h1 class="title">
      Whack-a-Mole
      <span>Arcade Challenge</span>
    </h1>

    <button
      class="sound-button"
      id="soundButton"
      type="button"
      aria-label="Toggle sound"
      title="Toggle sound"
    >
      🔊
    </button>
  </header>

  <section class="hud" aria-label="Game statistics">
    <div class="hud-card">
      <span class="hud-label">Score</span>
      <strong class="hud-value" id="scoreValue">0</strong>
    </div>

    <div class="hud-card">
      <span class="hud-label">Best</span>
      <strong class="hud-value" id="bestValue">0</strong>
    </div>

    <div class="hud-card timer-card">
      <span class="hud-label">Time</span>
      <strong class="hud-value" id="timerValue">30.0</strong>
    </div>

    <div class="hud-card">
      <span class="hud-label">Level</span>
      <strong class="hud-value" id="levelValue">1</strong>
    </div>

    <div class="hud-card combo-card" id="comboCard">
      <span class="hud-label">Combo</span>
      <strong class="hud-value" id="comboValue">×0</strong>
    </div>
  </section>

  <div class="progress-wrap" aria-hidden="true">
    <div class="progress-bar" id="progressBar"></div>
  </div>

  <section class="board disabled" id="board" aria-label="Whack-a-mole board">
    <div class="hole" data-index="0"></div>
    <div class="hole" data-index="1"></div>
    <div class="hole" data-index="2"></div>
    <div class="hole" data-index="3"></div>
    <div class="hole" data-index="4"></div>
    <div class="hole" data-index="5"></div>
    <div class="hole" data-index="6"></div>
    <div class="hole" data-index="7"></div>
    <div class="hole" data-index="8"></div>
  </section>

  <div class="countdown" id="countdown">3</div>
  <div class="level-banner" id="levelBanner">LEVEL 2</div>

  <section class="start-overlay" id="startOverlay">
    <div class="modal">
      <div class="modal-icon" aria-hidden="true">🔨</div>
      <h2>Ready to Whack?</h2>
      <p>
        Smash the moles before they hide. Faster moles award more points,
        but every missed swing costs you!
      </p>

      <div class="tips">
        <div class="tip">
          <b>⚡ Speed</b>
          Fast = More
        </div>
        <div class="tip">
          <b>🔥 Combo</b>
          Chain Hits
        </div>
        <div class="tip">
          <b>⏱ 30 Sec</b>
          Beat Best
        </div>
      </div>

      <button class="arcade-button" id="startButton" type="button">
        Start Game
      </button>
    </div>
  </section>

  <section class="game-over-overlay hidden" id="gameOverOverlay">
    <div class="modal">
      <div class="modal-icon" aria-hidden="true">🏆</div>
      <h2>Time's Up!</h2>
      <p id="gameOverMessage">Great whacking!</p>

      <div class="new-record" id="newRecord">★ NEW HIGH SCORE ★</div>

      <div class="results">
        <div class="result-item">
          <span>Final Score</span>
          <strong id="finalScore">0</strong>
        </div>
        <div class="result-item">
          <span>High Score</span>
          <strong id="finalBest">0</strong>
        </div>
        <div class="result-item">
          <span>Moles Hit</span>
          <strong id="finalHits">0</strong>
        </div>
        <div class="result-item">
          <span>Best Combo</span>
          <strong id="finalCombo">×0</strong>
        </div>
      </div>

      <button class="arcade-button" id="restartButton" type="button">
        Play Again
      </button>
    </div>
  </section>
</section>
</main> <div class="hammer" id="hammer" aria-hidden="true"> <div class="hammer-head"></div> <div class="hammer-handle"></div> </div> <script> (() => { "use strict"; const GAME_DURATION = 30; const STORAGE_KEY = "ultimateWhackAMoleHighScore"; const SOUND_KEY = "ultimateWhackAMoleSound"; const board = document.getElementById("board"); const gameShell = document.getElementById("gameShell"); const holes = [...document.querySelectorAll(".hole")]; const scoreValue = document.getElementById("scoreValue"); const bestValue = document.getElementById("bestValue"); const timerValue = document.getElementById("timerValue"); const levelValue = document.getElementById("levelValue"); const comboValue = document.getElementById("comboValue"); const comboCard = document.getElementById("comboCard"); const progressBar = document.getElementById("progressBar"); const startOverlay = document.getElementById("startOverlay"); const gameOverOverlay = document.getElementById("gameOverOverlay"); const startButton = document.getElementById("startButton"); const restartButton = document.getElementByI
