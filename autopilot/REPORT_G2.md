# REPORT G2

**NO - cross-asset drivers into BTC and VX (GAPMAP D07 H5/H6): best selected cell G2_GC_10_1_h5_BTC: standalone Sharpe 2013-22 0.05, pair window 1.56, own-null rank pair window 1.00; additive uplift at 20% clean/H1/H2 +0.38/-0.37/+0.21, bootstrap lo +0.06; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea G2: BTC follows/inverts ES/NQ/GC/6J moves; VX reacts to ES and own momentum = 30 cells; clean-only selection.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 30 cells; eligible 5
| cell               |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------|-----------------:|-------------:|----------:|
| G2_GC_10_1_h5_BTC  |       1000000000 |         2.29 |        10 |
| G2_ES_10_1_h5_BTC  |       1000000000 |         1.11 |        10 |
| G2_6J_5_-1_h5_BTC  |       1000000000 |         0.85 |        10 |
| G2_NQ_10_1_h5_BTC  |                0 |         0.71 |         0 |
| G2_6J_10_-1_h5_BTC |                0 |         0.68 |         0 |
| G2_ES_5_1_h5_BTC   |       1000000000 |         0.61 |        10 |
| G2_NQ_5_1_h5_BTC   |       1000000000 |         0.52 |        10 |
| G2_GC_5_1_h5_BTC   |                0 |         0.52 |         0 |
| G2o_20_1_h5_VX     |                0 |         0.06 |         0 |
| G2o_10_1_h5_VX     |                0 |         0    |         0 |

Multiplicity: 30 cells x 5% = 1.5 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G2_GC_10_1_h5_BTC | 0.05 | 1 | 2.29 | -1.08 | 1.58 | 1.56 | 0.82 | 1.11 | 1.00 | 0.55 | 0.61 |
| G2_ES_10_1_h5_BTC | -0.17 | 0 | 1.11 | -0.58 | -1.74 | 0.23 | 0.03 | 0.89 | 0.65 | 0.48 | 0.40 |
| G2_6J_5_-1_h5_BTC | -0.11 | 0 | 0.85 | -1.01 | -1.35 | 0.05 | -0.06 | 0.97 | 0.53 | 0.43 | 0.41 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G2_GC_10_1_h5_BTC | 6.0 | 10% | 0.20 | -0.17 | 0.13 | 0.13 | 7 | 0.04 | 0.08 | -0.17 | 0.12 | NO |
| G2_GC_10_1_h5_BTC | 6.0 | 20% | 0.38 | -0.37 | 0.21 | 0.24 | 22 | 0.06 | 0.08 | -0.17 | 0.12 | NO |
| G2_GC_10_1_h5_BTC | 6.0 | 30% | 0.54 | -0.58 | 0.26 | 0.32 | 36 | 0.06 | 0.08 | -0.17 | 0.12 | NO |
| G2_GC_10_1_h5_BTC | 6.0 | 50% | 0.77 | -1.01 | 0.29 | 0.41 | 64 | 0.02 | 0.08 | -0.17 | 0.12 | NO |
| G2_ES_10_1_h5_BTC | 5.2 | 10% | 0.09 | -0.12 | -0.13 | 0.01 | 9 | -0.08 | 0.47 | -0.18 | 0.00 | NO |
| G2_ES_10_1_h5_BTC | 5.2 | 20% | 0.17 | -0.26 | -0.29 | 0.01 | 25 | -0.18 | 0.47 | -0.18 | 0.00 | NO |
| G2_ES_10_1_h5_BTC | 5.2 | 30% | 0.23 | -0.42 | -0.46 | -0.01 | 41 | -0.30 | 0.47 | -0.18 | 0.00 | NO |
| G2_ES_10_1_h5_BTC | 5.2 | 50% | 0.30 | -0.74 | -0.84 | -0.10 | 74 | -0.55 | 0.47 | -0.18 | 0.00 | NO |
| G2_6J_5_-1_h5_BTC | 5.9 | 10% | 0.09 | -0.16 | -0.13 | 0.01 | 10 | -0.09 | 0.74 | 0.40 | -0.05 | NO |
| G2_6J_5_-1_h5_BTC | 5.9 | 20% | 0.16 | -0.35 | -0.28 | -0.01 | 24 | -0.20 | 0.74 | 0.40 | -0.05 | NO |
| G2_6J_5_-1_h5_BTC | 5.9 | 30% | 0.22 | -0.58 | -0.44 | -0.04 | 37 | -0.31 | 0.74 | 0.40 | -0.05 | NO |
| G2_6J_5_-1_h5_BTC | 5.9 | 50% | 0.28 | -1.06 | -0.76 | -0.15 | 65 | -0.57 | 0.74 | 0.40 | -0.05 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| G2_GC_10_1_h5_BTC | 10% | -0.7 | 1.9 | 7.3 | 12.0 | 1/8 | 3/7 | NO |
| G2_GC_10_1_h5_BTC | 20% | -1.4 | -3.0 | 13.1 | 23.9 | -4/14 | 5/14 | NO |
| G2_GC_10_1_h5_BTC | 30% | -2.1 | -7.8 | 18.0 | 35.9 | -9/19 | 6/17 | NO |
| G2_GC_10_1_h5_BTC | 50% | -3.6 | -17.5 | 16.9 | 39.6 | -18/20 | 10/13 | NO |
| G2_ES_10_1_h5_BTC | 10% | -8.8 | -0.1 | 6.5 | 10.3 | -1/7 | 2/4 | NO |
| G2_ES_10_1_h5_BTC | 20% | -17.5 | -6.8 | 11.7 | 20.6 | -8/12 | 2/8 | NO |
| G2_ES_10_1_h5_BTC | 30% | -26.3 | -13.5 | 16.7 | 24.2 | -14/17 | 2/12 | NO |
| G2_ES_10_1_h5_BTC | 50% | -43.8 | -26.9 | 9.5 | 12.6 | -28/10 | 2/12 | NO |
| G2_6J_5_-1_h5_BTC | 10% | -9.7 | -0.6 | 3.2 | 9.5 | -1/5 | 1/2 | NO |
| G2_6J_5_-1_h5_BTC | 20% | -19.4 | -4.5 | 5.5 | 19.1 | -5/8 | 1/4 | NO |
| G2_6J_5_-1_h5_BTC | 30% | -29.1 | -8.3 | 4.7 | 27.4 | -9/7 | 0/6 | NO |
| G2_6J_5_-1_h5_BTC | 50% | -48.5 | -44.6 | -0.6 | 4.1 | -46/3 | -1/10 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| G2_GC_10_1_h5_BTC | 0.24 | 4 | 0.00 | 0.03 / 0.08 | 0.38 / -0.37 / 0.21 / 0.24 | 1.54 | 0.37 / -0.27 / 0.19 / 0.23 |
| G2_ES_10_1_h5_BTC | 0.01 | 4 | 0.50 | -0.06 / 0.00 | 0.17 / -0.27 / -0.29 / 0.00 | 0.21 | 0.17 / -0.18 / -0.30 / 0.00 |
| G2_6J_5_-1_h5_BTC | -0.01 | 4 | 0.00 | 0.02 / 0.05 | 0.16 / -0.36 / -0.28 / -0.01 | 0.03 | 0.17 / -0.28 / -0.26 / -0.00 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| G2_GC_10_1_h5_BTC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | PASS | fail (0.00) | fail | PASS (-0.17) | NO |
| G2_ES_10_1_h5_BTC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | PASS (-0.18) | NO |
| G2_6J_5_-1_h5_BTC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | fail (0.40) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G2_GC_10_1_h5_BTC | clean | 2.29 | 2,087,855 | -117,034 | -87,066 | -71,901 | 269,666 | 5.12 | 7.74 | 44 | 2.00 | -112,052 | -86,355 | 263,561 | 7.42 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| G2_GC_10_1_h5_BTC | H1 | -1.08 | -270,124 | -128,955 | -113,551 | -105,787 | 466,558 | -1.48 | -0.58 | 57 | 2.25 | -96,326 | -84,442 | 165,119 | 3.11 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| G2_GC_10_1_h5_BTC | H2 | 1.58 | 676,620 | -100,214 | -81,535 | -66,727 | 222,693 | 4.72 | 3.04 | 41 | 2.53 | -93,943 | -87,497 | 223,168 | 4.32 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| G2_GC_10_1_h5_BTC | all | 1.56 | 2,494,352 | -128,955 | -98,428 | -82,510 | 570,826 | 3.33 | 4.37 | 46 | 2.17 | -112,052 | -87,717 | 263,561 | 13.03 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| G2_ES_10_1_h5_BTC | clean | 1.11 | 1,010,900 | -181,363 | -113,736 | -94,650 | 327,252 | 1.89 | 3.09 | 47 | 1.69 | -116,751 | -88,306 | 277,537 | 5.88 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| G2_ES_10_1_h5_BTC | H1 | -0.58 | -131,155 | -112,921 | -95,022 | -88,781 | 328,753 | -0.85 | -0.40 | 61 | 2.41 | -100,069 | -91,715 | 220,754 | 2.51 | 46 | 2.83 | -78,287 | -77,610 | 151,713 |
| G2_ES_10_1_h5_BTC | H2 | -1.74 | -548,039 | -271,912 | -226,594 | -147,382 | 722,792 | -1.81 | -0.76 | 54 | 1.80 | -86,564 | -83,900 | 261,806 | 2.28 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| G2_ES_10_1_h5_BTC | all | 0.23 | 331,706 | -271,912 | -138,725 | -110,406 | 831,279 | 0.33 | 0.40 | 51 | 1.84 | -116,751 | -89,315 | 277,537 | 10.03 | 41 | 1.86 | -82,524 | -79,220 | 280,110 |
| G2_6J_5_-1_h5_BTC | clean | 0.85 | 773,099 | -204,048 | -122,922 | -98,827 | 426,867 | 1.39 | 1.81 | 51 | 1.68 | -113,339 | -94,356 | 283,958 | 5.50 | 38 | 1.46 | -81,874 | -78,736 | 280,110 |
| G2_6J_5_-1_h5_BTC | H1 | -1.01 | -293,918 | -102,949 | -99,940 | -96,005 | 570,025 | -1.57 | -0.52 | 61 | 2.25 | -101,180 | -96,172 | 167,432 | 3.02 | 46 | 2.83 | -78,287 | -77,610 | 151,713 |
| G2_6J_5_-1_h5_BTC | H2 | -1.35 | -401,310 | -207,866 | -148,171 | -108,742 | 733,580 | -1.63 | -0.55 | 57 | 1.83 | -106,196 | -99,750 | 255,995 | 2.50 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| G2_6J_5_-1_h5_BTC | all | 0.05 | 77,871 | -207,866 | -127,253 | -105,556 | 1,014,666 | 0.08 | 0.08 | 55 | 1.82 | -113,339 | -97,559 | 283,958 | 9.54 | 41 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE G2
