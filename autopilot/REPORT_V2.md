# REPORT V2

**NO - FOMC+NFP event-day drift: best selected cell V2_long_1_h1_NQ: standalone Sharpe 2013-22 0.73, pair window 0.00, own-null rank pair window 0.50; additive uplift at 20% clean/H1/H2 +0.15/-0.31/-0.27, bootstrap lo -0.24; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea V2: long/short ES NQ ZN GC 6E on event day or day-before+event day = 20 cells (min 150 trades, small-sample).

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 20 cells; eligible 0
| cell             |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-----------------|-----------------:|-------------:|----------:|
| V2_long_2_h2_NQ  |              195 |         0.79 |         8 |
| V2_long_2_h2_ES  |              195 |         0.79 |         7 |
| V2_long_1_h1_NQ  |              196 |         0.73 |         8 |
| V2_long_1_h1_ES  |              196 |         0.61 |         7 |
| V2_long_2_h2_GC  |              193 |         0.44 |         7 |
| V2_long_1_h1_GC  |              195 |         0.43 |         8 |
| V2_long_2_h2_6E  |              195 |         0.13 |         5 |
| V2_long_1_h1_6E  |              196 |         0.01 |         5 |
| V2_long_2_h2_ZN  |              194 |        -0.2  |         4 |
| V2_short_1_h1_6E |              196 |        -0.2  |         4 |

Multiplicity: 20 cells x 5% = 1.0 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| V2_long_2_h2_NQ | 0.79 | 8 | 0.07 | -0.24 | -1.45 | -0.27 | 0.54 | 0.83 | 0.38 | 0.49 | 1.00 |
| V2_long_2_h2_ES | 0.79 | 7 | -0.22 | -0.84 | -2.25 | -0.53 | 0.40 | 0.98 | 0.15 | 0.35 | 1.00 |
| V2_long_1_h1_NQ | 0.73 | 8 | 0.60 | -1.10 | -0.99 | 0.00 | 0.55 | 0.86 | 0.50 | 0.56 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V2_long_2_h2_NQ | 12.0 | 10% | 0.01 | -0.04 | -0.13 | -0.02 | 10 | -0.12 | 0.87 | 0.50 | -0.09 | NO |
| V2_long_2_h2_NQ | 12.0 | 20% | -0.00 | -0.11 | -0.28 | -0.07 | 26 | -0.26 | 0.87 | 0.50 | -0.09 | NO |
| V2_long_2_h2_NQ | 12.0 | 30% | -0.03 | -0.18 | -0.44 | -0.14 | 45 | -0.43 | 0.87 | 0.50 | -0.09 | NO |
| V2_long_2_h2_NQ | 12.0 | 50% | -0.13 | -0.37 | -0.80 | -0.32 | 83 | -0.80 | 0.87 | 0.50 | -0.09 | NO |
| V2_long_2_h2_ES | 12.1 | 10% | -0.03 | -0.08 | -0.15 | -0.06 | 9 | -0.16 | 0.93 | 0.46 | -0.12 | NO |
| V2_long_2_h2_ES | 12.1 | 20% | -0.08 | -0.17 | -0.30 | -0.14 | 28 | -0.35 | 0.93 | 0.46 | -0.12 | NO |
| V2_long_2_h2_ES | 12.1 | 30% | -0.16 | -0.28 | -0.48 | -0.25 | 48 | -0.58 | 0.93 | 0.46 | -0.12 | NO |
| V2_long_2_h2_ES | 12.1 | 50% | -0.36 | -0.53 | -0.84 | -0.51 | 88 | -1.05 | 0.93 | 0.46 | -0.12 | NO |
| V2_long_1_h1_NQ | 17.9 | 10% | 0.09 | -0.13 | -0.12 | 0.02 | 12 | -0.10 | 0.91 | 0.26 | -0.13 | NO |
| V2_long_1_h1_NQ | 17.9 | 20% | 0.15 | -0.31 | -0.27 | -0.00 | 36 | -0.24 | 0.91 | 0.26 | -0.13 | NO |
| V2_long_1_h1_NQ | 17.9 | 30% | 0.17 | -0.52 | -0.46 | -0.05 | 59 | -0.41 | 0.91 | 0.26 | -0.13 | NO |
| V2_long_1_h1_NQ | 17.9 | 50% | 0.15 | -1.00 | -0.85 | -0.21 | 106 | -0.80 | 0.91 | 0.26 | -0.13 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| V2_long_2_h2_NQ | 10% | -11.7 | -0.3 | 6.1 | 7.1 | -1/6 | 10/10 | NO |
| V2_long_2_h2_NQ | 20% | -23.4 | -8.4 | 11.5 | 14.3 | -9/10 | 20/20 | NO |
| V2_long_2_h2_NQ | 30% | -35.1 | -18.4 | 17.0 | 14.8 | -19/15 | 30/30 | NO |
| V2_long_2_h2_NQ | 50% | -58.4 | -40.2 | -15.2 | -27.1 | -40/-12 | -7/21 | NO |
| V2_long_2_h2_ES | 10% | -13.7 | 0.5 | 5.7 | 6.6 | -0/6 | 10/10 | NO |
| V2_long_2_h2_ES | 20% | -27.4 | -10.7 | 10.7 | 13.2 | -12/10 | 20/20 | NO |
| V2_long_2_h2_ES | 30% | -41.2 | -21.8 | 14.1 | 2.9 | -23/12 | 30/30 | NO |
| V2_long_2_h2_ES | 50% | -68.6 | -110.5 | -32.9 | -97.0 | -112/-44 | -12/18 | NO |
| V2_long_1_h1_NQ | 10% | -10.0 | -3.1 | 7.9 | 9.8 | -4/7 | 10/10 | NO |
| V2_long_1_h1_NQ | 20% | -20.0 | -17.9 | 15.1 | 19.4 | -19/13 | 20/20 | NO |
| V2_long_1_h1_NQ | 30% | -30.0 | -32.6 | 16.4 | 10.5 | -34/15 | 16/22 | NO |
| V2_long_1_h1_NQ | 50% | -50.0 | -114.9 | -34.5 | -30.4 | -69/-35 | -46/-39 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| V2_long_2_h2_NQ | -0.07 | 0 | n/a | n/a / n/a | -0.00 / -0.11 / -0.28 / -0.07 | -0.28 | -0.01 / -0.06 / -0.27 / -0.08 |
| V2_long_2_h2_ES | -0.14 | 0 | n/a | n/a / n/a | -0.09 / -0.18 / -0.31 / -0.15 | -0.56 | -0.09 / -0.12 / -0.30 / -0.14 |
| V2_long_1_h1_NQ | -0.00 | 0 | n/a | n/a / n/a | 0.14 / -0.31 / -0.27 / -0.00 | -0.01 | 0.13 / -0.24 / -0.27 / -0.01 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| V2_long_2_h2_NQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | fail (0.50) | NO |
| V2_long_2_h2_ES | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | fail (0.46) | NO |
| V2_long_1_h1_NQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | PASS (0.26) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V2_long_2_h2_NQ | clean | 0.07 | 72,470 | -353,918 | -190,214 | -136,053 | 929,245 | 0.09 | 0.08 | 16 | 1.43 | -119,599 | -90,342 | 304,171 | 4.44 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| V2_long_2_h2_NQ | H1 | -0.24 | -41,992 | -175,727 | -131,348 | -97,886 | 268,104 | -0.29 | -0.16 | 11 | 2.64 | -78,287 | -77,610 | 195,834 | 2.97 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| V2_long_2_h2_NQ | H2 | -1.45 | -483,664 | -299,068 | -202,895 | -151,961 | 601,833 | -1.59 | -0.80 | 24 | 1.82 | -104,634 | -92,144 | 287,311 | 2.14 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| V2_long_2_h2_NQ | all | -0.27 | -453,186 | -353,918 | -202,724 | -143,578 | 1,515,396 | -0.36 | -0.30 | 17 | 1.71 | -119,599 | -89,403 | 304,171 | 8.38 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| V2_long_2_h2_ES | clean | -0.22 | -291,059 | -518,378 | -248,139 | -176,439 | 1,305,794 | -0.28 | -0.22 | 16 | 1.30 | -122,417 | -90,433 | 309,596 | 4.01 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| V2_long_2_h2_ES | H1 | -0.84 | -143,063 | -183,050 | -131,114 | -107,685 | 235,041 | -0.94 | -0.61 | 11 | 2.55 | -78,287 | -77,610 | 187,025 | 2.95 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V2_long_2_h2_ES | H2 | -2.25 | -564,059 | -212,239 | -178,316 | -129,259 | 618,183 | -2.26 | -0.91 | 27 | 1.79 | -105,578 | -95,239 | 262,206 | 2.26 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| V2_long_2_h2_ES | all | -0.53 | -998,181 | -518,378 | -238,779 | -164,721 | 2,050,250 | -0.66 | -0.49 | 17 | 1.60 | -122,417 | -90,384 | 309,596 | 7.71 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| V2_long_1_h1_NQ | clean | 0.60 | 761,841 | -439,514 | -232,898 | -150,362 | 871,753 | 0.82 | 0.87 | 12 | 1.63 | -131,341 | -87,432 | 283,634 | 5.49 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| V2_long_1_h1_NQ | H1 | -1.10 | -313,167 | -269,238 | -252,850 | -173,985 | 486,548 | -1.19 | -0.64 | 11 | 2.31 | -78,287 | -77,610 | 215,119 | 2.32 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| V2_long_1_h1_NQ | H2 | -0.99 | -447,805 | -422,398 | -275,679 | -192,381 | 632,728 | -1.12 | -0.71 | 22 | 1.81 | -83,671 | -81,662 | 303,347 | 2.07 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| V2_long_1_h1_NQ | all | 0.00 | 869 | -439,514 | -249,653 | -165,816 | 1,356,071 | 0.00 | 0.00 | 14 | 1.80 | -131,341 | -85,134 | 303,347 | 8.85 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE V2
