# REPORT PA9 - ST/HM BRACKET ASYMMETRY BY MULTI-DAY ALIGNMENT (D11 x M5/M6, H5)
**Verdict: NO. FOUND 0. Selected L60_WITH_ONLY: weekly Sharpe uplift -0.06 clean / -0.26 H1 / -0.21 H2 (needed +0.10 each); all-in -0.09; bootstrap 90% CI of all-in uplift [-0.41, +0.22]; plateau 0.00 of 6; null rank clean 0.97 (p95 -0.12).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PA2 batch' before the first run.

## Set-up and fill model
- a_L = side x (D[t]-D[t-L])/(sigma_D60 sqrt L) on NQ 17:00 ET closes strictly before the entry label day, L {10,30,60}; top tercile (with trend) stop 50/target 70, bottom tercile (against) stop 70/target 50, middle 60/60; schemes BOTH, WITH_ONLY, AGAINST_ONLY; fixed lots; 9 cells. All 13,089 pair rows replayed from the actual fill on 1-second bars (G11-C machinery, stop before target in a second; rows closed externally in the baseline, ~41%, keep their exit). Null: alignment values permuted within (book, year, ET hour) blocks, full account re-run (100 reps). DISCLOSURE: parent J9P-A feature H1/H2 read once (L60_ALIGN_UP +0.45/+0.11/-0.58): non-virgin.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): L10_BOTH -0.682, L10_WITH_ONLY -0.360, L10_AGAINST_ONLY -0.703, L30_BOTH -1.066, L30_WITH_ONLY -0.220, L30_AGAINST_ONLY -1.022, L60_BOTH -0.438, L60_WITH_ONLY -0.056, L60_AGAINST_ONLY -0.382. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.40 | -0.06 | +0.08 | +0.07 |
| H1 | 2.83 | 2.57 | -0.26 | +0.26 | -0.18 |
| H2 | 2.30 | 2.09 | -0.21 | -0.40 | -0.22 |
| all | 1.86 | 1.77 | -0.09 | +0.01 | +0.00 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.97/-0.12, H1 0.24/+0.72, H2 0.38/+0.70, all 0.88/+0.02
- plateau neighbours (all-in uplift): {'share25': -0.08, 'share42': -0.38, 'dist x0.75': -0.05, 'dist x1.25': -0.04, 'L x0.75': -0.09, 'L x1.25': -0.31}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.94; no hedge claim)
- affected share/range: min 0.83 max 1.00 mean 0.947
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = L60_WITH_ONLY (uplift -0.27); read on held-out months +0.11. Carried clean cell L60_WITH_ONLY: selection-months -0.27, held-out +0.11.
- even->odd: cell selected on the selection months = L30_WITH_ONLY (uplift +0.27); read on held-out months -0.56. Carried clean cell L60_WITH_ONLY: selection-months +0.11, held-out -0.27.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.40 | 2.68 | 4.21 | -78.6k | -78.0k | 307k | -80.3k | 44.8 |
| H1 cand | 2.57 | 5.73 | 5.03 | -77.3k | -77.2k | 138k | -77.4k | 39.3 |
| H2 cand | 2.09 | 4.42 | 3.15 | -78.0k | -77.6k | 217k | -78.4k | 44.4 |
| all cand | 1.77 | 3.53 | 8.69 | -78.4k | -77.8k | 307k | -80.3k | 44.0 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -2.8, 0.1, 2.0, -9.7); H1 (False, 16.6, 0.4, 1.1, 9.3); H2 (False, -10.0, 3.8, 5.0, 0.0); all (False, -0.6, 1.1, 2.7, -9.7)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pa2_9run.py, ap_pa2_9core.py, ap_pa2_rep.py, ap_pa2_alt.py, ap_pa2_doc.py; outputs/autopilot/pa9/.

DONE PA9
