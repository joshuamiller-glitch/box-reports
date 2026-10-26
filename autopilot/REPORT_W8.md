# REPORT W8

**NO - bond momentum -> equity lead-lag: best selected cell W8_10_1_h5_NQ: standalone Sharpe 2013-22 0.58, pair window 0.31, own-null rank pair window 0.73; additive uplift at 20% clean/H1/H2 +0.08/+0.29/-0.20, bootstrap lo -0.12; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea W8: sign of ZN 10/20-day return sets long/short ES NQ RTY (both signs), hold 5 = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 4
| cell            |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:----------------|-----------------:|-------------:|----------:|
| W8_20_1_h5_NQ   |              614 |         0.6  |         7 |
| W8_20_1_h5_ES   |              614 |         0.59 |         7 |
| W8_10_1_h5_NQ   |              613 |         0.58 |         9 |
| W8_20_1_h5_RTY  |              336 |         0.55 |         4 |
| W8_10_1_h5_ES   |              613 |         0.46 |         9 |
| W8_10_1_h5_RTY  |              336 |         0.39 |         4 |
| W8_10_-1_h5_RTY |              336 |        -0.47 |         1 |
| W8_20_-1_h5_RTY |              336 |        -0.62 |         2 |
| W8_10_-1_h5_NQ  |              613 |        -0.69 |         1 |
| W8_10_-1_h5_ES  |              613 |        -0.71 |         1 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| W8_20_1_h5_NQ | 0.60 | 7 | -0.47 | 4.89 | -0.78 | 0.17 | 0.49 | 0.99 | 0.58 | 0.45 | 0.99 |
| W8_20_1_h5_ES | 0.59 | 7 | -0.65 | 4.69 | -0.91 | -0.02 | 0.41 | 0.75 | 0.55 | 0.34 | 1.00 |
| W8_10_1_h5_NQ | 0.58 | 9 | 0.15 | 3.11 | -0.91 | 0.31 | 0.53 | 0.82 | 0.73 | 0.52 | 0.96 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W8_20_1_h5_NQ | 5.0 | 10% | -0.05 | 0.40 | -0.03 | 0.02 | 11 | -0.07 | 0.84 | 0.24 | -0.07 | NO |
| W8_20_1_h5_NQ | 5.0 | 20% | -0.11 | 0.76 | -0.07 | 0.02 | 24 | -0.15 | 0.84 | 0.24 | -0.07 | NO |
| W8_20_1_h5_NQ | 5.0 | 30% | -0.18 | 1.08 | -0.14 | 0.01 | 40 | -0.25 | 0.84 | 0.24 | -0.07 | NO |
| W8_20_1_h5_NQ | 5.0 | 50% | -0.35 | 1.59 | -0.32 | -0.07 | 70 | -0.49 | 0.84 | 0.24 | -0.07 | NO |
| W8_20_1_h5_ES | 4.8 | 10% | -0.06 | 0.38 | -0.05 | 0.00 | 15 | -0.09 | 0.83 | 0.31 | -0.07 | NO |
| W8_20_1_h5_ES | 4.8 | 20% | -0.14 | 0.72 | -0.11 | -0.01 | 30 | -0.19 | 0.83 | 0.31 | -0.07 | NO |
| W8_20_1_h5_ES | 4.8 | 30% | -0.23 | 1.04 | -0.18 | -0.05 | 45 | -0.31 | 0.83 | 0.31 | -0.07 | NO |
| W8_20_1_h5_ES | 4.8 | 50% | -0.43 | 1.56 | -0.35 | -0.15 | 76 | -0.57 | 0.83 | 0.31 | -0.07 | NO |
| W8_10_1_h5_NQ | 5.0 | 10% | 0.05 | 0.16 | -0.10 | 0.04 | 12 | -0.05 | 0.89 | 0.40 | -0.11 | NO |
| W8_10_1_h5_NQ | 5.0 | 20% | 0.08 | 0.29 | -0.20 | 0.07 | 24 | -0.12 | 0.89 | 0.40 | -0.11 | NO |
| W8_10_1_h5_NQ | 5.0 | 30% | 0.09 | 0.39 | -0.32 | 0.07 | 37 | -0.21 | 0.89 | 0.40 | -0.11 | NO |
| W8_10_1_h5_NQ | 5.0 | 50% | 0.05 | 0.54 | -0.58 | 0.03 | 62 | -0.44 | 0.89 | 0.40 | -0.11 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| W8_20_1_h5_NQ | 10% | -9.1 | -1.5 | 3.5 | 0.6 | -2/2 | 10/14 | NO |
| W8_20_1_h5_NQ | 20% | -18.1 | -5.5 | 6.0 | 1.2 | -6/3 | 19/27 | NO |
| W8_20_1_h5_NQ | 30% | -27.2 | -11.6 | 8.5 | 1.8 | -13/5 | 28/41 | NO |
| W8_20_1_h5_NQ | 50% | -45.3 | -23.8 | 8.0 | 3.0 | -25/3 | 45/55 | NO |
| W8_20_1_h5_ES | 10% | -10.1 | -4.6 | 2.5 | 0.5 | -5/1 | 14/15 | NO |
| W8_20_1_h5_ES | 20% | -20.2 | -10.1 | 4.6 | 1.0 | -11/1 | 25/31 | NO |
| W8_20_1_h5_ES | 30% | -30.3 | -15.5 | 6.4 | 1.5 | -16/1 | 37/46 | NO |
| W8_20_1_h5_ES | 50% | -50.4 | -29.7 | 1.6 | -2.7 | -31/-7 | 61/63 | NO |
| W8_10_1_h5_NQ | 10% | -8.2 | -1.8 | 6.2 | 11.3 | -3/8 | 10/14 | NO |
| W8_10_1_h5_NQ | 20% | -16.5 | -4.4 | 11.8 | 22.7 | -5/16 | 19/27 | NO |
| W8_10_1_h5_NQ | 30% | -24.7 | -6.9 | 17.3 | 32.5 | -8/24 | 28/40 | NO |
| W8_10_1_h5_NQ | 50% | -41.2 | -29.2 | 11.3 | 35.5 | -30/10 | 45/45 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| W8_20_1_h5_NQ | 0.02 | 4 | 0.50 | -0.02 / 0.01 | -0.11 / 0.75 / -0.08 / 0.02 | 0.16 | -0.10 / 0.65 / -0.05 / 0.03 |
| W8_20_1_h5_ES | -0.01 | 4 | 0.00 | -0.07 / -0.04 | -0.15 / 0.71 / -0.11 / -0.02 | -0.06 | -0.14 / 0.60 / -0.08 / -0.00 |
| W8_10_1_h5_NQ | 0.07 | 4 | 0.25 | -0.10 / 0.00 | 0.07 / 0.29 / -0.21 / 0.07 | 0.31 | 0.07 / 0.33 / -0.18 / 0.07 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| W8_20_1_h5_NQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | PASS (0.24) | NO |
| W8_20_1_h5_ES | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | fail (0.31) | NO |
| W8_10_1_h5_NQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.25) | fail | fail (0.40) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W8_20_1_h5_NQ | clean | -0.47 | -445,501 | -181,637 | -138,845 | -122,887 | 804,501 | -0.62 | -0.55 | 53 | 1.28 | -115,219 | -98,290 | 359,049 | 3.33 | 47 | 1.46 | -81,874 | -78,736 | 280,110 |
| W8_20_1_h5_NQ | H1 | 4.89 | 925,472 | -37,096 | -35,080 | -34,196 | 125,054 | 17.35 | 7.40 | 29 | 3.90 | -79,681 | -69,428 | 147,235 | 5.92 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| W8_20_1_h5_NQ | H2 | -0.78 | -228,489 | -149,323 | -120,913 | -102,858 | 448,425 | -1.00 | -0.51 | 49 | 2.12 | -106,801 | -95,987 | 214,872 | 3.22 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| W8_20_1_h5_NQ | all | 0.17 | 251,483 | -181,637 | -133,531 | -114,212 | 804,501 | 0.24 | 0.31 | 49 | 1.86 | -115,219 | -95,997 | 359,049 | 7.69 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| W8_20_1_h5_ES | clean | -0.65 | -624,698 | -213,151 | -159,754 | -128,714 | 1,126,114 | -0.82 | -0.55 | 49 | 1.23 | -119,877 | -101,265 | 359,816 | 3.18 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| W8_20_1_h5_ES | H1 | 4.69 | 820,264 | -40,931 | -38,053 | -35,608 | 122,058 | 15.72 | 6.72 | 25 | 3.87 | -72,102 | -65,032 | 146,450 | 5.73 | 29 | 2.83 | -78,287 | -77,610 | 151,713 |
| W8_20_1_h5_ES | H2 | -0.91 | -219,120 | -90,626 | -86,598 | -83,798 | 366,249 | -1.18 | -0.60 | 51 | 2.08 | -104,424 | -94,423 | 205,103 | 3.39 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| W8_20_1_h5_ES | all | -0.02 | -23,554 | -213,151 | -139,743 | -111,690 | 1,126,114 | -0.02 | -0.02 | 46 | 1.81 | -119,877 | -97,660 | 359,816 | 7.44 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |
| W8_10_1_h5_NQ | clean | 0.15 | 146,159 | -279,639 | -149,695 | -126,791 | 568,008 | 0.20 | 0.26 | 44 | 1.55 | -112,801 | -83,460 | 268,843 | 5.11 | 46 | 1.46 | -81,874 | -78,736 | 280,110 |
| W8_10_1_h5_NQ | H1 | 3.11 | 592,017 | -68,416 | -63,844 | -62,219 | 232,148 | 6.18 | 2.55 | 32 | 3.22 | -79,686 | -69,413 | 182,741 | 4.22 | 46 | 2.83 | -78,287 | -77,610 | 151,713 |
| W8_10_1_h5_NQ | H2 | -0.91 | -266,157 | -135,978 | -125,609 | -105,146 | 491,697 | -1.16 | -0.54 | 49 | 1.94 | -106,683 | -101,000 | 214,883 | 3.17 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| W8_10_1_h5_NQ | all | 0.31 | 472,019 | -279,639 | -140,171 | -118,203 | 571,784 | 0.43 | 0.83 | 43 | 1.93 | -112,801 | -89,061 | 268,843 | 10.51 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE W8
