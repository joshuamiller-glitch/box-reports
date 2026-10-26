# REPORT PX26 - OVERNIGHT GAP / ADR RTH REGIME TILT (BACKLOG2 #74; D06/D08 x M4/M8, H4)
**Verdict: NO. FOUND 0. Selected ALIGN_COUNTER_DOWN: weekly Sharpe uplift +0.17 clean / +0.13 H1 / +0.08 H2 (needed +0.10 each); all-in +0.16; bootstrap 90% CI of all-in uplift [-0.03, +0.38]; plateau 1.00 of 4; null rank clean 0.78 (p95 +0.26).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PX20-PX27' (plus PX AMENDMENT 1 for the PX21/PX22 threshold) before the first run.

## Set-up and fill model
- gap = ln(09:30 bar close / previous 15:59 close) (roll days missing), ABS = |gap|/(ADR20/price), ALIGN = side x gap/(ADR20/price); RTH entries only; ABS x {HIGH_DOWN, HIGH_UP, TWO_V}, ALIGN x {COUNTER_DOWN, ALIGN_UP, TWO}; 6 cells.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): ABS_HIGH_DOWN -0.012, ABS_HIGH_UP -0.020, ABS_TWO_V -0.134, ALIGN_COUNTER_DOWN +0.166, ALIGN_ALIGN_UP -0.073, ALIGN_TWO +0.146. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.63 | +0.17 | +0.24 | +0.18 |
| H1 | 2.83 | 2.96 | +0.13 | +0.26 | +0.06 |
| H2 | 2.30 | 2.38 | +0.08 | +0.04 | -0.23 |
| all | 1.86 | 2.02 | +0.16 | +0.20 | +0.09 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: PASS
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.78/+0.26, H1 0.57/+0.40, H2 0.95/+0.06, all 0.92/+0.17
- plateau neighbours (all-in uplift): {'share25': 0.14, 'share42': 0.19, 'm x0.75': 0.16, 'm x1.25': 0.19}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.98; no hedge claim)
- affected share/range: min 0.50 max 1.00 mean 0.929
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = ALIGN_TWO (uplift +0.29); read on held-out months +0.07. Carried clean cell ALIGN_COUNTER_DOWN: selection-months +0.27, held-out -0.03.
- even->odd: cell selected on the selection months = ALIGN_TWO (uplift +0.07); read on held-out months +0.29. Carried clean cell ALIGN_COUNTER_DOWN: selection-months -0.03, held-out +0.27.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.63 | 3.15 | 5.30 | -78.8k | -78.1k | 279k | -81.9k | 41.0 |
| H1 cand | 2.96 | 7.31 | 4.71 | -77.8k | -64.8k | 146k | -78.3k | 39.3 |
| H2 cand | 2.38 | 4.94 | 3.66 | -81.1k | -79.3k | 220k | -82.5k | 41.7 |
| all cand | 2.02 | 4.08 | 10.65 | -79.3k | -78.3k | 279k | -82.5k | 41.1 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 11.3, -0.1, 0.0, 0.3); H1 (False, 15.9, -0.3, 0.0, 3.6); H2 (False, 5.8, 0.0, 0.0, -1.2); all (False, 10.8, -0.1, 0.0, 0.3)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pc_run.py (copy ap_pxw_run.py), ap_g10_rep.py, ap_h7_alt.py, ap_pxw_doc.py; outputs/autopilot/px26/.

DONE PX26
