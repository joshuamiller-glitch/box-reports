# REPORT G1

**NO - realised-vol-regime timing, 9 instruments (GAPMAP D08 H5/H6): best selected cell G1_('hi', 0.67)_1_h5_GC: standalone Sharpe 2013-22 0.14, pair window 0.93, own-null rank pair window 0.94; additive uplift at 20% clean/H1/H2 +0.18/+0.58/-0.10, bootstrap lo -0.02; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea G1: long/short each instrument in low/high own-vol state, hold 1/5 = 72 cells; clean-only selection (ERA amendment).

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 72 cells; eligible 18
| cell                     |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------------|-----------------:|-------------:|----------:|
| G1_('lo', 0.33)_1_h5_CL  |       1000000000 |         0.99 |        10 |
| G1_('hi', 0.67)_1_h5_GC  |       1000000000 |         0.91 |        10 |
| G1_('lo', 0.33)_1_h5_NQ  |       1000000000 |         0.74 |        10 |
| G1_('hi', 0.67)_1_h5_BTC |                0 |         0.7  |         0 |
| G1_('hi', 0.67)_1_h1_BTC |       1000000000 |         0.65 |        10 |
| G1_('hi', 0.67)_-1_h1_CL |       1000000000 |         0.64 |        10 |
| G1_('hi', 0.67)_1_h1_GC  |       1000000000 |         0.61 |        10 |
| G1_('lo', 0.33)_-1_h1_YM |       1000000000 |         0.57 |        10 |
| G1_('hi', 0.67)_1_h5_ES  |       1000000000 |         0.55 |        10 |
| G1_('hi', 0.67)_-1_h5_CL |       1000000000 |         0.53 |        10 |

Multiplicity: 72 cells x 5% = 3.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G1_('lo', 0.33)_1_h5_CL | -0.15 | 5 | 0.99 | -1.54 | n/a | 0.41 | -0.05 | 0.82 | 0.80 | 0.47 | 0.41 |
| G1_('hi', 0.67)_1_h5_GC | 0.14 | 5 | 0.91 | 2.21 | -0.77 | 0.93 | 0.36 | 0.99 | 0.94 | 0.49 | 0.71 |
| G1_('lo', 0.33)_1_h5_NQ | 0.47 | 7 | 0.74 | -0.04 | 0.95 | 0.57 | 0.69 | 0.97 | 0.83 | 0.46 | 0.95 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G1_('lo', 0.33)_1_h5_CL | 6.7 | 10% | 0.11 | -0.03 | 0.00 | 0.06 | 14 | -0.02 | 0.99 | 0.06 | -0.20 | UNSCORED (does not cover H2) |
| G1_('lo', 0.33)_1_h5_CL | 6.7 | 20% | 0.21 | -0.09 | 0.00 | 0.11 | 29 | -0.07 | 0.99 | 0.06 | -0.20 | UNSCORED (does not cover H2) |
| G1_('lo', 0.33)_1_h5_CL | 6.7 | 30% | 0.29 | -0.20 | 0.00 | 0.14 | 43 | -0.12 | 0.99 | 0.06 | -0.20 | UNSCORED (does not cover H2) |
| G1_('lo', 0.33)_1_h5_CL | 6.7 | 50% | 0.40 | -0.58 | 0.00 | 0.16 | 72 | -0.27 | 0.99 | 0.06 | -0.20 | UNSCORED (does not cover H2) |
| G1_('hi', 0.67)_1_h5_GC | 7.3 | 10% | 0.10 | 0.34 | -0.04 | 0.10 | 16 | -0.00 | 0.89 | -0.20 | -0.09 | NO |
| G1_('hi', 0.67)_1_h5_GC | 7.3 | 20% | 0.18 | 0.58 | -0.10 | 0.19 | 39 | -0.02 | 0.89 | -0.20 | -0.09 | NO |
| G1_('hi', 0.67)_1_h5_GC | 7.3 | 30% | 0.25 | 0.74 | -0.16 | 0.25 | 62 | -0.06 | 0.89 | -0.20 | -0.09 | NO |
| G1_('hi', 0.67)_1_h5_GC | 7.3 | 50% | 0.33 | 0.85 | -0.31 | 0.30 | 107 | -0.18 | 0.89 | -0.20 | -0.09 | NO |
| G1_('lo', 0.33)_1_h5_NQ | 8.9 | 10% | 0.06 | -0.00 | 0.01 | 0.04 | 11 | -0.05 | 0.30 | 0.21 | 0.04 | NO |
| G1_('lo', 0.33)_1_h5_NQ | 8.9 | 20% | 0.10 | -0.08 | 0.01 | 0.06 | 33 | -0.12 | 0.30 | 0.21 | 0.04 | NO |
| G1_('lo', 0.33)_1_h5_NQ | 8.9 | 30% | 0.13 | -0.21 | 0.01 | 0.06 | 55 | -0.21 | 0.30 | 0.21 | 0.04 | NO |
| G1_('lo', 0.33)_1_h5_NQ | 8.9 | 50% | 0.15 | -0.55 | -0.02 | 0.02 | 100 | -0.40 | 0.30 | 0.21 | 0.04 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| G1_('lo', 0.33)_1_h5_CL | 10% | -8.0 | -3.9 | 8.4 | 5.3 | -5/7 | 12/19 | NO |
| G1_('lo', 0.33)_1_h5_CL | 20% | -16.1 | -8.7 | 15.9 | 10.2 | -10/14 | 21/38 | NO |
| G1_('lo', 0.33)_1_h5_CL | 30% | -24.1 | -13.4 | 22.6 | 13.9 | -14/19 | 31/40 | NO |
| G1_('lo', 0.33)_1_h5_CL | 50% | -40.2 | -48.9 | 20.4 | -3.6 | -50/11 | 28/32 | NO |
| G1_('hi', 0.67)_1_h5_GC | 10% | -4.8 | -6.8 | 5.6 | 17.6 | -8/6 | -3/19 | NO |
| G1_('hi', 0.67)_1_h5_GC | 20% | -9.6 | -20.2 | 9.8 | 28.0 | -21/11 | -6/19 | NO |
| G1_('hi', 0.67)_1_h5_GC | 30% | -14.5 | -33.5 | 13.3 | 33.8 | -35/14 | -9/7 | NO |
| G1_('hi', 0.67)_1_h5_GC | 50% | -24.1 | -60.3 | 5.4 | 7.6 | -62/11 | -16/-17 | NO |
| G1_('lo', 0.33)_1_h5_NQ | 10% | -6.8 | -1.8 | 7.6 | 10.0 | -3/6 | 10/11 | NO |
| G1_('lo', 0.33)_1_h5_NQ | 20% | -13.6 | -15.2 | 14.6 | 15.5 | -16/12 | 20/22 | NO |
| G1_('lo', 0.33)_1_h5_NQ | 30% | -20.5 | -28.6 | 21.5 | 13.1 | -30/17 | 30/33 | NO |
| G1_('lo', 0.33)_1_h5_NQ | 50% | -34.1 | -55.4 | 7.2 | 6.6 | -57/8 | -15/6 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| G1_('lo', 0.33)_1_h5_CL | 0.11 | 4 | 0.50 | 0.03 / 0.08 | 0.20 / -0.11 / 0.00 / 0.10 | 0.36 | 0.22 / -0.20 / 0.00 / 0.11 |
| G1_('hi', 0.67)_1_h5_GC | 0.19 | 4 | 0.50 | 0.08 / 0.14 | 0.18 / 0.58 / -0.10 / 0.18 | 0.91 | 0.18 / 0.61 / -0.09 / 0.20 |
| G1_('lo', 0.33)_1_h5_NQ | 0.06 | 4 | 0.75 | 0.04 / 0.07 | 0.10 / -0.08 / 0.01 / 0.06 | 0.57 | 0.11 / -0.03 / -0.00 / 0.07 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| G1_('lo', 0.33)_1_h5_CL | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | PASS (0.06) | NO |
| G1_('hi', 0.67)_1_h5_GC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | PASS (-0.20) | NO |
| G1_('lo', 0.33)_1_h5_NQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | PASS (0.75) | fail | PASS (0.21) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G1_('lo', 0.33)_1_h5_CL | clean | 0.99 | 902,342 | -312,166 | -125,153 | -91,824 | 528,737 | 1.59 | 1.71 | 23 | 1.75 | -118,137 | -86,736 | 322,997 | 4.96 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| G1_('lo', 0.33)_1_h5_CL | H1 | -1.54 | -375,588 | -125,875 | -118,737 | -112,068 | 510,940 | -1.95 | -0.74 | 46 | 2.62 | -76,932 | -62,335 | 150,280 | 3.20 | 46 | 2.83 | -78,287 | -77,610 | 151,713 |
| G1_('lo', 0.33)_1_h5_CL | H2 | n/a | 0 | 0 | 0 | 0 | 0 | n/a | n/a | 0 | 2.26 | -82,524 | -81,089 | 217,425 | 3.50 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| G1_('lo', 0.33)_1_h5_CL | all | 0.41 | 526,754 | -312,166 | -123,164 | -93,494 | 542,211 | 0.62 | 0.97 | 21 | 2.00 | -118,137 | -84,455 | 322,997 | 8.80 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| G1_('hi', 0.67)_1_h5_GC | clean | 0.91 | 827,130 | -187,558 | -137,263 | -104,895 | 264,367 | 1.48 | 3.13 | 26 | 1.71 | -133,326 | -90,215 | 255,577 | 6.17 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| G1_('hi', 0.67)_1_h5_GC | H1 | 2.21 | 736,922 | -170,580 | -136,731 | -121,628 | 450,008 | 4.44 | 1.64 | 29 | 3.57 | -109,152 | -85,773 | 188,535 | 4.32 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| G1_('hi', 0.67)_1_h5_GC | H2 | -0.77 | -172,671 | -192,872 | -152,975 | -95,631 | 360,479 | -0.87 | -0.48 | 22 | 2.10 | -86,661 | -84,593 | 217,425 | 3.26 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| G1_('hi', 0.67)_1_h5_GC | all | 0.93 | 1,391,381 | -192,872 | -144,456 | -110,274 | 614,078 | 1.51 | 2.27 | 26 | 2.10 | -133,326 | -91,541 | 255,577 | 12.14 | 39 | 1.86 | -82,524 | -79,220 | 280,110 |
| G1_('lo', 0.33)_1_h5_NQ | clean | 0.74 | 676,762 | -208,707 | -140,607 | -92,355 | 353,966 | 1.27 | 1.91 | 10 | 1.59 | -128,001 | -88,631 | 310,398 | 4.94 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| G1_('lo', 0.33)_1_h5_NQ | H1 | -0.04 | -12,599 | -253,330 | -189,145 | -165,884 | 542,915 | -0.05 | -0.02 | 21 | 2.62 | -78,287 | -75,253 | 194,484 | 3.03 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| G1_('lo', 0.33)_1_h5_NQ | H2 | 0.95 | 190,163 | -91,819 | -85,385 | -49,372 | 106,905 | 1.82 | 1.78 | 8 | 2.27 | -82,524 | -81,089 | 233,304 | 3.51 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| G1_('lo', 0.33)_1_h5_NQ | all | 0.57 | 854,326 | -253,330 | -161,954 | -113,722 | 542,915 | 0.88 | 1.57 | 11 | 1.92 | -128,001 | -85,806 | 310,398 | 9.48 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE G1
