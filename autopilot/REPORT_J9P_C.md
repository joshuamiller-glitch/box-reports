# REPORT J9P-C - RUN-UP-INTO-ENTRY (CHASE) SIZE TILT (D11 x M4/M8, H2)
**Verdict: NO. FOUND 0. Selected L30_CHASE_DOWN: weekly Sharpe uplift +0.25 clean / -0.09 H1 / -0.38 H2 (needed +0.10 each); all-in +0.09; bootstrap 90% CI of all-in uplift [-0.41, +0.57]; plateau 0.50 of 6; null rank clean 0.97 (p95 +0.19).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'J7V + J9P' before the first run.

## Set-up and fill model
- u_k = side x (c[EI-1]-c[EI-1-k])/(sigma_1m sqrt k) on 1-minute closes, k {10,30,60}; terciles frozen from clean; CHASE_DOWN (top x0.5), PULL_UP (bottom x1.5), TWO (0.75/1.25); 9 cells.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): L10_CHASE_DOWN -0.177, L10_PULL_UP -0.743, L10_TWO_C -0.310, L30_CHASE_DOWN +0.246, L30_PULL_UP -0.348, L30_TWO_C +0.110, L60_CHASE_DOWN -0.111, L60_PULL_UP -0.318, L60_TWO_C +0.026. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.71 | +0.25 | +0.50 | +0.36 |
| H1 | 2.83 | 2.74 | -0.09 | +0.96 | -0.23 |
| H2 | 2.30 | 1.91 | -0.38 | -0.51 | -0.31 |
| all | 1.86 | 1.94 | +0.09 | +0.36 | +0.14 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.97/+0.19, H1 0.26/+0.96, H2 0.46/+0.35, all 0.83/+0.15
- plateau neighbours (all-in uplift): {'share25': 0.08, 'share42': 0.07, 'm x0.75': -0.01, 'm x1.25': -0.0, 'L x0.75': -0.16, 'L x1.25': 0.12}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.87; no hedge claim)
- affected share/range: min 0.50 max 1.00 mean 0.845
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = L30_CHASE_DOWN (uplift +0.02); read on held-out months -0.03. Carried clean cell L30_CHASE_DOWN: selection-months +0.02, held-out -0.03.
- even->odd: cell selected on the selection months = L30_CHASE_DOWN (uplift -0.03); read on held-out months +0.02. Carried clean cell L30_CHASE_DOWN: selection-months -0.03, held-out +0.02.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.71 | 3.11 | 6.65 | -80.7k | -79.2k | 218k | -84.7k | 41.0 |
| H1 cand | 2.74 | 5.66 | 5.11 | -78.0k | -77.7k | 131k | -78.2k | 28.6 |
| H2 cand | 1.91 | 4.21 | 2.46 | -80.2k | -71.4k | 257k | -82.1k | 52.8 |
| all cand | 1.94 | 3.75 | 10.70 | -80.3k | -78.9k | 257k | -84.7k | 41.7 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (True, 9.1, -2.5, -3.4, 22.1); H1 (False, 12.6, -0.5, 0.1, 13.8); H2 (False, -17.0, 1.1, 0.5, -18.2); all (False, 2.4, -1.4, -2.6, 8.3)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_j79_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_j79_doc.py; outputs/autopilot/j9p_c/.

DONE J9P-C
