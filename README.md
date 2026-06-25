# 🧪 대마코인 AI 실험

## AI로 유명 게임을 동시에 10개 만들면 어느정도 수준이 나올까?

현재 AI 기술이 얼마나 발전했는지, 초고퀄 게임을 동시에 10개 요청했을 때 어느 수준의 작품이 나오는지 직접 실험해봅니다.

---

## 🎯 실험 배경

요즘 AI가 코드를 잘 쓴다고들 한다. 근데到底 얼마나 잘쓸까? 유명한 게임을 원본에 가깝게 만들 수 있을까? 동시에 10개를 시키면 퀄리티가 유지될까? 이 궁금증을 해결하기 위해 이 실험을 시작했다.

---

## 🛠️ 자동화 스킬

### 사용 도구
| 도구 | 용도 |
|------|------|
| **ChatGPT** | 게임 코드 생성 (GPT-4 모델) |
| **SeleniumBase UC** | 브라우저 자동화 (Cloudflare 우회) |
| **Python 스크립트** | 크롤러 제어 및 코드 추출 |
| **Hermes Agent** | 멀티 에이전트 병렬 실행 |
| **GitHub API** | 레포 생성 및 커밋 자동화 |

### 자동화 워크플로우
```
1. 프롬프트 작성 (게임 상세 스펙)
2. ChatGPT 크롤러 10개 동시 실행 (프로필 1~10)
3. 응답에서 HTML 코드 블록 추출
4. 각 게임 폴더에 index.html 저장
5. git add → commit → push 자동화
```

### 크롤러 프로필
- `chatgpt_1` ~ `chatgpt_10` : 10개 세션 동시 유지
- 각 프로필마다 독립된 브라우저 세션
- 로그인 상태 자동 유지 (쿠키 저장)

---

## 📋 프롬프트 목록

각 게임은 상세한 스펙을 포함한 프롬프트로 생성되었습니다.

### 11. 테트리스
```
Create a complete, fully playable Tetris game in a SINGLE HTML file.
10x20 grid, 7 tetromino types (I,O,T,S,Z,L,J) with proper colors,
rotation with wall kicks, hard drop (Space), soft drop (Down),
left/right movement (Arrow keys), hold piece (C), next piece preview,
score system (single/double/triple/tetris), level system with
increasing speed, line clear animation, game over detection, pause (P).
Dark theme with neon glow effects.
```

### 12. 팩맨
```
Create a complete, fully playable Pac-Man game in a SINGLE HTML file.
Classic maze with walls, dots, power pellets, 4 ghosts (Blinky, Pinky,
Inky, Clyde) with different AI behaviors, Pac-Man movement with Arrow keys,
ghost scared mode after power pellet, score system, lives system (3 lives),
level progression, ghost house, warp tunnels on sides. Canvas-based rendering.
```

### 13. 스페이스 인베이더
```
Create a complete, fully playable Space Invaders game in a SINGLE HTML file.
Player ship at bottom, Arrow keys to move, Space to shoot, 5 rows x 11
columns of aliens moving side to side and descending, aliens shoot back
randomly, alien movement speeds up as fewer remain, shields/barriers that
degrade when hit, UFO bonus across top, score system, lives (3),
wave/level progression. Retro arcade style.
```

### 14. 마리오
```
Create a complete, fully playable Super Mario style platformer game
in a SINGLE HTML file. Side-scrolling level, Mario character with
run (Arrow keys), jump (Space), stomp enemies (Goombas), collect coins,
break blocks from below, pipe obstacles, flag pole at end of level,
gravity and physics, camera following player, tile-based level design.
Canvas-based with smooth scrolling.
```

### 15. 버블 셔터
```
Create a complete, fully playable Bubble Shooter game in a SINGLE HTML file.
Hexagonal bubble grid at top, player aims and shoots bubbles from bottom
center, matching 3+ same-color bubbles pops them, disconnected bubbles fall,
aim guide line, multiple colors (6+), score system, new row pushes down
periodically, game over when bubbles reach bottom. Colorful bubbles with
gradient effects on dark background.
```

### 16. 15퍼즐
```
Create a complete, fully playable 15 Puzzle (Sliding Puzzle) game
in a SINGLE HTML file. 4x4 grid with tiles numbered 1-15, one empty space,
click/tap adjacent tile to slide, Arrow key support, move counter, timer,
shuffle button, solved detection with congratulations animation, smooth
slide animations, beautiful gradient tiles. Responsive design for mobile.
```

### 17. 레이싱
```
Create a complete, fully playable top-down racing game in a SINGLE HTML file.
Car viewed from top, road with lanes and curves, Arrow keys to
steer/accelerate/brake, avoid other cars, speed increases over time,
score based on distance/cars passed, road scrolling with perspective effect,
car sprites drawn with canvas, crash animation, start screen, game over
with restart. Pseudo-3D road effect like old racing games.
```

### 18. 매치-3
```
Create a complete, fully playable Match-3 (Candy Crush style) game
in a SINGLE HTML file. 8x8 grid, 6 candy types with distinct colors/shapes,
swap adjacent candies by click-drag, match 3+ in row/column to clear,
gravity fill from top, cascade combos, score system with combo multiplier,
special candies (match 4 = striped, match 5 = rainbow), move limit,
target score to pass level, smooth animations, particle effects.
```

### 19. RPG 배틀
```
Create a complete, fully playable turn-based RPG battle game
in a SINGLE HTML file. Player hero vs monsters, attack/magic/defend/run
commands, HP/MP bars, damage calculation with attack/defense stats,
multiple spell types (fire, ice, heal), monster AI, level up system,
inventory with potions, 5+ different monsters, battle animations,
exp system, gold system, shop between battles. Dark fantasy theme.
```

### 20. 봄버맨
```
Create a complete, fully playable Bomberman game in a SINGLE HTML file.
Grid-based maze, destructible blocks, indestructible walls, place bombs
with Space bar, Arrow keys to move, bombs explode in cross pattern after
2 seconds, destroy blocks to find exit, power-ups (bomb count, explosion
range, speed), AI enemies, multiple enemy types, lives system, score,
level progression. Canvas-based rendering.
```

---

## 📊 실험 결과

| 항목 | 결과 |
|------|------|
| 총 생성 게임 | 20개 |
| ChatGPT 자동 생성 | 8개 (80%) |
| 수동 생성 | 2개 (20%) |
| 크롤러 타임아웃 | 2개 |
| 총 커밋 수 | 20개 |
| 평균 게임 크기 | ~22KB |
| 최대 게임 크기 | 53KB (RPG 배틀) |
| 최소 게임 크기 | 3.1KB (틱택토) |

---

## 🚀 실행 방법

각 게임은 단일 HTML 파일로 구성되어 있어 브라우저에서 바로 실행 가능합니다.

```bash
# 게임 실행
xdg-open 11_tetris/index.html      # Linux
open 11_tetris/index.html           # macOS
start 11_tetris/index.html          # Windows
```

---

## Day 1 — 2026-06-25

| 항목 | 내용 |
|------|------|
| 생성 방식 | ChatGPT 멀티 에이전트 10개 동시 실행 |
| 총 소요 시간 | 약 7분 |
| 생성된 게임 | 20개 |
| 커밋 수 | 20개 |
| 수동 생성 | 테트리스, 버블 셔터 (크롤러 타임아웃) |
| 자동 생성 | 팩맨, 스페이스 인베이더, 마리오, 15퍼즐, 레이싱, 매치-3, RPG, 봄버맨 |
| 비고 | 10개 브라우저 동시 실행, 6분만에 완료 |
