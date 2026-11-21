# BRACKET FIRST LOOK, NYAM (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-21 20:21 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 5903 of 5946.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed120/60 | 1012 | 1167 | 884 |
| sym8u | 711 | 776 | 329 |
| fixed90/30 | 550 | 482 | 405 |
| fixed80/40 | 464 | 413 | 339 |
| fixed60/120 | 463 | 417 | 331 |
| fixed90/90 | 403 | 472 | 347 |
| fixed30/90 | 307 | 228 | 198 |
| plain60/60 | 304 | 262 | 147 |
| asym20u/10u | 273 | 321 | 274 |
| fixed40/80 | 264 | 173 | 160 |
| fixed45/45 | 247 | 161 | 160 |
| sym15u | 246 | 328 | 95 |
| asym10u/20u | 214 | 283 | 244 |
| fixed30/30 | 208 | 145 | 150 |
| sym30u | 104 | 125 | 107 |
| asym15u/30u | 100 | 120 | 118 |
| fixed120/120 | 33 | 30 | 38 |

Cells whose ladder bracket is already the best in L6M: 421 of 5903. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 4326.

## NULL for the best-of-17 pick (exchangeable shape labels)

If the 17 shapes were interchangeable, calling any one of them the "own bracket" would give per cell the same two numbers. Averaged over all 17 possible own brackets of every cell: own bracket is the best in L6M in 6.1% of cells (the real ladder bracket: 7.1%); SOME other shape beats it at equal risk in BOTH windows in 81.3% of cells (the real ladder bracket: 73.3%). READING: the real ladder bracket is NOT better than a random one and the share of cells with a "better" shape is what chance gives, so the headline count is not evidence of a better bracket; only cells that also pass the engine, walk-forward and the null count.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 420016; failed at both pass-1 brackets: 200859; positive in both windows at another shape: 79671. By shape: {'fixed30/30': 5915, 'fixed90/90': 6637, 'fixed30/90': 6626, 'fixed60/120': 5947, 'fixed40/80': 5313, 'fixed90/30': 14475, 'fixed80/40': 8887, 'fixed45/45': 4938, 'fixed120/60': 13789, 'sym8u': 2553, 'asym10u/20u': 1034, 'asym20u/10u': 1870, 'sym30u': 817, 'asym15u/30u': 320, 'fixed120/120': 550}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 1986 cells, 16 distinct: 1935 cells, 15 distinct: 212 cells, 14 distinct: 600 cells, 13 distinct: 111 cells, 12 distinct: 381 cells, 11 distinct: 667 cells, 2 distinct: 11 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 55001 of 144832 grid cells in these jobs.

## Top 30 ladder cells by L6M equal-risk net points/week (best shape), L3M beside, plain 60/60 number beside

| cell | row | module | ladder bracket | best shape (L6M) | L6M eq pts/wk | L3M at that shape | own bracket L6M | plain 60/60 L6M |
|---|---|---|---|---|---|---|---|---|
| Bf66cc006 | dlt_70 | tape_stack | sym15u | fixed80/40 | 1178.76 | 2010.98 | -19.61 | 80.74 |
| Bf204caa8 | dib_240 | structure_level | plain60/60 | fixed120/120 | 1146.88 | 374.39 | 45.53 | 45.53 |
| Le910fc68 | tm1200 | bands_avwap0930 | sym15u | fixed90/30 | 1065.87 | 201.54 | -1.94 | 28.13 |
| B626712f0 | tm780 | levels_session_hl | sym15u | fixed90/30 | 990.73 | 308.92 | -58.94 | -37.82 |
| L24545c52 | tm30 | momentum_stoch | asym15u/30u | fixed120/60 | 954.16 | 405.46 | 36.23 | -163.41 |
| L0848d6b3 | tm30 | momentum_stoch | asym15u/30u | fixed120/60 | 954.16 | 405.46 | 36.23 | -163.41 |
| B89f1e462 | rng_14 | tape_delta | asym10u/20u | fixed120/60 | 953.91 | 675.25 | -57.53 | -33.76 |
| B589f1a47 | mrenko_14 | confluence_xfam | sym15u | fixed120/60 | 922.43 | 129.04 | -55.79 | 39.86 |
| Bbaf67379 | vsess_80 | bands_atrchan | asym10u/20u | fixed90/30 | 917.54 | 725.66 | -16.53 | 208.99 |
| L3183d440 | vsess_80 | book_cancel | sym15u | sym8u | 888.52 | 512.15 | 37.72 | -5.47 |
| Bace079e3 | pnf_14 | levels_fibr_on | plain60/60 | sym8u | 881.24 | 1253.16 | -34.3 | -34.3 |
| Ba93746f2 | cdr_250 | xmarket_fx | sym15u | fixed90/30 | 877.24 | 3799.51 | 27.02 | 88.94 |
| L00850065 | renko_10 | levels_opens | asym15u/30u | plain60/60 | 860.57 | 146.6 | -16.97 | 110.6 |
| L572fbd88 | pnf_7 | book_cancel | plain60/60 | fixed45/45 | 844.17 | 96.39 | -0.83 | -0.83 |
| L86479d0c | renko_40 | levels_prior_day | plain60/60 | fixed120/60 | 830.69 | 144.4 | 1.77 | 1.77 |
| Bf4aef582 | mom_20 | tape_delta | sym15u | plain60/60 | 769.36 | 727.34 | 3.15 | 128.31 |
| Lf81d9af6 | dib_6000 | bands_regchan | sym15u | plain60/60 | 758.54 | 658.6 | 22.78 | 145.39 |
| Lf66cc006 | dlt_70 | tape_stack | sym15u | fixed80/40 | 750.54 | 1517.2 | 7.31 | 53.23 |
| L72736052 | dol_500 | momentum_roc | asym15u/30u | fixed90/30 | 748.34 | 64.44 | 53.79 | -3.91 |
| Lf4ff805f | renko_10 | levels_opens | asym15u/30u | asym20u/10u | 738.27 | 134.83 | 21.87 | 128.98 |
| Bf3c9a017 | drb_400 | tape_vpin | sym15u | fixed45/45 | 727.0 | 459.15 | 42.37 | 48.1 |
| L57743b41 | rng_20 | levels_stack | plain60/60 | sym15u | 721.2 | 1842.76 | -15.95 | -15.95 |
| Lbaf67379 | vsess_80 | bands_atrchan | asym10u/20u | fixed90/30 | 720.98 | 771.53 | 25.42 | 103.51 |
| B7cd05a65 | vsess_600 | levels_round | sym30u | fixed90/30 | 701.25 | 436.49 | 11.89 | 53.4 |
| L56729447 | drb_3500 | structure_level | sym15u | fixed90/30 | 696.25 | 145.47 | 34.57 | 69.57 |
| B743baaf3 | cusum_28 | book_wall | sym15u | fixed45/45 | 683.28 | 504.51 | -54.16 | 18.86 |
| L39b1ea06 | pnf_10 | book_ofi | sym8u | fixed120/60 | 660.95 | 170.71 | 50.22 | 36.21 |
| Be4ff030d | vol_750 | bands_bollinger | asym10u/20u | fixed120/60 | 652.85 | 186.83 | 15.35 | -161.57 |
| L7346d4d2 | wrenko_14 | tape_run | sym15u | fixed120/60 | 652.29 | 96.76 | 28.31 | 34.97 |
| L1a2c2c00 | vol_750 | structure_breakout | sym15u | fixed30/30 | 644.16 | 157.09 | -18.12 | 34.51 |

## Not yet read (grid files not landed): 0 ladder cells

They are NOT dropped: the finisher re-reads them when their files land and appends their step-2 rows in a second file. Cells: 

