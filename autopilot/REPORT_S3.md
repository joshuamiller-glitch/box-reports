# REPORT S3

**NO - realised-skew reversal: best selected cell S3_60_1.25_h5_ALL26: standalone Sharpe 2013-22 0.19, pair window 0.55, own-null rank pair window 0.92; additive uplift at 20% clean/H1/H2 +0.00/+1.00/-0.10, bootstrap lo -0.10; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea S3: 20/60-day skew beyond +-0.75/1.25 -> contrarian, hold 3/5 = 16 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 16 cells; eligible 3
| cell                |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:--------------------|-----------------:|-------------:|----------:|
| S3_20_1.25_h5_SCR   |             1341 |         0.24 |         6 |
| S3_60_1.25_h5_ALL26 |              955 |         0.19 |         7 |
| S3_60_1.25_h5_SCR   |              718 |         0.16 |         6 |
| S3_60_1.25_h3_SCR   |             1124 |         0.09 |         7 |
| S3_60_1.25_h3_ALL26 |             1482 |         0.09 |         7 |
| S3_20_1.25_h5_ALL26 |             1982 |         0.05 |         4 |
| S3_60_0.75_h5_SCR   |             2312 |         0.05 |         5 |
| S3_20_1.25_h3_SCR   |             1916 |         0.03 |         5 |
| S3_60_0.75_h3_SCR   |             3650 |        -0    |         5 |
| S3_20_0.75_h5_SCR   |             3618 |        -0.09 |         4 |

Multiplicity: 16 cells x 5% = 0.8 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S3_60_1.25_h5_ALL26 | 0.19 | 7 | 0.27 | 2.45 | -0.32 | 0.55 | 0.25 | 0.63 | 0.92 | 0.28 | 0.91 |
| S3_60_1.25_h3_SCR | 0.09 | 7 | 0.00 | 2.68 | -0.15 | 0.47 | 0.17 | 0.70 | 0.88 | 0.31 | 0.78 |
| S3_60_1.25_h3_ALL26 | 0.09 | 7 | -0.25 | 1.62 | -0.33 | 0.11 | 0.06 | 0.53 | 0.79 | 0.14 | 0.93 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S3_60_1.25_h5_ALL26 | 2.7 | 10% | 0.01 | 0.51 | -0.03 | 0.06 | 6 | -0.04 | 0.77 | -0.33 | -0.05 | NO |
| S3_60_1.25_h5_ALL26 | 2.7 | 20% | 0.00 | 1.00 | -0.10 | 0.09 | 17 | -0.10 | 0.77 | -0.33 | -0.05 | NO |
| S3_60_1.25_h5_ALL26 | 2.7 | 30% | -0.01 | 1.43 | -0.20 | 0.11 | 29 | -0.17 | 0.77 | -0.33 | -0.05 | NO |
| S3_60_1.25_h5_ALL26 | 2.7 | 50% | -0.06 | 1.96 | -0.44 | 0.09 | 65 | -0.37 | 0.77 | -0.33 | -0.05 | NO |
| S3_60_1.25_h3_SCR | 3.3 | 10% | -0.01 | 0.54 | -0.04 | 0.05 | 11 | -0.06 | 0.62 | -0.39 | -0.03 | NO |
| S3_60_1.25_h3_SCR | 3.3 | 20% | -0.04 | 1.01 | -0.14 | 0.07 | 28 | -0.15 | 0.62 | -0.39 | -0.03 | NO |
| S3_60_1.25_h3_SCR | 3.3 | 30% | -0.07 | 1.36 | -0.29 | 0.07 | 45 | -0.28 | 0.62 | -0.39 | -0.03 | NO |
| S3_60_1.25_h3_SCR | 3.3 | 50% | -0.16 | 1.70 | -0.62 | -0.00 | 168 | -0.57 | 0.62 | -0.39 | -0.03 | NO |
| S3_60_1.25_h3_ALL26 | 2.9 | 10% | -0.04 | 0.42 | -0.04 | 0.01 | 9 | -0.08 | 0.80 | -0.30 | -0.07 | NO |
| S3_60_1.25_h3_ALL26 | 2.9 | 20% | -0.08 | 0.80 | -0.12 | 0.01 | 24 | -0.19 | 0.80 | -0.30 | -0.07 | NO |
| S3_60_1.25_h3_ALL26 | 2.9 | 30% | -0.14 | 1.09 | -0.24 | -0.02 | 39 | -0.32 | 0.80 | -0.30 | -0.07 | NO |
| S3_60_1.25_h3_ALL26 | 2.9 | 50% | -0.26 | 1.31 | -0.53 | -0.13 | 102 | -0.62 | 0.80 | -0.30 | -0.07 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| S3_60_1.25_h5_ALL26 | 10% | -7.0 | 3.8 | 7.8 | 9.8 | 6/8 | 13/19 | NO |
| S3_60_1.25_h5_ALL26 | 20% | -14.0 | 1.3 | 14.4 | 19.5 | 6/15 | 25/38 | NO |
| S3_60_1.25_h5_ALL26 | 30% | -21.1 | -1.1 | 15.9 | 24.2 | 5/19 | 36/48 | NO |
| S3_60_1.25_h5_ALL26 | 50% | -35.1 | -104.4 | 2.3 | 27.9 | 5/17 | 36/47 | NO |
| S3_60_1.25_h3_SCR | 10% | -6.9 | -1.5 | 7.6 | 9.3 | 3/8 | 14/17 | NO |
| S3_60_1.25_h3_SCR | 20% | -13.8 | -9.3 | 13.9 | 18.5 | 1/16 | 28/35 | NO |
| S3_60_1.25_h3_SCR | 30% | -20.7 | -53.0 | 7.9 | 23.1 | -2/21 | 42/49 | NO |
| S3_60_1.25_h3_SCR | 50% | -34.4 | -207.8 | -11.3 | 9.3 | -7/22 | 28/46 | NO |
| S3_60_1.25_h3_ALL26 | 10% | -9.3 | 0.5 | 7.3 | 9.4 | 5/8 | 10/11 | NO |
| S3_60_1.25_h3_ALL26 | 20% | -18.7 | -5.2 | 13.3 | 18.8 | 3/15 | 19/22 | NO |
| S3_60_1.25_h3_ALL26 | 30% | -28.0 | -13.0 | 11.6 | 25.3 | 2/19 | 28/33 | NO |
| S3_60_1.25_h3_ALL26 | 50% | -46.7 | -141.2 | -4.3 | 28.9 | 0/17 | 31/38 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| S3_60_1.25_h5_ALL26 | 0.09 | 6 | 0.67 | -0.03 / 0.08 | -0.01 / 0.92 / -0.13 / 0.07 | 0.41 | 0.01 / 0.68 / -0.11 / 0.09 |
| S3_60_1.25_h3_SCR | 0.07 | 6 | 0.67 | 0.01 / 0.09 | -0.05 / 0.99 / -0.17 / 0.06 | 0.41 | -0.03 / 0.80 / -0.15 / 0.08 |
| S3_60_1.25_h3_ALL26 | 0.01 | 6 | 0.67 | -0.07 / 0.04 | -0.11 / 0.67 / -0.16 / -0.04 | -0.09 | -0.08 / 0.51 / -0.12 / 0.01 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| S3_60_1.25_h5_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.67) | fail | PASS (-0.33) | NO |
| S3_60_1.25_h3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.67) | fail | PASS (-0.39) | NO |
| S3_60_1.25_h3_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.67) | fail | PASS (-0.30) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S3_60_1.25_h5_ALL26 | clean | 0.27 | 214,201 | -133,591 | -107,598 | -88,984 | 460,206 | 0.45 | 0.47 | 33 | 1.45 | -100,533 | -84,890 | 282,187 | 4.94 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| S3_60_1.25_h5_ALL26 | H1 | 2.45 | 719,751 | -107,931 | -97,871 | -92,872 | 341,315 | 5.18 | 2.11 | 39 | 4.26 | -72,900 | -57,840 | 134,326 | 6.03 | 29 | 2.83 | -78,287 | -77,610 | 151,713 |
| S3_60_1.25_h5_ALL26 | H2 | -0.32 | -133,995 | -402,725 | -264,113 | -171,965 | 451,784 | -0.36 | -0.30 | 41 | 2.07 | -106,676 | -94,100 | 260,862 | 2.76 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| S3_60_1.25_h5_ALL26 | all | 0.55 | 799,957 | -402,725 | -141,261 | -108,824 | 460,206 | 0.77 | 1.74 | 36 | 1.96 | -106,676 | -86,095 | 282,187 | 10.37 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| S3_60_1.25_h3_SCR | clean | 0.00 | 3,007 | -132,630 | -103,240 | -84,584 | 534,291 | 0.01 | 0.01 | 29 | 1.39 | -106,583 | -83,787 | 286,272 | 4.65 | 48 | 1.46 | -81,874 | -78,736 | 280,110 |
| S3_60_1.25_h3_SCR | H1 | 2.68 | 919,498 | -120,258 | -114,594 | -102,614 | 262,366 | 6.07 | 3.50 | 43 | 4.19 | -69,170 | -60,212 | 110,433 | 7.87 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| S3_60_1.25_h3_SCR | H2 | -0.15 | -86,966 | -573,372 | -364,028 | -236,057 | 573,372 | -0.17 | -0.15 | 38 | 1.97 | -119,757 | -113,204 | 273,944 | 2.68 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| S3_60_1.25_h3_SCR | all | 0.47 | 835,539 | -573,372 | -168,115 | -123,301 | 573,372 | 0.64 | 1.46 | 33 | 1.92 | -119,757 | -90,210 | 286,272 | 10.25 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |
| S3_60_1.25_h3_ALL26 | clean | -0.25 | -195,007 | -144,941 | -116,089 | -96,585 | 619,999 | -0.37 | -0.31 | 37 | 1.32 | -103,084 | -85,472 | 285,052 | 4.46 | 47 | 1.46 | -81,874 | -78,736 | 280,110 |
| S3_60_1.25_h3_ALL26 | H1 | 1.62 | 531,571 | -117,011 | -116,028 | -110,541 | 388,634 | 2.97 | 1.37 | 46 | 3.91 | -79,728 | -74,991 | 136,134 | 5.53 | 25 | 2.83 | -78,287 | -77,610 | 151,713 |
| S3_60_1.25_h3_ALL26 | H2 | -0.33 | -158,685 | -463,424 | -293,892 | -193,899 | 463,424 | -0.37 | -0.34 | 38 | 2.03 | -114,723 | -98,524 | 267,225 | 2.67 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| S3_60_1.25_h3_ALL26 | all | 0.11 | 177,878 | -463,424 | -159,621 | -123,465 | 661,918 | 0.15 | 0.27 | 39 | 1.83 | -114,723 | -87,734 | 285,052 | 9.61 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE S3
