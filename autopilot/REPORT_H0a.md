# REPORT H0a - concurrent ST+HM same-direction stacking multiplier
**Verdict: NO. FOUND 0, LEAD 0. Carried cell a0.5_b1: weekly Sharpe uplift -0.12 clean / +0.06 H1 / +0.17 H2 (needed +0.10 on each); all-in -0.00; plateau 0 of 2 neighbours; bootstrap 90% CI of all-in uplift [-0.43, +0.43]; 2x slippage uplift -0.04/-0.36/-0.28.** Use-mode M4/M8 pair conditioning, horizons H1-H3. Pre-registered in PREREG_AUTOPILOT.md (H0 batch) before the first run. Pool of 5.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine, clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_h0_core.py), lock stage copy with an optional second tier. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and variant. State uses only trades closed (or open) at the entry time.
- Rule: when the other book has an accepted open position at entry: same direction x a, opposite direction x b (neither changes the live per-book/day/week rules).
- Grid: 11 cells: a {1,0,0.5,1.5} x b {1,0.5,0,1.5} minus (1,1). Opposite-direction concurrency never occurs in the live rows (the opposite signal nets the open position first), so all b values are identical and the grid is effectively a in {0, 0.5, 1.5}.
- Selection on clean only, highest clean uplift among cells that change >= 5% of clean entries; one cell carried; H1/H2 read once. Clean uplift of all cells: a1_b0.5 +0.00, a1_b0 +0.00, a1_b1.5 +0.00, a0_b1 -0.33, a0_b0.5 -0.33, a0_b0 -0.33, a0_b1.5 -0.33, a0.5_b1 -0.12, a0.5_b0.5 -0.12, a0.5_b0 -0.12, a0.5_b1.5 -0.12, a1.5_b1 -0.19, a1.5_b0.5 -0.19, a1.5_b0 -0.19, a1.5_b1.5 -0.19.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (flag n/a; a limit of the test).

## Result (weekly Sharpe)
| span | pair | H0a | uplift | 2x slip uplift | worst-week delta ($) |
|---|---|---|---|---|---|
| clean | 1.46 | 1.34 | -0.12 | -0.04 | +2,276 |
| H1 | 2.83 | 2.89 | +0.06 | -0.36 | +861 |
| H2 | 2.30 | 2.46 | +0.17 | -0.28 | +4,489 |
| all-in | 1.86 | 1.85 | -0.00 | -0.12 | +2,926 |
Trades kept (all-in): 8678 vs 7320. Weekly correlation with the pair 0.87.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +2,926).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 +0.21, null mean -0.19, real rank 0.73; clean p95 +0.29 rank 0.62; H1 rank 0.35; H2 rank 0.83).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.43, +0.43]; clean [-0.57, +0.37]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: a x0.75 -0.16, a x1.25 -0.19).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.87); no hedge claim.
10. NT8-codable: yes. NT8: at OnOrderUpdate of the second strategy, read the other strategy Position (same account) and scale Quantity by a. Margin: a=0.5 lowers it; a=1.5 raises peak margin to 12+ contracts of one direction. Executable at NinjaTrader Brokerage via Rithmic.
Replication (reported, Amend. 2): H0 window 2023-02-10..2023-07-31 uplift -0.93; alternating months: odd->even: selected a1.5_b1 +0.06 -> read -0.45; even->odd: selected a0_b1 +0.65 -> read -1.08. Cross-instrument: n/a (pair engine is NQ only).
Overall: NO.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean H0a | 1.34 | 2.24 | 3.15 | -78.2k | -77.8k | 333k | -79.6k | 41.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 H0a | 2.89 | 6.44 | 3.29 | -66.4k | -58.9k | 166k | -77.4k | 32.1 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 H0a | 2.46 | 6.02 | 3.88 | -77.6k | -68.0k | 216k | -78.0k | 50.0 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all H0a | 1.85 | 3.49 | 7.32 | -78.0k | -77.6k | 333k | -79.6k | 42.3 |
Constant-risk/insurance read (all-in): cost -9.3% of net, CVaR5 improvement +1.5%, worst week +3.5%, maxDD -18.8% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
Every stacking cell is negative on clean (a=0 -0.33, a=0.5 -0.12, a=1.5 -0.19). Same-direction concurrency covers 29-34% of clean entries and those second entrants are as good as the first on average: cutting them removes edge in proportion to the risk, boosting them adds variance faster than mean. The carried cell is therefore a loss-making selection, and its H1/H2 gains (+0.06/+0.17) are noise (null rank 0.35/0.83). The weekly correlation with the pair is 0.87.
Files: code/census/night_ins/ap_h0_core.py, ap_h0_run.py, ap_h0_rep.py, ap_h0_mkrep.py; outputs/autopilot/h0a/{H0a_all.pkl,H0a_summary.json}. No stand-alone book series (pair rule), nothing saved to the library.

DONE H0a
