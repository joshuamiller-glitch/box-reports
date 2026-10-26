# REPORT PA8 - SUNDAY-OPEN WEEKEND-GAP STATE TILT OF THE FIRST HOURS OF THE WEEK (D06/D11 x M4/M8, H2)
**Verdict: NO. FOUND 0. Selected H12_TWO: weekly Sharpe uplift +0.22 clean / -0.24 H1 / -0.65 H2 (needed +0.10 each); all-in -0.03; bootstrap 90% CI of all-in uplift [-0.29, +0.23]; plateau 0.00 of 6; null rank clean 1.00 (p95 +0.15).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PA2 batch' before the first run.

## Set-up and fill model
- g = side x ln(first NQ 1-min close after the Sunday 18:00 ET reopen / last close before it) (contract-roll weekends neutral); entries from Sunday 18:00 ET to +H hours (H 3/6/12) get a multiplier from the tercile of g (edges frozen from clean entries in the window): AGAINST_DOWN (bottom x0.5), WITH_UP (top x1.5), TWO (0.75/1.25); 9 cells; others 1.0. Null: weekly gaps permuted across weekends (100 reps).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): H3_AGAINST_DOWN -0.012, H3_WITH_UP +0.034, H3_TWO +0.125, H6_AGAINST_DOWN +0.023, H6_WITH_UP +0.015, H6_TWO +0.140, H12_AGAINST_DOWN +0.048, H12_WITH_UP +0.026, H12_TWO +0.220. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.68 | +0.22 | +0.22 | +0.33 |
| H1 | 2.83 | 2.59 | -0.24 | +0.14 | -0.20 |
| H2 | 2.30 | 1.65 | -0.65 | -0.56 | -0.60 |
| all | 1.86 | 1.82 | -0.03 | +0.04 | +0.05 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 1.00/+0.15, H1 0.29/+0.50, H2 0.37/+0.20, all 0.78/+0.10
- plateau neighbours (all-in uplift): {'share25': -0.11, 'share42': 0.02, 'm x0.75': -0.01, 'm x1.25': -0.07, 'H x0.75': -0.1, 'H x1.25': -0.02}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.97; no hedge claim)
- affected share/range: min 0.75 max 1.25 mean 0.998
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = H12_WITH_UP (uplift +0.10); read on held-out months -0.21. Carried clean cell H12_TWO: selection-months +0.00, held-out -0.11.
- even->odd: cell selected on the selection months = H12_AGAINST_DOWN (uplift +0.07); read on held-out months -0.24. Carried clean cell H12_TWO: selection-months -0.11, held-out +0.00.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.68 | 3.26 | 5.54 | -77.8k | -77.5k | 275k | -78.8k | 41.0 |
| H1 cand | 2.59 | 5.54 | 3.29 | -77.7k | -77.5k | 184k | -77.8k | 39.3 |
| H2 cand | 1.65 | 3.19 | 2.72 | -80.5k | -79.2k | 218k | -81.4k | 44.4 |
| all cand | 1.82 | 3.57 | 9.90 | -78.6k | -78.0k | 275k | -81.4k | 41.7 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 14.5, 1.2, 3.8, 1.9); H1 (False, 1.8, -0.2, 0.7, -21.0); H2 (False, -22.2, 0.8, 1.4, -0.2); all (False, 1.3, 0.8, 1.4, 1.9)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pa2_run.py, ap_pa2_rep.py, ap_pa2_alt.py, ap_pa2_doc.py; outputs/autopilot/pa8/.

DONE PA8
