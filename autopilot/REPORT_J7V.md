# REPORT J7V - SMOOTHED DAILY RISK-ON/OFF COMPOSITE (ZN/6J/GC) AS SIZE TILT - variant of H7-C (D07 x M8, H5)
**Verdict: NO. FOUND 0. Selected W10_DOWN: weekly Sharpe uplift +0.16 clean / +0.83 H1 / -0.33 H2 (needed +0.10 each); all-in +0.13; bootstrap 90% CI of all-in uplift [-0.24, +0.49]; plateau 0.17 of 6; null rank clean 0.92 (p95 +0.26).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'J7V + J9P' before the first run.

## Set-up and fill model
- composite z_t = -(r1_ZN+r1_6J+r1_GC)/3, r1 = 1-day change / trailing-60-day sd, W-session rolling mean (W 10/20/40) of 17:00 ET closes strictly before the entry label day; terciles frozen from clean entries; schemes DOWN (bottom tercile x0.5), ASYM (bottom x0.5, top x1.25), UPONLY (top x1.25); 9 cells. Parent H7-C (SAFE_L5_DOWN +0.07/-0.02/+0.63) H1/H2 were read once: non-virgin; the variant needs the Amendment-2 replication to be FOUND.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): W10_DOWN +0.156, W10_ASYM +0.074, W10_UPONLY -0.064, W20_DOWN -0.048, W20_ASYM -0.129, W20_UPONLY -0.072, W40_DOWN -0.041, W40_ASYM +0.082, W40_UPONLY +0.115. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.62 | +0.16 | +0.26 | +0.18 |
| H1 | 2.83 | 3.66 | +0.83 | +0.63 | +0.75 |
| H2 | 2.30 | 1.97 | -0.33 | -0.41 | -0.25 |
| all | 1.86 | 1.98 | +0.13 | +0.18 | +0.15 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.92/+0.26, H1 0.99/+0.54, H2 0.50/+0.44, all 0.96/+0.10
- plateau neighbours (all-in uplift): {'share25': 0.23, 'share42': -0.16, 'm x0.75': 0.09, 'm x1.25': 0.09, 'W x0.75': 0.07, 'W x1.25': 0.08}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.92; no hedge claim)
- affected share/range: min 0.50 max 1.00 mean 0.876
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = W40_ASYM (uplift +0.20); read on held-out months -0.12. Carried clean cell W10_DOWN: selection-months -0.11, held-out +0.35.
- even->odd: cell selected on the selection months = W10_DOWN (uplift +0.35); read on held-out months -0.11. Carried clean cell W10_DOWN: selection-months +0.35, held-out -0.11.

## ES / RTY instrument cross-check (pre-registered, not used for selection; ST+HM books of d1_f4_core, ADR20 k=0.75, equal R, live account rules, 1 tick/side; multiplier = same daily state, same frozen edges, by entry label day; weekly-Sharpe uplift)
| book | cell | clean | H1 | H2 | all-in | base all-in Sharpe |
|---|---|---|---|---|---|---|
| ES | J7V W10_DOWN | -0.10 | -0.29 | -0.23 | -0.16 | -0.75 |
| ES | parent SAFE_L5_DOWN (report-only) | -0.07 | -0.56 | -0.27 | -0.17 | -0.75 |
| RTY | J7V W10_DOWN | +0.13 | +0.31 | -0.03 | +0.12 | -0.41 |
| RTY | parent SAFE_L5_DOWN (report-only) | +0.18 | +0.11 | +0.14 | +0.17 | -0.41 |
- Cross-check criterion (both > 0 and mean >= 50% of NQ all-in +0.13): FAILS. Same macro state and same calendar window as the NQ pair, so ES/RTY are correlated tests of one macro state, not independent draws.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.62 | 3.08 | 6.58 | -78.2k | -77.7k | 208k | -79.9k | 43.8 |
| H1 cand | 3.66 | 8.15 | 4.11 | -68.0k | -59.6k | 169k | -76.9k | 25.0 |
| H2 cand | 1.97 | 3.78 | 3.01 | -81.1k | -79.3k | 230k | -82.5k | 44.4 |
| all cand | 1.98 | 3.83 | 11.98 | -78.8k | -78.0k | 230k | -82.5k | 41.1 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (True, 3.0, 0.7, 2.5, 25.7); H1 (False, 16.8, 12.4, 1.7, -11.3); H2 (False, -8.8, 0.0, 0.0, -5.9); all (False, 2.7, 0.5, 0.0, 17.8)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_j79_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_j79_doc.py, ap_j7v_xi.py; outputs/autopilot/j7v/.

DONE J7V
