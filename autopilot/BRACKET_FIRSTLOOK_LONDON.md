# BRACKET FIRST LOOK, LONDON (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-24 21:28 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 1011 of 1017.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed120/60 | 143 | 71 | 112 |
| fixed60/120 | 114 | 92 | 98 |
| fixed90/90 | 90 | 68 | 72 |
| sym8u | 83 | 100 | 64 |
| fixed80/40 | 77 | 84 | 54 |
| fixed30/90 | 77 | 85 | 52 |
| fixed40/80 | 68 | 77 | 65 |
| fixed90/30 | 65 | 43 | 50 |
| fixed45/45 | 62 | 90 | 59 |
| plain60/60 | 56 | 110 | 27 |
| fixed30/30 | 41 | 55 | 36 |
| asym10u/20u | 35 | 35 | 33 |
| asym20u/10u | 32 | 31 | 25 |
| sym15u | 29 | 48 | 18 |
| asym15u/30u | 24 | 15 | 20 |
| sym30u | 8 | 6 | 9 |
| fixed120/120 | 7 | 1 | 6 |

Cells whose ladder bracket is already the best in L6M: 51 of 1011. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 800.

## NULL for the best-of-17 pick (exchangeable shape labels)

If the 17 shapes were interchangeable, calling any one of them the "own bracket" would give per cell the same two numbers. Averaged over all 17 possible own brackets of every cell: own bracket is the best in L6M in 6.1% of cells (the real ladder bracket: 5.0%); SOME other shape beats it at equal risk in BOTH windows in 83.4% of cells (the real ladder bracket: 79.1%). READING: the real ladder bracket is NOT better than a random one and the share of cells with a "better" shape is what chance gives, so the headline count is not evidence of a better bracket; only cells that also pass the engine, walk-forward and the null count.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 121092; failed at both pass-1 brackets: 53262; positive in both windows at another shape: 25867. By shape: {'fixed80/40': 2557, 'fixed90/90': 2245, 'fixed30/90': 3678, 'fixed40/80': 2635, 'fixed30/30': 2252, 'fixed120/60': 2062, 'fixed90/30': 2776, 'fixed60/120': 2173, 'fixed45/45': 2074, 'sym8u': 1026, 'asym20u/10u': 581, 'asym15u/30u': 277, 'sym30u': 391, 'asym10u/20u': 660, 'fixed120/120': 480}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 430 cells, 16 distinct: 310 cells, 15 distinct: 37 cells, 14 distinct: 85 cells, 13 distinct: 24 cells, 12 distinct: 28 cells, 11 distinct: 95 cells, 2 distinct: 2 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 11182 of 41286 grid cells in these jobs.

## Top 30 ladder cells by L6M equal-risk net points/week (best shape), L3M beside, plain 60/60 number beside

| cell | row | module | ladder bracket | best shape (L6M) | L6M eq pts/wk | L3M at that shape | own bracket L6M | plain 60/60 L6M |
|---|---|---|---|---|---|---|---|---|
| Ld35a3b52 | rng_28 | xmarket_commod | plain60/60 | fixed80/40 | 695.52 | 606.84 | 23.18 | 23.18 |
| L1e574f0f | cusum_80 | tape_speed | sym8u | fixed80/40 | 592.72 | 30.93 | 23.23 | -6.93 |
| Lbf1fdce0 | lbrk_4_10 | xmarket_fx | sym15u | fixed90/90 | 549.88 | 129.96 | -22.21 | 17.99 |
| Lfb2fcff0 | vsess_300 | levels_round | sym30u | fixed60/120 | 513.88 | 105.8 | 25.16 | 100.63 |
| Lee87874c | bmsgq_B500 | book_wall | sym15u | plain60/60 | 502.39 | 293.35 | 13.06 | 83.0 |
| L56530558 | rng_20 | book_pslope | asym10u/20u | fixed30/90 | 478.99 | 65.08 | 44.91 | 91.8 |
| L08c8180a | tib_10000 | manual_macd | plain60/60 | fixed120/60 | 450.57 | 143.97 | 0.61 | 0.61 |
| L3e5ef673 | rng_20 | book_pslope | sym8u | fixed30/90 | 346.77 | 449.2 | 24.42 | 86.55 |
| L9fc37083 | entropy_B050 | xmarket_rates | sym15u | fixed45/45 | 342.67 | 147.83 | 8.26 | 36.13 |
| L50c81352 | dltor_B320 | trend_macd | sym15u | asym20u/10u | 310.47 | 66.56 | 6.1 | 44.25 |
| L06bd96a8 | med_sessrng_B080 | bands_atrchan | sym15u | fixed90/90 | 307.09 | 215.2 | 37.09 | 33.2 |
| L19201dfc | trend_20 | xmarket_commod | plain60/60 | fixed90/30 | 294.6 | 129.76 | 54.6 | 54.6 |
| Lc78f2492 | renko_20 | xmarket_commod | plain60/60 | fixed90/30 | 294.6 | 129.76 | 54.6 | 54.6 |
| L2075382d | wrenko_20 | xmarket_commod | plain60/60 | fixed90/30 | 294.6 | 129.76 | 54.6 | 54.6 |
| Lcf0db86a | pnf_10 | levels_trendline | sym15u | fixed60/120 | 293.95 | 124.77 | 9.61 | 76.25 |
| Lbf4e5c85 | dltor_B200 | levels_ob5 | plain60/60 | fixed80/40 | 288.57 | 307.27 | 7.18 | 7.18 |
| L847f9d69 | vsess_50 | xmarket_commod | sym15u | fixed90/30 | 286.49 | 75.33 | 28.42 | 42.72 |
| L69ce70ab | time_m_30 | levels_fib5 | plain60/60 | sym8u | 283.8 | 100.76 | -0.27 | -0.27 |
| L77c60218 | cusum_20 | levels_fib60 | sym15u | plain60/60 | 279.44 | 135.27 | 4.8 | 76.31 |
| Ldb5d7d6f | drb_1200 | xmarket_commod | plain60/60 | fixed80/40 | 275.24 | 165.11 | 42.34 | 42.34 |
| L14b2c936 | vrb_700 | barnative_run | plain60/60 | sym15u | 270.37 | 104.64 | -3.25 | -3.25 |
| L4f432b57 | tm10 | trend_ma_hma | plain60/60 | fixed120/120 | 269.32 | 72.27 | -16.39 | -16.39 |
| L44a92486 | tib_6000 | book_cancel | plain60/60 | fixed90/30 | 268.72 | 160.93 | -3.25 | -3.25 |
| Ld7f3417f | tm45 | manual_macd | plain60/60 | sym8u | 266.85 | 135.97 | -10.49 | -10.49 |
| L6465973a | mom_80 | levels_channel | plain60/60 | fixed80/40 | 265.7 | 132.39 | -6.43 | -6.43 |
| L90fa58e0 | mrenko_20 | book_dwm | asym10u/20u | fixed30/30 | 260.85 | 77.98 | 39.58 | 51.98 |
| L3616edcb | dib_240 | xmarket_nkd | plain60/60 | fixed30/90 | 260.84 | 25.65 | -2.48 | -2.48 |
| Lc57c63c8 | vib_1200 | xmarket_rates | sym15u | fixed120/60 | 254.02 | 594.15 | 30.09 | 74.33 |
| L286505e8 | vsess_600 | trend_ma_hma | plain60/60 | fixed90/90 | 250.48 | 148.34 | -15.49 | -15.49 |
| L7934557d | swing_atr_0.1 | confluence_user | plain60/60 | asym10u/20u | 245.66 | 39.34 | -15.55 | -15.55 |

## Not yet read (grid files not landed): 0 ladder cells

They are NOT dropped: the finisher re-reads them when their files land and appends their step-2 rows in a second file. Cells: 

