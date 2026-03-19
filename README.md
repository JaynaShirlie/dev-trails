<div align="center">

<img src="https://img.shields.io/badge/Phase-1%20Seed-FFD700?style=for-the-badge&logoColor=black" />
<img src="https://img.shields.io/badge/DEVTrails-2026-0066CC?style=for-the-badge" />
<img src="https://img.shields.io/badge/Status-Active-22C55E?style=for-the-badge" />


<div align="center">
<pre>
 ██████╗ ██╗ ██████╗ ███████╗██╗  ██╗██╗███████╗██╗     ██████╗ 
██╔════╝ ██║██╔════╝ ██╔════╝██║  ██║██║██╔════╝██║     ██╔══██╗
██║  ███╗██║██║  ███╗███████╗███████║██║█████╗  ██║     ██║  ██║
██║   ██║██║██║   ██║╚════██║██╔══██║██║██╔══╝  ██║     ██║  ██║
╚██████╔╝██║╚██████╔╝███████║██║  ██║██║███████╗███████╗██████╔╝
 ╚═════╝ ╚═╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚═════╝
</pre>
</div>

### *parametric income insurance. zero claims. automatic payouts. built for the rain.*

**`Python`** **`FastAPI`** **`Scikit-learn`** **`MongoDB`** **`OpenWeatherMap`** **`Razorpay`**

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
traditional insurance doesn't know it's about to go broke until it already has. gigshield runs a **real-time pool health monitor**. if one zone has 200 active policies and a red-alert storm hits, the system pre-flags concentration risk before payouts fire — and can soft-cap new policy activations in high-risk zones during an active event.

```
pool health = (total_reserves) / (projected_max_payout_this_event)
if pool_health < 1.3 → trigger soft-cap + reinsurance flag
```

### 🏆 loyalty trust score
most fraud systems are purely punitive. gigshield flips it — workers **earn trust over time**. consistent premium payments, no anomalies, verified work history = higher trust tier = faster payouts and lower premiums.

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
| 🟢 Low | ₹20 | ₹500 |
| 🟡 Medium | ₹40 | ₹1,000 |
| 🔴 High | ₹70 | ₹1,500 |

premiums recalculate weekly based on forecasted zone risk. loyalty discounts applied on top.

---

## roadmap

- [x] **Phase 1** — architecture, workflow, anti-spoofing, income fingerprinting, liquidity model
- [ ] **Phase 2** — backend APIs, ML training, triggers, claims engine, frontend
- [ ] **Phase 3** — advanced fraud, payment simulation, dual dashboards, final pitch

---

<div align="center">

**gigshield. because the rain shouldn't cost them their rent.**

*Guidewire DEVTrails 2026 — built on 0 sleep and very strong chai ☕*

<img src="https://img.shields.io/badge/Anti--Spoofing-6--Signal-FF6B35?style=flat-square" />
<img src="https://img.shields.io/badge/Income%20Fingerprinting-Novel-8B5CF6?style=flat-square" />
<img src="https://img.shields.io/badge/Pool%20Liquidity%20Guard-Active-0066CC?style=flat-square" />

</div>
