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

updated 27 Nov 04:59Z UTC; signals tried (non-control): 0; (signal, side) tests charged in BH: 0; information=YES: 0

Columns: n = hold events (last 40 %% of trades by entry time), d = fire minus matched-null remaining P&L in R (negative = trade did worse after the signal = EXIT/TAKE information), exit gain = -d R per fired event, p_block = day-block bootstrap, q = Benjamini-Hochberg over all tests; dT/dS = change in P(Target)/P(Stop), pp; dMAE/dMFE of the remainder in R. d_fit = same on the first 60 %%.

| signal | family | agent | side | n | d R | d_fit R | p_plain | p_block | q (BH) | dT pp | dS pp | dMAE R | dMFE R | info |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

Controls (hold split): ctl_random L n=2228 d=+0.005 p=0.743; ctl_random P n=1735 d=+0.008 p=0.667; ctl_leak60 L n=4950 d=-0.237 p=0.000; ctl_leak60 P n=5845 d=+0.145 p=0.000

<!-- TABLE-END -->
