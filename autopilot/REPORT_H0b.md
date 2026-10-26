# REPORT H0b - re-entry cluster after a stop-out (time window)
**Verdict: NO. FOUND 0, LEAD 0. Carried cell same_N45_m1.5: weekly Sharpe uplift +0.19 clean / -0.29 H1 / -0.24 H2 (needed +0.10 on each); all-in +0.05; plateau 1 of 4 neighbours; bootstrap 90% CI of all-in uplift [-0.11, +0.21]; 2x slippage uplift +0.18/-0.17/-0.49.** Use-mode M4/M7 pair conditioning, horizons H1-H2. Pre-registered in PREREG_AUTOPILOT.md (H0 batch) before the first run. Pool of 5.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine, clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_h0_core.py), lock stage copy with an optional second tier. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and variant. State uses only trades closed (or open) at the entry time.
- Rule: multiply an entry by m if any accepted trade of either book exited by a stop in the previous N minutes on the same (or the opposite) side.
- Grid: 18 cells: side {same,opp} x N {5,15,45} min x m {0,0.5,1.5}.
- Selection on clean only, highest clean uplift among cells that change >= 5% of clean entries; one cell carried; H1/H2 read once. Clean uplift of all cells: same_N5_m0 +0.08, same_N5_m0.5 -0.00, same_N5_m1.5 -0.24, same_N15_m0 -0.04, same_N15_m0.5 -0.03, same_N15_m1.5 -0.17, same_N45_m0 -0.20, same_N45_m0.5 -0.20, same_N45_m1.5 +0.19, opp_N5_m0 +0.11, opp_N5_m0.5 -0.02, opp_N5_m1.5 -0.22, opp_N15_m0 +0.10, opp_N15_m0.5 -0.06, opp_N15_m1.5 -0.05, opp_N45_m0 +0.01, opp_N45_m0.5 -0.11, opp_N45_m1.5 -0.13.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (flag n/a; a limit of the test).

## Result (weekly Sharpe)
| span | pair | H0b | uplift | 2x slip uplift | worst-week delta ($) |
|---|---|---|---|---|---|
| clean | 1.46 | 1.65 | +0.19 | +0.18 | +2,006 |
| H1 | 2.83 | 2.54 | -0.29 | -0.17 | -997 |
| H2 | 2.30 | 2.05 | -0.24 | -0.49 | +3,226 |
| all-in | 1.86 | 1.91 | +0.05 | +0.00 | +2,657 |
Trades kept (all-in): 7155 vs 7320. Weekly correlation with the pair 0.97.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +2,657).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 +0.23, null mean -0.07, real rank 0.77; clean p95 +0.23 rank 0.93; H1 rank 0.23; H2 rank 0.30).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.11, +0.21]; clean [+0.04, +0.36]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: N x0.75 -0.11, m x0.75 -0.10, N x1.25 +0.09, m x1.25 -0.02).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.97); no hedge claim.
10. NT8-codable: yes. NT8: keep last-stop time and side per account (OnExecutionUpdate on stop fills); scale Quantity in the next entry. Boost cell raises per-entry risk to 1.5x for 5% of entries. Executable at NinjaTrader Brokerage via Rithmic.
Replication (reported, Amend. 2): H0 window 2023-02-10..2023-07-31 uplift -0.30; alternating months: odd->even: selected opp_N5_m0 +0.19 -> read +0.09; even->odd: selected same_N45_m0 +0.27 -> read -0.30. Cross-instrument: n/a (pair engine is NQ only).
Overall: NO.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean H0b | 1.65 | 3.14 | 5.51 | -78.0k | -77.6k | 274k | -79.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 H0b | 2.54 | 5.72 | 3.51 | -78.6k | -78.1k | 187k | -79.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 H0b | 2.05 | 4.57 | 3.43 | -78.7k | -78.0k | 223k | -79.3k | 47.2 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all H0b | 1.91 | 3.85 | 10.70 | -78.4k | -77.8k | 274k | -79.9k | 43.5 |
Constant-risk/insurance read (all-in): cost +9.1% of net, CVaR5 improvement +1.1%, worst week +3.2%, maxDD +2.2% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
Skip/halve cells are small and mixed (best skip: opposite-side within 5 min, m=0, +0.11 clean on 2.5% of entries); the selected cell is a BOOST (same side within 45 min, x1.5, 5.2% of entries, +0.19 clean) that reverses on H1 (-0.29) and H2 (-0.24). A stop-out is not informative about the next signal beyond what G0a found: neither a whipsaw regime nor a post-sweep impulse separates in time. Weekly corr with the pair 0.97 (the rule touches 5% of entries).
Files: code/census/night_ins/ap_h0_core.py, ap_h0_run.py, ap_h0_rep.py, ap_h0_mkrep.py; outputs/autopilot/h0b/{H0b_all.pkl,H0b_summary.json}. No stand-alone book series (pair rule), nothing saved to the library.

DONE H0b
