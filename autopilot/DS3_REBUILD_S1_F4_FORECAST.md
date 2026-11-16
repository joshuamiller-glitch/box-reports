# DS3_REBUILD_S1_F4_FORECAST - T-REBUILD Stage 1 family 4 (range forecasts: HAR, CME NQ options, UW; plus range used / remaining in engine points). W-R2, built 2026-11-16T18:02Z.

**VERDICT (data ends 2026-11-13 signals, 2026-10-30 not required here; FIRST PASS; no PASS claim): 50 forecast / range-used conditions (HAR 16, HAR+CME 16 [flag: options feed D7 lacks], UW a/b/c 6 each [flag: UW feed]) scored against path outcomes of the 193,628-signal universe (signals not in a position, thinned to one per book/side/30 min, 63,338 rows) per book and book x session. Cells passing the bar (|weekly-cluster zw| above the nonsense 99th percentile for that cell kind, same sign in L6M, same sign every year with >= 3 years): mfe_R 31 of 2150; mae_R 164 of 2150; p1R 4 of 2150; t_tgt 55 of 2200 (book and book x session cells). The mean-R effect against the W-PM raw table is pending (table not built yet); p1R is the proxy. Nonsense bar and nonsense rate (share of 200 meaningless conditions with |zw|>2) are printed beside every table.**

Conditions: for each source (har, v1, uwa, uwb, uwc): hi3 / lo3 = forecast of the signal session in the top / bottom expanding tercile, hi5 / lo5 = top / bottom quintile, rup / rdn = forecast ratio to its expanding median above 1.15 / below 0.87. For har and v1 also range used so far / forecast: u25 u50 u75 u100 (< k) and ge100; tgtover075/100/125/150/200 = target distance > k x remaining forecast range, in engine points (bar price used for the conversion: the minute bar store is additively spliced; ln ranges exact). Forecast of the session containing the signal, available at the session start; so-far range from complete 1-min bars. Column file: /mnt/l2/l2vast/_range2/cols_r2/r2_range.parquet (+ _meta.csv).

## MFE (max favourable 120 min, R; lift>0 = goes further)
Nonsense bar (99th pct |zw|): ALL 7.2, book 6.2, sess 5.2, book_sess 4.2; nonsense |zw|>2 rate: ALL 0.17, book 0.15, sess 0.13, book_sess 0.09

Pooled (ALL cells), top 14 by |zw|:

| condition | n yes | share | mean yes | mean no | lift | zw | yrs same sign | L6M lift | pass |
|---|---|---|---|---|---|---|---|---|---|
| c_R2_har_u25 | 3273 | 0.07 | 0.999 | 1.203 | -0.204 | -7.2 | 0/4 | -0.236 | False |
| c_R2_v1_tgtover075 | 27277 | 0.62 | 1.036 | 1.330 | -0.294 | -5.6 | 0/4 | -0.037 | False |
| c_R2_har_u100 | 36843 | 0.79 | 1.149 | 1.338 | -0.189 | -4.2 | 0/4 | -0.386 | False |
| c_R2_har_ge100 | 9868 | 0.21 | 1.338 | 1.149 | +0.189 | +4.2 | 4/4 | +0.386 | False |
| c_R2_v1_u25 | 3033 | 0.07 | 1.046 | 1.156 | -0.110 | -4.1 | 0/4 | -0.136 | False |
| c_R2_v1_tgtover100 | 22786 | 0.52 | 1.039 | 1.265 | -0.226 | -4.0 | 0/4 | +0.006 | False |
| c_R2_har_u75 | 27854 | 0.60 | 1.138 | 1.263 | -0.125 | -3.6 | 0/4 | -0.243 | False |
| c_R2_v1_lo5 | 4763 | 0.11 | 0.674 | 1.231 | -0.557 | -3.2 | 0/4 | -0.657 | False |
| c_R2_v1_hi3 | 25849 | 0.58 | 1.381 | 0.879 | +0.502 | +2.9 | 4/4 | +0.553 | False |
| c_R2_uwb_lo3 | 7431 | 0.27 | 0.952 | 1.428 | -0.476 | -2.8 | 0/2 | -0.326 | False |
| c_R2_har_tgtover200 | 16315 | 0.35 | 1.211 | 1.176 | +0.035 | +2.8 | 2/4 | +0.322 | False |
| c_R2_har_u50 | 14600 | 0.31 | 1.117 | 1.221 | -0.104 | -2.7 | 0/4 | -0.192 | False |
| c_R2_har_tgtover150 | 18823 | 0.40 | 1.189 | 1.188 | +0.001 | +2.7 | 2/4 | +0.288 | False |
| c_R2_v1_lo3 | 7685 | 0.17 | 0.759 | 1.257 | -0.498 | -2.6 | 0/4 | -0.429 | False |

Per book, top 4 per book by |zw| (same sign in L6M shown):

| book | condition | n yes | lift | zw | yrs | L6M lift | pass |
|---|---|---|---|---|---|---|---|
| A7 | c_R2_har_ge100 | 1761 | +0.296 | +4.1 | 4/4 | +0.519 | False |
| A7 | c_R2_har_u100 | 5493 | -0.296 | -4.1 | 0/4 | -0.519 | False |
| A7 | c_R2_v1_lo5 | 789 | -0.518 | -3.8 | 0/4 | -0.542 | False |
| A7 | c_R2_v1_u100 | 5101 | -0.231 | -3.7 | 0/4 | -0.510 | False |
| H7 | c_R2_har_u75 | 1793 | -0.273 | -4.9 | 0/4 | -0.386 | False |
| H7 | c_R2_har_u100 | 2288 | -0.327 | -4.7 | 0/3 | -0.593 | False |
| H7 | c_R2_har_ge100 | 467 | +0.327 | +4.7 | 3/3 | +0.593 | False |
| H7 | c_R2_har_tgtover200 | 915 | +0.072 | +3.8 | 3/4 | +0.499 | False |
| K7 | c_R2_v1_tgtover075 | 6346 | -0.313 | -6.5 | 0/4 | -0.019 | True |
| K7 | c_R2_v1_tgtover100 | 5352 | -0.242 | -5.9 | 0/4 | +0.023 | False |
| K7 | c_R2_har_u25 | 925 | -0.256 | -5.6 | 0/4 | -0.262 | False |
| K7 | c_R2_har_tgtover075 | 6968 | -0.185 | -3.9 | 1/4 | +0.169 | False |
| M7 | c_R2_har_u25 | 773 | -0.328 | -7.3 | 0/4 | -0.273 | True |
| M7 | c_R2_v1_u25 | 750 | -0.239 | -5.4 | 0/4 | -0.166 | False |
| M7 | c_R2_har_tgtover125 | 3407 | +0.097 | +5.2 | 3/4 | +0.323 | False |
| M7 | c_R2_har_tgtover150 | 3060 | +0.100 | +4.7 | 3/4 | +0.368 | False |
| O7 | c_R2_v1_tgtover100 | 132 | -0.991 | -2.3 | 0/2 | +0.607 | False |
| O7 | c_R2_v1_hi3 | 204 | +1.015 | +2.2 | 3/3 | +0.958 | False |
| O7 | c_R2_har_hi3 | 201 | +0.847 | +1.5 | 3/3 | +1.149 | False |
| O7 | c_R2_har_tgtover075 | 213 | -0.815 | -1.3 | 0/2 | +0.752 | False |
| P7 | c_R2_v1_hi3 | 7788 | +0.494 | +3.6 | 3/4 | +0.559 | False |
| P7 | c_R2_har_u100 | 10583 | -0.172 | -3.6 | 0/4 | -0.290 | False |
| P7 | c_R2_har_ge100 | 3019 | +0.172 | +3.6 | 4/4 | +0.290 | False |
| P7 | c_R2_v1_tgtover075 | 8114 | -0.243 | -3.4 | 0/4 | -0.042 | False |
| U7 | c_R2_har_u75 | 1292 | -0.220 | -3.3 | 0/4 | -0.464 | False |
| U7 | c_R2_har_u25 | 85 | -0.468 | -2.9 | 0/1 | -0.925 | False |
| U7 | c_R2_v1_tgtover100 | 1178 | -0.325 | -2.9 | 0/3 | +0.032 | False |
| U7 | c_R2_v1_u25 | 78 | -0.439 | -2.9 | 0/0 | -0.837 | False |

Book x session cells passing the bar: 29 of 1800:

| book | sess | condition | n yes | lift | zw | L6M lift |
|---|---|---|---|---|---|---|
| K7 | 3 | c_R2_har_u50 | 817 | +0.301 | +6.1 | +0.208 |
| K7 | 3 | c_R2_v1_u50 | 787 | +0.305 | +6.1 | +0.283 |
| M7 | 1 | c_R2_v1_u50 | 973 | -0.339 | -5.9 | -0.297 |
| K7 | 0 | c_R2_har_u25 | 393 | -0.403 | -5.8 | -0.468 |
| M7 | 1 | c_R2_v1_u75 | 1540 | -0.299 | -5.6 | -0.328 |
| M7 | 1 | c_R2_v1_tgtover125 | 986 | +0.118 | +5.5 | +0.241 |
| M7 | 1 | c_R2_har_u50 | 967 | -0.361 | -5.5 | -0.307 |
| H7 | 1 | c_R2_har_u50 | 250 | -0.318 | -5.4 | -0.246 |
| M7 | 1 | c_R2_har_tgtover150 | 871 | +0.182 | +5.4 | +0.290 |
| P7 | 4 | c_R2_v1_hi3 | 1363 | +0.704 | +5.4 | +1.205 |
| M7 | 1 | c_R2_har_tgtover100 | 1150 | +0.099 | +5.4 | +0.254 |
| M7 | 1 | c_R2_har_tgtover125 | 972 | +0.158 | +5.2 | +0.259 |
| M7 | 1 | c_R2_har_u75 | 1528 | -0.317 | -5.2 | -0.334 |
| M7 | 1 | c_R2_v1_tgtover100 | 1164 | +0.062 | +5.0 | +0.228 |
| M7 | 1 | c_R2_v1_tgtover150 | 861 | +0.144 | +4.9 | +0.284 |

## MAE (max adverse 120 min, R; lift>0 = more adverse)
Nonsense bar (99th pct |zw|): ALL 3.8, book 4.1, sess 3.3, book_sess 3.0; nonsense |zw|>2 rate: ALL 0.14, book 0.10, sess 0.08, book_sess 0.06

Pooled (ALL cells), top 14 by |zw|:

| condition | n yes | share | mean yes | mean no | lift | zw | yrs same sign | L6M lift | pass |
|---|---|---|---|---|---|---|---|---|---|
| c_R2_har_u25 | 3273 | 0.07 | 0.958 | 1.180 | -0.222 | -7.3 | 0/4 | -0.239 | True |
| c_R2_v1_u25 | 3033 | 0.07 | 0.968 | 1.125 | -0.157 | -7.1 | 0/4 | -0.158 | True |
| c_R2_v1_tgtover075 | 27277 | 0.62 | 0.993 | 1.309 | -0.315 | -6.5 | 0/4 | -0.106 | True |
| c_R2_har_u100 | 36843 | 0.79 | 1.123 | 1.317 | -0.194 | -5.9 | 0/4 | -0.206 | True |
| c_R2_har_ge100 | 9868 | 0.21 | 1.317 | 1.123 | +0.194 | +5.9 | 4/4 | +0.206 | True |
| c_R2_v1_lo5 | 4763 | 0.11 | 0.617 | 1.194 | -0.577 | -5.7 | 0/4 | -0.694 | True |
| c_R2_har_u75 | 27854 | 0.60 | 1.107 | 1.248 | -0.141 | -5.6 | 0/4 | -0.227 | True |
| c_R2_har_tgtover200 | 16315 | 0.35 | 1.196 | 1.147 | +0.049 | +4.9 | 4/4 | +0.201 | True |
| c_R2_v1_lo3 | 7685 | 0.17 | 0.693 | 1.224 | -0.532 | -4.9 | 0/4 | -0.603 | True |
| c_R2_v1_tgtover100 | 22786 | 0.52 | 1.002 | 1.234 | -0.232 | -4.5 | 0/4 | -0.041 | True |
| c_R2_har_u50 | 14600 | 0.31 | 1.095 | 1.196 | -0.101 | -4.1 | 0/4 | -0.171 | True |
| c_R2_uwc_lo3 | 7109 | 0.26 | 0.898 | 1.422 | -0.523 | -4.0 | 0/2 | -0.529 | False |
| c_R2_har_tgtover150 | 18823 | 0.40 | 1.169 | 1.161 | +0.007 | +4.0 | 3/4 | +0.197 | False |
| c_R2_v1_tgtover125 | 20005 | 0.45 | 1.013 | 1.197 | -0.184 | -3.4 | 0/4 | -0.015 | False |

Per book, top 4 per book by |zw| (same sign in L6M shown):

| book | condition | n yes | lift | zw | yrs | L6M lift | pass |
|---|---|---|---|---|---|---|---|
| A7 | c_R2_har_u75 | 3836 | -0.230 | -6.3 | 0/4 | -0.427 | True |
| A7 | c_R2_v1_u75 | 3461 | -0.143 | -5.9 | 0/4 | -0.292 | True |
| A7 | c_R2_har_tgtover200 | 3080 | +0.121 | +5.8 | 4/4 | +0.373 | True |
| A7 | c_R2_har_u100 | 5493 | -0.274 | -5.5 | 0/4 | -0.379 | True |
| H7 | c_R2_v1_tgtover075 | 1672 | -0.512 | -5.0 | 0/3 | -0.405 | True |
| H7 | c_R2_v1_tgtover100 | 1338 | -0.367 | -3.9 | 0/3 | -0.261 | False |
| H7 | c_R2_v1_tgtover125 | 1154 | -0.346 | -3.9 | 0/4 | -0.285 | False |
| H7 | c_R2_v1_tgtover150 | 1009 | -0.295 | -3.8 | 0/4 | -0.180 | False |
| K7 | c_R2_har_u25 | 925 | -0.207 | -6.6 | 0/4 | -0.156 | True |
| K7 | c_R2_v1_lo5 | 885 | -0.592 | -6.0 | 0/3 | -0.639 | True |
| K7 | c_R2_v1_u25 | 864 | -0.138 | -5.5 | 0/3 | -0.076 | True |
| K7 | c_R2_v1_tgtover075 | 6346 | -0.286 | -5.4 | 0/4 | -0.113 | True |
| M7 | c_R2_har_u25 | 773 | -0.372 | -7.5 | 0/4 | -0.321 | True |
| M7 | c_R2_har_u100 | 7128 | -0.263 | -6.1 | 0/4 | -0.283 | True |
| M7 | c_R2_har_ge100 | 1595 | +0.263 | +6.1 | 4/4 | +0.283 | True |
| M7 | c_R2_v1_u25 | 750 | -0.305 | -6.0 | 0/4 | -0.275 | True |
| O7 | c_R2_v1_tgtover100 | 132 | -0.808 | +1.9 | 0/2 | -2.225 | False |
| O7 | c_R2_har_tgtover075 | 213 | -0.976 | +1.6 | 0/2 | -1.796 | False |
| O7 | c_R2_v1_hi5 | 141 | +1.408 | +1.4 | 3/3 | +1.664 | False |
| O7 | c_R2_v1_tgtover075 | 218 | -1.010 | +1.3 | 0/3 | -1.933 | False |
| P7 | c_R2_har_u75 | 7997 | -0.172 | -5.5 | 0/4 | -0.301 | True |
| P7 | c_R2_v1_tgtover075 | 8114 | -0.285 | -5.2 | 0/4 | -0.063 | True |
| P7 | c_R2_v1_lo3 | 2358 | -0.525 | -5.0 | 0/4 | -0.667 | True |
| P7 | c_R2_har_ge100 | 3019 | +0.196 | +4.9 | 4/4 | +0.238 | True |
| U7 | c_R2_v1_tgtover075 | 1437 | -0.427 | -3.6 | 0/3 | -0.337 | False |
| U7 | c_R2_har_u50 | 554 | -0.206 | -3.4 | 0/4 | -0.212 | False |
| U7 | c_R2_uwc_lo5 | 197 | -0.613 | -3.4 | 0/2 | -0.837 | False |
| U7 | c_R2_v1_u25 | 78 | -0.261 | -3.3 | 0/0 | -0.101 | False |

Book x session cells passing the bar: 127 of 1800:

| book | sess | condition | n yes | lift | zw | L6M lift |
|---|---|---|---|---|---|---|
| K7 | 1 | c_R2_har_u75 | 1293 | -0.316 | -7.4 | -0.250 |
| K7 | 1 | c_R2_v1_tgtover100 | 1300 | +0.095 | +7.3 | +0.240 |
| M7 | 1 | c_R2_har_u75 | 1528 | -0.359 | -7.2 | -0.292 |
| M7 | 1 | c_R2_v1_u75 | 1540 | -0.357 | -7.1 | -0.388 |
| K7 | 1 | c_R2_har_tgtover125 | 1172 | +0.122 | +7.1 | +0.245 |
| M7 | 1 | c_R2_har_tgtover125 | 972 | +0.238 | +7.0 | +0.307 |
| M7 | 1 | c_R2_har_tgtover100 | 1150 | +0.163 | +6.8 | +0.273 |
| M7 | 1 | c_R2_v1_tgtover125 | 986 | +0.199 | +6.7 | +0.363 |
| P7 | 1 | c_R2_har_u75 | 1660 | -0.299 | -6.7 | -0.289 |
| K7 | 1 | c_R2_har_tgtover100 | 1335 | +0.089 | +6.7 | +0.188 |
| M7 | 1 | c_R2_v1_u50 | 973 | -0.363 | -6.7 | -0.321 |
| M7 | 1 | c_R2_har_u50 | 967 | -0.375 | -6.6 | -0.350 |
| P7 | 1 | c_R2_v1_u75 | 1667 | -0.262 | -6.6 | -0.287 |
| K7 | 1 | c_R2_har_tgtover150 | 1045 | +0.167 | +6.5 | +0.318 |
| M7 | 1 | c_R2_v1_tgtover100 | 1164 | +0.125 | +6.4 | +0.350 |

## mean-R proxy p1R (+1R before -1R; lift>0 = better)
Nonsense bar (99th pct |zw|): ALL 2.4, book 2.5, sess 2.5, book_sess 2.6; nonsense |zw|>2 rate: ALL 0.03, book 0.04, sess 0.05, book_sess 0.04

Pooled (ALL cells), top 14 by |zw|:

| condition | n yes | share | mean yes | mean no | lift | zw | yrs same sign | L6M lift | pass |
|---|---|---|---|---|---|---|---|---|---|
| c_R2_har_tgtover200 | 13274 | 0.35 | 0.512 | 0.518 | -0.006 | -1.8 | 2/4 | +0.021 | False |
| c_R2_uwa_lo3 | 5346 | 0.22 | 0.511 | 0.514 | -0.003 | -1.7 | 1/2 | +0.013 | False |
| c_R2_uwc_hi5 | 6114 | 0.25 | 0.517 | 0.512 | +0.004 | +1.5 | 2/2 | +0.012 | False |
| c_R2_har_u100 | 29898 | 0.78 | 0.518 | 0.507 | +0.011 | +1.4 | 3/4 | -0.030 | False |
| c_R2_har_ge100 | 8508 | 0.22 | 0.507 | 0.518 | -0.011 | -1.4 | 1/4 | +0.030 | False |
| c_R2_uwa_hi5 | 5293 | 0.22 | 0.510 | 0.514 | -0.004 | -1.4 | 1/2 | +0.016 | False |
| c_R2_v1_u25 | 2343 | 0.07 | 0.512 | 0.517 | -0.005 | -1.3 | 2/4 | +0.002 | False |
| c_R2_uwa_lo5 | 2749 | 0.11 | 0.521 | 0.512 | +0.009 | +1.3 | 1/2 | -0.004 | False |
| c_R2_v1_hi5 | 17085 | 0.47 | 0.513 | 0.521 | -0.009 | +1.3 | 1/4 | +0.005 | False |
| c_R2_har_u75 | 22495 | 0.59 | 0.516 | 0.515 | +0.001 | +1.2 | 3/4 | -0.009 | False |
| c_R2_uwb_lo3 | 5590 | 0.23 | 0.512 | 0.514 | -0.001 | -1.2 | 1/2 | +0.015 | False |
| c_R2_v1_tgtover125 | 15117 | 0.42 | 0.524 | 0.511 | +0.013 | +1.1 | 2/4 | +0.022 | False |
| c_R2_v1_tgtover075 | 20607 | 0.57 | 0.525 | 0.505 | +0.020 | +1.1 | 3/4 | +0.012 | False |
| c_R2_uwc_hi3 | 9957 | 0.41 | 0.516 | 0.512 | +0.004 | +1.1 | 2/2 | +0.001 | False |

Per book, top 4 per book by |zw| (same sign in L6M shown):

| book | condition | n yes | lift | zw | yrs | L6M lift | pass |
|---|---|---|---|---|---|---|---|
| A7 | c_R2_har_lo5 | 456 | +0.051 | +1.8 | 3/3 | +0.245 | False |
| A7 | c_R2_uwb_hi3 | 1264 | +0.004 | +1.5 | 1/2 | -0.030 | False |
| A7 | c_R2_uwa_lo5 | 431 | +0.011 | +1.2 | 2/2 | +0.115 | False |
| A7 | c_R2_uwb_hi5 | 702 | +0.040 | +1.1 | 2/2 | +0.010 | False |
| H7 | c_R2_uwb_lo3 | 365 | -0.008 | +2.0 | 1/2 | -0.018 | False |
| H7 | c_R2_har_tgtover150 | 785 | +0.035 | +2.0 | 4/4 | +0.026 | False |
| H7 | c_R2_uwa_lo3 | 347 | +0.001 | +1.8 | 1/2 | +0.012 | False |
| H7 | c_R2_uwa_hi3 | 434 | +0.002 | -1.7 | 0/2 | +0.056 | False |
| K7 | c_R2_har_tgtover200 | 3336 | -0.003 | -1.7 | 1/4 | +0.011 | False |
| K7 | c_R2_har_tgtover075 | 5646 | +0.002 | -1.5 | 2/4 | +0.004 | False |
| K7 | c_R2_uwa_hi3 | 2746 | -0.022 | -1.4 | 0/2 | +0.007 | False |
| K7 | c_R2_har_u75 | 5923 | +0.000 | +1.4 | 3/4 | -0.019 | False |
| M7 | c_R2_uwc_hi5 | 1036 | +0.020 | +1.9 | 2/2 | +0.022 | False |
| M7 | c_R2_har_u50 | 2436 | -0.028 | -1.8 | 1/4 | -0.024 | False |
| M7 | c_R2_uwa_lo5 | 557 | +0.010 | +1.6 | 1/2 | +0.053 | False |
| M7 | c_R2_v1_tgtover075 | 3693 | +0.023 | +1.6 | 3/4 | -0.025 | False |
| O7 | c_R2_har_u50 | 284 | -0.045 | -0.9 | 1/3 | +0.038 | False |
| O7 | c_R2_har_hi3 | 201 | -0.101 | +0.8 | 0/3 | -0.034 | False |
| O7 | c_R2_v1_u50 | 272 | -0.057 | -0.7 | 1/3 | +0.098 | False |
| O7 | c_R2_v1_tgtover100 | 130 | +0.048 | -0.6 | 1/2 | +0.452 | False |
| P7 | c_R2_har_u25 | 719 | +0.049 | +2.1 | 3/3 | +0.048 | False |
| P7 | c_R2_uwc_hi5 | 1849 | +0.011 | +2.0 | 2/2 | +0.006 | False |
| P7 | c_R2_v1_tgtover075 | 6042 | +0.023 | +2.0 | 2/4 | +0.023 | False |
| P7 | c_R2_v1_tgtover100 | 5069 | +0.017 | +1.6 | 3/4 | +0.019 | False |
| U7 | c_R2_v1_ge100 | 295 | -0.075 | -2.1 | 1/3 | -0.003 | False |
| U7 | c_R2_v1_u100 | 1284 | +0.075 | +2.1 | 2/3 | +0.003 | False |
| U7 | c_R2_har_tgtover200 | 634 | -0.043 | -2.0 | 1/3 | +0.031 | False |
| U7 | c_R2_har_u100 | 1331 | +0.054 | +2.0 | 2/3 | -0.065 | False |

Book x session cells passing the bar: 4 of 1800:

| book | sess | condition | n yes | lift | zw | L6M lift |
|---|---|---|---|---|---|---|
| K7 | 0 | c_R2_har_hi5 | 1371 | -0.040 | -3.2 | -0.045 |
| A7 | 2 | c_R2_har_u50 | 132 | +0.093 | +2.9 | +0.087 |
| K7 | 4 | c_R2_v1_u100 | 1650 | +0.062 | +2.8 | +0.087 |
| K7 | 4 | c_R2_v1_ge100 | 183 | -0.062 | -2.8 | -0.087 |

## time to target (h, sign: lift<0 = faster)
Nonsense bar (99th pct |zw|): ALL 6.7, book 5.9, sess 5.2, book_sess 3.8; nonsense |zw|>2 rate: ALL 0.17, book 0.12, sess 0.12, book_sess 0.08

Pooled (ALL cells), top 14 by |zw|:

| condition | n yes | share | mean yes | mean no | lift | zw | yrs same sign | L6M lift | pass |
|---|---|---|---|---|---|---|---|---|---|
| c_R2_v1_tgtover075 | 27277 | 0.62 | 2.727 | 2.317 | +0.410 | +6.3 | 4/4 | +0.046 | False |
| c_R2_v1_tgtover100 | 22786 | 0.52 | 2.731 | 2.400 | +0.331 | +4.9 | 4/4 | +0.003 | False |
| c_R2_v1_tgtover125 | 20005 | 0.45 | 2.715 | 2.451 | +0.265 | +3.6 | 3/4 | -0.029 | False |
| c_R2_har_u25 | 3539 | 0.07 | 2.863 | 2.723 | +0.140 | +3.4 | 4/4 | +0.157 | False |
| c_R2_har_u100 | 42233 | 0.78 | 2.755 | 2.651 | +0.104 | +3.2 | 4/4 | +0.227 | False |
| c_R2_har_ge100 | 11873 | 0.22 | 2.651 | 2.755 | -0.104 | -3.2 | 0/4 | -0.227 | False |
| c_R2_uwc_hi5 | 7140 | 0.23 | 2.177 | 2.690 | -0.513 | -2.9 | 0/2 | -0.315 | False |
| c_R2_uwb_lo3 | 8814 | 0.28 | 3.019 | 2.401 | +0.618 | +2.9 | 2/2 | +0.293 | False |
| c_R2_v1_tgtover150 | 17986 | 0.41 | 2.703 | 2.479 | +0.224 | +2.8 | 3/4 | -0.054 | False |
| c_R2_har_tgtover075 | 29349 | 0.63 | 2.620 | 2.382 | +0.238 | +2.6 | 3/4 | -0.142 | False |
| c_R2_har_u50 | 16545 | 0.31 | 2.804 | 2.700 | +0.104 | +2.6 | 3/4 | +0.165 | False |
| c_R2_v1_lo5 | 5757 | 0.11 | 3.367 | 2.672 | +0.695 | +2.4 | 4/4 | +0.671 | False |
| c_R2_uwb_lo5 | 4864 | 0.15 | 3.188 | 2.462 | +0.726 | +2.2 | 2/2 | +0.327 | False |
| c_R2_uwc_lo3 | 8442 | 0.27 | 3.038 | 2.404 | +0.633 | +2.1 | 2/2 | +0.387 | False |

Per book, top 4 per book by |zw| (same sign in L6M shown):

| book | condition | n yes | lift | zw | yrs | L6M lift | pass |
|---|---|---|---|---|---|---|---|
| A7 | c_R2_har_ge100 | 1761 | -0.306 | -3.7 | 0/4 | -0.480 | False |
| A7 | c_R2_har_u100 | 5493 | +0.306 | +3.7 | 4/4 | +0.480 | False |
| A7 | c_R2_v1_lo5 | 789 | +0.773 | +3.3 | 4/4 | +0.521 | False |
| A7 | c_R2_v1_u100 | 5101 | +0.220 | +3.1 | 4/4 | +0.494 | False |
| H7 | c_R2_har_u75 | 1793 | +0.343 | +4.8 | 4/4 | +0.319 | False |
| H7 | c_R2_har_u50 | 937 | +0.301 | +4.6 | 4/4 | +0.196 | False |
| H7 | c_R2_har_ge100 | 467 | -0.385 | -4.5 | 0/3 | -0.524 | False |
| H7 | c_R2_har_u100 | 2288 | +0.385 | +4.5 | 3/3 | +0.524 | False |
| K7 | c_R2_v1_tgtover075 | 6346 | +0.442 | +7.6 | 4/4 | +0.040 | True |
| K7 | c_R2_v1_tgtover100 | 5352 | +0.372 | +6.8 | 4/4 | +0.024 | True |
| K7 | c_R2_har_u25 | 925 | +0.353 | +5.7 | 4/4 | +0.378 | False |
| K7 | c_R2_v1_tgtover125 | 4744 | +0.289 | +5.1 | 3/4 | -0.026 | False |
| M7 | c_R2_har_tgtover150 | 3060 | -0.082 | -4.9 | 1/4 | -0.295 | False |
| M7 | c_R2_har_tgtover125 | 3407 | -0.067 | -4.8 | 1/4 | -0.257 | False |
| M7 | c_R2_har_tgtover200 | 2659 | -0.104 | -4.5 | 0/4 | -0.319 | False |
| M7 | c_R2_har_tgtover100 | 4005 | -0.014 | -4.1 | 1/4 | -0.208 | False |
| O7 | c_R2_v1_hi3 | 204 | -0.787 | -3.9 | 0/3 | -0.694 | False |
| O7 | c_R2_v1_tgtover100 | 132 | +0.783 | +2.4 | 2/2 | -0.389 | False |
| O7 | c_R2_har_hi3 | 201 | -0.649 | -2.3 | 0/3 | -0.756 | False |
| O7 | c_R2_har_tgtover075 | 213 | +0.572 | +1.5 | 2/2 | -0.251 | False |
| P7 | c_R2_v1_tgtover075 | 8114 | +0.391 | +4.4 | 4/4 | +0.058 | False |
| P7 | c_R2_har_u100 | 10583 | +0.159 | +3.5 | 4/4 | +0.249 | False |
| P7 | c_R2_har_ge100 | 3019 | -0.159 | -3.5 | 0/4 | -0.249 | False |
| P7 | c_R2_uwc_hi5 | 1914 | -0.621 | -3.3 | 0/2 | -0.512 | False |
| U7 | c_R2_har_u75 | 1292 | +0.229 | +2.9 | 4/4 | +0.391 | False |
| U7 | c_R2_v1_lo3 | 363 | +0.758 | +2.5 | 3/3 | +0.790 | False |
| U7 | c_R2_uwc_lo3 | 331 | +0.580 | +2.5 | 2/2 | +0.432 | False |
| U7 | c_R2_v1_lo5 | 234 | +0.696 | +2.5 | 2/2 | +0.778 | False |

Book x session cells passing the bar: 53 of 1850:

| book | sess | condition | n yes | lift | zw | L6M lift |
|---|---|---|---|---|---|---|
| H7 | 1 | c_R2_har_u50 | 250 | +0.535 | +5.7 | +0.320 |
| K7 | 3 | c_R2_har_u50 | 817 | -0.347 | -5.6 | -0.286 |
| K7 | 3 | c_R2_v1_u50 | 787 | -0.362 | -5.5 | -0.339 |
| M7 | 1 | c_R2_v1_u50 | 973 | +0.471 | +5.2 | +0.182 |
| M7 | 1 | c_R2_har_tgtover150 | 871 | -0.232 | -5.2 | -0.265 |
| H7 | 1 | c_R2_har_tgtover125 | 372 | -0.249 | -5.2 | -0.663 |
| M7 | 1 | c_R2_har_u75 | 1528 | +0.451 | +5.2 | +0.321 |
| M7 | 1 | c_R2_v1_tgtover125 | 986 | -0.119 | -5.2 | -0.117 |
| H7 | 1 | c_R2_v1_tgtover125 | 366 | -0.184 | -5.1 | -0.499 |
| M7 | 1 | c_R2_har_u50 | 967 | +0.508 | +5.1 | +0.229 |
| M7 | 1 | c_R2_har_tgtover125 | 972 | -0.221 | -5.1 | -0.228 |
| M7 | 1 | c_R2_v1_tgtover150 | 861 | -0.148 | -5.0 | -0.164 |
| K7 | 3 | c_R2_har_tgtover075 | 1170 | +0.442 | +5.0 | +0.085 |
| P7 | 4 | c_R2_v1_hi3 | 1363 | -0.792 | -5.0 | -1.293 |
| M7 | 1 | c_R2_har_tgtover200 | 760 | -0.238 | -5.0 | -0.270 |

## Reading (plain)
A high range forecast (HAR, HAR+CME, UW) goes with more MFE and more MAE in the bar path (31 / 164 book and book x session cells pass the nonsense bar on MFE / MAE): it forecasts range, which is what MFE and MAE are, so this is the forecast working, not an entry edge. On the outcome that decides a trade, p1R (+1R before -1R, the mean-R proxy), only 4 of 2150 cells pass the bar, which is below what 1 pct nonsense passes would give (about 21): no forecast, range-used or target-over-remaining condition improves the raw trade. Time to target: 55 cells pass (high forecast = slower, as expected). Pooled p1R lifts are within +-0.02 with |zw| < 2.0. UW conditions only exist from 2025-03; HAR+CME and UW need feeds D7 does not have live (flagged, not dropped); HAR needs only our own bars. Mean-R effect against the W-PM raw table is pending the table.
