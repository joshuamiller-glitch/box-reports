# REPORT G6b
**Verdict: NO** (0/6 measured gates pass). Selected cell MON_m0.5: weekly Sharpe uplift clean/H1/H2/all-in +0.15 / -1.68 / -0.39 / -0.23 (needed +0.10 on each of clean, H1, H2). Family: day-of-week / OPEX-week size tilt on the pair (M8/M4/M7, H5-H6).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model 1 tick/side + $34.88 per 8-lot round trip (2x = 2 ticks/side for the slippage test), ET clock, 1-min harness for locks.
- Rule: Targets by entry label day: MON, FRI, OPEXW (week of the 3rd Friday), TRIPLEW (quarterly OPEX week), MEND (last two weekdays of the month); m in {0.5,1.5}; 10 cells, mean-normalised on clean. Applied through B.Cfg.sizefn.
- Null: 100 permutations of day-level multipliers across days. Bootstrap 3000 weekly draws.
- Selection on clean only (max clean uplift over 10 cells); H1/H2 read once for the carried cell. Cells (clean uplift): MON_m0.5 +0.15; MON_m1.5 -0.11; FRI_m0.5 -0.16; FRI_m1.5 -0.24; OPEXW_m0.5 -0.52; OPEXW_m1.5 -0.22; TRIPLEW_m0.5 -0.33; TRIPLEW_m1.5 -0.26; MEND_m0.5 -0.21; MEND_m1.5 -0.23.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.61 | +0.15 | +0.13 | +0.16 |
| H1 | 2.83 | 1.15 | -1.68 | +0.03 | -1.74 |
| H2 | 2.30 | 1.90 | -0.39 | -0.57 | -0.39 |
| all-in | 1.86 | 1.62 | -0.23 | -0.05 | -0.23 |

Whole-lot rounding (round(8m)/8) uplift: +0.08 / -1.84 / -0.30 (all-in -0.29).

## Gate checklist
- 3. uplift >= +0.10 on clean, H1, H2: FAIL. +0.15 / -1.68 / -0.39
- 3b. worst week not worse (per span): FAIL. -81.0k vs -81.9k / -79.0k vs -78.3k / -80.7k vs -82.5k
- 4a. own null p95 (all-in uplift; rank): FAIL. real -0.23 vs p95 +0.00 (rank 0.71); clean +0.15 vs +0.16 (rank 0.94)
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.77, +0.28]; clean [-0.40, +0.80]
- 5a. plateau >= 75% of neighbours keep >= 75% of uplift: FAIL. 0 of 2; m dev x0.75 -0.16, m dev x1.25 -0.42
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.16 / -1.74 / -0.39
- 6. worst-decile corr (overlay; weekly corr with the pair): PASS. n/a for an overlay (weekly corr 0.86); no hedge claim
- 7. NT8 spec: yes. see Executability
- R. replication H0 2023-02..07 (uplift): PASS. +0.75 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating-month split (carried cell odd/even; protocol): FAIL. carried cell uplift odd -0.60 / even +0.13; select-odd MEND_m0.5 -0.00 -> even -0.28; select-even MEND_m1.5 +0.24 -> odd -0.57
- 1/2. Pre-registered in PREREG_AUTOPILOT.md before the first run; clean-only selection, H1/H2 read once: PASS (process).

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.61 | 2.95 | 5.70 | -79,024 | -78,387 | 250,213 | -80,976 | 41.0 |
| H1 cand | 1.15 | 1.85 | 1.03 | -78,422 | -78,141 | 243,350 | -78,995 | 42.9 |
| H2 cand | 1.90 | 4.22 | 2.91 | -79,972 | -79,036 | 250,882 | -80,705 | 50.0 |
| all cand | 1.62 | 3.05 | 9.59 | -79,321 | -78,554 | 250,882 | -80,976 | 43.5 |

INSURANCE flags (rep_common/ins_metrics, per span: flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, 7.169796355182615, -0.36581716721137114, 1.0961675186036792, 10.673298206768676]; H1: [False, -57.812985282518866, -1.0467493594666293, -0.9043141598577399, -60.401670746756544]; H2: [False, -4.185406349186722, 1.3769872802405745, 2.2045237708538474, -15.38771933505886]; all: [False, -10.420751743868104, -0.1273233594577262, 1.8758498293446146, 10.434369780665474]

## Replication and era
- H0 window (2023-02-10..07-31, pair only; the pair rows start 2023-02): uplift +0.75.
- Alternating-month split (2023-08..2026-10 weeks by month parity): protocol result in checklist. ES/RTY replication: not available (pair engine is NQ-only).
- ERA FLAG: n/a pre-2023 (the pair has no history before 2023-02; this overlay cannot be scaled back). Mechanism depends on the current clock-structure of NQ flow; no pre-2023 evidence.

## Executability
NT8: calendar lookup at entry; 0.5x = 4 lots, 1.5x = 12 lots. NinjaTrader Brokerage via Rithmic, NQ; no data beyond the strategy's own clock. Not recommended unless FOUND.

Cells closed: see GAPMAP_UPDATES.md (G6 worker).

DONE G6b