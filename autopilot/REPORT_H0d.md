# REPORT H0d - entry confirmation delay (1-3 min, move-in-direction filter)
**Verdict: NO. FOUND 0, LEAD 0. Carried cell d1_cNone: weekly Sharpe uplift +0.04 clean / -0.80 H1 / -0.90 H2 (needed +0.10 on each); all-in -0.28; plateau 0 of 2 neighbours; bootstrap 90% CI of all-in uplift [-0.70, +0.12]; 2x slippage uplift +0.15/-0.94/-0.98.** Use-mode M6 execution, horizons H0-H2. Pre-registered in PREREG_AUTOPILOT.md (H0 batch) before the first run. Pool of 5.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine, clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). 1-second replay of all 13,089 rows (G11-C/D2-E5 machinery). Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and variant. State uses only trades closed (or open) at the entry time.
- Rule: re-enter at the open of minute ei+d (fresh 60/60 bracket from the new fill, state and locks see the delayed timestamp), skipped when the signal row already exited or when the move since the signal fill is below c points in the trade direction.
- Grid: 12 cells: d {1,2,3} min x c {none,0,5,10} pts on the 13,089-row 1-second engine (control d=0 reproduces the live 1.46/2.83/2.30 exactly).
- Selection on clean only, highest clean uplift among cells that change >= 5% of clean entries; one cell carried; H1/H2 read once. Clean uplift of all cells: d1_cNone +0.04, d1_c0 -1.27, d1_c5 -1.38, d1_c10 -1.15, d2_cNone -0.69, d2_c0 -0.56, d2_c5 -1.68, d2_c10 -2.89, d3_cNone -0.61, d3_c0 -1.07, d3_c5 -0.93, d3_c10 -2.81.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (flag n/a; a limit of the test).

## Result (weekly Sharpe)
| span | pair | H0d | uplift | 2x slip uplift | worst-week delta ($) |
|---|---|---|---|---|---|
| clean | 1.46 | 1.50 | +0.04 | +0.15 | +926 |
| H1 | 2.83 | 2.03 | -0.80 | -0.94 | +529 |
| H2 | 2.30 | 1.39 | -0.90 | -0.98 | +3,271 |
| all-in | 1.86 | 1.58 | -0.28 | -0.25 | +1,577 |
Trades kept (all-in): 7122 vs 7320. Weekly correlation with the pair 0.90.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +1,577).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 -0.28, null mean -0.28, real rank 0.00; clean p95 +0.04 rank 0.00; H1 rank 0.00; H2 rank 0.00).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.70, +0.12]; clean [-0.36, +0.46]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: d=0 +0.00, d=2 -0.88).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.90); no hedge claim.
10. NT8-codable: yes. NT8: replace market entry by a timer/bar-count entry: submit the market order at the open of the d-th bar after the signal if Close[0]-signal price in the trade direction >= c. Executable; costs one more bar of latency risk. Executable at NinjaTrader Brokerage via Rithmic.
Replication (reported, Amend. 2): H0 window 2023-02-10..2023-07-31 uplift -0.49; alternating months: odd->even: selected d1_cNone -0.56 -> read +0.02; even->odd: selected d3_c5 +0.12 -> read -1.49. Cross-instrument: n/a (pair engine is NQ only).
Overall: NO.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean H0d | 1.50 | 2.73 | 3.89 | -79.2k | -78.4k | 356k | -80.9k | 40.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 H0d | 2.03 | 4.37 | 2.75 | -77.6k | -77.5k | 189k | -77.8k | 42.9 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 H0d | 1.39 | 2.58 | 1.96 | -78.5k | -78.0k | 245k | -79.3k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all H0d | 1.58 | 2.94 | 6.70 | -78.9k | -78.2k | 356k | -80.9k | 41.7 |
Constant-risk/insurance read (all-in): cost -11.2% of net, CVaR5 improvement +0.4%, worst week +1.9%, maxDD -26.9% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
Pure delay is the best cell on clean only by +0.04 and is -0.80/-0.90 on H1/H2: waiting gives away the first minute of the trend that the 1-minute flip is paying for. Confirmation filters cut 50-90% of trades (c=0 keeps about half) and every one loses 0.56-2.9 Sharpe on clean: the immediate reversals that confirmation avoids are not worth the lost winners and the worse fill (the filter keeps half or fewer of the entries and gives up the fill price of the ones it keeps). The null for the carried cell is degenerate (a pure delay skips nothing), so the gate-5 line is not informative; the verdict rests on gate 3.
Files: code/census/night_ins/ap_h0_core.py, ap_h0d_core.py, ap_h0d_run.py, ap_h0_rep.py, ap_h0_mkrep.py; outputs/autopilot/h0d/{H0d_all.pkl,H0d_summary.json}. No stand-alone book series (pair rule), nothing saved to the library.

DONE H0d
