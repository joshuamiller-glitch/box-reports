# REPORT S5

**NO - price-volume divergence (low-volume breakouts fail): best selected cell S5_20_1.0_h5_SCR: standalone Sharpe 2013-22 0.20, pair window 0.09, own-null rank pair window 0.60; additive uplift at 20% clean/H1/H2 +0.14/-0.48/-0.14, bootstrap lo -0.23; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea S5: new 20/60-day extreme on volume < 0.8/1.0 x mean -> fade, hold 3/5 = 16 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 16 cells; eligible 3
| cell               |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------|-----------------:|-------------:|----------:|
| S5_20_0.8_h5_SCR   |              806 |         0.26 |         5 |
| S5_60_0.8_h3_SCR   |              516 |         0.25 |         7 |
| S5_20_0.8_h3_SCR   |              840 |         0.24 |         7 |
| S5_60_0.8_h5_SCR   |              493 |         0.24 |         5 |
| S5_20_1.0_h5_SCR   |             1098 |         0.2  |         7 |
| S5_60_1.0_h5_SCR   |              661 |         0.18 |         5 |
| S5_60_1.0_h3_SCR   |              720 |         0.14 |         6 |
| S5_20_1.0_h3_SCR   |             1189 |         0.1  |         6 |
| S5_20_0.8_h5_ALL26 |             1143 |        -0.1  |         4 |
| S5_20_0.8_h3_ALL26 |             1184 |        -0.14 |         3 |

Multiplicity: 16 cells x 5% = 0.8 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S5_60_0.8_h3_SCR | 0.25 | 7 | 0.68 | -1.87 | 0.46 | 0.25 | 0.21 | 0.74 | 0.69 | 0.40 | 0.88 |
| S5_20_0.8_h3_SCR | 0.24 | 7 | 0.43 | -2.06 | 0.97 | 0.13 | 0.17 | 0.79 | 0.70 | 0.38 | 0.84 |
| S5_20_1.0_h5_SCR | 0.20 | 7 | 0.83 | -1.42 | -0.61 | 0.09 | 0.10 | 0.80 | 0.60 | 0.36 | 0.86 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S5_60_0.8_h3_SCR | 5.0 | 10% | 0.08 | -0.45 | 0.07 | -0.00 | 0 | -0.14 | 0.23 | -0.15 | 0.05 | NO |
| S5_60_0.8_h3_SCR | 5.0 | 20% | 0.10 | -0.93 | 0.08 | -0.05 | 10 | -0.31 | 0.23 | -0.15 | 0.05 | NO |
| S5_60_0.8_h3_SCR | 5.0 | 30% | 0.09 | -1.38 | 0.06 | -0.14 | 58 | -0.51 | 0.23 | -0.15 | 0.05 | NO |
| S5_60_0.8_h3_SCR | 5.0 | 50% | 0.01 | -2.12 | -0.09 | -0.35 | 154 | -0.90 | 0.23 | -0.15 | 0.05 | NO |
| S5_20_0.8_h3_SCR | 4.0 | 10% | 0.05 | -0.39 | 0.12 | -0.00 | 6 | -0.11 | 0.49 | 0.08 | 0.00 | NO |
| S5_20_0.8_h3_SCR | 4.0 | 20% | 0.05 | -0.81 | 0.20 | -0.04 | 12 | -0.26 | 0.49 | 0.08 | 0.00 | NO |
| S5_20_0.8_h3_SCR | 4.0 | 30% | 0.03 | -1.23 | 0.26 | -0.11 | 29 | -0.43 | 0.49 | 0.08 | 0.00 | NO |
| S5_20_0.8_h3_SCR | 4.0 | 50% | -0.06 | -1.97 | 0.28 | -0.30 | 105 | -0.78 | 0.49 | 0.08 | 0.00 | NO |
| S5_20_1.0_h5_SCR | 2.8 | 10% | 0.08 | -0.23 | -0.05 | 0.00 | 7 | -0.10 | 0.64 | 0.01 | -0.03 | NO |
| S5_20_1.0_h5_SCR | 2.8 | 20% | 0.14 | -0.48 | -0.14 | -0.02 | 20 | -0.23 | 0.64 | 0.01 | -0.03 | NO |
| S5_20_1.0_h5_SCR | 2.8 | 30% | 0.17 | -0.76 | -0.26 | -0.06 | 34 | -0.38 | 0.64 | 0.01 | -0.03 | NO |
| S5_20_1.0_h5_SCR | 2.8 | 50% | 0.20 | -1.28 | -0.58 | -0.20 | 101 | -0.72 | 0.64 | 0.01 | -0.03 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| S5_60_0.8_h3_SCR | 10% | -7.6 | 9.3 | 9.1 | 14.5 | 10/10 | 6/7 | NO |
| S5_60_0.8_h3_SCR | 20% | -15.3 | -7.2 | 13.6 | 20.7 | 20/20 | -13/-3 | NO |
| S5_60_0.8_h3_SCR | 30% | -22.9 | -53.8 | 3.2 | 5.3 | 5/22 | -62/-42 | NO |
| S5_60_0.8_h3_SCR | 50% | -38.1 | -146.9 | -37.1 | -56.2 | -94/11 | -160/-127 | NO |
| S5_20_0.8_h3_SCR | 10% | -8.9 | 4.1 | 8.4 | 14.2 | 12/10 | 7/8 | NO |
| S5_20_0.8_h3_SCR | 20% | -17.9 | 8.2 | 14.3 | 21.7 | 19/19 | 8/9 | NO |
| S5_20_0.8_h3_SCR | 30% | -26.8 | -24.5 | 10.5 | 21.8 | 24/27 | -31/-27 | NO |
| S5_20_0.8_h3_SCR | 50% | -44.7 | -98.1 | -13.8 | -23.4 | -49/18 | -109/-101 | NO |
| S5_20_1.0_h5_SCR | 10% | -9.4 | 2.6 | 8.2 | 15.1 | 9/10 | -3/9 | NO |
| S5_20_1.0_h5_SCR | 20% | -18.8 | -1.6 | 13.9 | 24.3 | 12/19 | -7/2 | NO |
| S5_20_1.0_h5_SCR | 30% | -28.2 | -18.2 | 10.0 | 19.1 | 15/27 | -25/-19 | NO |
| S5_20_1.0_h5_SCR | 50% | -46.9 | -141.0 | -10.7 | -44.6 | 20/34 | -98/-60 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| S5_60_0.8_h3_SCR | -0.05 | 6 | 0.00 | -0.14 / -0.06 | 0.10 / -0.94 / 0.08 / -0.06 | 0.22 | 0.11 / -0.66 / 0.09 / -0.03 |
| S5_20_0.8_h3_SCR | -0.04 | 6 | 0.00 | -0.14 / -0.05 | 0.05 / -0.82 / 0.20 / -0.05 | 0.10 | 0.06 / -0.60 / 0.20 / -0.03 |
| S5_20_1.0_h5_SCR | -0.02 | 6 | 0.00 | -0.10 / -0.03 | 0.13 / -0.49 / -0.15 / -0.03 | 0.05 | 0.14 / -0.37 / -0.15 / -0.02 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| S5_60_0.8_h3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.15) | NO |
| S5_20_0.8_h3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.08) | NO |
| S5_20_1.0_h5_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.01) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S5_60_0.8_h3_SCR | clean | 0.68 | 1,161,513 | -360,329 | -145,594 | -99,751 | 493,378 | 1.81 | 2.35 | 24 | 1.55 | -82,410 | -79,585 | 287,487 | 5.84 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| S5_60_0.8_h3_SCR | H1 | -1.87 | -754,703 | -396,001 | -340,772 | -255,188 | 1,035,458 | -2.02 | -0.73 | 36 | 1.45 | -130,368 | -113,625 | 262,941 | 1.40 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| S5_60_0.8_h3_SCR | H2 | 0.46 | 229,744 | -386,469 | -220,269 | -126,249 | 399,923 | 0.69 | 0.57 | 19 | 2.32 | -93,367 | -86,510 | 217,809 | 3.81 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| S5_60_0.8_h3_SCR | all | 0.25 | 636,555 | -396,001 | -218,960 | -141,598 | 1,208,353 | 0.45 | 0.53 | 25 | 1.71 | -130,368 | -90,423 | 287,487 | 10.00 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| S5_20_0.8_h3_SCR | clean | 0.43 | 625,958 | -287,058 | -157,091 | -109,906 | 482,127 | 0.97 | 1.30 | 32 | 1.49 | -84,606 | -79,570 | 283,497 | 5.35 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| S5_20_0.8_h3_SCR | H1 | -2.06 | -713,721 | -315,477 | -301,114 | -223,055 | 980,656 | -2.19 | -0.73 | 54 | 1.59 | -106,210 | -101,728 | 244,357 | 1.55 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| S5_20_0.8_h3_SCR | H2 | 0.97 | 373,071 | -186,717 | -121,358 | -83,663 | 389,833 | 2.10 | 0.96 | 27 | 2.52 | -97,184 | -93,626 | 219,067 | 3.99 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| S5_20_0.8_h3_SCR | all | 0.13 | 285,308 | -315,477 | -192,388 | -128,249 | 980,656 | 0.24 | 0.29 | 35 | 1.74 | -106,210 | -89,121 | 283,497 | 9.77 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| S5_20_1.0_h5_SCR | clean | 0.83 | 834,873 | -150,304 | -107,403 | -80,210 | 333,751 | 1.95 | 2.50 | 45 | 1.63 | -93,061 | -80,679 | 272,387 | 5.80 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| S5_20_1.0_h5_SCR | H1 | -1.42 | -391,351 | -298,020 | -204,688 | -159,238 | 811,353 | -1.57 | -0.48 | 50 | 2.07 | -110,339 | -105,656 | 231,220 | 2.06 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| S5_20_1.0_h5_SCR | H2 | -0.61 | -278,890 | -463,156 | -301,741 | -180,084 | 502,071 | -0.67 | -0.56 | 43 | 2.00 | -91,132 | -87,894 | 215,560 | 3.14 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| S5_20_1.0_h5_SCR | all | 0.09 | 164,633 | -463,156 | -175,708 | -121,470 | 949,145 | 0.14 | 0.17 | 46 | 1.79 | -110,339 | -88,185 | 272,387 | 10.04 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE S5
