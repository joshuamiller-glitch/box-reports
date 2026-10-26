# REPORT T1b

**NO - session-aligned weekend-gap fade/follow, 150-trade floor (T1b amendment): best selected cell T1_0.25_1_fade: standalone Sharpe 2013-22 0.56, pair window 0.83, own-null rank pair window 0.99; additive uplift at 20% clean/H1/H2 +0.15/-0.16/+0.18, bootstrap lo -0.07; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea T1b: same 18 T1 cells with the sample floor lowered to 150 trades (dev-only information, pre-registered amendment).

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 18 cells; eligible 0
| cell            |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:----------------|-----------------:|-------------:|----------:|
| T1_1.0_4_fade   |               10 |         0.62 |         5 |
| T1_0.25_2_fade  |              167 |         0.59 |         7 |
| T1_1.0_2_fade   |               10 |         0.57 |         5 |
| T1_0.25_1_fade  |              164 |         0.56 |         7 |
| T1_0.25_4_fade  |              170 |         0.49 |         8 |
| T1_0.5_2_fade   |               65 |         0.28 |         8 |
| T1_1.0_1_fade   |               11 |         0.22 |         5 |
| T1_0.5_4_fade   |               69 |         0.2  |         6 |
| T1_0.5_1_fade   |               67 |         0.19 |         7 |
| T1_0.5_4_follow |               69 |        -0.3  |         3 |

Multiplicity: 18 cells x 5% = 0.9 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 0.59 | 7 | 0.79 | -1.86 | 1.30 | 0.72 | 0.59 | 0.66 | 0.96 | 0.30 | 0.99 |
| T1_0.25_1_fade | 0.56 | 7 | 0.87 | -0.61 | 1.29 | 0.83 | 0.62 | 0.65 | 0.99 | 0.28 | 1.00 |
| T1_0.25_4_fade | 0.49 | 8 | 0.58 | -1.70 | 0.98 | 0.54 | 0.47 | 0.83 | 0.90 | 0.24 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 14.9 | 10% | 0.09 | -0.25 | 0.18 | 0.07 | 13 | -0.05 | 0.08 | 0.57 | 0.10 | NO |
| T1_0.25_2_fade | 14.9 | 20% | 0.15 | -0.51 | 0.16 | 0.06 | 25 | -0.14 | 0.08 | 0.57 | 0.10 | NO |
| T1_0.25_2_fade | 14.9 | 30% | 0.16 | -0.77 | 0.06 | 0.01 | 38 | -0.25 | 0.08 | 0.57 | 0.10 | NO |
| T1_0.25_2_fade | 14.9 | 50% | 0.12 | -1.26 | -0.15 | -0.15 | 64 | -0.53 | 0.08 | 0.57 | 0.10 | NO |
| T1_0.25_1_fade | 13.5 | 10% | 0.09 | -0.07 | 0.18 | 0.09 | 11 | -0.03 | 0.09 | 0.56 | 0.09 | NO |
| T1_0.25_1_fade | 13.5 | 20% | 0.15 | -0.16 | 0.18 | 0.11 | 22 | -0.07 | 0.09 | 0.56 | 0.09 | NO |
| T1_0.25_1_fade | 13.5 | 30% | 0.18 | -0.27 | 0.10 | 0.09 | 33 | -0.16 | 0.09 | 0.56 | 0.09 | NO |
| T1_0.25_1_fade | 13.5 | 50% | 0.17 | -0.52 | -0.11 | -0.03 | 55 | -0.38 | 0.09 | 0.56 | 0.09 | NO |
| T1_0.25_4_fade | 12.9 | 10% | 0.05 | -0.16 | 0.14 | 0.04 | 8 | -0.07 | 0.18 | 0.51 | 0.07 | NO |
| T1_0.25_4_fade | 12.9 | 20% | 0.07 | -0.33 | 0.11 | 0.03 | 17 | -0.16 | 0.18 | 0.51 | 0.07 | NO |
| T1_0.25_4_fade | 12.9 | 30% | 0.07 | -0.50 | -0.01 | -0.03 | 25 | -0.28 | 0.18 | 0.51 | 0.07 | NO |
| T1_0.25_4_fade | 12.9 | 50% | 0.02 | -0.84 | -0.27 | -0.19 | 42 | -0.54 | 0.18 | 0.51 | 0.07 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 10% | -1.7 | -2.6 | 7.7 | 20.4 | 10/10 | 9/9 | NO |
| T1_0.25_2_fade | 20% | -3.4 | -5.2 | 15.0 | 29.2 | 20/20 | 16/16 | NO |
| T1_0.25_2_fade | 30% | -5.1 | -7.9 | 18.8 | 38.1 | 30/30 | -7/7 | NO |
| T1_0.25_2_fade | 50% | -8.5 | -48.4 | 17.7 | 30.7 | 33/45 | -56/-18 | NO |
| T1_0.25_1_fade | 10% | -1.2 | -0.9 | 8.2 | 20.4 | 10/10 | 10/10 | NO |
| T1_0.25_1_fade | 20% | -2.4 | -1.9 | 16.3 | 25.3 | 20/20 | 20/19 | NO |
| T1_0.25_1_fade | 30% | -3.5 | -2.8 | 22.5 | 29.7 | 30/30 | 13/20 | INSURANCE |
| T1_0.25_1_fade | 50% | -5.9 | -16.7 | 21.0 | 24.6 | 36/47 | -23/7 | NO |
| T1_0.25_4_fade | 10% | -4.5 | 1.5 | 8.3 | 20.4 | 10/10 | 9/9 | NO |
| T1_0.25_4_fade | 20% | -9.1 | 3.0 | 15.7 | 29.2 | 18/19 | 17/18 | NO |
| T1_0.25_4_fade | 30% | -13.6 | 4.5 | 21.8 | 33.7 | 9/26 | 25/27 | NO |
| T1_0.25_4_fade | 50% | -22.7 | -9.1 | 15.1 | 20.2 | -10/37 | 9/11 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 0.06 | 3 | 0.67 | -0.01 / 0.07 | 0.14 / -0.53 / 0.15 / 0.05 | 0.69 | 0.15 / -0.36 / 0.17 / 0.09 |
| T1_0.25_1_fade | 0.11 | 3 | 0.00 | 0.05 / 0.07 | 0.14 / -0.18 / 0.16 / 0.10 | 0.80 | 0.15 / -0.11 / 0.20 / 0.14 |
| T1_0.25_4_fade | 0.03 | 3 | 0.67 | -0.04 / 0.03 | 0.06 / -0.35 / 0.09 / 0.02 | 0.51 | 0.08 / -0.23 / 0.10 / 0.05 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.67) | fail | fail (0.57) | NO |
| T1_0.25_1_fade | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.00) | fail | fail (0.56) | NO |
| T1_0.25_4_fade | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.67) | fail | fail (0.51) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T1_0.25_2_fade | clean | 0.79 | 1,180,405 | -156,147 | -78,661 | -42,906 | 212,386 | 3.71 | 5.56 | 5 | 1.62 | -81,874 | -78,736 | 247,894 | 6.79 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| T1_0.25_2_fade | H1 | -1.86 | -392,291 | -219,122 | -156,612 | -135,278 | 421,415 | -2.02 | -0.93 | 25 | 2.06 | -91,551 | -87,517 | 169,839 | 2.80 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| T1_0.25_2_fade | H2 | 1.30 | 1,438,304 | -141,990 | -125,345 | -107,108 | 468,804 | 7.47 | 3.07 | 19 | 2.36 | -113,778 | -102,076 | 230,383 | 5.18 | 50 | 2.30 | -82,524 | -81,089 | 217,425 |
| T1_0.25_2_fade | all | 0.72 | 2,226,419 | -219,122 | -122,227 | -88,858 | 533,463 | 2.98 | 4.17 | 11 | 1.87 | -113,778 | -86,328 | 247,894 | 13.53 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |
| T1_0.25_1_fade | clean | 0.87 | 1,126,627 | -100,368 | -67,440 | -36,785 | 172,551 | 4.53 | 6.53 | 6 | 1.64 | -81,874 | -78,736 | 267,168 | 6.24 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| T1_0.25_1_fade | H1 | -0.61 | -117,289 | -166,760 | -128,406 | -101,579 | 349,143 | -0.81 | -0.34 | 25 | 2.56 | -78,835 | -78,561 | 154,130 | 3.62 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| T1_0.25_1_fade | H2 | 1.29 | 1,359,746 | -218,812 | -169,218 | -123,748 | 502,535 | 5.80 | 2.71 | 17 | 2.39 | -109,604 | -99,221 | 228,848 | 5.11 | 47 | 2.30 | -82,524 | -81,089 | 217,425 |
| T1_0.25_1_fade | all | 0.83 | 2,369,083 | -218,812 | -112,833 | -78,460 | 502,535 | 3.42 | 4.71 | 11 | 1.94 | -109,604 | -83,640 | 267,168 | 12.71 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| T1_0.25_4_fade | clean | 0.58 | 728,139 | -127,947 | -91,506 | -52,345 | 354,795 | 2.22 | 2.05 | 7 | 1.53 | -90,549 | -80,942 | 248,777 | 6.22 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| T1_0.25_4_fade | H1 | -1.70 | -246,263 | -115,340 | -111,791 | -93,103 | 246,263 | -1.96 | -1.00 | 25 | 2.33 | -82,169 | -80,228 | 157,653 | 3.30 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| T1_0.25_4_fade | H2 | 0.98 | 986,399 | -193,721 | -189,843 | -134,193 | 527,178 | 3.94 | 1.87 | 17 | 2.28 | -103,550 | -96,678 | 229,815 | 4.60 | 50 | 2.30 | -82,524 | -81,089 | 217,425 |
| T1_0.25_4_fade | all | 0.54 | 1,468,274 | -193,721 | -121,855 | -89,346 | 527,178 | 1.96 | 2.79 | 12 | 1.83 | -103,550 | -84,871 | 248,777 | 12.56 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE T1b
