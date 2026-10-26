# REPORT G6a
**Verdict: NO** (0/6 measured gates pass). Selected cell GLX_A_m1.5: weekly Sharpe uplift clean/H1/H2/all-in +0.12 / -1.54 / -1.42 / -0.49 (needed +0.10 on each of clean, H1, H2). Family: session-phase entry size/filter on the pair (M4/M8, H3-H4).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model 1 tick/side + $34.88 per 8-lot round trip (2x = 2 ticks/side for the slippage test), ET clock, 1-min harness for locks.
- Rule: Phase by entry ET: OPEN 09:30-10:30, LUNCH 11:30-13:30, LATE 14:00-17:00, GLX_A 18:00-02:00, GLX_B 02:00-09:30; entries in the phase get multiplier m (0 = skip), multiplier mean-normalised to 1 over clean trades (risk-neutral; skip cells inflate the rest). Grid 5 phases x m in {0,0.5,1.5} = 15 cells. Applied through B.Cfg.sizefn; every dollar rule (per-book 5R/-2R, day cap, week floor) scales with the size in force.
- Null: 100 permutations of the realised per-trade multipliers across trades (same multiset). Bootstrap 3000 weekly draws.
- Selection on clean only (max clean uplift over 15 cells); H1/H2 read once for the carried cell. Cells (clean uplift): OPEN_m0.0 -0.06; OPEN_m0.5 -0.21; OPEN_m1.5 -0.35; LUNCH_m0.0 +0.08; LUNCH_m0.5 -0.01; LUNCH_m1.5 -0.29; LATE_m0.0 -0.21; LATE_m0.5 -0.01; LATE_m1.5 -0.27; GLX_A_m0.0 -1.98; GLX_A_m0.5 -0.46; GLX_A_m1.5 +0.12; GLX_B_m0.0 -0.54; GLX_B_m0.5 -0.15; GLX_B_m1.5 -0.04.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.58 | +0.12 | +0.27 | +0.27 |
| H1 | 2.83 | 1.29 | -1.54 | -0.04 | -1.45 |
| H2 | 2.30 | 0.88 | -1.42 | -0.60 | -1.67 |
| all-in | 1.86 | 1.37 | -0.49 | +0.02 | -0.45 |

Whole-lot rounding (round(8m)/8) uplift: +0.12 / -1.66 / -1.42 (all-in -0.52).

## Gate checklist
- 3. uplift >= +0.10 on clean, H1, H2: FAIL. +0.12 / -1.54 / -1.42
- 3b. worst week not worse (per span): FAIL. -80.3k vs -81.9k / -80.3k vs -78.3k / -78.7k vs -82.5k
- 4a. own null p95 (all-in uplift; rank): FAIL. real -0.49 vs p95 +0.08 (rank 0.20); clean +0.12 vs +0.19 (rank 0.91)
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-1.08, +0.09]; clean [-0.50, +0.75]
- 5a. plateau >= 75% of neighbours keep >= 75% of uplift: FAIL. 0 of 4; m dev x0.75 -0.40, m dev x1.25 -0.62, width x0.75 -0.32, width x1.25 -0.49
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.27 / -1.45 / -1.67
- 6. worst-decile corr (overlay; weekly corr with the pair): PASS. n/a for an overlay (weekly corr 0.81); no hedge claim
- 7. NT8 spec: yes. see Executability
- R. replication H0 2023-02..07 (uplift): FAIL. -0.10 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating-month split (carried cell odd/even; protocol): FAIL. carried cell uplift odd -0.45 / even -0.53; select-odd LUNCH_m0.0 +0.04 -> even -0.12; select-even GLX_A_m0.5 +0.29 -> odd -0.83
- 1/2. Pre-registered in PREREG_AUTOPILOT.md before the first run; clean-only selection, H1/H2 read once: PASS (process).

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.58 | 3.13 | 3.74 | -78,936 | -78,255 | 418,058 | -80,330 | 41.9 |
| H1 cand | 1.29 | 2.25 | 1.75 | -79,066 | -78,647 | 181,905 | -80,290 | 39.3 |
| H2 cand | 0.88 | 1.67 | 1.51 | -78,589 | -78,200 | 234,015 | -78,737 | 50.0 |
| all cand | 1.37 | 2.62 | 5.34 | -79,035 | -78,390 | 418,058 | -80,330 | 43.5 |

INSURANCE flags (rep_common/ins_metrics, per span: flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, 17.499705732290867, -0.2545725895846997, 1.8863227297046132, -49.2480854666742]; H1: [False, -46.26994612099932, -1.87609675531526, -2.5581235472121415, -19.901220044117252]; H2: [False, -53.71630226138157, 3.0831992066237737, 4.589007477477869, -7.630226773594845]; all: [False, -16.79429550090848, 0.2337514891023648, 2.6597760599765556, -49.2480854666742]

## Replication and era
- H0 window (2023-02-10..07-31, pair only; the pair rows start 2023-02): uplift -0.10.
- Alternating-month split (2023-08..2026-10 weeks by month parity): protocol result in checklist. ES/RTY replication: not available (pair engine is NQ-only).
- ERA FLAG: n/a pre-2023 (the pair has no history before 2023-02; this overlay cannot be scaled back). Mechanism depends on the current clock-structure of NQ flow; no pre-2023 evidence.

## Executability
NT8: size is decided at order time from the entry clock; a 1.5x multiplier means 12 lots, 0 means skip. Margin at 12 lots about 1.5x the 8-lot margin for the tilted phase. NinjaTrader Brokerage via Rithmic, NQ; no data beyond the strategy's own clock. Not recommended unless FOUND.

Cells closed: see GAPMAP_UPDATES.md (G6 worker).

DONE G6a