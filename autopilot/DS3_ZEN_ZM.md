# DS3_ZEN_ZM - F5, the Zen model as written (ZM1-ZM4), D3ZF5, 2026-10-28

Research only. Prereg ZEN_F5_ZM sha256 88f32d6afff6de6ba69fe4fae602d0546328ef038e6609a547b5830cd2bc8302 (hashed before any cell was scored); PREHOLD sha256 569a17345890c32d465a089ae08247ccf24d9ceccaa5bb2c863afd0380a0ddab (hashed and the look logged before HOLD / X were read). Data cut ld <= 20260206; screen on PRE 2024-02-01..2025-06-30 only.

**VERDICT (F5, ZM tiers): DEAD at the screen; win rate does NOT rise ZM1 -> ZM4 and no tier is above its break-even.** At the model's 15-pt stop with the nearest-swing target the nested tiers ZM1/ZM2/ZM3/ZM4 win 40.5% / 42.3% / 41.2% / 41.6% (PRE, n = 2,612 / 423 / 2,465 / 202 trades) against cost-adjusted break-evens of 42.0% / 45.3% / 42.5% / 49.6% (empirical 45.7 / 48.8 / 45.9 / 54.7%), mean -1.71 / -1.96 / -1.53 / -3.44 pts per trade ($ -342 / -392 / -306 / -688 per 10-lot trade), effect vs random-in-regime -0.15 / -0.35 / +0.03 / -1.75 pts (MDE80 0.93 / 2.0 / 0.95 / 2.8; every CI contains zero); HOLD (one look) ZM1 41.5% / +0.71 pts [-0.24, +1.65 inside MDE 1.40], X 43.2% / -0.05. The random comparator at the same 15-pt stop wins 45.6% against a 47.1% break-even and loses -1.58 pts per trade (-$316 per 10 lots): the 15-pt stop by itself is a losing bracket on random entries in the 5-min-EMA200 regime, and the ZM tiers neither fix it nor add to it. 0 of 146 effect-scored cells pass G1 (CI lower bound > 0), 0 pass G5 (effect >= MDE80), best-of-N p for the best cell (ZM3 stack-3 + FVG, 60/60, flat 15:55, +5.5 pts, n = 105, MDE80 14.2) is 0.08 over the n >= 100 cells and 0.43 over all 151; HOLD: 0 of 30 cells have CI lower > 0. Best NY window: none (descriptive only; 14:00-15:30 is the highest at +0.72 pts for ZM1, CI lower -0.34, inside MDE 1.55). Trades per week: ZM1 35.5, ZM2 5.8, ZM3 33.5, ZM4 2.7 (sequenced, 10:00-14:00). Labels: no LEAD / CANDIDATE / CONFIRMED cell. G10 (direct 1-s/L2 replay) was not run (needs a governor entry; MORNING).


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

## 2. Counts block and the tier answer (descriptive items first, as the plan orders them)

- M8 table: section 1. Day typing: section 1b. Both written before the prereg hash.
- Cells: 176 enumerated = 96 tier cells + 60 red-flag rows + 12 day-type / runner cells + 8 sizing cells. Scored 172 (4 rows = the FOMC-eve flag are NOT BUILT: no economic calendar on disk, counted not scored). Of the 152 trade-level cells (96 tier + 44 skip-flag + 12 day-type) 146 carry an effect vs random-in-regime (the 6 layered ZM4 cells have no draw placebo, see 2d); 121 of the 146 have PRE sequenced n >= 100, 25 have n < 100 (a COUNT, not a verdict): ZM3 stack-3 + OB at b2040/b6060 (n 72), ZM4 stack-3 at b2040/b6060 (n 69), ZM4 stack-5 at b6060, layered ZM4 at b6060 (85), exclusive ZM2 (28), ZM4 trend-day cells (33, 24), among others (list in PRE_cells_final.csv, column n).
- Screened N for best-of-N: 176 plus 5 descriptive re-slices (exclusive tier labels ZMx1-4, nested ZMi3) = 181; the null was run over the 151 cells that have draws (146 + 5), max-statistic p95 = 12.23 pts (all 151) and 6.14 pts (the 125 with n >= 100); best observed effect 5.52 pts (n = 105). Program N 291,130.
- Gate tally on the 146 effect-scored cells: G1 0, G2 1, G3 (mean > 0 at 1x and 2x) 8 (all 60/60 with ZM2/ZM3/ZM4 stack-3; n 69-112; net2 +0.15..+3.3 but CI wide), G4 (win > both break-evens) 9, G5 0. No cell has effect >= MDE80.

### 2a. Win rate by tier against break-even, per bracket

Break-even = cost-adjusted win rate of the realised mean stop / target (th) and from the realised mean win / loss (emp, includes time exits). WR-MDE = 80%-power detectable win-rate difference (binomial, design effect 1.3). eff = mean pts/trade minus the random-in-regime mean (same bracket, window, flat). Windows: PRE 2024-02..2025-06 / HOLD 2025-07..2026-02-06 (one look) / X 2023-04..2024-01.

**Bracket model: 15-pt stop + nearest-swing target (the model bracket)**

| tier | PRE n | trades/wk | WR | BE th / emp | WR-MDE (pp) | mean pts | $/trade (10 lots) | eff vs random | CI | MDE80 | rank | HOLD n / WR / eff [CI lo] | X n / WR / eff |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZM1 (nested) | 2612 | 35.5 | 0.405 | 0.420 / 0.457 | 3.1 | -1.71 | -341 | -0.15 | [-0.78, +0.50] | 0.93 | 0.26 | 964 / 0.415 / +0.71 [-0.24] | 1318 / 0.432 / -0.05 |
| ZM2 (nested, stack 5) | 423 | 5.7 | 0.423 | 0.453 / 0.488 | 7.7 | -1.96 | -391 | -0.35 | [-1.70, +1.13] | 2.00 | 0.28 | 125 / 0.424 / +0.13 [-2.08] | 329 / 0.459 / +0.29 |
| ZM3 (nested) | 2465 | 33.5 | 0.412 | 0.425 / 0.459 | 3.2 | -1.53 | -306 | +0.03 | [-0.60, +0.70] | 0.95 | 0.62 | 904 / 0.417 / +0.58 [-0.36] | 1295 / 0.432 / -0.16 |
| ZM4 (nested, stack 5) | 202 | 2.7 | 0.416 | 0.496 / 0.547 | 11.1 | -3.44 | -688 | -1.75 | [-3.71, +0.20] | 2.83 | 0.02 | 69 / 0.406 / -0.87 [-3.54] | 182 / 0.478 / -0.01 |
| ZM1 exclusive | 209 | 2.8 | 0.316 | 0.387 / 0.440 | 10.3 | -4.30 | -860 | -2.63 | [-5.03, +0.10] | 3.66 | 0.00 | 102 / 0.451 / +2.26 [-0.84] | 53 / 0.472 / +0.69 |
| ZM2 exclusive | 28 | 0.4 | 0.393 | 0.437 / 0.520 | 29.5 | -3.72 | -744 | -2.41 | [-8.17, +4.26] | 8.82 | 0.20 | 6 / 0.333 / -4.29 [-13.55] | 14 / 0.643 / +6.27 |
| ZM3 exclusive | 2324 | 31.6 | 0.414 | 0.422 / 0.456 | 3.3 | -1.37 | -273 | +0.21 | [-0.47, +0.94] | 1.00 | 0.77 | 859 / 0.418 / +0.59 [-0.35] | 1178 / 0.429 / -0.18 |
| ZM4 exclusive | 202 | 2.7 | 0.416 | 0.496 / 0.547 | 11.1 | -3.44 | -688 | -1.75 | [-3.71, +0.20] | 2.83 | 0.02 | 69 / 0.406 / -0.87 [-3.54] | 182 / 0.478 / -0.01 |

**Bracket b2040: 20-pt target / 40-pt stop**

| tier | PRE n | trades/wk | WR | BE th / emp | WR-MDE (pp) | mean pts | $/trade (10 lots) | eff vs random | CI | MDE80 | rank | HOLD n / WR / eff [CI lo] | X n / WR / eff |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZM1 (nested) | 1742 | 23.7 | 0.648 | 0.702 / 0.685 | 3.7 | -1.99 | -398 | -0.24 | [-1.46, +1.00] | 1.76 | 0.30 | 674 / 0.642 / -0.45 [-2.13] | 794 / 0.613 / -1.68 |
| ZM2 (nested, stack 5) | 261 | 3.5 | 0.628 | 0.701 / 0.671 | 9.5 | -2.15 | -430 | -0.48 | [-3.33, +2.51] | 4.13 | 0.31 | 78 / 0.577 / -3.77 [-8.36] | 192 / 0.609 / -1.70 |
| ZM3 (nested) | 1655 | 22.5 | 0.650 | 0.702 / 0.684 | 3.7 | -1.84 | -368 | -0.08 | [-1.25, +1.13] | 1.73 | 0.42 | 624 / 0.635 / -0.90 [-2.53] | 781 / 0.611 / -1.82 |
| ZM4 (nested, stack 5) | 132 | 1.8 | 0.591 | 0.698 / 0.639 | 13.7 | -2.23 | -447 | -0.38 | [-5.63, +4.49] | 7.20 | 0.36 | 48 / 0.583 / -2.80 [-9.19] | 113 / 0.593 / -1.20 |
| ZM1 exclusive | 190 | 2.6 | 0.589 | 0.705 / 0.696 | 11.4 | -5.77 | -1155 | -4.02 | [-8.14, -0.16] | 5.63 | 0.01 | 96 / 0.656 / +0.05 [-3.88] | 50 / 0.680 / +2.72 |
| ZM2 exclusive | 25 | 0.3 | 0.640 | 0.703 / 0.709 | 30.6 | -3.89 | -779 | -3.29 | [-13.75, +7.67] | 15.50 | 0.22 | 6 / 0.833 / +8.84 [-10.34] | 13 / 0.769 / +3.65 |
| ZM3 exclusive | 1601 | 21.8 | 0.653 | 0.702 / 0.685 | 3.8 | -1.67 | -333 | +0.09 | [-1.13, +1.35] | 1.75 | 0.57 | 602 / 0.630 / -1.10 [-2.85] | 737 / 0.615 / -1.59 |
| ZM4 exclusive | 132 | 1.8 | 0.591 | 0.698 / 0.639 | 13.7 | -2.23 | -447 | -0.38 | [-5.63, +4.49] | 7.20 | 0.36 | 48 / 0.583 / -2.80 [-9.19] | 113 / 0.593 / -1.20 |

**Bracket b6060: 60/60 comparator**

| tier | PRE n | trades/wk | WR | BE th / emp | WR-MDE (pp) | mean pts | $/trade (10 lots) | eff vs random | CI | MDE80 | rank | HOLD n / WR / eff [CI lo] | X n / WR / eff |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZM1 (nested) | 843 | 11.5 | 0.484 | 0.514 / 0.509 | 5.5 | -2.51 | -503 | -2.05 | [-5.22, +1.07] | 4.51 | 0.01 | - | - |
| ZM2 (nested, stack 5) | 163 | 2.2 | 0.479 | 0.514 / 0.500 | 12.5 | -1.87 | -374 | -1.84 | [-7.94, +4.26] | 8.71 | 0.20 | - | - |
| ZM3 (nested) | 815 | 11.1 | 0.485 | 0.514 / 0.510 | 5.6 | -2.54 | -507 | -2.12 | [-5.25, +1.10] | 4.52 | 0.01 | - | - |
| ZM4 (nested, stack 5) | 98 | 1.3 | 0.439 | 0.512 / 0.456 | 16.0 | -1.36 | -273 | -1.31 | [-9.96, +7.72] | 12.71 | 0.31 | - | - |
| ZM1 exclusive | 164 | 2.2 | 0.457 | 0.514 / 0.525 | 12.4 | -6.71 | -1341 | -6.56 | [-15.43, +1.76] | 12.29 | 0.02 | - | - |
| ZM2 exclusive | 23 | 0.3 | 0.522 | 0.511 / 0.591 | 33.3 | -6.02 | -1203 | -6.32 | [-23.55, +14.17] | 26.95 | 0.26 | - | - |
| ZM3 exclusive | 801 | 10.9 | 0.496 | 0.514 / 0.510 | 5.6 | -1.38 | -276 | -0.93 | [-4.13, +2.39] | 4.64 | 0.14 | - | - |
| ZM4 exclusive | 98 | 1.3 | 0.439 | 0.512 / 0.456 | 16.0 | -1.36 | -273 | -1.31 | [-9.96, +7.72] | 12.71 | 0.31 | - | - |

**Monotone-trend test** (OLS slope of win on the exclusive tier index 1-4, week-block bootstrap, PRE): model: slope +3.8 pp per tier [+0.6, +6.8], WR [0.316, 0.393, 0.414, 0.416], n [209, 28, 2324, 202]; b2040: slope +1.5 pp per tier [-1.9, +4.7], WR [0.589, 0.64, 0.653, 0.591], n [190, 25, 1601, 132]; b6060: slope +0.5 pp per tier [-2.9, +3.9], WR [0.457, 0.522, 0.496, 0.439], n [164, 23, 801, 98]


Reading: (1) nested tiers (ZM-k-or-better): win rate is flat at 40.5-42.3% for ZM1-ZM3 and 41.6% for ZM4 at the model bracket in PRE, 41.5 / 42.4 / 41.7 / 40.6% in HOLD, 43.2 / 45.9 / 43.2 / 47.8% in X (ZM4 n = 182): it does not rise with tier in two of three samples and the X rise is inside the ZM4 win-rate MDE (11 pp). (2) The exclusive-label table rises in PRE at the model bracket (31.6 / 39.3 / 41.4 / 41.6%, slope +3.8 pp per tier [+0.6, +6.8]) only because exclusive ZM1 (a hold candle with no stack, FVG or OB within 5 pt: n = 209) is a bad subset (effect vs random -2.63, rank 0.00); in HOLD that same subset wins 45.1% (effect +2.26, CI lower -0.84), and in X 47.2%: the slope is not stable, and at 20/40 and 60/60 the PRE slope is 0 (+1.5 pp [-1.9, +4.7]; +0.5 pp [-2.9, +3.9]). (3) The reason the higher tiers cannot show a lift is the definition: an FVG within 5 pt exists at 89% of ZM1 setups, so ZM3 is ZM1 relabelled (n 2,465 of 2,612); ZM2 (stack) and ZM4 are small and negative. (4) Above break-even by more than MDE: no. At the model bracket every tier is below its break-even (the nearest is ZM3 exclusive, 41.4% vs 42.2%); the six cells with win rate above break-even (G4) are the 60/60 stack-3 cells, which are inconclusive (effect +2..+5.5 pts, MDE80 11-15).

### 2b. What the 15-pt stop does to the random comparator

| bracket | flat | candidate minutes | WR | BE th / emp | mean pts | 2x cost | $/trade | median / p90 target distance | swing-target share |
|---|---|---|---|---|---|---|---|---|---|
| model | 840 | 86252 | 0.456 | 0.471 / 0.510 | -1.58 | -3.43 | -316 | 20.0 / 33.5 | 0.65 |
| model | 955 | 86252 | 0.455 | 0.471 / 0.509 | -1.57 | -3.42 | -315 | 20.0 / 33.5 | 0.65 |
| b2040 | 840 | 86252 | 0.634 | 0.700 / 0.670 | -1.82 | -4.18 | -364 | 20.0 / 20.0 |  |
| b2040 | 955 | 86252 | 0.661 | 0.699 / 0.693 | -1.82 | -4.20 | -364 | 20.0 / 20.0 |  |
| b6060 | 840 | 86252 | 0.499 | 0.513 / 0.503 | -0.34 | -2.30 | -68 | 60.0 / 60.0 |  |
| b6060 | 955 | 86252 | 0.509 | 0.513 / 0.507 | +0.14 | -1.83 | +28 | 60.0 / 60.0 |  |


Reading: the random-in-regime entry with a 15-pt stop and a swing-or-20-pt target wins 45.6% against a 47.1% theoretical (51.0% empirical) break-even and loses 1.58 pts per trade after $4.84 and the mapped correction (3.43 at 2x cost): the stop is tight relative to a 1-min noise range, so the bracket is a payoff cost, not an edge, and a 'tier' has to beat that comparator, which none does. The 20/40 bracket (target 20, stop 40) wins 63-66% against a 70% break-even (-1.82 pts). At 60/60 the random pool is flat (-0.34 flat 14:00, +0.14 flat 15:55: drift).

### 2c. Per NY window (random-in-regime effect per tier and window)

| tier | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | 14:00-15:30 | RTH pooled |
|---|---|---|---|---|---|---|---|
| ZMi1 | 1085 / 0.42 / +0.25 [1.3] | 1050 / 0.38 / -0.68 [1.4] | 648 / 0.42 / +0.47 [1.8] | 530 / 0.44 / +0.06 [1.9] | 523 / 0.41 / -0.16 [1.7] | 789 / 0.44 / +0.72 [1.5] | 4707 / 0.41 / +0.07 [0.7] |
| ZMi2 | 112 / 0.44 / -0.84 [3.8] | 104 / 0.39 / -2.00 [4.3] | 112 / 0.41 / -0.17 [4.8] | 137 / 0.47 / +1.06 [4.1] | 104 / 0.44 / +0.51 [3.8] | 109 / 0.46 / +1.56 [4.8] | 676 / 0.43 / -0.07 [1.7] |
| ZMi3 | 1014 / 0.42 / +0.33 [1.3] | 986 / 0.39 / -0.54 [1.5] | 614 / 0.43 / +0.62 [1.9] | 496 / 0.45 / +0.24 [1.9] | 492 / 0.42 / +0.17 [1.9] | 743 / 0.46 / +1.01 [1.7] | 4438 / 0.42 / +0.23 [0.7] |
| ZMi4 | 43 / 0.49 / +1.56 [8.2] | 51 / 0.41 / -2.59 [6.2] | 57 / 0.42 / -0.83 [6.9] | 59 / 0.42 / -1.89 [5.6] | 46 / 0.37 / -3.01 [4.9] | 63 / 0.44 / -0.59 [5.7] | 319 / 0.44 / -0.96 [2.7] |
| ZMx1 | 78 / 0.37 / -1.91 [5.7] | 83 / 0.33 / -2.58 [6.1] | 47 / 0.34 / -1.04 [6.6] | 41 / 0.29 / -3.03 [7.4] | 43 / 0.26 / -5.16 [6.9] | 67 / 0.31 / -2.21 [6.4] | 378 / 0.32 / -2.41 [2.8] |
| ZMx2 | n=0 | n=5 | n=7 | n=14 | n=0 | n=6 | 38 / 0.37 / -2.47 [7.2] |
| ZMx3 | 978 / 0.42 / +0.29 [1.4] | 942 / 0.39 / -0.41 [1.5] | 573 / 0.43 / +0.74 [1.8] | 458 / 0.45 / +0.31 [2.0] | 458 / 0.43 / +0.45 [2.0] | 693 / 0.46 / +1.12 [1.7] | 4204 / 0.42 / +0.33 [0.8] |
| ZMx4 | 43 / 0.49 / +1.56 [8.2] | 51 / 0.41 / -2.59 [6.2] | 57 / 0.42 / -0.83 [6.9] | 59 / 0.42 / -1.89 [5.6] | 46 / 0.37 / -3.01 [4.9] | 63 / 0.44 / -0.59 [5.7] | 319 / 0.44 / -0.96 [2.7] |

20/40 bracket (same layout):

| tier | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | 14:00-15:30 | RTH pooled |
|---|---|---|---|---|---|---|---|
| ZMi1 | 845 / 0.67 / +0.26 [2.1] | 748 / 0.66 / -0.63 [2.5] | 457 / 0.67 / +0.11 [3.5] | 359 / 0.70 / +1.56 [3.6] | 366 / 0.64 / -0.72 [3.5] | 542 / 0.67 / +1.73 [2.4] | 3192 / 0.66 / +0.23 [1.0] |
| ZMi2 | 82 / 0.67 / +0.84 [8.1] | 64 / 0.52 / -8.31 [11.6] | 76 / 0.63 / -0.99 [8.4] | 96 / 0.72 / +3.39 [6.6] | 72 / 0.71 / +2.92 [7.7] | 77 / 0.62 / +0.63 [7.2] | 417 / 0.65 / +0.36 [3.2] |
| ZMi3 | 801 / 0.68 / +0.51 [2.1] | 718 / 0.66 / -0.42 [2.4] | 431 / 0.68 / +0.86 [3.4] | 339 / 0.69 / +1.08 [3.5] | 347 / 0.64 / -0.93 [3.5] | 512 / 0.68 / +1.97 [2.6] | 3030 / 0.66 / +0.43 [1.0] |
| ZMi4 | 37 / 0.73 / +5.10 [12.4] | 33 / 0.52 / -8.67 [17.2] | 40 / 0.57 / -3.25 [12.6] | 46 / 0.67 / +2.65 [11.1] | 37 / 0.76 / +6.67 [12.5] | 43 / 0.56 / -1.73 [8.9] | 212 / 0.65 / +1.32 [5.3] |
| ZMx1 | 74 / 0.65 / -0.95 [9.0] | 75 / 0.59 / -4.87 [9.2] | 44 / 0.61 / -3.06 [12.4] | 37 / 0.62 / -4.01 [12.1] | 40 / 0.62 / -1.95 [12.5] | 62 / 0.61 / -1.52 [11.6] | 343 / 0.61 / -2.72 [4.3] |
| ZMx2 | n=0 | n=4 | n=7 | n=12 | n=0 | n=5 | 34 / 0.62 / -3.70 [13.5] |
| ZMx3 | 782 / 0.67 / +0.36 [2.2] | 696 / 0.67 / +0.11 [2.4] | 414 / 0.69 / +1.18 [3.5] | 322 / 0.70 / +1.00 [3.5] | 326 / 0.64 / -1.16 [3.6] | 488 / 0.68 / +2.31 [2.6] | 2937 / 0.66 / +0.48 [1.1] |
| ZMx4 | 37 / 0.73 / +5.10 [12.4] | 33 / 0.52 / -8.67 [17.2] | 40 / 0.57 / -3.25 [12.6] | 46 / 0.67 / +2.65 [11.1] | 37 / 0.76 / +6.67 [12.5] | 43 / 0.56 / -1.73 [8.9] | 212 / 0.65 / +1.32 [5.3] |
Cells with n < 30 are shown as a count. No window claim is made (a best-window claim would add 8 x 30 = 240 to N). Highest windows: 14:00-15:30 at the model bracket (ZM1 +0.72 [MDE 1.55], exclusive ZM3 +1.12 with CI lower -0.01) and at 20/40 (ZM1 +1.73, CI lower +0.04, MDE 2.39, n = 542; ZM3 exclusive +2.31, CI lower +0.34, MDE 2.61, n = 488, the only window rows whose CI excludes zero): these two rows are 2 of 112 window rows, are a descriptive look at a late-day drift (the random comparator itself loses -2.1 pts there at 20/40), not tested on HOLD, and would be corrected away by the 240-cell N.

### 2d. Layered ZM4 (thirds at the FVG zone top / mid / lower third), model bracket
n = 131 sequenced positions (327 signals, 248 with at least one fill, 2.7 of 3 layers fill on average), mean -1.82 pts per full position, win 46.6%, 2x cost -3.35; paired against the single-entry ZM4@5 on the same signals +4.85 pts [+2.93, +6.90]. This is a comparison with a losing cell (single ZM4@5 -3.44), not an edge: the layered position is also negative in absolute terms and has no random-in-regime draw placebo (labelled in the prereg).

## 3. Grid enumeration (copied from the prereg) and screened N

Tier cells 16 definitions x 3 brackets (model, 20/40, 60/60) x 2 flat rules = 96; red flags 15 x 2 base cells x 2 brackets = 60 (4 unbuilt); day type 8 + trend-day runner 4 = 12; M11 8. Total 176 = N. Base cell B of Z4 (rule-chosen on PRE after Block A): ZM3 stack-3 + FVG (ZM3_ZM2_3_FVG, model, flat 14:00, n = 258, effect +0.75). Skipped and counted: 4 FOMC-eve rows (no calendar); 6 layered cells without a draw placebo; n < 100 cells 25. Holdout: 30 cells (top by PRE effect among n >= 100) + 8 M11 + 16 headline re-slices in ONE look, then X once.

## 4. Top 10 cells by PRE effect vs random-in-regime (regardless of verdict; n >= 100)

Win rate vs break-even th / emp; pts/trade net1 / net2; fwd wk = forward weeks for 80% power to detect the observed PRE effect with the PRE MDE (73.6 x (MDE80 / effect)^2). HOLD / X columns are the one look. Gates: G1 CI lower > 0 and rank >= 0.95, G2 random-direction, G3 net > 0 at 1x and 2x, G4 win > break-even, G5 n >= 100 and effect >= MDE80, G6 HOLD sign and CI, G7 X >= 0, G8 best-of-N p <= 0.05 (n >= 100 null), G9 positive in >= 2 years and no year > 60%, G10 replay (not run).

| # | cell | PRE n | WR vs BE th/emp | pts/trade (net1 / net2) | trades/wk | eff vs random [CI] | MDE80 | rank | dir-eff / rank | fwd wk 80% | HOLD n / eff [CI lo] | X n / eff | best-of-N p | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | T/ZM3_ZM2_3_FVG/b6060/f955 | 105 | 0.571 vs 0.512/0.511 | +6.07 / +4.04 | 1.4 | +5.52 [-3.99, +15.67] | 14.2 | 0.95 | +8.63 / 0.95 | 486 | 32 / +11.12 [-0.66] | 76 / +5.67 | 0.08 | G1, G5, G6, G8, G10 not run |
| 2 | T/ZM2_3/b6060/f955 | 112 | 0.562 vs 0.512/0.511 | +5.14 / +3.09 | 1.5 | +4.59 [-4.54, +14.09] | 13.5 | 0.93 | +7.76 / 0.92 | 636 | 34 / +6.78 [-5.71] | 81 / +7.57 | 0.15 | G1, G2, G5, G6, G8, G10 not run |
| 3 | Z4/B=ZM3_ZM2_3_FVG/b2040/oppOB10/f840 | 103 | 0.680 vs 0.699/0.673 | +0.36 / -2.02 | 1.4 | +2.42 [-2.17, +7.06] | 6.7 | 0.83 | +3.13 / 0.92 | 558 | 23 / +1.58 [-6.64] | 66 / +3.34 | 0.55 | G1, G2, G3, G4, G5, G6, G8, G9, G10 not run |
| 4 | T/ZM3_ZM2_3_FVG/b6060/f840 | 105 | 0.524 vs 0.513/0.496 | +2.31 / +0.41 | 1.4 | +2.21 [-5.80, +10.22] | 11.5 | 0.81 | +4.60 / 0.85 | 1990 | 32 / +10.15 [-0.97] | 76 / +1.92 | 0.57 | G1, G2, G5, G6, G8, G9, G10 not run |
| 5 | Z4/B=ZM3_ZM2_3_FVG/model/oppOB10/f840 | 130 | 0.469 vs 0.430/0.453 | +0.55 / -1.26 | 1.8 | +2.18 [-0.93, +5.61] | 4.8 | 0.95 | +1.08 / 0.81 | 353 | 30 / +0.62 [-3.02] | 77 / +2.92 | 0.59 | G1, G2, G3, G5, G6, G8, G9, G10 not run |
| 6 | T/ZM2_3/b6060/f840 | 112 | 0.527 vs 0.513/0.502 | +2.10 / +0.15 | 1.5 | +1.95 [-5.51, +9.56] | 11.0 | 0.77 | +4.40 / 0.83 | 2332 | 34 / +5.81 [-5.88] | 81 / +3.17 | 0.69 | G1, G2, G5, G6, G8, G9, G10 not run |
| 7 | Z4/B=ZM3_ZM2_3_FVG/model/fvg4h_40/f840 | 106 | 0.481 vs 0.457/0.476 | +0.15 / -1.87 | 1.4 | +1.69 [-1.05, +4.62] | 4.0 | 0.91 | +0.68 / 0.67 | 417 | 28 / -1.09 [-5.77] | 70 / +3.00 | 0.72 | G1, G2, G3, G5, G6, G8, G9, G10 not run |
| 8 | Z4/B=ZM3_ZM2_3_FVG/model/range2_skip/f840 | 109 | 0.477 vs 0.445/0.483 | -0.17 / -2.05 | 1.5 | +1.55 [-1.32, +5.09] | 4.5 | 0.90 | +1.89 / 0.88 | 625 | 24 / -3.81 [-8.09] | 64 / +1.54 | 0.78 | G1, G2, G3, G4, G5, G6, G8, G9, G10 not run |
| 9 | Z4/B=ZM3_ZM2_3_FVG/b2040/rel15/f840 | 139 | 0.669 vs 0.700/0.673 | -0.19 / -2.63 | 1.9 | +1.44 [-2.96, +5.89] | 6.4 | 0.89 | +1.73 / 0.85 | 1439 | 37 / -4.01 [-11.81] | 93 / +0.60 | 0.78 | G1, G2, G3, G4, G5, G6, G8, G9, G10 not run |
| 10 | T/ZM4_8/b2040/f955 | 218 | 0.679 vs 0.698/0.684 | -0.30 / -2.64 | 3.0 | +1.39 [-2.65, +4.96] | 5.5 | 0.87 | +1.01 / 0.76 | 1140 | 70 / -1.93 [-7.48] | 165 / +1.35 | 0.79 | G1, G2, G3, G4, G5, G6, G8, G9, G10 not run |

Notes. All ten are inconclusive: effects of +1.4..+5.5 pts sit inside MDE80 of 4-14 pts and every CI lower bound is negative. Five of the ten are 60/60 or 20/40 cells with n 103-218 selected from the best of 121 eligible cells (max statistic null p95 6.14, best 5.52). The ZM3 stack-3 + FVG 60/60 cell has the largest HOLD effect (+11.12 pts, n = 32, CI lower -0.66, MDE 16.6: inside MDE), positive X (+5.67), positive 2 of 3 years with max year share 55%: it passes G2, G3, G4, G7, G9 and fails G1, G5, G6, G8 and G10; at flat 15:55 the pool drift also lifts the comparator (+0.14), the cell's n = 32 HOLD trades are 4 months of data. It is a LEAD-class curiosity at most and needs forward weeks (486 for 80% power at its PRE effect), not a candidate.

| # | cell | PRE 2024 n / mean | PRE 2025H1 n / mean | long n / mean / win | short n / mean / win | stop med / p90 | target med / p90 | mean R:R | median hold (bars) | WF yr means 2024 / 2025 / 2026 |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | T/ZM3_ZM2_3_FVG/b6060/f955 | 72 / +7.71 | 33 / +2.51 | 60 / +7.18 / 0.58 | 45 / +4.60 / 0.56 | 60.0 / 60.0 | 60.0 / 60.0 | 1.00 | 51 | +7.71 / +8.10 / -60.24 |
| 2 | T/ZM2_3/b6060/f955 | 75 / +6.15 | 37 / +3.10 | 64 / +4.97 / 0.56 | 48 / +5.37 / 0.56 | 60.0 / 60.0 | 60.0 / 60.0 | 1.00 | 52 | +6.15 / +7.07 / -60.24 |
| 3 | Z4/B=ZM3_ZM2_3_FVG/b2040/oppOB10/f840 | 70 / +1.53 | 33 / -2.11 | 57 / +2.58 / 0.74 | 46 / -2.39 / 0.61 | 40.0 / 40.0 | 20.0 / 20.0 | 0.50 | 10 | +1.53 / -1.43 / -5.99 |
| 4 | T/ZM3_ZM2_3_FVG/b6060/f840 | 72 / +2.15 | 33 / +2.67 | 60 / +4.47 / 0.57 | 45 / -0.56 / 0.47 | 60.0 / 60.0 | 60.0 / 60.0 | 1.00 | 43 | +2.15 / +6.99 / -5.99 |
| 5 | Z4/B=ZM3_ZM2_3_FVG/model/oppOB10/f840 | 88 / +0.62 | 42 / +0.41 | 71 / +2.89 / 0.54 | 59 / -2.25 / 0.39 | 15.0 / 15.0 | 20.0 / 37.2 | 1.52 | 4 | +0.62 / -0.25 / -9.49 |
| 6 | T/ZM2_3/b6060/f840 | 75 / +1.14 | 37 / +4.04 | 64 / +3.30 / 0.56 | 48 / +0.49 / 0.48 | 60.0 / 60.0 | 60.0 / 60.0 | 1.00 | 44 | +1.13 / +6.49 / -33.12 |
| 7 | Z4/B=ZM3_ZM2_3_FVG/model/fvg4h_40/f840 | 65 / -0.65 | 41 / +1.43 | 78 / +0.47 / 0.50 | 28 / -0.74 / 0.43 | 15.0 / 15.0 | 20.0 / 36.6 | 1.41 | 4 | -0.65 / -0.30 / -15.24 |
| 8 | Z4/B=ZM3_ZM2_3_FVG/model/range2_skip/f840 | 71 / +0.53 | 38 / -1.47 | 63 / +0.39 / 0.49 | 46 / -0.93 / 0.46 | 15.0 / 15.0 | 20.0 / 39.7 | 1.45 | 5 | +0.53 / -2.82 / -11.33 |
| 9 | Z4/B=ZM3_ZM2_3_FVG/b2040/rel15/f840 | 91 / +0.09 | 48 / -0.72 | 84 / -1.59 / 0.66 | 55 / +1.94 / 0.69 | 40.0 / 40.0 | 20.0 / 20.0 | 0.50 | 13 | +0.09 / -2.93 / -5.99 |
| 10 | T/ZM4_8/b2040/f955 | 161 / -1.41 | 57 / +2.82 | 125 / -0.69 / 0.68 | 93 / +0.23 / 0.68 | 40.0 / 40.0 | 20.0 / 20.0 | 0.50 | 15 | -1.41 / -1.07 / +15.43 |

By-year, half-year, long/short and realised stop / target distributions for all 30 holdout-eligible cells: l2vast/ds3/out/zen/zm/PRE_top30_tables.json (year, half-year, by-side, hour, stop and target median / p90, R:R); trades per cell in PRE_trades_all.pkl. For the model bracket the stop is fixed at 15 pt and the target is the latest confirmed 1-min swing (4-60 pt beyond entry) in 64% of candidates and the 20-pt fallback otherwise: ZM1 realised target median 20.0, p90 41.8 pt; exits 1,511 stops / 1,018 targets / 83 flat in 2,612 PRE trades (58% stopped).

## 5. Red flags (Z4), day typing (Z6), tier sizing (M11)

**Z4 (56 scored rows on bases A = ZM1 and B = ZM3 stack-3 + FVG, brackets model and 20/40, flat 14:00; paired delta = kept trades minus the unfiltered base on identical entries).** No skip flag has a paired CI lower bound above zero (0 of 44). Three have an upper bound below zero (skipping range days by 'crossed the 5-min EMA200 >= 3 times' on ZM1 at 20/40: -1.02 pts [-1.91, -0.26], i.e. the model's own range-day skip removes better-than-average trades; opex afternoon removes 19-26 trades and costs -0.10 [-0.19, -0.03]). The largest positive paired deltas are on the small base B (opposing OB within 10 pt: +1.68 [-0.63, +4.36], n 130 kept of 258) and are inside MDE. 'Opposing 1-min FVG within 20 pt' is a degenerate flag (removes 93.4% of ZM1 trades). Half-size flags (range-day >= 2 / >= 3, after a 300+ pt day): lot-matched delta -0.12 [-0.29, +0.06] (range >= 2, model), -0.16 / -0.35 for >= 3, +0.02 / +0.11 for the post-300 day; none positive with CI above zero; these 12 cells were PRE-only (not ranked by effect vs random, not in the look). FOMC-eve and the 'session before FOMC' are not built (no calendar).

**Z6 day typing (rule fixed ex ante at 10:15; TREND days only; 8 tier x bracket cells + 4 runner cells).** PRE labels: TREND 112 / RANGE 148 / MIXED 103 days. On TREND days the model bracket is worse than random: ZM1 n = 674, -2.39 pts, effect -0.74 [CI lower -1.97], rank 0.08; ZM3 -0.72; ZM4 (n = 33) -5.83; at 20/40 ZM1 -1.40, ZM3 -1.52 (rank 0.04-0.05). The Z2c runner (50% off at the target, stop to entry, remainder on the last closed 5-min low) beats the plain bracket on identical TREND-day entries by +0.58 pts [+0.02, +1.19] (ZM1) and +0.62 [+0.06, +1.23] (ZM3), but the runner cell is still negative (-1.66 pts) and below the random runner (effect -0.47, CI lower -1.83). 'Does the day label help': TREND days are not where the tiers work in PRE; the RANGE-day skip hurts (Z4 above). No Z6 cell reached the top 30, so none was looked at on HOLD.

**M11 sizing by tier (8 cells; lot-matched delta vs flat sizing at the same mean lots, ZM1 population, flat 14:00).** PRE: lots 1/2/3/4 by exclusive tier +0.105 pts/trade [-0.34, +0.53] (model), +0.165 [-0.54, +0.87] (20/40); lots 1/1/2/2 +0.129 [-0.07, +0.32], +0.139 [-0.18, +0.45]. HOLD (one look): -0.414 [-1.10, +0.24], -0.592, -0.137, -0.324; X: -0.340, -0.477, -0.177, -0.082. Range-day half: PRE -0.116 / -0.254, HOLD -0.04 / -0.09, X +0.09 / +0.22; post-300-day half: PRE +0.02 / +0.11, HOLD +0.11 / +0.35, X -0.05 / +0.01 (all CI contain zero). Because tiers do not differ in mean pts, sizing by tier moves nothing; it is not live-eligible (the underlying book fails).

## 6. Holdout stage (ONE logged look: HOLD 2025-07-01..2026-02-06, then X 2023-04-01..2024-01-31)

30 top cells + 8 M11 + 16 headline re-slices (PREHOLD sha above). G6 (HOLD sign and CI lower > 0): 0 of 30 (HOLD effect > 0 in 7, best +11.1 pts, CI lower -0.66, all inside MDE80 of 3.3-17); G7 (X effect >= 0): 22 of 30; G8: 0 of 30 (best-of-N p 0.08 at best); G9: 2 of 30 (both 60/60 stack-3 cells at flat 15:55: 2 of 3 years positive, max year share 55-59%); G10 not run. Full table: l2vast/ds3/out/zen/zm/HOLD_X_cells.csv, HOLD_X_M11.csv. Since G1 and G5 fail in PRE and G6 and G8 fail afterwards, nothing is CANDIDATE.

## 7. Deviations and disclosures

1. Prereg followed; deviations: (a) the one look included 16 descriptive headline-tier re-slices (ZMi1-4, ZMx1-4 at model and 20/40) beyond the prereg holdout list (30 + 8), declared in the hashed PREHOLD text before any HOLD / X number was read, so that 'does win rate rise with tier' has a holdout answer; (b) the five descriptive re-slices were added to the best-of-N null (N = 181 > 176).
2. Where the addenda are silent: touch tolerance 5 pt; 'hold candle' = wick within 5 pt of the line and body close on the trend side with the previous close also on the trend side; first hold candle of an episode only; 'nearest 1-min swing target' = latest confirmed 1-min fractal swing (strength 2) 4-60 pt beyond the entry, fallback fixed 20 pt (36% of candidates); the model's 'stop 10-15 below the level' is implemented as a 15-pt stop from the entry price (the level-relative and invalidation stops are F3's); ZM3/ZM4 'at the level' = zone within 5 pt of the level price; stack tiers measured at the E/V midpoint; 4-hour FVG on 240-min bars anchored 18:00 ET; opex = third Friday afternoon; release proxy = fixed 08:30 / 10:00 / 14:00 clock; Z6 thresholds: crosses >= 2 or wick share (0.5162 = PRE median, descriptive only).
3. FVG base rate: 89% of ZM1 setups have a trend-direction body-gap FVG within 5 pt (1-min FVGs are ubiquitous), so ZM3-with-FVG is nearly ZM1 and ZM2/ZM4 carry the only real selection; this is a property of the plan's fixed definition and is reported, not tuned. A stricter FVG definition (larger minimum gap, 5-min FVG) would be a new family.
4. Screen basis is the mapped conservative 1-min path; with a 15-pt stop it is 0.08-0.13 pt/trade more conservative than the 1-s path (plan section 3), far below the MDEs. Win = net1 > 0 (a time exit with a small profit is a win). G4 uses max(theoretical, empirical) break-even.
5. G10 (direct 1-s/L2 replay) was NOT run: it needs a PRIO_ALLOW entry in replay_governor.py and a governor restart by main; nothing here would qualify (G1, G5, G6, G8 fail), so no request is urgent.
6. The layered ZM4 and the Z4 half-size / M11 cells have no draw placebo (not applicable); Z4 skip rows are post-hoc removals from the sequenced base set (no re-sequencing), the random pool was filtered by the same flag at its own minute.
7. Selection effects: base B of Z4 and the 30 holdout cells were chosen on PRE by the stated rules; the top-10 table is therefore optimistically biased and all of its cells are still insignificant.
8. Holdout looks used: one HOLD look and one X look (tracks D3ZF5_ZM, D3ZF5_ZM_SPAN2, l2vast/ds3/out/zen/zm/looks.jsonl). No lib bug found. The signal / zone / flag unit test (t_leak) passes (True, True, True).
9. LIB BUG (D3ZF1 warning, zen_struct grid_eval fill_mode=1): not affected. F5 never calls grid_eval or _grid; every cell, pool and placebo uses Z.simulate() (market entries, and the layered ZM4 limit entries with fill_mode=1 through Z.simulate), so the fill-bar running-max issue does not apply.
10. Not built: FOMC-eve / pre-FOMC sizing (no calendar), Z1 level-relative and invalidation stops, other Z2 shapes (F3), Z5 and SMT (F4), the Addendum 3 book (L2).

## 8. Files

Code: l2vast/ds3/code/zen/f5/{zen_zm.py (detector, flags, day labels, t_leak), score.py (engine), run_pre.py, analyze_pre.py, run_hold.py, m8.py}. Prereg: l2vast/ds3/prereg/ZEN_F5_ZM_prereg.md (+ .sha256, ZEN_F5_ZM_cells.json). PREHOLD: autopilot/DS3_ZEN_ZM_PREHOLD.md. PRE tables: l2vast/ds3/out/zen/zm/ (M8_frequency_PRE.csv, PRE_cells_final.csv, PRE_reslices.csv, PRE_headline_tiers.csv, PRE_tier_windows.csv, PRE_random_comparator.csv, PRE_top30.csv, PRE_top30_tables.json, PRE_bestofN.csv, HOLD_X_cells.csv, HOLD_X_M11.csv, looks.jsonl).

DONE F5
