# REPORT G5

**NO - BTC weekly price patterns (GAPMAP D11 H6): best selected cell G5_tsm_4_follow_h5_BTC: standalone Sharpe 2013-22 -0.08, pair window 0.83, own-null rank pair window 0.95; additive uplift at 20% clean/H1/H2 +0.38/-0.12/-0.22, bootstrap lo -0.01; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea G5: weekly TS momentum and Donchian, follow/fade = 12 cells; clean-only selection.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 3
| cell                    |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:------------------------|-----------------:|-------------:|----------:|
| G5_tsm_4_follow_h5_BTC  |       1000000000 |         1.73 |        10 |
| G5_don_4_follow_h5_BTC  |                0 |         1.12 |         0 |
| G5_don_13_follow_h5_BTC |                0 |         0.89 |         0 |
| G5_tsm_13_follow_h5_BTC |       1000000000 |         0.46 |        10 |
| G5_tsm_26_follow_h5_BTC |       1000000000 |         0.45 |        10 |
| G5_tsm_8_follow_h5_BTC  |                0 |         0.45 |         0 |
| G5_tsm_8_fade_h5_BTC    |                0 |        -0.49 |         0 |
| G5_tsm_26_fade_h5_BTC   |                0 |        -0.5  |         0 |
| G5_tsm_13_fade_h5_BTC   |                0 |        -0.51 |         0 |
| G5_don_13_fade_h5_BTC   |                0 |        -0.9  |         0 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G5_tsm_4_follow_h5_BTC | -0.08 | 0 | 1.73 | -0.08 | -0.59 | 0.83 | 0.15 | 0.81 | 0.95 | 0.49 | 0.44 |
| G5_tsm_13_follow_h5_BTC | -0.18 | 0 | 0.46 | -0.32 | -2.20 | -0.33 | -0.28 | 0.97 | 0.32 | 0.48 | 0.34 |
| G5_tsm_26_follow_h5_BTC | 0.17 | 1 | 0.45 | 0.23 | -0.38 | 0.20 | -0.07 | 0.90 | 0.67 | 0.46 | 0.72 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G5_tsm_4_follow_h5_BTC | 5.8 | 10% | 0.20 | -0.04 | -0.09 | 0.10 | 6 | 0.00 | 0.92 | 0.03 | -0.11 | NO |
| G5_tsm_4_follow_h5_BTC | 5.8 | 20% | 0.38 | -0.12 | -0.22 | 0.18 | 16 | -0.01 | 0.92 | 0.03 | -0.11 | NO |
| G5_tsm_4_follow_h5_BTC | 5.8 | 30% | 0.54 | -0.22 | -0.36 | 0.23 | 26 | -0.06 | 0.92 | 0.03 | -0.11 | NO |
| G5_tsm_4_follow_h5_BTC | 5.8 | 50% | 0.79 | -0.47 | -0.66 | 0.27 | 46 | -0.21 | 0.92 | 0.03 | -0.11 | NO |
| G5_tsm_13_follow_h5_BTC | 5.7 | 10% | 0.06 | -0.02 | -0.22 | -0.01 | 6 | -0.11 | 0.99 | 0.03 | -0.17 | NO |
| G5_tsm_13_follow_h5_BTC | 5.7 | 20% | 0.11 | -0.09 | -0.47 | -0.05 | 16 | -0.25 | 0.99 | 0.03 | -0.17 | NO |
| G5_tsm_13_follow_h5_BTC | 5.7 | 30% | 0.14 | -0.18 | -0.74 | -0.10 | 25 | -0.41 | 0.99 | 0.03 | -0.17 | NO |
| G5_tsm_13_follow_h5_BTC | 5.7 | 50% | 0.15 | -0.44 | -1.30 | -0.26 | 61 | -0.75 | 0.99 | 0.03 | -0.17 | NO |
| G5_tsm_26_follow_h5_BTC | 5.7 | 10% | 0.05 | 0.08 | -0.04 | 0.03 | 8 | -0.07 | 0.91 | 0.33 | -0.11 | NO |
| G5_tsm_26_follow_h5_BTC | 5.7 | 20% | 0.09 | 0.11 | -0.11 | 0.04 | 17 | -0.16 | 0.91 | 0.33 | -0.11 | NO |
| G5_tsm_26_follow_h5_BTC | 5.7 | 30% | 0.11 | 0.11 | -0.20 | 0.03 | 27 | -0.27 | 0.91 | 0.33 | -0.11 | NO |
| G5_tsm_26_follow_h5_BTC | 5.7 | 50% | 0.11 | -0.01 | -0.45 | -0.04 | 61 | -0.53 | 0.91 | 0.33 | -0.11 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| G5_tsm_4_follow_h5_BTC | 10% | -5.1 | 3.3 | 6.6 | 17.6 | 9/8 | 2/4 | NO |
| G5_tsm_4_follow_h5_BTC | 20% | -10.2 | 3.1 | 12.2 | 30.3 | 13/15 | 1/7 | NO |
| G5_tsm_4_follow_h5_BTC | 30% | -15.4 | 2.9 | 17.8 | 23.4 | 17/22 | 1/11 | NO |
| G5_tsm_4_follow_h5_BTC | 50% | -25.6 | -61.4 | 9.1 | 0.4 | 24/32 | -4/-3 | NO |
| G5_tsm_13_follow_h5_BTC | 10% | -11.9 | 3.6 | 7.5 | 9.3 | 10/8 | 8/14 | NO |
| G5_tsm_13_follow_h5_BTC | 20% | -23.8 | 3.6 | 13.9 | -1.3 | 13/15 | 15/25 | NO |
| G5_tsm_13_follow_h5_BTC | 30% | -35.7 | -0.7 | 17.0 | -11.9 | -1/17 | 23/26 | NO |
| G5_tsm_13_follow_h5_BTC | 50% | -59.4 | -55.2 | -3.7 | -33.0 | -41/12 | -1/9 | NO |
| G5_tsm_26_follow_h5_BTC | 10% | -8.8 | 1.6 | 7.6 | 4.5 | 1/8 | 12/16 | NO |
| G5_tsm_26_follow_h5_BTC | 20% | -17.7 | 2.4 | 13.9 | 1.2 | 2/14 | 25/29 | NO |
| G5_tsm_26_follow_h5_BTC | 30% | -26.5 | -0.7 | 17.4 | -8.1 | -1/16 | 30/33 | NO |
| G5_tsm_26_follow_h5_BTC | 50% | -44.2 | -55.2 | -2.4 | -27.0 | -41/3 | 20/21 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| G5_tsm_4_follow_h5_BTC | 0.18 | 4 | 1.00 | 0.16 / 0.17 | 0.37 / -0.12 / -0.22 / 0.18 | 0.81 | 0.36 / -0.08 / -0.20 / 0.17 |
| G5_tsm_13_follow_h5_BTC | -0.05 | 4 | 0.00 | -0.06 / 0.02 | 0.10 / -0.09 / -0.47 / -0.05 | -0.34 | 0.11 / -0.04 / -0.45 / -0.04 |
| G5_tsm_26_follow_h5_BTC | 0.04 | 4 | 0.25 | -0.05 / 0.00 | 0.08 / 0.11 / -0.11 / 0.04 | 0.18 | 0.08 / 0.09 / -0.09 / 0.04 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| G5_tsm_4_follow_h5_BTC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | PASS (1.00) | fail | PASS (0.03) | NO |
| G5_tsm_13_follow_h5_BTC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.03) | NO |
| G5_tsm_26_follow_h5_BTC | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.25) | fail | fail (0.33) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G5_tsm_4_follow_h5_BTC | clean | 1.73 | 1,571,758 | -101,542 | -90,074 | -76,521 | 291,035 | 3.70 | 5.40 | 44 | 2.00 | -91,327 | -84,652 | 216,410 | 8.32 | 38 | 1.46 | -81,874 | -78,736 | 280,110 |
| G5_tsm_4_follow_h5_BTC | H1 | -0.08 | -19,719 | -176,275 | -151,142 | -126,990 | 308,466 | -0.10 | -0.06 | 50 | 2.61 | -100,538 | -92,244 | 158,318 | 3.71 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| G5_tsm_4_follow_h5_BTC | H2 | -0.59 | -242,410 | -378,060 | -229,633 | -140,275 | 589,812 | -0.71 | -0.41 | 49 | 1.91 | -104,015 | -92,577 | 260,000 | 2.65 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| G5_tsm_4_follow_h5_BTC | all | 0.83 | 1,309,629 | -378,060 | -135,807 | -103,636 | 589,812 | 1.28 | 2.22 | 46 | 2.09 | -104,015 | -88,604 | 260,000 | 11.84 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |
| G5_tsm_13_follow_h5_BTC | clean | 0.46 | 421,190 | -196,380 | -124,438 | -94,584 | 564,193 | 0.76 | 0.75 | 57 | 1.60 | -93,451 | -86,699 | 380,683 | 3.83 | 39 | 1.46 | -81,874 | -78,736 | 280,110 |
| G5_tsm_13_follow_h5_BTC | H1 | -0.32 | -78,580 | -171,515 | -147,061 | -125,655 | 618,295 | -0.42 | -0.13 | 50 | 2.65 | -83,797 | -75,760 | 171,339 | 3.33 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| G5_tsm_13_follow_h5_BTC | H2 | -2.20 | -849,744 | -367,851 | -289,145 | -185,385 | 1,002,404 | -2.19 | -0.85 | 54 | 1.52 | -103,358 | -92,267 | 263,201 | 1.92 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| G5_tsm_13_follow_h5_BTC | all | -0.33 | -507,135 | -367,851 | -171,605 | -125,282 | 1,251,093 | -0.43 | -0.41 | 55 | 1.75 | -103,358 | -87,675 | 380,683 | 6.65 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |
| G5_tsm_26_follow_h5_BTC | clean | 0.45 | 410,895 | -196,361 | -130,082 | -103,023 | 559,977 | 0.71 | 0.73 | 50 | 1.57 | -104,400 | -87,763 | 370,100 | 3.93 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| G5_tsm_26_follow_h5_BTC | H1 | 0.23 | 55,823 | -122,595 | -107,951 | -99,579 | 340,261 | 0.36 | 0.16 | 50 | 2.93 | -72,842 | -70,281 | 158,139 | 3.86 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| G5_tsm_26_follow_h5_BTC | H2 | -0.38 | -154,998 | -367,815 | -226,022 | -145,431 | 419,277 | -0.46 | -0.37 | 41 | 2.06 | -103,355 | -92,266 | 257,430 | 2.78 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| G5_tsm_26_follow_h5_BTC | all | 0.20 | 311,721 | -367,815 | -151,579 | -115,944 | 559,977 | 0.28 | 0.56 | 48 | 1.89 | -104,400 | -87,468 | 370,100 | 7.51 | 41 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE G5
