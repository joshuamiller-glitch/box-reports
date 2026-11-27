# DYNEXIT ATTRIBUTION (W-DYNA): does an exit signal carry information about the rest of a live-book trade?

Answer first: see the table at the bottom (auto-updated). Harness is live; everything is research only (no engine, no live, nothing bought).

## What it measures
For each exit signal, on the 22,063 past trades of the 9 live-book streams (Asia MF1-MF4, NY AM MF5-MF9; Apr 2023 - Oct 2026; 21,244 pass the price-path check): the FIRST moment the signal is ON while the trade is open and at a LOSS (open R <= -0.15) = loss side, or in PROFIT (open R >= +0.15) = profit side. Outcome of the rest of the trade (to the book's ORIGINAL exit, fixed bracket + Trade Health + time exit all as they were): remaining P&L in R (R = the trade's stop distance), P(exit by Target), P(exit by Stop), MAE and MFE of the remainder. Compared with a matched null: the 200 nearest moments (same book, other trades) in (open R, time in trade) space, moments every 60 s. Effect d = fire minus null remaining P&L in R. d < 0: the trade did worse than a random matched moment after the signal (information to EXIT / TAKE; exit gain = -d R per fired event, before any trading cost of the exit itself). d > 0: better (HOLD / PRESS).

## Decision rule (fixed before the first table)
Fit = first 60 % of trades by entry time, HOLD = last 40 %. Signal parameters are fixed a priori (no tuning on these trades; where a signal needs past-trade percentiles they use only trades closed before the entry). Carries information: YES iff (1) BH q <= 0.05 on the holdout day-block bootstrap p, BH over ALL (signal, side) pairs ever tried (non-control), (2) >= 100 holdout events, (3) the fit part has the same sign of d. Effect size always printed; |d| < 0.03 R is statistically real but not tradeable. Controls: a random-moment signal (must show nothing) and a future-leaking signal (must show a big effect); not charged.
Caveats: the 9 books were picked on the same weeks (selection); the book's exit (UWTime / Trade Health / policy) is inside the "remaining P&L", so d answers "hold to the original exit vs leave now", not "bracket vs no bracket"; a positive exit gain is before slippage/fees of exiting early (the walk-forward and exact engine decide that); 5-s grid, bars complete at their end (causal, one second conservative); the matched null is by (open R, time) only, so a signal that merely marks "a trade that is stuck at -0.5R for 2 hours" is credited if it beats the random matched moment. Luck charge: the number of signals tried is printed in the table header; BH handles it.

## How to use it (other agents)
1. Code: code/th_dynexit/attrib.py (API), attrib_run.py (runner), attrib_build.py (path store builder). Path store: /mnt/l2/l2vast/_dynexit/attrib/paths/ (5-s grid, 1 h pre-entry window; built from W-DYNX8's tape + entries3). Results: /mnt/l2/l2vast/_dynexit/attrib/results.jsonl (append only), table.csv, all_rows.csv, per-signal events ev/<signal>.parquet (event level, with null columns n_*).
2. Write /mnt/l2/l2vast/_dynexit/attrib/signals_<agent>.py with `SIGNALS = [Signal(name, family, agent, fn, desc)]`, `from attrib import Signal` (sys.path.insert(0, 'code/th_dynexit')). fn(p) gets a Path: arrays on the 5-s grid p.t, p.ns, p.px, p.hi, p.lo, p.vol (also the hour BEFORE entry, index < p.i0), p.openR, p.advR, p.favR (cumulative worst/best open R), p.live; scalars p.side, p.S0, p.T0, p.entry_px, p.book, p.mix, p.lots, p.i0; p.bars(60) = clock-aligned COMPLETE bars (o,h,l,c,v,end,tend) and p.expand(arr, bars) to put a per-bar series back on the grid; p.et_secs() = seconds since ET midnight. Return None, a grid index, or a bool mask over the grid (True where the signal is ON; the first ON in each side region counts). For other markets/UW/etc. join on p.ns (absolute ns).
3. Run: `nice -n 15 python3 -I code/th_dynexit/attrib_run.py signals_<agent> --workers 8` (about 20-60 s per signal; runs a causality check first: the fire must not move when the path is cut at the fire) then the table below refreshes. Or tell me in MORNING.md and I run it.
4. Signals that say YES with a stated direction and effect go to the walk-forward and exact engine (that is step 2 of the catalogue); the entries without YES are screen noise as far as the live-book past trades can tell.


## First table summary (03:55Z, W-DYNA a-priori signals)
25 signals defined by me at one textbook default each (free settings searched: 0; the default IS the committed setting, so fit/hold is a stability check only), evaluated inside the trade at 1-min / 5-min bar rate (dynamic, not set once); 50 (signal, side) tests charged in BH. RESULT: 0 of 50 carry information (best q = 0.30: x12_mfe_p50 profit side d=-0.031R, x17_w60cross loss side +0.042R (fit part 0.001R), x17_w60mean profit side -0.073R). Everything is within +-0.08 R, same as chance (about 2-3 of 50 expected raw p<0.05; 6 seen). Not evaluated: x16_supertrend5 (failed the causality check at short paths, dropped), x18_clk_0229/0829/0929/1359/1555 (the books are never open at those clock times in a loss/profit region). Controls pass (random time d=0.00, leak d=-0.23R). Consistent with W-DYNB1 (no information in X12/X16/X17/X18) and W-DYNOF. For other agents' committed defaults (fixed_rules_b1/b2/dynh.json): add them as signals_<agent>.py with the committed setting and name the file in MORNING.md; the table will show the setting in the signal name/desc.

## Combined result (06:20Z): 4 of 149 (signal, side) tests pass, all tiny or artefacts
Subjects extended: London (LO 3 books) and NY PM (NP 3 books; NP_MF2 dropped, no stop/target exits to read the bracket from) added to AS/NY AM; 75 signals incl. ports of W-DYNOF X14/X19, W-DYNB2 X15/X20, X24 count, MBO-derived 1-s aggregates (proxies), X23b sweep/reclaim, combinations (2/3 of k), static twins. Passes: (1) x18_clk_0829 loss and profit side, London only: leaving at 08:29 ET, one minute before the book's own 08:30 time exit, saves 0.04 R per trade (the 08:30 data print costs these trades on average): a time-exit-edge artefact, not a new exit. (2) of_x19_T2_toend15 profit side, d=-0.049 R (Asia -0.074, NY AM -0.038): flatten in profit 15 min before the session end (W-DYNOF survivor reproduced; loss side 0 information); it still has to beat the exact engine and costs. (3) of_x19_L1_NQ_ahead_of_ES_30 profit side n=114, HOLD +0.17 R, fit part +0.007: rare, ES exists only from 2023-08, treat as noise. NY PM (NP): no (signal, side) test is significant on its own (W-PLAN-NP found 0 of 108; consistent). Near misses all say HOLD after loss-side signals (+0.02 to +0.04 R, fit part about 0): x17_w60cross, mbo_best_cleared_own, x24 count, sweep-against, iceberg refill, combo_all_2of16: not exit information, and not stable on the fit part. The static twins of the moving inputs (frozen at entry) give the same answers as the dynamic ones (x17_w60cross loss side +0.042 R dynamic vs +0.042 R static; see the table rows x17_w60cross/x17_w60mean/x18_vc_contract and their _STATIC twins) so updating inside the trade adds nothing measurable. Region x book-type cells: 0 of 512 pass BH (best q=0.085: x18_clk_0829 L_mid, toend15 on fade books). Combinations (2 of 6 momentum ... 3 of 16 all): no stronger than their parts. Not done: order-level MBO items (wall persistence by order age, per-order iceberg, cancel-vs-trade at a named wall, stop-run footprint) and the X23 liquidity hit-rate table: they need raw MBO per trade window (about 20,000 trade-hours); MBO exists 2023-04-02..2026-11-13 in /mnt/l2/l2vast/raw/NQ_mbo (Y2023_04_2024_04, Y2024_05_2025_04, Y2025_05_2026_04, L3M, TAIL_20261105): all months can be READ in place (read-only) with output kept in memory / server C; I used the 1-s book-event aggregates (depletion by trade/cancel, refills, sweeps, cleared levels) as proxies and none carries information. Test 5 qualifiers' entries not added yet.


## Order-level MBO walls (07:00Z, W-DYNA; sample months only)
dyn_mbo.py replays raw/NQ_mbo day files (read only, box1) for every second of every open live-book trade in 8 sample months (2023-06, 2023-09, 2024-01, 2024-06, 2024-10, 2025-03, 2025-09, 2026-06; 206 UTC day files, 6,207 trades: AS 1,032, NY AM 2,996, London 974, NY PM 1,205; output 26 MB, assembled on server C as store v3). Per 5-s bar: behind wall (support at the stop side) and ahead wall (in front of the target): size, share resting >= 120 s (order age), distance, cancelled vs traded size at the wall tick, pulled / consumed events, iceberg-like refills. 12 signals x 2 sides = 24 tests, BH over them: 0 pass (best q = 0.16: cancel-versus-trade at the behind wall, iceberg refill at the behind wall, behind wall pulled / consumed, all profit side with HOLD sign +0.06 to +0.10 R and fit part of the opposite sign). Sample is small (n 100-700 per test, se about 0.04 R; the random-time control itself reads +0.08 to +0.10 R at p 0.05 on this sample), so only a large effect would show: none does. Wall persistence by order age, iceberg refill, cancel-versus-trade and the footprint of a consumed behind wall carry no exit information in these months. Not done on the full history (it would be the 1,130 day files, about 2 h on 6 processes).

## Results table (auto)

<!-- TABLE-START (auto) -->

updated 27 Nov 06:16Z UTC. Store v2 = AS + NY AM + London + NY PM live-book trades (about 33,800 trades), signals tried: 75 (non-control, 0 free settings searched: every one is a single fixed default; some are ports of other agents committed defaults, column default), (signal, side) tests charged in BH: 149; information YES: 4.

Raw p<0.05: 34 of 149 (chance 7.5). Mean d over all loss-side tests +0.014 R (positive: after a loss-side signal trades do slightly BETTER than a matched random moment, i.e. hold, not exit), profit side +0.002 R.

| signal | family | side | n hold | d R | d_fit R | p_plain | p_block | q BH | dT pp | dS pp | dMAE R | dMFE R | committed default of | info |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| x18_clk_0829 | X18 | loss | 215 | -0.038 | -0.025 | 0.000 | 0.000 | 0.025 | -13.7 | -28.7 | +0.232 | -0.292 |  | YES EXIT |
| of_x19_T2_toend15 | X19 | profit | 889 | -0.049 | -0.025 | 0.000 | 0.000 | 0.025 | -19.5 | -9.0 | +0.163 | -0.162 | W-DYNOF survivor (Asia flatten-profit) | YES EXIT |
| x17_w60cross | X17 | loss | 4133 | +0.042 | -0.009 | 0.002 | 0.000 | 0.025 | +3.8 | +2.5 | -0.004 | +0.048 |  | no |
| mbo_best_cleared_own | X14m | loss | 10321 | +0.030 | -0.001 | 0.001 | 0.001 | 0.037 | +3.1 | +2.0 | -0.009 | +0.040 |  | no |
| x18_clk_0829 | X18 | profit | 130 | -0.046 | -0.048 | 0.001 | 0.001 | 0.037 | -47.3 | -11.0 | +0.353 | -0.247 |  | YES EXIT |
| of_x19_L1_NQ_ahead_of_ES_30 | X19 | profit | 114 | +0.170 | +0.007 | 0.003 | 0.001 | 0.037 | +29.7 | -7.7 | +0.075 | +0.049 |  | YES HOLD |
| x17_w60cross_STATIC | X17s | loss | 3458 | +0.042 | -0.002 | 0.001 | 0.002 | 0.047 | +3.2 | +2.4 | -0.003 | +0.048 |  | no |
| x24_count_against2 | X24 | loss | 9334 | +0.029 | -0.003 | 0.001 | 0.002 | 0.047 | +2.6 | +2.5 | -0.009 | +0.041 | W-DYNL x24 count cutoff -2 (committed) | no |
| mbo_sweep_against150 | X14m | loss | 3758 | +0.039 | -0.001 | 0.001 | 0.004 | 0.060 | +5.8 | +1.8 | +0.008 | +0.028 | W-DYNOF M9 threshold | no |
| mbo_iceberg_refill_x3 | X14m | loss | 6109 | +0.032 | -0.007 | 0.004 | 0.004 | 0.060 | +3.2 | +2.6 | -0.009 | +0.047 |  | no |
| combo_all_2of16 | X22c | loss | 9277 | +0.026 | -0.003 | 0.003 | 0.005 | 0.068 | +2.6 | +2.7 | -0.011 | +0.041 |  | no |
| x18_clk_1555 | X18 | loss | 131 | -0.098 | -0.044 | 0.004 | 0.008 | 0.105 | -15.6 | -23.5 | +0.099 | -0.239 |  | no |
| x12_mae_w75 | X12 | loss | 7519 | +0.024 | -0.010 | 0.008 | 0.010 | 0.115 | +1.2 | +2.6 | +0.001 | +0.040 |  | no |
| of_x14_F1_dlt_W15_t30 | X14 | loss | 7951 | +0.023 | -0.010 | 0.011 | 0.013 | 0.130 | +1.9 | +2.5 | -0.009 | +0.039 |  | no |
| x24_count_against3 | X24 | loss | 8111 | +0.025 | -0.008 | 0.007 | 0.013 | 0.130 | +2.8 | +2.7 | -0.008 | +0.037 |  | no |
| x12_mfe_p50 | X12 | profit | 5676 | -0.019 | -0.015 | 0.025 | 0.014 | 0.130 | -3.1 | -0.2 | +0.010 | -0.016 |  | no |
| mbo_sweep_with300 | X14m | profit | 1301 | -0.052 | -0.035 | 0.003 | 0.019 | 0.137 | +7.2 | +1.2 | -0.013 | -0.062 |  | no |
| x18_vc_exp_adv | X18 | loss | 6254 | +0.027 | +0.007 | 0.006 | 0.019 | 0.137 | +2.5 | +3.5 | -0.011 | +0.047 |  | no |
| of_x19_L1_NQ_ahead_of_ES_15 | X19 | profit | 444 | +0.076 | +0.022 | 0.012 | 0.022 | 0.137 | +20.2 | -1.4 | -0.018 | +0.010 | W-DYNOF committed X19 profit | no |
| combo_mom_2of6 | X22c | loss | 7203 | +0.024 | -0.014 | 0.006 | 0.017 | 0.137 | +2.8 | +2.3 | -0.009 | +0.037 |  | no |
| combo_flow_2of3 | X22c | loss | 4285 | +0.030 | -0.005 | 0.012 | 0.021 | 0.137 | +0.7 | +1.7 | -0.007 | +0.050 |  | no |
| combo_all_3of16 | X22c | loss | 8628 | +0.021 | -0.007 | 0.017 | 0.022 | 0.137 | +2.5 | +2.8 | -0.012 | +0.036 |  | no |
| mbo_depl_cancel_own_x3 | X14m | loss | 3775 | +0.032 | -0.008 | 0.014 | 0.019 | 0.137 | +4.4 | +3.1 | -0.015 | +0.049 |  | no |
| of_x14_F1_dlt_W60_t30 | X14 | loss | 4066 | +0.031 | -0.007 | 0.016 | 0.019 | 0.137 | +0.9 | +1.7 | -0.005 | +0.050 |  | no |
| x12_mae_w90 | X12 | loss | 5697 | +0.020 | -0.009 | 0.015 | 0.027 | 0.160 | +0.2 | +2.9 | +0.017 | +0.019 | W-DYNB1 committed X12 loss | no |
| mbo_depl_trade_own_x3 | X14m | loss | 6891 | +0.022 | -0.013 | 0.018 | 0.030 | 0.160 | +2.5 | +2.7 | -0.009 | +0.037 |  | no |
| mbo_cancel_dominates | X14m | loss | 5971 | +0.024 | -0.011 | 0.014 | 0.028 | 0.160 | +3.5 | +3.3 | -0.017 | +0.045 |  | no |
| of_x14_F1_dlt_W15_t50 | X14 | loss | 4253 | +0.029 | -0.010 | 0.012 | 0.029 | 0.160 | +0.4 | +1.6 | -0.008 | +0.045 |  | no |
| x16_donch20 | X16 | loss | 5133 | +0.022 | -0.010 | 0.032 | 0.032 | 0.164 | +2.3 | +2.2 | -0.008 | +0.036 |  | no |
| x24_count_against3 | X24 | profit | 2087 | +0.035 | -0.012 | 0.044 | 0.035 | 0.176 | +7.4 | +2.2 | -0.035 | +0.068 |  | no |
| x18_vc_exp_fav | X18 | loss | 4493 | +0.026 | +0.002 | 0.052 | 0.038 | 0.183 | +4.1 | +5.5 | -0.026 | +0.063 |  | no |
| x18_clk_1555 | X18 | profit | 99 | -0.079 | -0.039 | 0.030 | 0.042 | 0.192 | -27.5 | -9.7 | +0.141 | -0.148 |  | no |
| x12_mfe_p75 | X12 | profit | 1227 | -0.045 | -0.036 | 0.029 | 0.042 | 0.192 | -13.4 | +0.1 | -0.014 | +0.014 |  | no |
| x16_slope20 | X16 | loss | 4690 | +0.024 | -0.009 | 0.028 | 0.049 | 0.215 | +3.0 | +2.9 | -0.015 | +0.040 |  | no |
| x16_3bar | X16 | loss | 7015 | +0.018 | -0.013 | 0.050 | 0.065 | 0.277 | +2.1 | +2.6 | -0.011 | +0.033 |  | no |
| x16_bb20 | X16 | profit | 4671 | +0.018 | -0.008 | 0.073 | 0.074 | 0.306 | +3.6 | +1.3 | -0.019 | +0.034 |  | no |
| of_x19_C1_RTY_adv10 | X19 | profit | 1054 | -0.041 | -0.019 | 0.067 | 0.090 | 0.341 | +9.6 | +5.3 | -0.064 | +0.001 |  | no |
| x17_w60mean | X17 | profit | 2000 | -0.027 | -0.028 | 0.086 | 0.086 | 0.341 | +2.1 | +2.2 | -0.047 | +0.003 |  | no |
| of_x19_C1_ES_adv10 | X19 | profit | 196 | +0.101 | +0.118 | 0.050 | 0.091 | 0.341 | +25.0 | +1.2 | -0.037 | +0.071 |  | no |
| x16_ha5 | X16 | loss | 4622 | +0.020 | -0.011 | 0.071 | 0.087 | 0.341 | +3.9 | +3.3 | -0.020 | +0.045 |  | no |
| x23b_behind_reclaim | X23b | loss | 2016 | +0.025 | -0.021 | 0.127 | 0.106 | 0.356 | +4.8 | +2.9 | -0.018 | +0.051 |  | no |
| x23b_ahead_reject | X23b | loss | 1853 | +0.032 | +0.026 | 0.101 | 0.098 | 0.356 | +10.2 | +7.7 | -0.053 | +0.080 |  | no |
| of_x14_F1_dlt_W60_t70 | X14 | profit | 40 | -0.238 | +0.053 | 0.091 | 0.112 | 0.356 | -2.8 | +12.2 | -0.210 | +0.082 |  | no |
| of_x14_F1_dlt_W60_t50 | X14 | loss | 1250 | +0.038 | -0.009 | 0.067 | 0.103 | 0.356 | +0.1 | +2.9 | -0.013 | +0.071 | W-DYNOF committed X14 loss | no |
| of_x19_L1_NQ_ahead_of_ES_15 | X19 | loss | 185 | +0.093 | +0.024 | 0.101 | 0.112 | 0.356 | +16.9 | +1.3 | -0.004 | +0.085 | W-DYNOF committed X19 profit | no |
| x17_w60mean_STATIC | X17s | profit | 1763 | -0.028 | -0.031 | 0.087 | 0.108 | 0.356 | +1.7 | +2.2 | -0.046 | -0.001 |  | no |
| of_x19_C1_ES_adv30 | X19 | profit | 15 | +0.260 | +nan | 0.140 | 0.108 | 0.356 | +36.3 | -5.7 | +0.095 | +0.128 |  | no |
| x16_rsi14 | X16 | loss | 1472 | +0.039 | -0.001 | 0.053 | 0.118 | 0.368 | +3.1 | +1.0 | +0.002 | +0.035 |  | no |
| combo_anch_2of3 | X22c | loss | 2649 | +0.023 | -0.015 | 0.121 | 0.122 | 0.372 | +6.1 | +5.2 | -0.036 | +0.070 |  | no |
| x16_macd | X16 | loss | 5670 | +0.017 | -0.009 | 0.094 | 0.130 | 0.389 | +2.8 | +3.2 | -0.015 | +0.039 | W-DYNB1 committed X16 loss (MACD flip) | no |
| combo_mom_3of6 | X22c | loss | 5106 | +0.016 | -0.011 | 0.131 | 0.147 | 0.422 | +2.6 | +2.9 | -0.013 | +0.040 |  | no |
| of_x14_F5_absorb_W120_z40 | X14 | profit | 146 | -0.090 | +0.024 | 0.117 | 0.147 | 0.422 | -4.3 | +4.6 | -0.055 | -0.004 |  | no |
| of_x14_F1_dlt_W60_t30 | X14 | profit | 1741 | +0.028 | -0.012 | 0.143 | 0.166 | 0.466 | +1.7 | +3.0 | -0.033 | +0.076 |  | no |
| x18_clk_0959 | X18 | profit | 365 | -0.059 | +0.011 | 0.108 | 0.180 | 0.496 | +16.2 | +7.2 | -0.048 | -0.024 |  | no |
| b2_x20_peer_stop | X20 | loss | 1725 | +0.026 | -0.009 | 0.105 | 0.186 | 0.504 | +4.9 | +3.4 | +0.002 | +0.024 | W-DYNB2 committed X20 (cut-loss branch tested as ON at loss) | no |
| x18_clk_0229 | X18 | profit | 97 | +0.094 | -0.007 | 0.167 | 0.196 | 0.512 | +19.4 | +1.1 | -0.038 | +0.068 |  | no |
| of_x14_F5_absorb_W30_z40 | X14 | profit | 847 | -0.035 | -0.010 | 0.163 | 0.194 | 0.512 | -4.7 | +3.9 | -0.057 | +0.046 |  | no |
| x16_ema9_21 | X16 | loss | 4599 | +0.016 | -0.012 | 0.164 | 0.202 | 0.515 | +2.5 | +3.1 | -0.016 | +0.035 |  | no |
| of_x19_C1_ES_adv20 | X19 | profit | 39 | +0.139 | +0.239 | 0.218 | 0.207 | 0.515 | +30.6 | -1.8 | +0.017 | +0.097 | W-DYNOF committed X19 loss | no |
| x17_avwap | X17 | loss | 4835 | +0.016 | -0.015 | 0.158 | 0.206 | 0.515 | +5.0 | +5.6 | -0.035 | +0.059 |  | no |
| x12_tpeak_p75 | X12 | loss | 1503 | +0.022 | +0.003 | 0.186 | 0.211 | 0.516 | +4.8 | +4.9 | -0.040 | +0.068 |  | no |
| of_x19_C3_ESbreak30 | X19 | loss | 3718 | +0.014 | +0.001 | 0.254 | 0.231 | 0.556 | +1.9 | +2.3 | -0.003 | +0.024 |  | no |
| mbo_sweep_against150 | X14m | profit | 1443 | -0.026 | -0.003 | 0.167 | 0.241 | 0.570 | +9.6 | +1.8 | -0.020 | -0.030 | W-DYNOF M9 threshold | no |
| of_x14_F5_absorb_W120_z25 | X14 | profit | 502 | -0.039 | -0.005 | 0.232 | 0.256 | 0.588 | -4.6 | +3.9 | -0.049 | +0.047 | W-DYNOF committed X14 profit (port approximate) | no |
| x12_mfe_p50 | X12 | loss | 1169 | +0.027 | -0.025 | 0.287 | 0.256 | 0.588 | +11.9 | +10.9 | -0.086 | +0.147 |  | no |
| of_x19_C1_RTY_adv30 | X19 | loss | 504 | -0.037 | +0.021 | 0.229 | 0.265 | 0.598 | +0.1 | +6.0 | +0.001 | -0.017 |  | no |
| x18_clk_1359 | X18 | profit | 105 | +0.066 | +0.020 | 0.322 | 0.269 | 0.599 | +11.0 | -2.2 | -0.040 | +0.050 |  | no |
| of_x14_F1_dlt_W15_t50 | X14 | profit | 2340 | +0.018 | -0.017 | 0.269 | 0.275 | 0.602 | +1.2 | +2.5 | -0.032 | +0.057 |  | no |
| x18_vc_contract | X18 | loss | 194 | -0.060 | -0.040 | 0.176 | 0.282 | 0.609 | -5.6 | -4.2 | +0.002 | -0.086 |  | no |
| x12_tpeak_p50 | X12 | loss | 3733 | +0.011 | +0.001 | 0.328 | 0.303 | 0.637 | +4.3 | +5.1 | -0.036 | +0.055 |  | no |
| of_x14_F1_dlt_W180_t50 | X14 | loss | 134 | -0.062 | +0.033 | 0.236 | 0.301 | 0.637 | -2.4 | +9.6 | -0.043 | +0.016 |  | no |
| mbo_best_cleared_own | X14m | profit | 11039 | -0.008 | -0.013 | 0.254 | 0.309 | 0.640 | +2.0 | +2.0 | -0.026 | +0.013 |  | no |
| x18_vc_contract_STATIC | X18s | loss | 343 | -0.035 | -0.028 | 0.262 | 0.329 | 0.671 | -2.3 | -2.4 | +0.011 | -0.055 |  | no |
| of_x19_C1_RTY_adv20 | X19 | loss | 1712 | -0.017 | -0.011 | 0.315 | 0.347 | 0.699 | +0.5 | +3.8 | +0.008 | -0.010 |  | no |
| x18_clk_1359 | X18 | loss | 124 | +0.068 | -0.030 | 0.332 | 0.360 | 0.716 | +8.8 | +7.2 | -0.037 | +0.095 |  | no |
| x16_psar5 | X16 | loss | 3207 | +0.013 | -0.003 | 0.324 | 0.375 | 0.725 | +3.2 | +3.2 | -0.022 | +0.036 |  | no |
| of_x14_F1_dlt_W15_t30 | X14 | profit | 5198 | +0.010 | -0.007 | 0.352 | 0.375 | 0.725 | +2.3 | +1.4 | -0.022 | +0.024 |  | no |
| combo_mom_3of6 | X22c | profit | 1410 | -0.019 | -0.008 | 0.393 | 0.406 | 0.775 | +4.7 | +5.4 | -0.054 | +0.058 |  | no |
| combo_anch_2of3 | X22c | profit | 903 | -0.021 | -0.013 | 0.446 | 0.421 | 0.794 | +9.9 | +8.7 | -0.110 | +0.081 |  | no |
| x16_macd | X16 | profit | 3003 | +0.011 | -0.007 | 0.414 | 0.434 | 0.802 | +3.5 | +3.2 | -0.038 | +0.048 | W-DYNB1 committed X16 loss (MACD flip) | no |
| mbo_sweep_with300 | X14m | loss | 384 | +0.031 | +0.003 | 0.346 | 0.436 | 0.802 | +6.2 | -2.3 | +0.030 | +0.011 |  | no |
| x17_w60cross_STATIC | X17s | profit | 910 | +0.020 | -0.044 | 0.443 | 0.445 | 0.809 | +6.8 | +3.4 | -0.050 | +0.055 |  | no |
| x18_vc_exp_fav | X18 | profit | 6729 | -0.007 | -0.011 | 0.440 | 0.466 | 0.815 | +1.7 | +2.3 | -0.030 | +0.016 |  | no |
| x16_ha5 | X16 | profit | 2465 | +0.012 | -0.013 | 0.442 | 0.460 | 0.815 | +6.3 | +3.8 | -0.044 | +0.056 |  | no |
| of_x19_C3_ESbreak30 | X19 | profit | 344 | +0.030 | +0.035 | 0.472 | 0.454 | 0.815 | +12.8 | +2.1 | -0.045 | +0.053 |  | no |
| b2_x20_peer_stop | X20 | profit | 692 | +0.020 | -0.015 | 0.443 | 0.470 | 0.815 | +21.2 | +4.1 | -0.061 | +0.038 | W-DYNB2 committed X20 (cut-loss branch tested as ON at loss) | no |
| combo_all_2of16 | X22c | profit | 7074 | -0.007 | -0.012 | 0.462 | 0.479 | 0.821 | +3.1 | +3.4 | -0.041 | +0.026 |  | no |
| of_x19_C1_ES_adv10 | X19 | loss | 5793 | +0.007 | -0.014 | 0.466 | 0.487 | 0.824 | +0.4 | +1.7 | +0.001 | +0.010 |  | no |
| of_x19_C1_RTY_adv30 | X19 | profit | 168 | +0.038 | +0.110 | 0.498 | 0.505 | 0.836 | +23.0 | +3.4 | -0.013 | +0.026 |  | no |
| x16_rsi14 | X16 | profit | 2583 | +0.011 | -0.011 | 0.448 | 0.501 | 0.836 | +1.5 | +1.3 | -0.018 | +0.031 |  | no |
| x16_donch20 | X16 | profit | 889 | -0.017 | +0.007 | 0.510 | 0.513 | 0.837 | +3.1 | +4.9 | -0.037 | +0.066 |  | no |
| x16_3bar | X16 | profit | 3027 | -0.010 | -0.014 | 0.505 | 0.522 | 0.837 | +3.0 | +3.7 | -0.051 | +0.043 |  | no |
| of_x14_F5_absorb_W120_z40 | X14 | loss | 51 | +0.067 | +0.031 | 0.494 | 0.521 | 0.837 | +0.5 | -3.2 | -0.017 | +0.127 |  | no |
| of_x19_C1_ES_adv30 | X19 | loss | 522 | -0.018 | -0.016 | 0.501 | 0.545 | 0.864 | -1.3 | +4.0 | +0.032 | -0.049 |  | no |
| x16_ema9_21 | X16 | profit | 1251 | -0.013 | +0.001 | 0.558 | 0.558 | 0.876 | +4.7 | +5.4 | -0.064 | +0.064 |  | no |
| x18_vc_exp_adv | X18 | profit | 2756 | +0.010 | -0.020 | 0.561 | 0.570 | 0.880 | +3.4 | +5.0 | -0.057 | +0.068 |  | no |
| of_x14_F5_absorb_W30_z25 | X14 | profit | 1799 | +0.011 | -0.010 | 0.539 | 0.573 | 0.880 | -1.7 | +2.2 | -0.028 | +0.050 |  | no |
| mbo_iceberg_refill_x3 | X14m | profit | 6564 | -0.005 | -0.012 | 0.569 | 0.589 | 0.896 | +1.1 | +1.8 | -0.022 | +0.017 |  | no |
| x16_psar5 | X16 | profit | 1474 | -0.012 | -0.020 | 0.577 | 0.601 | 0.904 | +4.7 | +4.8 | -0.054 | +0.037 |  | no |
| of_x14_F1_dlt_W180_t30 | X14 | profit | 457 | -0.021 | +0.006 | 0.601 | 0.609 | 0.908 | +1.3 | +7.5 | -0.096 | +0.115 |  | no |
| x17_w60mean | X17 | loss | 319 | +0.021 | -0.032 | 0.635 | 0.622 | 0.918 | +10.0 | +7.2 | -0.074 | +0.108 |  | no |
| x18_clk_0959 | X18 | loss | 426 | +0.020 | -0.010 | 0.600 | 0.644 | 0.941 | +12.9 | +9.6 | -0.048 | +0.074 |  | no |
| x17_w60cross | X17 | profit | 1170 | +0.010 | -0.024 | 0.671 | 0.667 | 0.951 | +7.1 | +4.4 | -0.060 | +0.064 |  | no |
| of_x19_T2_toend15 | X19 | loss | 934 | -0.006 | -0.011 | 0.655 | 0.729 | 0.951 | -12.7 | -18.6 | +0.129 | -0.171 | W-DYNOF survivor (Asia flatten-profit) | no |
| x16_slope20 | X16 | profit | 1438 | +0.006 | -0.008 | 0.768 | 0.756 | 0.951 | +5.6 | +4.2 | -0.047 | +0.065 |  | no |
| of_x14_F1_dlt_W180_t50 | X14 | profit | 30 | +0.043 | +0.078 | 0.697 | 0.706 | 0.951 | +6.8 | -2.1 | +0.006 | +0.111 |  | no |
| x16_bb20 | X16 | loss | 2322 | +0.005 | +0.002 | 0.727 | 0.763 | 0.951 | +2.3 | +4.7 | -0.022 | +0.043 |  | no |
| mbo_pull_vs_add | X14m | profit | 653 | +0.010 | -0.012 | 0.718 | 0.742 | 0.951 | -3.0 | +2.6 | -0.055 | +0.079 |  | no |
| x12_mfe_p75 | X12 | loss | 245 | -0.019 | -0.033 | 0.734 | 0.742 | 0.951 | +6.0 | +12.2 | -0.102 | +0.188 |  | no |
| of_x14_F1_dlt_W60_t50 | X14 | profit | 413 | -0.020 | +0.033 | 0.630 | 0.672 | 0.951 | +0.1 | +6.6 | -0.083 | +0.110 | W-DYNOF committed X14 loss | no |
| x12_tpeak_p50 | X12 | profit | 3664 | -0.003 | -0.001 | 0.749 | 0.709 | 0.951 | +5.3 | +3.3 | -0.044 | +0.034 |  | no |
| x12_tpeak_p75 | X12 | profit | 1450 | -0.006 | +0.004 | 0.717 | 0.687 | 0.951 | +6.0 | +2.7 | -0.047 | +0.036 |  | no |
| combo_mom_2of6 | X22c | profit | 3422 | -0.004 | -0.018 | 0.763 | 0.751 | 0.951 | +5.0 | +4.0 | -0.051 | +0.047 |  | no |
| combo_xm_2of4 | X22c | loss | 5082 | +0.003 | -0.021 | 0.766 | 0.765 | 0.951 | +0.4 | +2.0 | -0.002 | +0.007 |  | no |
| x24_count_against2 | X24 | profit | 4703 | +0.004 | -0.004 | 0.727 | 0.719 | 0.951 | +2.1 | +2.5 | -0.034 | +0.034 | W-DYNL x24 count cutoff -2 (committed) | no |
| x16_keltner | X16 | loss | 2047 | +0.007 | -0.005 | 0.667 | 0.718 | 0.951 | +1.3 | +3.5 | -0.018 | +0.036 |  | no |
| x17_failbo | X17 | loss | 1023 | -0.008 | -0.013 | 0.738 | 0.707 | 0.951 | +1.4 | +3.7 | -0.018 | +0.026 |  | no |
| x17_w60mean_STATIC | X17s | loss | 155 | +0.028 | -0.109 | 0.705 | 0.671 | 0.951 | +10.3 | +9.0 | -0.064 | +0.137 |  | no |
| mbo_cancel_dominates | X14m | profit | 6251 | -0.003 | -0.014 | 0.715 | 0.766 | 0.951 | +2.4 | +2.1 | -0.026 | +0.019 |  | no |
| b2_x15_sr_lb30_st30 | X15 | profit | 6208 | -0.004 | -0.007 | 0.681 | 0.688 | 0.951 | +1.8 | +1.8 | -0.028 | +0.015 | W-DYNB2 committed X15 profit | no |
| of_x19_L1_NQ_ahead_of_ES_30 | X19 | loss | 21 | +0.033 | +0.326 | 0.842 | 0.825 | 0.960 | +17.6 | -0.5 | -0.039 | +0.138 |  | no |
| mbo_pull_vs_add | X14m | loss | 604 | +0.007 | -0.009 | 0.798 | 0.820 | 0.960 | -1.8 | +1.8 | -0.022 | +0.053 |  | no |
| of_x14_F5_absorb_W30_z25 | X14 | loss | 1221 | +0.005 | -0.009 | 0.797 | 0.796 | 0.960 | +0.4 | +3.3 | -0.029 | +0.056 |  | no |
| of_x14_F1_dlt_W15_t70 | X14 | loss | 1563 | +0.005 | +0.004 | 0.780 | 0.804 | 0.960 | -0.0 | +4.7 | -0.021 | +0.060 |  | no |
| of_x14_F5_absorb_W30_z40 | X14 | loss | 409 | -0.007 | +0.014 | 0.826 | 0.809 | 0.960 | -1.0 | +5.8 | -0.030 | +0.055 |  | no |
| x17_avwap | X17 | profit | 2493 | +0.004 | +0.001 | 0.804 | 0.781 | 0.960 | +5.3 | +5.1 | -0.060 | +0.063 |  | no |
| x17_failbo | X17 | profit | 260 | -0.013 | -0.006 | 0.790 | 0.790 | 0.960 | +9.1 | +5.2 | -0.096 | +0.071 |  | no |
| combo_flow_2of3 | X22c | profit | 2328 | +0.004 | -0.018 | 0.817 | 0.815 | 0.960 | +0.4 | +4.0 | -0.042 | +0.060 |  | no |
| combo_xm_2of4 | X22c | profit | 1062 | -0.005 | -0.003 | 0.816 | 0.834 | 0.963 | +11.9 | +4.0 | -0.051 | +0.010 |  | no |
| x12_mae_w90 | X12 | profit | 1456 | +0.004 | -0.017 | 0.814 | 0.846 | 0.969 | +12.7 | +6.6 | -0.076 | +0.057 | W-DYNB1 committed X12 loss | no |
| x16_climax | X16 | profit | 2831 | -0.003 | -0.022 | 0.808 | 0.865 | 0.983 | +1.4 | +1.4 | -0.015 | +0.011 |  | no |
| of_x19_C1_ES_adv20 | X19 | loss | 1926 | +0.003 | -0.014 | 0.875 | 0.875 | 0.987 | -0.2 | +1.1 | +0.024 | -0.015 | W-DYNOF committed X19 loss | no |
| of_x14_F1_dlt_W60_t70 | X14 | loss | 115 | +0.010 | +0.012 | 0.862 | 0.883 | 0.989 | -1.4 | +5.9 | -0.013 | +0.038 |  | no |
| x16_keltner | X16 | profit | 3860 | +0.001 | -0.011 | 0.925 | 0.931 | 0.998 | +1.5 | +2.0 | -0.028 | +0.029 |  | no |
| x18_vc_contract_STATIC | X18s | profit | 363 | -0.002 | -0.005 | 0.963 | 0.964 | 0.998 | +3.3 | -0.0 | +0.039 | -0.017 |  | no |
| of_x19_C1_RTY_adv10 | X19 | loss | 5152 | -0.001 | -0.019 | 0.925 | 0.935 | 0.998 | +0.8 | +2.6 | -0.006 | +0.009 |  | no |
| of_x14_F5_absorb_W120_z25 | X14 | loss | 250 | -0.004 | -0.018 | 0.950 | 0.935 | 0.998 | +0.4 | +9.4 | -0.064 | +0.084 | W-DYNOF committed X14 profit (port approximate) | no |
| of_x14_F1_dlt_W15_t70 | X14 | profit | 771 | -0.001 | +0.005 | 0.983 | 0.972 | 0.998 | -0.6 | +5.0 | -0.073 | +0.101 |  | no |
| of_x14_F1_dlt_W180_t30 | X14 | loss | 1629 | -0.001 | +0.010 | 0.974 | 0.982 | 0.998 | +0.5 | +5.6 | -0.030 | +0.052 |  | no |
| x12_mae_w75 | X12 | profit | 3362 | -0.000 | -0.013 | 0.991 | 0.991 | 0.998 | +9.8 | +6.2 | -0.069 | +0.054 |  | no |
| mbo_depl_trade_own_x3 | X14m | profit | 6513 | -0.001 | -0.013 | 0.917 | 0.925 | 0.998 | +1.6 | +1.3 | -0.014 | +0.013 |  | no |
| x18_clk_0229 | X18 | loss | 117 | -0.003 | -0.042 | 0.962 | 0.968 | 0.998 | +11.4 | +12.3 | -0.099 | +0.078 |  | no |
| mbo_depl_cancel_own_x3 | X14m | profit | 3966 | -0.000 | -0.017 | 0.997 | 0.998 | 0.998 | +2.6 | +2.0 | -0.021 | +0.025 |  | no |
| x16_climax | X16 | loss | 430 | -0.002 | -0.055 | 0.971 | 0.973 | 0.998 | +3.8 | +8.9 | -0.045 | +0.044 |  | no |
| of_x19_C1_RTY_adv20 | X19 | profit | 337 | -0.001 | +0.003 | 0.973 | 0.971 | 0.998 | +18.0 | +4.3 | -0.060 | +0.019 |  | no |
| x18_vc_contract | X18 | profit | 208 | -0.003 | -0.003 | 0.943 | 0.941 | 0.998 | -3.5 | -3.2 | +0.044 | -0.024 |  | no |
| x23b_ahead_reject | X23b | profit | 3053 | -0.000 | -0.007 | 0.989 | 0.992 | 0.998 | +5.4 | +3.1 | -0.035 | +0.014 |  | no |
| combo_all_3of16 | X22c | profit | 4868 | -0.001 | -0.006 | 0.965 | 0.958 | 0.998 | +4.9 | +4.1 | -0.049 | +0.042 |  | no |
| x23b_behind_reclaim | X23b | profit | 640 | +0.002 | -0.035 | 0.944 | 0.944 | 0.998 | +12.6 | +6.1 | -0.076 | +0.046 |  | no |

### Cells: open-profit region and book type (post hoc split of the same events; 512 cells charged in one BH; info YES: 0)

| signal | split | cell | side | n hold | d R | d_fit R | p_block | q BH |
|---|---|---|---|---|---|---|---|---|
| x18_clk_0829 | region | L_mid | L | 186 | -0.037 | -0.026 | 0.000 | 0.085 |
| x18_clk_0829 | btype | unknown | L | 215 | -0.038 | -0.025 | 0.000 | 0.085 |
| of_x19_T2_toend15 | btype | fade | P | 371 | -0.072 | -0.044 | 0.000 | 0.085 |
| mbo_best_cleared_own | btype | breakout | L | 3820 | +0.042 | +0.002 | 0.001 | 0.093 |
| x18_clk_0829 | btype | unknown | P | 130 | -0.046 | -0.048 | 0.001 | 0.093 |
| mbo_iceberg_refill_x3 | btype | breakout | L | 2114 | +0.053 | -0.004 | 0.002 | 0.093 |
| x18_clk_1555 | region | L_mid | L | 106 | -0.118 | -0.043 | 0.002 | 0.093 |
| mbo_best_cleared_own | region | L_mid | L | 10309 | +0.030 | -0.001 | 0.001 | 0.093 |
| x12_mfe_p50 | btype | breakout | P | 2315 | -0.041 | -0.022 | 0.001 | 0.093 |
| x24_count_against2 | btype | breakout | L | 3408 | +0.038 | -0.001 | 0.002 | 0.093 |
| x17_w60cross | region | L_mid | L | 3359 | +0.044 | -0.007 | 0.001 | 0.093 |
| x12_mfe_p75 | btype | breakout | P | 499 | -0.071 | -0.044 | 0.002 | 0.098 |
| of_x19_T2_toend15 | region | P_mid | P | 770 | -0.043 | -0.022 | 0.002 | 0.098 |
| mbo_iceberg_refill_x3 | region | L_mid | L | 5628 | +0.034 | -0.007 | 0.003 | 0.102 |
| x24_count_against2 | region | L_mid | L | 9032 | +0.029 | -0.003 | 0.003 | 0.102 |

<!-- TABLE-END -->
