# REPORT W6

**LEAD-weak (same family as Z3; not FOUND) - gap-size-conditioned gap fade: best selected cell W6_0.25_h1_SCR: standalone Sharpe 2013-22 0.63, pair window 0.77, own-null rank pair window 0.93; additive uplift at 20% clean/H1/H2 +0.14/-0.69/+0.37, bootstrap lo -0.13; FOUND 0. Dev Sharpe 0.5-0.6 with 7-9 of 10 positive years for every 0.25-ATR cell and positive in the pair window (0.51-0.77), own-null rank 0.91-0.98, but H1 uplift -0.27..-0.69 (H1 standalone -0.9..-2.7), bootstrap lo < 0, plateau and 2x-slippage gates fail. Gap fade does not help the pair in H1.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea W6: gap >= 0.25/0.5/1.0 ATR with confirming candle, fade next open, hold 1/3, ALL26 or SCR = 12 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 5
| cell             |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-----------------|-----------------:|-------------:|----------:|
| W6_0.25_h1_SCR   |              598 |         0.63 |         9 |
| W6_0.25_h3_SCR   |              594 |         0.61 |         8 |
| W6_0.25_h1_ALL26 |             1476 |         0.53 |         7 |
| W6_0.5_h1_ALL26  |              477 |         0.53 |         9 |
| W6_0.5_h1_SCR    |              242 |         0.52 |         9 |
| W6_1.0_h1_SCR    |               52 |         0.51 |         7 |
| W6_1.0_h1_ALL26  |              100 |         0.48 |         7 |
| W6_1.0_h3_SCR    |               52 |         0.44 |         7 |
| W6_0.25_h3_ALL26 |             1367 |         0.44 |         7 |
| W6_0.5_h3_SCR    |              241 |         0.36 |         7 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| W6_0.25_h1_SCR | 0.63 | 9 | 0.78 | -2.08 | 1.64 | 0.77 | 0.61 | 0.86 | 0.93 | 0.23 | 1.00 |
| W6_0.25_h3_SCR | 0.61 | 8 | 0.73 | -0.91 | 0.65 | 0.51 | 0.55 | 0.74 | 0.91 | 0.44 | 0.98 |
| W6_0.25_h1_ALL26 | 0.53 | 7 | 0.51 | -2.69 | 1.72 | 0.67 | 0.53 | 0.40 | 0.98 | -0.13 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W6_0.25_h1_SCR | 6.7 | 10% | 0.09 | -0.35 | 0.29 | 0.08 | 6 | -0.05 | 0.13 | 0.13 | 0.09 | NO |
| W6_0.25_h1_SCR | 6.7 | 20% | 0.14 | -0.69 | 0.37 | 0.09 | 14 | -0.13 | 0.13 | 0.13 | 0.09 | NO |
| W6_0.25_h1_SCR | 6.7 | 30% | 0.16 | -1.02 | 0.34 | 0.06 | 24 | -0.25 | 0.13 | 0.13 | 0.09 | NO |
| W6_0.25_h1_SCR | 6.7 | 50% | 0.15 | -1.62 | 0.19 | -0.08 | 76 | -0.50 | 0.13 | 0.13 | 0.09 | NO |
| W6_0.25_h3_SCR | 3.2 | 10% | 0.07 | -0.12 | -0.00 | 0.02 | 15 | -0.07 | 0.08 | -0.00 | 0.11 | NO |
| W6_0.25_h3_SCR | 3.2 | 20% | 0.11 | -0.27 | -0.04 | 0.02 | 31 | -0.16 | 0.08 | -0.00 | 0.11 | NO |
| W6_0.25_h3_SCR | 3.2 | 30% | 0.12 | -0.45 | -0.10 | -0.01 | 47 | -0.27 | 0.08 | -0.00 | 0.11 | NO |
| W6_0.25_h3_SCR | 3.2 | 50% | 0.10 | -0.81 | -0.25 | -0.12 | 79 | -0.50 | 0.08 | -0.00 | 0.11 | NO |
| W6_0.25_h1_ALL26 | 4.7 | 10% | 0.04 | -0.23 | 0.29 | 0.06 | 4 | -0.06 | 0.10 | -0.65 | 0.10 | NO |
| W6_0.25_h1_ALL26 | 4.7 | 20% | 0.04 | -0.49 | 0.41 | 0.06 | 14 | -0.15 | 0.10 | -0.65 | 0.10 | NO |
| W6_0.25_h1_ALL26 | 4.7 | 30% | 0.02 | -0.75 | 0.41 | 0.01 | 25 | -0.26 | 0.10 | -0.65 | 0.10 | NO |
| W6_0.25_h1_ALL26 | 4.7 | 50% | -0.06 | -1.29 | 0.30 | -0.12 | 46 | -0.51 | 0.10 | -0.65 | 0.10 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| W6_0.25_h1_SCR | 10% | -1.8 | 4.3 | 6.8 | 19.7 | 4/7 | 8/8 | NO |
| W6_0.25_h1_SCR | 20% | -3.6 | 4.7 | 12.6 | 27.8 | 7/15 | 13/13 | NO |
| W6_0.25_h1_SCR | 30% | -5.4 | -8.6 | 12.1 | 36.0 | 11/22 | -14/-6 | NO |
| W6_0.25_h1_SCR | 50% | -8.9 | -60.2 | 0.4 | 25.6 | 18/36 | -69/-61 | NO |
| W6_0.25_h3_SCR | 10% | -6.3 | -5.2 | 5.8 | 21.4 | -6/5 | 9/9 | NO |
| W6_0.25_h3_SCR | 20% | -12.6 | -11.3 | 10.5 | 30.0 | -12/10 | 16/17 | NO |
| W6_0.25_h3_SCR | 30% | -18.8 | -17.3 | 15.2 | 33.8 | -18/15 | 24/26 | NO |
| W6_0.25_h3_SCR | 50% | -31.4 | -32.1 | 6.9 | 23.0 | -30/22 | 6/9 | NO |
| W6_0.25_h1_ALL26 | 10% | -3.2 | 5.5 | 7.7 | 16.4 | 5/7 | 9/10 | NO |
| W6_0.25_h1_ALL26 | 20% | -6.5 | 4.3 | 13.7 | 16.3 | 4/14 | 17/19 | NO |
| W6_0.25_h1_ALL26 | 30% | -9.7 | 3.1 | 18.1 | 16.3 | 2/18 | 24/28 | NO |
| W6_0.25_h1_ALL26 | 50% | -16.1 | -17.3 | 11.7 | 7.7 | 0/23 | -2/8 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| W6_0.25_h1_SCR | 0.09 | 2 | 0.50 | 0.05 / 0.07 | 0.13 / -0.71 / 0.35 / 0.08 | 0.74 | 0.14 / -0.48 / 0.35 / 0.11 |
| W6_0.25_h3_SCR | 0.02 | 4 | 0.25 | -0.05 / -0.02 | 0.10 / -0.28 / -0.05 / 0.01 | 0.49 | 0.10 / -0.19 / -0.06 / 0.02 |
| W6_0.25_h1_ALL26 | 0.06 | 2 | 0.50 | 0.03 / 0.06 | 0.01 / -0.55 / 0.34 / 0.01 | 0.53 | 0.05 / -0.39 / 0.37 / 0.07 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| W6_0.25_h1_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.50) | fail | PASS (0.13) | NO |
| W6_0.25_h3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.25) | fail | PASS (-0.00) | NO |
| W6_0.25_h1_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.50) | fail | PASS (-0.65) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| W6_0.25_h1_SCR | clean | 0.78 | 1,005,588 | -110,087 | -66,159 | -54,282 | 318,487 | 3.41 | 3.16 | 31 | 1.62 | -97,702 | -85,254 | 253,689 | 6.43 | 46 | 1.46 | -81,874 | -78,736 | 280,110 |
| W6_0.25_h1_SCR | H1 | -2.08 | -526,922 | -238,528 | -231,556 | -186,807 | 580,582 | -2.07 | -0.91 | 25 | 1.80 | -97,373 | -91,497 | 175,660 | 2.48 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| W6_0.25_h1_SCR | H2 | 1.64 | 1,726,947 | -220,230 | -170,191 | -122,247 | 299,724 | 7.39 | 5.76 | 19 | 2.60 | -102,449 | -93,838 | 242,458 | 5.28 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| W6_0.25_h1_SCR | all | 0.77 | 2,205,612 | -238,528 | -136,551 | -95,419 | 580,582 | 2.50 | 3.80 | 28 | 1.91 | -102,449 | -89,346 | 253,689 | 13.19 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| W6_0.25_h3_SCR | clean | 0.73 | 900,121 | -131,618 | -66,795 | -51,429 | 479,621 | 3.01 | 1.88 | 29 | 1.58 | -121,359 | -90,519 | 239,176 | 6.69 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| W6_0.25_h3_SCR | H1 | -0.91 | -212,266 | -135,816 | -129,198 | -119,848 | 294,433 | -1.30 | -0.72 | 29 | 2.38 | -82,840 | -80,564 | 171,229 | 3.10 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| W6_0.25_h3_SCR | H2 | 0.65 | 310,470 | -258,302 | -184,550 | -130,526 | 482,570 | 1.18 | 0.64 | 32 | 2.16 | -110,655 | -95,154 | 250,665 | 3.41 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| W6_0.25_h3_SCR | all | 0.51 | 998,326 | -258,302 | -123,034 | -86,712 | 482,570 | 1.27 | 2.07 | 30 | 1.84 | -121,359 | -90,696 | 250,665 | 11.91 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| W6_0.25_h1_ALL26 | clean | 0.51 | 714,702 | -99,076 | -85,395 | -70,681 | 564,453 | 1.85 | 1.27 | 42 | 1.48 | -103,059 | -86,763 | 304,623 | 5.07 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| W6_0.25_h1_ALL26 | H1 | -2.69 | -492,884 | -148,411 | -139,274 | -126,021 | 519,211 | -2.65 | -0.95 | 43 | 2.08 | -82,584 | -78,469 | 155,301 | 2.87 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| W6_0.25_h1_ALL26 | H2 | 1.72 | 1,596,604 | -237,856 | -165,769 | -118,461 | 325,341 | 6.62 | 4.91 | 30 | 2.67 | -95,241 | -90,698 | 215,698 | 5.75 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| W6_0.25_h1_ALL26 | all | 0.67 | 1,818,421 | -237,856 | -118,616 | -96,184 | 575,219 | 2.16 | 3.16 | 40 | 1.87 | -103,059 | -87,173 | 304,623 | 10.61 | 45 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE W6
