# DS3_REBUILD_S1 - Stage 1: every condition family scored against the RAW book trades (W-S1; order DIRECTIVE_REBUILD_20261116 + addenda + REFILL 11-17)
> VALIDATION (FIRST PASS, written 2026-11-17 04:18 UTC): trials counted = condition columns x 20 outcomes x book-session cells x 7 windows (TRIALS_LEDGER.csv RB1_RAW; correlated: outcomes, windows and cells overlap); correction = cell nonsense bar (99th pct of 200 nonsense columns) + sign stable in every year and L6M + BH 10% across all scored tests per window/outcome + shifted-label (11/23/37) and block-shift permutation nulls + 90 persistent-draw random columns + planted-edge columns per shard; ulcer-primary tier test (skip-rule path arithmetic vs 60 persistent draws, week-clustered bootstrap) on survivors; PBO: selecting best-of-65k is a fit, the permutation nulls play that role, no walk-forward fit in stage 1; in-sample on 2023-04..2026-10-30, NOT walk-forward or untouched; engine-exact re-runs of leads not done (no re-entry, no freed-book effect). Dollar columns: engine $ at base lots and engine fees $1.18 RT, $4.84 RT repriced and x1.75 live lots shown for the tier leaders.

VERDICT (data ends 2026-10-30; FIRST PASS): shards landed S 36 of 1624, permutation shards 0 of 32480; this page is rewritten as shards land. See "Read this first" below for what is and is not finished.

## Status
Raw base: 21049 trades, 7 books (K7 M7 P7 U7 A7 H7 O7); X3 X4 X5 raw cells hold 0 trades (shadow books not tradable in the raw chassis: not scored; S7, X1 X2 X6 X7 X8 have no engine definition). Driver: box 1 running 2, server 2 leased 0, load1 box 1 37.5. Shards: S (real + shifted labels + controls) 36/1624, P (50 block-shift permutations each, 20 batches = 1,000 per chunk x book) 0/32480. Updated 2026-11-17 04:18 UTC.

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
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 36/1192 | 13653 | 1.85 | 1.10 | 0.53 | 0.69 | 1.26 | 0.41 | 73 | 0 | not finished |

## Family table, window ALL43, outcomes 12 fixed brackets (stop 20/30/40 x target 15/20/30/45) (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 36/1192 | 54612 | 2.30 | 1.27 | 0.42 | 1.16 | 0.98 | 0.45 | 56 | 0 | not finished |

## Family table, window ALL43, outcomes mark-to-market 1/5/15/30/60 min (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 36/1192 | 22755 | 1.24 | 0.69 | 0.50 | 0.85 | 0.99 | 0.38 | 47 | 0 | not finished |

## Family table, window L6M, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 36/1192 | 11211 | 1.29 | 1.29 | 0.95 | 1.31 | 2.14 | 0.99 | 51 | 0 | not finished |

## Family table, window L6M, outcomes 12 fixed brackets (stop 20/30/40 x target 15/20/30/45) (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 36/1192 | 44844 | 2.05 | 2.05 | 0.98 | 1.90 | 2.01 | 1.00 | 34 | 0 | not finished |

## Family table, window L6M, outcomes mark-to-market 1/5/15/30/60 min (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 36/1192 | 18685 | 1.82 | 1.82 | 0.95 | 1.96 | 2.16 | 1.00 | 36 | 0 | not finished |

## Family table, window L3M, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 36/1192 | 8214 | 1.77 | 1.77 | 1.06 | 1.94 | 2.15 | 1.04 | 37 | 0 | not finished |

## Family table, window HOLD, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 36/1192 | 10026 | 1.82 | 1.74 | 0.94 | 2.14 | 1.62 | 0.96 | 44 | 0 | not finished |

## Survivors with the ulcer-primary tier test (outcome R, ALL43 stable, per book x session cell, top 60 by |zw| per cell; skip rule on the raw cell, path arithmetic)
Tier counts: {'FAIL': 26, 'CONFIRMED': 18, 'LEAD': 8}. Persistent draws 60 (5-minute bucket per book and side, same skipped share). Tiers need ulcer-or-mean percentile >= .85 (CONFIRMED) / .75 (LEAD) in L6M and L3M, P(ulcer lower, L6M) >= .80, nothing below .25 in older windows.
| tier | family | cell | condition | rule | zw | lift R | BH ok | L6M ulc raw -> rule | L6M mean $/wk raw -> rule | pct ulc / mean L6M | L3M | HOLD ulc | P(ulc lower L6M) | L6M $/wk $4.84 | L6M $/wk x1.75 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| CONFIRMED | 1 | K7|S0 | c_B_cl_ahead_kinds2_15 | skip no | 6.3 | 0.259 | yes | -28120 -> -5082 | 3429 -> 3062 | 0.98 / 0.98 | 1.00 / 1.00 | 0.42 | 0.97 | -367 | -643 |
| CONFIRMED | 1 | K7|S0 | c_B_cl_ahead_cnt2_15 | skip no | 6.1 | 0.255 | yes | -28120 -> -5340 | 3429 -> 2972 | 0.95 / 0.97 | 1.00 / 1.00 | 0.52 | 0.96 | -457 | -799 |
| CONFIRMED | 1 | P7|S0 | c_B_cl_ahead_kinds2_10 | skip no | 4.9 | 0.222 | yes | -36590 -> -29394 | 16772 -> 9689 | 0.50 / 0.93 | 0.95 / 0.90 | 0.85 | 0.84 | -7083 | -12395 |
| CONFIRMED | 1 | K7|S3 | c_S_weekrange_used_le0.8 | skip no | 3.9 | 0.075 | yes | -24248 -> -11774 | -995 -> -209 | 0.78 / 0.87 | 0.98 / 0.98 | 0.82 | 0.94 | 786 | 1375 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_kinds2_10 | skip no | 3.8 | 0.272 | yes | -4779 -> -3464 | 587 -> 967 | 0.80 / 0.93 | 0.95 / 0.97 | 0.98 | 0.89 | 380 | 665 |
| CONFIRMED | 1 | U7|S0 | c_B_cl_ahead_kinds2_a2 | skip no | 3.7 | 0.405 | no | -10662 -> -5178 | 2753 -> 5119 | 1.00 / 1.00 | 0.87 / 0.90 | 0.52 | 0.91 | 2366 | 4141 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_cnt2_10 | skip no | 3.6 | 0.249 | no | -4779 -> -3768 | 587 -> 879 | 0.72 / 0.92 | 0.98 / 0.97 | 1.00 | 0.84 | 291 | 510 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_kinds2_5 | skip no | 3.5 | 0.276 | no | -4779 -> -2233 | 587 -> 1690 | 0.98 / 1.00 | 1.00 / 0.97 | 0.65 | 0.96 | 1103 | 1930 |
| CONFIRMED | 1 | P7|S1 | c_D4_stoch14_n6 | skip yes | -3.6 | -0.117 | no | -32871 -> -24469 | 2733 -> 4042 | 0.83 / 0.92 | 0.85 / 0.90 | 0.70 | 0.85 | 1309 | 2291 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_kinds2_15 | skip no | 2.8 | 0.238 | yes | -4779 -> -2086 | 587 -> 1137 | 0.98 / 0.97 | 0.98 / 0.97 | 0.97 | 0.97 | 550 | 963 |
| CONFIRMED | 1 | M7|S3 | c_B_gap_open | skip no | 2.7 | 0.085 | no | -8747 -> -4528 | 199 -> 256 | 0.87 / 0.68 | 0.75 / 0.85 | 0.75 | 0.81 | 58 | 101 |
| CONFIRMED | 1 | H7|S3 | c_D4_cci14_n6 | skip no | 3.4 | 0.226 | no | -1725 -> -1024 | 623 -> 500 | 0.78 / 0.93 | 1.00 / 0.90 | 0.37 | 0.92 | -123 | -215 |
| CONFIRMED | 1 | K7|S0 | c_S_pivot_R1S1_beyond | skip no | 2.7 | 0.173 | no | -28120 -> -5424 | 3429 -> 1591 | 0.88 / 0.92 | 0.52 / 0.93 | 0.45 | 0.97 | -1837 | -3216 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_cnt2_5 | skip no | 2.6 | 0.226 | no | -4779 -> -2650 | 587 -> 1423 | 0.93 / 1.00 | 0.92 / 0.92 | 0.62 | 0.92 | 836 | 1463 |
| CONFIRMED | 1 | A7|S0 | c_B_cl_ahead_cnt2_15 | skip no | 2.6 | 0.225 | no | -4779 -> -2161 | 587 -> 1049 | 0.97 / 0.95 | 0.98 / 0.97 | 0.95 | 0.96 | 461 | 807 |
| CONFIRMED | 1 | A7|S0 | c_S_pivot_R1S1_beyond | skip no | 2.6 | 0.191 | no | -4779 -> -1665 | 587 -> 784 | 0.97 / 0.93 | 0.73 / 0.97 | 0.98 | 0.95 | 196 | 344 |
| CONFIRMED | 1 | M7|S3 | c_D4_ema21_px_n5 | skip yes | -2.5 | -0.090 | no | -8747 -> -2349 | 199 -> 262 | 0.95 / 0.80 | 0.97 / 0.75 | 0.30 | 0.97 | 63 | 110 |
| CONFIRMED | 1 | K7|S3 | c_D4_rsi14_n4 | skip yes | -2.5 | -0.097 | no | -24248 -> -2140 | -995 -> 127 | 1.00 / 0.88 | 1.00 / 0.88 | 0.40 | 1.00 | 1122 | 1963 |
| LEAD | 1 | P7|S0 | c_B_cl_ahead_cnt2_10 | skip no | 4.8 | 0.219 | yes | -36590 -> -26662 | 16772 -> 8763 | 0.55 / 0.90 | 0.93 / 0.88 | 0.82 | 0.77 | -8009 | -14016 |
| LEAD | 1 | P7|S0 | c_B_cl_ahead_cnt3_15 | skip no | 4.2 | 0.227 | yes | -36590 -> -26545 | 16772 -> 17613 | 0.60 / 0.98 | 0.68 / 0.98 | 0.88 | 0.60 | 841 | 1472 |
| LEAD | 1 | P7|S0 | c_B_cl_ahead_kinds2_5 | skip no | 3.9 | 0.236 | yes | -36590 -> -36435 | 16772 -> 10985 | 0.32 / 0.83 | 0.87 / 0.80 | 1.00 | 0.44 | -5787 | -10127 |
| LEAD | 1 | U7|S0 | c_B_cl_ahead_kinds2_5 | skip no | 3.4 | 0.312 | no | -10662 -> -5393 | 2753 -> 4217 | 0.93 / 1.00 | 0.77 / 0.60 | 0.58 | 0.87 | 1464 | 2561 |
| LEAD | 1 | A7|S0 | c_S_atrmove_le1 | skip yes | -3.5 | -0.272 | yes | -4779 -> -3133 | 587 -> 188 | 0.37 / 0.80 | 0.92 / 0.98 | 0.97 | 0.89 | -399 | -699 |
| LEAD | 1 | K7|S4 | c_D4_aroon25_n6 | skip no | 3.0 | 0.232 | no | -13606 -> -2931 | 1320 -> 417 | 0.83 / 0.68 | 0.87 / 0.65 | 0.83 | 0.96 | -902 | -1579 |
| LEAD | 1 | K7|S0 | c_B_cl_ahead_cnt3_15 | skip no | 2.7 | 0.152 | no | -28120 -> -13026 | 3429 -> 2877 | 0.92 / 0.80 | 0.93 / 0.92 | 0.38 | 0.56 | -552 | -966 |
| LEAD | 1 | K7|S4 | c_C_px_oPOC_side | skip no | 2.5 | 0.133 | no | -13606 -> -6428 | 1320 -> 2395 | 0.90 / 0.97 | 0.78 / 0.95 | 0.42 | 0.79 | 1075 | 1882 |
| FAIL | 1 | K7|S0 | c_B_cl_ahead_kinds2_10 | skip no | 4.7 | 0.216 | yes | -28120 -> -12877 | 3429 -> 1547 | 0.60 / 0.58 | 0.83 / 0.77 | 0.82 | 0.78 | -1881 | -3293 |
| FAIL | 1 | K7|S0 | c_B_cl_ahead_cnt2_10 | skip no | 4.5 | 0.219 | yes | -28120 -> -13043 | 3429 -> 1460 | 0.60 / 0.55 | 0.82 / 0.77 | 0.85 | 0.77 | -1969 | -3445 |
| FAIL | 1 | K7|S0 | c_B_cl_ahead_kinds2_5 | skip no | 4.3 | 0.185 | yes | -28120 -> -16011 | 3429 -> 2028 | 0.65 / 0.67 | 0.60 / 0.52 | 0.77 | 0.57 | -1401 | -2451 |
| FAIL | 1 | K7|S0 | c_B_cl_ahead_cnt2_5 | skip no | 3.9 | 0.190 | yes | -28120 -> -14830 | 3429 -> 1877 | 0.58 / 0.63 | 0.67 / 0.57 | 0.68 | 0.61 | -1552 | -2716 |
| FAIL | 1 | P7|S0 | c_B_cl_ahead_cnt3_5 | skip no | 3.6 | 0.208 | yes | -36590 -> -36226 | 16772 -> 14408 | 0.47 / 0.60 | 0.83 / 0.58 | 0.95 | 0.41 | -2363 | -4136 |
| FAIL | 1 | U7|S0 | c_B_cl_ahead_cnt3_10 | skip no | 3.5 | 0.305 | no | -10662 -> -11604 | 2753 -> 3959 | 0.35 / 0.93 | 0.22 / 0.27 | 0.73 | 0.68 | 1206 | 2111 |
| FAIL | 1 | K7|S0 | c_S_vwapmax_ge4 | skip no | 3.1 | 0.124 | no | -28120 -> -13746 | 3429 -> 3827 | 1.00 / 0.93 | 0.87 / 0.88 | 1.00 | 0.94 | 398 | 697 |
| FAIL | 1 | P7|S1 | c_S_dpmr_used_le0.6 | skip no | 3.7 | 0.237 | no | -32871 -> -438 | 2733 -> 1411 | 1.00 / 0.98 | 0.97 / 1.00 | 0.77 | 1.00 | -1322 | -2313 |
| FAIL | 1 | U7|S0 | c_B_cl_ahead_cnt3_a2 | skip no | 3.5 | 0.350 | no | -10662 -> -9534 | 2753 -> 3996 | 0.70 / 0.97 | 0.57 / 0.62 | 1.00 | 0.83 | 1243 | 2175 |
| FAIL | 1 | H7|S3 | c_D4_boll20_pctb_n6 | skip no | 4.1 | 0.182 | no | -1725 -> -1241 | 623 -> 351 | 0.62 / 0.83 | 1.00 / 0.72 | 0.70 | 0.91 | -272 | -476 |
| FAIL | 1 | U7|S1 | c_S_sqzstat_pos_5m | skip yes | -3.0 | -0.210 | no | -13693 -> -6074 | -180 -> 1367 | 1.00 / 0.93 | 0.95 / 0.97 | 0.88 | 0.97 | 1548 | 2709 |
| FAIL | 1 | P7|S3 | c_A_px_ema200_1m | skip no | 3.0 | 0.160 | no | -52822 -> -42891 | -169 -> 612 | 0.77 / 0.83 | 0.38 / 0.63 | 0.45 | 0.77 | 781 | 1367 |
| FAIL | 1 | M7|S1 | c_V_qp_inside | skip no | 2.8 | 0.146 | no | -32674 -> -29803 | -623 -> -101 | 0.38 / 0.58 | 0.43 / 0.67 | 1.00 | 0.71 | 522 | 914 |
| FAIL | 1 | K7|S3 | c_B_cl_ahead_far | skip yes | -2.8 | -0.066 | no | -24248 -> -13920 | -995 -> -405 | 0.57 / 0.68 | 0.78 / 0.98 | 0.73 | 0.87 | 589 | 1031 |
(The $4.84 column here equals the engine-$ change with the commission repricing not applied per trade: a skip removes trades, so the $4.84 repricing changes only the removed trades; exact repricing is in the Stage 6 head-to-head. x1.75 = live lots.)

## Read this first
- Missing controls are "not finished", never passing: the perm p column is blank until every chunk x book permutation shard of a batch has landed for that family.
- Conditions that need a feed D7 lacks (L3, UW, options, order-message rates, cross-market) are scored but flagged: see chunks.csv feed column (/mnt/l2/l2vast/_rebuild/s1/chunks.csv).
- Not scored: X3/X4/X5 (0 raw trades), S7 and X1 X2 X6 X7 X8 (no engine definition), W-AL1 forecast conditions (pending), W-CH1 day/regime column (fam8 file empty), L3 combine/deepen flag files (derived from members already scored), cf4 state-wait float columns.
- Numbers CSVs: /mnt/l2/l2vast/_rebuild/s1/out/ (family_*.csv, survivors_detail.parquet, tiers.parquet).
