# REPORT K22 - synchronised-whipsaw lock (both books stopped within 5 min -> halt 30/60 min)
**Verdict: NO. FOUND 0. Carried cell H60: weekly Sharpe uplift +0.02 clean / -0.42 H1 / -0.33 H2 (needed +0.10 on each); all-in -0.11; plateau 0 of 4 neighbours; random-placement null all-in p95 +0.34 (rank 0.24); bootstrap 90% CI of all-in uplift [-0.47, +0.24]; 2x slippage uplift +0.19/-0.38/-0.63.** BACKLOG2 item 22 (M7 risk rule, D00 H1-H2). Pre-registered in PREREG_AUTOPILOT.md (BACKLOG2 GROUP C, worker K) before the first run. Pool of 5, run a few minutes.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine in a clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_k22_core.py); state uses only trades closed before the entry. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Dollar rules (per-book 5R/-2R, day cap 8R / 67% give-back, week floor -8R) unchanged.
- Rule: halt all new entries (both books) for H minutes after the later of two Stop exits from different books that closed within W=5 minutes of each other.
- Grid: 2 cells: H in {30, 60} min (W fixed 5 min). Plateau: H and W x0.75/x1.25.
- Selection on clean only (cells changing >= 5% of clean raw entries; else all); H1/H2 read once for the carried cell. Share of clean raw entries changed by the carried cell: 5.1%; actions H60: 417 trigger events, 673 skipped raw entries. Clean uplift of all cells: H30 -0.16, H60 +0.02.
- Disclosure: before the runner I smoke-tested every pre-registered cell once and saw all spans; no cell, window or parameter was changed afterwards, selection is by the clean rule above.
- Relation to tested families: G0a halts the rest of the day after n consecutive stops of any speed; H11-B after N stops within X min of entry (day-long). K22 triggers on cross-book synchronicity of the exits and is timed (30/60 min): a different trigger and horizon, not a duplicate. E4 (consecutive-stop count x halt length) is a different trigger. Result mirrors them: the response is not smooth (H30 -0.16, H60 +0.02 on clean).
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (ERA FLAG n/a; limit of the test).

## Result (weekly Sharpe)
| span | pair | K22 | uplift | 2x slip uplift | uplift vs B.Cfg() base | worst-week delta ($) |
|---|---|---|---|---|---|---|
| clean | 1.46 | 1.48 | +0.02 | +0.19 | +0.24 | +0 |
| H1 | 2.83 | 2.41 | -0.42 | -0.38 | -0.08 | -405 |
| H2 | 2.30 | 1.96 | -0.33 | -0.63 | -0.61 | +5,109 |
| all-in | 1.86 | 1.74 | -0.11 | -0.07 | +0.00 | +651 |
Trades kept (all-in): 7105 vs 7320. Weekly correlation with the pair 0.93.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week not worse (all-in +651; per span clean +0 / H1 -405 / H2 +5,109): PASS.
5. Own timing-destroyed null, real all-in uplift above p95: FAIL (all-in p95 +0.34, null mean +0.02, real rank 0.24; clean p95 +0.53 rank 0.22; H1 rank 0.25; H2 rank 0.56). Null: each trigger event re-placed at a random entry time of the same label day with the same halt length (100 draws).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.47, +0.24]; clean [-0.39, +0.42]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (neighbour all-in uplifts: H x0.75 -0.07, H x1.25 -0.39, W x0.75 -0.14, W x1.25 -0.10).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.93); no hedge claim.
10. NT8-codable: yes. NT8: strategy-level watcher over the two strategies stop fills (OnExecutionUpdate, exit name Stop); if stop times of ST and HM differ <= 5 min set blockUntil = later + H min and reject entries until then. Margin lower or unchanged. Executable at NinjaTrader Brokerage via Rithmic.
11. Replication (Amend. 2, need 2 of: newest live weeks n/a, H0, ES/RTY n/a, alternating months): H0 2023-02-10..07-31 uplift +0.08 (fails); alternating months odd->even: selected H30 -0.39 -> read +0.17; even->odd: selected H60 +0.46 -> read -0.59 (fails) -> 0 of 2 available: FAIL.
Overall: NO.

## Insurance metrics (weekly; candidate vs pair; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean K22 | 1.48 | 2.74 | 5.04 | -79.1k | -78.4k | 276k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 K22 | 2.41 | 4.93 | 3.03 | -78.4k | -78.2k | 189k | -78.7k | 35.7 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 K22 | 1.96 | 4.11 | 3.29 | -77.3k | -77.0k | 200k | -77.4k | 41.7 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all K22 | 1.74 | 3.35 | 9.51 | -78.8k | -78.2k | 276k | -81.9k | 41.7 |
Constant-risk/insurance read (all-in): cost -2.4% of net, CVaR5 change +0.5%, worst week +0.8%, maxDD +1.6% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Reading
Neither halt length clears +0.10 on clean (H60 +0.02 is the carried cell, below the 0.10 gate by selection), H1 -0.42 and H2 -0.33; the 30-min cell is negative on clean. The synchronous-stop event is frequent (417 triggers over 3.5 years) and what follows it is not worse than average: the pair keeps its edge after both books are stopped together. The random-placement null (clean mean +0.19) shows that skipping an arbitrary 30-60 min window of the same count gains more on clean than the rule does (rank 0.22). Closes D00 H1/H2 M7 NQ (synchronised-stop timed halt).
Files: code/census/night_ins/ap_k22_core.py, ap_k22_run.py, ap_h0_rep.py, ap_k22_mkrep.py; outputs/autopilot/k22/{K22_all.pkl,K22_summary.json}. Pair rule, no stand-alone book series: nothing saved to the library.

DONE K22
