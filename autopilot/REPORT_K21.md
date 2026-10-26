# REPORT K21 - minimum spacing between entries per book
**Verdict: NO. FOUND 0, LEAD 0. Carried cell N30: weekly Sharpe uplift -0.13 clean / -0.25 H1 / -0.58 H2 (needed +0.10 on each); all-in -0.24; plateau 0 of 2 neighbours; bootstrap 90% CI of all-in uplift [-0.70, +0.21]; 2x slippage uplift -0.00/-0.31/-0.50.** Use-mode M4/M7, horizons H1-H2. Pre-registered in PREREG_AUTOPILOT.md (K19/K20/K21/K23 block) before the first run. Pool of 5.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine, clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_kc_core.py, on ap_h0_core/ap_g0_core), optional per-book give-back stage before the combined lock. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and variant. State uses only trades closed (or open) at the entry time.
- Rule: skip an entry if the same book's previous accepted entry was less than N minutes earlier.
- Grid: 3 cells: N {10,20,30} min. Differs from H0b (conditioned on a recent STOP-OUT, either book, multipliers 0/0.5/1.5): here the condition is entry spacing within one book, regardless of outcome.
- Selection on clean only, highest clean uplift among cells that change >= 5% of clean entries; one cell carried; H1/H2 read once. Clean uplift of all cells: N10 -0.02, N20 +0.04, N30 -0.13.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (flag n/a; a limit of the test).

## Result (weekly Sharpe)
| span | pair | K21 | uplift | 2x slip uplift | worst-week delta ($) |
|---|---|---|---|---|---|
| clean | 1.46 | 1.33 | -0.13 | -0.00 | -4,100 |
| H1 | 2.83 | 2.58 | -0.25 | -0.31 | -1,034 |
| H2 | 2.30 | 1.72 | -0.58 | -0.50 | +2,871 |
| all-in | 1.86 | 1.61 | -0.24 | -0.15 | -3,449 |
Trades kept (all-in): 6972 vs 7320. Weekly correlation with the pair 0.88.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: FAIL (delta -3,449).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 +0.15, null mean -0.20, real rank 0.46; clean p95 +0.25 rank 0.59; H1 rank 0.35; H2 rank 0.37).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.70, +0.21]; clean [-0.51, +0.29]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: N x0.75 +0.08, N x1.25 -0.12).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.88); no hedge claim.
10. NT8-codable: yes. NT8: store last entry timestamp per strategy; ignore a signal inside the window. Executable; reduces trades by 1-7%. Executable at NinjaTrader Brokerage via Rithmic.
Replication (reported, Amend. 2): H0 window 2023-02-10..2023-07-31 uplift -0.06; alternating months: odd->even: selected N20 +0.04 -> read -0.18; even->odd: selected N30 +0.03 -> read -0.47. Cross-instrument: n/a (pair engine is NQ only).
Overall: NO. Replication fails or n/a: same-sign >= 50% of uplift needed on two of the replication legs.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean K21 | 1.33 | 2.29 | 4.37 | -80.2k | -79.0k | 263k | -86.0k | 43.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 K21 | 2.58 | 5.08 | 3.01 | -78.1k | -74.8k | 175k | -79.3k | 32.1 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 K21 | 1.72 | 3.43 | 2.84 | -78.9k | -78.1k | 207k | -79.7k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all K21 | 1.61 | 2.91 | 8.61 | -79.9k | -78.7k | 263k | -86.0k | 42.3 |
Constant-risk/insurance read (all-in): cost -15.7% of net, CVaR5 improvement -0.8%, worst week -4.2%, maxDD +6.1% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
Spacing touches only 2-7% of entries and the carried cell N30 loses on all three spans (clean -0.13, H1 -0.25, H2 -0.58) with a worse worst week; N10/N20 are +/-0.04 on clean (noise). Quick re-entries by the same book are as good as spaced ones, the same finding as H0b (stop-out clustering carries no information).
Files: code/census/night_ins/ap_h0_core.py, ap_kc_core.py, ap_kc_run.py, ap_h0_rep.py, ap_kc_mkrep.py; outputs/autopilot/k21/{K21_all.pkl,K21_summary.json}. No stand-alone book series (pair rule), nothing saved to the library.

DONE K21
