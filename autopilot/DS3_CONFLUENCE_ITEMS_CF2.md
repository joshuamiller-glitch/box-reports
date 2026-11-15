# DS3_CONFLUENCE_ITEMS_CF2 (W-CF2): each condition of categories F, G, H, I, J and Block 5 alone (STEP 3)
VERDICT (data ends 2026-11-13): 786 conditions measured alone on 20,138 taken JN05W2 trades; 122 have |z|>2 in the pooled cell (chance alone gives about 39); 72 of those have the same sign in every year and in L6M; no condition is a lead on this table alone (a lead needs the step 5 proofs, W-CF3); the map is below. No PASS claim.

Basis: net $ per trade at base lots, engine fee $1.18/contract (pnl in the entry table; the FEES.md $4.84 basis lowers each trade by lots x $3.66 x sides, a difference between yes and no groups only through their lot mix), taken trades only until the skipped-signal rows land. Lift = mean $ when the condition is yes minus when it is no (95% CI Welch). `share_yes` over entries where the condition could be computed. Years: 2023..2026; L6M = 2026-05..10, L3M = 2026-08..10, L1M = 2026-10 (cap 2026-10-31). Cells: ALL, per book (K7 M7 U7 P7 H7 A7 O7), per session (0 Asia, 1 London, 3 NY, 4 close), book x session. Full table (26,724 rows): /mnt/l2/l2vast/_confl/cols_cf2/step3_ALL.csv. Multiple-testing note: 22,477 (cell, condition) tests with n>=50 each side; at 5% about 1,123 will show |z|>2 by chance, so cell-level tops below are a map, not leads.

## L3 RESULT (full NQ MBO history 2023-04..2026-11, 19,798 taken entries, 191,520 universe rows; added after the history purchase)

- Drift: L3 microstructure changed a lot (share of entries with a spoof-like add-and-pull ahead fell from 26-41% in 2023-25 to 4% in 2026-H2; share with cancel-to-trade at my side < 10 fell from 94% to 17%; mean order size at the touch fell). Absolute L3 thresholds are therefore NOT comparable across years. The one-year lead (spoof-like ahead, 179 entries, -$546, z -4.25) was partly this drift: on the full history the same item is 6,373 entries, lift -$106/trade, z -3.4, by year 2023 +1, 2024 -97, 2025 -76, 2026 -246 (negative in 3 of 4 years, ~0 in 2023), and it shrinks to t = -1.6 once trend/tape/book controls are added.
- Drift-robust items (code derive_h.py, c_H2_*): each raw L3 value vs its own entries of the previous 20 trading days (above the 80th / at or below the 20th percentile). Four of them keep the sign in every year: arrival_imb60_lo (fewer order adds on my side than ahead, 20% of entries) +$144/trade, z 3.4, years +75/+200/+114/+160, L6M +249; ctr_mine300_lo (low own-side cancel-to-trade) +$129, z 2.8; spoof_ahead300_lo +$85, z 2.7; ctr_mine60_hi -$117 (negative in 4 of 4). They hold at the reference levels except exactly AT a level (behind<=3 pts: arrival_imb60_lo +94, z 1.0, n 873); strongest with a cluster behind (+167, z 3.3) and a level within 20 pts ahead (+139, z 3.1).
- Controls (week-clustered OLS on pnl, controls = NQ 5m EMA stack, NQ 15m hold of EMA21, ES 5m hold21, NQ 5m squeeze momentum, rvol5, cd5, book imbalance, book and session dummies):

| cond                   |     n |   lift_alone |   t_week_cluster |   lift_with_controls |   t_with_controls |
|:-----------------------|------:|-------------:|-----------------:|---------------------:|------------------:|
| c_H2_arrival_imb60_lo  | 19350 |          142 |             3.25 |                  118 |              2.69 |
| c_H2_spoof_ahead60_lo  | 19350 |          105 |             2.68 |                   70 |              1.62 |
| c_H2_ctr_mine300_lo    | 19350 |          142 |             2.66 |                  107 |              1.99 |
| c_H2_spoof_ahead300_lo | 19350 |           86 |             2.37 |                   48 |              1.22 |
| c_H2_ctr_mine60_hi     | 19350 |         -120 |            -2.99 |                 -157 |             -3.64 |
| c_H2_spoof_ahead60_hi  | 19350 |          -89 |            -2.12 |                  -40 |             -0.84 |
| c_H_spoof_ahead60_ge1  | 19361 |         -106 |            -2.7  |                  -70 |             -1.63 |


- Reading: 39 drift-robust L3 items were tried; about 13 reach |z|>2 pooled (chance ~2), several with the same sign in 4 of 4 years, and two (arrival_imb60_lo, ctr_mine60_hi) keep |t| 2.7-3.6 after controls with week clustering. That is a set of leads for W-CF3 (matched-count control, shuffled-search control, walk-forward), not a result; the spoof-like item does not survive controls. Did the L3 history justify its $1,095.50? Cost is small against D7 (a few days of one book) and it removed one false one-year lead and produced 2-3 year-stable candidates, so the data were worth buying as research; whether they are worth a LIVE L3 feed (about $199/month on Databento Standard) depends only on whether these items add to the free L1/L2/intermarket/options items in the step 5 proofs. Until then the answer is 'justified as a test, unproven as a trading input'.

## Per category (pooled ALL cell, both sides n>=100)

| category                              |   conditions |   abs_z_gt2 |   stable_and_gt2 |
|:--------------------------------------|-------------:|------------:|-----------------:|
| B14 breadth, rotation, relative value |           38 |           4 |                2 |
| B15 macro, sentiment, positioning     |           70 |           8 |                4 |
| B5 indicator states on other markets  |          257 |          47 |               31 |
| F tape                                |           50 |           4 |                2 |
| G order book L2                       |           49 |           1 |                0 |
| H order by order L3                   |           53 |          13 |                8 |
| H2 drift-robust L3                    |           38 |          12 |                9 |
| I intermarket                         |           72 |           9 |                4 |
| J options/positioning                 |          148 |          24 |               12 |

## Pooled ALL cell: 30 largest |z| (n_yes, n_no >= 100)

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_big_yield_day_ge8bp           |    3060 |  17078 |        15.2 |       -70 |      136 |      40.1 |     44.4 |   -206 | -290 | -122 | -4.79 |         0 |          4 |       -236 |       -187 |       -563 |
| c_B15_fed_speech_started_last_90min |     557 |  19581 |         2.8 |      -189 |      113 |      35.2 |     44   |   -302 | -430 | -174 | -4.64 |         0 |          4 |       -308 |        -66 |        nan |
| c_B14_avg_corr60_ge0.3              |    1579 |   1178 |        57.3 |       -45 |      149 |      40.5 |     47.1 |   -194 | -294 |  -93 | -3.78 |         0 |          3 |        -27 |       -158 |        nan |
| c_B5_NQ_5m_sqz_mom_with             |   15293 |   4827 |        76   |       135 |       13 |      44.3 |     41.8 |    121 |   58 |  185 |  3.76 |         3 |          4 |        170 |        280 |        183 |
| c_I_ratio_trend240_pos              |   12916 |   4620 |        73.6 |       121 |       -8 |      44.2 |     41.3 |    129 |   62 |  197 |  3.76 |         4 |          4 |         98 |        163 |         40 |
| c_B5_ALL_1m_sqz_fired_dir_ge3of4    |     161 |  19958 |         0.8 |      -299 |      109 |      30.4 |     43.8 |   -408 | -624 | -193 | -3.72 |         0 |          4 |       -314 |        nan |        nan |
| c_B5_NQ_15m_hold21_with             |   11296 |   8379 |        57.4 |       151 |       45 |      44.4 |     42.9 |    106 |   45 |  167 |  3.4  |         4 |          4 |        147 |        236 |        254 |
| c_B5_ES_5m_hold21_with              |   13841 |   6279 |        68.8 |       138 |       33 |      44.6 |     41.9 |    105 |   45 |  166 |  3.4  |         4 |          4 |         24 |         77 |        -18 |
| c_H2_arrival_imb60_lo               |    3906 |  16058 |        19.6 |       217 |       76 |      46   |     43.2 |    141 |   59 |  223 |  3.37 |         4 |          4 |        249 |        184 |        -73 |
| c_J_nowall_ahead25_SPX_vol          |   12163 |   1036 |        92.2 |       140 |      -96 |      43.9 |     40   |    236 |   98 |  373 |  3.36 |         3 |          3 |        254 |          1 |         75 |
| c_B5_NQ_5m_supertrend_with          |   16435 |   3685 |        81.7 |       122 |       33 |      43.9 |     43.2 |     89 |   36 |  141 |  3.31 |         4 |          4 |        144 |        172 |         93 |
| c_H_spoof_ahead60_ge1               |    6376 |  13601 |        31.9 |        34 |      136 |      42.4 |     44.3 |   -102 | -164 |  -41 | -3.27 |         1 |          4 |       -546 |       -741 |       -560 |
| c_B15_pc_etp_pct_ge80               |    3774 |  15520 |        19.6 |         5 |      135 |      42   |     44.1 |   -129 | -207 |  -52 | -3.26 |         1 |          4 |       -220 |       -127 |        -87 |
| c_H2_spoof_ahead60_lo               |   13592 |   6372 |        68.1 |       136 |       35 |      44.3 |     42.5 |    101 |   40 |  162 |  3.23 |         3 |          4 |        546 |        741 |        560 |
| c_B5_ES_5m_sqz_mom_with             |   14786 |   5334 |        73.5 |       133 |       31 |      44.3 |     42.2 |    102 |   40 |  164 |  3.23 |         3 |          4 |         87 |        224 |         27 |
| c_B5_NQ_1m_adx_di_with              |   13906 |   6213 |        69.1 |       140 |       31 |      44.5 |     41.9 |    109 |   42 |  175 |  3.21 |         4 |          4 |         20 |         93 |        210 |
| c_F_ice_with5_ge1                   |    7993 |  12081 |        39.8 |        49 |      144 |      43.4 |     44   |    -95 | -154 |  -37 | -3.2  |         0 |          4 |       -137 |       -113 |       -122 |
| c_B5_NQ_5m_hold21_with              |   14595 |   5525 |        72.5 |       133 |       33 |      44.5 |     41.7 |    100 |   39 |  162 |  3.19 |         4 |          4 |        150 |        268 |        246 |
| c_B5_NQ_5m_adx_di_with              |   12359 |   7761 |        61.4 |       143 |       47 |      44.4 |     42.8 |     96 |   36 |  156 |  3.14 |         4 |          4 |         81 |        202 |         73 |
| c_J_beyond_flip_SPX_vol             |    7852 |   5347 |        59.5 |       170 |       50 |      44.9 |     41.6 |    120 |   44 |  196 |  3.1  |         2 |          3 |        195 |        307 |        505 |
| c_B5_RTY_15m_rsi_with               |   13081 |   6594 |        66.5 |       139 |       40 |      44.3 |     42.6 |     99 |   36 |  162 |  3.06 |         4 |          4 |        100 |        197 |        362 |
| c_B5_ES_15m_rsi_with                |   14276 |   5399 |        72.6 |       133 |       34 |      44.3 |     42.2 |    100 |   35 |  164 |  3.04 |         4 |          4 |         97 |        104 |        162 |
| c_B5_NQ_5m_ema_stack_with           |   13945 |   6175 |        69.3 |       135 |       40 |      44.3 |     42.4 |     95 |   34 |  156 |  3.04 |         4 |          4 |        158 |        286 |        438 |
| c_B5_NQ_5m_sqz_on                   |    3993 |  16127 |        19.8 |        28 |      125 |      41.8 |     44.2 |    -97 | -160 |  -34 | -3.04 |         0 |          4 |       -100 |       -119 |        -47 |
| c_J_0dte_flip_far50_Nh_vol          |    3660 |   1033 |        78   |       133 |      -80 |      44.1 |     39.4 |    212 |   75 |  350 |  3.03 |         3 |          3 |         74 |         44 |        143 |
| c_B5_RTY_15m_supertrend_with        |   11284 |   8391 |        57.4 |       146 |       51 |      44.4 |     42.8 |     95 |   33 |  158 |  2.99 |         4 |          4 |         78 |        178 |        365 |
| c_H2_ctr_mine300_lo                 |    3381 |  16583 |        16.9 |       218 |       80 |      47.5 |     42.9 |    138 |   46 |  229 |  2.96 |         4 |          4 |         99 |        284 |        563 |
| c_B5_NQ_5m_rsi_with                 |   17910 |   2210 |        89   |       121 |      -17 |      44   |     41.7 |    138 |   46 |  230 |  2.94 |         4 |          4 |         50 |        287 |        215 |
| c_B15_pc_idx_pct_le20               |    4581 |  14713 |        23.7 |        26 |      135 |      41.3 |     44.5 |   -109 | -182 |  -36 | -2.94 |         1 |          4 |       -171 |       -107 |        -29 |
| c_B5_RTY_1m_macd_with               |   13134 |   6978 |        65.3 |        71 |      173 |      43.4 |     44.4 |   -102 | -170 |  -33 | -2.9  |         0 |          4 |        -90 |        -66 |        201 |

## Pooled ALL cell: stable conditions (same sign in every evaluated year and in L6M), 25 largest |z|

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_big_yield_day_ge8bp           |    3060 |  17078 |        15.2 |       -70 |      136 |      40.1 |     44.4 |   -206 | -290 | -122 | -4.79 |         0 |          4 |       -236 |       -187 |       -563 |
| c_B15_fed_speech_started_last_90min |     557 |  19581 |         2.8 |      -189 |      113 |      35.2 |     44   |   -302 | -430 | -174 | -4.64 |         0 |          4 |       -308 |        -66 |        nan |
| c_B14_avg_corr60_ge0.3              |    1579 |   1178 |        57.3 |       -45 |      149 |      40.5 |     47.1 |   -194 | -294 |  -93 | -3.78 |         0 |          3 |        -27 |       -158 |        nan |
| c_I_ratio_trend240_pos              |   12916 |   4620 |        73.6 |       121 |       -8 |      44.2 |     41.3 |    129 |   62 |  197 |  3.76 |         4 |          4 |         98 |        163 |         40 |
| c_B5_ALL_1m_sqz_fired_dir_ge3of4    |     161 |  19958 |         0.8 |      -299 |      109 |      30.4 |     43.8 |   -408 | -624 | -193 | -3.72 |         0 |          4 |       -314 |        nan |        nan |
| c_B5_NQ_15m_hold21_with             |   11296 |   8379 |        57.4 |       151 |       45 |      44.4 |     42.9 |    106 |   45 |  167 |  3.4  |         4 |          4 |        147 |        236 |        254 |
| c_B5_ES_5m_hold21_with              |   13841 |   6279 |        68.8 |       138 |       33 |      44.6 |     41.9 |    105 |   45 |  166 |  3.4  |         4 |          4 |         24 |         77 |        -18 |
| c_H2_arrival_imb60_lo               |    3906 |  16058 |        19.6 |       217 |       76 |      46   |     43.2 |    141 |   59 |  223 |  3.37 |         4 |          4 |        249 |        184 |        -73 |
| c_J_nowall_ahead25_SPX_vol          |   12163 |   1036 |        92.2 |       140 |      -96 |      43.9 |     40   |    236 |   98 |  373 |  3.36 |         3 |          3 |        254 |          1 |         75 |
| c_B5_NQ_5m_supertrend_with          |   16435 |   3685 |        81.7 |       122 |       33 |      43.9 |     43.2 |     89 |   36 |  141 |  3.31 |         4 |          4 |        144 |        172 |         93 |
| c_B5_NQ_1m_adx_di_with              |   13906 |   6213 |        69.1 |       140 |       31 |      44.5 |     41.9 |    109 |   42 |  175 |  3.21 |         4 |          4 |         20 |         93 |        210 |
| c_F_ice_with5_ge1                   |    7993 |  12081 |        39.8 |        49 |      144 |      43.4 |     44   |    -95 | -154 |  -37 | -3.2  |         0 |          4 |       -137 |       -113 |       -122 |
| c_B5_NQ_5m_hold21_with              |   14595 |   5525 |        72.5 |       133 |       33 |      44.5 |     41.7 |    100 |   39 |  162 |  3.19 |         4 |          4 |        150 |        268 |        246 |
| c_B5_NQ_5m_adx_di_with              |   12359 |   7761 |        61.4 |       143 |       47 |      44.4 |     42.8 |     96 |   36 |  156 |  3.14 |         4 |          4 |         81 |        202 |         73 |
| c_B5_RTY_15m_rsi_with               |   13081 |   6594 |        66.5 |       139 |       40 |      44.3 |     42.6 |     99 |   36 |  162 |  3.06 |         4 |          4 |        100 |        197 |        362 |
| c_B5_ES_15m_rsi_with                |   14276 |   5399 |        72.6 |       133 |       34 |      44.3 |     42.2 |    100 |   35 |  164 |  3.04 |         4 |          4 |         97 |        104 |        162 |
| c_B5_NQ_5m_ema_stack_with           |   13945 |   6175 |        69.3 |       135 |       40 |      44.3 |     42.4 |     95 |   34 |  156 |  3.04 |         4 |          4 |        158 |        286 |        438 |
| c_B5_NQ_5m_sqz_on                   |    3993 |  16127 |        19.8 |        28 |      125 |      41.8 |     44.2 |    -97 | -160 |  -34 | -3.04 |         0 |          4 |       -100 |       -119 |        -47 |
| c_J_0dte_flip_far50_Nh_vol          |    3660 |   1033 |        78   |       133 |      -80 |      44.1 |     39.4 |    212 |   75 |  350 |  3.03 |         3 |          3 |         74 |         44 |        143 |
| c_B5_RTY_15m_supertrend_with        |   11284 |   8391 |        57.4 |       146 |       51 |      44.4 |     42.8 |     95 |   33 |  158 |  2.99 |         4 |          4 |         78 |        178 |        365 |
| c_H2_ctr_mine300_lo                 |    3381 |  16583 |        16.9 |       218 |       80 |      47.5 |     42.9 |    138 |   46 |  229 |  2.96 |         4 |          4 |         99 |        284 |        563 |
| c_B5_NQ_5m_rsi_with                 |   17910 |   2210 |        89   |       121 |      -17 |      44   |     41.7 |    138 |   46 |  230 |  2.94 |         4 |          4 |         50 |        287 |        215 |
| c_B5_RTY_1m_macd_with               |   13134 |   6978 |        65.3 |        71 |      173 |      43.4 |     44.4 |   -102 | -170 |  -33 | -2.9  |         0 |          4 |        -90 |        -66 |        201 |
| c_B5_ES_5m_cci_with                 |   16649 |   3471 |        82.8 |       126 |       10 |      44.2 |     41.7 |    116 |   37 |  195 |  2.88 |         4 |          4 |         30 |         89 |        -20 |
| c_F_big10_net15_pos                 |   10944 |   9130 |        54.5 |        64 |      156 |      43.2 |     44.4 |    -92 | -154 |  -29 | -2.87 |         0 |          4 |       -117 |       -137 |       -215 |

## Recent windows: |lift| in L3M with same sign as the full sample and as L6M (pooled, n_yes and n_no in L3M >= 40)

| cond                                     |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_J_0dte_pw0_not_ahead25_Nh_vol          |    4433 |    319 |        93.3 |        66 |      353 |      42.6 |     48.9 |   -286 | -526 |  -47 | -2.34 |         1 |          3 |       -457 |      -1057 |       -538 |
| c_B15_earn_big5_report_today_after_close |    1003 |  19135 |         5   |        45 |      108 |      42.6 |     43.8 |    -63 | -207 |   80 | -0.86 |         2 |          4 |       -410 |       -636 |       -590 |
| c_H_no_aged_big_ahead                    |   18776 |   1201 |        94   |        94 |      255 |      43.3 |     49.5 |   -161 | -288 |  -34 | -2.49 |         1 |          4 |       -484 |       -632 |      -1085 |
| c_J_0dte_pw0_not_ahead50_Nh_vol          |    4145 |    607 |        87.2 |        68 |      203 |      42.6 |     46.3 |   -135 | -314 |   44 | -1.48 |         1 |          3 |       -330 |       -626 |       -779 |
| c_B15_earn_any_report_today_after_close  |    1763 |  18375 |         8.8 |        30 |      112 |      42.5 |     43.8 |    -83 | -192 |   27 | -1.47 |         2 |          4 |       -530 |       -588 |       -557 |
| c_J_wall_behind50_Nd_oi                  |     928 |   8773 |         9.6 |       132 |       82 |      44.8 |     42.6 |     50 |  -97 |  197 |  0.67 |         2 |          3 |         30 |        570 |        620 |
| c_J_0dte_flip_far25_Nh_oi                |    4261 |    381 |        91.8 |        99 |       29 |      43.4 |     39.9 |     70 | -161 |  300 |  0.59 |         3 |          3 |        565 |        566 |        nan |
| c_J_0dte_pw0_not_ahead50_Nd_oi           |    4436 |    324 |        93.2 |        78 |       73 |      42.6 |     45.1 |      5 | -228 |  237 |  0.04 |         2 |          3 |        321 |        492 |        857 |
| c_H2_bmax_ahead_hi                       |    1932 |  18032 |         9.7 |       184 |       95 |      48.2 |     43.2 |     90 |   -7 |  186 |  1.82 |         4 |          4 |        193 |        485 |       1092 |
| c_H_no_big10_ahead                       |   17885 |   2092 |        89.5 |        93 |      194 |      43.1 |     48.6 |   -101 | -194 |   -8 | -2.12 |         0 |          4 |       -193 |       -485 |      -1092 |
| c_H2_bmax_ahead_lo                       |   17876 |   2088 |        89.5 |        93 |      194 |      43.2 |     48.6 |   -102 | -195 |   -8 | -2.13 |         0 |          4 |       -193 |       -485 |      -1092 |
| c_J_wall_behind25_NDX_oi                 |     764 |  12419 |         5.8 |       -32 |      133 |      41.9 |     43.7 |   -165 | -325 |   -5 | -2.02 |         0 |          3 |       -438 |       -446 |       -276 |
| c_J_gex_pos_NDX_oi                       |    2834 |    557 |        83.6 |        56 |       28 |      43.2 |     42   |     27 |  -93 |  148 |  0.44 |         2 |          3 |        307 |        430 |        687 |
| c_B5_ES_15m_sqz_fired_dir_with           |    1523 |  18152 |         7.7 |        42 |      111 |      44   |     43.7 |    -70 | -192 |   53 | -1.11 |         1 |          4 |       -407 |       -416 |       -530 |
| c_B14_NQ_rich_vs_QQQ_with_ge0.5          |    2543 |    863 |        74.7 |        52 |       47 |      43   |     42.8 |      5 |  -94 |  105 |  0.1  |         2 |          3 |        328 |        414 |        130 |
| c_J_tide_npp_s_neg                       |    2322 |   1144 |        67   |        72 |       13 |      43.5 |     42   |     59 |  -32 |  150 |  1.27 |         3 |          3 |        244 |        408 |        273 |
| c_J_0dte_pw0_not_ahead25_Nd_vol          |    4712 |    263 |        94.7 |        68 |      155 |      42.6 |     44.1 |    -87 | -363 |  188 | -0.62 |         2 |          3 |       -311 |       -407 |       -869 |
| c_J_0dte_cw0_not_ahead50_Nd_oi           |    4444 |    316 |        93.4 |        83 |        2 |      43   |     39.9 |     81 | -168 |  330 |  0.64 |         2 |          3 |        337 |        372 |        882 |
| c_B15_pc_eq_pct_le20                     |    3916 |  15378 |        20.3 |        47 |      125 |      42.3 |     44.1 |    -79 | -157 |   -1 | -1.97 |         1 |          4 |        -53 |       -371 |        nan |
| c_J_tide_net_s15_pos                     |    2579 |    629 |        80.4 |        37 |       12 |      43   |     43.7 |     25 | -102 |  152 |  0.38 |         2 |          3 |         62 |        369 |       -728 |

## Per session (cells sess:0..4), 8 largest |z| each with n_yes,n_no >= 100


### sess:0.0 (n=7,525)

| cond                         |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_big_yield_day_ge8bp    |    1177 |   6348 |        15.6 |      -114 |      292 |      40.8 |     47.6 |   -406 | -588 | -225 | -4.39 |         0 |          4 |       -431 |       -377 |       -843 |
| c_B5_NQ_5m_supertrend_with   |    6262 |   1245 |        83.4 |       268 |       44 |      47.2 |     43.3 |    223 |  113 |  333 |  3.98 |         4 |          4 |        246 |        292 |         97 |
| c_B5_NQ_5m_sqz_mom_with      |    5636 |   1871 |        75.1 |       299 |       25 |      47.8 |     42.8 |    273 |  132 |  414 |  3.8  |         4 |          4 |        191 |        325 |        218 |
| c_B5_NQ_5m_adx_di_with       |    4455 |   3052 |        59.3 |       330 |       85 |      48.3 |     44   |    246 |  114 |  377 |  3.67 |         4 |          4 |         72 |        235 |         54 |
| c_B5_RTY_15m_supertrend_with |    3960 |   3102 |        56.1 |       352 |       95 |      48.4 |     44.5 |    258 |  117 |  399 |  3.58 |         4 |          4 |        285 |        447 |        688 |
| c_B5_NQ_15m_hold21_with      |    4342 |   2720 |        61.5 |       331 |       92 |      48.1 |     44.4 |    239 |  100 |  379 |  3.37 |         3 |          4 |        328 |        347 |        312 |
| c_B15_pc_etp_pct_le20        |    1458 |   5834 |        20   |       476 |      174 |      52.1 |     45.2 |    302 |  125 |  479 |  3.34 |         4 |          4 |        265 |        232 |        249 |
| c_B5_RTY_15m_rsi_with        |    4903 |   2159 |        69.4 |       315 |       67 |      48   |     43.7 |    248 |  100 |  397 |  3.28 |         4 |          4 |        348 |        446 |        656 |

### sess:1.0 (n=6,551)

| cond                       |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:---------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_pc_tot_pct_le20      |    1441 |   4895 |        22.7 |      -164 |       90 |      36.2 |     42.9 |   -254 | -358 | -149 | -4.76 |         0 |          4 |       -360 |       -403 |       -942 |
| c_B5_ALL_15m_adx_di_ge3of4 |    1931 |   4620 |        29.5 |       -86 |       75 |      37.8 |     42.9 |   -161 | -258 |  -64 | -3.26 |         0 |          4 |       -188 |        -36 |        295 |
| c_I_ZN_with60              |    2474 |   2844 |        46.5 |        96 |      -48 |      43.3 |     39.5 |    144 |   46 |  242 |  2.89 |         4 |          4 |        189 |        456 |        304 |
| c_B5_YM_15m_adx_di_with    |    2695 |   3856 |        41.1 |       -44 |       77 |      39.2 |     42.9 |   -122 | -211 |  -32 | -2.66 |         0 |          4 |        -59 |        -18 |        500 |
| c_G_imb1_ge0.35            |     479 |   6060 |         7.3 |      -189 |       46 |      36.7 |     41.8 |   -234 | -410 |  -59 | -2.62 |         0 |          4 |       -594 |       -412 |         75 |
| c_J_em_frac_pos_Nd         |    2401 |   1352 |        64   |       -10 |      148 |      40.2 |     43.4 |   -158 | -276 |  -39 | -2.6  |         1 |          3 |       -109 |       -173 |        138 |
| c_H2_ctr_mine300_hi        |    1719 |   4767 |        26.5 |       -64 |       61 |      37.8 |     42.7 |   -125 | -220 |  -29 | -2.57 |         0 |          4 |       -106 |         41 |       -566 |
| c_B15_cot_am_net_rising_1w |    3438 |   3113 |        52.5 |       -27 |       88 |      39.6 |     43.4 |   -115 | -203 |  -27 | -2.56 |         1 |          4 |        -52 |       -223 |        nan |

### sess:3.0 (n=4,926)

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B5_RTY_15m_macd_rising_with |    2848 |   2078 |        57.8 |       103 |      -70 |      44.8 |     38.4 |    173 |   96 |  250 |  4.4  |         4 |          4 |        140 |        172 |        476 |
| c_G_no_wall_ahead4_lt15       |    4529 |    397 |        91.9 |         5 |      309 |      40.9 |     55.7 |   -304 | -444 | -164 | -4.25 |         0 |          4 |        nan |        nan |        nan |
| c_B5_ES_1m_hold21_with        |    3549 |   1377 |        72   |        84 |     -111 |      43.4 |     38.8 |    196 |  104 |  287 |  4.2  |         3 |          4 |        216 |        342 |        635 |
| c_H2_bmax_ahead_lo            |    4177 |    733 |        85.1 |        -3 |      221 |      40.6 |     50.5 |   -224 | -332 | -116 | -4.06 |         0 |          4 |        -37 |       -248 |        nan |
| c_H_no_big10_ahead            |    4181 |    735 |        85   |        -4 |      217 |      40.6 |     50.3 |   -221 | -329 | -113 | -4.01 |         0 |          4 |        -37 |       -248 |        nan |
| c_H2_bmax_ahead_hi            |     669 |   4241 |        13.6 |       214 |        1 |      50.1 |     40.9 |    213 |  101 |  325 |  3.73 |         4 |          4 |         37 |        248 |        nan |
| c_G_no_wall_ahead10_lt15      |    3714 |   1212 |        75.4 |       -10 |      151 |      40.2 |     48   |   -161 | -249 |  -73 | -3.58 |         1 |          4 |        104 |         14 |        nan |
| c_G_no_wall_ahead40_lt15      |    3714 |   1212 |        75.4 |       -10 |      151 |      40.2 |     48   |   -161 | -249 |  -73 | -3.58 |         1 |          4 |        104 |         14 |        nan |

### sess:4.0 (n=1,136)

| cond                      |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:--------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_J_tide_net_s30_pos      |     550 |    110 |        83.3 |        -5 |      426 |      43.3 |     60.9 |   -431 | -676 | -185 | -3.44 |         0 |          3 |       -757 |        nan |        nan |
| c_J_flip_far100_SPX_oi    |     509 |    128 |        79.9 |       142 |     -236 |      49.5 |     33.6 |    377 |  158 |  596 |  3.37 |         3 |          3 |        269 |        nan |        nan |
| c_G_imb5_ge0.2            |     103 |   1033 |         9.1 |       436 |       25 |      61.2 |     44.2 |    411 |  162 |  661 |  3.23 |         4 |          4 |        702 |        nan |        nan |
| c_B5_corr_mean3_60_ge0.8  |     622 |    514 |        54.8 |       -43 |      189 |      41.6 |     50.8 |   -231 | -374 |  -88 | -3.17 |         0 |          4 |        -90 |       -711 |        nan |
| c_B5_corr_NQ_YM_60_ge0.8  |     506 |    630 |        44.5 |       -65 |      164 |      41.3 |     49.4 |   -228 | -369 |  -87 | -3.17 |         0 |          4 |       -226 |       -786 |        nan |
| c_H2_aggr20_against300_hi |     489 |    647 |        43   |       194 |      -38 |      50.5 |     42.2 |    231 |   88 |  375 |  3.16 |         3 |          4 |        -46 |       -201 |        nan |
| c_B5_NQ_5m_sqz_on         |     310 |    826 |        27.3 |      -102 |      124 |      39   |     48.3 |   -226 | -367 |  -85 | -3.15 |         0 |          4 |       -239 |       -333 |        nan |
| c_B14_avg_corr60_ge0.5    |     269 |    391 |        40.8 |      -110 |      189 |      39.8 |     50.6 |   -299 | -486 | -113 | -3.14 |         0 |          3 |        144 |        nan |        nan |

## Per book (cells book:*), 6 largest |z| each with n_yes,n_no >= 100


### book:A7 (n=1,197)

| cond                  |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_ctr_mine_lt10_300 |     599 |    579 |        50.8 |       222 |        2 |      57.6 |     46.3 |    219 |   90 |  348 |  3.33 |         3 |          3 |        111 |        432 |        554 |
| c_H2_ctr_mine300_hi   |     190 |    987 |        16.1 |      -121 |      158 |      40.5 |     54.2 |   -279 | -450 | -108 | -3.2  |         0 |          4 |       -123 |        -46 |       -227 |
| c_H2_ctr_mine60_hi    |     234 |    943 |        19.9 |       -94 |      164 |      42.3 |     54.4 |   -258 | -418 |  -98 | -3.15 |         0 |          4 |       -102 |       -231 |       -457 |
| c_J_em_used_lt0.5_Nh  |     504 |    148 |        77.3 |        17 |      339 |      47.6 |     61.5 |   -322 | -525 | -119 | -3.11 |         0 |          2 |       -358 |       -489 |       -820 |
| c_B15_pc_etp_pct_le20 |     238 |    929 |        20.4 |       310 |       68 |      60.9 |     49.7 |    242 |   83 |  400 |  2.99 |         4 |          4 |        140 |        -65 |       -313 |
| c_J_em_room_ge150_Nh  |     526 |    126 |        80.7 |        31 |      337 |      48.1 |     61.9 |   -306 | -523 |  -90 | -2.77 |         0 |          3 |       -419 |       -629 |       -848 |

### book:H7 (n=1,058)

| cond                              |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H2_touch_mine_sz_hi             |     155 |    901 |        14.7 |      -247 |      233 |      41.9 |     48.9 |   -480 | -773 | -187 | -3.21 |         0 |          4 |       -144 |       -120 |        nan |
| c_F_big10_noagainst15             |     358 |    697 |        33.9 |       454 |        5 |      52.2 |     45.6 |    449 |  165 |  733 |  3.09 |         3 |          4 |        154 |         12 |        nan |
| c_H_mine_touch_ge5                |     107 |    950 |        10.1 |      -277 |      209 |      43.9 |     48.3 |   -486 | -841 | -132 | -2.69 |         0 |          3 |        nan |        nan |        nan |
| c_B14_NQ_rich_vs_ES_with_ge1.5    |     221 |    739 |        23   |       422 |       40 |      51.6 |     46.7 |    382 |   71 |  693 |  2.41 |         4 |          4 |          1 |       -594 |        nan |
| c_B15_yield10_fell_prior_day_with |     527 |    531 |        49.8 |       309 |        9 |      50.7 |     45   |    300 |   42 |  559 |  2.27 |         3 |          4 |       -311 |       -106 |       -335 |
| c_B14_NQ_rich_vs_ES_with_ge0.5    |     435 |    525 |        45.3 |       295 |      -10 |      50.1 |     45.9 |    305 |   38 |  572 |  2.24 |         3 |          4 |        320 |       -363 |        nan |

### book:K7 (n=7,197)

| cond                    |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B5_NQ_5m_sqz_on       |    1764 |   5426 |        24.5 |       -17 |       79 |      41.2 |     44.6 |    -96 | -155 |  -37 | -3.2  |         0 |          4 |       -129 |       -130 |       -344 |
| c_B5_NQ_5m_sqz_mom_with |    4595 |   2595 |        63.9 |        89 |       -3 |      45   |     41.6 |     92 |   35 |  148 |  3.2  |         3 |          4 |        172 |        211 |        266 |
| c_F_rvol5_ge1.6         |    2513 |   4659 |        35   |       119 |       21 |      45.6 |     42.8 |     98 |   37 |  159 |  3.16 |         4 |          4 |        -12 |         54 |         57 |
| c_I_NQ_leads_RTY5       |    5162 |   2001 |        72.1 |        82 |      -16 |      44.6 |     41.4 |     97 |   35 |  160 |  3.04 |         4 |          4 |         68 |       -130 |         44 |
| c_H_touch_ratio_ge2.0   |    1750 |   5395 |        24.5 |       131 |       29 |      46.5 |     42.9 |    101 |   36 |  167 |  3.02 |         3 |          4 |         91 |          4 |        -52 |
| c_F_rvol15_ge1.3        |    2786 |   4386 |        38.8 |       111 |       20 |      45.1 |     42.9 |     91 |   32 |  150 |  3.01 |         4 |          4 |        -18 |        -11 |        121 |

### book:M7 (n=4,038)

| cond                       |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:---------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_G_no_wall_ahead4_lt15    |    3841 |    188 |        95.3 |         0 |      307 |      41   |     56.9 |   -307 | -478 | -135 | -3.51 |         0 |          4 |        nan |        nan |        nan |
| c_G_imb5_ge0.1             |    1065 |   2964 |        26.4 |       -96 |       54 |      37.5 |     43.3 |   -150 | -235 |  -64 | -3.44 |         0 |          4 |        -52 |         85 |        -25 |
| c_I_ZN_with60              |    1524 |   1777 |        46.2 |        80 |      -53 |      44.6 |     38.9 |    133 |   49 |  218 |  3.11 |         4 |          4 |        151 |        383 |        273 |
| c_B5_ES_1m_supertrend_with |    3381 |    653 |        83.8 |       -12 |      144 |      40.9 |     45.8 |   -156 | -266 |  -45 | -2.76 |         0 |          4 |       -123 |       -222 |         -3 |
| c_G_imb1_ge0.35            |     382 |   3647 |         9.5 |      -140 |       31 |      37.4 |     42.2 |   -171 | -296 |  -46 | -2.67 |         0 |          4 |       -345 |       -145 |       -226 |
| c_B15_auction_day_5y       |     165 |   3873 |         4.1 |       271 |        2 |      50.3 |     41.3 |    269 |   66 |  472 |  2.6  |         4 |          4 |        252 |        -24 |        536 |

### book:O7 (n=455)

| cond                      |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:--------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_arrival_imb30_pos     |     164 |    288 |        36.3 |       -12 |      283 |      29.9 |     41.7 |   -296 | -508 |  -83 | -2.72 |         1 |          4 |       -286 |        nan |        nan |
| c_B5_YM_1m_ema_stack_with |     216 |    239 |        47.5 |        29 |      320 |      30.6 |     43.9 |   -291 | -501 |  -81 | -2.72 |         0 |          4 |       -498 |        nan |        nan |
| c_I_NKD_with5             |     246 |    209 |        54.1 |        49 |      338 |      32.9 |     43.1 |   -289 | -502 |  -76 | -2.66 |         0 |          4 |       -220 |        nan |        nan |
| c_B5_YM_5m_hold21_with    |     135 |    320 |        29.7 |       -30 |      271 |      27.4 |     41.9 |   -301 | -525 |  -77 | -2.63 |         0 |          4 |       -262 |        nan |        nan |
| c_B5_YM_1m_sqz_mom_with   |     231 |    224 |        50.8 |        44 |      323 |      32   |     43.3 |   -280 | -490 |  -69 | -2.6  |         0 |          4 |       -656 |      -1055 |        nan |
| c_I_NVDA_with60           |     181 |    269 |        40.2 |       354 |       83 |      43.6 |     34.2 |    271 |   52 |  490 |  2.42 |         3 |          3 |       -198 |        nan |        nan |

### book:P7 (n=4,845)

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |    lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|------:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_fed_speech_started_last_90min |     109 |   4736 |         2.2 |      -521 |      207 |      26.6 |     41.1 |   -728 | -1183 | -273 | -3.14 |         0 |          4 |       -801 |        nan |        nan |
| c_B15_big_yield_day_ge8bp           |     749 |   4096 |        15.5 |      -154 |      253 |      37.2 |     41.4 |   -407 |  -676 | -138 | -2.97 |         0 |          4 |       -325 |        -62 |      -1233 |
| c_B5_NQ_1m_adx_di_with              |    2704 |   2134 |        55.9 |       318 |       35 |      40.9 |     40.8 |    283 |    84 |  481 |  2.79 |         4 |          4 |        119 |        289 |        367 |
| c_B5_NQ_15m_hold21_with             |    3188 |   1618 |        66.3 |       288 |        8 |      41.2 |     40.1 |    279 |    79 |  479 |  2.73 |         4 |          4 |        450 |        663 |        911 |
| c_I_NVDA_with15                     |    1087 |   2129 |        33.8 |       -95 |      227 |      36   |     43   |   -322 |  -554 |  -90 | -2.72 |         0 |          3 |       -508 |       -384 |       -446 |
| c_F_ice_with5_ge1                   |    1507 |   3319 |        31.2 |        14 |      277 |      39.5 |     41.5 |   -263 |  -455 |  -71 | -2.68 |         1 |          4 |       -610 |       -486 |       -325 |

### book:U7 (n=1,348)

| cond                        |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_I_NQ_leads_RTY15          |     915 |    370 |        71.2 |       399 |     -121 |      53.6 |     46.2 |    520 |  129 |  910 |  2.61 |         3 |          4 |        970 |       1883 |        nan |
| c_B5_ES_5m_sqz_mom_with     |    1232 |    115 |        91.5 |       312 |     -283 |      52.6 |     40   |    595 |  128 | 1063 |  2.5  |         4 |          4 |       1189 |       2154 |        nan |
| c_H_arrival_imb30_pos       |     771 |    570 |        57.5 |        65 |      508 |      49.4 |     54   |   -442 | -793 |  -92 | -2.47 |         1 |          4 |       -333 |       -542 |       -448 |
| c_B15_pc_idx_pct_le20       |     309 |    978 |        24   |      -112 |      402 |      46   |     53.5 |   -514 | -924 | -104 | -2.46 |         1 |          4 |       -210 |       -206 |        nan |
| c_J_nowall_ahead100_SPX_vol |     638 |    216 |        74.7 |       436 |     -177 |      53.1 |     45.8 |    613 |  116 | 1110 |  2.42 |         3 |          3 |        306 |         85 |        nan |
| c_I_NQ_lags_ES5             |     554 |    793 |        41.1 |        23 |      427 |      47.6 |     54.2 |   -404 | -756 |  -51 | -2.24 |         0 |          4 |       -232 |          5 |       -541 |

## H (L3) items: MBO months only; pooled and strata

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H2_arrival_imb60_lo         |    3906 |  16058 |        19.6 |       217 |       76 |      46   |     43.2 |    141 |   59 |  223 |  3.37 |         4 |          4 |        249 |        184 |        -73 |
| c_H_spoof_ahead60_ge1         |    6376 |  13601 |        31.9 |        34 |      136 |      42.4 |     44.3 |   -102 | -164 |  -41 | -3.27 |         1 |          4 |       -546 |       -741 |       -560 |
| c_H2_spoof_ahead60_lo         |   13592 |   6372 |        68.1 |       136 |       35 |      44.3 |     42.5 |    101 |   40 |  162 |  3.23 |         3 |          4 |        546 |        741 |        560 |
| c_H2_ctr_mine300_lo           |    3381 |  16583 |        16.9 |       218 |       80 |      47.5 |     42.9 |    138 |   46 |  229 |  2.96 |         4 |          4 |         99 |        284 |        563 |
| c_H_spoof_ahead300_ge1        |    9517 |  10460 |        47.6 |        58 |      145 |      43   |     44.4 |    -87 | -148 |  -26 | -2.79 |         0 |          4 |       -227 |       -195 |       -230 |
| c_H2_ctr_mine60_hi            |    3927 |  16037 |        19.7 |         8 |      127 |      40.6 |     44.5 |   -119 | -203 |  -35 | -2.79 |         0 |          4 |        -97 |       -242 |       -334 |
| c_H_gmax_against60_lt10       |   10795 |   9182 |        54   |       140 |       61 |      44   |     43.4 |     79 |   19 |  139 |  2.59 |         4 |          4 |         86 |         92 |        -18 |
| c_H2_spoof_ahead300_lo        |   10615 |   9349 |        53.2 |       141 |       61 |      44.4 |     43   |     80 |   19 |  141 |  2.57 |         4 |          4 |        227 |        195 |        230 |
| c_H_arrival_imb60_pos         |   12983 |   6994 |        65   |        74 |      158 |      43.1 |     44.9 |    -83 | -148 |  -19 | -2.53 |         0 |          4 |       -201 |        -88 |        135 |
| c_H2_ctr_mine60_lo            |    3631 |  16333 |        18.2 |       191 |       84 |      47.2 |     42.9 |    108 |   24 |  191 |  2.53 |         4 |          4 |        212 |        266 |        487 |
| c_H2_spoof_ahead60_hi         |    3641 |  16323 |        18.2 |        33 |      119 |      42.8 |     43.9 |    -86 | -152 |  -19 | -2.53 |         0 |          4 |       -546 |       -741 |       -560 |
| c_H_aggr50_with300_ge1        |    5865 |  14112 |        29.4 |        52 |      125 |      42.8 |     44.1 |    -74 | -131 |  -16 | -2.51 |         0 |          4 |       -177 |       -188 |       -274 |
| c_H_gmax_with60_ge10          |   12527 |   7450 |        62.7 |        71 |      158 |      43.3 |     44.4 |    -87 | -155 |  -19 | -2.49 |         0 |          4 |        -12 |        109 |        143 |
| c_H_no_aged_big_ahead         |   18776 |   1201 |        94   |        94 |      255 |      43.3 |     49.5 |   -161 | -288 |  -34 | -2.49 |         1 |          4 |       -484 |       -632 |      -1085 |
| c_H2_ctr_ahead60_hi           |    4186 |  15778 |        21   |        29 |      123 |      41.4 |     44.3 |    -95 | -171 |  -18 | -2.44 |         0 |          4 |         19 |       -162 |       -220 |
| c_H_sweep3_with60_ge1         |   15447 |   4530 |        77.3 |        81 |      179 |      43   |     46.1 |    -98 | -180 |  -15 | -2.33 |         0 |          4 |       -111 |         36 |        522 |
| c_H_aggr50_with_gt_against300 |    4615 |  15362 |        23.1 |        48 |      120 |      43   |     43.9 |    -72 | -132 |  -11 | -2.32 |         0 |          4 |       -107 |        -87 |       -180 |
| c_H_arrival_imb30_pos         |   12146 |   7831 |        60.8 |        75 |      148 |      43.4 |     44.2 |    -73 | -136 |   -9 | -2.25 |         1 |          4 |          8 |          2 |        194 |
| c_H2_aggr20_with300_hi        |    4775 |  15189 |        23.9 |        56 |      118 |      43.2 |     43.9 |    -63 | -118 |   -8 | -2.23 |         0 |          4 |        -94 |       -125 |       -135 |
| c_H_aggr50_with60_ge1         |    2647 |  17330 |        13.2 |        36 |      114 |      42.8 |     43.8 |    -77 | -146 |   -8 | -2.2  |         1 |          4 |        -51 |         17 |        -59 |
| c_H_no_spoof_mine300          |   10712 |   9265 |        53.6 |       135 |       67 |      44.1 |     43.2 |     68 |    7 |  128 |  2.18 |         3 |          4 |        167 |        282 |        368 |
| c_H2_spoof_ahead300_hi        |    4380 |  15584 |        21.9 |        49 |      119 |      42.7 |     44   |    -70 | -132 |   -7 | -2.17 |         0 |          4 |       -170 |       -195 |       -230 |
| c_H2_ctr_ahead300_hi          |    4166 |  15798 |        20.9 |        37 |      121 |      40.4 |     44.6 |    -83 | -160 |   -7 | -2.14 |         1 |          4 |        -40 |       -108 |       -257 |
| c_H2_bmax_ahead_lo            |   17876 |   2088 |        89.5 |        93 |      194 |      43.2 |     48.6 |   -102 | -195 |   -8 | -2.13 |         0 |          4 |       -193 |       -485 |      -1092 |
| c_H_no_big10_ahead            |   17885 |   2092 |        89.5 |        93 |      194 |      43.1 |     48.6 |   -101 | -194 |   -8 | -2.12 |         0 |          4 |       -193 |       -485 |      -1092 |

### H items in stratum lvl:ahead<=10pts(level close ahead) (n=12,471), 12 largest |z|

| cond                    |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_spoof_ahead60_ge1   |    3978 |   8432 |        32   |        11 |      139 |      41.8 |     44.4 |   -127 | -207 |  -48 | -3.14 |         1 |          4 |       -691 |       -919 |        nan |
| c_H2_spoof_ahead60_lo   |    8427 |   3974 |        68   |       138 |       12 |      44.4 |     41.8 |    126 |   46 |  205 |  3.1  |         3 |          4 |        691 |        919 |        nan |
| c_H2_aggr20_with300_hi  |    2800 |   9601 |        22.6 |        21 |      120 |      42.4 |     44   |    -99 | -170 |  -29 | -2.76 |         1 |          4 |       -280 |       -294 |       -702 |
| c_H_spoof_ahead300_ge1  |    5975 |   6435 |        48.2 |        42 |      150 |      42.6 |     44.5 |   -108 | -187 |  -29 | -2.67 |         1 |          4 |       -313 |       -304 |       -736 |
| c_H_ahead_touch_le2     |    9033 |   3377 |        72.8 |       129 |       15 |      43.8 |     43.1 |    114 |   29 |  198 |  2.63 |         4 |          4 |        183 |        346 |       1143 |
| c_H_aggr50_with60_ge1   |    1553 |  10857 |        12.5 |        -4 |      112 |      41.5 |     43.9 |   -116 | -206 |  -27 | -2.54 |         0 |          4 |       -100 |         57 |       -299 |
| c_H2_spoof_ahead300_lo  |    6543 |   5858 |        52.8 |       145 |       45 |      44.5 |     42.7 |    100 |   21 |  180 |  2.49 |         3 |          4 |        313 |        304 |        736 |
| c_H2_arrival_imb60_lo   |    2508 |   9893 |        20.2 |       203 |       71 |      46.2 |     43   |    132 |   26 |  237 |  2.45 |         4 |          4 |        200 |        181 |       -286 |
| c_H_gmax_against60_lt10 |    7030 |   5380 |        56.6 |       139 |       44 |      44.2 |     42.8 |     96 |   19 |  172 |  2.44 |         4 |          4 |         93 |         52 |         -8 |
| c_H_arrival_imb30_pos   |    7476 |   4934 |        60.2 |        58 |      159 |      43   |     44.4 |   -101 | -183 |  -19 | -2.42 |         1 |          4 |        -37 |        -45 |        271 |
| c_H_arrival_imb60_pos   |    7992 |   4418 |        64.4 |        62 |      162 |      42.8 |     45   |   -100 | -183 |  -17 | -2.36 |         1 |          4 |       -168 |       -112 |        176 |
| c_H2_touch_mine_sz_hi   |    1378 |  11023 |        11.1 |       -15 |      112 |      42.6 |     43.7 |   -127 | -237 |  -17 | -2.27 |         2 |          4 |       -272 |       -384 |       -485 |

### H items in stratum lvl:ahead<=20pts (n=17,116), 12 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_spoof_ahead60_ge1         |    5476 |  11531 |        32.2 |        11 |      133 |      41.6 |     44   |   -122 | -189 |  -55 | -3.58 |         1 |          4 |       -488 |       -898 |        nan |
| c_H2_spoof_ahead60_lo         |   11524 |   5472 |        67.8 |       133 |       11 |      44.1 |     41.7 |    121 |   54 |  188 |  3.55 |         3 |          4 |        488 |        898 |        nan |
| c_H2_arrival_imb60_lo         |    3362 |  13634 |        19.8 |       204 |       66 |      45.9 |     42.6 |    138 |   49 |  227 |  3.04 |         4 |          4 |        234 |        205 |        -84 |
| c_H_spoof_ahead300_ge1        |    8184 |   8823 |        48.1 |        42 |      142 |      42.4 |     44.1 |   -100 | -167 |  -33 | -2.94 |         1 |          4 |       -128 |       -239 |       -517 |
| c_H2_ctr_mine300_lo           |    2923 |  14073 |        17.2 |       217 |       68 |      47   |     42.5 |    149 |   49 |  249 |  2.92 |         4 |          4 |        133 |        252 |        494 |
| c_H2_spoof_ahead300_lo        |    8958 |   8038 |        52.7 |       137 |       45 |      44.1 |     42.4 |     93 |   26 |  159 |  2.73 |         3 |          4 |        128 |        239 |        517 |
| c_H_aggr50_with300_ge1        |    4839 |  12168 |        28.4 |        31 |      118 |      41.9 |     43.8 |    -87 | -149 |  -24 | -2.72 |         0 |          4 |       -253 |       -265 |       -325 |
| c_H_gmax_with60_ge10          |   10406 |   6601 |        61.2 |        54 |      155 |      42.5 |     44.4 |   -100 | -174 |  -27 | -2.69 |         0 |          4 |         38 |        107 |        259 |
| c_H2_ctr_mine60_lo            |    3117 |  13879 |        18.3 |       194 |       71 |      46.7 |     42.5 |    123 |   31 |  214 |  2.63 |         4 |          4 |        246 |        291 |        422 |
| c_H2_aggr20_with300_hi        |    3957 |  13039 |        23.3 |        32 |      112 |      42.4 |     43.6 |    -80 | -140 |  -20 | -2.63 |         1 |          4 |       -142 |       -196 |       -262 |
| c_H_arrival_imb60_pos         |   11010 |   5997 |        64.7 |        61 |      153 |      42.5 |     44.7 |    -93 | -163 |  -23 | -2.59 |         0 |          4 |       -202 |       -156 |         13 |
| c_H_aggr50_with_gt_against300 |    3791 |  13216 |        22.3 |        26 |      113 |      42   |     43.6 |    -86 | -152 |  -20 | -2.57 |         0 |          4 |       -164 |       -148 |       -185 |

### H items in stratum lvl:behind<=3pts(at a level) (n=4,346), 12 largest |z|

| cond                        |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_no_aged_big_ahead       |    4014 |    309 |        92.8 |        95 |      418 |      44.1 |     51.8 |   -323 | -577 |  -68 | -2.48 |         0 |          4 |         -8 |        nan |        nan |
| c_H2_bmax_ahead_lo          |    3817 |    502 |        88.4 |        90 |      326 |      43.8 |     51.6 |   -236 | -429 |  -43 | -2.4  |         0 |          4 |       -254 |        -49 |        nan |
| c_H_no_big10_ahead          |    3820 |    503 |        88.4 |        91 |      323 |      43.7 |     51.5 |   -232 | -425 |  -39 | -2.36 |         0 |          4 |       -254 |        -49 |        nan |
| c_H_arrival_imb30_pos       |    2590 |   1733 |        59.9 |        54 |      213 |      44.2 |     45.2 |   -159 | -298 |  -21 | -2.25 |         0 |          4 |       -174 |        235 |        573 |
| c_H2_bmax_ahead_hi          |     453 |   3866 |        10.5 |       286 |       97 |      50.3 |     44   |    189 |  -12 |  390 |  1.84 |         4 |          4 |        254 |         49 |        nan |
| c_H2_spoof_mine_gt_ahead300 |     902 |   3421 |        20.9 |         7 |      147 |      42.5 |     45.2 |   -140 | -294 |   14 | -1.78 |         2 |          4 |        -81 |        -94 |        nan |
| c_H_touch_ratio_ge1.0       |    2894 |   1429 |        66.9 |        77 |      201 |      43.6 |     46.8 |   -123 | -267 |   20 | -1.69 |         0 |          4 |       -386 |       -185 |       -881 |
| c_H_sweep3_with60_ge1       |    3013 |   1310 |        69.7 |        77 |      212 |      43.2 |     48   |   -135 | -296 |   26 | -1.64 |         0 |          4 |       -118 |        104 |        795 |
| c_H2_gmax_with60_lo         |    1038 |   3281 |        24   |       227 |       82 |      46.3 |     44.1 |    144 |  -34 |  323 |  1.59 |         3 |          4 |        -64 |       -545 |       -311 |
| c_H2_touch_mine_sz_hi       |     482 |   3837 |        11.2 |        -9 |      133 |      42.3 |     45   |   -142 | -327 |   43 | -1.51 |         1 |          4 |        -15 |       -106 |        362 |
| c_H2_spoof_ahead_gt_mine300 |    1267 |   3056 |        29.3 |       194 |       86 |      46.7 |     43.8 |    107 |  -35 |  250 |  1.47 |         2 |          4 |       -467 |         77 |        nan |
| c_H2_ctr_mine60_hi          |     789 |   3530 |        18.3 |         7 |      142 |      41.9 |     45.3 |   -135 | -320 |   50 | -1.43 |         1 |          4 |        -58 |       -169 |       -266 |

### H items in stratum lvl:behind<=5&ahead>=20 (n=1,186), 12 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_touch_ratio_ge1.0         |     813 |    351 |        69.8 |        61 |      415 |      44.8 |     51.8 |   -354 | -598 | -110 | -2.85 |         0 |          4 |       -419 |       -303 |        nan |
| c_H_ctr_mine_lt10_300         |     529 |    635 |        45.4 |       329 |       34 |      51.8 |     42.8 |    295 |   64 |  526 |  2.5  |         1 |          3 |        -45 |         55 |        nan |
| c_H2_touch_ahead_sz_lo        |     585 |    577 |        50.3 |        23 |      305 |      43.6 |     50.1 |   -282 | -514 |  -50 | -2.39 |         1 |          4 |       -311 |       -421 |        nan |
| c_H_no_aged_big_ahead         |    1088 |     76 |        93.5 |       134 |      653 |      45.9 |     61.8 |   -519 | -948 |  -89 | -2.37 |         0 |          3 |        nan |        nan |        nan |
| c_H2_spoof_mine300_hi         |     261 |    901 |        22.5 |       -31 |      219 |      45.6 |     47.2 |   -250 | -496 |   -4 | -2    |         0 |          4 |       -641 |       -561 |        nan |
| c_H2_spoof_mine_gt_ahead300   |     253 |    911 |        21.7 |        -3 |      215 |      45.1 |     47.4 |   -219 | -474 |   37 | -1.68 |         1 |          4 |       -411 |        nan |        nan |
| c_H_no_big10_ahead            |    1036 |    128 |        89   |       139 |      403 |      45.7 |     57   |   -264 | -596 |   68 | -1.56 |         1 |          4 |        -51 |        nan |        nan |
| c_H_arrival_imb60_ge0.1       |     246 |    918 |        21.1 |       362 |      116 |      52   |     45.5 |    246 |  -65 |  557 |  1.55 |         4 |          4 |        -95 |       -275 |       -310 |
| c_H_no_big20_ahead            |    1120 |     44 |        96.2 |       154 |      532 |      46.2 |     65.9 |   -379 | -892 |  134 | -1.45 |         1 |          1 |        nan |        nan |        nan |
| c_H2_bmax_ahead_lo            |    1035 |    127 |        89.1 |       138 |      368 |      45.6 |     56.7 |   -230 | -557 |   97 | -1.38 |         2 |          4 |        -51 |        nan |        nan |
| c_H2_touch_mine_sz_hi         |     143 |   1019 |        12.3 |       -46 |      192 |      46.2 |     46.9 |   -238 | -578 |  102 | -1.37 |         1 |          4 |        -74 |        430 |        nan |
| c_H_aggr50_with_gt_against300 |     285 |    879 |        24.5 |       295 |      127 |      51.2 |     45.5 |    168 |  -73 |  410 |  1.37 |         1 |          4 |        580 |        575 |         61 |

### H items in stratum lvl:behind<=5pts (n=7,675), 12 largest |z|

| cond                    |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H2_spoof_ahead300_hi  |    1519 |   6102 |        19.9 |        14 |      137 |      42.9 |     44.6 |   -123 | -224 |  -21 | -2.37 |         1 |          4 |       -443 |        -72 |       -634 |
| c_H_touch_ratio_ge1.0   |    5194 |   2435 |        68.1 |        74 |      198 |      43.2 |     46.5 |   -124 | -232 |  -16 | -2.26 |         0 |          4 |       -311 |       -213 |       -503 |
| c_H_no_aged_big_ahead   |    7079 |    550 |        92.8 |        98 |      310 |      43.7 |     51.4 |   -212 | -407 |  -17 | -2.13 |         0 |          4 |        272 |        804 |        nan |
| c_H_no_aggr50_against60 |    7290 |    339 |        95.6 |       121 |      -52 |      44.5 |     38.9 |    173 |   10 |  336 |  2.08 |         3 |          4 |        287 |       -553 |        nan |
| c_H2_spoof_ahead60_hi   |    1290 |   6331 |        16.9 |        23 |      130 |      43   |     44.6 |   -107 | -214 |   -0 | -1.97 |         2 |          4 |       -689 |        nan |        nan |
| c_H2_touch_mine_sz_hi   |     864 |   6757 |        11.3 |       -11 |      128 |      41.8 |     44.6 |   -139 | -279 |    1 | -1.94 |         1 |          4 |       -135 |       -199 |        625 |
| c_H_no_big10_ahead      |    6743 |    886 |        88.4 |        98 |      234 |      43.4 |     51.1 |   -136 | -284 |   11 | -1.81 |         1 |          4 |        114 |        468 |       -231 |
| c_H2_ctr_mine60_lo      |    1582 |   6039 |        20.8 |       208 |       87 |      47   |     43.6 |    121 |  -10 |  252 |  1.81 |         3 |          4 |        366 |        230 |         78 |
| c_H_refill_mine300_ge1  |     357 |   7272 |         4.7 |       -27 |      120 |      40.1 |     44.5 |   -147 | -308 |   13 | -1.8  |         0 |          4 |       -129 |       -190 |        nan |
| c_H2_bmax_ahead_lo      |    6737 |    884 |        88.4 |        97 |      230 |      43.4 |     51.1 |   -133 | -280 |   14 | -1.77 |         1 |          4 |        114 |        468 |       -231 |
| c_H2_spoof_mine60_hi    |    1325 |   6296 |        17.4 |        32 |      129 |      42.6 |     44.6 |    -98 | -207 |   11 | -1.76 |         1 |          4 |       -346 |       -336 |        nan |
| c_H2_aggr20_with300_hi  |    1616 |   6005 |        21.2 |        50 |      129 |      43.2 |     44.6 |    -79 | -168 |   11 | -1.73 |         1 |          4 |       -149 |        128 |       -364 |

### H items in stratum lvl:behind>5 (n=12,463), 12 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H2_arrival_imb60_lo         |    2343 |  10000 |        19   |       251 |       62 |      46.4 |     42.6 |    189 |   84 |  294 |  3.53 |         4 |          4 |        245 |        348 |        172 |
| c_H2_spoof_ahead60_lo         |    8337 |   4006 |        67.5 |       135 |       22 |      43.9 |     42.3 |    113 |   35 |  190 |  2.86 |         4 |          4 |        502 |        739 |        nan |
| c_H_spoof_ahead60_ge1         |    4008 |   8340 |        32.5 |        21 |      134 |      42.3 |     43.9 |   -113 | -190 |  -35 | -2.85 |         0 |          4 |       -502 |       -739 |        nan |
| c_H_spoof_ahead300_ge1        |    5925 |   6423 |        48   |        41 |      150 |      42.6 |     44   |   -109 | -186 |  -32 | -2.78 |         0 |          4 |       -158 |       -254 |        -67 |
| c_H2_ctr_mine300_lo           |    1840 |  10503 |        14.9 |       241 |       73 |      48   |     42.6 |    168 |   46 |  290 |  2.69 |         4 |          4 |         15 |        128 |        706 |
| c_H2_spoof_ahead300_lo        |    6504 |   5839 |        52.7 |       148 |       43 |      44   |     42.6 |    105 |   28 |  182 |  2.68 |         4 |          4 |        158 |        254 |         67 |
| c_H_arrival_imb60_pos         |    8046 |   4302 |        65.2 |        59 |      170 |      42.4 |     45.1 |   -111 | -192 |  -30 | -2.67 |         0 |          4 |       -214 |       -150 |        -19 |
| c_H_aggr50_with300_ge1        |    3841 |   8507 |        31.1 |        36 |      125 |      42.6 |     43.7 |    -90 | -162 |  -17 | -2.42 |         1 |          4 |       -219 |       -254 |       -336 |
| c_H2_ctr_ahead300_hi          |    2750 |   9593 |        22.3 |        10 |      123 |      39.4 |     44.5 |   -113 | -208 |  -18 | -2.34 |         1 |          4 |       -103 |       -288 |       -354 |
| c_H_aggr50_with_gt_against300 |    3019 |   9329 |        24.4 |        29 |      120 |      42.8 |     43.5 |    -91 | -167 |  -15 | -2.34 |         0 |          4 |       -136 |       -112 |       -218 |
| c_H2_ctr_mine60_hi            |    2470 |   9873 |        20   |        -3 |      123 |      39.8 |     44.3 |   -126 | -232 |  -20 | -2.32 |         0 |          4 |        -94 |       -303 |       -413 |
| c_H2_spoof_ahead_gt_mine60    |    2575 |   9773 |        20.8 |        17 |      119 |      41.8 |     43.8 |   -102 | -189 |  -14 | -2.28 |         2 |          4 |       -662 |       -727 |        nan |

### H items in stratum lvl:cluster_behind_10 (n=12,840), 12 largest |z|

| cond                    |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_spoof_ahead60_ge1   |    4469 |   8329 |        34.9 |        26 |      170 |      42.3 |     45   |   -143 | -217 |  -70 | -3.81 |         0 |          4 |       -882 |      -1134 |        nan |
| c_H2_spoof_ahead60_lo   |    8321 |   4465 |        65.1 |       169 |       27 |      45   |     42.4 |    141 |   67 |  215 |  3.75 |         4 |          4 |        882 |       1134 |        nan |
| c_H_gmax_against60_lt10 |    6817 |   5981 |        53.3 |       179 |       52 |      44.8 |     43.3 |    128 |   54 |  201 |  3.4  |         3 |          4 |        144 |        145 |         44 |
| c_H2_arrival_imb60_lo   |    2508 |  10278 |        19.6 |       254 |       86 |      47.2 |     43.3 |    168 |   68 |  268 |  3.3  |         4 |          4 |        404 |        233 |        -11 |
| c_H_arrival_imb30_pos   |    7680 |   5118 |        60   |        70 |      195 |      43.2 |     45.4 |   -125 | -202 |  -48 | -3.19 |         0 |          4 |       -201 |       -109 |         89 |
| c_H_no_aged_big_ahead   |   11878 |    920 |        92.8 |       104 |      322 |      43.6 |     50.9 |   -218 | -362 |  -74 | -2.98 |         1 |          4 |       -167 |       -178 |       -890 |
| c_H_arrival_imb60_pos   |    8261 |   4537 |        64.6 |        80 |      193 |      43.1 |     45.8 |   -113 | -191 |  -35 | -2.84 |         0 |          4 |       -264 |        -98 |        -11 |
| c_H2_spoof_ahead300_hi  |    3059 |   9727 |        23.9 |        43 |      143 |      43.3 |     44.3 |   -100 | -174 |  -25 | -2.63 |         0 |          4 |       -324 |       -348 |       -570 |
| c_H2_ctr_mine300_hi     |    2768 |  10018 |        21.6 |        24 |      146 |      40.5 |     45.1 |   -122 | -213 |  -30 | -2.6  |         0 |          4 |          3 |        -89 |       -380 |
| c_H_spoof_ahead300_ge1  |    6551 |   6247 |        51.2 |        71 |      170 |      43.5 |     44.7 |    -99 | -174 |  -23 | -2.56 |         1 |          4 |       -338 |       -348 |       -570 |
| c_H2_ctr_mine60_hi      |    2446 |  10340 |        19.1 |        13 |      144 |      40.8 |     44.9 |   -132 | -234 |  -30 | -2.53 |         0 |          4 |        -39 |       -336 |       -385 |
| c_H2_spoof_ahead300_lo  |    6343 |   6443 |        49.6 |       168 |       71 |      44.7 |     43.5 |     97 |   21 |  172 |  2.52 |         3 |          4 |        338 |        348 |        570 |

### Year-by-year for the spoof-like items and the five largest pooled H items (lift in $/trade, yes minus no; n_yes shown)


`c_H_spoof_ahead60_ge1`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |    6376 |  13601 |   -102 | -3.27 |           1 |         -97 |         -76 |        -236 |       -546 |
| sess:0.0                            |    1329 |   6108 |   -157 | -1.72 |         180 |        -196 |        -116 |        -447 |      -1330 |
| sess:1.0                            |    1484 |   5004 |     19 |  0.35 |         149 |          88 |         -23 |         -57 |       -610 |
| sess:3.0                            |    2945 |   1971 |    -86 | -2.18 |        -100 |        -153 |         -13 |        -110 |       -355 |
| sess:4.0                            |     618 |    518 |     14 |  0.19 |         134 |         174 |          70 |        -374 |        -98 |
| lvl:behind<=3pts(at a level)        |    1333 |   2990 |    -39 | -0.57 |         232 |        -176 |         -52 |        -170 |       -778 |
| lvl:behind<=5pts                    |    2368 |   5261 |    -85 | -1.65 |          38 |        -112 |         -72 |        -320 |       -689 |
| lvl:ahead<=10pts(level close ahead) |    3978 |   8432 |   -127 | -3.14 |          21 |         -95 |         -79 |        -305 |       -691 |
| lvl:ahead<=20pts                    |    5476 |  11531 |   -122 | -3.58 |          21 |        -131 |         -76 |        -269 |       -488 |
| lvl:cluster_behind_10               |    4469 |   8329 |   -143 | -3.81 |         -65 |        -174 |        -118 |        -217 |       -882 |
| lvl:behind<=5&ahead>=20             |     349 |    815 |     17 |  0.14 |         -99 |         -78 |        -301 |        -193 |       -969 |
| lvl:behind>5                        |    4008 |   8340 |   -113 | -2.85 |         -29 |         -67 |         -80 |        -204 |       -502 |

`c_H_spoof_ahead300_ge1`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |    9517 |  10460 |    -87 | -2.79 |         -16 |          -9 |        -156 |         -98 |       -227 |
| sess:0.0                            |    2360 |   5077 |    -55 | -0.73 |         333 |          41 |        -229 |        -186 |       -363 |
| sess:1.0                            |    2536 |   3952 |    -55 | -1.18 |        -164 |         -27 |         -99 |          20 |       -166 |
| sess:3.0                            |    3793 |   1123 |    -28 | -0.6  |        -750 |         264 |         -33 |         -32 |       -238 |
| sess:4.0                            |     828 |    308 |    -62 | -0.76 |         nan |         181 |         -45 |        -215 |         35 |
| lvl:behind<=3pts(at a level)        |    2039 |   2284 |      5 |  0.08 |         333 |         -19 |        -197 |         -74 |       -532 |
| lvl:behind<=5pts                    |    3592 |   4037 |    -51 | -0.99 |         152 |          61 |        -268 |        -146 |       -428 |
| lvl:ahead<=10pts(level close ahead) |    5975 |   6435 |   -108 | -2.67 |          26 |          -6 |        -137 |        -151 |       -313 |
| lvl:ahead<=20pts                    |    8184 |   8823 |   -100 | -2.94 |           3 |         -35 |        -151 |        -104 |       -128 |
| lvl:cluster_behind_10               |    6551 |   6247 |    -99 | -2.56 |        -115 |         -68 |        -160 |           1 |       -338 |
| lvl:behind<=5&ahead>=20             |     517 |    647 |     49 |  0.41 |          49 |         325 |        -587 |        -101 |       -998 |
| lvl:behind>5                        |    5925 |   6423 |   -109 | -2.78 |        -260 |         -52 |         -97 |         -78 |       -158 |

`c_H_no_spoof_mine60`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |   14068 |   5909 |     46 |  1.45 |          12 |         -38 |          77 |         104 |        268 |
| sess:0.0                            |    6254 |   1183 |     57 |  0.6  |        -489 |         -53 |         174 |         312 |        998 |
| sess:1.0                            |    5157 |   1331 |    -63 | -1.1  |         -10 |        -206 |         -31 |          -4 |        233 |
| sess:3.0                            |    2084 |   2832 |      1 |  0.02 |         125 |         -56 |         -42 |         -84 |        -10 |
| sess:4.0                            |     573 |    563 |     29 |  0.4  |         -64 |         -56 |         140 |          -0 |       -220 |
| lvl:behind<=3pts(at a level)        |    3102 |   1221 |     14 |  0.21 |        -270 |          72 |         132 |         100 |        410 |
| lvl:behind<=5pts                    |    5452 |   2177 |     73 |  1.39 |         -79 |          58 |         129 |         248 |        346 |
| lvl:ahead<=10pts(level close ahead) |    8767 |   3643 |     57 |  1.39 |          -7 |         -42 |          66 |         125 |        217 |
| lvl:ahead<=20pts                    |   11953 |   5054 |     52 |  1.52 |         -11 |         -22 |          63 |         122 |        242 |
| lvl:cluster_behind_10               |    8675 |   4123 |     94 |  2.5  |         119 |          72 |         138 |         -59 |        227 |
| lvl:behind<=5&ahead>=20             |     832 |    332 |     90 |  0.77 |          74 |         288 |         518 |         184 |        468 |
| lvl:behind>5                        |    8616 |   3732 |     29 |  0.73 |          97 |        -132 |          52 |          44 |        235 |

`c_H2_arrival_imb60_lo`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |    3906 |  16058 |    141 |  3.37 |          75 |         200 |         114 |         150 |        249 |
| sess:0.0                            |    1698 |   5734 |    181 |  2.17 |         112 |          49 |         254 |         227 |        324 |
| sess:1.0                            |    1292 |   5194 |     89 |  1.5  |          66 |         251 |          21 |          60 |        148 |
| sess:3.0                            |     755 |   4155 |    109 |  1.98 |          33 |         284 |         -63 |         150 |        268 |
| sess:4.0                            |     161 |    975 |     -4 | -0.04 |         -90 |         142 |          97 |        -273 |       -207 |
| lvl:behind<=3pts(at a level)        |     873 |   3446 |     98 |  1.07 |          -1 |         222 |         106 |          26 |        295 |
| lvl:behind<=5pts                    |    1563 |   6058 |     67 |  1    |         106 |         141 |         -50 |          83 |        260 |
| lvl:ahead<=10pts(level close ahead) |    2508 |   9893 |    132 |  2.45 |          88 |         253 |          86 |          90 |        200 |
| lvl:ahead<=20pts                    |    3362 |  13634 |    138 |  3.04 |          74 |         184 |         128 |         139 |        234 |
| lvl:cluster_behind_10               |    2508 |  10278 |    168 |  3.3  |          87 |         154 |         135 |         270 |        404 |
| lvl:behind<=5&ahead>=20             |     210 |    952 |     56 |  0.35 |         438 |         156 |         275 |        -239 |       -182 |
| lvl:behind>5                        |    2343 |  10000 |    189 |  3.53 |          34 |         244 |         210 |         178 |        245 |

`c_H2_spoof_ahead60_lo`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |   13592 |   6372 |    101 |  3.23 |          -9 |          97 |          76 |         236 |        546 |
| sess:0.0                            |    6103 |   1329 |    155 |  1.7  |        -199 |         196 |         116 |         447 |       1330 |
| sess:1.0                            |    5002 |   1484 |    -18 | -0.33 |        -142 |         -88 |          23 |          57 |        610 |
| sess:3.0                            |    1969 |   2941 |     86 |  2.17 |         115 |         153 |          13 |         110 |        355 |
| sess:4.0                            |     518 |    618 |    -14 | -0.19 |        -134 |        -174 |         -70 |         374 |         98 |
| lvl:behind<=3pts(at a level)        |    2988 |   1331 |     36 |  0.52 |        -250 |         176 |          52 |         170 |        778 |
| lvl:behind<=5pts                    |    5255 |   2366 |     81 |  1.59 |         -56 |         112 |          72 |         320 |        689 |
| lvl:ahead<=10pts(level close ahead) |    8427 |   3974 |    126 |  3.1  |         -29 |          95 |          79 |         305 |        691 |
| lvl:ahead<=20pts                    |   11524 |   5472 |    121 |  3.55 |         -26 |         131 |          76 |         269 |        488 |
| lvl:cluster_behind_10               |    8321 |   4465 |    141 |  3.75 |          53 |         174 |         118 |         217 |        882 |
| lvl:behind<=5&ahead>=20             |     813 |    349 |    -24 | -0.2  |          20 |          78 |         301 |         193 |        969 |
| lvl:behind>5                        |    8337 |   4006 |    113 |  2.86 |          36 |          67 |          80 |         204 |        502 |

`c_H2_ctr_mine300_lo`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |    3381 |  16583 |    138 |  2.96 |         190 |          82 |         151 |         155 |         99 |
| sess:0.0                            |    1861 |   5571 |    150 |  1.88 |         169 |          27 |         291 |         160 |        -21 |
| sess:1.0                            |     802 |   5684 |     75 |  0.98 |         360 |         176 |        -183 |         188 |        420 |
| sess:3.0                            |     581 |   4329 |    -19 | -0.32 |          30 |        -159 |          39 |         -14 |         -2 |
| sess:4.0                            |     137 |    999 |    142 |  1.18 |         nan |          75 |         140 |         175 |        172 |
| lvl:behind<=3pts(at a level)        |     905 |   3414 |    -44 | -0.48 |        -110 |        -210 |         214 |          -5 |       -103 |
| lvl:behind<=5pts                    |    1541 |   6080 |     97 |  1.38 |         142 |         -67 |          57 |         324 |        275 |
| lvl:ahead<=10pts(level close ahead) |    2265 |  10136 |    111 |  1.86 |         138 |          87 |         161 |          86 |        -36 |
| lvl:ahead<=20pts                    |    2923 |  14073 |    149 |  2.92 |         169 |          96 |         175 |         177 |        133 |
| lvl:cluster_behind_10               |    2336 |  10450 |     72 |  1.31 |         188 |          36 |          32 |          72 |        -92 |
| lvl:behind<=5&ahead>=20             |     209 |    953 |    -98 | -0.61 |         242 |        -102 |          -2 |        -361 |       -518 |
| lvl:behind>5                        |    1840 |  10503 |    168 |  2.69 |         271 |         216 |         212 |          70 |         15 |

H caveat: MBO covers 2023-04..2026-11 after the history purchase, so years can test stability.

## BLOCK 14 breadth, rotation, relative value: single-condition tables (pooled, per session; stable = same sign in every evaluated year and in L6M)

38 conditions with n>=100 each side, 4 with |z|>2 (chance about 2), 2 of those stable. Largest |z| pooled:

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_avg_corr60_ge0.3              |    1579 |   1178 |        57.3 |       -45 |      149 |      40.5 |     47.1 |   -194 | -294 |  -93 | -3.78 |         0 |          3 |        -27 |       -158 |        nan |
| c_B14_avg_corr60_ge0.5              |     678 |   2079 |        24.6 |       -69 |       73 |      40   |     44.4 |   -141 | -252 |  -31 | -2.51 |         0 |          3 |        265 |        nan |        nan |
| c_B14_avg_corr60_le0.2              |     596 |   2161 |        21.6 |       148 |        8 |      47.5 |     42.2 |    140 |   18 |  262 |  2.25 |         3 |          3 |         -7 |         97 |       -289 |
| c_B14_hl_net_15bars_with_pos        |    2355 |   1085 |        68.5 |        84 |      -15 |      44   |     40.9 |    100 |    7 |  193 |  2.1  |         3 |          3 |        151 |        127 |        624 |
| c_B14_NVDA_minus_QQQ_15_with        |    1966 |   1219 |        61.7 |        -2 |       92 |      42.2 |     44.9 |    -95 | -191 |    2 | -1.92 |         1 |          3 |         13 |       -144 |        -27 |
| c_B14_largest_minus_QQQ_15_with     |    1972 |   1213 |        61.9 |         0 |       88 |      42.1 |     45   |    -88 | -184 |    9 | -1.78 |         1 |          3 |        -31 |        -85 |       -243 |
| c_B14_eq7_minus_QQQ_15_with         |    1830 |   1355 |        57.5 |        -1 |       81 |      42.5 |     44.2 |    -82 | -176 |   13 | -1.69 |         1 |          3 |        118 |        354 |        342 |
| c_B14_RTY_outperforming_ES_240_with |    9385 |   8310 |        53   |        64 |      113 |      42.9 |     44.1 |    -49 | -112 |   14 | -1.53 |         1 |          4 |         52 |         38 |        240 |
| c_B14_eq7_minus_QQQ_60_with         |    1247 |    961 |        56.5 |         0 |       81 |      42   |     45.4 |    -80 | -191 |   30 | -1.42 |         0 |          3 |          0 |         30 |        795 |
| c_B14_NQ_rich_vs_ES_with_ge1.0      |    6246 |  12103 |        34   |       120 |       75 |      43.6 |     43.5 |     46 |  -21 |  112 |  1.35 |         2 |          4 |         -3 |        -40 |       -130 |
| c_B14_NQ_rich_vs_ES_with_ge1.5      |    3937 |  14412 |        21.5 |       123 |       81 |      43.9 |     43.4 |     42 |  -33 |  117 |  1.1  |         4 |          4 |        -77 |         33 |       -347 |
| c_B14_NQ_rich_vs_ES_with_ge0.5      |    8084 |  10265 |        44.1 |       110 |       75 |      43.4 |     43.6 |     34 |  -29 |   97 |  1.06 |         2 |          4 |         24 |       -114 |       -374 |
| c_B14_share_ma20_with_ge4of7        |    2724 |    461 |        85.5 |        23 |       97 |      42.9 |     45.1 |    -74 | -223 |   75 | -0.98 |         1 |          3 |        242 |        148 |        519 |
| c_B14_MSFT_minus_NVDA_60_with       |     844 |   1364 |        38.2 |         3 |       56 |      42.1 |     44.4 |    -53 | -165 |   60 | -0.92 |         0 |          3 |         30 |        -19 |        324 |
| c_B14_MSFT_minus_NVDA_15_with       |    1163 |   2022 |        36.5 |        63 |       17 |      44.3 |     42.6 |     45 |  -53 |  144 |  0.91 |         2 |          3 |         49 |        233 |        -30 |

### B14 sess:0.0 (n=7,525), 6 largest |z|

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_NQ_rich_vs_ES_with_ge1.0      |    2134 |   3809 |        35.9 |       304 |      152 |      47.6 |     45.6 |    152 |   -6 |  309 |  1.89 |         3 |          4 |       -180 |       -385 |         43 |
| c_B14_NQ_rich_vs_ES_with_ge0.5      |    2687 |   3256 |        45.2 |       283 |      144 |      47.5 |     45.4 |    140 |  -13 |  292 |  1.8  |         3 |          4 |        -82 |       -410 |       -174 |
| c_B14_NQ_cheap_vs_ES_with_ge0.5     |    2458 |   3485 |        41.4 |       127 |      263 |      44.8 |     47.4 |   -136 | -289 |   17 | -1.74 |         1 |          4 |         81 |        409 |        335 |
| c_B14_NQ_rich_vs_ES_with_ge1.5      |    1341 |   4602 |        22.6 |       306 |      178 |      47.4 |     46   |    128 |  -48 |  304 |  1.42 |         4 |          4 |       -311 |       -358 |       -434 |
| c_B14_RTY_outperforming_ES_240_with |    2839 |   2476 |        53.4 |       171 |      256 |      45.5 |     47.5 |    -85 | -247 |   78 | -1.02 |         1 |          4 |        250 |        226 |        485 |
| c_B14_NQ_cheap_vs_ES_with_ge1.5     |    1159 |   4784 |        19.5 |       142 |      222 |      45   |     46.6 |    -80 | -268 |  109 | -0.83 |         2 |          4 |        -18 |        256 |       -225 |

### B14 sess:1.0 (n=6,551), 6 largest |z|

| cond                               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_NQ_cheap_vs_ES_with_ge1.0    |    1827 |   4552 |        28.6 |       109 |        5 |      44   |     40.7 |    104 |    5 |  202 |  2.06 |         3 |          4 |        153 |        180 |        549 |
| c_B14_RTY_outperforming_ES_60_with |    3768 |   2604 |        59.1 |         5 |       79 |      40.9 |     42.8 |    -74 | -166 |   17 | -1.59 |         0 |          4 |          1 |        -98 |       -189 |
| c_B14_NQ_cheap_vs_ES_with_ge1.5    |    1104 |   5275 |        17.3 |       107 |       20 |      43.4 |     41.3 |     87 |  -30 |  204 |  1.45 |         3 |          4 |        260 |        403 |        756 |
| c_B14_NQ_cheap_vs_ES_with_ge0.5    |    2488 |   3891 |        39   |        72 |       11 |      43.2 |     40.7 |     61 |  -31 |  152 |  1.3  |         2 |          4 |        -55 |        -50 |        502 |
| c_B14_NQ_rich_vs_ES_with_ge0.5     |    2768 |   3611 |        43.4 |        10 |       54 |      40.5 |     42.5 |    -44 | -134 |   47 | -0.95 |         2 |          4 |        112 |         30 |       -950 |
| c_B14_NQ_rich_vs_ES_with_ge1.0     |    2097 |   4282 |        32.9 |         8 |       48 |      40.4 |     42.3 |    -41 | -137 |   55 | -0.83 |         2 |          4 |        131 |        193 |       -750 |

### B14 sess:3.0 (n=4,926), 6 largest |z|

| cond                               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_avg_corr60_ge0.3             |    1092 |   1005 |        52.1 |       -54 |      119 |      39.5 |     45.7 |   -174 | -289 |  -58 | -2.94 |         0 |          3 |         24 |        124 |        nan |
| c_B14_hl_net_15bars_with_pos       |    2037 |    743 |        73.3 |        81 |      -38 |      43.4 |     39.4 |    119 |    7 |  232 |  2.09 |         3 |          3 |        187 |        112 |        757 |
| c_B14_RTY_outperforming_ES_60_with |    2375 |   2519 |        48.5 |        66 |       -6 |      43.6 |     40.6 |     73 |   -3 |  149 |  1.88 |         3 |          4 |         61 |         63 |        112 |
| c_B14_NVDA_minus_QQQ_15_with       |    1536 |    989 |        60.8 |       -13 |       84 |      41.3 |     44.2 |    -97 | -207 |   13 | -1.73 |         1 |          3 |         25 |       -189 |       -145 |
| c_B14_eq7_minus_QQQ_15_with        |    1417 |   1108 |        56.1 |       -17 |       78 |      41.4 |     43.7 |    -95 | -203 |   13 | -1.73 |         1 |          3 |        144 |        305 |        424 |
| c_B14_avg_corr60_le0.2             |     514 |   1583 |        24.5 |       114 |        1 |      46.1 |     41.2 |    113 |  -22 |  248 |  1.64 |         2 |          3 |         -9 |         12 |       -263 |

### B14 sess:4.0 (n=1,136), 6 largest |z|

| cond                            |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:--------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_avg_corr60_ge0.5          |     269 |    391 |        40.8 |      -110 |      189 |      39.8 |     50.6 |   -299 | -486 | -113 | -3.14 |         0 |          3 |        144 |        nan |        nan |
| c_B14_avg_corr60_ge0.3          |     487 |    173 |        73.8 |       -23 |      321 |      42.9 |     55.5 |   -344 | -561 | -128 | -3.12 |         0 |          2 |       -265 |       -711 |        nan |
| c_B14_share_ma20_with_ge6of7    |     479 |    181 |        72.6 |       -13 |      280 |      43.4 |     53.6 |   -294 | -513 |  -75 | -2.63 |         1 |          3 |       -274 |       -643 |        nan |
| c_B14_share_vwap_with_ge4of7    |     461 |    199 |        69.8 |        23 |      170 |      44.2 |     50.7 |   -146 | -341 |   48 | -1.47 |         1 |          3 |       -175 |        301 |        nan |
| c_B14_largest_minus_QQQ_15_with |     435 |    225 |        65.9 |        21 |      157 |      45.3 |     48   |   -136 | -337 |   66 | -1.32 |         0 |          3 |        -37 |        222 |        nan |
| c_B14_adl_at_extreme_with_ge0.9 |     426 |    234 |        64.6 |        23 |      148 |      44.4 |     49.6 |   -124 | -322 |   73 | -1.23 |         1 |          3 |        -47 |         99 |        nan |

## BLOCK 15 macro, sentiment, positioning (day context): single-condition tables (pooled, per session; stable = same sign in every evaluated year and in L6M)

70 conditions with n>=100 each side, 8 with |z|>2 (chance about 4), 4 of those stable. Largest |z| pooled:

| cond                                     |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_big_yield_day_ge8bp                |    3060 |  17078 |        15.2 |       -70 |      136 |      40.1 |     44.4 |   -206 | -290 | -122 | -4.79 |         0 |          4 |       -236 |       -187 |       -563 |
| c_B15_fed_speech_started_last_90min      |     557 |  19581 |         2.8 |      -189 |      113 |      35.2 |     44   |   -302 | -430 | -174 | -4.64 |         0 |          4 |       -308 |        -66 |        nan |
| c_B15_pc_etp_pct_ge80                    |    3774 |  15520 |        19.6 |         5 |      135 |      42   |     44.1 |   -129 | -207 |  -52 | -3.26 |         1 |          4 |       -220 |       -127 |        -87 |
| c_B15_pc_idx_pct_le20                    |    4581 |  14713 |        23.7 |        26 |      135 |      41.3 |     44.5 |   -109 | -182 |  -36 | -2.94 |         1 |          4 |       -171 |       -107 |        -29 |
| c_B15_fed_speech_within_60min            |     640 |  19498 |         3.2 |       -67 |      111 |      38.9 |     43.9 |   -178 | -313 |  -43 | -2.58 |         1 |          4 |         73 |         87 |       -784 |
| c_B15_yield10_fell_5d_with               |    9894 |  10244 |        49.1 |       146 |       66 |      44.7 |     42.8 |     80 |   18 |  141 |  2.54 |         4 |          4 |         11 |       -249 |       -317 |
| c_B15_pc_tot_pct_le20                    |    4366 |  14928 |        22.6 |        39 |      130 |      41.8 |     44.3 |    -91 | -166 |  -16 | -2.37 |         1 |          4 |        -50 |         -1 |        249 |
| c_B15_skew_pct_ge80                      |    5479 |  14659 |        27.2 |        45 |      128 |      42.8 |     44   |    -83 | -152 |  -14 | -2.35 |         0 |          4 |       -118 |        -58 |        119 |
| c_B15_pc_eq_pct_le20                     |    3916 |  15378 |        20.3 |        47 |      125 |      42.3 |     44.1 |    -79 | -157 |   -1 | -1.97 |         1 |          4 |        -53 |       -371 |        nan |
| c_B15_yield10_fell_prior_day_with        |    9600 |  10538 |        47.7 |       136 |       76 |      44.4 |     43.1 |     60 |   -1 |  122 |  1.92 |         3 |          4 |        -11 |        123 |        114 |
| c_B15_pc_etp_pct_le20                    |    4357 |  14937 |        22.6 |       165 |       93 |      44.6 |     43.5 |     72 |   -4 |  148 |  1.86 |         3 |          4 |        163 |        103 |        221 |
| c_B15_pc_idx_pct_ge80                    |    3044 |  16250 |        15.8 |       179 |       96 |      45.3 |     43.4 |     82 |   -5 |  169 |  1.86 |         2 |          4 |        301 |        413 |        526 |
| c_B15_hy_narrowed_prior_day_with         |    7852 |   9844 |        44.4 |        84 |      143 |      42.5 |     44.6 |    -59 | -125 |    7 | -1.75 |         2 |          4 |        -78 |          2 |          7 |
| c_B15_earn_nvda_report_today_after_close |     245 |  19893 |         1.2 |      -135 |      108 |      38.8 |     43.8 |   -242 | -520 |   35 | -1.71 |         1 |          4 |       -794 |       -519 |        nan |
| c_B15_fed_speaker_today                  |    5495 |  14643 |        27.3 |        63 |      121 |      42.8 |     44.1 |    -57 | -126 |   12 | -1.62 |         0 |          4 |        -56 |        -41 |       -152 |

### B15 sess:0.0 (n=7,525), 6 largest |z|

| cond                                     |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |    lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|------:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_big_yield_day_ge8bp                |    1177 |   6348 |        15.6 |      -114 |      292 |      40.8 |     47.6 |   -406 |  -588 | -225 | -4.39 |         0 |          4 |       -431 |       -377 |       -843 |
| c_B15_pc_etp_pct_le20                    |    1458 |   5834 |        20   |       476 |      174 |      52.1 |     45.2 |    302 |   125 |  479 |  3.34 |         4 |          4 |        265 |        232 |        249 |
| c_B15_fed_chair_speaks_today             |     170 |   7355 |         2.3 |       952 |      212 |      60.6 |     46.2 |    740 |   286 | 1195 |  3.19 |         3 |          3 |        nan |        nan |        nan |
| c_B15_earn_nvda_report_today_after_close |     105 |   7420 |         1.4 |      -578 |      240 |      30.5 |     46.7 |   -818 | -1341 | -296 | -3.07 |         0 |          2 |       -854 |       -236 |        nan |
| c_B15_pc_etp_pct_ge80                    |    1531 |   5761 |        21   |        40 |      286 |      43.2 |     47.5 |   -247 |  -408 |  -85 | -3    |         1 |          4 |       -409 |       -273 |        -92 |
| c_B15_yield10_fell_5d_with               |    3830 |   3695 |        50.9 |       324 |      129 |      48.1 |     44.8 |    196 |    61 |  330 |  2.85 |         4 |          4 |        103 |       -245 |       -449 |

### B15 sess:1.0 (n=6,551), 6 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_pc_tot_pct_le20         |    1441 |   4895 |        22.7 |      -164 |       90 |      36.2 |     42.9 |   -254 | -358 | -149 | -4.76 |         0 |          4 |       -360 |       -403 |       -942 |
| c_B15_cot_am_net_rising_1w    |    3438 |   3113 |        52.5 |       -27 |       88 |      39.6 |     43.4 |   -115 | -203 |  -27 | -2.56 |         1 |          4 |        -52 |       -223 |        nan |
| c_B15_auction_day_5y          |     276 |   6275 |         4.2 |       305 |       15 |      48.6 |     41.1 |    290 |   56 |  524 |  2.43 |         4 |          4 |        532 |       -155 |        432 |
| c_B15_auction_day_3y          |     320 |   6231 |         4.9 |      -200 |       39 |      35.3 |     41.7 |   -238 | -434 |  -43 | -2.4  |         1 |          4 |       -396 |       -174 |        nan |
| c_B15_usd_fell_20d_with_STALE |    3314 |   3237 |        50.6 |        80 |      -27 |      42.9 |     39.8 |    107 |   19 |  195 |  2.39 |         3 |          4 |        136 |        109 |        541 |
| c_B15_pc_idx_pct_le20         |    1509 |   4827 |        23.8 |       -60 |       61 |      38.4 |     42.3 |   -121 | -223 |  -18 | -2.31 |         1 |          4 |        -69 |        -69 |        292 |

### B15 sess:3.0 (n=4,926), 6 largest |z|

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_fed_speech_started_last_90min |     378 |   4548 |         7.7 |      -187 |       48 |      36.5 |     42.6 |   -235 | -370 | -100 | -3.4  |         0 |          4 |         17 |        109 |        nan |
| c_B15_pc_etp_pct_ge80               |     807 |   3791 |        17.5 |      -101 |       56 |      38.4 |     42.6 |   -157 | -259 |  -55 | -3.03 |         0 |          4 |       -124 |       -635 |        nan |
| c_B15_big_yield_day_ge8bp           |     754 |   4172 |        15.3 |       -97 |       53 |      37.5 |     42.9 |   -150 | -251 |  -48 | -2.88 |         0 |          4 |       -486 |       -584 |        nan |
| c_B15_pc_tot_pct_ge80               |     780 |   3818 |        17   |       -83 |       51 |      39.5 |     42.4 |   -134 | -236 |  -32 | -2.58 |         0 |          4 |        176 |        nan |        nan |
| c_B15_pc_idx_pct_ge80               |     774 |   3824 |        16.8 |       -65 |       47 |      39.4 |     42.4 |   -112 | -213 |  -10 | -2.16 |         2 |          4 |        441 |        nan |        nan |
| c_B15_fed_speech_within_60min       |     385 |   4541 |         7.8 |      -106 |       41 |      38.4 |     42.4 |   -148 | -282 |  -13 | -2.15 |         0 |          4 |         64 |        228 |        nan |

### B15 sess:4.0 (n=1,136), 6 largest |z|

| cond                        |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_curve_steepened_ge3bp |     234 |    902 |        20.6 |      -113 |      107 |      41.9 |     46.8 |   -220 | -385 |  -55 | -2.61 |         1 |          4 |       -130 |        nan |        nan |
| c_B15_cot_am_net_pct_le20   |     304 |    832 |        26.8 |       -75 |      112 |      40.8 |     47.6 |   -187 | -342 |  -31 | -2.36 |         0 |          3 |       -395 |       -573 |        nan |
| c_B15_vvix_pct_ge80         |     259 |    877 |        22.8 |       -86 |      106 |      40.2 |     47.4 |   -192 | -361 |  -23 | -2.23 |         0 |          4 |        nan |        nan |        nan |
| c_B15_cor1m_pct_ge80        |     156 |    980 |        13.7 |      -130 |       92 |      38.5 |     46.9 |   -222 | -424 |  -21 | -2.16 |         0 |          3 |        nan |        nan |        nan |
| c_B15_pc_eq_pct_ge80        |     213 |    855 |        19.9 |       -88 |       99 |      37.6 |     47.8 |   -187 | -369 |   -5 | -2.01 |         0 |          4 |        -80 |        nan |        nan |
| c_B15_vix_pct_ge80          |     215 |    921 |        18.9 |       -83 |       96 |      40   |     47.1 |   -178 | -357 |    0 | -1.96 |         0 |          3 |        nan |        nan |        nan |

## Quotes only (nothing bought): data for Blocks 14-15 that is not on the box (Databento get_cost, 2026-11-15)

| item | full 2023-04..2026-11 | L6M |
|--|--|--|
| Nasdaq closing/opening imbalance (XNAS.ITCH imbalance) QQQ + 7 megacaps, the 15:50 publication data | $6.42 (0.43 GB) | $0.97 |
| same, QQQ only | $0.80 | $0.12 |
| SPY imbalance (XNYS.PILLAR) | $0.00 returned (not covered) | $0.00 |
| HYG LQD TLT IEF 1-minute bars (DBEQ.BASIC) = credit/bond proxies | $4.50 | $0.58 |
| SMH XLK IGV SOXX 1-minute bars (DBEQ.BASIC) = semis/software ETFs | $3.25 | $0.57 |

Nasdaq-100 component bars: W-CH3 quotes in DS3_DEEPEN_OUTSIDE.md (not bought).

Needs a paid feed, not built: economic surprise index (Citi/Bloomberg consensus, paid), MOVE index (ICE, paid; ZN realized-vol proxy built instead), DXY (paid; 6E and FRED broad dollar used), Cboe daily market statistics older than 2023-04 not needed. Free sources used: Treasury, FRED, Cboe csv and daily JSON, CFTC public reporting, TreasuryDirect, SEC EDGAR, federalreserve.gov.

## Skipped signals (not taken by the live stack): the same conditions on the hypothetical outcome (1-minute bars, entry-table outcome_type hyp1m), lift in R (units of risk), not $


### ALL_skipped (n=173,490; mean R = nan typical), 10 largest |z|

| cond               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |   z |   yrs_pos |   yrs_eval |
|:-------------------|--------:|-------:|------------:|----------:|---------:|-------:|----:|----------:|-----------:|
| c_F_rvol5_ge0.8    |  121865 |  51174 |        70.4 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.0    |   91230 |  81809 |        52.7 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.3    |   54916 | 118123 |        31.7 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.6    |   33798 | 139241 |        19.5 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge2.0    |   18750 | 154289 |        10.8 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge0.8   |  122714 |  50325 |        70.9 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.0   |   86791 |  86248 |        50.2 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.3   |   46862 | 126177 |        27.1 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.6   |   26016 | 147023 |        15   |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_volrise5_ge1.0 |   91834 |  81205 |        53.1 |       nan |      nan |    nan | nan |         0 |          4 |

### reason:SCR_gate (n=14,295; mean R = nan typical), 10 largest |z|

| cond               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |   z |   yrs_pos |   yrs_eval |
|:-------------------|--------:|-------:|------------:|----------:|---------:|-------:|----:|----------:|-----------:|
| c_F_rvol5_ge0.8    |   11513 |   2646 |        81.3 |       nan |      nan |    nan | nan |         0 |          3 |
| c_F_rvol5_ge1.0    |    8929 |   5230 |        63.1 |       nan |      nan |    nan | nan |         0 |          3 |
| c_F_rvol5_ge1.3    |    5378 |   8781 |        38   |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.6    |    3253 |  10906 |        23   |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge2.0    |    1734 |  12425 |        12.2 |       nan |      nan |    nan | nan |         1 |          3 |
| c_F_rvol15_ge0.8   |   11778 |   2381 |        83.2 |       nan |      nan |    nan | nan |         0 |          3 |
| c_F_rvol15_ge1.0   |    8807 |   5352 |        62.2 |       nan |      nan |    nan | nan |         0 |          3 |
| c_F_rvol15_ge1.3   |    4915 |   9244 |        34.7 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.6   |    2624 |  11535 |        18.5 |       nan |      nan |    nan | nan |         0 |          3 |
| c_F_volrise5_ge1.0 |    7285 |   6874 |        51.4 |       nan |      nan |    nan | nan |         1 |          4 |

### reason:dayHalt (n=7,595; mean R = nan typical), 10 largest |z|

| cond               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |   z |   yrs_pos |   yrs_eval |
|:-------------------|--------:|-------:|------------:|----------:|---------:|-------:|----:|----------:|-----------:|
| c_F_rvol5_ge0.8    |    5722 |   1813 |        75.9 |       nan |      nan |    nan | nan |         1 |          4 |
| c_F_rvol5_ge1.0    |    4320 |   3215 |        57.3 |       nan |      nan |    nan | nan |         1 |          4 |
| c_F_rvol5_ge1.3    |    2584 |   4951 |        34.3 |       nan |      nan |    nan | nan |         1 |          4 |
| c_F_rvol5_ge1.6    |    1646 |   5889 |        21.8 |       nan |      nan |    nan | nan |         1 |          4 |
| c_F_rvol5_ge2.0    |     925 |   6610 |        12.3 |       nan |      nan |    nan | nan |         2 |          4 |
| c_F_rvol15_ge0.8   |    5876 |   1659 |        78   |       nan |      nan |    nan | nan |         1 |          4 |
| c_F_rvol15_ge1.0   |    4300 |   3235 |        57.1 |       nan |      nan |    nan | nan |         1 |          4 |
| c_F_rvol15_ge1.3   |    2410 |   5125 |        32   |       nan |      nan |    nan | nan |         2 |          4 |
| c_F_rvol15_ge1.6   |    1442 |   6093 |        19.1 |       nan |      nan |    nan | nan |         2 |          4 |
| c_F_volrise5_ge1.0 |    3810 |   3725 |        50.6 |       nan |      nan |    nan | nan |         0 |          4 |

### reason:inTrade (n=92,672; mean R = nan typical), 10 largest |z|

| cond               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |   z |   yrs_pos |   yrs_eval |
|:-------------------|--------:|-------:|------------:|----------:|---------:|-------:|----:|----------:|-----------:|
| c_F_rvol5_ge0.8    |   59898 |  32688 |        64.7 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.0    |   43574 |  49012 |        47.1 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.3    |   25223 |  67363 |        27.2 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.6    |   15004 |  77582 |        16.2 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge2.0    |    8000 |  84586 |         8.6 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge0.8   |   59525 |  33061 |        64.3 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.0   |   39939 |  52647 |        43.1 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.3   |   20093 |  72493 |        21.7 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.6   |   10548 |  82038 |        11.4 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_volrise5_ge1.0 |   50218 |  42368 |        54.2 |       nan |      nan |    nan | nan |         0 |          4 |

### reason:other (n=8,289; mean R = nan typical), 10 largest |z|

| cond               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |   z |   yrs_pos |   yrs_eval |
|:-------------------|--------:|-------:|------------:|----------:|---------:|-------:|----:|----------:|-----------:|
| c_F_rvol5_ge0.8    |    5917 |   2372 |        71.4 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.0    |    4232 |   4057 |        51.1 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.3    |    2429 |   5860 |        29.3 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.6    |    1454 |   6835 |        17.5 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge2.0    |     806 |   7483 |         9.7 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge0.8   |    6290 |   1999 |        75.9 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.0   |    4543 |   3746 |        54.8 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.3   |    2591 |   5698 |        31.3 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.6   |    1503 |   6786 |        18.1 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_volrise5_ge1.0 |    3364 |   4925 |        40.6 |       nan |      nan |    nan | nan |         0 |          4 |

### reason:session_lots_0 (n=34,987; mean R = nan typical), 10 largest |z|

| cond               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |   z |   yrs_pos |   yrs_eval |
|:-------------------|--------:|-------:|------------:|----------:|---------:|-------:|----:|----------:|-----------:|
| c_F_rvol5_ge0.8    |   26763 |   8176 |        76.6 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.0    |   21554 |  13385 |        61.7 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.3    |   14639 |  20300 |        41.9 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.6    |    9765 |  25174 |        28   |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge2.0    |    5834 |  29105 |        16.7 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge0.8   |   26956 |   7983 |        77.1 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.0   |   20730 |  14209 |        59.3 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.3   |   12614 |  22325 |        36.1 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.6   |    7662 |  27277 |        21.9 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_volrise5_ge1.0 |   18417 |  16522 |        52.7 |       nan |      nan |    nan | nan |         0 |          4 |

### reason:timeBlocked (n=15,652; mean R = nan typical), 10 largest |z|

| cond               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |   z |   yrs_pos |   yrs_eval |
|:-------------------|--------:|-------:|------------:|----------:|---------:|-------:|----:|----------:|-----------:|
| c_F_rvol5_ge0.8    |   12052 |   3479 |        77.6 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.0    |    8621 |   6910 |        55.5 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.3    |    4663 |  10868 |        30   |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge1.6    |    2676 |  12855 |        17.2 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol5_ge2.0    |    1451 |  14080 |         9.3 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge0.8   |   12289 |   3242 |        79.1 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.0   |    8472 |   7059 |        54.6 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.3   |    4239 |  11292 |        27.3 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_rvol15_ge1.6   |    2237 |  13294 |        14.4 |       nan |      nan |    nan | nan |         0 |          4 |
| c_F_volrise5_ge1.0 |    8740 |   6791 |        56.3 |       nan |      nan |    nan | nan |         0 |          4 |
