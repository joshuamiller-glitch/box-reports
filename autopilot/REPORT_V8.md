# REPORT V8

**NO - post-event continuation/fade: best selected cell V8_follow_h1_GC: standalone Sharpe 2013-22 0.80, pair window 0.24, own-null rank pair window 0.67; additive uplift at 20% clean/H1/H2 +0.04/+0.08/-0.01, bootstrap lo -0.09; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea V8: FOMC+NFP event-day candle followed/faded next open, ES NQ ZN GC 6E, hold 1/3 = 20 cells (min 150 trades).

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 20 cells; eligible 0
| cell            |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:----------------|-----------------:|-------------:|----------:|
| V8_follow_h1_GC |              195 |         0.8  |         9 |
| V8_follow_h3_GC |              175 |         0.44 |         7 |
| V8_follow_h1_ES |              196 |         0.24 |         7 |
| V8_fade_h3_6E   |              177 |         0.22 |         7 |
| V8_follow_h1_NQ |              197 |         0.15 |         7 |
| V8_follow_h3_ES |              176 |         0.04 |         4 |
| V8_follow_h3_NQ |              177 |        -0.01 |         6 |
| V8_follow_h1_6E |              197 |        -0.04 |         6 |
| V8_fade_h3_ZN   |              174 |        -0.06 |         5 |
| V8_fade_h3_NQ   |              177 |        -0.07 |         4 |

Multiplicity: 20 cells x 5% = 1.0 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| V8_follow_h1_GC | 0.80 | 9 | 0.18 | 0.74 | 0.03 | 0.24 | 0.60 | 0.92 | 0.67 | 0.43 | 1.00 |
| V8_follow_h3_GC | 0.44 | 7 | -0.69 | -1.16 | 1.38 | -0.44 | 0.12 | 0.82 | 0.28 | 0.51 | 0.93 |
| V8_follow_h1_ES | 0.24 | 7 | -0.50 | 0.52 | -0.13 | -0.30 | 0.09 | 0.88 | 0.36 | 0.34 | 0.89 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V8_follow_h1_GC | 21.8 | 10% | 0.02 | 0.05 | 0.01 | 0.02 | 5 | -0.04 | 0.85 | -0.69 | -0.08 | NO |
| V8_follow_h1_GC | 21.8 | 20% | 0.04 | 0.08 | -0.01 | 0.04 | 16 | -0.09 | 0.85 | -0.69 | -0.08 | NO |
| V8_follow_h1_GC | 21.8 | 30% | 0.04 | 0.09 | -0.03 | 0.04 | 27 | -0.16 | 0.85 | -0.69 | -0.08 | NO |
| V8_follow_h1_GC | 21.8 | 50% | 0.03 | 0.04 | -0.13 | 0.01 | 50 | -0.31 | 0.85 | -0.69 | -0.08 | NO |
| V8_follow_h3_GC | 13.5 | 10% | -0.07 | -0.46 | 0.15 | -0.07 | 15 | -0.21 | 0.58 | -0.44 | -0.02 | NO |
| V8_follow_h3_GC | 13.5 | 20% | -0.15 | -0.97 | 0.28 | -0.16 | 83 | -0.45 | 0.58 | -0.44 | -0.02 | NO |
| V8_follow_h3_GC | 13.5 | 30% | -0.24 | -1.42 | 0.38 | -0.27 | 168 | -0.70 | 0.58 | -0.44 | -0.02 | NO |
| V8_follow_h3_GC | 13.5 | 50% | -0.43 | -2.09 | 0.52 | -0.52 | 338 | -1.15 | 0.58 | -0.44 | -0.02 | NO |
| V8_follow_h1_ES | 23.8 | 10% | -0.04 | 0.04 | 0.01 | -0.02 | 5 | -0.12 | 0.98 | 0.40 | -0.12 | NO |
| V8_follow_h1_ES | 23.8 | 20% | -0.11 | 0.06 | 0.00 | -0.06 | 10 | -0.26 | 0.98 | 0.40 | -0.12 | NO |
| V8_follow_h1_ES | 23.8 | 30% | -0.19 | 0.06 | -0.03 | -0.11 | 26 | -0.43 | 0.98 | 0.40 | -0.12 | NO |
| V8_follow_h1_ES | 23.8 | 50% | -0.37 | -0.01 | -0.13 | -0.27 | 107 | -0.79 | 0.98 | 0.40 | -0.12 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| V8_follow_h1_GC | 10% | -9.0 | 4.5 | 8.9 | 20.1 | 11/9 | 10/10 | NO |
| V8_follow_h1_GC | 20% | -18.0 | 2.6 | 16.8 | 28.7 | 17/18 | 20/20 | NO |
| V8_follow_h1_GC | 30% | -27.0 | 0.6 | 24.5 | 37.4 | 23/27 | 30/30 | NO |
| V8_follow_h1_GC | 50% | -45.0 | -3.4 | 32.8 | 28.8 | 30/39 | 17/33 | NO |
| V8_follow_h3_GC | 10% | -13.0 | -6.1 | 2.1 | 15.1 | -7/0 | -2/3 | NO |
| V8_follow_h3_GC | 20% | -26.1 | -80.8 | -6.4 | 2.6 | -20/-0 | -91/-36 | NO |
| V8_follow_h3_GC | 30% | -39.1 | -164.3 | -15.1 | -16.5 | -33/-1 | -179/-76 | NO |
| V8_follow_h3_GC | 50% | -65.2 | -331.5 | -43.8 | -54.7 | -58/-18 | -355/-181 | NO |
| V8_follow_h1_ES | 10% | -11.7 | 4.9 | 7.9 | -0.3 | 5/8 | 10/10 | NO |
| V8_follow_h1_ES | 20% | -23.4 | 9.7 | 14.8 | -0.6 | 10/15 | 20/20 | NO |
| V8_follow_h1_ES | 30% | -35.1 | -24.7 | 16.9 | -0.9 | -26/14 | 30/30 | NO |
| V8_follow_h1_ES | 50% | -58.5 | -106.0 | -9.9 | -4.5 | -108/-20 | 50/50 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| V8_follow_h1_GC | 0.04 | 0 | n/a | n/a / n/a | 0.03 / 0.08 / -0.01 / 0.03 | 0.19 | 0.04 / 0.10 / -0.03 / 0.04 |
| V8_follow_h3_GC | -0.16 | 2 | 0.00 | -0.15 / -0.12 | -0.15 / -0.97 / 0.27 / -0.16 | -0.45 | -0.15 / -0.62 / 0.26 / -0.15 |
| V8_follow_h1_ES | -0.06 | 0 | n/a | n/a / n/a | -0.12 / 0.05 / -0.01 / -0.07 | -0.35 | -0.11 / 0.07 / 0.02 / -0.06 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| V8_follow_h1_GC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | PASS (-0.69) | NO |
| V8_follow_h3_GC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.44) | NO |
| V8_follow_h1_ES | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | fail (0.40) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V8_follow_h1_GC | clean | 0.18 | 122,869 | -160,052 | -100,300 | -66,696 | 645,283 | 0.32 | 0.19 | 17 | 1.50 | -86,503 | -80,708 | 249,856 | 5.47 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| V8_follow_h1_GC | H1 | 0.74 | 139,344 | -118,015 | -114,941 | -82,665 | 118,015 | 1.16 | 1.18 | 14 | 2.92 | -78,287 | -77,610 | 173,037 | 3.67 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| V8_follow_h1_GC | H2 | 0.03 | 7,853 | -120,604 | -119,942 | -106,191 | 212,024 | 0.04 | 0.04 | 19 | 2.23 | -105,186 | -92,420 | 219,079 | 3.49 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| V8_follow_h1_GC | all | 0.24 | 270,066 | -160,052 | -117,693 | -81,887 | 645,283 | 0.39 | 0.42 | 17 | 1.89 | -105,186 | -83,210 | 249,856 | 11.07 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| V8_follow_h3_GC | clean | -0.69 | -607,032 | -216,823 | -156,336 | -127,368 | 1,387,332 | -0.92 | -0.44 | 28 | 1.22 | -131,615 | -103,111 | 269,793 | 4.25 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| V8_follow_h3_GC | H1 | -1.16 | -642,800 | -700,973 | -433,805 | -316,674 | 705,734 | -1.21 | -0.91 | 21 | 1.41 | -221,512 | -149,899 | 347,924 | 1.15 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V8_follow_h3_GC | H2 | 1.38 | 431,430 | -100,021 | -87,352 | -61,542 | 128,540 | 3.63 | 3.36 | 27 | 2.64 | -90,843 | -85,248 | 198,554 | 4.49 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| V8_follow_h3_GC | all | -0.44 | -818,401 | -700,973 | -214,012 | -153,401 | 1,538,793 | -0.52 | -0.53 | 26 | 1.58 | -221,512 | -112,297 | 376,182 | 6.48 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| V8_follow_h1_ES | clean | -0.50 | -513,962 | -337,550 | -203,388 | -130,741 | 1,005,079 | -0.63 | -0.51 | 18 | 1.27 | -103,642 | -87,698 | 366,622 | 3.21 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| V8_follow_h1_ES | H1 | 0.52 | 97,289 | -115,501 | -92,262 | -76,558 | 117,515 | 0.91 | 0.83 | 14 | 2.88 | -78,287 | -77,610 | 186,363 | 3.34 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| V8_follow_h1_ES | H2 | -0.13 | -40,867 | -228,058 | -171,617 | -115,048 | 441,769 | -0.18 | -0.09 | 19 | 2.24 | -95,269 | -88,513 | 221,767 | 3.38 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| V8_follow_h1_ES | all | -0.30 | -457,540 | -337,550 | -191,580 | -125,482 | 1,122,593 | -0.38 | -0.41 | 17 | 1.74 | -103,642 | -87,049 | 366,622 | 6.95 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE V8
