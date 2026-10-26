# REPORT B3

**NO - trend on NQ/ES, NQ/RTY, ES/RTY ratios: 48 cells, only 2 pass the 2013-22 development screen (daily TSM20 on NQ/RTY and NQ/ES); best all-in additive uplift 0.00 at 20% share (NQ_RTY_D_TSM20), clean/H1/H2 -0.09/-0.04/0.29; own-null rank 0.82; all 30-minute cells lose to cost (mean 2013-22 Sharpe -1.01); FOUND 0.**



## Scope and protocol
Pre-registered (PREREG_AUTOPILOT.md CAPACITY BACKLOG B3, 2026-10-16T14:06Z). Ratio index x = cumulative sum of (pct return A - pct return B) built from the 1-minute back-adjusted series aggregated to 30-minute bars and to label-day bars (NQ/ES 2013-2026, RTY 2017-07..2026). Rules per timeframe (8): EMA cross, Donchian N/M, time-series momentum sign. 3 pairs x 2 timeframes x 8 rules = 48 cells. Long spread = long A / short B; legs sized to equal dollar ATR20 risk ($7,000 per leg per ATR20, refreshed weekly from prior data, fractional contracts); signal at bar close, position at the next bar open; costs and slippage on BOTH legs on every change of either leg's contract count, plus both legs' roll round trip when held through a roll. Selection on 2013-2022 only (RTY pairs 2017-07..2022): >= 100 position segments, >= 7 of 10 positive calendar years (>= 4 of 6 for RTY pairs), top 3 per timeframe. Scale: 2013-22 (RTY pairs: 2017-22) weekly vol -> pair clean weekly vol. Own null: random segments with the same durations per calendar year, random side (203 draws).

Fill model: market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; slippage 1 tick per side per leg (NQ $5, ES $12.50, RTY $5) + $4.36 round trip per contract per leg; 2x slippage = 2 ticks.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022) - top cells and family summary
| cell                 |   segs_2013_22 |   segs_pairwin |   sh_2013_22 |   yrs_pos |   need |
|:---------------------|---------------:|---------------:|-------------:|----------:|-------:|
| ES_RTY_D_TSM120      |             26 |             24 |         0.82 |         3 |      4 |
| NQ_RTY_D_EMA50-200   |              4 |              6 |         0.75 |         5 |      4 |
| NQ_RTY_D_EMA20-100   |             14 |             16 |         0.74 |         4 |      4 |
| NQ_RTY_D_TSM120      |             46 |             56 |         0.65 |         5 |      4 |
| NQ_ES_D_EMA20-100    |             21 |             14 |         0.35 |         7 |      7 |
| NQ_RTY_D_TSM20       |            136 |             75 |         0.31 |         5 |      4 |
| NQ_ES_D_TSM20        |            231 |            110 |         0.3  |         7 |      7 |
| NQ_ES_D_TSM120       |             67 |             52 |         0.25 |         8 |      7 |
| NQ_RTY_30m_EMA48-192 |            382 |            246 |         0.22 |         2 |      4 |
| NQ_ES_D_EMA50-200    |             14 |              4 |         0.16 |         6 |      7 |
| ES_RTY_D_DON55-20    |             24 |             17 |         0.16 |         3 |      4 |
| NQ_RTY_D_DON55-20    |             25 |             19 |         0.14 |         3 |      4 |
| NQ_ES_D_DON20-10     |            110 |             39 |         0.11 |         5 |      7 |
| ES_RTY_D_EMA10-40    |             39 |             31 |         0.11 |         2 |      4 |

Mean/max 2013-22 Sharpe by pair x timeframe (cells per group = 8):

| pair   | tf   |   mean |   max |
|:-------|:-----|-------:|------:|
| ES_RTY | 30m  |  -1.32 | -0.28 |
| ES_RTY | D    |   0.11 |  0.82 |
| NQ_ES  | 30m  |  -1.37 | -0.1  |
| NQ_ES  | D    |   0.14 |  0.35 |
| NQ_RTY | 30m  |  -0.35 |  0.22 |
| NQ_RTY | D    |   0.29 |  0.75 |

Eligible cells: daily 2, 30-minute 0. Several slow daily cells with Sharpe 0.7-0.8 on RTY pairs (EMA50/200, EMA20/100, TSM120) are ineligible: 4-46 segments and 2-5 positive years of the 6 available. The 30-minute cells average Sharpe -1.3 on NQ/ES and ES/RTY: the spread moves a few basis points per bar and two legs of costs overwhelm it.

## Selected cells
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ_RTY_D_TSM20 | 0.31 | 5 | 0.04 | 0.87 | 2.26 | 0.56 | 0.41 | 0.86 | 0.82 | 0.66 | 0.81 |
| NQ_ES_D_TSM20 | 0.30 | 7 | -0.83 | -1.25 | 1.69 | -0.31 | 0.21 | 0.79 | 0.34 | 0.40 | 0.92 |

### Additive
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ_RTY_D_TSM20 | 8.2 | 10% | -0.04 | -0.00 | 0.16 | 0.01 | 8 | -0.09 | 0.01 | -0.05 | 0.18 | NO |
| NQ_RTY_D_TSM20 | 8.2 | 20% | -0.09 | -0.04 | 0.29 | 0.00 | 22 | -0.20 | 0.01 | -0.05 | 0.18 | NO |
| NQ_RTY_D_TSM20 | 8.2 | 30% | -0.16 | -0.11 | 0.40 | -0.03 | 37 | -0.31 | 0.01 | -0.05 | 0.18 | NO |
| NQ_RTY_D_TSM20 | 8.2 | 50% | -0.30 | -0.27 | 0.55 | -0.12 | 65 | -0.56 | 0.01 | -0.05 | 0.18 | NO |
| NQ_ES_D_TSM20 | 12.4 | 10% | -0.08 | -0.14 | 0.09 | -0.05 | 6 | -0.12 | 0.01 | 0.00 | 0.17 | NO |
| NQ_ES_D_TSM20 | 12.4 | 20% | -0.16 | -0.29 | 0.16 | -0.11 | 17 | -0.25 | 0.01 | 0.00 | 0.17 | NO |
| NQ_ES_D_TSM20 | 12.4 | 30% | -0.25 | -0.44 | 0.22 | -0.17 | 29 | -0.38 | 0.01 | 0.00 | 0.17 | NO |
| NQ_ES_D_TSM20 | 12.4 | 50% | -0.42 | -0.74 | 0.30 | -0.30 | 53 | -0.63 | 0.01 | 0.00 | 0.17 | NO |

### Constant-risk
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| NQ_RTY_D_TSM20 | 10% | -6.3 | 1.2 | 3.4 | 8.6 | 0/2 | 7/6 | NO |
| NQ_RTY_D_TSM20 | 20% | -12.6 | -3.5 | 5.4 | 17.1 | -4/2 | 13/13 | NO |
| NQ_RTY_D_TSM20 | 30% | -18.9 | -8.3 | 6.6 | 14.0 | -9/2 | 18/19 | NO |
| NQ_RTY_D_TSM20 | 50% | -31.6 | -41.2 | -3.0 | -34.6 | -42/-13 | 8/17 | NO |
| NQ_ES_D_TSM20 | 10% | -11.2 | 4.1 | 6.0 | 4.9 | 3/5 | -1/3 | NO |
| NQ_ES_D_TSM20 | 20% | -22.5 | 1.7 | 10.7 | 4.2 | 7/10 | -4/5 | NO |
| NQ_ES_D_TSM20 | 30% | -33.7 | -0.8 | 13.4 | -2.6 | 10/15 | -6/8 | NO |
| NQ_ES_D_TSM20 | 50% | -56.2 | -5.9 | 16.0 | -35.5 | 17/21 | -12/14 | NO |

### Plateau, 2x slippage, alt baseline
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| NQ_RTY_D_TSM20 | 0.00 | 2 | 0.00 | -0.13 / -0.12 | -0.10 / -0.05 / 0.29 / -0.00 | 0.54 | -0.09 / 0.07 / 0.31 / 0.02 |
| NQ_ES_D_TSM20 | -0.11 | 2 | 0.00 | -0.08 / -0.07 | -0.18 / -0.31 / 0.15 / -0.12 | -0.41 | -0.15 / -0.22 / 0.16 / -0.10 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| NQ_RTY_D_TSM20 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.05) | NO |
| NQ_ES_D_TSM20 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.00) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ_RTY_D_TSM20 | clean | 0.04 | 52,287 | -233,860 | -155,066 | -128,505 | 774,966 | 0.07 | 0.07 | 55 | 1.30 | -112,648 | -99,993 | 294,772 | 4.57 | 47 | 1.46 | -81,874 | -78,736 | 280,110 |
| NQ_RTY_D_TSM20 | H1 | 0.87 | 239,298 | -136,579 | -106,667 | -96,630 | 215,856 | 1.53 | 1.11 | 57 | 2.72 | -87,326 | -86,174 | 163,674 | 4.07 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| NQ_RTY_D_TSM20 | H2 | 2.26 | 698,179 | -74,994 | -73,713 | -60,224 | 172,653 | 5.46 | 4.04 | 42 | 2.69 | -93,515 | -92,052 | 176,532 | 5.50 | 42 | 2.30 | -82,524 | -81,089 | 217,425 |
| NQ_RTY_D_TSM20 | all | 0.56 | 989,764 | -233,860 | -141,150 | -115,039 | 774,966 | 0.92 | 1.28 | 52 | 1.83 | -112,648 | -96,821 | 294,772 | 10.12 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| NQ_ES_D_TSM20 | clean | -0.83 | -548,935 | -140,576 | -93,789 | -80,884 | 644,194 | -1.10 | -0.85 | 59 | 1.21 | -98,281 | -90,707 | 355,747 | 3.28 | 48 | 1.46 | -81,874 | -78,736 | 280,110 |
| NQ_ES_D_TSM20 | H1 | -1.25 | -190,491 | -97,909 | -87,123 | -73,885 | 388,330 | -1.60 | -0.49 | 57 | 2.39 | -106,305 | -94,599 | 160,052 | 3.35 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| NQ_ES_D_TSM20 | H2 | 1.69 | 407,641 | -87,774 | -82,968 | -63,658 | 230,955 | 3.19 | 1.77 | 42 | 2.52 | -83,653 | -82,368 | 195,508 | 4.52 | 39 | 2.30 | -82,524 | -81,089 | 217,425 |
| NQ_ES_D_TSM20 | all | -0.31 | -331,785 | -140,576 | -92,292 | -79,048 | 854,111 | -0.44 | -0.39 | 55 | 1.69 | -106,305 | -90,788 | 355,747 | 7.27 | 45 | 1.86 | -82,524 | -79,220 | 280,110 |

### Margin / size
| cell | avg contracts leg A / leg B per unit of risk | k | contracts at pair-vol scale A / B | margin $ (T4 table) |
|---|---|---|---|---|
| NQ_RTY_D_TSM20 | 1.85 / 4.13 | 8.2 | 15.1 / 33.8 | 493,405 |
| NQ_ES_D_TSM20 | 3.61 / 4.37 | 12.4 | 44.8 / 54.2 | 1,411,269 |


## Verdict and reading
FOUND 0. Trend on the ratios is not an edge here: both selected daily TSM20 cells have 2013-22 Sharpe 0.30-0.31 (5 of 10 / 7 of 10 positive years) and are indistinguishable from their random-segment null in the pair window (ranks above); the NQ/ES cell loses -0.83/-1.25 on clean/H1. Both are small-sample flagged in the pair window (75 and 110 segments; NQ/RTY < 100 segments carries the flag, 2013-26 Sharpe 0.41 beside it). Correlation with the pair is low (worst-decile corr -0.05 / 0.00), which is why H2 shows positive uplift (+0.29 / +0.16), but H2 is the only span where it helps. Trend on spreads joins mean reversion (C1-F4) as tested and rejected.

## Executability (G7)
Spec: two legs in NT8 as a multi-instrument strategy (daily series for NQ and the second leg, e.g. RTY/ES/NQ continuous), signal = sign(x_t - x_{t-20}) of the cumulative return difference, trade at the next session open, size both legs to equal ATR20 dollar risk (use micro contracts MNQ/MES/M2K for granularity), margin per the table (outright margins from the T4 table, offset between index legs would be lower at the broker but is not assumed). Not recommended: gates fail.


DONE B3
