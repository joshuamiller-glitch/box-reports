# BRACKET FIRST LOOK, ASIA (step 1, order 1632Z; prereg autopilot/PREREG_BRKT_FIRSTLOOK_STEP1.md)

Written 2026-11-21 18:09 UTC by W-BRKT from the bfl17 grid results (17 shapes, the ladder cells' grid jobs); screen level, weekly bins, net points per lot after cost; equal risk = scaled to the ulcer (weekly) of the cell's ladder bracket; L6M = weeks 2026-05-01..10-31, L3M = 2026-08-01..10-31; shapes with < 20 trades in L6M are not ranked. The 15% max-DD / worst-week guard is agent-added, not Josh's, and is not applied. Cells read: 1838 of 1890.

## Per shape: ladder cells where it is the best at equal risk

| shape | best in L6M | best in L3M | best in BOTH windows (beats own bracket in both) |
|---|---|---|---|
| fixed45/45 | 298 | 277 | 278 |
| fixed30/90 | 278 | 174 | 211 |
| fixed40/80 | 265 | 228 | 229 |
| fixed60/120 | 236 | 102 | 147 |
| fixed30/30 | 185 | 128 | 155 |
| plain60/60 | 105 | 167 | 78 |
| sym8u | 95 | 125 | 81 |
| fixed80/40 | 65 | 123 | 64 |
| fixed120/60 | 63 | 138 | 73 |
| fixed90/90 | 61 | 58 | 49 |
| asym20u/10u | 47 | 80 | 48 |
| asym10u/20u | 44 | 56 | 45 |
| fixed90/30 | 37 | 93 | 26 |
| sym15u | 23 | 42 | 19 |
| sym30u | 20 | 22 | 22 |
| asym15u/30u | 10 | 22 | 16 |
| fixed120/120 | 6 | 3 | 5 |

Cells whose ladder bracket is already the best in L6M: 47 of 1838. Cells with some shape beating the ladder bracket at equal risk in BOTH windows: 1546.

## NULL for the best-of-17 pick (exchangeable shape labels)

If the 17 shapes were interchangeable, calling any one of them the "own bracket" would give per cell the same two numbers. Averaged over all 17 possible own brackets of every cell: own bracket is the best in L6M in 5.9% of cells (the real ladder bracket: 2.6%); SOME other shape beats it at equal risk in BOTH windows in 86.3% of cells (the real ladder bracket: 84.1%). READING: the real ladder bracket is NOT better than a random one and the share of cells with a "better" shape is what chance gives, so the headline count is not evidence of a better bracket; only cells that also pass the engine, walk-forward and the null count.

## Cells that FAILED the first look (not positive in L6M at plain 60/60 AND at sym15u) but are positive in L6M and L3M (>= 20 trades L6M) at another shape: the books the search never saw

Grid cells (param x mode) in these jobs: 194474; failed at both pass-1 brackets: 61223; positive in both windows at another shape: 30926. By shape: {'fixed30/90': 7604, 'fixed60/120': 2659, 'asym15u/30u': 218, 'fixed90/90': 3081, 'sym8u': 1235, 'fixed45/45': 3458, 'fixed40/80': 4564, 'fixed30/30': 2765, 'fixed120/60': 1272, 'asym10u/20u': 684, 'fixed80/40': 912, 'asym20u/10u': 617, 'fixed90/30': 1015, 'sym30u': 491, 'fixed120/120': 351}. CAUTION: with 17 shapes some of these are chance (best-of-17 on 26 weeks); the engine step and the null decide.

## Clip: distinct shapes per ladder cell (of 17 weekly series)

17 distinct: 754 cells, 16 distinct: 501 cells, 15 distinct: 117 cells, 14 distinct: 172 cells, 13 distinct: 88 cells, 12 distinct: 74 cells, 11 distinct: 132 cells

Cells where sym15u and sym30u are identical (clipped to the same points): 18063 of 65945 grid cells in these jobs.

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

## Not yet read (grid files not landed): 52 ladder cells

They are NOT dropped: the finisher re-reads them when their files land and appends their step-2 rows in a second file. Cells: L0489ddef, L05bccf89, L08605126, L089ebe19, L097e1631, L115f64a4, L1716c153, L17a2ecf5, L18f91359, L20fc98b0, L2c1bf899, L36f1a14e, L3956ac61, L4db8ff7e, L59a6d32a, L5f26dfa6, L60d9ee7d, L63286bf2, L669d0c39, L6a8ee65c, L73cfff68, L7494cd72, L774720c8, L7d8ae0b9, L80af094b, L84bf98c0, L8bbb588c, L8cd3af6f, La1bd302b, La51a4a7b, La6fc9235, Laf04f24d, Lb48be81e, Lb7ac1fa5, Lb955d493, Lbace6732, Lbb476f9f, Lbdfdc937, Lc132feb3, Lca44c64b, Lcab3013a, Lcefc61e6, Ld273811a, Ld4149cfb, Ld8c178bf, Ldddaf334, Ldf6b9b20, Le4c6c635, Le6624699, Lea571969, Ledee09fc, Lf696f5fe

