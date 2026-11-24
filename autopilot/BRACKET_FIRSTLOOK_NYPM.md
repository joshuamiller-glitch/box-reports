# BRACKET FIRST LOOK, NYPM (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-24 11:19 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 394 of 396.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed120/60 | 43 | 46 | 39 |
| sym8u | 39 | 33 | 26 |
| fixed90/90 | 39 | 25 | 32 |
| fixed60/120 | 37 | 29 | 28 |
| plain60/60 | 35 | 47 | 21 |
| fixed40/80 | 31 | 14 | 19 |
| fixed30/90 | 31 | 33 | 22 |
| fixed90/30 | 28 | 33 | 21 |
| fixed45/45 | 26 | 19 | 23 |
| fixed30/30 | 26 | 33 | 26 |
| fixed80/40 | 21 | 30 | 21 |
| asym10u/20u | 12 | 16 | 10 |
| sym15u | 10 | 15 | 3 |
| asym20u/10u | 8 | 13 | 9 |
| sym30u | 5 | 4 | 5 |
| fixed120/120 | 3 | 1 | 3 |
| asym15u/30u | 0 | 3 | 1 |

Cells whose ladder bracket is already the best in L6M: 14 of 394. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 309.

## NULL for the best-of-17 pick (exchangeable shape labels)

If the 17 shapes were interchangeable, calling any one of them the "own bracket" would give per cell the same two numbers. Averaged over all 17 possible own brackets of every cell: own bracket is the best in L6M in 6.4% of cells (the real ladder bracket: 3.6%); SOME other shape beats it at equal risk in BOTH windows in 82.9% of cells (the real ladder bracket: 78.4%). READING: the real ladder bracket is NOT better than a random one and the share of cells with a "better" shape is what chance gives, so the headline count is not evidence of a better bracket; only cells that also pass the engine, walk-forward and the null count.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 46602; failed at both pass-1 brackets: 16932; positive in both windows at another shape: 7456. By shape: {'fixed60/120': 452, 'fixed30/90': 869, 'fixed120/60': 785, 'fixed80/40': 696, 'fixed30/30': 752, 'fixed90/30': 1049, 'fixed45/45': 543, 'fixed40/80': 810, 'fixed90/90': 679, 'sym8u': 235, 'asym20u/10u': 246, 'sym30u': 143, 'asym10u/20u': 96, 'asym15u/30u': 27, 'fixed120/120': 74}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 133 cells, 16 distinct: 101 cells, 15 distinct: 18 cells, 14 distinct: 64 cells, 13 distinct: 6 cells, 12 distinct: 31 cells, 11 distinct: 39 cells, 2 distinct: 2 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 5883 of 15904 grid cells in these jobs.

## Top 30 ladder cells by L6M equal-risk net points/week (best shape), L3M beside, plain 60/60 number beside

| cell | row | module | ladder bracket | best shape (L6M) | L6M eq pts/wk | L3M at that shape | own bracket L6M | plain 60/60 L6M |
|---|---|---|---|---|---|---|---|---|
| L4121a16f | tm30 | trend_macd | asym10u/20u | fixed60/120 | 1059.15 | 1584.17 | 0.59 | 80.62 |
| Lbc2a9b27 | tm30 | trend_macd | asym10u/20u | fixed60/120 | 1059.15 | 1584.17 | 0.59 | 80.62 |
| L090c6275 | vol_500 | tape_vpin | sym15u | fixed60/120 | 585.92 | 731.84 | 10.68 | 41.71 |
| Lc6ea6ddc | drb_1200 | tape_exhaust | sym15u | fixed30/30 | 561.07 | 90.97 | 17.45 | 23.9 |
| L7011bfdd | drb_2000 | manual_macd | sym15u | fixed30/90 | 553.43 | 265.17 | 19.76 | 32.1 |
| L99705afd | tib_240 | tape_vpin | plain60/60 | fixed60/120 | 490.54 | 240.42 | 26.51 | 26.51 |
| L6d238076 | vsess_50 | manual_macd | sym15u | fixed90/30 | 466.55 | 264.65 | 0.9 | 47.85 |
| L12a7a808 | tm45 | bands_regchan | asym10u/20u | fixed90/90 | 460.66 | 76.01 | 5.16 | 33.73 |
| L92dc4be3 | wrenko_10 | tape_delta | sym15u | fixed60/120 | 445.1 | 153.93 | -44.34 | 14.09 |
| L9c2ef06f | dchg_40 | levels_zones | sym15u | fixed90/30 | 443.9 | 217.0 | -8.88 | 23.29 |
| Lb83f5c59 | kagi_40 | levels_zones | sym15u | fixed90/30 | 443.31 | 216.7 | -8.96 | 23.21 |
| L8310df10 | pnf_5 | levels_fvg5 | sym15u | fixed90/90 | 418.38 | 243.07 | 19.41 | 48.9 |
| Lc8319f0b | drb_1200 | book_cancel | plain60/60 | fixed90/90 | 412.94 | 415.42 | 11.44 | 11.44 |
| La1ad0f6a | mom_28 | xmarket_ym | sym15u | fixed45/45 | 405.32 | 178.64 | 12.18 | 22.37 |
| Lef27b653 | time_m_10 | bands_avwap0930 | plain60/60 | fixed90/30 | 390.01 | 256.93 | -9.83 | -9.83 |
| Lca7966bd | time_m_10 | bands_avwap0930 | plain60/60 | fixed90/30 | 390.01 | 256.93 | -9.83 | -9.83 |
| L4b0bad8c | vol_350 | trend_ma_kama | sym15u | fixed120/60 | 380.35 | 92.92 | -22.89 | 44.95 |
| L2a92b331 | renko_20 | tape_speed | plain60/60 | fixed90/90 | 352.41 | 186.96 | 22.12 | 22.12 |
| Lc536dec7 | drb_1200 | levels_profile_va | asym20u/10u | fixed30/90 | 326.64 | 42.06 | -11.23 | -6.0 |
| Lc51b2697 | bmsg_B050 | levels_round | sym15u | fixed40/80 | 306.05 | 251.11 | -2.76 | 15.84 |
| L11b5e8ad | dol_500 | levels_vwap | plain60/60 | fixed45/45 | 303.18 | 49.53 | 5.88 | 5.88 |
| L2c32e2a8 | bmsg_B320 | tape_block | sym15u | fixed120/60 | 285.68 | 219.01 | 20.25 | 80.0 |
| Lca96fd06 | dltor_B320 | levels_fvg5 | plain60/60 | asym20u/10u | 273.8 | 65.5 | 6.61 | 6.61 |
| L18eca11f | renko_80 | book_ice | sym15u | fixed40/80 | 271.74 | 50.79 | 30.94 | 28.57 |
| L64cf7475 | tm45 | manual_macd | sym30u | fixed40/80 | 270.65 | 1629.53 | 25.35 | 68.54 |
| L8e0bf58c | anch_PDN_B25 | xmarket_rates | plain60/60 | sym8u | 260.17 | 105.03 | 18.56 | 18.56 |
| L20756075 | vol_350 | trend_psar | sym30u | plain60/60 | 254.28 | 150.56 | 17.55 | 70.22 |
| L95416473 | time_s_30 | levels_profile_va | sym15u | fixed60/120 | 248.51 | 3.32 | 10.92 | 44.34 |
| L19a1a442 | rng_14 | tape_div | sym30u | fixed45/45 | 232.78 | 257.67 | 37.22 | 32.36 |
| L3f71a0d2 | rng_10 | levels_round | sym30u | asym20u/10u | 231.69 | 64.69 | -18.75 | -31.6 |

## Not yet read (grid files not landed): 0 ladder cells

They are NOT dropped: the finisher re-reads them when their files land and appends their step-2 rows in a second file. Cells: 

