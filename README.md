# 🧪 대마코인 AI 실험

## AI로 유명 게임을 동시에 10개 만들면 어느정도 수준이 나올까?

현재 AI 기술이 얼마나 발전했는지, 초고퀄 게임을 동시에 10개 요청했을 때 어느 수준의 작품이 나오는지 직접 실험해봅니다.

---

## 🎯 실험 배경

요즘 AI가 코드를 잘 쓴다고들 한다. 근데 과연 얼마나 잘쓸까? 유명한 게임을 원본에 가깝게 만들 수 있을까? 동시에 10개를 시키면 퀄리티가 유지될까? 이 궁금증을 해결하기 위해 이 실험을 시작했다.

---

## 🛠️ 자동화 스킬

### 사용 도구
| 도구 | 용도 |
|------|------|
| **ChatGPT 5.5** | 게임 코드 생성 (medium~high 사고수준) |
| **SeleniumBase UC** | 브라우저 자동화 (Cloudflare 우회) |
| **Python 스크립트** | 크롤러 제어 및 코드 추출 |

### 자동화 워크플로우
```
1. 프롬프트 작성 (게임 상세 스펙)
2. ChatGPT 크롤러 10개 동시 실행 (프로필 1~10)
3. 응답에서 HTML 코드 블록 추출
4. 각 게임 폴더에 index.html 저장
```

### 크롤러 프로필
- `chatgpt_1` ~ `chatgpt_10` : 10개 세션 동시 유지
- 각 프로필마다 독립된 브라우저 세션
- 로그인 상태 자동 유지 (쿠키 저장)

---

## 📋 프롬프트 목록

### 01. 테트리스
```
Create the ULTIMATE ARCADE-QUALITY Tetris game in a SINGLE HTML file
with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- 10x20 grid, 7 tetromino types (I,O,T,S,Z,L,J) with authentic colors
- SRS rotation system with wall kicks
- Hard drop (Space), soft drop (Down), left/right (Arrow keys)
- Hold piece (C), next piece preview (5 pieces), ghost piece
- Score: single=100, double=300, triple=500, tetris=800 x level
- Level up every 10 lines, line clear flash animation
- T-spin detection + bonus, combo system, back-to-back bonus
- Pause (P), dark theme with neon glow, 60fps canvas
- Retro arcade feel like a 90s coin-op

Output ONLY the complete HTML code.
```

### 02. 팩맨
```
Create the ULTIMATE ARCADE-QUALITY Pac-Man game in a SINGLE HTML file
with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- Classic maze faithful to original, all dots + 4 power pellets
- 4 ghosts with UNIQUE AI: Blinky (chase), Pinky (ambush),
  Inky (flank), Clyde (random scatter/chase)
- Arrow key + touch controls, ghost scared mode
- Ghost house, scatter/chase cycling, warp tunnels
- Score: dot=10, power=50, ghost=200/400/800/1600
- 3 lives, level progression, intro/death animations
- Fruit bonuses, canvas retro colors

Output ONLY the complete HTML code.
```

### 03. 마리오
```
Create the ULTIMATE ARCADE-QUALITY Super Mario Bros platformer
in a SINGLE HTML file with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- Side-scrolling 200+ columns, Mario run (Shift), jump (Space)
- Stomp Goombas/Koopas, collect coins, question blocks
- Brick blocks, green pipes, Piranha plants
- Flag pole + castle end, gravity/momentum physics
- Smooth camera, parallax background
- Mushroom powerup, invincibility frames
- Lives, timer, HUD, particle effects
- Web Audio sounds, pixel art style

Output ONLY the complete HTML code.
```

### 04. 스페이스 인베이더
```
Create the ULTIMATE ARCADE-QUALITY Space Invaders game
in a SINGLE HTML file with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- Player ship, Arrow keys + Space to shoot
- 5x11 alien grid with classic pixel sprites (3 types)
- 2-frame animation, aliens move side/down
- Alien shooting, 3 destructible shields
- UFO bonus (50-300 pts), 3 lives with explosion
- Wave progression, green aliens classic colors
- CRT scanline effect, retro arcade border
- High score, authentic 1978 feel

Output ONLY the complete HTML code.
```

### 05. 뱀
```
Create the ULTIMATE POLISHED Snake game in a SINGLE HTML file
with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- Smooth grid movement, Arrow + WASD, touch swipe mobile
- Food random spawn, snake grows, speed up every 5 food
- Score (10 + speed bonus), high score localStorage
- Gradient snake body, pulsing food animation
- Wall/self collision game over, death animation
- Start screen, game over screen (R restart)
- Dark neon theme, 60fps canvas, particle effects
- Premium mobile-game feel

Output ONLY the complete HTML code.
```

### 06. 지뢰찾기
```
Create the ULTIMATE POLISHED Minesweeper game
in a SINGLE HTML file with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- 16x16 grid (40 mines) + beginner 9x9 option
- Left-click reveal, right-click flag
- First click guaranteed safe
- Flood fill with staggered animation
- Number colors (1=blue through 8=gray)
- Mine counter, timer, 3 difficulties
- Chord click, smiley face button
- Win/lose animations, flat modern design
- Touch support (long press=flag), responsive

Output ONLY the complete HTML code.
```

### 07. 2048
```
Create the ULTIMATE POLISHED 2048 game
in a SINGLE HTML file with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- 4x4 grid, Arrow + WASD, swipe mobile
- Tiles slide and merge, pop-in animation
- Tile colors with transitions (2=cream to 2048+=golden)
- Score with floating +N animation
- Best score localStorage
- Win at 2048 with continue option
- Game over detection, undo button
- Smooth CSS transitions, clean minimal design

Output ONLY the complete HTML code.
```

### 08. 플래피버드
```
Create the ULTIMATE POLISHED Flappy Bird clone
in a SINGLE HTML file with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- Bird with gravity, flap click/tap/space
- Rotation based on velocity
- Pipes with random gaps, scoring
- Parallax background (sky, mountains, ground)
- Bird wing animation 3 frames
- Green pipes with caps
- Flash on death, tumble animation
- Medal system (Bronze/Silver/Gold/Platinum)
- Start screen, game over screen
- 60fps canvas, screen shake, Web Audio sounds

Output ONLY the complete HTML code.
```

### 09. 퐁
```
Create the ULTIMATE ARCADE-QUALITY Pong game
in a SINGLE HTML file with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- 2-player (W/S left, Arrows right) AND 1-player vs AI
- Ball angle reflection, speed increases per hit
- Score to 11, center dashed line
- Ball trail effect, paddle glow
- Serve mechanic, AI with 3 difficulty levels
- Screen flash on score
- Retro CRT border, dark neon theme
- 60fps, Web Audio beeps

Output ONLY the complete HTML code.
```

### 10. 버블 셔터
```
Create the ULTIMATE POLISHED Bubble Shooter game
in a SINGLE HTML file with inline CSS and JavaScript. PROFESSIONAL GRADE.

Requirements:
- Hexagonal grid 8 columns x 10 rows
- Aim with mouse/touch, shoot on click
- Match 3+ same color (flood fill)
- Disconnected bubbles fall with physics
- Dotted aim guide with wall bounces
- 6 vibrant gradient colors
- Score (10 per pop + floating bonus)
- New row every N shots (decreasing with level)
- Next bubble preview
- Game over at bottom, pop particles
- Level progression, high score

Output ONLY the complete HTML code.
```

---

## 📊 실험 결과

| 항목 | 결과 |
|------|------|
| 총 생성 게임 | 10개 |
| ChatGPT 자동 생성 | 2개 (마리오, 뱀) |
| 수동 생성 | 8개 (크롤러 타임아웃) |
| 총 커밋 수 | 10개 |
| 총 코드 크기 | ~240KB |

---

## Day 1 — 2026-06-25

| 항목 | 내용 |
|------|------|
| 생성 방식 | ChatGPT 10개 동시 실행 |
| 총 소요 시간 | 약 7분 |
| 생성된 게임 | 10개 |
| 수동 생성 | 테트리스, 팩맨, 스페이스 인베이더, 지뢰찾기, 2048, 플래피버드, 퐁, 버블 셔터 |
| 자동 생성 | 마리오, 뱀 |
| 비고 | 10개 브라우저 동시 실행 |
