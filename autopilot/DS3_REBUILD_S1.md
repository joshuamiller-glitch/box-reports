# DS3_REBUILD_S1 [AT-ENTRY CLEAN TABLES: NONE YET - every table below is NOT at-entry-clean unless marked; see AT-ENTRY STATUS] - Stage 1 on RAW book trades (W-S1; order DIRECTIVE_REBUILD_20261116 + addenda + REFILL 11-17)
AT-ENTRY STATUS (read first, 2026-11-17 05:57 UTC): NO table on this page is at-entry-clean yet. (1) The family tables below pool ALL columns including _d5/_d30/_d60/_d120 WAIT variants (read 5-120 s after the signal, scored against a signal-time entry = LOOK-AHEAD), "ahead" columns and family-9 context: they are NOT at-entry and must not be used for a decision. (2) The survivors screen lists only columns whose NAME is at-entry (no _d>=5, no ahead, no family 9); it is in-sample and selection-biased, NOT a result. (3) Clean tables (at-entry-only family comparison, walk-forward, selection null, wait-then-enter and early-exit re-scores) are being built: sections marked PENDING below.

> VALIDATION (FIRST PASS, written 2026-11-17 05:57 UTC): trials counted = condition columns x 20 outcomes x book-session cells x 7 windows (TRIALS_LEDGER.csv RB1_RAW; correlated: outcomes, windows and cells overlap); correction = cell nonsense bar (99th pct of 200 nonsense columns) + sign stable in every year and L6M + BH 10% across all scored tests per window/outcome + shifted-label (11/23/37) and block-shift permutation nulls + 90 persistent-draw random columns + planted-edge columns per shard; ulcer-primary tier test (skip-rule path arithmetic vs 60 persistent draws, week-clustered bootstrap) on survivors; PBO: selecting best-of-65k is a fit, the permutation nulls play that role, no walk-forward fit in stage 1; in-sample on 2023-04..2026-10-30, NOT walk-forward or untouched; engine-exact re-runs of leads not done (no re-entry, no freed-book effect). Dollar columns: engine $ at base lots and engine fees $1.18 RT, $4.84 RT repriced and x1.75 live lots shown for the tier leaders.

VERDICT (data ends 2026-10-30; FIRST PASS): shards landed S 1618 of 0, permutation shards 259 of 4503; this page is rewritten as shards land. See "Read this first" below for what is and is not finished.

## Status
Raw base: 21049 trades, 7 books (K7 M7 P7 U7 A7 H7 O7); X3 X4 X5 raw cells hold 0 trades (shadow books not tradable in the raw chassis: not scored; S7, X1 X2 X6 X7 X8 have no engine definition). Driver: box 1 running 0, server 2 leased 41, load1 box 1 42.8. Shards: S (real + shifted labels + controls) 1618/0, P (50 block-shift permutations each, 20 batches = 1,000 per chunk x book) 259/4503. Updated 2026-11-17 05:57 UTC.

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
Cells 1624, screened in 266, extended 64, calibration cells 54 (done with >=1,000 draws: 0). Cells with permutation p computed: 534.
Calibration check: 0 of 0 calibration cells with p < 0.05 (expected about 5%) - not finished (fewer than 20 cells done).
| family | cells | screened in | with perm p | p < 0.05 |
|--|--|--|--|--|
| 1 | 1192 | 152 | 408 | 38 |
| 10 | 16 | 3 | 3 | 2 |
| 2 | 144 | 26 | 31 | 6 |
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
| cf4_altagree_11 | P7 | 1 | 338 | 3.11 | 1.43 | 100 | 0.0099 | 0.049 |
| fam9_raw_00 | A7 | 9 | 100 | 8.93 | 0.76 | 100 | 0.0099 | 0.049 |
| TAPE_SPEED_01 | U7 | 5 | 382 | 4.42 | 1.11 | 100 | 0.0099 | 0.049 |
| cf6_analogs_00 | POOL | 9 | 321 | 4.56 | 0.99 | 100 | 0.0099 | 0.049 |
| cf6_analogs_00 | U7 | 9 | 124 | 4.70 | 0.82 | 100 | 0.0099 | 0.049 |
| FLOW_PARTA_00 | K7 | 5 | 2508 | 4.70 | 1.23 | 100 | 0.0099 | 0.049 |
| FLOW_PARTA_00 | A7 | 5 | 617 | 4.48 | 1.14 | 100 | 0.0099 | 0.049 |
| FLOW_PARTA_02 | K7 | 5 | 2556 | 4.72 | 1.52 | 100 | 0.0099 | 0.049 |
| FLOW_PARTA_00 | POOL | 5 | 5148 | 7.28 | 1.24 | 100 | 0.0099 | 0.049 |
| FLOW_PARTA_01 | K7 | 5 | 2416 | 4.38 | 1.58 | 100 | 0.0099 | 0.049 |
| FLOW_PARTA_01 | P7 | 5 | 1264 | 3.06 | 1.13 | 100 | 0.0099 | 0.049 |
| FLOW_PARTA_01 | POOL | 5 | 4303 | 6.06 | 1.36 | 100 | 0.0099 | 0.049 |
| FLOW_PARTA_02 | M7 | 5 | 831 | 3.07 | 1.57 | 100 | 0.0099 | 0.049 |
| FLOW_PARTA_00 | P7 | 5 | 1589 | 3.91 | 1.41 | 100 | 0.0099 | 0.049 |
| J_00 | A7 | 7 | 122 | 4.77 | 1.29 | 100 | 0.0099 | 0.049 |

## AT-ENTRY TABLES (name-clean columns only: no _d>=5 / _L>=5 wait variants, no unaudited ahead, no stack-based family 9; family 9 = rebuilt causal version) - written 2026-11-17 05:51 UTC; A shards landed 18 of 1576
STATUS: PARTIAL: the tables below cover only the families whose A shards landed; families marked with fewer shards are NOT finished

Family table at-entry, window ALL43, outcomes R/MFE_R/MAE_R, book x session cells (stable = beyond nonsense bar and sign stable by year/L6M). Real vs shifted-label (11/23/37) and nonsense/random controls:
| family | shards | tests | real beyond % | real STABLE % | shifted-label real STABLE % | nonsense stable % | random-draw stable % | planted detected % |
|--|--|--|--|--|--|--|--|--|
| 1 | 18/1192 | 13146 | 1.29 | 0.75 | 1.05 | 0.49 | 0.68 | 68 |

Family table at-entry, window L6M, outcomes R/MFE_R/MAE_R, book x session cells (stable = beyond nonsense bar and sign stable by year/L6M). Real vs shifted-label (11/23/37) and nonsense/random controls:
| family | shards | tests | real beyond % | real STABLE % | shifted-label real STABLE % | nonsense stable % | random-draw stable % | planted detected % |
|--|--|--|--|--|--|--|--|--|
| 1 | 18/1192 | 10650 | 1.73 | 1.73 | 1.99 | 0.95 | 1.27 | 48 |

Family table at-entry, window UNT, outcomes R/MFE_R/MAE_R, book x session cells (stable = beyond nonsense bar and sign stable by year/L6M). Real vs shifted-label (11/23/37) and nonsense/random controls:
| family | shards | tests | real beyond % | real STABLE % | shifted-label real STABLE % | nonsense stable % | random-draw stable % | planted detected % |
|--|--|--|--|--|--|--|--|--|
| 1 | 18/1192 | 11805 | 2.29 | 2.08 | 1.80 | 0.89 | 1.63 | 57 |

PENDING (A shards not all landed: 18 of 1576): walk-forward and selection-null tables are not finished and are not shown.

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

## Read this first
- Missing controls are "not finished", never passing: the perm p column is blank until every chunk x book permutation shard of a batch has landed for that family.
- Conditions that need a feed D7 lacks (L3, UW, options, order-message rates, cross-market) are scored but flagged: see chunks.csv feed column (/mnt/l2/l2vast/_rebuild/s1/chunks.csv).
- Not scored: X3/X4/X5 (0 raw trades), S7 and X1 X2 X6 X7 X8 (no engine definition), W-AL1 forecast conditions (pending), W-CH1 day/regime column (fam8 file empty), L3 combine/deepen flag files (derived from members already scored), cf4 state-wait float columns.
- Numbers CSVs: /mnt/l2/l2vast/_rebuild/s1/out/ (family_*.csv, survivors_detail.parquet, tiers.parquet).
