# REPORT PX27 - LAST-30-MIN REALISED-VOL STATE TILT (BACKLOG2 #70, 73 folded; D08 x M8, H2)
**Verdict: NO. FOUND 0. Selected W30_HIGH_UP: weekly Sharpe uplift +0.25 clean / -0.56 H1 / -0.23 H2 (needed +0.10 each); all-in +0.03; bootstrap 90% CI of all-in uplift [-0.33, +0.40]; plateau 0.17 of 6; null rank clean 0.97 (p95 +0.17).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PX20-PX27' (plus PX AMENDMENT 1 for the PX21/PX22 threshold) before the first run.

## Set-up and fill model
- q = ln(sqrt(sum r^2 over last 30 bars)/sqrt(30 x mean r^2 over trailing 7,800 bars)); terciles frozen on clean; HIGH_DOWN, HIGH_UP, TWO_V; 3 cells. Bracket variant not run (K18 vol-scaled targets: NO).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): W30_HIGH_DOWN -0.187, W30_HIGH_UP +0.250, W30_TWO_V -0.351. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.71 | +0.25 | +0.03 | +0.45 |
| H1 | 2.83 | 2.27 | -0.56 | -0.00 | -0.67 |
| H2 | 2.30 | 2.07 | -0.23 | +0.13 | -0.43 |
| all | 1.86 | 1.89 | +0.03 | +0.04 | +0.10 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.97/+0.17, H1 0.19/+0.80, H2 0.34/+0.53, all 0.86/+0.12
- plateau neighbours (all-in uplift): {'share25': 0.17, 'share42': -0.1, 'm x0.75': 0.02, 'm x1.25': -0.13, 'L x0.75': -0.06, 'L x1.25': -0.04}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.93; no hedge claim)
- affected share/range: min 1.00 max 1.50 mean 1.152
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = W30_HIGH_DOWN (uplift -0.02); read on held-out months -0.52. Carried clean cell W30_HIGH_UP: selection-months -0.13, held-out +0.17.
- even->odd: cell selected on the selection months = W30_HIGH_UP (uplift +0.17); read on held-out months -0.13. Carried clean cell W30_HIGH_UP: selection-months +0.17, held-out -0.13.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.71 | 3.22 | 5.10 | -82.3k | -80.6k | 332k | -87.2k | 41.9 |
| H1 cand | 2.27 | 4.24 | 3.13 | -81.0k | -80.4k | 170k | -82.2k | 39.3 |
| H2 cand | 2.07 | 4.41 | 3.02 | -79.6k | -78.5k | 259k | -81.6k | 44.4 |
| all cand | 1.89 | 3.63 | 9.06 | -82.0k | -80.3k | 332k | -87.2k | 42.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 27.3, -4.6, -6.5, -18.6); H1 (False, -10.3, -4.4, -5.0, -12.3); H2 (False, 2.8, 1.8, 1.1, -19.1); all (False, 12.0, -3.5, -5.6, -18.6)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pc_run.py (copy ap_pxw_run.py), ap_g10_rep.py, ap_h7_alt.py, ap_pxw_doc.py; outputs/autopilot/px27/.

DONE PX27
