# REPORT V3

**NO - gap fade conditioned on own-vol regime: best selected cell V3_('hi', 0.67)_h1_ALL26: standalone Sharpe 2013-22 0.40, pair window 1.02, own-null rank pair window 0.99; additive uplift at 20% clean/H1/H2 +0.19/-0.52/+0.56, bootstrap lo -0.05; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea V3: W6 gap fade filtered by ATR20 percentile (lo/hi), hold 1/3, SCR or ALL26 = 16 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 16 cells; eligible 5
| cell                     |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------------|-----------------:|-------------:|----------:|
| V3_('hi', 0.67)_h1_SCR   |              207 |         0.73 |         8 |
| V3_('hi', 0.5)_h3_SCR    |              288 |         0.61 |         9 |
| V3_('hi', 0.5)_h1_SCR    |              292 |         0.55 |         8 |
| V3_('hi', 0.67)_h3_SCR   |              204 |         0.53 |         8 |
| V3_('hi', 0.67)_h1_ALL26 |              547 |         0.4  |         9 |
| V3_('hi', 0.5)_h3_ALL26  |              692 |         0.38 |         9 |
| V3_('hi', 0.5)_h1_ALL26  |              755 |         0.37 |         7 |
| V3_('lo', 0.5)_h3_ALL26  |              569 |         0.35 |         5 |
| V3_('lo', 0.5)_h1_SCR    |              251 |         0.34 |         5 |
| V3_('lo', 0.5)_h3_SCR    |              251 |         0.33 |         7 |

Multiplicity: 16 cells x 5% = 0.8 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| V3_('hi', 0.67)_h1_ALL26 | 0.40 | 9 | 0.87 | -2.45 | 1.99 | 1.02 | 0.59 | 0.73 | 0.99 | 0.11 | 0.99 |
| V3_('hi', 0.5)_h3_ALL26 | 0.38 | 9 | 0.79 | -0.26 | 0.87 | 0.70 | 0.47 | 0.72 | 0.95 | 0.27 | 0.96 |
| V3_('hi', 0.5)_h1_ALL26 | 0.37 | 7 | 0.79 | -1.88 | 1.71 | 0.89 | 0.53 | 0.57 | 0.99 | 0.05 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V3_('hi', 0.67)_h1_ALL26 | 8.4 | 10% | 0.14 | -0.25 | 0.44 | 0.16 | 8 | 0.01 | 0.12 | 0.20 | 0.09 | NO |
| V3_('hi', 0.67)_h1_ALL26 | 8.4 | 20% | 0.19 | -0.52 | 0.56 | 0.18 | 16 | -0.05 | 0.12 | 0.20 | 0.09 | NO |
| V3_('hi', 0.67)_h1_ALL26 | 8.4 | 30% | 0.18 | -0.78 | 0.54 | 0.14 | 25 | -0.16 | 0.12 | 0.20 | 0.09 | NO |
| V3_('hi', 0.67)_h1_ALL26 | 8.4 | 50% | 0.09 | -1.28 | 0.41 | -0.02 | 42 | -0.43 | 0.12 | 0.20 | 0.09 | NO |
| V3_('hi', 0.5)_h3_ALL26 | 3.6 | 10% | 0.12 | -0.07 | 0.00 | 0.06 | 19 | -0.05 | 0.06 | 0.13 | 0.11 | NO |
| V3_('hi', 0.5)_h3_ALL26 | 3.6 | 20% | 0.16 | -0.18 | -0.04 | 0.06 | 40 | -0.15 | 0.06 | 0.13 | 0.11 | NO |
| V3_('hi', 0.5)_h3_ALL26 | 3.6 | 30% | 0.15 | -0.31 | -0.11 | 0.01 | 60 | -0.26 | 0.06 | 0.13 | 0.11 | NO |
| V3_('hi', 0.5)_h3_ALL26 | 3.6 | 50% | 0.06 | -0.60 | -0.26 | -0.14 | 100 | -0.53 | 0.06 | 0.13 | 0.11 | NO |
| V3_('hi', 0.5)_h1_ALL26 | 6.8 | 10% | 0.11 | -0.23 | 0.32 | 0.12 | 6 | -0.03 | 0.10 | 0.15 | 0.10 | NO |
| V3_('hi', 0.5)_h1_ALL26 | 6.8 | 20% | 0.16 | -0.48 | 0.38 | 0.13 | 13 | -0.11 | 0.10 | 0.15 | 0.10 | NO |
| V3_('hi', 0.5)_h1_ALL26 | 6.8 | 30% | 0.15 | -0.73 | 0.33 | 0.07 | 20 | -0.23 | 0.10 | 0.15 | 0.10 | NO |
| V3_('hi', 0.5)_h1_ALL26 | 6.8 | 50% | 0.07 | -1.22 | 0.17 | -0.08 | 44 | -0.51 | 0.10 | 0.15 | 0.10 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| V3_('hi', 0.67)_h1_ALL26 | 10% | 4.9 | 2.1 | 7.3 | 16.7 | 1/6 | 10/10 | NO |
| V3_('hi', 0.67)_h1_ALL26 | 20% | 9.8 | 3.4 | 14.2 | 21.9 | 3/11 | 20/21 | NO |
| V3_('hi', 0.67)_h1_ALL26 | 30% | 14.8 | 4.7 | 20.4 | 27.2 | 4/17 | 26/28 | INSURANCE |
| V3_('hi', 0.67)_h1_ALL26 | 50% | 24.6 | -7.0 | 20.9 | 30.3 | 7/26 | -13/-0 | NO |
| V3_('hi', 0.5)_h3_ALL26 | 10% | -2.4 | -9.4 | 5.5 | 20.3 | -10/6 | 7/7 | NO |
| V3_('hi', 0.5)_h3_ALL26 | 20% | -4.9 | -19.7 | 9.9 | 29.1 | -21/12 | 13/13 | NO |
| V3_('hi', 0.5)_h3_ALL26 | 30% | -7.3 | -29.9 | 12.2 | 36.8 | -31/15 | 19/20 | NO |
| V3_('hi', 0.5)_h3_ALL26 | 50% | -12.1 | -50.4 | -1.0 | 14.3 | -52/20 | -4/2 | NO |
| V3_('hi', 0.5)_h1_ALL26 | 10% | 2.0 | 3.7 | 7.1 | 15.0 | 3/6 | 12/12 | NO |
| V3_('hi', 0.5)_h1_ALL26 | 20% | 4.1 | 6.6 | 13.7 | 18.4 | 6/11 | 23/23 | NO |
| V3_('hi', 0.5)_h1_ALL26 | 30% | 6.1 | 9.5 | 17.9 | 21.9 | 9/16 | 7/20 | NO |
| V3_('hi', 0.5)_h1_ALL26 | 50% | 10.2 | -37.3 | 12.6 | 28.0 | 15/27 | -45/-17 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| V3_('hi', 0.67)_h1_ALL26 | 0.18 | 2 | 0.50 | 0.11 / 0.15 | 0.17 / -0.52 / 0.52 / 0.16 | 0.97 | 0.20 / -0.37 / 0.57 / 0.22 |
| V3_('hi', 0.5)_h3_ALL26 | 0.06 | 4 | 0.25 | -0.00 / 0.04 | 0.15 / -0.19 / -0.07 / 0.04 | 0.66 | 0.17 / -0.11 / -0.05 / 0.08 |
| V3_('hi', 0.5)_h1_ALL26 | 0.13 | 2 | 0.50 | 0.08 / 0.11 | 0.13 / -0.49 / 0.34 / 0.10 | 0.83 | 0.17 / -0.34 / 0.38 / 0.16 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| V3_('hi', 0.67)_h1_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.50) | fail | PASS (0.20) | NO |
| V3_('hi', 0.5)_h3_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.25) | fail | PASS (0.13) | NO |
| V3_('hi', 0.5)_h1_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.50) | fail | PASS (0.15) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V3_('hi', 0.67)_h1_ALL26 | clean | 0.87 | 1,934,595 | -83,793 | -76,057 | -61,909 | 381,740 | 5.97 | 5.07 | 25 | 1.64 | -103,230 | -88,877 | 278,393 | 6.86 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| V3_('hi', 0.67)_h1_ALL26 | H1 | -2.45 | -443,454 | -165,039 | -143,602 | -131,869 | 457,099 | -2.40 | -0.97 | 21 | 2.05 | -78,287 | -76,585 | 172,712 | 2.67 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V3_('hi', 0.67)_h1_ALL26 | H2 | 1.99 | 2,514,719 | -114,321 | -92,949 | -62,116 | 114,321 | 20.87 | 22.00 | 19 | 2.80 | -86,610 | -82,169 | 205,137 | 7.39 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| V3_('hi', 0.67)_h1_ALL26 | all | 1.02 | 4,005,860 | -165,039 | -101,242 | -79,903 | 550,979 | 6.05 | 7.27 | 23 | 1.99 | -103,230 | -86,249 | 278,393 | 13.96 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| V3_('hi', 0.5)_h3_ALL26 | clean | 0.79 | 1,592,445 | -166,318 | -95,119 | -67,532 | 382,899 | 4.14 | 4.16 | 30 | 1.61 | -131,769 | -88,860 | 248,225 | 7.28 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| V3_('hi', 0.5)_h3_ALL26 | H1 | -0.26 | -64,418 | -151,566 | -140,307 | -114,240 | 254,188 | -0.41 | -0.25 | 25 | 2.52 | -86,552 | -85,371 | 183,611 | 3.13 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V3_('hi', 0.5)_h3_ALL26 | H2 | 0.87 | 505,616 | -256,951 | -193,371 | -149,695 | 705,357 | 1.67 | 0.72 | 35 | 2.15 | -105,432 | -95,561 | 220,282 | 4.14 | 49 | 2.26 | -82,524 | -81,089 | 217,425 |
| V3_('hi', 0.5)_h3_ALL26 | all | 0.70 | 2,033,643 | -256,951 | -139,558 | -106,124 | 705,357 | 2.27 | 2.88 | 31 | 1.87 | -131,769 | -91,729 | 248,225 | 13.27 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| V3_('hi', 0.5)_h1_ALL26 | clean | 0.79 | 1,514,346 | -94,146 | -75,207 | -62,366 | 372,287 | 4.48 | 4.07 | 30 | 1.61 | -99,216 | -89,207 | 293,231 | 6.08 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| V3_('hi', 0.5)_h1_ALL26 | H1 | -1.88 | -394,849 | -215,109 | -162,624 | -141,565 | 405,929 | -1.90 | -0.97 | 18 | 2.10 | -76,100 | -75,684 | 157,091 | 3.03 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| V3_('hi', 0.5)_h1_ALL26 | H2 | 1.71 | 2,111,684 | -178,018 | -176,597 | -129,559 | 364,080 | 8.86 | 5.80 | 24 | 2.59 | -85,302 | -83,205 | 207,447 | 6.72 | 49 | 2.26 | -82,524 | -81,089 | 217,425 |
| V3_('hi', 0.5)_h1_ALL26 | all | 0.89 | 3,231,182 | -215,109 | -129,543 | -97,219 | 508,575 | 3.87 | 6.35 | 27 | 1.93 | -99,216 | -86,835 | 293,231 | 12.46 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE V3
