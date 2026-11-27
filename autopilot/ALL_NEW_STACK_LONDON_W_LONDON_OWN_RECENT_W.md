# ALL-NEW STACK, LONDON: WEIGHTED LOOP london-own-recent-w (W-COMBO, order 1416Z part 2). Updated 2026-11-27 17:19Z.

**DECISION BASIS: EQUAL L6M ULCER (recent basis, order 1552Z; 15% L6M max-DD / worst-week guard; L3M beside; prior years only as the 15-30% band, RED not chosen).** Candidates are tried at sizes [0.25, 0.5, 1.0, 2.0] relative to 1 lot (lots = round(4 x size)); a stack whose sizes are all 1 is the existing lot-1 stack set. Every window number below is in 1-lot units (x4-lots sets divided by 4).
**CAPS: scaled x4 with the lots: same-side lots cap 6 -> 24, each new-book stream day-cap pair $12,000/$4,800 -> $48,000/$19,200; NOT scaled: sizer thr 0.3 lo 0.5 hi 1.0, p7_daycap, StackCut / BookLock / c_gov / screens / ev_panel / ev_profit values (calibration of lot-linearity: see the CALIBRATION line); weights do not change the dollar layers meaning for the live D7**
**[x4-LOTS ENGINE RUNS ARE NOT LINEAR vs the 1-lot sets (calibration 2, 15:08Z: size-dependent fills, L6M -14%, prior years -21..-31% per lot-unit); compare weighted engine runs with the equal-weight x4-lots calibration set, not with the lot-1 set]**

**The equal-weight loop `london-own-recent` is the REFERENCE ROW (its FINAL has no weights).**

Phase **done**; pool 4 books (L12842dde.BRP45, L19201dfc.BRF90_30, L74274eca.BRF120_60, Lc78f2492.BRF90_30); steps 4; stop: no candidate passes the add rule.

## STEPS

| step | move | weights after | stack set | L6M ulcer / maxDD / worst wk / $ per wk | L3M | 2023 | 2024 | 2025 | persistence | worst prior-year maxDD |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | add L19201dfc.BRF90_30 x1 | (see FINAL) | `TL3_ALN_LO_L19201dfc_R0BRF90_30` | 1273 / -3809 / -2673 / 1768 | 1406 / -3402 / -2449 / 1643 | 1913 / -5238 / -2549 / 273 | 4372 / -11780 / -5793 / 251 | 5080 / -12803 / -4448 / 183 | 0.62 | -12803 |
| 2 | add L12842dde.BRP45 x0.25 | (see FINAL) | `TL3_ALN_LO_STKd83fd76625` | 1297 / -3763 / -2220 / 1858 | 1556 / -3763 / -2220 / 1547 | 2385 / -6338 / -3535 / 321 | 2971 / -8764 / -2996 / 393 | 10147 / -17408 / -6971 / 130 | 0.67 | -17408 |
| 3 | add L74274eca.BRF120_60 x0.25 | (see FINAL) | `TL3_ALN_LO_STKd8fd7c3c2d` | 1425 / -4590 / -2361 / 2309 | 1712 / -4590 / -2361 / 2195 | 2939 / -7970 / -5146 / 339 | 1799 / -8461 / -2835 / 613 | 8831 / -18672 / -7020 / 258 | 0.71 | -18672 |
| 4 | resize:L12842dde.BRP45:0.5 | (see FINAL) | `TL3_ALN_LO_STKd8e4ab42ac` | 1515 / -4846 / -2519 / 2508 | 1824 / -4846 / -2283 / 2309 | 3603 / -9037 / -6115 / 404 | 2199 / -10083 / -4090 / 666 | 11792 / -22867 / -9457 / 244 | 0.72 | -22867 |
- prior-year band, step 1 (first book: no stack before; colours vs bare D7 at equal L6M ulcer (information only)): 2023 RED / 2024 RED / 2025 RED
- prior-year band, step 2 (vs the stack before this step scaled to the candidate L6M ulcer (k = 1.02), information only): 2023 RED / 2024 GREEN / 2025 RED
- prior-year band, step 3 (vs the stack before this step scaled to the candidate L6M ulcer (k = 1.10), information only): 2023 RED / 2024 GREEN / 2025 GREEN
- prior-year band, step 4 (vs the stack before this step scaled to the candidate L6M ulcer (k = 1.06), information only): 2023 AMBER / 2024 RED / 2025 AMBER

## FINAL (weighted): L19201dfc.BRF90_30 x1 + L12842dde.BRP45 x0.5 + L74274eca.BRF120_60 x0.25

Controls beaten (30): (30, 23, 30) (L6M drawdown-first / L3M / ulcer-only); own persistence 0.72; moves: no swap/drop/resize passed the add rule + gate

### this mix, 1-lot units (ulcer / maxDD / worst wk / $ per wk)

| window | weighted |
|---|---|
| L6M | 1515 / -4846 / -2519 / 2508 |
| L3M | 1824 / -4846 / -2283 / 2309 |
| Y2023 | 3603 / -9037 / -6115 / 404 |
| Y2024 | 2199 / -10083 / -4090 / 666 |
| Y2025 | 11792 / -22867 / -9457 / 244 |

### SCALED TO EQUAL WORST-PRIOR-YEAR MAX DD of the equal-weight final (k = 0.560) beside the equal-weight final ['L19201dfc.BRF90_30']

| window | weighted x k | equal weights |
|---|---|---|
| L6M | 848 / -2713 / -1411 / 1404 | 1273 / -3809 / -2673 / 1768 |
| L3M | 1021 / -2713 / -1278 / 1293 | 1406 / -3402 / -2449 / 1643 |
| Y2023 | 2017 / -5060 / -3424 / 226 | 1913 / -5238 / -2549 / 273 |
| Y2024 | 1231 / -5645 / -2290 / 373 | 4372 / -11780 / -5793 / 251 |
| Y2025 | 6602 / -12803 / -5295 / 137 | 5080 / -12803 / -4448 / 183 |

### today's basis (scaled to equal L6M ulcer, k = 0.840)

| window | weighted x k | equal weights |
|---|---|---|
| L6M | 1273 / -4072 / -2117 / 2107 | 1273 / -3809 / -2673 / 1768 |
| L3M | 1533 / -4072 / -1918 / 1940 | 1406 / -3402 / -2449 / 1643 |
| Y2023 | 3028 / -7593 / -5138 / 340 | 1913 / -5238 / -2549 / 273 |
| Y2024 | 1847 / -8473 / -3436 / 559 | 4372 / -11780 / -5793 / 251 |
| Y2025 | 9908 / -19214 / -7946 / 205 | 5080 / -12803 / -4448 / 183 |

### BARE D7 session stack at the same L6M ulcer as the weighted mix (bare vs bare only)

| L6M | 1515 / -3158 / -1743 / 22 |
| L3M | 1248 / -2567 / -1743 / 55 |
| Y2023 | 1075 / -2534 / -686 / 24 |
| Y2024 | 4787 / -8517 / -1929 / -125 |
| Y2025 | 2469 / -4477 / -1135 / -33 |
