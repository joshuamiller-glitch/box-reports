# REPORT G4

**NO - BTC calendar sleeves (GAPMAP D06 H5/H6): best selected cell G4_dow_3_short_h1_BTC: standalone Sharpe 2013-22 0.23, pair window 1.15, own-null rank pair window 0.99; additive uplift at 20% clean/H1/H2 +0.13/+0.98/-0.12, bootstrap lo -0.02; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea G4: weekday and month-turn windows in BTC futures = 14 cells; clean-only selection.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 14 cells; eligible 4
| cell                     |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------------|-----------------:|-------------:|----------:|
| G4_dow_2_long_h1_BTC     |       1000000000 |         1.24 |        10 |
| G4_dow_0_long_h1_BTC     |       1000000000 |         1.12 |        10 |
| G4_dow_3_short_h1_BTC    |       1000000000 |         0.86 |        10 |
| G4_end2_0_short_h2_BTC   |                0 |         0.81 |         0 |
| G4_dow_4_long_h1_BTC     |       1000000000 |         0.63 |        10 |
| G4_start3_0_long_h3_BTC  |                0 |         0.18 |         0 |
| G4_dow_1_long_h1_BTC     |                0 |         0.01 |         0 |
| G4_dow_1_short_h1_BTC    |                0 |        -0.11 |         0 |
| G4_start3_0_short_h3_BTC |                0 |        -0.21 |         0 |
| G4_dow_4_short_h1_BTC    |                0 |        -0.75 |         0 |

Multiplicity: 14 cells x 5% = 0.7 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G4_dow_2_long_h1_BTC | -0.13 | 0 | 1.24 | 1.08 | 0.47 | 1.04 | 0.35 | 0.98 | 0.97 | 0.50 | 0.32 |
| G4_dow_0_long_h1_BTC | -0.25 | 0 | 1.12 | -0.09 | 2.93 | 1.30 | 0.36 | 1.00 | 0.99 | 0.55 | 0.32 |
| G4_dow_3_short_h1_BTC | 0.23 | 1 | 0.86 | 3.36 | -0.25 | 1.15 | 0.49 | 0.82 | 0.99 | 0.48 | 0.78 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G4_dow_2_long_h1_BTC | 13.4 | 10% | 0.11 | 0.07 | 0.00 | 0.08 | 6 | -0.00 | 0.20 | 0.11 | 0.07 | NO |
| G4_dow_2_long_h1_BTC | 13.4 | 20% | 0.20 | 0.11 | -0.02 | 0.14 | 12 | -0.03 | 0.20 | 0.11 | 0.07 | NO |
| G4_dow_2_long_h1_BTC | 13.4 | 30% | 0.28 | 0.12 | -0.06 | 0.18 | 20 | -0.06 | 0.20 | 0.11 | 0.07 | NO |
| G4_dow_2_long_h1_BTC | 13.4 | 50% | 0.37 | 0.10 | -0.17 | 0.21 | 37 | -0.17 | 0.20 | 0.11 | 0.07 | NO |
| G4_dow_0_long_h1_BTC | 11.3 | 10% | 0.10 | -0.03 | 0.17 | 0.10 | 19 | 0.01 | 0.24 | 0.20 | 0.05 | NO |
| G4_dow_0_long_h1_BTC | 11.3 | 20% | 0.19 | -0.08 | 0.33 | 0.19 | 38 | 0.01 | 0.24 | 0.20 | 0.05 | NO |
| G4_dow_0_long_h1_BTC | 11.3 | 30% | 0.26 | -0.14 | 0.46 | 0.25 | 58 | -0.01 | 0.24 | 0.20 | 0.05 | NO |
| G4_dow_0_long_h1_BTC | 11.3 | 50% | 0.34 | -0.30 | 0.68 | 0.33 | 97 | -0.08 | 0.24 | 0.20 | 0.05 | NO |
| G4_dow_3_short_h1_BTC | 15.4 | 10% | 0.08 | 0.54 | -0.05 | 0.11 | 17 | 0.00 | 0.42 | -0.20 | 0.02 | NO |
| G4_dow_3_short_h1_BTC | 15.4 | 20% | 0.13 | 0.98 | -0.12 | 0.19 | 41 | -0.02 | 0.42 | -0.20 | 0.02 | NO |
| G4_dow_3_short_h1_BTC | 15.4 | 30% | 0.18 | 1.31 | -0.21 | 0.25 | 64 | -0.05 | 0.42 | -0.20 | 0.02 | NO |
| G4_dow_3_short_h1_BTC | 15.4 | 50% | 0.22 | 1.67 | -0.39 | 0.31 | 111 | -0.16 | 0.42 | -0.20 | 0.02 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| G4_dow_2_long_h1_BTC | 10% | -4.4 | 4.0 | 6.9 | 14.0 | 9/8 | 1/9 | NO |
| G4_dow_2_long_h1_BTC | 20% | -8.7 | 7.1 | 12.6 | 28.0 | 12/15 | 2/18 | NO |
| G4_dow_2_long_h1_BTC | 30% | -13.1 | 8.1 | 16.4 | 34.2 | 15/19 | 3/22 | NO |
| G4_dow_2_long_h1_BTC | 50% | -21.9 | 10.1 | 19.1 | 27.9 | 15/22 | 5/14 | NO |
| G4_dow_0_long_h1_BTC | 10% | -3.5 | -8.8 | 7.5 | 5.0 | -10/6 | 4/9 | NO |
| G4_dow_0_long_h1_BTC | 20% | -7.0 | -18.4 | 12.1 | 9.9 | -19/10 | 7/18 | NO |
| G4_dow_0_long_h1_BTC | 30% | -10.4 | -27.9 | 14.7 | 14.1 | -29/12 | 9/20 | NO |
| G4_dow_0_long_h1_BTC | 50% | -17.4 | -47.1 | 10.0 | 15.1 | -48/4 | 14/18 | NO |
| G4_dow_3_short_h1_BTC | 10% | -3.2 | -7.9 | 4.6 | 12.8 | 4/7 | 3/8 | NO |
| G4_dow_3_short_h1_BTC | 20% | -6.4 | -21.9 | 6.8 | 20.2 | 2/12 | 6/15 | NO |
| G4_dow_3_short_h1_BTC | 30% | -9.5 | -36.0 | 5.6 | 11.9 | -0/14 | 9/23 | NO |
| G4_dow_3_short_h1_BTC | 50% | -15.9 | -64.1 | -0.6 | -5.9 | -11/7 | 15/22 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| G4_dow_2_long_h1_BTC | 0.14 | 0 | n/a | n/a / n/a | 0.19 / 0.10 / -0.03 / 0.13 | 1.00 | 0.19 / 0.14 / -0.00 / 0.14 |
| G4_dow_0_long_h1_BTC | 0.19 | 0 | n/a | n/a / n/a | 0.18 / -0.08 / 0.32 / 0.18 | 1.26 | 0.18 / -0.06 / 0.28 / 0.17 |
| G4_dow_3_short_h1_BTC | 0.19 | 0 | n/a | n/a / n/a | 0.12 / 0.98 / -0.13 / 0.18 | 1.11 | 0.13 / 0.82 / -0.11 / 0.19 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| G4_dow_2_long_h1_BTC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (n/a) | fail | PASS (0.11) | NO |
| G4_dow_0_long_h1_BTC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (n/a) | fail | PASS (0.20) | NO |
| G4_dow_3_short_h1_BTC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (n/a) | fail | PASS (-0.20) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G4_dow_2_long_h1_BTC | clean | 1.24 | 1,133,925 | -106,348 | -94,950 | -80,720 | 522,975 | 2.39 | 2.17 | 50 | 1.74 | -92,603 | -85,443 | 246,479 | 6.78 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| G4_dow_2_long_h1_BTC | H1 | 1.08 | 213,015 | -90,928 | -80,525 | -74,090 | 225,159 | 1.74 | 0.95 | 39 | 2.95 | -99,324 | -79,543 | 148,943 | 4.42 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| G4_dow_2_long_h1_BTC | H2 | 0.47 | 164,210 | -96,115 | -84,332 | -75,755 | 273,028 | 0.97 | 0.60 | 54 | 2.20 | -97,346 | -91,471 | 235,348 | 3.44 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| G4_dow_2_long_h1_BTC | all | 1.04 | 1,511,150 | -106,348 | -92,143 | -79,970 | 522,975 | 1.98 | 2.89 | 50 | 2.04 | -99,324 | -88,325 | 246,479 | 12.73 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| G4_dow_0_long_h1_BTC | clean | 1.12 | 1,015,890 | -160,909 | -121,659 | -93,881 | 358,468 | 1.90 | 2.83 | 51 | 1.72 | -130,147 | -91,680 | 322,506 | 5.07 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| G4_dow_0_long_h1_BTC | H1 | -0.09 | -15,948 | -84,647 | -81,543 | -77,400 | 185,840 | -0.13 | -0.09 | 43 | 2.68 | -94,321 | -79,861 | 163,968 | 3.59 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| G4_dow_0_long_h1_BTC | H2 | 2.93 | 751,865 | -108,172 | -90,534 | -70,868 | 127,362 | 5.44 | 5.90 | 30 | 2.73 | -89,017 | -76,092 | 208,619 | 4.73 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| G4_dow_0_long_h1_BTC | all | 1.30 | 1,751,806 | -160,909 | -111,246 | -88,764 | 358,468 | 2.20 | 4.89 | 46 | 2.11 | -130,147 | -89,523 | 322,506 | 9.96 | 41 | 1.86 | -82,524 | -79,220 | 280,110 |
| G4_dow_3_short_h1_BTC | clean | 0.86 | 786,947 | -174,449 | -121,576 | -102,176 | 334,895 | 1.38 | 2.35 | 49 | 1.64 | -105,225 | -89,059 | 256,722 | 6.10 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| G4_dow_3_short_h1_BTC | H1 | 3.36 | 1,123,366 | -121,443 | -97,452 | -84,576 | 121,443 | 9.21 | 9.25 | 32 | 4.14 | -94,898 | -82,938 | 145,537 | 6.40 | 29 | 2.83 | -78,287 | -77,610 | 151,713 |
| G4_dow_3_short_h1_BTC | H2 | -0.25 | -78,030 | -193,414 | -183,341 | -135,382 | 474,121 | -0.30 | -0.16 | 46 | 2.06 | -135,440 | -112,661 | 298,322 | 2.47 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| G4_dow_3_short_h1_BTC | all | 1.15 | 1,832,283 | -193,414 | -135,286 | -109,434 | 474,121 | 1.92 | 3.86 | 46 | 2.11 | -135,440 | -96,145 | 298,322 | 10.84 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE G4
