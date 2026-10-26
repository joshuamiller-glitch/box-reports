# REPORT Y4

**NO - short Donchian (10/20/40) close breakout: best selected cell Y4_40_h5_SCR: standalone Sharpe 2013-22 0.26, pair window 0.05, own-null rank pair window 0.68; additive uplift at 20% clean/H1/H2 -0.01/-0.20/+0.02, bootstrap lo -0.20; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea Y4: close beyond the previous N-day extreme, hold 3/5, ALL26 or SCR = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 4
| cell           |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:---------------|-----------------:|-------------:|----------:|
| Y4_20_h3_SCR   |             4086 |         0.34 |         8 |
| Y4_40_h3_SCR   |             2853 |         0.3  |         8 |
| Y4_40_h5_SCR   |             2345 |         0.26 |         7 |
| Y4_20_h5_SCR   |             3331 |         0.16 |         7 |
| Y4_40_h3_ALL26 |             4339 |         0.08 |         6 |
| Y4_40_h5_ALL26 |             3586 |         0.07 |         5 |
| Y4_10_h5_SCR   |             4532 |         0.05 |         5 |
| Y4_20_h5_ALL26 |             5144 |         0    |         5 |
| Y4_20_h3_ALL26 |             6279 |        -0.02 |         6 |
| Y4_10_h5_ALL26 |             7057 |        -0.17 |         5 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Y4_20_h3_SCR | 0.34 | 8 | -0.27 | -2.53 | -0.67 | -0.80 | 0.01 | 0.70 | 0.11 | 0.19 | 0.97 |
| Y4_40_h3_SCR | 0.30 | 8 | -0.15 | -1.39 | -0.50 | -0.47 | 0.05 | 0.66 | 0.30 | 0.26 | 0.96 |
| Y4_40_h5_SCR | 0.26 | 7 | -0.08 | -0.62 | 0.65 | 0.05 | 0.19 | 0.68 | 0.68 | 0.30 | 0.92 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y4_20_h3_SCR | 1.8 | 10% | -0.01 | -0.29 | -0.16 | -0.08 | 4 | -0.17 | 0.89 | -0.50 | -0.09 | NO |
| Y4_20_h3_SCR | 1.8 | 20% | -0.02 | -0.63 | -0.34 | -0.18 | 14 | -0.37 | 0.89 | -0.50 | -0.09 | NO |
| Y4_20_h3_SCR | 1.8 | 30% | -0.06 | -1.01 | -0.52 | -0.29 | 24 | -0.57 | 0.89 | -0.50 | -0.09 | NO |
| Y4_20_h3_SCR | 1.8 | 50% | -0.15 | -1.79 | -0.85 | -0.54 | 45 | -1.00 | 0.89 | -0.50 | -0.09 | NO |
| Y4_40_h3_SCR | 2.1 | 10% | 0.00 | -0.18 | -0.12 | -0.05 | 4 | -0.15 | 0.89 | -0.57 | -0.09 | NO |
| Y4_40_h3_SCR | 2.1 | 20% | -0.01 | -0.43 | -0.28 | -0.12 | 15 | -0.33 | 0.89 | -0.57 | -0.09 | NO |
| Y4_40_h3_SCR | 2.1 | 30% | -0.04 | -0.70 | -0.45 | -0.22 | 25 | -0.52 | 0.89 | -0.57 | -0.09 | NO |
| Y4_40_h3_SCR | 2.1 | 50% | -0.14 | -1.29 | -0.79 | -0.45 | 50 | -0.93 | 0.89 | -0.57 | -0.09 | NO |
| Y4_40_h5_SCR | 1.7 | 10% | 0.00 | -0.09 | 0.03 | 0.00 | 5 | -0.09 | 0.67 | -0.42 | -0.04 | NO |
| Y4_40_h5_SCR | 1.7 | 20% | -0.01 | -0.20 | 0.02 | -0.02 | 15 | -0.20 | 0.67 | -0.42 | -0.04 | NO |
| Y4_40_h5_SCR | 1.7 | 30% | -0.03 | -0.35 | -0.02 | -0.06 | 25 | -0.32 | 0.67 | -0.42 | -0.04 | NO |
| Y4_40_h5_SCR | 1.7 | 50% | -0.12 | -0.68 | -0.14 | -0.18 | 46 | -0.60 | 0.67 | -0.42 | -0.04 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| Y4_20_h3_SCR | 10% | -14.6 | 5.4 | 6.8 | 8.3 | 6/8 | 13/13 | NO |
| Y4_20_h3_SCR | 20% | -29.2 | 4.6 | 11.4 | 16.6 | 5/14 | 26/25 | NO |
| Y4_20_h3_SCR | 30% | -43.8 | 3.8 | 14.5 | 24.9 | 5/21 | 38/37 | NO |
| Y4_20_h3_SCR | 50% | -73.0 | -46.3 | 2.7 | 9.4 | 4/24 | -9/-7 | NO |
| Y4_40_h3_SCR | 10% | -13.0 | 5.3 | 7.9 | 10.2 | 5/7 | 15/18 | NO |
| Y4_40_h3_SCR | 20% | -26.1 | 4.0 | 14.3 | 16.2 | 3/13 | 30/35 | NO |
| Y4_40_h3_SCR | 30% | -39.1 | 2.7 | 16.6 | 15.3 | 2/19 | 20/26 | NO |
| Y4_40_h3_SCR | 50% | -65.2 | -56.0 | -3.6 | -3.5 | -1/17 | -24/-20 | NO |
| Y4_40_h5_SCR | 10% | -9.7 | 4.4 | 7.9 | 14.2 | 8/9 | -1/12 | NO |
| Y4_40_h5_SCR | 20% | -19.4 | 3.7 | 14.6 | 16.0 | 10/17 | -1/24 | NO |
| Y4_40_h5_SCR | 30% | -29.1 | 3.1 | 21.0 | 15.0 | 12/23 | -2/22 | NO |
| Y4_40_h5_SCR | 50% | -48.4 | 1.7 | 16.7 | 11.8 | 9/18 | -4/3 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| Y4_20_h3_SCR | -0.18 | 4 | 0.00 | -0.25 / -0.16 | -0.05 / -0.66 / -0.36 / -0.20 | -0.92 | -0.03 / -0.53 / -0.33 / -0.17 |
| Y4_40_h3_SCR | -0.12 | 4 | 0.00 | -0.18 / -0.15 | -0.04 / -0.45 / -0.29 / -0.15 | -0.56 | -0.01 / -0.31 / -0.28 / -0.11 |
| Y4_40_h5_SCR | -0.02 | 4 | 0.00 | -0.08 / -0.06 | -0.02 / -0.22 / 0.01 / -0.03 | -0.02 | -0.00 / -0.10 / 0.02 / -0.00 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| Y4_20_h3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.50) | NO |
| Y4_40_h3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.57) | NO |
| Y4_40_h5_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.42) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y4_20_h3_SCR | clean | -0.27 | -232,792 | -236,767 | -135,118 | -103,058 | 515,152 | -0.39 | -0.45 | 59 | 1.40 | -101,065 | -85,585 | 294,462 | 4.28 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y4_20_h3_SCR | H1 | -2.53 | -717,279 | -179,001 | -171,516 | -155,863 | 717,279 | -2.88 | -1.00 | 68 | 1.82 | -71,737 | -71,353 | 173,749 | 2.18 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y4_20_h3_SCR | H2 | -0.67 | -285,553 | -251,880 | -178,179 | -130,054 | 513,272 | -1.02 | -0.56 | 54 | 1.75 | -102,627 | -101,860 | 241,041 | 2.80 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y4_20_h3_SCR | all | -0.80 | -1,235,623 | -251,880 | -159,079 | -122,448 | 1,453,732 | -1.10 | -0.85 | 60 | 1.57 | -102,627 | -89,723 | 294,462 | 7.86 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |
| Y4_40_h3_SCR | clean | -0.15 | -138,613 | -218,149 | -134,625 | -105,512 | 527,901 | -0.23 | -0.26 | 54 | 1.42 | -103,439 | -87,206 | 305,968 | 4.21 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y4_40_h3_SCR | H1 | -1.39 | -433,329 | -182,350 | -182,324 | -160,704 | 442,227 | -1.79 | -0.98 | 61 | 2.12 | -67,052 | -66,489 | 176,646 | 2.63 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y4_40_h3_SCR | H2 | -0.50 | -246,935 | -267,864 | -196,427 | -136,506 | 644,346 | -0.85 | -0.38 | 54 | 1.81 | -97,647 | -88,134 | 210,103 | 3.27 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y4_40_h3_SCR | all | -0.47 | -818,876 | -267,864 | -165,015 | -124,968 | 941,866 | -0.72 | -0.87 | 55 | 1.64 | -103,439 | -86,318 | 305,968 | 7.97 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| Y4_40_h5_SCR | clean | -0.08 | -68,452 | -231,498 | -124,936 | -101,108 | 458,344 | -0.11 | -0.15 | 56 | 1.43 | -94,841 | -83,057 | 307,173 | 4.26 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y4_40_h5_SCR | H1 | -0.62 | -150,039 | -140,379 | -112,197 | -100,231 | 364,902 | -0.88 | -0.41 | 57 | 2.48 | -103,492 | -72,971 | 182,052 | 3.01 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y4_40_h5_SCR | H2 | 0.65 | 302,650 | -93,771 | -92,512 | -72,357 | 319,251 | 2.03 | 0.95 | 54 | 2.25 | -87,176 | -83,055 | 212,116 | 4.02 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y4_40_h5_SCR | all | 0.05 | 84,159 | -231,498 | -119,879 | -97,968 | 458,344 | 0.09 | 0.18 | 56 | 1.80 | -103,492 | -85,870 | 307,173 | 8.82 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE Y4
