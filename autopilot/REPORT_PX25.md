# REPORT PX25 - FIRST-HOUR RANGE / TREND-DAY TILT (BACKLOG2 #72; D08 x M4/M8, H4)
**Verdict: NO. FOUND 0. Selected RNG_HIGH_UP: weekly Sharpe uplift +0.03 clean / +0.51 H1 / -0.03 H2 (needed +0.10 each); all-in +0.08; bootstrap 90% CI of all-in uplift [-0.04, +0.22]; plateau 0.50 of 4; null rank clean 0.95 (p95 +0.03).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PX20-PX27' (plus PX AMENDMENT 1 for the PX21/PX22 threshold) before the first run.

## Set-up and fill model
- NQ 09:30-10:29 ET: RNG = FH close range / ADR20, EFF = |net|/range; RTH entries 10:30-15:59 only; features {RNG,EFF} x {HIGH_DOWN, HIGH_UP, TWO_V}; 6 cells.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): RNG_HIGH_DOWN -0.057, RNG_HIGH_UP +0.031, RNG_TWO_V -0.286, EFF_HIGH_DOWN -0.175, EFF_HIGH_UP -0.194, EFF_TWO_V -0.260. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.49 | +0.03 | -0.09 | +0.04 |
| H1 | 2.83 | 3.34 | +0.51 | +0.47 | +0.31 |
| H2 | 2.30 | 2.27 | -0.03 | +0.09 | -0.05 |
| all | 1.86 | 1.94 | +0.08 | +0.04 | +0.06 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: PASS
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.95/+0.03, H1 0.97/+0.34, H2 0.39/+0.25, all 0.98/+0.04
- plateau neighbours (all-in uplift): {'share25': 0.05, 'share42': -0.05, 'm x0.75': 0.07, 'm x1.25': 0.08}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.99; no hedge claim)
- affected share/range: min 1.00 max 1.50 mean 1.062
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = RNG_HIGH_UP (uplift +0.12); read on held-out months +0.06. Carried clean cell RNG_HIGH_UP: selection-months +0.12, held-out +0.06.
- even->odd: cell selected on the selection months = RNG_HIGH_UP (uplift +0.06); read on held-out months +0.12. Carried clean cell RNG_HIGH_UP: selection-months +0.06, held-out +0.12.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.49 | 2.85 | 4.95 | -78.9k | -78.2k | 283k | -81.9k | 44.8 |
| H1 cand | 3.34 | 7.70 | 4.71 | -78.6k | -66.4k | 152k | -79.0k | 32.1 |
| H2 cand | 2.27 | 4.83 | 3.72 | -81.1k | -79.3k | 217k | -82.5k | 47.2 |
| all cand | 1.94 | 3.88 | 10.33 | -79.5k | -78.5k | 283k | -82.5k | 43.5 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 5.5, -0.3, 0.0, -1.2); H1 (False, 20.5, -1.3, -0.9, 0.0); H2 (False, 6.3, 0.0, 0.0, 0.0); all (False, 9.0, -0.4, 0.0, -1.2)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pc_run.py (copy ap_pxw_run.py), ap_g10_rep.py, ap_h7_alt.py, ap_pxw_doc.py; outputs/autopilot/px25/.

DONE PX25
