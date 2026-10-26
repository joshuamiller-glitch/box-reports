# REPORT K19 - size declines with the day's trade count
**Verdict: NO. FOUND 0, LEAD 0. Carried cell K4_m0.5: weekly Sharpe uplift +0.10 clean / -0.27 H1 / -1.88 H2 (needed +0.10 on each); all-in -0.40; plateau 0 of 4 neighbours; bootstrap 90% CI of all-in uplift [-0.84, +0.02]; 2x slippage uplift +0.23/-0.25/-1.96.** Use-mode M8 pair sizing / M7 risk rule, horizons H2-H3. Pre-registered in PREREG_AUTOPILOT.md (K19/K20/K21/K23 block) before the first run. Pool of 5.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine, clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_kc_core.py, on ap_h0_core/ap_g0_core), optional per-book give-back stage before the combined lock. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and variant. State uses only trades closed (or open) at the entry time.
- Rule: the n-th accepted trade of the day (both books combined) is multiplied by m once n >= K+1 (first K full size).
- Grid: 4 cells: K {4,6} x m {0.5,0.75}. Differs from G0a, which HALTED after a fixed entry count (clean +0.32, H1 -1.40, H2 -1.84); this is a soft decline.
- Selection on clean only, highest clean uplift among cells that change >= 5% of clean entries; one cell carried; H1/H2 read once. Clean uplift of all cells: K4_m0.5 +0.10, K4_m0.75 +0.02, K6_m0.5 +0.09, K6_m0.75 +0.06.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (flag n/a; a limit of the test).

## Result (weekly Sharpe)
| span | pair | K19 | uplift | 2x slip uplift | worst-week delta ($) |
|---|---|---|---|---|---|
| clean | 1.46 | 1.56 | +0.10 | +0.23 | +3,473 |
| H1 | 2.83 | 2.56 | -0.27 | -0.25 | +894 |
| H2 | 2.30 | 0.42 | -1.88 | -1.96 | +1,843 |
| all-in | 1.86 | 1.45 | -0.40 | -0.34 | +1,843 |
Trades kept (all-in): 8928 vs 7320. Weekly correlation with the pair 0.89.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +1,843).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 +0.05, null mean -0.32, real rank 0.42; clean p95 +0.01 rank 0.97; H1 rank 0.26; H2 rank 0.00).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.84, +0.02]; clean [-0.39, +0.63]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: K x0.75 -0.35, m x0.75 -0.23, K x1.25 -0.32, m x1.25 -0.58).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.89); no hedge claim.
10. NT8-codable: yes. NT8: count fills per account per ET day in a shared static; scale Quantity of later entries (min 1 contract per book). Margin lower. Executable. Executable at NinjaTrader Brokerage via Rithmic.
Replication (reported, Amend. 2): H0 window 2023-02-10..2023-07-31 uplift -0.85; alternating months: odd->even: selected K6_m0.75 -0.07 -> read -0.01; even->odd: selected K6_m0.75 -0.01 -> read -0.07. Cross-instrument: n/a (pair engine is NQ only).
Overall: NO. Replication fails or n/a: same-sign >= 50% of uplift needed on two of the replication legs.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean K19 | 1.56 | 2.77 | 3.65 | -77.9k | -77.6k | 342k | -78.4k | 40.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 K19 | 2.56 | 5.38 | 3.09 | -77.2k | -71.1k | 181k | -77.4k | 35.7 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 K19 | 0.42 | 0.72 | 0.56 | -80.1k | -78.5k | 243k | -80.7k | 55.6 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all K19 | 1.45 | 2.61 | 5.68 | -78.3k | -77.8k | 342k | -80.7k | 42.9 |
Constant-risk/insurance read (all-in): cost -27.6% of net, CVaR5 improvement +1.1%, worst week +2.2%, maxDD -22.2% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
Only the K4/K6 half-size cells are near-zero on clean (+0.10 and +0.09, the carried K4_m0.5 is +0.097 before rounding, i.e. below the +0.10 gate), no cell is positive on H1 (-0.27) or H2 (-1.88). Later trades of busy days are not worse than early ones: removing size from them removes edge in proportion, and the day locks fire later because equity moves less, so the lock mechanics partly offset. Weekly corr with the pair 0.89. The soft decline confirms the G0a verdict.
Files: code/census/night_ins/ap_h0_core.py, ap_kc_core.py, ap_kc_run.py, ap_h0_rep.py, ap_kc_mkrep.py; outputs/autopilot/k19/{K19_all.pkl,K19_summary.json}. No stand-alone book series (pair rule), nothing saved to the library.

DONE K19
