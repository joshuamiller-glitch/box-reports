# REPORT G10-2 - EVENT-WINDOW SIZE TILT / POST-EVENT RE-ENGAGEMENT (D10 x M8)
**Verdict: NO. FOUND 0. Selected FNC_W2_m1.5: weekly Sharpe uplift +0.08 clean / +0.10 H1 / -0.14 H2 (needed +0.10 each); all-in +0.03; bootstrap 90% CI of all-in uplift [-0.05, +0.10]; plateau 0.50 of 4; null rank clean 0.95 (p95 +0.08).** Runtime ~15 min engine runs (pool of 5), pre-registered in PREREG_AUTOPILOT.md section G10 before the first run.

## Set-up and fill model
- Entries inside [T-60,T+60) or [T+60,T+240] of the release scaled by m in {0.5,1.5}; sets FNC/FNCE; 8 cells. Null: same window around pseudo-releases on random days, same count and clock (100 draws).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Multipliers through B.Cfg.sizefn (0 = skip entry), dollar rules unchanged. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised (net change shown). Whole-lot sizes at 8 contracts (4/6/12 lots), no rounding issue.
- Selection on clean only (uplift vs baseline per cell, clean): FNC_W1_m0.5 +0.081, FNC_W1_m1.5 -0.088, FNC_W2_m0.5 -0.015, FNC_W2_m1.5 +0.081, FNCE_W1_m0.5 +0.053, FNCE_W1_m1.5 -0.096, FNCE_W2_m0.5 -0.010, FNCE_W2_m1.5 +0.059. Top cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.54 | +0.08 | +0.05 | +0.09 |
| H1 | 2.83 | 2.92 | +0.10 | +0.07 | +0.09 |
| H2 | 2.30 | 2.15 | -0.14 | -0.13 | -0.14 |
| all | 1.86 | 1.88 | +0.03 | +0.01 | +0.03 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (uplift, rank): clean 0.95/+0.08, H1 0.63/+0.32, H2 0.02/+0.14, all 0.75/+0.07
- plateau neighbours (all-in uplift): {'win x0.75': 0.013668575299925045, 'm x0.75': 0.019699608489674558, 'win x1.25': 0.06774597797753601, 'm x1.25': 0.025542410442405794}
- worst-decile corr: n/a (size overlay, weekly corr with pair 1.00; no hedge claim)
- multiplier range 1.00-1.50, mean 1.013
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.54 | 2.96 | 5.13 | -78.8k | -78.0k | 277k | -81.9k | 42.9 |
| H1 cand | 2.92 | 6.25 | 4.01 | -77.6k | -66.0k | 152k | -78.3k | 35.7 |
| H2 cand | 2.15 | 4.39 | 3.31 | -81.1k | -79.2k | 217k | -82.5k | 47.2 |
| all cand | 1.88 | 3.70 | 9.92 | -79.2k | -78.3k | 277k | -82.5k | 42.9 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 7.0, -0.1, 0.0, 1.0); H1 (False, 2.5, 0.0, 0.0, 0.0); H2 (False, -5.6, 0.0, 0.0, 0.0); all (False, 2.5, -0.0, 0.0, 1.0)

## Executability / era / replication
NT8 at NinjaTrader Brokerage via Rithmic: a calendar table (or cross-asset data feed for G10-3: ZN/6J 1-min series in the same NT8 workspace) drives a size multiplier on the existing strategies; no new orders. Era flag: pair rows start 2023-08, so an H0 or pre-2023 replication of an overlay is not available; replication not attempted because a gate already fails.
ECB dates (G10-1/2 FNCE sets) are from memory, unverified; FOMC/NFP/CPI verified.

Files: code/census/night_ins/ap_g10_core.py, ap_g10_run.py, ap_g10_xa.py, ap_g10_rep.py (=ap_b17_rep), ap_g10_doc.py; outputs/autopilot/g10_2/.

DONE G10-2
