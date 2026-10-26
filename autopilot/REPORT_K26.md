# REPORT K26 - block entries while combined open risk >= 1.5R / 2R
**Verdict: NO. FOUND 0. Carried cell X1.5: weekly Sharpe uplift -0.36 clean / -0.04 H1 / -0.09 H2 (needed +0.10 on each); all-in -0.19; plateau 0 of 2 neighbours; random-placement null all-in p95 -0.05 (rank 0.87); bootstrap 90% CI of all-in uplift [-0.84, +0.49]; 2x slippage uplift -0.22/+0.02/-0.32.** BACKLOG2 item 26 (M7 risk rule, D00 H1-H2). Pre-registered in PREREG_AUTOPILOT.md (BACKLOG2 GROUP C, worker K) before the first run. Pool of 5, run a few minutes.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine in a clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_k22_core.py); state uses only trades closed before the entry. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Dollar rules (per-book 5R/-2R, day cap 8R / 67% give-back, week floor -8R) unchanged.
- Rule: open risk = proposed entry (1R) + sum over open accepted trades of (60 + u)/60 R, u = unrealised points clipped to [-60,+60] measured from the entry bar open of the new row; block the entry when the total >= X R and another position is open.
- Grid: 2 cells: X in {1.5, 2.0}. Plateau: X x0.75/x1.25 (1.125, 1.875). Nominal-1R-per-trade reading is degenerate (max 2 concurrent positions of 1R) and was not run.
- Selection on clean only (cells changing >= 5% of clean raw entries; else all); H1/H2 read once for the carried cell. Share of clean raw entries changed by the carried cell: 27.5%; actions X1.5: 3,288 blocked raw entries (27.5% of clean raw entries). Clean uplift of all cells: X1.5 -0.36, X2.0 -0.73.
- Disclosure: before the runner I smoke-tested every pre-registered cell once and saw all spans; no cell, window or parameter was changed afterwards, selection is by the clean rule above.
- Relation to tested families: H0a tested a same-direction stacking multiplier; K26 blocks on mark-to-market distance to stop. Both say concurrency is not the problem: cutting overlapping entries removes edge in proportion (X1.5 -0.36, X2 -0.73 on clean).
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (ERA FLAG n/a; limit of the test).

## Result (weekly Sharpe)
| span | pair | K26 | uplift | 2x slip uplift | uplift vs B.Cfg() base | worst-week delta ($) |
|---|---|---|---|---|---|---|
| clean | 1.46 | 1.10 | -0.36 | -0.22 | -0.15 | +4,192 |
| H1 | 2.83 | 2.79 | -0.04 | +0.02 | +0.60 | +255 |
| H2 | 2.30 | 2.20 | -0.09 | -0.32 | -0.28 | +4,766 |
| all-in | 1.86 | 1.67 | -0.19 | -0.14 | -0.03 | +4,492 |
Trades kept (all-in): 6883 vs 7320. Weekly correlation with the pair 0.71.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week not worse (all-in +4,492; per span clean +4,192 / H1 +255 / H2 +4,766): PASS.
5. Own timing-destroyed null, real all-in uplift above p95: FAIL (all-in p95 -0.05, null mean -0.46, real rank 0.87; clean p95 +0.19 rank 0.39; H1 rank 0.91; H2 rank 0.91). Null: the same number of skips drawn at random among entries that have another position open (100 draws).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.84, +0.49]; clean [-1.12, +0.46]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (neighbour all-in uplifts: X x0.75 -0.03, X x1.25 -0.31).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.71); no hedge claim.
10. NT8-codable: yes. NT8: read the other strategy Position and unrealised points via the shared account; block when the computed open risk >= X. Margin lower (never 16 contracts of risk). Executable at NinjaTrader Brokerage via Rithmic.
11. Replication (Amend. 2, need 2 of: newest live weeks n/a, H0, ES/RTY n/a, alternating months): H0 2023-02-10..07-31 uplift -0.81 (fails); alternating months odd->even: selected X1.5 -1.11 -> read +0.72; even->odd: selected X1.5 +0.72 -> read -1.11 (fails) -> 0 of 2 available: FAIL.
Overall: NO.

## Insurance metrics (weekly; candidate vs pair; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean K26 | 1.10 | 1.78 | 2.15 | -77.3k | -72.0k | 326k | -77.7k | 43.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 K26 | 2.79 | 5.42 | 3.23 | -77.6k | -67.9k | 164k | -78.0k | 32.1 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 K26 | 2.20 | 4.76 | 4.63 | -77.3k | -72.6k | 158k | -77.8k | 38.9 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all K26 | 1.67 | 3.04 | 6.02 | -77.4k | -73.1k | 326k | -78.0k | 41.1 |
Constant-risk/insurance read (all-in): cost -26.9% of net, CVaR5 change +2.3%, worst week +5.4%, maxDD -16.4% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Reading
Both cells are strongly negative on clean (-0.36, -0.73) and every span: the second concurrent entry is as good as the first and the rule removes 21-28% of entries. The worst week improves by $4.5k all-in (+5.4%) but net P&L falls 26.9%, CVaR5 improves only 2.3% and maxDD is 16% worse, so it is not insurance. The random concurrent-skip null (clean rank 0.39) shows the rule is no better than skipping the same number of concurrent entries at random. Closes D00 H1/H2 M7 NQ (open-risk gate).
Files: code/census/night_ins/ap_k22_core.py, ap_k22_run.py, ap_h0_rep.py, ap_k22_mkrep.py; outputs/autopilot/k26/{K26_all.pkl,K26_summary.json}. Pair rule, no stand-alone book series: nothing saved to the library.

DONE K26
