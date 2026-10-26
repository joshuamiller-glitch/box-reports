# REPORT PX24 - BTC OVERNIGHT TREND TILT OF GLOBEX ENTRIES (BACKLOG2 #65; D07 x M4/M8, H3)
**Verdict: NO. FOUND 0. Selected L360_COUNTER_DOWN: weekly Sharpe uplift +0.06 clean / +0.24 H1 / +0.07 H2 (needed +0.10 each); all-in +0.09; bootstrap 90% CI of all-in uplift [-0.02, +0.21]; plateau 0.00 of 6; null rank clean 0.90 (p95 +0.08).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PX20-PX27' (plus PX AMENDMENT 1 for the PX21/PX22 threshold) before the first run.

## Set-up and fill model
- n_L = side x (ln BTC[EI-1]-ln BTC[EI-1-L])/(sigma_BTC1m sqrt L), L {60,180,360} min, Globex entries 18:00-02:59 ET only; terciles frozen on clean; COUNTER_DOWN, ALIGN_UP, TWO; 9 cells (PA4 grid with BTC).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): L60_COUNTER_DOWN -0.235, L60_ALIGN_UP -0.342, L60_TWO -0.262, L180_COUNTER_DOWN -0.314, L180_ALIGN_UP -0.233, L180_TWO -0.271, L360_COUNTER_DOWN +0.056, L360_ALIGN_UP -0.108, L360_TWO -0.015. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.52 | +0.06 | +0.11 | +0.12 |
| H1 | 2.83 | 3.06 | +0.24 | +0.26 | +0.06 |
| H2 | 2.30 | 2.36 | +0.07 | -0.17 | -0.14 |
| all | 1.86 | 1.95 | +0.09 | +0.08 | +0.05 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.90/+0.08, H1 0.83/+0.32, H2 0.93/+0.12, all 0.99/+0.02
- plateau neighbours (all-in uplift): {'share25': 0.05, 'share42': -0.03, 'm x0.75': -0.03, 'm x1.25': 0.06, 'L x0.75': -0.05, 'L x1.25': 0.02}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.99; no hedge claim)
- affected share/range: min 0.50 max 1.00 mean 0.991
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = L360_COUNTER_DOWN (uplift +0.13); read on held-out months +0.05. Carried clean cell L360_COUNTER_DOWN: selection-months +0.13, held-out +0.05.
- even->odd: cell selected on the selection months = L180_COUNTER_DOWN (uplift +0.10); read on held-out months -0.50. Carried clean cell L360_COUNTER_DOWN: selection-months +0.05, held-out +0.13.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.52 | 2.92 | 5.62 | -79.6k | -78.5k | 248k | -83.5k | 44.8 |
| H1 cand | 3.06 | 6.94 | 4.52 | -77.1k | -65.7k | 147k | -77.4k | 35.7 |
| H2 cand | 2.36 | 4.84 | 3.67 | -81.1k | -79.3k | 220k | -82.5k | 41.7 |
| all cand | 1.95 | 3.87 | 11.56 | -79.7k | -78.5k | 248k | -83.5k | 42.9 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 4.7, -1.0, -2.0, 11.5); H1 (False, 11.9, 0.6, 1.2, 3.2); H2 (False, 5.9, 0.0, 0.0, -1.0); all (False, 6.6, -0.6, -1.2, 11.5)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pc_run.py (copy ap_pxw_run.py), ap_g10_rep.py, ap_h7_alt.py, ap_pxw_doc.py; outputs/autopilot/px24/.

DONE PX24
