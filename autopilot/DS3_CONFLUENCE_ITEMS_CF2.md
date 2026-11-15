# DS3_CONFLUENCE_ITEMS_CF2 (W-CF2): each condition of categories F, G, H, I, J and Block 5 alone (STEP 3)
VERDICT: 786 conditions measured alone on 19,798 taken JN05W2 trades; 116 have |z|>2 in the pooled cell (chance alone gives about 39); 72 of those have the same sign in every year and in L6M; no condition is a lead on this table alone (a lead needs the step 5 proofs, W-CF3); the map is below. No PASS claim.

Basis: net $ per trade at base lots, engine fee $1.18/contract (pnl in the entry table; the FEES.md $4.84 basis lowers each trade by lots x $3.66 x sides, a difference between yes and no groups only through their lot mix), taken trades only until the skipped-signal rows land. Lift = mean $ when the condition is yes minus when it is no (95% CI Welch). `share_yes` over entries where the condition could be computed. Years: 2023..2026; L6M = 2026-05..10, L3M = 2026-08..10, L1M = 2026-10 (cap 2026-10-31). Cells: ALL, per book (K7 M7 U7 P7 H7 A7 O7), per session (0 Asia, 1 London, 3 NY, 4 close), book x session. Full table (26,724 rows): /mnt/l2/l2vast/_confl/cols_cf2/step3_ALL.csv. Multiple-testing note: 22,456 (cell, condition) tests with n>=50 each side; at 5% about 1,122 will show |z|>2 by chance, so cell-level tops below are a map, not leads.

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
| B15 macro, sentiment, positioning     |           70 |          10 |                4 |
| B5 indicator states on other markets  |          257 |          44 |               31 |
| F tape                                |           50 |           3 |                2 |
| G order book L2                       |           49 |           1 |                0 |
| H order by order L3                   |           53 |          14 |                9 |
| H2 drift-robust L3                    |           38 |          13 |                9 |
| I intermarket                         |           72 |           6 |                4 |
| J options/positioning                 |          148 |          21 |               11 |

## Pooled ALL cell: 30 largest |z| (n_yes, n_no >= 100)

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_fed_speech_started_last_90min |     554 |  19244 |         2.8 |      -205 |      115 |      35   |     44   |   -320 | -444 | -196 | -5.04 |         0 |          4 |       -308 |        -66 |        nan |
| c_B15_big_yield_day_ge8bp           |    2948 |  16850 |        14.9 |       -80 |      138 |      39.9 |     44.4 |   -218 | -303 | -133 | -5.02 |         0 |          4 |       -236 |       -187 |       -563 |
| c_I_ratio_trend240_pos              |   12916 |   4620 |        73.6 |       121 |       -8 |      44.2 |     41.3 |    129 |   62 |  197 |  3.76 |         4 |          4 |         98 |        163 |         40 |
| c_B5_NQ_5m_sqz_mom_with             |   15025 |   4772 |        75.9 |       135 |       14 |      44.4 |     41.9 |    121 |   57 |  185 |  3.73 |         3 |          4 |        170 |        280 |        183 |
| c_B14_avg_corr60_ge0.3              |    1575 |   1172 |        57.3 |       -46 |      143 |      40.4 |     46.9 |   -189 | -290 |  -89 | -3.69 |         0 |          3 |        -27 |       -158 |        nan |
| c_B5_ALL_1m_sqz_fired_dir_ge3of4    |     160 |  19637 |         0.8 |      -293 |      109 |      30.6 |     43.9 |   -402 | -618 | -185 | -3.64 |         0 |          4 |       -314 |        nan |        nan |
| c_B5_NQ_15m_hold21_with             |   11088 |   8273 |        57.3 |       154 |       43 |      44.4 |     42.9 |    111 |   49 |  172 |  3.53 |         4 |          4 |        145 |        233 |        246 |
| c_H2_arrival_imb60_lo               |    3861 |  15924 |        19.5 |       222 |       78 |      46.1 |     43.2 |    144 |   62 |  226 |  3.44 |         4 |          4 |        249 |        184 |        -73 |
| c_H_spoof_ahead60_ge1               |    6373 |  13425 |        32.2 |        34 |      140 |      42.4 |     44.4 |   -106 | -168 |  -45 | -3.38 |         1 |          4 |       -546 |       -741 |       -560 |
| c_J_nowall_ahead25_SPX_vol          |   11866 |   1035 |        92   |       141 |      -95 |      43.9 |     40   |    236 |   99 |  374 |  3.37 |         3 |          3 |        254 |          1 |         75 |
| c_B5_NQ_5m_supertrend_with          |   16171 |   3626 |        81.7 |       122 |       32 |      43.9 |     43.2 |     91 |   38 |  144 |  3.36 |         4 |          4 |        144 |        172 |         93 |
| c_H2_spoof_ahead60_lo               |   13416 |   6369 |        67.8 |       140 |       35 |      44.4 |     42.5 |    105 |   43 |  166 |  3.34 |         3 |          4 |        546 |        741 |        560 |
| c_B5_ES_5m_hold21_with              |   13613 |   6184 |        68.8 |       138 |       35 |      44.6 |     42   |    103 |   42 |  164 |  3.31 |         4 |          4 |         24 |         77 |        -18 |
| c_B5_NQ_5m_adx_di_with              |   12136 |   7661 |        61.3 |       145 |       43 |      44.4 |     42.7 |    102 |   41 |  162 |  3.3  |         4 |          4 |         99 |        242 |        203 |
| c_B5_NQ_5m_ema_stack_with           |   13706 |   6091 |        69.2 |       137 |       36 |      44.4 |     42.3 |    101 |   39 |  163 |  3.22 |         4 |          4 |        160 |        292 |        458 |
| c_B15_pc_etp_pct_ge80               |    3752 |  15202 |        19.8 |         9 |      135 |      42.1 |     44.2 |   -126 | -204 |  -48 | -3.18 |         1 |          4 |       -220 |       -127 |        -87 |
| c_F_ice_with5_ge1                   |    7960 |  11838 |        40.2 |        50 |      144 |      43.4 |     44   |    -94 | -152 |  -35 | -3.12 |         0 |          4 |       -137 |       -113 |       -122 |
| c_B5_NQ_5m_sqz_on                   |    3929 |  15868 |        19.8 |        26 |      126 |      41.6 |     44.3 |    -99 | -163 |  -36 | -3.07 |         0 |          4 |       -100 |       -119 |        -47 |
| c_B5_ES_5m_sqz_mom_with             |   14540 |   5257 |        73.4 |       132 |       34 |      44.3 |     42.3 |     98 |   35 |  160 |  3.07 |         3 |          4 |         85 |        218 |          8 |
| c_B5_NQ_5m_hold21_with              |   14351 |   5446 |        72.5 |       132 |       36 |      44.5 |     41.8 |     97 |   35 |  159 |  3.06 |         4 |          4 |        150 |        268 |        246 |
| c_J_0dte_flip_far50_Nh_vol          |    3660 |   1033 |        78   |       133 |      -80 |      44.1 |     39.4 |    212 |   75 |  350 |  3.03 |         3 |          3 |         74 |         44 |        143 |
| c_B5_NQ_5m_rsi_with                 |   17616 |   2181 |        89   |       122 |      -20 |      44   |     41.6 |    142 |   49 |  234 |  3    |         4 |          4 |         52 |        289 |        223 |
| c_B15_pc_idx_pct_le20               |    4581 |  14373 |        24.2 |        26 |      137 |      41.3 |     44.6 |   -111 | -184 |  -38 | -2.98 |         1 |          4 |       -171 |       -107 |        -29 |
| c_B5_NQ_1m_adx_di_with              |   13686 |   6111 |        69.1 |       137 |       36 |      44.5 |     42   |    101 |   35 |  168 |  2.98 |         4 |          4 |         22 |         99 |        231 |
| c_B5_RTY_15m_supertrend_with        |   11090 |   8271 |        57.3 |       147 |       52 |      44.4 |     42.9 |     95 |   32 |  157 |  2.95 |         4 |          4 |         95 |        216 |        485 |
| c_B5_ES_15m_rsi_with                |   14056 |   5305 |        72.6 |       133 |       36 |      44.3 |     42.3 |     97 |   33 |  162 |  2.95 |         4 |          4 |         99 |        107 |        169 |
| c_H_spoof_ahead300_ge1              |    9509 |  10289 |        48   |        58 |      150 |      43   |     44.5 |    -92 | -154 |  -31 | -2.95 |         0 |          4 |       -227 |       -195 |       -230 |
| c_B15_fed_speech_within_60min       |     633 |  19165 |         3.2 |       -88 |      112 |      38.6 |     43.9 |   -200 | -334 |  -67 | -2.94 |         0 |          4 |         73 |         87 |       -784 |
| c_B5_RTY_1m_macd_with               |   12915 |   6875 |        65.3 |        70 |      174 |      43.4 |     44.5 |   -103 | -172 |  -34 | -2.93 |         0 |          4 |        -90 |        -66 |        201 |
| c_J_beyond_flip_SPX_vol             |    7680 |   5221 |        59.5 |       169 |       54 |      44.9 |     41.7 |    115 |   38 |  192 |  2.93 |         2 |          3 |        195 |        307 |        505 |

## Pooled ALL cell: stable conditions (same sign in every evaluated year and in L6M), 25 largest |z|

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_fed_speech_started_last_90min |     554 |  19244 |         2.8 |      -205 |      115 |      35   |     44   |   -320 | -444 | -196 | -5.04 |         0 |          4 |       -308 |        -66 |        nan |
| c_B15_big_yield_day_ge8bp           |    2948 |  16850 |        14.9 |       -80 |      138 |      39.9 |     44.4 |   -218 | -303 | -133 | -5.02 |         0 |          4 |       -236 |       -187 |       -563 |
| c_I_ratio_trend240_pos              |   12916 |   4620 |        73.6 |       121 |       -8 |      44.2 |     41.3 |    129 |   62 |  197 |  3.76 |         4 |          4 |         98 |        163 |         40 |
| c_B14_avg_corr60_ge0.3              |    1575 |   1172 |        57.3 |       -46 |      143 |      40.4 |     46.9 |   -189 | -290 |  -89 | -3.69 |         0 |          3 |        -27 |       -158 |        nan |
| c_B5_ALL_1m_sqz_fired_dir_ge3of4    |     160 |  19637 |         0.8 |      -293 |      109 |      30.6 |     43.9 |   -402 | -618 | -185 | -3.64 |         0 |          4 |       -314 |        nan |        nan |
| c_B5_NQ_15m_hold21_with             |   11088 |   8273 |        57.3 |       154 |       43 |      44.4 |     42.9 |    111 |   49 |  172 |  3.53 |         4 |          4 |        145 |        233 |        246 |
| c_H2_arrival_imb60_lo               |    3861 |  15924 |        19.5 |       222 |       78 |      46.1 |     43.2 |    144 |   62 |  226 |  3.44 |         4 |          4 |        249 |        184 |        -73 |
| c_J_nowall_ahead25_SPX_vol          |   11866 |   1035 |        92   |       141 |      -95 |      43.9 |     40   |    236 |   99 |  374 |  3.37 |         3 |          3 |        254 |          1 |         75 |
| c_B5_NQ_5m_supertrend_with          |   16171 |   3626 |        81.7 |       122 |       32 |      43.9 |     43.2 |     91 |   38 |  144 |  3.36 |         4 |          4 |        144 |        172 |         93 |
| c_B5_ES_5m_hold21_with              |   13613 |   6184 |        68.8 |       138 |       35 |      44.6 |     42   |    103 |   42 |  164 |  3.31 |         4 |          4 |         24 |         77 |        -18 |
| c_B5_NQ_5m_adx_di_with              |   12136 |   7661 |        61.3 |       145 |       43 |      44.4 |     42.7 |    102 |   41 |  162 |  3.3  |         4 |          4 |         99 |        242 |        203 |
| c_B5_NQ_5m_ema_stack_with           |   13706 |   6091 |        69.2 |       137 |       36 |      44.4 |     42.3 |    101 |   39 |  163 |  3.22 |         4 |          4 |        160 |        292 |        458 |
| c_F_ice_with5_ge1                   |    7960 |  11838 |        40.2 |        50 |      144 |      43.4 |     44   |    -94 | -152 |  -35 | -3.12 |         0 |          4 |       -137 |       -113 |       -122 |
| c_B5_NQ_5m_sqz_on                   |    3929 |  15868 |        19.8 |        26 |      126 |      41.6 |     44.3 |    -99 | -163 |  -36 | -3.07 |         0 |          4 |       -100 |       -119 |        -47 |
| c_B5_NQ_5m_hold21_with              |   14351 |   5446 |        72.5 |       132 |       36 |      44.5 |     41.8 |     97 |   35 |  159 |  3.06 |         4 |          4 |        150 |        268 |        246 |
| c_J_0dte_flip_far50_Nh_vol          |    3660 |   1033 |        78   |       133 |      -80 |      44.1 |     39.4 |    212 |   75 |  350 |  3.03 |         3 |          3 |         74 |         44 |        143 |
| c_B5_NQ_5m_rsi_with                 |   17616 |   2181 |        89   |       122 |      -20 |      44   |     41.6 |    142 |   49 |  234 |  3    |         4 |          4 |         52 |        289 |        223 |
| c_B5_NQ_1m_adx_di_with              |   13686 |   6111 |        69.1 |       137 |       36 |      44.5 |     42   |    101 |   35 |  168 |  2.98 |         4 |          4 |         22 |         99 |        231 |
| c_B5_RTY_15m_supertrend_with        |   11090 |   8271 |        57.3 |       147 |       52 |      44.4 |     42.9 |     95 |   32 |  157 |  2.95 |         4 |          4 |         95 |        216 |        485 |
| c_B5_ES_15m_rsi_with                |   14056 |   5305 |        72.6 |       133 |       36 |      44.3 |     42.3 |     97 |   33 |  162 |  2.95 |         4 |          4 |         99 |        107 |        169 |
| c_H_spoof_ahead300_ge1              |    9509 |  10289 |        48   |        58 |      150 |      43   |     44.5 |    -92 | -154 |  -31 | -2.95 |         0 |          4 |       -227 |       -195 |       -230 |
| c_B5_RTY_1m_macd_with               |   12915 |   6875 |        65.3 |        70 |      174 |      43.4 |     44.5 |   -103 | -172 |  -34 | -2.93 |         0 |          4 |        -90 |        -66 |        201 |
| c_B5_RTY_15m_rsi_with               |   12869 |   6492 |        66.5 |       137 |       45 |      44.2 |     42.8 |     93 |   29 |  156 |  2.86 |         4 |          4 |         99 |        196 |        352 |
| c_B5_NQ_15m_cci_with                |   14646 |   4715 |        75.6 |       129 |       37 |      44.2 |     42.5 |     92 |   29 |  155 |  2.86 |         4 |          4 |        174 |        239 |        381 |
| c_B5_ES_5m_cci_with                 |   16381 |   3416 |        82.7 |       125 |       12 |      44.2 |     41.8 |    113 |   33 |  193 |  2.78 |         4 |          4 |         30 |         89 |        -20 |

## Recent windows: |lift| in L3M with same sign as the full sample and as L6M (pooled, n_yes and n_no in L3M >= 40)

| cond                                     |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_J_0dte_pw0_not_ahead25_Nh_vol          |    4433 |    319 |        93.3 |        66 |      353 |      42.6 |     48.9 |   -286 | -526 |  -47 | -2.34 |         1 |          3 |       -457 |      -1057 |       -538 |
| c_B15_earn_big5_report_today_after_close |     977 |  18821 |         4.9 |        50 |      109 |      42.7 |     43.8 |    -59 | -203 |   85 | -0.8  |         2 |          4 |       -410 |       -636 |       -590 |
| c_H_no_aged_big_ahead                    |   18599 |   1199 |        93.9 |        96 |      261 |      43.4 |     49.5 |   -165 | -291 |  -39 | -2.57 |         1 |          4 |       -484 |       -632 |      -1085 |
| c_J_0dte_pw0_not_ahead50_Nh_vol          |    4145 |    607 |        87.2 |        68 |      203 |      42.6 |     46.3 |   -135 | -314 |   44 | -1.48 |         1 |          3 |       -330 |       -626 |       -779 |
| c_B15_earn_any_report_today_after_close  |    1737 |  18061 |         8.8 |        32 |      113 |      42.6 |     43.9 |    -81 | -191 |   29 | -1.44 |         2 |          4 |       -530 |       -588 |       -557 |
| c_J_wall_behind50_Nd_oi                  |     928 |   8773 |         9.6 |       132 |       82 |      44.8 |     42.6 |     50 |  -97 |  197 |  0.67 |         2 |          3 |         30 |        570 |        620 |
| c_J_0dte_flip_far25_Nh_oi                |    4261 |    381 |        91.8 |        99 |       29 |      43.4 |     39.9 |     70 | -161 |  300 |  0.59 |         3 |          3 |        565 |        566 |        nan |
| c_J_0dte_pw0_not_ahead50_Nd_oi           |    4436 |    324 |        93.2 |        78 |       73 |      42.6 |     45.1 |      5 | -228 |  237 |  0.04 |         2 |          3 |        321 |        492 |        857 |
| c_H2_bmax_ahead_lo                       |   17700 |   2085 |        89.5 |        95 |      198 |      43.2 |     48.6 |   -104 | -197 |  -11 | -2.18 |         0 |          4 |       -193 |       -485 |      -1092 |
| c_H2_bmax_ahead_hi                       |    1929 |  17856 |         9.8 |       189 |       97 |      48.2 |     43.3 |     92 |   -4 |  188 |  1.88 |         4 |          4 |        193 |        485 |       1092 |
| c_H_no_big10_ahead                       |   17709 |   2089 |        89.4 |        95 |      198 |      43.2 |     48.6 |   -103 | -196 |  -10 | -2.17 |         0 |          4 |       -193 |       -485 |      -1092 |
| c_J_tide_npp_s15_neg                     |    2323 |    858 |        73   |        30 |       29 |      42.7 |     44.1 |      1 | -106 |  109 |  0.03 |         2 |          3 |        159 |        479 |        122 |
| c_J_wall_behind25_NDX_oi                 |     749 |  12136 |         5.8 |       -32 |      134 |      41.8 |     43.7 |   -166 | -328 |   -3 | -2    |         0 |          3 |       -438 |       -446 |       -276 |
| c_J_gex_pos_NDX_oi                       |    2826 |    548 |        83.8 |        52 |       29 |      43   |     42   |     23 |  -98 |  144 |  0.37 |         2 |          3 |        307 |        430 |        687 |
| c_B14_NQ_rich_vs_QQQ_with_ge0.5          |    2543 |    863 |        74.7 |        52 |       47 |      43   |     42.8 |      5 |  -94 |  105 |  0.1  |         2 |          3 |        328 |        414 |        130 |
| c_J_tide_npp_s_neg                       |    2303 |   1130 |        67.1 |        68 |       10 |      43.3 |     41.9 |     57 |  -34 |  148 |  1.24 |         3 |          3 |        244 |        408 |        273 |
| c_J_0dte_pw0_not_ahead25_Nd_vol          |    4712 |    263 |        94.7 |        68 |      155 |      42.6 |     44.1 |    -87 | -363 |  188 | -0.62 |         2 |          3 |       -311 |       -407 |       -869 |
| c_B5_ES_15m_sqz_fired_dir_with           |    1513 |  17848 |         7.8 |        43 |      112 |      44.1 |     43.7 |    -69 | -192 |   54 | -1.1  |         1 |          4 |       -400 |       -403 |       -482 |
| c_J_0dte_cw0_not_ahead50_Nd_oi           |    4444 |    316 |        93.4 |        83 |        2 |      43   |     39.9 |     81 | -168 |  330 |  0.64 |         2 |          3 |        337 |        372 |        882 |
| c_B15_pc_eq_pct_le20                     |    3874 |  15080 |        20.4 |        45 |      127 |      42.3 |     44.1 |    -82 | -160 |   -3 | -2.03 |         1 |          4 |        -53 |       -371 |        nan |

## Per session (cells sess:0..4), 8 largest |z| each with n_yes,n_no >= 100


### sess:0 (n=7,299)

| cond                         |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_big_yield_day_ge8bp    |    1101 |   6198 |        15.1 |      -150 |      300 |      40.2 |     47.8 |   -450 | -637 | -263 | -4.72 |         0 |          4 |       -431 |       -377 |       -843 |
| c_B5_NQ_5m_supertrend_with   |    6087 |   1211 |        83.4 |       271 |       36 |      47.3 |     43   |    235 |  123 |  347 |  4.13 |         4 |          4 |        246 |        292 |         97 |
| c_B5_NQ_5m_adx_di_with       |    4298 |   3000 |        58.9 |       345 |       71 |      48.7 |     43.7 |    274 |  141 |  408 |  4.03 |         4 |          4 |        103 |        308 |        251 |
| c_B5_NQ_5m_sqz_mom_with      |    5463 |   1835 |        74.9 |       303 |       21 |      47.9 |     42.7 |    282 |  139 |  425 |  3.86 |         4 |          4 |        191 |        325 |        218 |
| c_B5_NQ_15m_hold21_with      |    4189 |   2673 |        61   |       342 |       84 |      48.3 |     44.3 |    258 |  116 |  399 |  3.57 |         3 |          4 |        328 |        347 |        312 |
| c_B5_RTY_15m_supertrend_with |    3833 |   3029 |        55.9 |       355 |       99 |      48.4 |     44.7 |    256 |  113 |  400 |  3.5  |         4 |          4 |        306 |        497 |        826 |
| c_B5_NQ_15m_adx_di_with      |    3016 |   3846 |        44   |       377 |      136 |      48.8 |     45.1 |    242 |   94 |  389 |  3.2  |         4 |          4 |        270 |        276 |        215 |
| c_B15_pc_etp_pct_le20        |    1424 |   5642 |        20.2 |       472 |      180 |      52.1 |     45.4 |    292 |  112 |  472 |  3.18 |         4 |          4 |        265 |        232 |        249 |

### sess:1 (n=6,452)

| cond                       |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:---------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_pc_tot_pct_le20      |    1422 |   4815 |        22.8 |      -166 |       95 |      36.2 |     43   |   -261 | -366 | -156 | -4.87 |         0 |          4 |       -360 |       -403 |       -942 |
| c_B5_ALL_15m_adx_di_ge3of4 |    1904 |   4548 |        29.5 |       -89 |       80 |      37.7 |     43.1 |   -169 | -267 |  -71 | -3.39 |         0 |          4 |       -197 |        -57 |        215 |
| c_I_ZN_with60              |    2427 |   2792 |        46.5 |       102 |      -47 |      43.5 |     39.6 |    149 |   50 |  248 |  2.94 |         4 |          4 |        189 |        456 |        304 |
| c_B5_YM_15m_adx_di_with    |    2659 |   3793 |        41.2 |       -45 |       83 |      39.3 |     43.1 |   -128 | -218 |  -37 | -2.77 |         0 |          4 |        -59 |        -18 |        500 |
| c_G_imb1_ge0.35            |     475 |   5977 |         7.4 |      -188 |       48 |      36.8 |     41.9 |   -235 | -412 |  -59 | -2.61 |         0 |          4 |       -594 |       -412 |         75 |
| c_J_em_frac_pos_Nd         |    2401 |   1352 |        64   |       -10 |      148 |      40.2 |     43.4 |   -158 | -276 |  -39 | -2.6  |         1 |          3 |       -109 |       -173 |        138 |
| c_B5_ES_1m_sqz_mom_with    |    4768 |   1684 |        73.9 |        -6 |      133 |      41.2 |     42.5 |   -139 | -244 |  -34 | -2.6  |         0 |          4 |        -84 |       -216 |       -132 |
| c_H_big10_mine_present     |     257 |   6195 |         4   |       329 |       18 |      48.6 |     41.2 |    311 |   73 |  549 |  2.56 |         4 |          4 |        772 |        925 |        nan |

### sess:3 (n=4,911)

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B5_RTY_15m_macd_rising_with |    2838 |   2073 |        57.8 |        99 |      -71 |      44.7 |     38.3 |    170 |   93 |  247 |  4.33 |         4 |          4 |        140 |        172 |        476 |
| c_B5_ES_1m_hold21_with        |    3541 |   1370 |        72.1 |        83 |     -116 |      43.3 |     38.7 |    198 |  107 |  290 |  4.26 |         3 |          4 |        216 |        342 |        635 |
| c_G_no_wall_ahead4_lt15       |    4515 |    396 |        91.9 |         3 |      307 |      40.8 |     55.6 |   -304 | -445 | -164 | -4.24 |         0 |          4 |        nan |        nan |        nan |
| c_H2_bmax_ahead_lo            |    4172 |    733 |        85.1 |        -5 |      221 |      40.6 |     50.5 |   -226 | -334 | -118 | -4.09 |         0 |          4 |        -37 |       -248 |        nan |
| c_H_no_big10_ahead            |    4176 |    735 |        85   |        -6 |      217 |      40.5 |     50.3 |   -223 | -331 | -115 | -4.05 |         0 |          4 |        -37 |       -248 |        nan |
| c_H2_bmax_ahead_hi            |     669 |   4236 |        13.6 |       214 |       -1 |      50.1 |     40.8 |    215 |  103 |  327 |  3.76 |         4 |          4 |         37 |        248 |        nan |
| c_G_no_wall_ahead40_lt15      |    3701 |   1210 |        75.4 |       -12 |      149 |      40.1 |     47.9 |   -162 | -250 |  -73 | -3.6  |         1 |          4 |        104 |         14 |        nan |
| c_G_no_wall_ahead10_lt15      |    3701 |   1210 |        75.4 |       -12 |      149 |      40.1 |     47.9 |   -162 | -250 |  -73 | -3.6  |         1 |          4 |        104 |         14 |        nan |

### sess:4 (n=1,136)

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


### book:A7 (n=1,156)

| cond                  |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_ctr_mine_lt10_300 |     597 |    559 |        51.6 |       218 |        5 |      57.4 |     46.5 |    214 |   83 |  344 |  3.21 |         3 |          3 |        111 |        432 |        554 |
| c_H2_ctr_mine300_hi   |     180 |    975 |        15.6 |      -127 |      158 |      40.6 |     54.3 |   -285 | -460 | -110 | -3.19 |         0 |          4 |       -123 |        -46 |       -227 |
| c_H2_ctr_mine60_hi    |     226 |    929 |        19.6 |       -96 |      165 |      42.5 |     54.5 |   -261 | -424 |  -98 | -3.13 |         0 |          4 |       -102 |       -231 |       -457 |
| c_J_em_used_lt0.5_Nh  |     504 |    148 |        77.3 |        17 |      339 |      47.6 |     61.5 |   -322 | -525 | -119 | -3.11 |         0 |          2 |       -358 |       -489 |       -820 |
| c_B15_pc_etp_pct_le20 |     229 |    897 |        20.3 |       314 |       67 |      61.6 |     49.8 |    247 |   84 |  409 |  2.98 |         4 |          4 |        140 |        -65 |       -313 |
| c_J_em_room_ge150_Nh  |     526 |    126 |        80.7 |        31 |      337 |      48.1 |     61.9 |   -306 | -523 |  -90 | -2.77 |         0 |          3 |       -419 |       -629 |       -848 |

### book:H7 (n=1,048)

| cond                              |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_F_big10_noagainst15             |     355 |    693 |        33.9 |       471 |       -2 |      52.7 |     45.6 |    474 |  188 |  759 |  3.25 |         3 |          4 |        154 |         12 |        nan |
| c_H2_touch_mine_sz_hi             |     154 |    893 |        14.7 |      -239 |      230 |      42.2 |     49   |   -469 | -763 | -174 | -3.12 |         0 |          4 |       -144 |       -120 |        nan |
| c_H_mine_touch_ge5                |     107 |    941 |        10.2 |      -277 |      208 |      43.9 |     48.5 |   -485 | -840 | -130 | -2.68 |         0 |          3 |        nan |        nan |        nan |
| c_B14_NQ_rich_vs_ES_with_ge1.5    |     221 |    739 |        23   |       422 |       40 |      51.6 |     46.7 |    382 |   71 |  693 |  2.41 |         4 |          4 |          1 |       -594 |        nan |
| c_B15_yield10_fell_prior_day_with |     522 |    526 |        49.8 |       317 |        1 |      51   |     45.1 |    316 |   56 |  576 |  2.38 |         3 |          4 |       -311 |       -106 |       -335 |
| c_B14_NQ_rich_vs_ES_with_ge0.5    |     435 |    525 |        45.3 |       295 |      -10 |      50.1 |     45.9 |    305 |   38 |  572 |  2.24 |         3 |          4 |        320 |       -363 |        nan |

### book:K7 (n=7,078)

| cond                      |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:--------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B5_NQ_5m_sqz_on         |    1732 |   5345 |        24.5 |       -25 |       79 |      40.9 |     44.7 |   -104 | -163 |  -44 | -3.42 |         0 |          4 |       -129 |       -130 |       -344 |
| c_B5_NQ_5m_sqz_mom_with   |    4515 |   2562 |        63.8 |        87 |       -5 |      45   |     41.6 |     92 |   35 |  148 |  3.18 |         3 |          4 |        172 |        211 |        266 |
| c_H_touch_ratio_ge2.0     |    1738 |   5340 |        24.6 |       132 |       28 |      46.6 |     42.8 |    104 |   38 |  170 |  3.09 |         3 |          4 |         91 |          4 |        -52 |
| c_B15_big_yield_day_ge8bp |    1008 |   6070 |        14.2 |       -54 |       72 |      40.3 |     44.3 |   -126 | -207 |  -45 | -3.05 |         0 |          4 |       -185 |       -197 |       -432 |
| c_B5_NQ_5m_hold21_with    |    4231 |   2846 |        59.8 |        89 |        2 |      45.1 |     41.8 |     87 |   31 |  143 |  3.04 |         4 |          4 |        133 |        180 |        245 |
| c_I_NQ_leads_RTY5         |    5082 |   1968 |        72.1 |        80 |      -17 |      44.6 |     41.4 |     97 |   34 |  160 |  3.02 |         4 |          4 |         76 |       -114 |         96 |

### book:M7 (n=3,985)

| cond                       |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:---------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_G_no_wall_ahead4_lt15    |    3797 |    188 |        95.3 |        -1 |      307 |      40.9 |     56.9 |   -308 | -480 | -137 | -3.52 |         0 |          4 |        nan |        nan |        nan |
| c_G_imb5_ge0.1             |    1045 |   2940 |        26.2 |       -93 |       51 |      37.5 |     43.2 |   -144 | -230 |  -57 | -3.27 |         0 |          4 |        -52 |         85 |        -25 |
| c_I_ZN_with60              |    1497 |   1751 |        46.1 |        75 |      -49 |      44.4 |     39   |    125 |   40 |  210 |  2.89 |         4 |          4 |        151 |        383 |        273 |
| c_B5_ES_1m_supertrend_with |    3338 |    647 |        83.8 |       -13 |      150 |      40.9 |     46.1 |   -163 | -274 |  -52 | -2.88 |         0 |          4 |       -123 |       -222 |         -3 |
| c_G_imb1_ge0.35            |     378 |   3607 |         9.5 |      -143 |       30 |      37.3 |     42.2 |   -172 | -299 |  -46 | -2.68 |         0 |          4 |       -345 |       -145 |       -226 |
| c_B15_auction_day_5y       |     165 |   3820 |         4.1 |       271 |        2 |      50.3 |     41.3 |    269 |   67 |  472 |  2.6  |         4 |          4 |        252 |        -24 |        536 |

### book:O7 (n=452)

| cond                        |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B5_YM_5m_hold21_with      |     133 |    319 |        29.4 |       -58 |      274 |      26.3 |     42   |   -331 | -554 | -108 | -2.91 |         0 |          4 |       -262 |        nan |        nan |
| c_B5_YM_1m_ema_stack_with   |     214 |    238 |        47.3 |        12 |      324 |      29.9 |     44.1 |   -312 | -522 | -101 | -2.91 |         0 |          4 |       -498 |        nan |        nan |
| c_B5_YM_1m_sqz_mom_with     |     229 |    223 |        50.7 |        28 |      328 |      31.4 |     43.5 |   -299 | -510 |  -89 | -2.78 |         0 |          4 |       -656 |      -1055 |        nan |
| c_I_NKD_with5               |     243 |    209 |        53.8 |        37 |      338 |      32.5 |     43.1 |   -300 | -513 |  -87 | -2.76 |         0 |          4 |       -220 |        nan |        nan |
| c_H_arrival_imb30_pos       |     164 |    288 |        36.3 |       -12 |      283 |      29.9 |     41.7 |   -296 | -508 |  -83 | -2.72 |         1 |          4 |       -286 |        nan |        nan |
| c_B5_YM_5m_macd_rising_with |     242 |    210 |        53.5 |        50 |      321 |      32.2 |     43.3 |   -271 | -483 |  -58 | -2.5  |         0 |          4 |       -881 |      -1056 |        nan |

### book:P7 (n=4,748)

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |    lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|------:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_fed_speech_started_last_90min |     108 |   4640 |         2.3 |      -604 |      215 |      25.9 |     41.2 |   -819 | -1248 | -390 | -3.74 |         0 |          4 |       -801 |        nan |        nan |
| c_B15_big_yield_day_ge8bp           |     716 |   4032 |        15.1 |      -163 |      260 |      37.3 |     41.5 |   -423 |  -696 | -151 | -3.05 |         0 |          4 |       -325 |        -62 |      -1233 |
| c_B5_NQ_15m_hold21_with             |    3118 |   1597 |        66.1 |       302 |       -3 |      41.4 |     39.9 |    305 |   103 |  507 |  2.97 |         4 |          4 |        450 |        663 |        911 |
| c_J_tide_nv_s_pos                   |     403 |    151 |        72.7 |        94 |     -424 |      41.2 |     29.8 |    518 |   149 |  887 |  2.75 |         3 |          3 |        644 |        330 |        nan |
| c_H2_aggr20_with300_hi              |     682 |   4062 |        14.4 |       -41 |      236 |      38.7 |     41.3 |   -277 |  -480 |  -73 | -2.66 |         1 |          4 |       -219 |       -255 |        171 |
| c_H_spoof_ahead60_ge1               |    1407 |   3341 |        29.6 |         9 |      276 |      38.2 |     42   |   -266 |  -470 |  -63 | -2.56 |         1 |          4 |      -1967 |        nan |        nan |

### book:U7 (n=1,331)

| cond                        |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |    lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|------:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B5_ES_5m_sqz_mom_with     |    1218 |    113 |        91.5 |       316 |     -301 |      52.7 |     39.8 |    617 |   144 | 1090 |  2.56 |         4 |          4 |       1189 |       2154 |        nan |
| c_B15_pc_idx_pct_le20       |     309 |    961 |        24.3 |      -112 |      409 |      46   |     53.7 |   -521 |  -932 | -110 | -2.48 |         1 |          4 |       -210 |       -206 |        nan |
| c_I_NQ_leads_RTY15          |     903 |    366 |        71.2 |       395 |     -101 |      53.6 |     46.4 |    496 |   103 |  889 |  2.47 |         3 |          4 |        970 |       1883 |        nan |
| c_H_arrival_imb30_pos       |     764 |    567 |        57.4 |        74 |      518 |      49.6 |     54.3 |   -444 |  -796 |  -92 | -2.47 |         1 |          4 |       -333 |       -542 |       -448 |
| c_J_nowall_ahead100_SPX_vol |     625 |    214 |        74.5 |       443 |     -156 |      53.3 |     46.3 |    599 |    97 | 1100 |  2.34 |         3 |          3 |        306 |         85 |        nan |
| c_B5_MEGA_1m_adx_di_with    |     208 |    100 |        67.5 |        30 |      909 |      46.6 |     60   |   -879 | -1637 | -120 | -2.27 |         0 |          2 |       -220 |        173 |        nan |

## H (L3) items: MBO months only; pooled and strata

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H2_arrival_imb60_lo         |    3861 |  15924 |        19.5 |       222 |       78 |      46.1 |     43.2 |    144 |   62 |  226 |  3.44 |         4 |          4 |        249 |        184 |        -73 |
| c_H_spoof_ahead60_ge1         |    6373 |  13425 |        32.2 |        34 |      140 |      42.4 |     44.4 |   -106 | -168 |  -45 | -3.38 |         1 |          4 |       -546 |       -741 |       -560 |
| c_H2_spoof_ahead60_lo         |   13416 |   6369 |        67.8 |       140 |       35 |      44.4 |     42.5 |    105 |   43 |  166 |  3.34 |         3 |          4 |        546 |        741 |        560 |
| c_H_spoof_ahead300_ge1        |    9509 |  10289 |        48   |        58 |      150 |      43   |     44.5 |    -92 | -154 |  -31 | -2.95 |         0 |          4 |       -227 |       -195 |       -230 |
| c_H2_ctr_mine300_lo           |    3372 |  16413 |        17   |       213 |       84 |      47.4 |     43   |    129 |   38 |  220 |  2.77 |         4 |          4 |         99 |        284 |        563 |
| c_H2_spoof_ahead300_lo        |   10444 |   9341 |        52.8 |       146 |       61 |      44.4 |     43   |     85 |   24 |  146 |  2.73 |         4 |          4 |        227 |        195 |        230 |
| c_H2_ctr_mine60_hi            |    3868 |  15917 |        19.6 |        12 |      128 |      40.7 |     44.5 |   -116 | -201 |  -32 | -2.72 |         0 |          4 |        -97 |       -242 |       -334 |
| c_H2_spoof_ahead60_hi         |    3638 |  16147 |        18.4 |        33 |      122 |      42.8 |     44   |    -89 | -155 |  -22 | -2.61 |         0 |          4 |       -546 |       -741 |       -560 |
| c_H_gmax_against60_lt10       |   10693 |   9105 |        54   |       142 |       63 |      44   |     43.5 |     79 |   19 |  139 |  2.57 |         4 |          4 |         86 |         92 |        -18 |
| c_H_no_aged_big_ahead         |   18599 |   1199 |        93.9 |        96 |      261 |      43.4 |     49.5 |   -165 | -291 |  -39 | -2.57 |         1 |          4 |       -484 |       -632 |      -1085 |
| c_H_aggr50_with300_ge1        |    5828 |  13970 |        29.4 |        54 |      128 |      42.9 |     44.1 |    -74 | -132 |  -16 | -2.52 |         0 |          4 |       -177 |       -188 |       -274 |
| c_H_arrival_imb60_pos         |   12870 |   6928 |        65   |        77 |      159 |      43.1 |     45   |    -82 | -146 |  -17 | -2.48 |         0 |          4 |       -201 |        -88 |        135 |
| c_H_gmax_with60_ge10          |   12415 |   7383 |        62.7 |        74 |      159 |      43.3 |     44.5 |    -85 | -154 |  -17 | -2.44 |         0 |          4 |        -12 |        109 |        143 |
| c_H2_aggr20_with300_hi        |    4770 |  15015 |        24.1 |        54 |      122 |      43.2 |     43.9 |    -68 | -123 |  -12 | -2.4  |         0 |          4 |        -94 |       -125 |       -135 |
| c_H2_ctr_ahead60_hi           |    4122 |  15663 |        20.8 |        32 |      125 |      41.6 |     44.4 |    -93 | -169 |  -16 | -2.37 |         0 |          4 |         19 |       -162 |       -220 |
| c_H2_ctr_mine60_lo            |    3620 |  16165 |        18.3 |       188 |       87 |      47.2 |     43   |    100 |   17 |  184 |  2.36 |         4 |          4 |        212 |        266 |        487 |
| c_H_aggr50_with60_ge1         |    2629 |  17169 |        13.3 |        35 |      117 |      42.7 |     43.9 |    -81 | -150 |  -12 | -2.31 |         1 |          4 |        -51 |         17 |        -59 |
| c_H_arrival_imb30_pos         |   12023 |   7775 |        60.7 |        77 |      151 |      43.4 |     44.3 |    -75 | -138 |  -11 | -2.3  |         1 |          4 |          8 |          2 |        194 |
| c_H2_spoof_ahead300_hi        |    4372 |  15413 |        22.1 |        49 |      122 |      42.8 |     44   |    -73 | -136 |  -10 | -2.28 |         0 |          4 |       -170 |       -195 |       -230 |
| c_H_aggr50_with_gt_against300 |    4583 |  15215 |        23.2 |        52 |      122 |      43   |     44   |    -70 | -131 |  -10 | -2.27 |         0 |          4 |       -107 |        -87 |       -180 |
| c_H_no_spoof_mine300          |   10547 |   9251 |        53.3 |       138 |       69 |      44.2 |     43.3 |     70 |    9 |  131 |  2.24 |         3 |          4 |        167 |        282 |        368 |
| c_H2_bmax_ahead_lo            |   17700 |   2085 |        89.5 |        95 |      198 |      43.2 |     48.6 |   -104 | -197 |  -11 | -2.18 |         0 |          4 |       -193 |       -485 |      -1092 |
| c_H_no_big10_ahead            |   17709 |   2089 |        89.4 |        95 |      198 |      43.2 |     48.6 |   -103 | -196 |  -10 | -2.17 |         0 |          4 |       -193 |       -485 |      -1092 |
| c_H_sweep3_with60_ge1         |   15287 |   4511 |        77.2 |        85 |      176 |      43.1 |     46.1 |    -91 | -173 |   -8 | -2.15 |         0 |          4 |       -111 |         36 |        522 |
| c_H2_ctr_ahead300_hi          |    4103 |  15682 |        20.7 |        41 |      123 |      40.4 |     44.6 |    -82 | -159 |   -5 | -2.1  |         1 |          4 |        -40 |       -108 |       -257 |

### H items in stratum lvl:ahead<=10pts(level close ahead) (n=12,346), 12 largest |z|

| cond                    |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_spoof_ahead60_ge1   |    3977 |   8369 |        32.2 |        12 |      138 |      41.8 |     44.5 |   -127 | -206 |  -47 | -3.12 |         1 |          4 |       -691 |       -919 |        nan |
| c_H2_spoof_ahead60_lo   |    8364 |   3973 |        67.8 |       138 |       13 |      44.5 |     41.9 |    125 |   46 |  205 |  3.08 |         3 |          4 |        691 |        919 |        nan |
| c_H2_aggr20_with300_hi  |    2799 |   9538 |        22.7 |        21 |      120 |      42.4 |     44   |    -99 | -170 |  -29 | -2.76 |         1 |          4 |       -280 |       -294 |       -702 |
| c_H_spoof_ahead300_ge1  |    5973 |   6373 |        48.4 |        41 |      151 |      42.6 |     44.6 |   -110 | -190 |  -31 | -2.72 |         1 |          4 |       -313 |       -304 |       -736 |
| c_H_ahead_touch_le2     |    8975 |   3371 |        72.7 |       129 |       15 |      43.8 |     43   |    114 |   29 |  199 |  2.63 |         4 |          4 |        183 |        346 |       1143 |
| c_H_aggr50_with60_ge1   |    1547 |  10799 |        12.5 |        -7 |      112 |      41.4 |     43.9 |   -119 | -209 |  -30 | -2.61 |         0 |          4 |       -100 |         57 |       -299 |
| c_H2_spoof_ahead300_lo  |    6481 |   5856 |        52.5 |       146 |       44 |      44.5 |     42.7 |    102 |   23 |  182 |  2.53 |         3 |          4 |        313 |        304 |        736 |
| c_H_gmax_against60_lt10 |    6996 |   5350 |        56.7 |       140 |       43 |      44.2 |     42.9 |     97 |   20 |  174 |  2.47 |         4 |          4 |         93 |         52 |         -8 |
| c_H_arrival_imb30_pos   |    7430 |   4916 |        60.2 |        56 |      160 |      43   |     44.5 |   -103 | -186 |  -21 | -2.47 |         1 |          4 |        -37 |        -45 |        271 |
| c_H2_arrival_imb60_lo   |    2495 |   9842 |        20.2 |       201 |       71 |      46.2 |     43   |    130 |   25 |  236 |  2.42 |         4 |          4 |        200 |        181 |       -286 |
| c_H2_touch_mine_sz_hi   |    1376 |  10961 |        11.2 |       -17 |      112 |      42.5 |     43.8 |   -129 | -239 |  -19 | -2.3  |         2 |          4 |       -272 |       -384 |       -485 |
| c_H_arrival_imb60_pos   |    7952 |   4394 |        64.4 |        63 |      160 |      42.9 |     45   |    -96 | -180 |  -13 | -2.27 |         1 |          4 |       -168 |       -112 |        176 |

### H items in stratum lvl:ahead<=20pts (n=16,903), 12 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_spoof_ahead60_ge1         |    5473 |  11430 |        32.4 |        11 |      135 |      41.6 |     44.1 |   -124 | -191 |  -57 | -3.63 |         1 |          4 |       -488 |       -898 |        nan |
| c_H2_spoof_ahead60_lo         |   11423 |   5469 |        67.6 |       135 |       11 |      44.1 |     41.7 |    123 |   56 |  190 |  3.6  |         3 |          4 |        488 |        898 |        nan |
| c_H2_arrival_imb60_lo         |    3335 |  13557 |        19.7 |       206 |       67 |      45.9 |     42.7 |    139 |   50 |  228 |  3.06 |         4 |          4 |        234 |        205 |        -84 |
| c_H_spoof_ahead300_ge1        |    8177 |   8726 |        48.4 |        41 |      145 |      42.4 |     44.1 |   -104 | -171 |  -37 | -3.03 |         1 |          4 |       -128 |       -239 |       -517 |
| c_H_aggr50_with300_ge1        |    4821 |  12082 |        28.5 |        29 |      121 |      41.9 |     43.9 |    -91 | -154 |  -29 | -2.86 |         0 |          4 |       -253 |       -265 |       -325 |
| c_H2_spoof_ahead300_lo        |    8861 |   8031 |        52.5 |       140 |       44 |      44.1 |     42.4 |     96 |   29 |  163 |  2.82 |         3 |          4 |        128 |        239 |        517 |
| c_H2_ctr_mine300_lo           |    2916 |  13976 |        17.3 |       212 |       70 |      46.9 |     42.6 |    142 |   42 |  242 |  2.78 |         4 |          4 |        133 |        252 |        494 |
| c_H2_aggr20_with300_hi        |    3954 |  12938 |        23.4 |        32 |      114 |      42.4 |     43.6 |    -82 | -142 |  -23 | -2.7  |         1 |          4 |       -142 |       -196 |       -262 |
| c_H_gmax_with60_ge10          |   10343 |   6560 |        61.2 |        56 |      156 |      42.5 |     44.5 |   -100 | -174 |  -27 | -2.67 |         0 |          4 |         38 |        107 |        259 |
| c_H_aggr50_with_gt_against300 |    3775 |  13128 |        22.3 |        25 |      114 |      42   |     43.7 |    -89 | -156 |  -23 | -2.64 |         0 |          4 |       -164 |       -148 |       -185 |
| c_H2_spoof_ahead60_hi         |    3100 |  13792 |        18.4 |        18 |      112 |      42   |     43.6 |    -94 | -166 |  -22 | -2.56 |         1 |          4 |       -488 |       -898 |        nan |
| c_H_arrival_imb30_pos         |   10239 |   6664 |        60.6 |        59 |      149 |      42.7 |     44.2 |    -89 | -158 |  -20 | -2.53 |         1 |          4 |        -19 |        -54 |        125 |

### H items in stratum lvl:behind<=3pts(at a level) (n=4,312), 12 largest |z|

| cond                        |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:----------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_no_aged_big_ahead       |    4003 |    309 |        92.8 |        98 |      418 |      44.2 |     51.8 |   -320 | -574 |  -65 | -2.46 |         0 |          4 |         -8 |        nan |        nan |
| c_H2_bmax_ahead_lo          |    3806 |    502 |        88.4 |        93 |      326 |      43.8 |     51.6 |   -233 | -426 |  -40 | -2.36 |         0 |          4 |       -254 |        -49 |        nan |
| c_H_no_big10_ahead          |    3809 |    503 |        88.3 |        94 |      323 |      43.8 |     51.5 |   -229 | -422 |  -36 | -2.33 |         0 |          4 |       -254 |        -49 |        nan |
| c_H_arrival_imb30_pos       |    2580 |   1732 |        59.8 |        58 |      214 |      44.3 |     45.3 |   -156 | -295 |  -17 | -2.2  |         0 |          4 |       -174 |        235 |        573 |
| c_H2_bmax_ahead_hi          |     453 |   3855 |        10.5 |       286 |      100 |      50.3 |     44.1 |    186 |  -15 |  387 |  1.82 |         4 |          4 |        254 |         49 |        nan |
| c_H2_spoof_mine_gt_ahead300 |     900 |   3412 |        20.9 |        14 |      149 |      42.6 |     45.3 |   -136 | -289 |   18 | -1.73 |         2 |          4 |        -81 |        -94 |        nan |
| c_H_touch_ratio_ge1.0       |    2883 |   1429 |        66.9 |        81 |      201 |      43.7 |     46.8 |   -119 | -263 |   24 | -1.63 |         0 |          4 |       -386 |       -185 |       -881 |
| c_H2_gmax_with60_lo         |    1035 |   3273 |        24   |       233 |       84 |      46.5 |     44.2 |    148 |  -30 |  327 |  1.63 |         3 |          4 |        -64 |       -545 |       -311 |
| c_H_sweep3_with60_ge1       |    3003 |   1309 |        69.6 |        80 |      213 |      43.3 |     48   |   -133 | -294 |   28 | -1.62 |         0 |          4 |       -118 |        104 |        795 |
| c_H2_touch_mine_sz_hi       |     482 |   3826 |        11.2 |        -9 |      136 |      42.3 |     45   |   -145 | -330 |   40 | -1.54 |         1 |          4 |        -15 |       -106 |        362 |
| c_H_sweep3_with300_ge1      |    3955 |    357 |        91.7 |       140 |      -92 |      44.8 |     43.7 |    232 |  -82 |  546 |  1.45 |         3 |          4 |        nan |        nan |        nan |
| c_H2_spoof_ahead_gt_mine300 |    1267 |   3045 |        29.4 |       194 |       90 |      46.7 |     43.9 |    104 |  -39 |  246 |  1.42 |         2 |          4 |       -467 |         77 |        nan |

### H items in stratum lvl:behind<=5&ahead>=20 (n=1,154), 12 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_touch_ratio_ge1.0         |     805 |    349 |        69.8 |        73 |      411 |      45.1 |     51.6 |   -338 | -583 |  -93 | -2.7  |         0 |          4 |       -419 |       -303 |        nan |
| c_H_ctr_mine_lt10_300         |     529 |    625 |        45.8 |       329 |       45 |      51.8 |     43   |    284 |   52 |  517 |  2.39 |         1 |          3 |        -45 |         55 |        nan |
| c_H_no_aged_big_ahead         |    1078 |     76 |        93.4 |       141 |      653 |      46   |     61.8 |   -512 | -941 |  -82 | -2.33 |         0 |          3 |        nan |        nan |        nan |
| c_H2_touch_ahead_sz_lo        |     578 |    574 |        50.2 |        40 |      300 |      44.1 |     49.8 |   -260 | -493 |  -27 | -2.18 |         1 |          4 |       -311 |       -421 |        nan |
| c_H2_spoof_mine300_hi         |     259 |    893 |        22.5 |       -10 |      222 |      46   |     47.3 |   -232 | -477 |   14 | -1.85 |         0 |          4 |       -641 |       -561 |        nan |
| c_H_arrival_imb60_ge0.1       |     242 |    912 |        21   |       392 |      117 |      52.5 |     45.6 |    274 |  -39 |  587 |  1.72 |         4 |          4 |        -95 |       -275 |       -310 |
| c_H_aggr50_with_gt_against300 |     280 |    874 |        24.3 |       320 |      128 |      51.8 |     45.5 |    192 |  -50 |  434 |  1.55 |         1 |          4 |        580 |        575 |         61 |
| c_H2_spoof_mine_gt_ahead300   |     251 |    903 |        21.8 |        19 |      218 |      45.4 |     47.5 |   -199 | -454 |   56 | -1.53 |         1 |          4 |       -411 |        nan |        nan |
| c_H_no_big10_ahead            |    1026 |    128 |        88.9 |       146 |      403 |      45.8 |     57   |   -256 | -588 |   76 | -1.51 |         1 |          4 |        -51 |        nan |        nan |
| c_H_no_big20_ahead            |    1110 |     44 |        96.2 |       161 |      532 |      46.3 |     65.9 |   -372 | -885 |  142 | -1.42 |         1 |          1 |        nan |        nan |        nan |
| c_H2_touch_mine_sz_hi         |     142 |   1010 |        12.3 |       -43 |      200 |      46.5 |     47   |   -242 | -585 |  100 | -1.39 |         1 |          4 |        -74 |        430 |        nan |
| c_H_no_refill_ahead300        |    1061 |     93 |        91.9 |       190 |       -1 |      47.4 |     43   |    192 |  -84 |  468 |  1.36 |         3 |          4 |       -259 |        nan |        nan |

### H items in stratum lvl:behind<=5pts (n=7,606), 12 largest |z|

| cond                    |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H2_spoof_ahead300_hi  |    1518 |   6080 |        20   |        15 |      138 |      42.9 |     44.7 |   -123 | -225 |  -22 | -2.38 |         1 |          4 |       -443 |        -72 |       -634 |
| c_H_touch_ratio_ge1.0   |    5174 |   2432 |        68   |        76 |      198 |      43.3 |     46.5 |   -122 | -230 |  -14 | -2.21 |         0 |          4 |       -311 |       -213 |       -503 |
| c_H_no_aged_big_ahead   |    7056 |    550 |        92.8 |       100 |      310 |      43.8 |     51.4 |   -210 | -405 |  -15 | -2.11 |         0 |          4 |        272 |        804 |        nan |
| c_H_no_aggr50_against60 |    7267 |    339 |        95.5 |       123 |      -52 |      44.6 |     38.9 |    175 |   12 |  337 |  2.1  |         3 |          4 |        287 |       -553 |        nan |
| c_H2_spoof_ahead60_hi   |    1289 |   6309 |        17   |        25 |      132 |      43   |     44.6 |   -107 | -214 |   -1 | -1.97 |         2 |          4 |       -689 |        nan |        nan |
| c_H2_touch_mine_sz_hi   |     863 |   6735 |        11.4 |       -11 |      130 |      41.8 |     44.6 |   -140 | -281 |    0 | -1.96 |         1 |          4 |       -135 |       -199 |        625 |
| c_H_refill_mine300_ge1  |     357 |   7249 |         4.7 |       -27 |      122 |      40.1 |     44.5 |   -149 | -309 |   11 | -1.82 |         0 |          4 |       -129 |       -190 |        nan |
| c_H_no_big10_ahead      |    6720 |    886 |        88.4 |        99 |      234 |      43.4 |     51.1 |   -134 | -282 |   13 | -1.79 |         1 |          4 |        114 |        468 |       -231 |
| c_H_gmax_against60_lt25 |    6543 |   1063 |        86   |       129 |       31 |      44.5 |     43.2 |     98 |  -10 |  206 |  1.78 |         3 |          4 |       -102 |       -476 |        -24 |
| c_H2_aggr20_with300_hi  |    1615 |   5983 |        21.3 |        50 |      131 |      43.3 |     44.6 |    -80 | -170 |    9 | -1.76 |         1 |          4 |       -149 |        128 |       -364 |
| c_H2_bmax_ahead_lo      |    6714 |    884 |        88.4 |        98 |      230 |      43.4 |     51.1 |   -132 | -279 |   16 | -1.75 |         1 |          4 |        114 |        468 |       -231 |
| c_H2_ctr_mine60_lo      |    1581 |   6017 |        20.8 |       205 |       90 |      47   |     43.6 |    116 |  -16 |  247 |  1.72 |         3 |          4 |        366 |        230 |         78 |

### H items in stratum lvl:behind>5 (n=12,192), 12 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H2_arrival_imb60_lo         |    2299 |   9888 |        18.9 |       260 |       64 |      46.6 |     42.7 |    196 |   90 |  301 |  3.64 |         4 |          4 |        245 |        348 |        172 |
| c_H2_spoof_ahead60_lo         |    8183 |   4004 |        67.2 |       140 |       21 |      44   |     42.3 |    118 |   40 |  196 |  2.98 |         4 |          4 |        502 |        739 |        nan |
| c_H_spoof_ahead60_ge1         |    4006 |   8186 |        32.9 |        21 |      139 |      42.3 |     44   |   -118 | -196 |  -40 | -2.98 |         0 |          4 |       -502 |       -739 |        nan |
| c_H_spoof_ahead300_ge1        |    5918 |   6274 |        48.5 |        40 |      157 |      42.6 |     44.1 |   -116 | -194 |  -39 | -2.95 |         0 |          4 |       -158 |       -254 |        -67 |
| c_H2_spoof_ahead300_lo        |    6355 |   5832 |        52.2 |       154 |       42 |      44.2 |     42.6 |    112 |   35 |  190 |  2.85 |         4 |          4 |        158 |        254 |         67 |
| c_H_arrival_imb60_pos         |    7952 |   4240 |        65.2 |        62 |      172 |      42.5 |     45.1 |   -110 | -192 |  -29 | -2.64 |         0 |          4 |       -214 |       -150 |        -19 |
| c_H_aggr50_with300_ge1        |    3810 |   8382 |        31.2 |        37 |      129 |      42.6 |     43.8 |    -92 | -164 |  -19 | -2.48 |         1 |          4 |       -219 |       -254 |       -336 |
| c_H2_ctr_mine300_lo           |    1831 |  10356 |        15   |       232 |       77 |      47.8 |     42.6 |    154 |   32 |  277 |  2.47 |         4 |          4 |         15 |        128 |        706 |
| c_H2_spoof_ahead_gt_mine60    |    2573 |   9619 |        21.1 |        16 |      122 |      41.7 |     43.8 |   -106 | -194 |  -18 | -2.37 |         2 |          4 |       -662 |       -727 |        nan |
| c_H2_ctr_ahead300_hi          |    2694 |   9493 |        22.1 |        12 |      126 |      39.4 |     44.6 |   -114 | -210 |  -18 | -2.33 |         1 |          4 |       -103 |       -288 |       -354 |
| c_H_aggr50_with_gt_against300 |    2993 |   9199 |        24.6 |        32 |      122 |      42.8 |     43.6 |    -91 | -167 |  -14 | -2.33 |         0 |          4 |       -136 |       -112 |       -218 |
| c_H_no_spoof_mine300          |    6362 |   5830 |        52.2 |       143 |       53 |      43.8 |     43   |     90 |   13 |  167 |  2.29 |         3 |          4 |        126 |        342 |        376 |

### H items in stratum lvl:cluster_behind_10 (n=12,752), 12 largest |z|

| cond                    |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_H_spoof_ahead60_ge1   |    4469 |   8283 |        35   |        26 |      171 |      42.3 |     45.1 |   -145 | -219 |  -71 | -3.85 |         0 |          4 |       -882 |      -1134 |        nan |
| c_H2_spoof_ahead60_lo   |    8275 |   4465 |        65   |       170 |       27 |      45.1 |     42.4 |    143 |   69 |  217 |  3.79 |         4 |          4 |        882 |       1134 |        nan |
| c_H_gmax_against60_lt10 |    6786 |   5966 |        53.2 |       181 |       52 |      44.8 |     43.3 |    129 |   55 |  202 |  3.42 |         3 |          4 |        144 |        145 |         44 |
| c_H2_arrival_imb60_lo   |    2492 |  10248 |        19.6 |       255 |       87 |      47.3 |     43.4 |    167 |   67 |  267 |  3.28 |         4 |          4 |        404 |        233 |        -11 |
| c_H_arrival_imb30_pos   |    7651 |   5101 |        60   |        71 |      195 |      43.2 |     45.4 |   -124 | -202 |  -47 | -3.16 |         0 |          4 |       -201 |       -109 |         89 |
| c_H_no_aged_big_ahead   |   11832 |    920 |        92.8 |       105 |      322 |      43.6 |     50.9 |   -217 | -361 |  -73 | -2.96 |         1 |          4 |       -167 |       -178 |       -890 |
| c_H_arrival_imb60_pos   |    8234 |   4518 |        64.6 |        81 |      193 |      43.1 |     45.9 |   -112 | -190 |  -33 | -2.8  |         0 |          4 |       -264 |        -98 |        -11 |
| c_H2_spoof_ahead300_hi  |    3059 |   9681 |        24   |        43 |      144 |      43.3 |     44.4 |   -101 | -175 |  -27 | -2.66 |         0 |          4 |       -324 |       -348 |       -570 |
| c_H_spoof_ahead300_ge1  |    6551 |   6201 |        51.4 |        71 |      173 |      43.5 |     44.8 |   -101 | -177 |  -25 | -2.62 |         0 |          4 |       -338 |       -348 |       -570 |
| c_H2_spoof_ahead300_lo  |    6297 |   6443 |        49.4 |       170 |       71 |      44.7 |     43.5 |     99 |   23 |  175 |  2.57 |         4 |          4 |        338 |        348 |        570 |
| c_H2_ctr_mine300_hi     |    2750 |   9990 |        21.6 |        27 |      146 |      40.6 |     45.1 |   -119 | -211 |  -27 | -2.54 |         0 |          4 |          3 |        -89 |       -380 |
| c_H_no_spoof_mine60     |    8629 |   4123 |        67.7 |       152 |       56 |      44.7 |     42.9 |     96 |   22 |  170 |  2.54 |         3 |          4 |        227 |        137 |       -446 |

### Year-by-year for the spoof-like items and the five largest pooled H items (lift in $/trade, yes minus no; n_yes shown)


`c_H_spoof_ahead60_ge1`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |    6373 |  13425 |   -106 | -3.38 |           1 |         -97 |         -76 |        -246 |       -546 |
| sess:0                              |    1327 |   5972 |   -166 | -1.82 |         180 |        -196 |        -116 |        -470 |      -1330 |
| sess:1                              |    1483 |   4969 |     15 |  0.28 |         149 |          88 |         -23 |         -64 |       -610 |
| sess:3                              |    2945 |   1966 |    -82 | -2.08 |        -100 |        -153 |         -13 |        -100 |       -355 |
| sess:4                              |     618 |    518 |     14 |  0.19 |         134 |         174 |          70 |        -374 |        -98 |
| lvl:behind<=3pts(at a level)        |    1333 |   2979 |    -43 | -0.63 |         232 |        -176 |         -52 |        -184 |       -778 |
| lvl:behind<=5pts                    |    2367 |   5239 |    -86 | -1.67 |          38 |        -112 |         -72 |        -320 |       -689 |
| lvl:ahead<=10pts(level close ahead) |    3977 |   8369 |   -127 | -3.12 |          21 |         -95 |         -79 |        -302 |       -691 |
| lvl:ahead<=20pts                    |    5473 |  11430 |   -124 | -3.63 |          21 |        -131 |         -76 |        -276 |       -488 |
| lvl:cluster_behind_10               |    4469 |   8283 |   -145 | -3.85 |         -65 |        -174 |        -118 |        -223 |       -882 |
| lvl:behind<=5&ahead>=20             |     349 |    805 |      7 |  0.06 |         -99 |         -78 |        -301 |        -208 |       -969 |
| lvl:behind>5                        |    4006 |   8186 |   -118 | -2.98 |         -29 |         -67 |         -80 |        -218 |       -502 |

`c_H_spoof_ahead300_ge1`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |    9509 |  10289 |    -92 | -2.95 |         -16 |          -9 |        -156 |        -110 |       -227 |
| sess:0                              |    2355 |   4944 |    -67 | -0.9  |         333 |          41 |        -229 |        -217 |       -363 |
| sess:1                              |    2533 |   3919 |    -58 | -1.25 |        -164 |         -27 |         -99 |          16 |       -166 |
| sess:3                              |    3793 |   1118 |    -20 | -0.44 |        -750 |         264 |         -33 |         -18 |       -238 |
| sess:4                              |     828 |    308 |    -62 | -0.76 |         nan |         181 |         -45 |        -215 |         35 |
| lvl:behind<=3pts(at a level)        |    2039 |   2273 |      0 |  0    |         333 |         -19 |        -197 |         -92 |       -532 |
| lvl:behind<=5pts                    |    3591 |   4015 |    -53 | -1.03 |         152 |          61 |        -268 |        -150 |       -428 |
| lvl:ahead<=10pts(level close ahead) |    5973 |   6373 |   -110 | -2.72 |          26 |          -6 |        -137 |        -162 |       -313 |
| lvl:ahead<=20pts                    |    8177 |   8726 |   -104 | -3.03 |           3 |         -35 |        -151 |        -115 |       -128 |
| lvl:cluster_behind_10               |    6551 |   6201 |   -101 | -2.62 |        -115 |         -68 |        -160 |          -6 |       -338 |
| lvl:behind<=5&ahead>=20             |     517 |    637 |     36 |  0.31 |          49 |         325 |        -587 |        -119 |       -998 |
| lvl:behind>5                        |    5918 |   6274 |   -116 | -2.95 |        -260 |         -52 |         -97 |         -93 |       -158 |

`c_H_no_spoof_mine60`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |   13894 |   5904 |     48 |  1.53 |          12 |         -38 |          77 |         110 |        268 |
| sess:0                              |    6118 |   1181 |     59 |  0.62 |        -489 |         -53 |         174 |         307 |        998 |
| sess:1                              |    5122 |   1330 |    -61 | -1.07 |         -10 |        -206 |         -31 |           1 |        233 |
| sess:3                              |    2081 |   2830 |      1 |  0.02 |         125 |         -56 |         -42 |         -67 |        -10 |
| sess:4                              |     573 |    563 |     29 |  0.4  |         -64 |         -56 |         140 |          -0 |       -220 |
| lvl:behind<=3pts(at a level)        |    3091 |   1221 |     18 |  0.26 |        -270 |          72 |         132 |         115 |        410 |
| lvl:behind<=5pts                    |    5430 |   2176 |     72 |  1.38 |         -79 |          58 |         129 |         234 |        346 |
| lvl:ahead<=10pts(level close ahead) |    8703 |   3643 |     57 |  1.38 |          -7 |         -42 |          66 |         126 |        217 |
| lvl:ahead<=20pts                    |   11850 |   5053 |     53 |  1.53 |         -11 |         -22 |          63 |         120 |        242 |
| lvl:cluster_behind_10               |    8629 |   4123 |     96 |  2.54 |         119 |          72 |         138 |         -54 |        227 |
| lvl:behind<=5&ahead>=20             |     822 |    332 |    100 |  0.86 |          74 |         288 |         518 |         199 |        468 |
| lvl:behind>5                        |    8464 |   3728 |     34 |  0.85 |          97 |        -132 |          52 |          57 |        235 |

`c_H2_arrival_imb60_lo`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |    3861 |  15924 |    144 |  3.44 |          75 |         200 |         114 |         160 |        249 |
| sess:0                              |    1666 |   5628 |    178 |  2.12 |         112 |          49 |         254 |         222 |        324 |
| sess:1                              |    1279 |   5171 |    100 |  1.67 |          66 |         251 |          21 |          89 |        148 |
| sess:3                              |     755 |   4150 |    111 |  2.01 |          33 |         284 |         -63 |         159 |        268 |
| sess:4                              |     161 |    975 |     -4 | -0.04 |         -90 |         142 |          97 |        -273 |       -207 |
| lvl:behind<=3pts(at a level)        |     873 |   3435 |     94 |  1.03 |          -1 |         222 |         106 |          10 |        295 |
| lvl:behind<=5pts                    |    1562 |   6036 |     66 |  0.98 |         106 |         141 |         -50 |          78 |        260 |
| lvl:ahead<=10pts(level close ahead) |    2495 |   9842 |    130 |  2.42 |          88 |         253 |          86 |          84 |        200 |
| lvl:ahead<=20pts                    |    3335 |  13557 |    139 |  3.06 |          74 |         184 |         128 |         142 |        234 |
| lvl:cluster_behind_10               |    2492 |  10248 |    167 |  3.28 |          87 |         154 |         135 |         270 |        404 |
| lvl:behind<=5&ahead>=20             |     210 |    942 |     47 |  0.3  |         438 |         156 |         275 |        -255 |       -182 |
| lvl:behind>5                        |    2299 |   9888 |    196 |  3.64 |          34 |         244 |         210 |         196 |        245 |

`c_H2_spoof_ahead60_lo`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |   13416 |   6369 |    105 |  3.34 |          -9 |          97 |          76 |         246 |        546 |
| sess:0                              |    5967 |   1327 |    164 |  1.8  |        -199 |         196 |         116 |         470 |       1330 |
| sess:1                              |    4967 |   1483 |    -15 | -0.27 |        -142 |         -88 |          23 |          64 |        610 |
| sess:3                              |    1964 |   2941 |     82 |  2.07 |         115 |         153 |          13 |         100 |        355 |
| sess:4                              |     518 |    618 |    -14 | -0.19 |        -134 |        -174 |         -70 |         374 |         98 |
| lvl:behind<=3pts(at a level)        |    2977 |   1331 |     40 |  0.58 |        -250 |         176 |          52 |         184 |        778 |
| lvl:behind<=5pts                    |    5233 |   2365 |     83 |  1.61 |         -56 |         112 |          72 |         320 |        689 |
| lvl:ahead<=10pts(level close ahead) |    8364 |   3973 |    125 |  3.08 |         -29 |          95 |          79 |         302 |        691 |
| lvl:ahead<=20pts                    |   11423 |   5469 |    123 |  3.6  |         -26 |         131 |          76 |         276 |        488 |
| lvl:cluster_behind_10               |    8275 |   4465 |    143 |  3.79 |          53 |         174 |         118 |         223 |        882 |
| lvl:behind<=5&ahead>=20             |     803 |    349 |    -14 | -0.11 |          20 |          78 |         301 |         208 |        969 |
| lvl:behind>5                        |    8183 |   4004 |    118 |  2.98 |          36 |          67 |          80 |         218 |        502 |

`c_H2_ctr_mine300_lo`

| cell                                |   n_yes |   n_no |   lift |     z |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------------------|--------:|-------:|-------:|------:|------------:|------------:|------------:|------------:|-----------:|
| ALL                                 |    3372 |  16413 |    129 |  2.77 |         190 |          82 |         151 |         127 |         99 |
| sess:0                              |    1854 |   5440 |    130 |  1.62 |         169 |          27 |         291 |         105 |        -21 |
| sess:1                              |     801 |   5649 |     74 |  0.97 |         360 |         176 |        -183 |         194 |        420 |
| sess:3                              |     580 |   4325 |    -19 | -0.33 |          30 |        -159 |          39 |         -11 |         -2 |
| sess:4                              |     137 |    999 |    142 |  1.18 |         nan |          75 |         140 |         175 |        172 |
| lvl:behind<=3pts(at a level)        |     905 |   3403 |    -48 | -0.52 |        -110 |        -210 |         214 |         -21 |       -103 |
| lvl:behind<=5pts                    |    1541 |   6057 |     95 |  1.36 |         142 |         -67 |          57 |         317 |        275 |
| lvl:ahead<=10pts(level close ahead) |    2260 |  10077 |    104 |  1.74 |         138 |          87 |         161 |          56 |        -36 |
| lvl:ahead<=20pts                    |    2916 |  13976 |    142 |  2.78 |         169 |          96 |         175 |         152 |        133 |
| lvl:cluster_behind_10               |    2334 |  10406 |     68 |  1.24 |         188 |          36 |          32 |          57 |        -92 |
| lvl:behind<=5&ahead>=20             |     209 |    943 |   -107 | -0.67 |         242 |        -102 |          -2 |        -377 |       -518 |
| lvl:behind>5                        |    1831 |  10356 |    154 |  2.47 |         271 |         216 |         212 |          29 |         15 |

H caveat: MBO covers 2023-04..2026-11 after the history purchase, so years can test stability.

## BLOCK 14 breadth, rotation, relative value: single-condition tables (pooled, per session; stable = same sign in every evaluated year and in L6M)

38 conditions with n>=100 each side, 4 with |z|>2 (chance about 2), 2 of those stable. Largest |z| pooled:

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_avg_corr60_ge0.3              |    1575 |   1172 |        57.3 |       -46 |      143 |      40.4 |     46.9 |   -189 | -290 |  -89 | -3.69 |         0 |          3 |        -27 |       -158 |        nan |
| c_B14_avg_corr60_ge0.5              |     678 |   2069 |        24.7 |       -69 |       68 |      40   |     44.3 |   -137 | -248 |  -26 | -2.42 |         0 |          3 |        265 |        nan |        nan |
| c_B14_avg_corr60_le0.2              |     595 |   2152 |        21.7 |       146 |        4 |      47.4 |     42   |    142 |   20 |  265 |  2.28 |         3 |          3 |         -7 |         97 |       -289 |
| c_B14_hl_net_15bars_with_pos        |    2345 |   1080 |        68.5 |        82 |      -22 |      43.9 |     40.7 |    104 |   11 |  197 |  2.18 |         3 |          3 |        151 |        127 |        624 |
| c_B14_NVDA_minus_QQQ_15_with        |    1962 |   1211 |        61.8 |        -2 |       84 |      42.2 |     44.6 |    -86 | -183 |   11 | -1.74 |         1 |          3 |         13 |       -144 |        -27 |
| c_B14_largest_minus_QQQ_15_with     |    1968 |   1205 |        62   |        -0 |       82 |      42   |     44.8 |    -83 | -180 |   14 | -1.67 |         1 |          3 |        -31 |        -85 |       -243 |
| c_B14_eq7_minus_QQQ_15_with         |    1826 |   1347 |        57.6 |        -2 |       76 |      42.4 |     44   |    -78 | -173 |   16 | -1.62 |         1 |          3 |        118 |        354 |        342 |
| c_B14_RTY_outperforming_ES_240_with |    9385 |   8310 |        53   |        64 |      113 |      42.9 |     44.1 |    -49 | -112 |   14 | -1.53 |         1 |          4 |         52 |         38 |        240 |
| c_B14_NQ_rich_vs_ES_with_ge1.0      |    6246 |  12103 |        34   |       120 |       75 |      43.6 |     43.5 |     46 |  -21 |  112 |  1.35 |         2 |          4 |         -3 |        -40 |       -130 |
| c_B14_eq7_minus_QQQ_60_with         |    1247 |    952 |        56.7 |         0 |       70 |      42   |     45   |    -70 | -180 |   41 | -1.23 |         0 |          3 |          0 |         30 |        795 |
| c_B14_NQ_rich_vs_ES_with_ge1.5      |    3937 |  14412 |        21.5 |       123 |       81 |      43.9 |     43.4 |     42 |  -33 |  117 |  1.1  |         4 |          4 |        -77 |         33 |       -347 |
| c_B14_NQ_rich_vs_ES_with_ge0.5      |    8084 |  10265 |        44.1 |       110 |       75 |      43.4 |     43.6 |     34 |  -29 |   97 |  1.06 |         2 |          4 |         24 |       -114 |       -374 |
| c_B14_MSFT_minus_NVDA_15_with       |    1158 |   2015 |        36.5 |        59 |       15 |      44.1 |     42.5 |     44 |  -54 |  143 |  0.89 |         2 |          3 |         49 |        233 |        -30 |
| c_B14_NQ_cheap_vs_QQQ_with_ge1.0    |     143 |   3263 |         4.2 |       142 |       47 |      39.2 |     43.1 |     95 | -130 |  319 |  0.83 |         2 |          3 |       -506 |       -614 |        nan |
| c_B14_MSFT_minus_NVDA_60_with       |     843 |   1356 |        38.3 |         1 |       49 |      42   |     44.1 |    -47 | -160 |   65 | -0.82 |         0 |          3 |         30 |        -19 |        324 |

### B14 sess:0 (n=7,299), 6 largest |z|

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_NQ_rich_vs_ES_with_ge1.0      |    2134 |   3809 |        35.9 |       304 |      152 |      47.6 |     45.6 |    152 |   -6 |  309 |  1.89 |         3 |          4 |       -180 |       -385 |         43 |
| c_B14_NQ_rich_vs_ES_with_ge0.5      |    2687 |   3256 |        45.2 |       283 |      144 |      47.5 |     45.4 |    140 |  -13 |  292 |  1.8  |         3 |          4 |        -82 |       -410 |       -174 |
| c_B14_NQ_cheap_vs_ES_with_ge0.5     |    2458 |   3485 |        41.4 |       127 |      263 |      44.8 |     47.4 |   -136 | -289 |   17 | -1.74 |         1 |          4 |         81 |        409 |        335 |
| c_B14_NQ_rich_vs_ES_with_ge1.5      |    1341 |   4602 |        22.6 |       306 |      178 |      47.4 |     46   |    128 |  -48 |  304 |  1.42 |         4 |          4 |       -311 |       -358 |       -434 |
| c_B14_RTY_outperforming_ES_240_with |    2839 |   2476 |        53.4 |       171 |      256 |      45.5 |     47.5 |    -85 | -247 |   78 | -1.02 |         1 |          4 |        250 |        226 |        485 |
| c_B14_NQ_cheap_vs_ES_with_ge1.5     |    1159 |   4784 |        19.5 |       142 |      222 |      45   |     46.6 |    -80 | -268 |  109 | -0.83 |         2 |          4 |        -18 |        256 |       -225 |

### B14 sess:1 (n=6,452), 6 largest |z|

| cond                               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_NQ_cheap_vs_ES_with_ge1.0    |    1827 |   4552 |        28.6 |       109 |        5 |      44   |     40.7 |    104 |    5 |  202 |  2.06 |         3 |          4 |        153 |        180 |        549 |
| c_B14_RTY_outperforming_ES_60_with |    3768 |   2604 |        59.1 |         5 |       79 |      40.9 |     42.8 |    -74 | -166 |   17 | -1.59 |         0 |          4 |          1 |        -98 |       -189 |
| c_B14_NQ_cheap_vs_ES_with_ge1.5    |    1104 |   5275 |        17.3 |       107 |       20 |      43.4 |     41.3 |     87 |  -30 |  204 |  1.45 |         3 |          4 |        260 |        403 |        756 |
| c_B14_NQ_cheap_vs_ES_with_ge0.5    |    2488 |   3891 |        39   |        72 |       11 |      43.2 |     40.7 |     61 |  -31 |  152 |  1.3  |         2 |          4 |        -55 |        -50 |        502 |
| c_B14_NQ_rich_vs_ES_with_ge0.5     |    2768 |   3611 |        43.4 |        10 |       54 |      40.5 |     42.5 |    -44 | -134 |   47 | -0.95 |         2 |          4 |        112 |         30 |       -950 |
| c_B14_NQ_rich_vs_ES_with_ge1.0     |    2097 |   4282 |        32.9 |         8 |       48 |      40.4 |     42.3 |    -41 | -137 |   55 | -0.83 |         2 |          4 |        131 |        193 |       -750 |

### B14 sess:3 (n=4,911), 6 largest |z|

| cond                               |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_avg_corr60_ge0.3             |    1088 |    999 |        52.1 |       -57 |      112 |      39.3 |     45.4 |   -169 | -285 |  -53 | -2.86 |         0 |          3 |         24 |        124 |        nan |
| c_B14_hl_net_15bars_with_pos       |    2027 |    738 |        73.3 |        79 |      -47 |      43.2 |     39.2 |    126 |   14 |  238 |  2.21 |         3 |          3 |        187 |        112 |        757 |
| c_B14_RTY_outperforming_ES_60_with |    2375 |   2519 |        48.5 |        66 |       -6 |      43.6 |     40.6 |     73 |   -3 |  149 |  1.88 |         3 |          4 |         61 |         63 |        112 |
| c_B14_avg_corr60_le0.2             |     513 |   1574 |        24.6 |       112 |       -4 |      46   |     41   |    117 |  -19 |  252 |  1.69 |         2 |          3 |         -9 |         12 |       -263 |
| c_B14_eq7_minus_QQQ_15_with        |    1413 |   1100 |        56.2 |       -19 |       73 |      41.3 |     43.4 |    -91 | -199 |   17 | -1.66 |         1 |          3 |        144 |        305 |        424 |
| c_B14_NVDA_minus_QQQ_15_with       |    1532 |    981 |        61   |       -12 |       74 |      41.2 |     43.8 |    -87 | -197 |   23 | -1.54 |         1 |          3 |         25 |       -189 |       -145 |

### B14 sess:4 (n=1,136), 6 largest |z|

| cond                            |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:--------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B14_avg_corr60_ge0.5          |     269 |    391 |        40.8 |      -110 |      189 |      39.8 |     50.6 |   -299 | -486 | -113 | -3.14 |         0 |          3 |        144 |        nan |        nan |
| c_B14_avg_corr60_ge0.3          |     487 |    173 |        73.8 |       -23 |      321 |      42.9 |     55.5 |   -344 | -561 | -128 | -3.12 |         0 |          2 |       -265 |       -711 |        nan |
| c_B14_share_ma20_with_ge6of7    |     479 |    181 |        72.6 |       -13 |      280 |      43.4 |     53.6 |   -294 | -513 |  -75 | -2.63 |         1 |          3 |       -274 |       -643 |        nan |
| c_B14_share_vwap_with_ge4of7    |     461 |    199 |        69.8 |        23 |      170 |      44.2 |     50.7 |   -146 | -341 |   48 | -1.47 |         1 |          3 |       -175 |        301 |        nan |
| c_B14_largest_minus_QQQ_15_with |     435 |    225 |        65.9 |        21 |      157 |      45.3 |     48   |   -136 | -337 |   66 | -1.32 |         0 |          3 |        -37 |        222 |        nan |
| c_B14_adl_at_extreme_with_ge0.9 |     426 |    234 |        64.6 |        23 |      148 |      44.4 |     49.6 |   -124 | -322 |   73 | -1.23 |         1 |          3 |        -47 |         99 |        nan |

## BLOCK 15 macro, sentiment, positioning (day context): single-condition tables (pooled, per session; stable = same sign in every evaluated year and in L6M)

70 conditions with n>=100 each side, 10 with |z|>2 (chance about 4), 4 of those stable. Largest |z| pooled:

| cond                                     |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_fed_speech_started_last_90min      |     554 |  19244 |         2.8 |      -205 |      115 |      35   |     44   |   -320 | -444 | -196 | -5.04 |         0 |          4 |       -308 |        -66 |        nan |
| c_B15_big_yield_day_ge8bp                |    2948 |  16850 |        14.9 |       -80 |      138 |      39.9 |     44.4 |   -218 | -303 | -133 | -5.02 |         0 |          4 |       -236 |       -187 |       -563 |
| c_B15_pc_etp_pct_ge80                    |    3752 |  15202 |        19.8 |         9 |      135 |      42.1 |     44.2 |   -126 | -204 |  -48 | -3.18 |         1 |          4 |       -220 |       -127 |        -87 |
| c_B15_pc_idx_pct_le20                    |    4581 |  14373 |        24.2 |        26 |      137 |      41.3 |     44.6 |   -111 | -184 |  -38 | -2.98 |         1 |          4 |       -171 |       -107 |        -29 |
| c_B15_fed_speech_within_60min            |     633 |  19165 |         3.2 |       -88 |      112 |      38.6 |     43.9 |   -200 | -334 |  -67 | -2.94 |         0 |          4 |         73 |         87 |       -784 |
| c_B15_yield10_fell_5d_with               |    9749 |  10049 |        49.2 |       148 |       64 |      44.8 |     42.8 |     84 |   22 |  146 |  2.67 |         4 |          4 |         11 |       -249 |       -317 |
| c_B15_skew_pct_ge80                      |    5338 |  14460 |        27   |        40 |      130 |      42.9 |     44.1 |    -90 | -160 |  -21 | -2.54 |         0 |          4 |       -118 |        -58 |        119 |
| c_B15_pc_tot_pct_le20                    |    4324 |  14630 |        22.8 |        38 |      132 |      41.8 |     44.3 |    -94 | -169 |  -18 | -2.44 |         1 |          4 |        -50 |         -1 |        249 |
| c_B15_pc_eq_pct_le20                     |    3874 |  15080 |        20.4 |        45 |      127 |      42.3 |     44.1 |    -82 | -160 |   -3 | -2.03 |         1 |          4 |        -53 |       -371 |        nan |
| c_B15_pc_idx_pct_ge80                    |    3022 |  15932 |        15.9 |       186 |       96 |      45.4 |     43.4 |     90 |    2 |  177 |  2.02 |         2 |          4 |        301 |        413 |        526 |
| c_B15_yield10_fell_prior_day_with        |    9438 |  10360 |        47.7 |       139 |       76 |      44.5 |     43.1 |     63 |    1 |  125 |  1.99 |         3 |          4 |        -11 |        123 |        114 |
| c_B15_hy_narrowed_prior_day_with         |    7673 |   9683 |        44.2 |        84 |      144 |      42.5 |     44.7 |    -60 | -126 |    7 | -1.76 |         2 |          4 |        -78 |          2 |          7 |
| c_B15_earn_nvda_report_today_after_close |     245 |  19553 |         1.2 |      -135 |      109 |      38.8 |     43.8 |   -243 | -521 |   34 | -1.72 |         1 |          4 |       -794 |       -519 |        nan |
| c_B15_bondvol_proxy_le0.8                |    4222 |  12257 |        25.6 |       163 |       92 |      45.6 |     43.2 |     71 |  -12 |  153 |  1.69 |         3 |          4 |         -4 |        119 |        101 |
| c_B15_pc_etp_pct_le20                    |    4293 |  14661 |        22.7 |       158 |       96 |      44.4 |     43.6 |     62 |  -14 |  138 |  1.6  |         3 |          4 |        163 |        103 |        221 |

### B15 sess:0 (n=7,299), 6 largest |z|

| cond                                     |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |    lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:-----------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|------:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_big_yield_day_ge8bp                |    1101 |   6198 |        15.1 |      -150 |      300 |      40.2 |     47.8 |   -450 |  -637 | -263 | -4.72 |         0 |          4 |       -431 |       -377 |       -843 |
| c_B15_pc_etp_pct_le20                    |    1424 |   5642 |        20.2 |       472 |      180 |      52.1 |     45.4 |    292 |   112 |  472 |  3.18 |         4 |          4 |        265 |        232 |        249 |
| c_B15_fed_chair_speaks_today             |     170 |   7129 |         2.3 |       952 |      215 |      60.6 |     46.3 |    737 |   282 | 1191 |  3.18 |         3 |          3 |        nan |        nan |        nan |
| c_B15_earn_nvda_report_today_after_close |     105 |   7194 |         1.4 |      -578 |      244 |      30.5 |     46.8 |   -823 | -1345 | -300 | -3.09 |         0 |          2 |       -854 |       -236 |        nan |
| c_B15_yield10_fell_5d_with               |    3739 |   3560 |        51.2 |       336 |      124 |      48.4 |     44.8 |    212 |    76 |  349 |  3.04 |         4 |          4 |        103 |       -245 |       -449 |
| c_B15_pc_etp_pct_ge80                    |    1509 |   5557 |        21.4 |        49 |      290 |      43.4 |     47.6 |   -242 |  -405 |  -78 | -2.9  |         1 |          4 |       -409 |       -273 |        -92 |

### B15 sess:1 (n=6,452), 6 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_pc_tot_pct_le20         |    1422 |   4815 |        22.8 |      -166 |       95 |      36.2 |     43   |   -261 | -366 | -156 | -4.87 |         0 |          4 |       -360 |       -403 |       -942 |
| c_B15_auction_day_3y          |     319 |   6133 |         4.9 |      -204 |       42 |      35.1 |     41.8 |   -246 | -442 |  -51 | -2.47 |         1 |          4 |       -396 |       -174 |        nan |
| c_B15_cot_am_net_rising_1w    |    3402 |   3050 |        52.7 |       -22 |       88 |      39.7 |     43.5 |   -110 | -199 |  -21 | -2.43 |         1 |          4 |        -52 |       -223 |        nan |
| c_B15_auction_day_5y          |     276 |   6176 |         4.3 |       305 |       18 |      48.6 |     41.2 |    287 |   53 |  521 |  2.4  |         4 |          4 |        532 |       -155 |        432 |
| c_B15_usd_fell_20d_with_STALE |    3266 |   3186 |        50.6 |        84 |      -25 |      43   |     40   |    108 |   20 |  197 |  2.39 |         3 |          4 |        136 |        109 |        541 |
| c_B15_pc_idx_pct_le20         |    1509 |   4728 |        24.2 |       -60 |       65 |      38.4 |     42.5 |   -125 | -228 |  -23 | -2.39 |         1 |          4 |        -69 |        -69 |        292 |

### B15 sess:3 (n=4,911), 6 largest |z|

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   win_yes |   win_no |   lift |   lo |   hi |     z |   yrs_pos |   yrs_eval |   lift_L6M |   lift_L3M |   lift_L1M |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|----------:|---------:|-------:|-----:|-----:|------:|----------:|-----------:|-----------:|-----------:|-----------:|
| c_B15_fed_speech_started_last_90min |     378 |   4533 |         7.7 |      -187 |       45 |      36.5 |     42.5 |   -232 | -368 |  -97 | -3.37 |         0 |          4 |         17 |        109 |        nan |
| c_B15_big_yield_day_ge8bp           |     749 |   4162 |        15.2 |      -109 |       52 |      37.1 |     42.9 |   -161 | -262 |  -59 | -3.1  |         0 |          4 |       -486 |       -584 |        nan |
| c_B15_pc_etp_pct_ge80               |     807 |   3776 |        17.6 |      -101 |       53 |      38.4 |     42.5 |   -154 | -256 |  -52 | -2.97 |         0 |          4 |       -124 |       -635 |        nan |
| c_B15_pc_tot_pct_ge80               |     780 |   3803 |        17   |       -83 |       48 |      39.5 |     42.3 |   -131 | -234 |  -29 | -2.52 |         0 |          4 |        176 |        nan |        nan |
| c_B15_fed_speech_within_60min       |     385 |   4526 |         7.8 |      -106 |       39 |      38.4 |     42.3 |   -145 | -280 |  -10 | -2.11 |         0 |          4 |         64 |        228 |        nan |
| c_B15_pc_idx_pct_ge80               |     774 |   3809 |        16.9 |       -65 |       44 |      39.4 |     42.3 |   -109 | -210 |   -7 | -2.1  |         2 |          4 |        441 |        nan |        nan |

### B15 sess:4 (n=1,136), 6 largest |z|

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


### ALL_skipped (n=171,722; mean R = 0.017 typical), 10 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |      z |   yrs_pos |   yrs_eval |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|-------:|-------:|----------:|-----------:|
| c_I_ratio_trend240_pos        |  117022 |  38766 |        75.1 |     0.033 |   -0.025 |  0.058 |  11.74 |         4 |          4 |
| c_B15_vix_fell_prior_day_with |   86431 |  85291 |        50.3 |     0.043 |   -0.003 |  0.045 |  11.19 |         4 |          4 |
| c_B5_NQ_15m_ema_stack_with    |   99787 |  70138 |        58.7 |     0.039 |   -0.006 |  0.045 |  10.85 |         4 |          4 |
| c_B5_corr_mean3_60_ge0.8      |   50887 | 120632 |        29.7 |    -0.012 |    0.034 | -0.046 | -10    |         1 |          4 |
| c_J_flip_far50_NDX_vol        |   66955 |  26907 |        71.3 |     0.045 |   -0.015 |  0.06  |   9.7  |         3 |          3 |
| c_B5_corr_NQ_YM_60_ge0.8      |   35895 | 133567 |        21.2 |    -0.021 |    0.03  | -0.051 |  -9.69 |         1 |          4 |
| c_B5_NQ_15m_supertrend_with   |  112527 |  57398 |        66.2 |     0.034 |   -0.005 |  0.039 |   9.13 |         4 |          4 |
| c_B5_NQ_15m_rsi_with          |  138890 |  31035 |        81.7 |     0.029 |   -0.017 |  0.046 |   8.89 |         4 |          4 |
| c_B5_NQ_15m_hold21_with       |  113702 |  56223 |        66.9 |     0.033 |   -0.005 |  0.038 |   8.72 |         4 |          4 |
| c_J_flip_far25_NDX_vol        |   79275 |  14587 |        84.5 |     0.038 |   -0.027 |  0.065 |   8.7  |         3 |          3 |

### reason:SCR_gate (n=13,681; mean R = -0.013 typical), 10 largest |z|

| cond                             |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |     z |   yrs_pos |   yrs_eval |
|:---------------------------------|--------:|-------:|------------:|----------:|---------:|-------:|------:|----------:|-----------:|
| c_J_gex_pos_SPY_vol              |    4593 |   5630 |        44.9 |    -0.108 |    0.06  | -0.169 | -8.67 |         0 |          3 |
| c_B15_earn_big5_day_after_report |    1082 |  12599 |         7.9 |     0.234 |   -0.032 |  0.266 |  8.6  |         3 |          3 |
| c_J_gex_pos_QQQ_vol              |    4852 |   5393 |        47.4 |    -0.099 |    0.061 | -0.161 | -8.28 |         0 |          3 |
| c_B15_earn_any_day_after_report  |    1694 |  11987 |        12.4 |     0.165 |   -0.036 |  0.201 |  7.97 |         4 |          4 |
| c_J_em_room_ge100_Nd             |    7438 |   3028 |        71.1 |    -0.044 |    0.124 | -0.168 | -7.95 |         0 |          3 |
| c_J_gex_pos_SPX_vol              |    4703 |   5475 |        46.2 |    -0.101 |    0.051 | -0.152 | -7.82 |         1 |          3 |
| c_J_em_room_ge150_Nd             |    6773 |   3693 |        64.7 |    -0.05  |    0.105 | -0.154 | -7.72 |         0 |          3 |
| c_J_gdir_with_QQQ                |    3803 |   6442 |        37.1 |    -0.111 |    0.042 | -0.154 | -7.65 |         1 |          3 |
| c_J_em_room_ge50_Nd              |    7975 |   2491 |        76.2 |    -0.034 |    0.13  | -0.165 | -7.32 |         0 |          3 |
| c_B5_RTY_5m_adx_di_with          |    7548 |   6133 |        55.2 |     0.043 |   -0.077 |  0.12  |  7.13 |         2 |          3 |

### reason:dayHalt (n=7,359; mean R = 0.024 typical), 10 largest |z|

| cond                                |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |     z |   yrs_pos |   yrs_eval |
|:------------------------------------|--------:|-------:|------------:|----------:|---------:|-------:|------:|----------:|-----------:|
| c_B15_fed_speech_started_last_90min |     231 |   7128 |         3.1 |    -0.286 |    0.038 | -0.324 | -5.37 |         1 |          4 |
| c_J_flip_far50_NDX_vol              |    4081 |   1068 |        79.3 |     0.047 |   -0.125 |  0.172 |  5.34 |         3 |          3 |
| c_B5_YM_15m_sqz_on                  |    1742 |   5590 |        23.8 |    -0.07  |    0.059 | -0.129 | -4.99 |         0 |          4 |
| c_B15_big_yield_day_ge8bp           |    1337 |   6022 |        18.2 |    -0.084 |    0.053 | -0.137 | -4.83 |         0 |          4 |
| c_B5_ES_15m_sqz_on                  |    1794 |   5538 |        24.5 |    -0.059 |    0.057 | -0.116 | -4.54 |         0 |          4 |
| c_J_beyond_0dte_flip_Nd_oi          |    1210 |    834 |        59.2 |     0.058 |   -0.131 |  0.189 |  4.38 |         3 |          3 |
| c_I_ratio_trend240_pos              |    5042 |   1936 |        72.3 |     0.06  |   -0.05  |  0.11  |  4.34 |         3 |          4 |
| c_B5_RTY_1m_adx_di_with             |    3413 |   3919 |        46.6 |     0.08  |   -0.016 |  0.096 |  4.31 |         3 |          4 |
| c_B15_fed_speech_within_60min       |     336 |   7023 |         4.6 |    -0.184 |    0.038 | -0.222 | -4.24 |         0 |          4 |
| c_B5_ES_15m_adx_di_with             |    3686 |   3646 |        50.3 |     0.075 |   -0.018 |  0.093 |  4.21 |         3 |          4 |

### reason:inTrade (n=92,261; mean R = 0.028 typical), 10 largest |z|

| cond                        |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |     z |   yrs_pos |   yrs_eval |
|:----------------------------|--------:|-------:|------------:|----------:|---------:|-------:|------:|----------:|-----------:|
| c_J_flip_far50_NDX_vol      |   28920 |  15913 |        64.5 |     0.07  |   -0.021 |  0.091 | 11.03 |         3 |          3 |
| c_B5_NQ_15m_ema_stack_with  |   51474 |  40710 |        55.8 |     0.047 |   -0.005 |  0.053 |  9.93 |         4 |          4 |
| c_B5_NQ_15m_rsi_with        |   72726 |  19458 |        78.9 |     0.037 |   -0.024 |  0.061 |  9.53 |         4 |          4 |
| c_B5_RTY_15m_rsi_with       |   63041 |  29143 |        68.4 |     0.04  |   -0.012 |  0.052 |  9.24 |         4 |          4 |
| c_J_nowall_ahead50_NDX_vol  |   36316 |   8517 |        81   |     0.055 |   -0.036 |  0.092 |  9.11 |         3 |          3 |
| c_J_flip_far25_NDX_vol      |   36178 |   8655 |        80.7 |     0.055 |   -0.033 |  0.088 |  9.08 |         3 |          3 |
| c_B5_ES_15m_ema_stack_with  |   49903 |  42281 |        54.1 |     0.046 |   -0.002 |  0.048 |  9.07 |         4 |          4 |
| c_B5_NQ_15m_supertrend_with |   58383 |  33801 |        63.3 |     0.041 |   -0.005 |  0.045 |  8.37 |         4 |          4 |
| c_I_ratio_trend240_pos      |   60229 |  22345 |        72.9 |     0.037 |   -0.016 |  0.053 |  8.36 |         4 |          4 |
| c_B5_RTY_15m_ema_stack_with |   46545 |  45639 |        50.5 |     0.046 |    0.002 |  0.044 |  8.3  |         4 |          4 |

### reason:other (n=8,221; mean R = 0.010 typical), 10 largest |z|

| cond                        |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |     z |   yrs_pos |   yrs_eval |
|:----------------------------|--------:|-------:|------------:|----------:|---------:|-------:|------:|----------:|-----------:|
| c_B15_ZN_up_since_0930_with |    2293 |   2422 |        48.6 |     0.104 |   -0.06  |  0.164 |  6.16 |         4 |          4 |
| c_B5_corr_NQ_ES_60_ge0.9    |    5520 |   2697 |        67.2 |    -0.023 |    0.095 | -0.117 | -5.68 |         1 |          4 |
| c_B15_cot_lev_net_pct_ge80  |    2107 |   6114 |        25.6 |    -0.076 |    0.048 | -0.124 | -5.45 |         1 |          3 |
| c_B5_ALL_15m_adx_di_ge3of4  |    3280 |   4857 |        40.3 |    -0.045 |    0.057 | -0.103 | -4.99 |         1 |          4 |
| c_B15_fed_speaker_today     |    2365 |   5856 |        28.8 |    -0.061 |    0.047 | -0.108 | -4.86 |         0 |          4 |
| c_B15_auction_day_10y       |     452 |   7769 |         5.5 |     0.211 |    0.005 |  0.206 |  4.83 |         4 |          4 |
| c_B15_cot_am_net_rising_1w  |    4298 |   3923 |        52.3 |    -0.029 |    0.066 | -0.095 | -4.75 |         0 |          4 |
| c_J_wall_behind50_Nh_oi     |     575 |   3347 |        14.7 |     0.162 |   -0.033 |  0.195 |  4.75 |         3 |          3 |
| c_B15_pc_etp_pct_ge80       |    1591 |   6237 |        20.3 |    -0.077 |    0.046 | -0.123 | -4.74 |         1 |          4 |
| c_B15_vvix_pct_le20         |    1832 |   6389 |        22.3 |     0.1   |   -0.008 |  0.108 |  4.56 |         3 |          4 |

### reason:session_lots_0 (n=34,664; mean R = 0.032 typical), 10 largest |z|

| cond                          |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |     z |   yrs_pos |   yrs_eval |
|:------------------------------|--------:|-------:|------------:|----------:|---------:|-------:|------:|----------:|-----------:|
| c_B5_corr_mean3_60_ge0.8      |   10849 |  23815 |        31.3 |    -0.016 |    0.056 | -0.072 | -7.25 |         0 |          4 |
| c_B5_corr_NQ_YM_60_ge0.8      |    7627 |  26513 |        22.3 |    -0.026 |    0.05  | -0.076 | -6.71 |         0 |          4 |
| c_B15_vix_fell_prior_day_with |   17904 |  16760 |        51.6 |     0.062 |    0.003 |  0.059 |  6.67 |         4 |          4 |
| c_B15_fed_speech_within_60min |     900 |  33764 |         2.6 |    -0.147 |    0.039 | -0.185 | -6.18 |         0 |          4 |
| c_B14_avg_corr60_ge0.5        |    1245 |   3678 |        25.3 |    -0.11  |    0.084 | -0.195 | -6.12 |         0 |          3 |
| c_I_ratio_trend240_pos        |   24842 |   5676 |        81.4 |     0.044 |   -0.031 |  0.075 |  6.07 |         4 |          4 |
| c_J_beyond_0dte_flip_Nd_vol   |    5100 |   2270 |        69.2 |     0.065 |   -0.063 |  0.128 |  5.88 |         3 |          3 |
| c_B5_corr_NQ_YM_60_ge0.9      |    1836 |  32304 |         5.4 |    -0.091 |    0.04  | -0.131 | -5.82 |         0 |          4 |
| c_B14_avg_corr60_ge0.3        |    2741 |   2182 |        55.7 |    -0.033 |    0.12  | -0.153 | -5.77 |         0 |          3 |
| c_J_beyond_0dte_flip_Nd_oi    |    4558 |   2381 |        65.7 |     0.07  |   -0.055 |  0.125 |  5.69 |         3 |          3 |

### reason:timeBlocked (n=15,536; mean R = -0.013 typical), 10 largest |z|

| cond                             |   n_yes |   n_no |   share_yes |   exp_yes |   exp_no |   lift |     z |   yrs_pos |   yrs_eval |
|:---------------------------------|--------:|-------:|------------:|----------:|---------:|-------:|------:|----------:|-----------:|
| c_B5_corr_NQ_YM_60_ge0.8         |    4337 |  11016 |        28.2 |    -0.085 |    0.022 | -0.106 | -6.87 |         0 |          4 |
| c_B15_pc_tot_pct_ge80            |    2351 |  12140 |        16.2 |    -0.125 |    0.011 | -0.136 | -6.83 |         0 |          4 |
| c_B5_YM_15m_rsi_with             |   10048 |   4302 |        70   |    -0.039 |    0.069 | -0.108 | -6.72 |         0 |          4 |
| c_B15_hy_narrowed_prior_day_with |    5642 |   6895 |        45   |     0.053 |   -0.051 |  0.104 |  6.55 |         3 |          4 |
| c_B5_corr_mean3_60_ge0.8         |    5137 |  10231 |        33.4 |    -0.07  |    0.023 | -0.093 | -6.29 |         0 |          4 |
| c_B5_YM_5m_ema_stack_with        |    9084 |   5266 |        63.3 |    -0.039 |    0.049 | -0.089 | -5.81 |         0 |          4 |
| c_B5_corr_NQ_RTY_240_ge0.8       |    3187 |  12160 |        20.8 |    -0.088 |    0.012 | -0.1   | -5.67 |         1 |          4 |
| c_B5_NQ_15m_vwap_with            |   11066 |   3284 |        77.1 |    -0.029 |    0.07  | -0.099 | -5.65 |         0 |          4 |
| c_I_YM_conf60                    |   10827 |   4212 |        72   |    -0.034 |    0.055 | -0.089 | -5.6  |         1 |          4 |
| c_B14_share_vwap_with_ge6of7     |    1809 |   2758 |        39.6 |    -0.076 |    0.08  | -0.156 | -5.55 |         0 |          3 |
