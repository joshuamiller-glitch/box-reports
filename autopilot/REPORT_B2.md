# REPORT B2

> **UPDATE 2026-10-16: compression-breakout results (X1, Y6, B2-D) are NOT CONFIRMED under path-resolved 30-min execution (REPORT_Z1.md); the daily-bar fill model resolved 52% of triggers (both-touch days) incorrectly. Lead withdrawn.**

**NO (LEAD-standalone only) - best B2 cell P10_h1_k2: standalone 2013-2026 Sharpe 0.94 (own-null rank 1.00 in 2013-22 and the pair window) but additive uplift at 20% share only 0.15/-0.27/0.28 on clean/H1/H2 (gate +0.10) and bootstrap lo -0.05; FOUND 0. B2-D 36 cells, B2-M 36 cells, runtime ~2 min each (7 workers).**



## Scope and protocol
Pre-registered in PREREG_AUTOPILOT.md (CAPACITY BACKLOG B2/B3/B5/B6) before any run. Two families: B2-D daily on the 26-market universe (data/t4), 36 cells = setup {NR7, inside day, 20-day range percentile <= 10%} x hold {1,2,3,5} days x ATR stop {1,2,3}; B2-M 30-minute bars on NQ ES RTY GC CL ZN (6 markets pooled equal-risk), 36 cells, same setup/hold/stop grid with stops {0.5,1,1.5} x daily ATR20 and holds in label days. Entry: stop order beyond the setup bar's high/low on the next bar (next 30-min bar for B2-M), OCO, side nearest the open if both are touched. Development and selection on 2013-2022 ONLY (>= 300 trades, >= 7 of 10 calendar years with positive weekly Sharpe, top 3 by 2013-22 weekly Sharpe); clean 2023-08..2025-07, H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once for the selected cells; UNTOUCHED never touched. Sleeve scaled so its 2013-22 weekly vol equals the pair's clean weekly vol (k below), so the pair-window numbers carry no fitted scale. Baseline pair B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30), computed in a clean process.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## B2-D daily: development table (2013-2022; pair-window numbers are shown only for the 3 selected cells below)
Eligible (>= 300 trades, >= 7/10 positive years): 23 of 36. Top 12 by 2013-22 weekly Sharpe:

| cell      |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:----------|-----------------:|-------------:|----------:|
| ID_h1_k3  |            13439 |         1    |        10 |
| ID_h1_k2  |            13439 |         1    |        10 |
| P10_h1_k2 |             6506 |         0.93 |         9 |
| P10_h1_k3 |             6506 |         0.88 |         9 |
| ID_h2_k3  |            13439 |         0.85 |         9 |
| ID_h2_k2  |            13439 |         0.84 |         9 |
| P10_h1_k1 |             6506 |         0.77 |         7 |
| ID_h3_k3  |            11405 |         0.77 |         9 |
| ID_h3_k2  |            11438 |         0.74 |         9 |
| NR7_h1_k2 |             7209 |         0.71 |         8 |
| NR7_h1_k3 |             7209 |         0.66 |         8 |
| ID_h3_k1  |            11702 |         0.62 |         7 |

Multiplicity: 36 cells x 5% = 1.8 expected cells passing a p95 null by chance, but the daily ID/P10 cells beat their own null by a wide margin in both 2013-22 (rank 1.00) and the pair window, so the standalone edge is real in-sample and out-of-sample (pair window = out-of-development).

### Standalone, own random-entry null (203 draws; same count per instrument per calendar year, same hold and stop, random side, open entry)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ID_h1_k3 | 1.00 | 10 | 0.25 | -0.18 | 1.91 | 0.60 | 0.84 | -0.51 | 1.00 | -1.45 | 1.00 |
| ID_h1_k2 | 1.00 | 10 | 0.22 | -0.32 | 1.88 | 0.55 | 0.83 | -0.56 | 1.00 | -1.38 | 1.00 |
| P10_h1_k2 | 0.93 | 9 | 1.03 | -1.54 | 2.53 | 1.08 | 0.94 | -0.16 | 1.00 | -0.82 | 1.00 |

### Additive framing vs the pair (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ID_h1_k3 | 1.9 | 10% | 0.02 | -0.02 | 0.11 | 0.04 | 13 | -0.05 | 0.23 | 0.15 | 0.06 | NO |
| ID_h1_k3 | 1.9 | 20% | 0.03 | -0.06 | 0.19 | 0.06 | 26 | -0.11 | 0.23 | 0.15 | 0.06 | NO |
| ID_h1_k3 | 1.9 | 30% | 0.02 | -0.12 | 0.25 | 0.07 | 40 | -0.19 | 0.23 | 0.15 | 0.06 | NO |
| ID_h1_k3 | 1.9 | 50% | -0.02 | -0.30 | 0.31 | 0.04 | 69 | -0.36 | 0.23 | 0.15 | 0.06 | NO |
| ID_h1_k2 | 1.9 | 10% | 0.02 | -0.02 | 0.11 | 0.03 | 13 | -0.05 | 0.23 | 0.15 | 0.06 | NO |
| ID_h1_k2 | 1.9 | 20% | 0.02 | -0.07 | 0.19 | 0.05 | 26 | -0.12 | 0.23 | 0.15 | 0.06 | NO |
| ID_h1_k2 | 1.9 | 30% | 0.01 | -0.14 | 0.24 | 0.05 | 40 | -0.19 | 0.23 | 0.15 | 0.06 | NO |
| ID_h1_k2 | 1.9 | 50% | -0.03 | -0.34 | 0.30 | 0.02 | 67 | -0.38 | 0.23 | 0.15 | 0.06 | NO |
| P10_h1_k2 | 3.2 | 10% | 0.08 | -0.13 | 0.16 | 0.07 | 5 | -0.02 | 0.04 | 0.02 | 0.14 | NO |
| P10_h1_k2 | 3.2 | 20% | 0.15 | -0.27 | 0.28 | 0.12 | 16 | -0.05 | 0.04 | 0.02 | 0.14 | NO |
| P10_h1_k2 | 3.2 | 30% | 0.20 | -0.44 | 0.37 | 0.15 | 27 | -0.10 | 0.04 | 0.02 | 0.14 | NO |
| P10_h1_k2 | 3.2 | 50% | 0.26 | -0.80 | 0.49 | 0.17 | 49 | -0.22 | 0.04 | 0.02 | 0.14 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| ID_h1_k3 | 10% | -6.9 | -2.9 | 5.2 | 6.4 | -4/3 | 9/12 | NO |
| ID_h1_k3 | 20% | -13.8 | -6.6 | 9.1 | 12.8 | -7/4 | 19/23 | NO |
| ID_h1_k3 | 30% | -20.7 | -10.7 | 11.4 | 14.7 | -12/3 | 28/35 | NO |
| ID_h1_k3 | 50% | -34.4 | -22.1 | 11.6 | 7.8 | -23/-1 | 47/47 | NO |
| ID_h1_k2 | 10% | -7.1 | -2.9 | 5.3 | 6.4 | -4/3 | 9/12 | NO |
| ID_h1_k2 | 20% | -14.3 | -6.5 | 9.0 | 12.7 | -7/4 | 19/23 | NO |
| ID_h1_k2 | 30% | -21.4 | -10.1 | 11.2 | 14.7 | -11/3 | 28/35 | NO |
| ID_h1_k2 | 50% | -35.7 | -17.5 | 11.2 | 14.8 | -18/-2 | 47/48 | NO |
| P10_h1_k2 | 10% | -4.3 | 4.3 | 5.9 | 6.5 | 4/5 | 1/9 | NO |
| P10_h1_k2 | 20% | -8.5 | 2.7 | 10.7 | 13.0 | 2/10 | 2/18 | NO |
| P10_h1_k2 | 30% | -12.8 | 1.2 | 15.4 | 19.5 | 0/14 | 2/23 | NO |
| P10_h1_k2 | 50% | -21.3 | -2.0 | 19.3 | 27.4 | -3/16 | 4/23 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| ID_h1_k3 | 0.06 | 2 | 1.00 | 0.05 / 0.05 | -0.15 / -0.31 / 0.05 / -0.12 | -0.36 | 0.04 / -0.03 / 0.19 / 0.07 |
| ID_h1_k2 | 0.05 | 2 | 0.50 | 0.04 / 0.05 | -0.15 / -0.32 / 0.05 / -0.13 | -0.41 | 0.03 / -0.04 / 0.18 / 0.06 |
| P10_h1_k2 | 0.12 | 6 | 0.67 | 0.03 / 0.10 | 0.00 / -0.47 / 0.15 / -0.03 | 0.29 | 0.15 / -0.21 / 0.29 / 0.13 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| ID_h1_k3 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | PASS (1.00) | fail | PASS (0.15) | NO |
| ID_h1_k2 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.50) | fail | PASS (0.15) | NO |
| P10_h1_k2 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (0.67) | fail | PASS (0.02) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ID_h1_k3 | clean | 0.25 | 214,070 | -148,128 | -124,192 | -105,101 | 609,243 | 0.36 | 0.35 | 50 | 1.48 | -115,588 | -98,526 | 313,383 | 4.45 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| ID_h1_k3 | H1 | -0.18 | -34,658 | -147,337 | -122,579 | -103,310 | 309,641 | -0.23 | -0.11 | 54 | 2.71 | -79,501 | -73,735 | 171,682 | 3.40 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| ID_h1_k3 | H2 | 1.91 | 657,345 | -74,945 | -74,218 | -65,228 | 267,158 | 5.37 | 2.46 | 49 | 2.51 | -82,710 | -81,932 | 228,931 | 4.19 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| ID_h1_k3 | all | 0.60 | 836,757 | -148,128 | -121,062 | -99,827 | 609,243 | 0.96 | 1.37 | 49 | 1.92 | -115,588 | -92,856 | 313,383 | 9.37 | 41 | 1.86 | -82,524 | -79,220 | 280,110 |
| ID_h1_k2 | clean | 0.22 | 184,321 | -149,897 | -121,786 | -103,303 | 647,183 | 0.31 | 0.28 | 50 | 1.47 | -115,445 | -98,672 | 313,404 | 4.42 | 45 | 1.46 | -81,874 | -78,736 | 280,110 |
| ID_h1_k2 | H1 | -0.32 | -64,914 | -146,714 | -129,010 | -107,506 | 340,909 | -0.42 | -0.19 | 54 | 2.69 | -79,496 | -73,752 | 169,801 | 3.38 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| ID_h1_k2 | H2 | 1.88 | 648,810 | -74,628 | -73,905 | -66,392 | 271,786 | 5.23 | 2.39 | 49 | 2.50 | -82,709 | -81,924 | 228,883 | 4.18 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| ID_h1_k2 | all | 0.55 | 768,217 | -149,897 | -119,789 | -99,218 | 647,183 | 0.88 | 1.19 | 49 | 1.91 | -115,445 | -93,033 | 313,404 | 9.30 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |
| P10_h1_k2 | clean | 1.03 | 876,498 | -145,040 | -109,146 | -89,392 | 357,592 | 1.72 | 2.45 | 47 | 1.66 | -104,888 | -90,697 | 309,435 | 5.15 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| P10_h1_k2 | H1 | -1.54 | -288,953 | -112,182 | -92,094 | -83,930 | 339,748 | -1.96 | -0.85 | 61 | 2.39 | -99,889 | -79,554 | 158,459 | 3.20 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| P10_h1_k2 | H2 | 2.53 | 952,863 | -76,003 | -71,345 | -63,652 | 235,570 | 7.75 | 4.04 | 41 | 2.63 | -77,796 | -76,534 | 240,610 | 4.35 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| P10_h1_k2 | all | 1.08 | 1,540,409 | -145,040 | -102,163 | -85,108 | 357,592 | 1.97 | 4.31 | 48 | 2.01 | -104,888 | -90,476 | 309,435 | 10.17 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |

### Margin / size
| cell | instrument | median ATR20 (pair window) | contracts per trade at pair-vol scale (k x $7,000 per ATR) | margin per trade $ (T4 table; unverified) |
|---|---|---|---|---|
| ID_h1_k3 | ES | 59.49 | 4.5 | 54,474 |
| ID_h1_k3 | NQ | 301.3 | 2.2 | 38,088 |
| ID_h1_k3 | CL | 1.876 | 7.2 | 50,381 |
| ID_h1_k3 | GC | 39.62 | 3.4 | 126,767 |
| ID_h1_k3 | ZN | 0.4805 | 28.1 | 61,825 |
| ID_h1_k3 | ZC | 8.356 | 32.3 | 64,633 |
| ID_h1_k2 | ES | 59.49 | 4.5 | 54,244 |
| ID_h1_k2 | NQ | 301.3 | 2.2 | 37,927 |
| ID_h1_k2 | CL | 1.876 | 7.2 | 50,168 |
| ID_h1_k2 | GC | 39.62 | 3.4 | 126,232 |
| ID_h1_k2 | ZN | 0.4805 | 28.0 | 61,563 |
| ID_h1_k2 | ZC | 8.356 | 32.2 | 64,360 |
| P10_h1_k2 | ES | 59.49 | 7.5 | 89,673 |
| P10_h1_k2 | NQ | 301.3 | 3.7 | 62,699 |
| P10_h1_k2 | CL | 1.876 | 11.8 | 82,936 |
| P10_h1_k2 | GC | 39.62 | 5.6 | 208,680 |
| P10_h1_k2 | ZN | 0.4805 | 46.3 | 101,773 |
| P10_h1_k2 | ZC | 8.356 | 53.2 | 106,396 |

(Examples of 6 of 26 markets; the sleeve trades all 26, about 4.4 trades per trading day pooled for the selected cells.)

## B2-M 30-minute: development table (2013-2022)
Eligible: 1 of 36. Top 12:

| cell        |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:------------|-----------------:|-------------:|----------:|
| P10_h5_k1.5 |             1031 |         0.25 |         7 |
| ID_h5_k0.5  |             5262 |         0.18 |         6 |
| ID_h5_k1.5  |             3186 |         0.16 |         5 |
| ID_h5_k1    |             3667 |         0.15 |         6 |
| P10_h3_k1.5 |             1317 |         0.12 |         5 |
| P10_h5_k0.5 |             1294 |         0.1  |         5 |
| ID_h3_k1    |             5347 |         0.06 |         6 |
| P10_h5_k1   |             1103 |         0    |         6 |
| ID_h3_k0.5  |             7056 |         0    |         5 |
| ID_h2_k0.5  |             9082 |        -0.16 |         4 |
| ID_h1_k1    |            13396 |        -0.2  |         5 |
| NR7_h5_k1.5 |             3135 |        -0.25 |         3 |

Only one cell passes the development screen; it has 2013-22 Sharpe 0.25, own-null rank 0.98 in 2013-22 and 0.49 in the pair window.
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P10_h5_k1.5 | 0.25 | 7 | -0.13 | 0.06 | -0.46 | -0.18 | 0.05 | 0.66 | 0.49 | 0.18 | 0.98 |

| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P10_h5_k1.5 | 5.1 | 10% | -0.02 | -0.18 | -0.08 | -0.04 | 5 | -0.13 | 0.17 | -0.18 | 0.07 | NO |
| P10_h5_k1.5 | 5.1 | 20% | -0.05 | -0.35 | -0.17 | -0.10 | 16 | -0.27 | 0.17 | -0.18 | 0.07 | NO |
| P10_h5_k1.5 | 5.1 | 30% | -0.09 | -0.51 | -0.29 | -0.17 | 27 | -0.42 | 0.17 | -0.18 | 0.07 | NO |
| P10_h5_k1.5 | 5.1 | 50% | -0.19 | -0.80 | -0.54 | -0.33 | 49 | -0.73 | 0.17 | -0.18 | 0.07 | NO |

| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| P10_h5_k1.5 | 10% | -11.0 | 4.8 | 4.3 | 7.5 | 4/3 | -0/3 | NO |
| P10_h5_k1.5 | 20% | -22.0 | 3.1 | 6.9 | 14.9 | 2/5 | -2/7 | NO |
| P10_h5_k1.5 | 30% | -33.0 | 1.3 | 8.2 | 17.6 | 1/7 | -4/10 | NO |
| P10_h5_k1.5 | 50% | -55.0 | -7.0 | 3.8 | 7.1 | -8/5 | -7/8 | NO |

| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| P10_h5_k1.5 | -0.10 | 8 | 0.00 | -0.19 / -0.12 | -0.08 / -0.40 / -0.21 / -0.13 | -0.36 | -0.04 / -0.16 / -0.19 / -0.09 |

| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| P10_h5_k1.5 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (-0.18) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P10_h5_k1.5 | clean | -0.13 | -114,573 | -167,864 | -126,091 | -104,282 | 799,941 | -0.19 | -0.14 | 51 | 1.37 | -104,560 | -96,506 | 301,340 | 4.30 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| P10_h5_k1.5 | H1 | 0.06 | 15,211 | -125,261 | -109,768 | -103,559 | 327,899 | 0.09 | 0.05 | 50 | 2.32 | -104,275 | -93,152 | 175,496 | 3.41 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| P10_h5_k1.5 | H2 | -0.46 | -166,671 | -182,541 | -160,031 | -126,631 | 511,004 | -0.65 | -0.33 | 56 | 2.01 | -84,087 | -82,315 | 235,530 | 3.02 | 44 | 2.30 | -82,524 | -81,089 | 217,425 |
| P10_h5_k1.5 | all | -0.18 | -266,033 | -182,541 | -139,562 | -114,699 | 934,291 | -0.26 | -0.28 | 52 | 1.69 | -104,560 | -95,206 | 301,340 | 8.65 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |


## Verdict and reading
- FOUND 0. B2-M (30-minute) is dead: negative or near-zero gross edge after 1 tick/side; the selected cell fails its own null in the pair window (rank 0.49).
- B2-D is a genuine but small standalone edge: the inside-day and range-percentile breakouts with a 1-day hold earn about +0.04-0.08 ATR per trade gross over a random-entry baseline across most markets, Sharpe about +1.0 on 2013-22 (10 of 10 years positive) and about +0.6-1.1 in the pair window, beating the own null at rank 1.00. But the pair's Sharpe is 1.5-2.8, so adding a sleeve of Sharpe ~0.6-1.0 at 10-50% of pair risk moves the pair Sharpe by only 0.15/-0.27/0.28 (clean/H1/H2, best cell, 20%), H1 negative, bootstrap 90% lower bounds below zero, and it does not survive 2x slippage as an uplift. Logged as a weak standalone LEAD (diversifier, not a pair-improver); gates failing: G3 (all shares), bootstrap, 2x slippage, plateau for 2 of 3 cells.
- The cost sensitivity is large in low-ATR products (ZT, ZF, 6x: 1 tick is 5-10% of an ATR), so a live version would drop those; not examined (would be a post-hoc selection).

## Executability (G7)
Spec (B2-D): daily bars, 26 markets at NinjaTrader Brokerage via Rithmic (micros for MES/MNQ/M2K/MGC/MCL available for small shares); after each close compute inside-day (h<=prior h and l>=prior l) and place OCO buy-stop at the day's high / sell-stop at the day's low for the next session with an ATR(20) stop at 2-3 ATR and a market-on-close exit that same session. NT8: one strategy per instrument with OnBarUpdate at session close (daily bars aligned to the CME 17:00 ET close; note the study used UTC-day bars), no new DualStrat work. Sizing $7,000 per ATR20 per trade times the scale k (tables above), roughly 5 simultaneous trades per day across the universe, margin per the T4 table (unverified, metals 9% assumed). Not recommended: gates fail.


DONE B2
