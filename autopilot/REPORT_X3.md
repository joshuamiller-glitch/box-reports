# REPORT X3

**NO - trend-aligned continuation after >= 1.5/2.0 ATR days: best selected cell X3_1.5_h5_ALL26: standalone Sharpe 2013-22 0.45, pair window 0.31, own-null rank pair window 0.82; additive uplift at 20% clean/H1/H2 -0.02/-0.03/+0.11, bootstrap lo -0.25; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea X3: follow the 1-day move >= m ATR20 (m 1.5,2.0) only if it agrees with sign(c-EMA100) of the prior day; hold 2/3/5; ALL26 or COM+RATES = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 3
| cell                |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:--------------------|-----------------:|-------------:|----------:|
| X3_2_h5_ALL26       |              311 |         0.47 |         6 |
| X3_1.5_h5_ALL26     |             1060 |         0.45 |         7 |
| X3_2_h5_COM+RATES   |              195 |         0.41 |         7 |
| X3_2_h3_ALL26       |              325 |         0.34 |         8 |
| X3_1.5_h3_ALL26     |             1113 |         0.34 |         7 |
| X3_1.5_h5_COM+RATES |              682 |         0.31 |         6 |
| X3_2_h3_COM+RATES   |              207 |         0.27 |         8 |
| X3_1.5_h3_COM+RATES |              718 |         0.2  |         6 |
| X3_2_h2_ALL26       |              333 |        -0.01 |         6 |
| X3_1.5_h2_ALL26     |             1153 |        -0.08 |         5 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X3_1.5_h5_ALL26 | 0.45 | 7 | 0.13 | -0.28 | 1.18 | 0.31 | 0.26 | 0.67 | 0.82 | 0.26 | 1.00 |
| X3_2_h3_ALL26 | 0.34 | 8 | 0.34 | 0.35 | -0.15 | 0.18 | 0.27 | 0.80 | 0.73 | 0.30 | 0.97 |
| X3_1.5_h3_ALL26 | 0.34 | 7 | 0.05 | -2.30 | 0.12 | -0.25 | 0.07 | 0.56 | 0.48 | 0.20 | 0.98 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X3_1.5_h5_ALL26 | 2.5 | 10% | 0.01 | 0.01 | 0.08 | 0.03 | 2 | -0.10 | 0.50 | -0.11 | -0.01 | NO |
| X3_1.5_h5_ALL26 | 2.5 | 20% | -0.02 | -0.03 | 0.11 | 0.01 | 19 | -0.25 | 0.50 | -0.11 | -0.01 | NO |
| X3_1.5_h5_ALL26 | 2.5 | 30% | -0.08 | -0.11 | 0.11 | -0.04 | 47 | -0.43 | 0.50 | -0.11 | -0.01 | NO |
| X3_1.5_h5_ALL26 | 2.5 | 50% | -0.24 | -0.37 | 0.04 | -0.21 | 182 | -0.80 | 0.50 | -0.11 | -0.01 | NO |
| X3_2_h3_ALL26 | 5.2 | 10% | 0.03 | 0.09 | -0.05 | 0.02 | 5 | -0.08 | 0.63 | -0.39 | -0.03 | NO |
| X3_2_h3_ALL26 | 5.2 | 20% | 0.04 | 0.13 | -0.14 | 0.01 | 16 | -0.18 | 0.63 | -0.39 | -0.03 | NO |
| X3_2_h3_ALL26 | 5.2 | 30% | 0.05 | 0.10 | -0.26 | -0.02 | 36 | -0.31 | 0.63 | -0.39 | -0.03 | NO |
| X3_2_h3_ALL26 | 5.2 | 50% | 0.03 | -0.10 | -0.53 | -0.12 | 114 | -0.58 | 0.63 | -0.39 | -0.03 | NO |
| X3_1.5_h3_ALL26 | 3.0 | 10% | -0.00 | -0.35 | -0.02 | -0.05 | 3 | -0.19 | 0.72 | -0.58 | -0.05 | NO |
| X3_1.5_h3_ALL26 | 3.0 | 20% | -0.04 | -0.76 | -0.07 | -0.15 | 9 | -0.41 | 0.72 | -0.58 | -0.05 | NO |
| X3_1.5_h3_ALL26 | 3.0 | 30% | -0.12 | -1.18 | -0.14 | -0.28 | 30 | -0.65 | 0.72 | -0.58 | -0.05 | NO |
| X3_1.5_h3_ALL26 | 3.0 | 50% | -0.31 | -1.96 | -0.33 | -0.56 | 139 | -1.14 | 0.72 | -0.58 | -0.05 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| X3_1.5_h5_ALL26 | 10% | -7.3 | 7.3 | 7.1 | 6.5 | 7/8 | 4/13 | NO |
| X3_1.5_h5_ALL26 | 20% | -14.6 | -6.3 | 9.4 | 13.0 | -7/9 | 9/26 | NO |
| X3_1.5_h5_ALL26 | 30% | -21.9 | -59.0 | 1.4 | 18.8 | -60/-5 | 13/29 | NO |
| X3_1.5_h5_ALL26 | 50% | -36.6 | -231.1 | -21.1 | -9.0 | -234/-42 | 14/17 | NO |
| X3_2_h3_ALL26 | 10% | -8.9 | 4.7 | 10.0 | 11.3 | 4/9 | 18/25 | NO |
| X3_2_h3_ALL26 | 20% | -17.8 | 0.7 | 13.9 | 18.7 | -0/12 | 12/24 | NO |
| X3_2_h3_ALL26 | 30% | -26.7 | -27.0 | 7.0 | 19.9 | -18/15 | -24/14 | NO |
| X3_2_h3_ALL26 | 50% | -44.6 | -120.0 | -10.2 | 6.4 | -55/16 | -98/-30 | NO |
| X3_1.5_h3_ALL26 | 10% | -12.3 | 6.8 | 8.1 | 4.9 | 8/9 | 8/15 | NO |
| X3_1.5_h3_ALL26 | 20% | -24.5 | 4.8 | 11.6 | 9.8 | 4/12 | 15/16 | NO |
| X3_1.5_h3_ALL26 | 30% | -36.8 | -33.3 | 0.0 | 14.4 | -34/1 | -15/3 | NO |
| X3_1.5_h3_ALL26 | 50% | -61.3 | -188.2 | -41.3 | -1.9 | -191/-35 | -82/-41 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| X3_1.5_h5_ALL26 | 0.01 | 4 | 0.25 | -0.19 / -0.11 | -0.04 / -0.05 / 0.09 / -0.01 | 0.23 | -0.01 / -0.01 / 0.13 / 0.03 |
| X3_2_h3_ALL26 | 0.01 | 4 | 0.00 | -0.33 / -0.12 | 0.03 / 0.10 / -0.15 / -0.01 | 0.11 | 0.05 / 0.15 / -0.14 / 0.03 |
| X3_1.5_h3_ALL26 | -0.15 | 4 | 0.00 | -0.40 / -0.19 | -0.07 / -0.79 / -0.09 / -0.18 | -0.35 | -0.02 / -0.56 / -0.06 / -0.12 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| X3_1.5_h5_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.25) | fail | PASS (-0.11) | NO |
| X3_2_h3_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.39) | NO |
| X3_1.5_h3_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.58) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X3_1.5_h5_ALL26 | clean | 0.13 | 208,674 | -628,172 | -226,738 | -164,491 | 687,256 | 0.19 | 0.30 | 43 | 1.38 | -121,166 | -96,822 | 309,613 | 4.50 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| X3_1.5_h5_ALL26 | H1 | -0.28 | -75,469 | -131,902 | -130,424 | -121,849 | 337,606 | -0.43 | -0.22 | 57 | 2.72 | -91,622 | -70,454 | 163,873 | 3.49 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| X3_1.5_h5_ALL26 | H2 | 1.18 | 589,023 | -99,417 | -73,642 | -58,853 | 342,755 | 4.60 | 1.72 | 43 | 2.37 | -94,014 | -90,405 | 201,442 | 4.66 | 49 | 2.26 | -82,524 | -81,089 | 217,425 |
| X3_1.5_h5_ALL26 | all | 0.31 | 722,228 | -628,172 | -191,295 | -140,584 | 687,256 | 0.50 | 1.05 | 45 | 1.81 | -121,166 | -95,431 | 309,613 | 9.37 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |
| X3_2_h3_ALL26 | clean | 0.34 | 261,706 | -201,096 | -135,507 | -94,676 | 520,598 | 0.50 | 0.50 | 17 | 1.50 | -112,493 | -88,981 | 294,611 | 4.78 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| X3_2_h3_ALL26 | H1 | 0.35 | 104,431 | -298,456 | -197,432 | -136,688 | 391,677 | 0.45 | 0.27 | 18 | 2.92 | -100,757 | -79,884 | 177,847 | 3.51 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| X3_2_h3_ALL26 | H2 | -0.15 | -74,462 | -373,504 | -253,413 | -144,858 | 563,447 | -0.22 | -0.13 | 16 | 2.01 | -101,674 | -91,683 | 208,654 | 3.54 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| X3_2_h3_ALL26 | all | 0.18 | 291,675 | -373,504 | -182,509 | -119,342 | 563,447 | 0.26 | 0.52 | 17 | 1.84 | -112,493 | -90,890 | 294,611 | 9.41 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |
| X3_1.5_h3_ALL26 | clean | 0.05 | 84,492 | -557,492 | -223,047 | -155,097 | 721,696 | 0.09 | 0.12 | 41 | 1.34 | -107,462 | -90,409 | 322,907 | 4.20 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| X3_1.5_h3_ALL26 | H1 | -2.30 | -744,763 | -274,319 | -217,731 | -193,856 | 744,763 | -2.49 | -1.00 | 61 | 1.65 | -93,515 | -88,696 | 197,108 | 1.88 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| X3_1.5_h3_ALL26 | H2 | 0.12 | 50,990 | -280,267 | -179,107 | -118,597 | 514,080 | 0.19 | 0.10 | 35 | 2.12 | -95,365 | -91,962 | 207,513 | 3.74 | 49 | 2.26 | -82,524 | -81,089 | 217,425 |
| X3_1.5_h3_ALL26 | all | -0.25 | -609,281 | -557,492 | -230,520 | -165,908 | 1,011,294 | -0.39 | -0.60 | 43 | 1.58 | -107,462 | -92,088 | 322,907 | 7.75 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE X3
