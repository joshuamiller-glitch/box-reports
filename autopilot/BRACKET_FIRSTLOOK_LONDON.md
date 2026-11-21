# BRACKET FIRST LOOK, LONDON (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-21 20:24 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 803 of 808.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed120/60 | 121 | 56 | 95 |
| fixed60/120 | 89 | 81 | 77 |
| fixed90/90 | 70 | 48 | 54 |
| sym8u | 65 | 75 | 54 |
| fixed30/90 | 63 | 67 | 41 |
| fixed40/80 | 56 | 57 | 56 |
| fixed80/40 | 55 | 72 | 43 |
| fixed90/30 | 53 | 33 | 39 |
| fixed45/45 | 51 | 73 | 48 |
| asym10u/20u | 33 | 34 | 31 |
| plain60/60 | 32 | 76 | 20 |
| fixed30/30 | 30 | 44 | 27 |
| asym20u/10u | 26 | 28 | 20 |
| asym15u/30u | 23 | 14 | 20 |
| sym15u | 22 | 38 | 17 |
| fixed120/120 | 7 | 1 | 6 |
| sym30u | 7 | 6 | 8 |

Cells whose ladder bracket is already the best in L6M: 27 of 803. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 656.

## NULL for the best-of-17 pick (exchangeable shape labels)

If the 17 shapes were interchangeable, calling any one of them the "own bracket" would give per cell the same two numbers. Averaged over all 17 possible own brackets of every cell: own bracket is the best in L6M in 6.0% of cells (the real ladder bracket: 3.4%); SOME other shape beats it at equal risk in BOTH windows in 83.9% of cells (the real ladder bracket: 81.7%). READING: the real ladder bracket is NOT better than a random one and the share of cells with a "better" shape is what chance gives, so the headline count is not evidence of a better bracket; only cells that also pass the engine, walk-forward and the null count.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 94797; failed at both pass-1 brackets: 42754; positive in both windows at another shape: 21396. By shape: {'fixed80/40': 2105, 'fixed90/90': 1835, 'fixed30/90': 3049, 'fixed40/80': 2049, 'fixed30/30': 1801, 'fixed120/60': 1651, 'fixed90/30': 2163, 'fixed60/120': 1846, 'fixed45/45': 1724, 'sym8u': 902, 'asym15u/30u': 269, 'sym30u': 356, 'asym20u/10u': 555, 'asym10u/20u': 619, 'fixed120/120': 472}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 403 cells, 16 distinct: 239 cells, 15 distinct: 29 cells, 14 distinct: 59 cells, 13 distinct: 11 cells, 12 distinct: 21 cells, 11 distinct: 40 cells, 2 distinct: 1 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 6460 of 32370 grid cells in these jobs.

## Top 30 ladder cells by L6M equal-risk net points/week (best shape), L3M beside, plain 60/60 number beside

| cell | row | module | ladder bracket | best shape (L6M) | L6M eq pts/wk | L3M at that shape | own bracket L6M | plain 60/60 L6M |
|---|---|---|---|---|---|---|---|---|
| Ld35a3b52 | rng_28 | xmarket_commod | plain60/60 | fixed80/40 | 695.52 | 606.84 | 23.18 | 23.18 |
| Lfb2fcff0 | vsess_300 | levels_round | sym30u | fixed60/120 | 513.88 | 105.8 | 25.16 | 100.63 |
| L56530558 | rng_20 | book_pslope | asym10u/20u | fixed30/90 | 478.99 | 65.08 | 44.91 | 91.8 |
| L08c8180a | tib_10000 | manual_macd | plain60/60 | fixed120/60 | 450.57 | 143.97 | 0.61 | 0.61 |
| L3e5ef673 | rng_20 | book_pslope | sym8u | fixed30/90 | 346.77 | 449.2 | 24.42 | 86.55 |
| L50c81352 | dltor_B320 | trend_macd | sym15u | asym20u/10u | 310.47 | 66.56 | 6.1 | 44.25 |
| L19201dfc | trend_20 | xmarket_commod | plain60/60 | fixed90/30 | 294.6 | 129.76 | 54.6 | 54.6 |
| Lc78f2492 | renko_20 | xmarket_commod | plain60/60 | fixed90/30 | 294.6 | 129.76 | 54.6 | 54.6 |
| Lcf0db86a | pnf_10 | levels_trendline | sym15u | fixed60/120 | 293.95 | 124.77 | 9.61 | 76.25 |
| L847f9d69 | vsess_50 | xmarket_commod | sym15u | fixed90/30 | 286.49 | 75.33 | 28.42 | 42.72 |
| L69ce70ab | time_m_30 | levels_fib5 | plain60/60 | sym8u | 283.8 | 100.76 | -0.27 | -0.27 |
| L77c60218 | cusum_20 | levels_fib60 | sym15u | plain60/60 | 279.44 | 135.27 | 4.8 | 76.31 |
| Ldb5d7d6f | drb_1200 | xmarket_commod | plain60/60 | fixed80/40 | 275.24 | 165.11 | 42.34 | 42.34 |
| L14b2c936 | vrb_700 | barnative_run | plain60/60 | sym15u | 270.37 | 104.64 | -3.25 | -3.25 |
| L4f432b57 | tm10 | trend_ma_hma | plain60/60 | fixed120/120 | 269.32 | 72.27 | -16.39 | -16.39 |
| L44a92486 | tib_6000 | book_cancel | plain60/60 | fixed90/30 | 268.72 | 160.93 | -3.25 | -3.25 |
| Ld7f3417f | tm45 | manual_macd | plain60/60 | sym8u | 266.85 | 135.97 | -10.49 | -10.49 |
| L3616edcb | dib_240 | xmarket_nkd | plain60/60 | fixed30/90 | 260.84 | 25.65 | -2.48 | -2.48 |
| L286505e8 | vsess_600 | trend_ma_hma | plain60/60 | fixed90/90 | 250.48 | 148.34 | -15.49 | -15.49 |
| L7934557d | swing_atr_0.1 | confluence_user | plain60/60 | asym10u/20u | 245.66 | 39.34 | -15.55 | -15.55 |
| L543771d5 | rng_56 | xmarket_ym | plain60/60 | sym8u | 245.42 | 54.15 | 3.58 | 3.58 |
| L9fe27587 | swing_pct_5 | trend_macd | sym15u | fixed45/45 | 238.32 | 293.92 | -22.26 | 17.0 |
| L7c8d160d | swing_pct_5 | trend_macd | sym15u | fixed45/45 | 238.32 | 293.92 | -22.26 | 17.0 |
| L0c82a93c | pasl_14 | bands_regchan | plain60/60 | sym8u | 230.14 | 50.81 | -4.74 | -4.74 |
| L7f4c2c7f | vsess_200 | levels_stack | asym20u/10u | fixed60/120 | 228.73 | 294.08 | 80.32 | 7.69 |
| L6c89365d | bmsg_B320 | xmarket_rates | sym15u | fixed60/120 | 228.14 | 337.71 | 23.36 | 96.47 |
| Le938cb34 | wrenko_14 | book_sweep | sym15u | fixed80/40 | 220.99 | 197.19 | -3.05 | 54.46 |
| Lb6428710 | dltor_B320 | book_imb | sym15u | fixed40/80 | 216.5 | 194.4 | -10.0 | -105.31 |
| L53b0a025 | vsess_30 | tape_stoprun | sym15u | fixed120/60 | 210.92 | 114.04 | -27.12 | 16.08 |
| Lc2651d0a | vol_500 | xmarket_rates | plain60/60 | fixed90/90 | 207.8 | 32.11 | 5.31 | 5.31 |

## Not yet read (grid files not landed): 0 ladder cells

They are NOT dropped: the finisher re-reads them when their files land and appends their step-2 rows in a second file. Cells: 

