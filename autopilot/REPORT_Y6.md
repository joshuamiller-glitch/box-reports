# REPORT Y6

> **UPDATE 2026-10-16: compression-breakout results (X1, Y6, B2-D) are NOT CONFIRMED under path-resolved 30-min execution (REPORT_Z1.md); the daily-bar fill model resolved 52% of triggers (both-touch days) incorrectly. Lead withdrawn.**

**LEAD (same family as X1, not independent evidence; not FOUND) - depth-of-compression breakouts (ID2/NR4/NR7ID): best selected cell Y6_NR4_3.0_h1_SCR: standalone Sharpe 2013-22 1.46, pair window 1.51, own-null rank pair window 1.00; additive uplift at 20% clean/H1/H2 +0.21/+0.07/+0.30, bootstrap lo +0.04; FOUND 0. Fails: H1 uplift +0.07 (<0.10), worst week +32% vs 20% share, 2x slippage (H1 -0.01), bootstrap lo < 0 at some shares. Plateau 1.00, wd corr -0.05, own null rank 1.00; NR4 (range below previous 3) 1-day breakouts on the 16 screened markets.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea Y6: X1 mechanics with setups ID2 / NR4 / NR7ID, stop 2/3, hold 1, SCR or ALL26 = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 10
| cell                  |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:----------------------|-----------------:|-------------:|----------:|
| Y6_NR4_2.0_h1_SCR     |            10334 |         1.47 |        10 |
| Y6_NR4_3.0_h1_SCR     |            10334 |         1.46 |        10 |
| Y6_NR4_3.0_h1_ALL26   |            16472 |         1.17 |         8 |
| Y6_NR4_2.0_h1_ALL26   |            16472 |         1.17 |         8 |
| Y6_NR7ID_2.0_h1_SCR   |             3158 |         0.6  |         8 |
| Y6_NR7ID_3.0_h1_SCR   |             3158 |         0.55 |         8 |
| Y6_NR7ID_2.0_h1_ALL26 |             4801 |         0.53 |         8 |
| Y6_NR7ID_3.0_h1_ALL26 |             4801 |         0.49 |         8 |
| Y6_ID2_3.0_h1_SCR     |             1000 |         0.44 |         8 |
| Y6_ID2_2.0_h1_SCR     |             1000 |         0.42 |         8 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Y6_NR4_2.0_h1_SCR | 1.47 | 10 | 1.06 | 0.52 | 3.03 | 1.43 | 1.37 | 0.35 | 1.00 | -0.42 | 1.00 |
| Y6_NR4_3.0_h1_SCR | 1.46 | 10 | 1.19 | 0.55 | 3.05 | 1.51 | 1.38 | 0.23 | 1.00 | -0.37 | 1.00 |
| Y6_NR4_3.0_h1_ALL26 | 1.17 | 8 | 0.67 | 0.27 | 2.51 | 1.08 | 1.12 | -0.79 | 1.00 | -1.49 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y6_NR4_2.0_h1_SCR | 2.0 | 10% | 0.10 | 0.05 | 0.16 | 0.11 | 13 | 0.02 | 0.12 | -0.03 | 0.10 | NO |
| Y6_NR4_2.0_h1_SCR | 2.0 | 20% | 0.18 | 0.07 | 0.29 | 0.20 | 32 | 0.03 | 0.12 | -0.03 | 0.10 | NO |
| Y6_NR4_2.0_h1_SCR | 2.0 | 30% | 0.25 | 0.04 | 0.40 | 0.27 | 51 | 0.02 | 0.12 | -0.03 | 0.10 | NO |
| Y6_NR4_2.0_h1_SCR | 2.0 | 50% | 0.35 | -0.09 | 0.56 | 0.35 | 88 | -0.04 | 0.12 | -0.03 | 0.10 | NO |
| Y6_NR4_3.0_h1_SCR | 2.0 | 10% | 0.11 | 0.05 | 0.16 | 0.12 | 13 | 0.03 | 0.12 | -0.05 | 0.10 | NO |
| Y6_NR4_3.0_h1_SCR | 2.0 | 20% | 0.21 | 0.07 | 0.30 | 0.22 | 32 | 0.04 | 0.12 | -0.05 | 0.10 | NO |
| Y6_NR4_3.0_h1_SCR | 2.0 | 30% | 0.29 | 0.04 | 0.41 | 0.29 | 51 | 0.04 | 0.12 | -0.05 | 0.10 | NO |
| Y6_NR4_3.0_h1_SCR | 2.0 | 50% | 0.40 | -0.08 | 0.56 | 0.39 | 89 | -0.01 | 0.12 | -0.05 | 0.10 | NO |
| Y6_NR4_3.0_h1_ALL26 | 1.6 | 10% | 0.06 | 0.04 | 0.13 | 0.07 | 11 | -0.01 | 0.06 | 0.16 | 0.13 | NO |
| Y6_NR4_3.0_h1_ALL26 | 1.6 | 20% | 0.10 | 0.04 | 0.22 | 0.13 | 28 | -0.04 | 0.06 | 0.16 | 0.13 | NO |
| Y6_NR4_3.0_h1_ALL26 | 1.6 | 30% | 0.13 | 0.01 | 0.30 | 0.16 | 44 | -0.09 | 0.06 | 0.16 | 0.13 | NO |
| Y6_NR4_3.0_h1_ALL26 | 1.6 | 50% | 0.15 | -0.13 | 0.39 | 0.18 | 77 | -0.19 | 0.06 | 0.16 | 0.13 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| Y6_NR4_2.0_h1_SCR | 10% | -2.6 | -4.0 | 4.0 | 2.8 | -3/5 | -10/0 | NO |
| Y6_NR4_2.0_h1_SCR | 20% | -5.1 | -13.1 | 7.2 | 5.7 | -12/9 | -19/1 | NO |
| Y6_NR4_2.0_h1_SCR | 30% | -7.7 | -22.3 | 10.1 | 8.5 | -21/13 | -29/1 | NO |
| Y6_NR4_2.0_h1_SCR | 50% | -12.8 | -40.5 | 8.9 | 12.2 | -40/12 | -48/-6 | NO |
| Y6_NR4_3.0_h1_SCR | 10% | -2.1 | -3.9 | 4.0 | 3.2 | -4/5 | -10/0 | NO |
| Y6_NR4_3.0_h1_SCR | 20% | -4.3 | -13.1 | 7.2 | 6.4 | -14/9 | -19/1 | NO |
| Y6_NR4_3.0_h1_SCR | 30% | -6.4 | -22.9 | 10.3 | 9.6 | -24/13 | -29/1 | NO |
| Y6_NR4_3.0_h1_SCR | 50% | -10.6 | -42.3 | 9.0 | 15.9 | -43/12 | -48/-5 | NO |
| Y6_NR4_3.0_h1_ALL26 | 10% | -4.3 | -1.8 | 3.1 | 2.4 | -0/4 | -7/5 | NO |
| Y6_NR4_3.0_h1_ALL26 | 20% | -8.5 | -8.7 | 5.4 | 4.8 | -7/7 | -15/9 | NO |
| Y6_NR4_3.0_h1_ALL26 | 30% | -12.8 | -15.6 | 7.4 | 7.2 | -13/10 | -22/14 | NO |
| Y6_NR4_3.0_h1_ALL26 | 50% | -21.3 | -29.5 | 7.9 | 12.0 | -25/11 | -36/8 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| Y6_NR4_2.0_h1_SCR | 0.20 | 2 | 1.00 | 0.21 / 0.21 | 0.11 / -0.01 / 0.24 / 0.13 | 1.04 | 0.19 / 0.08 / 0.30 / 0.21 |
| Y6_NR4_3.0_h1_SCR | 0.22 | 2 | 1.00 | 0.20 / 0.21 | 0.13 / -0.01 / 0.24 / 0.15 | 1.13 | 0.21 / 0.08 / 0.30 / 0.22 |
| Y6_NR4_3.0_h1_ALL26 | 0.13 | 2 | 1.00 | 0.11 / 0.12 | -0.09 / -0.22 / 0.07 / -0.06 | 0.08 | 0.10 / 0.06 / 0.24 / 0.14 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| Y6_NR4_2.0_h1_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | PASS (1.00) | fail | PASS (-0.03) | NO |
| Y6_NR4_3.0_h1_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | PASS (1.00) | fail | PASS (-0.05) | NO |
| Y6_NR4_3.0_h1_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | PASS (1.00) | fail | PASS (0.16) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y6_NR4_2.0_h1_SCR | clean | 1.06 | 873,361 | -151,249 | -102,827 | -82,833 | 607,138 | 1.84 | 1.44 | 49 | 1.71 | -122,633 | -91,781 | 340,354 | 4.68 | 39 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y6_NR4_2.0_h1_SCR | H1 | 0.52 | 129,080 | -153,633 | -123,936 | -105,194 | 367,945 | 0.79 | 0.35 | 39 | 2.87 | -124,377 | -99,945 | 173,291 | 3.65 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y6_NR4_2.0_h1_SCR | H2 | 3.03 | 996,399 | -80,073 | -71,023 | -64,627 | 221,375 | 7.71 | 4.50 | 35 | 2.66 | -96,007 | -88,254 | 243,889 | 4.35 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y6_NR4_2.0_h1_SCR | all | 1.43 | 1,998,840 | -153,633 | -105,559 | -84,370 | 607,138 | 2.59 | 3.29 | 44 | 2.13 | -124,377 | -94,619 | 340,354 | 9.65 | 38 | 1.86 | -82,524 | -79,220 | 280,110 |
| Y6_NR4_3.0_h1_SCR | clean | 1.19 | 980,632 | -157,685 | -99,884 | -80,430 | 568,609 | 2.10 | 1.72 | 48 | 1.75 | -124,564 | -91,669 | 337,384 | 4.81 | 38 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y6_NR4_3.0_h1_SCR | H1 | 0.55 | 136,512 | -153,065 | -123,391 | -104,705 | 366,188 | 0.85 | 0.37 | 39 | 2.87 | -124,207 | -99,864 | 173,171 | 3.67 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y6_NR4_3.0_h1_SCR | H2 | 3.05 | 996,147 | -79,629 | -70,629 | -64,268 | 222,473 | 7.83 | 4.48 | 35 | 2.67 | -95,904 | -88,208 | 244,440 | 4.34 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y6_NR4_3.0_h1_SCR | all | 1.51 | 2,113,291 | -157,685 | -103,533 | -82,460 | 568,609 | 2.78 | 3.72 | 43 | 2.15 | -124,564 | -94,515 | 337,384 | 9.84 | 38 | 1.86 | -82,524 | -79,220 | 280,110 |
| Y6_NR4_3.0_h1_ALL26 | clean | 0.67 | 556,986 | -127,471 | -94,871 | -83,527 | 627,729 | 1.11 | 0.89 | 50 | 1.59 | -115,500 | -94,015 | 343,927 | 4.35 | 39 | 1.46 | -81,874 | -78,736 | 280,110 |
| Y6_NR4_3.0_h1_ALL26 | H1 | 0.27 | 63,745 | -135,383 | -106,414 | -93,319 | 319,513 | 0.43 | 0.20 | 54 | 2.84 | -118,902 | -89,894 | 166,207 | 3.69 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| Y6_NR4_3.0_h1_ALL26 | H2 | 2.51 | 920,314 | -87,655 | -86,291 | -79,204 | 377,275 | 5.73 | 2.44 | 38 | 2.56 | -99,368 | -93,533 | 247,906 | 4.18 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| Y6_NR4_3.0_h1_ALL26 | all | 1.08 | 1,541,046 | -135,383 | -97,646 | -85,218 | 627,729 | 1.91 | 2.45 | 47 | 2.02 | -118,902 | -96,673 | 343,927 | 9.15 | 38 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE Y6
