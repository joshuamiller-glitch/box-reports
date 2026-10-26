# REPORT Y5

**NO - volume-spike follow/fade: best selected cell Y5_1.5_fade_h1_SCR: standalone Sharpe 2013-22 0.04, pair window 0.07, own-null rank pair window 0.86; additive uplift at 20% clean/H1/H2 -0.05/+0.01/-0.14, bootstrap lo -0.25; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea Y5: volume >= m x 20-day mean, follow or fade the candle, hold 1/3, ALL26 or SCR = 16 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 16 cells; eligible 1
| cell                 |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:---------------------|-----------------:|-------------:|----------:|
| Y5_2.0_fade_h3_SCR   |             1354 |         0.07 |         6 |
| Y5_1.5_fade_h1_SCR   |             8403 |         0.04 |         7 |
| Y5_2.0_fade_h1_SCR   |             1812 |        -0    |         5 |
| Y5_2.0_fade_h3_ALL26 |             2006 |        -0.03 |         5 |
| Y5_1.5_fade_h3_SCR   |             5169 |        -0.15 |         3 |
| Y5_2.0_fade_h1_ALL26 |             2677 |        -0.18 |         5 |
| Y5_1.5_fade_h3_ALL26 |             7612 |        -0.24 |         3 |
| Y5_2.0_follow_h3_SCR |             1354 |        -0.28 |         4 |
| Y5_1.5_follow_h3_SCR |             5169 |        -0.32 |         4 |
| Y5_2.0_follow_h1_SCR |             1812 |        -0.35 |         1 |

Multiplicity: 16 cells x 5% = 0.8 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Y5_1.5_fade_h1_SCR | 0.04 | 7 | 0.16 | 0.71 | -0.81 | 0.07 | 0.03 | 0.29 | 0.86 | -0.30 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y5_1.5_fade_h1_SCR | 1.7 | 10% | -0.01 | 0.02 | -0.06 | -0.02 | 13 | -0.11 | 0.09 | 0.62 | 0.08 | NO |
| Y5_1.5_fade_h1_SCR | 1.7 | 20% | -0.05 | 0.01 | -0.14 | -0.07 | 27 | -0.25 | 0.09 | 0.62 | 0.08 | NO |
| Y5_1.5_fade_h1_SCR | 1.7 | 30% | -0.09 | -0.02 | -0.23 | -0.12 | 40 | -0.39 | 0.09 | 0.62 | 0.08 | NO |
| Y5_1.5_fade_h1_SCR | 1.7 | 50% | -0.21 | -0.13 | -0.44 | -0.27 | 68 | -0.70 | 0.09 | 0.62 | 0.08 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| Y5_1.5_fade_h1_SCR | 10% | -9.6 | -3.0 | 4.5 | 4.1 | -4/5 | 3/10 | NO |
| Y5_1.5_fade_h1_SCR | 20% | -19.1 | -6.8 | 8.2 | 8.3 | -8/9 | 6/21 | NO |
| Y5_1.5_fade_h1_SCR | 30% | -28.7 | -10.6 | 9.9 | 12.4 | -12/10 | 10/31 | NO |
| Y5_1.5_fade_h1_SCR | 50% | -47.8 | -101.2 | -3.1 | -14.9 | -103/-6 | 16/26 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| Y5_1.5_fade_h1_SCR | -0.07 | 2 | 0.00 | -0.12 / -0.06 | -0.10 / -0.05 / -0.18 / -0.12 | -0.16 | -0.05 / 0.08 / -0.11 / -0.05 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| Y5_1.5_fade_h1_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | fail (0.62) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y5_1.5_fade_h1_SCR | clean | 0.16 | 181,532 | -398,592 | -157,449 | -115,935 | 628,153 | 0.25 | 0.29 | 47 | 1.37 | -115,860 | -91,603 | 329,457 | 4.20 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y5_1.5_fade_h1_SCR | H1 | 0.71 | 154,747 | -115,148 | -101,939 | -90,249 | 202,107 | 1.14 | 0.77 | 50 | 2.81 | -94,143 | -76,721 | 160,878 | 3.98 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y5_1.5_fade_h1_SCR | H2 | -0.81 | -218,026 | -244,691 | -153,736 | -105,107 | 368,555 | -0.92 | -0.59 | 54 | 2.03 | -101,359 | -96,321 | 238,515 | 2.92 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y5_1.5_fade_h1_SCR | all | 0.07 | 118,252 | -398,592 | -157,121 | -114,030 | 628,153 | 0.11 | 0.19 | 48 | 1.73 | -115,860 | -93,317 | 329,457 | 8.26 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE Y5
