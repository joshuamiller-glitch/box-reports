# REPORT N6

**NO - overnight-range position at RTH open: best selected cell N6_0.15_follow_END: standalone Sharpe 2013-22 0.06, pair window 0.49, own-null rank pair window 0.95; additive uplift at 20% clean/H1/H2 +0.07/+0.29/-0.09, bootstrap lo -0.15; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea N6: first RTH bar close in top/bottom 15/25% of the overnight range, follow/fade, 8 cells; clean-only selection.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 8 cells; eligible 1
| cell               |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------|-----------------:|-------------:|----------:|
| N6_0.15_follow_END |       1000000000 |         0.56 |        10 |
| N6_0.25_follow_END |                0 |         0.03 |         0 |
| N6_0.15_fade_h4    |                0 |        -0.1  |         0 |
| N6_0.25_fade_h4    |                0 |        -0.21 |         0 |
| N6_0.25_fade_END   |                0 |        -0.48 |         0 |
| N6_0.25_follow_h4  |                0 |        -0.65 |         0 |
| N6_0.15_follow_h4  |                0 |        -0.66 |         0 |
| N6_0.15_fade_END   |                0 |        -0.97 |         0 |

Multiplicity: 8 cells x 5% = 0.4 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| N6_0.15_follow_END | 0.06 | 6 | 0.56 | 0.48 | 0.32 | 0.49 | 0.13 | 0.47 | 0.95 | -0.09 | 0.98 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N6_0.15_follow_END | 4.0 | 10% | 0.04 | 0.20 | -0.04 | 0.04 | 9 | -0.06 | 0.37 | 0.21 | 0.03 | NO |
| N6_0.15_follow_END | 4.0 | 20% | 0.07 | 0.29 | -0.09 | 0.05 | 24 | -0.15 | 0.37 | 0.21 | 0.03 | NO |
| N6_0.15_follow_END | 4.0 | 30% | 0.08 | 0.26 | -0.15 | 0.04 | 39 | -0.25 | 0.37 | 0.21 | 0.03 | NO |
| N6_0.15_follow_END | 4.0 | 50% | 0.07 | -0.03 | -0.28 | -0.02 | 70 | -0.49 | 0.37 | 0.21 | 0.03 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| N6_0.15_follow_END | 10% | -7.0 | 0.5 | 4.3 | 15.8 | -0/3 | 20/22 | NO |
| N6_0.15_follow_END | 20% | -14.1 | -5.4 | 8.3 | 31.5 | -6/5 | 39/43 | NO |
| N6_0.15_follow_END | 30% | -21.1 | -11.4 | 11.6 | 38.3 | -12/7 | 46/47 | NO |
| N6_0.15_follow_END | 50% | -35.2 | -43.9 | -8.1 | 28.4 | -36/-6 | -52/-37 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| N6_0.15_follow_END | 0.05 | 2 | 0.00 | 0.01 / 0.02 | 0.04 / 0.25 / -0.11 / 0.02 | 0.36 | 0.05 / 0.24 / -0.08 / 0.06 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| N6_0.15_follow_END | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.00) | fail | PASS (0.21) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N6_0.15_follow_END | clean | 0.56 | 509,757 | -266,577 | -138,468 | -113,641 | 388,924 | 0.79 | 1.31 | 46 | 1.54 | -115,050 | -96,309 | 235,853 | 6.29 | 40 | 1.46 | -81,874 | -78,736 | 280,110 |
| N6_0.15_follow_END | H1 | 0.48 | 190,382 | -310,490 | -283,028 | -214,456 | 461,752 | 0.62 | 0.41 | 39 | 3.09 | -55,512 | -54,608 | 192,762 | 3.38 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| N6_0.15_follow_END | H2 | 0.32 | 92,293 | -64,631 | -63,815 | -60,749 | 223,236 | 0.61 | 0.41 | 58 | 2.14 | -88,151 | -87,489 | 207,351 | 3.80 | 47 | 2.30 | -82,524 | -81,089 | 217,425 |
| N6_0.15_follow_END | all | 0.49 | 792,432 | -310,490 | -165,382 | -123,397 | 461,752 | 0.68 | 1.72 | 47 | 1.90 | -115,050 | -93,138 | 235,853 | 12.39 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE N6
