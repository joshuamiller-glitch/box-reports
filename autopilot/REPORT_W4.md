# REPORT W4

**NO - weekday x asset-class sleeves (dev-signed): best selected cell W4_2_EQ_h1_EQ: standalone Sharpe 2013-22 0.45, pair window 0.08, own-null rank pair window 0.67; additive uplift at 20% clean/H1/H2 -0.02/+0.29/-0.30, bootstrap lo -0.25; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea W4: class x weekday, direction signed on 2013-22 mean, hold 1 day = 30 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 30 cells; eligible 2
| cell            |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:----------------|-----------------:|-------------:|----------:|
| W4_2_EQ_h1_EQ   |             1823 |         0.45 |         7 |
| W4_0_EQ_h1_EQ   |             1832 |         0.41 |         6 |
| W4_0_EN_h1_EN   |             2068 |         0.3  |         6 |
| W4_0_MET_h1_MET |             2068 |         0.21 |         4 |
| W4_2_EN_h1_EN   |             2064 |         0.17 |         5 |
| W4_3_MET_h1_MET |             2064 |         0.15 |         7 |
| W4_4_MET_h1_MET |             2008 |         0.13 |         5 |
| W4_4_FX_h1_FX   |             2515 |         0.09 |         6 |
| W4_3_EQ_h1_EQ   |             1829 |         0.06 |         5 |
| W4_1_MET_h1_MET |             2064 |         0.05 |         5 |

Multiplicity: 30 cells x 5% = 1.5 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| W4_2_EQ_h1_EQ | 0.45 | 7 | 0.14 | 1.82 | -1.40 | 0.08 | 0.31 | 0.75 | 0.67 | 0.18 | 1.00 |
| W4_3_MET_h1_MET | 0.15 | 7 | -1.64 | -1.16 | 0.72 | -1.03 | -0.10 | 0.57 | 0.05 | 0.04 | 0.97 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W4_2_EQ_h1_EQ | 3.3 | 10% | 0.00 | 0.16 | -0.14 | -0.01 | 11 | -0.11 | 0.35 | 0.14 | 0.02 | NO |
| W4_2_EQ_h1_EQ | 3.3 | 20% | -0.02 | 0.29 | -0.30 | -0.04 | 28 | -0.25 | 0.35 | 0.14 | 0.02 | NO |
| W4_2_EQ_h1_EQ | 3.3 | 30% | -0.07 | 0.39 | -0.46 | -0.10 | 45 | -0.40 | 0.35 | 0.14 | 0.02 | NO |
| W4_2_EQ_h1_EQ | 3.3 | 50% | -0.19 | 0.50 | -0.78 | -0.25 | 80 | -0.71 | 0.35 | 0.14 | 0.02 | NO |
| W4_3_MET_h1_MET | 4.0 | 10% | -0.18 | -0.24 | 0.03 | -0.13 | 12 | -0.24 | 0.23 | -0.20 | 0.07 | NO |
| W4_3_MET_h1_MET | 4.0 | 20% | -0.36 | -0.48 | 0.04 | -0.28 | 32 | -0.48 | 0.23 | -0.20 | 0.07 | NO |
| W4_3_MET_h1_MET | 4.0 | 30% | -0.55 | -0.73 | 0.02 | -0.43 | 51 | -0.72 | 0.23 | -0.20 | 0.07 | NO |
| W4_3_MET_h1_MET | 4.0 | 50% | -0.92 | -1.19 | -0.05 | -0.74 | 89 | -1.17 | 0.23 | -0.20 | 0.07 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| W4_2_EQ_h1_EQ | 10% | -9.5 | -1.5 | 4.6 | 13.3 | -2/4 | 2/15 | NO |
| W4_2_EQ_h1_EQ | 20% | -19.0 | -9.4 | 6.8 | 14.4 | -10/6 | 3/24 | NO |
| W4_2_EQ_h1_EQ | 30% | -28.5 | -17.3 | 6.7 | 9.7 | -18/5 | 5/25 | NO |
| W4_2_EQ_h1_EQ | 50% | -47.5 | -33.1 | -7.4 | 0.2 | -34/-12 | 9/26 | NO |
| W4_3_MET_h1_MET | 10% | -16.0 | -3.1 | 0.9 | 1.8 | 3/3 | -9/-3 | NO |
| W4_3_MET_h1_MET | 20% | -31.9 | -12.9 | -1.4 | 2.2 | 1/5 | -19/-6 | NO |
| W4_3_MET_h1_MET | 30% | -47.9 | -22.8 | -4.3 | -11.8 | -1/5 | -29/-9 | NO |
| W4_3_MET_h1_MET | 50% | -79.8 | -42.5 | -13.9 | -79.6 | -5/-1 | -50/-23 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| W4_2_EQ_h1_EQ | -0.04 | 0 | n/a | n/a / n/a | -0.03 / 0.28 / -0.30 / -0.06 | 0.03 | -0.01 / 0.32 / -0.29 / -0.02 |
| W4_3_MET_h1_MET | -0.28 | 0 | n/a | n/a / n/a | -0.39 / -0.50 / 0.03 / -0.30 | -1.13 | -0.36 / -0.35 / 0.06 / -0.27 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| W4_2_EQ_h1_EQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | PASS (0.14) | NO |
| W4_3_MET_h1_MET | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (n/a) | fail | PASS (-0.20) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W4_2_EQ_h1_EQ | clean | 0.14 | 171,037 | -381,471 | -179,592 | -148,014 | 421,141 | 0.20 | 0.41 | 50 | 1.39 | -120,002 | -96,027 | 317,068 | 4.36 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| W4_2_EQ_h1_EQ | H1 | 1.82 | 377,399 | -77,478 | -74,124 | -70,976 | 212,712 | 3.36 | 1.77 | 39 | 3.22 | -97,691 | -76,674 | 142,906 | 4.95 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| W4_2_EQ_h1_EQ | H2 | -1.40 | -411,697 | -135,257 | -130,664 | -120,711 | 651,913 | -1.64 | -0.63 | 54 | 1.81 | -96,382 | -93,202 | 237,578 | 2.68 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| W4_2_EQ_h1_EQ | all | 0.08 | 136,739 | -381,471 | -162,164 | -134,962 | 651,913 | 0.11 | 0.21 | 50 | 1.75 | -120,002 | -95,584 | 317,068 | 8.60 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| W4_3_MET_h1_MET | clean | -1.64 | -1,555,983 | -174,246 | -134,701 | -119,218 | 1,675,491 | -1.99 | -0.93 | 60 | 0.91 | -106,343 | -96,800 | 363,837 | 2.37 | 50 | 1.46 | -81,874 | -78,736 | 280,110 |
| W4_3_MET_h1_MET | H1 | -1.16 | -298,928 | -158,319 | -140,232 | -121,143 | 481,876 | -1.54 | -0.62 | 61 | 2.10 | -124,428 | -108,199 | 174,983 | 2.88 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| W4_3_MET_h1_MET | H2 | 0.72 | 254,456 | -169,812 | -132,337 | -111,127 | 300,673 | 1.13 | 0.85 | 41 | 2.29 | -111,148 | -108,377 | 242,016 | 3.46 | 35 | 2.26 | -82,524 | -81,089 | 217,425 |
| W4_3_MET_h1_MET | all | -1.03 | -1,600,455 | -174,246 | -139,831 | -120,085 | 2,081,885 | -1.34 | -0.77 | 57 | 1.42 | -124,428 | -105,333 | 363,837 | 6.06 | 45 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE W4
