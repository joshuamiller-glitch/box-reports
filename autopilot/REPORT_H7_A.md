# REPORT H7-A - NQ-vs-ES/RTY RELATIVE-STRENGTH DIVERGENCE as entry size tilt (D07 x M4/M8, H2-H4)
**Verdict: NO. FOUND 0. Selected RTY_L30_A3: weekly Sharpe uplift +0.23 clean / -0.13 H1 / -0.08 H2 (needed +0.10 each); all-in +0.11; bootstrap 90% CI of all-in uplift [-0.30, +0.52]; plateau 0.50 of 4; null rank clean 0.98 (p95 +0.15).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md section H7 before the first run.

## Set-up and fill model
- RS = side x (dlnNQ - dlnREF over L bars) / (sigma_spread x sqrt L), REF in {ES,RTY}, L in {30,60}; actions A1 half on top-30% RS, A2 skip top-30%, A3 1.5x on bottom-30% (edges frozen from clean); 12 cells. Null: RS permuted within (year x book x ET-hour) blocks, same edges (100 draws).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only bars closed before the entry bar (ES/RTY/macro 1-min back-adjusted, forward-filled, stale>5min -> off).
- Selection on clean only (uplift vs baseline per cell, clean): ES_L30_A1 -0.103, ES_L30_A2 -0.312, ES_L30_A3 -0.101, ES_L60_A1 +0.019, ES_L60_A2 -0.341, ES_L60_A3 -0.627, RTY_L30_A1 -0.131, RTY_L30_A2 -0.203, RTY_L30_A3 +0.234, RTY_L60_A1 -0.039, RTY_L60_A2 -0.625, RTY_L60_A3 -0.128. Top cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.69 | +0.23 | +0.41 | +0.23 |
| H1 | 2.83 | 2.70 | -0.13 | -0.00 | -0.18 |
| H2 | 2.30 | 2.22 | -0.08 | -0.19 | -0.22 |
| all | 1.86 | 1.96 | +0.11 | +0.21 | +0.07 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- null p95 clean and all-in: PASS
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.98/+0.15, H1 0.74/+0.60, H2 0.70/+0.31, all 0.97/+0.08
- plateau neighbours (all-in uplift): {'share22.5': -0.06, 'share37.5': 0.32, 'm x0.75': 0.28, 'm x1.25': 0.08}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.90; no hedge claim)
- affected share/range: min 1.00 max 1.50 mean 1.142
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = RTY_L30_A3 (uplift +0.05); read on held-out months +0.07. Carried clean cell RTY_L30_A3: selection-months +0.05, held-out +0.07.
- even->odd: cell selected on the selection months = RTY_L30_A2 (uplift +0.96); read on held-out months -1.05. Carried clean cell RTY_L30_A3: selection-months +0.07, held-out +0.05.
- Cross-instrument: REF dimension (ES vs RTY) is inside the grid (see per-cell clean uplifts above); H0 / pre-2023: not testable (pair rows and harness series start 2023-02/08). ERA FLAG: not testable.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.69 | 3.19 | 5.49 | -82.3k | -80.5k | 301k | -84.8k | 41.0 |
| H1 cand | 2.70 | 5.44 | 3.38 | -77.9k | -71.4k | 170k | -77.9k | 32.1 |
| H2 cand | 2.22 | 4.95 | 3.75 | -78.3k | -77.9k | 229k | -78.3k | 44.4 |
| all cand | 1.96 | 3.87 | 10.25 | -81.1k | -79.6k | 301k | -84.8k | 40.5 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 24.1, -4.5, -3.5, -7.3); H1 (False, -3.4, -0.4, 0.5, -11.9); H2 (False, 12.9, 3.4, 5.1, -5.5); all (False, 14.8, -2.4, -2.7, -7.3)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: ES/RTY (or macro) 1-min feeds in the same workspace drive an entry-size multiplier (A, C) or a market exit on the open position (B) of the existing strategies; margin unchanged (multiplier <= 1.5 raises peak contracts only on flagged entries).

Files: code/census/night_ins/ap_h7_core.py, ap_h7_run.py, ap_h7_alt.py, ap_h7_doc.py (rep = ap_g10_rep.py); outputs/autopilot/h7_a/.


DONE H7-A
