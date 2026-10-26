# REPORT Y3

**NO - 52-week-extreme proximity follow: best selected cell Y3_1.0_h5_SCR: standalone Sharpe 2013-22 0.78, pair window -0.13, own-null rank pair window 0.52; additive uplift at 20% clean/H1/H2 -0.12/+0.43/-0.09, bootstrap lo -0.24; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea Y3: within p ATR of the 252-day high (long) / low (short), hold 3/5/10, ALL26 or SCR = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 6
| cell             |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-----------------|-----------------:|-------------:|----------:|
| Y3_1.0_h5_ALL26  |             3041 |         0.9  |         8 |
| Y3_1.0_h5_SCR    |             2047 |         0.78 |         8 |
| Y3_1.0_h10_ALL26 |             1886 |         0.67 |         7 |
| Y3_1.0_h3_ALL26  |             4378 |         0.65 |         6 |
| Y3_2.0_h10_ALL26 |             2846 |         0.62 |         5 |
| Y3_1.0_h10_SCR   |             1257 |         0.58 |         7 |
| Y3_1.0_h3_SCR    |             2972 |         0.52 |         7 |
| Y3_2.0_h5_ALL26  |             5042 |         0.49 |         5 |
| Y3_2.0_h10_SCR   |             1887 |         0.46 |         6 |
| Y3_2.0_h5_SCR    |             3358 |         0.45 |         6 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Y3_1.0_h5_ALL26 | 0.90 | 8 | -1.13 | 0.60 | -0.23 | -0.64 | 0.50 | 0.52 | 0.27 | 0.13 | 1.00 |
| Y3_1.0_h5_SCR | 0.78 | 8 | -0.68 | 1.02 | 0.05 | -0.13 | 0.54 | 0.85 | 0.52 | 0.30 | 1.00 |
| Y3_1.0_h10_ALL26 | 0.67 | 7 | -1.04 | 1.02 | 0.56 | -0.33 | 0.44 | 0.69 | 0.38 | 0.21 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y3_1.0_h5_ALL26 | 1.4 | 10% | -0.10 | 0.11 | -0.04 | -0.06 | 16 | -0.15 | 0.80 | -0.12 | -0.07 | NO |
| Y3_1.0_h5_ALL26 | 1.4 | 20% | -0.20 | 0.19 | -0.09 | -0.13 | 39 | -0.31 | 0.80 | -0.12 | -0.07 | NO |
| Y3_1.0_h5_ALL26 | 1.4 | 30% | -0.32 | 0.23 | -0.16 | -0.21 | 62 | -0.48 | 0.80 | -0.12 | -0.07 | NO |
| Y3_1.0_h5_ALL26 | 1.4 | 50% | -0.56 | 0.23 | -0.34 | -0.41 | 108 | -0.83 | 0.80 | -0.12 | -0.07 | NO |
| Y3_1.0_h5_SCR | 1.8 | 10% | -0.05 | 0.24 | -0.02 | -0.01 | 9 | -0.11 | 0.81 | -0.04 | -0.08 | NO |
| Y3_1.0_h5_SCR | 1.8 | 20% | -0.12 | 0.43 | -0.09 | -0.04 | 25 | -0.24 | 0.81 | -0.04 | -0.08 | NO |
| Y3_1.0_h5_SCR | 1.8 | 30% | -0.19 | 0.55 | -0.19 | -0.10 | 41 | -0.39 | 0.81 | -0.04 | -0.08 | NO |
| Y3_1.0_h5_SCR | 1.8 | 50% | -0.36 | 0.58 | -0.42 | -0.25 | 73 | -0.71 | 0.81 | -0.04 | -0.08 | NO |
| Y3_1.0_h10_ALL26 | 1.2 | 10% | -0.08 | 0.13 | 0.05 | -0.02 | 13 | -0.11 | 0.80 | -0.16 | -0.07 | NO |
| Y3_1.0_h10_ALL26 | 1.2 | 20% | -0.18 | 0.23 | 0.09 | -0.06 | 34 | -0.23 | 0.80 | -0.16 | -0.07 | NO |
| Y3_1.0_h10_ALL26 | 1.2 | 30% | -0.28 | 0.30 | 0.12 | -0.11 | 54 | -0.36 | 0.80 | -0.16 | -0.07 | NO |
| Y3_1.0_h10_ALL26 | 1.2 | 50% | -0.48 | 0.35 | 0.11 | -0.24 | 94 | -0.64 | 0.80 | -0.16 | -0.07 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| Y3_1.0_h5_ALL26 | 10% | -13.2 | -6.9 | 6.3 | 6.0 | -8/5 | 8/13 | NO |
| Y3_1.0_h5_ALL26 | 20% | -26.4 | -20.5 | 11.9 | 11.9 | -21/10 | 15/26 | NO |
| Y3_1.0_h5_ALL26 | 30% | -39.7 | -34.1 | 15.7 | 14.0 | -35/12 | 23/32 | NO |
| Y3_1.0_h5_ALL26 | 50% | -66.1 | -61.4 | -3.2 | -5.8 | -63/-7 | 12/12 | NO |
| Y3_1.0_h5_SCR | 10% | -10.8 | -0.0 | 6.5 | 8.5 | -1/6 | 12/19 | NO |
| Y3_1.0_h5_SCR | 20% | -21.6 | -6.7 | 12.4 | 15.3 | -8/11 | 25/37 | NO |
| Y3_1.0_h5_SCR | 30% | -32.4 | -13.4 | 16.7 | 13.7 | -14/16 | 32/32 | NO |
| Y3_1.0_h5_SCR | 50% | -54.0 | -59.2 | -11.1 | 8.4 | -60/-3 | -14/-10 | NO |
| Y3_1.0_h10_ALL26 | 10% | -11.5 | -4.1 | 7.5 | 4.7 | -5/6 | 9/13 | NO |
| Y3_1.0_h10_ALL26 | 20% | -23.0 | -14.9 | 13.8 | 9.5 | -16/12 | 18/26 | NO |
| Y3_1.0_h10_ALL26 | 30% | -34.5 | -25.7 | 17.3 | 14.2 | -27/15 | 25/26 | NO |
| Y3_1.0_h10_ALL26 | 50% | -57.6 | -47.3 | 4.5 | 2.4 | -48/0 | -15/9 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| Y3_1.0_h5_ALL26 | -0.13 | 4 | 0.00 | -0.15 / -0.11 | -0.24 / 0.16 / -0.13 / -0.16 | -0.82 | -0.20 / 0.15 / -0.07 / -0.11 |
| Y3_1.0_h5_SCR | -0.04 | 4 | 0.00 | -0.09 / -0.01 | -0.13 / 0.42 / -0.10 / -0.06 | -0.19 | -0.12 / 0.34 / -0.06 / -0.03 |
| Y3_1.0_h10_ALL26 | -0.06 | 4 | 0.00 | -0.11 / -0.08 | -0.19 / 0.21 / 0.07 / -0.08 | -0.43 | -0.17 / 0.19 / 0.11 / -0.05 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| Y3_1.0_h5_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.12) | NO |
| Y3_1.0_h5_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.04) | NO |
| Y3_1.0_h10_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.16) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y3_1.0_h5_ALL26 | clean | -1.13 | -918,798 | -337,668 | -161,167 | -123,053 | 1,038,771 | -1.25 | -0.88 | 50 | 1.14 | -133,798 | -90,980 | 313,992 | 3.36 | 46 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y3_1.0_h5_ALL26 | H1 | 0.60 | 130,275 | -138,693 | -132,278 | -110,055 | 241,099 | 0.84 | 0.54 | 39 | 3.06 | -84,048 | -70,286 | 173,265 | 3.65 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y3_1.0_h5_ALL26 | H2 | -0.23 | -76,036 | -162,889 | -129,004 | -97,041 | 588,741 | -0.37 | -0.13 | 54 | 2.10 | -96,423 | -85,929 | 192,316 | 3.84 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y3_1.0_h5_ALL26 | all | -0.64 | -864,559 | -337,668 | -155,876 | -118,839 | 1,190,042 | -0.79 | -0.73 | 49 | 1.64 | -133,798 | -89,359 | 313,992 | 7.73 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |
| Y3_1.0_h5_SCR | clean | -0.68 | -541,903 | -344,574 | -152,524 | -113,449 | 710,477 | -0.79 | -0.76 | 48 | 1.27 | -116,709 | -89,094 | 310,090 | 3.76 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y3_1.0_h5_SCR | H1 | 1.02 | 303,274 | -180,605 | -165,801 | -145,835 | 307,983 | 1.51 | 0.98 | 32 | 3.38 | -72,668 | -64,594 | 173,154 | 3.95 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y3_1.0_h5_SCR | H2 | 0.05 | 22,705 | -236,259 | -187,744 | -131,921 | 510,809 | 0.09 | 0.04 | 57 | 2.08 | -103,947 | -91,719 | 198,889 | 3.86 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y3_1.0_h5_SCR | all | -0.13 | -215,924 | -344,574 | -169,503 | -128,320 | 767,291 | -0.19 | -0.28 | 47 | 1.76 | -116,709 | -88,359 | 310,090 | 8.45 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| Y3_1.0_h10_ALL26 | clean | -1.04 | -774,366 | -283,064 | -147,497 | -117,467 | 970,360 | -1.16 | -0.80 | 50 | 1.18 | -126,848 | -89,056 | 324,378 | 3.38 | 48 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y3_1.0_h10_ALL26 | H1 | 1.02 | 211,498 | -169,514 | -136,552 | -107,280 | 295,447 | 1.37 | 0.72 | 36 | 3.13 | -80,219 | -71,147 | 184,868 | 3.56 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y3_1.0_h10_ALL26 | H2 | 0.56 | 157,333 | -116,946 | -104,084 | -88,857 | 364,683 | 0.92 | 0.43 | 51 | 2.38 | -97,159 | -85,546 | 184,834 | 4.37 | 35 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y3_1.0_h10_ALL26 | all | -0.33 | -405,534 | -283,064 | -142,096 | -113,206 | 982,948 | -0.41 | -0.41 | 48 | 1.74 | -126,848 | -87,353 | 324,378 | 7.90 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE Y3
