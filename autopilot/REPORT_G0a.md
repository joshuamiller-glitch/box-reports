# REPORT G0a - intraday entry halts (consecutive stops / max entries per day)
**Verdict: NO. FOUND 0, LEAD 0. Carried cell pair_n2: weekly Sharpe uplift +0.32 clean / -1.40 H1 / -1.84 H2 (needed +0.10 on each); all-in -0.42; plateau 0 of 2 neighbours; bootstrap 90% CI of all-in uplift [-1.07, +0.23]; 2x slippage uplift +0.51/-1.34/-1.76.** Use-mode M7 risk rule, horizons H1-H3. Pre-registered in PREREG_AUTOPILOT.md (G0 batch) before the first run. Pool of 5, about 15-20 min incl. 100-draw null.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine in a clean process (reproduced 1.46 / 2.83 / 2.30; all-in 1.86). pass1 copy with a state hook (ap_g0_core.py); state uses only trades closed before the entry. Dollar rules (per-book 5R/-2R, day cap 8R / 67% give-back, week floor -8R) unchanged. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Whole-lot: rule is skip-or-multiply by 0.5/0.25 (4 or 2 lots) so integer-lot executable.
- Rule: skip an entry if the last n closed trades of the day in scope (book or pair) were all stop exits, or if the book already has m entries that day. Grid: 9 cells: scope{book,pair} x n{2,3,4}; max entries per book per day {5,8,12}.
- Selection on clean only, among cells changing >= 5% of clean raw entries; one cell carried; H1/H2 read once. Clean uplift of all cells: book_n2 -0.04, book_n3 -0.05, book_n4 +0.00, pair_n2 +0.32, pair_n3 +0.10, pair_n4 -0.05, max5 +0.05, max8 -0.16, max12 -0.01.
- ERA: the live engine rows start 2023-08, so no 2013-22 replication exists for a pair-state rule (flag n/a); this is a limit of the test, not evidence.

## Result (weekly Sharpe)
| span | pair | G0a | uplift | vs B.Cfg() uplift (clean/H1/H2) | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.78 | +0.32 | +0.54 | +0.51 |
| H1 | 2.83 | 1.43 | -1.40 | -0.45 | -1.34 |
| H2 | 2.30 | 0.46 | -1.84 | -1.49 | -1.76 |
| all-in | 1.86 | 1.44 | -0.42 | -0.07 | -0.29 |
Trades kept (all-in): 5079 vs 7320. Weekly correlation with the pair 0.78.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +1,101).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 +1.01, null mean +0.64, real rank 0.00; clean p95 +1.40 rank 0.00; H1 rank 0.01; H2 rank 0.00).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-1.07, +0.23]; clean [-0.32, +1.01]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: n-1 -0.31, n+1 +0.01).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.78); no hedge claim.
10. NT8-codable: yes (strategy-level counters of the day's closed trades / equity; no new data). Margin unchanged or lower than the 16-contract pair. Executable at NinjaTrader Brokerage via Rithmic.
Overall: NO.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean G0a | 1.78 | 3.40 | 4.60 | -78.6k | -78.0k | 326k | -79.4k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 G0a | 1.43 | 2.64 | 1.52 | -73.0k | -68.9k | 199k | -81.4k | 50.0 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 G0a | 0.46 | 0.79 | 0.59 | -77.7k | -77.4k | 236k | -77.9k | 58.3 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all G0a | 1.44 | 2.65 | 5.25 | -78.7k | -77.6k | 370k | -81.4k | 47.6 |
Constant-risk/insurance read (all-in): cost -27.7% of net, CVaR5 improvement +0.7%, worst week +1.3%, maxDD -31.9% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
Halting after two pair-wide stops removes 41% of raw entries and lifts clean (+0.32) but destroys H1 (-1.40) and H2 (-1.84): after a stop-out the next trades are, if anything, better (mean reversion of the signal quality), so the halt cuts winners. The matched random-halt null has a clean mean uplift of +1.06 (random truncation of the day tail helps in clean because late-day entries were net-negative in 2023-25), so the clean gain is a time-of-day artefact, not a stop-streak effect; real rank 0 on the null.
Files: code/census/night_ins/ap_g0_core.py, ap_g0_run.py, ap_g0_rep.py, ap_g0_mkrep.py; outputs/autopilot/g0a/{G0a_all.pkl,G0a_summary.json}. No book series (pair rule), so nothing saved to the library.

DONE G0a
