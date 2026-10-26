# REPORT N2

**NO - macro event bars (FOMC 14:00, NFP/CPI 08:30) follow/fade to the day end: best selected cell N2_NFP_fade: standalone Sharpe 2013-22 -0.07, pair window 0.74, own-null rank pair window 0.98; additive uplift at 20% clean/H1/H2 +0.23/-0.15/-0.11, bootstrap lo -0.06; FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea N2: ES NQ ZN GC 6E pooled, 6 cells; clean-only selection.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 6 cells; eligible 2
| cell           |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:---------------|-----------------:|-------------:|----------:|
| N2_NFP_fade    |       1000000000 |         1.38 |        10 |
| N2_FOMC_follow |       1000000000 |         0.82 |        10 |
| N2_CPI_fade    |                0 |        -0.12 |         0 |
| N2_CPI_follow  |                0 |        -0.29 |         0 |
| N2_FOMC_fade   |                0 |        -0.97 |         0 |
| N2_NFP_follow  |                0 |        -1.63 |         0 |

Multiplicity: 6 cells x 5% = 0.3 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| N2_NFP_fade | -0.07 | 5 | 1.38 | 0.53 | -0.48 | 0.74 | 0.13 | 0.59 | 0.98 | 0.11 | 0.87 |
| N2_FOMC_follow | 0.15 | 6 | 0.82 | -0.28 | 1.07 | 0.72 | 0.23 | 0.55 | 0.98 | 0.11 | 0.97 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N2_NFP_fade | 9.5 | 10% | 0.13 | -0.06 | -0.04 | 0.07 | 0 | -0.02 | 0.52 | -0.54 | -0.00 | NO |
| N2_NFP_fade | 9.5 | 20% | 0.23 | -0.15 | -0.11 | 0.12 | 7 | -0.06 | 0.52 | -0.54 | -0.00 | NO |
| N2_NFP_fade | 9.5 | 30% | 0.32 | -0.26 | -0.22 | 0.14 | 14 | -0.13 | 0.52 | -0.54 | -0.00 | NO |
| N2_NFP_fade | 9.5 | 50% | 0.44 | -0.49 | -0.49 | 0.13 | 99 | -0.32 | 0.52 | -0.54 | -0.00 | NO |
| N2_FOMC_follow | 8.8 | 10% | 0.05 | -0.06 | 0.06 | 0.04 | -1 | -0.03 | 0.04 | -0.56 | 0.11 | NO |
| N2_FOMC_follow | 8.8 | 20% | 0.09 | -0.13 | 0.11 | 0.06 | -1 | -0.07 | 0.04 | -0.56 | 0.11 | NO |
| N2_FOMC_follow | 8.8 | 30% | 0.12 | -0.22 | 0.15 | 0.07 | -1 | -0.13 | 0.04 | -0.56 | 0.11 | NO |
| N2_FOMC_follow | 8.8 | 50% | 0.13 | -0.40 | 0.20 | 0.05 | -1 | -0.27 | 0.04 | -0.56 | 0.11 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| N2_NFP_fade | 10% | -5.5 | 9.1 | 9.8 | 13.7 | 8/10 | 10/10 | NO |
| N2_NFP_fade | 20% | -11.0 | 11.6 | 19.0 | 16.8 | 11/18 | 20/20 | NO |
| N2_NFP_fade | 30% | -16.5 | -11.0 | 22.7 | 6.5 | 13/27 | 18/23 | NO |
| N2_NFP_fade | 50% | -27.6 | -139.7 | 14.6 | -14.0 | 18/39 | -43/3 | NO |
| N2_FOMC_follow | 10% | -6.5 | 10.7 | 10.6 | 7.5 | 10/10 | 10/10 | NO |
| N2_FOMC_follow | 20% | -13.1 | 20.6 | 20.4 | 14.9 | 20/20 | 20/20 | NO |
| N2_FOMC_follow | 30% | -19.6 | 30.6 | 30.2 | 22.4 | 30/30 | 30/30 | NO |
| N2_FOMC_follow | 50% | -32.7 | -13.1 | 35.1 | 24.5 | -14/34 | 13/31 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| N2_NFP_fade | 0.12 | 0 | n/a | n/a / n/a | 0.21 / -0.16 / -0.14 / 0.10 | 0.63 | 0.23 / -0.01 / -0.12 / 0.12 |
| N2_FOMC_follow | 0.06 | 0 | n/a | n/a / n/a | 0.08 / -0.15 / 0.10 / 0.05 | 0.64 | 0.10 / -0.06 / 0.09 / 0.07 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| N2_NFP_fade | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (n/a) | fail | PASS (-0.54) | NO |
| N2_FOMC_follow | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (n/a) | fail | PASS (-0.56) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N2_NFP_fade | clean | 1.38 | 1,254,452 | -89,123 | -61,908 | -39,889 | 141,365 | 5.43 | 8.87 | 9 | 1.78 | -94,024 | -80,760 | 248,735 | 6.86 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| N2_NFP_fade | H1 | 0.53 | 150,698 | -231,174 | -146,400 | -97,600 | 231,174 | 0.86 | 0.65 | 7 | 2.57 | -78,287 | -77,610 | 151,713 | 4.21 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| N2_NFP_fade | H2 | -0.48 | -200,227 | -463,209 | -240,230 | -123,038 | 492,152 | -0.52 | -0.41 | 8 | 2.08 | -82,524 | -81,089 | 314,443 | 2.23 | 44 | 2.30 | -82,524 | -81,089 | 217,425 |
| N2_NFP_fade | all | 0.74 | 1,204,923 | -463,209 | -125,273 | -71,984 | 492,152 | 1.23 | 2.45 | 8 | 2.00 | -94,024 | -80,559 | 314,443 | 9.69 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| N2_FOMC_follow | clean | 0.82 | 748,423 | -231,900 | -77,689 | -42,652 | 304,618 | 1.91 | 2.46 | 7 | 1.58 | -81,874 | -78,727 | 301,496 | 5.16 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| N2_FOMC_follow | H1 | -0.28 | -43,648 | -124,483 | -113,712 | -75,808 | 124,483 | -0.37 | -0.35 | 7 | 2.61 | -78,287 | -77,610 | 174,978 | 3.32 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| N2_FOMC_follow | H2 | 1.07 | 225,905 | -93,178 | -51,059 | -25,530 | 93,178 | 2.90 | 2.42 | 6 | 2.45 | -79,829 | -79,741 | 217,425 | 3.81 | 44 | 2.30 | -82,524 | -81,089 | 217,425 |
| N2_FOMC_follow | all | 0.72 | 930,679 | -231,900 | -87,845 | -46,983 | 304,618 | 1.55 | 3.06 | 7 | 1.92 | -81,874 | -78,921 | 301,496 | 9.83 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE N2
