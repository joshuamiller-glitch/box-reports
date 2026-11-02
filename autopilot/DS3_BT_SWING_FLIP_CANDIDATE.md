# DS3_BT_SWING_FLIP_CANDIDATE - SHADOW CANDIDATE ONE-PAGER (ZL-1, written 2026-11-02 09:15Z; all numbers D7 V13Y = D7 v1.3 EXACT + the add-fill ordering fix, new windows; lock=None is the headline frame, lock=12R beside it)
**Status: LEAD, a MEAN-type effect (it saves dollars by not taking a class of trades that lose money in expectancy), NOT a drawdown cut, NOT RISK-KEEP, nothing promoted, Shadow only. Post-hoc on 2023-04..2026-10 data. The user decides whether it is logged in the forward Shadow register; nothing here is acted on.**

## 1. The rule in one sentence
Do not take a base entry if a fresh "flip level" (a recent 5-minute swing high/low that price has already broken by 10 points or more, now acting as support/resistance) lies between the entry price and the target, within 40 points of the entry, in the direction of travel.

## 2. Exact live definition (what D7 computes from its own tape; no daily file)
1. **5-minute bars**, clock-aligned (xx:00, xx:05, ...), built from trade prints: bar high = highest print price in the 5 minutes, bar low = lowest. Same continuous (back-adjusted) price frame as the entry/target/stop prices the base uses.
2. **Fractal (swing)**: a bar whose HIGH is strictly above the highs of the 2 bars before it and the 2 bars after it is a swing high (a swing low mirrors with LOWs). It becomes known when the 2nd bar after it closes (no look-ahead). Keep the last 3 swing highs and last 3 swing lows; a 4th newer one of the same kind drops the oldest.
3. **Broken by >= 10 pts means a PRINT, not a close**: the swing high L is broken at the first second at which any trade prints at or above L + 10.0 pts (swing low: at or below L - 10.0). Prices are in points (NQ, tick 0.25). The break second creates a **flip level at L**: support if a high was broken upward, resistance if a low was broken downward.
4. **Validity / freshness**: the flip level is valid for 4 hours after the break second. It is FRESH until price returns to L after having been more than 0.5 pt away from it (at the break price is 10+ pts away, so fresh ends at the first return to L). Only fresh levels count.
5. **Direction rule at a base signal** (entry E, trade side, target distance td): FLAGGED if a fresh flip level lies between E and the target in the direction of travel with 0 <= distance <= min(40, td) pts (a long: L - E; a short: E - L; L equal to E counts as distance 0). Support-type and resistance-type flip levels both count (only their position ahead matters).
6. **Per-book application**: every base signal of every core book (K6 P6 U6 H6 M6 A6 / KB PE SM HM MV PB) is tested the same way; the tests cover the six core books' taken trades (the X1-X5 cells are not in the taken-trade tables). The Shadow action is would_skip = 1 (nothing is skipped live).
7. **Inputs D7 needs**: the trade tape (prints with price and time) to build the 5-min bars and detect the 10-pt break; the entry price, side and target distance of each signal. No L2 data, no daily file. Latency: the flip level exists from the break second; a signal in the same second sees it (stream convention = state at the end of the signal second); a 1-3 s lag in D7's detection is not expected to matter (the same type of stream, PUL, was insensitive to a 1/3-s event delay; the BT-specific delay test has not been run).
8. **Causal checks done**: 100/100 random stream rows reproduced from raw 1-s data truncated at the end of the event bin (max level difference 0); events start 2023-08 in the main stream (a path-based version covers 2023-04..07, see section 8).

## 3. How often it fires (V13Y taken trades)
### lock None

flagged taken trades per month (2023-08..2026-10, 39 months; total 1035; 26.5 per month; last 12 months 29.9 per month) by book|session (session 0 asia 1 london 2 pre 3 nyam 4 nypm):
| k    |   per_month_all |   per_month_last12 |
|:-----|----------------:|-------------------:|
| KB|0 |            5.1  |               6.83 |
| KB|1 |            4.85 |               5.5  |
| PE|0 |            3.18 |               3.17 |
| HM|0 |            2.41 |               2.75 |
| PE|1 |            1.97 |               2.67 |
| KB|3 |            1.92 |               1.25 |
| SM|1 |            1.77 |               1.83 |
| MV|1 |            1.54 |               3.08 |
| KB|4 |            1.13 |               0.75 |
| HM|3 |            0.85 |               0.33 |
| SM|0 |            0.72 |               0.83 |
| MV|3 |            0.46 |               0.42 |
| PE|3 |            0.38 |               0.08 |
| PB|0 |            0.26 |               0.42 |



## 4. The numbers (V13Y; saved dollars = minus the base net of the flagged trades, i.e. what skipping them would have changed first-order; positive = good)
### 4a. Row level, per window, with 90% day-clustered CIs and three placebos (200 draws: A same count per book x session, B same count per day, C other-day same book x session; rank = share of placebo sums at least as good; low = real)
### lock None: BT|swing_F10|4h AHEAD D40 skip; taken trades 18827, flagged 1035 (5.5%)

| window   |   n_flag |   flag_sum_k |   flag_mean |   unflag_mean |   flag_hit |   unflag_hit |   flag_ci_lo_k |   flag_ci_hi_k |   rank_A |   rank_B |   rank_C |   plcA_mean_k |   plcB_mean_k |   plcC_mean_k |
|:---------|---------:|-------------:|------------:|--------------:|-----------:|-------------:|---------------:|---------------:|---------:|---------:|---------:|--------------:|--------------:|--------------:|
| L3M      |       94 |      -30.431 |    -323.73  |       156.466 |      0.394 |        0.479 |        -63.253 |          4.034 |    0.07  |    0.1   |    0.1   |        16.372 |         9.127 |        12.592 |
| L6M      |      204 |      -69.777 |    -342.046 |       197.606 |      0.377 |        0.472 |       -116.996 |        -19.764 |    0.005 |    0.025 |    0.015 |        50.401 |        17.798 |        46.929 |
| HOLD     |      359 |      -74.915 |    -208.677 |       182.225 |      0.398 |        0.471 |       -145.72  |         -4.258 |    0.005 |    0.015 |    0.035 |        74.045 |        36.414 |        75.391 |
| MID      |       84 |      -17.872 |    -212.763 |       139.821 |      0.44  |        0.461 |        -59.154 |         25.516 |    0.204 |    0.224 |    0.204 |         7.216 |         9.674 |        11.09  |
| PRE      |      416 |     -103.432 |    -248.636 |       156.288 |      0.438 |        0.484 |       -200.759 |         -3.825 |    0.04  |    0.08  |    0.03  |        21.227 |       -20.687 |        14.264 |
| X'       |      155 |      -50.13  |    -323.417 |        48.724 |      0.477 |        0.51  |       -123.346 |         16.541 |    0.075 |    0.274 |    0.055 |         0.498 |       -30.094 |         2.917 |

flagged rows by book|session in HOLD (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     33 |   8.4 |   255.2 |
| HM|3  |      4 |  -0.8 |  -190.8 |
| KB|0  |     82 |  -1.9 |   -22.8 |
| KB|1  |     66 | -21.1 |  -320.1 |
| KB|3  |     15 |  -6.4 |  -429.2 |
| KB|4  |      9 |  -4.9 |  -541.7 |
| MV|1  |     37 |   2.3 |    61.3 |
| MV|3  |      5 |  -1   |  -208.9 |
| PB|0  |      5 |  -2.2 |  -436.3 |
| PE|0  |     38 | -16.5 |  -434.7 |
| PE|1  |     32 | -13.9 |  -435   |
| PE|3  |      1 |  11.5 | 11479.6 |
| SM|0  |     10 |  -6.2 |  -622   |
| SM|1  |     22 | -22.1 | -1005.9 |

flagged rows by book|session in PRE (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     34 | -12.6 |  -371.8 |
| HM|3  |     15 |  -4.6 |  -303.6 |
| KB|0  |     76 | -19.9 |  -261.5 |
| KB|1  |     72 |   8.8 |   121.7 |
| KB|3  |     30 |   4.5 |   151   |
| KB|4  |     24 |  -4   |  -164.7 |
| MV|1  |     18 |  -5.1 |  -280.8 |
| MV|3  |      7 |  -4.1 |  -591.7 |
| PB|0  |      4 |   3.5 |   867.3 |
| PE|0  |     53 | -45.3 |  -855.4 |
| PE|1  |     32 | -14.5 |  -453   |
| PE|3  |      9 | -10.6 | -1176.5 |
| SM|0  |     14 |  -2.3 |  -161   |
| SM|1  |     28 |   2.7 |    96.5 |

### lock 12R: BT|swing_F10|4h AHEAD D40 skip; taken trades 12835, flagged 704 (5.5%)

| window   |   n_flag |   flag_sum_k |   flag_mean |   unflag_mean |   flag_hit |   unflag_hit |   flag_ci_lo_k |   flag_ci_hi_k |   rank_A |   rank_B |   rank_C |   plcA_mean_k |   plcB_mean_k |   plcC_mean_k |
|:---------|---------:|-------------:|------------:|--------------:|-----------:|-------------:|---------------:|---------------:|---------:|---------:|---------:|--------------:|--------------:|--------------:|
| L3M      |       65 |      -24.762 |    -380.958 |       155.428 |      0.369 |        0.484 |        -55.411 |          2.924 |    0.1   |    0.109 |    0.095 |         9.213 |         5.417 |         8.704 |
| L6M      |      136 |      -70.142 |    -515.748 |       220.721 |      0.338 |        0.474 |       -114.064 |        -29.249 |    0.02  |    0.005 |    0.005 |        36.674 |        11.555 |        35.123 |
| HOLD     |      237 |     -107.054 |    -451.706 |       188.261 |      0.363 |        0.471 |       -165.481 |        -48.797 |    0.005 |    0.01  |    0.01  |        51.258 |        19.494 |        48.242 |
| MID      |       57 |      -47.301 |    -829.84  |       109.608 |      0.351 |        0.462 |        -75.501 |        -21.122 |    0.04  |    0.06  |    0.05  |         1.104 |         3.604 |         0     |
| PRE      |      260 |     -123.118 |    -473.532 |       134.178 |      0.404 |        0.476 |       -200.509 |        -51.553 |    0.01  |    0.03  |    0.005 |         9.968 |       -25.14  |        12.193 |
| X'       |      116 |      -66.28  |    -571.383 |        10.188 |      0.44  |        0.507 |       -118.271 |        -18.791 |    0.03  |    0.184 |    0.005 |        -8.141 |       -39.707 |        -4.927 |

flagged rows by book|session in HOLD (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     17 |  -1.1 |   -64.3 |
| HM|3  |      2 |  -0.2 |  -115.1 |
| KB|0  |     53 |  -1   |   -19.7 |
| KB|1  |     50 | -18.4 |  -369   |
| KB|3  |      8 |  -3.9 |  -486.2 |
| KB|4  |      8 |  -6.1 |  -762.1 |
| MV|1  |     22 |  -2.7 |  -123.3 |
| MV|3  |      3 |  -0.4 |  -130.4 |
| PB|0  |      4 |  -4.6 | -1142.9 |
| PE|0  |     25 | -28.6 | -1143   |
| PE|1  |     21 | -22.1 | -1051.7 |
| PE|3  |      1 |  11.5 | 11479.6 |
| SM|0  |      7 |  -9.2 | -1312.8 |
| SM|1  |     16 | -20.2 | -1262.9 |

flagged rows by book|session in PRE (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     26 | -11.4 |  -439.2 |
| HM|3  |     10 |  -4.6 |  -456.4 |
| KB|0  |     51 | -19.3 |  -378.1 |
| KB|1  |     42 |  -1   |   -23.4 |
| KB|3  |     20 |  -0   |    -2   |
| KB|4  |     12 |   4.1 |   341.1 |
| MV|1  |     12 |  -6.7 |  -561.3 |
| MV|3  |      4 |  -1.7 |  -418.8 |
| PB|0  |      2 |  -0   |   -17.6 |
| PE|0  |     37 | -39.2 | -1058.2 |
| PE|1  |     16 | -17.1 | -1071.3 |
| PE|3  |      5 | -12.4 | -2483.3 |
| SM|0  |      6 |  -5.5 |  -922.3 |
| SM|1  |     17 |  -8.2 |  -483.9 |

### 4b. Per calendar year / half-year / quarter
### V13Y lock None: saved $k by calendar period

**year** (positive 4 / 4 with flags):
| period   |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:---------|---------:|----------:|------------:|--------------:|
| (2023,)  |      122 |      56.9 |      -466.1 |          46.5 |
| (2024,)  |      304 |      29.3 |       -96.3 |         155.2 |
| (2025,)  |      288 |      28   |       -97.1 |         174.4 |
| (2026,)  |      321 |      89.2 |      -277.7 |         178.1 |

**half-year** (positive 5 / 7 with flags):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 1) |        0 |      -0   |       nan   |         -19.4 |
| (2023, 2) |      122 |      56.9 |      -466.1 |          79.2 |
| (2024, 1) |      157 |      37.4 |      -238.1 |         140.5 |
| (2024, 2) |      147 |      -8.1 |        55.2 |         165.1 |
| (2025, 1) |      145 |      67.4 |      -465   |         149.1 |
| (2025, 2) |      143 |     -39.5 |       276.1 |         204.9 |
| (2026, 1) |      191 |      51.6 |      -270.3 |         232.8 |
| (2026, 2) |      130 |      37.5 |      -288.7 |         106.4 |

**quarter** (positive 11 / 14 with flags):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 2) |        0 |      -0   |       nan   |         -19.4 |
| (2023, 3) |       50 |       6.2 |      -123.1 |           8.6 |
| (2023, 4) |       72 |      50.7 |      -704.3 |         160.2 |
| (2024, 1) |       80 |       6.3 |       -78.3 |         114.9 |
| (2024, 2) |       77 |      31.1 |      -404.1 |         165.6 |
| (2024, 3) |       77 |      19   |      -246.3 |         180.8 |
| (2024, 4) |       70 |     -27.1 |       386.9 |         145.7 |
| (2025, 1) |       73 |      12.3 |      -168.9 |          20.6 |
| (2025, 2) |       72 |      55.1 |      -765.3 |         254.3 |
| (2025, 3) |       82 |      -7.7 |        93.3 |         225.6 |
| (2025, 4) |       61 |     -31.8 |       521.7 |         191.6 |
| (2026, 1) |       84 |      21.2 |      -252.4 |          91.7 |
| (2026, 2) |      107 |      30.4 |      -284.3 |         347.7 |
| (2026, 3) |       92 |      32.5 |      -353.4 |          88.4 |
| (2026, 4) |       38 |       5   |      -132   |         160.1 |

### V13Y lock 12R: saved $k by calendar period

**year** (positive 4 / 4 with flags):
| period   |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:---------|---------:|----------:|------------:|--------------:|
| (2023,)  |       94 |      64.1 |      -682.2 |          18.6 |
| (2024,)  |      189 |      83.9 |      -443.9 |         111.9 |
| (2025,)  |      212 |      16.8 |       -79.2 |         180.3 |
| (2026,)  |      209 |     122.4 |      -585.9 |         178.8 |

**half-year** (positive 6 / 7 with flags):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 1) |        0 |      -0   |       nan   |        -234.3 |
| (2023, 2) |       94 |      64.1 |      -682.2 |         109.8 |
| (2024, 1) |       92 |      50.8 |      -552.6 |          62.4 |
| (2024, 2) |       97 |      33.1 |      -340.8 |         145.4 |
| (2025, 1) |       93 |      41.4 |      -445   |         143.1 |
| (2025, 2) |      119 |     -24.6 |       206.7 |         220   |
| (2026, 1) |      129 |      96.3 |      -746.4 |         204.6 |
| (2026, 2) |       80 |      26.2 |      -327.1 |         140.7 |

**quarter** (positive 11 / 14 with flags):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 2) |        0 |      -0   |       nan   |        -234.3 |
| (2023, 3) |       33 |      18.4 |      -557.4 |          17.9 |
| (2023, 4) |       61 |      45.7 |      -749.7 |         195.9 |
| (2024, 1) |       47 |      30.6 |      -650.1 |          61.3 |
| (2024, 2) |       45 |      20.3 |      -450.8 |          63.5 |
| (2024, 3) |       51 |      22.3 |      -438   |         280.2 |
| (2024, 4) |       46 |      10.7 |      -233   |         -33.7 |
| (2025, 1) |       51 |      12.9 |      -252.2 |        -110.8 |
| (2025, 2) |       42 |      28.5 |      -679   |         327.1 |
| (2025, 3) |       74 |      -7.3 |        98.8 |         262.2 |
| (2025, 4) |       45 |     -17.3 |       384.1 |         191.3 |
| (2026, 1) |       48 |      40.7 |      -848.1 |          22.3 |
| (2026, 2) |       81 |      55.6 |      -686.1 |         313.7 |
| (2026, 3) |       55 |      28.9 |      -525.2 |         159.9 |
| (2026, 4) |       25 |      -2.7 |       108.9 |          93.2 |


### 4c. Best-of-N null: the same test on 1,980 random level sets of the same density (990 offset +-80 pts, 990 shuffled-day offsets); n tested by ZL-1 = 818 appended cells (plus about 1,000 including unappended screens)
V13Y best-of-N null: families 1980 (offset 990 , shuffled-day 990 ); flagged taken trades null mean 600 vs BT 1035
| frame   | stat                |    BT_k |   null_median |   null_p99 |   null_max |   rank |
|:--------|:--------------------|--------:|--------------:|-----------:|-----------:|-------:|
| none    | L3M                 |  30.431 |         0.688 |     31.637 |     55.382 |  0.014 |
| none    | L6M                 |  69.777 |       -11.394 |     37.597 |     68.464 |  0.001 |
| none    | HOLD                |  74.915 |       -14.522 |     58.264 |     94.38  |  0.003 |
| none    | MID                 |  17.872 |         4.684 |     41.101 |     53.861 |  0.19  |
| none    | PRE                 | 103.432 |        -5.005 |     73.671 |    102.55  |  0.001 |
| none    | X                   |  50.13  |       -19.985 |     28.435 |     50.628 |  0.001 |
| none    | min(L6M,HOLD,PRE)   |  69.777 |       -29.481 |     16.19  |     37.365 |  0.001 |
| none    | min(L6M,HOLD,PRE,X) |  50.13  |       -37.205 |      0.265 |     17.166 |  0.001 |
| lock12  | L3M                 |  24.762 |         0.319 |     26.611 |     35.034 |  0.014 |
| lock12  | L6M                 |  70.142 |       -10.199 |     29.262 |     46.443 |  0.001 |
| lock12  | HOLD                | 107.054 |        -4.116 |     48.753 |     78.477 |  0.001 |
| lock12  | MID                 |  47.301 |        10.561 |     41.008 |     59.21  |  0.002 |
| lock12  | PRE                 | 123.118 |        -1.459 |     70.731 |     97.196 |  0.001 |
| lock12  | X                   |  66.28  |        -0.205 |     41.772 |     67.912 |  0.001 |
| lock12  | min(L6M,HOLD,PRE)   |  70.142 |       -21.019 |     14.643 |     27.022 |  0.001 |
| lock12  | min(L6M,HOLD,PRE,X) |  66.28  |       -23.617 |      6.969 |     15.397 |  0.001 |


### 4d. Plateau over the definition (144 configs) and purged walk-forward 2024-01..2026-10
### lock None: parameter plateau of the flip-level skip (saved $k = -sum of the flagged rows' base net; 144 configs = swing ['5m', '15m', '1h'] x break [5, 10, 15, 20] x keep ['1h', '4h', '24h'] x reach [20, 30, 40, 60])

share of configs with positive saved dollars: L6M 76%, HOLD 85%, MID 90%, PRE 66%, X' 87%; all four of L6M/HOLD/PRE/X': 42%

median saved $k by swing timeframe:
| TF   |   L6M |   HOLD |   PRE |   X' |
|:-----|------:|-------:|------:|-----:|
| 15m  |  14.1 |   15.2 |  26   | 10.6 |
| 1h   |   1.7 |    8.4 |  -0.6 |  8.5 |
| 5m   |  35.3 |   28   |  28.9 | 15.9 |

median saved $k by F:
|   F |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|   5 |  11.9 |   11.4 |   6.3 |  7.5 |
|  10 |  10.9 |    8.4 |  28.8 |  8.9 |
|  15 |  12   |   22.6 |   8.8 | 15.1 |
|  20 |  10.7 |   19.4 |   2.9 | 14.4 |

median saved $k by keep:
| keep   |   L6M |   HOLD |   PRE |   X' |
|:-------|------:|-------:|------:|-----:|
| 1h     |   5.1 |    8.3 |  19   |  6.8 |
| 24h    |  18.1 |   32.4 | -33.5 | 21.5 |
| 4h     |  20.4 |   21.3 |  41.4 | 10.7 |

median saved $k by D:
|   D |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|  20 |   7.4 |    5.6 |   8.8 | 10.5 |
|  30 |   9   |    9.3 |   6.7 | 10.7 |
|  40 |  11.8 |   25.1 |   1.9 | 11   |
|  60 |  12.8 |   20   |  22.8 |  8   |

reference config (5m, break 10, 4h, reach 40):
| TF   |   F | keep   |   D |   n_flag |   L6M |   HOLD |   MID |   PRE |   X' |   hit_all |
|:-----|----:|:-------|----:|---------:|------:|-------:|------:|------:|-----:|----------:|
| 5m   |  10 | 4h     |  40 |     1104 |  72.3 |   77.5 |  17.4 |  98.2 | 33.7 |     184.1 |

**Walk-forward (12-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  46.1 |   56.2 |   6.6 |       2.1 |  54.2 |
| fixed reference config                           |  72.3 |   77.5 |  17.4 |      45.7 | 137.4 |
| mean of all 144 configs (random choice)          |  18.7 |   26.1 |  10.1 |      12.8 |  33.1 |
| best config in hindsight each month              | 205.5 |  393.2 | 109.4 |     601.9 | 928.2 |

months with positive walk-forward saving: 15 / 31 active; fixed-config positive months 18 / 31

most-chosen configs: ('5m', np.int64(15), '4h', np.int64(60)) x7; ('5m', np.int64(10), '4h', np.int64(30)) x4; ('15m', np.int64(15), '4h', np.int64(60)) x4; ('15m', np.int64(20), '24h', np.int64(40)) x4

**Walk-forward (6-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  23.8 |   54.6 |   4.2 |      52.8 |  51.4 |
| fixed reference config                           |  72.3 |   77.5 |  17.4 |      52   | 143.7 |
| mean of all 144 configs (random choice)          |  18.7 |   26.1 |  10.1 |       1   |  21.4 |
| best config in hindsight each month              | 205.5 |  393.2 | 109.4 |     661.3 | 987.7 |

months with positive walk-forward saving: 18 / 34 active; fixed-config positive months 19 / 34

most-chosen configs: ('5m', np.int64(15), '4h', np.int64(60)) x5; ('15m', np.int64(20), '24h', np.int64(40)) x5; ('5m', np.int64(20), '4h', np.int64(60)) x3; ('5m', np.int64(15), '4h', np.int64(20)) x2

### lock 12R: parameter plateau of the flip-level skip (saved $k = -sum of the flagged rows' base net; 144 configs = swing ['5m', '15m', '1h'] x break [5, 10, 15, 20] x keep ['1h', '4h', '24h'] x reach [20, 30, 40, 60])

share of configs with positive saved dollars: L6M 83%, HOLD 90%, MID 85%, PRE 77%, X' 99%; all four of L6M/HOLD/PRE/X': 64%

median saved $k by swing timeframe:
| TF   |   L6M |   HOLD |   PRE |   X' |
|:-----|------:|-------:|------:|-----:|
| 15m  |  17.3 |   24.2 |  19.9 | 15.4 |
| 1h   |   1.6 |    6.1 |  -0.2 |  5.8 |
| 5m   |  28.5 |   48.5 |  49.2 | 34.4 |

median saved $k by F:
|   F |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|   5 |  12.6 |   12.3 |  21   | 15.3 |
|  10 |  11.1 |   14.2 |  33   | 34.7 |
|  15 |  13.6 |   22.6 |  17.5 | 30.8 |
|  20 |  14.5 |   21.7 |  17   | 16.2 |

median saved $k by keep:
| keep   |   L6M |   HOLD |   PRE |   X' |
|:-------|------:|-------:|------:|-----:|
| 1h     |   9.1 |   11.7 |  14.7 |  4.8 |
| 24h    |  13.4 |   29.7 |   7.3 | 39.2 |
| 4h     |  25   |   30.7 |  69.7 | 14.7 |

median saved $k by D:
|   D |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|  20 |  11.1 |   13.1 |  20.7 | 21   |
|  30 |   8.3 |   12.9 |  18.9 | 16.7 |
|  40 |  13.6 |   19   |  17.6 | 18.9 |
|  60 |  18.6 |   24.2 |  22.5 | 20.9 |

reference config (5m, break 10, 4h, reach 40):
| TF   |   F | keep   |   D |   n_flag |   L6M |   HOLD |   MID |   PRE |   X' |   hit_all |
|:-----|----:|:-------|----:|---------:|------:|-------:|------:|------:|-----:|----------:|
| 5m   |  10 | 4h     |  40 |      750 |  72.7 |  109.6 |  43.9 | 117.9 | 58.1 |     276.4 |

**Walk-forward (12-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  25   |   44.2 |  37.3 |      86   | 134.2 |
| fixed reference config                           |  72.7 |  109.6 |  43.9 |      64.9 | 189.9 |
| mean of all 144 configs (random choice)          |  18.9 |   31.7 |  13.2 |      22.2 |  51.9 |
| best config in hindsight each month              | 175.2 |  331.1 |  91.4 |     532.4 | 808.1 |

months with positive walk-forward saving: 19 / 31 active; fixed-config positive months 22 / 31

most-chosen configs: ('5m', np.int64(10), '4h', np.int64(60)) x9; ('5m', np.int64(15), '4h', np.int64(60)) x5; ('15m', np.int64(15), '24h', np.int64(60)) x4; ('15m', np.int64(20), '24h', np.int64(40)) x3

**Walk-forward (6-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  83.8 |  125.5 |  34.9 |      81.7 | 179.6 |
| fixed reference config                           |  72.7 |  109.6 |  43.9 |      95.4 | 220.4 |
| mean of all 144 configs (random choice)          |  18.9 |   31.7 |  13.2 |      20.2 |  50   |
| best config in hindsight each month              | 175.2 |  331.1 |  91.4 |     591.2 | 866.9 |

months with positive walk-forward saving: 23 / 34 active; fixed-config positive months 25 / 34

most-chosen configs: ('5m', np.int64(15), '4h', np.int64(60)) x5; ('5m', np.int64(10), '4h', np.int64(20)) x3; ('5m', np.int64(20), '4h', np.int64(60)) x3; ('15m', np.int64(20), '24h', np.int64(40)) x3

### 4e. Phase / placebo checks on the engine (maxDD and dollars)
## V13Y checks
### phase-averaged (lock-reset week key shifted -2..+2): dollar delta per window = cell minus base, maxDD cut, 8 same-volume draws per phase
**lock None**
| window   |   phases |   total_dollar_delta_k_mean |   dollar_min |   dollar_max |   phases_positive |   maxDD_cut_mean |   cut_min |   cut_max |   placebo_dollar_k |   placebo_cut |
|:---------|---------:|----------------------------:|-------------:|-------------:|------------------:|-----------------:|----------:|----------:|-------------------:|--------------:|
| L3M      |        5 |                      21.573 |       17.8   |       23.334 |                 5 |            0.117 |     0.098 |     0.159 |            -25.27  |        -0.203 |
| L6M      |        5 |                      49.4   |       41.021 |       63.512 |                 5 |           -0.101 |    -0.178 |     0.05  |            -40.546 |         0.042 |
| HOLD     |        5 |                      96.007 |       72.152 |      125.092 |                 5 |           -0.095 |    -0.178 |     0.081 |            -83.528 |        -0.031 |
| MID      |        5 |                      33.397 |       22.111 |       45.878 |                 5 |            0.248 |    -0.014 |     0.422 |            -13.516 |        -0.36  |
| PRE      |        5 |                      96.356 |       59.669 |      141.359 |                 5 |            0.026 |    -0.038 |     0.096 |            -41.121 |        -0.01  |
| X'       |        5 |                      29.802 |       13.472 |       49.552 |                 5 |           -0.11  |    -0.364 |     0.073 |            -15.454 |        -0.024 |

**lock 12R**
| window   |   phases |   total_dollar_delta_k_mean |   dollar_min |   dollar_max |   phases_positive |   maxDD_cut_mean |   cut_min |   cut_max |   placebo_dollar_k |   placebo_cut |
|:---------|---------:|----------------------------:|-------------:|-------------:|------------------:|-----------------:|----------:|----------:|-------------------:|--------------:|
| L3M      |        5 |                      16.477 |       11.901 |       25.063 |                 5 |            0.17  |     0.025 |     0.333 |            -10.627 |        -0.117 |
| L6M      |        5 |                      14.459 |      -82.91  |       97.104 |                 3 |           -0.223 |    -0.518 |     0.082 |            -30.881 |        -0.07  |
| HOLD     |        5 |                      17.26  |     -158.461 |      234.399 |                 3 |           -0.1   |    -0.414 |     0.356 |            -19.098 |        -0.077 |
| MID      |        5 |                     -16.011 |      -84.029 |       37.108 |                 2 |           -0.005 |    -0.498 |     0.205 |            -12.816 |        -0.269 |
| PRE      |        5 |                     100.942 |      -47.637 |      239.592 |                 4 |           -0.008 |    -0.312 |     0.24  |            -12.275 |         0.012 |
| X'       |        5 |                      33.468 |       -6.318 |       69.312 |                 4 |            0.066 |    -0.156 |     0.243 |            -12.096 |         0.052 |

### maxDD / dollar placebos (A same-volume stratified, B random rows same count per day, C other-day same book x session)
**lock None**
| kind   |   draws | window   |   cell_cut |   placebo_cut |   rank_cut |   cell_dmean_k |   placebo_dmean_k |   rank_dmean |
|:-------|--------:|:---------|-----------:|--------------:|-----------:|---------------:|------------------:|-------------:|
| A      |      40 | L3M      |      0.102 |        -0.286 |      0.195 |          1.369 |            -1.774 |        0.171 |
| A      |      40 | L6M      |      0.05  |        -0.009 |      0.512 |          2.352 |            -1.358 |        0.098 |
| A      |      40 | HOLD     |      0.081 |        -0.136 |      0.146 |          2.406 |            -1.125 |        0.024 |
| A      |      40 | MID      |      0.288 |        -0.366 |      0.024 |          3.823 |            -0.258 |        0.073 |
| A      |      40 | PRE      |      0.009 |        -0.128 |      0.195 |          1.128 |            -0.823 |        0.024 |
| A      |      40 | X'       |     -0.097 |        -0.085 |      0.585 |          0.396 |             0.111 |        0.39  |
| B      |      40 | L3M      |      0.102 |        -0.1   |      0.195 |          1.369 |            -1.236 |        0.073 |
| B      |      40 | L6M      |      0.05  |        -0.002 |      0.415 |          2.352 |            -0.561 |        0.024 |
| B      |      40 | HOLD     |      0.081 |        -0.029 |      0.122 |          2.406 |            -0.06  |        0.024 |
| B      |      40 | MID      |      0.288 |        -0.084 |      0.073 |          3.823 |             1.127 |        0.146 |
| B      |      40 | PRE      |      0.009 |        -0.037 |      0.293 |          1.128 |            -0.04  |        0.024 |
| B      |      40 | X'       |     -0.097 |         0.059 |      0.878 |          0.396 |             0.776 |        0.659 |
| C      |      40 | L3M      |      0.102 |        -0.222 |      0.195 |          1.369 |            -1.596 |        0.146 |
| C      |      40 | L6M      |      0.05  |         0.003 |      0.439 |          2.352 |            -1.269 |        0.049 |
| C      |      40 | HOLD     |      0.081 |        -0.082 |      0.195 |          2.406 |            -1.001 |        0.024 |
| C      |      40 | MID      |      0.288 |        -0.359 |      0.073 |          3.823 |            -0.43  |        0.195 |
| C      |      40 | PRE      |      0.009 |        -0.148 |      0.146 |          1.128 |            -0.919 |        0.073 |
| C      |      40 | X'       |     -0.097 |        -0.129 |      0.537 |          0.396 |             0.24  |        0.537 |

**lock 12R**
| kind   |   draws | window   |   cell_cut |   placebo_cut |   rank_cut |   cell_dmean_k |   placebo_dmean_k |   rank_dmean |
|:-------|--------:|:---------|-----------:|--------------:|-----------:|---------------:|------------------:|-------------:|
| A      |      40 | L3M      |      0.152 |        -0.39  |      0.073 |          1.075 |            -0.718 |        0.341 |
| A      |      40 | L6M      |      0.082 |        -0.292 |      0.146 |          3.596 |            -0.23  |        0.122 |
| A      |      40 | HOLD     |      0.356 |        -0.059 |      0.024 |          4.508 |             0.559 |        0.049 |
| A      |      40 | MID      |      0.204 |         0.015 |      0.22  |          3.092 |             1.561 |        0.293 |
| A      |      40 | PRE      |      0.24  |         0.169 |      0.39  |          3.195 |            -0.688 |        0.024 |
| A      |      40 | X'       |      0     |        -0.073 |      0.39  |          1.575 |            -0.587 |        0.049 |
| B      |      40 | L3M      |      0.152 |        -0.246 |      0.098 |          1.075 |            -0.085 |        0.268 |
| B      |      40 | L6M      |      0.082 |        -0.251 |      0.049 |          3.596 |             0.517 |        0.073 |
| B      |      40 | HOLD     |      0.356 |         0.037 |      0.049 |          4.508 |             1.187 |        0.049 |
| B      |      40 | MID      |      0.204 |         0.005 |      0.195 |          3.092 |             1.085 |        0.146 |
| B      |      40 | PRE      |      0.24  |         0.176 |      0.415 |          3.195 |             0.251 |        0.049 |
| B      |      40 | X'       |      0     |        -0.032 |      0.805 |          1.575 |            -0.052 |        0.049 |
| C      |      40 | L3M      |      0.152 |        -0.451 |      0.073 |          1.075 |             0.183 |        0.415 |
| C      |      40 | L6M      |      0.082 |        -0.316 |      0.098 |          3.596 |             0.357 |        0.098 |
| C      |      40 | HOLD     |      0.356 |        -0.017 |      0.049 |          4.508 |             1.283 |        0.098 |
| C      |      40 | MID      |      0.204 |         0.029 |      0.341 |          3.092 |             2.638 |        0.463 |
| C      |      40 | PRE      |      0.24  |         0.173 |      0.415 |          3.195 |            -0.854 |        0.049 |
| C      |      40 | X'       |      0     |        -0.027 |      0.488 |          1.575 |            -0.185 |        0.098 |

Reading of 4e: with the lock off the dollar delta of the engine is positive in all 5 lock phases in every window (L6M +49k, HOLD +96k, PRE +96k, X' +30k, MID +33k, L3M +22k; same-volume random skips lose -14..-84k) and its weekly-mean placebo ranks are 0.02-0.10 in L6M, HOLD and PRE (0.07-0.2 in L3M and MID, 0.4-0.66 in X'); the maxDD cut averaged over the phases is +12% L3M, +25% MID, but -10% L6M, -10% HOLD, +3% PRE, -11% X' (cut ranks 0.12-0.58 except MID 0.02-0.07), i.e. NOT a drawdown cut. With the 12R lock the engine dollars are lock-phase noise (L6M from -83k to +97k across the 5 phases, HOLD -158k..+234k, positive in only 3 of 5 phases), so the 12R-frame engine numbers are not usable evidence either way; the row-level dollars (4a) do not depend on the lock phase.

## 5. By book x session (V13Y)

| book_session   | window   |   n |   saved_k |   ci90_lo_k |   ci90_hi_k |   mean_flagged |
|:---------------|:---------|----:|----------:|------------:|------------:|---------------:|
| HM|0           | HOLD     |  33 |      -8.4 |       -23   |         7.5 |          255.2 |
| HM|0           | ALL      |  94 |      13.9 |       -21.3 |        51   |         -147.7 |
| HM|3           | HOLD     |   4 |       0.8 |        -1   |         2.9 |         -190.8 |
| HM|3           | ALL      |  33 |       5.1 |        -1   |        11.4 |         -153.3 |
| KB|0           | HOLD     |  82 |       1.9 |       -22.7 |        21.1 |          -22.8 |
| KB|0           | ALL      | 199 |      31.9 |        -3.1 |        66.6 |         -160.4 |
| KB|1           | HOLD     |  66 |      21.1 |         9.2 |        33.2 |         -320.1 |
| KB|1           | ALL      | 189 |       9.2 |       -17.5 |        37.8 |          -48.9 |
| KB|3           | HOLD     |  15 |       6.4 |         1.6 |        11.7 |         -429.2 |
| KB|3           | ALL      |  75 |       0.4 |       -14   |        15.2 |           -5.1 |
| KB|4           | HOLD     |   9 |       4.9 |        -0.7 |        11   |         -541.7 |
| KB|4           | ALL      |  44 |       8.1 |        -6.3 |        22.2 |         -183.4 |
| MV|1           | HOLD     |  37 |      -2.3 |       -18.1 |        12.1 |           61.3 |
| MV|1           | ALL      |  60 |       2.3 |       -18.5 |        22.7 |          -38.2 |
| MV|3           | HOLD     |   5 |       1   |        -1.3 |         3.4 |         -208.9 |
| MV|3           | ALL      |  18 |       4.4 |        -1.6 |        10.5 |         -245   |
| PB|0           | HOLD     |   5 |       2.2 |        -3.8 |         8.6 |         -436.3 |
| PB|0           | ALL      |  10 |      -3.4 |       -12.6 |         5.3 |          342.6 |
| PE|0           | HOLD     |  38 |      16.5 |       -24.5 |        62.2 |         -434.7 |
| PE|0           | ALL      | 124 |      90.1 |         1.1 |       189.3 |         -727   |
| PE|1           | HOLD     |  32 |      13.9 |       -15.1 |        45.1 |         -435   |
| PE|1           | ALL      |  77 |      12.7 |       -37.2 |        65.3 |         -164.7 |
| PE|3           | HOLD     |   1 |     -11.5 |       -34.4 |         0   |        11479.6 |
| PE|3           | ALL      |  15 |      -5.4 |       -33.1 |        21.9 |          361.1 |
| SM|0           | HOLD     |  10 |       6.2 |        -4.4 |        16.8 |         -622   |
| SM|0           | ALL      |  28 |      13.1 |       -12.9 |        38.5 |         -468.3 |
| SM|1           | HOLD     |  22 |      22.1 |         3.3 |        42.7 |        -1005.9 |
| SM|1           | ALL      |  69 |      20.9 |       -10.3 |        52.2 |         -302.6 |



## 6. Interaction with the shipped zone layer and with the other mean-type lines
 (candidate rows: BT 2819, layer 12939, intersection 1126, Jaccard 0.077; 39.9% of BT rows are already in the layer). Saved $k of skipping each set on the V13Y taken trades (layer rows are already halved in the base):
| set                                           |    n |   L6M |   HOLD |   PRE |    X' |
|:----------------------------------------------|-----:|------:|-------:|------:|------:|
| BT alone                                      | 1035 |  69.8 |   74.9 | 103.4 |  50.1 |
| shipped layer (7 lines D20 + OTE62 D30) alone | 3332 | -72.6 |  -85.7 |  90.8 | -24.5 |
| BT & layer                                    |  447 |   3.8 |   16.1 |  21.1 |  29.7 |
| BT minus layer                                |  588 |  66   |   58.8 |  82.3 |  20.5 |
| layer minus BT                                | 2885 | -76.5 | -101.8 |  69.8 | -54.2 |
| union                                         | 3920 |  -6.7 |  -26.9 | 173.2 |  -4   |


## 8. Overlap with the other mean-type lines (88,490 candidate rows): Jaccard of the flagged sets, share of BT rows inside the other set
|                              |   BT swing flip  |   large print >= |   TCD TCD_ext D4 |   TCD TCD_div D4 |   TCD TCD_burst  |   Keltner upper  |
|:-----------------------------|-----------------:|-----------------:|-----------------:|-----------------:|-----------------:|-----------------:|
| BT swing flip D40            |            1     |            0.038 |            0.018 |            0.003 |            0.013 |            0.008 |
| large print >=25 lots 4h D40 |            0.038 |            1     |            0.05  |            0.03  |            0.017 |            0.011 |
| TCD TCD_ext D40              |            0.018 |            0.05  |            1     |            0.006 |            0.01  |            0.011 |
| TCD TCD_div D40              |            0.003 |            0.03  |            0.006 |            1     |            0.004 |            0.008 |
| TCD TCD_burst D40            |            0.013 |            0.017 |            0.01  |            0.004 |            1     |            0.004 |
| Keltner upper 4h D20 (coded) |            0.008 |            0.011 |            0.011 |            0.008 |            0.004 |            1     |
rows flagged: BT swing flip D40 2819, large print >=25 lots 4h D40 5110, TCD TCD_ext D40 15965, TCD TCD_div D40 3318, TCD TCD_burst D40 695, Keltner upper 4h D20 (coded) 1177
share of BT rows also flagged by: large print >=25 lots 4h D40 10.3%, TCD TCD_ext D40 11.8%, TCD TCD_div D40 0.6%, TCD TCD_burst D40 1.6%, Keltner upper 4h D20 (coded) 1.1%

### saved $k on V13X taken trades, lock None
| other                        | set            |   L6M |   HOLD |    PRE |    X' |    n |
|:-----------------------------|:---------------|------:|-------:|-------:|------:|-----:|
| large print >=25 lots 4h D40 | BT alone       |  69.8 |   74.9 |  103.4 |  50.1 | 1035 |
| large print >=25 lots 4h D40 | other alone    |  95.4 |  104.7 |    9.2 | -51.9 | 1204 |
| large print >=25 lots 4h D40 | union          | 169.9 |  193.3 |  109.6 | -17.5 | 2124 |
| large print >=25 lots 4h D40 | BT minus other |  74.5 |   88.6 |  100.3 |  34.4 |  920 |
| large print >=25 lots 4h D40 | other minus BT | 100.1 |  118.4 |    6.1 | -67.6 | 1089 |
| TCD TCD_ext D40              | BT alone       |  69.8 |   74.9 |  103.4 |  50.1 | 1035 |
| TCD TCD_ext D40              | other alone    |  33   | -121.1 | -520   | 117.2 | 3594 |
| TCD TCD_ext D40              | union          | 103.8 |  -43.2 | -403.9 | 160.1 | 4535 |
| TCD TCD_ext D40              | BT minus other |  70.7 |   77.9 |  116.1 |  42.9 |  941 |
| TCD TCD_ext D40              | other minus BT |  34   | -118.1 | -507.3 | 109.9 | 3500 |
| TCD TCD_div D40              | BT alone       |  69.8 |   74.9 |  103.4 |  50.1 | 1035 |
| TCD TCD_div D40              | other alone    | -54.5 |  -80.8 |  -19   |  19.2 |  633 |
| TCD TCD_div D40              | union          |  15.2 |   -5.9 |   81.6 |  68.4 | 1660 |
| TCD TCD_div D40              | BT minus other |  69.8 |   74.9 |  100.5 |  49.2 | 1027 |
| TCD TCD_div D40              | other minus BT | -54.5 |  -80.8 |  -21.9 |  18.3 |  625 |
| TCD TCD_burst D40            | BT alone       |  69.8 |   74.9 |  103.4 |  50.1 | 1035 |
| TCD TCD_burst D40            | other alone    |   0.2 |  -10.2 |   11   | -44   |  164 |
| TCD TCD_burst D40            | union          |  70   |   66   |  115.4 |   5.4 | 1182 |
| TCD TCD_burst D40            | BT minus other |  69.8 |   76.2 |  104.4 |  49.4 | 1018 |
| TCD TCD_burst D40            | other minus BT |   0.2 |   -8.9 |   12   | -44.8 |  147 |
| Keltner upper 4h D20 (coded) | BT alone       |  69.8 |   74.9 |  103.4 |  50.1 | 1035 |
| Keltner upper 4h D20 (coded) | other alone    |   8.6 |    8.9 |   -6.9 |  -6.2 |  189 |
| Keltner upper 4h D20 (coded) | union          |  75.2 |   80.6 |   91.1 |  35.7 | 1214 |
| Keltner upper 4h D20 (coded) | BT minus other |  66.5 |   71.7 |   98   |  41.9 | 1025 |
| Keltner upper 4h D20 (coded) | other minus BT |   5.4 |    5.7 |  -12.3 | -14.5 |  179 |

### saved $k on V13X taken trades, lock 12R
| other                        | set            |   L6M |   HOLD |    PRE |    X' |    n |
|:-----------------------------|:---------------|------:|-------:|-------:|------:|-----:|
| large print >=25 lots 4h D40 | BT alone       |  70.1 |  107.1 |  123.1 |  66.3 |  704 |
| large print >=25 lots 4h D40 | other alone    |  57.2 |   60.9 |  104.5 | -55.7 |  795 |
| large print >=25 lots 4h D40 | union          | 128.6 |  176.6 |  220.1 |   4.1 | 1416 |
| large print >=25 lots 4h D40 | BT minus other |  71.5 |  115.8 |  115.6 |  59.8 |  621 |
| large print >=25 lots 4h D40 | other minus BT |  58.5 |   69.6 |   97   | -62.2 |  712 |
| TCD TCD_ext D40              | BT alone       |  70.1 |  107.1 |  123.1 |  66.3 |  704 |
| TCD TCD_ext D40              | other alone    |  24.2 |  -65.9 | -222.7 | 125.6 | 2377 |
| TCD TCD_ext D40              | union          |  93   |   32.9 | -107.4 | 184.3 | 3022 |
| TCD TCD_ext D40              | BT minus other |  68.9 |   98.8 |  115.4 |  58.7 |  645 |
| TCD TCD_ext D40              | other minus BT |  22.9 |  -74.1 | -230.5 | 118   | 2318 |
| TCD TCD_div D40              | BT alone       |  70.1 |  107.1 |  123.1 |  66.3 |  704 |
| TCD TCD_div D40              | other alone    | -26.4 |  -34   |   -2   |  -3   |  417 |
| TCD TCD_div D40              | union          |  43.7 |   73.1 |  121.1 |  62.3 | 1117 |
| TCD TCD_div D40              | BT minus other |  70.1 |  107.1 |  123.1 |  65.3 |  700 |
| TCD TCD_div D40              | other minus BT | -26.4 |  -34   |   -2   |  -4   |  413 |
| TCD TCD_burst D40            | BT alone       |  70.1 |  107.1 |  123.1 |  66.3 |  704 |
| TCD TCD_burst D40            | other alone    |  -6.3 |   -7.4 |   16   | -40.6 |  133 |
| TCD TCD_burst D40            | union          |  63.8 |  101.6 |  138.9 |  24.2 |  824 |
| TCD TCD_burst D40            | BT minus other |  70.1 |  108.9 |  122.9 |  64.9 |  691 |
| TCD TCD_burst D40            | other minus BT |  -6.3 |   -5.5 |   15.8 | -42   |  120 |
| Keltner upper 4h D20 (coded) | BT alone       |  70.1 |  107.1 |  123.1 |  66.3 |  704 |
| Keltner upper 4h D20 (coded) | other alone    |   5.3 |    8.1 |   10.7 |   2.9 |  133 |
| Keltner upper 4h D20 (coded) | union          |  75.9 |  115.5 |  131.4 |  60.9 |  829 |
| Keltner upper 4h D20 (coded) | BT minus other |  70.5 |  107.5 |  120.7 |  58   |  696 |
| Keltner upper 4h D20 (coded) | other minus BT |   5.7 |    8.5 |    8.3 |  -5.4 |  125 |

## 7. What it does NOT do
It is not a drawdown cut: the phase-averaged maxDD cut is about 0 or negative in most windows (section 4e); the engine maxDD cut is large in some windows and absent in others and depends on the lock phase. It does not improve the library bracket outcome significantly in the recent windows (CI includes 0). It is not a protective stop, a size-up or a timing signal; it removes a class of entries. It has no L2 content. It has not been tested on the forward data.

## 8. What could make this wrong (checked and open)
 early = realised exit earlier than the library bracket exit (TH-L2 cut, take line, lock, trail):
| set       |     n |   early_exit_share |   mean_net_early |   mean_net_notearly |   loser_share |   library_stop_share |   mean_net |
|:----------|------:|-------------------:|-----------------:|--------------------:|--------------:|---------------------:|-----------:|
| flagged   |  1035 |              0.864 |         -283.667 |             357.169 |         0.564 |                0.519 |   -196.365 |
| unflagged | 17792 |              0.82  |         -127.73  |            1449.45  |         0.518 |                0.471 |    155.492 |

of 1035 flagged trades: 584 losers (sum -1017k) and 451 winners (sum 814k); losers exiting early 552 (sum -859k), losers at full library stop 32 (sum -158k)


* **Regime / timeframe**: 5-minute swings carry it; 15-minute and 1-hour swings give less in total (5m n=1,104, 15m 475, 1h 134 candidate trades; saved $ per flagged trade 167 / 232 / 95), i.e. the effect scales with the number of flip events, not with a better per-trade edge at 5m. Whether the effect is a property of recent-swing levels or just of "price has already moved 10+ pts past a recent extreme" (a trend/overextension filter) is NOT separated.
* **Start of events**: BT events start 2023-08. Over 2023-04..07 the path-based version of the same rule flagged 69 trades and saved -15.9k (the opposite sign); excluding those months the totals are unchanged (200.0k vs 203.2k).
* **Dependence on the base exits**: 86% of the flagged trades are closed early by the base (TH-L2 loss cut, take lines, locks) and 552 of the 584 flagged losers (-859k) exit before the library stop; only 32 losers (-158k) run to the full stop. The flagged winners that run to the library exit earn +357 per trade vs +1,449 for unflagged: the take lines cut them. So the dollar effect depends on the TH-L2 / take-line exits being what they are; a different exit stack changes it. The library bracket test agrees in sign in 5 of 6 windows but with wide CIs.
* **Which books/sessions carry it**: broad, not one book: the largest are PE Asia (+90k over the full sample, CI [1, 189]), KB Asia and London, SM London; per book x session CIs are mostly wide (only a few exclude 0). Asia + London carry about 80% of the flagged trades.
* **Stability over time**: all four calendar years positive, but 2025 is weak (+28k) and 2024-Q4, 2025-Q3, 2025-Q4 are negative (flagged trades then had a positive mean); 2026 carries about 45% of the total.
* **Multiplicity**: priced by the null in 4c (beats all 1,980 same-density nulls); the definition grid (144 configs) is a second selection layer handled by the walk-forward.
* **Not yet done**: forward data; BT-specific 1-s/3-s delay; per vol-tercile table for the V13Y rows (on V13X it came from the middle and top terciles); the V13Y noise band for the maxDD columns (Z3 publishes).

## 9. Shadow log fields
See autopilot/FORWARD_SHADOW_ZONES_SPEC.md, section "ZL-1: BT swing flip" (flag, flip level price/age/break size, distance to entry/target, would_skip, trade_taken, base_net_dollars, exit_type; plus the flip-level creation log for the reproducibility check).

Sources: out/zl_new (/mnt/l2/l2vast/ds3_zones3_new/zl1): base_rows_ynone.pkl, base_rows_ylock12.pkl, bnull2Y_*.csv, plateau_Y_*.csv, wf_Y_*.csv, res_a1/a2/b1/b2 pkl, pager_parts.md. Code: l2vast/ds3/code/zones3/zl1 (zrow.py zrowan_y.py zwf_y.py zbnull2_y.py zpager.py zpage_cand.py zwrite_cand.py) and l2vast/ds3/code/zl (zl1_build.py, zl_btcfg.py, zl_bt_audit.py).


## 10. Exit-set robustness (is the edge a property of the zone or of its interaction with the live exits?)
## Exit-set robustness of the BT swing-flip saved dollars (V13Y engine, lock None, D40 5-min swing flip skip; saved $k = minus the flagged taken trades' net; rank = share of 100 random same-count-per-day sets at least as good)
| variant                  |   taken |   flagged |   flag_mean |   unflag_mean |   base_total_M |    L3M |     L6M |    HOLD |    MID |     PRE |     X' |   rank_L6M |   rank_HOLD |   rank_PRE |   rank_X' |
|:-------------------------|--------:|----------:|------------:|--------------:|---------------:|-------:|--------:|--------:|-------:|--------:|-------:|-----------:|------------:|-----------:|----------:|
| V13Y base (exact exits)  |   18827 |      1035 |    -196.365 |       155.492 |          2.563 | 30.431 |  69.777 |  74.915 | 17.872 | 103.432 | 50.13  |       0.01 |       0.04  |      0.109 |     0.287 |
| V13X exits (defect)      |   18716 |      1032 |    -203.151 |       138.17  |          2.234 | 38.45  |  86.234 |  99.631 | 29.867 |  89.363 | 40.829 |       0.01 |       0.02  |      0.168 |     0.317 |
| (a) TH-L2 loss cut OFF   |   16000 |       873 |    -397.583 |       277.193 |          3.846 | 85.072 | 168.584 | 197.359 | 56.752 |  64.912 | 90.838 |       0.01 |       0.03  |      0.297 |     0.158 |
| (b) take lines OFF       |   18203 |      1011 |    -286.017 |       220.19  |          3.496 | 71.914 | 120.85  | 164.649 | 10.424 |  82.429 | 66.456 |       0.01 |       0.01  |      0.079 |     0.277 |
| (c) both OFF             |   16000 |       873 |    -397.583 |       277.193 |          3.846 | 85.072 | 168.584 | 197.359 | 56.752 |  64.912 | 90.838 |       0.01 |       0.03  |      0.297 |     0.158 |
| (e) take thresholds x0.5 |   19790 |      1077 |    -145.773 |       112.408 |          1.946 | 26.393 |  53.411 |  37.002 |  7.499 |  75.467 | 53.41  |       0.03 |       0.079 |      0.079 |     0.287 |
| (e) x0.75                |   19181 |      1041 |    -177.942 |       116.33  |          1.925 | 28.296 |  71.456 |  69.645 |  6.378 |  86.806 | 48.845 |       0.03 |       0.02  |      0.178 |     0.337 |
| (e) x1.25                |   18352 |      1014 |    -263.501 |       194.821 |          3.111 | 59.203 | 111.34  | 141.476 | 23.435 |  81.288 | 56.737 |       0.01 |       0.01  |      0.129 |     0.228 |
| (e) x1.5                 |   18316 |      1016 |    -265.342 |       229.554 |          3.702 | 64.277 | 102.931 | 144.3   | 19.073 |  81.54  | 63.116 |       0.01 |       0.01  |      0.079 |     0.198 |

Per calendar year (saved $k):
| variant                  |   2023 |   2024 |   2025 |   2026 |
|:-------------------------|-------:|-------:|-------:|-------:|
| V13Y base (exact exits)  |   56.9 |   29.3 |   28   |   89.2 |
| V13X exits (defect)      |   50.4 |   24.7 |   13.8 |  120.7 |
| (a) TH-L2 loss cut OFF   |   60.5 |   36.9 |   42.4 |  207.2 |
| (b) take lines OFF       |   49.2 |   15.3 |   85.9 |  138.8 |
| (c) both OFF             |   60.5 |   36.9 |   42.4 |  207.2 |
| (e) take thresholds x0.5 |   45.3 |   16.2 |   40.6 |   55   |
| (e) x0.75                |   44   |   24.3 |   34.6 |   82.3 |
| (e) x1.25                |   40.4 |   39.7 |   48.7 |  138.3 |
| (e) x1.5                 |   45.8 |   16.6 |   85.4 |  121.8 |

Reading: the saved-dollar edge persists under every exit set tried and is LARGER when the live exits are removed: with the TH-L2 loss cut off the flagged trades average -$398 vs +$277 for the rest (L6M +169k, HOLD +197k, PRE +65k, X' +91k, all four years positive, 2026 +207k); with the take lines off alone -$286 vs +$220 (L6M +121k, HOLD +165k); with the take thresholds scaled x0.5..x1.5 the edge stays +53..+111k in L6M, +37..+144k in HOLD, +75..+87k in PRE, +49..+63k in X' (weakest at x0.5, where the lines exit most trades early, +37k in HOLD); against random same-count-per-day sets the L6M rank is 0.01-0.03 and the HOLD rank 0.01-0.08 in every variant, PRE 0.08-0.30 and X' 0.16-0.34 (not significant, same as the base). So the effect is a property of the flip-level zone, and the live exits dilute it (the flagged trades that reach the library exit win less, +357 vs +1,449, because the take lines cut them). Caveat: in this engine path variants (a) and (c) are identical (16,000 taken trades): the take lines are only injected together with the TH-L2 loss exits, so (a) is effectively 'no overlay exits' and cannot isolate 'loss cut off, lines on'.


## 11. Definition variants (ZL-1, V13Y taken trades, lock None, row-level saved $k = minus the flagged taken trades' net; D40 reach unless stated; base definition = 5-min swing, print break >= 10, 4 h keep, freshness 0.5 pt)
Windows: L6M 2026-05..10, HOLD 2025-11..2026-10, PRE 2024-02..2025-06, X' 2023-04..2024-01 (events exist from 2023-08), H1 = 2023-08..2024-12, H2 = 2025-01..2026-10. Nothing was fitted; every row is a separate definition on the same trades. File out/zl_new/zvar_rows.pkl, plot out/zl_new/bt_timeframe.png.

### 11a. Swing timeframe (fractal-5 on clock-aligned bars; events/month = flip events created per month, before the reach rule)
| variant   |   flagged_taken |   flag_mean |   per_trade_saved |   L6M |   HOLD |   PRE |    X |   H1_2023-08..2024-12 |   H2_2025-01..2026-10 |   ALL |   events_per_month |   candidate_rows |
|:----------|----------------:|------------:|------------------:|------:|-------:|------:|-----:|----------------------:|----------------------:|------:|-------------------:|-----------------:|
| TF 1m     |            2998 |       -55.2 |              55.2 |  -5.8 |   35.6 | 143.7 | 47.3 |                 131.2 |                  54.6 | 185.8 |             2607.4 |            12436 |
| TF 2m     |            1940 |       -24.3 |              24.3 |  30.4 |   48.4 |  79   | -6.6 |                  67.9 |                  32.6 | 100.5 |             1601.3 |             7203 |
| TF 3m     |            1529 |       -72.7 |              72.7 |  31.8 |   64.2 | 101.9 | -4   |                  75   |                  98.2 | 173.2 |             1182.5 |             5075 |
| TF 5m     |            1104 |      -166.8 |             166.8 |  72.3 |   77.5 |  98.2 | 33.7 |                  80.4 |                 119.7 | 200   |              786.5 |             3027 |
| TF 8m     |             768 |      -160.3 |             160.3 |  54.6 |   69   |  14.6 | 41.5 |                  44.6 |                  92.7 | 137.3 |              535   |             1902 |
| TF 10m    |             643 |      -245.6 |             245.6 |  52.4 |   53.8 |  40.5 | 63.9 |                  84.5 |                  78.9 | 163.5 |              443.4 |             1523 |
| TF 15m    |             475 |      -232.3 |             232.3 |  26.1 |   26   |  68.8 | 10.8 |                  32.2 |                  79.6 | 111.7 |              311.2 |             1062 |
| TF 1h     |             134 |       -94.8 |              94.8 |   2.2 |   15.2 |   0.3 |  9.2 |                  -4.2 |                  11.4 |   7.3 |               87.8 |              308 |
Reading: not monotone and not a clean peak. Saved dollars: 1m 186k, 2m 101k, 3m 173k, 5m 200k, 8m 137k, 10m 164k, 15m 112k, 1h 7k (all 2023-08..2026-10). The coarse side decays (15m 112k, 1h 7k); the fine side is noisy and changes character: 1m flags 2,998 trades at only $55 per trade, is negative in L6M (-6k) and gets 72% of its total from PRE and 2023-24; 3m-10m are all in the 137-200k band with $73-$246 per flagged trade. Dollars do not scale with events per month (1m has 3x the events of 5m and the same total; 10m has 56% of the events of 5m and 82% of the dollars): the 5m>>15m/1h statement is about a plateau 3-10 minutes, not a sharp peak at 5m.

### 11b. Direction (5-min base): which side of the book is blocked
| variant                                                      |   flagged_taken |   flag_mean |   per_trade_saved |   L6M |   HOLD |   PRE |    X |   H1_2023-08..2024-12 |   H2_2025-01..2026-10 |   ALL |
|:-------------------------------------------------------------|----------------:|------------:|------------------:|------:|-------:|------:|-----:|----------------------:|----------------------:|------:|
| all flagged                                                  |            1104 |      -166.8 |             166.8 |  72.3 |   77.5 |  98.2 | 33.7 |                  80.4 |                 119.7 | 200   |
| longs (blocked by resistance flips = swing lows broken down) |             577 |      -204.7 |             204.7 |  38.3 |   68.5 |  66.4 |  2.7 |                  36.9 |                  93.1 | 130   |
| shorts (blocked by support flips = swing highs broken up)    |             527 |      -125.3 |             125.3 |  34   |    8.9 |  31.8 | 31   |                  43.5 |                  26.5 |  70.1 |
Reading: both sides carry it, longs more. Longs are flagged by RESISTANCE flips (a swing low broken down, now above the entry): 577 trades, -$205 each, 130k in total (H1 37k, H2 93k, L6M 38k, HOLD 69k, X' 3k). Shorts are flagged by SUPPORT flips (a swing high broken up, now below the entry): 527 trades, -$125 each, 70k (H1 44k, H2 27k, HOLD only 9k, X' 31k). The long side dominates the recent windows; the short side is the more stable early one. Neither side alone is the whole effect.

### 11c. How the break is defined
| variant         |   flagged_taken |   flag_mean |   per_trade_saved |   L6M |   HOLD |   PRE |    X |   H1_2023-08..2024-12 |   H2_2025-01..2026-10 |   ALL |   events |
|:----------------|----------------:|------------:|------------------:|------:|-------:|------:|-----:|----------------------:|----------------------:|------:|---------:|
| break by print  |            1104 |      -166.8 |             166.8 |  72.3 |   77.5 |  98.2 | 33.7 |                  80.4 |                 119.7 | 200   |    34637 |
| break by close  |            1487 |      -148.5 |             148.5 |  82.1 |  115   |  85.3 | 42.2 |                  56.7 |                 174.1 | 230.8 |    28448 |
| break by retest |             243 |      -277.1 |             277.1 |  34.4 |   40.3 |  16.1 |  9.8 |                   5.6 |                  60.5 |  66.1 |    27090 |
Reading: a CLOSE of the 5-min bar beyond the swing by 10 pts works as well or better than a print (231k vs 200k; HOLD 115k, H2 174k; 1,487 vs 1,104 flagged trades, $149 vs $167 per trade), so the print/close choice is not critical and the close version is easier to compute from bars. Waiting for the RETEST (the level is only flagged after price has come back within 1 pt of it) loses most of the effect (66k, 243 trades, 5.6k in H1): the damage is done in the first move after the break, before any retest; the retested trades that remain are worse ($277 each) but too few.

### 11d. Validity (keep) and freshness
| variant                             |   flagged_taken |   flag_mean |   per_trade_saved |   L6M |   HOLD |   PRE |    X |   H1_2023-08..2024-12 |   H2_2025-01..2026-10 |   ALL |
|:------------------------------------|----------------:|------------:|------------------:|------:|-------:|------:|-----:|----------------------:|----------------------:|------:|
| keep 30m                            |              69 |       114.3 |            -114.3 | -13.2 |  -17.2 |  14.1 |  0.7 |                  22.3 |                 -23.9 |  -1.6 |
| keep 1h                             |             246 |      -250.6 |             250.6 |  -2.9 |   -1.3 |  66.6 |  2.7 |                  52.7 |                  12.6 |  65.3 |
| keep 2h                             |             591 |      -191.7 |             191.7 |  34.1 |   41.9 |  65.5 | 12.2 |                  81.5 |                  54   | 135.5 |
| keep 4h                             |            1104 |      -166.8 |             166.8 |  72.3 |   77.5 |  98.2 | 33.7 |                  80.4 |                 119.7 | 200   |
| keep 8h                             |            1734 |       -85.5 |              85.5 |  39.9 |   22.6 |  97.7 | 49.4 |                  91   |                  55   | 145.9 |
| keep 24h                            |            2430 |        19.1 |             -19.1 |  49.3 |   51.7 | -39.4 | -3.8 |                 -25.9 |                   4.2 | -21.7 |
| freshness away 0.0 pt               |            1104 |      -166.8 |             166.8 |  72.3 |   77.5 |  98.2 | 33.7 |                  80.4 |                 119.7 | 200   |
| freshness away 0.5 pt               |            1104 |      -166.8 |             166.8 |  72.3 |   77.5 |  98.2 | 33.7 |                  80.4 |                 119.7 | 200   |
| freshness away 2.0 pt               |            1104 |      -166.8 |             166.8 |  72.3 |   77.5 |  98.2 | 33.7 |                  80.4 |                 119.7 | 200   |
| freshness away 5.0 pt               |            1108 |      -177.8 |             177.8 |  72.3 |   77.5 | 111   | 33.7 |                  80.4 |                 132.5 | 212.9 |
| freshness away 10.0 pt              |            1164 |      -185.8 |             185.8 |  82   |   94   | 112.9 | 31.4 |                  90.8 |                 142.5 | 233.3 |
| freshness away none (never expires) |            2810 |      -121.2 |             121.2 |  25   |  119.6 | 197.7 | 58.3 |                 142.2 |                 209.8 | 352.1 |
Reading: the 4 h validity is a real optimum, not a plateau: 30 min and 1 h are too short (negative to flat), 2 h 136k, 4 h 200k, 8 h 146k, 24 h turns the flagged mean positive (+$19, saved -22k). The freshness rule (0.5 pt) is not what makes it work: 0, 0.5 and 2.0 pts are identical (price is already 10+ pts away at the break, so the first return ends freshness regardless), 5 and 10 pts are slightly better (213k, 233k); with NO freshness limit (a level stays flagged for 4 h even after price has come back to it) the total rises to 352k (2,810 flagged trades, $121 each, PRE 198k, HOLD 120k, but L6M only 25k): dropping freshness would be simpler to implement and does not hurt the total.

### 11e. Reach (distance ahead of the entry), for completeness
| variant   |   flagged_taken |   flag_mean |   per_trade_saved |   L6M |   HOLD |   PRE |     X |   H1_2023-08..2024-12 |   H2_2025-01..2026-10 |   ALL |
|:----------|----------------:|------------:|------------------:|------:|-------:|------:|------:|----------------------:|----------------------:|------:|
| reach 10  |             359 |       -65.9 |              65.9 |   8.5 |   -1.4 |  56.8 | -11.3 |                  22.5 |                   3   |  25.5 |
| reach 20  |             715 |      -214.8 |             214.8 |  36.9 |   20.4 |  98   |  51.3 |                  96.1 |                  67.7 | 163.8 |
| reach 30  |             944 |      -172.8 |             172.8 |  57.3 |   24.8 | 119.3 |  31.7 |                  96.4 |                  85   | 181.3 |
| reach 40  |            1104 |      -166.8 |             166.8 |  72.3 |   77.5 |  98.2 |  33.7 |                  80.4 |                 119.7 | 200   |
| reach 60  |            1289 |      -200.3 |             200.3 |  87   |   98.4 | 130.5 |  40.1 |                  91.1 |                 178.5 | 269.6 |
| reach 80  |            1289 |      -200.3 |             200.3 |  87   |   98.4 | 130.5 |  40.1 |                  91.1 |                 178.5 | 269.6 |
Reading: 40-60 is the plateau (reach 60 and 80 identical because the target distance caps it at 60).

### 11f. Holdout-style check (nothing is fitted; compare halves)
Halves: Spearman correlation across the 29 variants of saved dollars H1 vs H2 = 0.50; best variant in H1 = freshness away none (never expires) (142k in H1, 210k in H2); best in H2 = freshness away none (never expires) (142k in H1, 210k in H2); base definition (5m, print, 4h, away 0.5, reach 40): H1 80k, H2 120k. The base definition is positive in both halves (80k, 120k) and the single best variant is the same in both halves (no freshness limit), so the best variant does not migrate; the rank correlation of the 29 variants between halves is 0.50 (moderate): variants that work in 2023-24 mostly work in 2025-26. H2 is larger than H1 for most variants (the recent months carry more).
