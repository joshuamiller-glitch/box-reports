# REPORT PX23 - GOLD + YEN RISK-OFF COMPOSITE SHOCK HALT (BACKLOG2 #69; D07 x M4/M7, H2-H3)
**Verdict: NO. FOUND 0. Selected W30_HALF: weekly Sharpe uplift -0.40 clean / +0.49 H1 / -0.70 H2 (needed +0.10 each); all-in -0.31; bootstrap 90% CI of all-in uplift [-0.80, +0.16]; plateau 0.00 of 4; null rank clean 0.26 (p95 +0.17).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PX20-PX27' (plus PX AMENDMENT 1 for the PX21/PX22 threshold) before the first run.

## Set-up and fill model
- c = (z5_GC + z5_6J)/2 (both up = risk-off), F_W = max c over last W minutes, flagged if F_W > 1.5; W {30,60} x HALF/SKIP, 4 cells.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): W30_HALF -0.405, W30_SKIP -0.922, W60_HALF -0.372, W60_SKIP -0.893. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.06 | -0.40 | -0.11 | -0.19 |
| H1 | 2.83 | 3.32 | +0.49 | +0.67 | +0.70 |
| H2 | 2.30 | 1.59 | -0.70 | -0.01 | -0.85 |
| all | 1.86 | 1.55 | -0.31 | +0.07 | -0.18 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.26/+0.17, H1 0.86/+0.71, H2 0.27/+0.38, all 0.37/+0.09
- plateau neighbours (all-in uplift): {'thr x0.75': -0.42, 'thr x1.25': -0.4, 'W x0.75': -0.53, 'W x1.25': -0.2}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.86; no hedge claim)
- affected share/range: min 0.50 max 1.00 mean 0.820
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = W30_HALF (uplift -0.74); read on held-out months +0.11. Carried clean cell W30_HALF: selection-months -0.74, held-out +0.11.
- even->odd: cell selected on the selection months = W30_SKIP (uplift +0.15); read on held-out months -1.41. Carried clean cell W30_HALF: selection-months +0.11, held-out -0.74.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.06 | 1.78 | 2.60 | -79.5k | -78.7k | 328k | -81.9k | 42.9 |
| H1 cand | 3.32 | 7.00 | 4.52 | -78.2k | -70.5k | 159k | -78.8k | 28.6 |
| H2 cand | 1.59 | 3.06 | 2.81 | -79.0k | -78.2k | 192k | -79.3k | 50.0 |
| all cand | 1.55 | 2.78 | 6.42 | -79.3k | -78.5k | 328k | -81.9k | 42.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -35.9, -0.9, 0.0, -17.2); H1 (False, 20.6, -0.7, -0.6, -4.5); H2 (False, -29.4, 2.6, 3.9, 11.9); all (False, -21.6, -0.1, 0.8, -17.2)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pc_run.py (copy ap_pxw_run.py), ap_g10_rep.py, ap_h7_alt.py, ap_pxw_doc.py; outputs/autopilot/px23/.

DONE PX23
