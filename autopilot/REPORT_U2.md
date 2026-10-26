# REPORT U2 - inverse-vol aggregate of the weak next-open leads, scored as ONE book

**NO (hedge-type LEAD-weak, not FOUND) - book pair-window Sharpe 1.15 vs random-entry null p95 0.71 but below the selection-corrected percentile (1.17 at 1-0.05/6; null max 1.30); additive uplift at 20% clean/H1/H2/all +0.26/-0.26/+0.44/+0.23, bootstrap lo +0.02, worst-decile corr -0.45 (hedge claim), plateau (drop-one) 0.83. Fails H1 (-0.26: the book contains four weekend-gap-fade variants whose H1 is -1.6..-2.7) and the corrected null; 2x slippage uplift 0.25/-0.28/0.41. FOUND 0.**

Pre-registered in PREREG_AUTOPILOT.md ("STRUCTURAL BATCH U1-U3", 2026-10-16T15:03Z). Components (6, choice counted toward false discovery): W6_0.25_h1_SCR, W6_0.25_h1_ALL26, Z3_fade_h3_SCR, V4_0.25_against_h1_SCR, V5_5_rev_h10_EQ, ES dip-buy (RSI2<5, close>SMA200, exit 5 days, 3 ATR stop, long only). Weights 1/(2013-22 weekly vol). Fill model: next-open entries, 1 tick/side + commission (ES dip-buy: stop test first), 2x slippage = 2 ticks. Null: every component replaced by its own timing-destroyed (random-entry, same count per year, same hold/stop, random side; long for the dip) replicate, 105 draws, summed with the same weights. Baseline B.Cfg(wk_floor=8, wk_loss_pb=None).

## Components (standalone weekly Sharpe)
| component | vol 2013-22 | Sh 2013-22 | clean | H1 | H2 | pair win | 2013-26 |
|---|---|---|---|---|---|---|---|
| W6_0.25_h1_SCR | 9,370 | 0.63 | 0.78 | -2.08 | 1.64 | 0.77 | 0.61 |
| W6_0.25_h1_ALL26 | 13,288 | 0.53 | 0.51 | -2.69 | 1.72 | 0.67 | 0.53 |
| Z3_fade_h3_SCR | 16,122 | 0.31 | 1.00 | -1.59 | 1.84 | 0.91 | 0.48 |
| V4_0.25_against_h1_SCR | 6,771 | 0.81 | 0.93 | -1.59 | 1.37 | 0.82 | 0.73 |
| V5_5_rev_h10_EQ | 18,700 | 0.22 | 1.96 | -0.36 | -1.32 | 0.83 | 0.39 |
| ES_DIP | 4,938 | 0.21 | 0.94 | 3.64 | 1.29 | 1.44 | 0.54 |

Weekly correlation of the components in the pair window:

|                        |   W6_0.25_h1_SCR |   W6_0.25_h1_ALL26 |   Z3_fade_h3_SCR |   V4_0.25_against_h1_SCR |   V5_5_rev_h10_EQ |   ES_DIP |
|:-----------------------|-----------------:|-------------------:|-----------------:|-------------------------:|------------------:|---------:|
| W6_0.25_h1_SCR         |             1    |               0.95 |             0.64 |                     0.94 |              0.07 |    -0.05 |
| W6_0.25_h1_ALL26       |             0.95 |               1    |             0.67 |                     0.9  |              0.08 |    -0.04 |
| Z3_fade_h3_SCR         |             0.64 |               0.67 |             1    |                     0.6  |              0.05 |    -0.05 |
| V4_0.25_against_h1_SCR |             0.94 |               0.9  |             0.6  |                     1    |              0.08 |    -0.05 |
| V5_5_rev_h10_EQ        |             0.07 |               0.08 |             0.05 |                     0.08 |              1    |     0.01 |
| ES_DIP                 |            -0.05 |              -0.04 |            -0.05 |                    -0.05 |              0.01 |     1    |

The four gap-fade variants correlate 0.64-0.95: they are one trade type (weekend-gap fade; see REPORT_U3), so the book is effectively three independent ideas (weekend fade, equity relative-strength reversal, ES dip).

| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| BOOK | 0.71 | 10 | 1.27 | -1.34 | 1.69 | 1.15 | 0.83 | 0.71 | 0.99 | 0.10 | 1.00 |

| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BOOK | 1.4 | 10% | 0.16 | -0.12 | 0.31 | 0.15 | 7 | 0.03 | 0.11 | -0.45 | 0.09 | NO |
| BOOK | 1.4 | 20% | 0.26 | -0.26 | 0.44 | 0.23 | 20 | 0.02 | 0.11 | -0.45 | 0.09 | NO |
| BOOK | 1.4 | 30% | 0.33 | -0.42 | 0.45 | 0.25 | 33 | -0.02 | 0.11 | -0.45 | 0.09 | NO |
| BOOK | 1.4 | 50% | 0.38 | -0.76 | 0.34 | 0.20 | 59 | -0.17 | 0.11 | -0.45 | 0.09 | NO |

| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| BOOK | 10% | 1.8 | 2.5 | 8.0 | 23.6 | 9/8 | 9/12 | NO |
| BOOK | 20% | 3.5 | -1.3 | 13.9 | 32.2 | 7/14 | 18/23 | NO |
| BOOK | 30% | 5.3 | -5.0 | 18.1 | 38.9 | 6/20 | 20/23 | NO |
| BOOK | 50% | 8.8 | -17.9 | 18.4 | 45.2 | 2/32 | -24/-4 | NO |

| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| BOOK | 0.23 | 6 | 0.83 | 0.17 / 0.21 | 0.25 / -0.28 / 0.41 / 0.21 | 1.09 | 0.27 / -0.19 / 0.41 / 0.24 |

Drop-one-component neighbours:
- drop_W6_0.25_h1_SCR: all-in uplift 0.23 (clean 0.25, H1 -0.06, H2 0.40)
- drop_W6_0.25_h1_ALL26: all-in uplift 0.24 (clean 0.27, H1 -0.13, H2 0.40)
- drop_Z3_fade_h3_SCR: all-in uplift 0.20 (clean 0.23, H1 -0.17, H2 0.37)
- drop_V4_0.25_against_h1_SCR: all-in uplift 0.21 (clean 0.23, H1 -0.11, H2 0.41)
- drop_V5_5_rev_h10_EQ: all-in uplift 0.19 (clean 0.18, H1 -0.28, H2 0.48)
- drop_ES_DIP: all-in uplift 0.17 (clean 0.24, H1 -0.52, H2 0.38)

| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| BOOK | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | PASS (0.83) | fail | PASS (-0.45) | NO |

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BOOK | clean | 1.27 | 1,869,029 | -88,614 | -66,316 | -53,524 | 161,166 | 6.16 | 11.60 | 40 | 1.79 | -99,157 | -85,825 | 237,871 | 7.95 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| BOOK | H1 | -1.34 | -255,497 | -183,066 | -142,804 | -113,406 | 416,529 | -1.49 | -0.61 | 57 | 2.41 | -80,619 | -73,634 | 159,199 | 3.25 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| BOOK | H2 | 1.69 | 1,542,899 | -134,679 | -121,436 | -97,401 | 268,853 | 8.47 | 5.74 | 41 | 2.71 | -109,874 | -93,331 | 235,845 | 5.19 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| BOOK | all | 1.15 | 3,156,431 | -183,066 | -103,230 | -76,864 | 438,795 | 4.59 | 7.19 | 43 | 2.11 | -109,874 | -86,915 | 237,871 | 15.27 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |


## Reading
Diversifying the weak leads lifts the pair-window standalone Sharpe to 1.15 (components 0.67-1.44) and gives clean +0.26 / H2 +0.44 uplift at 20% with bootstrap lower bound +0.02 and a negative worst-decile correlation (-0.45), but H1 is negative (-0.26) because the weekend-gap component dominates the book's risk and loses in H1, and the book does not clear the selection-corrected null. It stays a hedge-type weak lead; with the circular-shift null applying (wd corr < 0) it is not FOUND-PENDING.

## Executability
Components are next-open daily rules: weekend-gap fade (Sunday evening NT8 strategy), ES/NQ/RTY/YM 5-day relative-strength reversal (multi-leg, micros), ES RSI2 dip-buy (daily). Needs three small NT8 strategies; margin modest at 20% share.

DONE U2
