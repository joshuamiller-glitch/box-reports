# REPORT PX22 - CL SHOCK PAUSE/HALF (BACKLOG2 #66; D07 x M4/M7, H2-H3)
**Verdict: NO. FOUND 0. Selected W60_SKIP: weekly Sharpe uplift +0.49 clean / -1.08 H1 / -2.33 H2 (needed +0.10 each); all-in -0.42; bootstrap 90% CI of all-in uplift [-1.11, +0.28]; plateau 0.00 of 4; null rank clean 0.95 (p95 +0.48).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PX20-PX27' (plus PX AMENDMENT 1 for the PX21/PX22 threshold) before the first run.

## Set-up and fill model
- as PX20 on CL with threshold 3.0 (amendment 1: at 2.0, 54-66% of entries flagged); 4 cells.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): W30_HALF +0.039, W30_SKIP -0.020, W60_HALF +0.061, W60_SKIP +0.492. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.95 | +0.49 | +0.60 | +0.65 |
| H1 | 2.83 | 1.74 | -1.08 | +0.33 | -1.05 |
| H2 | 2.30 | -0.04 | -2.33 | -2.17 | -2.30 |
| all | 1.86 | 1.44 | -0.42 | -0.10 | -0.31 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.95/+0.48, H1 0.38/+0.16, H2 0.00/+0.62, all 0.25/+0.24
- plateau neighbours (all-in uplift): {'thr x0.75': -0.56, 'thr x1.25': -0.45, 'W x0.75': -0.49, 'W x1.25': -0.31}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.73; no hedge claim)
- affected share/range: min 0.00 max 1.00 mean 0.621
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = W60_HALF (uplift -0.26); read on held-out months -0.25. Carried clean cell W60_SKIP: selection-months -0.67, held-out -0.21.
- even->odd: cell selected on the selection months = W30_SKIP (uplift -0.06); read on held-out months -0.75. Carried clean cell W60_SKIP: selection-months -0.21, held-out -0.67.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.95 | 3.46 | 6.30 | -78.8k | -76.6k | 229k | -81.9k | 38.1 |
| H1 cand | 1.74 | 2.97 | 2.28 | -78.3k | -77.9k | 157k | -78.3k | 32.1 |
| H2 cand | -0.04 | -0.05 | -0.04 | -80.4k | -79.7k | 293k | -80.9k | 58.3 |
| all cand | 1.44 | 2.41 | 5.43 | -79.4k | -78.6k | 330k | -81.9k | 41.7 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 8.5, -0.1, 0.0, 18.3); H1 (False, -40.0, -0.9, -0.0, -3.2); H2 (False, -101.4, 0.9, 2.0, -34.5); all (False, -33.4, -0.3, 0.8, -17.7)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pc_run.py (copy ap_pxw_run.py), ap_g10_rep.py, ap_h7_alt.py, ap_pxw_doc.py; outputs/autopilot/px22/.

DONE PX22
