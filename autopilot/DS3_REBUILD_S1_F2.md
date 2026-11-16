# DS3_REBUILD_S1_F2 - T-REBUILD Stage 1, family 2: candle counting, ICT 7-13-21 count, IRL/ERL sweeps (W-CF6), FIRST TABLE 2026-11-16

**VERDICT (data ends 2026-10-31; scored against a RAW-PROXY outcome, not yet the Stage 0 raw trades): 2,031 family-2 conditions (1,065 counting + 310 ICT + 322 alt-bar counts + 334 IRL/ERL) scored in 15 book x session cells on three outcomes (raw R, MAE, MFE). Rule: |t_cr| above the cell's nonsense 99th percentile (200 nonsense conditions) AND same sign in 2023, 2024, 2025, 2026 AND in L6M. Pass rate on raw R: counting 1.25 pct, ICT 1.76 pct, alt-bar counts 1.56 pct, IRL/ERL 1.41 pct of (cell, condition) rows against 0.58 pct for the nonsense conditions through the same rule; on MAE 2.7 / 1.8 / 2.7 / 4.0 pct against 0.52 pct. A small, real-looking excess, concentrated in a few cells (K7, A7, M7, P7 NY sessions, H7 London) and, for MAE, in trade-context counts (earlier signals in the session). Treat every pass as a lead for Stage 2, not a result: effects are 0.1-0.4 R on 60-500 yes-rows, the conditions are strongly correlated, and the raw-proxy outcome is the signal's hypothetical 1-minute bracket.**

Outcome used until W-PM's Stage 0 raw trades exist: for every signal not blocked by an open position (in_pos = 0) or taken, 2023-04..2026-10: R = hypothetical 1-minute bracket pnl / stop, MFE and MAE in stop units from the same path (the engine trade of taken signals is NOT used). Statistic: lift (yes minus no) with week-cluster-robust t (sandwich, ISO weeks); nonsense bar per (cell, outcome) from 200 nonsense conditions put through the same pipeline; stability from calendar-year lifts and L6M. Files: cols_cf6/s1_family2.csv (214,176 rows), s1_family2_passes.csv, s1_family2_passrates.csv, s1_family2_nonsense_bars.csv; code code/th_confl_cf6/s1_family2.py.

## Checklist item 2 (tick): conditions scored per family

| family | conditions | file | needs a feed D7 lacks |
|---|---|---|---|
| F2a candle counting (Brooks H/L, second entry, legs/pushes/wedge, bar number, DeMark, streaks, time counts, waves, horizontal counts, D7 own events) | 1,065 | cf6_cols_all.parquet | no (D7's own bars and signal list) |
| F2b ICT 7-13-21 count (5/15/60/240-min, daily/weekly) | 310 | cf6_ictB_all.parquet | no |
| F2c counts / streaks on range, renko, volume, 2000-tick bars | 322 | cf6_alt_all.parquet | other: alternate-bar stores from tape |
| F2d IRL / ERL sweeps (W-CF4) | 334 | cols_cf4/cf4_irl.parquet | no |
| nonsense (calibration) | 200 | cols_nonsense | - |

## Pass rates (15 cells, STACK excluded)

| family                                                      | outcome   |   rows |   beats |   stable_only |   passes |   pass_rate |
|:------------------------------------------------------------|:----------|-------:|--------:|--------------:|---------:|------------:|
| F2a_count_brooks_demark_streak_bar_legs_wave_time_horiz_own | MAE       |  14114 |  0.0512 |        0.1204 |      382 |      0.0271 |
| F2a_count_brooks_demark_streak_bar_legs_wave_time_horiz_own | MFE       |  14114 |  0.0279 |        0.1053 |      203 |      0.0144 |
| F2a_count_brooks_demark_streak_bar_legs_wave_time_horiz_own | R         |  14114 |  0.0219 |        0.1001 |      176 |      0.0125 |
| F2b_ict_7_13_21_count                                       | MAE       |   4139 |  0.0288 |        0.1061 |       75 |      0.0181 |
| F2b_ict_7_13_21_count                                       | MFE       |   4139 |  0.0215 |        0.0974 |       60 |      0.0145 |
| F2b_ict_7_13_21_count                                       | R         |   4139 |  0.0275 |        0.0986 |       73 |      0.0176 |
| F2c_count_streak_on_alt_bars                                | MAE       |   3461 |  0.0532 |        0.1257 |       93 |      0.0269 |
| F2c_count_streak_on_alt_bars                                | MFE       |   3461 |  0.0315 |        0.106  |       62 |      0.0179 |
| F2c_count_streak_on_alt_bars                                | R         |   3461 |  0.0257 |        0.1008 |       54 |      0.0156 |
| F2d_irl_erl_sweeps                                          | MAE       |   4475 |  0.0628 |        0.1377 |      177 |      0.0396 |
| F2d_irl_erl_sweeps                                          | MFE       |   4475 |  0.0235 |        0.0809 |       56 |      0.0125 |
| F2d_irl_erl_sweeps                                          | R         |   4475 |  0.0219 |        0.0878 |       63 |      0.0141 |
| NONSENSE                                                    | MAE       |   6200 |  0.01   |        0.0924 |       32 |      0.0052 |
| NONSENSE                                                    | MFE       |   6200 |  0.01   |        0.1002 |       32 |      0.0052 |
| NONSENSE                                                    | R         |   6200 |  0.01   |        0.0835 |       36 |      0.0058 |

## Top passes on raw R (trade-context counts excluded)

| family   | cell   | cond                            |   n_yes |   lift |   t_cr |   bar99 |   lift_L6M |   yr_pos |   yr_neg |
|:---------|:-------|:--------------------------------|--------:|-------:|-------:|--------:|-----------:|---------:|---------:|
| F2d_     | A7|4.0 | c4_irl_a_pd_int_against_15      |     664 | -0.276 | -4.812 |   2.397 |     -0.506 |        0 |        4 |
| F2b_     | M7|1.0 | c_N_ict_d_a40_exhaust_with_move |     336 |  0.211 |  4.525 |   2.32  |      0.216 |        4 |        0 |
| F2a_     | K7|2.0 | c_N_wv_3_in_w4_with             |      67 |  0.546 |  4.492 |   2.506 |      0.286 |        4 |        0 |
| F2d_     | A7|4.0 | c4_irl_a_pd_int_against_5       |     305 | -0.284 | -4.439 |   2.397 |     -0.738 |        0 |        4 |
| F2d_     | A7|4.0 | c4_irl_a_pd_int_against_30      |     954 | -0.246 | -4.418 |   2.397 |     -0.461 |        0 |        4 |
| F2b_     | A7|4.0 | c_N_ict_60_cday_against_78      |     204 | -0.42  | -4.411 |   2.397 |     -0.881 |        0 |        4 |
| F2b_     | K7|4.0 | c_N_ict_ntf_atkey_against_ge2   |     453 | -0.199 | -4.37  |   2.634 |     -0.256 |        0 |        4 |
| F2d_     | A7|4.0 | c4_irl_a_pd_int_against_60      |    1277 | -0.235 | -4.302 |   2.397 |     -0.375 |        0 |        4 |
| F2d_     | P7|4.0 | c4_irl_a_pd_int_against_60      |    2421 | -0.164 | -4.272 |   2.144 |     -0.272 |        0 |        4 |
| F2b_     | K7|4.0 | c_N_ict_240_a40_r4_against_78   |     154 | -0.331 | -4.147 |   2.634 |     -0.195 |        0 |        4 |
| F2b_     | K7|4.0 | c_N_ict_240_a40_against_78      |     155 | -0.322 | -4.06  |   2.634 |     -0.195 |        0 |        4 |
| F2a_     | K7|0.0 | c_N_dm_3_flip_against_w11       |    2311 |  0.109 |  3.944 |   2.393 |      0.022 |        4 |        0 |
| F2b_     | P7|0.0 | c_N_ict_ntf_atkey_with_ge1      |    2944 |  0.132 |  3.93  |   2.719 |      0.173 |        4 |        0 |
| F2b_     | P7|1.0 | c_N_ict_60_a40_against_2021     |     230 | -0.344 | -3.913 |   2.286 |     -0.432 |        0 |        4 |
| F2a_     | H7|1.0 | c_N_dm_15_cd_against_ge13       |      91 | -0.37  | -3.871 |   2.3   |     -0.098 |        0 |        4 |
| F2a_     | A7|5.0 | c_N_dm_15_nine_against_w11      |     545 | -0.259 | -3.817 |   2.446 |     -0.275 |        0 |        4 |
| F2c_     | A7|4.0 | c_N_sk_range8_upclose_with_ge3  |     867 |  0.125 |  3.795 |   2.397 |      0.135 |        4 |        0 |
| F2a_     | U7|1.0 | c_N_hz_5_break_from_box_with    |     347 |  0.236 |  3.762 |   2.685 |      0.312 |        3 |        0 |
| F2a_     | P7|3.0 | c_N_lg_3_pbleg2_against_active  |     359 | -0.2   | -3.734 |   2.528 |     -0.323 |        0 |        4 |
| F2a_     | K7|2.0 | c_N_dm_15_nine_perf_support_w11 |     124 |  0.427 |  3.694 |   2.506 |      0.29  |        4 |        0 |

Reading of the strongest R leads: (a) IRL: price intruding into the prior-day range AGAINST the trade (pd_int_against) is negative for A7 and P7 NY PM (-0.16 to -0.28 R, 4 of 4 years, L6M -0.27 to -0.74): a gate of the kind 'not when fighting the prior-day range'; (b) ICT: two or more timeframes at a key count AGAINST the trade is negative for K7 NY PM (-0.20 R, t -4.4); a daily exhaustion count WITH the move is positive for M7 London (+0.21 R); at-key-count with the trade positive for P7 Asia (+0.13 R); (c) DeMark: price flip against the trade within 11 bars +0.11 R in K7 Asia, perfected 9 support +0.43 R in K7 pre-market (124 rows); (d) 9/13 completed on the trade's side negative for A7 close and H7 London (-0.26 / -0.37 R); (e) alt bars: range-8 'three up closes with the trade' +0.125 R (A7 NY PM), volume-2000 higher-high streak +0.39 R (P7 pre, 88 rows). MAE passes are dominated by trade-context items (earlier signals in the session, same-direction runs, bar-number windows): later in a busy session the trade takes more heat, a volatility / clock proxy rather than a counting effect; they are listed, not dropped.

Caveats: (1) raw-proxy outcome, to be replaced by W-PM's raw trades; (2) cells with fewer than 300 usable rows are dropped, S7 and X1-X8 are not in the signal universe; (3) November 2026 rows excluded ('engine copy store'); (4) about 214k hypotheses: a pass rate of 1-2 pct against 0.6 pct for nonsense is an excess, but each lead still needs its Stage 2 walk-forward and the exact engine; (5) conditions with fewer than 60 yes or no rows in a cell are not scored.
