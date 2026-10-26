# REPORT B6

**NO - B6: 128 cells (96 reversal COM/RATES/BOTH, 32 continuation); only 2 cells pass the 2013-22 screen (RV z>=2 1-day fade on COM+RATES, hold 1; CT m>=1.5 ATR hold 5); both beat their own null on 2013-22 (ranks 1.00/0.99) and then fail it in the pair window (0.86/0.84); additive uplift at 20% clean/H1/H2 -0.14/0.33/0.27 and -0.04/0.28/0.04; FOUND 0.**



## Scope and protocol
Pre-registered (PREREG_AUTOPILOT.md CAPACITY BACKLOG B6). Signal at the close of day t, entry at the next open, exit at the close of day t+hold, no stop, one position per instrument at a time, $7,000 per ATR20 (ATR through t). B6-RV: fade the n-day return z = (c_t - c_(t-n))/(ATR20 x sqrt n) when |z| >= zth; n in {1,2,3,5}, zth in {1,2}, hold in {1,2,3,5}, group in {COM (13 commodities), RATES (ZN ZB ZF ZT), BOTH} = 96 cells. B6-CT: follow the 1-day move when |ret|/ATR20 >= m in {1.5,2,2.5,3}, hold in {1,2,3,5}, universe {ALL26, COM+RATES} = 32 cells. Development/selection on 2013-2022 only (>= 300 trades, >= 7 of 10 positive years, top 3 per family; fewer if fewer qualify); clean/H1/H2 read once for the selected cells. Scale from 2013-22 weekly vol. Own null: 203 random-entry draws (same count per instrument per year, same hold, random side). Baseline B.Cfg(wk_floor=8, wk_loss_pb=None).

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022)
Cells with positive 2013-22 Sharpe: RV 24 of 96, CT 4 of 32; mean 2013-22 Sharpe over all RV cells -0.31, CT -0.33 (cost-dominated: most fades lose after 1 tick/side). Top 12:

| cell            |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:----------------|-----------------:|-------------:|----------:|
| RV_5_2_h5_RATES |               38 |         0.54 |         7 |
| RV_5_2_h1_BOTH  |              238 |         0.45 |         7 |
| CT_1.5_h5_BOTH  |             1335 |         0.44 |         7 |
| RV_1_2_h1_BOTH  |              431 |         0.42 |         7 |
| CT_1.5_h5_ALL26 |             2134 |         0.38 |         6 |
| RV_1_2_h1_RATES |              142 |         0.37 |         5 |
| RV_5_2_h1_RATES |               65 |         0.36 |         5 |
| RV_5_2_h1_COM   |              173 |         0.32 |         6 |
| RV_3_2_h1_BOTH  |              260 |         0.3  |         5 |
| RV_5_2_h2_RATES |               47 |         0.3  |         6 |
| RV_1_2_h2_RATES |              138 |         0.28 |         5 |
| RV_5_2_h3_RATES |               45 |         0.28 |         7 |

Multiplicity: 128 cells x 5% = 6.4 expected chance passes of a p95 null; only 2 cells survive the year-consistency screen at all. The selected cells have small 2013-22 Sharpes (0.42-0.44) with a small-sample flag in the pair window only for RATES-only cells (not selected); the selected cells have 156 and 471 trades in the pair window.

## Selected cells
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| RV_1_2_h1_BOTH | 0.42 | 7 | -0.61 | 1.01 | 0.85 | 0.14 | 0.30 | 0.50 | 0.86 | -0.02 | 1.00 |
| CT_1.5_h5_BOTH | 0.44 | 7 | -0.02 | 0.08 | 1.02 | 0.30 | 0.35 | 0.68 | 0.84 | 0.22 | 0.99 |

### Additive
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RV_1_2_h1_BOTH | 7.8 | 10% | -0.06 | 0.19 | 0.18 | 0.02 | 7 | -0.08 | 0.87 | -0.19 | -0.08 | NO |
| RV_1_2_h1_BOTH | 7.8 | 20% | -0.14 | 0.33 | 0.27 | 0.01 | 21 | -0.20 | 0.87 | -0.19 | -0.08 | NO |
| RV_1_2_h1_BOTH | 7.8 | 30% | -0.23 | 0.41 | 0.28 | -0.03 | 34 | -0.34 | 0.87 | -0.19 | -0.08 | NO |
| RV_1_2_h1_BOTH | 7.8 | 50% | -0.41 | 0.43 | 0.14 | -0.16 | 82 | -0.65 | 0.87 | -0.19 | -0.08 | NO |
| CT_1.5_h5_BOTH | 2.4 | 10% | -0.00 | 0.17 | 0.06 | 0.03 | 10 | -0.09 | 0.56 | 0.27 | -0.02 | NO |
| CT_1.5_h5_BOTH | 2.4 | 20% | -0.04 | 0.28 | 0.04 | 0.01 | 23 | -0.23 | 0.56 | 0.27 | -0.02 | NO |
| CT_1.5_h5_BOTH | 2.4 | 30% | -0.10 | 0.31 | -0.03 | -0.04 | 36 | -0.40 | 0.56 | 0.27 | -0.02 | NO |
| CT_1.5_h5_BOTH | 2.4 | 50% | -0.25 | 0.09 | -0.19 | -0.22 | 147 | -0.78 | 0.56 | 0.27 | -0.02 | NO |

### Constant-risk
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| RV_1_2_h1_BOTH | 10% | -9.0 | 2.3 | 8.9 | 8.7 | 2/8 | 10/12 | NO |
| RV_1_2_h1_BOTH | 20% | -18.0 | -1.8 | 16.4 | 17.4 | -3/14 | 18/24 | NO |
| RV_1_2_h1_BOTH | 30% | -27.0 | -5.9 | 16.8 | 7.5 | -7/11 | 26/30 | NO |
| RV_1_2_h1_BOTH | 50% | -45.0 | -122.4 | -9.7 | -52.5 | -124/-11 | 2/22 | NO |
| CT_1.5_h5_BOTH | 10% | -7.3 | 0.1 | 6.9 | 7.1 | 4/9 | 19/27 | NO |
| CT_1.5_h5_BOTH | 20% | -14.7 | -3.3 | 10.6 | 14.1 | 0/13 | 39/46 | NO |
| CT_1.5_h5_BOTH | 30% | -22.0 | -38.2 | 5.4 | 20.8 | -39/4 | 53/55 | NO |
| CT_1.5_h5_BOTH | 50% | -36.6 | -196.4 | -13.8 | 5.7 | -199/-28 | 16/25 | NO |

### Plateau, 2x slippage, alt baseline
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| RV_1_2_h1_BOTH | 0.01 | 2 | 0.00 | -0.31 / -0.17 | -0.17 / 0.28 / 0.25 / -0.02 | 0.02 | -0.13 / 0.23 / 0.29 / 0.02 |
| CT_1.5_h5_BOTH | 0.01 | 4 | 0.25 | -0.13 / 0.00 | -0.07 / 0.24 / 0.01 / -0.02 | 0.20 | -0.03 / 0.20 / 0.07 / 0.04 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| RV_1_2_h1_BOTH | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.19) | NO |
| CT_1.5_h5_BOTH | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.25) | fail | PASS (0.27) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RV_1_2_h1_BOTH | clean | -0.61 | -539,567 | -433,456 | -156,625 | -112,226 | 968,388 | -0.74 | -0.56 | 19 | 1.23 | -110,539 | -86,233 | 291,135 | 4.01 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| RV_1_2_h1_BOTH | H1 | 1.01 | 268,151 | -141,729 | -122,845 | -101,189 | 277,279 | 1.94 | 0.97 | 21 | 3.24 | -80,660 | -73,033 | 151,713 | 4.44 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| RV_1_2_h1_BOTH | H2 | 0.85 | 538,116 | -339,933 | -212,184 | -106,092 | 339,933 | 1.82 | 1.58 | 5 | 2.54 | -82,524 | -79,970 | 212,831 | 4.34 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| RV_1_2_h1_BOTH | all | 0.14 | 266,700 | -433,456 | -175,548 | -120,135 | 1,041,657 | 0.23 | 0.26 | 16 | 1.83 | -110,539 | -84,222 | 291,135 | 9.50 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| CT_1.5_h5_BOTH | clean | -0.02 | -29,696 | -570,994 | -213,485 | -150,301 | 655,959 | -0.03 | -0.05 | 46 | 1.36 | -111,916 | -89,914 | 304,750 | 4.33 | 46 | 1.46 | -81,874 | -78,736 | 280,110 |
| CT_1.5_h5_BOTH | H1 | 0.08 | 27,119 | -139,652 | -133,235 | -129,181 | 395,567 | 0.13 | 0.07 | 54 | 3.13 | -56,261 | -50,679 | 161,845 | 3.72 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| CT_1.5_h5_BOTH | H2 | 1.02 | 719,931 | -123,213 | -115,400 | -86,018 | 551,805 | 4.20 | 1.30 | 51 | 2.24 | -111,930 | -101,238 | 219,346 | 4.46 | 49 | 2.26 | -82,524 | -81,089 | 217,425 |
| CT_1.5_h5_BOTH | all | 0.30 | 717,353 | -570,994 | -184,466 | -140,626 | 655,959 | 0.52 | 1.09 | 48 | 1.81 | -111,930 | -92,395 | 304,750 | 9.52 | 45 | 1.86 | -82,524 | -79,220 | 280,110 |

### Margin / size
| cell | instrument | median ATR20 (pair window) | contracts per trade at pair-vol scale (k x $7,000 per ATR) | margin per trade $ (T4 table; unverified) |
|---|---|---|---|---|
| RV_1_2_h1_BOTH | GC | 39.62 | 13.7 | 510,621 |
| RV_1_2_h1_BOTH | CL | 1.876 | 29.0 | 202,937 |
| RV_1_2_h1_BOTH | NG | 0.129 | 42.1 | 168,576 |
| RV_1_2_h1_BOTH | ZN | 0.4805 | 113.2 | 249,030 |
| RV_1_2_h1_BOTH | ZB | 0.9719 | 56.0 | 251,824 |
| RV_1_2_h1_BOTH | ZC | 8.356 | 130.2 | 260,342 |
| RV_1_2_h1_BOTH | ZS | 18.68 | 58.2 | 174,737 |
| RV_1_2_h1_BOTH | HE | 1.831 | 74.3 | 148,548 |
| CT_1.5_h5_BOTH | GC | 39.62 | 4.3 | 158,513 |
| CT_1.5_h5_BOTH | CL | 1.876 | 9.0 | 62,998 |
| CT_1.5_h5_BOTH | NG | 0.129 | 13.1 | 52,332 |
| CT_1.5_h5_BOTH | ZN | 0.4805 | 35.1 | 77,307 |
| CT_1.5_h5_BOTH | ZB | 0.9719 | 17.4 | 78,174 |
| CT_1.5_h5_BOTH | ZC | 8.356 | 40.4 | 80,819 |
| CT_1.5_h5_BOTH | ZS | 18.68 | 18.1 | 54,244 |
| CT_1.5_h5_BOTH | HE | 1.831 | 23.1 | 46,114 |

(Selected cells trade COM+RATES (17 markets) with k scaling above; positions are open ~0.4 trades per day.)

## Verdict and reading
FOUND 0. Short-term reversal in commodities and rates does not exist after costs in this sample (mean 2013-22 Sharpe -0.3 over the 96 RV cells); the one surviving fade (|1-day move| >= 2 ATR, hold 1, COM+RATES) earns +0.42 on 2013-22 and +0.14 in the pair window with clean -0.61. Continuation after a >= 1.5 ATR day with a 5-day hold earns +0.44 on 2013-22 and +0.30 in the pair window; neither beats the pair-window null at p95, neither lifts the pair by +0.10 on any span consistently (H1 +0.33/+0.28 but clean negative), bootstrap lower bounds < 0.

## Executability (G7)
Rule: after each close compute the day's move in ATR20 units; if |move| >= 1.5 ATR enter at the next open in the direction of the move (continuation) and exit 5 sessions later at the close (or fade 2-ATR moves for one day); NT8 daily strategy per instrument; micro contracts for small sizes. Margin per table. Not recommended: gates fail.


DONE B6
