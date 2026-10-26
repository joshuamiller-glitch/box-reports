# REPORT J6a
**Verdict: LEAD** (4/6 measured gates pass). Selected cell b15k1_m0.0: weekly Sharpe uplift clean/H1/H2/all-in +0.18 / +0.38 / +0.14 / +0.20 (needed +0.10 on each of clean, H1, H2). Family: entry-minute 5/15-min bar-phase skip/halve on the pair (M4/M8, H1-H2).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model 1 tick/side + $34.88 per 8-lot round trip (2x = 2 ticks/side for the slippage test), ET clock, 1-min harness for locks.
- Rule: Entry whose ET minute-of-hour is in the first k minutes of a 5-min or 15-min bar gets mm in {0,0.5}; 8 cells; reduce-only, NOT mean-normalised. Applied through B.Cfg.sizefn.
- Null: 100 permutations of the per-trade multiplier vector across trades. Bootstrap 3000 weekly draws.
- Selection on clean only (max clean uplift over 8 cells); H1/H2 read once for the carried cell. Cells (clean uplift): b5k1_m0.0 -0.38; b5k1_m0.5 +0.07; b5k2_m0.0 -0.23; b5k2_m0.5 -0.22; b15k1_m0.0 +0.18; b15k1_m0.5 +0.15; b15k3_m0.0 -0.64; b15k3_m0.5 -0.62.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.64 | +0.18 | +0.13 | +0.16 |
| H1 | 2.83 | 3.21 | +0.38 | +0.60 | +0.42 |
| H2 | 2.30 | 2.44 | +0.14 | +0.08 | +0.19 |
| all-in | 1.86 | 2.05 | +0.20 | +0.19 | +0.20 |

Whole-lot rounding (round(8m)/8) uplift: +0.18 / +0.38 / +0.14 (all-in +0.20).

## Gate checklist
- 3. uplift >= +0.10 on clean, H1, H2: PASS. +0.18 / +0.38 / +0.14
- 3b. worst week not worse (per span): PASS. -79.9k vs -81.9k / -77.5k vs -78.3k / -79.7k vs -82.5k
- 4a. own null p95 (all-in uplift; rank): FAIL. real +0.20 vs p95 +0.29 (rank 0.88); clean +0.18 vs +0.29 (rank 0.87)
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.13, +0.55]; clean [-0.17, +0.57]
- 5a. plateau >= 75% of neighbours keep >= 75% of uplift: PASS. 4 of 4; mm x0.75 +0.15, k x0.75 +0.20, mm x1.25 +0.20, k x1.25 +0.20
- 5b. 2x slippage uplift >= +0.10 each span: PASS. +0.16 / +0.42 / +0.19
- 6. worst-decile corr (overlay; weekly corr with the pair): PASS. n/a for an overlay (weekly corr 0.93); no hedge claim
- 7. NT8 spec: yes. see Executability
- R. replication H0 2023-02..07 (uplift): FAIL. -0.22 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating split (carried cell odd/even; months; protocol): FAIL. carried cell uplift odd +0.17 / even +0.23; select-odd b15k1_m0.5 +0.26 -> even -0.03; select-even b15k1_m0.0 +0.23 -> odd +0.17
- 1/2. Pre-registered in PREREG_AUTOPILOT.md before the first run; clean-only selection, H1/H2 read once: PASS (process).

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.64 | 3.19 | 6.07 | -78,108 | -77,655 | 241,654 | -79,868 | 40.0 |
| H1 cand | 3.21 | 7.29 | 5.28 | -77,288 | -67,699 | 127,640 | -77,491 | 32.1 |
| H2 cand | 2.44 | 5.25 | 3.34 | -79,132 | -76,738 | 234,820 | -79,653 | 41.7 |
| all cand | 2.05 | 4.16 | 12.10 | -78,267 | -77,713 | 241,654 | -79,868 | 39.3 |

INSURANCE flags (rep_common/ins_metrics, per span: flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, 10.280836385658619, 0.7963877040502282, 2.450206366080923, 13.728675502060266]; H1: [False, 13.50213971956495, 0.4147923358251276, 1.017788823125474, 15.867049706603293]; H2: [False, 2.9937534679602242, 2.413349486785826, 3.4790161658697714, -8.000100080358582]; all: [False, 8.927202133610988, 1.2030580699366795, 3.2192144682401778, 13.728675502060266]

## Replication and era
- H0 window (2023-02-10..07-31, pair only; the pair rows start 2023-02): uplift -0.22.
- Alternating split (2023-08..2026-10 weeks by month parity): protocol result in checklist. ES/RTY replication: not available (pair engine is NQ-only).
- ERA FLAG: n/a pre-2023 (the pair has no history before 2023-02; this overlay cannot be scaled back). Mechanism depends on the current clock-structure of NQ flow; no pre-2023 evidence.

## Executability
NT8: entry-time minute test in the strategy; 0 = skip entry, 0.5x = 4 lots. NinjaTrader Brokerage via Rithmic, NQ; no data beyond the strategy's own clock. Not recommended unless FOUND.

Cells closed: see GAPMAP_UPDATES.md (J6 worker).

DONE J6a