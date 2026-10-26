# REPORT J6c
**Verdict: NO** (1/6 measured gates pass). Selected cell S2_X40: weekly Sharpe uplift clean/H1/H2/all-in -0.13 / +0.66 / -0.60 / -0.12 (needed +0.10 on each of clean, H1, H2). Family: profit-take into :00/:30 or quarter-hour bar-open minute (M5, H1-H2).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model 1 tick/side + $34.88 per 8-lot round trip (2x = 2 ticks/side for the slippage test), ET clock, 1-min harness for locks.
- Rule: Open trade in profit by >= X NQ points at the prior close is closed at the open of the first minute with minute-of-hour in S; 6 cells (S x X); locks re-run on changed exits. Applied by patching exit bar/points (G6c route).
- Null: same number of fired exits moved to a uniformly random bar within the same trade, 100 draws. Bootstrap 3000 weekly draws.
- Selection on clean only (max clean uplift over 6 cells); H1/H2 read once for the carried cell. Cells (clean uplift): S2_X10 -0.97; S2_X20 -0.62; S2_X40 -0.13; S4_X10 -1.61; S4_X20 -0.60; S4_X40 -0.61.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.33 | -0.13 | -0.21 | +0.00 |
| H1 | 2.83 | 3.48 | +0.66 | +1.01 | +0.46 |
| H2 | 2.30 | 1.70 | -0.60 | -0.61 | -0.78 |
| all-in | 1.86 | 1.73 | -0.12 | -0.11 | -0.10 |

Whole-lot rounding (round(8m)/8) uplift: -0.13 / +0.66 / -0.60 (all-in -0.12).

## Gate checklist
- 3. uplift >= +0.10 on clean, H1, H2: FAIL. -0.13 / +0.66 / -0.60
- 3b. worst week not worse (per span): FAIL. -81.9k vs -81.9k / -78.5k vs -78.3k / -79.7k vs -82.5k
- 4a. own null p95 (all-in uplift; rank): PASS. real -0.12 vs p95 -3.20 (rank 1.00); clean -0.13 vs -3.07 (rank 1.00)
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.53, +0.26]; clean [-0.62, +0.33]
- 5a. plateau >= 75% of neighbours keep >= 75% of uplift: FAIL. 0 of 2; X x0.75 -0.63, X x1.25 -0.24
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.00 / +0.46 / -0.78
- 6. worst-decile corr (overlay; weekly corr with the pair): PASS. n/a for an overlay (weekly corr 0.90); no hedge claim
- 7. NT8 spec: yes. see Executability
- R. replication H0 2023-02..07 (uplift): PASS. +0.25 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating split (carried cell odd/even; months; protocol): FAIL. carried cell uplift odd -0.29 / even +0.04; select-odd S2_X40 -0.29 -> even +0.04; select-even S2_X20 +0.25 -> odd -1.72
- 1/2. Pre-registered in PREREG_AUTOPILOT.md before the first run; clean-only selection, H1/H2 read once: PASS (process).

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.33 | 2.37 | 3.29 | -79,394 | -78,541 | 357,259 | -81,874 | 44.8 |
| H1 cand | 3.48 | 8.12 | 5.83 | -78,121 | -64,338 | 127,589 | -78,527 | 32.1 |
| H2 cand | 1.70 | 3.43 | 3.23 | -78,669 | -77,995 | 188,588 | -79,653 | 50.0 |
| all cand | 1.73 | 3.29 | 7.08 | -79,157 | -78,363 | 357,259 | -81,874 | 44.0 |

INSURANCE flags (rep_common/ins_metrics, per span: flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, -11.704134696752115, -0.8358785632371915, 0.0, -27.542574739273547]; H1: [False, 25.316646700261916, -0.6582663659491013, -0.30656289853176816, 15.900797718634427]; H2: [False, -19.904494476485098, 2.9843766648382055, 3.4790161658697714, 13.262855174890447]; all: [False, -5.8418541191882385, 0.08029363503511869, 0.7883236586282869, -27.542574739273547]

## Replication and era
- H0 window (2023-02-10..07-31, pair only; the pair rows start 2023-02): uplift +0.25.
- Alternating split (2023-08..2026-10 weeks by month parity): protocol result in checklist. ES/RTY replication: not available (pair engine is NQ-only).
- ERA FLAG: n/a pre-2023 (the pair has no history before 2023-02; this overlay cannot be scaled back). Mechanism depends on the current clock-structure of NQ flow; no pre-2023 evidence.

## Executability
NT8: strategy exit order at bar open of minutes in S when unrealised P&L >= X points. NinjaTrader Brokerage via Rithmic, NQ; no data beyond the strategy's own clock. Not recommended unless FOUND.

Cells closed: see GAPMAP_UPDATES.md (J6 worker).

DONE J6c