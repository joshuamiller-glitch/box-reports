# REPORT H7-C - DAILY CROSS-ASSET RISK-ON/OFF COMPOSITE (ZN/6J/GC) AND GROWTH PROXY (HG/CL) as size tilt (D07 x M8, H5)
**Verdict: NO. FOUND 0. Selected SAFE_L5_DOWN: weekly Sharpe uplift +0.07 clean / -0.02 H1 / +0.63 H2 (needed +0.10 each); all-in +0.20; bootstrap 90% CI of all-in uplift [-0.19, +0.59]; plateau 0.25 of 4; null rank clean 0.88 (p95 +0.20).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md section H7 before the first run.

## Set-up and fill model
- State from the previous trading date 17:00 ET closes, L-day return z-scored; SAFE=-(ZN+6J+GC)/3, GROW=(HG+CL)/2, NET; terciles frozen from clean; schemes DOWN (low tercile 0.5), UP (top 1.5), TWO (0.75/1.25); 18 cells. Null: state labels permuted among label days (100 draws).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only bars closed before the entry bar (ES/RTY/macro 1-min back-adjusted, forward-filled, stale>5min -> off).
- Selection on clean only (uplift vs baseline per cell, clean): SAFE_L5_DOWN +0.069, SAFE_L5_UP -0.309, SAFE_L5_TWO -0.240, SAFE_L20_DOWN +0.059, SAFE_L20_UP -0.101, SAFE_L20_TWO -0.465, GROW_L5_DOWN +0.016, GROW_L5_UP -0.187, GROW_L5_TWO -0.213, GROW_L20_DOWN -0.094, GROW_L20_UP -0.035, GROW_L20_TWO -0.128, NET_L5_DOWN +0.050, NET_L5_UP -0.265, NET_L5_TWO -0.223, NET_L20_DOWN -0.046, NET_L20_UP -0.299, NET_L20_TWO -0.300. Top cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.53 | +0.07 | +0.45 | +0.07 |
| H1 | 2.83 | 2.81 | -0.02 | +0.32 | -0.02 |
| H2 | 2.30 | 2.92 | +0.63 | +0.12 | +0.67 |
| all | 1.86 | 2.05 | +0.20 | +0.36 | +0.21 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.88/+0.20, H1 0.65/+0.59, H2 0.93/+0.71, all 0.97/+0.12
- plateau neighbours (all-in uplift): {'share25': -0.08, 'share42': 0.39, 'm x0.75': 0.11, 'm x1.25': 0.14}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.92; no hedge claim)
- affected share/range: min 0.50 max 1.00 mean 0.857
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = SAFE_L20_DOWN (uplift +0.14); read on held-out months -0.17. Carried clean cell SAFE_L5_DOWN: selection-months -0.03, held-out +0.36.
- even->odd: cell selected on the selection months = SAFE_L5_DOWN (uplift +0.36); read on held-out months -0.03. Carried clean cell SAFE_L5_DOWN: selection-months +0.36, held-out -0.03.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable. Cross-instrument n/a for a daily macro state on an NQ-only pair.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.53 | 2.75 | 4.42 | -78.2k | -77.6k | 287k | -79.9k | 39.0 |
| H1 cand | 2.81 | 5.46 | 2.95 | -77.6k | -77.4k | 198k | -78.1k | 39.3 |
| H2 cand | 2.92 | 6.47 | 4.29 | -77.3k | -72.9k | 208k | -77.4k | 36.1 |
| all cand | 2.05 | 3.89 | 9.57 | -78.0k | -77.5k | 287k | -79.9k | 38.7 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -4.8, 0.7, 2.5, -2.3); H1 (False, -1.3, 0.0, 0.3, -30.7); H2 (False, 17.1, 4.7, 6.2, 4.5); all (False, 2.2, 1.6, 3.2, -2.3)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: ES/RTY (or macro) 1-min feeds in the same workspace drive an entry-size multiplier (A, C) or a market exit on the open position (B) of the existing strategies; margin unchanged (multiplier <= 1.5 raises peak contracts only on flagged entries).

Files: code/census/night_ins/ap_h7_core.py, ap_h7_run.py, ap_h7_alt.py, ap_h7_doc.py (rep = ap_g10_rep.py); outputs/autopilot/h7_c/.


DONE H7-C
