# REPORT H10-A - EXIT-ALL / FLATTEN AT RELEASE (D10 x M5), live pair
**Verdict: NO. FOUND 0. Selected FNC / flatten at the print / only positions in unrealised loss: weekly Sharpe uplift +0.095 clean / +0.035 H1 / -0.104 H2 (needed +0.10 each); all-in +0.043; bootstrap 90% CI of all-in uplift [-0.06, +0.15]; plateau 0.5 of 2; null rank clean 0.97 (p95 +0.085, so clean beats null) but H2 rank 0.04.** Engine cost was small (rows replayed from fill on 1-second bars through ap_g11_c_core.rs, ~13 s per grid). Pre-registered in PREREG_AUTOPILOT.md section H10 before the first run.

## Set-up and fill model
- Calendars: VERIFIED only (FOMC_V 14:00 ET, NFP_V and CPI_V 08:30 ET, 2023-08-01..2026-10-13; no ECB). Rows open at the print: FOMC 33, NFP 50, CPI 41 of 13,089 pair rows (about 3% of days touched, so power is low by construction).
- Flatten: a pair row open at the flatten bar is exited at that bar's close (market, 1 tick/side + $34.88 per 8 lots as live), 60/60 bracket checked on 1-s bars until then; other rows and later pair signals unchanged; modified rows re-run through the live account (per-book rules, day lock, week floor 8R). Baseline B.Cfg(wk_floor=8,wk_loss_pb=None), clean process, reproduced 1.46/2.83/2.30. 2x slippage SLIP_PT 1.0 both sides.
- Grid (8): events {FOMC; FOMC+NFP+CPI} x offset {-5, 0 min} x scope {all open; only unrealised-loss}. Selection clean only. Null: same count of pseudo-events at the same clock times on random pair days, 100 draws, linear delta-P&L approximation (as G11-C).

## Grid, clean uplift (all spans printed after selection for transparency; only the selected cell was read)
| cell | rows flattened | clean | H1 | H2 | all |
|---|---|---|---|---|---|
| F -5 all | 33 | -0.034 | +0.010 | +0.016 | -0.013 |
| F -5 loss | 23 | -0.015 | +0.010 | +0.014 | -0.003 |
| F 0 all | 33 | -0.036 | -0.006 | +0.013 | -0.018 |
| F 0 loss | 20 | -0.039 | -0.006 | +0.013 | -0.021 |
| FNC -5 all | 131 | -0.044 | +0.086 | -0.303 | -0.085 |
| FNC -5 loss | 74 | +0.060 | +0.073 | +0.069 | +0.066 |
| FNC 0 all | 124 | -0.022 | +0.054 | -0.139 | -0.040 |
| **FNC 0 loss (selected)** | 68 | **+0.095** | +0.035 | -0.104 | +0.043 |
Unselected FNC -5 loss is positive on all three spans (+0.06/+0.07/+0.07) but below +0.10 everywhere and was not the clean-best; it is noted as an observation only, not carried (selection rule fixed in advance, no re-run).

## Result for the carried cell (weekly Sharpe)
| span | pair | flatten | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.55 | +0.095 | +0.088 |
| H1 | 2.83 | 2.86 | +0.035 | +0.033 |
| H2 | 2.30 | 2.19 | -0.104 | -0.103 |
| all | 1.86 | 1.90 | +0.043 | +0.038 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL (+0.095/+0.035/-0.104)
- worst week not worse (all-in): PASS (delta 0; worst week unchanged -82.5k)
- own null p95: clean PASS (rank 0.97, p95 +0.085 < +0.095), H1 FAIL (rank 0.74), H2 FAIL (rank 0.04), all-in FAIL (rank 0.88, p95 +0.071)
- bootstrap CI > 0: FAIL ([-0.06, +0.15])
- plateau: FAIL (0.5 of 2: offset x0.75 +0.045 keeps; x1.25 -0.027)
- 2x slip: FAIL (needs +0.10 each span)
- alternating-month split (pre-registered): select odd -> FNC 0 all (+0.086) reads -0.124 on even; select even -> FNC 0 loss (+0.102) reads +0.082 on odd: mixed, not 2 clean passes
- wd corr: n/a (flatten of pair rows; weekly corr with pair 0.993, no hedge claim)
- Pre-registration, clean-only selection, H1/H2 once: PASS (process)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.55 | 2.96 | 5.02 | -78.7k | -78.0k | 280k | -81.9k | 41.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.86 | 6.14 | 3.94 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 2.19 | 4.49 | 3.37 | -81.1k | -79.2k | 217k | -82.5k | 47.2 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 1.90 | 3.71 | 9.77 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
The worst weeks and CVaR do not move: flattening into prints does not touch the pair's tail weeks (not an insurance rule).

## Executability / era / replication
NT8 would need a calendar-driven flatten of open positions at 08:30 / 14:00 ET on event days when in unrealised loss (strategy-side time check, no new data feed). Era flag: pair rows start 2023-08, so pre-2023 and H0 are n/a. Replication not attempted (primary gates fail). Mechanism depends on current structure of scheduled-release gap risk; no evidence it pays.
Files: code/census/night_ins/ap_h10_a.py, ap_h10_a_rep.py; outputs/autopilot/h10_a/.

DONE H10-A
