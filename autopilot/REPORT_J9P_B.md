# REPORT J9P-B - UNSCHEDULED 1-MIN JUMP SHOCK SKIP/HALF (D07/D10 x M7, H1-H2)
**Verdict: NO. FOUND 0. Selected k16_W60_HALF: weekly Sharpe uplift +0.07 clean / +0.59 H1 / -0.90 H2 (needed +0.10 each); all-in -0.09; bootstrap 90% CI of all-in uplift [-0.42, +0.20]; plateau 0.00 of 4; null rank clean 0.98 (p95 +0.05).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'J7V + J9P' before the first run.

## Set-up and fill model
- jump bar = |1-min log return| / mean |r| at the same ET minute of the prior 20 sessions >= k (post-gap bars excluded); entry flagged if a jump bar occurred in the W minutes before the signal bar; SKIP (0) or HALF (0.5); k {8,12,16} x W {15,30,60} x action; 18 cells; cells with < 3% of clean entries flagged ineligible.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): k8_W15_SKIP -0.222, k8_W15_HALF -0.021, k8_W30_SKIP -0.084, k8_W30_HALF +0.029, k8_W60_SKIP -0.462, k8_W60_HALF -0.028, k12_W15_SKIP -0.062, k12_W15_HALF -0.052, k12_W30_SKIP -0.171, k12_W30_HALF +0.056, k12_W60_SKIP -0.544, k12_W60_HALF -0.028, k16_W15_SKIP -0.056, k16_W15_HALF -0.034, k16_W30_SKIP -0.320, k16_W30_HALF -0.051, k16_W60_SKIP -0.437, k16_W60_HALF +0.065. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.53 | +0.07 | +0.13 | +0.05 |
| H1 | 2.83 | 3.42 | +0.59 | +0.46 | +0.52 |
| H2 | 2.30 | 1.40 | -0.90 | -0.51 | -1.09 |
| all | 1.86 | 1.76 | -0.09 | +0.05 | -0.15 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.98/+0.05, H1 0.95/+0.56, H2 0.00/+0.39, all 0.12/+0.12
- plateau neighbours (all-in uplift): {'k x0.75': -0.06, 'k x1.25': -0.1, 'W x0.75': -0.02, 'W x1.25': -0.08}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.94; no hedge claim)
- affected share/range: min 0.50 max 1.00 mean 0.985
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = k12_W15_SKIP (uplift +0.08); read on held-out months +0.11. Carried clean cell k16_W60_HALF: selection-months -0.32, held-out +0.16.
- even->odd: cell selected on the selection months = k12_W30_HALF (uplift +0.31); read on held-out months -0.36. Carried clean cell k16_W60_HALF: selection-months +0.16, held-out -0.32.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.53 | 2.91 | 5.02 | -78.7k | -78.0k | 274k | -81.9k | 41.9 |
| H1 cand | 3.42 | 7.56 | 4.82 | -77.6k | -66.0k | 147k | -78.3k | 32.1 |
| H2 cand | 1.40 | 2.52 | 2.05 | -81.1k | -79.4k | 245k | -82.5k | 47.2 |
| all cand | 1.76 | 3.35 | 9.43 | -79.3k | -78.3k | 274k | -82.5k | 41.7 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 3.3, 0.0, 0.0, 2.2); H1 (False, 19.0, 0.0, 0.0, 3.3); H2 (False, -34.0, 0.0, 0.0, -12.8); all (False, -3.8, -0.1, 0.0, 2.2)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_j79_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_j79_doc.py; outputs/autopilot/j9p_b/.

DONE J9P-B
