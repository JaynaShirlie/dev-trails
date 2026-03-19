<div align="center">

# 🛡️ GigShield

### *When the storm hits — the payout drops. Automatically.*

**AI-powered parametric income insurance for India's gig delivery workers.**
No claims. No calls. No waiting.

<br>

![Phase](https://img.shields.io/badge/Phase_1-Ideation_%26_Foundation-00c432?style=flat-square)
![Persona](https://img.shields.io/badge/Persona-Food_Delivery_(Zomato%2FSwiggy)-00c432?style=flat-square)
![Status](https://img.shields.io/badge/Submitted-On_Time-00c432?style=flat-square)
![Defense](https://img.shields.io/badge/Anti--Spoofing-Included-ff3c3c?style=flat-square)

<br>

| 12M+ gig workers | ₹0 current safety net | 27% income lost in disruptions | **< 90s payout** |
|:---:|:---:|:---:|:---:|

</div>

---

## 🎯 The Problem

India's delivery riders (Zomato, Swiggy) lose **₹600–900 in a single rain event.** No platform compensates. Traditional insurance is built for salaried employees — monthly premiums, forms, and 30-day waits don't work for someone earning ₹700/day.

**GigShield's answer →** Parametric model. External trigger fires (rain > 50mm/hr, AQI > 300, curfew declared) → payout hits UPI in **under 90 seconds**. No rider action needed. Ever.

---

## 👤 Persona — Rajan, 26

> *Zomato delivery partner, Bengaluru. ₹18–22K/month. Bike EMI. Zero savings buffer. One bad monsoon week = missed rent.*

`UPI Native` `2-Wheeler` `Tier-1 Cities` `Peak: 6–9PM` `Monsoon = Crisis`

---

## 🔄 How It Works

```
Rider onboards (< 3 min)  →  Picks weekly plan  →  GigShield monitors 24/7
        ↓
Trigger fires (rain / AQI / curfew)
        ↓
Fraud engine runs 12-point check (< 8 sec)
        ↓
Clean claim → ₹ hits UPI in 90 seconds ✅
```

---

## 💰 Weekly Plans

| Tier | Premium | Coverage | Events/Week |
|:---:|:---:|:---:|:---:|
| Basic Shield | ₹29/week | ₹400/day | 2 |
| **Pro Shield ⭐** | **₹49/week** | **₹700/day** | **3** |
| Max Shield | ₹79/week | ₹1,200/day | 5 |

**Dynamic pricing formula:**
```
premium = base × zone_risk(0.8–1.4) × seasonal(1.3x monsoon) × activity_discount(0.9x)
```

---

## ⚡ Parametric Triggers

| # | Event | Threshold | API Source |
|:---:|---|---|---|
| 1 | 🌧️ Heavy Rain | > 50mm/hr for 30 min | OpenWeatherMap |
| 2 | 😷 Air Pollution | AQI > 300 for 2 hrs | CPCB / AirVisual |
| 3 | 🚨 Curfew / Section 144 | Official order in zone | News API + Govt feeds |
| 4 | 🌊 Flash Flood | IMD Red Alert + road gridlock > 60 min | IMD + HERE Traffic |
| 5 | 📱 Platform Downtime | App unresponsive > 45 min | Zomato/Swiggy health (simulated) |

---

## 🧠 AI / ML Architecture

| Model | Algorithm | Purpose |
|---|---|---|
| Risk Pricing Engine | XGBoost (14 features) | Dynamic weekly premium calculation |
| Fraud Detector | Isolation Forest + LSTM | Real-time anomaly + behavioral drift detection |
| Disruption Forecaster | Prophet + LSTM | Next-week disruption probability by zone |
| Zone Risk Mapper | DBSCAN + Geospatial | Hyper-local risk tier clustering |
| Claims Classifier | Random Forest | AUTO-APPROVE / SOFT-FLAG / HARD-BLOCK |
| Support Chatbot | Fine-tuned LLM | Hindi / Kannada / Tamil rider support |

---

## 🚨 Adversarial Defense & Anti-Spoofing Strategy

> **Market Crash Response — Phase 1 Mandatory Update**

```
THREAT  : 500 actors · Telegram-coordinated · GPS spoofing apps
ATTACK  : Fake location → spoofed disruption zone → mass false claims
DAMAGE  : Liquidity pool drained
ROOT CAUSE: Platform trusted GPS as the single source of truth
OUR FIX : GPS is ONE signal among TWELVE. Always was.
```

---

### 1️⃣ Differentiating Real Riders vs Bad Actors

| Signal | Source | How it catches spoofing |
|---|---|---|
| 📳 Motion pattern | IMU (accelerometer/gyro) | Real riders show 2-wheeler vibration signatures. Stationary spoofing shows flat motion. |
| 📡 Cell tower vs GPS delta | Telecom network | GPS is fakeable. Cell towers aren't. Mismatch = instant red flag. |
| 📦 Last order timestamp | Platform API | Genuine rider has order activity within 60 min pre-disruption. Fraud actor has zero. |
| 📱 App foreground state | Device telemetry | Real riders have delivery app in foreground. Spoofers have the spoofing tool open instead. |
| 📊 Behavioral baseline | LSTM (90-day history) | First-ever claim on day of mass coordinated event = anomalous. Model flags it. |
| 🌦️ GPS vs weather grid | 500m resolution API | Claimed zone shows red alert but rider's exact coordinates show 12mm/hr, not 60mm/hr. |

---

### 2️⃣ Detecting a Coordinated Fraud Ring

| Detection Method | What It Catches |
|---|---|
| 📈 **Claim velocity spike** | > 3 std deviations above zone mean in 30 min → entire zone soft-held. Would've caught the 500-person syndicate instantly. |
| 🔏 **Device fingerprint clustering** | 50+ claims with identical hashed device profiles = account farm. Auto-blocked. |
| 🌐 **IP / VPN detection** | Spoofing apps route through VPNs. Same IP/exit node across multiple claims = flagged. |
| ⏱️ **Timestamp uniformity** | Real riders submit staggered over 40 min. Telegram "GO" signal = submissions within seconds. We detect the batch. |
| 🆔 **KYC graph analysis** | Graph ML detects accounts sharing bank account, UPI ID, or Aadhaar address at onboarding — before the attack. |
| 📋 **Platform activity cross-check** | Fraud actors aren't real riders. Zero Zomato/Swiggy session data = hard block. |

---

### 3️⃣ UX Balance — Flagged ≠ Punished

> A rider with bad signal in a storm is not a criminal.

```
Score ≥ 80  →  ✅ AUTO-APPROVE   Payout in < 90 seconds. No friction.
Score 55–79 →  ⚠️  SOFT-FLAG     "Payout reserved. Verifying — up to 15 mins."
                                  System re-polls signals. One-tap confirm if needed.
                                  Guaranteed resolution in 2 hrs.
Score < 55  →  🚫 HARD-BLOCK    Clear denial reason given. Human appeal in 24 hrs.
                                  No vague rejections. No immediate bans.
```

**Fraud score breakdown (100 pts):**

| Signal | Weight |
|---|---|
| GPS ↔ Cell Tower match | 20 pts |
| Platform activity verified | 25 pts |
| Motion sensor authentic | 15 pts |
| No velocity spike in zone | 20 pts |
| Behavioral history normal | 12 pts |
| No IP / network flag | 8 pts |

---

## 🏗️ Tech Stack

| Layer | Tech |
|---|---|
| Mobile App | React Native + Expo |
| Admin Dashboard | Next.js 14 + Tailwind |
| Backend API | Node.js + Fastify |
| Database | PostgreSQL + Redis |
| ML Pipeline | Python + FastAPI + Scikit-learn |
| Trigger Engine | Node-cron + Bull Queue |
| Payments | Razorpay test mode + UPI |
| Weather / AQI | OpenWeatherMap + CPCB |
| Auth | JWT + Phone OTP |
| Hosting | AWS (EC2 + RDS + Lambda) |
| Fraud | Custom ML + IPQualityScore API |

---

## 🗓️ Roadmap

| Phase | Timeline | Focus |
|---|---|---|
| ✅ **Phase 1** | Mar 4–20 | Ideation, architecture, adversarial defense, README |
| 🔲 **Phase 2** | Mar 21–Apr 4 | Onboarding, policy UI, premium ML, 5 triggers, mock payouts |
| 🔲 **Phase 3** | Apr 5–17 | Full fraud engine, insurer dashboard, vernacular bot, demo video |

---

## ⛔ Out of Scope

> Per DEVTrails 2026 golden rules — GigShield covers **lost income only.**

`❌ Health insurance` `❌ Accident claims` `❌ Vehicle repair` `❌ Life insurance`

---

<div align="center">

**GigShield · Guidewire DEVTrails 2026 · Phase 1 · Food Delivery Persona**
*README v2.0 — Adversarial Defense Included · March 20, 2026*

</div>
