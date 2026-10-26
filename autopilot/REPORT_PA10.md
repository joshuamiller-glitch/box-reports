# REPORT PA10 - K4 WALK-FORWARD DAILY FORECAST AS DIRECTION-ALIGNMENT TILT (D12 x M4, H5)
**Verdict: NO. FOUND 0. Selected d2_TWO: weekly Sharpe uplift +0.21 clean / -0.62 H1 / -0.67 H2 (needed +0.10 each); all-in -0.10; bootstrap 90% CI of all-in uplift [-0.65, +0.43]; plateau 0.00 of 6; null rank clean 0.75 (p95 +0.35).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PA2 batch' before the first run.

## Set-up and fill model
- a = side x (p-0.5), p = K4 pooled ES/NQ/RTY/YM LightGBM forecast (walk-forward quarterly refits since 2016, purged) for NQ of the last completed daily label strictly before the entry label day; model {d2,d4} x scheme {COUNTER_DOWN bottom tercile x0.5, ALIGN_UP top x1.5, TWO 0.75/1.25}; 6 cells. Null: p permuted across label days (100 reps). DISCLOSURE: K4 sleeve results and parent J9P-A had read the pair H1/H2: non-virgin.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): d2_COUNTER_DOWN -0.311, d2_ALIGN_UP +0.044, d2_TWO +0.211, d4_COUNTER_DOWN -0.611, d4_ALIGN_UP -0.032, d4_TWO +0.010. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.67 | +0.21 | +0.29 | +0.22 |
| H1 | 2.83 | 2.21 | -0.62 | +0.43 | -0.62 |
| H2 | 2.30 | 1.62 | -0.67 | +0.35 | -1.00 |
| all | 1.86 | 1.76 | -0.10 | +0.33 | -0.17 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.75/+0.35, H1 0.22/+0.80, H2 0.46/+0.48, all 0.52/+0.16
- plateau neighbours (all-in uplift): {'share25': -0.0, 'share42': -0.03, 'm x0.75': 0.2, 'm x1.25': -0.48, 'd2_s1': 0.0, 'd2_t188': -0.04}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.84; no hedge claim)
- affected share/range: min 0.75 max 1.25 mean 0.999
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = d2_ALIGN_UP (uplift -0.31); read on held-out months -0.09. Carried clean cell d2_TWO: selection-months -0.45, held-out +0.27.
- even->odd: cell selected on the selection months = d2_COUNTER_DOWN (uplift +0.46); read on held-out months -0.83. Carried clean cell d2_TWO: selection-months +0.27, held-out -0.45.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.67 | 3.25 | 4.75 | -79.0k | -78.2k | 330k | -80.2k | 41.0 |
| H1 cand | 2.21 | 4.29 | 4.49 | -77.7k | -77.6k | 123k | -77.9k | 28.6 |
| H2 cand | 1.62 | 3.10 | 2.70 | -80.9k | -79.7k | 213k | -82.1k | 41.7 |
| all cand | 1.76 | 3.39 | 8.16 | -79.4k | -78.5k | 330k | -82.1k | 39.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 17.9, -0.3, 2.1, -17.8); H1 (False, -7.1, -0.1, 0.5, 19.0); H2 (False, -24.7, 0.2, 0.5, 2.3); all (False, 0.3, -0.2, 0.5, -17.8)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pa2_run.py, ap_pa2_k4gen.py, ap_pa2_rep.py, ap_pa2_alt.py, ap_pa2_doc.py; outputs/autopilot/pa10/.

DONE PA10
