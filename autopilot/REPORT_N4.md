# REPORT N4

**NO - risk-driver lead (6J, 6A, HG) -> ES+NQ: best selected cell N4_HG_5_1_h5_EQ2: standalone Sharpe 2013-22 -0.44, pair window 0.49, own-null rank pair window 0.80; additive uplift at 20% clean/H1/H2 +0.20/-0.31/-0.03, bootstrap lo -0.09; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea N4: 5/10-day driver move, both signs, hold 5, 12 cells; clean-only selection.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 4
| cell               |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------|-----------------:|-------------:|----------:|
| N4_HG_5_1_h5_EQ2   |       1000000000 |         1.18 |        10 |
| N4_6J_10_1_h5_EQ2  |       1000000000 |         0.52 |        10 |
| N4_HG_10_1_h5_EQ2  |                0 |         0.48 |         0 |
| N4_6A_5_-1_h5_EQ2  |       1000000000 |         0.35 |        10 |
| N4_6A_10_-1_h5_EQ2 |       1000000000 |         0.23 |        10 |
| N4_6J_5_1_h5_EQ2   |                0 |         0.15 |         0 |
| N4_6J_5_-1_h5_EQ2  |                0 |        -0.22 |         0 |
| N4_6A_10_1_h5_EQ2  |                0 |        -0.29 |         0 |
| N4_6A_5_1_h5_EQ2   |                0 |        -0.42 |         0 |
| N4_HG_10_-1_h5_EQ2 |                0 |        -0.54 |         0 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| N4_HG_5_1_h5_EQ2 | -0.44 | 3 | 1.18 | -1.75 | -0.01 | 0.49 | -0.27 | 0.91 | 0.80 | 0.38 | 0.15 |
| N4_6J_10_1_h5_EQ2 | 0.27 | 8 | 0.52 | -0.16 | -0.06 | 0.31 | 0.27 | 0.80 | 0.73 | 0.40 | 0.89 |
| N4_6A_5_-1_h5_EQ2 | -0.13 | 4 | 0.35 | 0.33 | 0.51 | 0.38 | -0.03 | 1.01 | 0.67 | 0.49 | 0.45 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N4_HG_5_1_h5_EQ2 | 2.3 | 10% | 0.11 | -0.14 | -0.01 | 0.04 | 11 | -0.04 | 0.65 | 0.19 | -0.03 | NO |
| N4_HG_5_1_h5_EQ2 | 2.3 | 20% | 0.20 | -0.31 | -0.03 | 0.07 | 23 | -0.09 | 0.65 | 0.19 | -0.03 | NO |
| N4_HG_5_1_h5_EQ2 | 2.3 | 30% | 0.27 | -0.50 | -0.07 | 0.08 | 36 | -0.16 | 0.65 | 0.19 | -0.03 | NO |
| N4_HG_5_1_h5_EQ2 | 2.3 | 50% | 0.36 | -0.95 | -0.18 | 0.05 | 60 | -0.34 | 0.65 | 0.19 | -0.03 | NO |
| N4_6J_10_1_h5_EQ2 | 2.4 | 10% | 0.03 | -0.09 | -0.09 | -0.01 | 12 | -0.09 | 0.01 | 0.20 | 0.18 | NO |
| N4_6J_10_1_h5_EQ2 | 2.4 | 20% | 0.04 | -0.20 | -0.18 | -0.03 | 24 | -0.20 | 0.01 | 0.20 | 0.18 | NO |
| N4_6J_10_1_h5_EQ2 | 2.4 | 30% | 0.04 | -0.31 | -0.27 | -0.07 | 39 | -0.31 | 0.01 | 0.20 | 0.18 | NO |
| N4_6J_10_1_h5_EQ2 | 2.4 | 50% | 0.02 | -0.54 | -0.44 | -0.16 | 69 | -0.54 | 0.01 | 0.20 | 0.18 | NO |
| N4_6A_5_-1_h5_EQ2 | 2.4 | 10% | 0.02 | -0.04 | 0.08 | 0.03 | 13 | -0.06 | 0.45 | -0.01 | 0.01 | NO |
| N4_6A_5_-1_h5_EQ2 | 2.4 | 20% | 0.02 | -0.10 | 0.14 | 0.03 | 27 | -0.13 | 0.45 | -0.01 | 0.01 | NO |
| N4_6A_5_-1_h5_EQ2 | 2.4 | 30% | 0.02 | -0.16 | 0.20 | 0.03 | 41 | -0.20 | 0.45 | -0.01 | 0.01 | NO |
| N4_6A_5_-1_h5_EQ2 | 2.4 | 50% | -0.03 | -0.32 | 0.28 | -0.02 | 69 | -0.38 | 0.45 | -0.01 | 0.01 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| N4_HG_5_1_h5_EQ2 | 10% | -7.4 | -1.4 | 6.1 | 8.8 | -2/5 | 10/13 | NO |
| N4_HG_5_1_h5_EQ2 | 20% | -14.8 | -3.7 | 11.1 | 17.7 | -4/9 | 18/26 | NO |
| N4_HG_5_1_h5_EQ2 | 30% | -22.3 | -5.9 | 15.9 | 26.5 | -7/13 | 27/39 | NO |
| N4_HG_5_1_h5_EQ2 | 50% | -37.1 | -10.3 | 24.4 | 39.8 | -11/21 | 38/40 | NO |
| N4_6J_10_1_h5_EQ2 | 10% | -8.4 | -1.9 | 2.9 | 6.4 | -3/3 | 2/5 | NO |
| N4_6J_10_1_h5_EQ2 | 20% | -16.8 | -5.1 | 4.9 | 12.8 | -6/4 | 4/10 | NO |
| N4_6J_10_1_h5_EQ2 | 30% | -25.2 | -11.0 | 6.7 | 19.2 | -12/6 | 6/15 | NO |
| N4_6J_10_1_h5_EQ2 | 50% | -42.0 | -22.7 | 6.1 | 13.2 | -24/3 | 9/25 | NO |
| N4_6A_5_-1_h5_EQ2 | 10% | -8.1 | -3.2 | 3.9 | 3.2 | -4/3 | -3/6 | NO |
| N4_6A_5_-1_h5_EQ2 | 20% | -16.3 | -7.1 | 6.5 | 6.4 | -8/5 | -9/12 | NO |
| N4_6A_5_-1_h5_EQ2 | 30% | -24.4 | -11.1 | 8.8 | 9.2 | -12/6 | -14/17 | NO |
| N4_6A_5_-1_h5_EQ2 | 50% | -40.7 | -20.2 | 8.7 | -3.6 | -21/6 | -24/16 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| N4_HG_5_1_h5_EQ2 | 0.07 | 4 | 0.00 | -0.02 / 0.01 | 0.19 / -0.31 / -0.03 / 0.07 | 0.46 | 0.19 / -0.27 / -0.06 / 0.06 |
| N4_6J_10_1_h5_EQ2 | -0.03 | 4 | 0.00 | -0.17 / -0.12 | 0.04 / -0.20 / -0.18 / -0.04 | 0.28 | 0.05 / -0.10 / -0.17 / -0.02 |
| N4_6A_5_-1_h5_EQ2 | 0.03 | 6 | 0.00 | -0.11 / -0.05 | 0.02 / -0.10 / 0.14 / 0.03 | 0.35 | 0.04 / -0.05 / 0.14 / 0.04 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| N4_HG_5_1_h5_EQ2 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.19) | NO |
| N4_6J_10_1_h5_EQ2 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.20) | NO |
| N4_6A_5_-1_h5_EQ2 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.01) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N4_HG_5_1_h5_EQ2 | clean | 1.18 | 1,071,374 | -137,254 | -104,797 | -91,862 | 260,664 | 1.99 | 4.11 | 41 | 1.73 | -111,933 | -91,877 | 289,974 | 5.69 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| N4_HG_5_1_h5_EQ2 | H1 | -1.75 | -376,872 | -169,713 | -138,247 | -122,570 | 464,957 | -1.95 | -0.81 | 57 | 2.33 | -80,575 | -70,247 | 179,451 | 2.68 | 46 | 2.83 | -78,287 | -77,610 | 151,713 |
| N4_HG_5_1_h5_EQ2 | H2 | -0.01 | -2,895 | -128,176 | -109,961 | -89,799 | 416,526 | -0.01 | -0.01 | 54 | 2.19 | -90,036 | -89,150 | 227,419 | 3.34 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| N4_HG_5_1_h5_EQ2 | all | 0.49 | 691,607 | -169,713 | -121,003 | -101,893 | 537,391 | 0.73 | 1.29 | 46 | 1.93 | -111,933 | -90,015 | 289,974 | 9.98 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| N4_6J_10_1_h5_EQ2 | clean | 0.52 | 474,346 | -125,580 | -108,699 | -96,308 | 470,152 | 0.82 | 1.01 | 46 | 1.50 | -114,682 | -97,247 | 310,339 | 4.74 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| N4_6J_10_1_h5_EQ2 | H1 | -0.16 | -30,307 | -83,833 | -75,273 | -71,471 | 206,895 | -0.24 | -0.15 | 50 | 2.52 | -97,447 | -89,080 | 177,445 | 3.30 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| N4_6J_10_1_h5_EQ2 | H2 | -0.06 | -16,753 | -109,438 | -101,476 | -87,666 | 268,047 | -0.09 | -0.06 | 51 | 2.00 | -107,708 | -97,473 | 214,757 | 3.52 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| N4_6J_10_1_h5_EQ2 | all | 0.31 | 427,286 | -136,062 | -110,134 | -95,414 | 508,993 | 0.47 | 0.84 | 47 | 1.79 | -114,682 | -97,344 | 310,339 | 9.06 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| N4_6A_5_-1_h5_EQ2 | clean | 0.35 | 322,341 | -158,414 | -122,138 | -102,943 | 385,014 | 0.54 | 0.84 | 52 | 1.48 | -116,226 | -97,142 | 337,193 | 4.23 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| N4_6A_5_-1_h5_EQ2 | H1 | 0.33 | 61,000 | -117,805 | -91,669 | -81,659 | 294,690 | 0.49 | 0.21 | 57 | 2.66 | -112,274 | -87,492 | 176,358 | 3.47 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| N4_6A_5_-1_h5_EQ2 | H2 | 0.51 | 117,410 | -121,293 | -110,084 | -92,686 | 261,594 | 0.68 | 0.45 | 41 | 2.46 | -83,807 | -80,595 | 209,944 | 3.79 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| N4_6A_5_-1_h5_EQ2 | all | 0.38 | 500,750 | -158,414 | -118,978 | -99,985 | 385,014 | 0.56 | 1.30 | 50 | 1.89 | -116,226 | -95,542 | 337,193 | 8.41 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE N4
