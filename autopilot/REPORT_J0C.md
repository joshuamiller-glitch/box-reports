# REPORT J0C
**Verdict: NO** (1/6 measured gates pass). Selected cell N120_X30: weekly Sharpe uplift clean/H1/H2/all-in +0.14 / -0.28 / +0.11 / +0.08 (needed +0.10 each of clean, H1, H2). Stuck-underwater time check (M5, H4).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill 1 tick/side + $34.88 per 8-lot RT (2x = 2 ticks/side), ET clock, 1-min bars. Patch machinery as G6c (exit rows rewritten, locks/week rules re-run).
- Rule and grid as pre-registered in PREREG_AUTOPILOT.md (J0 batch): at age N min exit at the open of bar ei+N if the close of bar ei+N-1 is <= entry-X pts (side-signed); N {30,60,120} x X {15,30,40}; null = same number of random trades alive at age N exited at age N; plateau N,X x0.75/x1.25.
- Cells (clean uplift; trades fired total / in clean): N30_X15 -0.15 (2062/1028); N30_X30 -0.34 (868/417); N30_X40 -0.00 (426/214); N60_X15 +0.05 (1602/847); N60_X30 -0.21 (704/358); N60_X40 -0.05 (339/169); N120_X15 +0.09 (960/552); N120_X30 +0.14 (433/251); N120_X40 +0.00 (195/107)
- Null: 100 draws as pre-registered. Bootstrap 3000 weekly draws. Selection on clean only; H1/H2 read once for the carried cell.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.60 | +0.14 | +0.32 | +0.22 |
| H1 | 2.83 | 2.55 | -0.28 | -0.36 | -0.28 |
| H2 | 2.30 | 2.40 | +0.11 | +0.00 | +0.12 |
| all | 1.86 | 1.93 | +0.08 | +0.13 | +0.13 |

## Gate checklist
- 3. uplift >= +0.10 clean/H1/H2: FAIL. +0.14 / -0.28 / +0.11
- 3b. worst week not worse: PASS. {'clean': (-81874, -81874), 'H1': (-77007, -78287), 'H2': (-80430, -82524), 'all': (-81874, -82524)}
- 4a. own null p95 (all-in uplift): FAIL. real +0.08 vs p95 +0.09 (rank 0.93); clean rank 0.94, H1 0.47, H2 0.79
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.12, +0.30]; clean [-0.15, +0.47]
- 5a. plateau: FAIL. 1 of 4 neighbours keep 75% of all-in uplift; N x0.75 +0.02/+0.35/+0.09/+0.07, N x1.25 -0.03/+0.00/-0.08/-0.04, X x0.75 +0.00/-0.60/-0.62/-0.22, X x1.25 -0.17/-0.09/-0.11/-0.16 (clean/H1/H2/all)
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.22 / -0.28 / +0.12
- R. H0 2023-02..07 replication: PASS. +0.69 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating-month split (carried cell odd/even > 0): FAIL. odd -0.00 / even +0.15; select-odd N30_X40 -> even +0.26; select-even N30_X15 -> odd -0.74
- 6. worst-decile corr: n/a for an overlay (weekly corr with pair 0.97); no hedge claim
- 7. NT8 spec: yes, see Executability
- 1/2. Pre-registered before the first run, clean-only selection, H1/H2 read once: PASS (process)

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.60 | 2.85 | 4.91 | -79,214 | -78,332 | 286,053 | -81,874 | 38.1 |
| H1 cand | 2.55 | 5.46 | 3.40 | -76,970 | -64,723 | 157,807 | -77,007 | 39.3 |
| H2 cand | 2.40 | 4.94 | 3.68 | -79,959 | -78,954 | 213,625 | -80,430 | 38.9 |
| all cand | 1.93 | 3.63 | 9.53 | -79,271 | -78,331 | 286,053 | -81,874 | 38.7 |

INSURANCE flags (flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, 5.59, -0.61, 0.0, -2.12]; H1: [False, -9.66, 0.82, 1.64, -4.02]; H2: [False, 3.17, 1.39, 2.54, 1.75]; all: [False, 1.53, -0.06, 0.79, -2.12]

## Replication and era
- H0 window and alternating-month split in checklist. ES/RTY replication not available (pair engine NQ-only). ERA FLAG: n/a pre-2023 (pair rows start 2023-02).
- Disclosure: H1/H2 were read once, for the carried cell only; the other cells' H1/H2 values were not used for selection.

## Executability
NT8: strategy-clock based market exit (bar-open of the exit minute) plus per-trade MFE/close tracking; codable with no data beyond the instrument. NinjaTrader Brokerage via Rithmic, NQ; no margin change (exits only, reduces time in market). Not recommended unless FOUND.

DONE J0C