# REPORT K17 - FLATTEN 5/15/30 MIN BEFORE CPI/NFP/FOMC (exits only), live pair
**Verdict: NO. FOUND 0. Selected flatten 5 min before the print (all open rows, FOMC+NFP+CPI): weekly Sharpe uplift -0.044 clean / +0.086 H1 / -0.303 H2 (needed +0.10 each); all-in -0.085; bootstrap CI [-0.26, +0.07]; 15- and 30-minute offsets also negative on clean (-0.078, -0.057)**

## Set-up and fill model
- Calendars: verified FOMC (14:00 ET), NFP and CPI (08:30 ET), 2023-08-01..2026-10-13 (same lists as H10-A). Pair rows open at flatten time: about 130 of 13,089 per offset (about 1% of rows; power is low by construction).
- Flatten (exits only): every pair row open at the flatten bar is exited at that bar's close (market, 1 tick/side + $34.88 per 8 lots), the 60/60 bracket checked on 1-second bars until then; later pair signals and entries between the flatten time and the print are unchanged (so a flip at 08:20 still enters and is held through an 08:30 print when the offset is 30 min: exits only, as the backlog says). Modified rows re-run through the live account (per-book rules, day lock, week floor 8R). Baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean process: 1.46/2.83/2.30. 2x slippage SLIP_PT 1.0.
- The 5-minute cell is the same as H10-A cell FNC -5 all and reproduces it (-0.044/+0.086/-0.303), disclosed duplicate; 15 and 30 minutes are new.
- Null: the same number of pseudo-events at the same clock times on random pair days (100 draws, linear delta-P&L swap against the baseline locks). Plateau: offset x0.75 / x1.25 (4 and 6 minutes).

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| ('FNC', -5, 'all') **(selected)** | -0.044 | +0.086 | -0.303 | -0.085 |
| ('FNC', -15, 'all') | -0.078 | +0.103 | -0.308 | -0.106 |
| ('FNC', -30, 'all') | -0.057 | +0.172 | -0.321 | -0.082 |

## Result for the carried cell: ('FNC', -5, 'all')
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.42 | -0.044 | -0.095 |
| H1 | 2.83 | 2.91 | +0.086 | +0.082 |
| H2 | 2.30 | 1.99 | -0.303 | -0.300 |
| all | 1.86 | 1.77 | -0.085 | -0.117 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean -0.044 vs -0.040 / 0.92; H1 +0.086 vs +0.279 / 0.66; H2 -0.303 vs +0.371 / 0.00; all -0.085 vs +0.048 / 0.21
- bootstrap 90% CI of all-in uplift: [-0.259, +0.069]
- plateau: 0.00 of 2 neighbours keep >= 75% of the all-in uplift; neighbours: off x0.75 -0.108; off x1.25 -0.104
- alternating-month split (pre-registered): select ('FNC', -5, 'all') (+0.062) reads -0.139 on the other half; select ('FNC', -30, 'all') (-0.072) reads -0.024 on the other half
- H0 (2023-02-10..07-31) uplift: n/a; replications counted (alt-month, H0): 0 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -81.9k vs -81.9k; H1 -78.3k vs -78.3k; H2 -82.5k vs -82.5k; all -82.5k vs -82.5k; weekly corr with pair 0.983 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.42 | 2.66 | 4.36 | -78.7k | -78.0k | 294k | -81.9k | 43.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.91 | 6.25 | 3.99 | -77.6k | -66.0k | 152k | -78.3k | 35.7 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 1.99 | 3.95 | 3.13 | -81.1k | -79.2k | 217k | -82.5k | 47.2 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 1.77 | 3.41 | 8.73 | -79.2k | -78.2k | 294k | -82.5k | 43.5 |

## Reading
Flattening open positions ahead of scheduled prints costs Sharpe on clean and H2 at every offset: the positions open at the print are on average carrying the pair's edge (trend continuation through the event), and only 130 rows are touched, so the cell moves weekly Sharpe by a few hundredths with a +-0.2 bootstrap interval. H1 is positive at every offset (+0.09 to +0.17) but H2 is -0.30 at every offset, so the sign is not stable. Together with H10-A (loss-only flatten, FNC -5 loss +0.06/+0.07/+0.07 unselected) the event-flatten idea is closed: it is not an insurance rule (worst week and CVaR unchanged) and not a Sharpe rule.

## Executability / era / replication
NT8: calendar-driven flatten of open positions N minutes before 08:30/14:00 ET on event days (strategy-side time check, no data feed); trivial to code but not recommended. Era: pair rows start 2023-02, calendars verified from 2023-08, so pre-2023 and H0 are n/a (ERA flag n/a). Replication not attempted beyond the pre-registered alternating-month split (fails). Mechanism depends on current structure of scheduled-release gap risk; no evidence it pays. Files: code/census/night_ins/ap_k17.py, ap_k17_rep.py, ap_k_lib.py; outputs/autopilot/k17/.

DONE K17
