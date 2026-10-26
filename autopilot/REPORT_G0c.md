# REPORT G0c - per-side asymmetric daily loss limit
**Verdict: NO. FOUND 0, LEAD 0. Carried cell short_L1.5: weekly Sharpe uplift +0.05 clean / -0.27 H1 / -0.64 H2 (needed +0.10 on each); all-in -0.13; plateau 0 of 2 neighbours; bootstrap 90% CI of all-in uplift [-0.52, +0.25]; 2x slippage uplift +0.09/-0.37/-1.06.** Use-mode M7 risk rule, horizons H1-H3. Pre-registered in PREREG_AUTOPILOT.md (G0 batch) before the first run. Pool of 5, about 15-20 min incl. 100-draw null.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine in a clean process (reproduced 1.46 / 2.83 / 2.30; all-in 1.86). pass1 copy with a state hook (ap_g0_core.py); state uses only trades closed before the entry. Dollar rules (per-book 5R/-2R, day cap 8R / 67% give-back, week floor -8R) unchanged. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Whole-lot: rule is skip-or-multiply by 0.5/0.25 (4 or 2 lots) so integer-lot executable.
- Rule: skip an entry on side s once closed accepted trades on side s that day (both books) are <= -L R; long-only / short-only / both-sides variants. Grid: 8 cells: both L{1,1.5,2,3}R; long-only L{1.5,2}; short-only L{1.5,2}.
- Selection on clean only, among cells changing >= 5% of clean raw entries; one cell carried; H1/H2 read once. Clean uplift of all cells: both_L1 -0.09, both_L1.5 -0.19, both_L2 +0.05, both_L3 +0.08, long_L1.5 -0.23, long_L2 -0.05, short_L1.5 +0.05, short_L2 +0.11.
- ERA: the live engine rows start 2023-08, so no 2013-22 replication exists for a pair-state rule (flag n/a); this is a limit of the test, not evidence.

## Result (weekly Sharpe)
| span | pair | G0c | uplift | vs B.Cfg() uplift (clean/H1/H2) | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.51 | +0.05 | +0.20 | +0.09 |
| H1 | 2.83 | 2.56 | -0.27 | -0.17 | -0.37 |
| H2 | 2.30 | 1.66 | -0.64 | -0.69 | -1.06 |
| all-in | 1.86 | 1.73 | -0.13 | -0.06 | -0.22 |
Trades kept (all-in): 6972 vs 7320. Weekly correlation with the pair 0.93.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +2,268).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 +0.54, null mean +0.35, real rank 0.00; clean p95 +0.55 rank 0.00; H1 rank 0.02; H2 rank 0.00).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.52, +0.25]; clean [-0.29, +0.40]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: L x0.75 -0.10, L x1.25 -0.03).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.93); no hedge claim.
10. NT8-codable: yes (strategy-level counters of the day's closed trades / equity; no new data). Margin unchanged or lower than the 16-contract pair. Executable at NinjaTrader Brokerage via Rithmic.
Overall: NO.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean G0c | 1.51 | 2.88 | 4.85 | -77.6k | -77.4k | 285k | -77.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 G0c | 2.56 | 5.65 | 3.51 | -78.2k | -73.1k | 175k | -78.3k | 35.7 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 G0c | 1.66 | 3.35 | 2.31 | -78.8k | -78.1k | 243k | -80.3k | 47.2 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all G0c | 1.73 | 3.38 | 8.98 | -78.1k | -77.7k | 285k | -80.3k | 42.9 |
Constant-risk/insurance read (all-in): cost -4.8% of net, CVaR5 improvement +1.4%, worst week +2.7%, maxDD -1.6% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
Short-side limit L=1.5R touches 6% of entries; clean +0.05 only, H1 -0.27, H2 -0.64. The random side-halt null has mean +0.35 uplift, i.e. the real rule is worse than random truncation: stopping a side after losses removes entries that tend to win back. The best clean cell is statistically indistinguishable from nothing.
Files: code/census/night_ins/ap_g0_core.py, ap_g0_run.py, ap_g0_rep.py, ap_g0_mkrep.py; outputs/autopilot/g0c/{G0c_all.pkl,G0c_summary.json}. No book series (pair rule), so nothing saved to the library.

DONE G0c
