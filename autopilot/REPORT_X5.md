# REPORT X5

**NO - daily-candle follow-through (body ratio >= 0.6/0.8, range >= 1.0/1.5 ATR): best selected cell X5_0.8_1.5_h3_COM+RATES: standalone Sharpe 2013-22 0.42, pair window -0.16, own-null rank pair window 0.63; additive uplift at 20% clean/H1/H2 +0.16/-0.26/-0.40, bootstrap lo -0.24; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea X5: follow candles with body ratio >= b and range >= r ATR20; hold 1/3; ALL26 or COM+RATES = 16 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 16 cells; eligible 2
| cell                    |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:------------------------|-----------------:|-------------:|----------:|
| X5_0.8_1.5_h3_ALL26     |             2191 |         0.52 |         7 |
| X5_0.8_1.5_h3_COM+RATES |             1360 |         0.42 |         7 |
| X5_0.6_1.5_h3_ALL26     |             5172 |         0.35 |         6 |
| X5_0.6_1.5_h3_COM+RATES |             3283 |         0.21 |         5 |
| X5_0.8_1_h3_ALL26       |             4460 |         0.21 |         5 |
| X5_0.8_1_h3_COM+RATES   |             2874 |         0.11 |         4 |
| X5_0.6_1_h3_ALL26       |            10756 |        -0.02 |         6 |
| X5_0.6_1_h3_COM+RATES   |             6989 |        -0.06 |         5 |
| X5_0.8_1_h1_COM+RATES   |             3244 |        -0.43 |         4 |
| X5_0.8_1.5_h1_ALL26     |             2346 |        -0.45 |         4 |

Multiplicity: 16 cells x 5% = 0.8 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X5_0.8_1.5_h3_ALL26 | 0.52 | 7 | 0.08 | -1.72 | -1.34 | -0.61 | 0.30 | 0.47 | 0.36 | 0.13 | 1.00 |
| X5_0.8_1.5_h3_COM+RATES | 0.42 | 7 | 0.95 | -1.22 | -1.66 | -0.16 | 0.35 | 0.65 | 0.63 | 0.12 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X5_0.8_1.5_h3_ALL26 | 2.4 | 10% | 0.02 | -0.15 | -0.12 | -0.04 | 4 | -0.12 | 1.00 | -0.09 | -0.16 | NO |
| X5_0.8_1.5_h3_ALL26 | 2.4 | 20% | 0.04 | -0.38 | -0.25 | -0.09 | 12 | -0.27 | 1.00 | -0.09 | -0.16 | NO |
| X5_0.8_1.5_h3_ALL26 | 2.4 | 30% | 0.04 | -0.68 | -0.38 | -0.16 | 32 | -0.43 | 1.00 | -0.09 | -0.16 | NO |
| X5_0.8_1.5_h3_ALL26 | 2.4 | 50% | 0.02 | -1.36 | -0.65 | -0.34 | 99 | -0.77 | 1.00 | -0.09 | -0.16 | NO |
| X5_0.8_1.5_h3_COM+RATES | 3.5 | 10% | 0.08 | -0.09 | -0.20 | -0.01 | 12 | -0.11 | 0.87 | 0.17 | -0.09 | NO |
| X5_0.8_1.5_h3_COM+RATES | 3.5 | 20% | 0.16 | -0.26 | -0.40 | -0.04 | 25 | -0.24 | 0.87 | 0.17 | -0.09 | NO |
| X5_0.8_1.5_h3_COM+RATES | 3.5 | 30% | 0.22 | -0.52 | -0.61 | -0.09 | 38 | -0.39 | 0.87 | 0.17 | -0.09 | NO |
| X5_0.8_1.5_h3_COM+RATES | 3.5 | 50% | 0.30 | -1.15 | -1.02 | -0.23 | 64 | -0.71 | 0.87 | 0.17 | -0.09 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| X5_0.8_1.5_h3_ALL26 | 10% | -13.1 | 5.5 | 6.6 | 7.9 | 8/8 | 22/23 | NO |
| X5_0.8_1.5_h3_ALL26 | 20% | -26.1 | 6.5 | 11.0 | 15.8 | 16/15 | 11/27 | NO |
| X5_0.8_1.5_h3_ALL26 | 30% | -39.2 | -22.6 | 12.2 | 23.8 | 21/22 | -16/20 | NO |
| X5_0.8_1.5_h3_ALL26 | 50% | -65.3 | -83.0 | 1.7 | 25.5 | 4/26 | -71/-22 | NO |
| X5_0.8_1.5_h3_COM+RATES | 10% | -10.9 | -2.3 | 3.2 | 2.8 | -3/6 | 26/26 | NO |
| X5_0.8_1.5_h3_COM+RATES | 20% | -21.8 | -5.4 | 5.3 | 5.5 | -6/11 | 28/38 | NO |
| X5_0.8_1.5_h3_COM+RATES | 30% | -32.8 | -8.5 | 3.2 | 8.3 | -9/13 | 9/24 | NO |
| X5_0.8_1.5_h3_COM+RATES | 50% | -54.6 | -42.3 | -15.3 | 13.2 | -16/15 | -28/-18 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| X5_0.8_1.5_h3_ALL26 | -0.09 | 6 | 0.00 | -0.25 / -0.15 | -0.01 / -0.45 / -0.29 / -0.14 | -0.85 | 0.04 / -0.34 / -0.24 / -0.08 |
| X5_0.8_1.5_h3_COM+RATES | -0.04 | 6 | 0.00 | -0.19 / -0.11 | 0.11 / -0.34 / -0.45 / -0.09 | -0.41 | 0.16 / -0.24 / -0.39 / -0.02 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| X5_0.8_1.5_h3_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.09) | NO |
| X5_0.8_1.5_h3_COM+RATES | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.17) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X5_0.8_1.5_h3_ALL26 | clean | 0.08 | 62,841 | -247,289 | -127,051 | -95,384 | 529,980 | 0.11 | 0.12 | 44 | 1.50 | -87,873 | -84,515 | 297,591 | 4.53 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| X5_0.8_1.5_h3_ALL26 | H1 | -1.72 | -550,468 | -240,897 | -206,359 | -181,076 | 551,535 | -1.92 | -1.00 | 54 | 2.15 | -98,653 | -74,963 | 144,827 | 2.96 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| X5_0.8_1.5_h3_ALL26 | H2 | -1.34 | -331,537 | -199,538 | -138,613 | -104,333 | 548,903 | -1.50 | -0.60 | 49 | 1.88 | -100,264 | -99,416 | 210,718 | 3.14 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| X5_0.8_1.5_h3_ALL26 | all | -0.61 | -819,163 | -275,702 | -169,447 | -127,872 | 1,137,003 | -0.73 | -0.72 | 46 | 1.69 | -109,095 | -91,224 | 297,591 | 8.20 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| X5_0.8_1.5_h3_COM+RATES | clean | 0.95 | 734,166 | -139,918 | -116,127 | -95,237 | 539,911 | 1.48 | 1.36 | 38 | 1.68 | -114,099 | -90,167 | 340,981 | 4.55 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| X5_0.8_1.5_h3_COM+RATES | H1 | -1.22 | -431,048 | -248,756 | -211,683 | -195,549 | 456,626 | -1.47 | -0.94 | 54 | 2.31 | -78,767 | -65,577 | 150,136 | 3.09 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| X5_0.8_1.5_h3_COM+RATES | H2 | -1.66 | -551,035 | -239,935 | -181,403 | -144,977 | 787,934 | -1.86 | -0.70 | 51 | 1.65 | -112,740 | -110,965 | 226,339 | 2.63 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| X5_0.8_1.5_h3_COM+RATES | all | -0.16 | -247,917 | -248,756 | -165,390 | -134,256 | 1,175,465 | -0.21 | -0.21 | 43 | 1.77 | -114,099 | -97,864 | 340,981 | 7.66 | 41 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE X5
