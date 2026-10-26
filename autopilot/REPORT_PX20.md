# REPORT PX20 - ZN 5-MIN SHOCK PAUSE/HALF (BACKLOG2 #62; D07 x M4/M7, H2-H3)
**Verdict: NO. FOUND 0. Selected W30_SKIP: weekly Sharpe uplift +0.23 clean / -0.91 H1 / -0.28 H2 (needed +0.10 each); all-in -0.04; bootstrap 90% CI of all-in uplift [-0.66, +0.58]; plateau 0.00 of 4; null rank clean 0.89 (p95 +0.38).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PX20-PX27' (plus PX AMENDMENT 1 for the PX21/PX22 threshold) before the first run.

## Set-up and fill model
- z5 = 5-minute ZN log return / (trailing-1300-min 1-min sigma x sqrt5); F_W = max|z5| over the last W minutes, flagged if F_W > 2.0; W {30,60} x HALF/SKIP, 4 cells; touched-share eligibility 3-45% of clean entries.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): W30_HALF -0.133, W30_SKIP +0.227, W60_HALF -0.010, W60_SKIP +0.063. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.69 | +0.23 | +0.36 | +0.42 |
| H1 | 2.83 | 1.92 | -0.91 | +0.02 | -0.80 |
| H2 | 2.30 | 2.01 | -0.28 | -0.49 | -0.25 |
| all | 1.86 | 1.81 | -0.04 | +0.11 | +0.10 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.89/+0.38, H1 0.13/+0.53, H2 0.79/+0.19, all 0.84/+0.07
- plateau neighbours (all-in uplift): {'thr x0.75': -0.37, 'thr x1.25': -0.13, 'W x0.75': -0.25, 'W x1.25': 0.06}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.78; no hedge claim)
- affected share/range: min 0.00 max 1.00 mean 0.692
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = W30_SKIP (uplift +0.14); read on held-out months -0.25. Carried clean cell W30_SKIP: selection-months +0.14, held-out -0.25.
- even->odd: cell selected on the selection months = W60_SKIP (uplift -0.12); read on held-out months -0.25. Carried clean cell W30_SKIP: selection-months -0.25, held-out +0.14.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.69 | 3.10 | 5.17 | -79.1k | -78.3k | 266k | -81.9k | 41.0 |
| H1 cand | 1.92 | 3.62 | 2.66 | -77.7k | -77.5k | 187k | -77.8k | 35.7 |
| H2 cand | 2.01 | 3.83 | 3.06 | -78.4k | -77.8k | 214k | -79.0k | 44.4 |
| all cand | 1.81 | 3.37 | 9.25 | -78.8k | -78.2k | 273k | -81.9k | 41.1 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 3.5, -0.5, 0.0, 4.9); H1 (False, -16.4, -0.2, 0.6, -23.0); H2 (False, -13.9, 3.3, 4.3, 1.5); all (False, -5.8, 0.5, 0.8, 2.4)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pc_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_pc_doc.py; outputs/autopilot/px20/.

DONE PX20
