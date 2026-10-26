> REGENERATED 2026-10-16 by worker I from outputs/autopilot/b2356/R10_*.pkl with ap_y_report.py after the original REPORT_R10.md (b2356 worker) was overwritten by an ID collision (my batch R, now REPORT_RW*). Content is the b2356 worker's result; verdict unchanged (see DECISIONS.md line 71).

# REPORT R10

**NO - 2-4 week macro REVERSAL, monthly rebalance: best selected cell R10_15_TS_h19_MACRO12: standalone Sharpe 2013-22 0.27, pair window -0.27, own-null rank pair window 0.33; additive uplift at 20% clean/H1/H2 -0.17/-0.08/-0.06, bootstrap lo -0.31; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea R10: R9 grid with the opposite sign = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 1
| cell                  |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:----------------------|-----------------:|-------------:|----------:|
| R10_10_TS_h19_MACRO12 |             1362 |         0.31 |         6 |
| R10_15_TS_h19_MACRO12 |             1361 |         0.27 |         9 |
| R10_20_TS_h19_MACRO12 |             1361 |         0.15 |         5 |
| R10_10_XS_h19_MACRO12 |              708 |         0.08 |         5 |
| R10_15_TS_h19_ALL26   |             2933 |        -0    |         5 |
| R10_20_TS_h19_ALL26   |             2939 |        -0.01 |         5 |
| R10_10_TS_h19_ALL26   |             2938 |        -0.02 |         5 |
| R10_10_XS_h19_ALL26   |             1190 |        -0.2  |         4 |
| R10_15_XS_h19_MACRO12 |              708 |        -0.3  |         3 |
| R10_20_XS_h19_ALL26   |             1190 |        -0.33 |         2 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_15_TS_h19_MACRO12 | 0.27 | 9 | -0.42 | 0.00 | 0.14 | -0.27 | 0.15 | 0.79 | 0.33 | 0.39 | 0.89 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_15_TS_h19_MACRO12 | 1.2 | 10% | -0.08 | -0.04 | -0.03 | -0.07 | 21 | -0.15 | 0.01 | 0.33 | 0.19 | NO |
| R10_15_TS_h19_MACRO12 | 1.2 | 20% | -0.17 | -0.08 | -0.06 | -0.14 | 45 | -0.31 | 0.01 | 0.33 | 0.19 | NO |
| R10_15_TS_h19_MACRO12 | 1.2 | 30% | -0.26 | -0.13 | -0.10 | -0.22 | 71 | -0.47 | 0.01 | 0.33 | 0.19 | NO |
| R10_15_TS_h19_MACRO12 | 1.2 | 50% | -0.45 | -0.23 | -0.21 | -0.40 | 123 | -0.78 | 0.01 | 0.33 | 0.19 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| R10_15_TS_h19_MACRO12 | 10% | -11.4 | -11.3 | -1.9 | -0.2 | -12/-5 | 9/10 | NO |
| R10_15_TS_h19_MACRO12 | 20% | -22.8 | -26.5 | -4.6 | -0.4 | -27/-11 | 18/21 | NO |
| R10_15_TS_h19_MACRO12 | 30% | -34.2 | -43.0 | -7.9 | -0.7 | -44/-16 | 27/31 | NO |
| R10_15_TS_h19_MACRO12 | 50% | -57.0 | -76.1 | -24.1 | -7.8 | -77/-37 | 46/48 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| R10_15_TS_h19_MACRO12 | -0.14 | 4 | 0.00 | -0.21 / -0.09 | -0.18 / -0.10 / -0.07 / -0.15 | -0.35 | -0.16 / -0.03 / -0.05 / -0.12 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| R10_15_TS_h19_MACRO12 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | fail (0.33) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_15_TS_h19_MACRO12 | clean | -0.42 | -409,647 | -213,567 | -169,904 | -141,558 | 850,592 | -0.54 | -0.48 | 45 | 1.20 | -141,129 | -114,951 | 366,023 | 3.30 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| R10_15_TS_h19_MACRO12 | H1 | 0.00 | 451 | -77,395 | -62,836 | -55,257 | 241,920 | 0.01 | 0.00 | 50 | 2.70 | -80,269 | -76,876 | 163,409 | 3.63 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| R10_15_TS_h19_MACRO12 | H2 | 0.14 | 33,434 | -143,744 | -129,256 | -93,847 | 285,107 | 0.19 | 0.12 | 43 | 2.16 | -116,955 | -97,658 | 237,111 | 3.25 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| R10_15_TS_h19_MACRO12 | all | -0.27 | -375,763 | -213,567 | -155,249 | -125,059 | 850,592 | -0.36 | -0.44 | 46 | 1.63 | -141,129 | -108,511 | 366,023 | 7.03 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE R10
