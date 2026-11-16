# DS3_REBUILD_S1_TAPELEGS - T-REBUILD Stage 1, addendum 2 (tape speed), pullback-leg vs impulse-leg speed (W-CF6), FIRST TABLE 2026-11-16

**VERDICT (data ends 2026-10-31; scored against the RAW-PROXY outcome, not yet Stage 0 raw trades): 416 pullback-vs-impulse tape-speed conditions (2 swing scales x 4 latencies 0/1/2/5 s x trades/s, contracts/s, MBO messages/s, aggressor split, duration and depth ratios, versus the impulse leg and versus the same half-hour 20-day median and percentile) scored in 15 book x session cells on R, MAE and MFE. Against the per-cell nonsense bar (99th percentile of |t_cr| of 200 nonsense conditions) and same sign in all 4 years and L6M, the pass rate on raw R is 1.0 pct for the breakout books (K7 M7 U7 H7) and 1.0 pct for the pullback books (P7 A7 O7), against 0.5 pct and 0.65 pct for nonsense: a marginal excess. On MAE the breakout books pass at 2.9 pct against 0.36 pct nonsense (a real excess: 'impulse faster than usual / pullback faster than impulse' goes with MORE adverse excursion in K7 NY AM: lift +0.085 to +0.09 R of heat, t 4.1-4.4, 4 of 4 years); pullback books 0.9 pct vs 0.7 pct. 95 pct of the latency-0 passes keep their sign and |t|>2 at 5 s latency, so completed-leg timing is not what drives them. Not a lead for D7 yet: effects 0.1-0.4 R on 130-1,400 yes-rows, correlated conditions, proxy outcome.**

## Definitions (exact)
Swings: causal ATR zig-zag pivots on 5-min bars (mult 1.0, 'l5') or 1-min bars (mult 3.0, 'l1'), a pivot known only at its confirmation bar. At the entry second minus latency (0/1/2/5 s): PULLBACK = the latest completed leg AGAINST the trade side (long: a down leg); IMPULSE = the leg before it (trade direction); 'fresh' = the pullback is the latest completed leg. Leg window = [start of the first pivot bar, end of the last pivot bar). Speed from W-CF2's per-second MBO tables (cf2_mbo3) summed per minute: trades/s, contracts/s (aggressor volume), MBO messages/s (adds + cancels + modifies + fills + trades; needs the L3 feed), aggressor split (share of trades / contracts initiated in the trade's direction). Reference: mean rate of the leg's end half-hour slot over the previous 20 calendar days, median ratio and percentile of the leg speed among those 20. Legs spanning market closes (< 50 pct of minutes with tape) are unknown (-1). Conditions c_T_<l5|l1>_<name>_L<lat> in /mnt/l2/l2vast/_confl/cols_cf6/cf6_tapelegs.parquet (100,860 signals; 416 yes/no conditions, 208 per swing scale, plus 56 raw v_T_* values at latency 0); raw per-minute tape: cf6_tapemin.parquet.

Feed flags for D7: trades/s, contracts/s and the aggressor split are computable from NT8 prints (no new feed); messages/s needs the L3 (MBO) feed; leg detection uses D7's own 1- or 5-minute bars.

## Pass rates (pass = |t_cr| above the cell nonsense 99th percentile AND same sign in 2023-2026 and L6M)

| grp                  | outcome   |   rows |   passes |   rate |   nonsense_rate |
|:---------------------|:----------|-------:|---------:|-------:|----------------:|
| breakout K7/M7/U7/H7 | MAE       |   6080 |      175 | 0.0288 |          0.0036 |
| breakout K7/M7/U7/H7 | MFE       |   6080 |       55 | 0.009  |          0.0056 |
| breakout K7/M7/U7/H7 | R         |   6080 |       60 | 0.0099 |          0.0053 |
| pullback P7/A7/O7    | MAE       |   4500 |       41 | 0.0091 |          0.0073 |
| pullback P7/A7/O7    | MFE       |   4500 |       67 | 0.0149 |          0.0046 |
| pullback P7/A7/O7    | R         |   4500 |       47 | 0.0104 |          0.0065 |

## Top passes, raw R, pullback books (P7 A7 O7)

| cell   | cond                      |   n_yes |   lift |   t_cr |   bar99 |   lift_L6M |   yr_pos |   yr_neg |
|:-------|:--------------------------|--------:|-------:|-------:|--------:|-----------:|---------:|---------:|
| P7|2.0 | l1_pbpct_tps_lt0.25_L0    |     158 |  0.363 |  3.696 |   2.325 |      0.398 |        4 |        0 |
| P7|0.0 | l1_imp_aggv_with_gt0.6_L0 |     268 |  0.223 |  3.452 |   2.719 |      0.239 |        4 |        0 |
| P7|4.0 | l1_ratio_tps_lt0.75_L0    |    1413 |  0.16  |  3.323 |   2.144 |      0.111 |        4 |        0 |
| P7|2.0 | l1_pbpct_cps_lt0.25_L0    |     164 |  0.337 |  3.212 |   2.325 |      0.227 |        4 |        0 |
| P7|4.0 | l1_ratio_cps_lt0.75_L0    |    1520 |  0.143 |  3.172 |   2.144 |      0.094 |        4 |        0 |
| A7|5.0 | l1_ratio_cps_gt1.5_L0     |     278 |  0.234 |  3.07  |   2.446 |      0.37  |        4 |        0 |
| A7|5.0 | l1_ratio_tps_gt1.5_L0     |     262 |  0.241 |  3.061 |   2.446 |      0.444 |        4 |        0 |
| P7|0.0 | l1_pbmed_tps_gt1.0_L0     |    3056 | -0.116 | -2.916 |   2.719 |     -0.246 |        0 |        4 |
| A7|1.0 | l5_imp_agg_with_lt0.5_L0  |    1219 |  0.127 |  2.88  |   2.257 |      0.22  |        4 |        0 |
| P7|0.0 | l5_pbmed_mps_lt0.75_L0    |     664 |  0.134 |  2.743 |   2.719 |      0.253 |        4 |        0 |

## Top passes, raw R, breakout books (K7 M7 U7 H7)

| cell   | cond                   |   n_yes |   lift |   t_cr |   bar99 |   lift_L6M |   yr_pos |   yr_neg |
|:-------|:-----------------------|--------:|-------:|-------:|--------:|-----------:|---------:|---------:|
| M7|4.0 | l5_pbmed_mps_lt0.75_L0 |     438 | -0.244 | -3.611 |   2.564 |     -0.439 |        0 |        4 |
| M7|2.0 | l5_pbpct_cps_lt0.25_L0 |     127 |  0.405 |  3.6   |   2.453 |      0.223 |        4 |        0 |
| M7|2.0 | l1_pbpct_tps_lt0.25_L0 |     134 |  0.369 |  3.545 |   2.453 |      0.23  |        4 |        0 |
| M7|4.0 | l1_pbpct_tps_lt0.25_L0 |     187 | -0.297 | -3.524 |   2.564 |     -0.122 |        0 |        4 |
| K7|3.0 | l5_pbmed_tps_gt1.5_L0  |     656 | -0.147 | -3.479 |   2.196 |     -0.079 |        0 |        4 |
| M7|2.0 | l5_pbpct_tps_lt0.25_L0 |     136 |  0.357 |  3.22  |   2.453 |      0.206 |        4 |        0 |
| K7|2.0 | l5_depth_gt0.618_L0    |     659 |  0.249 |  3.121 |   2.506 |      0.189 |        4 |        0 |
| K7|1.0 | l1_ratio_mps_gt1.5_L0  |     313 | -0.162 | -2.843 |   2.832 |     -0.207 |        0 |        4 |
| U7|0.0 | l1_impmed_tps_gt1.5_L0 |     214 |  0.194 |  2.65  |   2.31  |      0.071 |        4 |        0 |
| U7|0.0 | l1_impmed_cps_gt1.5_L0 |     217 |  0.183 |  2.419 |   2.31  |      0.073 |        4 |        0 |

## Top passes, MAE, breakout books (positive lift = more adverse excursion)

| cell   | cond                   |   n_yes |   lift |   t_cr |   bar99 |   lift_L6M |   yr_pos |   yr_neg |
|:-------|:-----------------------|--------:|-------:|-------:|--------:|-----------:|---------:|---------:|
| K7|1.0 | l5_pbpct_mps_lt0.25_L0 |     341 | -0.087 | -4.413 |   2.653 |     -0.088 |        0 |        4 |
| K7|3.0 | l5_ratio_tps_gt1.5_L0  |     600 |  0.087 |  4.215 |   2.338 |      0.103 |        4 |        0 |
| K7|3.0 | l5_ratio_cps_gt1.5_L0  |     620 |  0.085 |  4.142 |   2.338 |      0.089 |        4 |        0 |
| K7|3.0 | l5_impmed_mps_gt1.5_L0 |     814 |  0.091 |  4.11  |   2.338 |      0.062 |        4 |        0 |
| K7|3.0 | l5_ratio_mps_gt1.5_L0  |     609 |  0.083 |  3.949 |   2.338 |      0.098 |        4 |        0 |
| H7|1.0 | l1_pbmed_tps_gt1.5_L0  |     201 |  0.125 |  3.874 |   2.381 |      0.024 |        4 |        0 |
| M7|5.0 | l1_pbmed_cps_lt0.5_L0  |     253 | -0.165 | -3.838 |   2.561 |     -0.167 |        0 |        4 |
| M7|2.0 | l1_pbpct_tps_lt0.25_L0 |     134 | -0.16  | -3.621 |   2.345 |     -0.083 |        0 |        4 |
| K7|3.0 | l1_ratio_tps_gt1.5_L0  |     938 |  0.049 |  3.326 |   2.338 |      0.036 |        4 |        0 |
| M7|3.0 | l5_impmed_mps_gt1.5_L0 |     780 |  0.067 |  3.264 |   2.38  |      0.034 |        4 |        0 |

Reading: (a) 'pullback speed in the bottom quartile of its slot' (pbpct_tps_lt0.25) is positive for P7 pre-market and M7 pre-market (+0.36 to +0.41 R, 130-160 rows, 4 of 4 years) but NEGATIVE for M7 NY PM (-0.30 R): the same slow-pullback reading means different things per session, consistent with a thin-market artifact; (b) P7 NY PM: pullback slower than 0.75x the impulse speed +0.16 R (1,400 rows, 4 of 4 years, L6M +0.11) - the textbook 'weak pullback' reading holds in that cell; (c) A7 close: pullback faster than 1.5x the impulse is +0.24 R; (d) K7 NY AM: impulse faster than the slot median by 1.5x brings +0.09 R more adverse excursion. Latency: 95 pct of latency-0 passes survive 5 s latency with the same sign (the legs are completed minutes earlier). Caveats: raw-proxy outcome; leg speed is minute-resolution (legs are at least 10 minutes on 5-min swings); selection effect: legs are active periods so speed ratios to the slot median are above 1 on average (median 1.16).
