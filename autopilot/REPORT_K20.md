# REPORT K20 - per-book give-back lock beside the combined lock
**Verdict: NO. FOUND 0, LEAD 0. Carried cell arm1.5_keep0.33: weekly Sharpe uplift -0.06 clean / +0.04 H1 / -0.17 H2 (needed +0.10 on each); all-in -0.07; plateau 0 of 4 neighbours; bootstrap 90% CI of all-in uplift [-0.38, +0.19]; 2x slippage uplift -0.11/+0.08/-0.21.** Use-mode M5 pair exit management, horizons H2-H3. Pre-registered in PREREG_AUTOPILOT.md (K19/K20/K21/K23 block) before the first run. Pool of 5.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine, clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_kc_core.py, on ap_h0_core/ap_g0_core), optional per-book give-back stage before the combined lock. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and variant. State uses only trades closed (or open) at the entry time.
- Rule: per (exit-day, book): book equity peak >= 1.5R and equity <= 0.33 x peak -> flatten that book and block its remaining entries that day; applied before the unchanged combined lock.
- Grid: 1 cell: arm 1.5R / keep 0.33. Differs from H0c, which added a second tier to the COMBINED day lock (A {3,4,5}R x k2 {0.5,0.67,0.8}); this adds a lock on each book separately while the other book keeps trading. Not a duplicate of H0c (different group key; fires on 24% of book-days).
- Selection on clean only, highest clean uplift among cells that change >= 5% of clean entries; one cell carried; H1/H2 read once. Clean uplift of all cells: arm1.5_keep0.33 -0.06.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (flag n/a; a limit of the test).

## Result (weekly Sharpe)
| span | pair | K20 | uplift | 2x slip uplift | worst-week delta ($) |
|---|---|---|---|---|---|
| clean | 1.46 | 1.40 | -0.06 | -0.11 | +0 |
| H1 | 2.83 | 2.86 | +0.04 | +0.08 | +0 |
| H2 | 2.30 | 2.12 | -0.17 | -0.21 | +2,871 |
| all-in | 1.86 | 1.78 | -0.07 | -0.11 | +651 |
Trades kept (all-in): 7015 vs 7320. Weekly correlation with the pair 0.96.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +651).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 +0.60, null mean +0.18, real rank 0.19; clean p95 +0.67 rank 0.23; H1 rank 0.45; H2 rank 0.26).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.38, +0.19]; clean [-0.36, +0.20]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: arm x0.75 -0.33, keep x0.75 -0.06, arm x1.25 +0.01, keep x1.25 -0.23).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.96); no hedge claim.
10. NT8-codable: yes. NT8: each strategy tracks its own session realised+open P&L (the per-book -2R/+5R watcher already exists) and adds a peak/give-back trigger; flatten own position, disable own entries. Margin unchanged. Executable. Executable at NinjaTrader Brokerage via Rithmic.
Replication (reported, Amend. 2): H0 window 2023-02-10..2023-07-31 uplift -0.23; alternating months: odd->even: selected arm1.5_keep0.33 -0.10 -> read -0.01; even->odd: selected arm1.5_keep0.33 -0.01 -> read -0.10. Cross-instrument: n/a (pair engine is NQ only).
Overall: NO. Replication fails or n/a: same-sign >= 50% of uplift needed on two of the replication legs.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean K20 | 1.40 | 2.63 | 4.38 | -79.1k | -78.4k | 298k | -81.9k | 44.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 K20 | 2.86 | 6.03 | 4.19 | -77.6k | -70.1k | 146k | -78.3k | 32.1 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 K20 | 2.12 | 4.29 | 3.73 | -79.4k | -79.0k | 193k | -79.7k | 41.7 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all K20 | 1.78 | 3.44 | 8.86 | -79.2k | -78.4k | 298k | -81.9k | 42.3 |
Constant-risk/insurance read (all-in): cost -1.8% of net, CVaR5 improvement -0.0%, worst week +0.8%, maxDD -6.3% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
The per-book lock fires on 24% of clean book-days and is negative on clean (-0.06) and H2 (-0.17), flat on H1 (+0.04): a book that has given back two thirds of a 1.5R peak is not in a failing regime for the rest of that day, and the combined lock already takes the large cases. Worst week delta is positive (+651) but the Sharpe loss makes it moot. The null (random per-book locks at the same rate) has p95 +0.60 on all-in, so the result is indistinguishable from random locking.
Files: code/census/night_ins/ap_h0_core.py, ap_kc_core.py, ap_kc_run.py, ap_h0_rep.py, ap_kc_mkrep.py; outputs/autopilot/k20/{K20_all.pkl,K20_summary.json}. No stand-alone book series (pair rule), nothing saved to the library.

DONE K20
