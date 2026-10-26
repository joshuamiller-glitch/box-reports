# REPORT B18 - size after the prior-day outcome (Q-4)
**Verdict: NO. FOUND 0, LEAD 0. All 8 cells have negative clean uplift (-0.14 to -0.36); the carried best cell (125% after a capped day and after a loss day) gives -0.14 clean / -0.50 H1 / -0.33 H2, all-in -0.23; plateau 0 of 4, bootstrap CI [-0.65, +0.19].** 8 cells, about 10 min (pool of 5). Pre-registered in PREREG_AUTOPILOT.md (section B18) before the first run.

## Set-up and fill model
- Engine and fill model as B17 (live pair, clean process, sizefn per entry day, fixed-dollar locks, 1 tick/side + $34.88 per 8 lots, 2x = SLIP_PT 1.0). Prior-day state from the baseline run: CAP = combined day lock kind 'cap' (22 clean / 6 H1 / 17 H2 days), LOSS = other days with net < 0 (194 / 49 / 58). Multiplier a after CAP, b after LOSS, else 1; normalised to mean 1 over clean days.
- Grid (a,b) in {0.75,1,1.25}^2 minus (1,1). Clean uplift vs the baseline: (0.75,0.75) -0.360; (0.75,1) -0.244; (0.75,1.25) -0.155; (1,0.75) -0.355; (1,1.25) -0.162; (1.25,0.75) -0.347; (1.25,1) -0.224; (1.25,1.25) -0.144. Best = (1.25,1.25), carried alone, H1/H2 read once. Direction is therefore neither momentum nor reversal: every tilt, including a pure variance injection, costs about 0.15-0.36 Sharpe.
- Mechanism check (clean, baseline daily P&L): mean next-day P&L after CAP +$6.4k, after LOSS +$7.4k, other days -$0.9k (H1 -1.7k / +5.7k / +4.1k; H2 -2.7k / +2.8k / +6.3k). The next-day edge after a loss day is positive in all spans (a mild reversal), after a capped day it flips sign across spans; the 22 / 6 / 17 capped days are too few to read.

## Result for the carried cell (1.25, 1.25) (weekly Sharpe)
| span | pair | B18 | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.32 | -0.144 | +0.159 | +0.043 |
| H1 | 2.83 | 2.32 | -0.505 | +0.527 | -0.382 |
| H2 | 2.30 | 1.96 | -0.335 | -0.243 | -0.469 |
| all-in | 1.86 | 1.63 | -0.226 | +0.136 | -0.123 |
(The positive numbers vs B.Cfg() come from that reference lacking the week floor, not from the tilt; the (1.25,1.25) tilt with the floor is worse than the floor alone.) Whole-lot rounding all-in +0.039 (noise).

## Gate checklist
1. Pre-registered before first run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 on clean / H1 / H2: FAIL (-0.144 / -0.505 / -0.335).
4. Worst week not worse: FAIL (all-in -$88.1k vs -$82.5k).
5. Matched random-size null (100 daily-multiplier permutations): clean real -0.144 vs p95 +0.159 (rank 0.68); all-in -0.226 vs p95 +0.018 (rank 0.55): FAIL. Mean null uplift -0.25: the cell is indistinguishable from random size noise.
6. Bootstrap 90% CI all-in [-0.65, +0.19], clean [-0.58, +0.27]: FAIL.
7. Plateau: a x0.75/x1.25 -> -0.26/-0.14, b x0.75/x1.25 -> -0.24/-0.11: 0 of 4: FAIL.
8. 2x slippage: +0.043 / -0.382 / -0.469: FAIL.
9. Worst-decile correlation: not applicable (weekly corr with pair 0.91).
10. NT8-codable: yes (lot count from the previous day's P&L / cap flag; 7-9 lots), but nothing to implement.
Overall: NO.

## Insurance metrics (candidate vs pair)
| span | Sharpe | Sortino | MAR | CVaR5 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|
| clean pair / B18 | 1.46 / 1.32 | 2.78 / 2.42 | 4.75 / 3.27 | -78.7k / -80.1k | 280k / 374k | -81.9k / -88.1k | 42.9 / 44.8 |
| H1 pair / B18 | 2.83 / 2.32 | 6.09 / 4.58 | 3.91 / 2.91 | -77.6k / -78.4k | 152k / 189k | -78.3k / -78.7k | 39.3 / 35.7 |
| H2 pair / B18 | 2.30 / 1.96 | 4.69 / 3.94 | 3.50 / 2.87 | -81.1k / -78.5k | 217k / 236k | -82.5k / -79.1k | 44.4 / 44.4 |
| all pair / B18 | 1.86 / 1.63 | 3.63 / 3.07 | 9.59 / 6.54 | -79.2k / -79.6k | 280k / 374k | -82.5k / -88.1k | 42.9 / 43.5 |
Mean size neutral (mean multiplier 0.999), net all-in -8.8%, maxDD 33% worse: INSURANCE NO.
Files: code/census/night_ins/ap_b17_core.py, ap_b17_run.py (arg b18), ap_b17_rep.py; outputs/autopilot/b18/{b18_all.pkl,b18_summary.json,run.log}.

DONE B18
