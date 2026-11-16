# DS3_REBUILD_S1_CF2 (W-CF2): Stage 1 contribution, families 5 (order flow: L3 arrival imbalance, L2 imbalance, walls, tape) and 7 (UW exposure/levels/tide/flow, QQQ gamma, CME options) - PROVISIONAL RAW BASE, FIRST PASS
VERDICT (data ends 2026-11-13; ): 482 conditions of families 5 and 7 scored per book x session against PROVISIONAL RAW (hyp1m bracket outcome, every universe signal, no layers): 14,369 (condition, cell) tests with n >= 100 each side, 370 beat the nonsense 99th-percentile bar of their cell (2.6% against about 1% expected by chance) and 243 of those keep the sign in >= 3 of 4 years and in L6M. This is a pre-check on hypothetical bracket outcomes of every universe signal (no layers, 1-minute path); the scored table that counts is W-CF3's against the W-PM raw trade table (engine 1-s paths). Conditions that need L3, UW or CME option feeds D7 lacks are flagged, not dropped. No PASS claim.

Basis: R = hypothetical bracket outcome / stop (R units) of every universe signal (193,628, to 2026-11-13) with the book's own target and stop from the entry table; MFE/MAE in points from the 1-minute path rows (outcome_type hyp1m; taken rows excluded from MFE/MAE because their path is the engine's). Cells = book x session (and book ALL sessions). Statistic: weekly-cluster t of (yes minus no); bar = 99th percentile of |t| of 200 persistent nonsense conditions (day-level component) in the same cell. Years and L6M computed for the rows that beat the bar. Rerun on the Stage 0 raw table: `RAW_TABLE=<parquet with sig_id, R, mfe, mae> python3 code/th_confl_cf2/rebuild_s1.py`.

## Checklist items covered by this contribution (count of conditions scored)

- Item 5 (order flow): L3 arrival imbalance (windows 15-300 s x distances 2/5/10/20 ticks x count/size, 90; windows 15/30/60/120 x percentiles 10/20/30, 48), L3 order-by-order absolute thresholds (55), L3 drift-robust (38), L2 imbalance/walls/pull-add/microprice/spread/resilience (49), L2 proxy of the L3 lead (2), L1 tape (52). The 'L2 entry gate' is an engine layer with no per-signal column on the box (not scored here). The T-FLOW library (282 representatives) is W-FL1's column set.
- Item 7 (options and positioning): UW gamma/OI levels, flips, walls, tide, flow bursts, IV term, CME NQ option snapshots (implied move, 0DTE flip/walls), QQQ gamma (148).

## Per family: tests, beating the bar, feed needed

| family                                                    |   tests |   beat_bar |   beat_pct | feed   |   conditions |
|:----------------------------------------------------------|--------:|-----------:|-----------:|:-------|-------------:|
| 5 L2 imbalance/walls/depth                                |    1568 |         41 |        2.6 | L2     |           49 |
| 5 L2 proxy of the L3 lead                                 |      66 |          2 |        3   | L2     |            2 |
| 5 L3 arrival imbalance (windows x distances x count/size) |    3019 |         71 |        2.4 | L3     |           90 |
| 5 L3 arrival imbalance (windows x percentiles)            |    1505 |         29 |        1.9 | L3     |           48 |
| 5 L3 drift-robust                                         |    1284 |         28 |        2.2 | L3     |           38 |
| 5 L3 order-by-order (absolute thresholds)                 |    1661 |         36 |        2.2 | L3     |           55 |
| 5 tape (L1)                                               |    1692 |         62 |        3.7 | L1     |           52 |
| 7 UW exposure/levels/tide/flow, QQQ gamma, CME options    |    3574 |        101 |        2.8 | UW     |          148 |

## Largest stable effects on mean R (same sign in >= 3 of 4 years and in L6M), 40 rows

| book   | sess   | cond                        |   n_yes |   liftR |    tR |   bar |   liftMFE |   liftMAE |   years_same | feed        |
|:-------|:-------|:----------------------------|--------:|--------:|------:|------:|----------:|----------:|-------------:|:------------|
| P7     | 3.0    | c_F_no_absorb_100           |     888 |  -0.209 | -5.19 |  2.67 |     -4.07 |      7.37 |            3 | L1          |
| A7     | 0.0    | c_J_flip_far100_NDX_vol     |    2029 |   0.224 |  4.43 |  2.17 |     12.06 |     -0.06 |            3 | UW          |
| K7     | 0.0    | c_F_big10_noagainst15       |    9777 |  -0.051 | -4.25 |  2.23 |     -2.58 |     -0.13 |            4 | L1          |
| M7     | 4.0    | c_J_beyond_flip_Nh_vol      |    2410 |   0.347 |  4.08 |  2.25 |      8.11 |     -8.63 |            3 | CME options |
| M7     | 3.0    | c_F_ice_against5_eq0        |     462 |  -0.238 | -4.06 |  2.78 |     -2.93 |      9.88 |            3 | L1          |
| A7     | 0.0    | c_J_em_used_lt0.5_Nh        |    2351 |  -0.308 | -4.01 |  2.17 |    -11.73 |      3.5  |            3 | CME options |
| A7     | 0.0    | c_J_em_room_ge150_Nh        |    2298 |  -0.285 | -3.96 |  2.17 |     -5.37 |      8.12 |            3 | CME options |
| M7     | 1.0    | c_J_0dte_flip_far50_Nd_oi   |    2610 |  -0.242 | -3.93 |  2.43 |     -4.09 |      2.75 |            3 | CME options |
| A7     | ALL    | c_F_ret5_pos                |   19920 |  -0.055 | -3.82 |  2.57 |     -0.6  |      1.63 |            4 | L1          |
| K7     | 0.0    | c_H_no_sweep3_against300    |    4726 |  -0.047 | -3.78 |  2.23 |     -9.31 |     -7.01 |            4 | L3          |
| M7     | ALL    | c_J_flip_far25_NDX_vol      |   17106 |   0.133 |  3.77 |  2.7  |      5.72 |     -1.74 |            3 | UW          |
| M7     | 1.0    | c_J_0dte_flip_far25_Nd_oi   |    2902 |  -0.314 | -3.76 |  2.43 |     -6.06 |      5.51 |            3 | CME options |
| K7     | ALL    | c_F_rvol15_ge1.6            |    6292 |   0.049 |  3.73 |  2.43 |      3.59 |      1.21 |            4 | L1          |
| M7     | ALL    | c_J_0dte_flip_far50_Nd_oi   |    6231 |  -0.174 | -3.72 |  2.7  |     -3.63 |      2.57 |            3 | CME options |
| P7     | 3.0    | c_H_no_aggr50_against300    |    3912 |  -0.1   | -3.69 |  2.67 |     -3.35 |      1.9  |            4 | L3          |
| A7     | 3.0    | c_G_behind_added30          |    3294 |   0.197 |  3.62 |  2.35 |      4.02 |     -5.69 |            4 | L2          |
| A7     | 1.0    | c_H2_touch_mine_sz_hi       |     587 |   0.143 |  3.61 |  2.81 |      4.34 |     -3.94 |            4 | L3          |
| M7     | 1.0    | c_J_flip_far25_NDX_vol      |    7350 |   0.176 |  3.61 |  2.43 |      6.5  |     -3.07 |            3 | UW          |
| A7     | ALL    | c_F_cd5_pos                 |   17798 |  -0.055 | -3.59 |  2.57 |     -1.31 |      0.84 |            4 | L1          |
| M7     | 1.0    | c_H2_gmax_with60_lo         |    4824 |  -0.059 | -3.58 |  2.43 |     -2.83 |      0.38 |            3 | L3          |
| P7     | 4.0    | c_F_cdz5_ge1.0              |    1681 |  -0.08  | -3.57 |  2.87 |     -1.41 |      1.8  |            4 | L1          |
| A7     | 0.0    | c_J_em_room_ge150_Nd        |    1848 |  -0.249 | -3.52 |  2.17 |     -5.02 |      8.9  |            3 | CME options |
| K7     | 0.0    | c_J_em_frac_pos_Nd          |    3830 |   0.131 |  3.52 |  2.23 |      3.86 |     -3.68 |            3 | CME options |
| A7     | ALL    | hi_w120_n_p10               |    1525 |   0.093 |  3.47 |  2.57 |     -1.05 |     -6.07 |            4 | L3          |
| M7     | 1.0    | c_H2_spoof_mine_gt_ahead300 |    2754 |   0.092 |  3.44 |  2.43 |      3.85 |     -1.05 |            4 | L3          |
| P7     | 3.0    | c_F_rvol5_ge1.6             |     379 |   0.199 |  3.44 |  2.67 |      6.95 |     -2.61 |            4 | L1          |
| P7     | 3.0    | c_F_big10_noagainst5        |     608 |  -0.167 | -3.43 |  2.67 |     -5.93 |      3.41 |            4 | L1          |
| M7     | 4.0    | c_J_flip_far100_SPX_vol     |    2903 |   0.246 |  3.42 |  2.25 |      4.15 |     -6.2  |            3 | UW          |
| M7     | 3.0    | c_H2_aggr20_with300_lo      |     213 |  -0.243 | -3.41 |  2.78 |    -10.37 |      0.26 |            3 | L3          |
| K7     | 0.0    | c_L3X_imb_n10_60_hi         |    4974 |  -0.041 | -3.41 |  2.23 |     -1.17 |      1.16 |            4 | L3          |
| M7     | 3.0    | c_G_imb5m60_ge0.0           |    2399 |  -0.084 | -3.41 |  2.78 |     -1.47 |      2.32 |            4 | L2          |
| M7     | ALL    | c_L3X_imb_n5_300_lo         |    6684 |   0.05  |  3.4  |  2.7  |      0.5  |     -1.17 |            4 | L3          |
| M7     | 3.0    | c_H_aggr20_with300_ge1      |    6166 |   0.241 |  3.39 |  2.78 |     10.31 |     -0.23 |            3 | L3          |
| K7     | 0.0    | c_L3X_imb_n2_60_hi          |    5037 |  -0.041 | -3.38 |  2.23 |     -1.28 |      1.12 |            4 | L3          |
| K7     | 0.0    | c_L3X_imb_v10_60_hi         |    4968 |  -0.041 | -3.34 |  2.23 |     -1.17 |      1.04 |            4 | L3          |
| K7     | ALL    | c_J_gex_pos_SPY_oi          |    3515 |   0.083 |  3.31 |  2.43 |     -2.05 |     -5.08 |            3 | UW          |
| M7     | 5.0    | lo_w60_n_p10                |     223 |   0.194 |  3.31 |  2.38 |      3.13 |     -4.46 |            3 | L3          |
| K7     | ALL    | c_F_rvol5_ge1.6             |   10273 |   0.033 |  3.31 |  2.43 |      1.77 |      0.28 |            4 | L1          |
| M7     | ALL    | c_J_0dte_flip_far25_Nd_oi   |    6724 |  -0.232 | -3.29 |  2.7  |     -4.76 |      3.89 |            3 | CME options |
| A7     | ALL    | c_L3X_imb_n20_15_hi         |    4384 |   0.06  |  3.29 |  2.57 |     -0.73 |     -3.86 |            4 | L3          |

## Per cell: how many conditions beat the bar (chance level about 1% of 482)

| book   | sess   |   tests |   beat |
|:-------|:-------|--------:|-------:|
| A7     | 0.0    |     415 |     38 |
| A7     | 1.0    |     429 |      6 |
| A7     | 2.0    |     324 |      3 |
| A7     | 3.0    |     354 |     18 |
| A7     | 4.0    |     362 |      7 |
| A7     | 5.0    |     361 |      0 |
| A7     | ALL    |     476 |     25 |
| H7     | 0.0    |     299 |      0 |
| H7     | 1.0    |     313 |      2 |
| H7     | 3.0    |     195 |      8 |
| H7     | 4.0    |     171 |      1 |
| H7     | ALL    |     434 |      6 |
| K7     | 0.0    |     433 |     54 |
| K7     | 1.0    |     436 |      8 |
| K7     | 2.0    |     358 |      5 |
| K7     | 3.0    |     433 |     11 |
| K7     | 4.0    |     435 |      6 |
| K7     | 5.0    |     428 |      0 |
| K7     | ALL    |     482 |     17 |
| M7     | 1.0    |     439 |     21 |
| M7     | 2.0    |     388 |      5 |
| M7     | 3.0    |     441 |     20 |
| M7     | 4.0    |     447 |     12 |
| M7     | 5.0    |     438 |     17 |
| M7     | ALL    |     480 |      8 |
| O7     | 3.0    |     151 |      1 |
| O7     | ALL    |     151 |      1 |
| P7     | 0.0    |     434 |      6 |
| P7     | 1.0    |     441 |      9 |
| P7     | 2.0    |     392 |      2 |
| P7     | 3.0    |     448 |     20 |
| P7     | 4.0    |     459 |      5 |
| P7     | 5.0    |     451 |      3 |
| P7     | ALL    |     481 |     15 |
| U7     | 0.0    |     290 |      6 |
| U7     | 1.0    |     313 |      3 |
| U7     | 3.0    |     169 |      1 |
| U7     | ALL    |     418 |      0 |

## Feed flags
L1 = NT8 prints (D7 computes today); L2 = NT8 depth (D7 has it live; depth-pollution fix first); L3 = live market-by-order feed + sidecar (DS3_CONFLUENCE_L3_LIVE_SPEC.md); UW = Unusual Whales feed; CME options = CME NQ option snapshots. Per column: cols_cf2/column_classification.csv and REBUILD_S1_CF2_conditions.csv. Stats: cols_cf2/REBUILD_S1_CF2_stats.csv.
