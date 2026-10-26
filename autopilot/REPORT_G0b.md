# REPORT G0b - multi-day equity-curve drawdown size step-down
**Verdict: NO. FOUND 0, LEAD 0. Carried cell W20_X6_k0.5: weekly Sharpe uplift +0.16 clean / -0.91 H1 / -0.77 H2 (needed +0.10 on each); all-in -0.20; plateau 0 of 6 neighbours; bootstrap 90% CI of all-in uplift [-0.73, +0.33]; 2x slippage uplift +0.18/-0.73/-0.76.** Use-mode M8 sizing, horizons H3-H4. Pre-registered in PREREG_AUTOPILOT.md (G0 batch) before the first run. Pool of 5, about 15-20 min incl. 100-draw null.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine in a clean process (reproduced 1.46 / 2.83 / 2.30; all-in 1.86). pass1 copy with a state hook (ap_g0_core.py); state uses only trades closed before the entry. Dollar rules (per-book 5R/-2R, day cap 8R / 67% give-back, week floor -8R) unchanged. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Whole-lot: rule is skip-or-multiply by 0.5/0.25 (4 or 2 lots) so integer-lot executable.
- Rule: trade at fraction k of size while realised pair equity (closed accepted trades) is >= X R below its trailing W-trading-day peak; resume at X/2 R (hysteresis). Grid: 8 cells: W{10,20} x X{6,10}R x k{0.5,0.25}. nfired n/a (a sizing rule; null = circular shift of the per-trade multiplier sequence).
- Selection on clean only, among cells changing >= 5% of clean raw entries; one cell carried; H1/H2 read once. Clean uplift of all cells: W10_X6_k0.5 -0.18, W10_X6_k0.25 -0.96, W10_X10_k0.5 -0.08, W10_X10_k0.25 -0.32, W20_X6_k0.5 +0.16, W20_X6_k0.25 +0.12, W20_X10_k0.5 +0.15, W20_X10_k0.25 -0.14.
- ERA: the live engine rows start 2023-08, so no 2013-22 replication exists for a pair-state rule (flag n/a); this is a limit of the test, not evidence.

## Result (weekly Sharpe)
| span | pair | G0b | uplift | vs B.Cfg() uplift (clean/H1/H2) | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.62 | +0.16 | +0.09 | +0.18 |
| H1 | 2.83 | 1.92 | -0.91 | -0.27 | -0.73 |
| H2 | 2.30 | 1.53 | -0.77 | -0.84 | -0.76 |
| all-in | 1.86 | 1.65 | -0.20 | -0.18 | -0.15 |
Trades kept (all-in): 10476 vs 7320. Weekly correlation with the pair 0.85.

## Gate checklist
1. Pre-registered before run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean, H1, H2: FAIL.
4. Worst week (all-in) not worse: PASS (delta +4,446).
5. Matched null, real all-in uplift above p95: FAIL (all-in p95 +0.09, null mean -0.28, real rank 0.57; clean p95 +0.14 rank 0.95; H1 rank 0.02; H2 rank 0.30).
6. Bootstrap 90% CI of all-in uplift > 0: FAIL ([-0.73, +0.33]; clean [-0.38, +0.74]).
7. Plateau (>= 75% of neighbours keep >= 75% of all-in uplift): FAIL (all-in uplifts of neighbours: W x0.75 -0.17, X x0.75 -0.40, k x0.75 -0.56, W x1.25 -0.22, X x1.25 -0.21, k x1.25 -0.03).
8. 2x slippage >= +0.10 each span: FAIL.
9. Worst-decile correlation: not applicable (rule on the pair, weekly corr 0.85); no hedge claim.
10. NT8-codable: yes (strategy-level counters of the day's closed trades / equity; no new data). Margin unchanged or lower than the 16-contract pair. Executable at NinjaTrader Brokerage via Rithmic.
Overall: NO.

## Insurance metrics (weekly; candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean G0b | 1.62 | 3.08 | 5.06 | -72.7k | -62.3k | 215k | -77.0k | 41.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 G0b | 1.92 | 3.38 | 2.34 | -77.9k | -74.0k | 152k | -78.1k | 32.1 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 G0b | 1.53 | 3.21 | 1.81 | -77.4k | -66.3k | 237k | -77.7k | 52.8 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all G0b | 1.65 | 3.17 | 7.88 | -76.3k | -66.5k | 237k | -78.1k | 42.9 |
Constant-risk/insurance read (all-in): cost -30.4% of net, CVaR5 improvement +3.6%, worst week +5.4%, maxDD +15.4% -> INSURANCE verdict NO (needs cost >= -5% and CVaR5/worst week >= +25% or maxDD >= +20%).

## Why
The step-down de-risks 57-81% of entries (the pair is in a >= 6-10R drawdown from its 10-20 day peak most of the time, because the book is a high-variance 43%-negative-week strategy), so it behaves as a blanket 0.5x size with timing noise. Clean +0.16 beats the shifted-multiplier null p95 (rank 0.95) but H1 -0.91, H2 -0.77, and the all-in net is -30%. As with B16, drawdowns of this pair are not predictive of worse next trades.
Files: code/census/night_ins/ap_g0_core.py, ap_g0_run.py, ap_g0_rep.py, ap_g0_mkrep.py; outputs/autopilot/g0b/{G0b_all.pkl,G0b_summary.json}. No book series (pair rule), so nothing saved to the library.

DONE G0b
