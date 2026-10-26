# REPORT H6b
**Verdict: NO** (1/6 measured gates pass). Selected cell QEND_m1.5: weekly Sharpe uplift clean/H1/H2/all-in +0.15 / -0.19 / -0.04 / +0.06 (needed +0.10 on each of clean, H1, H2). Family: quarter-phase size tilt on the pair (M4/M8, H6).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model 1 tick/side + $34.88 per 8-lot round trip (2x = 2 ticks/side for the slippage test), ET clock, 1-min harness for locks.
- Rule: Entry label day in MQ1/MQ2/MQ3 (month of calendar quarter) or QEND (last 10 trading days of Mar/Jun/Sep/Dec) gets m in {0.5,1.5}; 8 cells, mean-normalised on clean. A month-of-year effect is not tested (2 observations per month in the clean span) and cannot use alternating months, so the alternating split here is by calendar-quarter parity. Applied through B.Cfg.sizefn.
- Null: 100 permutations of day-level multipliers across days. Bootstrap 3000 weekly draws.
- Selection on clean only (max clean uplift over 8 cells); H1/H2 read once for the carried cell. Cells (clean uplift): MQ1_m0.5 -0.34; MQ1_m1.5 -0.54; MQ2_m0.5 -0.16; MQ2_m1.5 -0.09; MQ3_m0.5 -0.41; MQ3_m1.5 -0.03; QEND_m0.5 -0.14; QEND_m1.5 +0.15.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.61 | +0.15 | +0.11 | +0.33 |
| H1 | 2.83 | 2.63 | -0.19 | +0.32 | -0.06 |
| H2 | 2.30 | 2.25 | -0.04 | +0.04 | -0.33 |
| all-in | 1.86 | 1.91 | +0.06 | +0.14 | +0.13 |

Whole-lot rounding (round(8m)/8) uplift: -0.05 / +0.61 / -0.15 (all-in +0.01).

## Gate checklist
- 3. uplift >= +0.10 on clean, H1, H2: FAIL. +0.15 / -0.19 / -0.04
- 3b. worst week not worse (per span): FAIL. -82.5k vs -81.9k / -78.3k vs -78.3k / -79.1k vs -82.5k
- 4a. own null p95 (all-in uplift; rank): PASS. real +0.06 vs p95 +0.00 (rank 0.98); clean +0.15 vs +0.04 (rank 0.99)
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.41, +0.52]; clean [-0.30, +0.60]
- 5a. plateau >= 75% of neighbours keep >= 75% of uplift: FAIL. 0 of 2; m dev x0.75 -0.03, m dev x1.25 -0.21
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.33 / -0.06 / -0.33
- 6. worst-decile corr (overlay; weekly corr with the pair): PASS. n/a for an overlay (weekly corr 0.88); no hedge claim
- 7. NT8 spec: yes. see Executability
- R. replication H0 2023-02..07 (uplift): PASS. +0.53 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating split (carried cell odd/even; months, or calendar quarters for H6b; protocol): FAIL. carried cell uplift odd +0.45 / even -0.24; select-odd MQ1_m0.5 +0.95 -> even -1.13; select-even MQ2_m0.5 +0.22 -> odd -0.50
- 1/2. Pre-registered in PREREG_AUTOPILOT.md before the first run; clean-only selection, H1/H2 read once: PASS (process).

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.61 | 3.14 | 4.62 | -79,619 | -78,697 | 324,544 | -82,514 | 42.9 |
| H1 cand | 2.63 | 5.11 | 3.44 | -77,722 | -77,468 | 167,145 | -78,338 | 39.3 |
| H2 cand | 2.25 | 4.84 | 3.51 | -78,900 | -78,050 | 220,956 | -79,078 | 41.7 |
| all cand | 1.91 | 3.80 | 8.78 | -79,317 | -78,452 | 324,544 | -82,514 | 42.3 |

INSURANCE flags (rep_common/ins_metrics, per span: flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, 12.792617568879333, -1.121925102188195, -0.7812258529762219, -15.86297662285165]; H1: [False, -3.196179290466067, -0.14431085643421623, -0.06506650700027924, -10.172220263285618]; H2: [False, 1.78860442515109, 2.6992849198775026, 4.176368002575074, -1.6239091266283243]; all: [False, 6.136792696786387, -0.12185087768065972, 0.013256393878397239, -15.86297662285165]

## Replication and era
- H0 window (2023-02-10..07-31, pair only; the pair rows start 2023-02): uplift +0.53.
- Alternating split (2023-08..2026-10 weeks by month parity; calendar-quarter parity for H6b): protocol result in checklist. ES/RTY replication: not available (pair engine is NQ-only).
- ERA FLAG: n/a pre-2023 (the pair has no history before 2023-02; this overlay cannot be scaled back). Mechanism depends on the current clock-structure of NQ flow; no pre-2023 evidence.

## Executability
NT8: calendar lookup at entry; 0.5x = 4 lots, 1.5x = 12 lots. NinjaTrader Brokerage via Rithmic, NQ; no data beyond the strategy's own clock. Not recommended unless FOUND.

Cells closed: see GAPMAP_UPDATES.md (H6 worker).

DONE H6b