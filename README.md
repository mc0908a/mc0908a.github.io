# mc0908a.github.io

El trompo


<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>El Trompo — Al Pastor Taco Stand</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&family=VT323:wght@400&display=swap');

:root {
–bg: #1a0a00;
–counter: #3d1f00;
–orange: #ff6b00;
–red: #c0392b;
–yellow: #f39c12;
–cream: #fdf6e3;
–green: #27ae60;
–dark: #0d0500;
–meat: #c0392b;
–meat2: #e74c3c;
–tortilla: #f0d090;
–shadow: #7a3500;
}

- { margin: 0; padding: 0; box-sizing: border-box; image-rendering: pixelated; }

body {
background: var(–bg);
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
min-height: 100vh;
font-family: ‘Press Start 2P’, monospace;
overflow: hidden;
}

#game-wrapper {
position: relative;
width: 480px;
max-width: 100vw;
}

/* TITLE SCREEN */
#title-screen {
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
background: var(–dark);
border: 4px solid var(–orange);
width: 480px;
height: 560px;
position: relative;
overflow: hidden;
}

#title-screen::before {
content: ‘’;
position: absolute;
inset: 0;
background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(255,107,0,0.03) 3px, rgba(255,107,0,0.03) 4px);
pointer-events: none;
}

.title-logo {
text-align: center;
margin-bottom: 32px;
}

.title-logo .line1 {
font-family: ‘Press Start 2P’, monospace;
font-size: 11px;
color: var(–yellow);
letter-spacing: 4px;
text-shadow: 2px 2px var(–red);
margin-bottom: 8px;
display: block;
}

.title-logo .line2 {
font-family: ‘Press Start 2P’, monospace;
font-size: 22px;
color: var(–orange);
text-shadow: 3px 3px #7a1500, 0 0 20px rgba(255,107,0,0.5);
display: block;
line-height: 1.5;
}

.title-trompo-preview {
margin: 16px 0 28px;
}

.pixel-btn {
font-family: ‘Press Start 2P’, monospace;
font-size: 10px;
background: var(–orange);
color: var(–dark);
border: none;
padding: 12px 24px;
cursor: pointer;
text-transform: uppercase;
letter-spacing: 2px;
box-shadow: 4px 4px 0 var(–red);
transition: transform 0.05s, box-shadow 0.05s;
margin: 8px;
}

.pixel-btn:hover { background: var(–yellow); }
.pixel-btn:active { transform: translate(2px,2px); box-shadow: 2px 2px 0 var(–red); }

.pixel-btn.secondary {
background: transparent;
color: var(–orange);
border: 2px solid var(–orange);
box-shadow: 4px 4px 0 var(–shadow);
font-size: 8px;
}

/* GAME SCREEN */
#game-screen {
display: none;
flex-direction: column;
width: 480px;
background: var(–dark);
border: 4px solid var(–orange);
position: relative;
overflow: hidden;
}

#game-screen::before {
content: ‘’;
position: absolute;
inset: 0;
background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(255,107,0,0.02) 3px, rgba(255,107,0,0.02) 4px);
pointer-events: none;
z-index: 100;
}

/* HUD */
#hud {
background: var(–counter);
border-bottom: 4px solid var(–orange);
padding: 10px 16px;
display: flex;
justify-content: space-between;
align-items: center;
z-index: 10;
}

.hud-item { display: flex; flex-direction: column; align-items: center; gap: 4px; }
.hud-label { font-size: 6px; color: var(–yellow); letter-spacing: 1px; }
.hud-value { font-size: 14px; color: var(–cream); text-shadow: 2px 2px var(–orange); }

/* TIMER BAR */
#timer-container {
background: var(–counter);
border-bottom: 4px solid var(–shadow);
padding: 6px 16px;
display: flex;
align-items: center;
gap: 10px;
}

.timer-label { font-size: 6px; color: var(–yellow); white-space: nowrap; }
#timer-bar-bg {
flex: 1;
height: 12px;
background: #111;
border: 2px solid var(–shadow);
position: relative;
overflow: hidden;
}
#timer-bar-fill {
height: 100%;
background: var(–green);
transition: width 0.1s linear, background 0.3s;
width: 100%;
}

/* SCENE */
#scene {
position: relative;
height: 340px;
background: linear-gradient(180deg, #1a0800 0%, #2d1200 60%, #3d1f00 100%);
overflow: hidden;
}

/* Ambient light on floor */
#scene::after {
content: ‘’;
position: absolute;
bottom: 0; left: 0; right: 0;
height: 60px;
background: linear-gradient(0deg, rgba(255,107,0,0.08), transparent);
pointer-events: none;
}

/* COUNTER */
#counter-surface {
position: absolute;
bottom: 0; left: 0; right: 0;
height: 64px;
background: var(–counter);
border-top: 4px solid var(–shadow);
}

#counter-surface::before {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0;
height: 4px;
background: repeating-linear-gradient(90deg, var(–orange) 0px, var(–orange) 8px, var(–shadow) 8px, var(–shadow) 16px);
}

/* TROMPO */
#trompo-wrap {
position: absolute;
right: 60px;
top: 30px;
cursor: pointer;
user-select: none;
}

#trompo-wrap:hover canvas { filter: brightness(1.2); }
#trompo-wrap.cutting { animation: trompoShake 0.15s ease-in-out; }

@keyframes trompoShake {
0%,100% { transform: translateX(0); }
25% { transform: translateX(-3px); }
75% { transform: translateX(3px); }
}

/* TACO PLATE */
#taco-wrap {
position: absolute;
left: 40px;
bottom: 56px;
}

/* CHEF */
#knife-wrap {
position: absolute;
right: 120px;
bottom: 60px;
pointer-events: none;
transform-origin: center bottom;
}

#knife-wrap.slashing {
animation: chefSlash 0.22s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

@keyframes chefSlash {
0%   { transform: translateX(0px) rotate(0deg); }
30%  { transform: translateX(18px) rotate(8deg); }
55%  { transform: translateX(22px) rotate(12deg); }
100% { transform: translateX(0px) rotate(0deg); }
}

/* MEAT CHUNK flying animation */
.meat-chunk {
position: absolute;
pointer-events: none;
z-index: 50;
animation: meatFly 0.55s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
}

@keyframes meatFly {
0% { transform: translate(0, 0) rotate(0deg); opacity: 1; }
60% { opacity: 1; }
100% { transform: translate(var(–tx), var(–ty)) rotate(var(–tr)); opacity: 0; }
}

/* SCORE POP */
.score-pop {
position: absolute;
font-family: ‘Press Start 2P’, monospace;
font-size: 10px;
color: var(–yellow);
text-shadow: 2px 2px var(–orange);
pointer-events: none;
z-index: 60;
animation: scorePop 0.8s ease-out forwards;
}

@keyframes scorePop {
0% { transform: translateY(0) scale(1); opacity: 1; }
100% { transform: translateY(-50px) scale(1.3); opacity: 0; }
}

/* TACO COMPLETE flash */
.taco-complete-flash {
position: absolute;
inset: 0;
background: rgba(255,200,0,0.12);
pointer-events: none;
z-index: 55;
animation: flash 0.3s ease-out forwards;
}

@keyframes flash {
0% { opacity: 1; }
100% { opacity: 0; }
}

/* BOTTOM AREA - tortilla slots */
#taco-slots {
position: absolute;
bottom: 8px;
left: 24px;
display: flex;
gap: 6px;
align-items: center;
}

/* GAME OVER SCREEN */
#gameover-screen {
display: none;
flex-direction: column;
align-items: center;
justify-content: center;
width: 480px;
min-height: 560px;
background: var(–dark);
border: 4px solid var(–orange);
gap: 16px;
padding: 32px;
}

#gameover-screen h2 {
font-size: 18px;
color: var(–red);
text-shadow: 3px 3px var(–shadow);
text-align: center;
}

#gameover-screen .final-score {
font-size: 12px;
color: var(–yellow);
text-align: center;
line-height: 2;
}

#name-input {
font-family: ‘Press Start 2P’, monospace;
font-size: 11px;
background: #111;
border: 2px solid var(–orange);
color: var(–cream);
padding: 10px 14px;
text-align: center;
outline: none;
width: 220px;
text-transform: uppercase;
letter-spacing: 2px;
}

#name-input::placeholder { color: #555; font-size: 8px; }

.name-label {
font-size: 7px;
color: var(–yellow);
letter-spacing: 1px;
margin-bottom: -8px;
}

/* LEADERBOARD SCREEN */
#leaderboard-screen {
display: none;
flex-direction: column;
align-items: center;
width: 480px;
min-height: 560px;
background: var(–dark);
border: 4px solid var(–orange);
padding: 28px 24px;
gap: 16px;
}

#leaderboard-screen h2 {
font-size: 13px;
color: var(–orange);
text-shadow: 2px 2px var(–red);
letter-spacing: 2px;
}

.lb-subtitle { font-size: 7px; color: var(–yellow); letter-spacing: 2px; }

#lb-table {
width: 100%;
border-collapse: collapse;
margin-top: 8px;
}

#lb-table th {
font-size: 7px;
color: var(–orange);
padding: 6px 8px;
border-bottom: 2px solid var(–shadow);
text-align: left;
letter-spacing: 1px;
}

#lb-table th:last-child { text-align: right; }

#lb-table td {
font-family: ‘VT323’, monospace;
font-size: 20px;
padding: 6px 8px;
border-bottom: 1px solid #2a1000;
color: var(–cream);
}

#lb-table td:last-child { text-align: right; color: var(–yellow); }

#lb-table tr:first-child td { color: var(–orange); }
#lb-table tr:nth-child(2) td { color: #bdc3c7; }
#lb-table tr:nth-child(3) td { color: #d4a017; }

.rank-cell { color: var(–shadow) !important; font-size: 16px !important; }

.lb-empty { font-size: 8px; color: #555; text-align: center; margin-top: 20px; }

/* CLICK EFFECT */
.click-ripple {
position: absolute;
border: 2px solid var(–orange);
border-radius: 0;
pointer-events: none;
z-index: 80;
animation: ripple 0.4s ease-out forwards;
}

@keyframes ripple {
0% { width: 8px; height: 8px; opacity: 1; margin: -4px; }
100% { width: 40px; height: 40px; opacity: 0; margin: -20px; }
}

/* Decorative lantern lights top */
.lights-row {
position: absolute;
top: 0; left: 0; right: 0;
height: 20px;
background: repeating-linear-gradient(90deg,
transparent 0px, transparent 18px,
rgba(255,200,0,0.6) 18px, rgba(255,200,0,0.6) 22px,
transparent 22px, transparent 40px);
pointer-events: none;
z-index: 5;
}

.btn-row { display: flex; gap: 12px; flex-wrap: wrap; justify-content: center; }
</style>

</head>
<body>

<!-- TITLE SCREEN -->

<div id="title-screen">
  <div class="title-logo">
    <span class="line1">🌮 TAQUERIA PIXELADA 🌮</span>
    <span class="line2">EL<br>TROMPO</span>
  </div>
  <div class="title-trompo-preview">
    <canvas id="preview-canvas" width="80" height="100"></canvas>
  </div>
  <div style="font-size:7px; color:#888; margin-bottom:20px; text-align:center; line-height:2.2;">
    CLICK THE TROMPO<br>3 CUTS = 1 TACO<br>DON'T LET THE TIMER RUN OUT
  </div>
  <div class="btn-row">
    <button class="pixel-btn" onclick="startGame()">▶ START</button>
    <button class="pixel-btn secondary" onclick="showLeaderboard('title')">🏆 TOP TACOS</button>
  </div>
</div>

<!-- GAME SCREEN -->

<div id="game-screen">
  <div id="hud">
    <div class="hud-item">
      <span class="hud-label">TACOS</span>
      <span class="hud-value" id="taco-count">0</span>
    </div>
    <div class="hud-item">
      <span class="hud-label">CUTS</span>
      <span class="hud-value" id="cut-display">○ ○ ○</span>
    </div>
    <div class="hud-item">
      <span class="hud-label">BEST</span>
      <span class="hud-value" id="best-display">0</span>
    </div>
  </div>
  <div id="timer-container">
    <span class="timer-label">TIME</span>
    <div id="timer-bar-bg">
      <div id="timer-bar-fill"></div>
    </div>
  </div>
  <div id="scene">
    <div class="lights-row"></div>
    <!-- TROMPO -->
    <div id="trompo-wrap" onclick="cutMeat(event)">
      <canvas id="trompo-canvas" width="100" height="200"></canvas>
    </div>
    <!-- CHEF -->
    <div id="knife-wrap">
      <canvas id="knife-canvas" width="80" height="140"></canvas>
    </div>
    <!-- TACO PLATE -->
    <div id="taco-wrap">
      <canvas id="taco-canvas" width="120" height="80"></canvas>
    </div>
    <!-- COUNTER SURFACE -->
    <div id="counter-surface"></div>
    <!-- TACO SLOTS (meat progress) -->
    <div id="taco-slots"></div>
  </div>
</div>

<!-- GAME OVER SCREEN -->

<div id="gameover-screen">
  <h2>¡SE ACABÓ!<br><br>TIME'S UP</h2>
  <div class="final-score" id="final-score-text">YOU MADE<br>0 TACOS</div>
  <span class="name-label">ENTER YOUR NAME</span>
  <input type="text" id="name-input" maxlength="12" placeholder="YOUR NAME" />
  <div class="btn-row">
    <button class="pixel-btn" onclick="saveScore()">💾 SAVE SCORE</button>
    <button class="pixel-btn secondary" onclick="startGame()">↺ PLAY AGAIN</button>
  </div>
</div>

<!-- LEADERBOARD SCREEN -->

<div id="leaderboard-screen">
  <h2>🏆 HALL OF FAME</h2>
  <span class="lb-subtitle">TOP TAQUEROS</span>
  <table id="lb-table">
    <thead>
      <tr><th>#</th><th>NAME</th><th>TACOS</th></tr>
    </thead>
    <tbody id="lb-body"></tbody>
  </table>
  <div id="lb-empty" class="lb-empty" style="display:none">NO ENTRIES YET — BE THE FIRST!</div>
  <div class="btn-row" style="margin-top:12px;">
    <button class="pixel-btn" onclick="startGame()">▶ PLAY</button>
    <button class="pixel-btn secondary" id="lb-back-btn">← BACK</button>
  </div>
</div>

<script>
// ─── STATE ───────────────────────────────────────────────────────────────────
let tacoCount = 0;
let cutCount = 0;
let timerMax = 8000; // ms per taco
let timerLeft = timerMax;
let timerInterval = null;
let gameActive = false;
let lastFrom = 'title';

// ─── PIXEL ART HELPERS ───────────────────────────────────────────────────────
function px(ctx, x, y, w, h, color) {
  ctx.fillStyle = color;
  ctx.fillRect(x * 4, y * 4, w * 4, h * 4);
}

// ─── DRAW TROMPO ─────────────────────────────────────────────────────────────
function drawTrompo(canvasId, slice = 0) {
  const c = document.getElementById(canvasId);
  if (!c) return;
  const ctx = c.getContext('2d');
  ctx.clearRect(0, 0, c.width, c.height);
  const S = 4;

  // Spit / rod
  for (let y = 0; y < 48; y++) {
    ctx.fillStyle = (y % 3 === 0) ? '#999' : '#ccc';
    ctx.fillRect(11 * S, y * S, 1 * S, 1 * S);
  }

  // Pineapple on top
  const pineColors = ['#f1c40f', '#e67e22', '#f39c12'];
  for (let row = 0; row < 4; row++) {
    const w = [2, 3, 3, 2][row];
    const x = Math.floor((5 - w) / 2) + 9;
    ctx.fillStyle = pineColors[row % pineColors.length];
    ctx.fillRect(x * S, row * S, w * S, S);
  }

  // Meat cone (trompo shape)
  const meatLayers = [
    { y: 4,  w: 3 }, { y: 5,  w: 4 }, { y: 6,  w: 5 },
    { y: 7,  w: 6 }, { y: 8,  w: 7 }, { y: 9,  w: 8 },
    { y:10,  w: 9 }, { y:11,  w: 9 }, { y:12, w: 9 },
    { y:13,  w: 8 }, { y:14, w: 7 }, { y:15, w: 6 },
    { y:16,  w: 5 }, { y:17, w: 4 }, { y:18, w: 3 },
    { y:19,  w: 2 }, { y:20, w: 1 },
  ];

  const meatPalette = ['#c0392b','#e74c3c','#b03020','#922b21','#d44000','#c0392b','#e74c3c'];
  meatLayers.forEach(({ y, w }, i) => {
    const x = Math.floor((23 - w * 2) / 2) / 2;
    ctx.fillStyle = meatPalette[i % meatPalette.length];
    ctx.fillRect(x * S, y * S, w * S, S);
    // highlight edge
    if (i % 2 === 0) {
      ctx.fillStyle = 'rgba(255,150,100,0.3)';
      ctx.fillRect(x * S, y * S, S, S);
    }
  });

  // Charred bits
  ctx.fillStyle = '#5a1a00';
  ctx.fillRect(7*S, 8*S, S, S);
  ctx.fillRect(14*S, 11*S, S, S);
  ctx.fillRect(9*S, 14*S, S, S);

  // Slice mark if active
  if (slice > 0) {
    ctx.fillStyle = 'rgba(255,200,100,0.6)';
    ctx.fillRect(7*S, (10 + slice)*S, 8*S, S/2);
  }

  // Base/stand
  for (let row = 21; row < 25; row++) {
    const w = [6, 7, 6, 5][row - 21];
    const x = Math.floor((22 - w) / 2);
    ctx.fillStyle = row === 21 ? '#888' : '#555';
    ctx.fillRect(x * S, row * S, w * S, S);
  }
}

// ─── DRAW CHEF ───────────────────────────────────────────────────────────────
// Canvas is 80x140, pixel size S=4 → 20x35 pixel grid
function drawChef(slashing = false) {
  const c = document.getElementById('knife-canvas');
  if (!c) return;
  const ctx = c.getContext('2d');
  ctx.clearRect(0, 0, c.width, c.height);
  const S = 4;

  const _ = (x, y, w, h, col) => { ctx.fillStyle = col; ctx.fillRect(x*S, y*S, w*S, h*S); };

  // ── CHEF HAT ──
  // brim
  _(3, 0, 8, 1, '#f5f5f5');
  // tall hat body
  _(4, 1, 6, 1, '#ffffff');
  _(5, 2, 4, 1, '#ffffff');
  _(4, 3, 6, 3, '#ffffff');
  // hat shadow/detail
  _(5, 4, 1, 2, '#ddd');
  _(8, 4, 1, 2, '#ddd');

  // ── HEAD ──
  _(4, 6, 6, 5, '#f5c89a');   // face
  // eyes
  _(5, 7, 1, 1, '#2c1810');
  _(8, 7, 1, 1, '#2c1810');
  // smile
  _(5, 10, 1, 1, '#c0856a');
  _(6, 11, 2, 1, '#c0856a');
  _(8, 10, 1, 1, '#c0856a');
  // moustache
  _(5, 9, 2, 1, '#4a2c0a');
  _(7, 9, 2, 1, '#4a2c0a');
  // ear
  _(3, 8, 1, 2, '#e8a87c');
  _(10, 8, 1, 2, '#e8a87c');

  // ── NECK ──
  _(6, 11, 2, 1, '#f5c89a');

  // ── CHEF WHITES (torso) ──
  _(3, 12, 8, 8, '#f0f0f0');   // main body
  // jacket lapels / buttons
  _(6, 13, 1, 6, '#e0e0e0');
  _(7, 13, 1, 6, '#e0e0e0');
  _(6, 14, 1, 1, '#bbb');
  _(6, 16, 1, 1, '#bbb');
  _(6, 18, 1, 1, '#bbb');
  // jacket outline
  _(3, 12, 1, 8, '#ddd');
  _(10, 12, 1, 8, '#ddd');

  // ── APRON ──
  _(4, 14, 6, 7, '#ff6b00');    // apron body (orange like the game!)
  _(4, 14, 6, 1, '#ff8c33');    // apron top highlight
  // apron strings going around waist
  _(3, 15, 1, 1, '#e05a00');
  _(10, 15, 1, 1, '#e05a00');
  // apron pocket
  _(5, 17, 3, 3, '#e05a00');
  _(5, 17, 3, 1, '#c04a00');

  // ── LEFT ARM (idle, hanging down slightly) ──
  _(2, 13, 2, 5, '#f0f0f0');
  _(2, 18, 2, 2, '#f5c89a'); // hand

  // ── RIGHT ARM + KNIFE ──
  // arm position shifts forward when slashing
  const armX = slashing ? 10 : 9;
  const knifeAngle = slashing;

  _(armX, 13, 2, 4, '#f0f0f0');   // upper arm
  _(armX, 17, 2, 2, '#f5c89a');   // forearm/hand

  if (!slashing) {
    // Knife held upright at rest
    // handle (brown)
    _(armX+1, 12, 2, 3, '#8B4513');
    _(armX+1, 11, 2, 1, '#5D3010');
    // bolster
    _(armX+1, 10, 2, 1, '#aaa');
    // blade pointing up-right
    _(armX+1, 7,  2, 3, '#e0e0e0');
    _(armX+2, 6,  1, 1, '#ccc');
    _(armX+2, 5,  1, 1, '#bbb');
    // glint
    ctx.fillStyle = 'rgba(255,255,255,0.7)';
    ctx.fillRect((armX+1)*S, 7*S, S/2, 3*S);
  } else {
    // Knife thrusting forward (horizontal slash toward trompo)
    // arm extends right
    _(armX,   16, 4, 2, '#f0f0f0');   // extended forearm
    _(armX+3, 16, 2, 2, '#f5c89a');   // extended hand
    // knife horizontal: handle then blade going right
    _(armX+4, 16, 2, 2, '#8B4513');   // handle
    _(armX+5, 15, 1, 1, '#5D3010');
    _(armX+6, 15, 1, 4, '#aaa');      // bolster vertical
    // blade pointing right
    _(armX+7, 15, 4, 2, '#e0e0e0');
    _(armX+9, 15, 2, 2, '#ccc');
    _(armX+10,16, 1, 1, '#bbb');      // tip
    // glint
    ctx.fillStyle = 'rgba(255,255,255,0.7)';
    ctx.fillRect((armX+7)*S, 15*S, S/2, 2*S);
  }

  // ── LEGS ──
  _(4, 20, 3, 5, '#2c3e50');    // left trouser
  _(7, 20, 3, 5, '#2c3e50');    // right trouser
  // trouser crease
  _(5, 21, 1, 3, '#253545');
  _(8, 21, 1, 3, '#253545');

  // ── SHOES ──
  _(3, 25, 4, 2, '#1a1a1a');
  _(7, 25, 4, 2, '#1a1a1a');
  _(3, 26, 5, 1, '#111');       // sole left
  _(7, 26, 5, 1, '#111');       // sole right
}

// expose so slashing variant can be called
function drawChefSlashing() { drawChef(true); }
function drawChefIdle()     { drawChef(false); }

// ─── DRAW TACO ───────────────────────────────────────────────────────────────
function drawTaco(cuts) {
  const c = document.getElementById('taco-canvas');
  if (!c) return;
  const ctx = c.getContext('2d');
  ctx.clearRect(0, 0, c.width, c.height);
  const S = 4;

  // Plate shadow
  ctx.fillStyle = 'rgba(0,0,0,0.3)';
  ctx.fillRect(2*S, 15*S, 24*S, 2*S);

  // Tortilla shell (taco shape)
  const tortillaColor = '#f0d090';
  const tortillaDark = '#d4a84b';

  // bottom curve
  for (let x = 0; x < 18; x++) {
    const h = Math.floor(2 + Math.sin((x / 17) * Math.PI) * 2);
    ctx.fillStyle = tortillaColor;
    ctx.fillRect((x + 3)*S, 12*S, S, h*S);
  }
  // left wall
  for (let y = 4; y < 14; y++) {
    ctx.fillStyle = (y > 10) ? tortillaDark : tortillaColor;
    ctx.fillRect(3*S, y*S, S, S);
  }
  // right wall
  for (let y = 4; y < 14; y++) {
    ctx.fillStyle = (y > 10) ? tortillaDark : tortillaColor;
    ctx.fillRect(20*S, y*S, S, S);
  }
  // top left flap
  ctx.fillStyle = tortillaColor;
  ctx.fillRect(3*S, 3*S, 7*S, 2*S);
  // top right flap
  ctx.fillRect(13*S, 3*S, 7*S, 2*S);

  // Meat slices in taco
  if (cuts > 0) {
    const meatColors = ['#c0392b', '#e74c3c', '#922b21'];
    for (let i = 0; i < cuts; i++) {
      const mx = 5 + i * 5;
      ctx.fillStyle = meatColors[i % meatColors.length];
      ctx.fillRect(mx*S, 6*S, 3*S, 5*S);
      // fat edge
      ctx.fillStyle = '#ff9f7f';
      ctx.fillRect(mx*S, 6*S, S/2, 5*S);
    }
  }

  // Cilantro dots
  if (cuts >= 2) {
    ctx.fillStyle = '#27ae60';
    [[6,5],[9,5],[13,5],[10,6]].forEach(([x,y]) => {
      ctx.fillRect(x*S, y*S, S, S);
    });
  }

  // Onion bits
  if (cuts >= 3) {
    ctx.fillStyle = '#f0e6ff';
    [[7,5],[11,5],[14,6]].forEach(([x,y]) => {
      ctx.fillRect(x*S, y*S, S, S);
    });
  }
}

// ─── DRAW TROMPO PREVIEW (title) ─────────────────────────────────────────────
function drawPreview() {
  const c = document.getElementById('preview-canvas');
  if (!c) return;
  const ctx = c.getContext('2d');
  ctx.clearRect(0, 0, 80, 100);
  // mini trompo
  const colors = ['#c0392b','#e74c3c','#b03020'];
  ctx.fillStyle = '#f1c40f';
  ctx.fillRect(34, 0, 8, 12);
  for (let i = 0; i < 14; i++) {
    const w = Math.min(40, 8 + i * 3);
    const x = (80 - w) / 2;
    ctx.fillStyle = colors[i % colors.length];
    ctx.fillRect(x, 12 + i*5, w, 4);
  }
  ctx.fillStyle = '#888';
  ctx.fillRect(28, 82, 24, 6);
  ctx.fillRect(22, 88, 36, 6);
}

// ─── CUT DISPLAY ─────────────────────────────────────────────────────────────
function updateCutDisplay() {
  const symbols = ['●','●','●'].map((s,i) => i < cutCount ? `<span style="color:var(--orange)">${s}</span>` : `<span style="color:#333">○</span>`);
  document.getElementById('cut-display').innerHTML = symbols.join(' ');
}

// ─── TIMER ───────────────────────────────────────────────────────────────────
function startTimer() {
  timerLeft = timerMax;
  updateTimerBar();
  clearInterval(timerInterval);
  timerInterval = setInterval(() => {
    timerLeft -= 100;
    updateTimerBar();
    if (timerLeft <= 0) {
      timerLeft = 0;
      updateTimerBar();
      clearInterval(timerInterval);
      endGame();
    }
  }, 100);
}

function resetTimer() {
  timerLeft = timerMax;
  updateTimerBar();
}

function updateTimerBar() {
  const pct = (timerLeft / timerMax) * 100;
  const fill = document.getElementById('timer-bar-fill');
  fill.style.width = pct + '%';
  if (pct > 60) fill.style.background = 'var(--green)';
  else if (pct > 30) fill.style.background = 'var(--yellow)';
  else fill.style.background = 'var(--red)';
}

// ─── CUT MEAT ─────────────────────────────────────────────────────────────────
function cutMeat(e) {
  if (!gameActive) return;

  const wrap = document.getElementById('trompo-wrap');
  const scene = document.getElementById('scene');

  // visual feedback
  wrap.classList.remove('cutting');
  void wrap.offsetWidth;
  wrap.classList.add('cutting');

  // knife slash — swap chef sprite to slashing frame
  const knife = document.getElementById('knife-wrap');
  knife.classList.remove('slashing');
  void knife.offsetWidth;
  drawChefSlashing();
  knife.classList.add('slashing');
  setTimeout(() => {
    knife.classList.remove('slashing');
    drawChefIdle();
  }, 220);

  // ripple at click
  const rect = wrap.getBoundingClientRect();
  const sceneRect = scene.getBoundingClientRect();
  const ripple = document.createElement('div');
  ripple.className = 'click-ripple';
  ripple.style.left = (rect.left - sceneRect.left + (e.offsetX || 30)) + 'px';
  ripple.style.top = (rect.top - sceneRect.top + (e.offsetY || 60)) + 'px';
  scene.appendChild(ripple);
  setTimeout(() => ripple.remove(), 400);

  // spawn flying meat chunk
  spawnMeatChunk(wrap, scene);

  cutCount++;
  updateCutDisplay();

  if (cutCount >= 3) {
    completeTaco();
  } else {
    drawTaco(cutCount);
  }
}

function spawnMeatChunk(trompoWrap, scene) {
  const tRect = trompoWrap.getBoundingClientRect();
  const sRect = scene.getBoundingClientRect();
  const tacoWrap = document.getElementById('taco-wrap');
  const tacoRect = tacoWrap.getBoundingClientRect();

  const startX = tRect.left - sRect.left + 30;
  const startY = tRect.top - sRect.top + 80;
  const endX = tacoRect.left - sRect.left + 60 + (cutCount * 15);
  const endY = tacoRect.top - sRect.top + 30;

  const chunk = document.createElement('canvas');
  chunk.width = 20; chunk.height = 16;
  const ctx = chunk.getContext('2d');
  // draw tiny meat piece
  const colors = ['#c0392b','#e74c3c','#922b21'];
  ctx.fillStyle = colors[cutCount % colors.length];
  ctx.fillRect(2, 2, 14, 10);
  ctx.fillStyle = '#ff9f7f';
  ctx.fillRect(2, 2, 3, 10);
  ctx.fillStyle = '#5a1a00';
  ctx.fillRect(12, 4, 3, 4);

  chunk.className = 'meat-chunk';
  chunk.style.left = startX + 'px';
  chunk.style.top = startY + 'px';
  chunk.style.setProperty('--tx', (endX - startX) + 'px');
  chunk.style.setProperty('--ty', (endY - startY) + 'px');
  chunk.style.setProperty('--tr', (Math.random() * 360) + 'deg');

  scene.appendChild(chunk);
  setTimeout(() => {
    chunk.remove();
    drawTaco(cutCount); // update taco after meat lands
  }, 500);
}

// ─── COMPLETE TACO ────────────────────────────────────────────────────────────
function completeTaco() {
  tacoCount++;
  document.getElementById('taco-count').textContent = tacoCount;

  // flash
  const scene = document.getElementById('scene');
  const flash = document.createElement('div');
  flash.className = 'taco-complete-flash';
  scene.appendChild(flash);
  setTimeout(() => flash.remove(), 300);

  // score pop
  const pop = document.createElement('div');
  pop.className = 'score-pop';
  pop.textContent = '+1 TACO!';
  pop.style.left = '60px';
  pop.style.top = '100px';
  scene.appendChild(pop);
  setTimeout(() => pop.remove(), 800);

  // reset for next taco
  cutCount = 0;
  updateCutDisplay();
  resetTimer();

  setTimeout(() => {
    drawTaco(0);
    drawTrompo('trompo-canvas', 0);
  }, 300);
}

// ─── GAME START / END ─────────────────────────────────────────────────────────
function startGame() {
  tacoCount = 0;
  cutCount = 0;
  gameActive = true;

  document.getElementById('title-screen').style.display = 'none';
  document.getElementById('gameover-screen').style.display = 'none';
  document.getElementById('leaderboard-screen').style.display = 'none';
  document.getElementById('game-screen').style.display = 'flex';
  document.getElementById('game-screen').style.flexDirection = 'column';

  document.getElementById('taco-count').textContent = '0';
  updateCutDisplay();
  loadBest();
  drawTrompo('trompo-canvas', 0);
  drawChefIdle();
  drawTaco(0);
  startTimer();
}

function endGame() {
  gameActive = false;
  clearInterval(timerInterval);

  document.getElementById('game-screen').style.display = 'none';
  document.getElementById('gameover-screen').style.display = 'flex';
  document.getElementById('gameover-screen').style.flexDirection = 'column';
  document.getElementById('final-score-text').textContent = `YOU MADE\n${tacoCount} TACO${tacoCount !== 1 ? 'S' : ''}`;

  // check if personal best
  const best = getBest();
  if (tacoCount > best) saveBest(tacoCount);
}

// ─── STORAGE / LEADERBOARD ───────────────────────────────────────────────────
const STORAGE_KEY = 'el-trompo-leaderboard';
const BEST_KEY = 'el-trompo-best';

async function saveScore() {
  const nameInput = document.getElementById('name-input');
  const name = nameInput.value.trim().toUpperCase() || 'ANON';
  if (tacoCount === 0) { showLeaderboard('gameover'); return; }

  let board = await loadLeaderboard();
  board.push({ name, tacos: tacoCount, date: Date.now() });
  board.sort((a, b) => b.tacos - a.tacos);
  board = board.slice(0, 10);

  try {
    await window.storage.set(STORAGE_KEY, JSON.stringify(board), true);
  } catch(e) {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(board));
  }

  nameInput.value = '';
  showLeaderboard('gameover');
}

async function loadLeaderboard() {
  try {
    const result = await window.storage.get(STORAGE_KEY, true);
    return result ? JSON.parse(result.value) : [];
  } catch(e) {
    try {
      const local = localStorage.getItem(STORAGE_KEY);
      return local ? JSON.parse(local) : [];
    } catch { return []; }
  }
}

function getBest() {
  try { return parseInt(localStorage.getItem(BEST_KEY) || '0'); } catch { return 0; }
}

function saveBest(n) {
  try { localStorage.setItem(BEST_KEY, n); } catch {}
}

function loadBest() {
  const best = getBest();
  document.getElementById('best-display').textContent = best;
}

async function showLeaderboard(from) {
  lastFrom = from;
  document.getElementById('title-screen').style.display = 'none';
  document.getElementById('gameover-screen').style.display = 'none';
  document.getElementById('game-screen').style.display = 'none';

  const lb = document.getElementById('leaderboard-screen');
  lb.style.display = 'flex';
  lb.style.flexDirection = 'column';

  // back button
  document.getElementById('lb-back-btn').onclick = () => {
    lb.style.display = 'none';
    if (from === 'gameover') {
      document.getElementById('gameover-screen').style.display = 'flex';
      document.getElementById('gameover-screen').style.flexDirection = 'column';
    } else {
      document.getElementById('title-screen').style.display = 'flex';
      document.getElementById('title-screen').style.flexDirection = 'column';
    }
  };

  const board = await loadLeaderboard();
  const tbody = document.getElementById('lb-body');
  tbody.innerHTML = '';
  const empty = document.getElementById('lb-empty');

  if (board.length === 0) {
    empty.style.display = 'block';
  } else {
    empty.style.display = 'none';
    const medals = ['🥇','🥈','🥉'];
    board.forEach((entry, i) => {
      const tr = document.createElement('tr');
      tr.innerHTML = `
        <td class="rank-cell">${medals[i] || (i+1)}</td>
        <td>${entry.name}</td>
        <td>${entry.tacos} 🌮</td>
      `;
      tbody.appendChild(tr);
    });
  }
}

// ─── INIT ─────────────────────────────────────────────────────────────────────
drawPreview();

// Animate title trompo
let previewFrame = 0;
setInterval(() => {
  const c = document.getElementById('preview-canvas');
  if (!c || document.getElementById('title-screen').style.display === 'none') return;
  drawPreview();
  previewFrame++;
}, 800);

// Animate trompo shimmer when game active
setInterval(() => {
  if (!gameActive) return;
  drawTrompo('trompo-canvas', Math.random() > 0.7 ? 1 : 0);
}, 600);</script>

</body>
</html>
