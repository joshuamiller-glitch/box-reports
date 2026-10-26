# REPORT S8

**NO - options-expiry week / day / Monday after: best selected cell S8_mon_h1_NQ: standalone Sharpe 2013-22 0.43, pair window 1.76, own-null rank pair window 1.00; additive uplift at 20% clean/H1/H2 +0.40/+0.07/-0.08, bootstrap lo +0.07; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea S8: long ES NQ RTY YM in opex week, opex Friday, Monday after = 12 cells (60-trade floor).

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 0
| cell          |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:--------------|-----------------:|-------------:|----------:|
| S8_wk_h5_NQ   |              116 |         0.58 |         7 |
| S8_wk_h5_ES   |              116 |         0.46 |         7 |
| S8_mon_h1_NQ  |              116 |         0.43 |         7 |
| S8_wk_h5_YM   |              116 |         0.41 |         7 |
| S8_mon_h1_YM  |              116 |         0.3  |         5 |
| S8_mon_h1_RTY |               63 |         0.09 |         3 |
| S8_mon_h1_ES  |              116 |         0.01 |         5 |
| S8_fri_h1_RTY |               63 |        -0.07 |         2 |
| S8_fri_h1_YM  |              116 |        -0.13 |         5 |
| S8_fri_h1_ES  |              116 |        -0.19 |         4 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S8_wk_h5_NQ | 0.58 | 7 | -0.35 | 0.29 | 0.41 | -0.12 | 0.47 | 0.76 | 0.50 | 0.57 | 0.95 |
| S8_wk_h5_ES | 0.46 | 7 | -0.09 | 0.42 | 0.19 | 0.01 | 0.39 | 0.98 | 0.52 | 0.52 | 0.93 |
| S8_mon_h1_NQ | 0.43 | 7 | 2.33 | 0.84 | 0.90 | 1.76 | 0.75 | 0.92 | 1.00 | 0.48 | 0.93 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S8_wk_h5_NQ | 10.3 | 10% | -0.07 | 0.06 | -0.01 | -0.04 | 20 | -0.13 | 0.08 | -0.27 | 0.10 | NO |
| S8_wk_h5_NQ | 10.3 | 20% | -0.15 | 0.11 | -0.04 | -0.10 | 46 | -0.28 | 0.08 | -0.27 | 0.10 | NO |
| S8_wk_h5_NQ | 10.3 | 30% | -0.24 | 0.13 | -0.08 | -0.18 | 72 | -0.44 | 0.08 | -0.27 | 0.10 | NO |
| S8_wk_h5_NQ | 10.3 | 50% | -0.42 | 0.12 | -0.18 | -0.34 | 124 | -0.77 | 0.08 | -0.27 | 0.10 | NO |
| S8_wk_h5_ES | 10.3 | 10% | -0.03 | 0.07 | -0.03 | -0.02 | 15 | -0.10 | 0.22 | -0.12 | 0.05 | NO |
| S8_wk_h5_ES | 10.3 | 20% | -0.07 | 0.12 | -0.06 | -0.05 | 36 | -0.22 | 0.22 | -0.12 | 0.05 | NO |
| S8_wk_h5_ES | 10.3 | 30% | -0.13 | 0.16 | -0.11 | -0.10 | 57 | -0.35 | 0.22 | -0.12 | 0.05 | NO |
| S8_wk_h5_ES | 10.3 | 50% | -0.26 | 0.20 | -0.21 | -0.23 | 100 | -0.64 | 0.22 | -0.12 | 0.05 | NO |
| S8_mon_h1_NQ | 119.4 | 10% | 0.21 | 0.05 | -0.03 | 0.13 | 35 | 0.05 | 0.01 | 0.63 | 0.18 | NO |
| S8_mon_h1_NQ | 119.4 | 20% | 0.40 | 0.07 | -0.08 | 0.24 | 70 | 0.07 | 0.01 | 0.63 | 0.18 | NO |
| S8_mon_h1_NQ | 119.4 | 30% | 0.56 | 0.09 | -0.13 | 0.33 | 105 | 0.08 | 0.01 | 0.63 | 0.18 | NO |
| S8_mon_h1_NQ | 119.4 | 50% | 0.81 | 0.06 | -0.24 | 0.44 | 174 | 0.06 | 0.01 | 0.63 | 0.18 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| S8_wk_h5_NQ | 10% | -10.7 | -10.2 | 6.5 | 7.0 | -11/4 | 10/10 | NO |
| S8_wk_h5_NQ | 20% | -21.4 | -27.0 | 10.9 | 11.1 | -28/5 | 20/20 | NO |
| S8_wk_h5_NQ | 30% | -32.1 | -43.9 | 9.0 | 6.7 | -45/-2 | 30/30 | NO |
| S8_wk_h5_NQ | 50% | -53.5 | -84.8 | -17.4 | -2.1 | -86/-42 | 48/49 | NO |
| S8_wk_h5_ES | 10% | -9.9 | -5.4 | 7.2 | 7.5 | -6/6 | 10/10 | NO |
| S8_wk_h5_ES | 20% | -19.9 | -17.4 | 12.2 | 8.2 | -18/8 | 20/20 | NO |
| S8_wk_h5_ES | 30% | -29.8 | -29.4 | 13.8 | 2.5 | -30/6 | 30/30 | NO |
| S8_wk_h5_ES | 50% | -49.7 | -53.4 | -4.2 | -9.1 | -55/-27 | 50/50 | NO |
| S8_mon_h1_NQ | 10% | -0.2 | -24.9 | 6.0 | 15.2 | 10/10 | 10/10 | NO |
| S8_mon_h1_NQ | 20% | -0.4 | -49.8 | 12.0 | 28.0 | 20/20 | 20/20 | NO |
| S8_mon_h1_NQ | 30% | -0.6 | -74.7 | 17.8 | 24.1 | 30/30 | 30/29 | NO |
| S8_mon_h1_NQ | 50% | -1.1 | -124.4 | 19.2 | 16.4 | 25/45 | 5/27 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| S8_wk_h5_NQ | -0.10 | 0 | n/a | n/a / n/a | -0.15 / 0.11 / -0.04 / -0.10 | -0.13 | -0.14 / 0.06 / -0.06 / -0.09 |
| S8_wk_h5_ES | -0.05 | 0 | n/a | n/a / n/a | -0.08 / 0.12 / -0.06 / -0.06 | -0.01 | -0.06 / 0.07 / -0.07 / -0.04 |
| S8_mon_h1_NQ | 0.24 | 0 | n/a | n/a / n/a | 0.39 / 0.07 / -0.08 / 0.24 | 1.73 | 0.39 / 0.08 / -0.01 / 0.26 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| S8_wk_h5_NQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | PASS (-0.27) | NO |
| S8_wk_h5_ES | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | PASS (-0.12) | NO |
| S8_mon_h1_NQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | PASS | fail (n/a) | fail | fail (0.63) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S8_wk_h5_NQ | clean | -0.35 | -367,608 | -335,785 | -218,620 | -151,362 | 926,729 | -0.44 | -0.40 | 10 | 1.22 | -141,854 | -96,338 | 328,755 | 3.71 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| S8_wk_h5_NQ | H1 | 0.29 | 50,697 | -147,284 | -111,182 | -74,122 | 263,334 | 0.42 | 0.19 | 7 | 2.96 | -78,287 | -77,610 | 180,837 | 3.37 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| S8_wk_h5_NQ | H2 | 0.41 | 127,756 | -137,953 | -126,508 | -86,093 | 325,987 | 0.78 | 0.39 | 11 | 2.19 | -79,653 | -78,535 | 217,425 | 3.68 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| S8_wk_h5_NQ | all | -0.12 | -189,155 | -335,785 | -190,227 | -131,277 | 926,729 | -0.16 | -0.20 | 10 | 1.68 | -141,854 | -90,410 | 328,755 | 7.99 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| S8_wk_h5_ES | clean | -0.09 | -95,756 | -281,457 | -218,210 | -140,008 | 709,177 | -0.12 | -0.14 | 10 | 1.33 | -129,901 | -94,235 | 340,602 | 3.82 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| S8_wk_h5_ES | H1 | 0.42 | 60,039 | -130,383 | -84,582 | -56,388 | 263,232 | 0.60 | 0.23 | 7 | 2.99 | -78,287 | -77,610 | 169,005 | 3.62 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| S8_wk_h5_ES | H2 | 0.19 | 50,709 | -119,156 | -110,358 | -76,434 | 365,352 | 0.34 | 0.14 | 11 | 2.16 | -84,790 | -82,222 | 217,425 | 3.57 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| S8_wk_h5_ES | all | 0.01 | 14,992 | -281,457 | -185,424 | -118,529 | 709,177 | 0.01 | 0.02 | 10 | 1.75 | -129,901 | -89,793 | 340,602 | 7.90 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| S8_mon_h1_NQ | clean | 2.33 | 2,120,735 | -137,113 | -48,858 | -26,650 | 137,113 | 7.81 | 15.47 | 3 | 2.02 | -81,874 | -78,662 | 236,194 | 8.32 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| S8_mon_h1_NQ | H1 | 0.84 | 140,954 | -122,313 | -69,513 | -46,342 | 122,313 | 1.56 | 1.15 | 7 | 2.91 | -78,287 | -77,610 | 160,196 | 3.97 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| S8_mon_h1_NQ | H2 | 0.90 | 365,312 | -287,877 | -196,849 | -106,599 | 320,573 | 1.40 | 1.14 | 8 | 2.13 | -168,888 | -124,270 | 266,649 | 3.27 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| S8_mon_h1_NQ | all | 1.76 | 2,627,001 | -287,877 | -95,397 | -50,504 | 320,573 | 3.81 | 8.19 | 5 | 2.18 | -168,888 | -88,783 | 266,649 | 13.03 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE S8
