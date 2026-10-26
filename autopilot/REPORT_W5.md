# REPORT W5

**NO - time-of-day displacement vs prior close: best selected cell W5_840_1.25_follow: standalone Sharpe 2013-22 0.12, pair window -0.55, own-null rank pair window 0.38; additive uplift at 20% clean/H1/H2 -0.19/-0.05/+0.03, bootstrap lo -0.25; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea W5: at 09:30/11:00/14:00 ET displacement vs prior label-day close >= 0.75/1.25 ATR, fade or follow to the day end = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 1
| cell               |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------|-----------------:|-------------:|----------:|
| W5_570_1.25_follow |              266 |         0.39 |         7 |
| W5_840_1.25_follow |              738 |         0.12 |         7 |
| W5_660_1.25_follow |              459 |        -0.01 |         6 |
| W5_570_0.75_follow |             1510 |        -0.04 |         6 |
| W5_660_0.75_follow |             2175 |        -0.23 |         3 |
| W5_840_0.75_follow |             2823 |        -0.27 |         3 |
| W5_660_1.25_fade   |              459 |        -0.36 |         2 |
| W5_570_1.25_fade   |              266 |        -0.65 |         2 |
| W5_570_0.75_fade   |             1510 |        -0.76 |         1 |
| W5_660_0.75_fade   |             2175 |        -0.89 |         2 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| W5_840_1.25_follow | 0.12 | 7 | -1.26 | 0.33 | 0.62 | -0.55 | -0.02 | 0.46 | 0.38 | -0.00 | 0.98 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W5_840_1.25_follow | 15.5 | 10% | -0.10 | -0.02 | 0.02 | -0.06 | 11 | -0.12 | 0.08 | 0.23 | 0.10 | NO |
| W5_840_1.25_follow | 15.5 | 20% | -0.19 | -0.05 | 0.03 | -0.12 | 23 | -0.25 | 0.08 | 0.23 | 0.10 | NO |
| W5_840_1.25_follow | 15.5 | 30% | -0.30 | -0.11 | 0.03 | -0.19 | 36 | -0.38 | 0.08 | 0.23 | 0.10 | NO |
| W5_840_1.25_follow | 15.5 | 50% | -0.50 | -0.24 | -0.01 | -0.34 | 60 | -0.64 | 0.08 | 0.23 | 0.10 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| W5_840_1.25_follow | 10% | -12.1 | -1.4 | 5.4 | 4.3 | -2/4 | 7/8 | NO |
| W5_840_1.25_follow | 20% | -24.3 | -3.6 | 10.3 | 8.5 | -4/8 | 14/17 | NO |
| W5_840_1.25_follow | 30% | -36.4 | -5.8 | 15.2 | 12.8 | -7/12 | 21/25 | NO |
| W5_840_1.25_follow | 50% | -60.7 | -10.1 | 18.5 | -8.1 | -11/11 | 36/42 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| W5_840_1.25_follow | -0.12 | 4 | 0.00 | -0.18 / -0.06 | -0.24 / -0.10 / -0.01 / -0.17 | -0.90 | -0.19 / 0.00 / 0.04 / -0.11 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| W5_840_1.25_follow | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.23) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W5_840_1.25_follow | clean | -1.26 | -781,393 | -144,044 | -115,891 | -96,824 | 1,147,181 | -1.52 | -0.68 | 39 | 1.16 | -111,835 | -92,537 | 328,222 | 3.34 | 46 | 1.46 | -81,874 | -78,736 | 280,110 |
| W5_840_1.25_follow | H1 | 0.33 | 58,813 | -109,009 | -95,000 | -78,293 | 217,958 | 0.55 | 0.27 | 32 | 2.72 | -85,047 | -81,302 | 160,674 | 3.81 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| W5_840_1.25_follow | H2 | 0.62 | 147,704 | -89,122 | -72,151 | -53,351 | 148,507 | 1.41 | 0.99 | 33 | 2.32 | -86,785 | -85,905 | 225,617 | 3.57 | 44 | 2.30 | -82,524 | -81,089 | 217,425 |
| W5_840_1.25_follow | all | -0.55 | -574,875 | -144,044 | -108,865 | -88,976 | 1,147,181 | -0.78 | -0.50 | 37 | 1.66 | -111,835 | -90,839 | 328,222 | 7.66 | 45 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE W5
