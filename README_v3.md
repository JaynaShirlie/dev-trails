<div align="center">

<img src="https://img.shields.io/badge/Phase-1%20Seed-FFD45A?style=for-the-badge&logoColor=000000" />
<img src="https://img.shields.io/badge/DEVTrails-2026-FF8B5A?style=for-the-badge&logoColor=000000" />
<img src="https://img.shields.io/badge/Status-Active-FF5A5A?style=for-the-badge&logoColor=000000" />

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

## the problem

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
        payout hits UPI. done.
```

---

## what makes gigshield different

**🧬 income fingerprinting** — every worker has a unique earnings curve. gigshield builds a personal behavioral baseline at onboarding and checks if activity *actually dropped* during a claimed disruption. a spoofer at home keeps getting orders. a real worker doesn't.

**🌊 zone liquidity guard** — real-time pool health monitor. if projected payouts in a zone threaten reserves, the system soft-caps new activations before a single payout fires. traditional insurance finds out it's broke after the fact. gigshield doesn't.

**🏆 loyalty trust score** — workers earn faster payouts and lower premiums over time. clean history = Champion tier = instant payout. new accounts get a 6h verification window. fraud systems that only punish miss half the picture.

**☁️ multi-source weather consensus** — 2-of-3 source agreement required (OpenWeatherMap + IMD + satellite index) before any trigger fires. one bad API can't cause a false payout.

---

## charts

**fig 1 — weekly premium vs max coverage by risk tier**
<div align="center">
<img src="./assets/chart_pricing.svg" width="680" alt="Fig 1: Weekly Premium vs Coverage by Risk Tier"/>
</div>

> solid bars = weekly premium paid. faded bars = maximum coverage unlocked. low-risk workers pay ₹20 for ₹500 cover; high-risk pay ₹70 for ₹1,500.

---

**fig 2 — loyalty tier → payout speed funnel**
<div align="center">
<img src="./assets/chart_funnel.svg" width="680" alt="Fig 2: Loyalty Trust Tier Payout Speed Funnel"/>
</div>

> workers climb tiers through consistent payments and clean claim history. champion tier = instant payout + 20% premium discount.

---

**fig 3 — 6-signal anti-spoofing detection weights**
<div align="center">
<img src="./assets/chart_signals.svg" width="680" alt="Fig 3: Anti-Spoofing Signal Detection Weights"/>
</div>

> income fingerprint carries the highest weight (28%) because it's the hardest signal to fake. GPS alone is the easiest — so we weight it last.

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

**the attack:** 500 workers. telegram group. GPS spoofer apps. fake location → storm zone → mass false payouts → pool drained.

| Signal | Real Worker | GPS Spoofer |
|--------|------------|-------------|
| GPS location | storm zone ✅ | storm zone (faked) ✅ |
| Income fingerprint delta | orders stopped ✅ | orders still running ❌ |
| Accelerometer pattern | sheltering movement ✅ | stationary/home ❌ |
| Cell tower vs GPS match | consistent ✅ | mismatch ❌ |
| Peer cluster anomaly | organic spread ✅ | same-pincode spike ❌ |
| Historical claim velocity | normal ✅ | sudden burst ❌ |

```
trust > 0.75  → AUTO-APPROVED
trust 0.45–0.75 → SOFT-HOLD 6h (auto-resolves if weather persists)
trust < 0.45  → MANUAL REVIEW + optional 15-sec worker voice note
confirmed fraud → FLAGGED + suspended
```

> honest workers in a real flood never wait more than 6 hours.

---

## pricing

| Risk Level | Weekly Premium | Max Coverage |
|------------|---------------|--------------|
| 🟡 Low | ₹20 | ₹500 |
| 🟠 Medium | ₹40 | ₹1,000 |
| 🔴 High | ₹70 | ₹1,500 |

---

## roadmap

- [x] **Phase 1** — architecture, workflows, anti-spoofing, income fingerprinting, liquidity model
- [ ] **Phase 2** — backend APIs, ML models, triggers, claims engine, frontend
- [ ] **Phase 3** — advanced fraud, payment simulation, dashboards, final pitch

---

<div align="center">

**gigshield. because the rain shouldn't cost them their rent.**

*Guidewire DEVTrails 2026 — built on 0 sleep and very strong chai ☕*

<br/>

<img src="https://img.shields.io/badge/Anti--Spoofing-6--Signal-FF5A5A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/Income%20Fingerprinting-Novel-FF8B5A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/Pool%20Liquidity%20Guard-Active-FFA95A?style=flat-square&logoColor=000" />
<img src="https://img.shields.io/badge/Weather%20Consensus-2%20of%203-FFD45A?style=flat-square&logoColor=000" />

</div>
