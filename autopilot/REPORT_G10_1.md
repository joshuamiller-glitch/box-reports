# REPORT G10-1 - EVENT-DAY SIZE TILT of the live pair (D10 x M8)
**Verdict: NO. FOUND 0. Selected FNC_m0.75: weekly Sharpe uplift -0.01 clean / +0.21 H1 / -0.39 H2 (needed +0.10 each); all-in -0.06; bootstrap 90% CI of all-in uplift [-0.27, +0.12]; plateau 0.00 of 2; null rank clean 0.74 (p95 +0.10).** Runtime ~15 min engine runs (pool of 5), pre-registered in PREREG_AUTOPILOT.md section G10 before the first run.

## Set-up and fill model
- Entries on FOMC / FNC / FNCE event label days scaled by m in {0.5,0.75}; 6 cells. Null: same number of random label days, same m (100 draws).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Multipliers through B.Cfg.sizefn (0 = skip entry), dollar rules unchanged. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised (net change shown). Whole-lot sizes at 8 contracts (4/6/12 lots), no rounding issue.
- Selection on clean only (uplift vs baseline per cell, clean): F_m0.5 -0.092, F_m0.75 -0.048, FNC_m0.5 -0.006, FNC_m0.75 -0.005, FNCE_m0.5 -0.114, FNCE_m0.75 -0.027. Top cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.45 | -0.01 | +0.16 | +0.02 |
| H1 | 2.83 | 3.03 | +0.21 | +0.08 | +0.21 |
| H2 | 2.30 | 1.91 | -0.39 | -0.36 | -0.68 |
| all | 1.86 | 1.79 | -0.06 | +0.03 | -0.12 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (uplift, rank): clean 0.74/+0.10, H1 0.80/+0.37, H2 0.21/+0.38, all 0.50/+0.11
- plateau neighbours (all-in uplift): {'m x0.75': -0.1063891004721742, 'm x1.25': -0.10237652674195408}
- worst-decile corr: n/a (size overlay, weekly corr with pair 0.98; no hedge claim)
- multiplier range 0.75-1.00, mean 0.971
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.45 | 2.72 | 4.90 | -78.6k | -77.9k | 271k | -81.9k | 41.0 |
| H1 cand | 3.03 | 6.56 | 4.13 | -77.6k | -66.0k | 157k | -78.3k | 35.7 |
| H2 cand | 1.91 | 3.78 | 2.79 | -78.6k | -76.8k | 224k | -79.7k | 47.2 |
| all cand | 1.79 | 3.45 | 9.60 | -78.6k | -77.9k | 271k | -81.9k | 41.7 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -0.3, 0.2, 0.0, 3.4); H1 (False, 8.9, 0.0, 0.0, -3.2); H2 (False, -17.8, 3.1, 3.5, -3.2); all (False, -3.2, 0.8, 0.8, 3.4)

## Executability / era / replication
NT8 at NinjaTrader Brokerage via Rithmic: a calendar table (or cross-asset data feed for G10-3: ZN/6J 1-min series in the same NT8 workspace) drives a size multiplier on the existing strategies; no new orders. Era flag: pair rows start 2023-08, so an H0 or pre-2023 replication of an overlay is not available; replication not attempted because a gate already fails.
ECB dates (G10-1/2 FNCE sets) are from memory, unverified; FOMC/NFP/CPI verified.

Files: code/census/night_ins/ap_g10_core.py, ap_g10_run.py, ap_g10_xa.py, ap_g10_rep.py (=ap_b17_rep), ap_g10_doc.py; outputs/autopilot/g10_1/.

DONE G10-1
