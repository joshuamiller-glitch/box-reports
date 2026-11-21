# BRACKET FIRST LOOK, ASIA (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-21 19:34 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 1884 of 1890.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed45/45 | 302 | 281 | 281 |
| fixed30/90 | 284 | 181 | 215 |
| fixed40/80 | 268 | 232 | 231 |
| fixed60/120 | 240 | 104 | 151 |
| fixed30/30 | 189 | 132 | 158 |
| plain60/60 | 111 | 170 | 79 |
| sym8u | 99 | 128 | 83 |
| fixed80/40 | 67 | 124 | 66 |
| fixed90/90 | 65 | 61 | 51 |
| fixed120/60 | 64 | 145 | 74 |
| asym20u/10u | 50 | 84 | 52 |
| asym10u/20u | 46 | 58 | 47 |
| fixed90/30 | 37 | 94 | 26 |
| sym15u | 24 | 43 | 19 |
| sym30u | 21 | 22 | 23 |
| asym15u/30u | 11 | 22 | 17 |
| fixed120/120 | 6 | 3 | 5 |

Cells whose ladder bracket is already the best in L6M: 53 of 1884. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 1578.

## NULL for the best-of-17 pick (exchangeable shape labels)

If the 17 shapes were interchangeable, calling any one of them the "own bracket" would give per cell the same two numbers. Averaged over all 17 possible own brackets of every cell: own bracket is the best in L6M in 6.0% of cells (the real ladder bracket: 2.8%); SOME other shape beats it at equal risk in BOTH windows in 86.0% of cells (the real ladder bracket: 83.8%). READING: the real ladder bracket is NOT better than a random one and the share of cells with a "better" shape is what chance gives, so the headline count is not evidence of a better bracket; only cells that also pass the engine, walk-forward and the null count.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 200394; failed at both pass-1 brackets: 63699; positive in both windows at another shape: 31851. By shape: {'fixed30/90': 7895, 'fixed60/120': 2755, 'asym15u/30u': 221, 'fixed90/90': 3162, 'sym8u': 1243, 'fixed45/45': 3513, 'fixed40/80': 4700, 'fixed30/30': 2858, 'fixed120/60': 1324, 'asym10u/20u': 699, 'fixed80/40': 931, 'asym20u/10u': 629, 'fixed90/30': 1045, 'sym30u': 502, 'fixed120/120': 374}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 765 cells, 16 distinct: 506 cells, 15 distinct: 121 cells, 14 distinct: 176 cells, 13 distinct: 93 cells, 12 distinct: 76 cells, 11 distinct: 144 cells, 2 distinct: 3 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 19744 of 68308 grid cells in these jobs.

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
| Lf66e961d | wrenko_20 | structure_level | sym15u | plain60/60 | 1117.99 | 202.32 | 2.38 | 98.76 |
| L8ee9c7bb | trend_20 | structure_level | sym15u | plain60/60 | 1117.99 | 202.32 | 2.38 | 98.76 |
| Lce33ae93 | kagi_28 | barnative_avwap | sym15u | fixed30/30 | 1108.92 | 1145.12 | -9.4 | 32.02 |
| L5c493ea5 | dib_400 | momentum_mvote | sym15u | plain60/60 | 912.67 | 372.78 | -3.3 | 79.62 |
| L6b373671 | frenko_40 | levels_piv_floor | sym15u | plain60/60 | 845.66 | 221.33 | 14.87 | 120.94 |
| L4cdac967 | vol_1700 | structure_breakout | sym8u | fixed45/45 | 831.69 | 178.77 | 1.31 | 38.22 |
| Lee20a819 | urenko_20 | structure_breakout | sym15u | fixed60/120 | 810.8 | 391.67 | -25.54 | 45.63 |
| L57643f2f | tick_300 | levels_vwap | sym30u | plain60/60 | 807.13 | 907.85 | 16.7 | 134.15 |
| L55ccc884 | mom_10 | levels_vwap | plain60/60 | sym30u | 802.77 | 148.08 | 35.67 | 35.67 |
| L27d5734f | dib_2000 | bands_bollinger | sym15u | fixed40/80 | 791.94 | 293.99 | -2.27 | 84.72 |
| Ld7f44642 | rng_40 | book_cancel | sym15u | fixed45/45 | 779.19 | 42.64 | 4.2 | 66.56 |
| L9ec946d6 | tick_300 | levels_gaps | asym15u/30u | fixed30/90 | 763.88 | 267.96 | -31.18 | -7.84 |
| La339b56b | time_m_2 | structure_breakout | sym30u | plain60/60 | 731.61 | 340.27 | 2.68 | 94.46 |
| L8c6f2274 | time_m_5 | momentum_rsi | sym8u | plain60/60 | 717.38 | 842.27 | -29.01 | 101.04 |
| Lb1f1c309 | time_m_5 | momentum_rsi | sym8u | plain60/60 | 717.38 | 842.27 | -29.01 | 101.04 |
| L33b38abb | vol_4000 | levels_fib5 | sym15u | fixed30/90 | 704.21 | 269.82 | -13.62 | 23.08 |
| L40d82d81 | vol_1700 | barnative_delta | sym8u | fixed45/45 | 664.51 | 169.09 | 37.6 | 93.61 |
| L8280f7d4 | cusum_28 | levels_profile_nodes | sym15u | fixed45/45 | 660.17 | 250.55 | 3.92 | 80.54 |
| Ld58fdf3f | vsess_30 | momentum_willr | sym15u | fixed30/30 | 597.13 | 449.67 | -12.14 | 69.63 |
| L422121a0 | dlt_70 | structure_breakout | sym15u | fixed45/45 | 596.84 | 824.67 | -9.35 | 96.15 |
| L2c3e6790 | dlt_70 | bands_donchian | sym15u | fixed45/45 | 596.84 | 824.67 | -9.35 | 96.15 |
| L1343f8bd | frenko_28 | levels_trendline | plain60/60 | fixed45/45 | 582.84 | 424.45 | 19.26 | 19.26 |
| L205413af | renko_14 | bands_envelope | sym15u | fixed30/90 | 579.29 | 442.15 | -24.33 | -13.55 |

## Not yet read (grid files not landed): 0 ladder cells

They are NOT dropped: the finisher re-reads them when their files land and appends their step-2 rows in a second file. Cells: 

