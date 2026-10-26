# REPORT H10-B - EVENT-DAY TIGHTER DAY LOCK (D10 x M7), live pair
**Verdict: NO. FOUND 0. Selected L2W3 (per-book day-win cap cut 5R -> 3R on FOMC/NFP/CPI days only): weekly Sharpe uplift +0.001 clean / +0.011 H1 / -0.062 H2 (needed +0.10 each); all-in -0.009; bootstrap 90% CI of all-in uplift [-0.056, +0.045]; plateau 0.0 of 2; null rank clean 0.53 (p95 +0.040).** Runtime ~25 min (pool of 5). Pre-registered in PREREG_AUTOPILOT.md section H10 before the first run.

## Set-up and fill model
- Verified calendars only (FOMC 14:00, NFP and CPI 08:30 ET; 106 event label days 2023-08..2026-10-13; no ECB). On those label days only, the per-book daily limits (live: -2R loss, +5R win) and the combined day cap (live 8R; give-back arm 2R keep 33%) are tightened; all other days and the week floor (8R) are live. A custom pass1/lock-stage split (event-day groups vs other groups) reproduces the live engine exactly when parameters are unchanged (max |diff| 0.0 in the check). Fill model as live (1 tick/side + $34.88 per 8 lots); 2x slip SLIP_PT 1.0 both sides. Baseline B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process: 1.46/2.83/2.30.
- Grid (6): (day_loss R, day_win R) in {(1.0,5), (1.5,5), (2,3), (1.0,3), (1.5,3)} and combined cap 5R. Selection clean only. Null: same number of random label days, same parameters, 100 draws. Plateau: tightened parameter x0.75/x1.25.

## Grid, uplift on clean (other spans printed after selection for transparency)
| cell | clean | H1 | H2 | all |
|---|---|---|---|---|
| L1.0 W5 | -0.054 | -0.345 | -0.146 | -0.107 |
| L1.5 W5 | -0.017 | 0.000 | +0.079 | +0.010 |
| **L2 W3 (selected)** | +0.001 | +0.011 | -0.062 | -0.009 |
| L1.0 W3 | -0.053 | -0.331 | -0.199 | -0.112 |
| L1.5 W3 | -0.016 | +0.011 | +0.018 | +0.001 |
| cap 5R | -0.015 | +0.086 | -0.183 | -0.030 |
Tightening the loss limit on event days costs Sharpe on every span (stops-then-reversal days are net positive for the pair); no cell reaches +0.10 anywhere, and the best clean uplift is +0.001.

## Gate checklist (selected cell)
- 3 uplift >= +0.10 clean/H1/H2: FAIL (+0.001/+0.011/-0.062); vs B.Cfg(): -0.009/+0.021/-0.011
- worst week not worse (all-in): PASS (delta 0)
- null p95 clean/all-in: FAIL (rank 0.53 / 0.34)
- bootstrap CI > 0: FAIL ([-0.056, +0.045])
- plateau: FAIL (0 of 2: x0.75 -0.021, x1.25 +0.040 of all-in uplift -0.009)
- 2x slip: FAIL (+0.000/+0.015/-0.123)
- alternating-month split (pre-registered): select odd -> L1.5W3 (+0.043) reads -0.062 on even; select even -> cap 5R (+0.040) reads -0.048 on odd: both reverse, replication fails.
- wd corr: n/a (risk overlay; weekly corr with pair 0.997)
- Insurance flags: INS False on every span; CVaR5/10, worst week and maxDD identical to the pair (the event-day locks do not change the tail weeks).

## Insurance metrics (weekly): pair vs candidate
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.46 | 2.77 | 4.74 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.84 | 6.17 | 3.97 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 2.23 | 4.59 | 3.44 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 1.85 | 3.62 | 9.56 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |

## Executability / era / replication
NT8: per-strategy daily limits are already parameters of the live strategies; an event-day override needs a date table in the strategy (no new orders, no data feed). Era flag n/a (pair rows 2023-08+; H0 not available). Replication not attempted (primary gates fail). Files: code/census/night_ins/ap_h10_bc.py (b), ap_g10_rep.py; outputs/autopilot/h10_b/.

DONE H10-B
