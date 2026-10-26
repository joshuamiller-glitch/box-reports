# REPORT Z3

**LEAD-weak (hedge-type; not FOUND) - gap-and-go / gap fade: best selected cell Z3_fade_h3_SCR: standalone Sharpe 2013-22 0.31, pair window 0.91, own-null rank pair window 0.96; additive uplift at 20% clean/H1/H2 +0.20/-0.40/+0.39, bootstrap lo -0.05; FOUND 0. Passes own-null in the pair window (rank 0.96-0.97), worst-decile corr -0.59..-0.69 (hedge claim -> circular-shift null would apply), clean uplift +0.24, H2 +0.17..+0.39; fails: H1 uplift -0.34..-0.40 (H1 standalone Sharpe -1.6), 2013-22 Sharpe only 0.31-0.33, bootstrap lo < 0, 2x-slip gate, plateau. Next-open entry, so no intrabar fill ambiguity.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea Z3: open outside the prior range with confirming candle, follow or fade, hold 1/3, ALL26 or SCR = 8 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 8 cells; eligible 2
| cell               |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:-------------------|-----------------:|-------------:|----------:|
| Z3_fade_h1_SCR     |              573 |         0.33 |         7 |
| Z3_fade_h3_SCR     |              569 |         0.31 |         7 |
| Z3_fade_h3_ALL26   |             1329 |         0.08 |         5 |
| Z3_fade_h1_ALL26   |             1445 |         0.08 |         6 |
| Z3_follow_h3_SCR   |              569 |        -0.44 |         2 |
| Z3_follow_h3_ALL26 |             1329 |        -0.47 |         3 |
| Z3_follow_h1_SCR   |              573 |        -0.57 |         1 |
| Z3_follow_h1_ALL26 |             1445 |        -0.87 |         1 |

Multiplicity: 8 cells x 5% = 0.4 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Z3_fade_h1_SCR | 0.33 | 7 | 1.04 | -1.67 | 1.23 | 0.82 | 0.45 | 0.69 | 0.97 | 0.36 | 0.94 |
| Z3_fade_h3_SCR | 0.31 | 7 | 1.00 | -1.59 | 1.84 | 0.91 | 0.48 | 0.86 | 0.96 | 0.34 | 0.95 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Z3_fade_h1_SCR | 7.8 | 10% | 0.14 | -0.15 | 0.15 | 0.10 | 7 | -0.02 | 0.28 | -0.59 | 0.03 | NO |
| Z3_fade_h1_SCR | 7.8 | 20% | 0.24 | -0.34 | 0.17 | 0.15 | 20 | -0.08 | 0.28 | -0.59 | 0.03 | NO |
| Z3_fade_h1_SCR | 7.8 | 30% | 0.31 | -0.54 | 0.11 | 0.14 | 33 | -0.16 | 0.28 | -0.59 | 0.03 | NO |
| Z3_fade_h1_SCR | 7.8 | 50% | 0.35 | -0.98 | -0.05 | 0.05 | 59 | -0.37 | 0.28 | -0.59 | 0.03 | NO |
| Z3_fade_h3_SCR | 3.9 | 10% | 0.11 | -0.18 | 0.23 | 0.10 | 11 | -0.01 | 0.34 | -0.69 | 0.03 | NO |
| Z3_fade_h3_SCR | 3.9 | 20% | 0.20 | -0.40 | 0.39 | 0.16 | 28 | -0.05 | 0.34 | -0.69 | 0.03 | NO |
| Z3_fade_h3_SCR | 3.9 | 30% | 0.25 | -0.63 | 0.48 | 0.18 | 44 | -0.11 | 0.34 | -0.69 | 0.03 | NO |
| Z3_fade_h3_SCR | 3.9 | 50% | 0.29 | -1.12 | 0.54 | 0.16 | 78 | -0.28 | 0.34 | -0.69 | 0.03 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| Z3_fade_h1_SCR | 10% | -2.3 | 2.6 | 5.5 | 22.2 | 2/6 | 7/8 | NO |
| Z3_fade_h1_SCR | 20% | -4.6 | -1.1 | 9.6 | 24.5 | -1/10 | 13/16 | NO |
| Z3_fade_h1_SCR | 30% | -6.8 | -4.7 | 13.4 | 26.9 | -5/15 | 18/23 | NO |
| Z3_fade_h1_SCR | 50% | -11.4 | -11.9 | 14.8 | 2.9 | -12/17 | 23/26 | NO |
| Z3_fade_h3_SCR | 10% | -3.2 | -1.3 | 8.1 | 25.8 | 8/9 | 8/8 | NO |
| Z3_fade_h3_SCR | 20% | -6.4 | -8.8 | 14.3 | 29.7 | 10/17 | 15/17 | NO |
| Z3_fade_h3_SCR | 30% | -9.6 | -16.3 | 17.9 | 29.5 | 13/25 | 7/14 | NO |
| Z3_fade_h3_SCR | 50% | -16.1 | -38.4 | 12.5 | 17.9 | 17/35 | -46/-6 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| Z3_fade_h1_SCR | 0.15 | 0 | n/a | n/a / n/a | 0.23 / -0.35 / 0.15 / 0.13 | 0.78 | 0.25 / -0.28 / 0.14 / 0.15 |
| Z3_fade_h3_SCR | 0.16 | 2 | 0.50 | 0.08 / 0.11 | 0.19 / -0.40 / 0.38 / 0.15 | 0.88 | 0.20 / -0.31 / 0.30 / 0.15 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| Z3_fade_h1_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (n/a) | fail | PASS (-0.59) | NO |
| Z3_fade_h3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.50) | fail | PASS (-0.69) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Z3_fade_h1_SCR | clean | 1.04 | 1,379,564 | -110,637 | -85,521 | -71,519 | 417,326 | 3.57 | 3.31 | 31 | 1.77 | -109,089 | -90,186 | 272,176 | 6.41 | 40 | 1.46 | -81,874 | -78,736 | 280,110 |
| Z3_fade_h1_SCR | H1 | -1.67 | -355,235 | -107,213 | -95,872 | -90,702 | 374,898 | -2.34 | -0.95 | 39 | 2.29 | -87,043 | -82,665 | 162,150 | 3.00 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| Z3_fade_h1_SCR | H2 | 1.23 | 1,049,084 | -152,153 | -146,477 | -133,973 | 526,728 | 4.39 | 1.99 | 38 | 2.38 | -109,619 | -98,691 | 251,704 | 4.27 | 46 | 2.26 | -82,524 | -81,089 | 217,425 |
| Z3_fade_h1_SCR | all | 0.82 | 2,073,413 | -152,153 | -116,599 | -93,857 | 526,728 | 2.60 | 3.94 | 35 | 2.00 | -109,619 | -91,750 | 272,176 | 12.15 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| Z3_fade_h3_SCR | clean | 1.00 | 1,197,143 | -160,311 | -72,500 | -56,729 | 393,658 | 3.63 | 3.04 | 30 | 1.71 | -94,682 | -82,514 | 241,927 | 6.98 | 39 | 1.46 | -81,874 | -78,736 | 280,110 |
| Z3_fade_h3_SCR | H1 | -1.59 | -381,045 | -217,197 | -155,676 | -133,105 | 385,515 | -1.91 | -0.99 | 36 | 2.19 | -84,127 | -81,207 | 220,043 | 2.18 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| Z3_fade_h3_SCR | H2 | 1.84 | 1,005,352 | -208,073 | -173,666 | -105,206 | 426,971 | 4.53 | 2.35 | 43 | 2.75 | -119,193 | -98,170 | 252,058 | 4.22 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| Z3_fade_h3_SCR | all | 0.91 | 1,821,450 | -217,197 | -120,873 | -86,166 | 579,220 | 2.28 | 3.14 | 34 | 2.04 | -119,193 | -86,299 | 252,058 | 12.82 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE Z3
