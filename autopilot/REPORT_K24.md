# REPORT K24 - hourly per-book risk budget (max -1R per ET hour)
**Verdict: NO. FOUND 0. Carried cell L1.0: weekly Sharpe uplift +0.12 clean / +0.02 H1 / -0.20 H2 (needed +0.10 on each); all-in +0.06; plateau 0 of 2 neighbours; random-placement null all-in p95 +0.25 (rank 0.77); bootstrap 90% CI of all-in uplift [-0.36, +0.48]; 2x slippage uplift +0.23/-0.06/-0.46.** BACKLOG2 item 24 (M7 risk rule, D00 H1-H2). Pre-registered in PREREG_AUTOPILOT.md (BACKLOG2 GROUP C, worker K) before the first run. Pool of 5, run a few minutes.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine in a clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_k22_core.py); state uses only trades closed before the entry. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Dollar rules (per-book 5R/-2R, day cap 8R / 67% give-back, week floor -8R) unchanged.
- Rule: skip a book's entry while the sum of net P&L of that book's trades closed inside the current ET clock hour is <= -1.0R (R = $9,600), until the hour ends. Realised P&L only (no mark-to-market).
- Grid: 1 cell: L = 1.0R. Plateau: L x0.75/x1.25 (0.75R, 1.25R).
- Selection on clean only (cells changing >= 5% of clean raw entries; else all); H1/H2 read once for the carried cell. Share of clean raw entries changed by the carried cell: 6.7%; actions 896 blocked entries (a block fires only when a book closes -1R inside one hour). Clean uplift of all cells: L1.0 +0.12.
- Disclosure: before the runner I smoke-tested every pre-registered cell once and saw all spans; no cell, window or parameter was changed afterwards, selection is by the clean rule above.
- Relation to tested families: Live rules cap per book per DAY (5R win, -2R loss); G0a/H0b use stop counts/times. K24 is P&L-denominated and hour-anchored; not a duplicate. Clean +0.12 but H1 +0.02 and H2 -0.20.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (ERA FLAG n/a; limit of the test).

## Result (weekly Sharpe)
| span | pair | K24 | uplift | 2x slip uplift | uplift vs B.Cfg() base | worst-week delta ($) |
|---|---|---|---|---|---|---|
| clean | 1.46 | 1.58 | +0.12 | +0.23 | +0.27 | -14 |
| H1 | 2.83 | 2.85 | +0.02 | -0.06 | +0.75 | +352 |
| H2 | 2.30 | 2.10 | -0.20 | -0.46 | -0.35 | +1,424 |
| all-in | 1.86 | 1.91 | +0.06 | +0.06 | +0.21 | +636 |
Trades kept (all-in): 7199 vs 7320. Weekly correlation with the pair 0.91.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week not worse (all-in +636; per span clean -14 / H1 +352 / H2 +1,424): PASS.
5. Own timing-destroyed null, real all-in uplift above p95: FAIL (all-in p95 +0.25, null mean -0.06, real rank 0.77; clean p95 +0.36 rank 0.71; H1 rank 0.56; H2 rank 0.64). Null: each blocked (book, hour) re-placed at a random start among that book's entries of the same label day with the same remaining duration (100 draws).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.36, +0.48]; clean [-0.30, +0.58]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (neighbour all-in uplifts: L x0.75 -0.13, L x1.25 -0.16).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.91); no hedge claim.
10. NT8-codable: yes. NT8: per strategy, accumulate realised P&L of trades closed in the current clock hour (reset at the hour); block entries when <= -1R. Margin unchanged. Executable at NinjaTrader Brokerage via Rithmic.
11. Replication (Amend. 2, need 2 of: newest live weeks n/a, H0, ES/RTY n/a, alternating months): H0 2023-02-10..07-31 uplift -0.10 (fails); alternating months odd->even: selected L1.0 -0.22 -> read +0.31; even->odd: selected L1.0 +0.31 -> read -0.22 (fails) -> 0 of 2 available: FAIL.
Overall: NO.

## Insurance metrics (weekly; candidate vs pair; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean K24 | 1.58 | 2.93 | 5.27 | -78.6k | -78.1k | 266k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 K24 | 2.85 | 6.21 | 3.51 | -77.8k | -77.6k | 188k | -77.9k | 35.7 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 K24 | 2.10 | 4.34 | 4.05 | -80.1k | -78.9k | 177k | -81.1k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all K24 | 1.91 | 3.71 | 10.44 | -78.9k | -78.2k | 266k | -81.9k | 42.3 |
Constant-risk/insurance read (all-in): cost +3.6% of net, CVaR5 change +0.4%, worst week +0.8%, maxDD +4.9% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Reading
A single cell that is positive on clean (+0.12, rank 0.71 vs random placement, null p95 +0.36) and fades to +0.02 on H1 and -0.20 on H2: the usual reversal pattern. It binds on 6.7% of clean entries but a lost 1R inside an hour does not predict a worse next entry. The alternating-month split reverses (odd -0.22, even +0.31). Plateau 0/2: 0.75R and 1.25R neighbours do not keep 75% of the all-in uplift (+0.06). Closes D00 H1/H2 M7 NQ (hourly loss budget).
Files: code/census/night_ins/ap_k22_core.py, ap_k22_run.py, ap_h0_rep.py, ap_k22_mkrep.py; outputs/autopilot/k24/{K24_all.pkl,K24_summary.json}. Pair rule, no stand-alone book series: nothing saved to the library.

DONE K24
