# BRACKET FIRST LOOK, ASIA (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-21 16:49 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 625 of 1890.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed30/90 | 102 | 62 | 77 |
| fixed45/45 | 101 | 109 | 103 |
| fixed40/80 | 96 | 64 | 75 |
| fixed60/120 | 86 | 30 | 57 |
| fixed30/30 | 68 | 56 | 57 |
| sym8u | 31 | 40 | 26 |
| plain60/60 | 30 | 56 | 17 |
| fixed90/90 | 28 | 27 | 25 |
| fixed80/40 | 25 | 57 | 29 |
| fixed120/60 | 21 | 46 | 25 |
| fixed90/30 | 14 | 39 | 10 |
| asym10u/20u | 10 | 8 | 8 |
| asym20u/10u | 7 | 13 | 9 |
| sym15u | 6 | 11 | 4 |
| asym15u/30u | 0 | 2 | 4 |
| sym30u | 0 | 5 | 1 |

Cells whose ladder bracket is already the best in L6M: 19 of 625. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 527.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 78227; failed at both pass-1 brackets: 24127; positive in both windows at another shape: 11929. By shape: {'fixed30/90': 3169, 'fixed40/80': 1751, 'fixed30/30': 1236, 'fixed90/30': 546, 'fixed60/120': 1094, 'fixed80/40': 480, 'fixed45/45': 1414, 'sym8u': 332, 'fixed90/90': 1057, 'asym10u/20u': 155, 'fixed120/60': 479, 'asym20u/10u': 126, 'fixed120/120': 37, 'sym30u': 39, 'asym15u/30u': 14}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 135 cells, 16 distinct: 166 cells, 15 distinct: 48 cells, 14 distinct: 86 cells, 13 distinct: 46 cells, 12 distinct: 43 cells, 11 distinct: 101 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 11795 of 26500 grid cells in these jobs.

## Top 30 ladder cells by L6M equal-risk net points/week (best shape), L3M beside, plain 60/60 number beside

| cell | row | module | ladder bracket | best shape (L6M) | L6M eq pts/wk | L3M at that shape | own bracket L6M | plain 60/60 L6M |
|---|---|---|---|---|---|---|---|---|
| Lc05f2615 | tick_800 | bands_bollinger | sym15u | fixed30/30 | 7581.11 | 2034.6 | -11.56 | 66.13 |
| Ldf65c0b2 | time_m_10 | momentum_squeeze | sym8u | fixed40/80 | 2264.56 | 1147.83 | 2.02 | 66.68 |
| Lb01ab72b | time_m_10 | momentum_squeeze | sym8u | fixed40/80 | 2264.56 | 1147.83 | 2.02 | 66.68 |
| L4f4f6e98 | rng_56 | tape_stoprun | sym8u | fixed90/30 | 1431.98 | 131.71 | -2.28 | 52.94 |
| L5483cb3c | urenko_56 | levels_profile_nodes | sym15u | fixed45/45 | 1155.56 | 463.73 | 21.41 | 12.68 |
| Lf0a487b9 | urenko_56 | levels_profile_nodes | sym15u | fixed45/45 | 1155.56 | 463.73 | 21.41 | 12.68 |
| La70d834e | dchg_28 | barnative_avwap | sym15u | fixed30/30 | 1130.13 | 1163.32 | -9.02 | 32.66 |
| Lce33ae93 | kagi_28 | barnative_avwap | sym15u | fixed30/30 | 1108.92 | 1145.12 | -9.4 | 32.02 |
| L27d5734f | dib_2000 | bands_bollinger | sym15u | fixed40/80 | 791.94 | 293.99 | -2.27 | 84.72 |
| Ld58fdf3f | vsess_30 | momentum_willr | sym15u | fixed30/30 | 597.13 | 449.67 | -12.14 | 69.63 |
| L205413af | renko_14 | bands_envelope | sym15u | fixed30/90 | 579.29 | 442.15 | -24.33 | -13.55 |
| L302f2cbb | time_m_60 | levels_fib60 | sym15u | plain60/60 | 572.24 | 225.71 | -21.17 | 75.25 |
| L4f7bebff | cusum_40 | levels_fib15 | plain60/60 | fixed30/90 | 538.86 | 119.36 | 40.66 | 40.66 |
| L649b1f75 | cusum_40 | momentum_er | sym15u | fixed40/80 | 531.43 | 228.41 | 33.3 | 42.96 |
| L06669f1b | renko_20 | tape_delta | sym30u | fixed30/90 | 496.25 | 114.22 | 5.51 | 14.98 |
| L5293df31 | dlt_400 | trend_libstack | sym15u | fixed30/30 | 464.19 | 221.56 | 7.93 | 61.87 |
| Ld8421129 | vol_500 | bands_bollinger | sym8u | fixed30/30 | 460.34 | 530.26 | -1.66 | 40.52 |
| L1f772651 | tib_2000 | bands_bollinger | sym15u | fixed30/30 | 445.87 | 60.18 | 4.41 | 10.75 |
| L3f67f56f | drb_10000 | levels_fib5 | sym15u | plain60/60 | 441.05 | 512.37 | 29.36 | 53.54 |
| L8fbb41c8 | drb_10000 | levels_fib5 | sym15u | plain60/60 | 441.05 | 512.37 | 29.36 | 53.54 |
| Lc820c5e4 | mrenko_20 | momentum_er | plain60/60 | fixed60/120 | 409.5 | 594.9 | 46.57 | 46.57 |
| L027cc31f | tick_300 | bands_bollinger | asym10u/20u | fixed45/45 | 389.2 | 188.56 | -19.28 | 58.8 |
| L53acc1ea | tick_3200 | pullback_ema | sym8u | fixed30/90 | 383.54 | 106.63 | 22.89 | 11.2 |
| L7669e599 | cdr_100 | trend_libstack | sym15u | fixed45/45 | 369.41 | 137.32 | 4.67 | 17.75 |
| Ld200871e | vol_1700 | bands_bollinger | plain60/60 | fixed80/40 | 362.05 | 158.21 | 21.52 | 21.52 |
| L7f414f21 | tick_800 | momentum_roc | sym15u | fixed30/30 | 361.51 | 179.46 | 4.14 | 37.93 |
| L3374cedf | mrenko_20 | momentum_er | plain60/60 | fixed60/120 | 361.09 | 580.53 | 52.0 | 52.0 |
| Lc8dbef10 | tick_500 | levels_opens | sym8u | fixed40/80 | 353.19 | 92.89 | -0.88 | 42.06 |
| L56902473 | tick_500 | levels_opens | sym8u | fixed40/80 | 353.19 | 92.89 | -0.88 | 42.06 |
| L17e224fb | lbrk_3_10 | levels_round | asym20u/10u | sym8u | 350.39 | 183.18 | 4.65 | 84.0 |
