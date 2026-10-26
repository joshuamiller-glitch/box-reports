# REPORT V6

**NO - FX cross-sectional momentum/reversal: best selected cell V6_20_rev_h10_FX: standalone Sharpe 2013-22 0.41, pair window 0.46, own-null rank pair window 0.87; additive uplift at 20% clean/H1/H2 -0.01/+0.15/+0.24, bootstrap lo -0.10; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea V6: long 2 / short 2 of 6E 6J 6B 6A 6C by n-day z, hold 5/10 = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 1
| cell              |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:------------------|-----------------:|-------------:|----------:|
| V6_20_rev_h10_FX  |             1456 |         0.41 |         8 |
| V6_20_rev_h5_FX   |             2814 |         0.17 |         5 |
| V6_120_rev_h10_FX |             1350 |         0.15 |         4 |
| V6_120_rev_h5_FX  |             2594 |        -0.07 |         4 |
| V6_60_rev_h10_FX  |             1398 |        -0.07 |         4 |
| V6_60_mom_h10_FX  |             1398 |        -0.27 |         3 |
| V6_60_rev_h5_FX   |             2684 |        -0.29 |         4 |
| V6_60_mom_h5_FX   |             2684 |        -0.35 |         4 |
| V6_120_mom_h10_FX |             1350 |        -0.48 |         6 |
| V6_120_mom_h5_FX  |             2594 |        -0.55 |         4 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| V6_20_rev_h10_FX | 0.41 | 8 | -0.10 | 1.30 | 1.57 | 0.46 | 0.38 | 0.63 | 0.87 | 0.41 | 0.94 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V6_20_rev_h10_FX | 2.5 | 10% | 0.00 | 0.09 | 0.13 | 0.05 | 5 | -0.04 | 0.81 | 0.00 | -0.07 | NO |
| V6_20_rev_h10_FX | 2.5 | 20% | -0.01 | 0.15 | 0.24 | 0.08 | 14 | -0.10 | 0.81 | 0.00 | -0.07 | NO |
| V6_20_rev_h10_FX | 2.5 | 30% | -0.03 | 0.18 | 0.33 | 0.09 | 22 | -0.17 | 0.81 | 0.00 | -0.07 | NO |
| V6_20_rev_h10_FX | 2.5 | 50% | -0.12 | 0.18 | 0.45 | 0.07 | 39 | -0.36 | 0.81 | 0.00 | -0.07 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| V6_20_rev_h10_FX | 10% | -7.6 | 4.5 | 6.0 | 9.9 | 4/5 | 10/14 | NO |
| V6_20_rev_h10_FX | 20% | -15.3 | 5.8 | 10.4 | 17.3 | 5/7 | 19/25 | NO |
| V6_20_rev_h10_FX | 30% | -22.9 | 7.1 | 13.3 | 13.2 | 6/10 | 26/27 | NO |
| V6_20_rev_h10_FX | 50% | -38.2 | -7.4 | 12.2 | 5.0 | -8/8 | 14/28 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| V6_20_rev_h10_FX | 0.08 | 4 | 0.00 | -0.08 / -0.04 | -0.04 / 0.11 / 0.21 / 0.05 | 0.29 | -0.01 / 0.19 / 0.25 / 0.08 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| V6_20_rev_h10_FX | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.00) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V6_20_rev_h10_FX | clean | -0.10 | -87,257 | -201,216 | -141,028 | -113,097 | 536,743 | -0.13 | -0.16 | 53 | 1.43 | -100,651 | -94,021 | 305,705 | 4.26 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| V6_20_rev_h10_FX | H1 | 1.30 | 259,686 | -92,560 | -81,143 | -73,025 | 199,491 | 2.16 | 1.30 | 46 | 3.01 | -79,258 | -74,948 | 122,572 | 5.48 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| V6_20_rev_h10_FX | H2 | 1.57 | 460,956 | -70,660 | -68,931 | -65,448 | 202,220 | 3.33 | 2.28 | 49 | 2.59 | -93,052 | -87,121 | 197,062 | 4.56 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| V6_20_rev_h10_FX | all | 0.46 | 633,385 | -201,216 | -123,783 | -98,845 | 536,743 | 0.69 | 1.18 | 51 | 1.95 | -100,651 | -91,030 | 305,705 | 9.40 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE V6
