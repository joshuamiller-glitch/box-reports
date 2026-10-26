# REPORT X4

**NO - X4 gold Jan-Feb long does not replicate: SI_A 2013-26 Sharpe 0.11 (2013-22 null rank 0.80, pair-window rank 0.49), PL_A 0.22 (ranks 0.99/0.31); additive uplift at 20% SI +0.01/-0.25/+0.23, PL -0.11/-0.09/+0.12 (clean/H1/H2); FOUND 0, GC_A reference unchanged.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea X4: the GC_A rule (long Jan 1 - Feb 28) frozen and run on SI and PL (3 windows each in the pair window; small-sample); GC_A shown as reference only. Replication reading: SI and PL both needed Sharpe > 0 and own-null rank >= 0.90 in 2013-22 and the pair window.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| SI_A | 0.14 | 6 | -0.01 | 0.27 | 1.46 | 0.33 | 0.11 | 1.06 | 0.49 | 0.40 | 0.80 |
| PL_A | 0.42 | 7 | -0.38 | 0.04 | 1.34 | -0.10 | 0.22 | 0.96 | 0.31 | 0.23 | 0.99 |
| GC_A | 0.56 | 8 | 0.57 | 1.42 | 1.88 | 0.92 | 0.59 | 1.10 | 0.85 | 0.42 | 0.98 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SI_A | 11.3 | 10% | 0.01 | -0.07 | 0.12 | 0.03 | 3 | -0.08 | 0.66 | -0.08 | -0.03 | NO |
| SI_A | 11.3 | 20% | 0.01 | -0.25 | 0.23 | 0.04 | 41 | -0.18 | 0.66 | -0.08 | -0.03 | NO |
| SI_A | 11.3 | 30% | 0.00 | -0.47 | 0.33 | 0.03 | 104 | -0.30 | 0.66 | -0.08 | -0.03 | NO |
| SI_A | 11.3 | 50% | -0.03 | -0.90 | 0.48 | -0.03 | 231 | -0.56 | 0.66 | -0.08 | -0.03 | NO |
| PL_A | 12.5 | 10% | -0.05 | 0.01 | 0.06 | -0.02 | 5 | -0.13 | 0.63 | -0.08 | -0.03 | NO |
| PL_A | 12.5 | 20% | -0.11 | -0.09 | 0.12 | -0.05 | 24 | -0.28 | 0.63 | -0.08 | -0.03 | NO |
| PL_A | 12.5 | 30% | -0.18 | -0.25 | 0.18 | -0.11 | 79 | -0.45 | 0.63 | -0.08 | -0.03 | NO |
| PL_A | 12.5 | 50% | -0.34 | -0.66 | 0.28 | -0.25 | 189 | -0.78 | 0.63 | -0.08 | -0.03 | NO |
| GC_A | 9.6 | 10% | 0.04 | 0.31 | 0.10 | 0.09 | 0 | 0.00 | 0.91 | -0.08 | -0.11 | NO |
| GC_A | 9.6 | 20% | 0.07 | 0.52 | 0.19 | 0.16 | 0 | -0.00 | 0.91 | -0.08 | -0.11 | NO |
| GC_A | 9.6 | 30% | 0.10 | 0.61 | 0.27 | 0.22 | 21 | -0.02 | 0.91 | -0.08 | -0.11 | NO |
| GC_A | 9.6 | 50% | 0.14 | 0.53 | 0.43 | 0.29 | 93 | -0.10 | 0.91 | -0.08 | -0.11 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| SI_A | 10% | -8.2 | 6.2 | 9.0 | 13.9 | 5/8 | 10/14 | NO |
| SI_A | 20% | -16.3 | -37.9 | 10.6 | 1.0 | 6/17 | -45/-14 | NO |
| SI_A | 30% | -24.5 | -100.0 | 9.9 | -37.4 | 6/23 | -111/-42 | NO |
| SI_A | 50% | -40.8 | -224.3 | 2.4 | -114.3 | -20/27 | -242/-111 | NO |
| PL_A | 10% | -10.6 | 4.5 | 8.8 | 7.4 | 4/8 | 10/19 | NO |
| PL_A | 20% | -21.2 | -21.1 | 10.6 | -0.8 | 2/14 | -28/-5 | NO |
| PL_A | 30% | -31.8 | -74.9 | 3.0 | -9.9 | -1/8 | -84/-28 | NO |
| PL_A | 50% | -53.0 | -182.5 | -23.7 | -28.2 | -53/-19 | -198/-75 | NO |
| GC_A | 10% | -5.9 | 10.0 | 10.0 | 17.0 | 10/10 | 10/29 | NO |
| GC_A | 20% | -11.8 | 17.3 | 19.1 | 20.1 | 20/20 | 13/16 | NO |
| GC_A | 30% | -17.7 | -17.2 | 22.8 | 5.4 | 24/28 | -24/2 | NO |
| GC_A | 50% | -29.4 | -86.3 | 25.8 | -45.0 | -16/38 | -96/-24 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| SI_A | 0.04 | 4 | 0.25 | -0.03 / 0.02 | 0.01 / -0.25 / 0.23 / 0.04 | 0.32 | 0.00 / 0.02 / 0.21 / 0.05 |
| PL_A | -0.05 | 4 | 0.00 | -0.08 / -0.03 | -0.11 / -0.09 / 0.12 / -0.05 | -0.10 | -0.10 / 0.06 / 0.12 / -0.03 |
| GC_A | 0.16 | 4 | 0.75 | 0.11 / 0.16 | 0.07 / 0.52 / 0.19 / 0.16 | 0.92 | 0.06 / 0.56 / 0.18 / 0.17 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| SI_A | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.25) | fail | PASS (-0.08) | NO |
| PL_A | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.08) | NO |
| GC_A | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | PASS (0.75) | fail | PASS (-0.08) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SI_A | clean | -0.01 | -6,559 | -183,096 | -104,980 | -64,035 | 320,170 | -0.02 | -0.02 | 10 | 1.46 | -100,131 | -82,471 | 298,954 | 4.44 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| SI_A | H1 | 0.27 | 135,141 | -524,041 | -308,690 | -205,793 | 1,145,581 | 0.35 | 0.12 | 7 | 2.35 | -168,432 | -123,360 | 403,484 | 1.57 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| SI_A | H2 | 1.46 | 363,558 | -75,795 | -37,897 | -18,949 | 226,710 | 5.69 | 1.60 | 3 | 2.59 | -82,524 | -81,089 | 217,425 | 4.00 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| SI_A | all | 0.33 | 492,139 | -524,041 | -141,695 | -79,398 | 1,145,581 | 0.46 | 0.43 | 8 | 1.89 | -168,432 | -91,824 | 403,484 | 7.02 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |
| PL_A | clean | -0.38 | -357,927 | -231,643 | -167,867 | -121,519 | 550,778 | -0.56 | -0.65 | 10 | 1.28 | -104,356 | -88,246 | 377,347 | 3.24 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| PL_A | H1 | 0.04 | 17,562 | -454,985 | -227,492 | -151,662 | 565,384 | 0.05 | 0.03 | 4 | 2.58 | -147,715 | -113,001 | 230,356 | 2.60 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| PL_A | H2 | 1.34 | 180,219 | -57,625 | -28,812 | -14,406 | 93,002 | 3.71 | 1.94 | 3 | 2.44 | -82,524 | -81,089 | 217,425 | 3.75 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| PL_A | all | -0.10 | -160,146 | -454,985 | -183,183 | -108,783 | 596,278 | -0.14 | -0.27 | 8 | 1.75 | -147,715 | -93,286 | 377,347 | 6.99 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |
| GC_A | clean | 0.57 | 272,748 | -176,837 | -71,224 | -39,022 | 269,128 | 0.90 | 1.01 | 8 | 1.56 | -81,874 | -78,831 | 289,483 | 4.88 | 40 | 1.46 | -81,874 | -78,736 | 280,110 |
| GC_A | H1 | 1.42 | 549,155 | -296,289 | -148,145 | -98,763 | 758,600 | 2.53 | 0.72 | 4 | 3.43 | -100,107 | -89,197 | 281,113 | 2.70 | 29 | 2.83 | -78,287 | -77,610 | 151,713 |
| GC_A | H2 | 1.88 | 282,059 | -17,326 | -8,663 | -4,332 | 189,398 | 19.30 | 1.49 | 3 | 2.53 | -82,524 | -81,089 | 217,425 | 3.89 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| GC_A | all | 0.92 | 1,103,963 | -296,289 | -82,540 | -43,698 | 758,600 | 1.68 | 1.46 | 6 | 2.07 | -100,107 | -81,805 | 289,483 | 10.42 | 38 | 1.86 | -82,524 | -79,220 | 280,110 |


Reading: neither second metal reaches rank 0.90 in the pair window (SI 0.49, PL 0.31); the 2013-22 evidence is weak for SI (rank 0.80) and strong only for PL (0.99). The gold Jan-Feb effect is not a metals-wide pattern; GC_A remains a 3-window observation. Windows per sleeve: 13 (2013-2026), 3 in the pair window.


DONE X4
