# SIZER UNIVERSE AUDIT (S4a, 2026-11-03 17:36Z)

Question (lead, after S4b retracted confirm_n15): do the sizer constructs that use earlier signals use a universe the live box cannot see? The engine d table has 88,490 signal rows (11 books); the live box evaluates only live-session signals (**27,902**: books HM, KB, MV, PB, PE, SM in their live sessions) and the ts2 Q1-A run takes **21,397**. DN, MA, PBL, ST, WT have no live session; PB has 22,357 rows of which 5,403 are live; HM 6,198 of which 3,304; PE 8,203 of which 6,126.

## 1. Constructs and their universe (before)

| construct | owner | universe used | what the live box can compute |
|---|---|---|---|
| ranks_book.parquet / ranks_c / rk_* (expanding same-book percentile, min 100) | S4a | ALL engine rows of the book (non-live sessions and non-live books' rows excluded only by book, i.e. every row of the same book incl. non-live sessions, not-taken signals) | share of earlier evaluated signals (live sessions) of the same book below x; separately history of taken signals only if the state needs fills |
| ranks_roll250 (rolling 250) | S4a | same, last 250 earlier rows of the book | last 250 earlier live signals |
| rank-hysteresis tier state (S1_HYST, `hfam._hyst`) | S4a | tier updated at every row of the book in time order | tier updated at live signals only |
| vt_ratio: expanding same-book median of atr14_5m (S2V VT cells) | ZL-1 | all earlier rows of the book | median over earlier live signals |
| rank regime / R| cells state | ZL-1 | (rank-based: as ranks_book) | live universe |
| bk_sess_pnl_pts, bk_day_pnl_pts, bk_sess_n_closed ('session / book P&L so far') | S4b | library P&L of ALL signals of the book/session whose exit precedes the signal second (hypothetical; includes signals never evaluated or never taken) | P&L of fills actually taken so far (taken universe only) |
| EINT ranks / roll in other pages | other | not audited here | |

Not cross-signal (no universe issue): ER, ADX, chop, ATR, bar-based features, POI relative features (tot_rel, ahead_rel from tape arrays), zone distances.

## 2. Rebuild

`build_ranks_universe.py` rebuilds every rk_ (135 features of feat_signal, _b, _c) and rr_er_5m_{14,20,30} on (a) the **live** universe (history = earlier live-session signals of the book; query = live rows) and (b) the **taken** universe (history = earlier taken signals; query = live rows): `/mnt/l2/l2vast/ds3_sizer/ranks_live.parquet`, `ranks_taken.parquet`; masks `mask_live.npy`, `mask_taken2.npy` in /mnt/l2/l2vast/ds3_zones3_new/sizer_s4a/. Hysteresis state and the VT median are rebuilt with the same masks (live rows query; insert per universe).

Rank differences on live rows (old vs rebuilt):

| feature         |   rows |   mean_abs_diff_old_live |   mean_abs_diff_old_taken |   mean_abs_diff_live_taken |   corr_old_live |   share_defined_old |   share_defined_live |
|:----------------|-------:|-------------------------:|--------------------------:|---------------------------:|----------------:|--------------------:|---------------------:|
| rk_er_5m_20     |  26947 |                   0.0193 |                    0.0187 |                     0.0071 |          0.9945 |               0.988 |               0.9785 |
| rk_er_10m_20    |  26947 |                   0.0212 |                    0.0129 |                     0.0146 |          0.9935 |               0.988 |               0.9785 |
| rk_ers_15m_20   |  26947 |                   0.0191 |                    0.0184 |                     0.0179 |          0.9954 |               0.988 |               0.9785 |
| rk_adx14_1m     |  26947 |                   0.0193 |                    0.0275 |                     0.0113 |          0.9935 |               0.988 |               0.9785 |
| rk_atr_ratio_5m |  26947 |                   0.1262 |                    0.1184 |                     0.0324 |          0.7735 |               0.988 |               0.9785 |

## 3. Re-score of the top 20 cells per family vs Q1-A on ts2

Top 20 of each family by (cut L6M + cut PRE)/2 among cells that kept Q1-A's mean (S2: all, none kept it), as listed in the master. Each cell rebuilt on 'old' (control, original ranks), 'live' and 'taken' universe, run on ts2. flag_rule = cut > 0 on L6M and PRE, carrying week dropped > 0, mean >= Q1-A; harm_ok = PA9 within the flip-5 band on HOLD/MID/X'/PRE.

| family   | universe   |   cells |   mean_ok |   flag_rule |   flag_and_harm_ok |   median_cutL6M |   median_cutPRE |   median_pa9_L6M |   median_pa9_PRE |
|:---------|:-----------|--------:|----------:|------------:|-------------------:|----------------:|----------------:|-----------------:|-----------------:|
| HYST     | live       |      13 |         7 |           0 |                  0 |           0.221 |          -0.241 |            0.114 |           -0.135 |
| HYST     | old        |      13 |        13 |           0 |                  0 |           0.265 |          -0.192 |            0.146 |           -0.104 |
| HYST     | taken      |      13 |         8 |           0 |                  0 |           0.257 |          -0.241 |            0.146 |           -0.119 |
| S1       | live       |      20 |        18 |           3 |                  1 |           0.384 |          -0.052 |            0.216 |           -0.011 |
| S1       | old        |      20 |        20 |           3 |                  1 |           0.359 |          -0.046 |            0.204 |            0.003 |
| S1       | taken      |      20 |        17 |           3 |                  1 |           0.367 |          -0.055 |            0.209 |           -0.011 |
| S2       | live       |      20 |         0 |           0 |                  0 |           0.516 |           0.307 |            0.422 |            0.372 |
| S2       | old        |      20 |         0 |           0 |                  0 |           0.516 |           0.31  |            0.422 |            0.372 |
| S2       | taken      |      20 |         0 |           0 |                  0 |           0.516 |           0.301 |            0.422 |            0.372 |
| S2V      | live       |      20 |        16 |           0 |                  0 |           0.089 |           0.001 |            0.062 |           -0.008 |
| S2V      | old        |      20 |        20 |           4 |                  4 |           0.034 |           0.002 |            0.027 |           -0.008 |
| S2V      | taken      |      20 |        13 |           1 |                  1 |           0.084 |           0.01  |            0.064 |           -0.002 |

### Per cell: control vs live vs taken

| family   | cell                                      |   cutL6M_old |   cutL6M_live |   cutPRE_old |   cutPRE_live |   cutPRE_taken |   dmeanL6M_old |   dmeanL6M_live | flag_old   | flag_live   | flag_taken   |
|:---------|:------------------------------------------|-------------:|--------------:|-------------:|--------------:|---------------:|---------------:|----------------:|:-----------|:------------|:-------------|
| HYST     | fam#16                                    |        0.028 |        -0.034 |       -0.192 |        -0.181 |         -0.179 |       1054.01  |         141.294 | False      | False       | False        |
| HYST     | fam#19                                    |        0.219 |         0.297 |       -0.141 |        -0.355 |         -0.269 |        401.415 |        1339.49  | False      | False       | False        |
| HYST     | fam#26                                    |        0.327 |         0.362 |        0.006 |        -0.053 |         -0.054 |       1459.08  |        1427.39  | False      | False       | False        |
| HYST     | fam#31                                    |        0.317 |         0.281 |       -0.015 |        -0.149 |         -0.144 |       1477.23  |         355.895 | False      | False       | False        |
| HYST     | fam#37                                    |        0.299 |         0.311 |        0.012 |        -0.008 |          0.022 |       1032.91  |         938.189 | False      | False       | False        |
| HYST     | fam#38                                    |        0.307 |         0.163 |        0.032 |        -0.141 |         -0.083 |       1451.67  |        2084.17  | False      | False       | False        |
| HYST     | fam#4                                     |       -0.018 |         0.008 |       -0.238 |        -0.241 |         -0.241 |        127.113 |         227.355 | False      | False       | False        |
| HYST     | fam#41                                    |        0.279 |         0.173 |       -0.064 |        -0.128 |         -0.107 |        247.743 |       -1901.7   | False      | False       | False        |
| HYST     | fam#49                                    |        0.189 |         0.218 |       -0.314 |        -0.331 |         -0.331 |        626.132 |         765.678 | False      | False       | False        |
| HYST     | fam#51                                    |        0.284 |         0.187 |       -0.454 |        -0.398 |         -0.398 |        999.646 |        2672.15  | False      | False       | False        |
| HYST     | fam#53                                    |        0.265 |         0.221 |       -0.261 |        -0.312 |         -0.312 |       3413.7   |        1789.8   | False      | False       | False        |
| HYST     | fam#60                                    |        0.206 |         0.223 |       -0.288 |        -0.259 |         -0.302 |         82.137 |         315.68  | False      | False       | False        |
| HYST     | fam#63                                    |        0.168 |         0.248 |       -0.427 |        -0.376 |         -0.356 |        241.575 |         514.483 | False      | False       | False        |
| S1       | ('g12', 'er_10m_14', 'L3', 'A')           |        0.35  |         0.413 |       -0.046 |        -0.061 |         -0.081 |        750.67  |         952.249 | False      | False       | False        |
| S1       | ('g12', 'er_10m_14', 'L3', 'C')           |        0.35  |         0.413 |       -0.046 |        -0.061 |         -0.081 |        750.67  |         952.249 | False      | False       | False        |
| S1       | ('g12', 'er_10m_14', 'LIN', 'A')          |        0.411 |         0.411 |       -0.05  |        -0.061 |         -0.061 |        603.158 |         905.854 | False      | False       | False        |
| S1       | ('g12', 'er_10m_14', 'LIN', 'B')          |        0.242 |         0.28  |        0.03  |         0.033 |          0.025 |       1184.53  |        1002.74  | True       | True        | True         |
| S1       | ('g12', 'er_10m_14', 'SIG', 'A')          |        0.36  |         0.38  |       -0.008 |        -0.02  |         -0.02  |        337.906 |         237.704 | False      | False       | False        |
| S1       | ('g12', 'er_10m_14', 'SIG', 'B')          |        0.348 |         0.441 |        0.028 |         0.018 |          0.018 |       1547.66  |        1822.61  | True       | True        | True         |
| S1       | ('g12', 'er_1m_100', 'L3', 'A')           |        0.226 |         0.263 |       -0.004 |         0.003 |          0.003 |        733.353 |         431.182 | False      | False       | False        |
| S1       | ('g12', 'er_1m_100', 'L3', 'C')           |        0.226 |         0.263 |       -0.004 |         0.003 |          0.003 |        733.353 |         431.182 | False      | False       | False        |
| S1       | ('g13', 'ers_10m_20', 1, 'L5', 'A')       |        0.397 |         0.388 |       -0.177 |        -0.161 |         -0.144 |       1910.88  |        1925.26  | False      | False       | False        |
| S1       | ('g13', 'ers_10m_20', 1, 'L5', 'B')       |        0.357 |         0.339 |       -0.116 |        -0.098 |         -0.065 |       3923.85  |        3889.8   | False      | False       | False        |
| S1       | ('g13', 'ers_10m_20', 1, 'L5', 'C')       |        0.397 |         0.388 |       -0.177 |        -0.161 |         -0.144 |       1910.88  |        1925.26  | False      | False       | False        |
| S1       | ('g13', 'ers_10m_20', 1, 'LIN', 'A')      |        0.429 |         0.448 |       -0.094 |        -0.103 |         -0.103 |       1362.5   |        1445.01  | False      | False       | False        |
| S1       | ('g13', 'ers_10m_20', 1, 'LIN', 'B')      |        0.415 |         0.427 |       -0.073 |        -0.097 |         -0.085 |       1283.59  |        1521.23  | False      | False       | False        |
| S1       | ('g13', 'ers_10m_20', 1, 'SIG', 'B')      |        0.382 |         0.399 |       -0.071 |        -0.047 |         -0.028 |       3139.86  |        3198.17  | False      | False       | False        |
| S1       | ('g13', 'ers_15m_20', 1, 'L3', 'B')       |        0.368 |         0.238 |       -0.047 |        -0.05  |         -0.05  |       5257.14  |        5940.18  | False      | False       | False        |
| S1       | ('g13', 'ers_30m_20', 1, 'L3', 'B')       |        0.381 |         0.431 |       -0.119 |        -0.112 |         -0.112 |        325.095 |        1213.78  | False      | False       | False        |
| S1       | ('g13', 'ers_5m_20', 1, 'L5', 'B')        |        0.302 |         0.313 |       -0.012 |        -0.053 |         -0.08  |       1003.47  |        1008.45  | False      | False       | False        |
| S1       | ('g13', 'ers_5m_20', 1, 'LIN', 'B')       |        0.251 |         0.238 |        0.07  |         0.044 |          0.018 |       1318.82  |        1209.77  | False      | False       | False        |
| S1       | ('g13', 'ers_5m_20', 1, 'LIN', 'C')       |        0.364 |         0.353 |        0.006 |         0.016 |          0.002 |       1007.03  |         315.604 | False      | False       | False        |
| S1       | ('g13', 'ers_5m_20', 1, 'SIG', 'B')       |        0.234 |         0.158 |        0.027 |         0.025 |          0.022 |       1164.08  |         739.587 | True       | True        | True         |
| S2       | ('rk_bars_since_flip_5m', -1, 'D3', None) |        0.636 |         0.62  |        0.058 |         0.082 |          0.028 |       -749.413 |       -1231.93  | False      | False       | False        |
| S2       | ('rk_big2_net30_s', 1, 'D3', None)        |        0.514 |         0.514 |        0.352 |         0.352 |          0.352 |     -10140.4   |      -10140.4   | False      | False       | False        |
| S2       | ('rk_big2_net30_s', 1, 'L3', None)        |        0.467 |         0.467 |        0.305 |         0.305 |          0.305 |     -10062.5   |      -10062.5   | False      | False       | False        |
| S2       | ('rk_big2_net30_s', 1, 'LIN', None)       |        0.512 |         0.512 |        0.27  |         0.27  |          0.27  |      -9660.53  |       -9660.53  | False      | False       | False        |
| S2       | ('rk_big2_net30_s', 1, 'SIG', None)       |        0.512 |         0.512 |        0.27  |         0.27  |          0.27  |      -9660.53  |       -9660.53  | False      | False       | False        |
| S2       | ('rk_es_er_5m_20', -1, 'D3', None)        |        0.514 |         0.504 |        0.316 |         0.309 |          0.265 |         55.53  |         512.221 | False      | False       | False        |
| S2       | ('rk_fd_katz_5m_20', 1, 'D3', None)       |        0.533 |         0.577 |        0.262 |         0.246 |          0.244 |      -5817.81  |       -5726.99  | False      | False       | False        |
| S2       | ('rk_fd_katz_5m_20', 1, 'SIG', None)      |        0.531 |         0.526 |        0.197 |         0.183 |          0.183 |      -3604.3   |       -3839.68  | False      | False       | False        |
| S2       | ('rk_r2_5m_20', -1, 'D3', None)           |        0.608 |         0.595 |        0.203 |         0.297 |          0.297 |      -3696.02  |       -3414.55  | False      | False       | False        |
| S2       | ('rk_regime_with_5m', 1, 'D3', None)      |        0.516 |         0.516 |        0.44  |         0.44  |          0.44  |     -10874.7   |      -10874.7   | False      | False       | False        |
| S2       | ('rk_regime_with_5m', 1, 'L3', None)      |        0.516 |         0.516 |        0.44  |         0.44  |          0.44  |     -10874.7   |      -10874.7   | False      | False       | False        |
| S2       | ('rk_regime_with_5m', 1, 'LIN', None)     |        0.516 |         0.516 |        0.432 |         0.432 |          0.432 |     -10874.7   |      -10874.7   | False      | False       | False        |
| S2       | ('rk_regime_with_5m', 1, 'SIG', None)     |        0.516 |         0.516 |        0.44  |         0.44  |          0.44  |     -10874.7   |      -10874.7   | False      | False       | False        |
| S2       | ('rk_rst10_dir_s', 1, 'D3', None)         |        0.4   |         0.4   |        0.363 |         0.363 |          0.363 |      -9681.78  |       -9681.78  | False      | False       | False        |
| S2       | ('rk_rst10_dir_s', 1, 'L3', None)         |        0.4   |         0.4   |        0.363 |         0.363 |          0.363 |      -9681.78  |       -9681.78  | False      | False       | False        |
| S2       | ('rk_rst1_age_min', -1, 'D3', None)       |        0.53  |         0.424 |        0.252 |         0.209 |          0.237 |      -3028.75  |       -3022.59  | False      | False       | False        |
| S2       | ('rk_rst1_dir_s', 1, 'D3', None)          |        0.516 |         0.516 |        0.44  |         0.44  |          0.44  |     -10874.7   |      -10874.7   | False      | False       | False        |
| S2       | ('rk_rst1_dir_s', 1, 'L3', None)          |        0.516 |         0.516 |        0.44  |         0.44  |          0.44  |     -10874.7   |      -10874.7   | False      | False       | False        |
| S2       | ('rk_rst1_dir_s', 1, 'LIN', None)         |        0.558 |         0.558 |        0.292 |         0.292 |          0.292 |      -7951.62  |       -7951.62  | False      | False       | False        |
| S2       | ('rk_slope_atr_5m_20', -1, 'D3', None)    |        0.533 |         0.608 |        0.219 |         0.191 |          0.191 |      -5427.53  |       -4375.79  | False      | False       | False        |
| S2V      | V|VT|1.0|UP|INV|1.25                      |        0.218 |         0.226 |       -0.252 |        -0.275 |         -0.348 |       3777.79  |        3056.58  | False      | False       | False        |
| S2V      | V|VT|1.25|UP|INV|1.0                      |        0.048 |         0.102 |       -0.055 |        -0.037 |         -0.056 |       1146.47  |        1198.94  | False      | False       | False        |
| S2V      | V|atr_ratio_5m|L3|UP|DIR|1.25             |        0.084 |         0.2   |       -0.034 |        -0.035 |         -0.078 |         92.582 |         585.221 | False      | False       | False        |
| S2V      | V|atr_ratio_5m|LIN|UP|DIR|1.0             |       -0     |        -0.043 |        0.076 |         0.018 |          0.042 |         94.504 |        -240.405 | False      | False       | False        |
| S2V      | V|atr_ratio_5m|LIN|UP|DIR|1.25            |        0.153 |         0.146 |       -0.062 |        -0.143 |         -0.153 |        372.08  |          98.711 | False      | False       | False        |
| S2V      | V|atr_ratio_5m|SIG|UP|INV|1.0             |        0.083 |         0.106 |        0.08  |         0.105 |          0.01  |        359.708 |        1275.07  | False      | False       | False        |
| S2V      | V|dayrange_atrd|L3|UP|DIR|1.0             |       -0.038 |         0.061 |       -0.015 |         0.008 |          0.011 |         30.407 |         260.238 | False      | False       | True         |
| S2V      | V|dayrange_atrd|LIN|UP|DIR|1.0            |       -0     |         0.045 |        0.01  |         0.006 |          0.019 |        176.838 |         768.243 | False      | False       | False        |
| S2V      | V|dayrange_atrd|LIN|UP|INV|1.0            |       -0.001 |        -0.063 |        0.039 |         0.104 |          0.104 |        404.767 |         259.182 | False      | False       | False        |
| S2V      | V|dayrange_atrd|SIG|UP|DIR|1.0            |       -0.008 |         0.075 |        0.002 |         0.017 |          0.043 |        280.014 |         519.625 | False      | False       | False        |
| S2V      | V|pk_ratio_20d|LIN|UP|DIR|1.0             |        0.012 |        -0.015 |        0.043 |         0.045 |          0.058 |        112.187 |          98.056 | True       | False       | False        |
| S2V      | V|pk_ratio_20d|LIN|UP|DIR|1.25            |        0.186 |         0.176 |       -0.13  |        -0.146 |         -0.17  |         24.402 |          65.41  | False      | False       | False        |
| S2V      | V|pk_ratio_20d|LIN|UP|INV|1.0             |        0.17  |         0.18  |        0.012 |        -0.008 |         -0.013 |       1450.54  |        1118.28  | True       | False       | False        |
| S2V      | V|pk_ratio_20d|LIN|UP|INV|1.25            |        0.437 |         0.428 |       -0.18  |        -0.256 |         -0.245 |       7844.05  |        6869.07  | False      | False       | False        |
| S2V      | V|range_so_far_ratio|LIN|UP|DIR|1.0       |        0.006 |         0.027 |        0.002 |        -0.002 |          0.019 |        172.417 |         608.619 | True       | False       | False        |
| S2V      | V|range_so_far_ratio|LIN|UP|INV|1.0       |       -0.002 |        -0.048 |        0.046 |         0.117 |          0.117 |          2.748 |          -0.14  | False      | False       | False        |
| S2V      | V|range_so_far_ratio|SIG|UP|DIR|1.0       |        0.019 |         0.074 |        0.002 |         0.005 |          0.027 |        676.879 |         598.448 | False      | False       | False        |
| S2V      | V|rv_ratio_30m|LIN|UP|DIR|1.0             |        0.001 |        -0.005 |        0.038 |         0.036 |          0.038 |        181.118 |        -467.235 | True       | False       | False        |
| S2V      | V|rv_ratio_30m|LIN|UP|INV|1.0             |        0.161 |         0.112 |       -0.035 |        -0.032 |         -0.002 |       1743.87  |        1153.61  | False      | False       | False        |
| S2V      | V|rv_ratio_30m|SIG|UP|INV|1.0             |        0.134 |         0.17  |        0.001 |        -0.008 |         -0.019 |       1427.53  |        1787.26  | False      | False       | False        |

### Flags that change

| family   | cell                                |   cutL6M_old |   cutL6M_live |   cutPRE_old |   cutPRE_live |   cutPRE_taken |   dmeanL6M_old |   dmeanL6M_live | flag_old   | flag_live   | flag_taken   |
|:---------|:------------------------------------|-------------:|--------------:|-------------:|--------------:|---------------:|---------------:|----------------:|:-----------|:------------|:-------------|
| S2V      | V|dayrange_atrd|L3|UP|DIR|1.0       | -0.0381469   |     0.0613943 |  -0.014917   |    0.0076342  |      0.0109149 |         30.407 |        260.238  | False      | False       | True         |
| S2V      | V|pk_ratio_20d|LIN|UP|DIR|1.0       |  0.0119591   |    -0.0148173 |   0.0433144  |    0.0445474  |      0.0578458 |        112.187 |         98.0564 | True       | False       | False        |
| S2V      | V|pk_ratio_20d|LIN|UP|INV|1.0       |  0.170287    |     0.180294  |   0.0120902  |   -0.00766323 |     -0.0130946 |       1450.54  |       1118.28   | True       | False       | False        |
| S2V      | V|range_so_far_ratio|LIN|UP|DIR|1.0 |  0.00550928  |     0.0274039 |   0.00198318 |   -0.00208462 |      0.0188356 |        172.417 |        608.619  | True       | False       | False        |
| S2V      | V|rv_ratio_30m|LIN|UP|DIR|1.0       |  0.000805453 |    -0.0054999 |   0.0376975  |    0.0358181  |      0.0377173 |        181.118 |       -467.235  | True       | False       | False        |

## 4. Conclusions (S4a)
1. The universe error is real for every cross-signal construct S4a built (ranks_book / ranks_c / ranks_roll250, the hysteresis tier state) and for ZL-1's vol-target median and S4b's bk_* P&L-so-far features: all used the whole engine table (88,490 rows, 11 books) instead of what the box sees (27,902 live-session signals; 21,397 fills). The rank values move little on ER features (mean abs difference 0.02, correlation 0.994; 0.13 and correlation 0.77 on atr_ratio_5m) but the number of defined ranks falls (98.8% to 97.9% of live rows) because the 100-signal warm-up is counted on live signals only.
2. Effect on the top-20 cells vs Q1-A on ts2: S1 rank mappings: flag_rule count 3 / 3 / 3 (old / live / taken), no-harm-passing 1 / 1 / 1; mean-keeping cells 20 / 18 / 17. S1_HYST: mean-keeping 13 / 7 / 8, none meets the cut rule in any universe. S2 (S4b, gated and mapped modifiers): unchanged, none keeps the mean. S2V (ZL-1 V| cells): flag_rule 4 -> 0 on the live universe and 1 on taken; the four old flags (pk_ratio_20d LIN UP DIR and INV, range_so_far_ratio LIN UP DIR, rv_ratio_30m LIN UP DIR) all lose it on live, and one new one appears on taken (dayrange_atrd L3 UP DIR). None of those had cuts above the PA9 band (cuts 1-4%), so none was a lead.
3. No lead or flag from S1 / S1B / S1_HYST / S2 / S2V changes status from "none" in any universe. The retraction of confirm_n15 is consistent with this.
4. Not rebuilt here: bk_sess_pnl_pts / bk_day_pnl_pts / bk_sess_n_closed (S4b: need taken-fill P&L), ZL-1's R| regime cells and hybrids, S3 combinations built from the rank vectors (Z3 uses mult_*.npy and cell_mult from ranks_book: need re-run from ranks_live), Q-series (ER thresholds, no cross-signal state). Rank files and masks are in /mnt/l2/l2vast/ds3_sizer/ and /mnt/l2/l2vast/ds3_zones3_new/sizer_s4a/ for the owners.
