<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GigShield — DEVTrails 2026 README</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --g0: #000000;
    --g1: #030a03;
    --g2: #061206;
    --g3: #0a1f0a;
    --green: #00ff41;
    --green-dim: #00c432;
    --green-ghost: rgba(0,255,65,0.07);
    --green-glow: rgba(0,255,65,0.25);
    --green-mid: #39ff84;
    --accent: #b8ff6a;
    --warn: #ffea00;
    --red: #ff3c3c;
    --text: #d4f5d4;
    --text-dim: #6b9e6b;
    --text-muted: #3a5c3a;
    --border: rgba(0,255,65,0.15);
    --border-bright: rgba(0,255,65,0.4);
    --mono: 'Space Mono', monospace;
    --display: 'Syne', sans-serif;
    --body: 'DM Sans', sans-serif;
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--g0);
    color: var(--text);
    font-family: var(--body);
    font-size: 15px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* SCANLINE OVERLAY */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.07) 2px,
      rgba(0,0,0,0.07) 4px
    );
    pointer-events: none;
    z-index: 9999;
  }

  /* NOISE TEXTURE */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.035'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 9998;
    opacity: 0.6;
  }

  /* ===== HERO ===== */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 80px 60px 60px;
    position: relative;
    overflow: hidden;
    border-bottom: 1px solid var(--border-bright);
  }

  .hero-bg-grid {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(var(--border) 1px, transparent 1px),
      linear-gradient(90deg, var(--border) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 70% at 50% 50%, black 30%, transparent 100%);
    animation: gridPulse 8s ease-in-out infinite;
  }

  @keyframes gridPulse {
    0%,100% { opacity: 0.4; }
    50% { opacity: 0.9; }
  }

  .hero-orb {
    position: absolute;
    width: 700px;
    height: 700px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(0,255,65,0.12) 0%, transparent 70%);
    top: -200px;
    right: -200px;
    animation: orbFloat 10s ease-in-out infinite;
  }

  @keyframes orbFloat {
    0%,100% { transform: translate(0,0) scale(1); }
    50% { transform: translate(-40px, 40px) scale(1.08); }
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-family: var(--mono);
    font-size: 11px;
    color: var(--green);
    border: 1px solid var(--green-dim);
    padding: 5px 12px;
    border-radius: 2px;
    margin-bottom: 32px;
    background: var(--green-ghost);
    letter-spacing: 0.1em;
    width: fit-content;
    animation: badgeBlink 3s infinite;
  }

  @keyframes badgeBlink {
    0%,90%,100% { border-color: var(--green-dim); }
    95% { border-color: var(--green); box-shadow: 0 0 10px var(--green-glow); }
  }

  .badge-dot {
    width: 6px; height: 6px;
    background: var(--green);
    border-radius: 50%;
    animation: dotPulse 1.5s ease-in-out infinite;
  }

  @keyframes dotPulse {
    0%,100% { opacity:1; transform:scale(1); }
    50% { opacity:0.4; transform:scale(0.7); }
  }

  .hero h1 {
    font-family: var(--display);
    font-size: clamp(52px, 9vw, 110px);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.03em;
    color: #fff;
    position: relative;
    z-index: 2;
    margin-bottom: 8px;
  }

  .hero h1 .green { color: var(--green); text-shadow: 0 0 40px var(--green-glow); }

  .hero-sub {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--text-dim);
    letter-spacing: 0.06em;
    margin-bottom: 40px;
    z-index: 2;
    position: relative;
  }

  .hero-tagline {
    font-family: var(--display);
    font-size: clamp(18px, 2.5vw, 26px);
    font-weight: 600;
    color: var(--accent);
    max-width: 700px;
    line-height: 1.3;
    z-index: 2;
    position: relative;
    margin-bottom: 48px;
  }

  .hero-stats {
    display: flex;
    gap: 48px;
    flex-wrap: wrap;
    z-index: 2;
    position: relative;
  }

  .stat {
    display: flex;
    flex-direction: column;
  }

  .stat-num {
    font-family: var(--display);
    font-size: 36px;
    font-weight: 800;
    color: var(--green);
    line-height: 1;
    text-shadow: 0 0 20px rgba(0,255,65,0.4);
  }

  .stat-label {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--text-muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-top: 4px;
  }

  /* ===== LAYOUT ===== */
  .container {
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 60px;
  }

  section {
    padding: 80px 60px;
    border-bottom: 1px solid var(--border);
    max-width: 1200px;
    margin: 0 auto;
  }

  /* ===== SECTION HEADERS ===== */
  .section-label {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--green);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border-bright);
    max-width: 80px;
  }

  .section-title {
    font-family: var(--display);
    font-size: clamp(28px, 4vw, 46px);
    font-weight: 800;
    color: #fff;
    line-height: 1.1;
    margin-bottom: 16px;
    letter-spacing: -0.02em;
  }

  .section-title .green { color: var(--green); }
  .section-title .accent { color: var(--accent); }

  .section-desc {
    color: var(--text-dim);
    max-width: 620px;
    font-size: 15px;
    margin-bottom: 48px;
  }

  /* ===== PROBLEM SECTION ===== */
  .problem-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    background: var(--border);
    border: 1px solid var(--border-bright);
    margin-top: 40px;
  }

  .problem-card {
    background: var(--g1);
    padding: 36px;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }

  .problem-card:hover { background: var(--g2); }

  .problem-card::before {
    content: attr(data-num);
    position: absolute;
    top: -20px;
    right: 20px;
    font-family: var(--display);
    font-size: 100px;
    font-weight: 800;
    color: rgba(0,255,65,0.04);
    line-height: 1;
    pointer-events: none;
  }

  .problem-icon {
    font-size: 28px;
    margin-bottom: 16px;
  }

  .problem-title {
    font-family: var(--display);
    font-size: 18px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 10px;
  }

  .problem-text {
    color: var(--text-dim);
    font-size: 14px;
    line-height: 1.6;
  }

  .highlight-box {
    background: var(--green-ghost);
    border: 1px solid var(--border-bright);
    border-left: 3px solid var(--green);
    padding: 24px 28px;
    margin: 40px 0;
    position: relative;
  }

  .highlight-box p {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--green);
    line-height: 1.8;
  }

  /* ===== PERSONA ===== */
  .persona-card {
    background: var(--g1);
    border: 1px solid var(--border-bright);
    padding: 40px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    margin-top: 40px;
    position: relative;
    overflow: hidden;
  }

  .persona-card::after {
    content: 'ZOMATO / SWIGGY';
    position: absolute;
    top: 20px;
    right: 28px;
    font-family: var(--mono);
    font-size: 10px;
    color: var(--text-muted);
    letter-spacing: 0.15em;
  }

  .persona-name {
    font-family: var(--display);
    font-size: 32px;
    font-weight: 800;
    color: var(--green);
    margin-bottom: 8px;
  }

  .persona-desc {
    color: var(--text-dim);
    font-size: 14px;
    margin-bottom: 24px;
  }

  .tag-list {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tag {
    font-family: var(--mono);
    font-size: 11px;
    padding: 4px 10px;
    border: 1px solid var(--border-bright);
    color: var(--green-dim);
    border-radius: 2px;
    background: var(--green-ghost);
  }

  .scenario-list {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .scenario {
    padding: 16px 20px;
    border-left: 2px solid var(--green-dim);
    background: var(--g2);
  }

  .scenario-trigger {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--green);
    margin-bottom: 4px;
    letter-spacing: 0.05em;
  }

  .scenario-desc {
    font-size: 13px;
    color: var(--text-dim);
  }

  /* ===== WORKFLOW ===== */
  .flow-steps {
    display: flex;
    flex-direction: column;
    gap: 0;
    margin-top: 40px;
    position: relative;
  }

  .flow-steps::before {
    content: '';
    position: absolute;
    left: 23px;
    top: 0;
    bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, var(--green), transparent);
  }

  .flow-step {
    display: flex;
    gap: 24px;
    padding: 0 0 36px 0;
    position: relative;
  }

  .flow-num {
    width: 47px;
    height: 47px;
    min-width: 47px;
    border: 1px solid var(--green-dim);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--mono);
    font-size: 14px;
    font-weight: 700;
    color: var(--green);
    background: var(--g0);
    z-index: 2;
    position: relative;
    transition: all 0.3s;
  }

  .flow-step:hover .flow-num {
    background: var(--green);
    color: var(--g0);
    box-shadow: 0 0 20px var(--green-glow);
  }

  .flow-content { padding-top: 8px; }

  .flow-title {
    font-family: var(--display);
    font-size: 18px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 8px;
  }

  .flow-desc {
    color: var(--text-dim);
    font-size: 14px;
    line-height: 1.7;
  }

  .flow-tag {
    display: inline-block;
    font-family: var(--mono);
    font-size: 10px;
    padding: 2px 8px;
    background: var(--green-ghost);
    border: 1px solid var(--border-bright);
    color: var(--green-dim);
    margin-top: 8px;
    letter-spacing: 0.08em;
  }

  /* ===== PREMIUM MODEL ===== */
  .premium-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    background: var(--border);
    border: 1px solid var(--border-bright);
    margin: 40px 0;
  }

  .premium-tier {
    background: var(--g1);
    padding: 32px;
    text-align: center;
    position: relative;
    transition: background 0.3s;
  }

  .premium-tier.featured {
    background: var(--g2);
  }

  .premium-tier.featured::before {
    content: 'MOST POPULAR';
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    font-family: var(--mono);
    font-size: 9px;
    letter-spacing: 0.15em;
    color: var(--g0);
    background: var(--green);
    padding: 3px 10px;
  }

  .tier-name {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--text-muted);
    letter-spacing: 0.15em;
    margin-bottom: 16px;
    text-transform: uppercase;
  }

  .tier-price {
    font-family: var(--display);
    font-size: 42px;
    font-weight: 800;
    color: var(--green);
    line-height: 1;
    margin-bottom: 4px;
  }

  .tier-period {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--text-muted);
    margin-bottom: 20px;
  }

  .tier-coverage {
    font-size: 22px;
    font-weight: 700;
    font-family: var(--display);
    color: #fff;
    margin-bottom: 4px;
  }

  .tier-desc {
    font-size: 12px;
    color: var(--text-dim);
  }

  .premium-formula {
    background: var(--g1);
    border: 1px solid var(--border-bright);
    padding: 32px;
    font-family: var(--mono);
    font-size: 13px;
    color: var(--green);
    line-height: 2;
    margin-top: 0;
  }

  .premium-formula .comment { color: var(--text-muted); }
  .premium-formula .var { color: var(--accent); }
  .premium-formula .val { color: var(--green-mid); }

  /* ===== TRIGGERS ===== */
  .triggers-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
    margin-top: 40px;
  }

  .trigger-card {
    background: var(--g1);
    border: 1px solid var(--border);
    padding: 28px;
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
    cursor: default;
  }

  .trigger-card:hover {
    border-color: var(--border-bright);
    transform: translateY(-2px);
  }

  .trigger-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 2px;
    background: var(--green);
    transform: scaleX(0);
    transition: transform 0.3s;
    transform-origin: left;
  }

  .trigger-card:hover::before { transform: scaleX(1); }

  .trigger-type {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--text-muted);
    letter-spacing: 0.15em;
    margin-bottom: 12px;
    text-transform: uppercase;
  }

  .trigger-name {
    font-family: var(--display);
    font-size: 20px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 8px;
  }

  .trigger-threshold {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--green);
    padding: 6px 12px;
    background: var(--green-ghost);
    border: 1px solid var(--border);
    display: inline-block;
    margin-bottom: 12px;
  }

  .trigger-desc {
    font-size: 13px;
    color: var(--text-dim);
    line-height: 1.6;
  }

  /* ===== AI/ML STACK ===== */
  .ml-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    background: var(--border);
    border: 1px solid var(--border-bright);
    margin-top: 40px;
  }

  .ml-card {
    background: var(--g1);
    padding: 32px;
    transition: background 0.3s;
  }

  .ml-card:hover { background: var(--g2); }

  .ml-icon {
    font-size: 24px;
    margin-bottom: 16px;
  }

  .ml-title {
    font-family: var(--display);
    font-size: 16px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 10px;
  }

  .ml-model {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--green);
    letter-spacing: 0.1em;
    margin-bottom: 12px;
    padding: 3px 8px;
    border: 1px solid var(--border);
    display: inline-block;
    background: var(--green-ghost);
  }

  .ml-desc {
    font-size: 13px;
    color: var(--text-dim);
    line-height: 1.6;
  }

  /* ===== 🚨 ADVERSARIAL DEFENSE — THE CROWN JEWEL ===== */
  .adversarial {
    background: linear-gradient(135deg, #0a0000 0%, #050a05 50%, #000 100%);
    border-top: 2px solid var(--red);
    border-bottom: 2px solid var(--green);
  }

  .threat-banner {
    background: var(--red);
    color: #000;
    font-family: var(--mono);
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.2em;
    padding: 10px 20px;
    text-align: center;
    margin-bottom: 48px;
    animation: threatBlink 2s step-end infinite;
  }

  @keyframes threatBlink {
    0%,100% { background: var(--red); }
    50% { background: #cc0000; }
  }

  .adversarial .section-title { color: var(--red); }

  .threat-scenario {
    background: rgba(255,60,60,0.06);
    border: 1px solid rgba(255,60,60,0.25);
    border-left: 3px solid var(--red);
    padding: 28px;
    margin-bottom: 48px;
    font-family: var(--mono);
    font-size: 12px;
    color: #ff9999;
    line-height: 1.9;
  }

  .defense-layer {
    margin-bottom: 48px;
  }

  .defense-layer-title {
    font-family: var(--display);
    font-size: 22px;
    font-weight: 800;
    color: var(--green);
    margin-bottom: 6px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .layer-num {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--g0);
    background: var(--green);
    padding: 2px 8px;
    letter-spacing: 0.1em;
  }

  .defense-layer-sub {
    font-size: 13px;
    color: var(--text-muted);
    margin-bottom: 24px;
    font-family: var(--mono);
  }

  .signal-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
  }

  .signal-card {
    background: var(--g1);
    border: 1px solid var(--border);
    padding: 20px;
    position: relative;
    transition: border-color 0.3s;
  }

  .signal-card:hover { border-color: var(--green-dim); }

  .signal-source {
    font-family: var(--mono);
    font-size: 9px;
    color: var(--text-muted);
    letter-spacing: 0.15em;
    margin-bottom: 8px;
    text-transform: uppercase;
  }

  .signal-name {
    font-size: 13px;
    font-weight: 600;
    color: var(--text);
    margin-bottom: 6px;
  }

  .signal-why {
    font-size: 12px;
    color: var(--text-dim);
    line-height: 1.5;
  }

  .risk-score-visual {
    background: var(--g1);
    border: 1px solid var(--border-bright);
    padding: 32px;
    margin: 24px 0;
  }

  .risk-title {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--text-muted);
    letter-spacing: 0.15em;
    margin-bottom: 20px;
    text-transform: uppercase;
  }

  .risk-bar-container {
    display: flex;
    flex-direction: column;
    gap: 14px;
  }

  .risk-bar-row {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .risk-bar-label {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--text-dim);
    width: 180px;
    flex-shrink: 0;
  }

  .risk-bar-track {
    flex: 1;
    height: 6px;
    background: var(--g3);
    border-radius: 0;
    overflow: hidden;
  }

  .risk-bar-fill {
    height: 100%;
    background: var(--green);
    border-radius: 0;
    transition: width 1s ease;
  }

  .risk-bar-fill.high { background: var(--red); }
  .risk-bar-fill.medium { background: var(--warn); }

  .risk-bar-val {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--green);
    width: 40px;
    text-align: right;
  }

  .fraud-ring-detector {
    background: var(--g1);
    border: 1px solid var(--border-bright);
    padding: 32px;
    margin: 24px 0;
    position: relative;
    overflow: hidden;
  }

  .fraud-ring-detector::before {
    content: 'NETWORK ANALYSIS ENGINE';
    position: absolute;
    top: 14px;
    right: 20px;
    font-family: var(--mono);
    font-size: 9px;
    color: var(--text-muted);
    letter-spacing: 0.15em;
  }

  .fraud-signals {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
    margin-top: 20px;
  }

  .fraud-signal {
    display: flex;
    gap: 12px;
    align-items: flex-start;
    padding: 16px;
    border: 1px solid var(--border);
    background: var(--g2);
  }

  .fraud-signal-icon {
    font-size: 20px;
    line-height: 1;
    margin-top: 2px;
  }

  .fraud-signal-content { flex: 1; }

  .fraud-signal-name {
    font-family: var(--display);
    font-size: 14px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 4px;
  }

  .fraud-signal-desc {
    font-size: 12px;
    color: var(--text-dim);
    line-height: 1.5;
  }

  /* UX TRIAGE FLOW */
  .triage-flow {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0;
    border: 1px solid var(--border-bright);
    margin-top: 24px;
    background: var(--border);
  }

  .triage-lane {
    background: var(--g1);
    padding: 28px;
    position: relative;
  }

  .triage-lane-header {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.15em;
    padding: 4px 10px;
    margin-bottom: 20px;
    display: inline-block;
    text-transform: uppercase;
  }

  .triage-lane-header.green { background: var(--green); color: var(--g0); }
  .triage-lane-header.yellow { background: var(--warn); color: var(--g0); }
  .triage-lane-header.red { background: var(--red); color: #fff; }

  .triage-title {
    font-family: var(--display);
    font-size: 18px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 12px;
  }

  .triage-steps {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .triage-steps li {
    font-size: 12px;
    color: var(--text-dim);
    padding: 8px 12px;
    background: var(--g2);
    border-left: 2px solid var(--border-bright);
    line-height: 1.5;
  }

  .triage-steps li span {
    display: block;
    font-family: var(--mono);
    font-size: 10px;
    color: var(--text-muted);
    margin-bottom: 2px;
    letter-spacing: 0.05em;
  }

  /* ===== TECH STACK ===== */
  .stack-table {
    width: 100%;
    border-collapse: collapse;
    border: 1px solid var(--border-bright);
    margin-top: 40px;
    font-family: var(--mono);
    font-size: 12px;
  }

  .stack-table th {
    background: var(--g2);
    color: var(--green);
    text-align: left;
    padding: 14px 20px;
    letter-spacing: 0.12em;
    font-size: 11px;
    border-bottom: 1px solid var(--border-bright);
    text-transform: uppercase;
  }

  .stack-table td {
    padding: 14px 20px;
    border-bottom: 1px solid var(--border);
    vertical-align: top;
  }

  .stack-table tr:hover td { background: var(--g2); }

  .stack-table td:first-child { color: var(--text-muted); width: 180px; }
  .stack-table td:nth-child(2) { color: var(--accent); }
  .stack-table td:last-child { color: var(--text-dim); }

  /* ===== TIMELINE ===== */
  .timeline {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    background: var(--border);
    border: 1px solid var(--border-bright);
    margin-top: 40px;
  }

  .timeline-phase {
    background: var(--g1);
    padding: 32px;
    position: relative;
  }

  .phase-tag {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--g0);
    background: var(--green);
    padding: 3px 8px;
    display: inline-block;
    margin-bottom: 16px;
    letter-spacing: 0.1em;
  }

  .phase-tag.dim { background: var(--text-muted); }

  .phase-dates {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--text-muted);
    margin-bottom: 12px;
  }

  .phase-title {
    font-family: var(--display);
    font-size: 20px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 16px;
  }

  .phase-items {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .phase-items li {
    font-size: 12px;
    color: var(--text-dim);
    padding-left: 14px;
    position: relative;
    line-height: 1.5;
  }

  .phase-items li::before {
    content: '→';
    position: absolute;
    left: 0;
    color: var(--green-dim);
  }

  /* ===== FOOTER ===== */
  footer {
    padding: 48px 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px solid var(--border-bright);
    flex-wrap: wrap;
    gap: 20px;
  }

  .footer-brand {
    font-family: var(--display);
    font-size: 24px;
    font-weight: 800;
    color: var(--green);
  }

  .footer-meta {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--text-muted);
    text-align: right;
    line-height: 1.8;
    letter-spacing: 0.1em;
  }

  /* ===== SCROLLBAR ===== */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--g0); }
  ::-webkit-scrollbar-thumb { background: var(--green-dim); }

  /* ===== ANIMATIONS ===== */
  @keyframes fadeUp {
    from { opacity:0; transform: translateY(24px); }
    to { opacity:1; transform: translateY(0); }
  }

  section { animation: fadeUp 0.6s ease both; }

</style>
</head>
<body>

<!-- HERO -->
<header class="hero">
  <div class="hero-bg-grid"></div>
  <div class="hero-orb"></div>

  <div class="badge">
    <span class="badge-dot"></span>
    GUIDEWIRE DEVTRAILS 2026 · PHASE 1 · TEAM SUBMISSION
  </div>

  <h1>GIG<span class="green">SHIELD</span></h1>

  <p class="hero-sub">// AI-POWERED PARAMETRIC INSURANCE · INDIA'S GIG ECONOMY · FOOD DELIVERY PERSONA</p>

  <p class="hero-tagline">When the storm hits, the payout drops. Zero claims. Zero friction. Zero excuses.</p>

  <div class="hero-stats">
    <div class="stat">
      <span class="stat-num">12M+</span>
      <span class="stat-label">Gig Workers in India</span>
    </div>
    <div class="stat">
      <span class="stat-num">₹0</span>
      <span class="stat-label">Current Safety Net</span>
    </div>
    <div class="stat">
      <span class="stat-num">27%</span>
      <span class="stat-label">Income Lost in Disruptions</span>
    </div>
    <div class="stat">
      <span class="stat-num">&lt;90s</span>
      <span class="stat-label">Auto-Payout Time</span>
    </div>
  </div>
</header>


<!-- PROBLEM -->
<section>
  <div class="section-label">01 · THE PROBLEM</div>
  <h2 class="section-title">The system left them<br><span class="green">completely unprotected.</span></h2>
  <p class="section-desc">India's 12 million gig delivery workers are the last mile of a ₹4 lakh crore industry — and they absorb 100% of the financial risk when disruptions happen.</p>

  <div class="problem-grid">
    <div class="problem-card" data-num="01">
      <div class="problem-icon">🌧️</div>
      <div class="problem-title">No Warning, No Coverage</div>
      <div class="problem-text">A single heavy rain event in Mumbai can wipe out ₹600–900 of a Zomato rider's weekly earnings. There is currently no mechanism to recover this. Not one.</div>
    </div>
    <div class="problem-card" data-num="02">
      <div class="problem-icon">📱</div>
      <div class="problem-title">Platforms Don't Compensate</div>
      <div class="problem-text">Zomato and Swiggy explicitly shift weather/disruption risk to riders. App downtime, curfews, and floods are a rider's personal problem.</div>
    </div>
    <div class="problem-card" data-num="03">
      <div class="problem-icon">🏦</div>
      <div class="problem-title">Traditional Insurance Doesn't Fit</div>
      <div class="problem-text">Monthly premiums, extensive documentation, and claim investigation cycles are designed for salaried employees — not someone earning ₹700 a day.</div>
    </div>
    <div class="problem-card" data-num="04">
      <div class="problem-icon">📊</div>
      <div class="problem-title">Income Volatility = Debt Trap</div>
      <div class="problem-text">Without a safety net, one bad week means a rider skips EMIs, borrows from local lenders at 40% interest, or simply quits the platform.</div>
    </div>
  </div>

  <div class="highlight-box">
    <p>
      GigShield's answer → A <strong>parametric model</strong>: no claims filed, no investigator called, no waiting period.<br>
      When a pre-defined trigger fires (AQI &gt;300, rainfall &gt;50mm/hr, curfew declared),<br>
      the smart contract executes and ₹ lands in the rider's UPI account. Automatically. Always.
    </p>
  </div>
</section>


<!-- PERSONA -->
<section>
  <div class="section-label">02 · OUR PERSONA</div>
  <h2 class="section-title">We protect the <span class="green">Food Delivery Rider.</span></h2>
  <p class="section-desc">Focus: Zomato & Swiggy delivery partners in Tier-1 Indian cities — the most disruption-exposed, highest-density segment of the gig economy.</p>

  <div class="persona-card">
    <div>
      <div class="persona-name">Rajan, 26</div>
      <div class="persona-desc">Zomato delivery partner, Bengaluru. Works 10–14 hrs/day, 6 days/week. Earns ₹18,000–22,000/month. Has zero savings buffer for disruption weeks. Pays rent, bike EMI, and sends money home.</div>
      <div class="tag-list">
        <span class="tag">No Emergency Fund</span>
        <span class="tag">UPI Native</span>
        <span class="tag">2-Wheeler</span>
        <span class="tag">Bengaluru / Mumbai / Delhi</span>
        <span class="tag">Peak: 6–9PM</span>
        <span class="tag">Monsoon = Crisis</span>
      </div>
    </div>

    <div class="scenario-list">
      <div class="scenario">
        <div class="scenario-trigger">TRIGGER: RAINFALL &gt; 50mm/hr</div>
        <div class="scenario-desc">Platform goes quiet. Orders drop 80%. Rajan earns ₹120 in 4 hrs. GigShield pays the difference to his baseline.</div>
      </div>
      <div class="scenario">
        <div class="scenario-trigger">TRIGGER: AQI &gt; 300 (Delhi NCR)</div>
        <div class="scenario-desc">Govt advisory issued. Delivery volumes collapse. GigShield detects the AQI API crossing threshold — auto-triggers payout.</div>
      </div>
      <div class="scenario">
        <div class="scenario-trigger">TRIGGER: CURFEW / SECTION 144</div>
        <div class="scenario-desc">Unplanned civil restriction. Pickup zones inaccessible. Parametric trigger fires within 15 minutes of official order via news API.</div>
      </div>
    </div>
  </div>
</section>


<!-- WORKFLOW -->
<section>
  <div class="section-label">03 · APPLICATION WORKFLOW</div>
  <h2 class="section-title">From sign-up to payout in <span class="green">under 3 minutes.</span></h2>
  <p class="section-desc">Every touchpoint is designed for a rider who has 30 seconds, a cheap Android phone, and spotty connectivity.</p>

  <div class="flow-steps">
    <div class="flow-step">
      <div class="flow-num">01</div>
      <div class="flow-content">
        <div class="flow-title">AI-Powered Onboarding (< 3 min)</div>
        <div class="flow-desc">Rider logs in via Zomato/Swiggy OAuth or phone number. The system auto-fetches their delivery zone, average earnings, and active hours from platform API (simulated). Risk profile generated instantly. No paperwork, no forms longer than 4 fields.</div>
        <span class="flow-tag">AI RISK PROFILING · PLATFORM API INTEGRATION</span>
      </div>
    </div>

    <div class="flow-step">
      <div class="flow-num">02</div>
      <div class="flow-content">
        <div class="flow-title">Smart Policy Selection & Weekly Premium</div>
        <div class="flow-desc">Based on their zone risk score, earnings history, and delivery category, the AI recommends one of 3 weekly coverage tiers. The rider sees clearly: "₹49/week → covered up to ₹800 per disruption day." They pay via UPI. Policy activates instantly.</div>
        <span class="flow-tag">DYNAMIC PRICING ML · WEEKLY BILLING CYCLE</span>
      </div>
    </div>

    <div class="flow-step">
      <div class="flow-num">03</div>
      <div class="flow-content">
        <div class="flow-title">Real-Time Disruption Monitoring</div>
        <div class="flow-desc">GigShield's backend continuously polls weather APIs (OpenWeatherMap), AQI feeds (CPCB/AirVisual), traffic APIs, and news APIs for civil disruptions — every 10 minutes across covered zones. No human intervention needed.</div>
        <span class="flow-tag">PARAMETRIC TRIGGER ENGINE · MULTI-API MONITORING</span>
      </div>
    </div>

    <div class="flow-step">
      <div class="flow-num">04</div>
      <div class="flow-content">
        <div class="flow-title">Automated Claim Initiation & Fraud Check</div>
        <div class="flow-desc">When a trigger fires, the system cross-validates: Is the rider active/enrolled? Does their location data match the declared disruption zone? Do behavioral signals look legitimate? The fraud engine runs a 12-point check in parallel. The whole process takes under 8 seconds.</div>
        <span class="flow-tag">FRAUD DETECTION ML · MULTI-SIGNAL VALIDATION</span>
      </div>
    </div>

    <div class="flow-step">
      <div class="flow-num">05</div>
      <div class="flow-content">
        <div class="flow-title">Instant Payout via UPI / Wallet</div>
        <div class="flow-desc">Clean claims get the payout in under 90 seconds — directly to UPI ID, Paytm wallet, or linked bank account. Flagged claims enter a 15-minute soft-hold review with automated re-verification. Worker receives an in-app notification with transparent status at every step.</div>
        <span class="flow-tag">RAZORPAY / UPI INTEGRATION · &lt;90s PAYOUT SLA</span>
      </div>
    </div>
  </div>
</section>


<!-- PREMIUM MODEL -->
<section>
  <div class="section-label">04 · WEEKLY PREMIUM MODEL</div>
  <h2 class="section-title">Priced for a <span class="green">₹700/day</span> reality.</h2>
  <p class="section-desc">Three tiers. Weekly billing. AI-adjusted based on hyper-local zone risk, weather season, and rider activity score.</p>

  <div class="premium-grid">
    <div class="premium-tier">
      <div class="tier-name">Basic Shield</div>
      <div class="tier-price">₹29</div>
      <div class="tier-period">/ week</div>
      <div class="tier-coverage">₹400/day</div>
      <div class="tier-desc">Coverage cap · 2 disruption events/week · Low-risk zones</div>
    </div>
    <div class="premium-tier featured">
      <div class="tier-name">Pro Shield</div>
      <div class="tier-price">₹49</div>
      <div class="tier-period">/ week</div>
      <div class="tier-coverage">₹700/day</div>
      <div class="tier-desc">Coverage cap · 3 disruption events/week · Moderate-risk zones</div>
    </div>
    <div class="premium-tier">
      <div class="tier-name">Max Shield</div>
      <div class="tier-price">₹79</div>
      <div class="tier-period">/ week</div>
      <div class="tier-coverage">₹1,200/day</div>
      <div class="tier-desc">Coverage cap · 5 disruption events/week · High-risk / monsoon zones</div>
    </div>
  </div>

  <div class="premium-formula">
    <span class="comment">// Weekly Premium Formula — Dynamic AI Pricing Engine</span><br><br>
    <span class="var">weekly_premium</span> = <span class="val">base_tier_price</span><br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;× <span class="val">zone_risk_multiplier</span> &nbsp;<span class="comment">// 0.8–1.4 based on historical flood/AQI data</span><br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;× <span class="val">seasonal_factor</span> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="comment">// 1.3x during monsoon (June–Sept)</span><br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;× <span class="val">activity_discount</span> &nbsp;&nbsp;&nbsp;&nbsp;<span class="comment">// 0.9x if rider has 30+ active days/quarter</span><br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;× <span class="val">claim_history_factor</span> &nbsp;<span class="comment">// Adjusts up if repeated edge-case claims</span>
  </div>
</section>


<!-- TRIGGERS -->
<section>
  <div class="section-label">05 · PARAMETRIC TRIGGERS</div>
  <h2 class="section-title">No human judgment. <span class="green">Just data.</span></h2>
  <p class="section-desc">Five automated triggers mapped to real, measurable events. Each threshold is calibrated to the point at which delivery orders actually collapse — not theoretical safety limits.</p>

  <div class="triggers-grid">
    <div class="trigger-card">
      <div class="trigger-type">ENVIRONMENTAL · API: OPENWEATHERMAP</div>
      <div class="trigger-name">Heavy Rainfall Event</div>
      <div class="trigger-threshold">THRESHOLD: &gt; 50mm / hr sustained for 30min</div>
      <div class="trigger-desc">At this rainfall intensity, 2-wheelers cannot safely operate. Platform data shows order completion rates drop below 20%. Hyper-local zone-level data used — not city-wide averages.</div>
    </div>

    <div class="trigger-card">
      <div class="trigger-type">ENVIRONMENTAL · API: CPCB / AIRVISUAL</div>
      <div class="trigger-name">Severe Air Pollution</div>
      <div class="trigger-threshold">THRESHOLD: AQI &gt; 300 (Hazardous) for &gt; 2hrs</div>
      <div class="trigger-desc">Delhi NCR specific. GRAP Stage 4 restrictions kick in at this level. Government advisory makes outdoor work officially inadvisable. Rider health risk is real and documented.</div>
    </div>

    <div class="trigger-card">
      <div class="trigger-type">SOCIAL · API: NEWS API + GOVT ALERTS</div>
      <div class="trigger-name">Curfew / Section 144</div>
      <div class="trigger-threshold">THRESHOLD: Official order within covered zone</div>
      <div class="trigger-desc">Scraped from official government portals + major news APIs within 15 minutes of declaration. Zone mapping cross-referenced with rider's last active location and coverage PIN code.</div>
    </div>

    <div class="trigger-card">
      <div class="trigger-type">ENVIRONMENTAL · API: IMD + TRAFFIC</div>
      <div class="trigger-name">Flash Flood / Waterlogging</div>
      <div class="trigger-threshold">THRESHOLD: IMD Red Alert + traffic gridlock &gt;60min</div>
      <div class="trigger-desc">IMD red alert combined with Google Maps / HERE traffic API showing arterial roads fully blocked. Dual-source verification reduces false positives while catching genuine flood events early.</div>
    </div>

    <div class="trigger-card">
      <div class="trigger-type">PLATFORM · API: ZOMATO/SWIGGY SIMULATED</div>
      <div class="trigger-name">Platform Downtime / App Crash</div>
      <div class="trigger-threshold">THRESHOLD: Platform API unresponsive &gt; 45min</div>
      <div class="trigger-desc">If the delivery platform itself goes down, riders earn zero regardless of weather. GigShield monitors platform health and triggers a coverage event if the rider was active during the outage window.</div>
    </div>

    <div class="trigger-card">
      <div class="trigger-type">ENVIRONMENTAL · API: IMD</div>
      <div class="trigger-name">Cyclone / Extreme Heat</div>
      <div class="trigger-threshold">THRESHOLD: IMD Orange+ Alert or &gt;44°C sustained</div>
      <div class="trigger-desc">Cyclone warnings along coastal cities (Chennai, Mumbai, Kolkata) or extreme heat events where outdoor work becomes medically dangerous — triggers income protection without any rider action needed.</div>
    </div>
  </div>
</section>


<!-- AI/ML -->
<section>
  <div class="section-label">06 · AI & ML ARCHITECTURE</div>
  <h2 class="section-title">Three models. One <span class="green">intelligent spine.</span></h2>
  <p class="section-desc">Every intelligent decision in GigShield is backed by a purpose-built model — not a generic off-the-shelf classifier.</p>

  <div class="ml-grid">
    <div class="ml-card">
      <div class="ml-icon">🧠</div>
      <div class="ml-title">Dynamic Risk Pricing Engine</div>
      <div class="ml-model">GRADIENT BOOSTED TREES (XGBoost)</div>
      <div class="ml-desc">Ingests 14 features: delivery zone, historical disruption frequency, IMD seasonal risk, rider activity score, platform order density. Outputs a weekly premium multiplier. Retrained every 2 weeks on fresh disruption data.</div>
    </div>

    <div class="ml-card">
      <div class="ml-icon">🔍</div>
      <div class="ml-title">Fraud & Anomaly Detection</div>
      <div class="ml-model">ISOLATION FOREST + BEHAVIORAL LSTM</div>
      <div class="ml-desc">Isolation Forest for real-time point anomaly detection on individual claims. LSTM trained on 6-month rider activity sequences to flag behavioral drift — e.g., someone who never claimed before suddenly claiming 5x in 2 weeks.</div>
    </div>

    <div class="ml-card">
      <div class="ml-icon">📈</div>
      <div class="ml-title">Disruption Prediction Engine</div>
      <div class="ml-model">TIME-SERIES FORECASTING (PROPHET + LSTM)</div>
      <div class="ml-desc">Forecasts next-week disruption probability by zone using IMD historical data + seasonal patterns. Enables proactive premium adjustments and pre-emptive liquidity pool management before a cyclone season begins.</div>
    </div>

    <div class="ml-card">
      <div class="ml-icon">🗺️</div>
      <div class="ml-title">Zone Risk Mapper</div>
      <div class="ml-model">CLUSTERING (DBSCAN) + GEOSPATIAL ANALYSIS</div>
      <div class="ml-desc">Uses 5 years of IMD data, historical flood maps (NDMA), and platform order density data to cluster delivery zones into risk tiers. Risk map updates every 90 days. Enables hyper-local premium precision.</div>
    </div>

    <div class="ml-card">
      <div class="ml-icon">🤖</div>
      <div class="ml-title">Claims Triage Classifier</div>
      <div class="ml-model">MULTI-CLASS RANDOM FOREST</div>
      <div class="ml-desc">Takes 12 input signals per claim and outputs one of three decisions: AUTO-APPROVE, SOFT-FLAG (15-min review), or HARD-BLOCK. Trained on synthetic fraud data + historical parametric claim patterns.</div>
    </div>

    <div class="ml-card">
      <div class="ml-icon">💬</div>
      <div class="ml-title">Vernacular Support Chatbot</div>
      <div class="ml-model">FINE-TUNED LLM (HINDI / KANNADA / TAMIL)</div>
      <div class="ml-desc">A lightweight fine-tuned LLM for rider support in regional languages. Handles policy queries, payout status, and appeals — reducing support load by 80%. Riders in Tamil Nadu can interact entirely in Tamil.</div>
    </div>
  </div>
</section>


<!-- 🚨 ADVERSARIAL DEFENSE — THE BIG SECTION -->
<section class="adversarial">
  <div class="threat-banner">🚨 CRITICAL UPDATE — ADVERSARIAL DEFENSE &amp; ANTI-SPOOFING STRATEGY — PHASE 1 MARKET CRASH RESPONSE 🚨</div>

  <div class="section-label" style="color: var(--red);">07 · ADVERSARIAL DEFENSE</div>
  <h2 class="section-title" style="color: #fff;">We <span style="color:var(--red);">saw the attack.</span><br>We <span class="green">built the fortress.</span></h2>
  <p class="section-desc">A 500-worker syndicate used GPS spoofing to drain a competitor's liquidity pool. Our response isn't a patch — it's a full architectural overhaul of how trust is established.</p>

  <div class="threat-scenario">
    // THREAT VECTOR ANALYSIS<br>
    // ─────────────────────────────────────────────────────────────────<br>
    // ATTACK: 500 coordinated actors · Telegram-organized · GPS spoofing apps<br>
    // METHOD: Fake location → simulated "disruption zone" → mass claim trigger<br>
    // DAMAGE: Liquidity pool drained · Honest riders unable to claim<br>
    // ROOT CAUSE: Platform trusted GPS as the single source of truth<br>
    // ─────────────────────────────────────────────────────────────────<br>
    // GigShield's architecture: GPS is ONE input among TWELVE. Always was.
  </div>

  <!-- LAYER 1: DIFFERENTIATION -->
  <div class="defense-layer">
    <div class="defense-layer-title">
      <span class="layer-num">LAYER 01</span>
      The Differentiation Engine
    </div>
    <div class="defense-layer-sub">// How we tell a stranded rider from a spoofing actor</div>

    <div class="signal-grid">
      <div class="signal-card">
        <div class="signal-source">DEVICE · IMU SENSOR</div>
        <div class="signal-name">Accelerometer + Gyroscope Pattern</div>
        <div class="signal-why">A real rider on a 2-wheeler in rain shows specific motion signatures — micro-vibrations, speed fluctuations, directional variance. A spoofed GPS from a stationary home shows none of this. Our model is trained on 90 days of genuine rider telemetry.</div>
      </div>
      <div class="signal-card">
        <div class="signal-source">NETWORK · TELECOM</div>
        <div class="signal-name">Cell Tower vs GPS Delta</div>
        <div class="signal-why">GPS can be faked. Cell tower triangulation cannot without carrier-level access. If GPS says "Bandra" but the nearest cell tower says "Andheri," that's a hard red flag. We use Android's network location API as a parallel verification channel.</div>
      </div>
      <div class="signal-card">
        <div class="signal-source">PLATFORM · ORDER DATA</div>
        <div class="signal-name">Last Active Order Timestamp</div>
        <div class="signal-why">A genuinely stranded rider will have accepted/rejected orders within the last 60 minutes of the disruption. A fraud actor sitting at home hasn't touched the platform. We cross-check their last Zomato/Swiggy order activity (via simulated API) against the claim timestamp.</div>
      </div>
      <div class="signal-card">
        <div class="signal-source">DEVICE · APP TELEMETRY</div>
        <div class="signal-name">App Foreground / Background State</div>
        <div class="signal-why">Real delivery riders have the Zomato/Swiggy app in foreground during work hours. Fraud actors using GPS spoofing tools typically have those tools in foreground and delivery apps backgrounded. We detect this app-state fingerprint.</div>
      </div>
      <div class="signal-card">
        <div class="signal-source">BEHAVIORAL · ML MODEL</div>
        <div class="signal-name">Historical Claim Pattern Baseline</div>
        <div class="signal-why">Our LSTM builds a 90-day behavioral fingerprint for every rider. First claim ever on day of a mass coordinated event? That's anomalous. We flag sudden, unprecedented claim behavior especially when it correlates with a spike across hundreds of accounts simultaneously.</div>
      </div>
      <div class="signal-card">
        <div class="signal-source">ENVIRONMENT · WEATHER CROSS-REF</div>
        <div class="signal-name">Claimed Zone vs API Weather Granularity</div>
        <div class="signal-why">Our weather data is pulled at 500m grid resolution. A rider claims they're in Zone A (red alert), but our weather API shows Zone A received only 12mm/hr at their exact coordinates while they claim 60mm/hr. Coordinate-level mismatch triggers a flag.</div>
      </div>
    </div>
  </div>

  <!-- LAYER 2: FRAUD RING DETECTION -->
  <div class="defense-layer">
    <div class="defense-layer-title">
      <span class="layer-num">LAYER 02</span>
      Coordinated Fraud Ring Detector
    </div>
    <div class="defense-layer-sub">// The signals that expose a Telegram-organized syndicate</div>

    <div class="fraud-ring-detector">
      <div class="risk-title">// NETWORK-LEVEL ANOMALY SIGNALS — REAL-TIME MONITORING</div>

      <div class="fraud-signals">
        <div class="fraud-signal">
          <div class="fraud-signal-icon">📈</div>
          <div class="fraud-signal-content">
            <div class="fraud-signal-name">Claim Velocity Spike Detector</div>
            <div class="fraud-signal-desc">If claims from a single zone spike by more than 3 standard deviations above the historical mean within a 30-minute window, the entire zone's claims are soft-held pending review. This alone would have caught the 500-person syndicate — their coordinated trigger creates an unmistakable statistical cliff.</div>
          </div>
        </div>

        <div class="fraud-signal">
          <div class="fraud-signal-icon">📱</div>
          <div class="fraud-signal-content">
            <div class="fraud-signal-name">Device Fingerprint Clustering</div>
            <div class="fraud-signal-desc">We store a hashed device fingerprint (OS version, screen resolution, installed app hash — no PII). If 50+ claims in one event share identical or near-identical device fingerprints, that's a factory-farmed account farm. Blocked automatically.</div>
          </div>
        </div>

        <div class="fraud-signal">
          <div class="fraud-signal-icon">🌐</div>
          <div class="fraud-signal-content">
            <div class="fraud-signal-name">IP + VPN / Proxy Detection</div>
            <div class="fraud-signal-desc">GPS spoofing apps frequently route through VPNs or shared IP addresses. We run every claim through an IP reputation check. Multiple claims originating from the same IP, VPN exit node, or datacenter IP range are immediately flagged as likely coordinated fraud.</div>
          </div>
        </div>

        <div class="fraud-signal">
          <div class="fraud-signal-icon">⏱️</div>
          <div class="fraud-signal-content">
            <div class="fraud-signal-name">Submission Timestamp Uniformity</div>
            <div class="fraud-signal-desc">Organic human behavior is noisy — real riders submit claims whenever they notice the disruption, staggered over 20–40 minutes. Coordinated fraud rings often submit within seconds of each other (Telegram group sends "GO" signal). We flag batch submissions with &lt;90 second inter-arrival times across 10+ accounts.</div>
          </div>
        </div>

        <div class="fraud-signal">
          <div class="fraud-signal-icon">🆔</div>
          <div class="fraud-signal-content">
            <div class="fraud-signal-name">KYC Linkage Graph Analysis</div>
            <div class="fraud-signal-desc">Using graph ML on our KYC data, we detect clusters of accounts sharing the same bank account, UPI ID, phone number prefix pattern, or Aadhaar-linked address. One person controlling 10 "rider" accounts is a documented fraud pattern we map at onboarding.</div>
          </div>
        </div>

        <div class="fraud-signal">
          <div class="fraud-signal-icon">📊</div>
          <div class="fraud-signal-content">
            <div class="fraud-signal-name">Platform Activity Cross-Validation</div>
            <div class="fraud-signal-desc">The most powerful signal: we check if the "stranded rider" actually had any delivery platform activity in the 2 hours before the disruption event. Fraud actors aren't actual delivery workers — they show zero Zomato/Swiggy session data. Real riders show order history right up to when conditions deteriorated.</div>
          </div>
        </div>
      </div>
    </div>

    <div class="risk-score-visual">
      <div class="risk-title">// FRAUD RISK SCORE COMPOSITION — PER CLAIM (100-POINT SCALE)</div>
      <div class="risk-bar-container">
        <div class="risk-bar-row">
          <div class="risk-bar-label">GPS ↔ Cell Tower Match</div>
          <div class="risk-bar-track"><div class="risk-bar-fill" style="width:20%"></div></div>
          <div class="risk-bar-val">20pts</div>
        </div>
        <div class="risk-bar-row">
          <div class="risk-bar-label">Platform Activity Verified</div>
          <div class="risk-bar-track"><div class="risk-bar-fill" style="width:25%"></div></div>
          <div class="risk-bar-val">25pts</div>
        </div>
        <div class="risk-bar-row">
          <div class="risk-bar-label">Motion Sensor Authentic</div>
          <div class="risk-bar-track"><div class="risk-bar-fill" style="width:15%"></div></div>
          <div class="risk-bar-val">15pts</div>
        </div>
        <div class="risk-bar-row">
          <div class="risk-bar-label">No Velocity Spike</div>
          <div class="risk-bar-track"><div class="risk-bar-fill" style="width:20%"></div></div>
          <div class="risk-bar-val">20pts</div>
        </div>
        <div class="risk-bar-row">
          <div class="risk-bar-label">Behavioral History Normal</div>
          <div class="risk-bar-track"><div class="risk-bar-fill" style="width:12%"></div></div>
          <div class="risk-bar-val">12pts</div>
        </div>
        <div class="risk-bar-row">
          <div class="risk-bar-label">No Network/IP Flag</div>
          <div class="risk-bar-track"><div class="risk-bar-fill" style="width:8%"></div></div>
          <div class="risk-bar-val">8pts</div>
        </div>
      </div>
      <br>
      <div style="font-family:var(--mono);font-size:11px;color:var(--text-muted);">
        SCORE ≥ 80 → AUTO-APPROVE &nbsp;|&nbsp; SCORE 55–79 → SOFT-FLAG (15-min review) &nbsp;|&nbsp; SCORE &lt; 55 → HARD-BLOCK + INVESTIGATION
      </div>
    </div>
  </div>

  <!-- LAYER 3: UX BALANCE -->
  <div class="defense-layer">
    <div class="defense-layer-title">
      <span class="layer-num">LAYER 03</span>
      The UX Balance — Fair Triage for Honest Workers
    </div>
    <div class="defense-layer-sub">// Being flagged ≠ being punished. A rider with bad signal in a storm is not a criminal.</div>

    <div class="triage-flow">
      <div class="triage-lane">
        <div class="triage-lane-header green">✅ AUTO-APPROVED</div>
        <div class="triage-title">Score ≥ 80</div>
        <ul class="triage-steps">
          <li><span>INSTANT</span>Payout initiated within 90 seconds. No friction whatsoever.</li>
          <li><span>NOTIFICATION</span>"₹700 credited to your UPI — stay safe out there 🌧️"</li>
          <li><span>BACKGROUND</span>Claim logged for weekly audit. No rider action needed.</li>
        </ul>
      </div>
      <div class="triage-lane">
        <div class="triage-lane-header yellow">⚠️ SOFT-FLAGGED</div>
        <div class="triage-title">Score 55–79</div>
        <ul class="triage-steps">
          <li><span>STEP 1 · TRANSPARENT</span>"We're verifying your claim — takes up to 15 mins. Your payout is reserved." The rider knows exactly what's happening. No fear, no confusion.</li>
          <li><span>STEP 2 · AUTOMATED RE-CHECK</span>System re-polls all signals after 15 minutes — most genuine riders resolve on their own as more data arrives (tower ping, updated weather grid).</li>
          <li><span>STEP 3 · ONE-TAP APPEAL</span>If still flagged, rider gets a single screen: "Confirm your location" via native GPS + one optional photo. No forms. No calls. One tap.</li>
          <li><span>STEP 4 · GUARANTEED SLA</span>All soft-flag cases resolved within 2 hours. If system can't verify AND can't disprove — rider gets the payout with a trust-flag note on account.</li>
        </ul>
      </div>
      <div class="triage-lane">
        <div class="triage-lane-header red">🚫 HARD-BLOCKED</div>
        <div class="triage-title">Score &lt; 55</div>
        <ul class="triage-steps">
          <li><span>TRANSPARENT DENIAL</span>Rider gets a clear reason: "We couldn't verify your location against disruption data." No vague rejections.</li>
          <li><span>HUMAN APPEALS TEAM</span>Every hard-blocked claim can be escalated to a human reviewer within 24 hours. Rider submits context — we review within 1 business day.</li>
          <li><span>NO IMMEDIATE BAN</span>First offense → warning + education. Second within 30 days → account review. We distinguish genuine edge cases from repeat fraud.</li>
          <li><span>TRANSPARENCY REPORT</span>Rider gets a fraud score breakdown in plain language. "Your GPS didn't match your nearest cell tower." Honest workers deserve to know why.</li>
        </ul>
      </div>
    </div>
  </div>
</section>


<!-- TECH STACK -->
<section>
  <div class="section-label">08 · TECH STACK</div>
  <h2 class="section-title">Built lean. <span class="green">Scales to millions.</span></h2>

  <table class="stack-table">
    <thead>
      <tr>
        <th>Layer</th>
        <th>Technology</th>
        <th>Why This Choice</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>Frontend (Mobile)</td><td>React Native + Expo</td><td>Single codebase for Android & iOS. Critical for India's fragmented Android market.</td></tr>
      <tr><td>Frontend (Admin Dashboard)</td><td>Next.js 14 + TailwindCSS</td><td>Server-side rendering for analytics-heavy insurer dashboard. Fast initial load.</td></tr>
      <tr><td>Backend API</td><td>Node.js + Fastify</td><td>10x faster than Express for high-throughput trigger-monitoring endpoints.</td></tr>
      <tr><td>Database</td><td>PostgreSQL + Redis</td><td>PostgreSQL for transactional policy/claims data. Redis for real-time trigger state & session cache.</td></tr>
      <tr><td>ML Pipeline</td><td>Python + FastAPI + Scikit-learn</td><td>Isolated ML microservice. Models served via REST. Independent scaling from core backend.</td></tr>
      <tr><td>Trigger Engine</td><td>Node-cron + Bull Queue</td><td>Cron polls APIs every 10 min. Bull handles async claim processing with retry logic.</td></tr>
      <tr><td>Payments</td><td>Razorpay (test mode) + UPI</td><td>Native UPI support. Test mode allows full payout simulation without real money.</td></tr>
      <tr><td>Weather / AQI APIs</td><td>OpenWeatherMap + CPCB AQI</td><td>OpenWeatherMap free tier for weather. CPCB open API for AQI. Both have Indian city coverage.</td></tr>
      <tr><td>Authentication</td><td>JWT + Phone OTP (Twilio)</td><td>OTP-first auth. No passwords. Matches how gig workers already use payment apps.</td></tr>
      <tr><td>Hosting</td><td>AWS (EC2 + RDS + Lambda)</td><td>Lambda for trigger engine (event-driven, cost-efficient). RDS for managed Postgres.</td></tr>
      <tr><td>Fraud Monitoring</td><td>Custom ML + IPQualityScore API</td><td>Hybrid: our models for behavioral fraud, IPQS for real-time IP/VPN reputation checks.</td></tr>
    </tbody>
  </table>
</section>


<!-- TIMELINE -->
<section>
  <div class="section-label">09 · DEVELOPMENT ROADMAP</div>
  <h2 class="section-title">6 weeks. <span class="green">Ship everything.</span></h2>

  <div class="timeline">
    <div class="timeline-phase">
      <div class="phase-tag">PHASE 1 · NOW</div>
      <div class="phase-dates">Mar 4 – Mar 20</div>
      <div class="phase-title">Ideate & Architect</div>
      <ul class="phase-items">
        <li>Problem research & persona definition</li>
        <li>Full README architecture document</li>
        <li>Tech stack decisions finalized</li>
        <li>Adversarial defense strategy</li>
        <li>2-min strategy video</li>
        <li>GitHub repo initialized</li>
      </ul>
    </div>
    <div class="timeline-phase">
      <div class="phase-tag dim">PHASE 2</div>
      <div class="phase-dates">Mar 21 – Apr 4</div>
      <div class="phase-title">Build Core Platform</div>
      <ul class="phase-items">
        <li>Rider registration + onboarding flow</li>
        <li>Weekly policy creation UI</li>
        <li>Dynamic premium calculation (ML model v1)</li>
        <li>3–5 parametric trigger automations</li>
        <li>Claims management dashboard</li>
        <li>Mock payout integration (Razorpay test)</li>
      </ul>
    </div>
    <div class="timeline-phase">
      <div class="phase-tag dim">PHASE 3</div>
      <div class="phase-dates">Apr 5 – Apr 17</div>
      <div class="phase-title">Scale & Harden</div>
      <ul class="phase-items">
        <li>Advanced fraud detection engine (full 12-signal)</li>
        <li>Anti-spoofing layer deployed</li>
        <li>Insurer analytics dashboard</li>
        <li>Vernacular chatbot (Hindi / Kannada)</li>
        <li>5-min demo video + final pitch deck</li>
        <li>Load testing & performance optimization</li>
      </ul>
    </div>
  </div>
</section>


<!-- FOOTER -->
<footer>
  <div>
    <div class="footer-brand">GigShield</div>
    <div style="font-family:var(--mono);font-size:11px;color:var(--text-muted);margin-top:6px;">
      Parametric Income Insurance · India's Gig Economy
    </div>
  </div>
  <div class="footer-meta">
    GUIDEWIRE DEVTRAILS 2026<br>
    PHASE 1 SUBMISSION · MARCH 20, 2026<br>
    FOOD DELIVERY PERSONA · TIER-1 CITIES<br>
    README v2.0 — ADVERSARIAL UPDATE INCLUDED
  </div>
</footer>

</body>
</html>
