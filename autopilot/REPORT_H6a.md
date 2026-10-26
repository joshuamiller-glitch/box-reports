# REPORT H6a
**Verdict: NO** (0/6 measured gates pass). Selected cell WOM2_m0.5: weekly Sharpe uplift clean/H1/H2/all-in +0.14 / -1.39 / -0.32 / -0.18 (needed +0.10 on each of clean, H1, H2). Family: week-of-month / turn-of-month size tilt on the pair (M4/M8, H5-H6).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model 1 tick/side + $34.88 per 8-lot round trip (2x = 2 ticks/side for the slippage test), ET clock, 1-min harness for locks.
- Rule: Entry label day in WOM1 (day 1-7), WOM2 (8-14), WOM3 (15-21), WOM4 (22-end) or TOM (last trading day + first 3 trading days of the month) gets multiplier m in {0.5,1.5}; 10 cells, mean-normalised on clean. Applied through B.Cfg.sizefn.
- Null: 100 permutations of day-level multipliers across days. Bootstrap 3000 weekly draws.
- Selection on clean only (max clean uplift over 10 cells); H1/H2 read once for the carried cell. Cells (clean uplift): WOM1_m0.5 -0.40; WOM1_m1.5 -0.29; WOM2_m0.5 +0.14; WOM2_m1.5 -0.41; WOM3_m0.5 -0.48; WOM3_m1.5 -0.03; WOM4_m0.5 -0.45; WOM4_m1.5 -0.25; TOM_m0.5 -0.36; TOM_m1.5 -0.30.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.60 | +0.14 | +0.42 | +0.28 |
| H1 | 2.83 | 1.44 | -1.39 | -0.46 | -1.42 |
| H2 | 2.30 | 1.98 | -0.32 | -0.45 | -0.50 |
| all-in | 1.86 | 1.67 | -0.18 | +0.09 | -0.14 |

Whole-lot rounding (round(8m)/8) uplift: +0.23 / -1.42 / -0.28 (all-in -0.12).

## Gate checklist
- 3. uplift >= +0.10 on clean, H1, H2: FAIL. +0.14 / -1.39 / -0.32
- 3b. worst week not worse (per span): FAIL. -80.2k vs -81.9k / -79.1k vs -78.3k / -81.5k vs -82.5k
- 4a. own null p95 (all-in uplift; rank): FAIL. real -0.18 vs p95 +0.07 (rank 0.67); clean +0.14 vs +0.19 (rank 0.93)
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.71, +0.30]; clean [-0.43, +0.69]
- 5a. plateau >= 75% of neighbours keep >= 75% of uplift: FAIL. 0 of 2; m dev x0.75 -0.18, m dev x1.25 -0.03
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.28 / -1.42 / -0.50
- 6. worst-decile corr (overlay; weekly corr with the pair): PASS. n/a for an overlay (weekly corr 0.86); no hedge claim
- 7. NT8 spec: yes. see Executability
- R. replication H0 2023-02..07 (uplift): FAIL. -0.07 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating split (carried cell odd/even; months, or calendar quarters for H6b; protocol): FAIL. carried cell uplift odd -0.27 / even -0.11; select-odd WOM4_m0.5 +0.08 -> even -0.65; select-even WOM3_m1.5 +0.33 -> odd -0.37
- 1/2. Pre-registered in PREREG_AUTOPILOT.md before the first run; clean-only selection, H1/H2 read once: PASS (process).

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.60 | 3.11 | 4.12 | -78,917 | -78,254 | 379,147 | -80,202 | 42.9 |
| H1 cand | 1.44 | 2.71 | 1.83 | -78,688 | -78,319 | 181,377 | -79,080 | 42.9 |
| H2 cand | 1.98 | 4.31 | 2.52 | -80,479 | -79,584 | 297,609 | -81,489 | 47.2 |
| all cand | 1.67 | 3.31 | 6.97 | -79,456 | -78,657 | 379,147 | -81,489 | 44.0 |

INSURANCE flags (rep_common/ins_metrics, per span: flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, 17.55397124077017, -0.22995414350164173, 2.042313331408658, -35.35641958681102]; H1: [False, -44.24380263966417, -1.388697617270278, -1.0118990176813625, -19.553175972134827]; H2: [False, -1.6761623210004508, 0.7526533765461553, 1.2545889640616923, -36.87881556299748]; all: [False, -1.564904669493006, -0.29698141653412574, 1.2545889640616923, -35.35641958681102]

## Replication and era
- H0 window (2023-02-10..07-31, pair only; the pair rows start 2023-02): uplift -0.07.
- Alternating split (2023-08..2026-10 weeks by month parity; calendar-quarter parity for H6b): protocol result in checklist. ES/RTY replication: not available (pair engine is NQ-only).
- ERA FLAG: n/a pre-2023 (the pair has no history before 2023-02; this overlay cannot be scaled back). Mechanism depends on the current clock-structure of NQ flow; no pre-2023 evidence.

## Executability
NT8: calendar lookup at entry; 0.5x = 4 lots, 1.5x = 12 lots. NinjaTrader Brokerage via Rithmic, NQ; no data beyond the strategy's own clock. Not recommended unless FOUND.

Cells closed: see GAPMAP_UPDATES.md (H6 worker).

DONE H6a