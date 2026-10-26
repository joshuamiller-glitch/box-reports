# REPORT B17 - trailing-realised-vol sizing of the live pair (Q-3)
**Verdict: NO. FOUND 0, LEAD 0. Selected cell K=4 wk, band (0.75,1.25): weekly Sharpe uplift +0.21 clean / +0.51 H1 / -0.23 H2 (needed +0.10 on each); plateau 0 of 4 neighbours, bootstrap 90% CI of the all-in uplift [-0.18, +0.51], 2x slippage H2 -0.50.** 4 cells, 17 s per engine run, about 9 min total (pool of 5). Pre-registered in PREREG_AUTOPILOT.md (section B17) before the first run.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common (clean process; reproduced 1.46 / 2.83 / 2.30, all-in 1.86). A weekly multiplier is applied to every entry through B.Cfg.sizefn, so the dollar rules (per-book 5R/-2R, day cap 8R/give-back, week floor -8R) stay fixed in dollars as live. Fill model 1 tick/side + $34.88 per 8 lots (2x slippage: SLIP_PT 1.0 on both baseline and variant). Fractional lots in the main run; a whole-lot rounding run is reported.
- Rule: sigma = stdev of the unit-size daily pair P&L over the last 5K trading days before the Monday open; raw = clip(T/sigma, lo, hi), T = clean median sigma; normalised to mean 1 over clean weeks. Spans clean 2023-08..2025-07, H1 to 2026-02-06, H2 to 2026-10-13.
- Selection on clean only (uplift vs baseline): K4 (0.6,1.4) -0.065; K4 (0.75,1.25) +0.207; K8 (0.6,1.4) +0.008; K8 (0.75,1.25) +0.008. Top cell carried; H1/H2 read once for it. (The unselected cells' H1/H2 are stored in b17/b17_summary.json for transparency and were not used; for the record K8 and K4 wide cells also fail H2: -0.12 to -0.51.)

## Result for the carried cell (weekly Sharpe)
| span | pair | B17 | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.67 | +0.207 | +0.317 | +0.136 |
| H1 | 2.83 | 3.34 | +0.512 | +0.677 | +0.414 |
| H2 | 2.30 | 2.07 | -0.229 | -0.184 | -0.504 |
| all-in | 1.86 | 2.02 | +0.162 | +0.272 | +0.039 |
Whole-lot rounding (round(8m) lots): +0.033 / +0.087 / -0.980 / -0.178 (all-in). The multiplier spans 0.74-1.23 (mean per trade 0.95, 35% of trades above 1), i.e. the live implementation would trade 6-10 lots, and rounding alone destroys the gain.

## Gate checklist
1. Pre-registered before first run: PASS.
2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean / H1 / H2: FAIL on H2 (+0.207 / +0.512 / -0.229).
4. Worst week not worse (all-in): PASS (-$80.8k vs -$82.5k, +$1.7k better).
5. Matched random-size null (100 permutations of the weekly multiplier sequence): clean real +0.207 vs p95 +0.080 (rank 0.99) PASS; all-in +0.162 vs p95 +0.102 (rank 0.97) PASS; H1 rank 0.81 / H2 rank 0.46 (p95 0.80 / 0.44) not exceeded. Mean null uplift is -0.20: random size variation hurts, so the clean gain is not size noise but it is not stable.
6. Bootstrap 90% CI (3000 weekly draws): all-in [-0.18, +0.51], clean [-0.10, +0.57]: FAIL (spans zero).
7. Plateau: K x0.75 / x1.25 -> all-in -0.18 / -0.14; band x0.75 / x1.25 -> +0.09 / -0.04; 0 of 4 keep 75% of +0.162: FAIL.
8. 2x slippage >= +0.10 on clean, H1, H2: FAIL (+0.136 / +0.414 / -0.504).
9. Worst-decile correlation with the pair: not applicable to a size overlay (weekly corr with the pair 0.93); no hedge claim.
10. NT8-codable: yes in principle (weekly lot count from the strategy's own trailing daily P&L divided by size in force; 6-10 lots, margin below the 8-lot book); not recommended.
Overall: NO.

## Insurance metrics (candidate vs pair; weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | n/a | 280k | -81.9k | 42.9 |
| clean B17 | 1.67 | 3.27 | 6.05 | -78.8k | -78.2k | 252k | -80.8k | 41.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | n/a | 152k | -78.3k | 39.3 |
| H1 B17 | 3.34 | 7.88 | 5.77 | -77.5k | -65.2k | 127k | -77.5k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | n/a | 217k | -82.5k | 44.4 |
| H2 B17 | 2.07 | 4.41 | 2.85 | -78.6k | -73.5k | 234k | -80.4k | 50.0 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | n/a | 280k | -82.5k | 42.9 |
| all B17 | 2.02 | 4.11 | 11.61 | -78.7k | -78.0k | 252k | -80.8k | 43.5 |
Constant risk: the normalisation makes mean size neutral, so this is the constant-risk framing; net all-in $2.92m vs pair (cost +8.9% by the ins_metrics convention, i.e. no cost). Tail improvements are tiny (CVaR5 +0.7%, worst week +2.1%, maxDD +10%): INSURANCE verdict NO (needs >= 25% / 20%). The weekly floor at -8R already clips the left tail near -$78k, which leaves sizing nothing to smooth.

## Why
The clean gain comes from a 2023-25 pattern where a quiet 4 weeks was followed by a good week; it reverses in H2 (size was cut as a volatile-but-profitable regime started) and does not survive window or band perturbation (the wider band at the same K is -0.065 on clean). Good news in H1 does not rescue the gate: H2 fails, plateau fails, and the effect vanishes on whole-lot rounding.
Files: code/census/night_ins/ap_b17_core.py, ap_b17_run.py, ap_b17_rep.py; outputs/autopilot/b17/{b17_all.pkl,b17_summary.json,run.log}.

DONE B17
