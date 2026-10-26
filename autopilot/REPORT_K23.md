# REPORT K23 - anti-martingale day start (half size until the day pays)
**Verdict: NO. FOUND 0, LEAD 0. Carried cell c_until_+0.5R: weekly Sharpe uplift -0.14 clean / +0.30 H1 / +0.84 H2 (needed +0.10 on each); all-in +0.22; plateau 1 of 4 neighbours; bootstrap 90% CI of all-in uplift [-0.41, +0.89]; 2x slippage uplift -0.02/+0.30/+0.69.** Use-mode M8 sizing, horizons H2-H3. Pre-registered in PREREG_AUTOPILOT.md (K19/K20/K21/K23 block) before the first run. Pool of 5.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine, clean process, reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). pass1 copy with a state hook (ap_kc_core.py, on ap_h0_core/ap_g0_core), optional per-book give-back stage before the combined lock. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and variant. State uses only trades closed (or open) at the entry time.
- Rule: entries at m=0.5 until a condition holds (a: only the first entry of the day; b: until a closed winner exists today; c: until day realised P&L >= +0.5R), then full.
- Grid: 3 cells (fixed in the pre-registration because the backlog gives no grid): a_first_half, b_until_win, c_until_+0.5R. Differs from H0b (stop-out window) and G0b/B17 (multi-day/prior-day state): conditions on the day's own opening P&L state.
- Selection on clean only, highest clean uplift among cells that change >= 5% of clean entries; one cell carried; H1/H2 read once. Clean uplift of all cells: a_first_half -0.74, b_until_win -0.92, c_until_+0.5R -0.14.
- ERA: engine rows start 2023-02, so a 2013-22 re-test does not exist for a pair-state rule (flag n/a; a limit of the test).

## Result (weekly Sharpe)
| span | pair | K23 | uplift | 2x slip uplift | worst-week delta ($) |
|---|---|---|---|---|---|
| clean | 1.46 | 1.32 | -0.14 | -0.02 | +3,653 |
| H1 | 2.83 | 3.13 | +0.30 | +0.30 | +1,464 |
| H2 | 2.30 | 3.13 | +0.84 | +0.69 | +3,379 |
| all-in | 1.86 | 2.07 | +0.22 | +0.25 | +3,379 |
Trades kept (all-in): 10224 vs 7320. Weekly correlation with the pair 0.73.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +3,379).
5. Matched null, real all-in uplift above p95: PASS (all-in p95 +0.20, null mean -0.29, real rank 0.97; clean p95 +0.19 rank 0.76; H1 rank 0.53; H2 rank 0.99).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.41, +0.89]; clean [-0.93, +0.70]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: m x0.75 -0.15, thr x0.75 -0.07, m x1.25 +0.02, thr x1.25 +0.23).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.73); no hedge claim.
10. NT8-codable: yes. NT8: static day P&L and winner flag shared by the two strategies (same account); scale Quantity by 0.5 (min 1 contract per book) until the condition holds. Margin lower early in day. Executable. Executable at NinjaTrader Brokerage via Rithmic.
Replication (reported, Amend. 2): H0 window 2023-02-10..2023-07-31 uplift -0.39; alternating months: odd->even: selected c_until_+0.5R -0.29 -> read +0.61; even->odd: selected c_until_+0.5R +0.61 -> read -0.29. Cross-instrument: n/a (pair engine is NQ only).
Overall: NO. Replication fails or n/a: same-sign >= 50% of uplift needed on two of the replication legs.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean K23 | 1.32 | 2.32 | 3.19 | -77.6k | -70.3k | 281k | -78.2k | 45.7 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 K23 | 3.13 | 6.52 | 5.26 | -68.8k | -61.0k | 115k | -76.8k | 28.6 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 K23 | 3.13 | 8.17 | 5.19 | -78.8k | -58.9k | 185k | -79.1k | 38.9 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all K23 | 2.07 | 4.14 | 8.77 | -77.8k | -68.2k | 281k | -79.1k | 41.7 |
Constant-risk/insurance read (all-in): cost -8.3% of net, CVaR5 improvement +1.8%, worst week +4.1%, maxDD -0.2% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
Every cell loses on clean (a -0.74, b -0.92, c -0.14); the least bad (c, half size until +0.5R realised, active on 72% of entries) is carried and it reverses sign: H1 +0.30, H2 +0.84. That is the classic pattern in reverse (clean loss, later gain), the selection rule forces the carried cell, so it fails gate 3 on clean; the later-span gain is non-virgin evidence after the clean loss and cannot make it FOUND. Half sizing cuts risk capital early in the day and so cuts gross P&L on the best days (the live system is flat-sized with locks for good reason in 2023-25), but it helps in 2025-26. Disclosed as a regime observation, not a lead: clean -0.14 (fail), plateau 1 of 4, bootstrap CI [-0.41,+0.89], H0 -0.39, alternating months odd->even selection -0.29 / read +0.61.
Files: code/census/night_ins/ap_h0_core.py, ap_kc_core.py, ap_kc_run.py, ap_h0_rep.py, ap_kc_mkrep.py; outputs/autopilot/k23/{K23_all.pkl,K23_summary.json}. No stand-alone book series (pair rule), nothing saved to the library.

DONE K23
