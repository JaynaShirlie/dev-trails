<svg viewBox="0 0 900 200" width="900" height="200" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="bggrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#000000"/>
      <stop offset="50%" stop-color="#050d05"/>
      <stop offset="100%" stop-color="#000000"/>
    </linearGradient>
    <radialGradient id="orb" cx="85%" cy="20%" r="50%">
      <stop offset="0%" stop-color="#00ff41" stop-opacity="0.12"/>
      <stop offset="100%" stop-color="#000000" stop-opacity="0"/>
    </radialGradient>
    <filter id="glow">
      <feGaussianBlur stdDeviation="3" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <filter id="softglow">
      <feGaussianBlur stdDeviation="8" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <!-- BG -->
  <rect width="900" height="200" fill="url(#bggrad)"/>
  <rect width="900" height="200" fill="url(#orb)"/>

  <!-- Grid -->
  <g stroke="#00ff41" stroke-width="0.4" opacity="0.1">
    <line x1="0" y1="40" x2="900" y2="40"/><line x1="0" y1="80" x2="900" y2="80"/>
    <line x1="0" y1="120" x2="900" y2="120"/><line x1="0" y1="160" x2="900" y2="160"/>
    <line x1="180" y1="0" x2="180" y2="200"/><line x1="360" y1="0" x2="360" y2="200"/>
    <line x1="540" y1="0" x2="540" y2="200"/><line x1="720" y1="0" x2="720" y2="200"/>
  </g>

  <!-- Corner brackets -->
  <path d="M0,18 L0,0 L18,0" fill="none" stroke="#00ff41" stroke-width="2.5"/>
  <path d="M882,0 L900,0 L900,18" fill="none" stroke="#00ff41" stroke-width="2.5"/>
  <path d="M0,182 L0,200 L18,200" fill="none" stroke="#00ff41" stroke-width="2.5"/>
  <path d="M882,200 L900,200 L900,182" fill="none" stroke="#00ff41" stroke-width="2.5"/>

  <!-- Outer border -->
  <rect x="1" y="1" width="898" height="198" fill="none" stroke="#00ff41" stroke-width="0.8" opacity="0.3"/>

  <!-- Scanline sweep -->
  <rect x="0" y="0" width="900" height="2" fill="#00ff41" opacity="0.08">
    <animateTransform attributeName="transform" type="translate" values="0,0;0,200;0,0" dur="3s" repeatCount="indefinite"/>
  </rect>

  <!-- Live dot + label -->
  <circle cx="36" cy="32" r="5" fill="#00ff41" filter="url(#glow)">
    <animate attributeName="opacity" values="1;0.3;1" dur="1.4s" repeatCount="indefinite"/>
  </circle>
  <text x="48" y="37" font-family="Courier New, monospace" font-size="10" fill="#00ff41" letter-spacing="2" opacity="0.8">DEVTRAILS 2026 · PHASE 1 · LIVE</text>

  <!-- Main title GIG -->
  <text x="36" y="115" font-family="Arial Black, Impact, sans-serif" font-size="76" font-weight="900" fill="#ffffff" letter-spacing="-3" filter="url(#softglow)">GIG</text>
  <!-- SHIELD in green -->
  <text x="182" y="115" font-family="Arial Black, Impact, sans-serif" font-size="76" font-weight="900" fill="#00ff41" letter-spacing="-3" filter="url(#softglow)">SHIELD</text>

  <!-- Blinking cursor -->
  <rect x="594" y="68" width="8" height="52" fill="#00ff41" opacity="0.9">
    <animate attributeName="opacity" values="0.9;0;0.9" dur="1s" repeatCount="indefinite"/>
  </rect>

  <!-- Subtitle -->
  <text x="36" y="140" font-family="Courier New, monospace" font-size="12" fill="#39ff84" letter-spacing="2.5" opacity="0.85">AI-POWERED PARAMETRIC INSURANCE · INDIA'S GIG ECONOMY</text>

  <!-- Tagline -->
  <text x="36" y="168" font-family="Georgia, serif" font-size="14" fill="#b8ff6a" font-style="italic" opacity="0.9">"When the storm hits — the payout drops. Zero claims. Zero friction."</text>

  <!-- Right side stats -->
  <text x="700" y="80" font-family="Courier New, monospace" font-size="10" fill="#00c432" letter-spacing="1" opacity="0.8">● 12M+ WORKERS</text>
  <text x="700" y="100" font-family="Courier New, monospace" font-size="10" fill="#00c432" letter-spacing="1" opacity="0.8">● ₹0 SAFETY NET</text>
  <text x="700" y="120" font-family="Courier New, monospace" font-size="10" fill="#00c432" letter-spacing="1" opacity="0.8">● &lt;90s PAYOUT</text>
  <text x="700" y="140" font-family="Courier New, monospace" font-size="10" fill="#00c432" letter-spacing="1" opacity="0.8">● 12-PT FRAUD SHIELD</text>
</svg>
