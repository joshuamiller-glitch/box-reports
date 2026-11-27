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

## Results table (auto)

<!-- TABLE-START (auto, attrib_run.py --md) -->

updated 27 Nov 04:14Z UTC; signals tried (non-control): 25; (signal, side) tests charged in BH: 50; information=YES: 0

Columns: n = hold events (last 40 %% of trades by entry time), d = fire minus matched-null remaining P&L in R (negative = trade did worse after the signal = EXIT/TAKE information), exit gain = -d R per fired event, p_block = day-block bootstrap, q = Benjamini-Hochberg over all tests; dT/dS = change in P(Target)/P(Stop), pp; dMAE/dMFE of the remainder in R. d_fit = same on the first 60 %%.

| signal | family | agent | side | n | d R | d_fit R | p_plain | p_block | q (BH) | dT pp | dS pp | dMAE R | dMFE R | info |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| x12_mfe_p50 | X12 | W-DYNA | profit | 3376 | -0.031 | -0.019 | 0.012 | 0.015 | 0.300 | -7.2 | +0.3 | +0.011 | -0.016 | no |
| x17_w60cross | X17 | W-DYNA | loss | 2663 | +0.042 | +0.001 | 0.007 | 0.009 | 0.300 | +3.5 | +3.3 | -0.006 | +0.048 | no |
| x17_w60mean | X17 | W-DYNA | profit | 762 | -0.073 | -0.031 | 0.015 | 0.018 | 0.300 | -0.2 | +5.1 | -0.064 | -0.004 | no |
| x12_mae_w90 | X12 | W-DYNA | loss | 3527 | +0.024 | -0.011 | 0.024 | 0.043 | 0.435 | +0.3 | +2.9 | +0.018 | +0.022 | no |
| x12_mfe_p75 | X12 | W-DYNA | profit | 1076 | -0.049 | -0.047 | 0.036 | 0.036 | 0.435 | -14.3 | +0.6 | -0.026 | +0.019 | no |
| x12_mae_w75 | X12 | W-DYNA | loss | 4623 | +0.022 | -0.007 | 0.052 | 0.081 | 0.675 | +0.6 | +3.0 | +0.000 | +0.039 | no |
| x16_rsi14 | X16 | W-DYNA | loss | 1093 | +0.049 | -0.003 | 0.041 | 0.104 | 0.684 | +3.4 | +0.7 | +0.008 | +0.039 | no |
| x18_clk_0959 | X18 | W-DYNA | profit | 349 | -0.076 | +0.018 | 0.056 | 0.109 | 0.684 | +15.0 | +8.2 | -0.054 | -0.028 | no |
| x18_vc_exp_adv | X18 | W-DYNA | loss | 3901 | +0.018 | +0.016 | 0.169 | 0.214 | 0.913 | +0.8 | +3.8 | -0.012 | +0.047 | no |
| x12_tpeak_p50 | X12 | W-DYNA | profit | 2276 | -0.016 | +0.006 | 0.227 | 0.231 | 0.913 | +3.9 | +3.8 | -0.049 | +0.037 | no |
| x18_vc_exp_fav | X18 | W-DYNA | loss | 2854 | +0.020 | +0.008 | 0.222 | 0.237 | 0.913 | +2.6 | +6.0 | -0.027 | +0.066 | no |
| x18_vc_contract | X18 | W-DYNA | loss | 79 | -0.126 | -0.026 | 0.022 | 0.210 | 0.913 | -3.3 | -3.1 | +0.018 | -0.144 | no |
| x16_ema9_21 | X16 | W-DYNA | loss | 2859 | +0.023 | -0.002 | 0.114 | 0.173 | 0.913 | +2.0 | +2.5 | -0.012 | +0.045 | no |
| x12_tpeak_p50 | X12 | W-DYNA | loss | 2342 | -0.004 | +0.010 | 0.758 | 0.764 | 0.938 | +2.9 | +6.2 | -0.042 | +0.056 | no |
| x16_bb20 | X16 | W-DYNA | loss | 1506 | +0.006 | +0.001 | 0.741 | 0.771 | 0.938 | +1.8 | +5.1 | -0.019 | +0.047 | no |
| x12_mae_w90 | X12 | W-DYNA | profit | 933 | +0.009 | -0.053 | 0.689 | 0.732 | 0.938 | +13.8 | +6.9 | -0.088 | +0.070 | no |
| x16_macd | X16 | W-DYNA | profit | 1799 | +0.007 | -0.006 | 0.690 | 0.719 | 0.938 | +2.0 | +4.2 | -0.050 | +0.064 | no |
| x16_keltner | X16 | W-DYNA | loss | 1438 | -0.004 | -0.014 | 0.859 | 0.882 | 0.938 | -0.1 | +4.3 | -0.018 | +0.032 | no |
| x16_donch20 | X16 | W-DYNA | profit | 508 | +0.007 | +0.020 | 0.870 | 0.858 | 0.938 | +3.9 | +5.1 | -0.044 | +0.111 | no |
| x16_climax | X16 | W-DYNA | profit | 2036 | -0.005 | -0.018 | 0.777 | 0.818 | 0.938 | +0.9 | +2.3 | -0.019 | +0.018 | no |
| x16_ha5 | X16 | W-DYNA | loss | 2692 | +0.014 | -0.003 | 0.328 | 0.415 | 0.938 | +2.8 | +3.6 | -0.020 | +0.053 | no |
| x16_ema9_21 | X16 | W-DYNA | profit | 737 | -0.022 | +0.002 | 0.487 | 0.508 | 0.938 | +3.1 | +6.6 | -0.069 | +0.084 | no |
| x16_ha5 | X16 | W-DYNA | profit | 1427 | +0.005 | -0.000 | 0.847 | 0.821 | 0.938 | +5.3 | +5.0 | -0.052 | +0.072 | no |
| x16_donch20 | X16 | W-DYNA | loss | 2865 | +0.014 | -0.005 | 0.336 | 0.335 | 0.938 | +1.2 | +2.6 | -0.010 | +0.036 | no |
| x16_psar5 | X16 | W-DYNA | profit | 939 | -0.026 | -0.005 | 0.347 | 0.346 | 0.938 | +3.7 | +6.1 | -0.069 | +0.049 | no |
| x16_psar5 | X16 | W-DYNA | loss | 1908 | +0.009 | +0.011 | 0.606 | 0.672 | 0.938 | +2.3 | +3.6 | -0.024 | +0.036 | no |
| x12_tpeak_p75 | X12 | W-DYNA | profit | 932 | -0.020 | +0.004 | 0.298 | 0.336 | 0.938 | +5.6 | +3.7 | -0.053 | +0.037 | no |
| x16_3bar | X16 | W-DYNA | loss | 4174 | +0.003 | -0.008 | 0.848 | 0.846 | 0.938 | +0.5 | +3.5 | -0.016 | +0.028 | no |
| x16_bb20 | X16 | W-DYNA | profit | 2723 | +0.011 | -0.003 | 0.485 | 0.495 | 0.938 | +2.0 | +2.2 | -0.028 | +0.044 | no |
| x16_3bar | X16 | W-DYNA | profit | 1721 | -0.009 | -0.014 | 0.650 | 0.642 | 0.938 | +1.9 | +4.6 | -0.062 | +0.067 | no |
| x12_mfe_p75 | X12 | W-DYNA | loss | 221 | -0.019 | -0.021 | 0.747 | 0.761 | 0.938 | +6.4 | +12.5 | -0.108 | +0.184 | no |
| x12_mae_w75 | X12 | W-DYNA | profit | 2119 | -0.007 | -0.018 | 0.652 | 0.673 | 0.938 | +10.2 | +7.6 | -0.080 | +0.065 | no |
| x18_vc_exp_adv | X18 | W-DYNA | profit | 1686 | +0.014 | -0.012 | 0.502 | 0.526 | 0.938 | +0.9 | +5.9 | -0.065 | +0.097 | no |
| x18_vc_exp_fav | X18 | W-DYNA | profit | 4159 | -0.009 | -0.005 | 0.472 | 0.523 | 0.938 | -0.3 | +2.6 | -0.027 | +0.024 | no |
| x17_failbo | X17 | W-DYNA | loss | 665 | -0.025 | -0.011 | 0.434 | 0.436 | 0.938 | -0.2 | +4.3 | -0.017 | +0.014 | no |
| x16_rsi14 | X16 | W-DYNA | profit | 1626 | +0.006 | -0.002 | 0.734 | 0.791 | 0.938 | -0.0 | +1.9 | -0.024 | +0.041 | no |
| x16_keltner | X16 | W-DYNA | profit | 2340 | -0.012 | -0.009 | 0.469 | 0.521 | 0.938 | -0.9 | +3.0 | -0.038 | +0.037 | no |
| x16_macd | X16 | W-DYNA | loss | 3422 | +0.011 | -0.010 | 0.428 | 0.476 | 0.938 | +2.2 | +3.9 | -0.016 | +0.038 | no |
| x17_avwap | X17 | W-DYNA | loss | 2859 | +0.014 | -0.012 | 0.348 | 0.453 | 0.938 | +4.3 | +6.6 | -0.040 | +0.071 | no |
| x16_slope20 | X16 | W-DYNA | loss | 2783 | +0.010 | -0.001 | 0.466 | 0.542 | 0.938 | +1.3 | +3.6 | -0.018 | +0.039 | no |
| x17_w60cross | X17 | W-DYNA | profit | 514 | -0.021 | -0.011 | 0.605 | 0.597 | 0.938 | +8.9 | +9.8 | -0.130 | +0.109 | no |
| x17_failbo | X17 | W-DYNA | profit | 190 | -0.038 | -0.029 | 0.514 | 0.530 | 0.938 | +9.0 | +7.1 | -0.120 | +0.071 | no |
| x18_vc_contract | X18 | W-DYNA | profit | 88 | +0.046 | +0.004 | 0.228 | 0.354 | 0.938 | -7.0 | -5.2 | +0.108 | -0.050 | no |
| x17_avwap | X17 | W-DYNA | profit | 1455 | -0.004 | +0.018 | 0.848 | 0.859 | 0.938 | +5.0 | +7.0 | -0.081 | +0.089 | no |
| x18_clk_0959 | X18 | W-DYNA | loss | 417 | +0.016 | -0.010 | 0.671 | 0.694 | 0.938 | +12.7 | +10.2 | -0.049 | +0.070 | no |
| x17_w60mean | X17 | W-DYNA | loss | 149 | +0.023 | -0.038 | 0.746 | 0.743 | 0.938 | +13.3 | +11.9 | -0.102 | +0.169 | no |
| x16_slope20 | X16 | W-DYNA | profit | 849 | +0.004 | +0.021 | 0.878 | 0.876 | 0.938 | +4.6 | +5.0 | -0.052 | +0.089 | no |
| x12_mfe_p50 | X12 | W-DYNA | loss | 817 | -0.003 | -0.028 | 0.929 | 0.935 | 0.974 | +10.8 | +13.3 | -0.103 | +0.154 | no |
| x12_tpeak_p75 | X12 | W-DYNA | loss | 934 | +0.001 | +0.010 | 0.976 | 0.972 | 0.992 | +3.2 | +6.9 | -0.049 | +0.061 | no |
| x16_climax | X16 | W-DYNA | loss | 359 | +0.001 | -0.057 | 0.989 | 0.994 | 0.994 | +5.0 | +10.0 | -0.040 | +0.034 | no |

Controls (hold split): ctl_random L n=1292 d=+0.001 p=0.980; ctl_random P n=1057 d=+0.032 p=0.147; ctl_leak60 L n=3051 d=-0.229 p=0.000; ctl_leak60 P n=3409 d=+0.139 p=0.000

<!-- TABLE-END -->
