# DS3_TREND_MAP - section B: the descriptive trend map (agent TG-1, 2026-10-30)

Prereg autopilot/TG1_prereg.md sha256 c6de24a3577b20521c20ce2346d186023d4e45a8fa9edad5d032ed8d34ae7b95. DESCRIPTIVE ONLY: every window is shown, recent first (2026 = 5 real weeks, sign only; L3M view-only); the map is NOT an input to any rule selection (selection code reads PRE and X' columns only). Every number is a lift of the bucket mean over the unconditional mean of the SAME unit / session / window, on the 70/30 plain dip split, basis N, per PLANNED lot unless stated; buckets are per-book terciles fixed on PRE+X' (T1 low .. T3 high of the SIDED measure; discrete measures by value). Full table: out/trendgate/tables/map_buckets.parquet (1499955 rows), quarterly spreads map_quarterly.parquet.

## 1. Is the trend premium new? (drift by quarter)

Mean top-minus-bottom tercile spread of market-at-signal N pts per trade over all trend measures (ENG6 = six engine books pooled; sided, so + = "more trend in the signal direction does better"):

| quarter | mean spread (pts) | share of measures with spread>0 | measures |
|---|---|---|---|
| 2026Q1 | -0.65 | 44% | 905 |
| 2025Q4 | +0.70 | 60% | 946 |
| 2025Q3 | +2.21 | 72% | 938 |
| 2025Q2 | -0.39 | 42% | 949 |
| 2025Q1 | +0.75 | 56% | 947 |
| 2024Q4 | +0.68 | 65% | 948 |
| 2024Q3 | +1.08 | 65% | 945 |
| 2024Q2 | +1.36 | 65% | 950 |
| 2024Q1 | +0.13 | 53% | 939 |
| 2023Q4 | +1.72 | 66% | 947 |
| 2023Q3 | +0.75 | 59% | 946 |
| 2023Q2 | -0.26 | 48% | 939 |

Last four quarters (2025Q2..2026Q1) vs the 8 earlier quarters, 951 trend measures: mean spread +0.47 vs +0.77 pts; 542 of 951 positive recently vs 684 earlier; 139 flipped from <=0 to >0, 281 the other way.

Per family (same definition):

| family/group | measures | recent-4Q spread | earlier spread | recent>0 | earlier>0 |
|---|---|---|---|---|---|
| MAGEO | 262 | +0.74 | +1.09 | 62% | 81% |
| STAT | 94 | +0.22 | -0.15 | 55% | 47% |
| STRENGTH | 351 | +0.31 | +0.73 | 52% | 72% |
| STRUCT | 54 | +0.63 | +0.85 | 70% | 70% |
| TRENDTOOL | 168 | +0.60 | +0.83 | 57% | 71% |
| XTF | 22 | -0.55 | +1.20 | 50% | 82% |

Named measures, spread by quarter (ENG6, market N pts/trade, newest first):

| measure | 2026Q1 | 2025Q4 | 2025Q3 | 2025Q2 | 2025Q1 | 2024Q4 | 2024Q3 | 2024Q2 | 2024Q1 | 2023Q4 | 2023Q3 | 2023Q2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 5-min ADX(14) | -2.1 | +5.0 | +0.4 | +3.8 | +1.9 | +5.5 | +11.1 | +3.3 | -0.5 | +1.0 | +3.5 | +0.8 |
| 15-min ADX(14) | -16.1 | +2.5 | +8.5 | +2.7 | -5.8 | +2.8 | +10.4 | +13.3 | -4.7 | -0.5 | +0.5 | +5.9 |
| 5-min Kaufman efficiency ratio(20) | +3.9 | +3.9 | +7.9 | +0.1 | +0.4 | +1.1 | +4.0 | +6.8 | +4.6 | -0.3 | +4.7 | -0.4 |
| 15-min Kaufman efficiency ratio(20) | -7.2 | -1.8 | +6.1 | -1.6 | -0.2 | +7.3 | +5.1 | +3.4 | -6.3 | -2.6 | -1.5 | -0.9 |
| 5-min Choppiness Index(14) | -7.8 | -6.4 | -3.6 | -5.2 | -1.4 | +1.4 | +6.2 | -3.1 | +4.7 | -3.0 | -0.9 | +8.7 |
| 15-min Choppiness Index(14) | +0.5 | -1.5 | -3.9 | +0.6 | +0.7 | -2.9 | -8.4 | -2.8 | +4.0 | -2.7 | -5.6 | +2.2 |
| 5-min EMA20-EMA50 separation (ATR) | -2.6 | +2.9 | +6.5 | +0.3 | -0.6 | +1.2 | +3.8 | +4.2 | +0.2 | -1.3 | +4.8 | +0.5 |
| 15-min EMA20-EMA50 separation (ATR) | -3.9 | +3.1 | +1.3 | -2.0 | -0.6 | +4.0 | +0.8 | +3.5 | +2.0 | +5.4 | +1.2 | +3.2 |
| 1-hour EMA20-EMA50 separation (ATR) | -7.9 | +2.5 | +5.4 | +0.8 | +7.0 | +2.8 | +4.2 | -0.8 | +3.1 | +6.5 | +0.8 | -4.8 |
| 5-min signed regression R2(50) | -2.3 | +0.7 | +5.1 | +0.3 | -0.5 | +1.4 | +6.0 | +1.0 | -2.9 | -2.2 | +1.4 | -0.8 |
| 15-min regression R2(50) | -3.3 | +3.5 | +5.1 | -1.3 | +4.1 | +7.1 | +3.7 | +7.0 | +1.6 | -1.8 | -7.7 | +8.6 |
| 1-min Supertrend(10,3) age (bars since flip) | +11.3 | +1.6 | +7.4 | -4.5 | -4.7 | +5.3 | -2.0 | +0.1 | -1.5 | +0.5 | +5.1 | -7.3 |
| 5-min Supertrend(10,3) age (bars since flip) | -1.1 | -4.7 | +3.5 | +1.8 | +0.3 | -1.6 | +8.2 | -4.0 | +7.5 | -7.3 | +0.2 | -5.5 |
| tsmom_z_1h | +9.1 | +0.1 | -0.6 | +0.2 | -0.8 | +2.3 | +0.4 | +8.2 | +0.3 | +6.3 | -1.5 | -3.7 |
| tsmom_z_1d | +3.2 | +2.1 | -1.8 | -4.3 | -1.7 | -2.3 | +1.6 | +4.3 | +5.6 | +4.1 | +0.6 | -1.6 |
| vr_q5_W1380 | +8.2 | +2.8 | -3.1 | -6.0 | +3.2 | -5.8 | +2.8 | -2.1 | -4.0 | +6.9 | +3.6 | -15.5 |
| hmm3_updown_5m | +1.1 | -1.1 | +5.6 | +0.7 | -5.7 | -0.6 | +6.3 | -3.0 | -1.2 | -2.9 | -7.2 | -1.5 |
| cross-timeframe agreement net_all | -1.4 | -0.1 | +5.8 | -1.1 | +4.4 | +1.5 | -2.4 | +3.3 | +0.8 | +4.0 | -1.0 | -2.4 |
| 1-hour Hurst exponent R/S (100 bars) | -1.8 | +0.8 | +3.7 | +3.6 | -4.2 | +0.5 | -2.0 | -6.2 | +5.8 | -6.2 | +1.8 | -3.0 |
| cvd_ratio_15m | +7.6 | +1.7 | -0.6 | +1.1 | -2.5 | -0.2 | -6.9 | -6.5 | -0.6 | -4.1 | -0.4 | -2.2 |
| sgn_acf_60m | +0.3 | +0.6 | +3.8 | +7.4 | -5.1 | -0.6 | +0.1 | -10.2 | +2.1 | +11.1 | -9.0 | -2.6 |

## 2. ALL10 pooled, ranked by L6M lift (ranked on looked data)

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 4-hour Hurst exponent R/S (100 bars) [T3] | ALL10/ALL | 2498 | 89.2 | +7.62 | +6.50 | +5.58 | +3.91 | -0.15 | +2.35 | 0.58/0.53 | +5.61 |
| 4-hour SMA50-SMA200 separation (ATR) [T1] | ALL10/ALL | 1724 | 61.6 | +nan | +9.42 | +5.27 | +2.54 | +1.25 | +1.98 | 0.58/0.53 | +5.27 |
| daily bars RSI>50 (signed run) [T1] | ALL10/ALL | 1789 | 63.9 | +nan | +5.59 | +5.01 | +2.43 | +0.67 | +0.70 | 0.57/0.53 | +5.02 |
| 4-hour Choppiness Index(28) [T1] | ALL10/ALL | 2235 | 79.8 | +7.86 | +7.78 | +4.87 | +5.43 | -1.28 | -1.54 | 0.56/0.53 | +4.88 |
| 1-min Supertrend(10,3) signed age [T3] (EINT-near) | ALL10/ALL | 2951 | 105.4 | +8.20 | +5.02 | +4.83 | +4.28 | -0.51 | +0.50 | 0.57/0.53 | +4.84 |
| 1-min Supertrend(10,3) age (bars since flip) [T3] (EINT-near) | ALL10/ALL | 2905 | 103.8 | +6.85 | +5.00 | +4.68 | +4.32 | -1.09 | +0.55 | 0.57/0.53 | +4.69 |
| large10_bias_60m [T3] | ALL10/ALL | 3372 | 120.4 | +5.30 | +5.32 | +4.51 | +4.40 | -0.38 | +0.16 | 0.57/0.53 | +4.51 |
| daily E50 slope over 3 bars (ATR/bar) [T1] (EINT-near) | ALL10/ALL | 2342 | 83.6 | +28.14 | +11.04 | +4.50 | +2.65 | +1.90 | -0.49 | 0.57/0.53 | +4.50 |
| 3-min bars RSI>50 (signed run) [T3] | ALL10/ALL | 3020 | 107.9 | +4.46 | +4.18 | +4.47 | +4.54 | +1.65 | +1.57 | 0.56/0.53 | +4.46 |
| daily signed regression R2(20) [T1] | ALL10/ALL | 2078 | 74.2 | +4.54 | +5.37 | +4.40 | +2.31 | +1.02 | +2.12 | 0.57/0.53 | +4.39 |
| 1-min E200 slope over 3 bars (ATR/bar) [T3] | ALL10/ALL | 3114 | 111.2 | +2.20 | +4.66 | +4.39 | +4.34 | +0.40 | +0.99 | 0.56/0.53 | +4.39 |
| 5-min regression R2(20) [T3] | ALL10/ALL | 3049 | 108.9 | +4.47 | +5.26 | +4.36 | +4.08 | +0.40 | +2.27 | 0.57/0.53 | +4.36 |
| 1-min price extension from the 200 average (ATR; high = over-extended) [T3] | ALL10/ALL | 3102 | 110.8 | +3.67 | +4.84 | +4.35 | +4.40 | -0.11 | +1.58 | 0.57/0.53 | +4.34 |
| 5-min consecutive higher-highs/higher-lows swing run [T3] | ALL10/ALL | 2721 | 97.2 | +3.79 | +4.97 | +4.13 | +3.99 | -0.56 | +1.72 | 0.56/0.53 | +4.13 |
| 1-min regression R2(100) [T3] | ALL10/ALL | 3034 | 108.4 | +3.13 | +4.46 | +4.10 | +3.91 | +0.29 | +2.09 | 0.57/0.53 | +4.10 |
| 1-hour Aroon(25) trend strength [T1] | ALL10/ALL | 2860 | 102.1 | +3.42 | +5.41 | +4.09 | +3.00 | -2.09 | +1.26 | 0.57/0.53 | +4.11 |
| daily linear-regression slope(20, ATR/bar) [T1] | ALL10/ALL | 2185 | 78.0 | +8.52 | +4.38 | +4.08 | +2.16 | +0.69 | +2.18 | 0.57/0.53 | +4.07 |
| daily price vs Ichimoku cloud (ATR) [T1] | ALL10/ALL | 2668 | 95.3 | +10.67 | +11.08 | +4.02 | +2.50 | -0.50 | -1.82 | 0.57/0.53 | +4.01 |
| 5-min Choppiness Index(28) [T1] | ALL10/ALL | 3021 | 107.9 | +1.80 | +6.23 | +4.00 | +3.73 | +0.81 | -0.67 | 0.57/0.53 | +4.00 |
| 3-min price extension from the s50 average (ATR; high = over-extended) [T3] | ALL10/ALL | 3030 | 108.2 | +3.16 | +3.16 | +3.98 | +3.97 | +1.08 | +1.19 | 0.57/0.53 | +3.97 |
| daily TRIX(15) [T1] | ALL10/ALL | 2349 | 83.9 | +nan | +12.80 | +3.97 | +2.22 | +0.41 | -0.54 | 0.57/0.53 | +3.96 |
| prev_close_loc [T1] | ALL10/ALL | 3130 | 111.8 | +9.52 | +4.24 | +3.96 | +3.71 | +0.15 | +0.84 | 0.57/0.53 | +3.97 |
| 5-min signed regression R2(20) [T3] | ALL10/ALL | 3093 | 110.5 | +5.05 | +5.26 | +3.91 | +3.63 | +0.53 | +2.26 | 0.56/0.53 | +3.92 |
| exhaust_net_60m [T1] | ALL10/ALL | 2510 | 89.6 | +6.39 | +5.56 | +3.89 | +2.70 | +2.49 | -0.01 | 0.57/0.53 | +3.91 |
| 5-min ADX(7) [T3] | ALL10/ALL | 3017 | 107.8 | +0.50 | +3.14 | +3.85 | +3.68 | +0.90 | +3.09 | 0.57/0.53 | +3.86 |

## 2. ALL10 pooled, worst buckets by L6M lift (the OFF side)

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| daily Ehlers dominant cycle period [v1] | ALL10/ALL | 1785 | 63.8 | +3.88 | -5.61 | -6.21 | -5.68 | +0.10 | +0.00 | 0.47/0.53 | -6.20 |
| daily Supertrend(7,2) signed age [T3] | ALL10/ALL | 1555 | 55.5 | -5.88 | -5.44 | -6.20 | -5.13 | +0.55 | +1.51 | 0.47/0.53 | -6.20 |
| 4-hour Trend Intensity Index [T3] | ALL10/ALL | 2638 | 94.2 | -17.19 | -5.50 | -5.98 | -5.09 | -0.23 | -1.06 | 0.48/0.53 | -5.99 |
| pc1_share_240 [T3] | ALL10/ALL | 1810 | 64.6 | -0.80 | -5.97 | -5.92 | -5.14 | -0.41 | -1.53 | 0.49/0.53 | -5.91 |
| idx3_agree_1d [T1] | ALL10/ALL | 2042 | 72.9 | -5.78 | -5.08 | -5.62 | -5.07 | -0.12 | -0.74 | 0.49/0.53 | -5.62 |
| daily Ehlers price minus instantaneous trendline (ATR) [T3] | ALL10/ALL | 1967 | 70.2 | -9.53 | -9.97 | -5.54 | -4.68 | +0.59 | -0.11 | 0.48/0.53 | -5.55 |
| idx4_agree_1d [T1] | ALL10/ALL | 2570 | 91.8 | -5.49 | -4.26 | -5.01 | -4.03 | +0.31 | -0.05 | 0.49/0.53 | -5.01 |
| 4-hour signed regression R2(50) [T3] | ALL10/ALL | 2655 | 94.8 | -15.79 | -7.08 | -4.97 | -4.53 | +0.43 | -0.58 | 0.48/0.53 | -4.97 |
| ret_YM_1d [T1] | ALL10/ALL | 2975 | 106.2 | -6.88 | -4.09 | -4.96 | -4.31 | +0.03 | +0.45 | 0.49/0.53 | -4.95 |
| daily HMA21 colour run length [T3] | ALL10/ALL | 2136 | 76.3 | -9.21 | -4.14 | -4.92 | -4.32 | +0.31 | -0.77 | 0.49/0.53 | -4.93 |
| daily E20 slope over 3 bars (ATR/bar) [T3] (EINT-near) | ALL10/ALL | 2008 | 71.7 | -13.70 | -10.41 | -4.89 | -4.16 | +0.57 | +0.85 | 0.48/0.53 | -4.89 |
| 4-hour linear-regression slope(50, ATR/bar) [T3] | ALL10/ALL | 2558 | 91.4 | -14.82 | -7.31 | -4.83 | -4.25 | +0.15 | -0.31 | 0.49/0.53 | -4.83 |
| daily Fisher transform(10) [T3] | ALL10/ALL | 1998 | 71.4 | -11.03 | -8.51 | -4.56 | -3.90 | +0.81 | +0.27 | 0.49/0.53 | -4.57 |
| 4-hour price extension from the 200 average (ATR; high = over-extended) [T3] | ALL10/ALL | 1640 | 58.6 | -15.87 | -17.33 | -4.56 | -3.91 | +1.56 | +1.80 | 0.47/0.53 | -4.56 |
| 4-hour SMA20-SMA50 separation (ATR) [T3] | ALL10/ALL | 2960 | 105.7 | -9.36 | -5.08 | -4.53 | -3.83 | -0.78 | -0.37 | 0.49/0.53 | -4.53 |
| 1-min 33/50/200 EMA stack order [v1] | ALL10/ALL | 1788 | 63.9 | -6.46 | -5.33 | -4.38 | -3.25 | -1.39 | +0.75 | 0.50/0.53 | -4.38 |
| pc1_share_60 [T3] | ALL10/ALL | 2274 | 81.2 | -0.25 | -3.57 | -4.37 | -4.01 | -1.50 | -2.51 | 0.50/0.53 | -4.37 |
| 4-hour consecutive structure breaks [T3] | ALL10/ALL | 1887 | 67.4 | -1.32 | -3.45 | -4.35 | -3.81 | -0.49 | +0.70 | 0.48/0.53 | -4.35 |
| 4-hour linear-regression slope(100, ATR/bar) [T3] | ALL10/ALL | 1925 | 68.8 | +8.14 | -5.84 | -4.21 | -3.63 | -0.29 | -0.96 | 0.49/0.53 | -4.22 |
| ret_RTY_1d [T1] | ALL10/ALL | 2901 | 103.6 | -3.96 | -3.13 | -4.09 | -4.26 | +0.91 | -0.45 | 0.50/0.53 | -4.09 |
| 4-hour 33/50/200 EMA stack order [T3] | ALL10/ALL | 3086 | 110.2 | -4.34 | -6.69 | -4.08 | -3.49 | +0.57 | +1.25 | 0.49/0.53 | -4.08 |
| 5-min Ehlers price minus instantaneous trendline (ATR) [T1] | ALL10/ALL | 3236 | 115.6 | -7.42 | -5.56 | -4.05 | -3.40 | -1.28 | -1.73 | 0.50/0.53 | -4.05 |
| daily Supertrend(10,3) distance (ATR) [T3] (EINT-near) | ALL10/ALL | 1968 | 70.3 | -4.97 | -5.85 | -3.99 | -3.45 | +0.84 | -0.33 | 0.50/0.53 | -3.99 |
| ret_ES_1d [T1] | ALL10/ALL | 3005 | 107.3 | -5.15 | -3.42 | -3.96 | -2.72 | +0.88 | -0.38 | 0.50/0.53 | -3.96 |
| ret_GC_1d [v1] | ALL10/ALL | 2684 | 95.9 | -10.68 | -3.22 | -3.85 | -2.43 | +1.12 | -0.34 | 0.50/0.53 | -3.85 |

## 3. Per book, recent first (ranked on L6M = looked data; lift per planned lot; n>=250 in L6M)

### KB: unconditional per planned lot (70/30, N): Y26 +2.76, L6M +1.33, HOLD +0.76, PRE +2.51, X -0.67; P(target) L6M 0.50

KB best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 3-min price extension from the s50 average (ATR; high = over-extended) [T3] | KB/ALL | 384 | 13.7 | +11.99 | +10.11 | +9.72 | +10.09 | +2.21 | +3.22 | 0.58/0.50 | +9.69 |
| 1-min Supertrend(10,3) signed age [T3] (EINT-near) | KB/ALL | 378 | 13.5 | +18.30 | +11.72 | +9.31 | +9.04 | -0.72 | -1.86 | 0.57/0.50 | +9.32 |
| 15-min CVD slope 60m [T3] | KB/ALL | 384 | 13.7 | +16.05 | +9.32 | +9.20 | +8.24 | +0.66 | +0.34 | 0.58/0.50 | +9.22 |
| 1-min Supertrend(10,3) age (bars since flip) [T3] (EINT-near) | KB/ALL | 379 | 13.5 | +17.31 | +11.36 | +9.12 | +8.87 | -0.72 | -1.89 | 0.57/0.50 | +9.13 |
| 3-min SMA20-SMA50 separation (ATR) [T3] | KB/ALL | 409 | 14.6 | +5.26 | +8.80 | +9.07 | +9.54 | +2.16 | +0.65 | 0.57/0.50 | +9.09 |
| 5-min Kaufman efficiency ratio(10) [T3] | KB/ALL | 413 | 14.8 | +12.73 | +6.96 | +8.92 | +7.59 | -0.59 | +2.54 | 0.57/0.50 | +8.94 |
| exhaust_net_60m [T1] | KB/ALL | 278 | 9.9 | +14.15 | +13.35 | +8.70 | +7.13 | +3.01 | +2.66 | 0.58/0.50 | +8.76 |
| 3-min consecutive higher-highs/higher-lows swing run [T3] | KB/ALL | 342 | 12.2 | +18.88 | +8.81 | +8.58 | +8.36 | -2.98 | +6.39 | 0.57/0.50 | +8.57 |

KB worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| impulse30 [T3] | KB/ALL | 385 | 13.8 | -12.62 | -8.13 | -8.71 | -7.44 | +1.19 | -2.22 | 0.44/0.50 | -8.71 |
| acf_L15_W1380 [T3] | KB/ALL | 391 | 14.0 | -11.27 | -6.88 | -8.27 | -8.72 | -0.38 | -2.84 | 0.43/0.50 | -8.24 |
| 3-min price extension from the s50 average (ATR; high = over-extended) [v1] | KB/ALL | 439 | 15.7 | -6.91 | -6.65 | -7.42 | -7.93 | -1.94 | -2.74 | 0.44/0.50 | -7.44 |
| daily RSI(14) [T1] | KB/ALL | 289 | 10.3 | -1.20 | -3.52 | -7.30 | -6.73 | -0.77 | -3.18 | 0.45/0.50 | -7.27 |
### PE: unconditional per planned lot (70/30, N): Y26 -3.76, L6M +0.80, HOLD +0.92, PRE +0.50, X +1.41; P(target) L6M 0.49

PE best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 15-min Supertrend(7,2) age (bars since flip) [T1] (EINT-near) | PE/ALL | 363 | 13.0 | +10.89 | +9.87 | +9.10 | +8.93 | +3.00 | +5.16 | 0.57/0.49 | +9.08 |
| kal_slope_a_1m [v1] | PE/ALL | 451 | 16.1 | +15.53 | +7.92 | +8.87 | +8.73 | -2.60 | +1.32 | 0.56/0.49 | +8.88 |
| kal_slopeT_a_1m [v1] | PE/ALL | 451 | 16.1 | +15.53 | +7.92 | +8.87 | +8.73 | -2.60 | +1.32 | 0.56/0.49 | +8.88 |
| 4-hour Choppiness Index(28) [T1] | PE/ALL | 254 | 9.1 | +8.64 | +11.61 | +8.47 | +8.93 | -2.31 | -3.87 | 0.55/0.49 | +8.48 |
| cross-timeframe agreement net_st [T3] | PE/ALL | 359 | 12.8 | +0.40 | +4.90 | +8.38 | +7.27 | +1.61 | +1.66 | 0.55/0.49 | +8.43 |
| 1-min regression R2(100) [T3] | PE/ALL | 378 | 13.5 | +7.60 | +7.79 | +7.97 | +7.30 | +0.23 | +0.75 | 0.56/0.49 | +7.98 |
| 1-min signed regression R2(100) [T3] | PE/ALL | 389 | 13.9 | +8.21 | +7.41 | +7.64 | +6.97 | +1.16 | +1.05 | 0.55/0.49 | +7.64 |
| 5-min regression R2(20) [T3] | PE/ALL | 384 | 13.7 | +9.05 | +8.10 | +7.42 | +6.97 | +0.19 | +1.89 | 0.55/0.49 | +7.42 |

PE worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 15-min Bollinger bandwidth [T3] | PE/ALL | 340 | 12.1 | -15.20 | -10.71 | -9.68 | -9.63 | +0.40 | -0.20 | 0.41/0.49 | -9.65 |
| kal_slope_a_1m [T1] | PE/ALL | 382 | 13.6 | -18.24 | -8.51 | -9.18 | -8.19 | -1.47 | -4.01 | 0.41/0.49 | -9.10 |
| kal_slopeT_a_1m [T1] | PE/ALL | 382 | 13.6 | -18.24 | -8.51 | -9.18 | -8.19 | -1.47 | -4.01 | 0.41/0.49 | -9.10 |
| 5-min consecutive higher-highs/higher-lows swing run [T1] | PE/ALL | 375 | 13.4 | -14.10 | -9.37 | -7.97 | -5.73 | -2.43 | +0.07 | 0.43/0.49 | -7.96 |
### SM: unconditional per planned lot (70/30, N): Y26 +4.43, L6M +3.24, HOLD +4.68, PRE +3.43, X +1.07; P(target) L6M 0.51

SM best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| exhaust_net_60m [v1] | SM/ALL | 253 | 9.4 | +5.28 | +3.58 | +2.69 | +2.24 | -1.11 | +1.64 | 0.53/0.51 | +2.67 |
| 30-min Wyckoff markup(+)/markdown(-) phase (approx) [v1] | SM/ALL | 252 | 9.3 | +2.90 | +2.52 | +2.43 | +1.54 | +0.15 | -0.70 | 0.53/0.51 | +2.42 |
| cvd_px_agree_5m [T3] | SM/ALL | 260 | 9.6 | -3.59 | +1.93 | +1.46 | +1.11 | -0.60 | -0.85 | 0.53/0.51 | +1.47 |
| 1-min CVD-price agreement 5m [T3] | SM/ALL | 260 | 9.6 | -3.59 | +1.93 | +1.46 | +1.11 | -0.60 | -0.85 | 0.53/0.51 | +1.47 |
| 15-min CVD-price agreement 60m [T3] | SM/ALL | 262 | 9.7 | -0.01 | +0.08 | +0.29 | -0.15 | +0.82 | -0.27 | 0.51/0.51 | +0.29 |
| 1-min CVD-price agreement 15m [T3] | SM/ALL | 283 | 10.5 | -0.63 | +1.22 | +0.27 | -0.14 | +0.17 | +0.35 | 0.51/0.51 | +0.27 |
| cvd_px_agree_15m [T3] | SM/ALL | 283 | 10.5 | -0.63 | +1.22 | +0.27 | -0.14 | +0.17 | +0.35 | 0.51/0.51 | +0.27 |
| 5-min CVD-price agreement 15m [T3] | SM/ALL | 283 | 10.5 | -0.63 | +1.22 | +0.27 | -0.14 | +0.17 | +0.35 | 0.51/0.51 | +0.27 |

SM worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 5-min consecutive structure breaks [v1] | SM/ALL | 252 | 9.3 | -1.81 | -3.48 | -3.41 | -2.94 | +1.55 | -2.21 | 0.48/0.51 | -3.39 |
| daily Wyckoff markup(+)/markdown(-) phase (approx) [v1] | SM/ALL | 275 | 10.2 | +0.00 | +0.00 | -2.89 | -4.22 | -0.31 | -1.02 | 0.49/0.51 | -2.88 |
| 5-min recent change of character direction [T3] | SM/ALL | 267 | 9.9 | +3.11 | -0.67 | -1.76 | -1.55 | +0.81 | -1.11 | 0.50/0.51 | -1.76 |
| absorb_net_60m [v1] | SM/ALL | 277 | 10.3 | -0.49 | -2.94 | -1.45 | -1.40 | -0.01 | -0.24 | 0.49/0.51 | -1.45 |
### HM: unconditional per planned lot (70/30, N): Y26 +5.50, L6M +4.32, HOLD +3.40, PRE +1.87, X +0.88; P(target) L6M 0.52

HM best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1-min Ehlers price minus instantaneous trendline (ATR) [T3] | HM/ALL | 255 | 9.1 | +9.40 | +12.29 | +12.24 | +11.14 | -4.30 | -0.17 | 0.63/0.52 | +12.33 |
| 1-min E20 slope over 5 bars (ATR/bar) [T3] (EINT-near) | HM/ALL | 274 | 9.8 | +4.97 | +11.65 | +10.93 | +9.32 | -4.42 | -2.59 | 0.62/0.52 | +11.01 |
| 1-min E20 slope over 3 bars (ATR/bar) [T3] (EINT-near) | HM/ALL | 256 | 9.1 | +2.60 | +8.18 | +10.17 | +9.60 | -5.33 | -2.43 | 0.62/0.52 | +10.25 |
| 1-min EMA9-EMA21 separation (ATR) [T3] (EINT-near) | HM/ALL | 277 | 9.9 | +6.62 | +9.41 | +9.97 | +8.54 | -4.08 | -0.87 | 0.60/0.52 | +10.07 |
| 1-min EMA8-EMA21 separation (ATR) [T3] (EINT-near) | HM/ALL | 271 | 9.7 | +5.36 | +8.16 | +9.97 | +8.24 | -4.91 | -1.02 | 0.61/0.52 | +10.06 |
| 3-min CVD slope 60m [v1] | HM/ALL | 283 | 10.1 | +9.27 | +10.37 | +9.92 | +7.44 | +1.14 | -2.86 | 0.59/0.52 | +9.94 |
| 3-min Supertrend(7,2) distance (ATR) [T3] (EINT-near) | HM/ALL | 262 | 9.4 | +5.03 | +3.04 | +9.76 | +7.13 | -3.98 | -3.96 | 0.61/0.52 | +9.83 |
| tsmom_z_15m [T3] | HM/ALL | 271 | 9.7 | +12.74 | +11.27 | +9.74 | +8.70 | -2.39 | -4.83 | 0.61/0.52 | +9.82 |

HM worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1-min Ehlers dominant cycle period [T1] | HM/ALL | 330 | 11.8 | -7.86 | -9.63 | -9.67 | -9.67 | +0.49 | +1.43 | 0.44/0.52 | -9.68 |
| 1-min Bollinger bandwidth [T1] | HM/ALL | 336 | 12.0 | -14.18 | -11.29 | -8.72 | -7.44 | -0.19 | +3.45 | 0.43/0.52 | -8.72 |
| 1-min distance to PSAR (ATR) [T1] | HM/ALL | 306 | 10.9 | -17.62 | -9.91 | -8.26 | -7.98 | +1.99 | +0.77 | 0.44/0.52 | -8.25 |
| 3-min Bollinger bandwidth [T1] | HM/ALL | 326 | 11.6 | -7.88 | -8.04 | -8.05 | -6.42 | +1.89 | +0.95 | 0.45/0.52 | -8.05 |
### MV: unconditional per planned lot (70/30, N): Y26 +4.42, L6M +2.30, HOLD +1.51, PRE +2.16, X -2.91; P(target) L6M 0.51

MV best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 4-hour Hurst exponent R/S (100 bars) [T3] | MV/ALL | 292 | 10.4 | +19.08 | +14.03 | +10.11 | +7.65 | -0.14 | +2.11 | 0.60/0.51 | +10.11 |
| 1-hour Bollinger bandwidth [v1] | MV/ALL | 378 | 13.5 | +6.36 | +8.99 | +8.44 | +8.24 | +1.74 | -1.20 | 0.57/0.51 | +8.41 |
| 1-min Parabolic SAR run length [T1] | MV/ALL | 290 | 10.4 | +2.91 | +7.22 | +7.30 | +6.47 | -0.18 | +2.45 | 0.56/0.51 | +7.28 |
| exhaust_net_60m [T1] | MV/ALL | 302 | 10.8 | +5.55 | +5.82 | +6.96 | +5.73 | +4.59 | +1.02 | 0.57/0.51 | +6.92 |
| 30-min EMA ribbon expansion [T3] | MV/ALL | 404 | 14.4 | +7.41 | +5.79 | +6.63 | +5.12 | +0.24 | -3.64 | 0.56/0.51 | +6.60 |
| 1-hour Hurst exponent R/S (100 bars) [v1] | MV/ALL | 389 | 13.9 | +6.11 | +7.55 | +6.55 | +8.19 | -1.64 | -1.69 | 0.56/0.51 | +6.55 |
| 15-min recent change of character direction [v1] | MV/ALL | 318 | 11.4 | +5.64 | +7.54 | +6.39 | +6.47 | +0.40 | -4.00 | 0.57/0.51 | +6.37 |
| 1-hour KAMA fast-slow separation (ATR) [T1] | MV/ALL | 358 | 12.8 | +2.63 | +5.97 | +6.28 | +6.89 | -0.68 | -0.48 | 0.57/0.51 | +6.26 |

MV worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| daily ADX(20) [v1] | MV/ALL | 292 | 10.4 | -1.23 | -6.50 | -7.28 | -3.75 | -0.98 | +1.86 | 0.45/0.51 | -7.24 |
| skew_1d [T1] | MV/ALL | 312 | 11.1 | -6.86 | -6.44 | -7.18 | -4.80 | +2.69 | +3.87 | 0.45/0.51 | -7.13 |
| 5-min regression R2(100) [T1] | MV/ALL | 363 | 13.0 | -8.72 | -6.89 | -7.13 | -6.42 | -1.10 | +0.67 | 0.46/0.51 | -7.13 |
| 4-hour ADX(14) 3-bar slope [T1] | MV/ALL | 311 | 11.1 | -3.29 | -4.81 | -7.10 | -6.59 | -0.30 | +0.26 | 0.45/0.51 | -7.07 |
### PB: unconditional per planned lot (70/30, N): Y26 +6.09, L6M +7.57, HOLD +6.05, PRE -0.34, X +2.33; P(target) L6M 0.54

PB best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1-hour Kaufman efficiency ratio(10) [v1] | PB/ALL | 272 | 9.7 | +18.30 | +9.82 | +8.38 | +8.16 | -3.35 | +3.42 | 0.60/0.54 | +8.35 |
| 1-min Kaufman efficiency ratio(20) [v1] | PB/ALL | 327 | 11.7 | +17.94 | +12.07 | +7.97 | +7.22 | -2.94 | +2.73 | 0.60/0.54 | +7.94 |
| large10_bias_60m [T3] | PB/ALL | 326 | 11.6 | +5.72 | +8.14 | +7.54 | +7.81 | +1.04 | -0.68 | 0.59/0.54 | +7.50 |
| 15-min Hurst exponent R/S (100 bars) [v1] | PB/ALL | 294 | 10.5 | +7.62 | +8.97 | +7.41 | +6.58 | -0.92 | +0.97 | 0.60/0.54 | +7.33 |
| 3-min price extension from the s50 average (ATR; high = over-extended) [T3] | PB/ALL | 290 | 10.4 | +13.46 | +4.88 | +6.47 | +5.98 | +1.32 | -2.55 | 0.59/0.54 | +6.47 |
| sig_rty_move20_atr [T3] | PB/ALL | 270 | 9.6 | +7.56 | +6.59 | +6.39 | +7.68 | +2.08 | +1.52 | 0.59/0.54 | +6.38 |
| 1-hour Supertrend(7,2) distance (ATR) [v1] (EINT-near) | PB/ALL | 314 | 11.2 | -4.76 | +3.46 | +6.36 | +6.83 | -1.57 | +2.82 | 0.61/0.54 | +6.44 |
| large10_bias_30m [T3] | PB/ALL | 298 | 10.6 | +9.83 | +9.19 | +6.21 | +6.21 | -2.32 | +1.60 | 0.58/0.54 | +6.19 |

PB worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| sig_imb5_s [T1] | PB/ALL | 271 | 9.7 | -8.64 | -8.27 | -9.33 | -8.17 | -1.98 | -2.43 | 0.45/0.54 | -9.29 |
| sig_absorb10_s [v1] | PB/ALL | 286 | 10.2 | -10.84 | -10.14 | -7.57 | -6.32 | -0.19 | +2.52 | 0.47/0.54 | -7.55 |
| large10_bias_60m [v1] | PB/ALL | 258 | 9.2 | -2.04 | -4.01 | -6.96 | -7.32 | -0.07 | -1.04 | 0.50/0.54 | -6.95 |
| ret_ES_1d [T1] | PB/ALL | 259 | 9.2 | -6.65 | -8.94 | -6.73 | -5.15 | +1.94 | +2.82 | 0.49/0.54 | -6.72 |
### DN: unconditional per planned lot (70/30, N): Y26 +14.20, L6M +5.46, HOLD +4.17, PRE +3.11, X +0.07; P(target) L6M 0.54

DN best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 15-min Kaufman efficiency ratio(10) [v1] | DN/ALL | 251 | 9.0 | +12.02 | +9.84 | +9.91 | +8.13 | -4.08 | -4.22 | 0.63/0.54 | +10.06 |
| rv30_over_vix [T1] | DN/ALL | 252 | 9.0 | +17.35 | +9.62 | +8.78 | +4.79 | -1.85 | +3.90 | 0.60/0.54 | +8.84 |
| acf_L5_W240 [v1] | DN/ALL | 255 | 9.1 | +5.65 | +3.82 | +8.02 | +6.70 | -3.20 | +0.49 | 0.60/0.54 | +8.12 |
| 30-min E20 slope over 1 bars (ATR/bar) [v1] (EINT-near) | DN/ALL | 251 | 9.0 | +11.27 | +5.26 | +7.95 | +7.07 | -0.09 | +5.50 | 0.60/0.54 | +7.99 |
| 30-min price extension from the 20 average (ATR; high = over-extended) [v1] (EINT-near) | DN/ALL | 251 | 9.0 | +11.27 | +5.26 | +7.95 | +7.07 | -0.09 | +5.50 | 0.60/0.54 | +7.99 |
| 15-min E50 slope over 3 bars (ATR/bar) [v1] (EINT-near) | DN/ALL | 251 | 9.0 | +12.35 | +9.85 | +7.83 | +6.75 | -1.72 | -1.97 | 0.60/0.54 | +7.92 |
| pc1_share_240 [v1] | DN/ALL | 290 | 10.4 | +9.56 | +11.81 | +7.76 | +7.71 | -2.19 | +7.37 | 0.60/0.54 | +7.78 |
| rv30_ann [T1] | DN/ALL | 259 | 9.2 | +13.72 | +6.74 | +7.71 | +4.11 | -3.01 | +4.39 | 0.59/0.54 | +7.77 |

DN worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 30-min Hurst exponent R/S (100 bars) [v1] | DN/ALL | 261 | 9.3 | -5.11 | -6.60 | -10.18 | -9.16 | +1.20 | +0.68 | 0.45/0.54 | -10.20 |
| 1-hour ATR(14) vs its 50-bar median [T3] (EINT-near) | DN/ALL | 255 | 9.1 | -1.15 | -6.68 | -8.46 | -6.24 | +1.97 | -0.72 | 0.47/0.54 | -8.50 |
| 5-min KAMA fast-slow separation (ATR) [T1] | DN/ALL | 253 | 9.0 | +2.32 | -6.45 | -7.18 | -5.64 | +4.23 | +6.07 | 0.49/0.54 | -7.21 |
| daily Supertrend(10,3) signed age [v1] (EINT-near) | DN/ALL | 284 | 10.1 | +nan | -10.58 | -7.13 | -5.84 | +1.35 | -2.08 | 0.48/0.54 | -7.17 |
### ST: unconditional per planned lot (70/30, N): Y26 +7.47, L6M +4.36, HOLD +3.49, PRE +2.00, X +0.71; P(target) L6M 0.52

ST best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 4-hour HMA20-HMA50 separation (ATR) [T3] (EINT-near) | ST/ALL | 377 | 13.5 | +1.51 | +4.27 | +7.72 | +7.35 | -0.57 | +2.75 | 0.58/0.52 | +7.72 |
| large10_bias_60m [T3] | ST/ALL | 449 | 16.0 | +11.82 | +10.40 | +7.37 | +6.92 | -1.12 | +1.18 | 0.58/0.52 | +7.36 |
| 1-min ATR(14) vs its 50-bar median [T1] (EINT-near) | ST/ALL | 401 | 14.3 | +1.10 | +3.90 | +7.02 | +7.09 | +0.05 | -1.48 | 0.56/0.52 | +6.97 |
| 5-min bar aggressor delta / volume [T3] | ST/ALL | 397 | 14.2 | +1.48 | +6.72 | +6.87 | +5.57 | +1.42 | +0.62 | 0.57/0.52 | +6.87 |
| 5-min consecutive higher-highs/higher-lows swing run [T3] | ST/ALL | 415 | 14.8 | +8.58 | +8.75 | +6.77 | +6.30 | +0.51 | +2.64 | 0.57/0.52 | +6.73 |
| 1-min +DI minus -DI (7) [T3] | ST/ALL | 350 | 12.5 | +12.45 | +5.88 | +6.69 | +5.47 | +0.51 | +2.44 | 0.57/0.52 | +6.64 |
| sig_es_nq_div5 [T3] | ST/ALL | 363 | 13.0 | +5.08 | +4.21 | +6.54 | +6.99 | +2.19 | -0.18 | 0.58/0.52 | +6.50 |
| 3-min ATR(5) vs ATR(14) [T1] (EINT-near) | ST/ALL | 349 | 12.5 | +3.41 | +4.68 | +6.35 | +5.97 | +2.64 | +0.54 | 0.56/0.52 | +6.36 |

ST worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1-min 33/50/200 EMA stack order [v1] | ST/ALL | 302 | 10.8 | -24.01 | -13.31 | -8.62 | -6.84 | -2.22 | +2.37 | 0.45/0.52 | -8.58 |
| pc1_share_240 [T3] | ST/ALL | 261 | 9.3 | -9.04 | -6.79 | -7.78 | -6.68 | -1.74 | -2.64 | 0.47/0.52 | -7.74 |
| 15-min consecutive higher-highs/higher-lows swing run [T1] | ST/ALL | 265 | 9.5 | -13.68 | -5.93 | -7.76 | -7.00 | +0.84 | +6.10 | 0.45/0.52 | -7.72 |
| vix_chg5 [T1] | ST/ALL | 302 | 10.8 | -4.29 | -14.50 | -7.71 | -5.64 | -0.97 | -5.51 | 0.44/0.52 | -7.68 |
### WT: unconditional per planned lot (70/30, N): Y26 +2.69, L6M +1.87, HOLD +1.29, PRE +0.59, X +0.46; P(target) L6M 0.60

WT best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1-min linear-regression slope(100, ATR/bar) [T3] | WT/ALL | 506 | 18.1 | +2.08 | +4.37 | +4.20 | +3.73 | -0.27 | +0.74 | 0.65/0.60 | +4.20 |
| 1-hour ATR(14) vs its 50-bar median [v1] (EINT-near) | WT/ALL | 517 | 18.5 | +2.39 | +3.35 | +4.08 | +3.14 | -0.56 | +0.16 | 0.65/0.60 | +4.13 |
| acf_L1_W1380 [v1] | WT/ALL | 529 | 18.9 | +3.41 | +4.53 | +3.97 | +2.78 | +0.66 | +0.98 | 0.64/0.60 | +4.00 |
| 4-hour Bollinger bandwidth percentile (100 bars) [T1] | WT/ALL | 377 | 13.5 | +10.44 | +2.60 | +3.94 | +1.90 | -0.28 | +1.87 | 0.64/0.60 | +3.97 |
| sig_intens_rel [v1] | WT/ALL | 567 | 20.2 | +6.39 | +4.81 | +3.84 | +3.56 | +0.70 | +1.98 | 0.65/0.60 | +3.88 |
| ret_ES_1h [T3] | WT/ALL | 439 | 15.7 | -0.22 | +2.84 | +3.78 | +3.15 | -0.36 | +0.96 | 0.65/0.60 | +3.77 |
| prev_close_loc [T1] | WT/ALL | 527 | 18.8 | +4.36 | +2.51 | +3.77 | +4.29 | +0.04 | +0.81 | 0.65/0.60 | +3.76 |
| 1-min ADX(14) signed by DI direction [T3] | WT/ALL | 525 | 18.8 | +5.99 | +4.52 | +3.74 | +2.75 | +1.29 | -0.69 | 0.64/0.60 | +3.74 |

WT worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pc1_share_240 [T3] | WT/ALL | 300 | 10.7 | -1.70 | -2.60 | -4.86 | -3.75 | +0.99 | -0.11 | 0.54/0.60 | -4.85 |
| 1-min Supertrend(7,2) signed age [T1] | WT/ALL | 427 | 15.2 | -4.34 | -5.19 | -4.70 | -4.05 | -1.18 | -0.14 | 0.54/0.60 | -4.72 |
| ret_YM_1d [T1] | WT/ALL | 540 | 19.3 | -7.44 | -2.96 | -4.66 | -4.13 | -0.50 | +2.38 | 0.54/0.60 | -4.68 |
| sig_intens_rel [T1] | WT/ALL | 473 | 16.9 | -4.43 | -4.34 | -4.02 | -3.77 | -0.79 | -1.44 | 0.53/0.60 | -4.03 |
### MA: unconditional per planned lot (70/30, N): Y26 +4.73, L6M +6.16, HOLD +4.85, PRE +2.56, X +2.47; P(target) L6M 0.55

MA best 8 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 3-min consecutive structure breaks [v1] | MA/ALL | 285 | 10.2 | -0.52 | +0.64 | +4.82 | +5.17 | +1.74 | +1.54 | 0.59/0.55 | +4.89 |
| 3-min recent change of character direction [T3] | MA/ALL | 290 | 10.4 | +2.95 | +1.64 | +4.60 | +4.69 | +1.32 | -1.08 | 0.59/0.55 | +4.70 |
| 3-min Aroon(25) trend strength [v1] | MA/ALL | 299 | 10.7 | -3.74 | +0.56 | +3.51 | +3.13 | -0.81 | -1.82 | 0.58/0.55 | +3.56 |
| 1-min Trend Intensity Index [v1] | MA/ALL | 263 | 9.4 | +2.95 | +4.69 | +2.93 | +3.08 | +0.10 | -0.05 | 0.57/0.55 | +3.01 |
| 3-min CVD-price agreement 15m [T3] | MA/ALL | 330 | 11.8 | +0.58 | +3.29 | +2.52 | +2.52 | +0.99 | -4.08 | 0.57/0.55 | +2.54 |
| tsmom_hz_sum [v1] | MA/ALL | 299 | 10.7 | +4.84 | +1.69 | +2.44 | +2.87 | +1.13 | -1.07 | 0.58/0.55 | +2.43 |
| 15-min aroon direction sign [T1] | MA/ALL | 299 | 10.7 | +6.08 | +3.79 | +1.86 | +1.80 | -0.72 | -1.16 | 0.56/0.55 | +1.86 |
| 5-min recent change of character direction [T3] | MA/ALL | 337 | 12.0 | -1.35 | +2.32 | +1.71 | +1.57 | +0.35 | -0.32 | 0.56/0.55 | +1.73 |

MA worst 4 buckets by L6M

| measure x bucket | unit | n L6M | tpw L6M | lift Y26 | L3M | L6M | HOLD | PRE | X' | P(tgt) L6M kept/all | per contract L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| cross-timeframe agreement net_lr50 [v1] | MA/ALL | 277 | 9.9 | +1.54 | -1.59 | -2.98 | -2.17 | -0.04 | -2.02 | 0.52/0.55 | -3.00 |
| 5-min bar delta sign run [v1] | MA/ALL | 260 | 9.3 | -4.82 | -3.25 | -2.66 | -3.73 | +3.64 | +1.81 | 0.52/0.55 | -2.69 |
| daily consecutive structure breaks [v1] | MA/ALL | 267 | 9.5 | -3.72 | -1.98 | -2.51 | -1.19 | +0.60 | -0.15 | 0.53/0.55 | -2.53 |
| 30-min MA stack fully aligned [v1] | MA/ALL | 308 | 11.0 | -4.70 | -1.73 | -1.97 | -1.15 | -0.73 | -1.59 | 0.53/0.55 | -1.99 |

## 4. The plain lines (conditions as in the directive)


**Signals with 5m ADX(14) > 25 AND the 5m EMA50/EMA200 separated by > 1 ATR in the signal direction vs all other signals (coverage 27% of signals)**

| book | window | n cond / n other | tpw cond | P(target) cond vs other | per contract cond vs other (70/30 N) | lift per contract |
|---|---|---|---|---|---|---|
| KB | L6M | 326 / 931 | 11.6 | 0.52 vs 0.49 | +4.19 vs +0.33 | +3.86 |
| KB | HOLD | 345 / 1029 | 10.8 | 0.51 vs 0.48 | +3.82 vs -0.27 | +4.09 |
| KB | PRE | 703 / 2390 | 9.4 | 0.51 vs 0.51 | +3.10 vs +2.35 | +0.75 |
| KB | X | 273 / 760 | 6.2 | 0.49 vs 0.43 | +4.30 vs -2.46 | +6.75 |
| PE | L6M | 374 / 820 | 13.4 | 0.50 vs 0.49 | +1.67 vs +0.40 | +1.27 |
| PE | HOLD | 406 / 905 | 12.7 | 0.49 vs 0.49 | +1.40 vs +0.70 | +0.70 |
| PE | PRE | 850 / 2199 | 11.3 | 0.52 vs 0.48 | +4.36 vs -1.00 | +5.36 |
| PE | X | 335 / 666 | 7.6 | 0.47 vs 0.45 | +1.86 vs +1.18 | +0.68 |
| SM | PRE | 49 / 855 | 1.3 | 0.51 vs 0.52 | +2.92 vs +3.47 | -0.55 |
| SM | X | 29 / 412 | 1.4 | 0.55 vs 0.46 | +21.89 vs -0.41 | +22.29 |
| HM | L6M | 237 / 672 | 8.5 | 0.53 vs 0.52 | +4.72 vs +4.18 | +0.54 |
| HM | HOLD | 260 / 748 | 8.1 | 0.52 vs 0.50 | +3.89 vs +3.24 | +0.66 |
| HM | PRE | 553 / 1732 | 7.4 | 0.52 vs 0.49 | +4.88 vs +0.92 | +3.96 |
| HM | X | 242 / 621 | 5.5 | 0.51 vs 0.43 | +7.82 vs -1.83 | +9.65 |
| MV | L6M | 334 / 797 | 11.9 | 0.54 vs 0.49 | +6.66 vs +0.44 | +6.22 |
| MV | HOLD | 357 / 894 | 11.2 | 0.53 vs 0.48 | +5.43 vs -0.07 | +5.50 |
| MV | PRE | 785 / 2132 | 10.5 | 0.52 vs 0.50 | +4.02 vs +1.47 | +2.55 |
| MV | X | 315 / 684 | 7.2 | 0.45 vs 0.42 | +1.58 vs -4.97 | +6.55 |
| PB | L6M | 339 / 527 | 12.1 | 0.55 vs 0.54 | +6.61 vs +8.17 | -1.56 |
| PB | HOLD | 372 / 593 | 11.6 | 0.53 vs 0.52 | +4.87 vs +6.76 | -1.89 |
| PB | PRE | 819 / 1442 | 10.9 | 0.51 vs 0.47 | +2.91 vs -2.18 | +5.09 |
| PB | X | 317 / 506 | 7.2 | 0.48 vs 0.45 | +4.23 vs +1.14 | +3.09 |
| DN | L6M | 237 / 464 | 8.5 | 0.51 vs 0.55 | +2.98 vs +6.76 | -3.78 |
| DN | HOLD | 251 / 531 | 8.1 | 0.50 vs 0.54 | +1.91 vs +5.26 | -3.35 |
| DN | PRE | 507 / 1254 | 6.8 | 0.52 vs 0.52 | +3.24 vs +3.11 | +0.13 |
| DN | X | 206 / 522 | 4.8 | 0.50 vs 0.45 | +3.97 vs -1.46 | +5.43 |
| ST | L6M | 404 / 852 | 14.4 | 0.55 vs 0.50 | +8.31 vs +2.47 | +5.84 |
| ST | HOLD | 439 / 943 | 13.7 | 0.54 vs 0.49 | +7.83 vs +1.46 | +6.37 |
| ST | PRE | 925 / 2095 | 12.3 | 0.50 vs 0.50 | +2.11 vs +1.95 | +0.17 |
| ST | X | 323 / 665 | 7.3 | 0.49 vs 0.45 | +3.06 vs -0.41 | +3.47 |
| WT | L6M | 501 / 1205 | 17.9 | 0.61 vs 0.59 | +3.28 vs +1.30 | +1.98 |
| WT | HOLD | 549 / 1344 | 17.2 | 0.60 vs 0.58 | +3.05 vs +0.58 | +2.47 |
| WT | PRE | 1155 / 3110 | 15.4 | 0.58 vs 0.59 | -0.06 vs +0.83 | -0.89 |
| WT | X | 491 / 1036 | 11.2 | 0.57 vs 0.58 | -0.60 vs +0.97 | -1.57 |
| MA | L6M | 25 / 382 | 1.6 | 0.56 vs 0.54 | +5.79 vs +6.23 | -0.43 |
| MA | HOLD | 26 / 448 | 1.5 | 0.54 vs 0.53 | +3.20 vs +4.97 | -1.77 |
| MA | PRE | 40 / 1049 | 1.3 | 0.50 vs 0.50 | -1.62 vs +2.72 | -4.34 |

**Signals with 15m ADX(14) > 25 AND the 15m EMA50/EMA200 separated by > 1 ATR in the signal direction vs all other signals (coverage 23% of signals)**

| book | window | n cond / n other | tpw cond | P(target) cond vs other | per contract cond vs other (70/30 N) | lift per contract |
|---|---|---|---|---|---|---|
| KB | L6M | 278 / 979 | 9.9 | 0.52 vs 0.50 | +5.74 vs +0.10 | +5.64 |
| KB | HOLD | 293 / 1081 | 9.2 | 0.51 vs 0.48 | +5.24 vs -0.44 | +5.68 |
| KB | PRE | 692 / 2401 | 9.4 | 0.54 vs 0.50 | +6.49 vs +1.37 | +5.12 |
| KB | X | 242 / 791 | 5.5 | 0.46 vs 0.44 | +1.01 vs -1.19 | +2.20 |
| PE | L6M | 267 / 927 | 9.5 | 0.49 vs 0.49 | +0.74 vs +0.82 | -0.08 |
| PE | HOLD | 281 / 1030 | 8.8 | 0.49 vs 0.49 | +1.49 vs +0.76 | +0.73 |
| PE | PRE | 724 / 2325 | 10.1 | 0.51 vs 0.48 | +2.50 vs -0.13 | +2.62 |
| PE | X | 240 / 761 | 5.6 | 0.47 vs 0.45 | +3.88 vs +0.63 | +3.25 |
| SM | L6M | 28 / 286 | 1.4 | 0.54 vs 0.51 | +12.08 vs +2.35 | +9.73 |
| SM | HOLD | 35 / 328 | 1.5 | 0.49 vs 0.52 | +4.42 vs +4.69 | -0.27 |
| SM | PRE | 104 / 800 | 1.9 | 0.49 vs 0.53 | +0.54 vs +3.82 | -3.28 |
| SM | X | 43 / 398 | 1.4 | 0.47 vs 0.47 | +3.30 vs +0.83 | +2.47 |
| HM | L6M | 201 / 708 | 7.2 | 0.50 vs 0.53 | +3.16 vs +4.66 | -1.50 |
| HM | HOLD | 219 / 789 | 6.8 | 0.48 vs 0.51 | +1.56 vs +3.93 | -2.37 |
| HM | PRE | 541 / 1744 | 7.4 | 0.55 vs 0.48 | +7.79 vs +0.04 | +7.75 |
| HM | X | 202 / 661 | 4.7 | 0.46 vs 0.45 | +2.76 vs +0.31 | +2.45 |
| MV | L6M | 266 / 865 | 9.5 | 0.51 vs 0.51 | +3.50 vs +1.91 | +1.59 |
| MV | HOLD | 284 / 967 | 8.9 | 0.50 vs 0.50 | +2.91 vs +1.09 | +1.81 |
| MV | PRE | 698 / 2219 | 9.7 | 0.51 vs 0.50 | +3.41 vs +1.76 | +1.66 |
| MV | X | 241 / 758 | 5.5 | 0.41 vs 0.44 | -3.09 vs -2.85 | -0.24 |
| PB | L6M | 240 / 626 | 8.6 | 0.58 vs 0.53 | +12.39 vs +5.72 | +6.67 |
| PB | HOLD | 262 / 703 | 8.2 | 0.55 vs 0.52 | +10.01 vs +4.55 | +5.46 |
| PB | PRE | 645 / 1616 | 8.8 | 0.51 vs 0.47 | +4.07 vs -2.10 | +6.17 |
| PB | X | 224 / 599 | 5.1 | 0.48 vs 0.46 | +4.12 vs +1.66 | +2.46 |
| DN | L6M | 168 / 533 | 6.0 | 0.45 vs 0.56 | -3.14 vs +8.19 | -11.33 |
| DN | HOLD | 181 / 601 | 5.7 | 0.44 vs 0.55 | -4.99 vs +6.95 | -11.94 |
| DN | PRE | 422 / 1339 | 5.9 | 0.54 vs 0.52 | +6.31 vs +2.16 | +4.15 |
| DN | X | 178 / 550 | 4.3 | 0.44 vs 0.47 | -2.86 vs +1.01 | -3.87 |
| ST | L6M | 289 / 967 | 10.3 | 0.51 vs 0.52 | +4.91 vs +4.19 | +0.72 |
| ST | HOLD | 306 / 1076 | 9.6 | 0.50 vs 0.51 | +4.79 vs +3.11 | +1.68 |
| ST | PRE | 730 / 2290 | 10.1 | 0.53 vs 0.50 | +4.90 vs +1.07 | +3.83 |
| ST | X | 258 / 730 | 5.9 | 0.48 vs 0.46 | +1.43 vs +0.47 | +0.96 |
| WT | L6M | 396 / 1310 | 14.1 | 0.62 vs 0.59 | +4.26 vs +1.16 | +3.09 |
| WT | HOLD | 425 / 1468 | 13.3 | 0.62 vs 0.58 | +4.39 vs +0.41 | +3.98 |
| WT | PRE | 984 / 3281 | 13.5 | 0.59 vs 0.58 | +1.32 vs +0.37 | +0.94 |
| WT | X | 370 / 1157 | 8.4 | 0.56 vs 0.58 | -1.45 vs +1.08 | -2.53 |
| MA | L6M | 41 / 366 | 1.6 | 0.66 vs 0.53 | +21.81 vs +4.44 | +17.37 |
| MA | HOLD | 48 / 426 | 1.6 | 0.58 vs 0.52 | +12.82 vs +3.97 | +8.86 |
| MA | PRE | 115 / 974 | 2.1 | 0.52 vs 0.50 | +4.31 vs +2.35 | +1.96 |
| MA | X | 41 / 479 | 1.4 | 0.39 vs 0.48 | -4.11 vs +3.03 | -7.14 |

**KB-style: 5-min EMA20/EMA50 separated by > 1 ATR in the signal direction AND 5-min ADX(14) > 25**

| book | window | n cond / n other | tpw cond | P(target) cond vs other | per contract cond vs other (70/30 N) | lift per contract |
|---|---|---|---|---|---|---|
| KB | L6M | 311 / 946 | 11.1 | 0.52 vs 0.49 | +4.05 vs +0.44 | +3.61 |
| KB | HOLD | 342 / 1032 | 10.7 | 0.51 vs 0.48 | +4.43 vs -0.46 | +4.88 |
| KB | PRE | 727 / 2366 | 9.7 | 0.53 vs 0.50 | +4.87 vs +1.80 | +3.07 |
| KB | X | 285 / 748 | 6.5 | 0.49 vs 0.43 | +3.76 vs -2.37 | +6.13 |
| ST | L6M | 449 / 807 | 16.0 | 0.53 vs 0.51 | +5.74 vs +3.58 | +2.15 |
| ST | HOLD | 493 / 889 | 15.4 | 0.52 vs 0.50 | +5.03 vs +2.63 | +2.40 |
| ST | PRE | 1072 / 1948 | 14.3 | 0.51 vs 0.50 | +2.75 vs +1.58 | +1.17 |
| ST | X | 376 / 612 | 8.5 | 0.47 vs 0.46 | +1.42 vs +0.29 | +1.14 |
| HM | L6M | 261 / 648 | 9.3 | 0.53 vs 0.51 | +4.79 vs +4.13 | +0.66 |
| HM | HOLD | 295 / 713 | 9.2 | 0.52 vs 0.50 | +3.78 vs +3.25 | +0.53 |
| HM | PRE | 625 / 1660 | 8.3 | 0.52 vs 0.49 | +3.97 vs +1.09 | +2.88 |
| HM | X | 257 / 606 | 5.8 | 0.49 vs 0.44 | +4.74 vs -0.75 | +5.50 |
| SM | PRE | 20 / 884 | 1.0 | 0.60 vs 0.52 | +9.39 vs +3.31 | +6.08 |
| PE | L6M | 413 / 781 | 14.8 | 0.50 vs 0.49 | +1.06 vs +0.66 | +0.40 |
| PE | HOLD | 456 / 855 | 14.2 | 0.49 vs 0.49 | +1.28 vs +0.73 | +0.56 |
| PE | PRE | 1020 / 2029 | 13.6 | 0.53 vs 0.47 | +4.55 vs -1.53 | +6.08 |
| PE | X | 385 / 616 | 8.8 | 0.47 vs 0.45 | +1.85 vs +1.13 | +0.72 |
| WT | L6M | 539 / 1167 | 19.2 | 0.60 vs 0.60 | +2.15 vs +1.75 | +0.40 |
| WT | HOLD | 609 / 1284 | 19.0 | 0.60 vs 0.58 | +2.24 vs +0.85 | +1.39 |
| WT | PRE | 1325 / 2940 | 17.7 | 0.59 vs 0.58 | +1.08 vs +0.37 | +0.70 |
| WT | X | 580 / 947 | 13.2 | 0.57 vs 0.58 | -0.38 vs +0.99 | -1.36 |

## 5. Exhaustion read: extension deciles (distance from the average in ATR, signal direction; D10 = most over-extended)


5-min price extension from the 20 average (ATR; high = over-extended) - KB (KB SEL deciles): lift per planned lot (70/30 N) and P(target)

| decile | n L6M | lift L6M | P(tgt) L6M | lift HOLD | lift PRE | lift X' |
|---|---|---|---|---|---|---|
| D1 | 139 | -2.26 | 0.49 | -3.01 | +0.46 | -4.60 |
| D2 | 133 | -12.49 | 0.40 | -11.55 | +3.83 | +1.67 |
| D3 | 124 | +2.74 | 0.52 | +2.86 | +0.92 | -3.52 |
| D4 | 98 | +0.85 | 0.51 | -0.93 | -4.39 | -1.25 |
| D5 | 114 | -4.46 | 0.46 | -4.18 | +6.12 | +2.64 |
| D6 | 130 | +2.82 | 0.52 | +3.08 | -3.27 | -8.86 |
| D7 | 141 | -0.97 | 0.49 | -1.66 | -3.01 | +2.57 |
| D8 | 134 | -2.90 | 0.48 | -2.54 | -7.35 | -3.25 |
| D9 | 133 | +10.88 | 0.59 | +12.82 | +3.06 | +5.88 |
| D10 | 111 | +6.96 | 0.56 | +4.91 | +4.68 | +5.59 |

5-min price extension from the 20 average (ATR; high = over-extended) - ALL10 (per-book SEL deciles): lift per planned lot (70/30 N) and P(target)

| decile | n L6M | lift L6M | P(tgt) L6M | lift HOLD | lift PRE | lift X' |
|---|---|---|---|---|---|---|
| D1 | 1029 | -4.16 | 0.50 | -3.06 | -0.76 | -3.15 |
| D2 | 996 | -3.29 | 0.50 | -2.29 | -1.36 | +0.94 |
| D3 | 922 | -0.46 | 0.52 | -0.58 | +0.64 | +0.09 |
| D4 | 917 | -0.73 | 0.52 | -0.59 | +0.16 | +0.80 |
| D5 | 1011 | -1.20 | 0.52 | -2.11 | +0.08 | +0.29 |
| D6 | 971 | -0.68 | 0.52 | -0.95 | -0.57 | -3.67 |
| D7 | 989 | +3.27 | 0.56 | +2.71 | +1.85 | -0.62 |
| D8 | 1042 | -1.07 | 0.52 | -0.72 | -0.95 | -0.47 |
| D9 | 964 | +5.23 | 0.57 | +5.71 | +0.90 | +1.77 |
| D10 | 900 | +3.73 | 0.58 | +2.39 | -0.00 | +3.51 |

15-min price extension from the 20 average (ATR; high = over-extended) - KB (KB SEL deciles): lift per planned lot (70/30 N) and P(target)

| decile | n L6M | lift L6M | P(tgt) L6M | lift HOLD | lift PRE | lift X' |
|---|---|---|---|---|---|---|
| D1 | 145 | -1.74 | 0.49 | -1.41 | +1.76 | -2.83 |
| D2 | 123 | -1.92 | 0.50 | -0.77 | -1.18 | -1.16 |
| D3 | 108 | +3.88 | 0.55 | +4.83 | +5.32 | -1.23 |
| D4 | 136 | -12.98 | 0.39 | -13.03 | -8.06 | -0.04 |
| D5 | 117 | -4.12 | 0.45 | -5.16 | +1.45 | -2.52 |
| D6 | 127 | +1.56 | 0.51 | -1.31 | -0.94 | -4.42 |
| D7 | 118 | +0.43 | 0.50 | -0.10 | +1.91 | -5.18 |
| D8 | 145 | +3.93 | 0.54 | +3.78 | -2.52 | +4.47 |
| D9 | 133 | +8.67 | 0.56 | +10.11 | -5.46 | +5.42 |
| D10 | 105 | +3.27 | 0.51 | +3.46 | +8.42 | +4.91 |

15-min price extension from the 20 average (ATR; high = over-extended) - ALL10 (per-book SEL deciles): lift per planned lot (70/30 N) and P(target)

| decile | n L6M | lift L6M | P(tgt) L6M | lift HOLD | lift PRE | lift X' |
|---|---|---|---|---|---|---|
| D1 | 997 | -2.24 | 0.52 | -1.28 | -0.34 | -3.94 |
| D2 | 953 | -1.89 | 0.51 | -1.65 | -1.14 | -0.64 |
| D3 | 950 | -0.06 | 0.53 | -0.47 | +2.25 | -0.57 |
| D4 | 992 | -2.33 | 0.51 | -2.05 | -2.57 | +2.88 |
| D5 | 982 | -1.49 | 0.51 | -2.32 | +0.50 | -0.77 |
| D6 | 986 | +2.47 | 0.55 | +1.42 | -0.46 | -1.70 |
| D7 | 980 | +2.39 | 0.54 | +2.55 | -0.48 | +0.01 |
| D8 | 1057 | +2.08 | 0.55 | +2.19 | -0.29 | +2.06 |
| D9 | 1014 | +0.06 | 0.53 | +1.31 | -3.87 | +0.68 |
| D10 | 830 | +1.00 | 0.54 | +0.15 | +6.62 | +1.77 |

15-min price extension from the 50 average (ATR; high = over-extended) - KB (KB SEL deciles): lift per planned lot (70/30 N) and P(target)

| decile | n L6M | lift L6M | P(tgt) L6M | lift HOLD | lift PRE | lift X' |
|---|---|---|---|---|---|---|
| D1 | 142 | +1.65 | 0.54 | +0.90 | +7.30 | -10.09 |
| D2 | 120 | -3.70 | 0.47 | -1.92 | -0.39 | -0.25 |
| D3 | 123 | -3.65 | 0.48 | -1.41 | +1.09 | +11.11 |
| D4 | 117 | -11.75 | 0.38 | -13.55 | -4.22 | -7.88 |
| D5 | 109 | -3.13 | 0.48 | -3.86 | -1.53 | +0.47 |
| D6 | 128 | +6.08 | 0.55 | +6.70 | -3.69 | +1.03 |
| D7 | 126 | +4.03 | 0.54 | +2.22 | -6.58 | -6.98 |
| D8 | 133 | +5.58 | 0.56 | +4.63 | +3.69 | -3.35 |
| D9 | 155 | -0.10 | 0.50 | +0.44 | -2.20 | +13.97 |
| D10 | 104 | +3.45 | 0.50 | +5.18 | +6.96 | -0.85 |

15-min price extension from the 50 average (ATR; high = over-extended) - ALL10 (per-book SEL deciles): lift per planned lot (70/30 N) and P(target)

| decile | n L6M | lift L6M | P(tgt) L6M | lift HOLD | lift PRE | lift X' |
|---|---|---|---|---|---|---|
| D1 | 994 | +0.05 | 0.54 | +0.97 | +0.43 | -5.95 |
| D2 | 982 | -5.07 | 0.49 | -4.10 | +0.85 | -1.04 |
| D3 | 932 | -4.00 | 0.50 | -3.56 | -0.67 | +2.54 |
| D4 | 940 | +1.07 | 0.54 | +0.02 | +0.35 | +0.98 |
| D5 | 945 | -0.45 | 0.52 | -0.32 | -0.70 | -1.74 |
| D6 | 927 | +2.73 | 0.55 | +1.64 | -3.16 | -1.61 |
| D7 | 1041 | +5.97 | 0.58 | +5.12 | -2.10 | -4.52 |
| D8 | 1047 | +0.91 | 0.54 | +0.87 | -1.15 | +6.26 |
| D9 | 1083 | -2.34 | 0.52 | -1.62 | +0.98 | +5.27 |
| D10 | 850 | +1.07 | 0.53 | +0.85 | +5.44 | -1.19 |

1-hour price extension from the 50 average (ATR; high = over-extended) - KB (KB SEL deciles): lift per planned lot (70/30 N) and P(target)

| decile | n L6M | lift L6M | P(tgt) L6M | lift HOLD | lift PRE | lift X' |
|---|---|---|---|---|---|---|
| D1 | 115 | +4.76 | 0.55 | +6.14 | +4.34 | -4.50 |
| D2 | 139 | -5.07 | 0.46 | -3.99 | -1.68 | -0.59 |
| D3 | 132 | +0.10 | 0.50 | -1.22 | -0.53 | -5.52 |
| D4 | 130 | -1.99 | 0.48 | -0.63 | -0.72 | -2.70 |
| D5 | 104 | +8.55 | 0.59 | +6.74 | +1.06 | +6.34 |
| D6 | 118 | -4.46 | 0.47 | -5.43 | -2.56 | +3.28 |
| D7 | 127 | +3.29 | 0.54 | +2.74 | -1.76 | +1.73 |
| D8 | 143 | -4.88 | 0.43 | -5.63 | -5.47 | -3.37 |
| D9 | 146 | -1.38 | 0.49 | -0.55 | -0.23 | +12.45 |
| D10 | 103 | +5.06 | 0.52 | +5.54 | +8.10 | -4.05 |

1-hour price extension from the 50 average (ATR; high = over-extended) - ALL10 (per-book SEL deciles): lift per planned lot (70/30 N) and P(target)

| decile | n L6M | lift L6M | P(tgt) L6M | lift HOLD | lift PRE | lift X' |
|---|---|---|---|---|---|---|
| D1 | 842 | +2.04 | 0.54 | +3.87 | -0.29 | -3.96 |
| D2 | 1092 | -4.31 | 0.50 | -3.41 | -0.39 | -2.30 |
| D3 | 1078 | -0.34 | 0.53 | -0.34 | +0.37 | -0.34 |
| D4 | 892 | +1.86 | 0.55 | +1.09 | +2.09 | -0.04 |
| D5 | 977 | -3.35 | 0.51 | -3.24 | -1.76 | +2.58 |
| D6 | 819 | +3.85 | 0.56 | +3.12 | -1.07 | -1.72 |
| D7 | 1016 | -0.38 | 0.53 | -1.21 | -2.61 | -2.03 |
| D8 | 1133 | +1.38 | 0.54 | +0.82 | -2.19 | +0.10 |
| D9 | 1163 | +0.88 | 0.53 | +1.18 | +1.77 | +6.81 |
| D10 | 729 | -0.52 | 0.51 | -0.64 | +4.30 | +0.52 |

## 6. Agree with the higher-timeframe trend vs not (sign of the HTF tool in the signal direction)

| HTF tool | agree share | lift agree-vs-disagree per contract: L6M | HOLD | PRE | X' | P(tgt) agree/disagree L6M | n disagree L6M |
|---|---|---|---|---|---|---|---|
| 1-hour ema2050 direction sign | 51% | +0.16 | -0.60 | +0.50 | +2.50 | 0.53/0.53 | 4703 |
| 1-hour st direction sign | 55% | +1.62 | +0.93 | +1.83 | +3.59 | 0.53/0.52 | 4234 |
| 1-hour di direction sign | 57% | +0.51 | +0.36 | +0.06 | +1.70 | 0.53/0.53 | 4063 |
| 1-hour c200 direction sign | 54% | -2.50 | -1.73 | +0.17 | +0.08 | 0.52/0.54 | 4431 |
| 1-hour lr50 direction sign | 50% | -0.51 | -2.22 | +2.12 | +3.80 | 0.53/0.53 | 4851 |
| 1-hour macd direction sign | 58% | +1.64 | +1.38 | -1.21 | +1.36 | 0.53/0.53 | 4072 |
| 1-hour ich direction sign | 56% | +2.38 | +1.25 | +2.33 | +3.88 | 0.53/0.52 | 3719 |
| 1-hour psar direction sign | 59% | -1.31 | -1.58 | +0.10 | +3.86 | 0.52/0.54 | 3961 |
| 4-hour ema2050 direction sign | 49% | -4.87 | -3.99 | -0.09 | -0.83 | 0.50/0.55 | 5073 |
| 4-hour st direction sign | 50% | +0.59 | +0.97 | -0.28 | +1.53 | 0.53/0.53 | 4866 |
| 4-hour di direction sign | 51% | -0.60 | -1.87 | -0.45 | +3.58 | 0.53/0.53 | 4711 |
| 4-hour c200 direction sign | 50% | -2.97 | -2.24 | +0.86 | +1.87 | 0.51/0.55 | 4936 |
| 4-hour lr50 direction sign | 49% | -4.37 | -3.56 | -0.55 | +0.53 | 0.51/0.55 | 5121 |
| 4-hour macd direction sign | 52% | +2.74 | +1.18 | +2.09 | +0.24 | 0.54/0.52 | 4595 |
| 4-hour ich direction sign | 51% | -2.97 | -2.29 | +0.12 | +2.57 | 0.51/0.54 | 4161 |
| 4-hour psar direction sign | 50% | -1.84 | -3.00 | +1.03 | +0.70 | 0.52/0.54 | 4887 |
| daily ema2050 direction sign | 50% | -1.13 | -0.58 | -0.81 | +2.49 | 0.52/0.54 | 4924 |
| daily st direction sign | 50% | -5.25 | -4.36 | +1.15 | -1.17 | 0.51/0.55 | 5194 |
| daily di direction sign | 49% | -1.28 | -0.76 | +0.48 | +1.32 | 0.53/0.53 | 5062 |
| daily c200 direction sign | 51% | -0.57 | -0.07 | +0.82 | +3.14 | 0.52/0.54 | 4875 |
| daily lr50 direction sign | 50% | -2.10 | -1.46 | -2.33 | +2.59 | 0.51/0.54 | 4958 |
| daily macd direction sign | 49% | -3.15 | -3.22 | -0.72 | -1.40 | 0.52/0.54 | 5067 |
| daily ich direction sign | 50% | -2.31 | -1.61 | +0.33 | +4.01 | 0.51/0.54 | 4594 |
| daily psar direction sign | 50% | -1.89 | -0.85 | +0.14 | +1.99 | 0.52/0.54 | 4917 |
| cross-timeframe agreement htf_ema2050 | 50% | -1.54 | -0.96 | +0.63 | +1.70 | 0.52/0.54 | 4942 |
| cross-timeframe agreement htf_st | 52% | +0.15 | +0.51 | +0.75 | +1.13 | 0.53/0.53 | 4623 |
| cross-timeframe agreement net_all | 78% | +0.04 | -1.03 | -0.84 | +3.30 | 0.53/0.53 | 1933 |
| cross-timeframe agreement tf_majority | 73% | +0.49 | -0.12 | +0.25 | +4.28 | 0.53/0.53 | 1743 |

## 7. Coverage, definitions, gaps
* Bars: 1/3/5/15/30-min = tick-built library bars (epoch buckets, partial session-end bars dropped); 1h/4h/1d = Databento NQ volume-roll 1-min series with roll jumps removed (adjusted OHLC, history from 2021, 4h/1d anchored at 18:00 ET). Every value is taken at the last bar CLOSED at or before the signal second. Daily items for the current label day are never used before the day completes.
* Cuts: per book, from PRE+X' trades only, fixed for every window. The map's "lift" is bucket mean minus the unconditional mean of the same unit / session / window.
* Measures: 1,219 (CHART 968, STAT 95, CROSS 76, FLOW 68, DAY 12); 22 are EINT1-NEAR (the generic 1-min versions already scored); the full per-book / per-session / per-window table is out/trendgate/tables/map_buckets.parquet (1,499,955 rows: measure x unit x session x window x bucket, with n, tpw, P(target), MAE, pts per planned lot and per contract on M/N/LC).
* NAMED GAPS (not built, nothing fabricated): breadth ($TICK/$ADD, advancers/decliners); a supplied dealer-gamma / strike file (the OPRA-flow-implied gamma proxy exists for RTH 2022+ but uses tick-rule customer signs that agree with the true side only 56%: proxy, capped at CANDIDATE); intraday VIX/VX/implied-vol surface (only the prior-day close of VIX, VIX9D, VIX3M, VIX6M, VVIX, SKEW and the 0DTE ATM IV at 30-min slots); VX futures curve; MBO-derived iceberg count and queue-refill ratio; OFI as a time series (only the signal-second OFI); earnings-night calendar; sector/factor ETFs; DX (6E used); CR book (no 1-s path, unavailable).
