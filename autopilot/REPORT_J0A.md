# REPORT J0A
**Verdict: NO** (1/6 measured gates pass). Selected cell N120_X10: weekly Sharpe uplift clean/H1/H2/all-in +0.37 / -0.63 / -0.04 / +0.14 (needed +0.10 each of clean, H1, H2). Progress-conditional stagnation stop (M5, H4).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill 1 tick/side + $34.88 per 8-lot RT (2x = 2 ticks/side), ET clock, 1-min bars. Patch machinery as G6c (exit rows rewritten, locks/week rules re-run).
- Rule and grid as pre-registered in PREREG_AUTOPILOT.md (J0 batch): at age N min exit at the open of bar ei+N if MFE since entry < X pts; N {60,120,240} x X {10,20,30}; null = same number of random trades alive at age N exited at age N; plateau N,X x0.75/x1.25.
- Cells (clean uplift; trades fired total / in clean): N60_X10 -0.40 (1440/877); N60_X20 -0.63 (2751/1570); N60_X30 -1.28 (3865/2126); N120_X10 +0.37 (674/441); N120_X20 -0.12 (1383/854); N120_X30 -0.32 (2089/1254); N240_X10 +0.03 (281/188); N240_X20 +0.25 (590/384); N240_X30 +0.04 (925/604)
- Null: 100 draws as pre-registered. Bootstrap 3000 weekly draws. Selection on clean only; H1/H2 read once for the carried cell.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.83 | +0.37 | +0.78 | +0.32 |
| H1 | 2.83 | 2.20 | -0.63 | -0.31 | -0.55 |
| H2 | 2.30 | 2.26 | -0.04 | +0.07 | -0.09 |
| all | 1.86 | 2.00 | +0.14 | +0.44 | +0.11 |

## Gate checklist
- 3. uplift >= +0.10 clean/H1/H2: FAIL. +0.37 / -0.63 / -0.04
- 3b. worst week not worse: FAIL. {'clean': (-81874, -81874), 'H1': (-78471, -78287), 'H2': (-82524, -82524), 'all': (-82524, -82524)}
- 4a. own null p95 (all-in uplift): PASS. real +0.14 vs p95 +0.04 (rank 0.99); clean rank 1.00, H1 0.18, H2 0.63
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.23, +0.53]; clean [-0.18, +0.99]
- 5a. plateau: FAIL. 1 of 4 neighbours keep 75% of all-in uplift; N x0.75 -0.01/-0.89/+0.17/-0.09, N x1.25 +0.32/-0.70/-0.14/+0.08, X x0.75 +0.26/-0.42/+0.15/+0.14, X x1.25 +0.19/-0.92/-0.06/-0.02 (clean/H1/H2/all)
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.32 / -0.55 / -0.09
- R. H0 2023-02..07 replication: FAIL. -1.37 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating-month split (carried cell odd/even > 0): PASS. odd +0.17 / even +0.09; select-odd N120_X10 -> even +0.09; select-even N60_X20 -> odd -1.31
- 6. worst-decile corr: n/a for an overlay (weekly corr with pair 0.91); no hedge claim
- 7. NT8 spec: yes, see Executability
- 1/2. Pre-registered before the first run, clean-only selection, H1/H2 read once: PASS (process)

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.83 | 3.27 | 5.62 | -78,514 | -77,872 | 281,243 | -81,874 | 37.1 |
| H1 cand | 2.20 | 4.12 | 2.54 | -77,974 | -77,710 | 182,458 | -78,471 | 35.7 |
| H2 cand | 2.26 | 4.51 | 3.44 | -81,089 | -79,249 | 209,135 | -82,524 | 41.7 |
| all cand | 2.00 | 3.67 | 9.82 | -79,110 | -78,218 | 281,243 | -82,524 | 38.1 |

INSURANCE flags (flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, 18.76, 0.28, 0.0, -0.4]; H1: [False, -22.0, -0.47, -0.23, -20.27]; H2: [False, -5.37, 0.0, 0.0, 3.81]; all: [False, 2.91, 0.14, 0.0, -0.4]

## Replication and era
- H0 window and alternating-month split in checklist. ES/RTY replication not available (pair engine NQ-only). ERA FLAG: n/a pre-2023 (pair rows start 2023-02).
- Disclosure: H1/H2 were read once, for the carried cell only; the other cells' H1/H2 values were not used for selection.

## Executability
NT8: strategy-clock based market exit (bar-open of the exit minute) plus per-trade MFE/close tracking; codable with no data beyond the instrument. NinjaTrader Brokerage via Rithmic, NQ; no margin change (exits only, reduces time in market). Not recommended unless FOUND.

DONE J0A