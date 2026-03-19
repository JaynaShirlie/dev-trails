<div align="center">

<img src="https://img.shields.io/badge/Phase-1%20%E2%80%94%20Seed-FFD700?style=for-the-badge&logoColor=black" />
<img src="https://img.shields.io/badge/DEVTrails-2026-0066CC?style=for-the-badge" />
<img src="https://img.shields.io/badge/Status-Submitted-22C55E?style=for-the-badge" />

<br/><br/>

```
   ██████╗ ██╗ ██████╗ ███████╗██╗  ██╗██╗███████╗██╗     ██████╗ 
  ██╔════╝ ██║██╔════╝ ██╔════╝██║  ██║██║██╔════╝██║     ██╔══██╗
  ██║  ███╗██║██║  ███╗███████╗███████║██║█████╗  ██║     ██║  ██║
  ██║   ██║██║██║   ██║╚════██║██╔══██║██║██╔══╝  ██║     ██║  ██║
  ╚██████╔╝██║╚██████╔╝███████║██║  ██║██║███████╗███████╗██████╔╝
   ╚═════╝ ╚═╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚═════╝ 
```

### *your safety net. zero drama. automatic payout. no cap.*

<br/>

**AI-Powered Parametric Income Insurance for India's Gig Workers**

`Python` `FastAPI` `Scikit-learn` `MongoDB` `OpenWeatherMap` `Razorpay`

<br/>

</div>

---

## the vibe check 🌧️

> a zomato partner leaves home at 7am. by 9am the city is underwater. no deliveries = no money. no money = no rent.  
> **gigshield detects the rain. gigshield pays them. they didn't even have to ask.**

that's it. that's the whole thing.

---

## what's actually broken rn

india has **11M+ gig delivery workers**. rain hits → they lose ₹300-500/day. no one covers that. traditional insurance? weeks of paperwork for ₹500. hard pass.

```
gig worker income loss from weather disruptions → 20-30% of monthly earnings
existing safety net → absolutely nothing
gigshield's job → fix that
```

---

## how gigshield works (the full flow)

<div align="center">

```
┌─────────────────────────────────────────────────────────────┐
│                     GIGSHIELD FLOW                          │
└─────────────────────────────────────────────────────────────┘

  [ sign up ] 
      ↓
  [ enter location + platform + avg weekly income ]
      ↓
  [ AI risk profiling ] ← weather history + zone data + past disruptions
      ↓
  [ dynamic weekly premium generated ] ← ₹20 / ₹40 / ₹70 based on risk
      ↓
  [ pay weekly. coverage activated. ]
      ↓
  [ system watches weather APIs 24/7 ]
      ↓
  [ threshold crossed? (rain > 50mm, temp > 42°C, AQI > 300) ]
      ↓
  ┌───────────────────────────────────────┐
  │     FRAUD CHECK (anti-spoofing)       │  ← NEW. mandatory. explained below.
  └───────────────────────────────────────┘
      ↓ (legit claim)
  [ workability score drops below threshold ]
      ↓
  [ claim auto-triggered. user notified. ]
      ↓
  [ payout calculated based on predicted daily loss ]
      ↓
  [ money hits UPI / Razorpay. done. zero touch. ]
```

</div>

---

## the brain — AI/ML stack 🧠

| Module | What it does | Model |
|--------|-------------|-------|
| **Risk Profiler** | scores each worker's location risk weekly | Random Forest |
| **Dynamic Pricer** | converts risk score → weekly premium | Rule-based + regression |
| **Earnings Estimator** | predicts what the worker *would* have earned | Linear Regression |
| **Fraud Detector** | catches bad actors before payout | Isolation Forest |
| **Workability Score** | 0-100 score of "can this person work right now?" | Weighted env. index |

### the workability score formula

$$W = 100 - \left(w_r \cdot R + w_t \cdot T + w_a \cdot A\right)$$

where $R$ = rainfall index, $T$ = temperature index, $A$ = AQI index, and $w_r, w_t, w_a$ are learned weights.  
**payout triggers when W < 40.**

---

## weekly pricing model 💸

> gig workers get paid weekly. so we charge weekly. simple math.

| Risk Level | Weekly Premium | Max Coverage |
|------------|---------------|--------------|
| 🟢 Low     | ₹20           | ₹500/week    |
| 🟡 Medium  | ₹40           | ₹1,000/week  |
| 🔴 High    | ₹70           | ₹1,500/week  |

premiums adjust dynamically every week based on forecasted weather risk for that worker's zone.

---

## parametric triggers ⚡

no paperwork. no adjuster. just data.

```python
TRIGGERS = {
    "heavy_rain":    {"threshold": 50,  "unit": "mm",  "coverage_hours": 6},
    "extreme_heat":  {"threshold": 42,  "unit": "°C",  "coverage_hours": 4},
    "severe_aqi":    {"threshold": 300, "unit": "AQI", "coverage_hours": 8},
}
# when threshold crossed → workability score computed → payout auto-initiated
```

---

## 🚨 adversarial defense & anti-spoofing strategy

> *this section addresses the Phase 1 mandatory market crash update — GPS spoofing by coordinated fraud rings.*

### the threat
500 delivery workers. telegram group. GPS spoofer apps. fake their location into a rain alert zone. trigger mass payouts. drain the pool. **this is a real attack vector.**

### 1. the differentiation — how we tell real from fake

gigshield uses a **multi-signal trust score**, not just GPS:

```
TRUST SCORE = f(GPS, accelerometer, platform_activity, peer_density, network_cell, historical_pattern)
```

| Signal | Legit Worker in Rain | GPS Spoofer at Home |
|--------|---------------------|---------------------|
| GPS location | storm zone ✅ | storm zone (faked) ✅ |
| Accelerometer | erratic / sheltering movement | stationary / home pattern ❌ |
| Platform app activity | last order 45 min ago, then gone | orders still completing normally ❌ |
| Cell tower triangulation | matches GPS zone ✅ | doesn't match home cell ❌ |
| Peer density signal | 80% of nearby workers also stopped | only this cluster claiming ❌ |
| Historical behavior | consistent zone pattern | sudden zone jump ❌ |

**if trust score < threshold → claim flagged, not rejected.**

### 2. the data — beyond GPS

gigshield analyzes:

- **Device motion sensors** — a person sheltering from rain moves differently than someone sitting at home
- **Platform-side order flow** — if the delivery app still shows them completing orders during a "disruption", something's off
- **Network cell ID** — cross-referenced against claimed GPS location
- **Hyper-local peer clustering** — if 50 workers from the same telegram-like group all claim simultaneously from one pincode, anomaly score spikes
- **Historical claim velocity** — first claim ever during a storm = normal. 4 claims in 3 weeks from a zone that had 1 alert = suspicious
- **Weather source cross-validation** — OpenWeather + IMD + satellite imagery. if one source says red alert and two say clear, the trigger holds but fraud score increases

### 3. the UX balance — flagged ≠ rejected

this is the hard part. a worker with a bad network in a flood zone looks exactly like a spoofer. we don't punish them.

```
CLAIM STATUS FLOW:

AUTO-APPROVED  → trust score > 0.75 + weather confirmed + no peer anomaly
     ↓
SOFT-HOLD (6h) → trust score 0.45–0.75 → system waits for additional signal resolution
     ↓              worker gets: "your claim is being verified. payment by [time]."
     ↓              if weather persists + no red flags → auto-approved after window
MANUAL REVIEW  → trust score < 0.45 OR peer cluster anomaly detected
     ↓              human reviewer + worker can submit a 15-sec voice note
     ↓              most legit edge cases resolved here
FLAGGED/DENIED → confirmed spoofing pattern. account suspended. reported.
```

> **the promise:** an honest worker in a genuine flood will never wait more than 6 hours. a fraudster running a spoofing app gets caught at the cluster-anomaly layer before payout happens.

---

## tech stack 🛠️

```
Backend      → Python + FastAPI
Frontend     → HTML / CSS / JS (web-first for demo ease)
ML Models    → Scikit-learn (Random Forest, Isolation Forest, Linear Regression)
Database     → MongoDB (user data, claims) + PostgreSQL (financial records)
Weather API  → OpenWeatherMap (free tier)
Payments     → Razorpay Test Mode
Deployment   → to be finalized in Phase 2
```

**why web over mobile?** faster to build, easier to demo to judges, accessible on any device a delivery partner carries. mobile-first UI design regardless.

---

## phase roadmap 🗺️

- [x] **Phase 1** — Ideation, architecture, workflow design, anti-spoofing strategy
- [ ] **Phase 2** — Backend APIs, ML models, automated triggers, claims engine
- [ ] **Phase 3** — Advanced fraud detection, payment simulation, dashboards, final pitch

---

## the team

> built with 0 sleep and very strong chai ☕  
> *Guidewire DEVTrails 2026 — Unicorn Chase*

---

<div align="center">

**gigshield. because the rain shouldn't cost them their rent.**

<img src="https://img.shields.io/badge/Phase%201-Complete-22C55E?style=flat-square" />
<img src="https://img.shields.io/badge/Anti--Spoofing-Implemented-FF6B35?style=flat-square" />
<img src="https://img.shields.io/badge/Weekly%20Pricing-Active-0066CC?style=flat-square" />

</div>
