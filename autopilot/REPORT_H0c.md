# REPORT H0c - second give-back tier on the combined day lock
**Verdict: NO. FOUND 0, LEAD 0. Carried cell A4_k0.5: weekly Sharpe uplift +0.12 clean / -0.53 H1 / -0.26 H2 (needed +0.10 on each); all-in -0.05; plateau 0 of 4 neighbours; bootstrap 90% CI of all-in uplift [-0.26, +0.15]; 2x slippage uplift +0.09/-0.66/-0.36.** Use-mode M5 pair exit management, horizons H1-H4. Pre-registered in PREREG_AUTOPILOT.md (H0 batch) before the first run. Pool of 5.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine, clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_h0_core.py), lock stage copy with an optional second tier. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and variant. State uses only trades closed (or open) at the entry time.
- Rule: additional day-lock trigger: day peak equity >= A R and equity <= peak x k2 (flatten and block the rest of the day, as the live give-back); week/month locks unchanged.
- Grid: 9 cells: A {3,4,5} R x k2 {0.5,0.67,0.8} (live: arm 2R, keep 0.33).
- Selection on clean only, highest clean uplift among cells that change >= 5% of clean entries; one cell carried; H1/H2 read once. Clean uplift of all cells: A3_k0.5 -0.05, A3_k0.67 -0.26, A3_k0.8 -0.44, A4_k0.5 +0.12, A4_k0.67 -0.04, A4_k0.8 -0.30, A5_k0.5 +0.08, A5_k0.67 -0.05, A5_k0.8 -0.14.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (flag n/a; a limit of the test).

## Result (weekly Sharpe)
| span | pair | H0c | uplift | 2x slip uplift | worst-week delta ($) |
|---|---|---|---|---|---|
| clean | 1.46 | 1.58 | +0.12 | +0.09 | +0 |
| H1 | 2.83 | 2.30 | -0.53 | -0.66 | +0 |
| H2 | 2.30 | 2.04 | -0.26 | -0.36 | +0 |
| all-in | 1.86 | 1.81 | -0.05 | -0.10 | +0 |
Trades kept (all-in): 7159 vs 7320. Weekly correlation with the pair 0.97.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +0).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 +0.27, null mean -0.02, real rank 0.44; clean p95 +0.34 rank 0.74; H1 rank 0.27; H2 rank 0.29).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.26, +0.15]; clean [-0.04, +0.27]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: A x0.75 -0.15, A x1.25 -0.06, k x0.75 -0.03, k x1.25 -0.04).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.97); no hedge claim.
10. NT8-codable: yes. NT8: same equity watcher as the live combined lock with a second (arm, keep) pair. Margin unchanged. Executable at NinjaTrader Brokerage via Rithmic.
Replication (reported, Amend. 2): H0 window 2023-02-10..2023-07-31 uplift +0.18; alternating months: odd->even: selected A4_k0.5 -0.06 -> read +0.02; even->odd: selected A3_k0.5 +0.10 -> read -0.28. Cross-instrument: n/a (pair engine is NQ only).
Overall: NO.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean H0c | 1.58 | 2.94 | 5.63 | -78.7k | -78.0k | 245k | -81.9k | 41.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 H0c | 2.30 | 5.09 | 3.21 | -77.6k | -66.6k | 162k | -78.3k | 46.4 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 H0c | 2.04 | 4.09 | 3.09 | -81.1k | -79.2k | 217k | -82.5k | 47.2 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all H0c | 1.81 | 3.50 | 10.50 | -79.2k | -78.2k | 245k | -82.5k | 43.5 |
Constant-risk/insurance read (all-in): cost -4.2% of net, CVaR5 improvement +0.0%, worst week +0.0%, maxDD +12.6% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
Only the loosest tiers are non-negative on clean (A4 k0.5 +0.12, A5 k0.5 +0.08; tighter keep fractions lose 0.04-0.44). The carried A4 k0.5 fires earlier than the live trigger on 22% of active days, banks the peak on some days but cuts the continuation that makes the live 67% give-back optimal: H1 -0.53, H2 -0.26, plateau 0/4. The worst-week figure is unchanged (the worst weeks are loss weeks, not give-back weeks). H0 window +0.18, alternating-month odd->even selection -0.06 so no replication.
Files: code/census/night_ins/ap_h0_core.py, ap_h0_run.py, ap_h0_rep.py, ap_h0_mkrep.py; outputs/autopilot/h0c/{H0c_all.pkl,H0c_summary.json}. No stand-alone book series (pair rule), nothing saved to the library.

DONE H0c
