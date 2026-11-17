# DS3_REBUILD_S1 [AT-ENTRY CLEAN TABLES: NONE YET - every table below is NOT at-entry-clean unless marked; see AT-ENTRY STATUS] - Stage 1 on RAW book trades (W-S1; order DIRECTIVE_REBUILD_20261116 + addenda + REFILL 11-17)
AT-ENTRY STATUS (read first, 2026-11-17 07:40 UTC): NO table on this page is at-entry-clean yet. (1) The family tables below pool ALL columns including _d5/_d30/_d60/_d120 WAIT variants (read 5-120 s after the signal, scored against a signal-time entry = LOOK-AHEAD), "ahead" columns and family-9 context: they are NOT at-entry and must not be used for a decision. (2) The survivors screen lists only columns whose NAME is at-entry (no _d>=5, no ahead, no family 9); it is in-sample and selection-biased, NOT a result. (3) Clean tables (at-entry-only family comparison, walk-forward, selection null, wait-then-enter and early-exit re-scores) are being built: sections marked PENDING below.

> VALIDATION (FIRST PASS, written 2026-11-17 07:40 UTC): trials counted = condition columns x 20 outcomes x book-session cells x 7 windows (TRIALS_LEDGER.csv RB1_RAW; correlated: outcomes, windows and cells overlap); correction = cell nonsense bar (99th pct of 200 nonsense columns) + sign stable in every year and L6M + BH 10% across all scored tests per window/outcome + shifted-label (11/23/37) and block-shift permutation nulls + 90 persistent-draw random columns + planted-edge columns per shard; ulcer-primary tier test (skip-rule path arithmetic vs 60 persistent draws, week-clustered bootstrap) on survivors; PBO: selecting best-of-65k is a fit, the permutation nulls play that role, no walk-forward fit in stage 1; in-sample on 2023-04..2026-10-30, NOT walk-forward or untouched; engine-exact re-runs of leads not done (no re-entry, no freed-book effect). Dollar columns: engine $ at base lots and engine fees $1.18 RT, $4.84 RT repriced and x1.75 live lots shown for the tier leaders.

VERDICT (data ends 2026-10-30; FIRST PASS): shards landed S 1618 of 0, permutation shards 417 of 3988; this page is rewritten as shards land. See "Read this first" below for what is and is not finished.

## Status
Raw base: 21049 trades, 7 books (K7 M7 P7 U7 A7 H7 O7); X3 X4 X5 raw cells hold 0 trades (shadow books not tradable in the raw chassis: not scored; S7, X1 X2 X6 X7 X8 have no engine definition). Driver: box 1 running 4, server 2 leased 73, load1 box 1 41.6. Shards: S (real + shifted labels + controls) 1618/0, P (50 block-shift permutations each, 20 batches = 1,000 per chunk x book) 417/3988. Updated 2026-11-17 07:40 UTC.

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
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 1189/1192 | 1677810 | 1.46 | 0.84 | 0.52 | 0.68 | 1.23 | 0.40 | 72 | 0 | not finished |
| 2 candle counting, ICT 7-13-21, IRL/ERL | 144/144 | 83778 | 2.02 | 1.42 | 0.52 | 0.68 | 1.57 | 0.40 | 72 | 0 | not finished |
| 3 zones | 8/8 | 1995 | 2.11 | 1.55 | 0.52 | 0.68 | 1.62 | 0.40 | 72 | 0 | not finished |
| 4 range (HAR / options / UW / own-bar) | 8/8 | 1476 | 2.51 | 1.63 | 0.52 | 0.68 | 1.22 | 0.40 | 72 | 0 | not finished |
| 5 order flow, L3, tape speed, L2 | 142/144 | 134928 | 2.67 | 1.76 | 0.52 | 0.68 | 0.98 | 0.40 | 71 | 0 | not finished |
| 6 other markets, breadth | 48/48 | 20382 | 1.23 | 0.74 | 0.52 | 0.68 | 1.21 | 0.40 | 72 | 0 | not finished |
| 7 options and positioning (UW) | 8/8 | 3660 | 2.65 | 2.08 | 0.52 | 0.68 | 1.56 | 0.40 | 72 | 0 | not finished |
| 8 day/regime/time of day/calendar/macro | 32/32 | 4992 | 2.06 | 1.22 | 0.52 | 0.68 | 1.35 | 0.40 | 72 | 0 | not finished |
| 9 trade context (RAW rebuilt)  | 15/16 | 2556 | 8.02 | 3.68 | 0.52 | 0.68 | 0.90 | 0.40 | 72 | 0 | not finished |
| 10 internals (TICK) | 16/16 | 774 | 1.55 | 1.29 | 0.52 | 0.68 | 0.69 | 0.40 | 72 | 0 | not finished |
| 8/9 day context + trade context (stack-based CF1 L/K) | 8/8 | 1761 | 4.54 | 1.53 | 0.52 | 0.68 | 1.21 | 0.40 | 72 | 0 | not finished |

## Family table, window ALL43, outcomes 12 fixed brackets (stop 20/30/40 x target 15/20/30/45) (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 1189/1192 | 6711240 | 2.00 | 1.14 | 0.41 | 1.15 | 1.04 | 0.44 | 54 | 0 | not finished |
| 2 candle counting, ICT 7-13-21, IRL/ERL | 144/144 | 335112 | 2.35 | 1.61 | 0.41 | 1.15 | 1.48 | 0.44 | 54 | 0 | not finished |
| 3 zones | 8/8 | 7980 | 3.08 | 2.02 | 0.41 | 1.15 | 1.68 | 0.44 | 54 | 0 | not finished |
| 4 range (HAR / options / UW / own-bar) | 8/8 | 5904 | 2.13 | 1.52 | 0.41 | 1.15 | 0.94 | 0.44 | 54 | 0 | not finished |
| 5 order flow, L3, tape speed, L2 | 142/144 | 539712 | 3.61 | 2.35 | 0.41 | 1.15 | 0.96 | 0.43 | 54 | 0 | not finished |
| 6 other markets, breadth | 48/48 | 81528 | 1.79 | 1.04 | 0.41 | 1.15 | 1.09 | 0.44 | 54 | 0 | not finished |
| 7 options and positioning (UW) | 8/8 | 14640 | 2.32 | 1.81 | 0.41 | 1.15 | 1.73 | 0.44 | 54 | 0 | not finished |
| 8 day/regime/time of day/calendar/macro | 32/32 | 19968 | 2.07 | 1.30 | 0.41 | 1.15 | 1.39 | 0.44 | 54 | 0 | not finished |
| 9 trade context (RAW rebuilt)  | 15/16 | 10224 | 5.02 | 2.17 | 0.41 | 1.15 | 0.95 | 0.44 | 54 | 0 | not finished |
| 10 internals (TICK) | 16/16 | 3096 | 0.87 | 0.48 | 0.41 | 1.15 | 0.75 | 0.44 | 54 | 0 | not finished |
| 8/9 day context + trade context (stack-based CF1 L/K) | 8/8 | 7044 | 4.49 | 2.24 | 0.41 | 1.15 | 1.35 | 0.44 | 54 | 0 | not finished |

## Family table, window ALL43, outcomes mark-to-market 1/5/15/30/60 min (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 1189/1192 | 2796350 | 1.42 | 0.80 | 0.49 | 0.86 | 1.00 | 0.37 | 46 | 0 | not finished |
| 2 candle counting, ICT 7-13-21, IRL/ERL | 144/144 | 139630 | 1.76 | 1.27 | 0.49 | 0.86 | 1.46 | 0.37 | 46 | 0 | not finished |
| 3 zones | 8/8 | 3325 | 2.53 | 2.05 | 0.49 | 0.86 | 1.42 | 0.37 | 46 | 0 | not finished |
| 4 range (HAR / options / UW / own-bar) | 8/8 | 2460 | 3.33 | 2.64 | 0.49 | 0.86 | 1.10 | 0.37 | 46 | 0 | not finished |
| 5 order flow, L3, tape speed, L2 | 142/144 | 224880 | 4.02 | 3.02 | 0.49 | 0.86 | 0.94 | 0.37 | 46 | 0 | not finished |
| 6 other markets, breadth | 48/48 | 33970 | 1.47 | 0.89 | 0.49 | 0.86 | 0.91 | 0.37 | 46 | 0 | not finished |
| 7 options and positioning (UW) | 8/8 | 6100 | 1.75 | 1.44 | 0.49 | 0.86 | 1.48 | 0.37 | 46 | 0 | not finished |
| 8 day/regime/time of day/calendar/macro | 32/32 | 8320 | 1.84 | 1.27 | 0.49 | 0.86 | 1.25 | 0.37 | 46 | 0 | not finished |
| 9 trade context (RAW rebuilt)  | 15/16 | 4260 | 2.89 | 1.01 | 0.49 | 0.86 | 0.92 | 0.37 | 46 | 0 | not finished |
| 10 internals (TICK) | 16/16 | 1290 | 1.01 | 0.62 | 0.49 | 0.86 | 1.24 | 0.37 | 46 | 0 | not finished |
| 8/9 day context + trade context (stack-based CF1 L/K) | 8/8 | 2935 | 2.59 | 1.29 | 0.49 | 0.86 | 1.24 | 0.37 | 46 | 0 | not finished |

## Family table, window L6M, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 1189/1192 | 1292091 | 1.40 | 1.40 | 0.95 | 1.33 | 2.07 | 0.99 | 51 | 0 | not finished |
| 2 candle counting, ICT 7-13-21, IRL/ERL | 144/144 | 52473 | 1.84 | 1.84 | 0.95 | 1.33 | 2.12 | 0.99 | 51 | 0 | not finished |
| 3 zones | 8/8 | 888 | 1.46 | 1.46 | 0.95 | 1.33 | 2.18 | 0.99 | 51 | 0 | not finished |
| 4 range (HAR / options / UW / own-bar) | 8/8 | 1056 | 0.28 | 0.28 | 0.95 | 1.33 | 2.87 | 0.99 | 51 | 0 | not finished |
| 5 order flow, L3, tape speed, L2 | 142/144 | 105219 | 1.97 | 1.97 | 0.95 | 1.32 | 1.92 | 0.99 | 51 | 0 | not finished |
| 6 other markets, breadth | 48/48 | 15927 | 1.41 | 1.41 | 0.95 | 1.33 | 1.96 | 0.99 | 51 | 0 | not finished |
| 7 options and positioning (UW) | 8/8 | 2418 | 1.82 | 1.82 | 0.95 | 1.33 | 2.25 | 0.99 | 51 | 0 | not finished |
| 8 day/regime/time of day/calendar/macro | 32/32 | 2559 | 1.84 | 1.84 | 0.95 | 1.33 | 2.38 | 0.99 | 51 | 0 | not finished |
| 9 trade context (RAW rebuilt)  | 15/16 | 2142 | 3.45 | 3.45 | 0.95 | 1.33 | 2.29 | 0.99 | 51 | 0 | not finished |
| 10 internals (TICK) | 16/16 | 366 | 1.09 | 1.09 | 0.95 | 1.33 | 3.46 | 0.99 | 51 | 0 | not finished |
| 8/9 day context + trade context (stack-based CF1 L/K) | 8/8 | 1263 | 2.69 | 2.69 | 0.95 | 1.33 | 1.66 | 0.99 | 51 | 0 | not finished |

## Family table, window L6M, outcomes 12 fixed brackets (stop 20/30/40 x target 15/20/30/45) (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 1189/1192 | 5168364 | 2.15 | 2.15 | 0.98 | 1.90 | 1.88 | 1.00 | 33 | 0 | not finished |
| 2 candle counting, ICT 7-13-21, IRL/ERL | 144/144 | 209892 | 2.43 | 2.43 | 0.98 | 1.90 | 2.09 | 1.00 | 33 | 0 | not finished |
| 3 zones | 8/8 | 3552 | 2.70 | 2.70 | 0.98 | 1.90 | 2.37 | 1.00 | 33 | 0 | not finished |
| 4 range (HAR / options / UW / own-bar) | 8/8 | 4224 | 2.46 | 2.46 | 0.98 | 1.90 | 2.00 | 1.00 | 33 | 0 | not finished |
| 5 order flow, L3, tape speed, L2 | 142/144 | 420876 | 3.23 | 3.23 | 0.98 | 1.89 | 1.92 | 1.00 | 33 | 0 | not finished |
| 6 other markets, breadth | 48/48 | 63708 | 1.81 | 1.81 | 0.98 | 1.90 | 1.68 | 1.00 | 33 | 0 | not finished |
| 7 options and positioning (UW) | 8/8 | 9672 | 3.47 | 3.47 | 0.98 | 1.90 | 2.34 | 1.00 | 33 | 0 | not finished |
| 8 day/regime/time of day/calendar/macro | 32/32 | 10236 | 2.19 | 2.19 | 0.98 | 1.90 | 2.20 | 1.00 | 33 | 0 | not finished |
| 9 trade context (RAW rebuilt)  | 15/16 | 8568 | 3.69 | 3.69 | 0.98 | 1.90 | 1.90 | 1.00 | 33 | 0 | not finished |
| 10 internals (TICK) | 16/16 | 1464 | 3.14 | 3.14 | 0.98 | 1.90 | 1.37 | 1.00 | 33 | 0 | not finished |
| 8/9 day context + trade context (stack-based CF1 L/K) | 8/8 | 5052 | 2.57 | 2.57 | 0.98 | 1.90 | 2.01 | 1.00 | 33 | 0 | not finished |

## Family table, window L6M, outcomes mark-to-market 1/5/15/30/60 min (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 1189/1192 | 2153485 | 1.76 | 1.76 | 0.95 | 1.98 | 2.02 | 1.00 | 35 | 0 | not finished |
| 2 candle counting, ICT 7-13-21, IRL/ERL | 144/144 | 87455 | 2.21 | 2.21 | 0.95 | 1.98 | 2.09 | 1.00 | 35 | 0 | not finished |
| 3 zones | 8/8 | 1480 | 2.70 | 2.70 | 0.95 | 1.98 | 2.27 | 1.00 | 35 | 0 | not finished |
| 4 range (HAR / options / UW / own-bar) | 8/8 | 1760 | 2.10 | 2.10 | 0.95 | 1.98 | 2.29 | 1.00 | 35 | 0 | not finished |
| 5 order flow, L3, tape speed, L2 | 142/144 | 175365 | 3.59 | 3.59 | 0.95 | 1.98 | 1.97 | 1.00 | 35 | 0 | not finished |
| 6 other markets, breadth | 48/48 | 26545 | 1.67 | 1.67 | 0.95 | 1.98 | 1.87 | 1.00 | 35 | 0 | not finished |
| 7 options and positioning (UW) | 8/8 | 4030 | 2.95 | 2.95 | 0.95 | 1.98 | 2.03 | 1.00 | 35 | 0 | not finished |
| 8 day/regime/time of day/calendar/macro | 32/32 | 4265 | 2.25 | 2.25 | 0.95 | 1.98 | 2.13 | 1.00 | 35 | 0 | not finished |
| 9 trade context (RAW rebuilt)  | 15/16 | 3570 | 3.61 | 3.61 | 0.95 | 1.98 | 1.94 | 1.00 | 35 | 0 | not finished |
| 10 internals (TICK) | 16/16 | 610 | 0.82 | 0.82 | 0.95 | 1.98 | 2.13 | 1.00 | 35 | 0 | not finished |
| 8/9 day context + trade context (stack-based CF1 L/K) | 8/8 | 2105 | 2.52 | 2.52 | 0.95 | 1.98 | 1.90 | 1.00 | 35 | 0 | not finished |

## Family table, window L3M, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 1189/1192 | 870354 | 1.78 | 1.78 | 1.06 | 1.96 | 2.21 | 1.05 | 37 | 0 | not finished |
| 2 candle counting, ICT 7-13-21, IRL/ERL | 144/144 | 27135 | 2.10 | 2.10 | 1.06 | 1.96 | 2.28 | 1.04 | 37 | 0 | not finished |
| 3 zones | 8/8 | 558 | 0.54 | 0.54 | 1.06 | 1.96 | 2.15 | 1.04 | 37 | 0 | not finished |
| 4 range (HAR / options / UW / own-bar) | 8/8 | 621 | 0.81 | 0.81 | 1.06 | 1.96 | 3.38 | 1.04 | 37 | 0 | not finished |
| 5 order flow, L3, tape speed, L2 | 142/144 | 70215 | 1.79 | 1.79 | 1.06 | 1.96 | 2.16 | 1.05 | 37 | 0 | not finished |
| 6 other markets, breadth | 48/48 | 11817 | 1.61 | 1.61 | 1.06 | 1.96 | 2.45 | 1.04 | 37 | 0 | not finished |
| 7 options and positioning (UW) | 8/8 | 1320 | 2.50 | 2.50 | 1.06 | 1.96 | 2.05 | 1.04 | 37 | 0 | not finished |
| 8 day/regime/time of day/calendar/macro | 32/32 | 1314 | 1.07 | 1.07 | 1.06 | 1.96 | 3.17 | 1.04 | 37 | 0 | not finished |
| 9 trade context (RAW rebuilt)  | 15/16 | 1467 | 2.86 | 2.86 | 1.06 | 1.96 | 2.50 | 1.04 | 37 | 0 | not finished |
| 10 internals (TICK) | 16/16 | 351 | 3.99 | 3.99 | 1.06 | 1.96 | 2.75 | 1.04 | 37 | 0 | not finished |
| 8/9 day context + trade context (stack-based CF1 L/K) | 8/8 | 927 | 2.27 | 2.27 | 1.06 | 1.96 | 2.52 | 1.04 | 37 | 0 | not finished |

## Family table, window HOLD, outcomes R / MFE_R / MAE_R (book x session cells only; stable = beyond bar AND same sign every year and L6M)
| family | shards | tests | real beyond bar % | real STABLE pass % | nonsense stable % | random-draw stable % | shifted-label real stable % | shifted-label nonsense % | planted detected % | perm draws | perm p (real stable count vs null) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 confluence/alt-bar/oscillator/trend/SMC/named/squeeze/session/profile | 1189/1192 | 1108554 | 2.11 | 2.05 | 0.95 | 2.14 | 2.01 | 0.97 | 44 | 0 | not finished |
| 2 candle counting, ICT 7-13-21, IRL/ERL | 144/144 | 39816 | 2.23 | 2.18 | 0.95 | 2.14 | 2.28 | 0.97 | 44 | 0 | not finished |
| 3 zones | 8/8 | 762 | 1.97 | 1.97 | 0.95 | 2.14 | 1.66 | 0.97 | 44 | 0 | not finished |
| 4 range (HAR / options / UW / own-bar) | 8/8 | 867 | 2.42 | 2.31 | 0.95 | 2.14 | 1.54 | 0.97 | 44 | 0 | not finished |
| 5 order flow, L3, tape speed, L2 | 142/144 | 89841 | 2.04 | 1.95 | 0.95 | 2.14 | 1.87 | 0.97 | 43 | 0 | not finished |
| 6 other markets, breadth | 48/48 | 13869 | 1.89 | 1.84 | 0.95 | 2.14 | 1.89 | 0.97 | 44 | 0 | not finished |
| 7 options and positioning (UW) | 8/8 | 1908 | 1.52 | 1.42 | 0.95 | 2.14 | 1.82 | 0.97 | 44 | 0 | not finished |
| 8 day/regime/time of day/calendar/macro | 32/32 | 2055 | 2.24 | 2.19 | 0.95 | 2.14 | 2.22 | 0.97 | 44 | 0 | not finished |
| 9 trade context (RAW rebuilt)  | 15/16 | 1827 | 2.24 | 2.19 | 0.95 | 2.14 | 1.70 | 0.97 | 44 | 0 | not finished |
| 10 internals (TICK) | 16/16 | 408 | 1.47 | 1.47 | 0.95 | 2.14 | 0.98 | 0.97 | 44 | 0 | not finished |
| 8/9 day context + trade context (stack-based CF1 L/K) | 8/8 | 1077 | 2.32 | 1.95 | 0.95 | 2.14 | 1.92 | 0.97 | 44 | 0 | not finished |

## In-sample survivors screen with the ulcer-primary percentile test (AT-ENTRY NAME-CLEAN COLUMNS ONLY; outcome R, ALL43 stable, per book x session cell; skip rule on the raw cell, path arithmetic)
IN-SAMPLE SCREEN ONLY (selection on the same 43 months it is tested on, top 60 by |zw| per cell: this ALWAYS passes against random skips; the words CONFIRMED / LEAD are NOT used here; see the walk-forward and selection-null sections). Tier counts: {'IS-FAIL': 553, 'IS-HI': 241, 'IS-MID': 106}. Persistent draws 60. IS-HI needs ulcer-or-mean percentile >= .85 in L6M and L3M, P(ulcer lower, L6M) >= .80, nothing below .25 in older windows; IS-MID >= .75. Only columns classified clean-by-name are listed (no _d>=5 wait variants, no ahead columns, no family-9 context).
| tier | family | cell | condition | rule | zw | lift R | BH ok | L6M ulc raw -> rule | L6M mean $/wk raw -> rule | pct ulc / mean L6M | L3M | HOLD ulc | P(ulc lower L6M) | L6M $/wk $4.84 | L6M $/wk x1.75 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| IS-HI | 1 | K7|S3 | c4_smieS_1m_divwith | skip no | 7.4 | 0.213 | yes | -24248 -> -1300 | -995 -> 86 | 0.85 / 0.82 | 0.53 / 0.87 | 0.30 | 1.00 | 1081 | 1892 |
| IS-HI | 1 | K7|S0 | c4_don20_pos_ha15_eenter | skip no | 9.4 | 0.322 | yes | -28120 -> -1590 | 3429 -> 1242 | 0.93 / 1.00 | 0.99 / 0.97 | 0.80 | 1.00 | -2187 | -3827 |
| IS-HI | 1 | K7|S0 | c4_w1_donchian20_pos_ha15_eenter | skip no | 9.4 | 0.322 | yes | -28120 -> -1590 | 3429 -> 1242 | 0.93 / 1.00 | 0.99 / 0.97 | 0.80 | 1.00 | -2187 | -3827 |
| IS-HI | 1 | P7|S3 | m_uo_1d_divwith | skip yes | -5.0 | -0.118 | yes | -52822 -> -42582 | -169 -> 1276 | 0.67 / 0.88 | 0.88 / 0.98 | 1.00 | 0.92 | 1445 | 2528 |
| IS-HI | 1 | K7|S0 | c4_fvgS_cnt_ha3_side | skip no | 4.6 | 0.292 | yes | -28120 -> -2668 | 3429 -> 2380 | 0.98 / 1.00 | 0.78 / 0.97 | 0.57 | 1.00 | -1048 | -1835 |
| IS-HI | 1 | K7|S3 | c4_mc_comp2_mtf_ge4 | skip yes | -4.3 | -0.104 | yes | -24248 -> -1349 | -995 -> 483 | 1.00 / 1.00 | 1.00 / 0.95 | 0.40 | 1.00 | 1478 | 2586 |
| IS-HI | 1 | K7|S1 | m_ao_5m_nodiv | skip yes | -4.6 | -0.336 | yes | -40458 -> -4691 | -1103 -> 983 | 0.87 / 0.98 | 1.00 / 1.00 | 0.98 | 0.99 | 2086 | 3650 |
| IS-HI | 1 | M7|S1 | c4_w1_kama200_px_range16_fresh5 | skip yes | -4.3 | -0.196 | yes | -32674 -> -25387 | -623 -> 369 | 0.75 / 0.93 | 0.72 / 0.92 | 0.97 | 0.90 | 992 | 1736 |
| IS-HI | 1 | H7|S0 | c4_lorS_1m_flip3 | skip yes | -4.5 | -0.195 | yes | -25780 -> -19680 | 1221 -> 2565 | 0.63 / 0.95 | 0.68 / 0.93 | 0.87 | 0.96 | 1344 | 2352 |
| IS-HI | 1 | U7|S1 | c4_sdF_dsup_range8_rise | skip yes | -4.4 | -0.116 | yes | -13693 -> -8035 | -180 -> 923 | 0.95 / 0.80 | 0.88 / 0.83 | 0.95 | 0.96 | 1103 | 1930 |
| IS-HI | 1 | K7|S0 | c4_kst_60m_nodiv | skip yes | -4.1 | -0.244 | yes | -28120 -> -5412 | 3429 -> 2699 | 0.88 / 0.98 | 0.63 / 0.90 | 1.00 | 0.97 | -730 | -1277 |
| IS-HI | 1 | M7|S1 | c4_w1_donchian50_pos_ha15_ewith | skip no | 4.6 | 0.219 | yes | -32674 -> -1149 | -623 -> 704 | 1.00 / 0.88 | 0.93 / 0.85 | 0.70 | 1.00 | 1328 | 2323 |
| IS-HI | 1 | K7|S4 | c4_wtS_1d_eagainst_z1 | skip no | 5.0 | 0.246 | yes | -13606 -> -0 | 1320 -> 0 | 1.00 / 0.42 | 0.99 / 0.45 | 0.92 | 1.00 | -1320 | -2309 |
| IS-HI | 1 | A7|S0 | c4_agr_smieS_fresh5_ge3 | skip yes | -4.3 | -0.292 | yes | -4779 -> -1277 | 587 -> 589 | 0.98 / 0.92 | 0.87 / 0.57 | 0.55 | 0.93 | 1 | 2 |
| IS-HI | 1 | A7|S0 | c4_sdflipS_in_ha60_against | skip no | 4.2 | 0.197 | yes | -4779 -> -910 | 587 -> 633 | 1.00 / 0.93 | 1.00 / 0.98 | 0.93 | 0.99 | 46 | 80 |
| IS-HI | 1 | P7|S1 | c4_agr_w1_willr14_ewith_ge3 | skip yes | -4.1 | -0.230 | yes | -32871 -> -7336 | 2733 -> 4535 | 0.97 / 0.98 | 0.88 / 0.93 | 1.00 | 0.98 | 1802 | 3153 |
| IS-HI | 2 | K7|S0 | c4_cdl_hammer_15m_against | skip no | 7.7 | 0.162 | yes | -28120 -> -1645 | 3429 -> 812 | 0.92 / 0.98 | 0.65 / 1.00 | 0.55 | 0.99 | -2617 | -4580 |
| IS-HI | 1 | K7|S1 | c4_agr_w1_mfi14_rise_ge6 | skip yes | -4.2 | -0.193 | yes | -40458 -> -4621 | -1103 -> 970 | 0.92 / 0.95 | 0.98 / 1.00 | 1.00 | 1.00 | 2073 | 3627 |
| IS-HI | 1 | P7|S0 | c4_fvg_cnt_ha60_fresh5 | skip no | 6.8 | 0.311 | yes | -36590 -> -2356 | 16772 -> 1572 | 0.95 / 0.80 | 0.97 / 0.68 | 0.92 | 0.99 | -15199 | -26599 |
| IS-HI | 1 | P7|S1 | c4_ker_dir_tick2000_eenter | skip yes | -4.0 | -0.162 | yes | -32871 -> -17828 | 2733 -> 3509 | 1.00 / 0.83 | 1.00 / 0.78 | 0.93 | 0.87 | 776 | 1358 |
| IS-HI | 1 | K7|S0 | c4_wtF_tick2000_eleave_z1 | skip yes | -4.6 | -0.421 | yes | -28120 -> -20683 | 3429 -> 4203 | 0.98 / 0.98 | 0.90 / 0.93 | 0.65 | 0.99 | 775 | 1356 |
| IS-HI | 1 | K7|S4 | c4_qqeS_15m_ewith | skip no | 4.8 | 0.354 | yes | -13606 -> -301 | 1320 -> 1291 | 1.00 / 1.00 | 1.00 / 1.00 | 0.88 | 1.00 | -28 | -50 |
| IS-HI | 1 | K7|S0 | c4_w1_macd12_26_9_line_ha60_nodiv | skip yes | -4.0 | -0.254 | yes | -28120 -> -6143 | 3429 -> 2150 | 0.83 / 0.97 | 0.58 / 0.87 | 0.92 | 0.98 | -1279 | -2237 |
| IS-HI | 1 | P7|S3 | m_demarker7_1d_divwith | skip yes | -4.2 | -0.222 | yes | -52822 -> -49316 | -169 -> 1321 | 0.47 / 0.93 | 0.65 / 0.93 | 0.73 | 0.89 | 1490 | 2608 |
| IS-HI | 5 | K7|S4 | fl070_d0 | skip yes | -3.9 | -0.169 | yes | -13606 -> -7637 | 1320 -> 2212 | 0.83 / 0.90 | 0.80 / 0.87 | 0.98 | 0.81 | 892 | 1561 |
| IS-HI | 1 | A7|S0 | c4_agr_tsi_fresh5_ge3 | skip yes | -4.0 | -0.180 | yes | -4779 -> -1433 | 587 -> 867 | 0.98 / 0.95 | 0.93 / 0.82 | 0.38 | 0.96 | 279 | 489 |
| IS-HI | 1 | O7|S3 | c4_w1_stoch14_tick2000_fresh5 | skip no | 5.4 | 0.232 | yes | -3756 -> -1951 | 311 -> 422 | 0.80 / 0.92 | 0.88 / 0.97 | 0.93 | 0.96 | 112 | 195 |
| IS-HI | 1 | M7|S1 | c4_don55_pos_ha15_ewith | skip no | 4.2 | 0.217 | yes | -32674 -> -1069 | -623 -> 881 | 1.00 / 0.90 | 0.97 / 0.88 | 0.85 | 1.00 | 1504 | 2632 |
| IS-HI | 6 | P7|S0 | c6_fc_agree_none5_against | skip no | 3.9 | 0.199 | yes | -36590 -> -8695 | 16772 -> 6148 | 1.00 / 0.92 | 0.97 / 0.88 | 0.68 | 1.00 | -10623 | -18591 |
| IS-HI | 1 | K7|S3 | c_S_weekrange_used_le0.8 | skip no | 3.9 | 0.075 | yes | -24248 -> -11774 | -995 -> -209 | 0.78 / 0.87 | 0.98 / 0.98 | 0.82 | 0.94 | 786 | 1375 |
| IS-HI | 1 | P7|S1 | c4_w1_willr7_ha15_nodiv | skip yes | -3.9 | -0.197 | no | -32871 -> -6918 | 2733 -> 4229 | 0.98 / 0.97 | 0.95 / 0.95 | 0.47 | 0.94 | 1496 | 2618 |
| IS-HI | 1 | K7|S1 | c4_agr_t3S_px_fresh5_ge6 | skip no | 3.8 | 0.164 | yes | -40458 -> -8022 | -1103 -> 1420 | 0.82 / 0.97 | 0.95 / 1.00 | 0.83 | 0.99 | 2523 | 4415 |
| IS-HI | 2 | K7|S1 | c4_pitchfork_15m_eleave | skip no | 3.8 | 0.187 | no | -40458 -> -8297 | -1103 -> 1418 | 0.82 / 0.97 | 1.00 / 1.00 | 0.98 | 0.97 | 2520 | 4411 |
| IS-HI | 1 | K7|S4 | c4_kerS_abs_tick2000_rise | skip no | 3.7 | 0.132 | yes | -13606 -> -6492 | 1320 -> 2663 | 0.83 / 0.98 | 0.97 / 0.97 | 0.92 | 0.96 | 1344 | 2351 |
| IS-HI | 5 | U7|S0 | fl214_d2 | skip no | 4.4 | 0.147 | yes | -10662 -> -4201 | 2753 -> 2019 | 0.90 / 0.95 | 0.90 / 0.83 | 0.85 | 0.95 | -735 | -1286 |
| IS-HI | 1 | P7|S0 | c4_w1_vortex21_ha1_divwith | skip yes | -3.9 | -0.185 | yes | -36590 -> -27981 | 16772 -> 19785 | 0.85 / 1.00 | 0.97 / 1.00 | 0.98 | 0.86 | 3013 | 5273 |
| IS-HI | 1 | M7|S1 | c4_obS_near_renko8_against | skip no | 3.7 | 0.177 | yes | -32674 -> -3487 | -623 -> 1000 | 0.98 / 0.88 | 0.82 / 0.87 | 0.78 | 1.00 | 1623 | 2840 |
| IS-HI | 2 | K7|S3 | c4_fib_cluster_dir_60m_side | skip yes | -3.8 | -0.213 | no | -24248 -> -15806 | -995 -> -420 | 0.87 / 0.93 | 0.95 / 0.98 | 0.95 | 0.94 | 574 | 1005 |
| IS-HI | 1 | P7|S0 | c4_fractal_alli_1d_fresh1 | skip no | 4.1 | 0.238 | yes | -36590 -> -4320 | 16772 -> 4630 | 0.98 / 0.93 | 1.00 / 0.93 | 0.65 | 0.97 | -12142 | -21248 |
| IS-HI | 5 | A7|S0 | fl190_d0 | skip no | 3.8 | 0.112 | yes | -4779 -> -1397 | 587 -> 538 | 0.98 / 0.87 | 0.92 / 0.77 | 0.73 | 0.94 | -50 | -87 |
(The $4.84 column here equals the engine-$ change with the commission repricing not applied per trade: a skip removes trades, so the $4.84 repricing changes only the removed trades; exact repricing is in the Stage 6 head-to-head. x1.75 = live lots.)

## Adaptive permutation screen (rb1_sched.py; replaces the fixed 1,000-permutation plan)
Rule: each chunk x book cell is SCREENED IN when its real STABLE pass count (book x session cells, windows ALL43+L6M, 20 outcomes) is >= 3 and >= 1.5 x the larger of the nonsense stable rate and the mean shifted-label (11/23/37) real stable rate on the same cell. Screened-in cells run 100 permutations first (batches 0,1); a cell is EXTENDED to 1,000 when its permutation p of the real stable count is <= 0.02 or its BH q (over all cells with 100 draws) is <= 0.10. A fixed-seed random 5% of the non-screened cells run the full 1,000 as a CALIBRATION check (their share with p < 0.05 should be about 5%); the other non-screened cells get 100 permutations last. Full 1,000 permutations are therefore not run for every cell: stated here, not hidden.
Cells 1624, screened in 266, extended 55, calibration cells 54 (done with >=1,000 draws: 0). Cells with permutation p computed: 534.
Calibration check: 0 of 0 calibration cells with p < 0.05 (expected about 5%) - not finished (fewer than 20 cells done).
| family | cells | screened in | with perm p | p < 0.05 |
|--|--|--|--|--|
| 1 | 1192 | 152 | 408 | 41 |
| 10 | 16 | 3 | 3 | 2 |
| 2 | 144 | 26 | 31 | 9 |
| 3 | 8 | 2 | 2 | 1 |
| 4 | 8 | 2 | 2 | 0 |
| 5 | 144 | 56 | 60 | 41 |
| 6 | 48 | 9 | 11 | 2 |
| 7 | 8 | 1 | 1 | 1 |
| 8 | 32 | 4 | 5 | 1 |
| 8/9 | 8 | 3 | 3 | 2 |
| 9 | 16 | 8 | 8 | 5 |

Leading cells by permutation p (count of real stable passes vs shifted nulls):
| chunk | book | family | real stable | real rate % | control rate % | draws | p | BH q |
|--|--|--|--|--|--|--|--|--|
| cf6_analogs_00 | U7 | 9 | 124 | 4.70 | 0.82 | 400 | 0.0025 | 0.031 |
| TAPE_SPEED_01 | U7 | 5 | 382 | 4.42 | 1.11 | 350 | 0.0028 | 0.031 |
| fam9_raw_00 | A7 | 9 | 100 | 8.93 | 0.76 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_01 | P7 | 5 | 1264 | 3.06 | 1.13 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_00 | P7 | 5 | 1589 | 3.91 | 1.41 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_00 | A7 | 5 | 617 | 4.48 | 1.14 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_01 | K7 | 5 | 2416 | 4.38 | 1.58 | 350 | 0.0028 | 0.031 |
| cf6_cols_all_01 | A7 | 2 | 229 | 4.06 | 1.80 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_04 | A7 | 5 | 515 | 3.90 | 1.04 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_05 | A7 | 5 | 365 | 4.30 | 1.42 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_05 | M7 | 5 | 781 | 4.54 | 1.24 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_05 | P7 | 5 | 1405 | 5.40 | 1.07 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_02 | U7 | 5 | 537 | 2.59 | 1.46 | 350 | 0.0028 | 0.031 |
| FLOW_PARTA_02 | K7 | 5 | 2556 | 4.72 | 1.52 | 300 | 0.0033 | 0.031 |
| FLOW_PARTA_00 | POOL | 5 | 5148 | 7.28 | 1.24 | 300 | 0.0033 | 0.031 |

## AT-ENTRY TABLES (name-clean columns only: no _d>=5 / _L>=5 wait variants, no unaudited ahead, no stack-based family 9; family 9 = rebuilt causal version) - written 2026-11-17 06:58 UTC; A shards landed 1576 of 1576
STATUS: COMPLETE

Family table at-entry, window ALL43, outcomes R/MFE_R/MAE_R, book x session cells (stable = beyond nonsense bar and sign stable by year/L6M). Real vs shifted-label (11/23/37) and nonsense/random controls:
| family | shards | tests | real beyond % | real STABLE % | shifted-label real STABLE % | nonsense stable % | random-draw stable % | planted detected % |
|--|--|--|--|--|--|--|--|--|
| 1 | 1192/1192 | 1678362 | 1.46 | 0.84 | 1.23 | 0.52 | 0.68 | 72 |
| 2 | 144/144 | 83487 | 2.03 | 1.42 | 1.57 | 0.52 | 0.68 | 72 |
| 3 | 8/8 | 714 | 2.10 | 1.40 | 1.77 | 0.52 | 0.68 | 72 |
| 4 | 8/8 | 1476 | 2.51 | 1.63 | 1.22 | 0.52 | 0.68 | 72 |
| 5 | 112/112 | 83394 | 1.84 | 1.11 | 0.99 | 0.52 | 0.68 | 72 |
| 6 | 48/48 | 20226 | 1.23 | 0.74 | 1.22 | 0.52 | 0.68 | 72 |
| 7 | 8/8 | 2751 | 2.98 | 2.29 | 1.44 | 0.52 | 0.68 | 72 |
| 8 | 32/32 | 4992 | 2.06 | 1.22 | 1.35 | 0.52 | 0.68 | 72 |
| 9 | 8/8 | 1128 | 7.71 | 2.22 | 1.00 | 0.52 | 0.68 | 72 |
| 10 | 16/16 | 774 | 1.55 | 1.29 | 0.69 | 0.52 | 0.68 | 72 |

Family table at-entry, window L6M, outcomes R/MFE_R/MAE_R, book x session cells (stable = beyond nonsense bar and sign stable by year/L6M). Real vs shifted-label (11/23/37) and nonsense/random controls:
| family | shards | tests | real beyond % | real STABLE % | shifted-label real STABLE % | nonsense stable % | random-draw stable % | planted detected % |
|--|--|--|--|--|--|--|--|--|
| 1 | 1192/1192 | 1292619 | 1.40 | 1.40 | 2.07 | 0.95 | 1.33 | 51 |
| 2 | 144/144 | 52239 | 1.84 | 1.84 | 2.12 | 0.95 | 1.33 | 51 |
| 3 | 8/8 | 192 | 1.56 | 1.56 | 2.95 | 0.95 | 1.33 | 51 |
| 4 | 8/8 | 1056 | 0.28 | 0.28 | 2.87 | 0.95 | 1.33 | 51 |
| 5 | 112/112 | 64554 | 1.51 | 1.51 | 1.99 | 0.95 | 1.33 | 51 |
| 6 | 48/48 | 15837 | 1.41 | 1.41 | 1.96 | 0.95 | 1.33 | 51 |
| 7 | 8/8 | 1965 | 1.88 | 1.88 | 2.17 | 0.95 | 1.33 | 51 |
| 8 | 32/32 | 2559 | 1.84 | 1.84 | 2.38 | 0.95 | 1.33 | 51 |
| 9 | 8/8 | 945 | 4.02 | 4.02 | 2.01 | 0.95 | 1.33 | 51 |
| 10 | 16/16 | 366 | 1.09 | 1.09 | 3.46 | 0.95 | 1.33 | 51 |

Family table at-entry, window UNT, outcomes R/MFE_R/MAE_R, book x session cells (stable = beyond nonsense bar and sign stable by year/L6M). Real vs shifted-label (11/23/37) and nonsense/random controls:
| family | shards | tests | real beyond % | real STABLE % | shifted-label real STABLE % | nonsense stable % | random-draw stable % | planted detected % |
|--|--|--|--|--|--|--|--|--|
| 1 | 1192/1192 | 1440045 | 1.97 | 1.83 | 1.81 | 0.88 | 1.69 | 61 |
| 2 | 144/144 | 65136 | 2.33 | 2.20 | 2.20 | 0.88 | 1.69 | 61 |
| 3 | 8/8 | 291 | 1.37 | 1.37 | 2.98 | 0.88 | 1.69 | 61 |
| 4 | 8/8 | 1221 | 0.41 | 0.41 | 1.83 | 0.88 | 1.69 | 61 |
| 5 | 112/112 | 72591 | 1.72 | 1.60 | 1.71 | 0.88 | 1.69 | 61 |
| 6 | 48/48 | 17205 | 1.97 | 1.83 | 1.72 | 0.88 | 1.69 | 61 |
| 7 | 8/8 | 2391 | 2.97 | 2.51 | 1.56 | 0.88 | 1.69 | 61 |
| 8 | 32/32 | 3687 | 2.25 | 2.17 | 2.52 | 0.88 | 1.69 | 61 |
| 9 | 8/8 | 999 | 6.61 | 5.81 | 1.47 | 0.88 | 1.69 | 61 |
| 10 | 16/16 | 450 | 3.11 | 3.11 | 1.26 | 0.88 | 1.69 | 61 |

### Selection null: the identical top-60-then-tier procedure (OLD = chosen and tested on the same 43 months, tiers renamed IS-HI / IS-MID so they cannot be read as CONFIRMED) on real, shifted-label and nonsense columns, outcome R, book x session cells, at-entry columns only
| procedure | source | rules selected | IS-HI | IS-MID | IS-FAIL |
|--|--|--|--|--|--|
| OLD | real | 900 | 238 | 109 | 553 |
| OLD | shift11 | 858 | 32 | 10 | 816 |
| OLD | shift23 | 900 | 39 | 19 | 842 |
| OLD | shift37 | 900 | 36 | 14 | 850 |
| OLD | nonsense | 720 | 300 | 60 | 360 |
Reading: the real IS-HI count only means something relative to the shifted-label / nonsense rows of the same procedure.

### Walk-forward: choose on 2023-04..2025-10 (SEL) only, freeze, report HOLD (2025-11..2026-04) and L6M (2026-05..10) untouched; skip-rule path arithmetic on the raw cell; ulcer change = rule vs raw (positive = lower ulcer), mean change in engine $/wk (base lots, $1.18 RT), $4.84 RT and x1.75 live
| source | cell | chosen | sign kept HOLD | sign kept L6M | median ulcer change HOLD % | median ulcer change L6M % | median mean $/wk HOLD (eng / $4.84 / x1.75) | median mean $/wk L6M (eng / $4.84 / x1.75) | share with pct>=.75 on ulcer or mean in HOLD and L6M |
|--|--|--|--|--|--|--|--|--|--|
| real | A7|S0 | 60 | 34 | 22 | 49.5 | -3.3 | -557 / -531 / -975 | -421 / -378 / -736 | 11% |
| real | H7|S0 | 60 | 31 | 25 | 27.6 | 34.4 | -24 / -13 / -42 | -774 / -756 / -1354 | 13% |
| real | H7|S3 | 25 | 5 | 13 | 15.7 | 13.3 | -67 / -64 / -117 | -371 / -365 / -650 | 8% |
| real | K7|S0 | 60 | 29 | 30 | 20.6 | 35.7 | -2234 / -2151 / -3910 | -1357 / -1337 / -2374 | 11% |
| real | K7|S1 | 60 | 31 | 21 | 22.2 | 20.0 | -26 / -14 / -45 | 118 / 127 / 206 | 15% |
| real | K7|S3 | 60 | 34 | 31 | 68.7 | 64.0 | 761 / 799 / 1331 | 706 / 748 / 1236 | 11% |
| real | K7|S4 | 60 | 24 | 32 | 44.3 | 40.3 | 953 / 987 / 1667 | -644 / -581 / -1127 | 5% |
| real | M7|S1 | 60 | 36 | 30 | 35.8 | 36.7 | -123 / -94 / -215 | 235 / 274 / 411 | 8% |
| real | M7|S3 | 60 | 34 | 20 | 32.2 | 36.5 | -296 / -259 / -518 | -175 / -155 / -306 | 15% |
| real | O7|S3 | 60 | 23 | 29 | 14.3 | 23.4 | -539 / -534 / -944 | -152 / -150 / -266 | 5% |
| real | P7|S0 | 60 | 26 | 22 | -8.6 | 16.6 | -3015 / -2949 / -5276 | -8002 / -7752 / -14003 | 8% |
| real | P7|S1 | 60 | 27 | 26 | 16.8 | 26.7 | -747 / -701 / -1307 | -1082 / -1050 / -1893 | 10% |
| real | P7|S3 | 60 | 35 | 31 | 31.0 | 28.7 | 1816 / 1958 / 3179 | 276 / 345 / 483 | 15% |
| real | U7|S0 | 60 | 25 | 34 | 22.8 | 6.7 | 158 / 185 / 277 | -807 / -791 / -1412 | 8% |
| real | U7|S1 | 60 | 29 | 29 | 27.9 | 8.3 | -306 / -271 / -536 | 28 / 46 / 49 | 6% |
| shift11 | A7|S0 | 60 | 24 | 32 | 40.7 | 16.2 | -594 / -567 / -1039 | -398 / -356 / -696 | 18% |
| shift11 | H7|S0 | 60 | 34 | 29 | 36.4 | 42.9 | 2 / 14 / 4 | -733 / -696 / -1282 | 13% |
| shift11 | H7|S3 | 15 | 11 | 10 | 52.7 | 1.6 | 239 / 243 / 418 | -360 / -355 / -629 | 20% |
| shift11 | K7|S0 | 60 | 15 | 22 | 8.7 | 48.4 | -3005 / -2927 / -5259 | -2202 / -2097 / -3854 | 3% |
| shift11 | K7|S1 | 60 | 28 | 24 | 18.7 | 40.4 | -209 / -144 / -366 | 522 / 629 / 914 | 8% |
| shift11 | K7|S3 | 60 | 22 | 27 | 40.2 | 61.4 | 361 / 382 / 632 | 519 / 546 / 909 | 6% |
| shift11 | K7|S4 | 60 | 26 | 14 | 61.7 | 33.2 | 1176 / 1241 / 2059 | -1266 / -1182 / -2216 | 8% |
| shift11 | M7|S1 | 60 | 25 | 23 | 17.1 | 31.1 | -385 / -298 / -673 | 233 / 286 / 408 | 11% |
| shift11 | M7|S3 | 60 | 23 | 24 | 19.8 | 20.5 | -282 / -279 / -494 | -106 / -87 / -186 | 16% |
| shift11 | O7|S3 | 60 | 19 | 5 | -9.1 | 20.2 | -671 / -664 / -1173 | -315 / -310 / -552 | 0% |
| shift11 | P7|S0 | 60 | 24 | 32 | 4.2 | 25.1 | -4821 / -4542 / -8436 | -8481 / -8116 / -14841 | 10% |
| shift11 | P7|S1 | 60 | 30 | 32 | 41.9 | 40.8 | -957 / -868 / -1675 | -1477 / -1243 / -2585 | 10% |
| shift11 | P7|S3 | 60 | 33 | 28 | 31.5 | 52.0 | 938 / 958 / 1641 | -46 / 132 / -81 | 15% |
| shift11 | U7|S0 | 60 | 26 | 35 | 26.5 | 10.2 | 197 / 225 / 346 | -1098 / -1060 / -1921 | 6% |
| shift11 | U7|S1 | 60 | 37 | 28 | 43.7 | 12.3 | -154 / -135 / -270 | 90 / 150 / 158 | 16% |
| shift23 | A7|S0 | 60 | 26 | 42 | 24.6 | 7.8 | -254 / -251 / -445 | -7 / -3 / -12 | 15% |
| shift23 | H7|S0 | 60 | 27 | 27 | 39.3 | 44.1 | -203 / -179 / -355 | -995 / -927 / -1742 | 10% |
| shift23 | H7|S3 | 60 | 41 | 38 | 50.4 | 12.9 | 76 / 81 / 133 | -221 / -216 / -387 | 15% |
| shift23 | K7|S0 | 60 | 32 | 33 | 21.2 | 26.5 | -734 / -717 / -1285 | -1355 / -1311 / -2371 | 16% |
| shift23 | K7|S1 | 60 | 27 | 33 | 5.5 | 8.1 | -110 / -62 / -193 | 218 / 224 / 381 | 5% |
| shift23 | K7|S3 | 60 | 28 | 23 | 62.5 | 64.6 | 659 / 686 / 1154 | 634 / 674 / 1110 | 3% |
| shift23 | K7|S4 | 60 | 40 | 18 | 76.4 | 31.8 | 1788 / 1860 / 3129 | -1255 / -1185 / -2195 | 13% |
| shift23 | M7|S1 | 60 | 35 | 28 | 29.6 | 25.0 | -81 / -53 / -141 | 281 / 298 / 491 | 16% |
| shift23 | M7|S3 | 60 | 41 | 33 | 36.4 | 44.8 | -255 / -233 / -446 | -114 / -82 / -200 | 30% |
| shift23 | O7|S3 | 60 | 20 | 16 | -11.2 | 14.8 | -455 / -452 / -796 | -220 / -216 / -385 | 5% |
| shift23 | P7|S0 | 60 | 34 | 34 | -15.7 | 2.1 | -1878 / -1758 / -3286 | -4651 / -4431 / -8140 | 21% |
| shift23 | P7|S1 | 60 | 26 | 44 | 31.3 | 43.7 | -1059 / -947 / -1853 | -186 / -162 / -325 | 15% |
| shift23 | P7|S3 | 60 | 31 | 33 | 56.6 | 67.1 | 1600 / 1721 / 2801 | 471 / 576 / 824 | 16% |
| shift23 | U7|S0 | 60 | 33 | 27 | 45.1 | 15.1 | 509 / 552 / 891 | -1588 / -1545 / -2779 | 11% |
| shift23 | U7|S1 | 60 | 32 | 36 | 21.1 | 8.7 | -168 / -136 / -293 | 367 / 377 / 643 | 21% |
| shift37 | A7|S0 | 60 | 31 | 34 | 31.2 | 14.8 | -356 / -350 / -623 | -332 / -289 / -581 | 20% |
| shift37 | H7|S0 | 60 | 27 | 24 | 32.2 | 38.4 | -204 / -166 / -357 | -929 / -873 / -1626 | 11% |
| shift37 | H7|S3 | 60 | 31 | 25 | 30.6 | 1.2 | 20 / 25 / 35 | -404 / -400 / -706 | 16% |
| shift37 | K7|S0 | 60 | 36 | 30 | 34.3 | 15.0 | -776 / -734 / -1357 | -771 / -714 / -1350 | 20% |
| shift37 | K7|S1 | 60 | 39 | 35 | 34.4 | 33.0 | 151 / 179 / 264 | 643 / 671 / 1125 | 30% |
| shift37 | K7|S3 | 60 | 31 | 40 | 56.9 | 63.3 | 676 / 697 / 1184 | 701 / 724 / 1226 | 26% |
| shift37 | K7|S4 | 60 | 27 | 34 | 60.9 | 37.7 | 1401 / 1470 / 2451 | -657 / -594 / -1150 | 23% |
| shift37 | M7|S1 | 60 | 29 | 11 | 40.2 | 29.8 | -351 / -308 / -614 | -189 / -112 / -332 | 8% |
| shift37 | M7|S3 | 60 | 24 | 23 | 41.0 | 33.7 | -444 / -425 / -777 | -124 / -113 / -217 | 13% |
| shift37 | O7|S3 | 60 | 37 | 28 | 17.1 | 24.5 | -402 / -399 / -704 | -162 / -158 / -283 | 18% |
| shift37 | P7|S0 | 60 | 29 | 29 | 14.5 | 29.6 | -5065 / -4705 / -8864 | -12977 / -12434 / -22710 | 6% |
| shift37 | P7|S1 | 60 | 38 | 26 | 33.1 | 19.2 | -123 / -35 / -216 | -1550 / -1370 / -2712 | 15% |
| shift37 | P7|S3 | 60 | 29 | 24 | 62.9 | 64.8 | 1521 / 1667 / 2661 | -20 / 123 / -36 | 8% |
| shift37 | U7|S0 | 60 | 33 | 22 | 38.0 | 2.6 | 496 / 507 / 869 | -1827 / -1774 / -3196 | 8% |
| shift37 | U7|S1 | 60 | 29 | 42 | 9.8 | 6.7 | -161 / -117 / -281 | 630 / 642 / 1102 | 21% |
| nonsense | A7|S0 | 60 | 0 | 60 | 31.2 | 14.0 | -572 / -557 / -1002 | -269 / -245 / -470 | 0% |
| nonsense | H7|S0 | 60 | 0 | 60 | -69.1 | 55.2 | -2099 / -2074 / -3673 | -220 / -183 / -384 | 0% |
| nonsense | K7|S0 | 60 | 0 | 60 | -7.1 | 59.9 | -3139 / -3079 / -5494 | -1461 / -1373 / -2557 | 0% |
| nonsense | K7|S1 | 60 | 60 | 60 | 38.1 | 63.1 | 603 / 658 / 1055 | 2683 / 2753 / 4694 | 100% |
| nonsense | K7|S3 | 60 | 60 | 60 | 37.3 | 71.4 | 579 / 602 / 1014 | 1373 / 1396 / 2402 | 0% |
| nonsense | K7|S4 | 60 | 60 | 60 | 57.9 | 71.1 | 1512 / 1549 / 2645 | 556 / 605 / 973 | 100% |
| nonsense | M7|S1 | 60 | 0 | 0 | 40.6 | 46.1 | -716 / -664 / -1253 | 162 / 236 / 283 | 0% |
| nonsense | M7|S3 | 60 | 0 | 0 | 33.1 | 4.0 | -342 / -324 / -599 | -686 / -663 / -1201 | 0% |
| nonsense | O7|S3 | 60 | 60 | 60 | 34.0 | 7.5 | -445 / -439 / -779 | -155 / -150 / -271 | 0% |
| nonsense | P7|S0 | 60 | 0 | 0 | -33.0 | -29.2 | -5359 / -5164 / -9378 | -11992 / -11701 / -20986 | 0% |
| nonsense | P7|S1 | 60 | 0 | 0 | -27.9 | 3.9 | -3238 / -3145 / -5666 | -1843 / -1715 / -3225 | 0% |
| nonsense | U7|S1 | 60 | 60 | 0 | 3.9 | -40.0 | -177 / -146 / -310 | -781 / -739 / -1366 | 0% |
"sign kept" = the rule raises mean R (remaining trades minus all trades) in that untouched window. Shifted-label and nonsense rows are the selection null for this table: compare each cell with its real row.

## WAIT variants re-scored honestly (every _d5/_d30/_d60/_d120 and tapelegs _L5 column; 7 of 7 book files landed)
WAIT-THEN-ENTER (WTE): entry at signal+delay at the price then, same native stop/target distances from the new entry; trades closed inside the wait are excluded; approximation: the 1-s path ends at the original exit, so unresolved new brackets are marked at that exit (share in the table). EARLY-EXIT (EE): entered at signal, rule acts at +delay, value = mark at +delay minus hold-to-raw-outcome (only the remaining path counts).
| kind | delay s | window | real columns scored | real beyond-bar % | shifted-label beyond-bar % | nonsense bar beyond % (by construction ~1) | unresolved WTE share |
|--|--|--|--|--|--|--|--|
| EARLY-EXIT | 5 | ALL43 | 394 | 1.62 | 1.54 | 1 |  |
| EARLY-EXIT | 5 | HOLD | 394 | 1.11 | 1.56 | 1 |  |
| EARLY-EXIT | 5 | L6M | 394 | 0.88 | 1.51 | 1 |  |
| EARLY-EXIT | 30 | ALL43 | 283 | 1.22 | 1.74 | 1 |  |
| EARLY-EXIT | 30 | HOLD | 283 | 1.36 | 1.73 | 1 |  |
| EARLY-EXIT | 30 | L6M | 283 | 0.94 | 1.25 | 1 |  |
| EARLY-EXIT | 60 | ALL43 | 282 | 1.15 | 1.47 | 1 |  |
| EARLY-EXIT | 60 | HOLD | 282 | 1.42 | 1.60 | 1 |  |
| EARLY-EXIT | 60 | L6M | 282 | 0.88 | 1.40 | 1 |  |
| EARLY-EXIT | 120 | ALL43 | 282 | 1.12 | 1.53 | 1 |  |
| EARLY-EXIT | 120 | HOLD | 282 | 1.03 | 1.23 | 1 |  |
| EARLY-EXIT | 120 | L6M | 282 | 1.50 | 1.44 | 1 |  |
| WAIT-THEN-ENTER | 5 | ALL43 | 394 | 1.54 | 1.50 | 1 | 0.66 |
| WAIT-THEN-ENTER | 5 | HOLD | 394 | 1.20 | 1.54 | 1 | 0.66 |
| WAIT-THEN-ENTER | 5 | L6M | 394 | 0.96 | 1.54 | 1 | 0.66 |
| WAIT-THEN-ENTER | 30 | ALL43 | 283 | 1.11 | 1.73 | 1 | 0.61 |
| WAIT-THEN-ENTER | 30 | HOLD | 283 | 1.62 | 1.72 | 1 | 0.61 |
| WAIT-THEN-ENTER | 30 | L6M | 283 | 1.22 | 1.23 | 1 | 0.61 |
| WAIT-THEN-ENTER | 60 | ALL43 | 282 | 1.17 | 1.53 | 1 | 0.60 |
| WAIT-THEN-ENTER | 60 | HOLD | 282 | 1.57 | 1.79 | 1 | 0.60 |
| WAIT-THEN-ENTER | 60 | L6M | 282 | 1.27 | 1.62 | 1 | 0.60 |
| WAIT-THEN-ENTER | 120 | ALL43 | 282 | 1.17 | 1.53 | 1 | 0.60 |
| WAIT-THEN-ENTER | 120 | HOLD | 282 | 1.14 | 1.28 | 1 | 0.60 |
| WAIT-THEN-ENTER | 120 | L6M | 282 | 1.50 | 1.47 | 1 | 0.60 |

Strongest wait columns after the honest re-score (ALL43, cell, kind; compare the pre-fix look-ahead zw 6-8): 
| kind | delay | book|cell | column | zw | lift (R) |
|--|--|--|--|--|--|
| EE | 5 | U7|S0 | fl214_d5 | -5.4 | -0.114 |
| WTE | 5 | U7|S0 | fl214_d5 | 5.1 | 0.108 |
| WTE | 120 | U7|S1 | fl248_d120 | 4.9 | 0.204 |
| EE | 30 | P7|S0 | fl268_d30 | 4.6 | 0.205 |
| WTE | 30 | P7|S0 | fl268_d30 | -4.5 | -0.206 |
| EE | 120 | U7|S1 | fl248_d120 | -4.5 | -0.215 |
| EE | 5 | P7|S3 | fl117_d5 | 4.2 | 0.186 |
| WTE | 5 | P7|S3 | fl117_d5 | -4.2 | -0.173 |
| EE | 120 | P7|S1 | fl135_d120 | -4.1 | -0.148 |
| EE | 120 | P7|S3 | fl231_d120 | 4.1 | 0.143 |
| EE | 30 | K7|S3 | fl020_d30 | -4.1 | -0.239 |
| WTE | 30 | U7|S1 | fl027_d30 | 4.1 | 0.091 |
| EE | 5 | U7|S0 | fl136_d5 | -4.1 | -0.182 |
| EE | 5 | U7|S1 | fl073_d5 | 4.1 | 0.154 |
| EE | 120 | O7|S3 | fl043_d120 | 4.1 | -0.052 |

## FAMILY-RESTRICTED WALK-FORWARD (JOB 1) - AT-ENTRY CLEAN (name-clean columns; family 9 audited causal) - families 9, 10, 7 separately, choose on 2023-04..2025-10 only, freeze, HOLD + L6M untouched
Procedure: per family, per book x session cell (book|S<k>, book|ALL): top 5 columns by |zw| among columns sign-stable across years inside the selection window (>=20 yes and >=20 no trades), direction = sign of the selection lift; rules = each column as SKIP and as HALF-SIZE of the unfavourable state, and an equal-weight FAMILY SCORE (sum of +1 favourable / -1 unfavourable / 0 unknown over the chosen columns; acts when score < 0). Controls: (a) the identical procedure with outcomes shifted 11/23/37 trades inside the selection window, rule evaluated on TRUE outcomes; (b) 200 persistent random skips / half-sizes of the same share (5-min bucket per book and side) = percentile columns. Ulcer = RMS daily drawdown of the cell P&L (positive change = lower ulcer). Dollar columns: engine $/wk at base lots ($1.18 RT), $4.84 RT repriced and x1.75 live lots. Path arithmetic on the raw cell (no re-entry, no freed-book effect). FIRST PASS.

### Family 9 trade context (rebuilt causal)
Feed: D7 own trade log (closed trades of the same book; NOTE: the raw-chassis history is the book alone, live D7 history is the stacked book, so live values differ and the rule must be re-derived on live-stack history). D7 live today: YES, computable today from D7 own trade log. Block-shift permutation test on the UNTOUCHED year (2025-11..2026-10, R/MFE_R/MAE_R, 15 book x session cells, 31 columns): real stable count 58 vs null mean 17.4, 95th pct 28, p = 0.0010 (1,000 draws).

Summary over all frozen rules (untouched windows). "sign kept" = share of rules whose flagged trades have LOWER mean R than the unflagged ones in that window (the direction chosen in the selection period holds); real vs the shifted-label procedure:
| source | rule | mode | window | rules | sign kept % | median lift R (unflagged minus flagged) | median ulcer change % | median mean $/wk eng / $4.84 / x1.75 | share with pct>=.75 on ulcer or mean vs 200 random |
|--|--|--|--|--|--|--|--|--|--|
| real | col | half | HOLD | 94 | 56 | 0.030 | 17.1 | -50 / -41 / -88 | 46% |
| real | col | half | L6M | 94 | 37 | -0.028 | 15.3 | -199 / -196 / -348 | 31% |
| shift | col | half | HOLD | 258 | 46 | -0.012 | 18.4 | -151 / -141 / -265 | 34% |
| shift | col | half | L6M | 257 | 51 | 0.007 | 18.0 | -161 / -127 / -282 | 36% |
| real | col | skip | HOLD | 94 | 56 | 0.030 | 20.0 | -100 / -83 / -175 | 45% |
| real | col | skip | L6M | 94 | 37 | -0.028 | 17.8 | -397 / -391 / -696 | 27% |
| shift | col | skip | HOLD | 258 | 46 | -0.012 | 22.3 | -303 / -283 / -530 | 35% |
| shift | col | skip | L6M | 257 | 51 | 0.007 | 25.6 | -322 / -254 / -564 | 37% |
| real | score | half | HOLD | 20 | 70 | 0.061 | 21.7 | 50 / 71 / 88 | 55% |
| real | score | half | L6M | 20 | 35 | -0.024 | 17.3 | -133 / -104 / -232 | 25% |
| shift | score | half | HOLD | 55 | 49 | -0.006 | 16.6 | -165 / -163 / -289 | 29% |
| shift | score | half | L6M | 54 | 54 | 0.011 | 14.0 | -214 / -191 / -374 | 30% |
| real | score | skip | HOLD | 20 | 70 | 0.061 | 28.4 | 100 / 142 / 176 | 60% |
| real | score | skip | L6M | 20 | 35 | -0.024 | 20.9 | -265 / -208 / -464 | 25% |
| shift | score | skip | HOLD | 55 | 49 | -0.006 | 23.3 | -331 / -326 / -579 | 38% |
| shift | score | skip | L6M | 54 | 54 | 0.011 | 17.6 | -428 / -381 / -748 | 30% |

Family-score SKIP rule per cell (real selection), calibrated tier from DS3_PASS_RULE.md (WF-CONFIRMED/WF-LEAD/WF-FAIL; HOLD and L6M untouched, GAP/PRE/XP inside the selection period):
| cell | tier | chosen columns | HOLD ulcer raw -> rule | L6M ulcer raw -> rule | HOLD mean $/wk raw -> rule | L6M mean $/wk raw -> rule | pct ulcer/mean HOLD | pct ulcer/mean L6M | P(ulcer lower) L6M | L6M $/wk $4.84 / x1.75 |
|--|--|--|--|--|--|--|--|--|--|--|
| A7|S0 | WF-FAIL | c_F9_day_net_ge0+c_F9_sess_net_ge0+c_F9_prev2_loss+c_F9_gap_le300+c_F9_gap_gt4h | -6016 -> -741 | -4779 -> -3130 | 832 -> 324 | 587 -> -21 | 0.99 / 0.78 | 0.55 / 0.33 | 0.57 | -574 / -1065 |
| H7|ALL | WF-FAIL | c_F9_opp_loser_prev+c_F9_day_net_le_m1+c_F9_sess_net_ge0+c_F9_same_side_prev+c_F9_fresh15 | -17428 -> -11214 | -23157 -> -20610 | 136 -> 985 | 1775 -> 2145 | 0.99 / 0.96 | 0.65 / 0.82 | 0.65 | 377 / 648 |
| H7|S0 | WF-FAIL | c_F9_ss_loser_prev+c_F9_first_sess+c_F9_rechase20+c_F9_gap_gt4h+c_F9_fresh5 | -17090 -> -17337 | -25780 -> -14291 | 147 -> -445 | 1221 -> 201 | 0.12 / 0.28 | 0.24 / 0.47 | 0.70 | -966 / -1785 |
| H7|S3 | WF-FAIL | c_F9_same_side_prev | -4043 -> -1607 | -1725 -> -1875 | -12 -> 325 | 623 -> 318 | 0.86 / 0.94 | 0.43 / 0.51 | 0.61 | -301 / -534 |
| K7|ALL | WF-FAIL | c_F9_same_side_prev+c_F9_opp_loser_prev+c_F9_ge3_sess+c_F9_day_net_le_m1+c_F9_prev_target | -58709 -> -32502 | -39645 -> -51068 | 1115 -> 2724 | 2602 -> -2071 | 0.81 / 0.94 | 0.09 / 0.01 | 0.06 | -4487 / -8178 |
| K7|S0 | WF-FAIL | c_F9_fresh15+c_F9_day_net_le_m1+c_F9_sess_net_le_m1+c_F9_rechase20+c_F9_day_ge3 | -16192 -> -10712 | -28120 -> -15438 | 3770 -> 587 | 3429 -> 1853 | 0.28 / 0.39 | 0.29 / 0.88 | 0.75 | -1453 / -2758 |
| K7|S1 | WF-FAIL | c_F9_prev3_loss+c_F9_gap_le60+c_F9_rechase10+c_F9_sess_net_le_m1+c_F9_gap_le900 | -20433 -> -9495 | -40458 -> -23514 | 323 -> 505 | -1103 -> -426 | 0.69 / 0.73 | 0.30 / 0.47 | 0.71 | 776 / 1184 |
| K7|S3 | WF-FAIL | c_F9_opp_loser_prev+c_F9_fresh15+c_F9_sess_net_ge0+c_F9_day_ge5+c_F9_same_side_prev | -24362 -> -24537 | -24248 -> -18861 | -1088 -> -1181 | -995 -> -855 | 0.12 / 0.13 | 0.39 / 0.33 | 0.67 | 149 / 244 |
| K7|S4 | WF-FAIL | c_F9_prev3_loss+c_F9_rechase20+c_F9_gap_le3600+c_F9_ge3_sess+c_F9_gap_le60 | -44579 -> -27648 | -13606 -> -12916 | -1890 -> -1058 | 1320 -> -74 | 0.33 / 0.33 | 0.32 / 0.21 | 0.34 | -1329 / -2438 |
| M7|ALL | WF-FAIL | c_F9_ss_loser_prev+c_F9_day_ge5+c_F9_second_sess+c_F9_first_sess+c_F9_fresh15 | -13398 -> -27493 | -40445 -> -29395 | 1147 -> -1918 | -424 -> -650 | 0.10 / 0.01 | 0.34 / 0.36 | 0.78 | -116 / -394 |
| M7|S1 | WF-FAIL | c_F9_prev2_loss+c_F9_gap_le60+c_F9_gap_le300+c_F9_gap_le900+c_F9_fresh5 | -19414 -> -1781 | -32674 -> -17477 | 485 -> 1886 | -623 -> 6 | 0.98 / 1.00 | 0.12 / 0.57 | 0.97 | 753 / 1100 |
| M7|S3 | WF-FAIL | c_F9_gap_le300+c_F9_ss_loser_30m+c_F9_fresh15+c_F9_first_sess+c_F9_sess_net_le_m1 | -8076 -> -6094 | -8747 -> -5108 | 662 -> 660 | 199 -> 157 | 0.90 / 0.56 | 1.00 / 0.51 | 0.72 | -36 / -73 |
| O7|S3 | WF-FAIL | c_F9_opp_loser_prev+c_F9_prev_stop+c_F9_prev_target+c_F9_rechase10+c_F9_same_side_prev | -1547 -> -1535 | -3756 -> -2763 | 1023 -> 709 | 311 -> 191 | 0.32 / 0.88 | 0.36 / 0.55 | 0.55 | -116 / -210 |
| P7|ALL | WF-FAIL | c_F9_ss_loser_30m+c_F9_rechase20+c_F9_gap_le60+c_F9_ss_loser_60m | -45045 -> -39084 | -40900 -> -32802 | 6421 -> 8043 | 19336 -> 18987 | 0.90 / 0.94 | 0.91 / 0.52 | 0.52 | -318 / -610 |
| P7|S0 | WF-FAIL | c_F9_gap_le900+c_F9_day_net_ge0+c_F9_sess_net_ge0+c_F9_gap_gt4h+c_F9_same_side_prev | -28855 -> -23902 | -36590 -> -38151 | 7077 -> 5424 | 16772 -> 6301 | 0.79 / 0.59 | 0.29 / 0.10 | 0.45 | -10170 / -18323 |
| P7|S1 | WF-FAIL | c_F9_fresh5+c_F9_first_sess+c_F9_second_sess+c_F9_ss_loser_60m+c_F9_rechase0 | -33536 -> -23661 | -32871 -> -46665 | 1443 -> 704 | 2733 -> -335 | 0.62 / 0.47 | 0.07 / 0.14 | 0.34 | -2938 / -5370 |
| P7|S3 | WF-FAIL | c_F9_fresh5+c_F9_ss_loser_30m+c_F9_ss_loser_60m+c_F9_ge3_sess+c_F9_sess_net_le_m1 | -37450 -> -32194 | -52822 -> -41196 | -2099 -> -1206 | -169 -> 543 | 0.71 / 0.79 | 0.67 / 0.69 | 0.88 | 749 / 1245 |
| U7|ALL | WF-FAIL | c_F9_prev2_loss+c_F9_gap_le900+c_F9_sess_net_ge0+c_F9_gap_le3600+c_F9_rechase20 | -29102 -> -21125 | -12603 -> -18174 | -176 -> 1780 | 2471 -> 378 | 0.64 / 0.92 | 0.27 / 0.29 | 0.24 | -2030 / -3662 |
| U7|S0 | WF-LEAD | c_F9_rechase0+c_F9_fresh5+c_F9_prev2_loss+c_F9_rechase10 | -26093 -> -11715 | -10662 -> -9742 | -705 -> -6 | 2753 -> 2691 | 0.78 / 0.62 | 0.64 / 0.95 | 0.59 | -25 / -109 |
| U7|S1 | WF-FAIL | c_F9_prev2_loss+c_F9_gap_le3600+c_F9_same_side_prev+c_F9_gap_le900+c_F9_opp_loser_prev | -18394 -> -18013 | -13693 -> -19495 | 529 -> 548 | -180 -> -75 | 0.46 / 0.60 | 0.20 / 0.55 | 0.54 | 130 / 184 |

Most-chosen columns in plain words (count of cells choosing it; feed: D7 own trade log; live today: YES, computable today from D7 own trade log):
- c_F9_same_side_prev (7 cells): same side as the last closed trade
- c_F9_sess_net_ge0 (5 cells): book net R this session so far >= 0
- c_F9_prev2_loss (5 cells): last two closed trades were both losers
- c_F9_rechase20 (5 cells): entry is 20+ pts beyond the last exit price (re-chase)
- c_F9_fresh5 (5 cells): entry is 5+ pts better than the last exit price (fresh)
- c_F9_opp_loser_prev (5 cells): last closed trade was an opposite-side loser
- c_F9_fresh15 (5 cells): entry is 15+ pts better than the last exit price (fresh)
- c_F9_gap_le900 (5 cells): gap since the last close <= 900 s

### Family 10 TICK internals
Feed: NYSE TICK index feed (delayed ok). D7 live today: NO: D7 does not have the TICK feed today. Block-shift permutation test on the UNTOUCHED year (2025-11..2026-10, R/MFE_R/MAE_R, 15 book x session cells, 80 columns): real stable count 14 vs null mean 8.1, 95th pct 16, p = 0.1019 (1,000 draws).

Summary over all frozen rules (untouched windows). "sign kept" = share of rules whose flagged trades have LOWER mean R than the unflagged ones in that window (the direction chosen in the selection period holds); real vs the shifted-label procedure:
| source | rule | mode | window | rules | sign kept % | median lift R (unflagged minus flagged) | median ulcer change % | median mean $/wk eng / $4.84 / x1.75 | share with pct>=.75 on ulcer or mean vs 200 random |
|--|--|--|--|--|--|--|--|--|--|
| real | col | half | HOLD | 40 | 72 | 0.109 | 24.3 | 258 / 274 / 451 | 55% |
| real | col | half | L6M | 36 | 36 | -0.023 | 12.1 | -87 / -83 / -153 | 25% |
| shift | col | half | HOLD | 125 | 69 | 0.067 | 15.1 | 75 / 77 / 132 | 46% |
| shift | col | half | L6M | 109 | 50 | -0.004 | 10.5 | -22 / 5 / -39 | 32% |
| real | col | skip | HOLD | 40 | 72 | 0.109 | 27.7 | 515 / 548 / 902 | 60% |
| real | col | skip | L6M | 36 | 36 | -0.023 | 19.6 | -174 / -166 / -305 | 31% |
| shift | col | skip | HOLD | 125 | 69 | 0.067 | 15.3 | 150 / 154 / 263 | 46% |
| shift | col | skip | L6M | 109 | 50 | -0.004 | 8.0 | -44 / 11 / -77 | 35% |
| real | score | half | HOLD | 8 | 75 | 0.093 | 24.6 | 462 / 490 / 809 | 50% |
| real | score | half | L6M | 8 | 12 | -0.078 | 7.5 | -268 / -236 / -468 | 25% |
| shift | score | half | HOLD | 27 | 67 | 0.068 | 11.3 | 47 / 48 / 82 | 37% |
| shift | score | half | L6M | 22 | 50 | -0.011 | 6.1 | -51 / -50 / -90 | 32% |
| real | score | skip | HOLD | 8 | 75 | 0.093 | 33.5 | 924 / 980 / 1618 | 62% |
| real | score | skip | L6M | 8 | 12 | -0.078 | 5.3 | -535 / -472 / -937 | 25% |
| shift | score | skip | HOLD | 27 | 67 | 0.068 | 11.3 | 94 / 97 / 164 | 37% |
| shift | score | skip | L6M | 22 | 50 | -0.011 | 6.6 | -103 / -100 / -180 | 36% |

Family-score SKIP rule per cell (real selection), calibrated tier from DS3_PASS_RULE.md (WF-CONFIRMED/WF-LEAD/WF-FAIL; HOLD and L6M untouched, GAP/PRE/XP inside the selection period):
| cell | tier | chosen columns | HOLD ulcer raw -> rule | L6M ulcer raw -> rule | HOLD mean $/wk raw -> rule | L6M mean $/wk raw -> rule | pct ulcer/mean HOLD | pct ulcer/mean L6M | P(ulcer lower) L6M | L6M $/wk $4.84 / x1.75 |
|--|--|--|--|--|--|--|--|--|--|--|
| K7|ALL | WF-FAIL | c_T_tick_no_ext_against_600+c_T_tick_ma5_side+c_T10_tk_now_with+c_T10_mean5_with200+c_T10_pos15_against60 | -58709 -> -31453 | -39645 -> -37566 | 1115 -> 2641 | 2602 -> 1589 | 0.84 / 0.93 | 0.38 / 0.46 | 0.33 | -915 / -1774 |
| K7|S3 | WF-FAIL | c_T10_ext600_30_against+c_T10_lastext800_against+c_T10_ext600_5_with+c_T10_tk_now_with500+c_T10_mean5_with200 | -24362 -> -23362 | -24248 -> -26358 | -1088 -> -766 | -995 -> -1081 | 0.30 / 0.69 | 0.04 / 0.18 | 0.51 | -83 / -151 |
| K7|S4 | WF-FAIL | c_T_tick_no_ext_against_600+c_T10_pos15_with60+c_T10_tk_now_with+c_T10_mean60_with+c_T10_cumslope15_with | -44579 -> -11469 | -13606 -> -14222 | -1890 -> 274 | 1320 -> -509 | 0.67 / 0.90 | 0.11 / 0.10 | 0.37 | -1760 / -3199 |
| M7|ALL | WF-FAIL | c_T10_ext600_15_with+c_T10_pos30_with60+c_T10_lastext800_against+c_T10_mean60_with200+c_T_tick_no_ext_against_600 | -13398 -> -19776 | -40445 -> -35012 | 1147 -> 491 | -424 -> -784 | 0.32 / 0.49 | 0.35 / 0.32 | 0.57 | -317 / -629 |
| M7|S3 | WF-FAIL | c_T10_ext600_15_with+c_T10_pos30_with60+c_T10_lastext800_against+c_T10_mean60_with200+c_T_tick_no_ext_against_600 | -8076 -> -1718 | -8747 -> -2634 | 662 -> 7 | 199 -> -161 | 0.76 / 0.41 | 0.59 / 0.28 | 0.98 | -317 / -629 |
| O7|S3 | WF-FAIL | c_T_tick_cum_slope+c_T10_pos15_against60+c_T10_pos60_against60+c_T10_pos30_against60+c_T_tick_ma15_strong | -1547 -> -1246 | -3756 -> -1862 | 1023 -> 545 | 311 -> 300 | 0.61 / 0.56 | 0.81 / 0.72 | 0.73 | -7 / -20 |
| P7|ALL | WF-FAIL | c_T10_cumslope15_with+c_T10_mean60_with200+c_T_tick_ext_with_600+c_T10_cumslope30_with+c_T10_f15_pos_with60 | -45045 -> -34466 | -40900 -> -44413 | 6421 -> 8531 | 19336 -> 18625 | 0.90 / 0.90 | 0.38 / 0.76 | 0.65 | -628 / -1244 |
| P7|S3 | WF-FAIL | c_T10_cumslope15_with+c_T10_mean60_with200+c_T_tick_ext_with_600+c_T10_cumslope30_with+c_T10_f15_pos_with60 | -37450 -> -21161 | -52822 -> -50007 | -2099 -> 10 | -169 -> -880 | 0.76 / 0.79 | 0.20 / 0.27 | 0.71 | -628 / -1244 |

Most-chosen columns in plain words (count of cells choosing it; feed: NYSE TICK index feed; live today: NO: D7 does not have the TICK feed today):
- c_T_tick_no_ext_against_600 (4 cells): - c_T_tick_no_ext_against_600 : NO TICK extreme beyond 600 against the trade within the last 15 min
- c_T10_mean60_with200 (4 cells): name only: c_T10_mean60_with200
- c_T10_lastext800_against (3 cells): name only: c_T10_lastext800_against
- c_T10_cumslope15_with (3 cells): name only: c_T10_cumslope15_with
- c_T10_mean5_with200 (2 cells): name only: c_T10_mean5_with200
- c_T10_tk_now_with (2 cells): name only: c_T10_tk_now_with
- c_T10_pos15_against60 (2 cells): name only: c_T10_pos15_against60
- c_T10_ext600_15_with (2 cells): name only: c_T10_ext600_15_with

### Family 7 UW options positioning
Feed: Unusual Whales options / gamma exposure subscription. D7 live today: NO: needs the UW subscription. Block-shift permutation test on the UNTOUCHED year (2025-11..2026-10, R/MFE_R/MAE_R, 15 book x session cells, 108 columns): real stable count 60 vs null mean 48.5, 95th pct 66, p = 0.1339 (1,000 draws).

Summary over all frozen rules (untouched windows). "sign kept" = share of rules whose flagged trades have LOWER mean R than the unflagged ones in that window (the direction chosen in the selection period holds); real vs the shifted-label procedure:
| source | rule | mode | window | rules | sign kept % | median lift R (unflagged minus flagged) | median ulcer change % | median mean $/wk eng / $4.84 / x1.75 | share with pct>=.75 on ulcer or mean vs 200 random |
|--|--|--|--|--|--|--|--|--|--|
| real | col | half | HOLD | 92 | 61 | 0.038 | 13.2 | 36 / 53 / 63 | 45% |
| real | col | half | L6M | 92 | 67 | 0.050 | 14.2 | 50 / 58 / 87 | 57% |
| shift | col | half | HOLD | 276 | 63 | 0.043 | 19.0 | 25 / 44 / 44 | 59% |
| shift | col | half | L6M | 276 | 54 | 0.018 | 16.6 | -69 / -54 / -120 | 52% |
| real | col | skip | HOLD | 92 | 61 | 0.038 | 15.9 | 72 / 105 / 126 | 47% |
| real | col | skip | L6M | 92 | 67 | 0.050 | 20.2 | 100 / 116 / 175 | 58% |
| shift | col | skip | HOLD | 276 | 63 | 0.043 | 24.4 | 50 / 87 / 87 | 58% |
| shift | col | skip | L6M | 276 | 54 | 0.018 | 21.5 | -137 / -108 / -240 | 47% |
| real | score | half | HOLD | 19 | 58 | 0.020 | 12.6 | -7 / 2 / -13 | 58% |
| real | score | half | L6M | 19 | 68 | 0.066 | 13.9 | 58 / 66 / 101 | 63% |
| shift | score | half | HOLD | 57 | 47 | -0.006 | 17.3 | -17 / -1 / -29 | 54% |
| shift | score | half | L6M | 57 | 54 | 0.026 | 15.3 | -9 / -6 / -15 | 58% |
| real | score | skip | HOLD | 19 | 58 | 0.020 | 15.2 | -15 / 4 / -26 | 42% |
| real | score | skip | L6M | 19 | 68 | 0.066 | 23.8 | 116 / 132 / 202 | 63% |
| shift | score | skip | HOLD | 57 | 47 | -0.006 | 22.1 | -33 / -3 / -58 | 53% |
| shift | score | skip | L6M | 57 | 54 | 0.026 | 18.0 | -18 / -11 / -31 | 53% |

Family-score SKIP rule per cell (real selection), calibrated tier from DS3_PASS_RULE.md (WF-CONFIRMED/WF-LEAD/WF-FAIL; HOLD and L6M untouched, GAP/PRE/XP inside the selection period):
| cell | tier | chosen columns | HOLD ulcer raw -> rule | L6M ulcer raw -> rule | HOLD mean $/wk raw -> rule | L6M mean $/wk raw -> rule | pct ulcer/mean HOLD | pct ulcer/mean L6M | P(ulcer lower) L6M | L6M $/wk $4.84 / x1.75 |
|--|--|--|--|--|--|--|--|--|--|--|
| A7|S0 | WF-CONFIRMED | c_J_em_room_ge150_Nh+c_J_beyond_flip_Nd_vol+c_J_em_used_lt0.5_Nh+c_J_em_frac_pos_Nd+c_J_em_room_ge100_Nh | -6016 -> -1404 | -4779 -> -2613 | 832 -> 760 | 587 -> 883 | 0.99 / 0.89 | 0.93 / 0.93 | 0.91 | 327 / 518 |
| H7|ALL | WF-FAIL | c_J_flip_far25_NDX_vol+c_J_flip_far50_NDX_vol+c_J_flip_far100_NDX_vol+c_J_wall_behind50_Nh_oi+c_J_netgamma_pos_Nh_vol | -17428 -> -14831 | -23157 -> -17641 | 136 -> -175 | 1775 -> 1593 | 0.71 / 0.33 | 0.75 / 0.54 | 0.45 | -163 / -318 |
| H7|S0 | WF-CONFIRMED | c_J_flip_far25_NDX_vol+c_J_flip_far50_NDX_vol+c_J_wall_behind50_NDX_oi+c_J_flip_far100_SPX_vol+c_J_flip_far100_NDX_oi | -17090 -> -14485 | -25780 -> -11096 | 147 -> 411 | 1221 -> 2234 | 0.69 / 0.69 | 0.99 / 0.94 | 0.89 | 1036 / 1773 |
| K7|ALL | WF-FAIL | c_J_0dte_flip_far50_Nd_oi+c_J_beyond_flip_Nh_vol+c_J_wall_behind50_SPX_oi+c_J_beyond_0dte_flip_Nd_oi+c_J_0dte_flip_far25 | -58709 -> -53645 | -39645 -> -31033 | 1115 -> -323 | 2602 -> 3500 | 0.46 / 0.08 | 0.80 / 0.84 | 0.86 | 953 / 1571 |
| K7|S0 | WF-FAIL | c_J_wall_behind25_SPX_vol+c_J_wall_behind50_SPX_vol+c_J_em_used_lt0.75_Nh+c_J_flip_far50_SPX_vol+c_J_netgamma_pos_Nh_vol | -16192 -> -16407 | -28120 -> -15219 | 3770 -> 2829 | 3429 -> 3219 | 0.20 / 0.52 | 0.93 / 0.81 | 0.92 | -165 / -367 |
| K7|S1 | WF-CONFIRMED | c_J_flip_far100_SPX_oi+c_J_beyond_flip_Nd_oi+c_J_wall_behind25_SPX_vol+c_J_beyond_flip_Nh_oi+c_J_netgamma_pos_Nh_oi | -20433 -> -8399 | -40458 -> -12800 | 323 -> 238 | -1103 -> 614 | 0.87 / 0.53 | 0.88 / 0.86 | 0.91 | 1815 / 3005 |
| K7|S3 | WF-FAIL | c_J_tide_npp_s5_neg+c_J_netgamma_pos_Nd_vol+c_J_wall_behind25_SPX_oi+c_J_flip_far25_SPX_oi+c_J_tide_nv_s5_pos | -24362 -> -13922 | -24248 -> -17419 | -1088 -> -535 | -995 -> -879 | 0.78 / 0.76 | 0.52 / 0.32 | 0.61 | 132 / 202 |
| K7|S4 | WF-CONFIRMED | c_J_0dte_flip_far50_Nh_oi+c_J_wall_behind50_Nh_vol+c_J_wall_behind50_SPX_oi+c_J_tide_nv_s30_pos+c_J_beyond_0dte_flip_Nh_ | -44579 -> -45844 | -13606 -> -9971 | -1890 -> -1967 | 1320 -> 1622 | 0.28 / 0.34 | 0.95 / 0.86 | 0.89 | 306 / 530 |
| M7|ALL | WF-FAIL | c_J_flip_far100_SPX_oi+c_J_wall_behind25_Nd_oi+c_J_flip_far100_NDX_oi+c_J_tide_npp_s_neg+c_J_flip_far25_NDX_vol | -13398 -> -23630 | -40445 -> -42808 | 1147 -> -84 | -424 -> 137 | 0.07 / 0.07 | 0.23 / 0.80 | 0.86 | 594 / 982 |
| M7|S1 | WF-FAIL | c_J_wall_behind50_Nd_oi+c_J_flip_far25_NDX_vol+c_J_wall_behind25_Nd_oi+c_J_flip_far25_SPX_oi+c_J_0dte_flip_far50_Nd_oi | -19414 -> -18412 | -32674 -> -24902 | 485 -> 772 | -623 -> -252 | 0.71 / 0.87 | 0.96 / 0.81 | 0.67 | 377 / 650 |
| M7|S3 | WF-FAIL | c_J_beyond_0dte_flip_Nh_vol+c_J_tide_npp_s_neg+c_J_beyond_0dte_flip_Nd_vol+c_J_beyond_flip_Nh_oi+c_J_gex_pos_QQQ_vol | -8076 -> -6881 | -8747 -> -9816 | 662 -> 609 | 199 -> -377 | 0.41 / 0.68 | 0.27 / 0.09 | 0.43 | -558 / -1007 |
| O7|S3 | WF-FAIL | c_J_beyond_flip_SPX_vol+c_J_tide_npp_s5_neg | -1547 -> -1488 | -3756 -> -3179 | 1023 -> 710 | 311 -> 352 | 0.46 / 0.14 | 0.67 / 0.76 | 0.77 | 44 / 72 |
| P7|ALL | WF-FAIL | c_J_wall_behind25_Nh_vol+c_J_gex_pos_QQQ_vol+c_J_wall_behind50_Nh_oi+c_J_gex_pos_NDX_oi+c_J_0dte_flip_far50_Nh_oi | -45045 -> -20718 | -40900 -> -43372 | 6421 -> 7887 | 19336 -> 7977 | 0.95 / 0.91 | 0.39 / 0.33 | 0.67 | -10651 / -19878 |
| P7|S0 | WF-FAIL | c_J_flip_far25_NDX_oi+c_J_wall_behind25_SPX_oi+c_J_flip_far100_NDX_oi+c_J_wall_behind50_SPX_oi+c_J_flip_far25_SPX_oi | -28855 -> -24122 | -36590 -> -51879 | 7077 -> 9085 | 16772 -> 12348 | 0.80 / 0.91 | 0.07 / 0.49 | 0.20 | -4228 / -7742 |
| P7|S1 | WF-LEAD | c_J_wall_behind50_Nd_oi+c_J_flip_far100_SPX_oi+c_J_flip_far25_NDX_vol+c_J_netgamma_pos_Nd_vol+c_J_netgamma_pos_Nh_vol | -33536 -> -20609 | -32871 -> -19621 | 1443 -> 2522 | 2733 -> 5591 | 0.88 / 0.85 | 0.94 / 0.97 | 0.95 | 2943 / 5001 |
| P7|S3 | WF-FAIL | c_J_gex_pos_QQQ_vol+c_J_wall_behind50_Nh_vol+c_J_netgamma_pos_Nh_vol+c_J_gex_pos_NDX_oi+c_J_wall_behind50_NDX_oi | -37450 -> -30878 | -52822 -> -53671 | -2099 -> -1688 | -169 -> -1247 | 0.62 / 0.55 | 0.23 / 0.15 | 0.59 | -1024 / -1887 |
| U7|ALL | WF-FAIL | c_J_flip_far100_SPX_vol+c_J_flip_far100_NDX_vol+c_J_wall_behind50_SPX_vol+c_J_flip_far50_SPX_oi+c_J_wall_behind25_SPX_vo | -29102 -> -29091 | -12603 -> -14033 | -176 -> -191 | 2471 -> 1750 | 0.51 / 0.50 | 0.40 / 0.26 | 0.35 | -713 / -1262 |
| U7|S0 | WF-FAIL | c_J_flip_far100_SPX_vol+c_J_beyond_flip_NDX_oi+c_J_ivshort_fell+c_J_flip_far100_SPX_oi+c_J_wall_behind50_NDX_vol | -26093 -> -17339 | -10662 -> -18655 | -705 -> -407 | 2753 -> -482 | 0.69 / 0.41 | 0.09 / 0.03 | 0.12 | -3195 / -5662 |
| U7|S1 | WF-LEAD | c_J_em_frac_pos_Nh+c_J_em_frac_pos_Nd+c_J_beyond_flip_SPX_oi+c_J_beyond_flip_NDX_vol+c_J_beyond_flip_SPX_vol | -18394 -> -11145 | -13693 -> -10378 | 529 -> 1900 | -180 -> 430 | 0.77 / 0.94 | 0.84 / 0.75 | 0.88 | 649 / 1069 |

Most-chosen columns in plain words (count of cells choosing it; feed: Unusual Whales options / gamma exposure subscription; live today: NO: needs the UW subscription):
- c_J_flip_far25_NDX_vol (5 cells): name only: c_J_flip_far25_NDX_vol
- c_J_netgamma_pos_Nh_vol (4 cells): name only: c_J_netgamma_pos_Nh_vol
- c_J_flip_far100_SPX_oi (4 cells): name only: c_J_flip_far100_SPX_oi
- c_J_flip_far100_SPX_vol (3 cells): name only: c_J_flip_far100_SPX_vol
- c_J_flip_far100_NDX_oi (3 cells): name only: c_J_flip_far100_NDX_oi
- c_J_wall_behind25_SPX_vol (3 cells): name only: c_J_wall_behind25_SPX_vol
- c_J_flip_far25_SPX_oi (3 cells): name only: c_J_flip_far25_SPX_oi
- c_J_wall_behind50_SPX_oi (3 cells): name only: c_J_wall_behind50_SPX_oi

Family 9 leakage check (rb1_fam9_check.py): see the log lines in MORNING.md; independent brute-force recompute of 8 features on 600 random trades from raw trades with exit_ts < signal second matched in every case, and scrambling the outcomes (R, exit price, P&L) of a trade and all later trades changed none of the features of earlier trades nor of the first scrambled trade of each book: the features use only trades CLOSED before the signal second on the raw chassis (book alone), not the JL2 stack.

## Read this first
- Missing controls are "not finished", never passing: the perm p column is blank until every chunk x book permutation shard of a batch has landed for that family.
- Conditions that need a feed D7 lacks (L3, UW, options, order-message rates, cross-market) are scored but flagged: see chunks.csv feed column (/mnt/l2/l2vast/_rebuild/s1/chunks.csv).
- Not scored: X3/X4/X5 (0 raw trades), S7 and X1 X2 X6 X7 X8 (no engine definition), W-AL1 forecast conditions (pending), W-CH1 day/regime column (fam8 file empty), L3 combine/deepen flag files (derived from members already scored), cf4 state-wait float columns.
- Numbers CSVs: /mnt/l2/l2vast/_rebuild/s1/out/ (family_*.csv, survivors_detail.parquet, tiers.parquet).
