# REPORT K100 - LOW-VOLUME-DAY FILTER (first-30-min volume < 20th pct => skip), live pair
**Verdict: NO. FOUND 0. One pre-declared cell (skip entries 10:00 ET to the label end on days whose first-30-min volume is below the 20th percentile of the trailing 60 labels; 1064 of 13,089 rows skipped): weekly Sharpe uplift -0.244 clean / -0.341 H1 / +0.225 H2 (needed +0.10 each); all-in -0.167; bootstrap CI [-0.52, +0.19]; random-day null all-in rank 0.07**

## Set-up and fill model
- Feature: NQ volume of the harness 1-minute bars 09:30-10:00 ET of the label date (947 labels with data); low day = below the 20th percentile of the previous 60 labels (at least 20 prior; first-30 history in the 2023-02..2026-10 bar set). Rule: pair entries from 10:00 ET until 17:00 ET on a low day are skipped (weight 0 in the account; Globex entries before 09:30 and after 18:00 unaffected, no look-ahead). 216 of the labels are low days.
- Account: live pair rows with weight 0 for skipped rows through the live rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean process 1.46/2.83/2.30; 1 tick/side + $34.88 per 8 lots; 2x slippage SLIP_PT 1.0. Skipped rows still exist in the netting history of the baseline (their offsetting effect on other rows is not modelled; same convention as all pair-conditioning families).
- Null: same number of low days drawn at random among labels with post-10:00 entries (100 draws, linear net swap). Plateau: q 15/25 and window 45/75. Alternating-month: single pre-declared cell, both halves reported.

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| (20, 60) **(selected)** | -0.244 | -0.341 | +0.225 | -0.167 |

## Result for the carried cell: (20, 60)
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.22 | -0.244 | -0.076 |
| H1 | 2.83 | 2.49 | -0.341 | -0.334 |
| H2 | 2.30 | 2.52 | +0.225 | +0.189 |
| all | 1.86 | 1.69 | -0.167 | -0.060 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean -0.244 vs +0.136 / 0.18; H1 -0.341 vs +0.629 / 0.21; H2 +0.225 vs +0.567 / 0.56; all -0.167 vs +0.197 / 0.07
- bootstrap 90% CI of all-in uplift: [-0.522, +0.191]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: q15 -0.204; q25 -0.140; win45 -0.262; win75 -0.101
- alternating-month split (pre-registered): select (20, 60) (+0.163) reads -0.596 on the other half; select (20, 60) (-0.596) reads +0.163 on the other half
- H0 (2023-02-10..07-31) uplift: -0.100; replications counted (alt-month, H0): 0 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -81.9k vs -81.9k; H1 -78.1k vs -78.3k; H2 -77.9k vs -82.5k; all -81.9k vs -82.5k; weekly corr with pair 0.934 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.22 | 2.16 | 4.20 | -79.2k | -78.4k | 267k | -81.9k | 43.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.49 | 5.22 | 2.87 | -77.5k | -66.0k | 179k | -78.1k | 42.9 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 2.52 | 5.06 | 3.79 | -77.7k | -77.4k | 213k | -77.9k | 41.7 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 1.69 | 3.13 | 9.13 | -78.7k | -78.1k | 267k | -81.9k | 43.5 |

## Reading
Skipping low-first-half-hour-volume days removes about 8% of rows and loses Sharpe on clean (-0.24) and H1 (-0.34); H2 is positive (+0.22) and a random choice of the same number of days beats the real rule in 82% of draws on clean and 79% on H1 (rank 0.18/0.21; real beats the null only on H2 at rank 0.56), and every plateau neighbour is negative (q15 -0.20, q25 -0.14, win45 -0.26, win75 -0.10). First-30-minute participation does not identify the days on which the trend books whipsaw. Closes B100.

## Executability / era / replication
NT8: needs a rolling 60-label store of first-30-minute volume (strategy-side, available from the chart); trivial to code, not recommended. Era: pair rows start 2023-02; pre-2023 n/a (ERA flag n/a). H0 and alternating-month do not replicate. Files: code/census/night_ins/ap_k100.py, ap_k100_rep.py, ap_k_lib.py; outputs/autopilot/k100/.

DONE K100
