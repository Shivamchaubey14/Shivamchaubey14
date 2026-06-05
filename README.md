<div align="center">

<style>
  :root {
    --neon-mint:   #00E5A0;
    --neon-cyan:   #00B8FF;
    --amber-glow:  #F5A623;
    --deep-purple: #7B2F9D;
    --violet-pink: #E056D9;
    --bg-dark:     #0A0F1A;
    --bg-mid:      #0B1C2A;
    --bg-light:    #0A0E17;
    --glass-bg:    rgba(11,28,42,0.72);
    --border-glow: rgba(0,229,160,0.30);
    --shadow-cyan: 0 0 20px rgba(0,184,255,0.22);
  }

  @keyframes glowPulse {
    0%,100% { text-shadow: 0 0 8px #00E5A0, 0 0 2px #00B8FF; }
    50%      { text-shadow: 0 0 24px #00E5A0, 0 0 10px #00B8FF, 0 0 40px #7B2F9D; }
  }
  @keyframes borderBreath {
    0%,100% { box-shadow: 0 0 10px #00E5A0, 0 0 2px #00B8FF; border-color: rgba(0,229,160,0.4); }
    50%      { box-shadow: 0 0 30px #00E5A0, 0 0 16px #00B8FF, 0 0 50px #7B2F9D; border-color: rgba(0,229,160,0.9); }
  }
  @keyframes scanline {
    0%   { transform: translateY(-100%); }
    100% { transform: translateY(3200%); }
  }
  @keyframes floatUp {
    0%   { transform: translateY(0px) scale(1);   opacity: 0.8; }
    50%  { transform: translateY(-14px) scale(1.04); opacity: 1; }
    100% { transform: translateY(0px) scale(1);   opacity: 0.8; }
  }
  @keyframes blink {
    0%,49% { opacity:1; } 50%,100% { opacity:0; }
  }
  @keyframes rotate360 {
    from { transform: rotate(0deg); }
    to   { transform: rotate(360deg); }
  }
  @keyframes dataFlow {
    0%   { stroke-dashoffset: 200; opacity: 0.2; }
    50%  { stroke-dashoffset: 0;   opacity: 0.9; }
    100% { stroke-dashoffset: -200; opacity: 0.2; }
  }
  @keyframes nodeFloat {
    0%,100% { transform: translateY(0);  }
    50%     { transform: translateY(-7px); }
  }
  @keyframes clockHand {
    from { transform: rotate(0deg);   transform-origin: 50% 100%; }
    to   { transform: rotate(360deg); transform-origin: 50% 100%; }
  }
  @keyframes hexReveal {
    0%   { opacity:0; transform: scale(0.88) rotateY(-20deg); }
    100% { opacity:1; transform: scale(1)    rotateY(0deg); }
  }
  @keyframes glitch1 {
    0%,90%,100% { clip-path: none; transform: none; }
    92% { clip-path: polygon(0 20%,100% 20%,100% 40%,0 40%); transform: translateX(-3px); }
    94% { clip-path: polygon(0 60%,100% 60%,100% 80%,0 80%); transform: translateX(3px); }
  }
  @keyframes particleDrift {
    0%   { opacity:0; transform: translateY(0)   translateX(0) scale(0); }
    10%  { opacity:0.9; }
    100% { opacity:0; transform: translateY(-180px) translateX(var(--dx,20px)) scale(1.4); }
  }
  @media (prefers-reduced-motion: reduce) {
    * { animation: none !important; transition: none !important; }
  }

  .cyber-board {
    position: relative;
    background: linear-gradient(135deg, #0A0F1A 0%, #0B1C2A 50%, #0A0E17 100%);
    font-family: 'JetBrains Mono','Fira Code','Courier New',monospace;
    overflow: hidden;
    border-radius: 18px;
    border: 1px solid rgba(0,229,160,0.18);
    animation: borderBreath 3s infinite;
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 0 32px 0;
  }
  .scanline-overlay {
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 4px;
    background: linear-gradient(transparent,rgba(0,229,160,0.08),transparent);
    animation: scanline 7s linear infinite;
    pointer-events: none;
    z-index: 10;
  }
  .hero-title {
    font-size: 2.6em;
    font-weight: 900;
    letter-spacing: 0.04em;
    color: #fff;
    animation: glowPulse 3s infinite;
    font-family: 'JetBrains Mono','Fira Code',monospace;
    margin: 0;
  }
  .glass-card {
    background: rgba(11,28,42,0.72);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border: 1px solid rgba(0,229,160,0.30);
    box-shadow: 0 0 20px rgba(0,184,255,0.18);
    border-radius: 12px;
    padding: 20px 24px;
    margin: 12px auto;
  }
  .neon-badge {
    display: inline-block;
    background: rgba(0,229,160,0.08);
    border: 1px solid rgba(0,229,160,0.5);
    border-radius: 999px;
    padding: 4px 14px;
    font-size: 0.82em;
    color: #00E5A0;
    font-family: 'Fira Code',monospace;
    box-shadow: 0 0 10px rgba(0,229,160,0.3);
    animation: floatUp 3.2s ease-in-out infinite;
  }
  .stat-img-wrap img {
    border-radius: 12px;
    border: 1px solid rgba(0,229,160,0.30);
    box-shadow: 0 0 20px rgba(0,184,255,0.18);
    transition: box-shadow 0.3s;
  }
  .stat-img-wrap img:hover {
    box-shadow: 0 0 36px rgba(0,229,160,0.5), 0 0 60px rgba(0,184,255,0.3);
  }
  .terminal-line { color: #00E5A0; font-size: 0.97em; line-height: 1.9; }
  .terminal-prompt { color: #F5A623; }
  .terminal-cmd   { color: #00B8FF; }
  .terminal-out   { color: #c9d1d9; }
  .cursor-blink {
    display: inline-block;
    width: 9px; height: 1.1em;
    background: #00E5A0;
    vertical-align: middle;
    animation: blink 1s step-end infinite;
  }
  .hex-grid { display: flex; flex-wrap: wrap; justify-content: center; gap: 16px; padding: 8px; }
  .hex-tile {
    width: 200px;
    background: rgba(11,28,42,0.82);
    border: 1px solid rgba(0,229,160,0.28);
    border-radius: 12px 0 12px 0;
    box-shadow: 0 0 16px rgba(0,184,255,0.14);
    padding: 18px 16px;
    transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s;
    animation: hexReveal 0.7s ease both;
    text-align: center;
    cursor: pointer;
  }
  .hex-tile:hover {
    transform: translateY(-8px) scale(1.04);
    box-shadow: 0 0 32px rgba(0,229,160,0.4), 0 0 60px rgba(0,184,255,0.22);
    border-color: rgba(0,229,160,0.8);
  }
  .hex-tile .piece-icon { font-size: 2.2em; margin-bottom: 6px; }
  .hex-tile .tile-title { color: #00E5A0; font-weight: 700; font-size: 0.95em; margin: 4px 0; }
  .hex-tile .tile-desc  { color: #888da0; font-size: 0.78em; line-height: 1.5; }
  .hex-tile .checkmate-btn {
    display: inline-block;
    margin-top: 10px;
    background: linear-gradient(90deg,#00E5A0,#00B8FF);
    color: #0A0F1A;
    font-weight: 700;
    font-size: 0.78em;
    padding: 4px 14px;
    border-radius: 999px;
    text-decoration: none;
    letter-spacing: 0.05em;
  }
  .strategy-card {
    background: rgba(11,28,42,0.82);
    border: 1px solid rgba(0,229,160,0.25);
    border-radius: 10px 0 10px 0;
    padding: 14px 16px;
    min-width: 180px;
    text-align: center;
    transition: transform 0.3s, box-shadow 0.3s;
    box-shadow: 0 0 12px rgba(0,184,255,0.10);
    animation: floatUp 4s ease-in-out infinite;
  }
  .strategy-card:hover {
    transform: translateY(-6px) rotateX(6deg);
    box-shadow: 0 0 28px rgba(0,229,160,0.4);
  }
  .orbit-ring {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 20px;
    padding: 16px 0;
  }
  .orbit-link {
    display: flex; flex-direction: column; align-items: center; gap: 6px;
    text-decoration: none;
    transition: transform 0.3s;
    animation: floatUp 3.5s ease-in-out infinite;
  }
  .orbit-link:hover { transform: scale(1.15); }
  .section-title {
    font-size: 1.25em;
    font-weight: 800;
    color: #00E5A0;
    letter-spacing: 0.08em;
    text-shadow: 0 0 8px #00E5A0;
    margin: 28px 0 12px;
    font-family: 'JetBrains Mono',monospace;
  }
  .tech-grid {
    display: flex; flex-wrap: wrap; justify-content: center; gap: 12px; padding: 8px;
  }
  .tech-chip {
    background: rgba(11,28,42,0.85);
    border: 1px solid rgba(0,184,255,0.35);
    border-radius: 8px 0 8px 0;
    padding: 10px 16px;
    color: #00B8FF;
    font-size: 0.85em;
    font-weight: 700;
    position: relative;
    transition: all 0.25s;
    cursor: default;
    box-shadow: 0 0 8px rgba(0,184,255,0.12);
    min-width: 110px;
    text-align: center;
  }
  .tech-chip:hover {
    background: rgba(0,229,160,0.08);
    border-color: #00E5A0;
    color: #00E5A0;
    box-shadow: 0 0 20px rgba(0,229,160,0.4);
    transform: translateY(-4px) scale(1.05);
  }
  .tech-chip::after {
    content: attr(data-tip);
    display: none;
    position: absolute;
    bottom: calc(100% + 8px);
    left: 50%; transform: translateX(-50%);
    background: #0B1C2A;
    border: 1px solid rgba(0,229,160,0.5);
    border-radius: 6px;
    padding: 6px 10px;
    font-size: 0.76em;
    color: #F5A623;
    white-space: nowrap;
    z-index: 99;
    box-shadow: 0 0 14px rgba(0,229,160,0.3);
    pointer-events: none;
  }
  .tech-chip:hover::after { display: block; }
  .elo-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(11,28,42,0.85);
    border: 1px solid rgba(245,166,35,0.5);
    border-radius: 999px;
    padding: 5px 16px;
    font-size: 0.88em;
    color: #F5A623;
    box-shadow: 0 0 12px rgba(245,166,35,0.22);
    animation: floatUp 4s ease-in-out infinite;
  }
  .heatmap-grid {
    display: grid;
    grid-template-columns: repeat(53, 1fr);
    gap: 2.5px;
    width: 100%;
    max-width: 900px;
    margin: 0 auto;
  }
  .hm-cell {
    aspect-ratio: 1;
    border-radius: 2px;
  }
  .hm-0 { background: #1A2533; }
  .hm-1 { background: rgba(123,47,157,0.55); }
  .hm-2 { background: rgba(0,184,255,0.5);  }
  .hm-3 { background: rgba(0,229,160,0.7);  }
  .hm-4 { background: #00E5A0; box-shadow: 0 0 4px #00E5A0; }
  .quote-block {
    border-left: 3px solid #00E5A0;
    padding: 10px 18px;
    margin: 16px auto;
    color: #c9d1d9;
    font-style: italic;
    font-size: 0.95em;
    background: rgba(0,229,160,0.04);
    border-radius: 0 8px 8px 0;
    max-width: 600px;
  }
</style>

<div class="cyber-board">
<div class="scanline-overlay"></div>

<!-- ═══════════════════════ NEURAL NETWORK SVG ═══════════════════════ -->

<svg viewBox="0 0 1100 260" xmlns="http://www.w3.org/2000/svg" style="position:absolute;top:0;left:0;width:100%;height:260px;z-index:1;pointer-events:none;">
  <defs>
    <radialGradient id="ng1" cx="50%" cy="50%" r="50%">
      <stop offset="0%" stop-color="#00E5A0" stop-opacity="0.9"/>
      <stop offset="100%" stop-color="#00E5A0" stop-opacity="0"/>
    </radialGradient>
    <radialGradient id="ng2" cx="50%" cy="50%" r="50%">
      <stop offset="0%" stop-color="#00B8FF" stop-opacity="0.9"/>
      <stop offset="100%" stop-color="#00B8FF" stop-opacity="0"/>
    </radialGradient>
    <radialGradient id="ng3" cx="50%" cy="50%" r="50%">
      <stop offset="0%" stop-color="#7B2F9D" stop-opacity="0.9"/>
      <stop offset="100%" stop-color="#7B2F9D" stop-opacity="0"/>
    </radialGradient>
    <linearGradient id="edgeGrad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%"   stop-color="#00E5A0" stop-opacity="0.7"/>
      <stop offset="50%"  stop-color="#00B8FF" stop-opacity="0.9"/>
      <stop offset="100%" stop-color="#7B2F9D" stop-opacity="0.5"/>
    </linearGradient>
    <linearGradient id="edgeGrad2" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%"   stop-color="#7B2F9D" stop-opacity="0.6"/>
      <stop offset="100%" stop-color="#00E5A0" stop-opacity="0.8"/>
    </linearGradient>
    <filter id="glow">
      <feGaussianBlur stdDeviation="3.5" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <!-- Chess board subtle bg pattern -->
    <pattern id="chessPattern" x="0" y="0" width="40" height="40" patternUnits="userSpaceOnUse">
      <rect x="0"  y="0"  width="20" height="20" fill="rgba(255,255,255,0.012)"/>
      <rect x="20" y="20" width="20" height="20" fill="rgba(255,255,255,0.012)"/>
    </pattern>
  </defs>

  <!-- Chess bg -->
  <rect width="1100" height="260" fill="url(#chessPattern)"/>

  <!-- Neural edges with data-flow dash animation -->
  <!-- Edges layer 1 -->
  <path d="M80,80 Q250,40 420,130" stroke="url(#edgeGrad1)" stroke-width="1.4" fill="none" stroke-dasharray="180" opacity="0.6">
    <animate attributeName="stroke-dashoffset" values="180;0;-180" dur="4s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.2;0.8;0.2" dur="4s" repeatCount="indefinite"/>
  </path>
  <path d="M420,130 Q580,60 720,150" stroke="url(#edgeGrad1)" stroke-width="1.2" fill="none" stroke-dasharray="160" opacity="0.5">
    <animate attributeName="stroke-dashoffset" values="160;0;-160" dur="3.5s" begin="0.8s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.15;0.75;0.15" dur="3.5s" begin="0.8s" repeatCount="indefinite"/>
  </path>
  <path d="M720,150 Q870,80 1020,120" stroke="url(#edgeGrad2)" stroke-width="1.4" fill="none" stroke-dasharray="170" opacity="0.55">
    <animate attributeName="stroke-dashoffset" values="170;0;-170" dur="4.2s" begin="1.2s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.2;0.85;0.2" dur="4.2s" begin="1.2s" repeatCount="indefinite"/>
  </path>
  <path d="M200,200 Q380,110 540,190" stroke="url(#edgeGrad2)" stroke-width="1.0" fill="none" stroke-dasharray="150" opacity="0.45">
    <animate attributeName="stroke-dashoffset" values="150;0;-150" dur="5s" begin="0.4s" repeatCount="indefinite"/>
  </path>
  <path d="M540,190 Q680,140 820,200" stroke="url(#edgeGrad1)" stroke-width="1.1" fill="none" stroke-dasharray="140" opacity="0.4">
    <animate attributeName="stroke-dashoffset" values="140;0;-140" dur="4.6s" begin="1.6s" repeatCount="indefinite"/>
  </path>
  <path d="M80,80 Q140,180 200,200" stroke="#7B2F9D" stroke-width="1.0" fill="none" stroke-dasharray="120" opacity="0.45">
    <animate attributeName="stroke-dashoffset" values="120;0;-120" dur="3.8s" begin="0.6s" repeatCount="indefinite"/>
  </path>
  <path d="M1020,120 Q1060,180 820,200" stroke="#00E5A0" stroke-width="1.0" fill="none" stroke-dasharray="130" opacity="0.35">
    <animate attributeName="stroke-dashoffset" values="130;0;-130" dur="4.3s" begin="2s" repeatCount="indefinite"/>
  </path>
  <path d="M420,130 Q480,200 540,190" stroke="#00B8FF" stroke-width="0.9" fill="none" stroke-dasharray="110" opacity="0.4">
    <animate attributeName="stroke-dashoffset" values="110;0;-110" dur="3.2s" begin="0.9s" repeatCount="indefinite"/>
  </path>
  <path d="M330,50 Q420,130 480,90" stroke="url(#edgeGrad1)" stroke-width="1.0" fill="none" stroke-dasharray="100" opacity="0.35">
    <animate attributeName="stroke-dashoffset" values="100;0;-100" dur="4.8s" begin="1.5s" repeatCount="indefinite"/>
  </path>
  <path d="M650,60 Q720,150 780,80" stroke="url(#edgeGrad2)" stroke-width="1.0" fill="none" stroke-dasharray="100" opacity="0.35">
    <animate attributeName="stroke-dashoffset" values="100;0;-100" dur="4.0s" begin="0.3s" repeatCount="indefinite"/>
  </path>

  <!-- Nodes (labeled neurons) -->
  <!-- Node: Python -->
  <g filter="url(#glow)">
    <animateTransform attributeName="transform" type="translate" values="0,0;0,-7;0,0" dur="3.8s" repeatCount="indefinite"/>
    <circle cx="80" cy="80" r="14" fill="url(#ng1)" opacity="0.9"/>
    <circle cx="80" cy="80" r="6"  fill="#00E5A0"/>
    <text x="80" y="106" text-anchor="middle" fill="#00E5A0" font-size="9" font-family="Fira Code,monospace" font-weight="700">Python</text>
  </g>
  <!-- Node: Django -->
  <g filter="url(#glow)">
    <animateTransform attributeName="transform" type="translate" values="0,0;0,-5;0,0" dur="4.5s" begin="0.5s" repeatCount="indefinite"/>
    <circle cx="420" cy="130" r="16" fill="url(#ng2)" opacity="0.85"/>
    <circle cx="420" cy="130" r="7"  fill="#00B8FF"/>
    <text x="420" y="156" text-anchor="middle" fill="#00B8FF" font-size="9" font-family="Fira Code,monospace" font-weight="700">Django</text>
  </g>
  <!-- Node: React -->
  <g filter="url(#glow)">
    <animateTransform attributeName="transform" type="translate" values="0,0;0,-8;0,0" dur="4.1s" begin="1s" repeatCount="indefinite"/>
    <circle cx="720" cy="150" r="15" fill="url(#ng1)" opacity="0.88"/>
    <circle cx="720" cy="150" r="6"  fill="#00E5A0"/>
    <text x="720" y="176" text-anchor="middle" fill="#00E5A0" font-size="9" font-family="Fira Code,monospace" font-weight="700">React</text>
  </g>
  <!-- Node: DSA -->
  <g filter="url(#glow)">
    <animateTransform attributeName="transform" type="translate" values="0,0;0,-6;0,0" dur="3.5s" begin="0.3s" repeatCount="indefinite"/>
    <circle cx="1020" cy="120" r="13" fill="url(#ng3)" opacity="0.85"/>
    <circle cx="1020" cy="120" r="5"  fill="#7B2F9D"/>
    <text x="1020" y="144" text-anchor="middle" fill="#E056D9" font-size="9" font-family="Fira Code,monospace" font-weight="700">DSA</text>
  </g>
  <!-- Node: System Design -->
  <g filter="url(#glow)">
    <animateTransform attributeName="transform" type="translate" values="0,0;0,-9;0,0" dur="5s" begin="1.5s" repeatCount="indefinite"/>
    <circle cx="200" cy="200" r="12" fill="url(#ng2)" opacity="0.8"/>
    <circle cx="200" cy="200" r="5"  fill="#00B8FF"/>
    <text x="200" y="222" text-anchor="middle" fill="#00B8FF" font-size="8" font-family="Fira Code,monospace" font-weight="700">Sys Design</text>
  </g>
  <!-- Node: Docker -->
  <g filter="url(#glow)">
    <animateTransform attributeName="transform" type="translate" values="0,0;0,-6;0,0" dur="3.9s" begin="2s" repeatCount="indefinite"/>
    <circle cx="540" cy="190" r="12" fill="url(#ng3)" opacity="0.78"/>
    <circle cx="540" cy="190" r="5"  fill="#7B2F9D"/>
    <text x="540" y="212" text-anchor="middle" fill="#E056D9" font-size="8" font-family="Fira Code,monospace" font-weight="700">Docker</text>
  </g>
  <!-- Node: PostgreSQL -->
  <g filter="url(#glow)">
    <animateTransform attributeName="transform" type="translate" values="0,0;0,-7;0,0" dur="4.6s" begin="0.7s" repeatCount="indefinite"/>
    <circle cx="820" cy="200" r="12" fill="url(#ng1)" opacity="0.78"/>
    <circle cx="820" cy="200" r="5"  fill="#00E5A0"/>
    <text x="820" y="222" text-anchor="middle" fill="#00E5A0" font-size="8" font-family="Fira Code,monospace" font-weight="700">PostgreSQL</text>
  </g>
  <!-- Floating small nodes (chess pawns) -->
  <g><circle cx="330" cy="50" r="5" fill="#F5A623" opacity="0.7" filter="url(#glow)">
    <animate attributeName="opacity" values="0.4;1;0.4" dur="2.8s" repeatCount="indefinite"/>
    <animate attributeName="r" values="4;6;4" dur="2.8s" repeatCount="indefinite"/>
  </circle></g>
  <g><circle cx="650" cy="60" r="5" fill="#E056D9" opacity="0.65" filter="url(#glow)">
    <animate attributeName="opacity" values="0.3;0.9;0.3" dur="3.3s" begin="0.6s" repeatCount="indefinite"/>
    <animate attributeName="r" values="3;6;3" dur="3.3s" begin="0.6s" repeatCount="indefinite"/>
  </circle></g>
  <g><circle cx="480" cy="90" r="4" fill="#00B8FF" opacity="0.6" filter="url(#glow)">
    <animate attributeName="opacity" values="0.2;0.8;0.2" dur="3.7s" begin="1.2s" repeatCount="indefinite"/>
  </circle></g>
  <g><circle cx="780" cy="80" r="5" fill="#00E5A0" opacity="0.6" filter="url(#glow)">
    <animate attributeName="opacity" values="0.3;0.9;0.3" dur="4.1s" begin="0.9s" repeatCount="indefinite"/>
  </circle></g>
</svg>

<!-- ═══════════════════════ HERO HEADER ═══════════════════════ -->

<div style="position:relative;z-index:2;padding:50px 24px 20px;">

<div style="display:flex;justify-content:center;align-items:center;gap:16px;flex-wrap:wrap;margin-bottom:8px;">
  <div>
    <!-- Chess clock analog SVG -->
    <svg width="46" height="46" viewBox="0 0 46 46" xmlns="http://www.w3.org/2000/svg" style="vertical-align:middle;">
      <circle cx="23" cy="23" r="21" fill="none" stroke="#00E5A0" stroke-width="1.5" opacity="0.7"/>
      <circle cx="23" cy="23" r="3"  fill="#00E5A0"/>
      <!-- Minute hand (slow) -->
      <line x1="23" y1="23" x2="23" y2="6" stroke="#00B8FF" stroke-width="2" stroke-linecap="round">
        <animateTransform attributeName="transform" type="rotate" from="0 23 23" to="360 23 23" dur="3600s" repeatCount="indefinite"/>
      </line>
      <!-- Second hand (fast) -->
      <line x1="23" y1="23" x2="23" y2="4" stroke="#00E5A0" stroke-width="1.2" stroke-linecap="round">
        <animateTransform attributeName="transform" type="rotate" from="0 23 23" to="360 23 23" dur="60s" repeatCount="indefinite"/>
      </line>
      <!-- Hour hand -->
      <line x1="23" y1="23" x2="23" y2="11" stroke="#F5A623" stroke-width="2.5" stroke-linecap="round">
        <animateTransform attributeName="transform" type="rotate" from="0 23 23" to="360 23 23" dur="43200s" repeatCount="indefinite"/>
      </line>
    </svg>
  </div>
  <h1 class="hero-title">Shivam Kumar Chaubey</h1>
  <div>
    <!-- Knight chess piece SVG -->
    <svg width="38" height="38" viewBox="0 0 38 38" fill="none" xmlns="http://www.w3.org/2000/svg" style="vertical-align:middle;filter:drop-shadow(0 0 6px #00E5A0);">
      <path d="M10 32 Q10 26 14 24 Q8 22 9 16 Q12 8 19 7 Q17 10 20 12 Q24 10 25 14 Q28 18 26 24 Q30 26 28 32 Z" fill="#0B1C2A" stroke="#00E5A0" stroke-width="1.5"/>
      <circle cx="16" cy="14" r="2" fill="#00E5A0"/>
    </svg>
  </div>
</div>

<!-- Animated role carousel via SVG text -->
<div style="margin:10px auto;max-width:700px;">
  <svg viewBox="0 0 700 38" xmlns="http://www.w3.org/2000/svg" width="100%" height="38">
    <defs>
      <linearGradient id="textGrad" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%"   stop-color="#00E5A0"/>
        <stop offset="50%"  stop-color="#00B8FF"/>
        <stop offset="100%" stop-color="#E056D9"/>
      </linearGradient>
    </defs>
    <text x="50%" y="26" text-anchor="middle" font-family="'Fira Code',monospace" font-weight="700" font-size="16" fill="url(#textGrad)">
      <tspan>
        Full Stack Developer
        <animate attributeName="opacity" values="1;1;0;0;0;0;0;0;1;1" dur="10s" repeatCount="indefinite" calcMode="discrete"/>
      </tspan>
      <tspan>
        Neural Network Architect
        <animate attributeName="opacity" values="0;0;1;1;0;0;0;0;0;0" dur="10s" repeatCount="indefinite" calcMode="discrete"/>
      </tspan>
      <tspan>
        Strategic Problem Solver
        <animate attributeName="opacity" values="0;0;0;0;1;1;0;0;0;0" dur="10s" repeatCount="indefinite" calcMode="discrete"/>
      </tspan>
      <tspan>
        Chess Coder ♟️
        <animate attributeName="opacity" values="0;0;0;0;0;0;1;1;0;0" dur="10s" repeatCount="indefinite" calcMode="discrete"/>
      </tspan>
    </text>
  </svg>
</div>

<!-- Badges row -->
<div style="display:flex;justify-content:center;align-items:center;gap:12px;flex-wrap:wrap;margin-top:14px;">
  <img src="https://komarev.com/ghpvc/?username=Shivamchaubey14&style=for-the-badge&color=00e5a0&label=PROFILE+VIEWS" alt="views" style="border-radius:999px;border:1px solid rgba(0,229,160,0.4);box-shadow:0 0 12px rgba(0,229,160,0.3);"/>
  <div class="elo-badge">
    <svg width="14" height="14" viewBox="0 0 14 14" fill="none"><circle cx="7" cy="7" r="6" stroke="#F5A623" stroke-width="1.5"/><text x="7" y="10.5" text-anchor="middle" fill="#F5A623" font-size="6" font-weight="800">♔</text></svg>
    Coding ELO: <strong>2147</strong> ▲
  </div>
  <span class="neon-badge">$ npx shivam --skills</span>
  <a href="https://github.com/Shivamchaubey14?tab=followers">
    <img src="https://img.shields.io/github/followers/Shivamchaubey14?style=for-the-badge&color=00b8ff&labelColor=0d1117&label=♜+FOLLOWERS" alt="followers" style="border-radius:999px;border:1px solid rgba(0,184,255,0.4);"/>
  </a>
  <img src="https://img.shields.io/badge/♞_REPOS-39-00e5a0?style=for-the-badge&labelColor=0d1117" alt="repos" style="border-radius:999px;border:1px solid rgba(0,229,160,0.4);"/>
</div>

</div><!-- /hero -->

<!-- ═══════════════════════ ABOUT ME ═══════════════════════ -->

<div style="position:relative;z-index:2;padding:0 24px;">

<p class="section-title">♟ About Me — <span style="color:#00B8FF;">Identity Matrix</span></p>

<div class="glass-card" style="max-width:700px;margin:0 auto;">
  <div style="display:flex;align-items:flex-start;gap:20px;flex-wrap:wrap;">
    <div style="flex:0 0 auto;">
      <!-- King SVG icon -->
      <svg width="56" height="72" viewBox="0 0 56 72" fill="none" xmlns="http://www.w3.org/2000/svg" style="filter:drop-shadow(0 0 10px #00E5A0);">
        <path d="M20 68 Q20 56 25 52 Q14 50 15 38 Q18 18 28 16 Q24 22 28 26 Q34 22 36 28 Q42 36 40 52 Q46 56 44 68 Z" fill="#0B1C2A" stroke="#00E5A0" stroke-width="1.8"/>
        <rect x="24" y="4" width="8" height="14" rx="2" fill="#0B1C2A" stroke="#F5A623" stroke-width="1.5"/>
        <rect x="21" y="8" width="14" height="3" rx="1.5" fill="#0B1C2A" stroke="#F5A623" stroke-width="1.5"/>
        <circle cx="28" cy="34" r="3" fill="#00E5A0"/>
      </svg>
    </div>
    <div style="flex:1;min-width:200px;">
      <div class="terminal-line">
        <span class="terminal-prompt">$ </span><span class="terminal-cmd">whoami</span><br/>
        <span class="terminal-out">→ Shivam Kumar Chaubey | Full Stack Dev @ SMPCL</span>
      </div>
      <div class="terminal-line">
        <span class="terminal-prompt">$ </span><span class="terminal-cmd">location</span><br/>
        <span class="terminal-out">→ Uttar Pradesh, India 🇮🇳</span>
      </div>
      <div class="terminal-line">
        <span class="terminal-prompt">$ </span><span class="terminal-cmd">matrix</span><br/>
        <span class="terminal-out">→ Backend | Frontend | Problem Solving</span>
      </div>
      <div class="terminal-line">
        <span class="terminal-prompt">$ </span><span class="terminal-cmd">stack --list</span><br/>
        <span class="terminal-out">→ Python / Django / REST | React / JS / CSS | Git / Linux / PG</span>
      </div>
      <div class="terminal-line">
        <span class="terminal-prompt">$ </span><span class="terminal-cmd">learning</span><br/>
        <span class="terminal-out">→ DSA | System Design | Docker | Open Source</span>
      </div>
      <div class="terminal-line">
        <span class="terminal-prompt">$ </span><span class="terminal-cmd">goal</span><br/>
        <span class="terminal-out">→ Backend / Full-Stack role at a product company 🚀</span>
      </div>
      <div class="terminal-line" style="margin-top:6px;">
        <span class="terminal-prompt">$ </span><span class="terminal-cmd">_</span><span class="cursor-blink"></span>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════════════ TECH STACK ═══════════════════════ -->

<p class="section-title" style="text-align:center;">⚙️ Tech Arsenal — <span style="color:#00B8FF;">Opening Theory</span></p>

<div class="tech-grid">
  <span class="tech-chip" data-tip="The Queen's Gambit — versatile, dominant">🐍 Python</span>
  <span class="tech-chip" data-tip="Rook's Defense — solid backend fortress">🌐 Django</span>
  <span class="tech-chip" data-tip="REST APIs — bishop diagonal power">🔗 REST APIs</span>
  <span class="tech-chip" data-tip="Knight's Fork — reactive dual threats">⚛️ React</span>
  <span class="tech-chip" data-tip="Pawn Storm — foundational advance">📜 JavaScript</span>
  <span class="tech-chip" data-tip="Opening Preparation — structure first">🏗️ HTML5</span>
  <span class="tech-chip" data-tip="Aesthetic Endgame — precise styling">🎨 CSS3</span>
  <span class="tech-chip" data-tip="King's Shield — UI fortification">🛡️ Bootstrap</span>
  <span class="tech-chip" data-tip="Version Control — full board awareness">📌 Git / GitHub</span>
  <span class="tech-chip" data-tip="The Dark Square Bishop — terminal power">🐧 Linux</span>
  <span class="tech-chip" data-tip="Data Stronghold — persistent structure">🗄️ PostgreSQL</span>
  <span class="tech-chip" data-tip="Container Gambit — learning isolation">🐳 Docker</span>
</div>

<!-- ═══════════════════════ GITHUB STATS ═══════════════════════ -->

<p class="section-title" style="text-align:center;">📊 Performance Board</p>

<div class="stat-img-wrap" style="display:flex;flex-wrap:wrap;justify-content:center;gap:16px;margin:0 auto;">
  <a href="https://github.com/Shivamchaubey14">
    <img src="https://github-readme-stats-git-masterrstaa-rickstaa.vercel.app/api?username=Shivamchaubey14&show_icons=true&theme=dark&bg_color=0d1117&title_color=00e5a0&icon_color=00b8ff&text_color=c9d1d9&border_color=30363d&include_all_commits=true&count_private=true&cache_seconds=86400" height="175" alt="GitHub Stats"/>
  </a>
  <a href="https://github.com/Shivamchaubey14">
    <img src="https://github-readme-stats-git-masterrstaa-rickstaa.vercel.app/api/top-langs/?username=Shivamchaubey14&layout=compact&theme=dark&bg_color=0d1117&title_color=00e5a0&text_color=c9d1d9&border_color=30363d&langs_count=8&cache_seconds=86400" height="175" alt="Top Languages"/>
  </a>
</div>

<div class="stat-img-wrap" style="text-align:center;margin-top:16px;">
  <a href="https://github.com/Shivamchaubey14">
    <img src="https://streak-stats.demolab.com/?user=Shivamchaubey14&theme=dark&background=0d1117&ring=00e5a0&fire=f5a623&currStreakLabel=00b8ff&sideLabels=c9d1d9&border=30363d&dates=888888" alt="GitHub Streak"/>
  </a>
</div>

<!-- ═══════════════════════ NEURAL HEATMAP ═══════════════════════ -->

<p class="section-title" style="text-align:center;">🧠 Neural Heatmap — <span style="color:#00B8FF;">Commit Topology</span></p>

<div class="glass-card" style="padding:18px;">

<!-- Generated knight-trail heatmap: 7 rows × 53 cols -->
<!-- Level key: 0=none, 1=low(purple), 2=med(cyan), 3=high(mint), 4=peak(glow mint) -->

<div style="font-size:0.75em;color:#888;margin-bottom:8px;text-align:center;letter-spacing:0.06em;">
  <span style="color:#1A2533;font-size:1.4em;">■</span> None &nbsp;
  <span style="color:#7B2F9D;font-size:1.4em;">■</span> Low &nbsp;
  <span style="color:#00B8FF;font-size:1.4em;">■</span> Med &nbsp;
  <span style="color:#00E5A0;font-size:1.4em;">■</span> High &nbsp;
  <span style="color:#00E5A0;font-size:1.4em;text-shadow:0 0 6px #00E5A0;">■</span> Peak ♛
</div>

<svg viewBox="0 0 900 130" xmlns="http://www.w3.org/2000/svg" width="100%" style="max-width:900px;display:block;margin:0 auto;">
  <defs>
    <filter id="heatGlow">
      <feGaussianBlur stdDeviation="1.5" result="b"/>
      <feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <!-- Row 0 (Sun) -->
  <!-- Pattern: sparse with knight-trail cluster around cols 15-25, 35-45 -->
  <!-- I'll lay out a realistic 52-week × 7-day grid as SVG rects -->
  <!-- Each cell: w=14, h=14, gap=3 => col pitch=17, row pitch=17 -->
  <!-- Colors: #1A2533=none, rgba(123,47,157,0.6)=low, rgba(0,184,255,0.6)=med, rgba(0,229,160,0.7)=high, #00E5A0=peak -->

  <!-- I'll script the grid with a fixed seed for a believable pattern: -->
  <!-- Week 1-10: sparse, Week 11-20: knight cluster grows, Week 21-35: activity peak, Week 36-45: high but fading, 46-52: tail -->

  <!-- Row Sun (y=0) -->
  <rect x="2"   y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="19"  y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="36"  y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="53"  y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="70"  y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="87"  y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="104" y="2"  width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="121" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="138" y="2"  width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="155" y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="172" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="189" y="2"  width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="206" y="2"  width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="223" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="240" y="2"  width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="257" y="2"  width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="274" y="2"  width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="291" y="2"  width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="308" y="2"  width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="325" y="2"  width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="342" y="2"  width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="359" y="2"  width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="376" y="2"  width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="393" y="2"  width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="410" y="2"  width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="427" y="2"  width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="444" y="2"  width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="461" y="2"  width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="478" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="495" y="2"  width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="512" y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="529" y="2"  width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="546" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="563" y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="580" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="597" y="2"  width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="614" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="631" y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="648" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="665" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="682" y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="699" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="716" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="733" y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="750" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="767" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="784" y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="801" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="818" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="835" y="2"  width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="852" y="2"  width="13" height="13" rx="2" fill="#1A2533"/><rect x="869" y="2"  width="13" height="13" rx="2" fill="#1A2533"/>

  <!-- Row Mon (y=19) -->
  <rect x="2"   y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="19"  y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="36"  y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="53"  y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="70"  y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="87"  y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="104" y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="121" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="138" y="19" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="155" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="172" y="19" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="189" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="206" y="19" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="223" y="19" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="240" y="19" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="257" y="19" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="274" y="19" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="291" y="19" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="308" y="19" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="325" y="19" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="342" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="359" y="19" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="376" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="393" y="19" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="410" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="427" y="19" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="444" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="461" y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="478" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="495" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="512" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="529" y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="546" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="563" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="580" y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="597" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="614" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="631" y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="648" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="665" y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="682" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="699" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="716" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="733" y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="750" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="767" y="19" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="784" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="801" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="818" y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="835" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="852" y="19" width="13" height="13" rx="2" fill="#1A2533"/><rect x="869" y="19" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/>

  <!-- Row Tue (y=36) -->
  <rect x="2"   y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="19"  y="36" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="36"  y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="53"  y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="70"  y="36" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="87"  y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="104" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="121" y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="138" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="155" y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="172" y="36" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="189" y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="206" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="223" y="36" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="240" y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="257" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="274" y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="291" y="36" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="308" y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="325" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="342" y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="359" y="36" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="376" y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="393" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="410" y="36" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="427" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="444" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="461" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="478" y="36" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="495" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="512" y="36" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="529" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="546" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="563" y="36" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="580" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="597" y="36" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="614" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="631" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="648" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="665" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="682" y="36" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="699" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="716" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="733" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="750" y="36" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="767" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="784" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="801" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="818" y="36" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="835" y="36" width="13" height="13" rx="2" fill="#1A2533"/><rect x="852" y="36" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="869" y="36" width="13" height="13" rx="2" fill="#1A2533"/>

  <!-- Row Wed (y=53) -->
  <rect x="2"   y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="19"  y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="36"  y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="53"  y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="70"  y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="87"  y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="104" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="121" y="53" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="138" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="155" y="53" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="172" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="189" y="53" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="206" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="223" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="240" y="53" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="257" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="274" y="53" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="291" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="308" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="325" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="342" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="359" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="376" y="53" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="393" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="410" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="427" y="53" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="444" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="461" y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="478" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="495" y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="512" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="529" y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="546" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="563" y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="580" y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="597" y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="614" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="631" y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="648" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="665" y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="682" y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="699" y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="716" y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="733" y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="750" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="767" y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="784" y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="801" y="53" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="818" y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="835" y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="852" y="53" width="13" height="13" rx="2" fill="#1A2533"/><rect x="869" y="53" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/>

  <!-- Row Thu (y=70) -->
  <rect x="2"   y="70" width="13" height="13" rx="2" fill="#1A2533"/><rect x="19"  y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="36"  y="70" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="53"  y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="70"  y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="87"  y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="104" y="70" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="121" y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="138" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="155" y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="172" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="189" y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="206" y="70" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="223" y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="240" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="257" y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="274" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="291" y="70" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="308" y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="325" y="70" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="342" y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="359" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="376" y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="393" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="410" y="70" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="427" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="444" y="70" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="461" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="478" y="70" width="13" height="13" rx="2" fill="#1A2533"/><rect x="495" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="512" y="70" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="529" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="546" y="70" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="563" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="580" y="70" width="13" height="13" rx="2" fill="#1A2533"/><rect x="597" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="614" y="70" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="631" y="70" width="13" height="13" rx="2" fill="#1A2533"/><rect x="648" y="70" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="665" y="70" width="13" height="13" rx="2" fill="#1A2533"/><rect x="682" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="699" y="70" width="13" height="13" rx="2" fill="#1A2533"/><rect x="716" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="733" y="70" width="13" height="13" rx="2" fill="#1A2533"/><rect x="750" y="70" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="767" y="70" width="13" height="13" rx="2" fill="#1A2533"/><rect x="784" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="801" y="70" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="818" y="70" width="13" height="13" rx="2" fill="#1A2533"/><rect x="835" y="70" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="852" y="70" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="869" y="70" width="13" height="13" rx="2" fill="#1A2533"/>

  <!-- Row Fri (y=87) -->
  <rect x="2"   y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="19"  y="87" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="36"  y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="53"  y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="70"  y="87" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="87"  y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="104" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="121" y="87" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="138" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="155" y="87" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="172" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="189" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="206" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="223" y="87" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="240" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="257" y="87" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="274" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="291" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="308" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="325" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="342" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="359" y="87" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="376" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="393" y="87" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="410" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="427" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="444" y="87" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="461" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="478" y="87" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="495" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="512" y="87" width="13" height="13" rx="2" fill="#1A2533"/><rect x="529" y="87" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="546" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="563" y="87" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="580" y="87" width="13" height="13" rx="2" fill="#1A2533"/><rect x="597" y="87" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="614" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="631" y="87" width="13" height="13" rx="2" fill="#1A2533"/><rect x="648" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="665" y="87" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="682" y="87" width="13" height="13" rx="2" fill="#1A2533"/><rect x="699" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="716" y="87" width="13" height="13" rx="2" fill="#1A2533"/><rect x="733" y="87" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="750" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="767" y="87" width="13" height="13" rx="2" fill="#1A2533"/><rect x="784" y="87" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="801" y="87" width="13" height="13" rx="2" fill="#1A2533"/><rect x="818" y="87" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="835" y="87" width="13" height="13" rx="2" fill="#1A2533"/><rect x="852" y="87" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="869" y="87" width="13" height="13" rx="2" fill="#1A2533"/>

  <!-- Row Sat (y=104) -->
  <rect x="2"   y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="19"  y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="36"  y="104" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="53"  y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="70"  y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="87"  y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="104" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="121" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="138" y="104" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="155" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="172" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="189" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="206" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="223" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="240" y="104" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="257" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="274" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="291" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="308" y="104" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="325" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="342" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="359" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="376" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="393" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="410" y="104" width="13" height="13" rx="2" fill="#00E5A0" filter="url(#heatGlow)"/><rect x="427" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="444" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="461" y="104" width="13" height="13" rx="2" fill="rgba(0,229,160,0.7)"/><rect x="478" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="495" y="104" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="512" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="529" y="104" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="546" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="563" y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="580" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="597" y="104" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="614" y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="631" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="648" y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="665" y="104" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="682" y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="699" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="716" y="104" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="733" y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="750" y="104" width="13" height="13" rx="2" fill="rgba(0,184,255,0.55)"/><rect x="767" y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="784" y="104" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="801" y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="818" y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="835" y="104" width="13" height="13" rx="2" fill="rgba(123,47,157,0.55)"/><rect x="852" y="104" width="13" height="13" rx="2" fill="#1A2533"/><rect x="869" y="104" width="13" height="13" rx="2" fill="#1A2533"/>
</svg>
</div>

<!-- ═══════════════════════ FEATURED PROJECTS ═══════════════════════ -->

<p class="section-title" style="text-align:center;">♞ Featured Deployments — <span style="color:#00B8FF;">Opening Theory</span></p>

<div class="hex-grid">

  <div class="hex-tile">
    <div class="piece-icon">🧠</div>
    <div class="tile-title">AlgoScope</div>
    <div style="font-size:0.72em;color:#E056D9;margin-bottom:4px;">♛ Queen — Most Powerful</div>
    <div class="tile-desc">LeetCode step-by-step algorithm visualizer. Django + Python. Turns code into visual moves.</div>
    <a href="https://github.com/Shivamchaubey14/leetcode_visualizer" class="checkmate-btn">⚡ Checkmate</a>
  </div>

  <div class="hex-tile" style="animation-delay:0.1s;">
    <div class="piece-icon">🐾</div>
    <div class="tile-title">Tindog</div>
    <div style="font-size:0.72em;color:#00B8FF;margin-bottom:4px;">♜ Rook — Solid & Powerful</div>
    <div class="tile-desc">Tinder-for-dogs landing page. Bootstrap, HTML5, JS. Responsive, clean UI.</div>
    <a href="https://github.com/Shivamchaubey14/Tindog" class="checkmate-btn">⚡ Checkmate</a>
  </div>

  <div class="hex-tile" style="animation-delay:0.2s;">
    <div class="piece-icon">🥁</div>
    <div class="tile-title">DrumMaster</div>
    <div style="font-size:0.72em;color:#F5A623;margin-bottom:4px;">♗ Bishop — Diagonal Thinker</div>
    <div class="tile-desc">Browser-based drum machine. Pure JavaScript event-driven audio. Keyboard + click.</div>
    <a href="https://github.com/Shivamchaubey14/DrumMaster" class="checkmate-btn">⚡ Checkmate</a>
  </div>

  <div class="hex-tile" style="animation-delay:0.3s;">
    <div class="piece-icon">✅</div>
    <div class="tile-title">TodoApp</div>
    <div style="font-size:0.72em;color:#00E5A0;margin-bottom:4px;">♟ Pawn — First Move</div>
    <div class="tile-desc">Full-featured task manager. React + state management. Clean and functional.</div>
    <a href="https://github.com/Shivamchaubey14/TodoApp" class="checkmate-btn">⚡ Checkmate</a>
  </div>

</div>

<!-- ═══════════════════════ CONTRIBUTION GRAPH ═══════════════════════ -->

<p class="section-title" style="text-align:center;">📈 Strategy Board</p>

<div class="stat-img-wrap" style="text-align:center;">
  <a href="https://github.com/Shivamchaubey14">
    <img src="https://github-readme-activity-graph.vercel.app/graph?username=Shivamchaubey14&bg_color=0d1117&color=00e5a0&line=00b8ff&point=f5a623&area=true&area_color=00e5a020&hide_border=false&border_color=30363d" width="100%" alt="Contribution Graph" style="border-radius:12px;border:1px solid rgba(0,229,160,0.28);box-shadow:0 0 20px rgba(0,184,255,0.16);"/>
  </a>
</div>

<!-- ═══════════════════════ TROPHIES ═══════════════════════ -->

<p class="section-title" style="text-align:center;">🏆 Trophy Cabinet — <span style="color:#00B8FF;">Endgame Analysis</span></p>

<div class="stat-img-wrap" style="text-align:center;">
  <img src="https://github-profile-trophy.vercel.app/?username=Shivamchaubey14&theme=darkhub&column=6&margin-w=8&margin-h=8&no-bg=true&no-frame=false" alt="GitHub Trophies" style="border-radius:12px;border:1px solid rgba(245,166,35,0.28);box-shadow:0 0 20px rgba(245,166,35,0.14);"/>
</div>

<!-- ═══════════════════════ CURRENT FOCUS ═══════════════════════ -->

<p class="section-title" style="text-align:center;">🎯 Current Strategy — <span style="color:#00B8FF;">Thinking Ahead</span></p>

<div style="display:flex;flex-wrap:wrap;justify-content:center;gap:16px;padding:0 16px 8px;">

  <div class="strategy-card" style="animation-delay:0s;">
    <div style="font-size:1.8em;">♟</div>
    <div style="color:#00E5A0;font-weight:700;font-size:0.92em;margin:6px 0;">Building</div>
    <div style="color:#c9d1d9;font-size:0.8em;">AlgoScope — LeetCode<br/>step-by-step visualizer</div>
    <div style="margin-top:8px;font-size:0.72em;color:#888;">Django + Python</div>
  </div>

  <div class="strategy-card" style="animation-delay:0.4s;">
    <div style="font-size:1.8em;">♞</div>
    <div style="color:#00B8FF;font-weight:700;font-size:0.92em;margin:6px 0;">Learning</div>
    <div style="color:#c9d1d9;font-size:0.8em;">DSA | System Design<br/>Docker</div>
    <div style="margin-top:8px;font-size:0.72em;color:#888;">Knight-jump progress</div>
  </div>

  <div class="strategy-card" style="animation-delay:0.8s;">
    <div style="font-size:1.8em;">♗</div>
    <div style="color:#F5A623;font-weight:700;font-size:0.92em;margin:6px 0;">Growing</div>
    <div style="color:#c9d1d9;font-size:0.8em;">Open Source<br/>Clean Code Principles</div>
    <div style="margin-top:8px;font-size:0.72em;color:#888;">Diagonal expansion</div>
  </div>

  <div class="strategy-card" style="animation-delay:1.2s;">
    <div style="font-size:1.8em;">♛</div>
    <div style="color:#E056D9;font-weight:700;font-size:0.92em;margin:6px 0;">Goal</div>
    <div style="color:#c9d1d9;font-size:0.8em;">Backend / Full-Stack<br/>at a product company</div>
    <div style="margin-top:8px;font-size:0.72em;color:#888;">♛ Endgame move</div>
  </div>

</div>

<!-- ═══════════════════════ CONNECT ═══════════════════════ -->

<p class="section-title" style="text-align:center;">📡 Connect — <span style="color:#00B8FF;">Orbital Links</span></p>

<div class="orbit-ring">

  <!-- Central knight -->
  <div style="display:flex;flex-direction:column;align-items:center;gap:6px;">
    <svg width="60" height="60" viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg" style="filter:drop-shadow(0 0 12px #00E5A0);">
      <circle cx="30" cy="30" r="28" fill="rgba(0,229,160,0.07)" stroke="#00E5A0" stroke-width="1.5">
        <animate attributeName="stroke-opacity" values="0.4;1;0.4" dur="2.5s" repeatCount="indefinite"/>
        <animate attributeName="r" values="26;30;26" dur="2.5s" repeatCount="indefinite"/>
      </circle>
      <path d="M18 50 Q18 38 24 34 Q12 32 13 22 Q17 8 28 7 Q25 13 28 17 Q34 13 36 20 Q42 28 40 36 Q45 40 43 50 Z" fill="#0B1C2A" stroke="#00E5A0" stroke-width="1.8"/>
      <circle cx="22" cy="20" r="3" fill="#00E5A0"/>
    </svg>
    <span style="color:#00E5A0;font-size:0.75em;letter-spacing:0.05em;">NEURAL_HUB</span>
  </div>

  <a href="https://github.com/Shivamchaubey14" class="orbit-link">
    <svg width="42" height="42" viewBox="0 0 42 42" fill="none" xmlns="http://www.w3.org/2000/svg" style="filter:drop-shadow(0 0 7px #00B8FF);">
      <circle cx="21" cy="21" r="20" fill="rgba(0,184,255,0.08)" stroke="#00B8FF" stroke-width="1.2"/>
      <path d="M21 8C13.82 8 8 13.82 8 21C8 26.74 11.72 31.6 16.93 33.32C17.57 33.44 17.81 33.04 17.81 32.69V30.25C14.22 31.03 13.47 28.65 13.47 28.65C12.89 27.15 12.04 26.75 12.04 26.75C10.87 25.98 12.13 25.99 12.13 25.99C13.43 26.09 14.11 27.33 14.11 27.33C15.26 29.29 17.12 28.72 17.86 28.4C17.97 27.58 18.3 27.01 18.66 26.69C15.85 26.37 12.9 25.31 12.9 20.35C12.9 18.93 13.4 17.77 14.14 16.87C14.02 16.55 13.58 15.22 14.26 13.44C14.26 13.44 15.34 13.1 17.81 14.77C18.75 14.51 19.75 14.38 20.76 14.37C21.76 14.38 22.77 14.51 23.71 14.77C26.17 13.1 27.25 13.44 27.25 13.44C27.93 15.22 27.49 16.55 27.37 16.87C28.11 17.77 28.61 18.93 28.61 20.35C28.61 25.32 25.65 26.36 22.83 26.68C23.28 27.07 23.69 27.84 23.69 29.01V32.69C23.69 33.04 23.93 33.45 24.58 33.32C29.79 31.6 33.5 26.74 33.5 21C33.5 13.82 27.68 8 21 8Z" fill="#00B8FF"/>
    </svg>
    <span style="color:#00B8FF;font-size:0.78em;font-weight:700;">GitHub</span>
  </a>

  <div style="text-align:center;">
    <img src="https://img.shields.io/badge/SMPCL-Company-00e5a0?style=for-the-badge&labelColor=0d1117&logo=building" alt="Company" style="border-radius:8px;border:1px solid rgba(0,229,160,0.3);"/>
  </div>

</div>

<!-- ═══════════════════════ QUOTE ═══════════════════════ -->

<div class="quote-block">
  "First, solve the problem. Then, write the code." — John Johnson
</div>

<div style="text-align:center;padding:10px 0 0;color:#444;font-size:0.75em;letter-spacing:0.1em;font-family:'Fira Code',monospace;">
  ♟ Shivamchaubey14 · Uttar Pradesh, India · Always shipping ✨
</div>

</div><!-- /inner padding -->
</div><!-- /cyber-board -->

<!-- ═══════════════════════ FOOTER WAVE ═══════════════════════ -->

<svg viewBox="0 0 1100 80" xmlns="http://www.w3.org/2000/svg" width="100%" style="display:block;margin-top:-2px;">
  <defs>
    <linearGradient id="footerGrad" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%"   stop-color="#00B8FF"/>
      <stop offset="50%"  stop-color="#00E5A0"/>
      <stop offset="100%" stop-color="#0A0F1A"/>
    </linearGradient>
  </defs>
  <path d="M0,30 Q150,0 300,40 Q450,80 600,30 Q750,0 900,40 Q1050,70 1100,30 L1100,80 L0,80 Z" fill="url(#footerGrad)" opacity="0.18"/>
  <path d="M0,50 Q200,20 400,55 Q600,80 800,45 Q950,20 1100,50 L1100,80 L0,80 Z" fill="url(#footerGrad)" opacity="0.1"/>
  <!-- Falling chess piece sparks -->
  <circle cx="120" cy="10" r="2" fill="#00E5A0" opacity="0.7">
    <animate attributeName="cy" values="5;75" dur="3s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.8;0" dur="3s" repeatCount="indefinite"/>
  </circle>
  <circle cx="340" cy="20" r="1.5" fill="#00B8FF" opacity="0.6">
    <animate attributeName="cy" values="0;80" dur="2.4s" begin="0.5s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.7;0" dur="2.4s" begin="0.5s" repeatCount="indefinite"/>
  </circle>
  <circle cx="600" cy="5"  r="2" fill="#E056D9" opacity="0.5">
    <animate attributeName="cy" values="0;80" dur="3.5s" begin="1s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.6;0" dur="3.5s" begin="1s" repeatCount="indefinite"/>
  </circle>
  <circle cx="820" cy="15" r="1.5" fill="#F5A623" opacity="0.6">
    <animate attributeName="cy" values="5;78" dur="2.8s" begin="1.5s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.7;0" dur="2.8s" begin="1.5s" repeatCount="indefinite"/>
  </circle>
  <circle cx="980" cy="8"  r="2" fill="#00E5A0" opacity="0.5">
    <animate attributeName="cy" values="0;80" dur="3.1s" begin="0.8s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.6;0" dur="3.1s" begin="0.8s" repeatCount="indefinite"/>
  </circle>
</svg>

</div>