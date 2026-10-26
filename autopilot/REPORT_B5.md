# REPORT B5

**NO - 8 pre-registered commodity/rates seasonal sleeves (no selection): none beats its random-date null in BOTH 2013-22 and the pair window; best all-in additive uplift 0.16 at 20% (GC_A: GC long Jan-Feb, 2013-26 Sharpe 0.59, 2013-22 null rank 0.98, pair-window rank 0.85, bootstrap lo -0.00); equal-risk combination 2013-26 Sharpe 0.27; all sleeves small-sample (3-4 windows per annual sleeve in the pair window); FOUND 0.**



## Scope and protocol
Pre-registered (PREREG_AUTOPILOT.md CAPACITY BACKLOG B5) from the literature/lore BEFORE any return was loaded; NO in-sample selection, all 8 sleeves and their equal-risk combination reported, no date tuned. Rules differ from the C2-G4 set (R1-R7). Window entered at the open of the first trading day on/after the start date and exited at the close of the last trading day on/before the end date, no stop; incomplete final windows dropped; sized $7,000 per ATR20 (prior-day ATR20), scaled to the pair's clean weekly vol with the sleeve's own 2013-22 weekly vol. Own null: random-date windows of the same length, one per calendar year (ZN: same count per year), same side, 504 draws; plateau = window start/end moved by +-25% of the window length (>= 1 day). Scored 2013-2026, then the pair window (clean/H1/H2).

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Windows
| sleeve | rule | windows 2013-26 | windows in pair window |
|---|---|---|---|
| NG_A | NG long Sep1-Nov30 | 13 | 3 |
| NG_B | NG short Mar1-Jun30 | 14 | 3 |
| CL_A | CL short Sep15-Nov15 | 13 | 3 |
| GC_A | GC long Jan1-Feb28 | 13 | 3 |
| GC_B | GC long Aug1-Sep30 | 14 | 4 |
| GC_C | GC short Apr1-Jun30 | 14 | 3 |
| ZN_A | ZN long around quarter-ends | 55 | 13 |
| ZN_B | ZN long first 3 days of month | 165 | 39 |

Every annual sleeve has only 3-4 windows in the 38-month pair window: the small-sample flag applies to all, and their 2013-2026 Sharpe is the primary evidence.

## Standalone and own null (2013-26 Sharpe in the last-but-one column of the first table)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| NG_A | -0.01 | 2 | -0.18 | 1.76 | n/a | 0.19 | 0.02 | 0.34 | 0.91 | 0.43 | 0.42 |
| NG_B | -0.14 | 5 | 0.40 | n/a | -0.02 | 0.28 | -0.00 | 0.96 | 0.35 | 0.39 | 0.44 |
| CL_A | 0.31 | 6 | 0.81 | 0.34 | n/a | 0.57 | 0.37 | 0.79 | 0.85 | 0.60 | 0.75 |
| GC_A | 0.56 | 8 | 0.57 | 1.42 | 1.88 | 0.92 | 0.59 | 1.10 | 0.85 | 0.42 | 0.98 |
| GC_B | -0.36 | 4 | -0.34 | 3.38 | 0.13 | 0.51 | -0.11 | 1.14 | 0.52 | 0.29 | 0.17 |
| GC_C | 0.26 | 5 | -0.33 | n/a | 2.44 | -0.08 | 0.19 | 0.02 | 0.90 | 0.54 | 0.72 |
| ZN_A | 0.21 | 6 | -0.72 | -0.40 | -0.44 | -0.61 | -0.01 | 0.56 | 0.27 | 0.40 | 0.86 |
| ZN_B | -0.33 | 4 | 0.20 | 0.95 | -1.50 | 0.05 | -0.19 | 0.52 | 0.74 | 0.28 | 0.36 |
| ALL8 | 0.17 | 4 | 0.01 | 2.40 | 0.11 | 0.47 | 0.27 | 0.79 | 0.82 | 0.31 | 0.85 |

### Additive
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NG_A | 5.6 | 10% | -0.01 | 0.13 | 0.00 | 0.01 | 0 | -0.04 | 0.56 | 0.10 | -0.01 | UNSCORED (does not cover H2) |
| NG_A | 5.6 | 20% | -0.03 | 0.25 | 0.00 | 0.01 | 0 | -0.09 | 0.56 | 0.10 | -0.01 | UNSCORED (does not cover H2) |
| NG_A | 5.6 | 30% | -0.06 | 0.35 | 0.00 | 0.01 | 0 | -0.14 | 0.56 | 0.10 | -0.01 | UNSCORED (does not cover H2) |
| NG_A | 5.6 | 50% | -0.12 | 0.50 | 0.00 | -0.01 | 13 | -0.26 | 0.56 | 0.10 | -0.01 | UNSCORED (does not cover H2) |
| NG_B | 9.7 | 10% | 0.02 | 0.00 | 0.01 | 0.01 | 34 | -0.08 | 0.34 | 0.58 | 0.03 | UNSCORED (does not cover H1) |
| NG_B | 9.7 | 20% | 0.03 | 0.00 | 0.00 | 0.01 | 68 | -0.18 | 0.34 | 0.58 | 0.03 | UNSCORED (does not cover H1) |
| NG_B | 9.7 | 30% | 0.02 | 0.00 | -0.03 | -0.01 | 102 | -0.29 | 0.34 | 0.58 | 0.03 | UNSCORED (does not cover H1) |
| NG_B | 9.7 | 50% | -0.03 | 0.00 | -0.13 | -0.08 | 171 | -0.53 | 0.34 | 0.58 | 0.03 | UNSCORED (does not cover H1) |
| CL_A | 13.1 | 10% | 0.08 | -0.16 | 0.00 | 0.04 | 41 | -0.07 | 0.36 | 0.14 | 0.04 | UNSCORED (does not cover H2) |
| CL_A | 13.1 | 20% | 0.15 | -0.35 | 0.00 | 0.06 | 87 | -0.15 | 0.36 | 0.14 | 0.04 | UNSCORED (does not cover H2) |
| CL_A | 13.1 | 30% | 0.20 | -0.55 | 0.00 | 0.06 | 133 | -0.25 | 0.36 | 0.14 | 0.04 | UNSCORED (does not cover H2) |
| CL_A | 13.1 | 50% | 0.25 | -0.90 | 0.00 | 0.02 | 225 | -0.45 | 0.36 | 0.14 | 0.04 | UNSCORED (does not cover H2) |
| GC_A | 9.6 | 10% | 0.04 | 0.31 | 0.10 | 0.09 | 0 | 0.00 | 0.91 | -0.08 | -0.11 | NO |
| GC_A | 9.6 | 20% | 0.07 | 0.52 | 0.19 | 0.16 | 0 | -0.00 | 0.91 | -0.08 | -0.11 | NO |
| GC_A | 9.6 | 30% | 0.10 | 0.61 | 0.27 | 0.22 | 21 | -0.02 | 0.91 | -0.08 | -0.11 | NO |
| GC_A | 9.6 | 50% | 0.14 | 0.53 | 0.43 | 0.29 | 93 | -0.10 | 0.91 | -0.08 | -0.11 | NO |
| GC_B | 12.6 | 10% | -0.06 | 0.40 | -0.07 | 0.01 | 16 | -0.10 | 0.01 | -0.17 | 0.18 | NO |
| GC_B | 12.6 | 20% | -0.13 | 0.69 | -0.16 | -0.01 | 38 | -0.22 | 0.01 | -0.17 | 0.18 | NO |
| GC_B | 12.6 | 30% | -0.20 | 0.89 | -0.27 | -0.04 | 60 | -0.35 | 0.01 | -0.17 | 0.18 | NO |
| GC_B | 12.6 | 50% | -0.37 | 1.10 | -0.49 | -0.14 | 152 | -0.60 | 0.01 | -0.17 | 0.18 | NO |
| GC_C | 9.4 | 10% | -0.08 | 0.00 | 0.09 | -0.04 | 29 | -0.14 | 0.16 | 0.05 | 0.08 | UNSCORED (does not cover H1) |
| GC_C | 9.4 | 20% | -0.18 | 0.00 | 0.17 | -0.09 | 61 | -0.31 | 0.16 | 0.05 | 0.08 | UNSCORED (does not cover H1) |
| GC_C | 9.4 | 30% | -0.29 | 0.00 | 0.25 | -0.17 | 93 | -0.48 | 0.16 | 0.05 | 0.08 | UNSCORED (does not cover H1) |
| GC_C | 9.4 | 50% | -0.50 | 0.00 | 0.41 | -0.33 | 157 | -0.84 | 0.16 | 0.05 | 0.08 | UNSCORED (does not cover H1) |
| ZN_A | 26.4 | 10% | -0.10 | -0.12 | -0.04 | -0.09 | 0 | -0.20 | 0.34 | 0.02 | 0.03 | NO |
| ZN_A | 26.4 | 20% | -0.20 | -0.29 | -0.11 | -0.19 | 0 | -0.43 | 0.34 | 0.02 | 0.03 | NO |
| ZN_A | 26.4 | 30% | -0.32 | -0.49 | -0.18 | -0.31 | 36 | -0.66 | 0.34 | 0.02 | 0.03 | NO |
| ZN_A | 26.4 | 50% | -0.56 | -0.92 | -0.36 | -0.56 | 128 | -1.09 | 0.34 | 0.02 | 0.03 | NO |
| ZN_B | 13.8 | 10% | 0.01 | 0.06 | -0.09 | -0.01 | 0 | -0.11 | 0.49 | 0.17 | 0.01 | NO |
| ZN_B | 13.8 | 20% | -0.00 | 0.09 | -0.21 | -0.05 | 0 | -0.25 | 0.49 | 0.17 | 0.01 | NO |
| ZN_B | 13.8 | 30% | -0.04 | 0.07 | -0.33 | -0.10 | 0 | -0.40 | 0.49 | 0.17 | 0.01 | NO |
| ZN_B | 13.8 | 50% | -0.14 | -0.03 | -0.61 | -0.26 | 35 | -0.73 | 0.49 | 0.17 | 0.01 | NO |
| ALL8 | 3.6 | 10% | -0.02 | 0.24 | 0.00 | 0.02 | 10 | -0.08 | 0.15 | 0.39 | 0.10 | NO |
| ALL8 | 3.6 | 20% | -0.06 | 0.41 | -0.01 | 0.02 | 21 | -0.18 | 0.15 | 0.39 | 0.10 | NO |
| ALL8 | 3.6 | 30% | -0.11 | 0.51 | -0.03 | -0.00 | 32 | -0.30 | 0.15 | 0.39 | 0.10 | NO |
| ALL8 | 3.6 | 50% | -0.24 | 0.58 | -0.11 | -0.09 | 71 | -0.54 | 0.15 | 0.39 | 0.10 | NO |

### Constant-risk
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| NG_A | 10% | -9.4 | 10.0 | 10.1 | 10.0 | 10/10 | 12/15 | NO |
| NG_A | 20% | -18.9 | 20.0 | 20.1 | 18.5 | 20/20 | 21/30 | NO |
| NG_A | 30% | -28.3 | 29.1 | 29.2 | 19.6 | 29/29 | 31/44 | NO |
| NG_A | 50% | -47.1 | 2.8 | 38.5 | 16.9 | 2/33 | 51/59 | NO |
| NG_B | 10% | -8.6 | -23.6 | 4.1 | 7.8 | -25/4 | 10/10 | NO |
| NG_B | 20% | -17.2 | -48.0 | 7.3 | 12.8 | -49/7 | 20/20 | NO |
| NG_B | 30% | -25.8 | -72.3 | 10.6 | 17.9 | -74/10 | 30/30 | NO |
| NG_B | 50% | -42.9 | -121.1 | -11.0 | -1.8 | -123/-17 | 50/50 | NO |
| CL_A | 10% | -6.8 | -31.3 | 4.7 | 10.0 | 10/10 | -38/-14 | NO |
| CL_A | 20% | -13.6 | -67.8 | 4.8 | 20.0 | 1/16 | -77/-37 | NO |
| CL_A | 30% | -20.5 | -104.3 | 0.6 | 28.4 | -23/17 | -115/-66 | NO |
| CL_A | 50% | -34.1 | -177.2 | -8.9 | 10.0 | -69/18 | -192/-125 | NO |
| GC_A | 10% | -5.9 | 10.0 | 10.0 | 17.0 | 10/10 | 10/29 | NO |
| GC_A | 20% | -11.8 | 17.3 | 19.1 | 20.1 | 20/20 | 13/16 | NO |
| GC_A | 30% | -17.7 | -17.2 | 22.8 | 5.4 | 24/28 | -24/2 | NO |
| GC_A | 50% | -29.4 | -86.3 | 25.8 | -45.0 | -16/38 | -96/-24 | NO |
| GC_B | 10% | -6.6 | -6.2 | 6.8 | 1.0 | -7/6 | 10/10 | NO |
| GC_B | 20% | -13.3 | -19.0 | 8.4 | -18.3 | -20/9 | 20/20 | NO |
| GC_B | 30% | -19.9 | -49.4 | 2.0 | -37.6 | -51/1 | 25/27 | NO |
| GC_B | 50% | -33.1 | -159.8 | -33.5 | -76.2 | -162/-37 | -19/15 | NO |
| GC_C | 10% | -10.5 | -19.1 | 4.8 | 10.0 | -20/2 | 10/10 | NO |
| GC_C | 20% | -21.0 | -41.3 | 8.4 | 20.0 | -42/3 | 20/20 | NO |
| GC_C | 30% | -31.5 | -63.6 | -1.3 | 24.5 | -65/-16 | 30/30 | NO |
| GC_C | 50% | -52.5 | -136.9 | -36.3 | -45.9 | -139/-74 | 50/50 | NO |
| ZN_A | 10% | -13.8 | 10.0 | 10.1 | 10.0 | 10/10 | 10/10 | NO |
| ZN_A | 20% | -27.5 | 9.9 | 18.3 | 20.0 | 20/20 | 5/12 | NO |
| ZN_A | 30% | -41.3 | -36.7 | 10.1 | 10.2 | -13/12 | -44/-8 | NO |
| ZN_A | 50% | -68.8 | -129.8 | -36.7 | -65.3 | -127/-35 | -142/-47 | NO |
| ZN_B | 10% | -9.7 | 10.0 | 10.2 | 11.4 | 12/11 | 10/10 | NO |
| ZN_B | 20% | -19.4 | 20.0 | 20.2 | 3.4 | 22/21 | 20/20 | NO |
| ZN_B | 30% | -29.1 | 17.1 | 25.4 | -8.0 | 16/24 | 30/30 | NO |
| ZN_B | 50% | -48.5 | -29.4 | -1.6 | -30.7 | -30/-9 | 19/33 | NO |
| ALL8 | 10% | -7.0 | -0.0 | 4.6 | 12.2 | -1/4 | -3/11 | NO |
| ALL8 | 20% | -14.1 | -0.9 | 7.1 | 12.7 | -2/6 | -6/21 | NO |
| ALL8 | 30% | -21.1 | -7.8 | 7.5 | 4.3 | -9/5 | -9/21 | NO |
| ALL8 | 50% | -35.2 | -44.7 | -6.8 | -16.1 | -46/-15 | -15/1 | NO |

### Plateau, 2x slippage, alt baseline
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| NG_A | 0.01 | 4 | 0.00 | -0.02 / -0.01 | -0.03 / 0.25 / 0.00 / 0.01 | 0.19 | -0.03 / 0.19 / 0.00 / 0.01 |
| NG_B | 0.01 | 4 | 0.75 | -0.01 / 0.01 | 0.03 / 0.00 / -0.00 / 0.01 | 0.27 | 0.03 / 0.00 / 0.00 / 0.01 |
| CL_A | 0.06 | 4 | 0.50 | 0.01 / 0.04 | 0.15 / -0.35 / 0.00 / 0.06 | 0.56 | 0.13 / -0.10 / 0.00 / 0.06 |
| GC_A | 0.16 | 4 | 0.75 | 0.11 / 0.16 | 0.07 / 0.52 / 0.19 / 0.16 | 0.92 | 0.06 / 0.56 / 0.18 / 0.17 |
| GC_B | -0.01 | 4 | 0.00 | -0.02 / 0.02 | -0.13 / 0.69 / -0.16 / -0.01 | 0.51 | -0.12 / 0.69 / -0.15 / 0.01 |
| GC_C | -0.09 | 4 | 0.00 | -0.17 / -0.13 | -0.18 / 0.00 / 0.17 / -0.09 | -0.08 | -0.17 / 0.00 / 0.17 / -0.08 |
| ZN_A | -0.19 | 4 | 0.00 | -0.28 / -0.17 | -0.22 / -0.33 / -0.13 / -0.22 | -0.70 | -0.20 / -0.17 / -0.12 / -0.18 |
| ZN_B | -0.05 | 4 | 0.00 | -0.10 / -0.07 | -0.03 / 0.04 / -0.24 / -0.08 | -0.10 | -0.02 / 0.12 / -0.21 / -0.05 |
| ALL8 | 0.02 | 4 | 0.50 | -0.01 / 0.02 | -0.08 / 0.38 / -0.03 / 0.00 | 0.38 | -0.07 / 0.48 / -0.02 / 0.03 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| NG_A | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.10) | NO |
| NG_B | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | PASS (0.75) | fail | fail (0.58) | NO |
| CL_A | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | PASS (0.14) | NO |
| GC_A | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | PASS (0.75) | fail | PASS (-0.08) | NO |
| GC_B | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.17) | NO |
| GC_C | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.05) | NO |
| ZN_A | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.02) | NO |
| ZN_B | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.17) | NO |
| ALL8 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | fail (0.39) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NG_A | clean | -0.18 | -101,260 | -171,560 | -103,413 | -75,994 | 482,794 | -0.25 | -0.21 | 12 | 1.40 | -81,874 | -78,736 | 295,407 | 4.40 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| NG_A | H1 | 1.76 | 254,666 | -87,730 | -59,200 | -46,837 | 210,052 | 3.62 | 1.21 | 18 | 3.17 | -76,932 | -65,627 | 137,633 | 4.87 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| NG_A | H2 | n/a | 0 | 0 | 0 | 0 | 0 | n/a | n/a | 0 | 2.26 | -82,524 | -81,089 | 217,425 | 3.50 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| NG_A | all | 0.19 | 153,405 | -171,560 | -90,240 | -61,189 | 482,794 | 0.28 | 0.32 | 11 | 1.87 | -82,524 | -79,112 | 295,407 | 9.24 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| NG_B | clean | 0.40 | 385,330 | -283,026 | -189,690 | -126,662 | 590,388 | 0.53 | 0.65 | 13 | 1.48 | -166,782 | -94,393 | 311,780 | 4.64 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| NG_B | H1 | n/a | 0 | 0 | 0 | 0 | 0 | n/a | n/a | 0 | 2.83 | -78,287 | -77,610 | 151,713 | 3.91 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| NG_B | H2 | -0.02 | -5,418 | -222,192 | -181,030 | -134,932 | 244,033 | -0.02 | -0.02 | 16 | 2.23 | -108,860 | -102,328 | 217,425 | 3.49 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| NG_B | all | 0.28 | 379,912 | -283,026 | -177,647 | -118,675 | 590,388 | 0.36 | 0.64 | 12 | 1.84 | -166,782 | -94,406 | 311,780 | 8.98 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| CL_A | clean | 0.81 | 706,931 | -233,995 | -105,583 | -63,481 | 423,945 | 1.62 | 1.67 | 9 | 1.66 | -113,443 | -85,593 | 280,110 | 5.51 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| CL_A | H1 | 0.34 | 145,811 | -379,216 | -288,800 | -197,792 | 380,742 | 0.46 | 0.38 | 14 | 2.28 | -192,052 | -147,219 | 237,725 | 2.68 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| CL_A | H2 | n/a | 0 | 0 | 0 | 0 | 0 | n/a | n/a | 0 | 2.26 | -82,524 | -81,089 | 217,425 | 3.50 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| CL_A | all | 0.57 | 852,743 | -379,216 | -137,509 | -76,260 | 423,945 | 0.90 | 2.01 | 8 | 1.92 | -192,052 | -99,121 | 280,110 | 10.50 | 41 | 1.86 | -82,524 | -79,220 | 280,110 |
| GC_A | clean | 0.57 | 272,748 | -176,837 | -71,224 | -39,022 | 269,128 | 0.90 | 1.01 | 8 | 1.56 | -81,874 | -78,831 | 289,483 | 4.88 | 40 | 1.46 | -81,874 | -78,736 | 280,110 |
| GC_A | H1 | 1.42 | 549,155 | -296,289 | -148,145 | -98,763 | 758,600 | 2.53 | 0.72 | 4 | 3.43 | -100,107 | -89,197 | 281,113 | 2.70 | 29 | 2.83 | -78,287 | -77,610 | 151,713 |
| GC_A | H2 | 1.88 | 282,059 | -17,326 | -8,663 | -4,332 | 189,398 | 19.30 | 1.49 | 3 | 2.53 | -82,524 | -81,089 | 217,425 | 3.89 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| GC_A | all | 0.92 | 1,103,963 | -296,289 | -82,540 | -43,698 | 758,600 | 1.68 | 1.46 | 6 | 2.07 | -100,107 | -81,805 | 289,483 | 10.42 | 38 | 1.86 | -82,524 | -79,220 | 280,110 |
| GC_B | clean | -0.34 | -321,004 | -442,228 | -185,688 | -113,444 | 941,765 | -0.41 | -0.34 | 10 | 1.26 | -131,852 | -94,929 | 452,483 | 2.73 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| GC_B | H1 | 3.38 | 1,169,180 | -177,601 | -88,800 | -59,200 | 296,568 | 8.97 | 3.94 | 4 | 3.72 | -78,287 | -77,610 | 151,713 | 6.23 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| GC_B | H2 | 0.13 | 57,784 | -197,868 | -165,536 | -141,150 | 657,588 | 0.23 | 0.09 | 16 | 1.99 | -115,665 | -103,013 | 320,297 | 2.43 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| GC_B | all | 0.51 | 905,960 | -442,228 | -185,694 | -119,768 | 941,765 | 0.78 | 0.96 | 11 | 1.82 | -131,852 | -95,522 | 452,483 | 6.53 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| GC_C | clean | -0.33 | -421,328 | -472,746 | -255,821 | -188,353 | 951,999 | -0.41 | -0.44 | 13 | 1.17 | -158,967 | -102,661 | 280,110 | 4.30 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| GC_C | H1 | n/a | 0 | 0 | 0 | 0 | 0 | n/a | n/a | 0 | 2.83 | -78,287 | -77,610 | 151,713 | 3.91 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| GC_C | H2 | 2.44 | 288,777 | -31,851 | -30,658 | -23,644 | 109,992 | 6.85 | 2.63 | 11 | 2.52 | -86,321 | -81,868 | 217,425 | 3.90 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| GC_C | all | -0.08 | -132,551 | -472,746 | -213,359 | -131,007 | 951,999 | -0.10 | -0.14 | 11 | 1.69 | -158,967 | -95,366 | 280,110 | 9.44 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| ZN_A | clean | -0.72 | -746,221 | -419,659 | -218,891 | -127,430 | 1,455,910 | -0.89 | -0.51 | 10 | 1.14 | -90,277 | -81,350 | 296,362 | 3.73 | 46 | 1.46 | -81,874 | -78,736 | 280,110 |
| ZN_A | H1 | -0.40 | -136,106 | -381,861 | -190,930 | -127,287 | 381,861 | -0.49 | -0.36 | 4 | 2.33 | -112,010 | -95,149 | 188,288 | 2.94 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| ZN_A | H2 | -0.44 | -129,105 | -265,506 | -167,871 | -83,936 | 415,530 | -0.56 | -0.31 | 5 | 2.08 | -82,524 | -81,089 | 220,811 | 3.27 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| ZN_A | all | -0.61 | -1,011,432 | -419,659 | -225,661 | -124,667 | 1,455,910 | -0.75 | -0.69 | 8 | 1.54 | -112,010 | -84,762 | 296,362 | 8.04 | 46 | 1.86 | -82,524 | -79,220 | 280,110 |
| ZN_B | clean | 0.20 | 242,378 | -223,103 | -183,228 | -126,846 | 578,178 | 0.35 | 0.42 | 20 | 1.42 | -79,868 | -77,875 | 364,467 | 3.85 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| ZN_B | H1 | 0.95 | 246,259 | -84,176 | -70,217 | -60,190 | 257,580 | 3.07 | 0.96 | 14 | 2.90 | -78,287 | -77,610 | 176,966 | 3.77 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| ZN_B | H2 | -1.50 | -406,437 | -263,607 | -186,590 | -121,284 | 542,283 | -1.60 | -0.75 | 22 | 1.93 | -82,524 | -81,863 | 221,211 | 2.89 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| ZN_B | all | 0.05 | 82,199 | -263,607 | -175,136 | -118,899 | 795,658 | 0.08 | 0.10 | 20 | 1.75 | -82,524 | -79,083 | 364,467 | 7.43 | 45 | 1.86 | -82,524 | -79,220 | 280,110 |
| ALL8 | clean | 0.01 | 5,968 | -280,419 | -169,057 | -131,709 | 824,457 | 0.01 | 0.01 | 40 | 1.35 | -108,505 | -96,597 | 327,458 | 4.07 | 40 | 1.46 | -81,874 | -78,736 | 280,110 |
| ALL8 | H1 | 2.40 | 756,906 | -130,527 | -116,087 | -110,453 | 275,279 | 5.04 | 2.75 | 25 | 3.34 | -108,781 | -79,613 | 154,120 | 5.33 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| ALL8 | H2 | 0.11 | 29,767 | -164,966 | -125,925 | -93,213 | 256,664 | 0.16 | 0.12 | 41 | 2.23 | -85,197 | -84,147 | 246,546 | 3.12 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| ALL8 | all | 0.47 | 792,642 | -280,419 | -156,831 | -124,389 | 824,457 | 0.72 | 0.96 | 38 | 1.85 | -108,781 | -95,350 | 327,458 | 8.93 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |

### Size / margin
Contracts per trade = k x $7,000 / (ATR20 x point value) at the pair's volatility (100% share; the 10-50% shares scale this down proportionally):

| sleeve | k | median ATR20 (pair window) | contracts at 100% share | margin $ (T4 table, metals 9% assumed) |
|---|---|---|---|---|
| NG_A | 5.6 | 0.129 | 30 | 121,316 |
| NG_B | 9.7 | 0.129 | 52 | 209,930 |
| CL_A | 13.1 | 1.876 | 49 | 341,931 |
| GC_A | 9.6 | 39.62 | 17 | 632,352 |
| GC_B | 12.6 | 39.62 | 22 | 828,332 |
| GC_C | 9.4 | 39.62 | 17 | 616,890 |
| ZN_A | 26.4 | 0.4805 | 384 | 845,424 |
| ZN_B | 13.8 | 0.4805 | 200 | 440,820 |

k is 4-26x for the sparse sleeves (a few weeks per year of exposure scaled to the pair's weekly vol), so full-share sizes are large; the 10-20% shares are 1/5-1/10 of the table.

## Verdict and reading
- FOUND 0, LEADS 0. Nothing carries a stable 2013-2026 seasonal edge: the 2013-26 Sharpes are -0.19 to +0.59 (GC long Jan-Feb +0.59 is the largest, 8 of 10 positive years and null rank 0.98 in 2013-22 but rank 0.85 in the pair window and the bootstrap lower bound is -0.00).
- GC_A (Jan-Feb gold) is the only sleeve with additive uplift positive on all three spans at 20% (0.07/0.52/0.19), but it is below +0.10 on clean, fails the null in the pair window, has only 3 windows there, and fails 2x slippage. It would need a replication on 2027 data to be anything.
- Multiplicity: 8 sleeves; expected chance passes of a p95 null in one span = 0.4, observed 1 in 2013-22 (GC_A) and 0 in the pair window.

## Executability (G7)
Calendar sleeves are trivially codable in NT8 (date-driven entries at the session open, exits at the close, no indicators): GC/MGC, NG/CL via micro (MCL) or outrights, ZN. Margin per the large sizes above; not recommended.


DONE B5
