# REPORT V4

**NO - gap fade with/against EMA50 trend: best selected cell V4_0.25_against_h1_SCR: standalone Sharpe 2013-22 0.81, pair window 0.82, own-null rank pair window 0.95; additive uplift at 20% clean/H1/H2 +0.20/-0.53/+0.27, bootstrap lo -0.10; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea V4: gap >= 0.25/0.5 ATR fade only with or only against the EMA50 trend, hold 1/3, SCR = 8 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 8 cells; eligible 2
| cell                   |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-----------------------|-----------------:|-------------:|----------:|
| V4_0.5_against_h1_SCR  |              124 |         0.9  |         8 |
| V4_0.25_against_h1_SCR |              327 |         0.81 |         7 |
| V4_0.5_against_h3_SCR  |              123 |         0.7  |         8 |
| V4_0.25_against_h3_SCR |              325 |         0.63 |         7 |
| V4_0.25_with_h3_SCR    |              218 |         0.36 |         8 |
| V4_0.25_with_h1_SCR    |              218 |        -0.02 |         4 |
| V4_0.5_with_h3_SCR     |               95 |        -0.06 |         5 |
| V4_0.5_with_h1_SCR     |               95 |        -0.09 |         5 |

Multiplicity: 8 cells x 5% = 0.4 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| V4_0.25_against_h1_SCR | 0.81 | 7 | 0.93 | -1.59 | 1.37 | 0.82 | 0.73 | 0.78 | 0.95 | 0.33 | 1.00 |
| V4_0.25_against_h3_SCR | 0.63 | 7 | 0.80 | -0.80 | 0.35 | 0.49 | 0.55 | 0.74 | 0.89 | 0.44 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V4_0.25_against_h1_SCR | 9.2 | 10% | 0.13 | -0.26 | 0.27 | 0.11 | 11 | -0.03 | 0.19 | 0.27 | 0.06 | NO |
| V4_0.25_against_h1_SCR | 9.2 | 20% | 0.20 | -0.53 | 0.27 | 0.12 | 22 | -0.10 | 0.19 | 0.27 | 0.06 | NO |
| V4_0.25_against_h1_SCR | 9.2 | 30% | 0.23 | -0.81 | 0.17 | 0.08 | 36 | -0.21 | 0.19 | 0.27 | 0.06 | NO |
| V4_0.25_against_h1_SCR | 9.2 | 50% | 0.21 | -1.32 | -0.06 | -0.08 | 102 | -0.48 | 0.19 | 0.27 | 0.06 | NO |
| V4_0.25_against_h3_SCR | 4.9 | 10% | 0.10 | -0.19 | -0.04 | 0.03 | 15 | -0.09 | 0.09 | 0.04 | 0.09 | NO |
| V4_0.25_against_h3_SCR | 4.9 | 20% | 0.15 | -0.45 | -0.12 | 0.00 | 35 | -0.20 | 0.09 | 0.04 | 0.09 | NO |
| V4_0.25_against_h3_SCR | 4.9 | 30% | 0.16 | -0.72 | -0.21 | -0.06 | 56 | -0.35 | 0.09 | 0.04 | 0.09 | NO |
| V4_0.25_against_h3_SCR | 4.9 | 50% | 0.09 | -1.26 | -0.41 | -0.22 | 98 | -0.63 | 0.09 | 0.04 | 0.09 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| V4_0.25_against_h1_SCR | 10% | 0.4 | -0.6 | 6.8 | 22.0 | 10/9 | 10/10 | NO |
| V4_0.25_against_h1_SCR | 20% | 0.7 | -3.0 | 12.3 | 29.7 | 18/19 | 9/14 | NO |
| V4_0.25_against_h1_SCR | 30% | 1.1 | -22.8 | 13.8 | 33.3 | 24/28 | -29/-1 | NO |
| V4_0.25_against_h1_SCR | 50% | 1.9 | -95.3 | 9.0 | 17.7 | 24/42 | -106/-50 | NO |
| V4_0.25_against_h3_SCR | 10% | -5.3 | -5.2 | 5.1 | 23.1 | 6/8 | 6/7 | NO |
| V4_0.25_against_h3_SCR | 20% | -10.5 | -16.7 | 9.6 | 25.6 | 7/16 | 10/13 | NO |
| V4_0.25_against_h3_SCR | 30% | -15.8 | -28.1 | 7.8 | 23.7 | 8/23 | -16/-2 | NO |
| V4_0.25_against_h3_SCR | 50% | -26.3 | -74.2 | -13.5 | 1.2 | -2/25 | -84/-58 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| V4_0.25_against_h1_SCR | 0.12 | 2 | 0.50 | 0.06 / 0.09 | 0.20 / -0.54 / 0.26 / 0.12 | 0.80 | 0.21 / -0.36 / 0.28 / 0.15 |
| V4_0.25_against_h3_SCR | 0.00 | 4 | 0.50 | -0.04 / -0.01 | 0.15 / -0.45 / -0.13 / -0.00 | 0.47 | 0.16 / -0.30 / -0.12 / 0.02 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| V4_0.25_against_h1_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.50) | fail | PASS (0.27) | NO |
| V4_0.25_against_h3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | PASS (0.04) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V4_0.25_against_h1_SCR | clean | 0.93 | 1,464,526 | -156,315 | -72,526 | -49,289 | 330,600 | 4.97 | 4.43 | 12 | 1.69 | -85,452 | -80,092 | 233,696 | 7.57 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| V4_0.25_against_h1_SCR | H1 | -1.59 | -398,165 | -310,764 | -213,480 | -160,768 | 472,414 | -1.61 | -0.84 | 18 | 2.02 | -104,797 | -91,542 | 183,562 | 2.58 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V4_0.25_against_h1_SCR | H2 | 1.37 | 1,718,093 | -115,464 | -110,533 | -93,266 | 267,282 | 10.38 | 6.43 | 19 | 2.43 | -112,055 | -110,411 | 252,064 | 5.06 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| V4_0.25_against_h1_SCR | all | 0.82 | 2,784,454 | -310,764 | -120,046 | -83,351 | 481,263 | 3.51 | 5.79 | 15 | 1.93 | -112,055 | -89,871 | 252,064 | 13.97 | 41 | 1.86 | -82,524 | -79,220 | 280,110 |
| V4_0.25_against_h3_SCR | clean | 0.80 | 1,405,574 | -199,060 | -95,597 | -64,691 | 554,857 | 3.66 | 2.53 | 10 | 1.62 | -98,502 | -83,325 | 232,727 | 7.53 | 40 | 1.46 | -81,874 | -78,736 | 280,110 |
| V4_0.25_against_h3_SCR | H1 | -0.80 | -296,625 | -276,337 | -233,129 | -197,835 | 347,840 | -1.11 | -0.85 | 21 | 2.10 | -94,121 | -92,205 | 235,110 | 2.15 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V4_0.25_against_h3_SCR | H2 | 0.35 | 164,092 | -212,178 | -191,923 | -135,150 | 936,613 | 0.63 | 0.18 | 24 | 2.05 | -128,916 | -115,015 | 268,926 | 3.01 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| V4_0.25_against_h3_SCR | all | 0.49 | 1,273,040 | -276,337 | -159,446 | -112,668 | 936,613 | 1.29 | 1.36 | 15 | 1.80 | -128,916 | -93,138 | 268,926 | 11.40 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE V4
