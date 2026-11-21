# BRACKET FIRST LOOK, ASIA (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-21 16:53 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 869 of 1890.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed45/45 | 144 | 146 | 144 |
| fixed30/90 | 136 | 78 | 102 |
| fixed60/120 | 124 | 57 | 85 |
| fixed40/80 | 123 | 93 | 98 |
| fixed30/30 | 95 | 72 | 81 |
| plain60/60 | 50 | 84 | 32 |
| fixed80/40 | 44 | 77 | 43 |
| sym8u | 38 | 47 | 32 |
| fixed90/90 | 38 | 39 | 35 |
| fixed120/60 | 27 | 67 | 32 |
| fixed90/30 | 21 | 55 | 14 |
| asym10u/20u | 11 | 9 | 9 |
| asym20u/10u | 9 | 21 | 12 |
| sym15u | 8 | 14 | 6 |
| sym30u | 1 | 7 | 2 |
| asym15u/30u | 0 | 3 | 5 |

Cells whose ladder bracket is already the best in L6M: 23 of 869. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 732.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 101318; failed at both pass-1 brackets: 31275; positive in both windows at another shape: 15688. By shape: {'sym8u': 479, 'fixed60/120': 1414, 'asym20u/10u': 203, 'fixed90/90': 1604, 'fixed40/80': 2300, 'asym10u/20u': 207, 'fixed45/45': 1796, 'fixed30/90': 4072, 'fixed120/60': 601, 'fixed30/30': 1644, 'fixed90/30': 636, 'fixed80/40': 562, 'sym30u': 78, 'fixed120/120': 58, 'asym15u/30u': 34}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 192 cells, 16 distinct: 245 cells, 15 distinct: 82 cells, 14 distinct: 113 cells, 13 distinct: 64 cells, 12 distinct: 57 cells, 11 distinct: 116 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 13255 of 34298 grid cells in these jobs.

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
| L8c6f2274 | time_m_5 | momentum_rsi | sym8u | plain60/60 | 717.38 | 842.27 | -29.01 | 101.04 |
| Lb1f1c309 | time_m_5 | momentum_rsi | sym8u | plain60/60 | 717.38 | 842.27 | -29.01 | 101.04 |
| L8280f7d4 | cusum_28 | levels_profile_nodes | sym15u | fixed45/45 | 660.17 | 250.55 | 3.92 | 80.54 |
| Ld58fdf3f | vsess_30 | momentum_willr | sym15u | fixed30/30 | 597.13 | 449.67 | -12.14 | 69.63 |
| L422121a0 | dlt_70 | structure_breakout | sym15u | fixed45/45 | 596.84 | 824.67 | -9.35 | 96.15 |
| L2c3e6790 | dlt_70 | bands_donchian | sym15u | fixed45/45 | 596.84 | 824.67 | -9.35 | 96.15 |
| L205413af | renko_14 | bands_envelope | sym15u | fixed30/90 | 579.29 | 442.15 | -24.33 | -13.55 |
| L302f2cbb | time_m_60 | levels_fib60 | sym15u | plain60/60 | 572.24 | 225.71 | -21.17 | 75.25 |
| L9e3c5607 | vol_1100 | bands_bollinger | sym8u | fixed45/45 | 543.87 | 352.59 | 13.46 | 50.13 |
| L4f7bebff | cusum_40 | levels_fib15 | plain60/60 | fixed30/90 | 538.86 | 119.36 | 40.66 | 40.66 |
| L649b1f75 | cusum_40 | momentum_er | sym15u | fixed40/80 | 531.43 | 228.41 | 33.3 | 42.96 |
| L06669f1b | renko_20 | tape_delta | sym30u | fixed30/90 | 496.25 | 114.22 | 5.51 | 14.98 |
| L45d0f6cc | dib_3500 | levels_vwap_bands | sym15u | fixed45/45 | 488.83 | 115.02 | -12.84 | 51.61 |
| L015ce9cd | dlt_150 | bands_donchian | sym15u | plain60/60 | 481.58 | 135.16 | -5.98 | 43.36 |
| L5293df31 | dlt_400 | trend_libstack | sym15u | fixed30/30 | 464.19 | 221.56 | 7.93 | 61.87 |
| Ld8421129 | vol_500 | bands_bollinger | sym8u | fixed30/30 | 460.34 | 530.26 | -1.66 | 40.52 |
| Ld0c2a94e | dlt_150 | structure_breakout | sym15u | plain60/60 | 450.14 | 115.6 | -9.32 | 38.9 |
| L93a79f26 | cusum_28 | levels_vwap | sym15u | fixed80/40 | 446.49 | 419.05 | -14.74 | 49.48 |
| Le3255198 | cusum_28 | levels_vwap | sym15u | fixed80/40 | 446.49 | 419.05 | -14.74 | 49.48 |
| L1f772651 | tib_2000 | bands_bollinger | sym15u | fixed30/30 | 445.87 | 60.18 | 4.41 | 10.75 |
| L3f67f56f | drb_10000 | levels_fib5 | sym15u | plain60/60 | 441.05 | 512.37 | 29.36 | 53.54 |
