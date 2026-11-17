# DS3_REBUILD_S1 - Stage 1: every condition family scored against the RAW book trades (W-S1; order DIRECTIVE_REBUILD_20261116 + addenda + REFILL 11-17)
> VALIDATION (FIRST PASS, written 2026-11-17 04:21 UTC): trials counted = condition columns x 20 outcomes x book-session cells x 7 windows (TRIALS_LEDGER.csv RB1_RAW; correlated: outcomes, windows and cells overlap); correction = cell nonsense bar (99th pct of 200 nonsense columns) + sign stable in every year and L6M + BH 10% across all scored tests per window/outcome + shifted-label (11/23/37) and block-shift permutation nulls + 90 persistent-draw random columns + planted-edge columns per shard; ulcer-primary tier test (skip-rule path arithmetic vs 60 persistent draws, week-clustered bootstrap) on survivors; PBO: selecting best-of-65k is a fit, the permutation nulls play that role, no walk-forward fit in stage 1; in-sample on 2023-04..2026-10-30, NOT walk-forward or untouched; engine-exact re-runs of leads not done (no re-entry, no freed-book effect). Dollar columns: engine $ at base lots and engine fees $1.18 RT, $4.84 RT repriced and x1.75 live lots shown for the tier leaders.

VERDICT (data ends 2026-10-30; FIRST PASS): shards landed S 83 of 1624, permutation shards 0 of 32480; this page is rewritten as shards land. See "Read this first" below for what is and is not finished.

## Status
Raw base: 21049 trades, 7 books (K7 M7 P7 U7 A7 H7 O7); X3 X4 X5 raw cells hold 0 trades (shadow books not tradable in the raw chassis: not scored; S7, X1 X2 X6 X7 X8 have no engine definition). Driver: box 1 running 6, server 2 leased 0, load1 box 1 40.1. Shards: S (real + shifted labels + controls) 83/1624, P (50 block-shift permutations each, 20 batches = 1,000 per chunk x book) 0/32480. Updated 2026-11-17 04:21 UTC.

## Raw base (stage 0 table used here, engine $ at base lots and $1.18 RT; MAE_R positive = worse; R = net / (lots x 20 x stop))
| book | session | trades | mean R | win % | net $ (base) | mean MFE_R | mean MAE_R |
|--|--|--|--|--|--|--|--|
| A7 | asia | 1165 | 0.092 | 54.2 | 128,135 | 0.69 | 0.64 |
| H7 | asia | 684 | 0.067 | 52.3 | 221,154 | 0.68 | 0.63 |
| H7 | nyam | 411 | 0.038 | 50.9 | 18,896 | 0.66 | 0.66 |
| K7 | asia | 2195 | 0.063 | 53.2 | 332,681 | 0.68 | 0.67 |
| K7 | london | 1748 | 0.024 | 51.0 | 99,829 | 0.66 | 0.68 |
| K7 | nyam | 1849 | 0.008 | 50.7 | 18,354 | 0.66 | 0.67 |
| K7 | nypm | 1648 | 0.015 | 50.8 | 60,799 | 0.64 | 0.65 |
| M7 | london | 2251 | -0.009 | 49.7 | -48,077 | 0.66 | 0.70 |
| M7 | nyam | 1648 | 0.047 | 52.4 | 93,250 | 0.67 | 0.67 |
| O7 | nyam | 506 | 0.236 | 37.9 | 95,512 | 1.23 | 0.72 |
| P7 | asia | 2128 | 0.053 | 52.9 | 943,979 | 0.69 | 0.67 |
| P7 | london | 1664 | 0.008 | 50.7 | 60,965 | 0.66 | 0.69 |
| P7 | nyam | 1803 | 0.006 | 50.9 | 72,896 | 0.67 | 0.68 |
| U7 | asia | 670 | 0.071 | 53.7 | 229,143 | 0.69 | 0.65 |
| U7 | london | 679 | 0.033 | 51.8 | 108,402 | 0.67 | 0.68 |

## Family table, window ALL43, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 83/1192 | 82137 | 1.50 | 0.85 | 0.52 | 0.68 | 1.10 | 0.40 | 71 | 0 | not finished |

## Family table, window ALL43, outcomes 12 fixed brackets (stop 20/30/40 x target 15/20/30/45) (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 83/1192 | 328548 | 1.90 | 1.05 | 0.41 | 1.15 | 1.02 | 0.43 | 54 | 0 | not finished |

## Family table, window ALL43, outcomes mark-to-market 1/5/15/30/60 min (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 83/1192 | 136895 | 1.39 | 0.79 | 0.49 | 0.86 | 0.95 | 0.37 | 45 | 0 | not finished |

## Family table, window L6M, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 83/1192 | 64407 | 1.60 | 1.60 | 0.95 | 1.32 | 2.15 | 0.99 | 50 | 0 | not finished |

## Family table, window L6M, outcomes 12 fixed brackets (stop 20/30/40 x target 15/20/30/45) (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 83/1192 | 257628 | 2.14 | 2.14 | 0.98 | 1.88 | 1.97 | 1.00 | 33 | 0 | not finished |

## Family table, window L6M, outcomes mark-to-market 1/5/15/30/60 min (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 83/1192 | 107345 | 1.82 | 1.82 | 0.95 | 1.97 | 2.05 | 1.00 | 35 | 0 | not finished |

## Family table, window L3M, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 83/1192 | 43146 | 1.87 | 1.87 | 1.06 | 1.96 | 2.34 | 1.05 | 37 | 0 | not finished |

## Family table, window HOLD, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 83/1192 | 54702 | 2.19 | 2.14 | 0.95 | 2.15 | 2.25 | 0.97 | 43 | 0 | not finished |

## Survivors with the ulcer-primary tier test (outcome R, ALL43 stable, per book x session cell, top 60 by |zw| per cell; skip rule on the raw cell, path arithmetic)
Tier counts: {'FAIL': 143, 'CONFIRMED': 56, 'LEAD': 23}. Persistent draws 60 (5-minute bucket per book and side, same skipped share). Tiers need ulcer-or-mean percentile >= .85 (CONFIRMED) / .75 (LEAD) in L6M and L3M, P(ulcer lower, L6M) >= .80, nothing below .25 in older windows.
| tier | family | cell | condition | rule | zw | lift R | BH ok | L6M ulc raw -> rule | L6M mean $/wk raw -> rule | pct ulc / mean L6M | L3M | HOLD ulc | P(ulc lower L6M) | L6M $/wk $4.84 | L6M $/wk x1.75 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| CONFIRMED | 1 | K7|S0 | c_B_cl_ahead_kinds2_15 | skip no | 6.3 | 0.259 | yes | -28120 -> -5082 | 3429 -> 3062 | 0.98 / 0.98 | 1.00 / 1.00 | 0.42 | 0.97 | -367 | -643 |
| CONFIRMED | 1 | K7|S0 | c_B_cl_ahead_cnt2_15 | skip no | 6.1 | 0.255 | yes | -28120 -> -5340 | 3429 -> 2972 | 0.95 / 0.97 | 1.00 / 1.00 | 0.52 | 0.96 | -457 | -799 |
| CONFIRMED | 1 | P7|S0 | c_B_cl_ahead_kinds2_10 | skip no | 4.9 | 0.222 | yes | -36590 -> -29394 | 16772 -> 9689 | 0.50 / 0.93 | 0.95 / 0.90 | 0.85 | 0.84 | -7083 | -12395 |
| CONFIRMED | 1 | K7|S3 | c_S_weekrange_used_le0.8 | skip no | 3.9 | 0.075 | yes | -24248 -> -11774 | -995 -> -209 | 0.78 / 0.87 | 0.98 / 0.98 | 0.82 | 0.94 | 786 | 1375 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_kinds2_10 | skip no | 3.8 | 0.272 | yes | -4779 -> -3464 | 587 -> 967 | 0.80 / 0.93 | 0.95 / 0.97 | 0.98 | 0.89 | 380 | 665 |
| CONFIRMED | 1 | P7|S1 | m_vwma34_px_1m_side | skip yes | -4.0 | -0.226 | no | -32871 -> -3876 | 2733 -> 2122 | 0.93 / 1.00 | 0.68 / 0.88 | 0.28 | 0.99 | -611 | -1069 |
| CONFIRMED | 1 | U7|S0 | c_B_cl_ahead_kinds2_a2 | skip no | 3.7 | 0.405 | no | -10662 -> -5178 | 2753 -> 5119 | 1.00 / 1.00 | 0.87 / 0.90 | 0.52 | 0.91 | 2366 | 4141 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_cnt2_10 | skip no | 3.6 | 0.249 | no | -4779 -> -3768 | 587 -> 879 | 0.72 / 0.92 | 0.98 / 0.97 | 1.00 | 0.84 | 291 | 510 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_kinds2_5 | skip no | 3.5 | 0.276 | no | -4779 -> -2233 | 587 -> 1690 | 0.98 / 1.00 | 1.00 / 0.97 | 0.65 | 0.96 | 1103 | 1930 |
| CONFIRMED | 1 | P7|S1 | c_D4_stoch14_n6 | skip yes | -3.6 | -0.117 | no | -32871 -> -24469 | 2733 -> 4042 | 0.83 / 0.92 | 0.85 / 0.90 | 0.70 | 0.85 | 1309 | 2291 |
| CONFIRMED | 1 | U7|S1 | m_uo_5m_divwith | skip yes | -4.0 | -0.365 | no | -13693 -> -9058 | -180 -> 1483 | 1.00 / 1.00 | 0.98 / 0.98 | 0.75 | 1.00 | 1663 | 2910 |
| CONFIRMED | 1 | P7|S0 | m_demarker21_1m_divwith | skip yes | -3.4 | -0.203 | no | -36590 -> -29784 | 16772 -> 20456 | 0.78 / 1.00 | 0.95 / 1.00 | 0.92 | 0.99 | 3684 | 6447 |
| CONFIRMED | 1 | K7|S1 | m_trix15_3m_divwith | skip no | 3.3 | 0.200 | no | -40458 -> -1733 | -1103 -> 2120 | 1.00 / 1.00 | 0.98 / 1.00 | 0.50 | 1.00 | 3223 | 5640 |
| CONFIRMED | 1 | P7|S3 | m_trix15_1m_divwith | skip no | 3.2 | 0.243 | no | -52822 -> -3927 | -169 -> 1087 | 1.00 / 0.90 | 0.92 / 0.90 | 0.95 | 0.99 | 1256 | 2198 |
| CONFIRMED | 1 | M7|S3 | m_di14_1m_fresh5 | skip yes | -3.1 | -0.191 | no | -8747 -> -3705 | 199 -> 1049 | 0.98 / 0.98 | 0.90 / 0.92 | 0.83 | 1.00 | 850 | 1487 |
| CONFIRMED | 1 | A7|S0 | m_hma200_px_3m_nodiv | skip yes | -3.1 | -0.274 | no | -4779 -> -1905 | 587 -> 631 | 0.90 / 0.90 | 1.00 / 0.88 | 0.98 | 0.98 | 44 | 77 |
| CONFIRMED | 1 | K7|S1 | m_stochrsi21_5m_nodiv | skip yes | -3.1 | -0.208 | no | -40458 -> -3070 | -1103 -> 798 | 1.00 / 0.90 | 0.98 / 0.82 | 0.52 | 0.98 | 1901 | 3326 |
| CONFIRMED | 1 | K7|S3 | m_mfi7_3m_divwith | skip no | 3.0 | 0.064 | yes | -24248 -> -1715 | -995 -> 67 | 0.98 / 0.83 | 0.98 / 0.97 | 0.63 | 1.00 | 1062 | 1858 |
| CONFIRMED | 1 | K7|S3 | m_cmf10_3m_divwith | skip no | 3.0 | 0.128 | no | -24248 -> -1515 | -995 -> 108 | 1.00 / 0.85 | 0.87 / 0.93 | 0.82 | 1.00 | 1103 | 1930 |
| CONFIRMED | 1 | M7|S1 | m_boll20_walk_3m_divwith | skip yes | -3.8 | -0.325 | no | -32674 -> -25321 | -623 -> 491 | 0.97 / 1.00 | 1.00 / 0.97 | 0.45 | 0.99 | 1114 | 1950 |
| CONFIRMED | 1 | P7|S3 | m_vwma200_px_3m_rise | skip no | 3.0 | 0.197 | no | -52822 -> -24297 | -169 -> 1940 | 1.00 / 0.98 | 0.85 / 0.70 | 0.52 | 0.95 | 2109 | 3690 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_kinds2_15 | skip no | 2.8 | 0.238 | yes | -4779 -> -2086 | 587 -> 1137 | 0.98 / 0.97 | 0.98 / 0.97 | 0.97 | 0.97 | 550 | 963 |
| CONFIRMED | 1 | M7|S3 | m_obv_3m_side | skip no | 2.9 | 0.244 | no | -8747 -> -8820 | 199 -> 635 | 0.43 / 0.93 | 0.82 / 0.90 | 0.58 | 0.90 | 436 | 764 |
| CONFIRMED | 1 | K7|S1 | m_willr21_5m_nodiv | skip yes | -2.9 | -0.188 | no | -40458 -> -4512 | -1103 -> 792 | 0.93 / 0.90 | 0.85 / 0.90 | 0.90 | 0.99 | 1895 | 3316 |
| CONFIRMED | 1 | K7|S0 | m_hma34_px_3m_side | skip yes | -2.8 | -0.170 | no | -28120 -> -4531 | 3429 -> 1241 | 0.95 / 0.90 | 0.72 / 0.92 | 0.92 | 0.88 | -2188 | -3829 |
| CONFIRMED | 1 | P7|S3 | m_cmo21_3m_side | skip no | 2.8 | 0.239 | no | -52822 -> -29897 | -169 -> 1891 | 0.95 / 0.97 | 0.98 / 0.97 | 0.25 | 0.99 | 2060 | 3605 |
| CONFIRMED | 1 | P7|S3 | m_sma21_px_3m_rise | skip no | 2.8 | 0.239 | no | -52822 -> -29897 | -169 -> 1891 | 0.95 / 0.97 | 0.98 / 0.97 | 0.25 | 0.99 | 2060 | 3605 |
| CONFIRMED | 1 | M7|S3 | c_B_gap_open | skip no | 2.7 | 0.085 | no | -8747 -> -4528 | 199 -> 256 | 0.87 / 0.68 | 0.75 / 0.85 | 0.75 | 0.81 | 58 | 101 |
| CONFIRMED | 1 | M7|S3 | m_stoch21_5m_eleave | skip no | 3.7 | 0.207 | no | -8747 -> -1211 | 199 -> 170 | 0.78 / 0.92 | 0.78 / 0.98 | 0.25 | 0.99 | -29 | -51 |
| CONFIRMED | 1 | U7|S1 | m_rsi7_1m_nodiv | skip yes | -2.9 | -0.221 | no | -13693 -> -5930 | -180 -> 1341 | 0.93 / 0.97 | 0.82 / 0.98 | 0.62 | 0.98 | 1522 | 2663 |
| CONFIRMED | 1 | K7|S1 | m_roc20_1m_rise | skip no | 2.7 | 0.120 | no | -40458 -> -14109 | -1103 -> 1616 | 0.93 / 1.00 | 0.82 / 0.95 | 0.57 | 0.97 | 2719 | 4758 |
| CONFIRMED | 1 | H7|S3 | c_D4_cci14_n6 | skip no | 3.4 | 0.226 | no | -1725 -> -1024 | 623 -> 500 | 0.78 / 0.93 | 1.00 / 0.90 | 0.37 | 0.92 | -123 | -215 |
| CONFIRMED | 1 | U7|S1 | m_boll20_walk_1m_fresh5 | skip no | 2.7 | 0.117 | no | -13693 -> -3993 | -180 -> 880 | 1.00 / 0.85 | 0.93 / 0.92 | 0.70 | 0.95 | 1060 | 1856 |
| CONFIRMED | 1 | K7|S0 | c_S_pivot_R1S1_beyond | skip no | 2.7 | 0.173 | no | -28120 -> -5424 | 3429 -> 1591 | 0.88 / 0.92 | 0.52 / 0.93 | 0.45 | 0.97 | -1837 | -3216 |
| CONFIRMED | 1 | K7|S0 | m_sma21_px_1m_divwith | skip no | 2.7 | 0.048 | yes | -28120 -> -3694 | 3429 -> 1000 | 0.88 / 0.93 | 0.90 / 0.83 | 0.42 | 0.98 | -2428 | -4250 |
| CONFIRMED | 1 | A7|S0 | m_kama21_px_3m_nodiv | skip yes | -2.7 | -0.241 | no | -4779 -> -3150 | 587 -> 988 | 0.63 / 1.00 | 0.95 / 0.95 | 0.42 | 0.99 | 400 | 701 |
| CONFIRMED | 1 | A7|S0 | m_obv_3m_nodiv | skip yes | -2.6 | -0.221 | no | -4779 -> -2214 | 587 -> 512 | 0.88 / 0.78 | 0.97 / 0.88 | 0.95 | 0.96 | -76 | -132 |
| CONFIRMED | 1 | K7|S4 | m_rsi14_5m_ewith | skip no | 2.8 | 0.198 | no | -13606 -> -1820 | 1320 -> 396 | 0.90 / 0.83 | 0.78 / 0.97 | 0.92 | 0.92 | -924 | -1616 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_cnt2_5 | skip no | 2.6 | 0.226 | no | -4779 -> -2650 | 587 -> 1423 | 0.93 / 1.00 | 0.92 / 0.92 | 0.62 | 0.92 | 836 | 1463 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_cnt2_15 | skip no | 2.6 | 0.225 | no | -4779 -> -2161 | 587 -> 1049 | 0.97 / 0.95 | 0.98 / 0.97 | 0.95 | 0.96 | 461 | 807 |
(The $4.84 column here equals the engine-$ change with the commission repricing not applied per trade: a skip removes trades, so the $4.84 repricing changes only the removed trades; exact repricing is in the Stage 6 head-to-head. x1.75 = live lots.)

## Read this first
- Missing controls are "not finished", never passing: the perm p column is blank until every chunk x book permutation shard of a batch has landed for that family.
- Conditions that need a feed D7 lacks (L3, UW, options, order-message rates, cross-market) are scored but flagged: see chunks.csv feed column (/mnt/l2/l2vast/_rebuild/s1/chunks.csv).
- Not scored: X3/X4/X5 (0 raw trades), S7 and X1 X2 X6 X7 X8 (no engine definition), W-AL1 forecast conditions (pending), W-CH1 day/regime column (fam8 file empty), L3 combine/deepen flag files (derived from members already scored), cf4 state-wait float columns.
- Numbers CSVs: /mnt/l2/l2vast/_rebuild/s1/out/ (family_*.csv, survivors_detail.parquet, tiers.parquet).
