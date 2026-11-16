# DS3_REBUILD_S1_TAPE_CF2 (W-CF2): TAPE SPEED readings, T-REBUILD Stage 1 item 5 addendum 2 - PROVISIONAL RAW BASE, FIRST PASS
VERDICT (data ends 2026-11-13; ): 576 tape-speed conditions (46 readings: trades/s, contracts/s, order messages/s, acceleration, speed into the signal, aggressor split; windows 5/15/30/60/300 s; raw, ratio to the same half-hour median of the previous 20 days, 20-day percentile; own/other/difference) scored per book x session against PROVISIONAL RAW (hyp1m bracket outcome of every universe signal, no layers): 25,671 tests, 371 beat the cell's nonsense p99 bar (1.4% vs ~1% by chance). Breakout books (K7 M7 U7 H7) ALL sessions: 3 of 576 beat the bar; pullback books (P7 A7 O7): 21 of 576. The expected opposite sign between the two groups is NOT found: only 3 conditions are |t|>2 in both groups and none has the opposite sign. Effects are small (|lift| 0.02-0.04 R). Nothing is a PASS.

Basis: R = hypothetical bracket outcome / stop of every universe signal (193,628, to 2026-11-13; no layers; W-PM's raw table replaces it via RAW_TABLE=<parquet with sig_id,R,mfe,mae>); MFE/MAE from 1-minute paths (hyp1m rows). Readings end the second before the entry second (latency 0) and 1/2/5 s earlier (t_d1/t_d2/t_d5 for the rows that beat the bar). Weekly-cluster t; bar = p99 |t| of 200 persistent nonsense conditions in the same cell. Books: breakout K7 M7 U7 H7, pullback P7 A7 O7 (user book types, autopilot/ANSWER_BOOK_TYPES_20261116.md). 'Order messages' = all MBO records per second (adds, cancels, modifies, fills, trades; the adds-within-9-ticks plus all-cancels subset is mps_book). Speed during the move into the signal = last 60 s rate / rate of the 300 s before it (into_*); acceleration = last 15 s / prior 60 s (acc_*); the pullback-leg versus impulse-leg readings need leg detection and are W-FL1's.

## Breakout books (K7 M7 U7 H7): 12 largest |t|, all sessions and by session (cells with the most conditions beating the bar)

| book     | sess   | cond                             |   n_yes |   liftR |    tR |   bar |   liftMFE |   liftMAE |   t_d1 |   t_d2 |   t_d5 |
|:---------|:-------|:---------------------------------|--------:|--------:|------:|------:|----------:|----------:|-------:|-------:|-------:|
| BREAKOUT | ALL    | c_T_cps_W300_other_ratio_le0.67  |   16899 |  -0.035 | -3.23 |   2.7 |     -4.47 |     -2.13 |  -3.37 |  -3.37 |  -3.47 |
| BREAKOUT | ALL    | c_T_cps_W300_other_pct_lo        |   16971 |  -0.033 | -3.09 |   2.7 |     -3.97 |     -1.77 |  -3.14 |  -3.14 |  -3.22 |
| BREAKOUT | ALL    | c_T_tps_W300_other_pct_lo        |   16458 |  -0.029 | -2.74 |   2.7 |     -3.91 |     -1.94 |  -2.8  |  -2.91 |  -2.81 |
| BREAKOUT | ALL    | c_T_tps_W300_other_ratio_le0.67  |   15288 |  -0.03  | -2.6  |   2.7 |     -4.28 |     -2.13 | nan    | nan    | nan    |
| BREAKOUT | ALL    | c_T_acc_cps_W15_own_raw_lo       |   14255 |   0.021 |  2.54 |   2.7 |     -3.34 |     -4.33 | nan    | nan    | nan    |
| BREAKOUT | ALL    | c_T_cps_W60_other_pct_lo         |   14467 |  -0.026 | -2.54 |   2.7 |     -3.26 |     -1.2  | nan    | nan    | nan    |
| BREAKOUT | ALL    | c_T_cps_tot_W30_own_ratio_le0.5  |    9607 |  -0.029 | -2.48 |   2.7 |     -4.39 |     -2.28 | nan    | nan    | nan    |
| BREAKOUT | ALL    | c_T_cps_tot_W60_own_pct_lo       |   11647 |  -0.029 | -2.47 |   2.7 |     -2.82 |     -0.86 | nan    | nan    | nan    |
| BREAKOUT | ALL    | c_T_cps_tot_W60_own_ratio_le0.67 |   13904 |  -0.026 | -2.43 |   2.7 |     -3.36 |     -1.3  | nan    | nan    | nan    |
| BREAKOUT | ALL    | c_T_acc_cps_W15_own_ratio_le0.5  |   13648 |   0.02  |  2.4  |   2.7 |     -3.02 |     -3.8  | nan    | nan    | nan    |
| BREAKOUT | ALL    | c_T_cps_W300_diff_pct_lo         |    4593 |   0.032 |  2.32 |   2.7 |      2.98 |      1.63 | nan    | nan    | nan    |
| BREAKOUT | ALL    | c_T_cps_tot_W300_own_ratio_le0.5 |    5844 |  -0.038 | -2.22 |   2.7 |     -4.78 |     -2.06 | nan    | nan    | nan    |

By session (beating the bar), BREAKOUT:

| book     |   sess | cond                                 |   n_yes |   liftR |    tR |   bar |   liftMFE |   liftMAE |   t_d1 |   t_d2 |   t_d5 |
|:---------|-------:|:-------------------------------------|--------:|--------:|------:|------:|----------:|----------:|-------:|-------:|-------:|
| BREAKOUT |      3 | c_T_cps_W300_own_ratio_le0.5         |     881 |  -0.177 | -3.64 |  2.7  |     -9.44 |      0.63 |  -3.67 |  -3.67 |  -3.43 |
| BREAKOUT |      0 | c_T_mps_book_W60_own_raw_lo          |    5656 |  -0.047 | -3.43 |  2.26 |     -9.32 |     -7.72 |  -3.2  |  -3.35 |  -3.56 |
| BREAKOUT |      0 | c_T_cps_W300_own_raw_lo              |    4148 |  -0.043 | -3.38 |  2.26 |     -5.55 |     -3.58 |  -3.25 |  -3.32 |  -3.17 |
| BREAKOUT |      0 | c_T_share_cps_W60_own_ratio_ge1.5    |    2047 |  -0.052 | -3.3  |  2.26 |     -3.43 |     -1.48 |  -2.19 |  -2.13 |  -1.66 |
| BREAKOUT |      3 | c_T_tps_W300_own_ratio_le0.5         |     881 |  -0.158 | -3.29 |  2.7  |     -9.06 |      0.14 |  -3.26 |  -3.11 |  -2.99 |
| BREAKOUT |      1 | c_T_cps_tot_W15_own_ratio_ge1.5      |   13731 |   0.04  |  3.28 |  2.35 |      2.17 |      0.2  |   2.55 |   2.51 |   1.85 |
| BREAKOUT |      0 | c_T_share_cps_W60_other_ratio_le0.5  |    1734 |  -0.059 | -3.24 |  2.26 |     -4.29 |     -1.21 |  -2.33 |  -2.58 |  -2.68 |
| BREAKOUT |      5 | c_T_share_tps_W60_own_pct_hi         |    2600 |  -0.074 | -3.23 |  2.53 |     -3.68 |      0.61 |  -2.85 |  -2.71 |  -3.27 |
| BREAKOUT |      3 | c_T_share_tps_W15_other_ratio_le0.67 |     220 |  -0.224 | -3.21 |  2.7  |    -14.21 |      3.11 |  -3.41 |  -2.87 |  -2.56 |
| BREAKOUT |      3 | c_T_share_tps_W5_own_ratio_le0.5     |     131 |  -0.238 | -3.16 |  2.7  |    -12.45 |     -1    |  -1.67 |  -3.1  |  -2.44 |
| BREAKOUT |      0 | c_T_cps_tot_W300_own_raw_lo          |    5433 |  -0.041 | -3.16 |  2.26 |     -5.9  |     -4.05 |  -3.25 |  -3.06 |  -3.46 |
| BREAKOUT |      5 | c_T_tps_W300_diff_raw_lo             |    1034 |   0.096 |  3.15 |  2.53 |      3.61 |     -2.01 |   2.91 |   3.01 |   3.17 |

## Pullback books (P7 A7 O7): 12 largest |t|, all sessions and by session (cells with the most conditions beating the bar)

| book     | sess   | cond                               |   n_yes |   liftR |    tR |   bar |   liftMFE |   liftMAE |   t_d1 |   t_d2 |   t_d5 |
|:---------|:-------|:-----------------------------------|--------:|--------:|------:|------:|----------:|----------:|-------:|-------:|-------:|
| PULLBACK | ALL    | c_T_cps_W60_diff_raw_hi            |   41450 |  -0.026 | -3.28 |  2.52 |      3.36 |      4.56 |  -3.69 |  -3.95 |  -4.3  |
| PULLBACK | ALL    | c_T_tps_W60_diff_raw_hi            |   40131 |  -0.024 | -3.15 |  2.52 |      3.49 |      4.62 |  -3.12 |  -3.24 |  -2.99 |
| PULLBACK | ALL    | c_T_share_cps_W30_own_ratio_ge1.5  |    9236 |   0.033 |  2.98 |  2.52 |     -5.04 |     -6.42 |   2.82 |   2.54 |   1.9  |
| PULLBACK | ALL    | c_T_cps_W300_diff_pct_lo           |    7952 |   0.036 |  2.87 |  2.52 |      1.72 |      0.5  |   2.8  |   2.72 |   2.82 |
| PULLBACK | ALL    | c_T_share_cps_W300_own_pct_lo      |    7842 |   0.033 |  2.85 |  2.52 |      0.4  |     -0.71 |   2.86 |   2.75 |   3.37 |
| PULLBACK | ALL    | c_T_share_cps_W60_diff_pct_hi      |   39255 |  -0.018 | -2.78 |  2.52 |     -0.94 |     -0.37 |  -2.5  |  -2.97 |  -2.94 |
| PULLBACK | ALL    | c_T_share_cps_W60_other_pct_lo     |   38387 |  -0.018 | -2.75 |  2.52 |     -0.92 |     -0.34 |  -2.72 |  -3.04 |  -3.26 |
| PULLBACK | ALL    | c_T_cps_W5_other_raw_lo            |   21081 |   0.028 |  2.72 |  2.52 |     -6.43 |     -7.84 |   2.6  |   2.15 |   1.78 |
| PULLBACK | ALL    | c_T_tps_W5_other_raw_lo            |   21081 |   0.028 |  2.72 |  2.52 |     -6.43 |     -7.84 |   2.6  |   2.15 |   1.78 |
| PULLBACK | ALL    | c_T_share_tps_W5_other_raw_lo      |   21081 |   0.028 |  2.72 |  2.52 |     -6.43 |     -7.84 |   2.6  |   2.15 |   1.78 |
| PULLBACK | ALL    | c_T_share_cps_W5_other_raw_lo      |   21081 |   0.028 |  2.72 |  2.52 |     -6.43 |     -7.84 |   2.6  |   2.15 |   1.78 |
| PULLBACK | ALL    | c_T_share_tps_W5_other_ratio_le0.5 |   20357 |   0.026 |  2.69 |  2.52 |     -4.54 |     -5.87 |   3.25 |   2.65 |   1.47 |

By session (beating the bar), PULLBACK:

| book     |   sess | cond                                 |   n_yes |   liftR |    tR |   bar |   liftMFE |   liftMAE |   t_d1 |   t_d2 |   t_d5 |
|:---------|-------:|:-------------------------------------|--------:|--------:|------:|------:|----------:|----------:|-------:|-------:|-------:|
| PULLBACK |      3 | c_T_share_tps_W15_other_raw_lo       |     132 |  -0.316 | -4.05 |  2.68 |    -13.25 |      5.98 |  -4    |  -4.03 |  -3.88 |
| PULLBACK |      5 | c_T_share_cps_W30_own_ratio_ge1.5    |     254 |   0.169 |  3.27 |  2.58 |     -1.82 |    -11.29 |   3.75 |   3.55 |   2.5  |
| PULLBACK |      3 | c_T_share_tps_W15_other_ratio_le0.67 |     197 |  -0.225 | -3.11 |  2.68 |     -9.74 |      4.41 |  -3.99 |  -3.85 |  -5.02 |
| PULLBACK |      0 | c_T_mps_book_W30_own_raw_lo          |    9575 |  -0.044 | -2.99 |  2.8  |    -10.04 |     -7.94 |  -2.59 |  -2.6  |  -2.68 |
| PULLBACK |      3 | c_T_share_tps_W300_other_raw_lo      |     484 |  -0.148 | -2.95 |  2.68 |     -7.58 |      1.18 |  -2.75 |  -2.87 |  -2.91 |
| PULLBACK |      3 | c_T_cps_W300_own_ratio_le0.5         |     737 |  -0.198 | -2.91 |  2.68 |     -8.97 |      3.14 |  -2.91 |  -2.97 |  -2.85 |
| PULLBACK |      3 | c_T_share_cps_W15_diff_pct_hi        |    3378 |  -0.059 | -2.9  |  2.68 |     -1.61 |      1.18 |  -2.72 |  -2.27 |  -2.1  |
| PULLBACK |      3 | c_T_share_cps_W60_diff_raw_hi        |    1879 |  -0.076 | -2.87 |  2.68 |     -2.64 |      0.63 |  -2.13 |  -2.68 |  -3.35 |
| PULLBACK |      2 | c_T_share_cps_W300_own_pct_lo        |     353 |   0.168 |  2.86 |  2.8  |      3.83 |     -1.1  |   2.53 |   2.32 |   2.41 |
| PULLBACK |      5 | c_T_mps_book_W15_own_raw_hi          |    2884 |  -0.095 | -2.85 |  2.58 |      3.72 |      7.87 |  -2.59 |  -2.65 |  -2.71 |
| PULLBACK |      3 | c_T_share_cps_W15_own_pct_hi         |    3392 |  -0.058 | -2.84 |  2.68 |     -1.47 |      1.23 |  -2.57 |  -2.33 |  -1.96 |
| PULLBACK |      3 | c_T_cps_tot_W300_own_ratio_le0.5     |     762 |  -0.185 | -2.82 |  2.68 |     -8.78 |      2.86 |  -2.77 |  -2.8  |  -2.8  |

## Counts per book x session (tests, beating the bar; chance about 1%)

| book     | sess   |   tests |   beat |
|:---------|:-------|--------:|-------:|
| A7       | 0.0    |     566 |     12 |
| A7       | 1.0    |     564 |      2 |
| A7       | 2.0    |     427 |      0 |
| A7       | 3.0    |     455 |      8 |
| A7       | 4.0    |     476 |      1 |
| A7       | 5.0    |     450 |      1 |
| A7       | ALL    |     576 |     41 |
| BREAKOUT | 0.0    |     569 |     21 |
| BREAKOUT | 1.0    |     575 |     13 |
| BREAKOUT | 2.0    |     524 |     19 |
| BREAKOUT | 3.0    |     490 |      9 |
| BREAKOUT | 4.0    |     507 |      0 |
| BREAKOUT | 5.0    |     553 |      9 |
| BREAKOUT | ALL    |     576 |      3 |
| H7       | 0.0    |     509 |      7 |
| H7       | 1.0    |     505 |      7 |
| H7       | 3.0    |     253 |      4 |
| H7       | 4.0    |     286 |      1 |
| H7       | ALL    |     570 |      3 |
| K7       | 0.0    |     569 |     24 |
| K7       | 1.0    |     570 |     16 |
| K7       | 2.0    |     477 |     15 |
| K7       | 3.0    |     463 |      5 |
| K7       | 4.0    |     482 |      1 |
| K7       | 5.0    |     507 |      3 |
| K7       | ALL    |     576 |     15 |
| M7       | 1.0    |     570 |     15 |
| M7       | 2.0    |     502 |      0 |
| M7       | 3.0    |     471 |      9 |
| M7       | 4.0    |     492 |      2 |
| M7       | 5.0    |     529 |     21 |
| M7       | ALL    |     576 |      1 |
| O7       | 3.0    |     130 |      2 |
| O7       | ALL    |     130 |      2 |
| P7       | 0.0    |     568 |      0 |
| P7       | 1.0    |     570 |      8 |
| P7       | 2.0    |     510 |      0 |
| P7       | 3.0    |     480 |      2 |
| P7       | 4.0    |     500 |      2 |
| P7       | 5.0    |     567 |      1 |
| P7       | ALL    |     576 |     10 |
| PULLBACK | 0.0    |     570 |      1 |
| PULLBACK | 1.0    |     570 |      1 |
| PULLBACK | 2.0    |     516 |      1 |
| PULLBACK | 3.0    |     487 |     15 |
| PULLBACK | 4.0    |     511 |      0 |
| PULLBACK | 5.0    |     570 |      8 |
| PULLBACK | ALL    |     576 |     21 |
| U7       | 0.0    |     428 |      6 |
| U7       | 1.0    |     454 |      0 |
| U7       | 3.0    |     175 |      2 |
| U7       | ALL    |     568 |      1 |

## Latency (rows beating the bar: share still above the bar with the same sign when the reading is 1 / 2 / 5 s old)

d1 56%, d2 50%, d5 43% of 371 rows.

## In-trade reading (Stage 3 exit input)
Per 5-second row for each taken trade from entry+5 s to min(exit, entry+60 min): adverse versus favourable aggressor rates over 5 and 15 s (trade records and contracts), their ratios, acceleration of the adverse side, message-rate acceleration and unrealised points: /mnt/l2/l2vast/_confl/cols_cf2/TAPE_INTRADE.parquet (JN05W2 engine trades; switch to W-PM raw trades with TRADES=<parquet with sig_id, side, ld, entry_ts, exit_ts>). Scored by W-CF3 in Stage 3.

## Feed flags
| feed                           |   conditions |
|:-------------------------------|-------------:|
| D7 computes today (NT8 prints) |          481 |
| L3 feed (order messages)       |           95 |
Trade and contract rates and the aggressor split come from NT8 prints (D7 computes them today; aggressor by print vs bid/ask); order-message rates (adds, cancels, modifies) need the live L3 feed. Files: cols_cf2/TAPE_SPEED.parquet (lag 0), TAPE_SPEED_LAT.parquet (_d1/_d2/_d5), TAPE_SPEED_conditions.csv, TAPE_SPEED_stats.csv.
