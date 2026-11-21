PARTIAL TEST RENDER, NOT A RESULT (grid jobs still running; the finisher overwrites this page when the session's results are complete)

# BRACKET FIRST LOOK, NYAM (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-21 16:55 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 1544 of 5946.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed120/60 | 269 | 307 | 220 |
| sym8u | 217 | 244 | 68 |
| fixed90/30 | 155 | 133 | 112 |
| fixed60/120 | 140 | 124 | 99 |
| fixed80/40 | 124 | 132 | 85 |
| fixed90/90 | 109 | 129 | 95 |
| fixed30/90 | 85 | 65 | 58 |
| plain60/60 | 68 | 72 | 36 |
| fixed30/30 | 64 | 37 | 41 |
| fixed45/45 | 64 | 32 | 33 |
| asym20u/10u | 63 | 68 | 70 |
| asym10u/20u | 59 | 67 | 59 |
| sym15u | 55 | 76 | 20 |
| fixed40/80 | 39 | 29 | 20 |
| asym15u/30u | 17 | 17 | 19 |
| sym30u | 13 | 11 | 26 |
| fixed120/120 | 3 | 1 | 3 |

Cells whose ladder bracket is already the best in L6M: 91 of 1544. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 1064.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 129179; failed at both pass-1 brackets: 62405; positive in both windows at another shape: 23574. By shape: {'fixed90/30': 4512, 'fixed45/45': 1569, 'fixed120/60': 4022, 'fixed80/40': 2533, 'sym8u': 494, 'asym20u/10u': 290, 'fixed30/30': 2196, 'fixed40/80': 1612, 'fixed30/90': 2035, 'fixed90/90': 2012, 'fixed60/120': 1898, 'asym10u/20u': 235, 'asym15u/30u': 44, 'fixed120/120': 42, 'sym30u': 80}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 301 cells, 16 distinct: 439 cells, 15 distinct: 74 cells, 14 distinct: 231 cells, 13 distinct: 47 cells, 12 distinct: 196 cells, 11 distinct: 256 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 22180 of 44004 grid cells in these jobs.

## Top 30 ladder cells by L6M equal-risk net points/week (best shape), L3M beside, plain 60/60 number beside

| cell | row | module | ladder bracket | best shape (L6M) | L6M eq pts/wk | L3M at that shape | own bracket L6M | plain 60/60 L6M |
|---|---|---|---|---|---|---|---|---|
| Bf66cc006 | dlt_70 | tape_stack | sym15u | fixed80/40 | 1178.76 | 2010.98 | -19.61 | 80.74 |
| Bbaf67379 | vsess_80 | bands_atrchan | asym10u/20u | fixed90/30 | 917.54 | 725.66 | -16.53 | 208.99 |
| Ba93746f2 | cdr_250 | xmarket_fx | sym15u | fixed90/30 | 877.24 | 3799.51 | 27.02 | 88.94 |
| Lf66cc006 | dlt_70 | tape_stack | sym15u | fixed80/40 | 750.54 | 1517.2 | 7.31 | 53.23 |
| Lbaf67379 | vsess_80 | bands_atrchan | asym10u/20u | fixed90/30 | 720.98 | 771.53 | 25.42 | 103.51 |
| L56729447 | drb_3500 | structure_level | sym15u | fixed90/30 | 696.25 | 145.47 | 34.57 | 69.57 |
| B743baaf3 | cusum_28 | book_wall | sym15u | fixed45/45 | 683.28 | 504.51 | -54.16 | 18.86 |
| L39b1ea06 | pnf_10 | book_ofi | sym8u | fixed120/60 | 660.95 | 170.71 | 50.22 | 36.21 |
| Be4ff030d | vol_750 | bands_bollinger | asym10u/20u | fixed120/60 | 652.85 | 186.83 | 15.35 | -161.57 |
| L7f20db08 | pnf_20 | levels_swsr5 | plain60/60 | sym8u | 634.37 | 139.8 | -22.1 | -22.1 |
| Lf33795f9 | pnf_20 | levels_swsr5 | plain60/60 | sym8u | 634.37 | 139.8 | -22.1 | -22.1 |
| B6060e7de | bmsg_B050 | xmarket_rty | sym15u | fixed80/40 | 628.68 | 188.69 | -35.75 | 5.76 |
| B531ae882 | bmsg_B080 | book_dwm | sym15u | fixed90/30 | 581.89 | 268.0 | -3.41 | -100.88 |
| La8b4356d | mom_40 | levels_session_hl | sym15u | fixed120/60 | 580.27 | 145.73 | 33.71 | -12.11 |
| Le30d987f | lbrk_3_40 | levels_prior_day | plain60/60 | fixed120/60 | 576.56 | 183.69 | -10.62 | -10.62 |
| L0fcf8761 | tick_5000 | momentum_er | sym8u | fixed30/90 | 540.02 | 134.22 | 17.21 | 3.27 |
| B2a83e05f | bmsg_B050 | manual_cci | sym15u | fixed40/80 | 514.76 | 157.79 | -29.49 | 46.08 |
| Ld669fb20 | dltor_B320 | bands_keltner | sym15u | fixed120/60 | 498.33 | 803.09 | 19.25 | -50.33 |
| L531ae882 | bmsg_B080 | book_dwm | sym15u | fixed90/30 | 458.63 | 61.39 | 20.87 | -41.12 |
| Bcbd629e5 | dol_500 | trend_linreg | sym30u | fixed90/30 | 453.48 | 136.57 | -4.49 | -73.13 |
| L86f0c198 | urenko_56 | levels_piv_floor | sym15u | fixed30/30 | 449.99 | 34.3 | -30.83 | -70.79 |
| L02c1f662 | mom_14 | barnative_run | sym15u | fixed30/90 | 449.53 | 70.93 | -9.82 | -60.66 |
| Lf0447f1d | vsess_30 | levels_vwap | sym8u | fixed80/40 | 447.37 | 917.52 | 30.72 | 22.73 |
| L9d14d49d | bmsg_B030 | book_cancel | sym15u | fixed80/40 | 443.89 | 440.15 | 58.48 | 4.59 |
| L15865e21 | bmsg_B320 | momentum_roc | sym15u | fixed60/120 | 433.26 | 171.63 | 19.5 | 8.3 |
| L728cd432 | cusum_112 | levels_fib60 | sym15u | fixed90/30 | 433.2 | 49.41 | 8.19 | -9.78 |
| Lddba3fab | drb_2000 | book_ice | plain60/60 | sym8u | 432.34 | 166.75 | 18.03 | 18.03 |
| L723eefc5 | kagi_56 | bands_bollinger | sym15u | fixed80/40 | 405.22 | 47.61 | -9.99 | 18.65 |
| Lfa0b8527 | cusum_28 | levels_round | asym10u/20u | fixed80/40 | 402.69 | 46.69 | 14.58 | 26.66 |
| B87f1447e | tick_500 | levels_opens | sym8u | fixed80/40 | 402.45 | 901.37 | -7.95 | 24.61 |
