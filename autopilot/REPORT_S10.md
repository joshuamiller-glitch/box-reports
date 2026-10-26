# REPORT S10

**NO - Monday -> Tuesday reversal/continuation by asset class: best selected cell S10_fade_h1_EQ: standalone Sharpe 2013-22 0.53, pair window -0.07, own-null rank pair window 0.43; additive uplift at 20% clean/H1/H2 +0.02/-0.28/+0.05, bootstrap lo -0.16; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea S10: Monday candle z >= 0.5, Tuesday fade/follow by class = 10 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 10 cells; eligible 1
| cell                |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:--------------------|-----------------:|-------------:|----------:|
| S10_fade_h1_EQ      |              793 |         0.53 |         7 |
| S10_follow_h1_EN    |              932 |         0.11 |         5 |
| S10_follow_h1_MET   |              830 |         0.07 |         4 |
| S10_fade_h1_FX      |             1002 |        -0.27 |         4 |
| S10_follow_h1_FX    |             1002 |        -0.31 |         3 |
| S10_fade_h1_EN      |              932 |        -0.38 |         3 |
| S10_fade_h1_MET     |              830 |        -0.47 |         3 |
| S10_follow_h1_RATES |              840 |        -0.54 |         3 |
| S10_fade_h1_RATES   |              840 |        -0.68 |         3 |
| S10_follow_h1_EQ    |              793 |        -0.74 |         2 |

Multiplicity: 10 cells x 5% = 0.5 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| S10_fade_h1_EQ | 0.53 | 7 | 0.14 | -1.17 | 0.16 | -0.07 | 0.42 | 0.92 | 0.43 | 0.25 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S10_fade_h1_EQ | 5.6 | 10% | 0.02 | -0.13 | 0.03 | 0.00 | 6 | -0.07 | 0.88 | 0.25 | -0.08 | NO |
| S10_fade_h1_EQ | 5.6 | 20% | 0.02 | -0.28 | 0.05 | -0.01 | 12 | -0.16 | 0.88 | 0.25 | -0.08 | NO |
| S10_fade_h1_EQ | 5.6 | 30% | 0.02 | -0.44 | 0.05 | -0.04 | 19 | -0.26 | 0.88 | 0.25 | -0.08 | NO |
| S10_fade_h1_EQ | 5.6 | 50% | -0.01 | -0.79 | 0.01 | -0.12 | 32 | -0.49 | 0.88 | 0.25 | -0.08 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| S10_fade_h1_EQ | 10% | -10.3 | 4.2 | 8.4 | 9.6 | 3/9 | 4/7 | NO |
| S10_fade_h1_EQ | 20% | -20.6 | 7.7 | 15.9 | 19.2 | 7/17 | 6/14 | NO |
| S10_fade_h1_EQ | 30% | -30.9 | 11.1 | 22.6 | 28.8 | 10/24 | 8/21 | NO |
| S10_fade_h1_EQ | 50% | -51.6 | -15.8 | 11.0 | 25.5 | -4/19 | -1/5 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| S10_fade_h1_EQ | -0.01 | 0 | n/a | n/a / n/a | 0.01 / -0.29 / 0.05 / -0.02 | -0.12 | 0.02 / -0.22 / 0.07 / -0.01 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| S10_fade_h1_EQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | PASS (0.25) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S10_fade_h1_EQ | clean | 0.14 | 106,765 | -202,458 | -119,826 | -94,148 | 329,527 | 0.21 | 0.32 | 33 | 1.48 | -97,940 | -82,414 | 283,351 | 4.81 | 40 | 1.46 | -81,874 | -78,736 | 280,110 |
| S10_fade_h1_EQ | H1 | -1.17 | -236,172 | -151,923 | -122,707 | -106,959 | 559,084 | -1.43 | -0.42 | 43 | 2.39 | -95,229 | -84,518 | 168,626 | 3.10 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| S10_fade_h1_EQ | H2 | 0.16 | 44,565 | -231,339 | -164,931 | -104,462 | 271,042 | 0.20 | 0.16 | 27 | 2.31 | -92,232 | -84,689 | 204,924 | 3.78 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| S10_fade_h1_EQ | all | -0.07 | -84,842 | -231,339 | -135,290 | -103,113 | 559,084 | -0.09 | -0.15 | 34 | 1.82 | -97,940 | -84,356 | 283,351 | 9.39 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE S10
