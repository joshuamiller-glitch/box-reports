# REPORT V7

**NO - commodity cross-sectional momentum/reversal: best selected cell V7_60_mom_h10_COM: standalone Sharpe 2013-22 0.11, pair window -0.36, own-null rank pair window 0.36; additive uplift at 20% clean/H1/H2 -0.12/-0.47/-0.02, bootstrap lo -0.33; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea V7: long 3 / short 3 of 13 commodities by n-day z, hold 5/10 = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 2
| cell               |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------|-----------------:|-------------:|----------:|
| V7_120_rev_h10_COM |             2129 |         0.54 |         7 |
| V7_60_mom_h10_COM  |             2289 |         0.11 |         7 |
| V7_120_rev_h5_COM  |             3597 |         0.1  |         5 |
| V7_20_rev_h10_COM  |             2632 |         0.09 |         5 |
| V7_60_mom_h5_COM   |             3848 |        -0.13 |         3 |
| V7_20_mom_h5_COM   |             4391 |        -0.32 |         3 |
| V7_20_rev_h5_COM   |             4391 |        -0.44 |         1 |
| V7_20_mom_h10_COM  |             2632 |        -0.5  |         3 |
| V7_60_rev_h10_COM  |             2289 |        -0.51 |         3 |
| V7_60_rev_h5_COM   |             3848 |        -0.56 |         3 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| V7_120_rev_h10_COM | 0.54 | 7 | 0.06 | -0.65 | -1.11 | -0.33 | 0.27 | 0.79 | 0.38 | 0.34 | 1.00 |
| V7_60_mom_h10_COM | 0.11 | 7 | -0.72 | -0.51 | 0.36 | -0.36 | -0.02 | 0.74 | 0.36 | 0.29 | 0.83 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V7_120_rev_h10_COM | 1.8 | 10% | -0.02 | -0.04 | -0.12 | -0.05 | 15 | -0.17 | 0.47 | 0.07 | 0.00 | NO |
| V7_120_rev_h10_COM | 1.8 | 20% | -0.06 | -0.15 | -0.26 | -0.13 | 31 | -0.36 | 0.47 | 0.07 | 0.00 | NO |
| V7_120_rev_h10_COM | 1.8 | 30% | -0.10 | -0.33 | -0.43 | -0.23 | 47 | -0.56 | 0.47 | 0.07 | 0.00 | NO |
| V7_120_rev_h10_COM | 1.8 | 50% | -0.22 | -0.79 | -0.79 | -0.44 | 91 | -0.96 | 0.47 | 0.07 | 0.00 | NO |
| V7_60_mom_h10_COM | 1.7 | 10% | -0.05 | -0.22 | 0.01 | -0.05 | 21 | -0.16 | 0.55 | -0.02 | -0.02 | NO |
| V7_60_mom_h10_COM | 1.7 | 20% | -0.12 | -0.47 | -0.02 | -0.12 | 47 | -0.33 | 0.55 | -0.02 | -0.02 | NO |
| V7_60_mom_h10_COM | 1.7 | 30% | -0.20 | -0.71 | -0.08 | -0.21 | 74 | -0.52 | 0.55 | -0.02 | -0.02 | NO |
| V7_60_mom_h10_COM | 1.7 | 50% | -0.38 | -1.13 | -0.26 | -0.42 | 126 | -0.89 | 0.55 | -0.02 | -0.02 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| V7_120_rev_h10_COM | 10% | -12.2 | -5.2 | 2.3 | 11.2 | -6/1 | 24/24 | NO |
| V7_120_rev_h10_COM | 20% | -24.3 | -11.3 | 3.1 | 22.4 | -12/-0 | 24/30 | NO |
| V7_120_rev_h10_COM | 30% | -36.5 | -17.6 | -0.5 | 25.7 | -19/-6 | 12/12 | NO |
| V7_120_rev_h10_COM | 50% | -60.8 | -75.2 | -18.8 | -5.3 | -77/-20 | -36/-23 | NO |
| V7_60_mom_h10_COM | 10% | -12.3 | -11.7 | 4.1 | 13.4 | -4/7 | -18/-6 | NO |
| V7_60_mom_h10_COM | 20% | -24.5 | -28.5 | 7.0 | 14.5 | -10/14 | -35/-12 | NO |
| V7_60_mom_h10_COM | 30% | -36.8 | -45.3 | 7.3 | 13.5 | -17/19 | -53/-21 | NO |
| V7_60_mom_h10_COM | 50% | -61.3 | -78.9 | -2.2 | -6.5 | -29/17 | -89/-63 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| V7_120_rev_h10_COM | -0.13 | 4 | 0.00 | -0.22 / -0.13 | -0.08 / -0.19 / -0.28 / -0.16 | -0.45 | -0.05 / -0.12 / -0.29 / -0.12 |
| V7_60_mom_h10_COM | -0.12 | 4 | 0.00 | -0.17 / -0.12 | -0.15 / -0.49 / -0.03 / -0.15 | -0.47 | -0.12 / -0.26 / 0.02 / -0.11 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| V7_120_rev_h10_COM | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.07) | NO |
| V7_60_mom_h10_COM | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.02) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V7_120_rev_h10_COM | clean | 0.06 | 64,245 | -263,346 | -154,594 | -126,398 | 688,850 | 0.09 | 0.09 | 47 | 1.36 | -121,381 | -104,385 | 273,385 | 4.94 | 40 | 1.46 | -81,874 | -78,736 | 280,110 |
| V7_120_rev_h10_COM | H1 | -0.65 | -216,063 | -201,435 | -163,182 | -147,525 | 615,939 | -0.89 | -0.35 | 57 | 2.49 | -80,349 | -76,173 | 170,112 | 3.11 | 46 | 2.83 | -78,287 | -77,610 | 151,713 |
| V7_120_rev_h10_COM | H2 | -1.11 | -430,559 | -219,523 | -211,029 | -157,922 | 612,047 | -1.30 | -0.70 | 51 | 1.83 | -100,629 | -94,470 | 269,433 | 2.35 | 49 | 2.26 | -82,524 | -81,089 | 217,425 |
| V7_120_rev_h10_COM | all | -0.33 | -582,376 | -263,346 | -174,578 | -142,308 | 983,316 | -0.44 | -0.59 | 49 | 1.63 | -121,381 | -100,571 | 273,385 | 9.18 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| V7_60_mom_h10_COM | clean | -0.72 | -612,180 | -137,289 | -122,141 | -110,712 | 993,275 | -0.93 | -0.62 | 49 | 1.26 | -119,451 | -86,445 | 312,474 | 3.67 | 46 | 1.46 | -81,874 | -78,736 | 280,110 |
| V7_60_mom_h10_COM | H1 | -0.51 | -166,421 | -216,989 | -207,983 | -183,062 | 543,240 | -0.67 | -0.31 | 57 | 2.12 | -143,384 | -114,785 | 231,393 | 2.35 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| V7_60_mom_h10_COM | H2 | 0.36 | 174,212 | -106,968 | -100,876 | -93,173 | 327,844 | 0.82 | 0.53 | 54 | 2.18 | -99,538 | -89,493 | 209,203 | 3.89 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| V7_60_mom_h10_COM | all | -0.36 | -604,389 | -216,989 | -145,675 | -122,582 | 1,178,118 | -0.53 | -0.51 | 51 | 1.64 | -143,384 | -94,907 | 312,474 | 8.01 | 45 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE V7
