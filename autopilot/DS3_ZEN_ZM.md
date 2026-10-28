# DS3_ZEN_ZM - F5, the Zen model as written (ZM1-ZM4), D3ZF5, 2026-10-28

Research only. Status: IN PROGRESS (this file is appended section by section; the verdict line is inserted at the end).

## 1. M8 frequency table (descriptive, written BEFORE any tier P&L and before the prereg hash)

Source: PRE 2024-02-01..2025-06-30 (73.6 calendar weeks, 363 labelled days), closed-bar detector `code/zen/f5/zen_zm.py` (unit test t_leak: signals, FVG/OB zone flags and red flags identical when all bars after 2025-01-02 are deleted; 26,352 ZM1 signals before the cut, all True). Counts are SETUPS (hold candles, first of an episode; entry bar at the window shown), before the one-open-trade rule; trades after sequencing are smaller and are reported with the P&L. Definitions are exactly those of the plan section 10 (FVG = body gap, first or second touch, OB = candle body, VWAP anchored 09:30) with the tolerances: touch/hold within 5 pt, stack d in {3,5,8} pt, FVG/OB within 5 pt of the level (touched line for ZM1-based, E/V midpoint for stack-based tiers). CSV: l2vast/ds3/out/zen/zm/M8_frequency_PRE.csv.

| cell | PRIMARY | W0930 | W10 | W11 | W12 | W13 | W14 | RTH | PRIMARY_per_wk | RTH_per_wk |
|---|---|---|---|---|---|---|---|---|---|---|
| ZM1 | 4126 | 1288 | 1376 | 984 | 907 | 859 | 1379 | 7307 | 56.08 | 99.32 |
| ZM2_3 | 473 | 62 | 84 | 145 | 148 | 96 | 125 | 697 | 6.43 | 9.47 |
| ZM2_5 | 728 | 124 | 138 | 201 | 226 | 163 | 179 | 1093 | 9.9 | 14.86 |
| ZM2_8 | 1141 | 195 | 242 | 302 | 348 | 249 | 291 | 1724 | 15.51 | 23.43 |
| ZM3_ZM1_FVG | 3668 | 1166 | 1211 | 876 | 802 | 779 | 1257 | 6557 | 49.86 | 89.12 |
| ZM3_ZM1_OB | 1776 | 482 | 590 | 424 | 396 | 366 | 650 | 3144 | 24.14 | 42.73 |
| ZM3_ZM2_3_FVG | 439 | 57 | 76 | 136 | 134 | 93 | 122 | 653 | 5.97 | 8.88 |
| ZM3_ZM2_3_OB | 217 | 18 | 38 | 70 | 65 | 44 | 73 | 331 | 2.95 | 4.5 |
| ZM3_ZM2_5_FVG | 667 | 117 | 127 | 182 | 199 | 159 | 169 | 1009 | 9.07 | 13.71 |
| ZM3_ZM2_5_OB | 348 | 51 | 73 | 92 | 108 | 75 | 96 | 529 | 4.73 | 7.19 |
| ZM3_ZM2_8_FVG | 1039 | 183 | 222 | 270 | 307 | 240 | 274 | 1585 | 14.12 | 21.54 |
| ZM3_ZM2_8_OB | 552 | 72 | 118 | 151 | 173 | 110 | 140 | 819 | 7.5 | 11.13 |
| ZM4_3 | 208 | 16 | 37 | 67 | 60 | 44 | 72 | 318 | 2.83 | 4.32 |
| ZM4_5 | 327 | 48 | 70 | 85 | 98 | 74 | 95 | 501 | 4.44 | 6.81 |
| ZM4_8 | 522 | 67 | 111 | 143 | 159 | 109 | 138 | 779 | 7.1 | 10.59 |
| ZM4L_5 | 327 | 48 | 70 | 85 | 98 | 74 | 95 | 501 | 4.44 | 6.81 |
| ZMi1 | 4126 | 1288 | 1376 | 984 | 907 | 859 | 1379 | 7307 | 56.08 | 99.32 |
| ZMi2 | 728 | 124 | 138 | 201 | 226 | 163 | 179 | 1093 | 9.9 | 14.86 |
| ZMi3 | 3833 | 1207 | 1275 | 912 | 841 | 805 | 1295 | 6815 | 52.1 | 92.63 |
| ZMi4 | 327 | 48 | 70 | 85 | 98 | 74 | 95 | 501 | 4.44 | 6.81 |
| ZMx1_exclusive | 255 | 79 | 93 | 60 | 51 | 51 | 76 | 441 | 3.47 | 5.99 |
| ZMx2_exclusive | 38 | 2 | 8 | 12 | 15 | 3 | 8 | 51 | 0.52 | 0.69 |
| ZMx3_exclusive | 3506 | 1159 | 1205 | 827 | 743 | 731 | 1200 | 6314 | 47.65 | 85.82 |
| ZMx4_exclusive | 327 | 48 | 70 | 85 | 98 | 74 | 95 | 501 | 4.44 | 6.81 |

Rows ZMi1..ZMi4 are the nested ("ZMk or better") default tiers (stack 5, zone 5); ZMx1..ZMx4_exclusive are the exclusive labels (highest tier satisfied). ZM4L_5 = the layered ZM4 (same signals as ZM4_5). Counts are for 10:00-14:00 (PRIMARY) unless the column is another window; per_wk divides by 73.6 calendar weeks.

Plain reading of the counts (no P&L seen):
- ZM1 4,126 setups in PRE 10:00-14:00 = 56 per week (about 11 per day-session of the week); ZM2 (stack within 5 pt) 728 = 9.9/wk; ZM4 at stack 5 = 327 = 4.4/wk (92 days of 363 have one), at stack 3 = 208 = 2.8/wk. ZM4 is NOT a 1-2-per-month event under these definitions.
- The reason is that the FVG condition is almost always met: a trend-direction 1-min body-gap FVG (first/second touch) within 5 pt of the level exists at 89% of ZM1 setups (3,668 / 4,126); the OB condition at 43% (1,776). So ZM3-with-FVG is nearly ZM1 relabelled and cannot be expected to separate from it; the discriminating ingredients are the stack and the OB. This is a property of the definition the plan fixed (body-gap FVG), reported, not tuned.
- Exclusive ZM2 (stack 5, no FVG/OB) has only 38 PRE setups: a count, not a verdict (n < 100).
- Level mix of ZM1 (PRE, 10:00-14:00): 1,948 EMA200 only, 1,768 VWAP only, 410 both on the same bar.
- Every cell has at least 208 setups in PRE 10:00-14:00 so none is excluded a priori; the n >= 100 rule is applied to SEQUENCED trades (G5).

### 1b. Day-typing rule (descriptive distribution only; no P&L), fixed ex ante for Z6
At 10:15 ET, from bars closed by 10:15: crosses = number of sign changes of the 5-min-EMA200 side (R1) over the 1-min bars 09:30-10:14; wick = sum(range - body) / sum(range) over the nine 5-min bars 09:30-10:10. RANGE if crosses >= 2; TREND if crosses <= 1 and wick <= 0.5162 (the median wick share of the 363 PRE days); else MIXED. PRE labels: TREND 112 days, RANGE 148, MIXED 103 (crosses: 0 on 184 days, 1 on 31, 2+ on 148). Trades entered before 10:15 carry no day label.
