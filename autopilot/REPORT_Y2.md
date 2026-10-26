# REPORT Y2

**NO - vol-contraction momentum (ATR5/ATR20 <= 0.6/0.8): best selected cell Y2_0.6_20_h5_SCR: standalone Sharpe 2013-22 0.34, pair window -0.27, own-null rank pair window 0.32; additive uplift at 20% clean/H1/H2 +0.05/-0.32/-0.16, bootstrap lo -0.23; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea Y2: trade the 20/60-day trend direction when ATR5/ATR20 <= r, hold 3/5, ALL26 or SCR = 16 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 16 cells; eligible 3
| cell               |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------|-----------------:|-------------:|----------:|
| Y2_0.8_20_h5_SCR   |             2903 |         0.36 |         5 |
| Y2_0.6_20_h5_ALL26 |              510 |         0.34 |         7 |
| Y2_0.6_20_h5_SCR   |              366 |         0.34 |         9 |
| Y2_0.6_20_h3_ALL26 |              606 |         0.32 |         5 |
| Y2_0.6_20_h3_SCR   |              439 |         0.3  |         6 |
| Y2_0.6_60_h5_ALL26 |              506 |         0.13 |         5 |
| Y2_0.8_60_h5_SCR   |             2871 |         0.04 |         8 |
| Y2_0.6_60_h5_SCR   |              362 |        -0.04 |         6 |
| Y2_0.8_20_h5_ALL26 |             4504 |        -0.07 |         4 |
| Y2_0.8_20_h3_SCR   |             3825 |        -0.12 |         4 |

Multiplicity: 16 cells x 5% = 0.8 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Y2_0.6_20_h5_ALL26 | 0.34 | 7 | 0.14 | -1.17 | -1.20 | -0.29 | 0.22 | 0.75 | 0.40 | 0.34 | 0.95 |
| Y2_0.6_20_h5_SCR | 0.34 | 9 | 0.29 | -1.22 | -1.11 | -0.27 | 0.21 | 0.88 | 0.32 | 0.36 | 0.93 |
| Y2_0.8_60_h5_SCR | 0.04 | 8 | -0.27 | 0.15 | -2.16 | -0.66 | -0.20 | 0.67 | 0.15 | 0.23 | 0.79 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y2_0.6_20_h5_ALL26 | 4.7 | 10% | 0.01 | -0.14 | -0.06 | -0.03 | 0 | -0.12 | 0.67 | -0.01 | -0.03 | NO |
| Y2_0.6_20_h5_ALL26 | 4.7 | 20% | 0.00 | -0.30 | -0.13 | -0.07 | 13 | -0.26 | 0.67 | -0.01 | -0.03 | NO |
| Y2_0.6_20_h5_ALL26 | 4.7 | 30% | -0.02 | -0.49 | -0.21 | -0.13 | 31 | -0.40 | 0.67 | -0.01 | -0.03 | NO |
| Y2_0.6_20_h5_ALL26 | 4.7 | 50% | -0.08 | -0.89 | -0.39 | -0.27 | 66 | -0.70 | 0.67 | -0.01 | -0.03 | NO |
| Y2_0.6_20_h5_SCR | 5.4 | 10% | 0.03 | -0.15 | -0.07 | -0.02 | 1 | -0.11 | 0.84 | 0.03 | -0.08 | NO |
| Y2_0.6_20_h5_SCR | 5.4 | 20% | 0.05 | -0.32 | -0.16 | -0.05 | 8 | -0.23 | 0.84 | 0.03 | -0.08 | NO |
| Y2_0.6_20_h5_SCR | 5.4 | 30% | 0.06 | -0.52 | -0.25 | -0.09 | 16 | -0.36 | 0.84 | 0.03 | -0.08 | NO |
| Y2_0.6_20_h5_SCR | 5.4 | 50% | 0.04 | -0.95 | -0.47 | -0.22 | 67 | -0.64 | 0.84 | 0.03 | -0.08 | NO |
| Y2_0.8_60_h5_SCR | 1.9 | 10% | -0.02 | -0.05 | -0.20 | -0.06 | 15 | -0.15 | 0.72 | 0.16 | -0.05 | NO |
| Y2_0.8_60_h5_SCR | 1.9 | 20% | -0.06 | -0.11 | -0.42 | -0.14 | 33 | -0.32 | 0.72 | 0.16 | -0.05 | NO |
| Y2_0.8_60_h5_SCR | 1.9 | 30% | -0.10 | -0.19 | -0.64 | -0.22 | 51 | -0.50 | 0.72 | 0.16 | -0.05 | NO |
| Y2_0.8_60_h5_SCR | 1.9 | 50% | -0.21 | -0.37 | -1.10 | -0.42 | 87 | -0.85 | 0.72 | 0.16 | -0.05 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| Y2_0.6_20_h5_ALL26 | 10% | -11.5 | 9.5 | 7.8 | -1.9 | 9/8 | 10/10 | NO |
| Y2_0.6_20_h5_ALL26 | 20% | -22.9 | 2.3 | 13.3 | -3.8 | 2/12 | 20/20 | NO |
| Y2_0.6_20_h5_ALL26 | 30% | -34.4 | -7.4 | 12.3 | -5.7 | -8/12 | -2/13 | NO |
| Y2_0.6_20_h5_ALL26 | 50% | -57.3 | -63.7 | -8.5 | -9.7 | -46/-5 | -73/-12 | NO |
| Y2_0.6_20_h5_SCR | 10% | -11.3 | 8.6 | 7.7 | 6.1 | 8/8 | 10/10 | NO |
| Y2_0.6_20_h5_SCR | 20% | -22.6 | 10.4 | 14.3 | 12.1 | 10/15 | 20/20 | NO |
| Y2_0.6_20_h5_SCR | 30% | -33.8 | 0.0 | 15.3 | 18.2 | 12/20 | -5/12 | NO |
| Y2_0.6_20_h5_SCR | 50% | -56.4 | -68.7 | -5.2 | 3.4 | -9/7 | -78/-15 | NO |
| Y2_0.8_60_h5_SCR | 10% | -13.3 | -5.0 | 2.3 | 1.8 | -2/2 | 10/13 | NO |
| Y2_0.8_60_h5_SCR | 20% | -26.6 | -13.5 | 3.6 | 3.6 | -6/3 | 20/26 | NO |
| Y2_0.8_60_h5_SCR | 30% | -39.8 | -21.9 | 3.7 | 5.5 | -10/4 | 30/39 | NO |
| Y2_0.8_60_h5_SCR | 50% | -66.4 | -38.9 | -6.7 | 9.1 | -18/-5 | 30/33 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| Y2_0.6_20_h5_ALL26 | -0.07 | 6 | 0.00 | -0.22 / -0.06 | -0.01 / -0.32 / -0.14 / -0.09 | -0.36 | 0.01 / -0.22 / -0.11 / -0.06 |
| Y2_0.6_20_h5_SCR | -0.05 | 6 | 0.00 | -0.11 / -0.06 | 0.04 / -0.33 / -0.16 / -0.06 | -0.31 | 0.05 / -0.24 / -0.13 / -0.04 |
| Y2_0.8_60_h5_SCR | -0.14 | 6 | 0.00 | -0.33 / -0.17 | -0.08 / -0.13 / -0.43 / -0.16 | -0.77 | -0.05 / -0.02 / -0.39 / -0.12 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| Y2_0.6_20_h5_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.01) | NO |
| Y2_0.6_20_h5_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.03) | NO |
| Y2_0.8_60_h5_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.16) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y2_0.6_20_h5_ALL26 | clean | 0.14 | 122,526 | -226,320 | -156,292 | -110,267 | 668,207 | 0.20 | 0.18 | 24 | 1.44 | -108,041 | -88,624 | 380,020 | 3.60 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y2_0.6_20_h5_ALL26 | H1 | -1.17 | -265,684 | -272,660 | -162,070 | -121,226 | 333,338 | -1.27 | -0.80 | 32 | 2.34 | -79,250 | -78,768 | 162,563 | 3.16 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y2_0.6_20_h5_ALL26 | H2 | -1.20 | -248,690 | -151,640 | -140,410 | -97,517 | 331,353 | -1.34 | -0.75 | 24 | 2.05 | -92,374 | -87,672 | 222,239 | 3.09 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y2_0.6_20_h5_ALL26 | all | -0.29 | -391,847 | -272,660 | -165,692 | -113,464 | 971,325 | -0.39 | -0.40 | 26 | 1.73 | -108,041 | -87,735 | 380,020 | 6.76 | 45 | 1.86 | -82,524 | -79,220 | 280,110 |
| Y2_0.6_20_h5_SCR | clean | 0.29 | 229,620 | -207,682 | -141,160 | -98,358 | 409,907 | 0.41 | 0.56 | 21 | 1.52 | -95,463 | -85,614 | 313,250 | 4.47 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y2_0.6_20_h5_SCR | H1 | -1.22 | -290,801 | -280,974 | -170,347 | -128,853 | 371,055 | -1.34 | -0.78 | 32 | 2.30 | -81,744 | -80,016 | 172,053 | 2.94 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y2_0.6_20_h5_SCR | H2 | -1.11 | -282,492 | -197,569 | -173,712 | -118,539 | 378,387 | -1.24 | -0.75 | 24 | 2.01 | -94,768 | -89,335 | 223,009 | 3.03 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y2_0.6_20_h5_SCR | all | -0.27 | -343,674 | -280,974 | -163,929 | -112,370 | 887,948 | -0.34 | -0.39 | 24 | 1.76 | -95,463 | -86,563 | 313,250 | 8.24 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |
| Y2_0.8_60_h5_SCR | clean | -0.27 | -226,272 | -154,704 | -131,447 | -107,111 | 536,431 | -0.38 | -0.42 | 47 | 1.36 | -113,840 | -98,870 | 348,837 | 3.62 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y2_0.8_60_h5_SCR | H1 | 0.15 | 29,088 | -112,775 | -109,854 | -95,555 | 238,606 | 0.21 | 0.12 | 54 | 2.64 | -78,337 | -70,569 | 149,840 | 4.02 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y2_0.8_60_h5_SCR | H2 | -2.16 | -683,937 | -149,539 | -138,394 | -125,214 | 946,474 | -2.42 | -0.72 | 65 | 1.62 | -124,515 | -106,941 | 206,120 | 2.70 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y2_0.8_60_h5_SCR | all | -0.66 | -881,121 | -154,704 | -131,089 | -115,180 | 1,088,120 | -0.86 | -0.81 | 52 | 1.63 | -124,515 | -99,239 | 348,837 | 6.94 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE Y2
