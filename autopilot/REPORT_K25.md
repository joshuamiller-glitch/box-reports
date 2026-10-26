# REPORT K25 - same-direction re-entry only after price clears the stop-out level by 10/20 pts
**Verdict: NO. FOUND 0. Carried cell X10: weekly Sharpe uplift +0.08 clean / +0.32 H1 / -0.37 H2 (needed +0.10 on each); all-in +0.02; plateau 2 of 2 neighbours; random-placement null all-in p95 +0.19 (rank 0.23); bootstrap 90% CI of all-in uplift [-0.13, +0.19]; 2x slippage uplift +0.02/+0.36/-0.34.** BACKLOG2 item 25 (M4/M7 pair conditioning, D00 H1-H2). Pre-registered in PREREG_AUTOPILOT.md (BACKLOG2 GROUP C, worker K) before the first run. Pool of 5, run a few minutes.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine in a clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_k22_core.py); state uses only trades closed before the entry. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Dollar rules (per-book 5R/-2R, day cap 8R / 67% give-back, week floor -8R) unchanged.
- Rule: if a book's most recent closed trade (same label day) was a Stop exit in the same direction as the new entry at stop price L, skip the entry unless side x (entry price - L) >= X points.
- Grid: 2 cells: X in {10, 20} pts. Plateau: X x0.75/x1.25.
- Selection on clean only (cells changing >= 5% of clean raw entries; else all); H1/H2 read once for the carried cell. Share of clean raw entries changed by the carried cell: 1.4%; actions X10: 200 skipped raw entries (1.4% of clean raw entries), small-sample flag (< 100 clean trades changed would apply; 156 events all-in). Clean uplift of all cells: X10 +0.08, X20 +0.07.
- Disclosure: before the runner I smoke-tested every pre-registered cell once and saw all spans; no cell, window or parameter was changed afterwards, selection is by the clean rule above.
- Relation to tested families: H0b multiplied entries after a stop within a time window (no price test; best cell a boost) and found nothing; K25 is a price-recovery skip rule, the opposite use. Not a duplicate; result agrees with H0b.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (ERA FLAG n/a; limit of the test).

## Result (weekly Sharpe)
| span | pair | K25 | uplift | 2x slip uplift | uplift vs B.Cfg() base | worst-week delta ($) |
|---|---|---|---|---|---|---|
| clean | 1.46 | 1.54 | +0.08 | +0.02 | +0.20 | +0 |
| H1 | 2.83 | 3.15 | +0.32 | +0.36 | +0.70 | +0 |
| H2 | 2.30 | 1.93 | -0.37 | -0.34 | -0.52 | +0 |
| all-in | 1.86 | 1.88 | +0.02 | -0.01 | +0.12 | +0 |
Trades kept (all-in): 7220 vs 7320. Weekly correlation with the pair 0.98.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week not worse (all-in +0; per span clean +0 / H1 +0 / H2 +0): PASS.
5. Own timing-destroyed null, real all-in uplift above p95: FAIL (all-in p95 +0.19, null mean +0.09, real rank 0.23; clean p95 +0.21 rank 0.43; H1 rank 0.79; H2 rank 0.03). Null: the same number of skips drawn at random among same-book same-direction entries of the same label days (100 draws).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.13, +0.19]; clean [-0.09, +0.30]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): PASS (neighbour all-in uplifts: X x0.75 +0.08, X x1.25 +0.03).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.98); no hedge claim.
10. NT8-codable: yes. NT8: store the last stop-out price/side/time per strategy; reject same-side entries on the same session day until price is X pts beyond. Margin lower. Executable at NinjaTrader Brokerage via Rithmic.
11. Replication (Amend. 2, need 2 of: newest live weeks n/a, H0, ES/RTY n/a, alternating months): H0 2023-02-10..07-31 uplift +0.06 (fails); alternating months odd->even: selected X10 -0.05 -> read +0.08; even->odd: selected X10 +0.08 -> read -0.05 (fails) -> 0 of 2 available: FAIL.
Overall: NO.

## Insurance metrics (weekly; candidate vs pair; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean K25 | 1.54 | 2.87 | 4.58 | -78.9k | -78.1k | 299k | -81.9k | 41.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 K25 | 3.15 | 6.91 | 4.36 | -77.9k | -66.2k | 151k | -78.3k | 32.1 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 K25 | 1.93 | 3.69 | 2.76 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all K25 | 1.88 | 3.57 | 8.80 | -79.3k | -78.3k | 299k | -82.5k | 40.5 |
Constant-risk/insurance read (all-in): cost -2.1% of net, CVaR5 change -0.1%, worst week +0.0%, maxDD -6.7% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Reading
The rule changes only 1.4% of clean entries, below the 5% eligibility line (all cells considered, as pre-registered), so a clean uplift of +0.08 comes from a handful of trades. H1 +0.32 and H2 -0.37; the alternating-month split gives -0.05/+0.08 (neither half reaches +0.10). Stop-outs followed by a same-direction signal are rare (price rarely re-flips the same book in the same direction within the day) and not systematically worse. Closes D00 H1/H2 M4 NQ (stop-level re-entry).
Files: code/census/night_ins/ap_k22_core.py, ap_k22_run.py, ap_h0_rep.py, ap_k22_mkrep.py; outputs/autopilot/k25/{K25_all.pkl,K25_summary.json}. Pair rule, no stand-alone book series: nothing saved to the library.

DONE K25
