# REPORT PX21 - 6E SHOCK PAUSE/HALF (BACKLOG2 #63, DXY proxy; D07 x M4/M7, H2-H3)
**Verdict: NO. FOUND 0. Selected W60_SKIP: weekly Sharpe uplift +0.11 clean / -1.86 H1 / -0.43 H2 (needed +0.10 each); all-in -0.30; bootstrap 90% CI of all-in uplift [-0.94, +0.35]; plateau 0.00 of 4; null rank clean 0.71 (p95 +0.42).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PX20-PX27' (plus PX AMENDMENT 1 for the PX21/PX22 threshold) before the first run.

## Set-up and fill model
- as PX20 on 6E with threshold 3.0 (amendment 1: at 2.0, 47-60% of entries flagged); 4 cells.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): W30_HALF -0.354, W30_SKIP -0.079, W60_HALF +0.013, W60_SKIP +0.111. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.57 | +0.11 | +0.10 | +0.35 |
| H1 | 2.83 | 0.97 | -1.86 | -0.58 | -1.94 |
| H2 | 2.30 | 1.87 | -0.43 | -0.89 | -0.93 |
| all | 1.86 | 1.56 | -0.30 | -0.24 | -0.29 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.71/+0.42, H1 0.00/+0.64, H2 0.61/+0.40, all 0.43/+0.10
- plateau neighbours (all-in uplift): {'thr x0.75': -0.25, 'thr x1.25': -0.31, 'W x0.75': -0.25, 'W x1.25': -0.24}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.77; no hedge claim)
- affected share/range: min 0.00 max 1.00 mean 0.687
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = W60_HALF (uplift +0.01); read on held-out months -0.67. Carried clean cell W60_SKIP: selection-months -0.13, held-out -0.61.
- even->odd: cell selected on the selection months = W60_SKIP (uplift -0.61); read on held-out months -0.13. Carried clean cell W60_SKIP: selection-months -0.61, held-out -0.13.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.57 | 2.71 | 5.25 | -80.1k | -78.3k | 234k | -85.9k | 38.1 |
| H1 cand | 0.97 | 1.57 | 1.12 | -77.8k | -77.7k | 178k | -78.1k | 35.7 |
| H2 cand | 1.87 | 3.59 | 3.01 | -77.8k | -77.4k | 198k | -78.1k | 44.4 |
| all cand | 1.56 | 2.72 | 8.65 | -79.4k | -78.4k | 234k | -85.9k | 39.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -7.4, -1.8, -4.9, 16.3); H1 (False, -66.3, -0.2, 0.3, -17.4); H2 (False, -21.6, 4.0, 5.4, 9.0); all (False, -24.5, -0.2, -4.1, 16.3)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pc_run.py (copy ap_pxw_run.py), ap_g10_rep.py, ap_h7_alt.py, ap_pxw_doc.py; outputs/autopilot/px21/.

DONE PX21
