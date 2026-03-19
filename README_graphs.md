<div align="center">

<img src="https://img.shields.io/badge/Phase-1%20Seed-FFD45A?style=for-the-badge&logoColor=000000" />
<img src="https://img.shields.io/badge/DEVTrails-2026-FF8B5A?style=for-the-badge&logoColor=000000" />
<img src="https://img.shields.io/badge/Status-Active-FF5A5A?style=for-the-badge&logoColor=000000" />

<br/>

<svg width="720" height="6" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="topbar" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%"   stop-color="#FF5A5A"/>
      <stop offset="33%"  stop-color="#FF8B5A"/>
      <stop offset="66%"  stop-color="#FFA95A"/>
      <stop offset="100%" stop-color="#FFD45A"/>
    </linearGradient>
  </defs>
  <rect width="720" height="6" rx="3" fill="url(#topbar)"/>
</svg>

<br/>

<pre>
 ██████╗ ██╗ ██████╗ ███████╗██╗  ██╗██╗███████╗██╗     ██████╗ 
██╔════╝ ██║██╔════╝ ██╔════╝██║  ██║██║██╔════╝██║     ██╔══██╗
██║  ███╗██║██║  ███╗███████╗███████║██║█████╗  ██║     ██║  ██║
██║   ██║██║██║   ██║╚════██║██╔══██║██║██╔══╝  ██║     ██║  ██║
╚██████╔╝██║╚██████╔╝███████║██║  ██║██║███████╗███████╗██████╔╝
 ╚═════╝ ╚═╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚═════╝
</pre>

### *parametric income insurance. zero claims. automatic payouts. built for the rain.*

<img src="https://img.shields.io/badge/Python-FF5A5A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/FastAPI-FF8B5A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/Scikit--learn-FFA95A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/MongoDB-FFD45A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/OpenWeatherMap-FF8B5A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/Razorpay-FF5A5A?style=flat-square&logoColor=000" />

</div>

---

## the problem, one sentence

a zomato partner loses ₹400 when it rains. no one pays them back. **gigshield does — automatically, before they even notice.**

---

## how it works

```
sign up → risk profiled → weekly premium set → coverage active
           ↓
        weather API triggers (rain > 50mm / temp > 42°C / AQI > 300)
           ↓
        income fingerprint + trust score computed  ← fraud layer
           ↓
        workability score drops below 40 → claim auto-fired
           ↓
        payout hits UPI. worker gets notified. done.
```

---

## platform at a glance

<div align="center">

<!-- CHART 1: Weekly Premium Distribution by Risk Tier -->
<svg width="680" height="200" xmlns="http://www.w3.org/2000/svg" font-family="monospace">
  <defs>
    <linearGradient id="barLow" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" stop-color="#FFD45A"/><stop offset="100%" stop-color="#FFA95A"/>
    </linearGradient>
    <linearGradient id="barMed" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" stop-color="#FFA95A"/><stop offset="100%" stop-color="#FF8B5A"/>
    </linearGradient>
    <linearGradient id="barHigh" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" stop-color="#FF8B5A"/><stop offset="100%" stop-color="#FF5A5A"/>
    </linearGradient>
  </defs>

  <!-- background -->
  <rect width="680" height="200" rx="12" fill="#0d1117"/>

  <!-- title -->
  <text x="340" y="28" text-anchor="middle" fill="#FFD45A" font-size="13" font-weight="bold">weekly premium vs coverage — by risk tier</text>

  <!-- y-axis gridlines -->
  <line x1="80" y1="40" x2="80" y2="155" stroke="#30363d" stroke-width="1"/>
  <line x1="80" y1="155" x2="620" y2="155" stroke="#30363d" stroke-width="1"/>
  <line x1="80" y1="115" x2="620" y2="115" stroke="#30363d" stroke-width="0.5" stroke-dasharray="4,4"/>
  <line x1="80" y1="80"  x2="620" y2="80"  stroke="#30363d" stroke-width="0.5" stroke-dasharray="4,4"/>

  <!-- y-axis labels -->
  <text x="72" y="158" text-anchor="end" fill="#8b949e" font-size="10">0</text>
  <text x="72" y="118" text-anchor="end" fill="#8b949e" font-size="10">500</text>
  <text x="72" y="83"  text-anchor="end" fill="#8b949e" font-size="10">1000</text>
  <text x="68" y="44"  text-anchor="end" fill="#8b949e" font-size="9">1500</text>

  <!-- PREMIUM bars (left of each group) -->
  <!-- Low risk premium ₹20 → height = 20/1500*115 = ~1.5 → too small, scale to /15 instead: 20/15=~13px -->
  <rect x="130" y="142" width="40" height="13" rx="4" fill="url(#barLow)"/>
  <!-- Medium ₹40 -->
  <rect x="310" y="129" width="40" height="26" rx="4" fill="url(#barMed)"/>
  <!-- High ₹70 -->
  <rect x="490" y="109" width="40" height="46" rx="4" fill="url(#barHigh)"/>

  <!-- COVERAGE bars (right of each group), scale /1500*115 -->
  <!-- Low ₹500 → 38px -->
  <rect x="175" y="117" width="40" height="38" rx="4" fill="url(#barLow)" opacity="0.5"/>
  <!-- Medium ₹1000 → 77px -->
  <rect x="355" y="78"  width="40" height="77" rx="4" fill="url(#barMed)"  opacity="0.5"/>
  <!-- High ₹1500 → 115px -->
  <rect x="535" y="40"  width="40" height="115" rx="4" fill="url(#barHigh)" opacity="0.5"/>

  <!-- x-axis labels -->
  <text x="183" y="172" text-anchor="middle" fill="#FFD45A" font-size="11" font-weight="bold">🟡 Low Risk</text>
  <text x="363" y="172" text-anchor="middle" fill="#FFA95A" font-size="11" font-weight="bold">🟠 Medium Risk</text>
  <text x="543" y="172" text-anchor="middle" fill="#FF5A5A" font-size="11" font-weight="bold">🔴 High Risk</text>

  <!-- value labels on bars -->
  <text x="150"  y="139" text-anchor="middle" fill="#fff" font-size="9">₹20</text>
  <text x="195"  y="113" text-anchor="middle" fill="#FFD45A" font-size="9">₹500</text>
  <text x="330"  y="125" text-anchor="middle" fill="#fff" font-size="9">₹40</text>
  <text x="375"  y="74"  text-anchor="middle" fill="#FFA95A" font-size="9">₹1k</text>
  <text x="510"  y="105" text-anchor="middle" fill="#fff" font-size="9">₹70</text>
  <text x="555"  y="36"  text-anchor="middle" fill="#FF5A5A" font-size="9">₹1.5k</text>

  <!-- legend -->
  <rect x="240" y="185" width="12" height="8" rx="2" fill="#FF8B5A"/>
  <text x="256" y="193" fill="#8b949e" font-size="9">premium (solid)</text>
  <rect x="360" y="185" width="12" height="8" rx="2" fill="#FF8B5A" opacity="0.5"/>
  <text x="376" y="193" fill="#8b949e" font-size="9">coverage (transparent)</text>
</svg>

<br/>

<!-- CHART 2: Trust Score → Payout Speed funnel -->
<svg width="680" height="210" xmlns="http://www.w3.org/2000/svg" font-family="monospace">
  <rect width="680" height="210" rx="12" fill="#0d1117"/>
  <text x="340" y="28" text-anchor="middle" fill="#FFD45A" font-size="13" font-weight="bold">trust tier → payout speed funnel</text>

  <!-- funnel trapezoids -->
  <!-- Champion (widest, top) -->
  <polygon points="100,45 580,45 520,85 160,85" fill="#FFD45A" opacity="0.9"/>
  <text x="340" y="71" text-anchor="middle" fill="#000" font-size="11" font-weight="bold">🏆 Champion — INSTANT payout · 20% discount</text>

  <!-- Trusted -->
  <polygon points="160,90 520,90 470,125 210,125" fill="#FFA95A" opacity="0.9"/>
  <text x="340" y="112" text-anchor="middle" fill="#000" font-size="11" font-weight="bold">✅ Trusted — 45 min · 12% discount</text>

  <!-- Verified -->
  <polygon points="210,130 470,130 430,163 250,163" fill="#FF8B5A" opacity="0.9"/>
  <text x="340" y="151" text-anchor="middle" fill="#000" font-size="11" font-weight="bold">🔵 Verified — 2 hours · 5% discount</text>

  <!-- New (narrowest, bottom) -->
  <polygon points="250,168 430,168 405,198 275,198" fill="#FF5A5A" opacity="0.9"/>
  <text x="340" y="188" text-anchor="middle" fill="#fff" font-size="11" font-weight="bold">🆕 New — 6h soft-hold · no discount</text>
</svg>

<br/>

<!-- CHART 3: 6-Signal fraud detection radar as horizontal score bars -->
<svg width="680" height="230" xmlns="http://www.w3.org/2000/svg" font-family="monospace">
  <rect width="680" height="230" rx="12" fill="#0d1117"/>
  <text x="340" y="28" text-anchor="middle" fill="#FFD45A" font-size="13" font-weight="bold">6-signal anti-spoofing — detection weight per signal</text>

  <!-- grid line -->
  <line x1="220" y1="42" x2="220" y2="210" stroke="#30363d" stroke-width="1"/>
  <line x1="400" y1="42" x2="400" y2="210" stroke="#30363d" stroke-width="0.5" stroke-dasharray="3,3"/>
  <line x1="580" y1="42" x2="580" y2="210" stroke="#30363d" stroke-width="0.5" stroke-dasharray="3,3"/>
  <text x="220" y="218" text-anchor="middle" fill="#8b949e" font-size="9">0%</text>
  <text x="400" y="218" text-anchor="middle" fill="#8b949e" font-size="9">50%</text>
  <text x="580" y="218" text-anchor="middle" fill="#8b949e" font-size="9">100%</text>

  <!-- Signal bars: label | bar -->
  <!-- 1. Income fingerprint — 28% weight → 0.28*360=101 -->
  <text x="215" y="62"  text-anchor="end" fill="#ccc" font-size="10">income fingerprint</text>
  <rect x="220" y="50" width="101" height="16" rx="4" fill="#FF5A5A"/>
  <text x="326" y="62" fill="#FF5A5A" font-size="9" font-weight="bold">  28%</text>

  <!-- 2. GPS + cell tower match — 22% → 79px -->
  <text x="215" y="92"  text-anchor="end" fill="#ccc" font-size="10">GPS × cell tower</text>
  <rect x="220" y="80" width="79" height="16" rx="4" fill="#FF8B5A"/>
  <text x="304" y="92" fill="#FF8B5A" font-size="9" font-weight="bold">  22%</text>

  <!-- 3. Peer cluster anomaly — 20% → 72px -->
  <text x="215" y="122" text-anchor="end" fill="#ccc" font-size="10">peer cluster anomaly</text>
  <rect x="220" y="110" width="72" height="16" rx="4" fill="#FFA95A"/>
  <text x="297" y="122" fill="#FFA95A" font-size="9" font-weight="bold">  20%</text>

  <!-- 4. Accelerometer — 15% → 54px -->
  <text x="215" y="152" text-anchor="end" fill="#ccc" font-size="10">accelerometer pattern</text>
  <rect x="220" y="140" width="54" height="16" rx="4" fill="#FFD45A"/>
  <text x="279" y="152" fill="#FFD45A" font-size="9" font-weight="bold">  15%</text>

  <!-- 5. Historical velocity — 10% → 36px -->
  <text x="215" y="182" text-anchor="end" fill="#ccc" font-size="10">historical claim velocity</text>
  <rect x="220" y="170" width="36" height="16" rx="4" fill="#FFA95A" opacity="0.7"/>
  <text x="261" y="182" fill="#FFA95A" font-size="9" font-weight="bold">  10%</text>

  <!-- 6. Weather source cross-val — 5% → 18px -->
  <text x="215" y="208" text-anchor="end" fill="#ccc" font-size="10">weather consensus check</text>
  <rect x="220" y="196" width="18" height="16" rx="4" fill="#FF8B5A" opacity="0.6"/>
  <text x="243" y="208" fill="#FF8B5A" font-size="9" font-weight="bold">  5%</text>
</svg>

</div>

---

## what makes gigshield different

### 🧬 income fingerprinting
every worker has a unique earnings curve — peak hours, active zones, weekly rhythm. gigshield builds an **individual behavioral baseline** at onboarding. when a claim fires, it cross-checks: *does this person's activity pattern actually look disrupted?* a spoofer's baseline never breaks. a real worker's does.

```python
# simplified income fingerprint check
baseline_activity = worker.avg_orders_per_hour[current_hour]
actual_activity   = platform_api.get_recent_orders(worker.id, window=2h)
disruption_delta  = baseline_activity - actual_activity
# genuine disruption → delta is large. spoofer → delta ≈ 0.
```

### 🌊 zone liquidity guard
traditional insurance doesn't know it's about to go broke until it already has. gigshield runs a **real-time pool health monitor** — pre-flags concentration risk before payouts fire and soft-caps new activations in high-risk zones during an active event.

```
pool health = (total_reserves) / (projected_max_payout_this_event)
if pool_health < 1.3 → trigger soft-cap + reinsurance flag
```

### 🏆 loyalty trust score
most fraud systems are purely punitive. gigshield flips it — workers **earn trust over time**. consistent premium payments + clean history = faster payouts and lower premiums.

| Trust Tier | Payout Speed | Premium Discount | Unlock |
|------------|-------------|-----------------|--------|
| New        | 6h soft-hold | 0%             | —      |
| Verified   | 2h           | 5%             | 3 months |
| Trusted    | 45 min       | 12%            | 6 months + 0 flags |
| Champion   | instant      | 20%            | 1yr + perfect record |

### ☁️ multi-source weather consensus
gigshield requires **2-of-3 source agreement** before a trigger fires — OpenWeatherMap, IMD data, and satellite-based precipitation index. no single API failure can cause a false payout.

---

## AI/ML stack

| Module | Model | Purpose |
|--------|-------|---------|
| Risk Profiler | Random Forest | weekly risk score per zone |
| Dynamic Pricer | Regression | risk score → weekly premium |
| Income Fingerprinter | LSTM / baseline deviation | behavioral disruption detection |
| Fraud Detector | Isolation Forest | anomaly + peer cluster detection |
| Workability Score | Weighted env. index | payout trigger (W < 40) |
| Pool Health Monitor | Rule-based + projection | liquidity risk management |

**workability score:** $W = 100 - (w_r \cdot R + w_t \cdot T + w_a \cdot A)$ — payout fires when $W < 40$

---

## 🚨 adversarial defense & anti-spoofing

> *mandatory Phase 1 update — response to coordinated GPS spoofing attack vector*

**the attack:** 500 workers. telegram group. GPS spoofer apps. fake location → storm zone → mass false payouts → pool drained.

**gigshield's defense — 6-signal trust score:**

| Signal | Real Worker | GPS Spoofer |
|--------|------------|-------------|
| GPS location | storm zone ✅ | storm zone (faked) ✅ |
| Income fingerprint delta | orders stopped ✅ | orders still running ❌ |
| Accelerometer pattern | sheltering movement ✅ | stationary/home ❌ |
| Cell tower vs GPS match | consistent ✅ | mismatch ❌ |
| Peer cluster anomaly | organic spread ✅ | same-pincode spike ❌ |
| Historical claim velocity | normal ✅ | sudden burst ❌ |

**claim resolution flow:**
```
trust > 0.75 → AUTO-APPROVED (speed based on loyalty tier)
trust 0.45–0.75 → SOFT-HOLD (6h window, auto-resolves if weather persists)
trust < 0.45 → MANUAL REVIEW (15-sec voice note option for worker)
confirmed fraud → FLAGGED + suspended
```

> honest workers in a real flood never wait more than 6 hours. fraudsters are caught at the cluster layer before a single payout fires.

---

## weekly pricing

| Risk Level | Weekly Premium | Coverage |
|------------|---------------|----------|
| 🟡 Low | ₹20 | ₹500 |
| 🟠 Medium | ₹40 | ₹1,000 |
| 🔴 High | ₹70 | ₹1,500 |

premiums recalculate weekly based on forecasted zone risk. loyalty discounts applied on top.

---

## roadmap

- [x] **Phase 1** — architecture, workflow, anti-spoofing, income fingerprinting, liquidity model
- [ ] **Phase 2** — backend APIs, ML training, triggers, claims engine, frontend
- [ ] **Phase 3** — advanced fraud, payment simulation, dual dashboards, final pitch

---

<div align="center">

<svg width="720" height="6" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="botbar" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%"   stop-color="#FFD45A"/>
      <stop offset="33%"  stop-color="#FFA95A"/>
      <stop offset="66%"  stop-color="#FF8B5A"/>
      <stop offset="100%" stop-color="#FF5A5A"/>
    </linearGradient>
  </defs>
  <rect width="720" height="6" rx="3" fill="url(#botbar)"/>
</svg>

<br/>

**gigshield. because the rain shouldn't cost them their rent.**

*Guidewire DEVTrails 2026 — built on 0 sleep and very strong chai ☕*

<br/>

<img src="https://img.shields.io/badge/Anti--Spoofing-6--Signal-FF5A5A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/Income%20Fingerprinting-Novel-FF8B5A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/Pool%20Liquidity%20Guard-Active-FFA95A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/Weather%20Consensus-2%20of%203-FFD45A?style=flat-square&logoColor=000" />

</div>
