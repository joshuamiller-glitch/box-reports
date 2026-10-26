# REPORT W2

**NO - session-block momentum/reversal: best selected cell W2_b_follow_0.5: standalone Sharpe 2013-22 0.27, pair window 0.33, own-null rank pair window 0.89; additive uplift at 20% clean/H1/H2 -0.03/+0.36/+0.17, bootstrap lo -0.10; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea W2: previous session-block return (Asia/Europe/US-AM) follow or fade into the next block, thr 0/0.5 ATR = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 1
| cell            |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:----------------|-----------------:|-------------:|----------:|
| W2_b_follow_0.5 |              782 |         0.27 |         7 |
| W2_a_fade_0.5   |              678 |         0    |         4 |
| W2_c_follow_0.5 |             2965 |        -0.42 |         2 |
| W2_a_follow_0.5 |              678 |        -0.77 |         2 |
| W2_b_fade_0.5   |              782 |        -0.86 |         0 |
| W2_b_follow_0.0 |            14115 |        -1.03 |         2 |
| W2_c_fade_0.5   |             2965 |        -1.16 |         0 |
| W2_a_fade_0.0   |            14114 |        -1.55 |         1 |
| W2_c_follow_0.0 |            14115 |        -1.69 |         0 |
| W2_c_fade_0.0   |            14115 |        -2.16 |         0 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| W2_b_follow_0.5 | 0.27 | 7 | -0.11 | 0.95 | 1.22 | 0.33 | 0.27 | 0.54 | 0.89 | -0.01 | 0.99 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W2_b_follow_0.5 | 10.3 | 10% | -0.01 | 0.20 | 0.09 | 0.04 | 3 | -0.04 | 0.82 | -0.27 | -0.07 | NO |
| W2_b_follow_0.5 | 10.3 | 20% | -0.03 | 0.36 | 0.17 | 0.06 | 13 | -0.10 | 0.82 | -0.27 | -0.07 | NO |
| W2_b_follow_0.5 | 10.3 | 30% | -0.07 | 0.47 | 0.23 | 0.06 | 22 | -0.19 | 0.82 | -0.27 | -0.07 | NO |
| W2_b_follow_0.5 | 10.3 | 50% | -0.17 | 0.52 | 0.29 | 0.00 | 41 | -0.40 | 0.82 | -0.27 | -0.07 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| W2_b_follow_0.5 | 10% | -8.2 | 6.0 | 7.1 | 12.5 | 7/7 | 13/21 | NO |
| W2_b_follow_0.5 | 20% | -16.3 | 5.9 | 13.3 | 24.9 | 9/13 | 24/39 | NO |
| W2_b_follow_0.5 | 30% | -24.5 | 5.7 | 18.1 | 37.1 | 12/17 | 35/47 | NO |
| W2_b_follow_0.5 | 50% | -40.9 | -33.8 | 8.6 | 17.0 | -35/6 | 3/30 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| W2_b_follow_0.5 | 0.06 | 2 | 0.50 | -0.05 / 0.01 | -0.06 / 0.30 / 0.14 / 0.03 | 0.18 | -0.03 / 0.24 / 0.17 / 0.06 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| W2_b_follow_0.5 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | PASS (-0.27) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W2_b_follow_0.5 | clean | -0.11 | -102,021 | -391,786 | -165,426 | -114,496 | 571,963 | -0.14 | -0.18 | 31 | 1.39 | -95,539 | -87,199 | 259,402 | 5.01 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| W2_b_follow_0.5 | H1 | 0.95 | 250,234 | -234,185 | -142,938 | -106,600 | 301,151 | 1.38 | 0.83 | 36 | 3.30 | -73,934 | -59,300 | 151,996 | 4.40 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| W2_b_follow_0.5 | H2 | 1.22 | 342,605 | -92,185 | -86,911 | -79,196 | 111,902 | 2.53 | 3.06 | 31 | 2.52 | -101,006 | -90,390 | 237,169 | 3.64 | 42 | 2.30 | -82,524 | -81,089 | 217,425 |
| W2_b_follow_0.5 | all | 0.33 | 490,817 | -391,786 | -156,096 | -109,536 | 571,963 | 0.47 | 0.86 | 32 | 1.91 | -101,006 | -87,302 | 259,402 | 10.92 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE W2
