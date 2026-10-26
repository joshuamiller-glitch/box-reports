# REPORT G6c
**Verdict: NO** (2/6 measured gates pass). Selected cell fri_1500: weekly Sharpe uplift clean/H1/H2/all-in +0.10 / +0.02 / +0.01 / +0.07 (needed +0.10 on each of clean, H1, H2). Family: time-flatten of the pair before RTH close / settlement (M5/M7, H3-H4).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model 1 tick/side + $34.88 per 8-lot round trip (2x = 2 ticks/side for the slippage test), ET clock, 1-min harness for locks.
- Rule: Any pair position still open at cutoff T (first occurrence after entry) is closed at the open of the cutoff 1-min bar, 1 tick/side + commission as modelled; rows re-fed through the lock/rules engine (exit label, week, lock timing recomputed). Grid 5 cells: all days T in {15:00,15:30,15:45}; Fridays only T in {15:00,15:45}. Applied rows patched (XI, PTS0, TOUT, labels) then B.run.
- Null: same number of truncated trades, truncation at a uniformly random minute inside each trade life, 100 draws. Bootstrap 3000 weekly draws.
- Selection on clean only (max clean uplift over 5 cells); H1/H2 read once for the carried cell. Cells (clean uplift): all_1500 -0.09; all_1530 -0.05; all_1545 -0.01; fri_1500 +0.10; fri_1545 +0.03.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.56 | +0.10 | +0.09 | +0.11 |
| H1 | 2.83 | 2.84 | +0.02 | +0.01 | -0.03 |
| H2 | 2.30 | 2.31 | +0.01 | +0.01 | +0.01 |
| all-in | 1.86 | 1.92 | +0.07 | +0.06 | +0.06 |

Whole-lot rounding (round(8m)/8) uplift: +0.00 / +0.00 / +0.00 (all-in +0.00).

## Gate checklist
- 3. uplift >= +0.10 on clean, H1, H2: FAIL. +0.10 / +0.02 / +0.01
- 3b. worst week not worse (per span): PASS. -81.9k vs -81.9k / -78.3k vs -78.3k / -82.5k vs -82.5k
- 4a. own null p95 (all-in uplift; rank): FAIL. real +0.07 vs p95 +0.08 (rank 0.61); clean +0.10 vs +0.12 (rank 0.68)
- 4b. bootstrap 90% CI all-in > 0: PASS. [+0.01, +0.13]; clean [+0.03, +0.18]
- 5a. plateau >= 75% of neighbours keep >= 75% of uplift: FAIL. 1 of 2; T-30 +0.07, T+30 +0.03
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.11 / -0.03 / +0.01
- 6. worst-decile corr (overlay; weekly corr with the pair): PASS. n/a for an overlay (weekly corr 1.00); no hedge claim
- 7. NT8 spec: yes. see Executability
- R. replication H0 2023-02..07 (uplift): FAIL. -0.03 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating-month split (carried cell odd/even; protocol): PASS. carried cell uplift odd +0.08 / even +0.06; select-odd fri_1500 +0.08 -> even +0.06; select-even fri_1500 +0.06 -> odd +0.08
- 1/2. Pre-registered in PREREG_AUTOPILOT.md before the first run; clean-only selection, H1/H2 read once: PASS (process).

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.56 | 2.99 | 5.04 | -78,736 | -78,009 | 280,110 | -81,874 | 41.9 |
| H1 cand | 2.84 | 6.14 | 3.92 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 cand | 2.31 | 4.69 | 3.49 | -81,089 | -79,185 | 217,425 | -82,524 | 41.7 |
| all cand | 1.92 | 3.78 | 9.87 | -79,220 | -78,243 | 280,110 | -82,524 | 41.7 |

INSURANCE flags (rep_common/ins_metrics, per span: flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, 6.087406983579148, 0.0, 0.0, 0.0]; H1: [False, 0.16840759704184619, 0.0, 0.0, 0.0]; H2: [False, -0.1786524977720979, 0.0, 0.0, 0.0]; all: [False, 3.001850391232721, 0.0, 0.0, 0.0]

## Replication and era
- H0 window (2023-02-10..07-31, pair only; the pair rows start 2023-02): uplift -0.03.
- Alternating-month split (2023-08..2026-10 weeks by month parity): protocol result in checklist. ES/RTY replication: not available (pair engine is NQ-only).
- ERA FLAG: n/a pre-2023 (the pair has no history before 2023-02; this overlay cannot be scaled back). Mechanism depends on the current clock-structure of NQ flow; no pre-2023 evidence.

## Executability
NT8: a time-based market-flatten order at T per strategy (ExitOnSession-style); trivially codable, no margin change. NinjaTrader Brokerage via Rithmic, NQ; no data beyond the strategy's own clock. Not recommended unless FOUND.

Cells closed: see GAPMAP_UPDATES.md (G6 worker).

DONE G6c