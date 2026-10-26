# REPORT J0B
**Verdict: NO** (1/6 measured gates pass). Selected cell T0925_age120: weekly Sharpe uplift clean/H1/H2/all-in +0.11 / -1.04 / +0.10 / -0.06 (needed +0.10 each of clean, H1, H2). Globex-carry flatten before the Europe / data / RTH open (M5/M6, H4-H5).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill 1 tick/side + $34.88 per 8-lot RT (2x = 2 ticks/side), ET clock, 1-min bars. Patch machinery as G6c (exit rows rewritten, locks/week rules re-run).
- Rule and grid as pre-registered in PREREG_AUTOPILOT.md (J0 batch): close an open trade at the open of the first occurrence of clock T after entry, T in {03:00,08:25,09:25} ET x scope {all, age>=120 min}; null = same trades truncated at a random minute in their life; plateau T+-15.
- Cells (clean uplift; trades fired total / in clean): T0300_age0 -0.67 (1360/762); T0300_age120 -0.60 (915/583); T0825_age0 -0.44 (1222/696); T0825_age120 -0.47 (707/427); T0925_age0 -0.27 (964/574); T0925_age120 +0.11 (492/286)
- Null: 100 draws as pre-registered. Bootstrap 3000 weekly draws. Selection on clean only; H1/H2 read once for the carried cell.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.57 | +0.11 | +0.18 | +0.24 |
| H1 | 2.83 | 1.79 | -1.04 | -0.87 | -0.95 |
| H2 | 2.30 | 2.40 | +0.10 | +0.30 | +0.08 |
| all | 1.86 | 1.80 | -0.06 | +0.02 | +0.04 |

## Gate checklist
- 3. uplift >= +0.10 clean/H1/H2: FAIL. +0.11 / -1.04 / +0.10
- 3b. worst week not worse: PASS. {'clean': (-81874, -81874), 'H1': (-78287, -78287), 'H2': (-82524, -82524), 'all': (-82524, -82524)}
- 4a. own null p95 (all-in uplift): FAIL. real -0.06 vs p95 -0.01 (rank 0.83); clean rank 0.93, H1 0.06, H2 0.65
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.30, +0.19]; clean [-0.22, +0.46]
- 5a. plateau: FAIL. 0 of 2 neighbours keep 75% of all-in uplift; T-15 +0.16/-1.00/+0.10/-0.02, T+15 -0.04/-0.62/+0.00/-0.12 (clean/H1/H2/all)
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.24 / -0.95 / +0.08
- R. H0 2023-02..07 replication: PASS. +0.45 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating-month split (carried cell odd/even > 0): FAIL. odd -0.13 / even +0.02; select-odd T0925_age120 -> even +0.02; select-even T0925_age0 -> odd -0.54
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
| clean cand | 1.57 | 3.05 | 5.86 | -78,214 | -77,738 | 243,238 | -81,874 | 44.8 |
| H1 cand | 1.79 | 3.26 | 2.02 | -77,957 | -77,615 | 187,148 | -78,287 | 39.3 |
| H2 cand | 2.40 | 4.85 | 3.61 | -80,386 | -78,834 | 217,425 | -82,524 | 38.9 |
| all cand | 1.80 | 3.49 | 10.64 | -78,750 | -78,022 | 243,238 | -82,524 | 42.9 |

INSURANCE flags (flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, 7.19, 0.66, 0.0, 13.16]; H1: [False, -36.3, -0.45, 0.0, -23.36]; H2: [False, 3.11, 0.87, 0.0, 0.0]; all: [False, -3.59, 0.59, 0.0, 13.16]

## Replication and era
- H0 window and alternating-month split in checklist. ES/RTY replication not available (pair engine NQ-only). ERA FLAG: n/a pre-2023 (pair rows start 2023-02).
- Disclosure: H1/H2 were read once, for the carried cell only; the other cells' H1/H2 values were not used for selection.

## Executability
NT8: strategy-clock based market exit (bar-open of the exit minute) plus per-trade MFE/close tracking; codable with no data beyond the instrument. NinjaTrader Brokerage via Rithmic, NQ; no margin change (exits only, reduces time in market). Not recommended unless FOUND.

DONE J0B