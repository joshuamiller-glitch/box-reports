> REGENERATED 2026-10-16 by worker I from outputs/autopilot/b2356/R9_*.pkl with ap_y_report.py after the original REPORT_R9.md (b2356 worker) was overwritten by an ID collision (my batch R, now REPORT_RW*). Content is the b2356 worker's result; verdict unchanged (see DECISIONS.md line 71).

# REPORT R9

**NO - 2-4 week macro momentum, monthly rebalance (TS and XS): best selected cell R9_20_XS_h19_MACRO12: standalone Sharpe 2013-22 0.27, pair window 0.74, own-null rank pair window 0.94; additive uplift at 20% clean/H1/H2 +0.17/+0.08/+0.04, bootstrap lo -0.04; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea R9: 10/15/20-day z, monthly, hold 19 days, time-series sign or cross-sectional top/bottom, ALL26 or macro12 = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 2
| cell                 |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:---------------------|-----------------:|-------------:|----------:|
| R9_20_XS_h19_MACRO12 |              708 |         0.27 |         7 |
| R9_15_XS_h19_ALL26   |             1190 |         0.24 |         6 |
| R9_15_XS_h19_MACRO12 |              708 |         0.14 |         5 |
| R9_20_XS_h19_ALL26   |             1190 |         0.12 |         7 |
| R9_10_XS_h19_ALL26   |             1190 |        -0.01 |         6 |
| R9_10_TS_h19_ALL26   |             2938 |        -0.24 |         4 |
| R9_10_XS_h19_MACRO12 |              708 |        -0.25 |         3 |
| R9_15_TS_h19_ALL26   |             2933 |        -0.25 |         2 |
| R9_20_TS_h19_ALL26   |             2939 |        -0.25 |         4 |
| R9_20_TS_h19_MACRO12 |             1361 |        -0.33 |         3 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| R9_20_XS_h19_MACRO12 | 0.27 | 7 | 0.85 | 0.81 | 0.27 | 0.74 | 0.38 | 0.79 | 0.94 | 0.38 | 0.88 |
| R9_20_XS_h19_ALL26 | 0.12 | 7 | 0.32 | 0.89 | 0.40 | 0.42 | 0.14 | 0.87 | 0.81 | 0.25 | 0.85 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9_20_XS_h19_MACRO12 | 2.0 | 10% | 0.09 | 0.05 | 0.02 | 0.07 | 3 | -0.01 | 0.89 | -0.53 | -0.09 | NO |
| R9_20_XS_h19_MACRO12 | 2.0 | 20% | 0.17 | 0.08 | 0.04 | 0.13 | 13 | -0.04 | 0.89 | -0.53 | -0.09 | NO |
| R9_20_XS_h19_MACRO12 | 2.0 | 30% | 0.23 | 0.09 | 0.04 | 0.18 | 23 | -0.08 | 0.89 | -0.53 | -0.09 | NO |
| R9_20_XS_h19_MACRO12 | 2.0 | 50% | 0.29 | 0.08 | 0.03 | 0.21 | 43 | -0.20 | 0.89 | -0.53 | -0.09 | NO |
| R9_20_XS_h19_ALL26 | 1.2 | 10% | 0.04 | -0.01 | 0.04 | 0.05 | 7 | -0.05 | 0.83 | -0.22 | -0.08 | NO |
| R9_20_XS_h19_ALL26 | 1.2 | 20% | 0.07 | -0.04 | 0.07 | 0.07 | 20 | -0.11 | 0.83 | -0.22 | -0.08 | NO |
| R9_20_XS_h19_ALL26 | 1.2 | 30% | 0.09 | -0.08 | 0.09 | 0.09 | 33 | -0.18 | 0.83 | -0.22 | -0.08 | NO |
| R9_20_XS_h19_ALL26 | 1.2 | 50% | 0.07 | -0.20 | 0.07 | 0.06 | 60 | -0.37 | 0.83 | -0.22 | -0.08 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| R9_20_XS_h19_MACRO12 | 10% | -6.4 | 6.1 | 7.7 | 13.8 | 5/6 | 6/11 | NO |
| R9_20_XS_h19_MACRO12 | 20% | -12.8 | 5.5 | 13.4 | 20.3 | 5/11 | 13/21 | NO |
| R9_20_XS_h19_MACRO12 | 30% | -19.2 | 4.9 | 16.7 | 21.6 | 4/13 | 19/32 | NO |
| R9_20_XS_h19_MACRO12 | 50% | -32.0 | 3.6 | 15.0 | 23.7 | 3/10 | 31/31 | NO |
| R9_20_XS_h19_ALL26 | 10% | -7.9 | 2.3 | 6.8 | 0.3 | 2/8 | -3/1 | NO |
| R9_20_XS_h19_ALL26 | 20% | -15.7 | -1.2 | 11.0 | 0.7 | -2/14 | -6/2 | NO |
| R9_20_XS_h19_ALL26 | 30% | -23.6 | -5.2 | 13.8 | 1.0 | -6/18 | -9/4 | NO |
| R9_20_XS_h19_ALL26 | 50% | -39.3 | -13.1 | 11.1 | -0.3 | -14/9 | -15/6 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| R9_20_XS_h19_MACRO12 | 0.13 | 4 | 0.50 | -0.03 / 0.11 | 0.16 / 0.07 / 0.03 / 0.12 | 0.68 | 0.17 / 0.10 / 0.01 / 0.13 |
| R9_20_XS_h19_ALL26 | 0.07 | 4 | 0.75 | 0.02 / 0.09 | 0.06 / -0.06 / 0.06 / 0.06 | 0.35 | 0.08 / 0.05 / 0.05 / 0.08 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| R9_20_XS_h19_MACRO12 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | PASS (-0.53) | NO |
| R9_20_XS_h19_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | PASS (0.75) | fail | PASS (-0.22) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9_20_XS_h19_MACRO12 | clean | 0.85 | 774,853 | -149,545 | -125,241 | -105,620 | 334,938 | 1.33 | 2.31 | 38 | 1.69 | -101,620 | -89,793 | 288,465 | 5.42 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| R9_20_XS_h19_MACRO12 | H1 | 0.81 | 133,622 | -115,313 | -92,501 | -82,321 | 185,913 | 1.16 | 0.72 | 36 | 2.92 | -86,602 | -75,873 | 148,959 | 4.26 | 46 | 2.83 | -78,287 | -77,610 | 151,713 |
| R9_20_XS_h19_MACRO12 | H2 | 0.27 | 57,585 | -86,832 | -77,083 | -68,433 | 240,048 | 0.40 | 0.24 | 41 | 2.30 | -87,235 | -81,235 | 220,148 | 3.54 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| R9_20_XS_h19_MACRO12 | all | 0.74 | 966,060 | -149,545 | -115,876 | -96,495 | 334,938 | 1.14 | 2.88 | 39 | 2.03 | -101,620 | -87,576 | 288,465 | 10.31 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| R9_20_XS_h19_ALL26 | clean | 0.32 | 281,170 | -134,308 | -116,776 | -101,095 | 600,728 | 0.49 | 0.47 | 50 | 1.55 | -109,913 | -86,830 | 361,366 | 3.91 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| R9_20_XS_h19_ALL26 | H1 | 0.89 | 178,885 | -113,865 | -107,846 | -92,590 | 240,723 | 1.33 | 0.74 | 39 | 2.74 | -108,835 | -98,100 | 189,186 | 3.42 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| R9_20_XS_h19_ALL26 | H2 | 0.40 | 112,096 | -114,834 | -109,147 | -94,449 | 287,749 | 0.60 | 0.39 | 38 | 2.35 | -89,292 | -89,203 | 227,477 | 3.49 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| R9_20_XS_h19_ALL26 | all | 0.42 | 572,151 | -134,308 | -114,420 | -99,608 | 600,728 | 0.65 | 0.95 | 46 | 1.94 | -109,913 | -90,770 | 361,366 | 7.91 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE R9
