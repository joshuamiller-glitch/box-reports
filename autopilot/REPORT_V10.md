# REPORT V10

**NO - gap fade conditioned on ZN 5-day range regime: best selected cell V10_('hi', 0.67)_h1_ALL26: standalone Sharpe 2013-22 0.60, pair window 0.46, own-null rank pair window 0.95; additive uplift at 20% clean/H1/H2 -0.05/-0.23/+0.20, bootstrap lo -0.25; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea V10: W6 gap fade filtered by the ZN range percentile (lo/hi), hold 1, SCR or ALL26 = 8 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 8 cells; eligible 2
| cell                      |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:--------------------------|-----------------:|-------------:|----------:|
| V10_('hi', 0.67)_h1_SCR   |              201 |         0.63 |         7 |
| V10_('hi', 0.67)_h1_ALL26 |              511 |         0.6  |         7 |
| V10_('hi', 0.5)_h1_SCR    |              282 |         0.59 |         7 |
| V10_('hi', 0.5)_h1_ALL26  |              735 |         0.49 |         7 |
| V10_('lo', 0.5)_h1_SCR    |              261 |         0.21 |         6 |
| V10_('lo', 0.5)_h1_ALL26  |              628 |         0.13 |         6 |
| V10_('lo', 0.33)_h1_SCR   |              162 |         0.07 |         4 |
| V10_('lo', 0.33)_h1_ALL26 |              413 |         0.05 |         5 |

Multiplicity: 8 cells x 5% = 0.4 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| V10_('hi', 0.67)_h1_ALL26 | 0.60 | 7 | 0.32 | -1.20 | 0.99 | 0.46 | 0.45 | 0.46 | 0.95 | 0.14 | 1.00 |
| V10_('hi', 0.5)_h1_ALL26 | 0.49 | 7 | 0.25 | -1.19 | 0.79 | 0.35 | 0.36 | 0.58 | 0.91 | 0.11 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V10_('hi', 0.67)_h1_ALL26 | 7.4 | 10% | -0.00 | -0.11 | 0.26 | 0.04 | 5 | -0.10 | 0.27 | -0.48 | 0.04 | NO |
| V10_('hi', 0.67)_h1_ALL26 | 7.4 | 20% | -0.05 | -0.23 | 0.20 | -0.03 | 16 | -0.25 | 0.27 | -0.48 | 0.04 | NO |
| V10_('hi', 0.67)_h1_ALL26 | 7.4 | 30% | -0.13 | -0.38 | 0.03 | -0.14 | 28 | -0.44 | 0.27 | -0.48 | 0.04 | NO |
| V10_('hi', 0.67)_h1_ALL26 | 7.4 | 50% | -0.29 | -0.70 | -0.30 | -0.39 | 72 | -0.82 | 0.27 | -0.48 | 0.04 | NO |
| V10_('hi', 0.5)_h1_ALL26 | 6.5 | 10% | -0.01 | -0.09 | 0.17 | 0.01 | 4 | -0.12 | 0.27 | -0.65 | 0.05 | NO |
| V10_('hi', 0.5)_h1_ALL26 | 6.5 | 20% | -0.06 | -0.19 | 0.09 | -0.06 | 14 | -0.27 | 0.27 | -0.65 | 0.05 | NO |
| V10_('hi', 0.5)_h1_ALL26 | 6.5 | 30% | -0.13 | -0.31 | -0.08 | -0.17 | 24 | -0.45 | 0.27 | -0.65 | 0.05 | NO |
| V10_('hi', 0.5)_h1_ALL26 | 6.5 | 50% | -0.29 | -0.59 | -0.42 | -0.41 | 46 | -0.83 | 0.27 | -0.65 | 0.05 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| V10_('hi', 0.67)_h1_ALL26 | 10% | -3.6 | 4.3 | 7.4 | 3.5 | 5/7 | 7/9 | NO |
| V10_('hi', 0.67)_h1_ALL26 | 20% | -7.3 | 2.4 | 12.6 | 5.7 | 10/13 | 13/19 | NO |
| V10_('hi', 0.67)_h1_ALL26 | 30% | -10.9 | 0.6 | 12.8 | 0.4 | 1/16 | 19/23 | NO |
| V10_('hi', 0.67)_h1_ALL26 | 50% | -18.2 | -98.5 | -2.5 | -10.9 | -25/16 | 4/13 | NO |
| V10_('hi', 0.5)_h1_ALL26 | 10% | -5.7 | 5.6 | 8.4 | 4.6 | 9/9 | 8/9 | NO |
| V10_('hi', 0.5)_h1_ALL26 | 20% | -11.4 | 5.0 | 14.6 | 5.2 | 13/15 | 15/19 | NO |
| V10_('hi', 0.5)_h1_ALL26 | 30% | -17.1 | 4.5 | 17.0 | -0.4 | 7/19 | 21/27 | NO |
| V10_('hi', 0.5)_h1_ALL26 | 50% | -28.4 | -72.6 | 5.8 | -11.9 | -14/20 | 13/23 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| V10_('hi', 0.67)_h1_ALL26 | -0.03 | 2 | 0.00 | -0.08 / -0.06 | -0.07 / -0.30 / 0.17 / -0.06 | 0.39 | -0.04 / -0.19 / 0.17 / -0.00 |
| V10_('hi', 0.5)_h1_ALL26 | -0.06 | 2 | 0.00 | -0.03 / -0.03 | -0.09 / -0.25 / 0.05 / -0.09 | 0.26 | -0.05 / -0.16 / 0.06 / -0.03 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| V10_('hi', 0.67)_h1_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.48) | NO |
| V10_('hi', 0.5)_h1_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.65) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V10_('hi', 0.67)_h1_ALL26 | clean | 0.32 | 622,789 | -154,880 | -107,864 | -79,961 | 796,118 | 1.43 | 0.78 | 24 | 1.33 | -96,230 | -87,965 | 349,316 | 4.34 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| V10_('hi', 0.67)_h1_ALL26 | H1 | -1.20 | -229,767 | -203,437 | -163,953 | -125,405 | 342,083 | -1.28 | -0.67 | 14 | 2.45 | -86,510 | -79,324 | 148,241 | 3.54 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V10_('hi', 0.67)_h1_ALL26 | H2 | 0.99 | 1,315,416 | -371,829 | -232,358 | -133,072 | 399,977 | 4.02 | 3.29 | 11 | 2.29 | -105,282 | -92,468 | 228,223 | 5.06 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| V10_('hi', 0.67)_h1_ALL26 | all | 0.46 | 1,708,438 | -371,829 | -152,611 | -104,474 | 796,118 | 1.72 | 2.15 | 20 | 1.71 | -105,282 | -88,804 | 349,316 | 9.15 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |
| V10_('hi', 0.5)_h1_ALL26 | clean | 0.25 | 432,435 | -137,057 | -99,294 | -76,602 | 807,137 | 1.05 | 0.54 | 30 | 1.33 | -91,870 | -85,574 | 351,513 | 4.15 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| V10_('hi', 0.5)_h1_ALL26 | H1 | -1.19 | -205,722 | -180,026 | -145,085 | -110,974 | 272,032 | -1.28 | -0.76 | 18 | 2.52 | -84,750 | -78,798 | 145,869 | 3.65 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V10_('hi', 0.5)_h1_ALL26 | H2 | 0.79 | 931,732 | -329,039 | -229,317 | -151,098 | 582,566 | 2.92 | 1.60 | 22 | 2.18 | -102,075 | -90,864 | 226,980 | 4.59 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| V10_('hi', 0.5)_h1_ALL26 | all | 0.35 | 1,158,445 | -329,039 | -144,304 | -103,034 | 807,137 | 1.23 | 1.44 | 27 | 1.69 | -102,075 | -86,658 | 351,513 | 8.63 | 44 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE V10
