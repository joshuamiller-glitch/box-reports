# ALL-NEW STACK, NY PM: WEIGHTED LOOP nypm-own-recent-w (W-COMBO, order 1416Z part 2). Updated 2026-11-24 09:44Z.

**DECISION BASIS: EQUAL L6M ULCER (recent basis, order 1552Z; 15% L6M max-DD / worst-week guard; L3M beside; prior years only as the 15-30% band, RED not chosen).** Candidates are tried at sizes [0.25, 0.5, 1.0, 2.0] relative to 1 lot (lots = round(4 x size)); a stack whose sizes are all 1 is the existing lot-1 stack set. Every window number below is in 1-lot units (x4-lots sets divided by 4).
**CAPS: scaled x4 with the lots: same-side lots cap 6 -> 24, each new-book stream day-cap pair $12,000/$4,800 -> $48,000/$19,200; NOT scaled: sizer thr 0.3 lo 0.5 hi 1.0, p7_daycap, StackCut / BookLock / c_gov / screens / ev_panel / ev_profit values (calibration of lot-linearity: see the CALIBRATION line); weights do not change the dollar layers meaning for the live D7**
**[x4-LOTS ENGINE RUNS ARE NOT LINEAR vs the 1-lot sets (calibration 2, 15:08Z: size-dependent fills, L6M -14%, prior years -21..-31% per lot-unit); compare weighted engine runs with the equal-weight x4-lots calibration set, not with the lot-1 set]**

**The equal-weight loop `nypm-own-recent` is the REFERENCE ROW (its FINAL has no weights).**

Phase **done**; pool 6 books (L2c6916a5.BRP60, L4bdd521a.BRF80_40, L52359bf4.BRP30, L7b1adff3.BRP60, L8dff280f.BRP90, L8e0bf58c.BRS8U); steps 4; stop: no candidate passes the add rule.

## STEPS

| step | move | weights after | stack set | L6M ulcer / maxDD / worst wk / $ per wk | L3M | 2023 | 2024 | 2025 | persistence | worst prior-year maxDD |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | add L52359bf4.BRP30 x1 | (see FINAL) | `TL3_ALN_NP_L52359bf4_R0BRP30` | 2064 / -6398 / -3204 / 1188 | 2454 / -6398 / -3204 / 483 | 3604 / -10745 / -4977 / 179 | 4798 / -12186 / -5767 / 189 | 3153 / -7798 / -3803 / 769 | 0.59 | -12186 |
| 2 | add L8e0bf58c.BRS8U x1 | (see FINAL) | `TL3_ALN_NP_STKd8038520b9` | 3164 / -8914 / -4106 / 2131 | 2184 / -6456 / -3156 / 1817 | 4897 / -16138 / -6442 / 915 | 8668 / -19192 / -6407 / 667 | 5948 / -14078 / -5410 / 866 | 0.67 | -19192 |
| 3 | add L4bdd521a.BRF80_40 x1 | (see FINAL) | `TL3_ALN_NP_STKd824815003` | 2883 / -8928 / -4005 / 3187 | 1931 / -5739 / -4005 / 2897 | 4334 / -16400 / -7871 / 1543 | 7203 / -17025 / -7544 / 854 | 4477 / -14857 / -8806 / 1997 | 0.72 | -17025 |
| 4 | add L2c6916a5.BRP60 x1 | (see FINAL) | `TL3_ALN_NP_STKd893133bd8` | 3038 / -9651 / -4238 / 4217 | 2375 / -7299 / -4238 / 3991 | 4147 / -16658 / -8495 / 1734 | 10616 / -28839 / -10732 / 1353 | 6495 / -19522 / -11299 / 2038 | 0.74 | -28839 |
- prior-year band, step 1 (first book: no stack before; colours vs bare D7 at equal L6M ulcer (information only)): 2023 AMBER / 2024 RED / 2025 GREEN
- prior-year band, step 2 (vs the stack before this step scaled to the candidate L6M ulcer (k = 1.53), information only): 2023 GREEN / 2024 AMBER / 2025 AMBER
- prior-year band, step 3 (vs the stack before this step scaled to the candidate L6M ulcer (k = 0.91), information only): 2023 RED / 2024 AMBER / 2025 RED
- prior-year band, step 4 (vs the stack before this step scaled to the candidate L6M ulcer (k = 1.05), information only): 2023 GREEN / 2024 RED / 2025 RED

## FINAL (weighted): L52359bf4.BRP30 x1 + L8e0bf58c.BRS8U x1 + L4bdd521a.BRF80_40 x1 + L2c6916a5.BRP60 x1

Controls beaten (30): (30, 18, 30) (L6M drawdown-first / L3M / ulcer-only); own persistence 0.74; moves: no swap/drop/resize passed the add rule + gate

### this mix, 1-lot units (ulcer / maxDD / worst wk / $ per wk)

| window | weighted |
|---|---|
| L6M | 3038 / -9651 / -4238 / 4217 |
| L3M | 2375 / -7299 / -4238 / 3991 |
| Y2023 | 4147 / -16658 / -8495 / 1734 |
| Y2024 | 10616 / -28839 / -10732 / 1353 |
| Y2025 | 6495 / -19522 / -11299 / 2038 |

### SCALED TO EQUAL WORST-PRIOR-YEAR MAX DD of the equal-weight final (k = 1.000) beside the equal-weight final ['L52359bf4.BRP30', 'L8e0bf58c.BRS8U', 'L4bdd521a.BRF80_40', 'L2c6916a5.BRP60']

| window | weighted x k | equal weights |
|---|---|---|
| L6M | 3038 / -9651 / -4238 / 4217 | 3038 / -9651 / -4238 / 4217 |
| L3M | 2375 / -7299 / -4238 / 3991 | 2375 / -7299 / -4238 / 3991 |
| Y2023 | 4147 / -16658 / -8495 / 1734 | 4147 / -16658 / -8495 / 1734 |
| Y2024 | 10616 / -28839 / -10732 / 1353 | 10616 / -28839 / -10732 / 1353 |
| Y2025 | 6495 / -19522 / -11299 / 2038 | 6495 / -19522 / -11299 / 2038 |

### today's basis (scaled to equal L6M ulcer, k = 1.000)

| window | weighted x k | equal weights |
|---|---|---|
| L6M | 3038 / -9651 / -4238 / 4217 | 3038 / -9651 / -4238 / 4217 |
| L3M | 2375 / -7299 / -4238 / 3991 | 2375 / -7299 / -4238 / 3991 |
| Y2023 | 4147 / -16658 / -8495 / 1734 | 4147 / -16658 / -8495 / 1734 |
| Y2024 | 10616 / -28839 / -10732 / 1353 | 10616 / -28839 / -10732 / 1353 |
| Y2025 | 6495 / -19522 / -11299 / 2038 | 6495 / -19522 / -11299 / 2038 |

### BARE D7 session stack at the same L6M ulcer as the weighted mix (bare vs bare only)

| L6M | 3038 / -6373 / -1878 / -14 |
| L3M | 3917 / -6043 / -1878 / -266 |
| Y2023 | 3933 / -7564 / -1961 / -143 |
| Y2024 | 3045 / -7504 / -2284 / 191 |
| Y2025 | 5042 / -9396 / -2331 / -84 |
