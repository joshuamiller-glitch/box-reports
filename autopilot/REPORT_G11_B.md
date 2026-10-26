# REPORT G11-B - prior-day range-state size tilt (NR7 / inside day / low range-to-ADR) and day-cap risk rule
**Verdict: NO. FOUND 0, LEAD 0. Clean-selected cell M8 NR7 x0.5 (HALVE size on days after an NR7 day, the opposite of the compression->expansion mechanism): weekly Sharpe uplift +0.19 clean / +0.01 H1 / +0.27 H2 (needed +0.10 on each); worst week 7% worse on clean; bootstrap 90% CI of the all-in uplift [-0.25, +0.67]; plateau 0 of 2; 2x slippage H1 -0.22, H2 -0.16.** 15 cells (12 size tilts, 3 day-cap rules), stage 1 2 min, stage 2 about 4 min, pool of 5. Pre-registered (PREREG_AUTOPILOT.md, G11-B) before the states were joined to pair rows.

## Set-up and fill model
- Engine and fill model as G11-A (live pair, clean process, sizefn per entry, fixed-dollar locks, 1 tick/side + $34.88 per 8 lots, 2x = SLIP_PT 1.0). States from the PREVIOUS label day's RTH bars (known at 16:00): NR7 (13.4% of entries), inside day (11.5%), LOW = range/ADR20 below the clean 33rd percentile. Truncation causality test: 0 mismatches (`g11/causality.txt`). M8 cells: multiplier a in {0.5, 0.75, 1.25, 1.5} on state days, renormalised to mean 1 over clean entries (risk-neutral); M7 cells: combined day cap 8R -> 4R on state days.
- Clean uplifts (exact): NR7 x0.5 +0.192 (carried), M7 NR7 +0.103, LOW x0.75 +0.049, NR7 x0.75 +0.014, M7 LOW -0.014, ID x0.75 -0.037, M7 ID -0.061, ID x0.5 -0.062, LOW x0.5 -0.101, LOW x1.25 -0.23, LOW x1.5 -0.36, ID x1.25 -0.40, NR7 x1.5 -0.43, NR7 x1.25 -0.45, ID x1.5 -0.48. The pre-registered direction (bigger size after compression) loses in every cell (-0.23 to -0.48); the best cells all cut size on compressed days.

## Result for the carried cell (weekly Sharpe)
| span | pair | NR7 x0.5 | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.65 | +0.192 | +0.310 | +0.299 |
| H1 | 2.83 | 2.84 | +0.014 | +1.516 | -0.222 |
| H2 | 2.30 | 2.56 | +0.269 | +0.136 | -0.158 |
| all-in | 1.86 | 2.06 | +0.209 | +0.464 | +0.138 |
Whole-lot rounding (NR7 days 4 lots, others 9 lots): +0.159 / -0.310 / -0.041 / all-in +0.068. H0 (2023-02-10..07-31) uplift +0.158.

## Gate checklist
1. Pre-registered: PASS. 2. Clean-only selection, H1/H2 once: PASS.
3. Uplift >= +0.10 each span: FAIL (H1 +0.014).
4. Worst week not worse: FAIL on clean (-87.8k vs -81.9k, 7.3% worse) and H1 (-79.4k vs -78.3k); H2 passes (-80.0k vs -82.5k).
5. Own timing-destroyed null (state labels permuted among days within year x month, 12 size cells x 200 replicates with the clean-only rule, linear screen; the 3 M7 cells are outside the linear null, stated): statistic mean(H1,H2) uplift real +0.26 (linear) vs p95 +0.22 (rank 0.97): nominally PASS, but the linear screen disagrees with the exact run on H1 (+0.67 linear vs +0.01 exact), so the pass is not credited. Clean-level: 8.5% of null replicates reach the real clean uplift.
6. Bootstrap 90% CI of the all-in uplift: [-0.25, +0.67]: FAIL.
7. Plateau (a-1 scaled x0.75 / x1.25): all-in +0.073 / +0.031 vs +0.209: 0 of 2 keep 75%: FAIL.
8. 2x slippage >= +0.10 each span: FAIL (clean +0.30, H1 -0.22, H2 -0.16).
9. Replication (need 2 of): H0 +0.158 (same sign, 76% of the all-in uplift): holds; alternating months: selected on odd months M7-NR7 +0.167 -> even +0.079 (47%: not >= 50%); selected on even months LOW x0.75 +0.53 -> odd -0.58: fails; newest weeks none yet: 1 of 2 available, so not replicated.
10. Worst-decile correlation: n/a. ERA FLAG: not testable pre-2023 (no pair rows). Executable: NT8 yes (previous-day RTH range/ADR rank, size by day), whole-lot rounding destroys the clean gain (H1 -0.31).
Overall: NO.

## Insurance metrics (weekly)
| span | pair Sharpe | cand Sharpe | uplift | cand Sortino | cand MAR | cand CVaR5 | cand CVaR10 | cand maxDD | cand worst wk (pair) | %neg wk cand (pair) |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.65 | +0.19 | 3.17 | 5.06 | -81.2k | -79.6k | 300k | -87.8k (-81.9k) | 40.0 (42.9) |
| H1 | 2.83 | 2.84 | +0.01 | 5.64 | 3.31 | -78.9k | -78.6k | 206k | -79.4k (-78.3k) | 35.7 (39.3) |
| H2 | 2.30 | 2.56 | +0.27 | 6.27 | 5.45 | -79.0k | -77.8k | 173k | -80.0k (-82.5k) | 44.4 (44.4) |
| all | 1.86 | 2.06 | +0.21 | 4.20 | 10.49 | -80.5k | -79.2k | 300k | -87.8k (-82.5k) | 40.5 (42.9) |
Constant-risk: the mean multiplier is 1 on clean by construction (net +14% clean, +15% H1, +24% H2, +17% all-in is a sizing-mix effect, partly from the day-lock interaction). Tails: CVaR5 -1.7%, worst week -6.4%, max DD -6.9% all-in (worse): insurance verdict NO.
## Reading
The clean gain is a 3-year pattern in which NR7 days (13% of entries) were poor days for the pair; it is the opposite sign to the mechanism, flips between H1 and H2 on the other cells, and disappears on H1 under 2x slippage and whole lots. Contra-mechanism winner chosen by a selection rule over 15 cells is what the chance-pass probability (about 14% for clean>=0.10 and mean(H1,H2)>=0.10 in the linear null) predicts. Closes D11-H5-M8 and D11-H5-M7 NQ (prior-day range states only). Code ap_g11_{feat,core,run,round}.py; outputs outputs/autopilot/g11/{stage1_B.csv,stage2_B.pkl}.

DONE G11-B
