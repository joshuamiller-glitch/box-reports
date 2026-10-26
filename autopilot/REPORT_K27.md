# REPORT K27 - last two RTH hours (14:00-16:00 ET) half size
**Verdict: NO. FOUND 0. Carried cell m0.5_14to16: weekly Sharpe uplift -0.04 clean / -0.07 H1 / -0.04 H2 (needed +0.10 on each); all-in -0.05; plateau 0 of 4 neighbours; random-placement null all-in p95 +0.11 (rank 0.58); bootstrap 90% CI of all-in uplift [-0.11, +0.02]; 2x slippage uplift -0.01/-0.04/-0.04.** BACKLOG2 item 27 (M8 sizing, D06 H3). Pre-registered in PREREG_AUTOPILOT.md (BACKLOG2 GROUP C, worker K) before the first run. Pool of 5, run a few minutes.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine in a clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_k22_core.py); state uses only trades closed before the entry. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Dollar rules (per-book 5R/-2R, day cap 8R / 67% give-back, week floor -8R) unchanged.
- Rule: entries with ET time in [14:00, 16:00) trade 4 lots (m = 0.5); others unchanged, not re-normalised.
- Grid: 1 cell. Plateau: m dev x0.75/x1.25 (0.625, 0.375) and window width 90/150 min.
- Selection on clean only (cells changing >= 5% of clean raw entries; else all); H1/H2 read once for the carried cell. Share of clean raw entries changed by the carried cell: 5.3%; actions 5.3% of clean raw entries halved. Clean uplift of all cells: m0.5_14to16 -0.04.
- Disclosure: before the runner I smoke-tested every pre-registered cell once and saw all spans; no cell, window or parameter was changed afterwards, selection is by the clean rule above.
- Relation to tested families: Near-duplicate of G6a LATE_m0.5 (14:00-17:00, mean-normalised, clean -0.01). Difference: window ends 16:00 and no re-normalisation (a pure risk cut). Result is the same: ~0 on every span (-0.04/-0.07/-0.04), as expected since the cut removes 5% of risk uniformly with no timing information.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (ERA FLAG n/a; limit of the test).

## Result (weekly Sharpe)
| span | pair | K27 | uplift | 2x slip uplift | uplift vs B.Cfg() base | worst-week delta ($) |
|---|---|---|---|---|---|---|
| clean | 1.46 | 1.42 | -0.04 | -0.01 | +0.12 | +0 |
| H1 | 2.83 | 2.76 | -0.07 | -0.04 | +0.11 | +0 |
| H2 | 2.30 | 2.26 | -0.04 | -0.04 | -0.03 | +1,337 |
| all-in | 1.86 | 1.81 | -0.05 | -0.02 | +0.09 | +651 |
Trades kept (all-in): 7330 vs 7320. Weekly correlation with the pair 1.00.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week not worse (all-in +651; per span clean +0 / H1 +0 / H2 +1,337): PASS.
5. Own timing-destroyed null, real all-in uplift above p95: FAIL (all-in p95 +0.11, null mean -0.08, real rank 0.58; clean p95 +0.06 rank 0.72; H1 rank 0.27; H2 rank 0.57). Null: m = 0.5 applied to a random set of entries of the same count (100 draws).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.11, +0.02]; clean [-0.14, +0.05]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (neighbour all-in uplifts: m dev x0.75 -0.04, m dev x1.25 -0.05, width x0.75 -0.06, width x1.25 -0.03).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 1.00); no hedge claim.
10. NT8-codable: yes. NT8: Quantity = 4 when time of entry in [14:00, 16:00) ET. Margin lower. Integer lots. Executable at NinjaTrader Brokerage via Rithmic.
11. Replication (Amend. 2, need 2 of: newest live weeks n/a, H0, ES/RTY n/a, alternating months): H0 2023-02-10..07-31 uplift +0.03 (fails); alternating months odd->even: selected m0.5_14to16 +0.07 -> read -0.13; even->odd: selected m0.5_14to16 -0.13 -> read +0.07 (fails) -> 0 of 2 available: FAIL.
Overall: NO.

## Insurance metrics (weekly; candidate vs pair; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean K27 | 1.42 | 2.64 | 4.51 | -78.7k | -78.0k | 283k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 K27 | 2.76 | 5.92 | 3.81 | -77.6k | -65.5k | 151k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 K27 | 2.26 | 4.58 | 3.39 | -80.4k | -78.9k | 218k | -81.2k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all K27 | 1.81 | 3.49 | 9.16 | -79.1k | -78.2k | 283k | -81.9k | 42.9 |
Constant-risk/insurance read (all-in): cost -3.5% of net, CVaR5 change +0.1%, worst week +0.8%, maxDD -1.0% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Reading
The cut is indistinguishable from a random 5% size cut (null rank 0.72 on clean: random halving does as well) and it shrinks all spans slightly: late-session entries earn their share. Worst week is unchanged on clean/H1 and $1.3k better on H2 only. Closes D06/D00 H3 M8 NQ (late-RTH size cut).
Files: code/census/night_ins/ap_k22_core.py, ap_k22_run.py, ap_h0_rep.py, ap_k22_mkrep.py; outputs/autopilot/k27/{K27_all.pkl,K27_summary.json}. Pair rule, no stand-alone book series: nothing saved to the library.

DONE K27
