# REPORT C8-Q1 — ERA DIAGNOSTIC (not a candidate; no gates)
Question: why does the pair earn only in 2024-2026? Descriptive only. n = 14 calendar years (2013-2026; 2026 has 196 RTH days / 42 weeks). Spec: PREREG_AUTOPILOT.md 'CYCLE 8'.

## Method
- NQ 1-minute bars 2013-2026 (data/autopilot/ohlcv1m), the C3-H2 back-adjusted series (outputs/autopilot/c3/h23/series_NQ_long.npz). All statistics are computed **within a contract and within an RTH session (09:30-16:00 ET)**; days with a roll or fewer than 300 bars are dropped (3,431 days kept). Variance ratio VR(q) = Var(q-min return) / (q * Var(1-min return)) from non-overlapping q-minute closes inside the session; autocorrelations are lag-1 of non-overlapping 1/5/15-minute point returns; VWAP persistence from the session VWAP (from 09:30); trend day = |close-open|/(high-low) > 0.5 (defined a priori); ADR% = mean RTH (high-low)/open on the raw open; realised vol = annualised RTH 1-min vol / open; volume = RTH contracts/day, plus shares in 09:30-10:00, 11:30-14:00 and 15:30-16:00.
- ST flip-to-flip run (ATR120 x 2.0, close, Wilder ATR) and HM flip-to-flip run (HMA20 vs HMA55 of close minus session VWAP reset 00:00 UTC-4) are measured on the continuous 24h 1-minute series as minutes between consecutive signal flips (approximation of the nt8sim signals: no slope or EMA filters, no session windows).
- Pair yearly weekly Sharpe: 2013-2022 from the C3-H2 1-minute engine (frozen live rules; 90% entry match to the 1-second engine, see REPORT_C3_H2.md); 2023-2026 from the live corrected rows, Cfg(wk_floor=8, wk_loss_pb=None), computed in a clean process (2023 starts 2023-02-10, 47 weeks).
- Relation = Spearman rank correlation of each yearly statistic with the pair's yearly Sharpe (n=14), 90% bootstrap interval over years (4,000), and a permutation p (4,000). Descriptive: 21 statistics tested, no multiplicity correction, nothing here is a test of a rule.

## Pair yearly Sharpe next to the statistics
|   yr |   pair_sharpe |   adr_pct |   rv_ann |   trend_share |   eff |   VR5 |   VR15 |   VR30 |   VR60 |    ac1 |    ac5 |   ac15 |   vwap_run_mean |   st_run_mean_min |   hm_run_mean_min |   volume |   vol_mid_share |
|-----:|--------------:|----------:|---------:|--------------:|------:|------:|-------:|-------:|-------:|-------:|-------:|-------:|----------------:|------------------:|------------------:|---------:|----------------:|
| 2013 |        -0.489 |     0.963 |   10.134 |         0.442 | 0.442 | 0.925 |  0.861 |  0.812 |  0.694 | -0.024 | -0.018 |  0.01  |          35.805 |            16.276 |            17.059 |   182367 |           0.253 |
| 2014 |        -1.088 |     1.105 |   11.746 |         0.481 | 0.471 | 0.932 |  0.839 |  0.79  |  0.788 | -0.044 | -0.006 |  0.01  |          37.608 |            16.406 |            17.171 |   233930 |           0.255 |
| 2015 |         0.622 |     1.274 |   13.738 |         0.452 | 0.474 | 0.967 |  0.872 |  0.824 |  0.788 | -0.014 | -0.02  | -0.01  |          36.758 |            16.996 |            17.062 |   201200 |           0.253 |
| 2016 |         0.128 |     1.158 |   12.468 |         0.442 | 0.458 | 0.987 |  0.944 |  0.919 |  0.772 | -0.015 | -0.006 | -0.006 |          36.174 |            17.517 |            17.169 |   193962 |           0.259 |
| 2017 |         0.13  |     0.781 |    8.381 |         0.414 | 0.44  | 0.948 |  0.855 |  0.81  |  0.775 | -0.026 | -0.009 |  0.001 |          37.514 |            17.424 |            17.209 |   209344 |           0.265 |
| 2018 |        -1.18  |     1.646 |   17.481 |         0.476 | 0.484 | 0.96  |  0.906 |  0.855 |  0.807 | -0.013 | -0.01  | -0.006 |          37.754 |            19.71  |            17.148 |   372714 |           0.287 |
| 2019 |        -0.094 |     1.131 |   11.657 |         0.43  | 0.45  | 0.987 |  0.898 |  0.816 |  0.724 |  0.009 | -0.005 | -0.02  |          40.443 |            20.323 |            17.203 |   323543 |           0.275 |
| 2020 |        -1.435 |     2.13  |   22.703 |         0.482 | 0.484 | 1.031 |  0.93  |  0.843 |  0.683 |  0.043 | -0.026 |  0.003 |          40.736 |            20.924 |            17.14  |   393624 |           0.29  |
| 2021 |        -0.746 |     1.371 |   14.156 |         0.546 | 0.503 | 1.008 |  0.934 |  0.876 |  0.769 |  0.018 | -0.007 | -0.013 |          45.932 |            20.713 |            17.144 |   400670 |           0.273 |
| 2022 |        -2.087 |     2.439 |   24.32  |         0.584 | 0.539 | 0.986 |  0.889 |  0.904 |  0.848 |  0.021 | -0.01  |  0.051 |          36.44  |            21.035 |            17.33  |   493967 |           0.28  |
| 2023 |        -0.029 |     1.451 |   14.309 |         0.52  | 0.493 | 0.944 |  0.915 |  0.886 |  0.795 | -0.004 |  0.016 |  0.015 |          36.281 |            20.68  |            17.124 |   485792 |           0.281 |
| 2024 |         2.149 |     1.3   |   13.262 |         0.466 | 0.466 | 1.025 |  0.939 |  0.918 |  0.769 |  0.01  | -0.032 |  0.022 |          36.934 |            20.765 |            17.229 |   453348 |           0.285 |
| 2025 |         2.35  |     1.508 |   16.313 |         0.494 | 0.483 | 0.982 |  1.034 |  0.923 |  0.856 | -0.007 |  0.009 | -0.024 |          35.7   |            20.479 |            17.162 |   420571 |           0.301 |
| 2026 |         1.984 |     1.419 |   14.946 |         0.469 | 0.468 | 0.954 |  0.908 |  0.801 |  0.699 |  0     | -0.005 | -0.009 |          41.828 |            20.522 |            17.086 |   400731 |           0.286 |

## Which statistic tracks the pair? (sorted by |rho|)
| stat             |    rho |    ci5 |   ci95 |   perm_p |   mean_2023_26 |   old_mean |     old_sd |      z |   pct_of_mean_2023_26 |   n_new_outside_old_range |
|:-----------------|-------:|-------:|-------:|---------:|---------------:|-----------:|-----------:|-------:|----------------------:|--------------------------:|
| eff              | -0.451 | -0.746 |  0.059 |    0.114 |          0.477 |      0.474 |      0.03  |  0.098 |                    60 |                         0 |
| ac15             | -0.371 | -0.784 |  0.188 |    0.194 |          0.001 |      0.002 |      0.02  | -0.054 |                    60 |                         1 |
| trend_share      | -0.367 | -0.722 |  0.116 |    0.19  |          0.487 |      0.475 |      0.053 |  0.234 |                    80 |                         0 |
| VR15             |  0.345 | -0.145 |  0.734 |    0.214 |          0.949 |      0.893 |      0.036 |  1.56  |                   100 |                         1 |
| vwap_run_mean    | -0.297 | -0.706 |  0.187 |    0.314 |         37.686 |     38.517 |      3.096 | -0.268 |                    60 |                         1 |
| rv_ann           | -0.292 | -0.734 |  0.316 |    0.305 |         14.708 |     14.678 |      5.263 |  0.006 |                    70 |                         0 |
| adr_pct          | -0.288 | -0.737 |  0.345 |    0.329 |          1.42  |      1.4   |      0.525 |  0.038 |                    70 |                         0 |
| vol_open_share   |  0.262 | -0.326 |  0.764 |    0.356 |          0.161 |      0.169 |      0.01  | -0.773 |                    30 |                         0 |
| ac5              |  0.244 | -0.321 |  0.739 |    0.384 |         -0.003 |     -0.012 |      0.007 |  1.202 |                   100 |                         3 |
| ac1              | -0.231 | -0.655 |  0.326 |    0.441 |         -0     |     -0.005 |      0.026 |  0.155 |                    60 |                         0 |
| VR30             |  0.169 | -0.413 |  0.654 |    0.557 |          0.882 |      0.845 |      0.043 |  0.864 |                    80 |                         1 |
| st_run_mean_min  | -0.165 | -0.641 |  0.395 |    0.566 |         20.612 |     18.732 |      1.977 |  0.951 |                    70 |                         0 |
| st_run_med_min   | -0.164 | -0.575 |  0.347 |    0.571 |         14     |     12.8   |      1.549 |  0.775 |                    90 |                         0 |
| vol_close_share  |  0.152 | -0.315 |  0.583 |    0.594 |          0.095 |      0.099 |      0.006 | -0.67  |                    20 |                         0 |
| vwap_above_share | -0.13  | -0.638 |  0.395 |    0.654 |          0.561 |      0.564 |      0.036 | -0.089 |                    40 |                         0 |
| vwap_run_med     | -0.103 | -0.494 |  0.346 |    0.726 |          3.625 |      3.35  |      0.474 |  0.58  |                    70 |                         0 |
| hm_run_mean_min  | -0.077 | -0.554 |  0.436 |    0.8   |         17.15  |     17.163 |      0.077 | -0.167 |                    50 |                         0 |
| vol_mid_share    |  0.055 | -0.488 |  0.594 |    0.854 |          0.288 |      0.269 |      0.014 |  1.379 |                    90 |                         1 |
| VR5              | -0.033 | -0.472 |  0.464 |    0.912 |          0.976 |      0.973 |      0.033 |  0.085 |                    50 |                         0 |
| VR60             |  0.033 | -0.558 |  0.605 |    0.914 |          0.78  |      0.765 |      0.051 |  0.289 |                    60 |                         1 |
| volume           |  0.007 | -0.532 |  0.515 |    0.987 |     440111     | 300532     | 110448     |  1.264 |                    90 |                         0 |

`z` = (mean of 2023-2026 yearly values - mean of 2013-2022) / sd of 2013-2022; `pct_of_mean_2023_26` = percentile rank of the 2023-26 mean among the ten 2013-2022 yearly values; the last column counts how many of the four 2023-2026 years fall outside the 2013-2022 min-max range.

## Half-years 2022-2026
|   yr |   half |   pair_live_sharpe |   adr_pct |   rv_ann |   trend_share |   VR15 |   VR60 |    ac5 |   vwap_run_mean |   volume |
|-----:|-------:|-------------------:|----------:|---------:|--------------:|-------:|-------:|-------:|----------------:|---------:|
| 2022 |      1 |            nan     |     2.67  |   25.961 |         0.597 |  0.879 |  0.831 | -0.009 |          36.691 |   500567 |
| 2022 |      2 |            nan     |     2.212 |   21.856 |         0.571 |  0.907 |  0.881 | -0.013 |          36.193 |   487473 |
| 2023 |      1 |             -0.025 |     1.616 |   15.986 |         0.532 |  0.894 |  0.805 |  0.038 |          38.281 |   485438 |
| 2023 |      2 |             -0.032 |     1.286 |   12.896 |         0.508 |  0.939 |  0.784 | -0.007 |          34.282 |   486146 |
| 2024 |      1 |              2.253 |     1.153 |   11.394 |         0.476 |  0.995 |  0.834 | -0.011 |          35.821 |   486106 |
| 2024 |      2 |              1.998 |     1.447 |   14.554 |         0.456 |  0.911 |  0.737 | -0.042 |          38.038 |   420852 |
| 2025 |      1 |              1.861 |     1.874 |   20.542 |         0.508 |  1.089 |  0.859 | -0     |          36.156 |   436068 |
| 2025 |      2 |              2.931 |     1.151 |   12.41  |         0.48  |  0.928 |  0.849 |  0.028 |          35.254 |   405446 |
| 2026 |      1 |              1.918 |     1.532 |   16.304 |         0.488 |  0.901 |  0.667 |  0.006 |          44.953 |   413981 |
| 2026 |      2 |              2.035 |     1.23  |   12.811 |         0.438 |  0.924 |  0.769 | -0.03  |          36.563 |   378406 |

## Reading (plain)
1. **No tested statistic explains the pair's edge.** The largest |rho| is 0.45 (RTH trend efficiency, negative) with a 90% interval [-0.75, +0.06] and permutation p = 0.11; every other interval also spans zero. With n = 14 and 21 statistics, none is distinguishable from chance. The sign pattern is mildly consistent (less efficient trending days and higher 15-minute variance ratio go with higher pair Sharpe, which is the opposite of the 'pair needs trends' story) but it is not significant.
2. **2023-2026 does not look like a different market on these measures.** The 2023-26 means sit between the 20th and 90th percentile of the 2013-2022 yearly values for 19 of the 21 statistics (|z| < 1 for 17; volume, mid-day volume share and ST median run exactly at the 90th); the two above the 90th percentile are VR(15) and the 5-minute autocorrelation. Outside the 2013-2022 range: VR(15) is above the old maximum in 2025 (1.03 vs old max 0.944, 1 year); the 5-minute autocorrelation, VWAP run length, VR(30), VR(60), mid-day volume share and the 15-minute autocorrelation each have one year outside the old range (3 for the 5-minute autocorrelation). These are single-year excursions, not a level shift. Realised vol and ADR in 2023-26 (14.7%, 1.42%) are at the median of the old years, and 2020 and 2022 (high vol, pair losing hardest at Sharpe -1.4 and -2.1) have higher vol than any of 2023-26.
3. **ST runs lengthened from 2013 to 2020 (mean 16 to 21 minutes) and have been flat since**; the HM cross-run length is a constant 17.1 minutes in every year (it is structural to HMA20/55, not informative). Neither moves with the pair's Sharpe (rho -0.17 and -0.08).
4. **What this says about the edge.** Market-structure measures from 1-minute bars do not separate the years in which the pair works (2024-2026, Sharpe 2.0-2.4) from those in which it loses (2018, 2020-2022), and the 2023-2026 values look like draws from the old distribution. The pair's change in performance is therefore **not explained by any of these variables**. The most economical reading consistent with the data (not proven by it) is that the frozen parameters and rules were fitted to 2023-2026 and the edge is period-specific, as the clean-only selection and the dispersion of the neighbour grid in D3 section 1 would also suggest. A genuine new regime driven by something not measured here (for example 0DTE option positioning, which needs options data this box does not have) cannot be excluded.
5. **What would sharpen it:** (a) the same diagnostic on ES 2013-2026 with the pair re-run on ES (does ES show the same 2024-26 pattern? T3 S2 says ES loses in the window, which argues against a market-wide regime); (b) options/open-interest data for 0DTE share; (c) walk-forward re-fit evidence from D3 section 4, which found re-fitting no better than a random neighbour.

## Caveats
n = 14 years, 2026 is partial; the 2013-2022 pair series comes from the 1-minute engine (90% entry match, 2023 optimistic) while 2023-2026 comes from the live corrected engine; the ST/HM run lengths are unfiltered approximations; statistics use RTH only while the pair trades 24 hours (Globex carries most of the P&L, per D1 Family 6) — a Globex-session version of VR and autocorrelation was not computed; no cost or slippage effects are involved here.

Runtime: about 1 minute of compute (stats 30 s, relations 20 s), 1 worker. Code: code/census/night_ins/ap_c8_q1_{live,stats,rel,rep}.py; data: outputs/autopilot/c8/q1/.

DONE C8_Q1
