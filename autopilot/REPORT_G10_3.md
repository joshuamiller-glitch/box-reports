# REPORT G10-3 - CROSS-ASSET RISK-OFF HALT of the live pair (D07 x M7)
**Verdict: NO. FOUND 0. Selected 6J_k3.0: weekly Sharpe uplift +0.41 clean / +0.11 H1 / -0.50 H2 (needed +0.10 each); all-in +0.17; bootstrap 90% CI of all-in uplift [-0.22, +0.60]; plateau 0.00 of 2; null rank clean 0.96 (p95 +0.34).** Runtime ~15 min engine runs (pool of 5), pre-registered in PREREG_AUTOPILOT.md section G10 before the first run.

## Set-up and fill model
- Halt new entries for the rest of the label day once ZN / 6J / either 60-min move >= +k sigma (k in {3,4,5} after the pre-run amendment); 9 cells. Null: real trigger offsets reassigned to random other label days (100 draws).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Multipliers through B.Cfg.sizefn (0 = skip entry), dollar rules unchanged. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised (net change shown). Whole-lot sizes at 8 contracts (4/6/12 lots), no rounding issue.
- Selection on clean only (uplift vs baseline per cell, clean): ZN_k3.0 -0.053, ZN_k4.0 -0.160, ZN_k5.0 -0.065, 6J_k3.0 +0.405, 6J_k4.0 +0.021, 6J_k5.0 +0.068, either_k3.0 +0.387, either_k4.0 -0.035, either_k5.0 +0.043. Top cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.86 | +0.41 | +0.19 | +0.47 |
| H1 | 2.83 | 2.93 | +0.11 | +0.76 | +0.18 |
| H2 | 2.30 | 1.80 | -0.50 | -0.05 | -0.44 |
| all | 1.86 | 2.03 | +0.17 | +0.22 | +0.24 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (uplift, rank): clean 0.96/+0.34, H1 0.83/+0.63, H2 0.29/+0.41, all 0.94/+0.18
- plateau neighbours (all-in uplift): {'k x0.75': -0.2906427281409336, 'k x1.25': 0.04642129264253736}
- worst-decile corr: n/a (size overlay, weekly corr with pair 0.91; no hedge claim)
- multiplier range 0.00-1.00, mean 0.805
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.86 | 3.50 | 6.98 | -78.1k | -77.6k | 232k | -79.9k | 38.1 |
| H1 cand | 2.93 | 6.29 | 4.76 | -77.5k | -68.0k | 136k | -77.9k | 35.7 |
| H2 cand | 1.80 | 3.45 | 3.26 | -81.1k | -79.1k | 180k | -82.5k | 44.4 |
| all cand | 2.03 | 3.88 | 12.30 | -78.7k | -78.0k | 232k | -82.5k | 39.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 22.0, 0.9, 2.5, 17.0); H1 (False, 9.2, 0.1, 0.5, 10.3); H2 (False, -22.9, 0.0, 0.0, 17.1); all (False, 6.4, 0.6, 0.0, 17.0)

## Executability / era / replication
NT8 at NinjaTrader Brokerage via Rithmic: a calendar table (or cross-asset data feed for G10-3: ZN/6J 1-min series in the same NT8 workspace) drives a size multiplier on the existing strategies; no new orders. Era flag: pair rows start 2023-08, so an H0 or pre-2023 replication of an overlay is not available; replication not attempted because a gate already fails.
ECB dates (G10-1/2 FNCE sets) are from memory, unverified; FOMC/NFP/CPI verified.

Files: code/census/night_ins/ap_g10_core.py, ap_g10_run.py, ap_g10_xa.py, ap_g10_rep.py (=ap_b17_rep), ap_g10_doc.py; outputs/autopilot/g10_3/.

DONE G10-3
