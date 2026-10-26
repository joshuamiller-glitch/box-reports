# REPORT V5

**NO - equity-index relative strength (ES NQ RTY YM): best selected cell V5_5_rev_h10_EQ: standalone Sharpe 2013-22 0.22, pair window 0.83, own-null rank pair window 0.96; additive uplift at 20% clean/H1/H2 +0.33/+0.01/-0.24, bootstrap lo -0.04; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea V5: long strongest / short weakest by n-day z, momentum or reversal, hold 5/10 = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 3
| cell             |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-----------------|-----------------:|-------------:|----------:|
| V5_20_mom_h10_EQ |              835 |         0.48 |         6 |
| V5_60_mom_h10_EQ |              756 |         0.32 |         7 |
| V5_5_rev_h10_EQ  |              926 |         0.22 |         7 |
| V5_5_mom_h5_EQ   |             1685 |         0.17 |         7 |
| V5_20_mom_h5_EQ  |             1512 |         0.1  |         6 |
| V5_60_rev_h5_EQ  |             1395 |        -0.04 |         5 |
| V5_60_mom_h5_EQ  |             1395 |        -0.34 |         4 |
| V5_5_mom_h10_EQ  |              926 |        -0.39 |         3 |
| V5_20_rev_h5_EQ  |             1512 |        -0.46 |         4 |
| V5_5_rev_h5_EQ   |             1685 |        -0.48 |         3 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| V5_60_mom_h10_EQ | 0.32 | 7 | 0.39 | -0.88 | -0.36 | 0.01 | 0.24 | 0.78 | 0.51 | 0.42 | 0.90 |
| V5_5_rev_h10_EQ | 0.22 | 7 | 1.96 | -0.36 | -1.32 | 0.83 | 0.39 | 0.77 | 0.96 | 0.40 | 0.81 |
| V5_5_mom_h5_EQ | 0.17 | 7 | -0.35 | 0.53 | 1.05 | 0.03 | 0.20 | 0.69 | 0.60 | 0.41 | 0.87 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V5_60_mom_h10_EQ | 4.6 | 10% | 0.04 | -0.10 | -0.06 | -0.00 | 10 | -0.09 | 0.67 | 0.07 | -0.04 | NO |
| V5_60_mom_h10_EQ | 4.6 | 20% | 0.06 | -0.24 | -0.14 | -0.02 | 24 | -0.20 | 0.67 | 0.07 | -0.04 | NO |
| V5_60_mom_h10_EQ | 4.6 | 30% | 0.07 | -0.40 | -0.23 | -0.06 | 38 | -0.33 | 0.67 | 0.07 | -0.04 | NO |
| V5_60_mom_h10_EQ | 4.6 | 50% | 0.05 | -0.77 | -0.45 | -0.17 | 66 | -0.60 | 0.67 | 0.07 | -0.04 | NO |
| V5_5_rev_h10_EQ | 3.3 | 10% | 0.18 | 0.03 | -0.11 | 0.09 | 9 | -0.01 | 0.61 | 0.33 | -0.03 | NO |
| V5_5_rev_h10_EQ | 3.3 | 20% | 0.33 | 0.01 | -0.24 | 0.15 | 22 | -0.04 | 0.61 | 0.33 | -0.03 | NO |
| V5_5_rev_h10_EQ | 3.3 | 30% | 0.47 | -0.07 | -0.38 | 0.18 | 39 | -0.09 | 0.61 | 0.33 | -0.03 | NO |
| V5_5_rev_h10_EQ | 3.3 | 50% | 0.66 | -0.36 | -0.72 | 0.20 | 73 | -0.23 | 0.61 | 0.33 | -0.03 | NO |
| V5_5_mom_h5_EQ | 3.7 | 10% | -0.05 | -0.05 | 0.02 | -0.03 | 27 | -0.12 | 0.06 | -0.05 | 0.13 | NO |
| V5_5_mom_h5_EQ | 3.7 | 20% | -0.11 | -0.12 | 0.03 | -0.07 | 61 | -0.25 | 0.06 | -0.05 | 0.13 | NO |
| V5_5_mom_h5_EQ | 3.7 | 30% | -0.18 | -0.20 | 0.02 | -0.12 | 95 | -0.38 | 0.06 | -0.05 | 0.13 | NO |
| V5_5_mom_h5_EQ | 3.7 | 50% | -0.33 | -0.38 | 0.00 | -0.25 | 163 | -0.65 | 0.06 | -0.05 | 0.13 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| V5_60_mom_h10_EQ | 10% | -10.0 | -0.7 | 7.5 | 11.8 | 10/10 | 7/10 | NO |
| V5_60_mom_h10_EQ | 20% | -19.9 | -4.9 | 13.3 | 23.6 | 15/19 | 13/20 | NO |
| V5_60_mom_h10_EQ | 30% | -29.9 | -9.0 | 17.0 | 35.5 | 21/26 | 19/29 | NO |
| V5_60_mom_h10_EQ | 50% | -49.8 | -20.3 | 10.4 | 32.5 | -21/20 | 23/26 | NO |
| V5_5_rev_h10_EQ | 10% | -5.1 | 0.8 | 5.2 | 21.7 | 3/6 | 5/11 | NO |
| V5_5_rev_h10_EQ | 20% | -10.2 | -4.5 | 9.5 | 34.7 | -5/12 | 9/22 | NO |
| V5_5_rev_h10_EQ | 30% | -15.3 | -12.5 | 12.5 | 36.2 | -13/15 | 14/29 | NO |
| V5_5_rev_h10_EQ | 50% | -25.5 | -28.6 | 9.7 | -1.9 | -30/16 | 3/12 | NO |
| V5_5_mom_h5_EQ | 10% | -9.8 | -17.9 | 1.9 | 7.0 | -19/1 | 3/5 | NO |
| V5_5_mom_h5_EQ | 20% | -19.7 | -42.6 | 2.2 | 14.0 | -44/1 | 5/10 | NO |
| V5_5_mom_h5_EQ | 30% | -29.5 | -67.2 | -1.6 | 17.1 | -69/-5 | 7/15 | NO |
| V5_5_mom_h5_EQ | 50% | -49.2 | -116.4 | -17.2 | 2.1 | -118/-29 | 10/25 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| V5_60_mom_h10_EQ | -0.02 | 4 | 0.00 | -0.19 / -0.11 | 0.05 / -0.25 / -0.14 / -0.03 | -0.02 | 0.06 / -0.18 / -0.11 / -0.02 |
| V5_5_rev_h10_EQ | 0.15 | 4 | 0.25 | -0.13 / -0.11 | 0.33 / 0.00 / -0.24 / 0.14 | 0.81 | 0.33 / -0.02 / -0.20 / 0.15 |
| V5_5_mom_h5_EQ | -0.07 | 4 | 0.00 | -0.07 / -0.04 | -0.12 / -0.13 / 0.02 / -0.08 | -0.02 | -0.08 / -0.02 / 0.03 / -0.04 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| V5_60_mom_h10_EQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.07) | NO |
| V5_5_rev_h10_EQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.25) | fail | fail (0.33) | NO |
| V5_5_mom_h5_EQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.05) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V5_60_mom_h10_EQ | clean | 0.39 | 349,866 | -199,756 | -125,174 | -102,178 | 385,994 | 0.60 | 0.91 | 50 | 1.53 | -88,505 | -80,533 | 264,801 | 5.42 | 48 | 1.46 | -81,874 | -78,736 | 280,110 |
| V5_60_mom_h10_EQ | H1 | -0.88 | -210,915 | -113,059 | -103,461 | -99,790 | 506,812 | -1.23 | -0.42 | 61 | 2.42 | -86,843 | -78,012 | 167,318 | 3.17 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| V5_60_mom_h10_EQ | H2 | -0.36 | -126,631 | -129,513 | -128,080 | -120,770 | 476,875 | -0.48 | -0.27 | 46 | 2.03 | -113,888 | -108,568 | 237,007 | 3.05 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| V5_60_mom_h10_EQ | all | 0.01 | 12,320 | -199,756 | -131,213 | -113,373 | 820,694 | 0.01 | 0.02 | 51 | 1.80 | -113,888 | -87,879 | 264,801 | 10.15 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| V5_5_rev_h10_EQ | clean | 1.96 | 1,856,217 | -140,949 | -102,812 | -84,330 | 215,990 | 3.92 | 8.59 | 35 | 1.93 | -114,759 | -88,954 | 234,153 | 8.06 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| V5_5_rev_h10_EQ | H1 | -0.36 | -100,937 | -158,525 | -141,561 | -132,487 | 557,937 | -0.48 | -0.18 | 54 | 2.76 | -91,122 | -75,443 | 224,322 | 2.51 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V5_5_rev_h10_EQ | H2 | -1.32 | -439,291 | -187,279 | -144,620 | -115,917 | 731,699 | -1.68 | -0.60 | 54 | 1.88 | -110,242 | -96,274 | 210,608 | 2.99 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| V5_5_rev_h10_EQ | all | 0.83 | 1,315,990 | -187,279 | -130,704 | -108,578 | 913,297 | 1.36 | 1.44 | 42 | 2.04 | -114,759 | -92,138 | 234,153 | 13.15 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| V5_5_mom_h5_EQ | clean | -0.35 | -327,118 | -280,214 | -175,166 | -133,475 | 848,677 | -0.43 | -0.39 | 48 | 1.28 | -161,072 | -102,210 | 305,201 | 4.04 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| V5_5_mom_h5_EQ | H1 | 0.53 | 115,627 | -74,370 | -69,420 | -67,568 | 259,713 | 1.03 | 0.45 | 64 | 2.62 | -96,092 | -89,299 | 181,535 | 3.46 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| V5_5_mom_h5_EQ | H2 | 1.05 | 253,074 | -92,550 | -85,270 | -79,708 | 426,906 | 1.69 | 0.59 | 43 | 2.29 | -110,289 | -97,183 | 250,491 | 3.34 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| V5_5_mom_h5_EQ | all | 0.03 | 41,584 | -280,214 | -147,738 | -113,288 | 848,677 | 0.04 | 0.05 | 49 | 1.73 | -161,072 | -100,896 | 305,201 | 8.84 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE V5
