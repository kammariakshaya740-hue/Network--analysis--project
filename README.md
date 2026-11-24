# Capstone Project: Network Analysis + Correction Design

**Author:** <your name>
**Course:** Electrical Network Analysis
**Date:** November 2026

## Objective

1. Analyse a DC resistive network using Thevenin's and Norton's theorems, verify the result by direct analysis, and find the condition for maximum power transfer.
2. Design a capacitor for power factor correction of an AC load.

---

## Part A: Network Analysis (DC Circuit)

### Circuit

```
        R1 = 4 Ω           A
 +12V ----/\/\/\----+-------+------+
                    |       |      |
                   R2      R_L     |
                  6 Ω      3 Ω     |
                    |       |      |
 GND ---------------+-------+------+
```

Given: Vs = 12 V, R1 = 4 Ω, R2 = 6 Ω, R_L = 3 Ω (load between node A and ground).

### 1. Thevenin equivalent (R_L removed)

- Vth = Vs × R2 / (R1 + R2) = 12 × 6 / 10 = **7.2 V**
- Rth = R1 ∥ R2 (source shorted) = (4 × 6) / (4 + 6) = **2.4 Ω**
- Load current: I_L = Vth / (Rth + R_L) = 7.2 / 5.4 = **1.333 A**
- Load voltage: V_L = I_L × R_L = **4 V**

### 2. Norton equivalent

- Short-circuit current (A shorted to ground, R2 bypassed): I_N = Vs / R1 = 12 / 4 = **3 A**
- Rth = **2.4 Ω**
- Check: Vth = I_N × Rth = 3 × 2.4 = 7.2 V (matches Thevenin)

### 3. Verification by direct analysis

- R2 ∥ R_L = (6 × 3) / 9 = 2 Ω
- Total resistance = 4 + 2 = 6 Ω
- Source current = 12 / 6 = 2 A
- V_A = 2 × 2 = 4 V, so I_L = 4 / 3 = **1.333 A** (matches)

### 4. Maximum power transfer

- Maximum power is delivered when R_L = Rth = **2.4 Ω**
- P_max = Vth² / (4 × Rth) = 51.84 / 9.6 = **5.4 W**
- At the actual load (R_L = 3 Ω): P = I_L² × R_L = 1.333² × 3 = **5.33 W**, slightly below the maximum, as expected.

### Part A results

| Quantity | Value |
|---|---|
| Vth | 7.2 V |
| Rth | 2.4 Ω |
| I_N | 3 A |
| Load current | 1.333 A |
| Load voltage | 4 V |
| Max power (at R_L = 2.4 Ω) | 5.4 W |
| Power at R_L = 3 Ω | 5.33 W |

---

## Part B: Correction Design (Power Factor Correction)

### Problem

A single-phase load on a 230 V, 50 Hz supply draws P = 5 kW at 0.7 power factor lagging. Design a parallel capacitor to improve the power factor to 0.95 lagging.

### Solution

**Before correction**
- φ₁ = cos⁻¹(0.7) = 45.57°
- Q₁ = P × tan φ₁ = 5000 × 1.0202 = **5101 VAr**
- Line current I₁ = P / (V × pf) = 5000 / (230 × 0.7) = **31.1 A**

**After correction**
- φ₂ = cos⁻¹(0.95) = 18.19°
- Q₂ = P × tan φ₂ = 5000 × 0.3287 = **1643 VAr**
- Line current I₂ = 5000 / (230 × 0.95) = **22.9 A**

**Capacitor design**
- Required reactive power: Q_c = Q₁ − Q₂ = 5101 − 1643 = **3458 VAr**
- C = Q_c / (ω V²), where ω = 2π × 50 = 314.16 rad/s
- C = 3458 / (314.16 × 230²) = **≈ 208 µF**

### Part B results

| Quantity | Before | After |
|---|---|---|
| Power factor | 0.70 lag | 0.95 lag |
| Reactive power | 5101 VAr | 1643 VAr |
| Line current | 31.1 A | 22.9 A |
| Capacitor | none | 208 µF |

---

## Conclusion

- Thevenin, Norton and direct analysis all give the same load current (1.333 A), confirming the equivalents are correct.
- Maximum power transfer happens when the load equals the Thevenin resistance (2.4 Ω); the given 3 Ω load is close to this and so draws nearly the maximum power.
- A 208 µF capacitor raises the power factor from 0.70 to 0.95 and cuts the line current by about 26%, which reduces line losses and supply loading.
kammari Akshaya 
