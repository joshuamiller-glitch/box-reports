# DS3_REBUILD_S1 - Stage 1: every condition family scored against the RAW book trades (W-S1; order DIRECTIVE_REBUILD_20261116 + addenda + REFILL 11-17)
> VALIDATION (FIRST PASS, written 2026-11-17 05:24 UTC): trials counted = condition columns x 20 outcomes x book-session cells x 7 windows (TRIALS_LEDGER.csv RB1_RAW; correlated: outcomes, windows and cells overlap); correction = cell nonsense bar (99th pct of 200 nonsense columns) + sign stable in every year and L6M + BH 10% across all scored tests per window/outcome + shifted-label (11/23/37) and block-shift permutation nulls + 90 persistent-draw random columns + planted-edge columns per shard; ulcer-primary tier test (skip-rule path arithmetic vs 60 persistent draws, week-clustered bootstrap) on survivors; PBO: selecting best-of-65k is a fit, the permutation nulls play that role, no walk-forward fit in stage 1; in-sample on 2023-04..2026-10-30, NOT walk-forward or untouched; engine-exact re-runs of leads not done (no re-entry, no freed-book effect). Dollar columns: engine $ at base lots and engine fees $1.18 RT, $4.84 RT repriced and x1.75 live lots shown for the tier leaders.

VERDICT (data ends 2026-10-30; FIRST PASS): shards landed S 1618 of 0, permutation shards 30 of 4055; this page is rewritten as shards land. See "Read this first" below for what is and is not finished.

## Status
Raw base: 21049 trades, 7 books (K7 M7 P7 U7 A7 H7 O7); X3 X4 X5 raw cells hold 0 trades (shadow books not tradable in the raw chassis: not scored; S7, X1 X2 X6 X7 X8 have no engine definition). Driver: box 1 running 9, server 2 leased 76, load1 box 1 40.9. Shards: S (real + shifted labels + controls) 1618/0, P (50 block-shift permutations each, 20 batches = 1,000 per chunk x book) 30/4055. Updated 2026-11-17 05:24 UTC.

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

## Survivors with the ulcer-primary tier test (outcome R, ALL43 stable, per book x session cell, top 60 by |zw| per cell; skip rule on the raw cell, path arithmetic)
Tier counts: {'FAIL': 532, 'CONFIRMED': 269, 'LEAD': 99}. Persistent draws 60 (5-minute bucket per book and side, same skipped share). Tiers need ulcer-or-mean percentile >= .85 (CONFIRMED) / .75 (LEAD) in L6M and L3M, P(ulcer lower, L6M) >= .80, nothing below .25 in older windows.
| tier | family | cell | condition | rule | zw | lift R | BH ok | L6M ulc raw -> rule | L6M mean $/wk raw -> rule | pct ulc / mean L6M | L3M | HOLD ulc | P(ulc lower L6M) | L6M $/wk $4.84 | L6M $/wk x1.75 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| CONFIRMED | 5 | M7|S3 | fl259_d120 | skip yes | -7.9 | -0.512 | yes | -8747 -> -1833 | 199 -> 3241 | 1.00 / 1.00 | 0.95 / 1.00 | 1.00 | 0.99 | 3042 | 5323 |
| CONFIRMED | 5 | P7|S3 | fl259_d120 | skip yes | -7.6 | -0.496 | yes | -52822 -> -5834 | -169 -> 8755 | 1.00 / 1.00 | 1.00 / 1.00 | 1.00 | 1.00 | 8924 | 15617 |
| CONFIRMED | 5 | K7|S3 | fl259_d120 | skip yes | -7.4 | -0.389 | yes | -24248 -> -3302 | -995 -> 1571 | 1.00 / 1.00 | 1.00 / 1.00 | 1.00 | 1.00 | 2566 | 4490 |
| CONFIRMED | 5 | K7|S4 | fl259_d120 | skip yes | -6.8 | -0.345 | yes | -13606 -> -3027 | 1320 -> 4116 | 1.00 / 1.00 | 1.00 / 1.00 | 0.98 | 1.00 | 2797 | 4894 |
| CONFIRMED | 5 | K7|S4 | fl051_d120 | skip no | 6.6 | 0.367 | yes | -13606 -> -1753 | 1320 -> 3676 | 1.00 / 1.00 | 1.00 / 1.00 | 0.98 | 1.00 | 2357 | 4124 |
| CONFIRMED | 5 | K7|S3 | fl116_d120 | skip no | 6.3 | 0.318 | yes | -24248 -> -3417 | -995 -> 862 | 0.97 / 1.00 | 0.78 / 1.00 | 0.95 | 1.00 | 1856 | 3249 |
| CONFIRMED | 1 | K7|S0 | c_B_cl_ahead_kinds2_15 | skip no | 6.3 | 0.259 | yes | -28120 -> -5082 | 3429 -> 3062 | 0.98 / 0.98 | 1.00 / 1.00 | 0.42 | 0.97 | -367 | -643 |
| CONFIRMED | 5 | K7|S4 | fl108_d120 | skip no | 6.3 | 0.356 | yes | -13606 -> -2050 | 1320 -> 3688 | 1.00 / 1.00 | 1.00 / 1.00 | 0.98 | 1.00 | 2368 | 4145 |
| CONFIRMED | 1 | K7|S0 | c_B_cl_ahead_cnt2_15 | skip no | 6.1 | 0.255 | yes | -28120 -> -5340 | 3429 -> 2972 | 0.95 / 0.97 | 1.00 / 1.00 | 0.52 | 0.96 | -457 | -799 |
| CONFIRMED | 5 | P7|S3 | fl222_d120 | skip yes | -6.1 | -0.361 | yes | -52822 -> -18718 | -169 -> 3259 | 1.00 / 1.00 | 0.98 / 1.00 | 0.98 | 1.00 | 3428 | 5999 |
| CONFIRMED | 5 | P7|S3 | fl051_d120 | skip no | 5.8 | 0.393 | yes | -52822 -> -5035 | -169 -> 5405 | 1.00 / 1.00 | 1.00 / 1.00 | 1.00 | 1.00 | 5575 | 9755 |
| CONFIRMED | 5 | M7|S3 | fl108_d120 | skip no | 5.5 | 0.380 | yes | -8747 -> -1140 | 199 -> 1680 | 1.00 / 1.00 | 0.90 / 0.93 | 0.98 | 1.00 | 1481 | 2592 |
| CONFIRMED | 5 | P7|S3 | fl103_d60 | skip no | 5.1 | 0.230 | yes | -52822 -> -7428 | -169 -> 3264 | 0.97 / 1.00 | 0.97 / 0.92 | 0.70 | 1.00 | 3433 | 6008 |
| CONFIRMED | 5 | K7|S3 | fl108_d120 | skip no | 5.0 | 0.300 | yes | -24248 -> -2198 | -995 -> 810 | 1.00 / 1.00 | 0.97 / 1.00 | 1.00 | 1.00 | 1805 | 3158 |
| CONFIRMED | 1 | P7|S0 | c_B_cl_ahead_kinds2_10 | skip no | 4.9 | 0.222 | yes | -36590 -> -29394 | 16772 -> 9689 | 0.50 / 0.93 | 0.95 / 0.90 | 0.85 | 0.84 | -7083 | -12395 |
| CONFIRMED | 5 | K7|S3 | fl018_d60 | skip no | 4.9 | 0.264 | yes | -24248 -> -3744 | -995 -> 727 | 0.97 / 1.00 | 0.83 / 0.97 | 0.95 | 1.00 | 1721 | 3012 |
| CONFIRMED | 5 | P7|S3 | fl165_d120 | skip yes | -4.9 | -0.314 | yes | -52822 -> -16222 | -169 -> 3779 | 1.00 / 1.00 | 0.97 / 1.00 | 1.00 | 1.00 | 3948 | 6910 |
| CONFIRMED | 1 | K7|S3 | c4_smieS_1m_divwith | skip no | 7.4 | 0.213 | yes | -24248 -> -1300 | -995 -> 86 | 0.85 / 0.82 | 0.53 / 0.87 | 0.30 | 1.00 | 1081 | 1892 |
| CONFIRMED | 1 | K7|S0 | c4_don20_pos_ha15_eenter | skip no | 9.4 | 0.322 | yes | -28120 -> -1590 | 3429 -> 1242 | 0.93 / 1.00 | 0.99 / 0.97 | 0.80 | 1.00 | -2187 | -3827 |
| CONFIRMED | 1 | K7|S0 | c4_w1_donchian20_pos_ha15_eenter | skip no | 9.4 | 0.322 | yes | -28120 -> -1590 | 3429 -> 1242 | 0.93 / 1.00 | 0.99 / 0.97 | 0.80 | 1.00 | -2187 | -3827 |
| CONFIRMED | 5 | M7|S3 | fl051_d120 | skip no | 4.7 | 0.371 | yes | -8747 -> -856 | 199 -> 1899 | 1.00 / 1.00 | 0.95 / 0.93 | 0.65 | 1.00 | 1700 | 2975 |
| CONFIRMED | 5 | P7|S3 | fl018_d120 | skip no | 4.7 | 0.262 | yes | -52822 -> -6274 | -169 -> 3193 | 1.00 / 1.00 | 0.98 / 0.98 | 1.00 | 1.00 | 3362 | 5884 |
| CONFIRMED | 1 | P7|S3 | m_uo_1d_divwith | skip yes | -5.0 | -0.118 | yes | -52822 -> -42582 | -169 -> 1276 | 0.67 / 0.88 | 0.88 / 0.98 | 1.00 | 0.92 | 1445 | 2528 |
| CONFIRMED | 5 | P7|S3 | fl126_d120 | skip no | 4.6 | 0.340 | no | -52822 -> -4040 | -169 -> 2015 | 1.00 / 0.93 | 1.00 / 1.00 | 1.00 | 1.00 | 2185 | 3823 |
| CONFIRMED | 5 | K7|S3 | fl151_d60 | skip yes | -4.6 | -0.242 | yes | -24248 -> -14699 | -995 -> -105 | 0.90 / 1.00 | 0.82 / 0.98 | 0.80 | 0.99 | 889 | 1557 |
| CONFIRMED | 1 | K7|S0 | c4_fvgS_cnt_ha3_side | skip no | 4.6 | 0.292 | yes | -28120 -> -2668 | 3429 -> 2380 | 0.98 / 1.00 | 0.78 / 0.97 | 0.57 | 1.00 | -1048 | -1835 |
| CONFIRMED | 5 | K7|S3 | fl222_d120 | skip yes | -4.6 | -0.292 | yes | -24248 -> -13410 | -995 -> -348 | 0.98 / 0.97 | 0.97 / 0.98 | 0.87 | 0.88 | 646 | 1131 |
| CONFIRMED | 5 | U7|S0 | fl214_d5 | skip no | 5.4 | 0.122 | yes | -10662 -> -3742 | 2753 -> 1681 | 0.93 / 0.93 | 0.92 / 0.83 | 0.92 | 0.91 | -1072 | -1876 |
| CONFIRMED | 1 | K7|S3 | c4_mc_comp2_mtf_ge4 | skip yes | -4.3 | -0.104 | yes | -24248 -> -1349 | -995 -> 483 | 1.00 / 1.00 | 1.00 / 0.95 | 0.40 | 1.00 | 1478 | 2586 |
| CONFIRMED | 5 | M7|S3 | fl178_d120 | skip no | 4.3 | 0.279 | yes | -8747 -> -1569 | 199 -> 1688 | 1.00 / 1.00 | 1.00 / 1.00 | 0.32 | 1.00 | 1489 | 2607 |
| CONFIRMED | 1 | K7|S1 | m_ao_5m_nodiv | skip yes | -4.6 | -0.336 | yes | -40458 -> -4691 | -1103 -> 983 | 0.87 / 0.98 | 1.00 / 1.00 | 0.98 | 0.99 | 2086 | 3650 |
| CONFIRMED | 5 | M7|S3 | fl116_d120 | skip no | 4.3 | 0.323 | yes | -8747 -> -1467 | 199 -> 1353 | 0.98 / 1.00 | 0.95 / 1.00 | 1.00 | 0.98 | 1154 | 2019 |
| CONFIRMED | 1 | M7|S1 | c4_w1_kama200_px_range16_fresh5 | skip yes | -4.3 | -0.196 | yes | -32674 -> -25387 | -623 -> 369 | 0.75 / 0.93 | 0.72 / 0.92 | 0.97 | 0.90 | 992 | 1736 |
| CONFIRMED | 5 | K7|S3 | fl274_d60 | skip yes | -4.2 | -0.255 | yes | -24248 -> -14794 | -995 -> -362 | 0.85 / 0.92 | 0.42 / 0.85 | 0.97 | 0.96 | 632 | 1106 |
| CONFIRMED | 5 | P7|S0 | fl268_d30 | skip yes | -4.2 | -0.200 | yes | -36590 -> -16746 | 16772 -> 22361 | 1.00 / 1.00 | 1.00 / 1.00 | 0.57 | 0.98 | 5589 | 9781 |
| CONFIRMED | 5 | U7|S0 | fl136_d5 | skip no | 4.7 | 0.193 | no | -10662 -> -3439 | 2753 -> 2895 | 0.95 / 0.98 | 0.93 / 0.97 | 0.98 | 0.94 | 141 | 247 |
| CONFIRMED | 1 | H7|S0 | c4_lorS_1m_flip3 | skip yes | -4.5 | -0.195 | yes | -25780 -> -19680 | 1221 -> 2565 | 0.63 / 0.95 | 0.68 / 0.93 | 0.87 | 0.96 | 1344 | 2352 |
| CONFIRMED | 1 | K7|S3 | n_dl_sp_ahead_60 | skip yes | -7.0 | -0.439 | yes | -24248 -> -20494 | -995 -> -766 | 0.98 / 0.98 | 0.75 / 0.98 | 0.43 | 0.94 | 229 | 400 |
| CONFIRMED | 1 | U7|S1 | c4_sdF_dsup_range8_rise | skip yes | -4.4 | -0.116 | yes | -13693 -> -8035 | -180 -> 923 | 0.95 / 0.80 | 0.88 / 0.83 | 0.95 | 0.96 | 1103 | 1930 |
| CONFIRMED | 1 | K7|S0 | c4_kst_60m_nodiv | skip yes | -4.1 | -0.244 | yes | -28120 -> -5412 | 3429 -> 2699 | 0.88 / 0.98 | 0.63 / 0.90 | 1.00 | 0.97 | -730 | -1277 |
(The $4.84 column here equals the engine-$ change with the commission repricing not applied per trade: a skip removes trades, so the $4.84 repricing changes only the removed trades; exact repricing is in the Stage 6 head-to-head. x1.75 = live lots.)

## Adaptive permutation screen (rb1_sched.py; replaces the fixed 1,000-permutation plan)
Rule: each chunk x book cell is SCREENED IN when its real STABLE pass count (book x session cells, windows ALL43+L6M, 20 outcomes) is >= 3 and >= 1.5 x the larger of the nonsense stable rate and the mean shifted-label (11/23/37) real stable rate on the same cell. Screened-in cells run 100 permutations first (batches 0,1); a cell is EXTENDED to 1,000 when its permutation p of the real stable count is <= 0.02 or its BH q (over all cells with 100 draws) is <= 0.10. A fixed-seed random 5% of the non-screened cells run the full 1,000 as a CALIBRATION check (their share with p < 0.05 should be about 5%); the other non-screened cells get 100 permutations last. Full 1,000 permutations are therefore not run for every cell: stated here, not hidden.
Cells 1624, screened in 266, extended 0, calibration cells 54 (done with >=1,000 draws: 0). Cells with permutation p computed: 165.
Calibration check: 0 of 0 calibration cells with p < 0.05 (expected about 5%) - not finished (fewer than 20 cells done).
| family | cells | screened in | with perm p | p < 0.05 |
|--|--|--|--|--|
| 1 | 1192 | 152 | 165 | 5 |
| 10 | 16 | 3 | 0 | 0 |
| 2 | 144 | 26 | 0 | 0 |
| 3 | 8 | 2 | 0 | 0 |
| 4 | 8 | 2 | 0 | 0 |
| 5 | 144 | 56 | 0 | 0 |
| 6 | 48 | 9 | 0 | 0 |
| 7 | 8 | 1 | 0 | 0 |
| 8 | 32 | 4 | 0 | 0 |
| 8/9 | 8 | 3 | 0 | 0 |
| 9 | 16 | 8 | 0 | 0 |

Leading cells by permutation p (count of real stable passes vs shifted nulls):
| chunk | book | family | real stable | real rate % | control rate % | draws | p | BH q |
|--|--|--|--|--|--|--|--|--|
| univ_entry_table_D4_00 | A7 | 1 | 161 | 3.55 | 0.76 | 50 | 0.0196 |  |
| univ_cols_M_12 | O7 | 1 | 74 | 1.99 | 0.70 | 50 | 0.0196 |  |
| univ_cols_M_09 | A7 | 1 | 460 | 3.36 | 1.43 | 50 | 0.0196 |  |
| univ_cols_M_01 | A7 | 1 | 281 | 3.13 | 2.18 | 50 | 0.0392 |  |
| univ_cols_M_08 | A7 | 1 | 362 | 2.69 | 1.51 | 50 | 0.0392 |  |
| univ_cols_M_03 | H7 | 1 | 183 | 1.98 | 1.22 | 50 | 0.0588 |  |
| entry_table_universe_00 | POOL | 1 | 699 | 1.91 | 1.44 | 50 | 0.0588 |  |
| entry_table_universe_00 | P7 | 1 | 420 | 2.05 | 1.55 | 50 | 0.0588 |  |
| univ_cols_M_13 | O7 | 1 | 54 | 1.28 | 0.32 | 50 | 0.0588 |  |
| univ_cols_M_14 | A7 | 1 | 83 | 3.67 | 0.94 | 50 | 0.0588 |  |
| cf4_osc_04 | A7 | 1 | 372 | 2.84 | 1.42 | 50 | 0.0588 |  |
| entry_table_universe_00 | A7 | 1 | 122 | 2.34 | 1.01 | 50 | 0.0784 |  |
| univ_entry_table_D4_00 | P7 | 1 | 270 | 1.88 | 1.92 | 50 | 0.0784 |  |
| univ_cols_M_10 | A7 | 1 | 462 | 3.23 | 1.66 | 50 | 0.0980 |  |
| univ_entry_table_U_00 | A7 | 1 | 10 | 5.00 | 0.83 | 50 | 0.0980 |  |

## Read this first
- Missing controls are "not finished", never passing: the perm p column is blank until every chunk x book permutation shard of a batch has landed for that family.
- Conditions that need a feed D7 lacks (L3, UW, options, order-message rates, cross-market) are scored but flagged: see chunks.csv feed column (/mnt/l2/l2vast/_rebuild/s1/chunks.csv).
- Not scored: X3/X4/X5 (0 raw trades), S7 and X1 X2 X6 X7 X8 (no engine definition), W-AL1 forecast conditions (pending), W-CH1 day/regime column (fam8 file empty), L3 combine/deepen flag files (derived from members already scored), cf4 state-wait float columns.
- Numbers CSVs: /mnt/l2/l2vast/_rebuild/s1/out/ (family_*.csv, survivors_detail.parquet, tiers.parquet).
