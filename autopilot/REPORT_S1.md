# REPORT S1

**NO - post-open drift per asset class (30-min path): best selected cell S1_EQ_follow_h4: standalone Sharpe 2013-22 0.57, pair window -0.27, own-null rank pair window 0.50; additive uplift at 20% clean/H1/H2 +0.01/-0.13/-0.44, bootstrap lo -0.31; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea S1: first-bar move at the class open followed/faded for 2h or to the day end; 5 classes x 2 x 2 = 20 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 20 cells; eligible 1
| cell              |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:------------------|-----------------:|-------------:|----------:|
| S1_EQ_follow_h4   |             4219 |         0.57 |         8 |
| S1_EQ_follow_END  |             4219 |         0.16 |         6 |
| S1_MET_follow_END |             1768 |        -0.24 |         5 |
| S1_EN_follow_h4   |             3248 |        -0.26 |         3 |
| S1_MET_follow_h4  |             1768 |        -0.3  |         4 |
| S1_FX_fade_END    |             1108 |        -0.3  |         3 |
| S1_EN_follow_END  |             3248 |        -0.32 |         3 |
| S1_EN_fade_END    |             3248 |        -0.37 |         3 |
| S1_FX_fade_h4     |             1108 |        -0.47 |         4 |
| S1_FX_follow_END  |             1108 |        -0.5  |         2 |

Multiplicity: 20 cells x 5% = 1.0 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S1_EQ_follow_h4 | 0.57 | 8 | 0.39 | -0.28 | -1.90 | -0.27 | 0.34 | 0.54 | 0.50 | -0.18 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S1_EQ_follow_h4 | 6.0 | 10% | 0.01 | -0.02 | -0.21 | -0.05 | 14 | -0.15 | 0.23 | 0.37 | 0.06 | NO |
| S1_EQ_follow_h4 | 6.0 | 20% | 0.01 | -0.13 | -0.44 | -0.12 | 31 | -0.31 | 0.23 | 0.37 | 0.06 | NO |
| S1_EQ_follow_h4 | 6.0 | 30% | -0.01 | -0.30 | -0.67 | -0.20 | 59 | -0.48 | 0.23 | 0.37 | 0.06 | NO |
| S1_EQ_follow_h4 | 6.0 | 50% | -0.05 | -0.72 | -1.13 | -0.38 | 117 | -0.82 | 0.23 | 0.37 | 0.06 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| S1_EQ_follow_h4 | 10% | -11.5 | -4.4 | 3.1 | 13.5 | -5/2 | 10/10 | NO |
| S1_EQ_follow_h4 | 20% | -23.1 | -16.0 | 3.0 | 26.7 | -10/3 | 19/19 | NO |
| S1_EQ_follow_h4 | 30% | -34.6 | -37.6 | 1.9 | 24.3 | -16/5 | 13/20 | NO |
| S1_EQ_follow_h4 | 50% | -57.7 | -80.7 | -8.8 | 8.2 | -26/3 | -9/-3 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| S1_EQ_follow_h4 | -0.12 | 0 | n/a | n/a / n/a | -0.03 / -0.17 / -0.47 / -0.16 | -0.45 | 0.00 / -0.09 / -0.44 / -0.11 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| S1_EQ_follow_h4 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | fail (0.37) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S1_EQ_follow_h4 | clean | 0.39 | 323,790 | -171,946 | -123,009 | -96,207 | 295,100 | 0.58 | 1.10 | 48 | 1.45 | -119,174 | -98,586 | 261,307 | 5.46 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| S1_EQ_follow_h4 | H1 | -0.28 | -103,052 | -222,446 | -215,031 | -202,293 | 548,178 | -0.36 | -0.19 | 39 | 2.53 | -81,303 | -80,369 | 203,068 | 2.77 | 29 | 2.83 | -78,287 | -77,610 | 151,713 |
| S1_EQ_follow_h4 | H2 | -1.90 | -632,842 | -238,006 | -198,105 | -158,295 | 1,015,064 | -2.09 | -0.62 | 58 | 1.62 | -131,606 | -109,062 | 262,471 | 2.18 | 42 | 2.30 | -82,524 | -81,089 | 217,425 |
| S1_EQ_follow_h4 | all | -0.27 | -412,103 | -238,006 | -174,986 | -136,350 | 1,074,924 | -0.35 | -0.38 | 49 | 1.66 | -131,606 | -99,952 | 262,471 | 9.76 | 39 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE S1
