# REPORT J9P-A - OWN-NQ MULTI-DAY RETURN ALIGNMENT AS ENTRY SIZE TILT (D11 x M4/M8, H5)
**Verdict: NO. FOUND 0. Selected L60_ALIGN_UP: weekly Sharpe uplift +0.45 clean / +0.11 H1 / -0.58 H2 (needed +0.10 each); all-in +0.21; bootstrap 90% CI of all-in uplift [-0.25, +0.66]; plateau 0.67 of 6; null rank clean 0.99 (p95 +0.21).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'J7V + J9P' before the first run.

## Set-up and fill model
- a_L = side x (D[t]-D[t-L])/(sigma_D60 sqrt L) on NQ 17:00 ET closes strictly before the entry label day, L in {3,10,30,60}; terciles frozen from clean; COUNTER_DOWN (bottom x0.5), ALIGN_UP (top x1.5), TWO (0.75/1.25); 12 cells.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): L3_COUNTER_DOWN +0.023, L3_ALIGN_UP +0.242, L3_TWO -0.090, L10_COUNTER_DOWN -0.362, L10_ALIGN_UP +0.024, L10_TWO -0.225, L30_COUNTER_DOWN -0.256, L30_ALIGN_UP -0.074, L30_TWO -0.322, L60_COUNTER_DOWN -0.187, L60_ALIGN_UP +0.453, L60_TWO +0.019. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.91 | +0.45 | +0.46 | +0.52 |
| H1 | 2.83 | 2.94 | +0.11 | +0.62 | +0.27 |
| H2 | 2.30 | 1.72 | -0.58 | -0.38 | -0.64 |
| all | 1.86 | 2.06 | +0.21 | +0.31 | +0.26 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: PASS
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.99/+0.21, H1 0.80/+0.63, H2 0.47/+0.22, all 0.97/+0.04
- plateau neighbours (all-in uplift): {'share25': 0.02, 'share42': 0.32, 'm x0.75': 0.24, 'm x1.25': 0.21, 'L x0.75': 0.13, 'L x1.25': 0.19}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.86; no hedge claim)
- affected share/range: min 1.00 max 1.50 mean 1.160
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = L3_COUNTER_DOWN (uplift -0.19); read on held-out months +0.48. Carried clean cell L60_ALIGN_UP: selection-months -0.37, held-out +0.83.
- even->odd: cell selected on the selection months = L60_ALIGN_UP (uplift +0.83); read on held-out months -0.37. Carried clean cell L60_ALIGN_UP: selection-months +0.83, held-out -0.37.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.91 | 3.84 | 6.82 | -78.4k | -77.9k | 277k | -79.8k | 42.9 |
| H1 cand | 2.94 | 7.26 | 6.07 | -77.2k | -77.1k | 138k | -77.3k | 39.3 |
| H2 cand | 1.72 | 3.58 | 2.81 | -79.3k | -78.8k | 217k | -80.0k | 50.0 |
| all cand | 2.06 | 4.30 | 12.05 | -78.7k | -78.0k | 277k | -80.0k | 44.0 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 41.8, 0.4, 2.5, 1.2); H1 (False, 40.6, 0.6, 1.3, 9.3); H2 (False, -19.6, 2.3, 3.0, 0.0); all (False, 24.1, 0.7, 3.0, 1.2)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_j79_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_j79_doc.py; outputs/autopilot/j9p_a/.

DONE J9P-A
