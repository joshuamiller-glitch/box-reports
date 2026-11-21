# BRACKET FIRST LOOK, ASIA6 (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-21 20:12 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 1163 of 1168.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed60/120 | 177 | 62 | 105 |
| fixed30/90 | 176 | 135 | 142 |
| fixed45/45 | 164 | 171 | 154 |
| fixed40/80 | 141 | 157 | 134 |
| fixed30/30 | 108 | 79 | 87 |
| plain60/60 | 69 | 96 | 52 |
| sym8u | 63 | 79 | 52 |
| fixed120/60 | 45 | 97 | 45 |
| asym10u/20u | 43 | 29 | 38 |
| fixed90/90 | 42 | 31 | 26 |
| asym20u/10u | 31 | 52 | 34 |
| fixed80/40 | 29 | 45 | 27 |
| fixed90/30 | 23 | 50 | 18 |
| sym15u | 19 | 38 | 13 |
| sym30u | 17 | 17 | 17 |
| asym15u/30u | 9 | 23 | 16 |
| fixed120/120 | 7 | 2 | 6 |

Cells whose ladder bracket is already the best in L6M: 33 of 1163. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 966.

## NULL for the best-of-17 pick (exchangeable shape labels)

If the 17 shapes were interchangeable, calling any one of them the "own bracket" would give per cell the same two numbers. Averaged over all 17 possible own brackets of every cell: own bracket is the best in L6M in 5.9% of cells (the real ladder bracket: 2.8%); SOME other shape beats it at equal risk in BOTH windows in 85.4% of cells (the real ladder bracket: 83.1%). READING: the real ladder bracket is NOT better than a random one and the share of cells with a "better" shape is what chance gives, so the headline count is not evidence of a better bracket; only cells that also pass the engine, walk-forward and the null count.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 92598; failed at both pass-1 brackets: 30167; positive in both windows at another shape: 14794. By shape: {'fixed60/120': 1319, 'fixed90/90': 1353, 'fixed30/30': 1342, 'fixed30/90': 3847, 'asym10u/20u': 303, 'fixed45/45': 1731, 'fixed40/80': 2180, 'fixed90/30': 422, 'sym8u': 455, 'sym30u': 312, 'asym20u/10u': 244, 'fixed120/60': 581, 'fixed80/40': 352, 'asym15u/30u': 139, 'fixed120/120': 214}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 491 cells, 16 distinct: 289 cells, 15 distinct: 97 cells, 14 distinct: 98 cells, 13 distinct: 62 cells, 12 distinct: 46 cells, 11 distinct: 80 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 9403 of 31801 grid cells in these jobs.

## Top 30 ladder cells by L6M equal-risk net points/week (best shape), L3M beside, plain 60/60 number beside

| cell | row | module | ladder bracket | best shape (L6M) | L6M eq pts/wk | L3M at that shape | own bracket L6M | plain 60/60 L6M |
|---|---|---|---|---|---|---|---|---|
| Ldf65c0b2 | time_m_10 | momentum_squeeze | sym8u | fixed40/80 | 2264.56 | 1147.83 | 2.02 | 66.68 |
| L4f4f6e98 | rng_56 | tape_stoprun | sym8u | fixed90/30 | 1431.98 | 131.71 | -2.28 | 52.94 |
| La70d834e | dchg_28 | barnative_avwap | sym15u | fixed30/30 | 1130.13 | 1163.32 | -9.02 | 32.66 |
| L6b373671 | frenko_40 | levels_piv_floor | sym15u | plain60/60 | 845.66 | 221.33 | 14.87 | 120.94 |
| Lee20a819 | urenko_20 | structure_breakout | sym15u | fixed60/120 | 810.8 | 391.67 | -25.54 | 45.63 |
| L8c6f2274 | time_m_5 | momentum_rsi | sym8u | plain60/60 | 717.38 | 842.27 | -29.01 | 101.04 |
| L205413af | renko_14 | bands_envelope | sym15u | fixed30/90 | 579.29 | 442.15 | -24.33 | -13.55 |
| M205413af | renko_14 | bands_envelope | sym15u | fixed30/90 | 579.29 | 442.15 | -24.33 | -13.55 |
| L302f2cbb | time_m_60 | levels_fib60 | sym15u | plain60/60 | 572.24 | 225.71 | -21.17 | 75.25 |
| L780f8501 | tm45 | bands_keltner | plain60/60 | sym8u | 509.68 | 319.61 | 13.59 | 13.59 |
| L998ddf71 | frenko_28 | levels_vwap | sym15u | fixed45/45 | 480.76 | 126.07 | 14.94 | 55.57 |
| L432c6d26 | time_m_30 | momentum_willr | sym15u | fixed30/30 | 401.18 | 443.68 | 10.71 | 70.96 |
| M6a390df6 | frenko_40 | levels_gaps | sym15u | fixed30/30 | 374.4 | 34.46 | 9.23 | 34.98 |
| L6a390df6 | frenko_40 | levels_gaps | sym15u | fixed30/30 | 374.4 | 34.46 | 9.23 | 34.98 |
| Ld64ef7e6 | rng_112 | manual_macd | sym15u | fixed45/45 | 367.99 | 24.46 | -42.33 | 25.1 |
| L9b2b3460 | tm1800 | bands_donchian | plain60/60 | fixed30/30 | 362.82 | 127.08 | 18.13 | 18.13 |
| L7919711a | tm900 | levels_fib5 | sym15u | fixed40/80 | 361.43 | 253.54 | -1.67 | 86.72 |
| L7ad79ca6 | tm120 | bands_atrchan | asym15u/30u | fixed30/30 | 352.12 | 65.13 | -3.94 | -7.23 |
| M7ad79ca6 | tm120 | bands_atrchan | asym15u/30u | fixed30/30 | 352.12 | 65.13 | -3.94 | -7.23 |
| L17e224fb | lbrk_3_10 | levels_round | asym20u/10u | sym8u | 350.39 | 183.18 | 4.65 | 84.0 |
| M17e224fb | lbrk_3_10 | levels_round | asym20u/10u | sym8u | 350.39 | 183.18 | 4.65 | 84.0 |
| M9898dbe0 | pasl_10 | bands_bollinger | sym15u | fixed45/45 | 346.14 | 224.62 | 25.97 | 61.53 |
| L8a9300ef | urenko_28 | book_imb | sym15u | fixed40/80 | 343.16 | 262.28 | -6.51 | 16.81 |
| Ma63029fb | urenko_28 | book_imb | sym15u | fixed40/80 | 343.16 | 262.28 | -6.51 | 16.81 |
| L0c4932ef | kagi_20 | trend_psar | sym15u | fixed60/120 | 341.49 | 152.68 | -12.41 | 7.63 |
| M0c4932ef | kagi_20 | trend_psar | sym15u | fixed60/120 | 341.49 | 152.68 | -12.41 | 7.63 |
| Laf511871 | rng_20 | levels_prior_day | asym20u/10u | fixed30/30 | 339.63 | 23.12 | -4.8 | -37.05 |
| L4d220cb8 | renko_20 | levels_vwap | sym8u | fixed80/40 | 331.51 | 842.97 | -15.91 | -26.19 |
| L58a809e7 | time_m_5 | bands_keltner | sym15u | fixed45/45 | 326.71 | 177.91 | 23.56 | 64.85 |
| L30c672a0 | swing_pct_5 | levels_vwap | sym15u | fixed45/45 | 315.1 | 57.05 | 8.73 | 33.52 |

## Not yet read (grid files not landed): 0 ladder cells

They are NOT dropped: the finisher re-reads them when their files land and appends their step-2 rows in a second file. Cells: 

