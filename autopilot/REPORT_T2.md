# REPORT T2

**NO - weekend-gap fade only when breadth is low: best selected cell T2_4_h3_SCR: standalone Sharpe 2013-22 0.63, pair window -1.55, own-null rank pair window 0.00; additive uplift at 20% clean/H1/H2 -0.19/-0.56/-0.43, bootstrap lo -0.48; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea T2: Monday gap fade only if <= q of the 16 SCR markets gapped, hold 1/3 = 6 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 6 cells; eligible 1
| cell        |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:------------|-----------------:|-------------:|----------:|
| T2_4_h3_SCR |              306 |         0.63 |         9 |
| T2_4_h1_SCR |              306 |         0.38 |         6 |
| T2_3_h3_SCR |              270 |         0.35 |         7 |
| T2_2_h3_SCR |              207 |         0.12 |         5 |
| T2_3_h1_SCR |              270 |         0.05 |         6 |
| T2_2_h1_SCR |              207 |        -0.1  |         4 |

Multiplicity: 6 cells x 5% = 0.3 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| T2_4_h3_SCR | 0.63 | 9 | -1.13 | -2.17 | -2.04 | -1.55 | 0.15 | 0.88 | 0.00 | 0.50 | 0.99 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T2_4_h3_SCR | 6.3 | 10% | -0.09 | -0.27 | -0.21 | -0.15 | 31 | -0.24 | 0.18 | 0.28 | 0.08 | NO |
| T2_4_h3_SCR | 6.3 | 20% | -0.19 | -0.56 | -0.43 | -0.30 | 62 | -0.48 | 0.18 | 0.28 | 0.08 | NO |
| T2_4_h3_SCR | 6.3 | 30% | -0.29 | -0.87 | -0.64 | -0.45 | 93 | -0.72 | 0.18 | 0.28 | 0.08 | NO |
| T2_4_h3_SCR | 6.3 | 50% | -0.50 | -1.47 | -1.05 | -0.77 | 156 | -1.17 | 0.18 | 0.28 | 0.08 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| T2_4_h3_SCR | 10% | -16.9 | -20.6 | 0.4 | 11.2 | -22/0 | 7/8 | NO |
| T2_4_h3_SCR | 20% | -33.9 | -42.0 | 0.1 | 22.3 | -43/0 | 12/15 | NO |
| T2_4_h3_SCR | 30% | -50.8 | -63.4 | -5.7 | 22.4 | -65/-2 | -12/1 | NO |
| T2_4_h3_SCR | 50% | -84.7 | -106.2 | -24.5 | -5.2 | -108/-9 | -78/-30 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| T2_4_h3_SCR | -0.30 | 4 | 0.00 | -0.30 / -0.23 | -0.20 / -0.57 / -0.43 / -0.30 | -1.59 | -0.20 / -0.44 / -0.44 / -0.29 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| T2_4_h3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.28) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T2_4_h3_SCR | clean | -1.13 | -763,142 | -258,529 | -120,088 | -92,571 | 841,035 | -1.40 | -0.91 | 27 | 1.17 | -159,432 | -102,272 | 270,243 | 4.07 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| T2_4_h3_SCR | H1 | -2.17 | -530,174 | -266,775 | -232,729 | -170,241 | 541,363 | -2.13 | -0.98 | 21 | 1.96 | -91,252 | -89,895 | 221,208 | 1.97 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| T2_4_h3_SCR | H2 | -2.04 | -570,430 | -217,633 | -211,650 | -146,726 | 639,053 | -2.05 | -0.89 | 24 | 1.62 | -142,706 | -112,615 | 282,715 | 2.09 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| T2_4_h3_SCR | all | -1.55 | -1,863,746 | -266,775 | -170,594 | -121,803 | 1,892,161 | -1.70 | -0.98 | 26 | 1.40 | -159,432 | -104,241 | 282,715 | 7.52 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE T2
