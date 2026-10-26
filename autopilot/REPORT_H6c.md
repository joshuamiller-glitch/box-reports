# REPORT H6c
**Verdict: NO** (1/6 measured gates pass). Selected cell HOLADJ_m0.5: weekly Sharpe uplift clean/H1/H2/all-in -0.01 / -0.38 / -0.01 / -0.05 (needed +0.10 on each of clean, H1, H2). Family: holiday-week / post-roll-week risk cut on the pair (M7, H3/H5).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model 1 tick/side + $34.88 per 8-lot round trip (2x = 2 ticks/side for the slippage test), ET clock, 1-min harness for locks.
- Rule: Entry label day in a holiday ISO week (HOLW), the last trading day before / first after a CME equity closure (HOLADJ), or the 5 trading days starting at the quarterly roll Thursday (ROLLW) gets m in {0,0.5}; 6 cells; reduce-only, NOT mean-normalised (pure risk cut). Applied through B.Cfg.sizefn.
- Null: 100 permutations of day-level multipliers across days (same multiset). Bootstrap 3000 weekly draws.
- Selection on clean only (max clean uplift over 6 cells); H1/H2 read once for the carried cell. Cells (clean uplift): HOLW_m0.0 -0.43; HOLW_m0.5 -0.25; HOLADJ_m0.0 -0.13; HOLADJ_m0.5 -0.01; ROLLW_m0.0 -0.14; ROLLW_m0.5 -0.13.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.45 | -0.01 | -0.05 | +0.01 |
| H1 | 2.83 | 2.44 | -0.38 | +0.07 | -0.38 |
| H2 | 2.30 | 2.29 | -0.01 | -0.14 | -0.04 |
| all-in | 1.86 | 1.80 | -0.05 | -0.05 | -0.04 |

Whole-lot rounding (round(8m)/8) uplift: -0.01 / -0.38 / -0.01 (all-in -0.05).

## Gate checklist
- 3. uplift >= +0.10 on clean, H1, H2: FAIL. -0.01 / -0.38 / -0.01
- 3b. worst week not worse (per span): PASS. -81.9k vs -81.9k / -78.3k vs -78.3k / -77.7k vs -82.5k
- 4a. own null p95 (all-in uplift; rank): FAIL. real -0.05 vs p95 +0.14 (rank 0.55); clean -0.01 vs +0.17 (rank 0.61)
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.24, +0.15]; clean [-0.17, +0.17]
- 5a. plateau >= 75% of neighbours keep >= 75% of uplift: FAIL. 0 of 2; m dev x0.75 -0.10, m dev x1.25 -0.16
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. +0.01 / -0.38 / -0.04
- 6. worst-decile corr (overlay; weekly corr with the pair): PASS. n/a for an overlay (weekly corr 0.98); no hedge claim
- 7. NT8 spec: yes. see Executability
- R. replication H0 2023-02..07 (uplift): FAIL. -0.42 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating split (carried cell odd/even; months, or calendar quarters for H6b; protocol): FAIL. carried cell uplift odd -0.15 / even +0.04; select-odd HOLADJ_m0.5 -0.15 -> even +0.04; select-even HOLW_m0.5 +0.07 -> odd -0.19
- 1/2. Pre-registered in PREREG_AUTOPILOT.md before the first run; clean-only selection, H1/H2 read once: PASS (process).

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.45 | 2.69 | 4.88 | -78,736 | -78,009 | 257,958 | -81,874 | 42.9 |
| H1 cand | 2.44 | 5.21 | 2.85 | -77,629 | -66,043 | 181,503 | -78,287 | 42.9 |
| H2 cand | 2.29 | 4.80 | 3.43 | -77,558 | -74,810 | 218,652 | -77,700 | 44.4 |
| all cand | 1.80 | 3.49 | 9.80 | -78,424 | -77,802 | 257,958 | -81,874 | 43.5 |

INSURANCE flags (rep_common/ins_metrics, per span: flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, -5.304308993891177, 0.0, 0.0, 7.908271386188059]; H1: [False, -12.756053646846302, -0.024532946303763233, 0.0, -19.636280800334113]; H2: [False, -1.5108326467472641, 4.35472350366805, 5.846313724121603, -0.5644237873351035]; all: [False, -5.876756030337523, 1.0052188618680018, 0.7883236586282869, 7.908271386188059]

## Replication and era
- H0 window (2023-02-10..07-31, pair only; the pair rows start 2023-02): uplift -0.42.
- Alternating split (2023-08..2026-10 weeks by month parity; calendar-quarter parity for H6b): protocol result in checklist. ES/RTY replication: not available (pair engine is NQ-only).
- ERA FLAG: n/a pre-2023 (the pair has no history before 2023-02; this overlay cannot be scaled back). Mechanism depends on the current clock-structure of NQ flow; no pre-2023 evidence.

## Executability
NT8: calendar lookup at entry (holiday table + roll rule); 0 = skip entry, 0.5x = 4 lots. NinjaTrader Brokerage via Rithmic, NQ; no data beyond the strategy's own clock. Not recommended unless FOUND.

Cells closed: see GAPMAP_UPDATES.md (H6 worker).

DONE H6c