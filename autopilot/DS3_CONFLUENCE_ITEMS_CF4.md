# DS3_CONFLUENCE_ITEMS_CF4: STEP 3 each condition alone, Block 2 (and 4) of the indicator library

**Verdict (data ends 2026-10-30) line: Block 2 conditions built so far = 39317 scored columns across 21 sub-blocks; every one is a MAP entry only (no PASS claim; matched-count and shuffled-outcome controls belong to W-CF3).**

## IRL / ERL Step A (Addendum 5): measure-only, headline = 5-min bars, 2 pts, W=3, minor pivot 3

**Verdict line: external better than internal for FADES under the fixed rule (matched difference of the 60-min fade return > 0, CI above 0 on full history, positive in L6M, and beating the random-level control): NO under every one of the 13 range definitions. Ranges with ext-minus-int matched difference > 0 on full history: e240_10; ranges where internal is significantly better: none. Measure-only; no PASS claim.**

Units: fav/net/mae in ATR(5m,14) of the sweep; net = fade return at the horizon close (positive = reversal followed through); cont = share of sweeps where a 1m close re-closed beyond the swept level (continuation) within the horizon; stop = adverse reached poke extreme +2 pts within the horizon; mdiff = matched (poke depth tercile x ET hour x ATR tercile) ext-minus-int difference in net60 with 95% week-block bootstrap CI; ctl = random level at the same distance (2 seeds). Windows recent first.

**L1M**

| range | n ext | n int | net60 ext | net60 int | matched diff [95% CI] | cont60 ext/int | MAE60 ext/int | stop60 ext/int | win60 ext/int | ctl net60 ext/int |
|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | 12 | 377 | -1.57 | 0.04 |  [, ] | 0.83/0.76 | 2.85/1.96 | 0.83/0.67 | 0.25/0.51 | -1.21/0.16 |
| b_ps | 19 | 364 | -0.72 | 0.31 |  [, ] | 0.74/0.75 | 3.08/1.85 | 0.79/0.66 | 0.42/0.54 | 0.71/0.33 |
| b_cs60 | 227 | 405 | -0.39 | 0.32 | -0.69 [-1.00, 0.94] | 0.78/0.75 | 1.95/1.82 | 0.69/0.66 | 0.42/0.53 | /0.16 |
| c_on | 9 | 129 | -0.13 | 0.29 |  [, ] | 0.89/0.70 | 2.52/1.58 | 0.89/0.61 | 0.44/0.57 | 0.14/0.14 |
| d_wk | 2 | 377 | -1.92 | 0.05 |  [, ] | 1.00/0.76 | 3.39/2.01 | 1.00/0.68 | 0.00/0.49 | 0.36/0.01 |
| e15_10 | 15 | 350 | 0.10 | 0.45 |  [, ] | 0.60/0.75 | 2.14/1.78 | 0.53/0.67 | 0.60/0.56 | -0.32/0.44 |
| e15_20 | 10 | 421 | -0.56 | 0.27 |  [, ] | 0.80/0.74 | 1.97/1.92 | 0.70/0.66 | 0.40/0.53 | -0.74/0.27 |
| e60_10 | 6 | 458 | -0.62 | 0.13 |  [, ] | 0.83/0.73 | 2.38/1.98 | 0.67/0.65 | 0.33/0.51 | -1.11/0.12 |
| e60_20 | 4 | 436 | -1.65 | 0.06 |  [, ] | 1.00/0.75 | 2.90/2.01 | 1.00/0.67 | 0.00/0.50 | -1.68/0.08 |
| e240_10 | 1 | 292 | -1.93 | 0.21 |  [, ] | 1.00/0.74 | 4.38/1.98 | 1.00/0.65 | 0.00/0.52 | 0.35/0.09 |
| e240_20 | 0 | 350 |  | 0.16 |  [, ] | /0.75 | /2.00 | /0.67 | /0.53 | /0.25 |
| f_or30 | 24 | 128 | 0.19 | 0.73 |  [, ] | 0.71/0.73 | 1.79/1.50 | 0.71/0.63 | 0.54/0.60 | -0.11/0.35 |
| f_or60 | 17 | 172 | 0.52 | 0.57 |  [, ] | 0.76/0.75 | 1.81/1.66 | 0.65/0.66 | 0.59/0.55 | 0.23/0.60 |

**L3M**

| range | n ext | n int | net60 ext | net60 int | matched diff [95% CI] | cont60 ext/int | MAE60 ext/int | stop60 ext/int | win60 ext/int | ctl net60 ext/int |
|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | 28 | 2031 | -0.98 | -0.08 |  [, ] | 0.82/0.76 | 2.61/2.03 | 0.71/0.66 | 0.25/0.51 | 0.01/-0.04 |
| b_ps | 84 | 2016 | -0.22 | 0.01 | 0.11 [-1.17, 1.01] | 0.77/0.77 | 2.64/2.00 | 0.71/0.66 | 0.48/0.51 | 0.34/0.04 |
| b_cs60 | 1032 | 1860 | -0.16 | 0.03 | -0.16 [-0.51, 0.18] | 0.77/0.76 | 1.99/1.95 | 0.66/0.66 | 0.49/0.51 | /0.04 |
| c_on | 34 | 653 | 0.56 | 0.06 | 0.53 [-0.69, 1.66] | 0.68/0.74 | 2.45/1.92 | 0.71/0.64 | 0.62/0.55 | 0.33/0.01 |
| d_wk | 5 | 2116 | -0.34 | -0.06 |  [, ] | 1.00/0.77 | 2.24/2.07 | 1.00/0.66 | 0.40/0.52 | 1.14/-0.00 |
| e15_10 | 77 | 1963 | -0.22 | 0.01 | 0.07 [-1.01, 0.97] | 0.74/0.77 | 2.45/1.96 | 0.65/0.66 | 0.52/0.52 | -0.12/0.07 |
| e15_20 | 42 | 2110 | -0.34 | -0.04 | 0.89 [-1.54, 1.27] | 0.76/0.77 | 2.22/2.03 | 0.71/0.66 | 0.48/0.51 | -0.22/0.01 |
| e60_10 | 19 | 1967 | -0.69 | -0.03 |  [, ] | 0.84/0.76 | 2.46/2.06 | 0.74/0.65 | 0.26/0.52 | -0.06/-0.00 |
| e60_20 | 10 | 1752 | -1.19 | -0.05 |  [, ] | 0.80/0.76 | 2.72/2.06 | 0.80/0.65 | 0.30/0.51 | -0.86/-0.00 |
| e240_10 | 7 | 2102 | -0.35 | -0.03 |  [, ] | 0.71/0.76 | 2.45/2.07 | 0.71/0.66 | 0.57/0.51 | -0.92/-0.02 |
| e240_20 | 2 | 2552 | -2.92 | -0.05 |  [, ] | 1.00/0.77 | 3.68/2.05 | 1.00/0.66 | 0.00/0.52 | -1.02/0.00 |
| f_or30 | 119 | 649 | 0.12 | 0.03 | -0.01 [-0.67, 0.57] | 0.83/0.77 | 1.84/1.83 | 0.66/0.67 | 0.53/0.54 | -0.13/-0.04 |
| f_or60 | 107 | 769 | 0.18 | 0.02 | -0.10 [-0.49, 0.69] | 0.81/0.78 | 1.87/1.86 | 0.61/0.68 | 0.52/0.52 | 0.37/0.08 |

**L6M**

| range | n ext | n int | net60 ext | net60 int | matched diff [95% CI] | cont60 ext/int | MAE60 ext/int | stop60 ext/int | win60 ext/int | ctl net60 ext/int |
|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | 70 | 4700 | -0.62 | -0.02 | 0.35 [-1.70, 0.70] | 0.80/0.78 | 2.31/2.04 | 0.71/0.69 | 0.37/0.50 | -0.20/-0.00 |
| b_ps | 206 | 4698 | -0.30 | 0.06 | -0.32 [-1.01, 0.09] | 0.79/0.77 | 2.69/2.03 | 0.70/0.68 | 0.45/0.51 | -0.02/0.04 |
| b_cs60 | 2490 | 4263 | -0.04 | 0.03 | -0.03 [-0.28, 0.19] | 0.78/0.77 | 1.93/1.92 | 0.68/0.69 | 0.49/0.50 | /0.04 |
| c_on | 83 | 1467 | -0.17 | 0.06 | -0.18 [-1.30, 0.76] | 0.72/0.76 | 2.79/2.13 | 0.66/0.68 | 0.55/0.52 | -0.15/0.01 |
| d_wk | 11 | 4922 | -0.22 | -0.01 |  [, ] | 0.91/0.78 | 1.86/2.04 | 0.82/0.68 | 0.45/0.50 | 0.73/0.03 |
| e15_10 | 203 | 4427 | -0.23 | 0.08 | -0.33 [-0.93, 0.01] | 0.77/0.77 | 2.34/1.98 | 0.68/0.68 | 0.46/0.52 | -0.06/0.09 |
| e15_20 | 107 | 4804 | -0.50 | 0.02 | -0.54 [-1.40, 0.16] | 0.81/0.78 | 2.36/2.06 | 0.73/0.69 | 0.44/0.50 | -0.28/0.01 |
| e60_10 | 51 | 4541 | -0.48 | 0.02 | -0.20 [-1.53, 0.80] | 0.84/0.77 | 2.22/2.05 | 0.73/0.68 | 0.39/0.50 | 0.20/0.06 |
| e60_20 | 28 | 4475 | -0.68 | 0.01 |  [, ] | 0.82/0.77 | 2.42/2.05 | 0.82/0.68 | 0.39/0.49 | -0.29/0.05 |
| e240_10 | 14 | 4375 | -0.60 | -0.01 |  [, ] | 0.71/0.77 | 2.41/2.07 | 0.71/0.68 | 0.43/0.50 | -0.63/0.01 |
| e240_20 | 3 | 5273 | -2.28 | 0.01 |  [, ] | 1.00/0.78 | 2.91/2.02 | 1.00/0.69 | 0.00/0.50 | -1.01/0.04 |
| f_or30 | 301 | 1431 | 0.27 | 0.06 | 0.24 [-0.25, 0.67] | 0.80/0.77 | 1.86/1.91 | 0.68/0.68 | 0.52/0.52 | 0.14/-0.00 |
| f_or60 | 272 | 1715 | 0.17 | 0.04 | 0.02 [-0.34, 0.44] | 0.82/0.78 | 1.87/1.89 | 0.65/0.68 | 0.51/0.51 | 0.21/0.07 |

**full**

| range | n ext | n int | net60 ext | net60 int | matched diff [95% CI] | cont60 ext/int | MAE60 ext/int | stop60 ext/int | win60 ext/int | ctl net60 ext/int |
|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | 450 | 31662 | -0.22 | -0.00 | -0.21 [-0.51, 0.14] | 0.74/0.78 | 2.17/2.10 | 0.59/0.64 | 0.50/0.51 | -0.19/-0.02 |
| b_ps | 1451 | 28208 | -0.16 | -0.00 | -0.15 [-0.33, 0.07] | 0.76/0.78 | 2.58/2.12 | 0.63/0.64 | 0.48/0.51 | -0.12/-0.02 |
| b_cs60 | 15727 | 26695 | -0.04 | 0.02 | -0.06 [-0.12, 0.00] | 0.78/0.78 | 1.93/2.00 | 0.65/0.65 | 0.50/0.51 | /-0.00 |
| c_on | 678 | 10154 | -0.28 | -0.12 | -0.10 [-0.39, 0.23] | 0.76/0.77 | 2.76/2.20 | 0.65/0.68 | 0.49/0.50 | -0.17/-0.14 |
| d_wk | 97 | 32360 | -0.05 | -0.04 | -0.52 [-0.97, 0.59] | 0.75/0.78 | 2.05/2.11 | 0.61/0.65 | 0.49/0.50 | 0.04/-0.02 |
| e15_10 | 1384 | 27332 | -0.08 | -0.03 | -0.07 [-0.19, 0.09] | 0.75/0.78 | 2.34/2.12 | 0.62/0.64 | 0.50/0.51 | -0.02/-0.04 |
| e15_20 | 698 | 31924 | -0.16 | -0.01 | -0.16 [-0.40, 0.11] | 0.74/0.78 | 2.26/2.16 | 0.60/0.65 | 0.52/0.50 | 0.05/-0.03 |
| e60_10 | 376 | 31662 | -0.12 | -0.01 | -0.13 [-0.45, 0.24] | 0.74/0.78 | 2.24/2.15 | 0.61/0.65 | 0.52/0.51 | -0.01/-0.02 |
| e60_20 | 209 | 28491 | -0.40 | -0.01 | -0.30 [-0.89, 0.11] | 0.78/0.78 | 2.37/2.13 | 0.67/0.65 | 0.48/0.51 | -0.04/-0.02 |
| e240_10 | 101 | 28559 | -0.24 | -0.03 | 0.22 [-1.05, 0.96] | 0.77/0.78 | 2.17/2.13 | 0.65/0.66 | 0.45/0.50 | -0.08/-0.01 |
| e240_20 | 38 | 28709 | -0.19 | -0.03 |  [-2.76, 2.39] | 0.79/0.78 | 2.21/2.10 | 0.74/0.66 | 0.34/0.50 | -0.62/-0.01 |
| f_or30 | 2040 | 8987 | -0.05 | 0.03 | -0.06 [-0.20, 0.07] | 0.78/0.78 | 2.06/1.97 | 0.65/0.64 | 0.50/0.52 | -0.07/0.03 |
| f_or60 | 1883 | 10753 | -0.02 | 0.01 | -0.04 [-0.20, 0.09] | 0.78/0.78 | 1.94/1.95 | 0.63/0.65 | 0.50/0.51 | -0.05/0.03 |

**Per session (matched diff net60, ext minus int)**

| range | session | window | n ext | n int | net60 ext | net60 int | matched diff [CI] |
|---|---|---|---|---|---|---|---|
| a_pd | asia | L6M | 41 | 1926 | -0.51 | -0.08 | 0.70 [-1.93, 1.32] |
| a_pd | asia | full | 164 | 9371 | -0.06 | -0.03 | -0.05 [-0.41, 0.45] |
| a_pd | london | L6M | 17 | 1694 | -0.86 | 0.04 |  [, ] |
| a_pd | london | full | 125 | 12513 | -0.08 | 0.07 | 0.23 [-1.23, 0.62] |
| a_pd | ny | L6M | 12 | 1080 | -0.67 | 0.00 |  [, ] |
| a_pd | ny | full | 161 | 9778 | -0.51 | -0.08 | -0.45 [-0.96, 0.07] |
| b_ps | asia | L6M | 41 | 1926 | -0.51 | -0.08 | 0.70 [-1.93, 1.32] |
| b_ps | asia | full | 163 | 9372 | -0.08 | -0.03 | -0.05 [-0.41, 0.43] |
| b_ps | london | L6M | 63 | 1675 | -0.53 | 0.19 | -0.51 [-1.27, 0.17] |
| b_ps | london | full | 524 | 10758 | -0.10 | 0.07 | -0.14 [-0.39, 0.11] |
| b_ps | ny | L6M | 102 | 1097 | -0.08 | 0.12 | -0.32 [-1.23, 0.35] |
| b_ps | ny | full | 764 | 8078 | -0.21 | -0.08 | -0.13 [-0.45, 0.19] |
| b_cs60 | asia | L6M | 960 | 1474 | -0.06 | -0.08 | 0.04 [-0.27, 0.32] |
| b_cs60 | asia | full | 4296 | 7039 | -0.08 | -0.01 | -0.09 [-0.18, -0.00] |
| b_cs60 | london | L6M | 940 | 1618 | -0.02 | 0.12 | -0.07 [-0.41, 0.23] |
| b_cs60 | london | full | 6342 | 10759 | 0.03 | 0.07 | -0.02 [-0.15, 0.09] |
| b_cs60 | ny | L6M | 590 | 1171 | -0.03 | 0.05 | -0.07 [-0.44, 0.36] |
| b_cs60 | ny | full | 5089 | 8897 | -0.08 | -0.01 | -0.07 [-0.21, 0.03] |
| c_on | asia | L6M | 0 | 0 |  |  |  [, ] |
| c_on | asia | full | 0 | 0 |  |  |  [, ] |
| c_on | london | L6M | 0 | 0 |  |  |  [, ] |
| c_on | london | full | 0 | 0 |  |  |  [, ] |
| c_on | ny | L6M | 83 | 1467 | -0.17 | 0.06 | -0.18 [-1.21, 0.76] |
| c_on | ny | full | 678 | 10154 | -0.28 | -0.12 | -0.10 [-0.38, 0.22] |
| d_wk | asia | L6M | 7 | 1777 | -0.00 | -0.11 |  [, ] |
| d_wk | asia | full | 32 | 8528 | 0.05 | -0.06 | -0.28 [-1.12, 1.51] |
| d_wk | london | L6M | 1 | 1785 | -2.43 | 0.07 |  [, ] |
| d_wk | london | full | 19 | 12352 | 0.09 | 0.01 |  [, ] |
| d_wk | ny | L6M | 3 | 1360 | -0.01 | 0.01 |  [, ] |
| d_wk | ny | full | 46 | 11480 | -0.18 | -0.08 | -0.73 [-1.55, 0.74] |
| e15_10 | asia | L6M | 65 | 1762 | -0.19 | -0.03 | 0.46 [-1.09, 0.71] |
| e15_10 | asia | full | 294 | 8704 | -0.20 | -0.02 | -0.24 [-0.47, -0.01] |
| e15_10 | london | L6M | 76 | 1547 | -0.44 | 0.19 | -0.87 [-1.61, 0.23] |
| e15_10 | london | full | 567 | 10747 | -0.02 | 0.02 | -0.07 [-0.33, 0.23] |
| e15_10 | ny | L6M | 62 | 1118 | -0.02 | 0.11 | -0.28 [-1.19, 0.55] |
| e15_10 | ny | full | 523 | 7881 | -0.09 | -0.10 | 0.01 [-0.24, 0.28] |
| e15_20 | asia | L6M | 26 | 1725 | -0.33 | -0.04 |  [, ] |
| e15_20 | asia | full | 106 | 8345 | 0.15 | -0.02 | 0.07 [-0.47, 0.86] |
| e15_20 | london | L6M | 36 | 1846 | -1.01 | 0.12 | -0.91 [-2.77, 0.33] |
| e15_20 | london | full | 262 | 13654 | -0.21 | 0.07 | -0.10 [-0.63, 0.17] |
| e15_20 | ny | L6M | 45 | 1233 | -0.19 | -0.02 | -0.38 [-0.95, 0.70] |
| e15_20 | ny | full | 330 | 9925 | -0.21 | -0.11 | -0.08 [-0.39, 0.33] |
| e60_10 | asia | L6M | 11 | 1437 | -0.38 | 0.01 |  [, ] |
| e60_10 | asia | full | 43 | 7107 | 0.20 | -0.02 | 0.76 [-1.37, 1.86] |
| e60_10 | london | L6M | 20 | 1776 | -0.75 | 0.07 |  [, ] |
| e60_10 | london | full | 134 | 13078 | -0.30 | 0.06 | -0.53 [-1.30, 0.36] |
| e60_10 | ny | L6M | 20 | 1328 | -0.26 | -0.04 |  [, ] |
| e60_10 | ny | full | 199 | 11477 | -0.07 | -0.07 | 0.07 [-0.39, 0.48] |
| e60_20 | asia | L6M | 7 | 1489 | -0.43 | -0.10 |  [, ] |
| e60_20 | asia | full | 26 | 6983 | -0.16 | -0.05 |  [, ] |
| e60_20 | london | L6M | 6 | 1574 | -1.53 | 0.13 |  [, ] |
| e60_20 | london | full | 42 | 10670 | -0.65 | 0.05 | -0.51 [-2.93, 0.81] |
| e60_20 | ny | L6M | 15 | 1412 | -0.45 | 0.01 |  [, ] |
| e60_20 | ny | full | 141 | 10838 | -0.38 | -0.05 | -0.32 [-0.99, 0.21] |
| e240_10 | asia | L6M | 4 | 1519 | -1.35 | -0.16 |  [, ] |
| e240_10 | asia | full | 16 | 7109 | -0.54 | -0.07 |  [, ] |
| e240_10 | london | L6M | 2 | 1609 | -2.06 | 0.06 |  [, ] |
| e240_10 | london | full | 18 | 11083 | -0.06 | 0.02 |  [, ] |
| e240_10 | ny | L6M | 8 | 1247 | 0.14 | 0.07 |  [, ] |
| e240_10 | ny | full | 67 | 10367 | -0.22 | -0.05 | 0.33 [-0.76, 1.02] |
| e240_20 | asia | L6M | 2 | 1857 | -2.57 | -0.08 |  [, ] |
| e240_20 | asia | full | 3 | 7579 | -1.76 | -0.04 |  [, ] |
| e240_20 | london | L6M | 1 | 1883 | -1.69 | 0.09 |  [, ] |
| e240_20 | london | full | 10 | 10859 | -1.15 | 0.01 |  [, ] |
| e240_20 | ny | L6M | 0 | 1533 |  | 0.03 |  [, ] |
| e240_20 | ny | full | 25 | 10271 | 0.38 | -0.06 |  [, ] |
| f_or30 | asia | L6M | 87 | 378 | 0.44 | -0.01 | 0.33 [-1.03, 0.99] |
| f_or30 | asia | full | 456 | 2203 | 0.07 | 0.00 | 0.07 [-0.14, 0.37] |
| f_or30 | london | L6M | 105 | 484 | 0.29 | 0.09 | 0.31 [-0.28, 1.21] |
| f_or30 | london | full | 740 | 2935 | 0.08 | 0.00 | 0.13 [-0.13, 0.33] |
| f_or30 | ny | L6M | 109 | 569 | 0.12 | 0.07 | 0.13 [-0.43, 0.65] |
| f_or30 | ny | full | 844 | 3849 | -0.22 | 0.06 | -0.30 [-0.50, -0.15] |
| f_or60 | asia | L6M | 86 | 460 | 0.38 | -0.02 | -0.07 [-0.83, 0.75] |
| f_or60 | asia | full | 440 | 2533 | -0.00 | 0.01 | -0.05 [-0.30, 0.19] |
| f_or60 | london | L6M | 106 | 599 | 0.06 | 0.14 | -0.06 [-0.60, 0.69] |
| f_or60 | london | full | 767 | 3554 | 0.06 | 0.02 | 0.00 [-0.27, 0.28] |
| f_or60 | ny | L6M | 80 | 656 | 0.09 | -0.01 | 0.21 [-0.20, 0.55] |
| f_or60 | ny | full | 676 | 4666 | -0.12 | -0.00 | -0.07 [-0.27, 0.08] |

**Sensitivity: matched diff (ext - int) of net60 full history, one parameter changed at a time from the headline**

| range | head | p2 | p5 | tf1 | tf15 | tf3 | thr_atr | thr_tick | w1 | w2 | w5 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | -0.21 | -0.23 | -0.23 | -0.07 | -0.11 | -0.16 | -0.26 | -0.23 | -0.09 | -0.17 | -0.15 |
| b_ps | -0.15 | -0.16 | -0.13 | -0.16 | -0.09 | -0.07 | -0.10 | -0.08 | -0.21 | -0.21 | -0.11 |
| b_cs60 | -0.06 | -0.06 | -0.04 | -0.01 | -0.05 | -0.03 | -0.05 | -0.04 | -0.07 | -0.06 | -0.05 |
| c_on | -0.10 | -0.09 | -0.08 | 0.04 | 0.07 | 0.06 | -0.08 | -0.11 | -0.21 | -0.19 | -0.00 |
| d_wk | -0.52 | -0.58 | -0.61 | -0.33 | -0.02 | 0.46 | -0.56 | -0.19 | 0.12 | 0.10 | -0.32 |
| e15_10 | -0.07 | -0.07 | -0.07 | -0.10 | -0.05 | 0.01 | -0.04 | -0.06 | -0.11 | -0.04 | -0.06 |
| e15_20 | -0.16 | -0.16 | -0.15 | -0.17 | -0.01 | -0.03 | -0.21 | -0.17 | -0.13 | -0.20 | -0.12 |
| e60_10 | -0.13 | -0.13 | -0.11 | -0.13 | 0.14 | -0.11 | -0.08 | 0.00 | -0.05 | -0.11 | -0.12 |
| e60_20 | -0.30 | -0.29 | -0.29 | -0.35 | -0.19 | -0.50 | -0.26 | -0.35 | 0.15 | -0.26 | -0.32 |
| e240_10 | 0.22 | 0.21 | 0.22 | -1.47 | 0.39 | 0.26 | 0.06 | 0.12 | 0.58 | 0.68 | 0.11 |
| e240_20 |  |  |  | 0.93 | -0.56 | 1.00 | -0.45 | 0.03 |  | 0.79 | -0.48 |
| f_or30 | -0.06 | -0.06 | -0.00 | -0.01 | -0.07 | -0.01 | -0.09 | -0.08 | -0.07 | -0.04 | -0.03 |
| f_or60 | -0.04 | -0.04 | 0.01 | 0.05 | -0.06 | 0.00 | -0.03 | 0.01 | -0.02 | -0.04 | -0.05 |

positive cells 28 of 139; CI above 0 in 0 cells; CI below 0 in 3 cells.


## IRL / ERL Step C: where D7 gets hurt (JN05W2 losing exits, 43 months)

**Verdict line: of 1895 full stops (Stop / StopJoin / StopJoinFallback), 4.2% were internal-level-only sweeps followed by a recovery of at least the risk within 30 min (6.6% within 60 min), and 5.8% were external-level sweeps followed by recovery within 60 min: SMALL, so the proposed stop-placement changes are not pursued from this table; recovery after a stop-out is higher when the swept level was internal-only (rec60 0.53) than external (0.34), in the direction of the claim, but descriptive only.**
A losing exit counts as "taken by a sweep" if a headline sweep event (fade direction = trade side) confirms within 15 min after the exit with the exit price inside the poke zone (level to poke extreme +-1 pt). ext = the swept level is external to at least one of the 13 ranges; int_only = tagged internal only. Recovery = price came back from the exit price toward/through the entry by at least the original risk (>= max(risk,1pt)) within 30/60 min (1m highs/lows). Descriptive only; the stop-placement tests (beyond the nearest external level within 1.25x the stop distance, lots reduced; no entry when the stop sits just inside an unswept internal level) need the exact engine hook (W-CF3) and are NOT run here.

| group | n losers | share swept | ext | int only | recovered 30m | recovered 60m | rec60 if swept | rec60 if int-only | rec60 if ext | sum loss $ |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL losers | 11135 | 0.263 | 0.106 | 0.157 | 0.288 | 0.405 | 0.455 | 0.534 | 0.338 | -16032286 |
| book A7 | 553 | 0.316 | 0.192 | 0.125 | 0.127 | 0.217 | 0.297 | 0.391 | 0.236 | -587025 |
| book H7 | 545 | 0.312 | 0.167 | 0.145 | 0.207 | 0.308 | 0.353 | 0.430 | 0.286 | -878226 |
| book K7 | 3981 | 0.255 | 0.092 | 0.163 | 0.289 | 0.406 | 0.445 | 0.509 | 0.334 | -3804342 |
| book M7 | 2323 | 0.224 | 0.078 | 0.146 | 0.317 | 0.447 | 0.486 | 0.550 | 0.365 | -2238420 |
| book O7 | 283 | 0.194 | 0.035 | 0.159 | 0.534 | 0.618 | 0.800 | 0.844 | 0.600 | -195288 |
| book P7 | 2806 | 0.274 | 0.100 | 0.174 | 0.307 | 0.430 | 0.495 | 0.571 | 0.365 | -6526100 |
| book U7 | 644 | 0.346 | 0.214 | 0.132 | 0.186 | 0.297 | 0.408 | 0.494 | 0.355 | -1802886 |
| exit BookLock | 104 | 0.173 | 0.019 | 0.154 | 0.510 | 0.577 | 0.500 | 0.500 | 0.500 | -100118 |
| exit EarlyCut | 2637 | 0.303 | 0.113 | 0.190 | 0.223 | 0.345 | 0.405 | 0.467 | 0.301 | -2852769 |
| exit StackCut | 291 | 0.402 | 0.285 | 0.117 | 0.199 | 0.302 | 0.444 | 0.412 | 0.458 | -266336 |
| exit StateCut | 6070 | 0.218 | 0.069 | 0.149 | 0.351 | 0.477 | 0.537 | 0.612 | 0.378 | -8937875 |
| exit Stop | 859 | 0.334 | 0.184 | 0.150 | 0.175 | 0.262 | 0.348 | 0.450 | 0.266 | -1248414 |
| exit StopJoin | 635 | 0.361 | 0.184 | 0.176 | 0.194 | 0.302 | 0.384 | 0.402 | 0.368 | -1476328 |
| exit StopJoinFallback | 401 | 0.382 | 0.239 | 0.142 | 0.097 | 0.202 | 0.314 | 0.404 | 0.260 | -1094865 |
| exit TimeBlock | 121 | 0.000 | 0.000 | 0.000 | 0.455 | 0.479 | nan | nan | nan | -47263 |

## IRL / ERL Step D: SCREEN of the proposed books (own 1m simulation, NOT the exact engine; no tuning; fixed small grid)

**Verdict line: Book 1 (fade external sweeps) averages -0.041 R/trade across range definitions and targets vs -0.053 R on its internal-sweep control; Book 2 (internal continuation) -0.069 R vs -0.176 R on external-sweep control. Screening only; positive cells: Book 1 ext 14 of 52, Book 1 control 0 of 52.**
Book 1 = fade the sweep of the range high/low at the close back inside, stop = poke extreme +2 pts, target 1R/1.5R/2R/range midpoint, time stop min(120 min, session end), cost 0.5 pt per trade. Control = the SAME book on internal sweeps. Book 2 = internal-sweep continuation: after an internal level is swept (poke direction), enter at the first retest of the level within 30 min, stop 1 ATR back inside, target the external boundary beyond (must be >1.5 ATR away); control = same on external sweeps. Table: expectancy in R per trade (net of cost), trades; full history and L6M. Per-session / per-side cells are in /mnt/l2/l2vast/_confl/irl/stepD.parquet. An exact-engine run through the CF hook is still to do for anything that looks interesting; screening results here are NOT leads.

**B1_ext_reversal, target 1.5R**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | ext | 450 | 0.032 | 0.45 | 70 | -0.114 |
| a_pd | int_control | 31662 | -0.049 | 0.41 | 4700 | 0.005 |
| b_ps | ext | 1451 | -0.049 | 0.40 | 206 | -0.103 |
| b_ps | int_control | 28208 | -0.051 | 0.40 | 4698 | -0.008 |
| b_cs60 | ext | 15732 | -0.056 | 0.40 | 2493 | -0.028 |
| b_cs60 | int_control | 26695 | -0.052 | 0.41 | 4263 | -0.011 |
| c_on | ext | 678 | -0.074 | 0.39 | 83 | -0.031 |
| c_on | int_control | 10154 | -0.052 | 0.40 | 1467 | -0.002 |
| d_wk | ext | 97 | 0.024 | 0.44 |  |  |
| d_wk | int_control | 32360 | -0.063 | 0.40 | 4922 | -0.022 |
| e15_10 | ext | 1384 | -0.037 | 0.42 | 203 | -0.062 |
| e15_10 | int_control | 27332 | -0.059 | 0.40 | 4427 | 0.011 |
| e15_20 | ext | 698 | 0.039 | 0.45 | 107 | -0.150 |
| e15_20 | int_control | 31924 | -0.054 | 0.40 | 4804 | -0.005 |
| e60_10 | ext | 376 | 0.041 | 0.44 | 51 | -0.179 |
| e60_10 | int_control | 31662 | -0.055 | 0.40 | 4541 | -0.001 |
| e60_20 | ext | 209 | -0.086 | 0.39 | 28 | -0.171 |
| e60_20 | int_control | 28491 | -0.062 | 0.40 | 4475 | -0.018 |
| e240_10 | ext | 101 | -0.072 | 0.41 |  |  |
| e240_10 | int_control | 28559 | -0.057 | 0.40 | 4375 | -0.022 |
| e240_20 | ext | 38 | -0.103 | 0.39 |  |  |
| e240_20 | int_control | 28709 | -0.057 | 0.40 | 5273 | -0.039 |
| f_or30 | ext | 2040 | -0.058 | 0.40 | 301 | 0.012 |
| f_or30 | int_control | 8987 | -0.038 | 0.41 | 1431 | 0.023 |
| f_or60 | ext | 1883 | -0.041 | 0.41 | 272 | 0.050 |
| f_or60 | int_control | 10753 | -0.045 | 0.41 | 1715 | 0.018 |

**B1_ext_reversal, target mid**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | ext | 445 | -0.122 | 0.33 | 69 | -0.450 |
| a_pd | int_control | 15573 | -0.093 | 0.33 | 2379 | -0.149 |
| b_ps | ext | 1407 | -0.043 | 0.38 | 198 | -0.201 |
| b_ps | int_control | 14408 | -0.060 | 0.40 | 2488 | -0.071 |
| b_cs60 | ext | 15452 | -0.076 | 0.33 | 2464 | -0.039 |
| b_cs60 | int_control | 15644 | -0.060 | 0.41 | 2463 | -0.041 |
| c_on | ext | 674 | -0.055 | 0.38 | 82 | -0.141 |
| c_on | int_control | 5501 | -0.026 | 0.43 | 809 | 0.067 |
| d_wk | ext | 97 | 0.113 | 0.33 |  |  |
| d_wk | int_control | 15926 | -0.045 | 0.28 | 2418 | 0.003 |
| e15_10 | ext | 1341 | -0.054 | 0.37 | 201 | -0.148 |
| e15_10 | int_control | 14263 | -0.076 | 0.39 | 2421 | -0.046 |
| e15_20 | ext | 688 | 0.027 | 0.37 | 107 | -0.431 |
| e15_20 | int_control | 16691 | -0.076 | 0.35 | 2595 | -0.127 |
| e60_10 | ext | 375 | 0.064 | 0.32 | 51 | -0.525 |
| e60_10 | int_control | 16475 | -0.066 | 0.32 | 2347 | -0.167 |
| e60_20 | ext | 209 | -0.156 | 0.28 | 28 | -0.431 |
| e60_20 | int_control | 14454 | -0.047 | 0.30 | 2277 | -0.024 |
| e240_10 | ext | 101 | -0.069 | 0.28 |  |  |
| e240_10 | int_control | 14366 | -0.048 | 0.29 | 2214 | -0.069 |
| e240_20 | ext | 38 | -0.047 | 0.24 |  |  |
| e240_20 | int_control | 14350 | -0.053 | 0.28 | 2683 | -0.013 |
| f_or30 | ext | 1911 | -0.056 | 0.47 | 289 | 0.176 |
| f_or30 | int_control | 3554 | -0.063 | 0.53 | 559 | 0.047 |
| f_or60 | ext | 1802 | -0.033 | 0.43 | 265 | 0.089 |
| f_or60 | int_control | 4630 | -0.050 | 0.49 | 757 | 0.049 |

**B2_int_continuation, target ext_level**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | int | 21550 | -0.099 | 0.25 | 3084 | -0.068 |
| b_ps | int | 16616 | -0.096 | 0.27 | 2859 | -0.103 |
| b_cs60 | int | 12122 | -0.068 | 0.29 | 1956 | -0.029 |
| b_cs60 | ext_control | 307 | -0.176 | 0.32 | 40 | -0.089 |
| c_on | int | 5287 | -0.058 | 0.28 | 789 | -0.085 |
| d_wk | int | 23720 | -0.040 | 0.25 | 3563 | -0.097 |
| e15_10 | int | 16369 | -0.065 | 0.27 | 2644 | -0.095 |
| e15_20 | int | 21185 | -0.082 | 0.26 | 3127 | -0.080 |
| e60_10 | int | 22212 | -0.082 | 0.25 | 3099 | -0.081 |
| e60_20 | int | 20525 | -0.065 | 0.25 | 3197 | -0.138 |
| e240_10 | int | 21068 | -0.042 | 0.25 | 3192 | -0.087 |
| e240_20 | int | 21264 | -0.051 | 0.25 | 3891 | -0.110 |
| f_or30 | int | 3225 | -0.073 | 0.31 | 556 | -0.076 |
| f_or60 | int | 4627 | -0.073 | 0.30 | 779 | -0.055 |


## B2-A momentum / oscillators

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 3105; |t|>2: 0 (chance expectation ~141 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_osc.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_1m_side | 175995 | 0.92 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_sig | 134641 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_rise | 149983 | 0.78 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_fresh5 | 91610 | 0.48 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_ewith_z1 | 17646 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eleave_z1 | 198 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eenter_z1 | 9182 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_ewith_z2 | 35175 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eleave_z2 | 571 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eenter_z2 | 17173 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_nodiv | 165370 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_divwith | 8535 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_side | 166514 | 0.87 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_sig | 136815 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_rise | 152052 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_fresh5 | 109815 | 0.57 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_ewith_z1 | 23582 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eleave_z1 | 354 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eenter_z1 | 17179 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_ewith_z2 | 42120 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eleave_z2 | 1160 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eenter_z2 | 27348 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_nodiv | 163009 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_divwith | 8651 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtS_1m_side | 176124 | 0.92 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_1m_side | 175995 | 0.92 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_sig | 134641 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_rise | 149983 | 0.78 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_fresh5 | 91610 | 0.48 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_ewith_z1 | 17646 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eleave_z1 | 198 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eenter_z1 | 9182 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_ewith_z2 | 35175 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eleave_z2 | 571 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eenter_z2 | 17173 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_nodiv | 165370 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_divwith | 8535 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_side | 166514 | 0.87 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_sig | 136815 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_rise | 152052 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_fresh5 | 109815 | 0.57 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_ewith_z1 | 23582 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eleave_z1 | 354 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eenter_z1 | 17179 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_ewith_z2 | 42120 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eleave_z2 | 1160 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eenter_z2 | 27348 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_nodiv | 163009 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_divwith | 8651 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtS_1m_side | 176124 | 0.92 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 174 of 18242 session-condition cells pass (chance-level expectation under independence ~226 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_crsi_15m_nodiv | 10490 | 0.131 | 0.076 | 3.1 | 4/4 | 0.301 |
| close | c4_elderS_bull_60m_divwith | 1946 | -0.164 | -0.073 | -2.9 | 0/4 | -0.294 |
| close | c4_sqzmS_on_3m_rise | 131 | -0.198 | -0.070 | -2.9 | 0/4 | -0.125 |
| close | c4_smiF_60m_eleave | 1900 | -0.135 | -0.068 | -2.7 | 0/4 | -0.015 |
| close | c4_stc_15m_fresh5 | 3871 | 0.101 | 0.065 | 2.7 | 4/4 | 0.141 |
| close | c4_smiS_5m_eenter | 1506 | 0.092 | 0.062 | 2.6 | 4/4 | 0.067 |
| nyam | c4_smieS_1d_eleave | 649 | -0.252 | -0.104 | -4.2 | 0/4 | -0.025 |
| nyam | c4_elderF_bull_15m_nodiv | 20580 | 0.167 | 0.094 | 3.8 | 4/4 | 0.158 |
| nyam | c4_smiS_1m_eagainst | 175 | -0.270 | -0.090 | -3.8 | 0/4 | -0.466 |
| nyam | c4_elder_bull_15m_nodiv | 20900 | 0.144 | 0.079 | 3.2 | 4/4 | 0.195 |
| nyam | c4_smiF_3m_eleave | 1961 | -0.106 | -0.077 | -3.5 | 0/4 | -0.124 |
| nyam | c4_smi_1m_eleave | 2183 | -0.091 | -0.073 | -3.6 | 0/4 | -0.104 |
| nypm | c4_coppS_60m_side | 14192 | 0.155 | 0.103 | 4.3 | 4/4 | 0.290 |
| nypm | c4_kstS_mtf_all | 3628 | 0.238 | 0.100 | 4.0 | 4/4 | 0.195 |
| nypm | c4_wt_60m_ewith_z1 | 3371 | 0.241 | 0.099 | 4.0 | 4/4 | 0.382 |
| nypm | c4_tsi_60m_side | 14971 | 0.146 | 0.097 | 4.1 | 4/4 | 0.234 |
| nypm | c4_elderF_bear_1d_rise | 12562 | 0.149 | 0.097 | 4.1 | 4/4 | 0.164 |
| nypm | c4_wtS_60m_ewith_z2 | 3910 | 0.202 | 0.096 | 3.8 | 4/4 | 0.299 |
| pre | c4_crsi_3m_eagainst_z2 | 213 | 0.311 | 0.096 | 4.2 | 4/4 | 0.117 |
| pre | c4_elderS_bear_60m_fresh5 | 2412 | 0.230 | 0.090 | 3.7 | 4/4 | 0.268 |
| pre | c4_sqzmF_bright_1m_against | 862 | 0.119 | 0.074 | 3.1 | 4/4 | 0.040 |
| pre | c4_rviS_5m_rise | 5887 | -0.111 | -0.073 | -3.1 | 0/4 | -0.103 |
| pre | c4_tsiS_1m_side | 8581 | -0.157 | -0.071 | -2.9 | 0/4 | -0.355 |
| pre | c4_tsi_1m_side | 8742 | -0.153 | -0.069 | -2.8 | 0/4 | -0.279 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (1041 of 92709 cell-conditions pass; chance at t>2.5 alone ~574)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| A7 | nypm | c4_coppS_60m_side | 2646 | 0.099 | -0.212 | 0.311 | 5.5 | 4/4 | 0.494 |
| K7 | asia | c4_qqeF_5m_ewith | 1905 | 0.136 | 0.017 | 0.119 | 5.4 | 4/4 | 0.180 |
| A7 | nypm | c4_wtS_60m_side | 2761 | 0.083 | -0.203 | 0.286 | 5.0 | 4/4 | 0.489 |
| A7 | nypm | c4_tsi_60m_side | 2879 | 0.078 | -0.221 | 0.298 | 5.0 | 4/4 | 0.493 |
| K7 | asia | c4_qqe_5m_ewith | 542 | 0.218 | 0.025 | 0.192 | 4.8 | 4/4 | 0.313 |
| K7 | asia | c4_tsiF_5m_ewith | 4536 | 0.087 | 0.009 | 0.078 | 4.8 | 4/4 | 0.102 |
| K7 | asia | c4_smieF_5m_ewith | 5783 | 0.073 | 0.008 | 0.065 | 4.8 | 3/4 | 0.085 |
| K7 | asia | c4_rsima21_5m_eenter | 96 | 0.342 | 0.030 | 0.311 | 4.7 | 4/4 | 0.345 |
| A7 | nypm | c4_kstS_mtf_all | 942 | 0.250 | -0.090 | 0.340 | 4.7 | 4/4 | 0.206 |
| K7 | asia | c4_smie_5m_ewith | 2508 | 0.118 | 0.015 | 0.103 | 4.6 | 4/4 | 0.103 |
| P7 | asia | c4_rsima14_15m_ewith | 1769 | 0.195 | 0.023 | 0.172 | 4.6 | 4/4 | 0.066 |
| K7 | asia | c4_mc_comp2_15m_side | 9735 | 0.064 | -0.023 | 0.087 | 4.6 | 4/4 | 0.189 |
| K7 | asia | c4_tsiS_3m_ewith | 1205 | 0.168 | 0.021 | 0.147 | 4.6 | 4/4 | 0.184 |
| K7 | asia | c4_wtF_60m_ewith_z1 | 906 | 0.206 | 0.021 | 0.185 | 4.6 | 4/4 | 0.164 |
| K7 | asia | c4_rsima14_5m_ewith | 646 | 0.196 | 0.025 | 0.171 | 4.6 | 4/4 | 0.220 |
| K7 | asia | c4_tsiS_5m_ewith | 1152 | 0.178 | 0.020 | 0.157 | 4.5 | 4/4 | 0.184 |
| K7 | asia | c4_elderS_bull_15m_side | 8840 | 0.071 | -0.021 | 0.092 | 4.5 | 4/4 | 0.181 |
| P7 | asia | c4_qqe_15m_ewith | 1447 | 0.219 | 0.024 | 0.195 | 4.5 | 4/4 | 0.096 |
| K7 | asia | c4_rsima14_15m_side | 9374 | 0.068 | -0.025 | 0.093 | 4.5 | 4/4 | 0.183 |
| K7 | asia | c4_smieS_5m_ewith | 1124 | 0.168 | 0.021 | 0.147 | 4.5 | 4/4 | 0.115 |
| K7 | asia | c4_qqeS_5m_side | 9564 | 0.063 | -0.020 | 0.083 | 4.5 | 4/4 | 0.127 |
| A7 | nypm | c4_qqeS_60m_side | 2878 | 0.073 | -0.209 | 0.282 | 4.4 | 4/4 | 0.492 |
| K7 | asia | c4_tsiS_5m_side | 8842 | 0.069 | -0.018 | 0.087 | 4.4 | 4/4 | 0.151 |
| A7 | nypm | c4_wt_60m_side | 2913 | 0.066 | -0.199 | 0.265 | 4.4 | 4/4 | 0.554 |
| K7 | asia | c4_qqeF_15m_side | 9542 | 0.062 | -0.018 | 0.081 | 4.4 | 4/4 | 0.148 |
| M7 | nypm | c4_elderF_bear_1d_rise | 3316 | 0.100 | -0.076 | 0.176 | 4.4 | 4/4 | 0.068 |
| K7 | asia | c4_qqeS_3m_side | 11390 | 0.053 | -0.029 | 0.082 | 4.4 | 4/4 | 0.147 |
| K7 | asia | c4_wtS_15m_ewith_z1 | 607 | 0.221 | 0.024 | 0.197 | 4.4 | 4/4 | 0.157 |
| A7 | nypm | c4_smieS_60m_side | 2929 | 0.065 | -0.200 | 0.265 | 4.3 | 4/4 | 0.530 |
| K7 | asia | c4_ker_abs_5m_hi_z1 | 1338 | 0.134 | 0.023 | 0.111 | 4.3 | 4/4 | 0.187 |

## B2-B trend followers

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 3313; |t|>2: 0 (chance expectation ~150 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_trend.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_utbot_1m_fresh5 | 88726 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_fresh1 | 30307 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_side | 156434 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_rise | 139650 | 0.73 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_fresh5 | 89070 | 0.47 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_fresh1 | 30610 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_side | 156959 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_rise | 138048 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_fresh5 | 41652 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_fresh1 | 14576 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_side | 160830 | 0.84 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_rise | 144495 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_fresh5 | 40993 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_fresh1 | 13748 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_side | 173669 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_against | 17851 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_hold3 | 151837 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_fresh5 | 67202 | 0.35 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_fresh1 | 22439 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_side | 162344 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_against | 29176 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_hold3 | 127644 | 0.67 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_fresh5 | 27755 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_fresh1 | 8298 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_side | 175145 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_utbot_1m_fresh5 | 88726 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_fresh1 | 30307 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_side | 156434 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_rise | 139650 | 0.73 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_fresh5 | 89070 | 0.47 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_fresh1 | 30610 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_side | 156959 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_rise | 138048 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_fresh5 | 41652 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_fresh1 | 14576 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_side | 160830 | 0.84 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_rise | 144495 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_fresh5 | 40993 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_fresh1 | 13748 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_side | 173669 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_against | 17851 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_hold3 | 151837 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_fresh5 | 67202 | 0.35 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_fresh1 | 22439 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_side | 162344 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_against | 29176 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_hold3 | 127644 | 0.67 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_fresh5 | 27755 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_fresh1 | 8298 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_side | 175145 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 197 of 19446 session-condition cells pass (chance-level expectation under independence ~241 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_rfiltF_60m_fresh5 | 3775 | -0.156 | -0.092 | -3.7 | 0/4 | -0.021 |
| close | c4_rfiltF_dir_60m_fresh5 | 3775 | -0.156 | -0.092 | -3.7 | 0/4 | -0.021 |
| close | c4_chand_60m_fresh5 | 3449 | -0.138 | -0.076 | -3.1 | 0/4 | -0.083 |
| close | c4_chand_60m_fresh1 | 885 | -0.198 | -0.069 | -2.9 | 0/4 | -0.240 |
| close | c4_stP_mtf_all | 2613 | 0.138 | 0.068 | 2.7 | 4/4 | 0.001 |
| close | c4_rfiltF_15m_side | 11662 | 0.119 | 0.068 | 2.7 | 4/4 | 0.384 |
| nyam | c4_lrcS_15m_eleave | 1118 | -0.187 | -0.081 | -3.3 | 0/4 | -0.097 |
| nyam | c4_alli_spread_1m_side | 20600 | 0.096 | 0.077 | 3.9 | 4/4 | 0.150 |
| nyam | c4_turt20_60m_fresh1 | 2179 | -0.142 | -0.074 | -3.0 | 0/4 | -0.094 |
| nyam | c4_alma_x_1d_fresh1 | 734 | -0.250 | -0.069 | -3.1 | 0/4 | -0.188 |
| nyam | c4_turt20_60m_fresh5 | 3857 | -0.123 | -0.069 | -2.8 | 0/4 | -0.017 |
| nyam | c4_halft_mtf_all | 3645 | 0.113 | 0.067 | 2.7 | 4/4 | 0.084 |
| nypm | c4_halft_60m_hold3 | 13520 | 0.142 | 0.090 | 3.8 | 4/4 | 0.142 |
| nypm | c4_turt55_mtf_all | 1909 | 0.263 | 0.089 | 3.8 | 4/4 | 0.025 |
| nypm | c4_stP_60m_against | 10118 | -0.137 | -0.086 | -3.6 | 0/4 | -0.169 |
| nypm | c4_stP_60m_side | 14798 | 0.137 | 0.086 | 3.6 | 4/4 | 0.169 |
| nypm | c4_ichiF_futcloud_60m_against | 9748 | -0.131 | -0.086 | -3.6 | 0/4 | -0.296 |
| nypm | c4_turt20_60m_hold3 | 10080 | 0.138 | 0.084 | 3.5 | 4/4 | 0.277 |
| pre | c4_sslhyb_5m_side | 7449 | -0.150 | -0.078 | -3.1 | 0/4 | -0.233 |
| pre | c4_ssl_5m_against | 1160 | 0.134 | 0.074 | 3.0 | 4/4 | 0.332 |
| pre | c4_ssl_5m_side | 8036 | -0.134 | -0.074 | -3.0 | 0/4 | -0.332 |
| pre | c4_lrcS_1m_side | 8240 | -0.202 | -0.074 | -3.1 | 0/4 | -0.284 |
| pre | c4_t3S_px_1d_rise | 4631 | 0.182 | 0.074 | 3.0 | 4/4 | 0.218 |
| pre | c4_sslS_3m_side | 8539 | -0.156 | -0.071 | -2.9 | 0/4 | -0.302 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (1324 of 97619 cell-conditions pass; chance at t>2.5 alone ~605)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_rfiltF_dir_mtf_ge4 | 9527 | 0.074 | -0.037 | 0.111 | 5.8 | 4/4 | 0.174 |
| K7 | asia | c4_rfiltS_15m_side | 8942 | 0.072 | -0.025 | 0.097 | 4.9 | 4/4 | 0.126 |
| K7 | asia | c4_turt55_5m_side | 5004 | 0.094 | 0.002 | 0.092 | 4.6 | 4/4 | 0.140 |
| K7 | asia | c4_fractal_alli_15m_hold3 | 6265 | 0.087 | -0.006 | 0.093 | 4.6 | 4/4 | 0.195 |
| K7 | asia | c4_turt55_5m_hold3 | 4843 | 0.093 | 0.004 | 0.089 | 4.4 | 4/4 | 0.143 |
| A7 | nypm | c4_lrc_slope_15m_side | 2725 | 0.074 | -0.177 | 0.251 | 4.4 | 4/4 | 0.461 |
| K7 | asia | c4_fractal_alli_15m_side | 7602 | 0.074 | -0.010 | 0.084 | 4.4 | 4/4 | 0.181 |
| K7 | asia | c4_turt55_mtf_ge4 | 3865 | 0.100 | 0.009 | 0.090 | 4.4 | 4/4 | 0.144 |
| K7 | asia | c4_ichiF_cloud_15m_side | 6977 | 0.078 | -0.006 | 0.084 | 4.3 | 4/4 | 0.143 |
| K7 | asia | c4_rfiltF_dir_15m_side | 8403 | 0.070 | -0.015 | 0.085 | 4.3 | 4/4 | 0.173 |
| H7 | asia | c4_ichiF_tk_15m_nodiv | 726 | 0.099 | -0.140 | 0.239 | 4.3 | 4/4 | 0.179 |
| K7 | asia | c4_ichiF_score_15m_side | 8865 | 0.064 | -0.012 | 0.076 | 4.3 | 4/4 | 0.121 |
| A7 | nypm | c4_lrcS_slope_5m_side | 2858 | 0.062 | -0.176 | 0.238 | 4.3 | 4/4 | 0.324 |
| K7 | nypm | c4_turt55_mtf_all | 250 | 0.277 | -0.021 | 0.298 | 4.3 | 4/4 | 0.202 |
| K7 | asia | c4_hiloS_15m_side | 8807 | 0.069 | -0.018 | 0.087 | 4.3 | 4/4 | 0.175 |
| K7 | asia | c4_ichiS_cloud_5m_hold3 | 6878 | 0.076 | -0.004 | 0.079 | 4.2 | 4/4 | 0.166 |
| K7 | asia | c4_rfiltF_60m_side | 8267 | 0.075 | -0.019 | 0.094 | 4.2 | 4/4 | 0.129 |
| K7 | asia | c4_don20_pos_15m_side | 9350 | 0.064 | -0.017 | 0.081 | 4.2 | 4/4 | 0.162 |
| K7 | asia | c4_hiloS_15m_hold3 | 7920 | 0.072 | -0.011 | 0.083 | 4.2 | 4/4 | 0.159 |
| K7 | asia | c4_rfiltF_dir_15m_hold3 | 7957 | 0.072 | -0.011 | 0.083 | 4.2 | 3/4 | 0.188 |
| K7 | asia | c4_mcgS_slope_15m_side | 9049 | 0.070 | -0.023 | 0.093 | 4.2 | 4/4 | 0.182 |
| K7 | asia | c4_mcgS_px_15m_side | 9049 | 0.070 | -0.023 | 0.093 | 4.2 | 4/4 | 0.182 |
| K7 | asia | c4_alli_spread_5m_side | 8715 | 0.063 | -0.009 | 0.071 | 4.2 | 4/4 | 0.134 |
| K7 | asia | c4_ichi_cloud_5m_hold3 | 7065 | 0.072 | -0.002 | 0.075 | 4.2 | 4/4 | 0.117 |
| K7 | asia | c4_chand_5m_hold3 | 8911 | 0.062 | -0.010 | 0.072 | 4.2 | 4/4 | 0.086 |
| K7 | asia | c4_rfiltS_mtf_ge4 | 9861 | 0.064 | -0.026 | 0.091 | 4.2 | 4/4 | 0.058 |
| K7 | asia | c4_mcg_slope_15m_side | 10146 | 0.057 | -0.018 | 0.075 | 4.1 | 4/4 | 0.156 |
| K7 | asia | c4_mcg_px_15m_side | 10146 | 0.057 | -0.018 | 0.075 | 4.1 | 4/4 | 0.156 |
| K7 | asia | c4_stAF_15m_side | 8417 | 0.069 | -0.013 | 0.082 | 4.1 | 4/4 | 0.068 |
| K7 | asia | c4_ichiF_cloud_5m_hold3 | 7435 | 0.067 | -0.001 | 0.068 | 4.1 | 4/4 | 0.071 |

## B2-C smart-money / price action

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 1909; |t|>2: 0 (chance expectation ~86 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_smc.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_struct_1m_fresh5 | 40414 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_fresh1 | 16352 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_side | 162210 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_against | 29310 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_hold3 | 146783 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_fresh5 | 28036 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_fresh1 | 10057 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_side | 162210 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_against | 29310 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_hold3 | 146783 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_fresh5 | 23879 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_fresh1 | 2277 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_side | 4608 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_against | 35242 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_hold3 | 2186 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_side | 24564 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_against | 53343 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_hold3 | 14136 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_side | 144289 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_rise | 36395 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_fresh5 | 9083 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dsup_1m_hi | 47233 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dsup_1m_rise | 91759 | 0.57 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dres_1m_hi | 41112 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dres_1m_rise | 76043 | 0.52 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_struct_1m_fresh5 | 40414 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_fresh1 | 16352 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_side | 162210 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_against | 29310 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_hold3 | 146783 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_fresh5 | 28036 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_fresh1 | 10057 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_side | 162210 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_against | 29310 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_hold3 | 146783 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_fresh5 | 23879 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_fresh1 | 2277 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_side | 4608 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_against | 35242 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_hold3 | 2186 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_side | 24564 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_against | 53343 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_hold3 | 14136 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_side | 144289 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_rise | 36395 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_fresh5 | 9083 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dsup_1m_hi | 47233 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dsup_1m_rise | 91759 | 0.57 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dres_1m_hi | 41112 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dres_1m_rise | 76043 | 0.52 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 131 of 10926 session-condition cells pass (chance-level expectation under independence ~135 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_oteF_5m_against | 987 | -0.138 | -0.091 | -3.8 | 0/4 | -0.157 |
| close | c4_sd_dres_1d_rise | 4367 | -0.153 | -0.091 | -3.7 | 0/4 | -0.102 |
| close | c4_sdF_dres_1d_rise | 4346 | -0.144 | -0.081 | -3.3 | 0/4 | -0.061 |
| close | c4_sdS_dres_1d_rise | 4259 | -0.143 | -0.078 | -3.1 | 0/4 | -0.040 |
| close | c4_brkS_near_3m_against | 1881 | -0.127 | -0.075 | -3.1 | 0/4 | -0.100 |
| close | c4_brkS_near_mtf_ge4 | 154 | 0.430 | 0.074 | 3.9 | 4/4 | 0.827 |
| nyam | c4_brk_in_3m_against | 2425 | -0.135 | -0.096 | -4.3 | 0/4 | -0.148 |
| nyam | c4_sdflip_in_1d_against | 2944 | 0.165 | 0.081 | 3.2 | 4/4 | 0.089 |
| nyam | c4_sdS_dsup_1d_rise | 13187 | 0.121 | 0.080 | 3.4 | 4/4 | 0.096 |
| nyam | c4_brkS_in_3m_side | 817 | 0.139 | 0.079 | 3.2 | 4/4 | 0.261 |
| nyam | c4_sdF_cnt_3m_fresh5 | 1479 | -0.142 | -0.077 | -3.1 | 0/4 | -0.041 |
| nyam | c4_fvgF_dres_1d_rise | 5150 | -0.130 | -0.076 | -3.1 | 0/4 | -0.142 |
| nypm | c4_fvgS_near_60m_against | 7375 | -0.169 | -0.099 | -4.0 | 0/4 | -0.160 |
| nypm | c4_pdS_5m_eleave | 1011 | -0.173 | -0.095 | -3.8 | 0/4 | -0.261 |
| nypm | c4_obS_cnt_mtf_all | 4523 | 0.204 | 0.090 | 3.6 | 4/4 | 0.215 |
| nypm | c4_fvgS_near_15m_against | 6410 | -0.135 | -0.089 | -3.7 | 0/4 | -0.212 |
| nypm | c4_sdS_cnt_mtf_all | 4852 | 0.177 | 0.087 | 3.5 | 4/4 | 0.164 |
| nypm | c4_pdS_60m_eagainst | 12457 | 0.126 | 0.084 | 3.6 | 4/4 | 0.352 |
| pre | c4_structS_1d_fresh1 | 135 | -0.713 | -0.105 | -5.9 | 0/4 | -0.636 |
| pre | c4_struct_1m_fresh1 | 795 | -0.123 | -0.074 | -3.0 | 0/4 | -0.054 |
| pre | c4_ob_in_3m_fresh5 | 1334 | 0.140 | 0.069 | 2.7 | 4/4 | 0.113 |
| pre | c4_fvgF_cnt_mtf_n | 1217 | -0.231 | -0.068 | -3.0 | 0/4 | -0.341 |
| pre | c4_eqpool_dnF_5m_rise | 1649 | -0.141 | -0.068 | -2.7 | 0/4 | -0.130 |
| pre | c4_ifvgF_in_5m_side | 600 | 0.185 | 0.066 | 2.8 | 4/4 | 0.117 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (537 of 51483 cell-conditions pass; chance at t>2.5 alone ~319)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | c4_fvgS_in_60m_fresh1 | 62 | 0.637 | 0.085 | 0.552 | 5.8 | 3/3 | 0.638 |
| P7 | london | c4_eqsweep_1d_fresh5 | 299 | 0.290 | 0.014 | 0.276 | 4.8 | 3/3 | 0.344 |
| P7 | close | c4_ob_in_60m_fresh1 | 72 | 0.471 | -0.010 | 0.480 | 4.3 | 3/3 | 0.948 |
| A7 | nypm | c4_obS_cnt_mtf_all | 1060 | 0.215 | -0.087 | 0.302 | 4.2 | 4/4 | 0.240 |
| K7 | asia | c4_fvgF_cnt_1m_side | 10125 | 0.061 | -0.025 | 0.086 | 4.2 | 4/4 | 0.169 |
| A7 | nypm | c4_pdS_60m_eagainst | 2620 | 0.069 | -0.149 | 0.217 | 4.2 | 4/4 | 0.537 |
| P7 | close | c4_obF_in_60m_fresh1 | 86 | 0.422 | -0.010 | 0.432 | 4.2 | 4/4 | 0.524 |
| M7 | pre | c4_ob_near_3m_side | 389 | 0.248 | -0.046 | 0.294 | 4.2 | 3/4 | 0.524 |
| M7 | pre | c4_ob_near_3m_hold3 | 178 | 0.339 | -0.027 | 0.366 | 4.1 | 3/4 | 0.650 |
| A7 | nypm | c4_struct_60m_hold3 | 2422 | 0.084 | -0.144 | 0.228 | 4.0 | 4/4 | 0.423 |
| A7 | nypm | c4_choch_60m_hold3 | 2422 | 0.084 | -0.144 | 0.228 | 4.0 | 4/4 | 0.423 |
| K7 | asia | c4_sdF_cnt_1m_side | 9428 | 0.065 | -0.021 | 0.086 | 4.0 | 4/4 | 0.187 |
| K7 | asia | c4_fvg_cnt_1m_side | 10066 | 0.060 | -0.022 | 0.082 | 4.0 | 4/4 | 0.176 |
| A7 | nypm | c4_sdS_cnt_mtf_all | 1124 | 0.183 | -0.081 | 0.263 | 3.9 | 4/4 | 0.220 |
| A7 | nypm | c4_sd_cnt_15m_side | 2812 | 0.064 | -0.172 | 0.237 | 3.9 | 3/4 | 0.402 |
| M7 | close | c4_obF_cnt_1d_rise | 295 | 0.311 | -0.012 | 0.323 | 3.8 | 4/4 | 0.605 |
| A7 | nypm | c4_ob_cnt_mtf_all | 1158 | 0.184 | -0.084 | 0.269 | 3.8 | 4/4 | 0.293 |
| K7 | asia | c4_sdS_cnt_1m_side | 8955 | 0.067 | -0.017 | 0.083 | 3.8 | 4/4 | 0.229 |
| K7 | london | c4_eqsweep_1d_fresh5 | 193 | 0.328 | 0.006 | 0.322 | 3.8 | 3/3 | 0.390 |
| K7 | pre | c4_ote_wideF_1d_against | 187 | 0.286 | -0.061 | 0.346 | 3.8 | 4/4 | 0.375 |
| K7 | asia | c4_fvgF_cnt_60m_rise | 2089 | 0.111 | 0.020 | 0.091 | 3.8 | 4/4 | 0.137 |
| K7 | nypm | c4_fvg_near_mtf_ge4 | 210 | 0.210 | -0.016 | 0.226 | 3.7 | 4/4 | 0.347 |
| K7 | asia | c4_choch_5m_hold3 | 8872 | 0.061 | -0.007 | 0.068 | 3.7 | 4/4 | 0.119 |
| K7 | asia | c4_struct_5m_hold3 | 8872 | 0.061 | -0.007 | 0.068 | 3.7 | 4/4 | 0.119 |
| K7 | asia | c4_obF_cnt_1m_side | 9390 | 0.063 | -0.016 | 0.079 | 3.7 | 4/4 | 0.200 |
| P7 | asia | c4_fvgS_cnt_3m_side | 13549 | 0.070 | -0.015 | 0.084 | 3.7 | 4/4 | 0.186 |
| M7 | nypm | c4_structF_60m_fresh1 | 197 | 0.398 | 0.001 | 0.397 | 3.7 | 4/4 | 0.563 |
| P7 | asia | c4_fvg_near_15m_side | 7193 | 0.090 | 0.011 | 0.079 | 3.6 | 4/4 | 0.065 |
| K7 | asia | c4_choch_5m_side | 9942 | 0.057 | -0.013 | 0.070 | 3.6 | 4/4 | 0.126 |
| K7 | asia | c4_struct_5m_side | 9942 | 0.057 | -0.013 | 0.070 | 3.6 | 4/4 | 0.126 |

## B2-D volume

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 482; |t|>2: 0 (chance expectation ~21 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_vol.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_rvol_1m_hi | 95391 | 0.50 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_hi_z1 | 50465 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_lo_z1 | 56523 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_hi_z2 | 18703 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_lo_z2 | 29993 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_rise | 113329 | 0.59 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_side | 158639 | 0.83 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_rise | 134430 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_fresh5 | 181736 | 0.95 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_ewith | 45278 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eagainst | 4755 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eleave | 27703 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eenter | 43882 | 0.23 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_side | 134254 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_rise | 117869 | 0.62 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_fresh5 | 174156 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_side | 134254 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_rise | 112570 | 0.59 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_fresh5 | 171140 | 0.90 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_ewith | 50613 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eagainst | 6284 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eleave | 46052 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eenter | 49082 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cvd_1m_side | 140951 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cvd_1m_rise | 119910 | 0.63 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_rvol_1m_hi | 95391 | 0.50 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_hi_z1 | 50465 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_lo_z1 | 56523 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_hi_z2 | 18703 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_lo_z2 | 29993 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_rise | 113329 | 0.59 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_side | 158639 | 0.83 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_rise | 134430 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_fresh5 | 181736 | 0.95 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_ewith | 45278 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eagainst | 4755 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eleave | 27703 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eenter | 43882 | 0.23 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_side | 134254 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_rise | 117869 | 0.62 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_fresh5 | 174156 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_side | 134254 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_rise | 112570 | 0.59 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_fresh5 | 171140 | 0.90 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_ewith | 50613 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eagainst | 6284 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eleave | 46052 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eenter | 49082 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cvd_1m_side | 140951 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cvd_1m_rise | 119910 | 0.63 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 18 of 2493 session-condition cells pass (chance-level expectation under independence ~30 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_avwap_swing_lo_15m_rise | 11633 | 0.108 | 0.062 | 2.5 | 4/4 | 0.276 |
| close | c4_rvol_60m_hi | 5741 | -0.098 | -0.061 | -2.5 | 0/4 | -0.067 |
| nyam | c4_vsa_stopvol_3m_against | 213 | 0.211 | 0.059 | 2.6 | 4/4 | 0.131 |
| nyam | c4_delta_60m_rise | 14018 | -0.061 | -0.049 | -2.5 | 0/4 | -0.082 |
| nyam | c4_cvd_ema_1m_nodiv | 19211 | -0.055 | -0.047 | -2.7 | 0/4 | -0.118 |
| nypm | c4_vsa_nodemand_1d_fresh5 | 7648 | -0.148 | -0.078 | -3.1 | 0/4 | -0.102 |
| nypm | c4_avwap_month_open_far | 21556 | 0.138 | 0.071 | 2.8 | 4/4 | 0.262 |
| nypm | c4_cvdS_60m_fresh5 | 5665 | 0.123 | 0.071 | 2.9 | 4/4 | 0.098 |
| nypm | c4_rvol_3m_rise | 12741 | -0.039 | -0.037 | -3.2 | 0/4 | -0.023 |
| nypm | c4_cvd_1m_rise | 16524 | -0.038 | -0.036 | -3.0 | 0/4 | -0.045 |
| pre | c4_vp_psess_hvn_near | 555 | 0.269 | 0.101 | 4.2 | 4/4 | 0.128 |
| pre | c4_rvol_dir_15m_eagainst | 303 | -0.399 | -0.088 | -4.2 | 0/4 | -0.590 |
| pre | c4_rvol_60m_hi_z1 | 1162 | -0.205 | -0.069 | -2.9 | 0/4 | -0.036 |
| pre | c4_rvol_dir_5m_eleave | 1025 | -0.162 | -0.067 | -2.7 | 0/4 | -0.281 |
| pre | c4_avwap_swing_lo_60m_far | 4897 | -0.122 | -0.065 | -2.6 | 0/4 | -0.121 |
| pre | c4_vp_frsw_pocdist_gt1.5 | 1635 | -0.149 | -0.063 | -2.6 | 0/4 | -0.248 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (98 of 11824 cell-conditions pass; chance at t>2.5 alone ~73)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_rvol_dir_15m_ewith | 1538 | 0.147 | 0.020 | 0.128 | 5.5 | 4/4 | 0.158 |
| K7 | asia | c4_rvol_dir_15m_eenter | 1455 | 0.139 | 0.021 | 0.118 | 5.3 | 4/4 | 0.143 |
| M7 | pre | c4_avwap_ge5 | 2522 | 0.015 | -0.650 | 0.665 | 5.2 | 4/4 | 1.016 |
| K7 | asia | c4_rvol_15m_hi_z1 | 2037 | 0.123 | 0.019 | 0.105 | 5.0 | 4/4 | 0.110 |
| K7 | asia | c4_vp_psess_va_above | 8832 | 0.076 | -0.028 | 0.105 | 4.6 | 4/4 | 0.157 |
| K7 | asia | c4_avwap_swing_lo_60m_side | 10047 | 0.064 | -0.030 | 0.094 | 4.2 | 4/4 | 0.239 |
| M7 | pre | c4_avwap_midnight_side | 2489 | 0.016 | -0.468 | 0.485 | 4.0 | 4/4 | 0.771 |
| K7 | asia | c4_avwap_swing_lo_60m_rise | 9226 | 0.066 | -0.019 | 0.084 | 3.9 | 4/4 | 0.202 |
| A7 | nypm | c4_vsa_upthrust_1m_fresh5 | 79 | 0.443 | -0.016 | 0.459 | 3.9 | 3/4 | 0.508 |
| K7 | asia | c4_vp_psess_poc_side | 10051 | 0.064 | -0.029 | 0.093 | 3.8 | 4/4 | 0.118 |
| A7 | nyam | c4_delta_5m_fresh5 | 3242 | 0.055 | -0.182 | 0.236 | 3.8 | 4/4 | 0.295 |
| A7 | nyam | c4_delta_ratio_5m_fresh5 | 3242 | 0.055 | -0.182 | 0.236 | 3.8 | 4/4 | 0.295 |
| A7 | nypm | c4_vp_fr1440_poc_side | 3692 | 0.017 | -0.280 | 0.298 | 3.7 | 4/4 | 0.457 |
| K7 | asia | c4_avwap_pd_low_side | 9485 | 0.065 | -0.022 | 0.087 | 3.7 | 4/4 | 0.121 |
| P7 | asia | c4_avwap_ge7 | 17451 | 0.057 | -0.037 | 0.094 | 3.7 | 4/4 | 0.195 |
| K7 | asia | c4_avwap_asia_open_rise | 10414 | 0.059 | -0.023 | 0.082 | 3.7 | 4/4 | 0.163 |
| K7 | asia | c4_avwap_pd_low_rise | 8849 | 0.068 | -0.017 | 0.086 | 3.7 | 4/4 | 0.121 |
| K7 | asia | c4_avwap_asia_open_side | 12164 | 0.052 | -0.046 | 0.097 | 3.7 | 4/4 | 0.179 |
| K7 | asia | c4_rvol_5m_hi_z1 | 2354 | 0.090 | 0.022 | 0.068 | 3.6 | 4/4 | 0.069 |
| K7 | asia | c4_avwap_ge9 | 8616 | 0.068 | -0.014 | 0.082 | 3.5 | 3/4 | 0.158 |
| P7 | nypm | c4_avwap_month_open_far | 7022 | 0.011 | -0.178 | 0.189 | 3.4 | 4/4 | 0.318 |
| K7 | nypm | c4_cvdS_60m_fresh5 | 1043 | 0.100 | -0.033 | 0.133 | 3.4 | 4/4 | 0.077 |
| K7 | asia | c4_avwap_nypm_open_side | 9515 | 0.062 | -0.017 | 0.080 | 3.4 | 3/4 | 0.223 |
| P7 | asia | c4_avwap_ge5 | 19949 | 0.047 | -0.055 | 0.102 | 3.4 | 4/4 | 0.238 |
| K7 | asia | c4_avwap_nypm_open_rise | 8822 | 0.065 | -0.012 | 0.077 | 3.3 | 3/4 | 0.244 |
| P7 | asia | c4_avwap_swing_lo_60m_side | 17269 | 0.054 | -0.025 | 0.080 | 3.3 | 4/4 | 0.178 |
| P7 | asia | c4_avwap_swing_lo_60m_rise | 16861 | 0.055 | -0.022 | 0.077 | 3.3 | 4/4 | 0.188 |
| K7 | asia | c4_avwap_ge7 | 10456 | 0.056 | -0.019 | 0.074 | 3.2 | 3/4 | 0.209 |
| K7 | asia | c4_rvol_15m_hi_z2 | 408 | 0.202 | 0.028 | 0.174 | 3.2 | 4/4 | 0.345 |
| K7 | asia | c4_rvol_dir_5m_eagainst | 512 | 0.149 | 0.028 | 0.120 | 3.2 | 4/4 | 0.218 |

## B2-E causal ML-style

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 222; |t|>2: 0 (chance expectation ~10 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_ml.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_kr_dir_1m_fresh5 | 23918 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_fresh1 | 6389 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_side | 185563 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_rise | 153289 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_side | 185469 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_rise | 151978 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_fresh5 | 61534 | 0.32 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_fresh5 | 36591 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_fresh1 | 10051 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_side | 178511 | 0.93 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_rise | 151199 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_side | 182972 | 0.96 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_rise | 149915 | 0.78 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_fresh5 | 87186 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_fresh5 | 16120 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_fresh1 | 4534 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_side | 184734 | 0.96 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_rise | 154641 | 0.81 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_side | 185504 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_rise | 153577 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_fresh5 | 42969 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_fresh5 | 22153 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_fresh1 | 5690 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_side | 181956 | 0.95 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_rise | 125645 | 0.66 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_kr_dir_1m_fresh5 | 23918 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_fresh1 | 6389 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_side | 185563 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_rise | 153289 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_side | 185469 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_rise | 151978 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_fresh5 | 61534 | 0.32 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_fresh5 | 36591 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_fresh1 | 10051 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_side | 178511 | 0.93 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_rise | 151199 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_side | 182972 | 0.96 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_rise | 149915 | 0.78 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_fresh5 | 87186 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_fresh5 | 16120 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_fresh1 | 4534 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_side | 184734 | 0.96 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_rise | 154641 | 0.81 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_side | 185504 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_rise | 153577 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_fresh5 | 42969 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_fresh5 | 22153 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_fresh1 | 5690 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_side | 181956 | 0.95 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_rise | 125645 | 0.66 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 12 of 1279 session-condition cells pass (chance-level expectation under independence ~15 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| london | c4_kr_dir_5m_side | 52685 | 0.084 | 0.066 | 3.2 | 4/4 | 0.220 |
| london | c4_kr_px_5m_side | 52907 | 0.078 | 0.060 | 2.9 | 4/4 | 0.211 |
| london | c4_lorS_60m_rise | 20799 | 0.049 | 0.044 | 2.7 | 4/4 | 0.088 |
| nyam | c4_kr_dir_1m_fresh1 | 880 | -0.127 | -0.080 | -3.3 | 0/4 | -0.198 |
| nyam | c4_krS_dir_1m_fresh5 | 2064 | -0.081 | -0.064 | -3.1 | 0/4 | -0.002 |
| nyam | c4_kr_dir_1m_fresh5 | 3172 | -0.071 | -0.059 | -3.2 | 0/4 | -0.069 |
| nyam | c4_krF_dir_1m_fresh5 | 4675 | -0.059 | -0.051 | -2.9 | 0/4 | -0.114 |
| nypm | c4_krF_px_60m_fresh5 | 12638 | -0.109 | -0.069 | -2.9 | 0/4 | -0.060 |
| nypm | c4_krS_px_60m_fresh5 | 8993 | -0.108 | -0.066 | -2.7 | 0/4 | -0.142 |
| nypm | c4_kr_px_1d_rise | 12377 | 0.111 | 0.062 | 2.5 | 4/4 | 0.047 |
| pre | c4_krS_dir_60m_side | 5417 | 0.153 | 0.067 | 2.7 | 4/4 | 0.192 |
| pre | c4_krF_dir_1d_fresh1 | 276 | 0.530 | 0.054 | 3.6 | 4/4 | 0.464 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (89 of 6387 cell-conditions pass; chance at t>2.5 alone ~39)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_krF_px_15m_side | 9895 | 0.064 | -0.027 | 0.092 | 4.6 | 4/4 | 0.178 |
| K7 | asia | c4_kr_px_15m_side | 9297 | 0.069 | -0.025 | 0.094 | 4.5 | 4/4 | 0.173 |
| K7 | asia | c4_kr_dir_15m_side | 9187 | 0.070 | -0.024 | 0.094 | 4.4 | 4/4 | 0.180 |
| K7 | asia | c4_krF_dir_15m_side | 10162 | 0.059 | -0.020 | 0.079 | 4.3 | 4/4 | 0.168 |
| P7 | asia | c4_krF_px_15m_side | 18387 | 0.054 | -0.044 | 0.098 | 4.1 | 4/4 | 0.113 |
| K7 | asia | c4_krS_px_15m_side | 8877 | 0.070 | -0.020 | 0.089 | 4.1 | 4/4 | 0.165 |
| P7 | asia | c4_kr_px_15m_side | 17507 | 0.056 | -0.037 | 0.093 | 3.8 | 4/4 | 0.155 |
| K7 | asia | c4_krS_dir_5m_side | 10599 | 0.055 | -0.019 | 0.073 | 3.8 | 3/4 | 0.147 |
| K7 | asia | c4_krS_px_5m_side | 11282 | 0.050 | -0.019 | 0.069 | 3.7 | 4/4 | 0.133 |
| P7 | asia | c4_kr_dir_15m_side | 17679 | 0.055 | -0.036 | 0.091 | 3.7 | 4/4 | 0.157 |
| K7 | asia | c4_kr_dir_5m_side | 12270 | 0.046 | -0.023 | 0.069 | 3.6 | 4/4 | 0.129 |
| K7 | asia | c4_kr_px_5m_side | 12366 | 0.046 | -0.025 | 0.071 | 3.6 | 4/4 | 0.139 |
| H7 | nypm | c4_lorS_3m_side | 188 | 0.177 | -0.100 | 0.278 | 3.5 | 4/4 | 0.059 |
| P7 | asia | c4_krS_px_15m_side | 16444 | 0.059 | -0.028 | 0.087 | 3.4 | 4/4 | 0.197 |
| K7 | asia | c4_kr_px_mtf_ge4 | 11176 | 0.052 | -0.022 | 0.074 | 3.4 | 3/4 | 0.167 |
| M7 | london | c4_kr_dir_5m_side | 15241 | 0.029 | -0.253 | 0.282 | 3.4 | 4/4 | 0.531 |
| A7 | pre | c4_lorF_1m_flip3 | 337 | 0.053 | -0.134 | 0.188 | 3.4 | 4/4 | 0.286 |
| P7 | asia | c4_kr_px_mtf_ge4 | 17802 | 0.051 | -0.022 | 0.073 | 3.3 | 3/4 | 0.108 |
| K7 | asia | c4_krS_dir_15m_side | 8567 | 0.067 | -0.012 | 0.079 | 3.3 | 4/4 | 0.154 |
| K7 | asia | c4_krS_dir_3m_side | 13497 | 0.041 | -0.038 | 0.079 | 3.3 | 4/4 | 0.032 |
| M7 | pre | c4_krF_dir_1d_fresh1 | 78 | 0.537 | -0.024 | 0.561 | 3.3 | 4/4 | 0.650 |
| P7 | asia | c4_krF_dir_15m_side | 18991 | 0.048 | -0.028 | 0.076 | 3.3 | 4/4 | 0.110 |
| P7 | asia | c4_kr_dir_mtf_ge4 | 17838 | 0.050 | -0.019 | 0.069 | 3.3 | 4/4 | 0.121 |
| U7 | pre | c4_krF_px_1d_rise | 104 | 0.203 | -0.232 | 0.436 | 3.2 | 3/4 | 0.907 |
| P7 | asia | c4_krS_dir_15m_side | 15480 | 0.062 | -0.020 | 0.082 | 3.1 | 4/4 | 0.200 |
| P7 | asia | c4_krS_dir_5m_side | 19439 | 0.046 | -0.027 | 0.073 | 3.1 | 4/4 | 0.141 |
| M7 | pre | c4_krF_dir_1d_rise | 1258 | 0.101 | -0.113 | 0.213 | 3.1 | 3/4 | 0.374 |
| H7 | nyam | c4_lor_60m_side | 279 | 0.187 | -0.019 | 0.206 | 3.1 | 4/4 | 0.176 |
| H7 | nyam | c4_lor_60m_flip3 | 210 | 0.221 | -0.004 | 0.225 | 3.0 | 3/4 | 0.217 |
| H7 | london | c4_krF_px_60m_side | 927 | 0.066 | -0.109 | 0.175 | 3.0 | 4/4 | 0.189 |

## B2-C2 IRL/ERL sweeps (Addendum 5 Step B)

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 294; |t|>2: 0 (chance expectation ~13 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_irl.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_irl_a_pd_ext_against_5 | 380 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_15 | 1202 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_fade_30 | 244 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_30 | 2190 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_fade_60 | 638 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_60 | 3864 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_5 | 4458 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_5 | 14937 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_15 | 13846 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_15 | 38086 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_30 | 28710 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_30 | 59699 | 0.31 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_60 | 54591 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_60 | 85687 | 0.45 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_20 | 5315 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_40 | 15099 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_80 | 34639 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_danger_20 | 161 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/2 | nan | nan |
| c4_irl_a_pd_valid | 189371 | 0.99 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_5 | 135 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_5 | 1265 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_15 | 571 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_15 | 3653 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_30 | 1341 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_30 | 6382 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_irl_a_pd_ext_against_5 | 380 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_15 | 1202 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_fade_30 | 244 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_30 | 2190 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_fade_60 | 638 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_60 | 3864 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_5 | 4458 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_5 | 14937 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_15 | 13846 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_15 | 38086 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_30 | 28710 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_30 | 59699 | 0.31 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_60 | 54591 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_60 | 85687 | 0.45 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_20 | 5315 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_40 | 15099 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_80 | 34639 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_danger_20 | 161 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/2 | nan | nan |
| c4_irl_a_pd_valid | 189371 | 0.99 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_5 | 135 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_5 | 1265 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_15 | 571 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_15 | 3653 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_30 | 1341 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_30 | 6382 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 30 of 1401 session-condition cells pass (chance-level expectation under independence ~17 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_irl_ge2_ext_against_60 | 1554 | 0.144 | 0.070 | 2.8 | 4/4 | 0.101 |
| london | c4_irl_f_or30_ext_against_5 | 502 | -0.125 | -0.068 | -2.7 | 0/4 | -0.087 |
| london | c4_irl_n_ext_fade_60 | 4020 | -0.087 | -0.063 | -2.8 | 0/4 | -0.079 |
| nyam | c4_irl_e60_10_ext_fade_30 | 102 | -0.497 | -0.090 | -4.7 | 0/4 | -0.230 |
| nyam | c4_irl_f_or30_ext_fade_15 | 131 | -0.316 | -0.078 | -3.6 | 0/4 | -0.218 |
| nyam | c4_irl_f_or60_ext_fade_60 | 473 | -0.229 | -0.070 | -3.0 | 0/4 | -0.077 |
| nypm | c4_irl_a_pd_int_against_60 | 8498 | -0.150 | -0.109 | -4.9 | 0/4 | -0.208 |
| nypm | c4_irl_a_pd_int_against_15 | 3683 | -0.140 | -0.100 | -4.4 | 0/4 | -0.181 |
| nypm | c4_irl_a_pd_int_against_30 | 5715 | -0.133 | -0.098 | -4.4 | 0/4 | -0.161 |
| nypm | c4_irl_a_pd_int_against_5 | 1480 | -0.147 | -0.096 | -4.0 | 0/4 | -0.217 |
| nypm | c4_irl_n_int_fade_15 | 218 | 0.384 | 0.093 | 4.3 | 4/4 | 0.629 |
| nypm | c4_irl_e60_20_int_against_60 | 10349 | -0.137 | -0.091 | -3.8 | 0/4 | -0.081 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (27 of 6073 cell-conditions pass; chance at t>2.5 alone ~37)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | c4_irl_f_or60_magnet_20 | 185 | 0.333 | 0.083 | 0.250 | 3.4 | 4/4 | 0.550 |
| M7 | nyam | c4_irl_f_or60_int_against_5 | 119 | 0.296 | 0.025 | 0.271 | 3.3 | 4/4 | 0.561 |
| A7 | nyam | c4_irl_n_int_against_60 | 107 | 0.425 | 0.015 | 0.410 | 3.2 | 3/4 | 1.024 |
| U7 | asia | c4_irl_ge2_ext_against_30 | 67 | 0.373 | 0.051 | 0.322 | 3.1 | 3/3 | 0.359 |
| P7 | nyam | c4_irl_e240_20_magnet_80 | 121 | 0.344 | 0.005 | 0.339 | 3.1 | 3/4 | 0.565 |
| P7 | london | c4_irl_ge2_int_fade_5 | 865 | 0.117 | 0.014 | 0.103 | 3.0 | 3/4 | 0.112 |
| P7 | london | c4_irl_any_int_fade_5 | 884 | 0.117 | 0.014 | 0.103 | 3.0 | 3/4 | 0.115 |
| M7 | nypm | c4_irl_n_int_fade_60 | 225 | 0.293 | 0.003 | 0.290 | 3.0 | 4/4 | 0.766 |
| M7 | nyam | c4_irl_f_or60_int_against_30 | 635 | 0.165 | 0.015 | 0.150 | 2.9 | 4/4 | 0.226 |
| H7 | close | c4_irl_d_wk_int_fade_60 | 101 | 0.216 | -0.076 | 0.292 | 2.9 | 4/4 | 0.053 |
| M7 | nyam | c4_irl_f_or60_int_against_15 | 340 | 0.190 | 0.021 | 0.169 | 2.8 | 4/4 | 0.176 |
| P7 | london | c4_irl_b_cs60_int_fade_5 | 735 | 0.116 | 0.014 | 0.102 | 2.8 | 3/4 | 0.088 |
| K7 | pre | c4_irl_e60_20_int_against_60 | 863 | 0.056 | -0.093 | 0.149 | 2.8 | 3/4 | 0.064 |
| P7 | nyam | c4_irl_n_int_against_60 | 156 | 0.294 | 0.004 | 0.290 | 2.7 | 3/4 | 0.385 |
| O7 | nyam | c4_irl_any_ext_against_30 | 118 | 0.557 | 0.117 | 0.440 | 2.7 | 4/4 | 0.909 |
| M7 | nypm | c4_irl_n_int_fade_30 | 127 | 0.316 | 0.007 | 0.309 | 2.7 | 4/4 | 0.984 |
| O7 | nyam | c4_irl_any_ext_against_15 | 99 | 0.604 | 0.126 | 0.478 | 2.7 | 4/4 | 0.661 |
| A7 | close | c4_irl_ge2_ext_against_60 | 373 | 0.116 | -0.069 | 0.185 | 2.7 | 4/4 | 0.051 |
| H7 | close | c4_irl_e15_20_int_fade_60 | 96 | 0.203 | -0.062 | 0.265 | 2.7 | 3/4 | 0.608 |
| M7 | close | c4_irl_a_pd_int_fade_15 | 211 | 0.204 | 0.003 | 0.201 | 2.7 | 3/4 | 0.154 |
| P7 | close | c4_irl_ge2_ext_against_60 | 496 | 0.146 | -0.019 | 0.165 | 2.7 | 4/4 | 0.160 |
| P7 | london | c4_irl_e60_20_int_fade_30 | 2287 | 0.092 | 0.008 | 0.084 | 2.6 | 4/4 | 0.068 |
| H7 | nyam | c4_irl_b_ps_ext_against_60 | 166 | 0.214 | 0.017 | 0.197 | 2.6 | 4/4 | 0.289 |
| U7 | asia | c4_irl_ge2_ext_against_60 | 86 | 0.301 | 0.051 | 0.250 | 2.6 | 3/4 | 0.177 |
| P7 | nypm | c4_irl_e60_20_int_fade_5 | 234 | 0.136 | -0.019 | 0.155 | 2.5 | 4/4 | 0.212 |
| U7 | asia | c4_irl_e240_20_int_against_15 | 169 | 0.221 | 0.039 | 0.181 | 2.5 | 3/4 | 0.328 |
| H7 | pre | c4_irl_e60_20_int_fade_60 | 110 | 0.159 | -0.142 | 0.301 | 2.5 | 4/4 | 0.702 |

## B11 candlestick library

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2228; |t|>2: 0 (chance expectation ~101 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_candle.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_cdl_hammer_1m_fresh5 | 9172 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_fresh1 | 717 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_fresh3 | 5160 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against3 | 9822 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against5 | 15739 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_side | 717 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against | 3751 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh5 | 7706 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh1 | 1373 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh3 | 4314 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against3 | 11545 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against5 | 18902 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_side | 1373 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against | 3327 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh5 | 8387 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh1 | 1428 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh3 | 4655 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against3 | 9194 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against5 | 14894 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_side | 1428 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against | 2654 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh5 | 7273 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh1 | 454 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh3 | 4009 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_against3 | 11096 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_cdl_hammer_1m_fresh5 | 9172 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_fresh1 | 717 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_fresh3 | 5160 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against3 | 9822 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against5 | 15739 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_side | 717 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against | 3751 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh5 | 7706 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh1 | 1373 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh3 | 4314 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against3 | 11545 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against5 | 18902 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_side | 1373 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against | 3327 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh5 | 8387 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh1 | 1428 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh3 | 4655 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against3 | 9194 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against5 | 14894 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_side | 1428 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against | 2654 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh5 | 7273 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh1 | 454 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh3 | 4009 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_against3 | 11096 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 137 of 9612 session-condition cells pass (chance-level expectation under independence ~119 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_cdl_harami_cross_1d_fresh5 | 564 | -0.254 | -0.096 | -4.0 | 0/4 | -0.259 |
| close | c4_cdl_morning_star_3m_against3 | 235 | 0.267 | 0.091 | 3.8 | 4/4 | 0.550 |
| close | c4_cdl_three_methods_1d_against3 | 239 | -0.335 | -0.088 | -4.0 | 0/4 | -0.237 |
| close | c4_cdl_mat_hold_15m_fresh5 | 3457 | -0.130 | -0.081 | -3.4 | 0/4 | -0.057 |
| close | c4_cdl_mat_hold_15m_fresh3 | 2413 | -0.133 | -0.076 | -3.1 | 0/4 | -0.067 |
| close | c4_cdl_inside_break_3m_fresh5 | 3313 | 0.097 | 0.074 | 3.5 | 4/4 | 0.183 |
| london | c4_cdl_marubozu_1d_against5 | 728 | -0.325 | -0.104 | -4.5 | 0/4 | -0.266 |
| london | c4_cdl_in_neck_3m_against5 | 105 | 0.423 | 0.096 | 4.6 | 4/4 | 0.620 |
| london | c4_cdl_on_neck_3m_against5 | 102 | 0.411 | 0.093 | 4.4 | 4/4 | 0.620 |
| london | c4_cdl_long_line_15m_against3_atlvl | 303 | 0.245 | 0.091 | 3.8 | 4/4 | 0.921 |
| london | c4_cdl_three_crows_3m_against5 | 247 | -0.319 | -0.090 | -4.0 | 0/4 | -0.387 |
| london | c4_cdl_hammer_60m_fresh1 | 980 | -0.246 | -0.077 | -3.3 | 0/4 | -0.405 |
| nyam | c4_cdl_shooting_star_3m_fresh5 | 676 | -0.215 | -0.098 | -3.9 | 0/4 | -0.008 |
| nyam | c4_cdl_harami_60m_side | 470 | -0.265 | -0.081 | -3.5 | 0/4 | -0.232 |
| nyam | c4_cdl_harami_60m_fresh1 | 470 | -0.265 | -0.081 | -3.5 | 0/4 | -0.232 |
| nyam | c4_cdl_gravestone_3m_against3 | 654 | 0.181 | 0.077 | 3.1 | 4/4 | 0.219 |
| nyam | c4_cdl_wide_range_trend_1m_fresh3_atlvl | 523 | -0.168 | -0.077 | -3.1 | 0/4 | -0.056 |
| nyam | c4_cdl_hanging_man_15m_against5 | 3353 | 0.140 | 0.074 | 3.0 | 4/4 | 0.098 |
| nypm | c4_cdl_harami_cross_1d_against | 322 | 0.526 | 0.107 | 5.3 | 4/4 | 0.527 |
| nypm | c4_cdl_harami_cross_1d_against3 | 815 | 0.323 | 0.081 | 3.7 | 4/4 | 0.424 |
| nypm | c4_cdl_harami_60m_against3_atlvl | 206 | 0.394 | 0.078 | 3.9 | 4/4 | 0.231 |
| nypm | c4_cdl_takuri_mtf_n | 124 | -0.353 | -0.077 | -3.7 | 0/4 | -0.277 |
| nypm | c4_cdl_opening_marubozu_1d_against5 | 4031 | 0.148 | 0.073 | 2.9 | 4/4 | 0.244 |
| nypm | c4_cdl_inside_break_close_15m_against5 | 2945 | -0.132 | -0.073 | -2.9 | 0/4 | -0.074 |
| pre | c4_cdl_marubozu_1d_against5 | 113 | -0.454 | -0.118 | -5.4 | 0/4 | -0.394 |
| pre | c4_cdl_belt_hold_1d_against | 132 | -0.603 | -0.076 | -4.6 | 0/3 | -0.943 |
| pre | c4_cdl_mat_hold_3m_fresh5 | 2096 | -0.125 | -0.074 | -3.0 | 0/4 | -0.283 |
| pre | c4_cdl_three_soldiers_1m_fresh5 | 194 | -0.330 | -0.067 | -3.3 | 0/4 | -0.368 |
| pre | c4_cdl_belt_hold_5m_fresh5 | 636 | 0.224 | 0.065 | 2.9 | 4/4 | 0.442 |
| pre | c4_cdl_mat_hold_3m_fresh3 | 1462 | -0.114 | -0.063 | -2.5 | 0/4 | -0.297 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (224 of 32282 cell-conditions pass; chance at t>2.5 alone ~200)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| A7 | nypm | c4_cdl_harami_cross_1d_against3 | 186 | 0.447 | -0.029 | 0.476 | 4.6 | 4/4 | 0.419 |
| A7 | nypm | c4_cdl_harami_cross_1d_against | 86 | 0.516 | -0.018 | 0.534 | 4.4 | 3/3 | 0.461 |
| A7 | nypm | c4_cdl_harami_cross_1d_against5 | 271 | 0.367 | -0.034 | 0.401 | 4.3 | 4/4 | 0.353 |
| A7 | nyam | c4_cdl_three_outside_5m_against3 | 63 | 0.461 | 0.019 | 0.442 | 4.3 | 3/3 | 0.233 |
| A7 | nypm | c4_cdl_hanging_man_mtf_n | 103 | 0.449 | -0.019 | 0.468 | 4.1 | 4/4 | 0.475 |
| K7 | pre | c4_cdl_tweezer_60m_against3 | 196 | 0.291 | -0.063 | 0.354 | 4.0 | 4/4 | 0.461 |
| M7 | nypm | c4_cdl_mat_hold_3m_fresh3_atlvl | 120 | 0.345 | 0.007 | 0.338 | 3.9 | 4/4 | 0.425 |
| K7 | asia | c4_cdl_gap_up_down_60m_fresh5 | 337 | 0.280 | 0.027 | 0.253 | 3.9 | 4/4 | 0.230 |
| H7 | london | c4_cdl_short_line_1m_rise | 98 | 0.322 | 0.000 | 0.322 | 3.9 | 4/4 | 0.204 |
| P7 | nypm | c4_cdl_harami_cross_1d_against3 | 232 | 0.357 | -0.025 | 0.383 | 3.8 | 4/4 | 0.538 |
| O7 | nyam | c4_cdl_wide_range_trend_3m_against5 | 136 | 0.595 | 0.082 | 0.513 | 3.8 | 4/4 | 0.327 |
| A7 | nypm | c4_cdl_hanging_man_15m_fresh3 | 65 | 0.508 | -0.016 | 0.523 | 3.7 | 3/3 | 0.399 |
| P7 | pre | c4_cdl_dragonfly_1d_fresh5 | 138 | 0.428 | 0.008 | 0.421 | 3.7 | 4/4 | 0.510 |
| M7 | nypm | c4_cdl_harami_60m_against3_atlvl | 62 | 0.455 | 0.009 | 0.446 | 3.6 | 4/4 | 0.224 |
| K7 | nyam | c4_cdl_gravestone_3m_against3 | 101 | 0.332 | 0.013 | 0.319 | 3.6 | 4/4 | 0.620 |
| A7 | pre | c4_cdl_belt_hold_mtf_n | 101 | 0.270 | -0.116 | 0.386 | 3.5 | 3/4 | 0.628 |
| A7 | nyam | c4_cdl_three_crows_1d_against5 | 168 | 0.330 | 0.012 | 0.318 | 3.5 | 3/3 | 0.478 |
| K7 | close | c4_cdl_inside_break_3m_fresh5 | 609 | 0.104 | -0.042 | 0.146 | 3.5 | 4/4 | 0.234 |
| P7 | nypm | c4_cdl_hanging_man_1d_side | 116 | 0.475 | -0.022 | 0.496 | 3.5 | 4/4 | 0.222 |
| P7 | nypm | c4_cdl_hanging_man_1d_fresh1 | 116 | 0.475 | -0.022 | 0.496 | 3.5 | 4/4 | 0.222 |
| K7 | close | c4_cdl_separating_lines_1m_fresh3 | 212 | 0.172 | -0.026 | 0.199 | 3.5 | 4/4 | 0.273 |
| P7 | nypm | c4_cdl_morning_star_60m_against5 | 213 | 0.319 | -0.023 | 0.342 | 3.4 | 3/4 | 0.284 |
| A7 | nyam | c4_cdl_marubozu_60m_side | 82 | 0.530 | 0.015 | 0.515 | 3.4 | 3/3 | 0.062 |
| A7 | nyam | c4_cdl_marubozu_60m_fresh1 | 82 | 0.530 | 0.015 | 0.515 | 3.4 | 3/3 | 0.062 |
| M7 | pre | c4_cdl_opening_marubozu_3m_against3 | 179 | 0.267 | -0.022 | 0.289 | 3.4 | 4/4 | 0.424 |
| M7 | london | c4_cdl_marubozu_15m_fresh3 | 260 | 0.317 | 0.020 | 0.297 | 3.4 | 4/4 | 0.345 |
| M7 | nypm | c4_cdl_harami_cross_1d_against | 84 | 0.529 | 0.006 | 0.523 | 3.4 | 3/3 | 0.672 |
| H7 | london | c4_cdl_harami_60m_against3 | 88 | 0.309 | 0.004 | 0.305 | 3.4 | 4/4 | 0.355 |
| P7 | pre | c4_cdl_belt_hold_5m_fresh5 | 153 | 0.337 | 0.010 | 0.326 | 3.3 | 4/4 | 0.531 |
| P7 | london | c4_cdl_separating_lines_60m_fresh5 | 1290 | 0.208 | 0.004 | 0.204 | 3.3 | 4/4 | 0.257 |

## B12 bar-level volume at price (footprint)

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 159; |t|>2: 0 (chance expectation ~7 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_fp.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_fp_1m_poc_with | 78923 | 0.41 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_against | 37799 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mid | 74798 | 0.39 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_with_2of3 | 55969 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_with_3of5 | 42601 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig1 | 151498 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig3 | 147570 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig_all3 | 45903 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_with | 10295 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_with3 | 18990 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack2_with | 34734 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_against | 1745 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_against3 | 7107 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_ahead | 23118 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_ahead3 | 65537 | 0.34 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_behind | 29632 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_behind3 | 71829 | 0.38 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with | 148561 | 0.78 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with3 | 143385 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with5 | 141520 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_div_with | 9870 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_div_against | 21354 | 0.11 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_dbot_with | 81392 | 0.42 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_dtop_with | 170805 | 0.89 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_close_delta_with | 104106 | 0.54 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_fp_1m_poc_with | 78923 | 0.41 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_against | 37799 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mid | 74798 | 0.39 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_with_2of3 | 55969 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_with_3of5 | 42601 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig1 | 151498 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig3 | 147570 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig_all3 | 45903 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_with | 10295 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_with3 | 18990 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack2_with | 34734 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_against | 1745 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_against3 | 7107 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_ahead | 23118 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_ahead3 | 65537 | 0.34 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_behind | 29632 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_behind3 | 71829 | 0.38 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with | 148561 | 0.78 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with3 | 143385 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with5 | 141520 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_div_with | 9870 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_div_against | 21354 | 0.11 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_dbot_with | 81392 | 0.42 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_dtop_with | 170805 | 0.89 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_close_delta_with | 104106 | 0.54 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 4 of 896 session-condition cells pass (chance-level expectation under independence ~11 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_fp_60m_dtop_with | 11059 | -0.114 | -0.067 | -2.7 | 0/4 | -0.162 |
| nyam | c4_fp_15m_delta_div_against | 3327 | 0.084 | 0.060 | 2.6 | 4/4 | 0.122 |
| nypm | c4_fp_mtf_stack3_with_n | 7491 | 0.065 | 0.054 | 3.0 | 4/4 | 0.107 |
| nypm | c4_fp_mtf_poc_with_n | 7846 | 0.039 | 0.035 | 2.5 | 4/4 | 0.044 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (31 of 4780 cell-conditions pass; chance at t>2.5 alone ~29)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | c4_fp_15m_stack3_against | 246 | 0.335 | 0.080 | 0.255 | 3.8 | 3/3 | 0.233 |
| M7 | nypm | c4_fp_mtf_stack3_with_n | 2103 | 0.088 | -0.022 | 0.110 | 3.7 | 4/4 | 0.110 |
| P7 | asia | c4_fp_5m_stack3_against | 271 | 0.181 | 0.035 | 0.146 | 3.3 | 4/4 | 0.184 |
| K7 | asia | c4_fp_5m_poc_with_3of5 | 2643 | 0.084 | 0.021 | 0.063 | 3.3 | 3/4 | 0.065 |
| P7 | nyam | c4_fp_15m_delta_div_against | 1070 | 0.113 | -0.007 | 0.121 | 3.3 | 4/4 | 0.100 |
| M7 | nyam | c4_fp_3m_poc_mig_all3 | 1224 | 0.108 | 0.012 | 0.096 | 3.2 | 3/4 | 0.177 |
| H7 | london | c4_fp_5m_delta_div_with | 116 | 0.259 | 0.001 | 0.258 | 3.1 | 4/4 | 0.366 |
| P7 | pre | c4_fp_60m_poc_against | 546 | 0.205 | -0.014 | 0.218 | 3.1 | 3/4 | 0.232 |
| P7 | nypm | c4_fp_1m_poc_against | 1396 | 0.051 | -0.028 | 0.079 | 3.0 | 4/4 | 0.132 |
| K7 | london | c4_fp_5m_stack3_with3 | 1158 | 0.090 | 0.003 | 0.087 | 3.0 | 4/4 | 0.089 |
| H7 | nyam | c4_fp_3m_poc_mid | 328 | 0.173 | -0.034 | 0.207 | 3.0 | 3/4 | 0.361 |
| A7 | nyam | c4_fp_1m_stack3_against | 107 | 0.278 | 0.019 | 0.259 | 3.0 | 4/4 | 0.536 |
| K7 | asia | c4_fp_60m_poc_mig3 | 8050 | 0.058 | 0.004 | 0.054 | 2.9 | 4/4 | 0.122 |
| M7 | london | c4_fp_5m_cen_against | 66 | 0.328 | 0.024 | 0.305 | 2.9 | 3/4 | 0.198 |
| A7 | london | c4_fp_1m_unf_ahead | 840 | 0.128 | 0.027 | 0.100 | 2.8 | 4/4 | 0.121 |
| A7 | nyam | c4_fp_5m_poc_against | 560 | 0.136 | 0.007 | 0.129 | 2.8 | 4/4 | 0.137 |
| P7 | asia | c4_fp_15m_stack3_with3 | 3823 | 0.081 | 0.027 | 0.054 | 2.7 | 3/4 | 0.107 |
| H7 | pre | c4_fp_3m_poc_with | 100 | 0.197 | -0.147 | 0.345 | 2.7 | 3/4 | 0.416 |
| M7 | london | c4_fp_60m_poc_mig3 | 10783 | 0.048 | -0.028 | 0.076 | 2.7 | 4/4 | 0.102 |
| K7 | close | c4_fp_3m_stack3_against | 79 | 0.240 | -0.019 | 0.259 | 2.7 | 3/4 | 0.444 |
| A7 | london | c4_fp_3m_delta_div_against | 899 | 0.111 | 0.029 | 0.082 | 2.7 | 4/4 | 0.136 |
| M7 | close | c4_fp_mtf_poc_mig1_n | 100 | 0.215 | 0.009 | 0.206 | 2.6 | 4/4 | 0.331 |
| H7 | nyam | c4_fp_1m_delta_with3 | 430 | 0.133 | -0.049 | 0.182 | 2.6 | 3/4 | 0.107 |
| K7 | asia | c4_fp_15m_poc_mig3 | 10154 | 0.044 | 0.009 | 0.034 | 2.6 | 4/4 | 0.099 |
| K7 | asia | c4_fp_mtf_poc_mig1_ge4 | 7708 | 0.049 | 0.016 | 0.033 | 2.6 | 4/4 | 0.091 |
| K7 | close | c4_fp_60m_unf_ahead | 369 | 0.112 | -0.030 | 0.142 | 2.6 | 4/4 | 0.327 |
| P7 | pre | c4_fp_15m_dext_and_close | 408 | 0.165 | 0.005 | 0.160 | 2.6 | 3/4 | 0.482 |
| M7 | london | c4_fp_15m_poc_mig_all3 | 3497 | 0.069 | 0.012 | 0.057 | 2.6 | 4/4 | 0.060 |
| K7 | asia | c4_fp_15m_stack3_with3 | 2503 | 0.079 | 0.023 | 0.056 | 2.6 | 4/4 | 0.011 |
| K7 | asia | c4_fp_5m_poc_with_2of3 | 3572 | 0.063 | 0.023 | 0.040 | 2.5 | 3/4 | 0.056 |

## B10 geometry and chart patterns

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 915; |t|>2: 0 (chance expectation ~41 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_geom.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_tl_state_3m_fresh5 | 36735 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_fresh1 | 12021 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_side | 89852 | 0.47 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_against | 12075 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_hold3 | 71891 | 0.38 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_fresh5 | 36735 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_fresh1 | 12021 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_side | 12021 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_against | 4361 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_fresh5 | 29160 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_fresh1 | 9767 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_side | 9767 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_against | 5972 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_hold3 | 1104 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_touch3_3m_hi | 32823 | 0.17 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_touch3_3m_rise | 17570 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_hi | 42818 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_hi_z1 | 31226 | 0.51 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_lo_z1 | 5539 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_rise | 32916 | 0.54 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_side | 52222 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_rise | 40598 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_fresh5 | 19298 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chan_pos_3m_side | 52928 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chan_pos_3m_rise | 57342 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_tl_state_3m_fresh5 | 36735 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_fresh1 | 12021 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_side | 89852 | 0.47 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_against | 12075 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_hold3 | 71891 | 0.38 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_fresh5 | 36735 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_fresh1 | 12021 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_side | 12021 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_against | 4361 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_fresh5 | 29160 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_fresh1 | 9767 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_side | 9767 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_against | 5972 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_hold3 | 1104 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_touch3_3m_hi | 32823 | 0.17 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_touch3_3m_rise | 17570 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_hi | 42818 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_hi_z1 | 31226 | 0.51 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_lo_z1 | 5539 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_rise | 32916 | 0.54 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_side | 52222 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_rise | 40598 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_fresh5 | 19298 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chan_pos_3m_side | 52928 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chan_pos_3m_rise | 57342 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 57 of 4250 session-condition cells pass (chance-level expectation under independence ~52 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_lmw_tri_15m_hold3 | 443 | 0.364 | 0.076 | 3.7 | 4/4 | 0.692 |
| close | c4_tl_dist_up_60m_lo_z1 | 111 | 0.297 | 0.072 | 3.3 | 4/4 | 0.327 |
| close | c4_chan_posS_5m_fresh5 | 2972 | 0.100 | 0.068 | 2.9 | 4/4 | 0.020 |
| close | c4_tl_retestS_5m_fresh1 | 528 | 0.147 | 0.068 | 2.7 | 4/4 | 0.220 |
| close | c4_tl_retestS_5m_side | 528 | 0.147 | 0.068 | 2.7 | 4/4 | 0.220 |
| close | c4_flag_15m_against | 1075 | 0.152 | 0.066 | 2.7 | 4/4 | 0.125 |
| london | c4_pennant_60m_fresh5 | 942 | -0.310 | -0.088 | -3.9 | 0/4 | -0.337 |
| london | c4_chan_posS_15m_eenter | 3842 | -0.142 | -0.087 | -3.6 | 0/4 | -0.203 |
| london | c4_wedge_rising_onS_15m_rise | 781 | -0.146 | -0.080 | -3.2 | 0/4 | -0.156 |
| london | c4_pnf_15m_side | 43820 | 0.087 | 0.072 | 3.7 | 4/4 | 0.028 |
| london | c4_pnf_15m_against | 13478 | -0.087 | -0.072 | -3.7 | 0/4 | -0.028 |
| london | c4_chan_posS_15m_ewith | 6422 | -0.114 | -0.068 | -2.8 | 0/4 | -0.114 |
| nyam | c4_wedge_rising_onS_60m_rise | 572 | 0.274 | 0.076 | 3.4 | 4/4 | 0.213 |
| nyam | c4_lmw_rect_15m_fresh5 | 100 | -0.538 | -0.065 | -4.0 | 0/4 | -0.128 |
| nyam | c4_tri_sym_60m_fresh5 | 939 | -0.212 | -0.064 | -2.8 | 0/4 | -0.390 |
| nyam | c4_chan_pos_5m_ewith | 2767 | 0.100 | 0.064 | 2.7 | 4/4 | 0.086 |
| nyam | c4_tl_dist_up_15m_lo_z1 | 264 | -0.239 | -0.062 | -2.8 | 0/4 | -0.342 |
| nyam | c4_chan_pos_3m_ewith | 2642 | 0.086 | 0.061 | 2.7 | 4/4 | 0.166 |
| nypm | c4_kagi_60m_hold3 | 13119 | 0.144 | 0.089 | 3.7 | 4/4 | 0.246 |
| nypm | c4_tl_stateS_60m_hold3 | 5321 | 0.154 | 0.087 | 3.5 | 4/4 | 0.301 |
| nypm | c4_tl_slope_upS_60m_side | 3801 | 0.188 | 0.086 | 3.5 | 4/4 | 0.223 |
| nypm | c4_tl_stateS_60m_side | 6316 | 0.143 | 0.080 | 3.2 | 4/4 | 0.280 |
| nypm | c4_tl_stateS_15m_hold3 | 6955 | 0.133 | 0.073 | 2.9 | 4/4 | 0.072 |
| nypm | c4_fib_clusterS_60m_hi_z1 | 1999 | -0.181 | -0.070 | -2.9 | 0/4 | -0.285 |
| pre | c4_chan_posS_60m_eagainst | 908 | 0.318 | 0.084 | 3.8 | 4/4 | 0.614 |
| pre | c4_fib_cluster_dirS_60m_against | 1062 | 0.217 | 0.067 | 2.9 | 4/4 | 0.204 |
| pre | c4_tl_retest_60m_against | 409 | 0.381 | 0.066 | 3.5 | 4/4 | 0.571 |
| pre | c4_threeline_15m_hold3 | 5551 | 0.157 | 0.064 | 2.6 | 4/4 | 0.439 |
| pre | c4_flag_5m_side | 773 | -0.199 | -0.062 | -2.7 | 0/4 | -0.412 |
| pre | c4_tl_dist_upS_60m_hi_z1 | 1613 | -0.226 | -0.057 | -2.6 | 0/4 | -0.168 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (150 of 18178 cell-conditions pass; chance at t>2.5 alone ~112)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_pnf_60m_fresh1 | 890 | 0.209 | 0.021 | 0.188 | 5.0 | 4/4 | 0.108 |
| A7 | nypm | c4_pennant_15m_side | 73 | 0.547 | -0.017 | 0.564 | 4.6 | 3/3 | 0.548 |
| A7 | nypm | c4_kagi_60m_hold3 | 2470 | 0.097 | -0.174 | 0.271 | 4.5 | 4/4 | 0.399 |
| P7 | asia | c4_pnf_60m_fresh5 | 5243 | 0.125 | 0.009 | 0.115 | 4.2 | 4/4 | 0.036 |
| M7 | pre | c4_chan_posS_60m_eagainst | 272 | 0.354 | -0.043 | 0.398 | 4.2 | 4/4 | 0.669 |
| A7 | london | c4_lmw_broaden_60m_hold3 | 219 | 0.385 | 0.028 | 0.357 | 4.1 | 4/4 | 0.074 |
| M7 | pre | c4_tl_retest_60m_against | 116 | 0.490 | -0.025 | 0.515 | 4.0 | 3/4 | 0.983 |
| K7 | asia | c4_tl_retestS_3m_against | 210 | 0.242 | 0.029 | 0.213 | 4.0 | 4/4 | 0.197 |
| K7 | asia | c4_pnf_60m_fresh5 | 3033 | 0.110 | 0.013 | 0.097 | 3.9 | 4/4 | 0.032 |
| K7 | nypm | c4_chan_posS_15m_eenter | 219 | 0.242 | -0.018 | 0.260 | 3.9 | 4/4 | 0.096 |
| A7 | nypm | c4_tl_slope_upS_60m_side | 839 | 0.210 | -0.064 | 0.274 | 3.9 | 4/4 | 0.372 |
| K7 | asia | c4_kagi_3m_hold3 | 9698 | 0.052 | -0.003 | 0.055 | 3.9 | 4/4 | 0.058 |
| K7 | close | c4_lmw_tri_15m_hold3 | 70 | 0.393 | -0.022 | 0.415 | 3.8 | 4/4 | 0.776 |
| P7 | nyam | c4_wedge_rising_onS_60m_rise | 184 | 0.339 | 0.002 | 0.337 | 3.8 | 4/4 | 0.395 |
| K7 | pre | c4_tl_retestS_60m_against | 79 | 0.385 | -0.045 | 0.430 | 3.8 | 4/4 | 0.492 |
| K7 | asia | c4_pnf_15m_fresh5 | 2726 | 0.112 | 0.015 | 0.097 | 3.7 | 3/4 | 0.157 |
| K7 | asia | c4_pnf_5m_fresh5 | 3674 | 0.079 | 0.017 | 0.061 | 3.7 | 3/4 | 0.012 |
| A7 | nypm | c4_fib_clusterS_15m_lo_z1 | 3439 | 0.027 | -0.207 | 0.234 | 3.6 | 4/4 | 0.354 |
| M7 | nypm | c4_kagi_60m_hold3 | 3505 | 0.089 | -0.074 | 0.162 | 3.6 | 4/4 | 0.381 |
| K7 | pre | c4_tl_retest_60m_against | 100 | 0.352 | -0.048 | 0.400 | 3.6 | 3/4 | 0.392 |
| A7 | nypm | c4_kagi_60m_side | 2961 | 0.053 | -0.175 | 0.228 | 3.6 | 4/4 | 0.316 |
| P7 | nypm | c4_tl_slope_upS_60m_side | 1147 | 0.172 | -0.045 | 0.217 | 3.5 | 4/4 | 0.267 |
| M7 | london | c4_chan_pos_60m_eenter | 1057 | 0.204 | 0.012 | 0.192 | 3.5 | 4/4 | 0.272 |
| A7 | london | c4_pnf_15m_hold3 | 5839 | 0.069 | -0.062 | 0.131 | 3.5 | 4/4 | 0.050 |
| K7 | close | c4_fib_cluster_dirS_60m_hold3 | 90 | 0.312 | -0.022 | 0.335 | 3.5 | 4/4 | 0.104 |
| K7 | asia | c4_pnf_15m_fresh1 | 1053 | 0.139 | 0.024 | 0.115 | 3.5 | 3/4 | 0.151 |
| U7 | nyam | c4_fib_cluster_15m_rise | 208 | 0.242 | -0.022 | 0.265 | 3.4 | 4/4 | 0.386 |
| M7 | london | c4_chan_pos_60m_ewith | 1567 | 0.166 | 0.009 | 0.157 | 3.4 | 4/4 | 0.141 |
| M7 | london | c4_chan_posS_60m_eenter | 796 | 0.231 | 0.014 | 0.217 | 3.4 | 3/4 | 0.238 |
| P7 | nypm | c4_tl_stateS_60m_hold3 | 1605 | 0.125 | -0.049 | 0.174 | 3.3 | 4/4 | 0.333 |

## B4 alternate bars: ha1

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2218; |t|>2: 333 (chance expectation ~100 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha1.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_sebS_ha1_eagainst | 1402 | 0.01 | 0.129 | 0.022 | 0.107 [0.053, 0.161] | 3.9 | 4/4 | 0.090 | 0.043 |
| c4_kerF_dir_ha1_eagainst | 11729 | 0.06 | 0.052 | 0.021 | 0.031 [0.015, 0.046] | 3.8 | 4/4 | 0.037 | 0.082 |
| c4_w1_stochrsi8_ha1_eagainst | 35072 | 0.18 | 0.040 | 0.019 | 0.021 [0.010, 0.033] | 3.7 | 4/4 | 0.035 | 0.040 |
| c4_srsiF_ha1_eagainst | 35072 | 0.18 | 0.040 | 0.019 | 0.021 [0.010, 0.033] | 3.7 | 4/4 | 0.035 | 0.040 |
| c4_fvgS_dsup_ha1_hi | 9093 | 0.80 | 0.072 | -0.067 | 0.138 [0.064, 0.213] | 3.6 | 4/4 | 0.210 | 0.100 |
| c4_w1_ema200_px_ha1_side | 179163 | 0.94 | 0.027 | -0.031 | 0.058 [0.025, 0.090] | 3.5 | 4/4 | 0.142 | 0.202 |
| c4_ichiF_thick_ha1_hi | 56514 | 0.30 | 0.038 | 0.016 | 0.022 [0.009, 0.034] | 3.4 | 4/4 | 0.064 | 0.059 |
| c4_stPS_ha1_hold3 | 157711 | 0.82 | 0.029 | -0.005 | 0.034 [0.014, 0.054] | 3.3 | 4/4 | 0.039 | 0.116 |
| c4_w1_sma200_px_ha1_side | 176906 | 0.92 | 0.027 | -0.023 | 0.050 [0.020, 0.080] | 3.2 | 4/4 | 0.146 | 0.192 |
| c4_w1_ema_stack_slow_ha1_side | 142562 | 0.74 | 0.033 | -0.006 | 0.039 [0.015, 0.063] | 3.2 | 4/4 | 0.083 | 0.136 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_smie_ha1_rise | 143681 | 0.75 | 0.018 | 0.038 | -0.020 [-0.030, -0.010] | -3.9 | 0/4 | -0.030 | -0.046 |
| c4_zlemaF_slope_ha1_side | 148712 | 0.78 | 0.018 | 0.039 | -0.021 [-0.031, -0.010] | -3.8 | 0/4 | -0.031 | -0.041 |
| c4_wt_ha1_rise | 144425 | 0.75 | 0.018 | 0.038 | -0.020 [-0.030, -0.009] | -3.8 | 0/4 | -0.028 | -0.037 |
| c4_w1_vortex7_ha1_side | 150207 | 0.78 | 0.019 | 0.038 | -0.020 [-0.031, -0.009] | -3.6 | 0/4 | -0.037 | -0.063 |
| c4_nweF_ha1_side | 159273 | 0.83 | 0.019 | 0.040 | -0.021 [-0.033, -0.010] | -3.6 | 0/4 | -0.035 | -0.036 |
| c4_elder_impulse_ha1_side | 129508 | 0.68 | 0.017 | 0.034 | -0.017 [-0.026, -0.008] | -3.6 | 0/4 | -0.025 | -0.034 |
| c4_w1_trendcolor_ha1_side | 155819 | 0.81 | 0.019 | 0.039 | -0.020 [-0.031, -0.009] | -3.6 | 0/4 | -0.021 | -0.035 |
| c4_elderF_impulse_ha1_side | 129838 | 0.68 | 0.017 | 0.034 | -0.017 [-0.027, -0.008] | -3.6 | 0/4 | -0.025 | -0.032 |
| c4_w1_ha_run_ha1_side | 160556 | 0.84 | 0.019 | 0.041 | -0.022 [-0.034, -0.010] | -3.5 | 0/4 | -0.028 | -0.039 |
| c4_w1_mfi21_ha1_rise | 133202 | 0.70 | 0.017 | 0.036 | -0.019 [-0.029, -0.008] | -3.5 | 0/4 | -0.029 | -0.039 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 297 of 12789 session-condition cells pass (chance-level expectation under independence ~158 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_fvgS_near_ha1_against | 640 | -0.183 | -0.089 | -3.6 | 0/4 | -0.298 |
| asia | c4_fvgS_dsup_ha1_hi | 5261 | 0.155 | 0.080 | 3.2 | 4/4 | 0.281 |
| asia | c4_fvgS_in_ha1_against | 333 | -0.199 | -0.078 | -3.2 | 0/4 | -0.165 |
| asia | c4_sebS_ha1_eagainst | 391 | 0.131 | 0.078 | 3.2 | 4/4 | 0.159 |
| asia | c4_w1_donchian50_pos_ha1_ewith | 1549 | 0.090 | 0.074 | 3.8 | 4/4 | 0.068 |
| asia | c4_w1_donchian50_pos_ha1_eenter | 1460 | 0.085 | 0.069 | 3.5 | 4/4 | 0.058 |
| close | c4_fvgF_in_ha1_fresh5 | 459 | 0.164 | 0.081 | 3.2 | 4/4 | 0.344 |
| close | c4_kerF_dir_ha1_eagainst | 921 | 0.107 | 0.076 | 3.3 | 4/4 | 0.128 |
| close | c4_w1_cmo9_ha1_eagainst | 312 | 0.149 | 0.074 | 3.0 | 4/4 | 0.286 |
| close | c4_pdS_ha1_fresh5 | 1116 | -0.111 | -0.071 | -2.9 | 0/4 | -0.095 |
| close | c4_elder_bear_ha1_side | 10412 | -0.089 | -0.061 | -2.6 | 0/4 | -0.036 |
| close | c4_w1_boll20_walk_ha1_divwith | 285 | 0.201 | 0.059 | 2.6 | 4/4 | 0.086 |
| london | c4_nweF_ha1_fresh5 | 432 | 0.130 | 0.072 | 2.9 | 4/4 | 0.207 |
| london | c4_w1_kama100_px_ha1_divwith | 1762 | -0.099 | -0.072 | -3.2 | 0/4 | -0.245 |
| london | c4_w1_ema100_px_ha1_divwith | 1548 | -0.103 | -0.071 | -3.1 | 0/4 | -0.266 |
| london | c4_w1_kama50_px_ha1_divwith | 2185 | -0.092 | -0.069 | -3.2 | 0/4 | -0.196 |
| london | c4_w1_sma100_px_ha1_divwith | 1706 | -0.096 | -0.068 | -3.0 | 0/4 | -0.142 |
| london | c4_w1_ema200_px_ha1_divwith | 1584 | -0.096 | -0.067 | -2.9 | 0/4 | -0.170 |
| nyam | c4_sfpS_ha1_fresh5 | 1165 | -0.136 | -0.086 | -3.5 | 0/4 | -0.001 |
| nyam | c4_smiS_ha1_eagainst | 285 | -0.179 | -0.080 | -3.2 | 0/4 | -0.419 |
| nyam | c4_w1_ao_ha1_side | 21715 | 0.103 | 0.077 | 3.6 | 4/4 | 0.193 |
| nyam | c4_alli_spread_ha1_side | 20575 | 0.094 | 0.075 | 3.8 | 4/4 | 0.148 |
| nyam | c4_w1_pat_pin_ha1_side | 211 | 0.209 | 0.072 | 3.0 | 4/4 | 0.115 |
| nyam | c4_seb_ha1_ewith | 5217 | -0.079 | -0.070 | -4.3 | 0/4 | -0.004 |
| nypm | c4_sqzmF_on_ha1_rise | 817 | -0.096 | -0.068 | -3.0 | 0/4 | -0.141 |
| nypm | c4_ob_dsup_ha1_hi | 4102 | 0.097 | 0.067 | 2.9 | 4/4 | 0.054 |
| nypm | c4_w1_kama34_px_ha1_side | 23072 | -0.093 | -0.067 | -3.0 | 0/4 | -0.087 |
| nypm | c4_chochS_ha1_side | 21365 | -0.075 | -0.057 | -2.6 | 0/4 | -0.113 |
| nypm | c4_structS_ha1_side | 21365 | -0.075 | -0.057 | -2.6 | 0/4 | -0.113 |
| nypm | c4_structS_ha1_against | 3551 | 0.075 | 0.057 | 2.6 | 4/4 | 0.113 |
| pre | c4_w1_mfi21_ha1_side | 7939 | -0.129 | -0.076 | -3.1 | 0/4 | -0.116 |
| pre | c4_elder_impulse_ha1_against | 699 | 0.126 | 0.071 | 2.8 | 4/4 | 0.123 |
| pre | c4_sdS_in_ha1_fresh5 | 701 | 0.140 | 0.069 | 2.8 | 4/4 | 0.140 |
| pre | c4_w1_kama100_px_ha1_side | 8848 | -0.204 | -0.068 | -2.9 | 0/4 | -0.343 |
| pre | c4_ker_dir_ha1_side | 7446 | -0.093 | -0.068 | -3.1 | 0/4 | -0.007 |
| pre | c4_w1_roc10_ha1_side | 7446 | -0.093 | -0.068 | -3.1 | 0/4 | -0.007 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (327 of 60425 cell-conditions pass; chance at t>2.5 alone ~374)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| M7 | london | c4_w1_vwma200_px_ha1_side | 15340 | 0.030 | -0.495 | 0.525 | 7.4 | 4/4 | 0.613 |
| K7 | asia | c4_w1_ema_stack_slow_ha1_side | 8070 | 0.074 | -0.015 | 0.089 | 4.9 | 4/4 | 0.143 |
| K7 | asia | c4_w1_ema_stack_slow_ha1_hold3 | 7778 | 0.074 | -0.011 | 0.086 | 4.9 | 4/4 | 0.129 |
| K7 | nyam | c4_sdF_dsup_ha1_hi | 263 | 0.271 | 0.008 | 0.263 | 4.7 | 4/4 | 0.104 |
| K7 | asia | c4_turt55_ha1_hold3 | 7055 | 0.067 | 0.002 | 0.064 | 4.3 | 4/4 | 0.046 |
| K7 | asia | c4_w1_sma200_px_ha1_side | 12342 | 0.048 | -0.034 | 0.082 | 4.1 | 4/4 | 0.142 |
| K7 | asia | c4_obF_cnt_ha1_side | 9991 | 0.059 | -0.019 | 0.079 | 4.1 | 4/4 | 0.173 |
| K7 | asia | c4_tsiS_ha1_ewith | 2167 | 0.098 | 0.021 | 0.077 | 4.0 | 4/4 | 0.097 |
| K7 | asia | c4_sdF_cnt_ha1_side | 10045 | 0.059 | -0.020 | 0.079 | 4.0 | 4/4 | 0.175 |
| K7 | asia | c4_w1_ema200_px_ha1_side | 12669 | 0.046 | -0.034 | 0.080 | 3.9 | 4/4 | 0.119 |
| P7 | pre | c4_w1_aroon50_ha1_eagainst | 81 | 0.406 | 0.017 | 0.389 | 3.7 | 4/4 | 0.820 |
| K7 | asia | c4_ob_cnt_ha1_side | 9903 | 0.057 | -0.013 | 0.069 | 3.7 | 4/4 | 0.167 |
| M7 | london | c4_w1_willr21_ha1_eleave | 664 | 0.148 | 0.020 | 0.128 | 3.7 | 4/4 | 0.073 |
| K7 | nyam | c4_sd_dsup_ha1_hi | 657 | 0.139 | -0.000 | 0.139 | 3.7 | 4/4 | 0.199 |
| K7 | asia | c4_fvgS_dsup_ha1_rise | 843 | 0.105 | -0.065 | 0.170 | 3.6 | 4/4 | 0.041 |
| A7 | london | c4_chochS_ha1_fresh5 | 275 | 0.206 | 0.032 | 0.174 | 3.6 | 4/4 | 0.250 |
| P7 | nyam | c4_smiS_ha1_side | 5434 | 0.038 | -0.066 | 0.104 | 3.6 | 4/4 | 0.201 |
| K7 | asia | c4_stPS_ha1_hold3 | 10059 | 0.050 | -0.003 | 0.053 | 3.6 | 3/4 | 0.057 |
| K7 | asia | c4_obS_cnt_ha1_side | 9707 | 0.058 | -0.012 | 0.070 | 3.5 | 4/4 | 0.148 |
| M7 | london | c4_w1_stoch8_ha1_eleave | 844 | 0.124 | 0.019 | 0.104 | 3.5 | 4/4 | 0.113 |
| K7 | asia | c4_w1_sma_stack_slow_ha1_side | 6295 | 0.068 | 0.007 | 0.062 | 3.5 | 4/4 | 0.103 |
| K7 | asia | c4_ichiF_thick_ha1_hi | 3949 | 0.067 | 0.020 | 0.047 | 3.5 | 3/4 | 0.155 |
| H7 | close | c4_pd_ha1_eagainst | 234 | 0.100 | -0.257 | 0.357 | 3.5 | 4/4 | 0.366 |
| K7 | asia | c4_stPS_ha1_side | 11514 | 0.046 | -0.009 | 0.055 | 3.5 | 3/4 | 0.081 |
| P7 | london | c4_w1_sqz_hist_ha1_fresh5 | 2812 | 0.067 | 0.010 | 0.057 | 3.4 | 4/4 | 0.080 |
| M7 | london | c4_smi_ha1_eagainst | 756 | 0.129 | 0.020 | 0.110 | 3.4 | 4/4 | 0.124 |
| M7 | nyam | c4_srsiF_ha1_eagainst | 1201 | 0.107 | 0.012 | 0.094 | 3.4 | 4/4 | 0.039 |
| M7 | nyam | c4_w1_stochrsi8_ha1_eagainst | 1201 | 0.107 | 0.012 | 0.094 | 3.4 | 4/4 | 0.039 |
| K7 | asia | c4_fvg_dres_ha1_hi | 3106 | 0.072 | -0.006 | 0.078 | 3.4 | 4/4 | 0.066 |
| M7 | close | c4_lrcS_slope_ha1_fresh5 | 93 | 0.295 | 0.007 | 0.288 | 3.4 | 4/4 | 0.223 |

## B4 alternate bars: ha15

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2267; |t|>2: 525 (chance expectation ~103 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha15.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_fvg_cnt_ha15_side | 66009 | 0.34 | 0.073 | -0.004 | 0.077 [0.046, 0.109] | 4.8 | 4/4 | 0.148 | 0.107 |
| c4_qqeS_ha15_ewith | 22296 | 0.12 | 0.113 | 0.011 | 0.102 [0.057, 0.148] | 4.4 | 4/4 | 0.132 | 0.140 |
| c4_qqeS_ha15_eenter | 4574 | 0.02 | 0.159 | 0.019 | 0.139 [0.075, 0.203] | 4.3 | 4/4 | 0.132 | 0.131 |
| c4_mcmf_ha15_side | 115429 | 0.60 | 0.046 | -0.013 | 0.059 [0.029, 0.089] | 3.9 | 4/4 | 0.096 | 0.109 |
| c4_w1_demarker14_ha15_side | 140673 | 0.73 | 0.036 | -0.014 | 0.050 [0.024, 0.075] | 3.9 | 4/4 | 0.139 | 0.189 |
| c4_mc_comp2_ha15_side | 146361 | 0.77 | 0.034 | -0.014 | 0.047 [0.023, 0.072] | 3.8 | 4/4 | 0.078 | 0.127 |
| c4_rfiltF_ha15_side | 155907 | 0.81 | 0.032 | -0.016 | 0.047 [0.022, 0.072] | 3.7 | 4/4 | 0.059 | 0.118 |
| c4_krF_px_ha15_side | 154609 | 0.81 | 0.032 | -0.017 | 0.049 [0.023, 0.075] | 3.7 | 4/4 | 0.089 | 0.149 |
| c4_fvgF_cnt_ha15_side | 84504 | 0.44 | 0.058 | -0.005 | 0.062 [0.029, 0.096] | 3.7 | 4/4 | 0.051 | 0.056 |
| c4_w1_cmo14_ha15_side | 145210 | 0.76 | 0.034 | -0.013 | 0.047 [0.022, 0.072] | 3.7 | 4/4 | 0.122 | 0.196 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_ichiF_chikou_ha15_against | 45307 | 0.24 | -0.013 | 0.034 | -0.047 [-0.073, -0.022] | -3.6 | 0/4 | -0.128 | -0.205 |
| c4_kerF_dir_ha15_rise | 106979 | 0.56 | 0.011 | 0.038 | -0.027 [-0.041, -0.012] | -3.5 | 0/4 | -0.055 | -0.043 |
| c4_w1_demarker14_ha15_eagainst | 14183 | 0.07 | -0.026 | 0.027 | -0.053 [-0.084, -0.022] | -3.4 | 0/4 | -0.140 | -0.158 |
| c4_crsi_ha15_fresh5 | 152752 | 0.80 | 0.016 | 0.052 | -0.036 [-0.057, -0.014] | -3.3 | 1/4 | -0.032 | -0.016 |
| c4_w1_rsi21_ha15_eagainst | 3846 | 0.02 | -0.065 | 0.025 | -0.090 [-0.144, -0.036] | -3.3 | 0/4 | -0.180 | -0.197 |
| c4_sdS_near_ha15_hold3 | 19611 | 0.10 | -0.035 | 0.029 | -0.064 [-0.103, -0.025] | -3.2 | 0/4 | -0.133 | -0.094 |
| c4_stPF_ha15_against | 70487 | 0.37 | -0.007 | 0.040 | -0.047 [-0.076, -0.019] | -3.2 | 0/4 | -0.093 | -0.081 |
| c4_w1_kama100_px_ha15_rise | 134578 | 0.71 | 0.015 | 0.043 | -0.028 [-0.045, -0.011] | -3.2 | 0/4 | -0.050 | -0.080 |
| c4_fractal_alli_ha15_against | 31758 | 0.17 | -0.016 | 0.030 | -0.046 [-0.074, -0.018] | -3.2 | 0/4 | -0.106 | -0.142 |
| c4_w1_rsi14_ha15_eagainst | 4539 | 0.02 | -0.053 | 0.025 | -0.077 [-0.124, -0.030] | -3.2 | 0/4 | -0.173 | -0.197 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 325 of 13214 session-condition cells pass (chance-level expectation under independence ~163 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_w1_keltner10_pos_ha15_ewith | 5335 | 0.124 | 0.089 | 4.0 | 4/4 | 0.075 |
| asia | c4_w1_keltner20_pos_ha15_ewith | 5612 | 0.133 | 0.088 | 3.7 | 4/4 | 0.084 |
| asia | c4_qqeS_ha15_ewith | 6648 | 0.127 | 0.085 | 3.6 | 4/4 | 0.120 |
| asia | c4_lrcF_ha15_ewith | 3343 | 0.144 | 0.084 | 3.4 | 4/4 | 0.168 |
| asia | c4_mcgS_px_ha15_side | 44627 | 0.093 | 0.079 | 4.4 | 4/4 | 0.175 |
| asia | c4_mcgS_slope_ha15_side | 44627 | 0.093 | 0.079 | 4.4 | 4/4 | 0.175 |
| close | c4_w1_demarker7_ha15_eenter | 3168 | 0.143 | 0.097 | 4.1 | 4/4 | 0.215 |
| close | c4_w1_donchian10_width_ha15_hi | 10413 | -0.133 | -0.078 | -3.1 | 0/4 | -0.070 |
| close | c4_sqzmF_on_ha15_hi | 10080 | 0.126 | 0.077 | 3.2 | 4/4 | 0.058 |
| close | c4_kerF_dir_ha15_eenter | 3780 | 0.098 | 0.071 | 3.2 | 4/4 | 0.047 |
| close | c4_sdF_dres_ha15_hi | 935 | -0.205 | -0.069 | -2.9 | 0/4 | -0.400 |
| close | c4_w1_linreg_chan50_ha15_fresh5 | 4175 | 0.105 | 0.069 | 2.9 | 4/4 | 0.165 |
| london | c4_nwe_ha15_fresh5 | 361 | 0.373 | 0.079 | 3.9 | 4/4 | 0.181 |
| london | c4_fvg_in_ha15_fresh5 | 433 | -0.348 | -0.074 | -3.6 | 0/4 | -0.072 |
| london | c4_rfiltF_ha15_side | 47197 | 0.090 | 0.074 | 3.8 | 4/4 | 0.127 |
| london | c4_zlema_px_ha15_nodiv | 44857 | -0.092 | -0.068 | -3.1 | 0/4 | -0.059 |
| london | c4_nweS_ha15_eleave | 144 | 0.439 | 0.067 | 3.7 | 4/4 | 0.146 |
| london | c4_chand_ha15_fresh1 | 1848 | -0.101 | -0.067 | -2.8 | 0/4 | -0.221 |
| nyam | c4_fvg_cnt_ha15_side | 9218 | 0.154 | 0.106 | 4.6 | 4/4 | 0.191 |
| nyam | c4_w1_pat_pin_ha15_fresh5 | 1730 | -0.160 | -0.079 | -3.2 | 0/4 | -0.039 |
| nyam | c4_fvg_dsup_ha15_hi | 6325 | 0.133 | 0.073 | 2.9 | 4/4 | 0.139 |
| nyam | c4_sdflipS_in_ha15_side | 1469 | -0.133 | -0.070 | -2.8 | 0/4 | -0.116 |
| nyam | c4_brkF_near_ha15_hold3 | 2810 | -0.110 | -0.069 | -2.8 | 0/4 | -0.112 |
| nyam | c4_w1_di21_ha15_nodiv | 21057 | 0.119 | 0.067 | 2.7 | 4/4 | 0.200 |
| nypm | c4_fvg_cnt_ha15_side | 9829 | 0.160 | 0.094 | 3.8 | 4/4 | 0.425 |
| nypm | c4_w1_aroon50_ha15_ewith | 5270 | 0.163 | 0.090 | 3.6 | 4/4 | 0.160 |
| nypm | c4_w1_sma200_px_ha15_fresh5 | 2524 | -0.186 | -0.088 | -3.5 | 0/4 | -0.278 |
| nypm | c4_w1_trix30_ha15_side | 14741 | 0.133 | 0.085 | 3.6 | 4/4 | 0.232 |
| nypm | c4_lrc_slope_ha15_side | 14436 | 0.122 | 0.081 | 3.4 | 4/4 | 0.281 |
| nypm | c4_sdflipF_in_ha15_against | 8100 | -0.116 | -0.079 | -3.4 | 0/4 | -0.102 |
| pre | c4_sdS_cnt_ha15_rise | 1145 | -0.176 | -0.080 | -3.2 | 0/4 | -0.391 |
| pre | c4_obS_cnt_ha15_rise | 989 | -0.181 | -0.071 | -2.9 | 0/4 | -0.173 |
| pre | c4_smie_ha15_eenter | 1285 | -0.210 | -0.068 | -2.9 | 0/4 | -0.645 |
| pre | c4_w1_demarker7_ha15_fresh5 | 3796 | -0.130 | -0.064 | -2.6 | 0/4 | -0.175 |
| pre | c4_w1_cci20_ha15_ewith_z2 | 1157 | -0.189 | -0.062 | -2.7 | 0/4 | -0.624 |
| pre | c4_chochS_ha15_fresh1 | 333 | -0.312 | -0.061 | -3.1 | 0/4 | -0.466 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (973 of 67828 cell-conditions pass; chance at t>2.5 alone ~420)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_mfi7_ha15_side | 8819 | 0.064 | -0.011 | 0.076 | 5.1 | 4/4 | 0.152 |
| A7 | nyam | c4_fvg_cnt_ha15_side | 1580 | 0.193 | -0.099 | 0.292 | 5.0 | 4/4 | 0.381 |
| P7 | nypm | c4_w1_supertrend_14_4_ha15_nodiv | 8046 | -0.010 | -0.558 | 0.548 | 4.9 | 4/4 | 0.558 |
| K7 | asia | c4_w1_mfi14_ha15_side | 8368 | 0.074 | -0.018 | 0.091 | 4.9 | 4/4 | 0.218 |
| K7 | asia | c4_chandF_ha15_side | 8543 | 0.073 | -0.020 | 0.093 | 4.8 | 4/4 | 0.140 |
| P7 | london | c4_nweS_ha15_fresh5 | 95 | 0.561 | 0.012 | 0.549 | 4.8 | 4/4 | 0.391 |
| A7 | nypm | c4_w1_trix30_ha15_side | 2735 | 0.079 | -0.189 | 0.268 | 4.7 | 4/4 | 0.455 |
| K7 | asia | c4_krF_px_ha15_side | 9266 | 0.068 | -0.024 | 0.092 | 4.6 | 4/4 | 0.156 |
| K7 | asia | c4_rfiltS_ha15_side | 8969 | 0.073 | -0.026 | 0.099 | 4.6 | 4/4 | 0.101 |
| K7 | asia | c4_w1_vortex14_ha15_side | 8726 | 0.070 | -0.018 | 0.088 | 4.6 | 4/4 | 0.171 |
| K7 | asia | c4_w1_di7_ha15_side | 9295 | 0.065 | -0.019 | 0.084 | 4.6 | 4/4 | 0.164 |
| K7 | asia | c4_ichiF_score_ha15_side | 8548 | 0.069 | -0.015 | 0.084 | 4.6 | 4/4 | 0.167 |
| K7 | asia | c4_krF_dir_ha15_side | 9422 | 0.065 | -0.021 | 0.086 | 4.6 | 4/4 | 0.167 |
| K7 | asia | c4_w1_keltner10_pos_ha15_side | 9931 | 0.060 | -0.019 | 0.079 | 4.6 | 4/4 | 0.154 |
| K7 | asia | c4_qqeF_ha15_side | 9017 | 0.067 | -0.018 | 0.085 | 4.5 | 4/4 | 0.165 |
| K7 | asia | c4_mcg_slope_ha15_side | 9438 | 0.066 | -0.022 | 0.087 | 4.5 | 4/4 | 0.166 |
| K7 | asia | c4_mcg_px_ha15_side | 9438 | 0.066 | -0.022 | 0.087 | 4.5 | 4/4 | 0.166 |
| K7 | asia | c4_mcgS_px_ha15_side | 8755 | 0.075 | -0.025 | 0.099 | 4.5 | 4/4 | 0.207 |
| K7 | asia | c4_mcgS_slope_ha15_side | 8755 | 0.075 | -0.025 | 0.099 | 4.5 | 4/4 | 0.207 |
| K7 | asia | c4_smieF_ha15_side | 9224 | 0.064 | -0.016 | 0.080 | 4.5 | 4/4 | 0.142 |
| K7 | asia | c4_w1_eom14_ha15_side | 8841 | 0.069 | -0.018 | 0.087 | 4.5 | 4/4 | 0.136 |
| K7 | asia | c4_wtS_ha15_ewith_z1 | 678 | 0.212 | 0.024 | 0.188 | 4.5 | 4/4 | 0.161 |
| K7 | asia | c4_w1_keltner20_pos_ha15_side | 9174 | 0.067 | -0.020 | 0.088 | 4.5 | 4/4 | 0.167 |
| K7 | asia | c4_nweS_ha15_side | 8697 | 0.069 | -0.024 | 0.093 | 4.5 | 4/4 | 0.179 |
| K7 | asia | c4_tsiF_ha15_side | 8534 | 0.070 | -0.016 | 0.086 | 4.5 | 4/4 | 0.158 |
| K7 | asia | c4_w1_keltner10_pos_ha15_ewith | 727 | 0.204 | 0.024 | 0.181 | 4.4 | 4/4 | 0.173 |
| K7 | asia | c4_w1_keltner20_pos_ha15_ewith | 817 | 0.210 | 0.022 | 0.188 | 4.4 | 4/4 | 0.197 |
| K7 | asia | c4_elderS_bull_ha15_side | 8740 | 0.071 | -0.020 | 0.091 | 4.4 | 4/4 | 0.173 |
| K7 | asia | c4_w1_rsi14_ha15_ewith | 1875 | 0.141 | 0.017 | 0.124 | 4.4 | 3/4 | 0.118 |
| K7 | asia | c4_w1_ema34_px_ha15_side | 8744 | 0.074 | -0.024 | 0.098 | 4.4 | 4/4 | 0.202 |

## B4 alternate bars: ha3

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2229; |t|>2: 0 (chance expectation ~101 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha3.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha3_side | 165507 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_sig | 133743 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_rise | 135539 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_fresh5 | 83756 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_ewith_z1 | 25039 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eleave_z1 | 961 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eenter_z1 | 8499 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_ewith_z2 | 49097 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eagainst_z2 | 296 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eleave_z2 | 2120 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha3_side | 165507 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_sig | 133743 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_rise | 135539 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_fresh5 | 83756 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_ewith_z1 | 25039 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eleave_z1 | 961 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eenter_z1 | 8499 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_ewith_z2 | 49097 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eagainst_z2 | 296 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eleave_z2 | 2120 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 76 of 12864 session-condition cells pass (chance-level expectation under independence ~159 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_w1_vwma100_px_ha3_divwith | 868 | 0.184 | 0.082 | 3.3 | 4/4 | 0.351 |
| close | c4_w1_sma100_px_ha3_divwith | 726 | 0.193 | 0.074 | 3.0 | 4/4 | 0.333 |
| close | c4_pdS_ha3_side | 1870 | -0.130 | -0.070 | -2.8 | 0/4 | -0.260 |
| close | c4_chand_ha3_side | 11637 | 0.120 | 0.069 | 2.8 | 4/4 | 0.312 |
| close | c4_chand_ha3_against | 2161 | -0.120 | -0.069 | -2.8 | 0/4 | -0.312 |
| close | c4_w1_hma200_px_ha3_divwith | 657 | 0.160 | 0.068 | 2.7 | 4/4 | 0.098 |
| nyam | c4_w1_mfi21_ha3_ewith | 2304 | 0.132 | 0.082 | 3.4 | 4/4 | 0.126 |
| nyam | c4_w1_obv_ha3_side | 21890 | 0.109 | 0.079 | 3.5 | 4/4 | 0.073 |
| nyam | c4_w1_aroon50_ha3_divwith | 2048 | 0.132 | 0.073 | 2.9 | 4/4 | 0.189 |
| nyam | c4_w1_mfi14_ha3_ewith | 3957 | 0.091 | 0.068 | 3.1 | 4/4 | 0.115 |
| nyam | c4_ote_wideF_ha3_side | 877 | -0.111 | -0.068 | -2.8 | 0/4 | -0.128 |
| nyam | c4_w1_mfi21_ha3_eenter | 1172 | 0.112 | 0.065 | 2.6 | 4/4 | 0.145 |
| nypm | c4_obF_cnt_ha3_fresh5 | 1081 | -0.130 | -0.072 | -2.9 | 0/4 | -0.197 |
| nypm | c4_elder_bull_ha3_divwith | 1845 | 0.112 | 0.062 | 2.5 | 4/4 | 0.059 |
| nypm | c4_elderF_bull_ha3_divwith | 2361 | 0.100 | 0.062 | 2.6 | 4/4 | 0.024 |
| nypm | c4_w1_ichi_slow_lag_ha3_divwith | 708 | 0.166 | 0.062 | 2.6 | 4/4 | 0.175 |
| nypm | c4_mcmf_ha3_rise | 16141 | -0.051 | -0.045 | -2.7 | 0/4 | -0.034 |
| nypm | c4_w1_fisher5_ha3_fresh5 | 7774 | -0.049 | -0.043 | -2.6 | 0/4 | -0.042 |
| pre | c4_ote_wide_ha3_side | 236 | 0.247 | 0.075 | 3.3 | 4/4 | 0.611 |
| pre | c4_qqemod_ha3_against | 536 | 0.165 | 0.075 | 3.0 | 4/4 | 0.314 |
| pre | c4_sqzm_bright_ha3_against | 463 | 0.182 | 0.074 | 3.0 | 4/4 | 0.353 |
| pre | c4_rsima21_ha3_eenter | 650 | -0.154 | -0.073 | -2.9 | 0/4 | -0.158 |
| pre | c4_w1_rsi21_ha3_eenter | 650 | -0.154 | -0.073 | -2.9 | 0/4 | -0.158 |
| pre | c4_kstF_ha3_side | 7754 | -0.117 | -0.071 | -2.9 | 0/4 | -0.333 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (533 of 62276 cell-conditions pass; chance at t>2.5 alone ~386)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_ema21_hold_ha3_hold3 | 4474 | 0.088 | 0.009 | 0.079 | 5.5 | 4/4 | 0.087 |
| K7 | asia | c4_w1_ema21_hold_ha3_side | 6210 | 0.073 | 0.004 | 0.069 | 5.4 | 4/4 | 0.070 |
| K7 | asia | c4_qqeS_ha3_ewith | 732 | 0.199 | 0.024 | 0.175 | 4.9 | 4/4 | 0.203 |
| K7 | asia | c4_smie_ha3_ewith | 5122 | 0.077 | 0.010 | 0.067 | 4.8 | 4/4 | 0.085 |
| K7 | asia | c4_kerS_abs_ha3_hi | 4726 | 0.081 | 0.010 | 0.071 | 4.7 | 4/4 | 0.035 |
| K7 | asia | c4_tsi_ha3_ewith | 4150 | 0.092 | 0.010 | 0.081 | 4.5 | 4/4 | 0.102 |
| A7 | close | c4_stc_ha3_divwith | 72 | 0.495 | -0.051 | 0.546 | 4.5 | 3/4 | 0.763 |
| K7 | asia | c4_ichi_cloud_ha3_hold3 | 7934 | 0.068 | -0.007 | 0.075 | 4.4 | 4/4 | 0.066 |
| K7 | asia | c4_qqeS_ha3_side | 10867 | 0.055 | -0.024 | 0.079 | 4.3 | 4/4 | 0.128 |
| K7 | asia | c4_w1_ema100_px_ha3_side | 10892 | 0.057 | -0.030 | 0.088 | 4.3 | 4/4 | 0.157 |
| K7 | asia | c4_smieS_ha3_ewith | 2690 | 0.104 | 0.017 | 0.088 | 4.3 | 4/4 | 0.073 |
| K7 | asia | c4_tsiS_ha3_ewith | 2582 | 0.111 | 0.016 | 0.095 | 4.3 | 4/4 | 0.040 |
| K7 | asia | c4_chandS_ha3_hold3 | 8784 | 0.066 | -0.014 | 0.080 | 4.2 | 4/4 | 0.125 |
| K7 | asia | c4_rfilt_dir_ha3_side | 9633 | 0.061 | -0.018 | 0.079 | 4.2 | 4/4 | 0.066 |
| K7 | asia | c4_turt20_ha3_hold3 | 7221 | 0.069 | -0.001 | 0.070 | 4.2 | 3/4 | 0.105 |
| K7 | asia | c4_w1_ema50_px_ha3_side | 13031 | 0.046 | -0.045 | 0.091 | 4.2 | 4/4 | 0.142 |
| K7 | asia | c4_kerS_dir_ha3_ewith | 1184 | 0.130 | 0.024 | 0.106 | 4.2 | 4/4 | 0.150 |
| P7 | pre | c4_w1_cmf20_ha3_fresh5 | 387 | 0.241 | -0.006 | 0.247 | 4.1 | 4/4 | 0.476 |
| K7 | asia | c4_stP_ha3_side | 9054 | 0.064 | -0.014 | 0.079 | 4.1 | 4/4 | 0.162 |
| K7 | asia | c4_qqe_ha3_ewith | 1530 | 0.126 | 0.022 | 0.104 | 4.1 | 4/4 | 0.088 |
| K7 | asia | c4_w1_trix30_ha3_side | 8416 | 0.069 | -0.013 | 0.082 | 4.1 | 4/4 | 0.140 |
| K7 | asia | c4_w1_ema200_px_ha3_side | 9448 | 0.067 | -0.025 | 0.093 | 4.1 | 4/4 | 0.199 |
| K7 | asia | c4_chandS_ha3_side | 9315 | 0.063 | -0.015 | 0.078 | 4.1 | 4/4 | 0.110 |
| K7 | asia | c4_w1_macd19_39_9_line_ha3_side | 9833 | 0.057 | -0.013 | 0.070 | 4.0 | 4/4 | 0.122 |
| P7 | asia | c4_w1_ema100_px_ha3_side | 18968 | 0.051 | -0.046 | 0.097 | 4.0 | 4/4 | 0.143 |
| K7 | asia | c4_kerF_dir_ha3_eagainst | 65 | 0.371 | 0.031 | 0.341 | 4.0 | 4/4 | 0.330 |
| K7 | asia | c4_qqeF_ha3_ewith | 5147 | 0.066 | 0.015 | 0.051 | 4.0 | 3/4 | 0.023 |
| K7 | asia | c4_tsiF_ha3_ewith | 8032 | 0.056 | 0.006 | 0.050 | 4.0 | 3/4 | 0.052 |
| K7 | asia | c4_stP_ha3_hold3 | 8780 | 0.065 | -0.012 | 0.076 | 4.0 | 4/4 | 0.147 |
| K7 | asia | c4_turt55_ha3_hold3 | 5400 | 0.081 | 0.006 | 0.075 | 4.0 | 4/4 | 0.140 |

## B4 alternate bars: ha5

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2249; |t|>2: 404 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha5.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_rfilt_dir_ha5_side | 152916 | 0.80 | 0.035 | -0.025 | 0.060 [0.034, 0.087] | 4.5 | 4/4 | -0.005 | 0.033 |
| c4_w1_vwma50_px_ha5_side | 166972 | 0.87 | 0.030 | -0.025 | 0.054 [0.029, 0.079] | 4.3 | 4/4 | 0.104 | 0.164 |
| c4_w1_ema50_px_ha5_side | 166946 | 0.87 | 0.030 | -0.027 | 0.057 [0.030, 0.084] | 4.2 | 4/4 | 0.113 | 0.167 |
| c4_stPS_ha5_side | 126917 | 0.66 | 0.042 | -0.015 | 0.057 [0.030, 0.085] | 4.1 | 4/4 | 0.114 | 0.135 |
| c4_stPS_ha5_hold3 | 123277 | 0.64 | 0.043 | -0.014 | 0.057 [0.030, 0.084] | 4.1 | 4/4 | 0.114 | 0.132 |
| c4_rfilt_dir_ha5_hold3 | 142653 | 0.74 | 0.036 | -0.017 | 0.053 [0.027, 0.079] | 4.0 | 4/4 | -0.014 | 0.031 |
| c4_w1_donchian50_pos_ha5_side | 164377 | 0.86 | 0.030 | -0.024 | 0.054 [0.027, 0.081] | 4.0 | 4/4 | 0.092 | 0.156 |
| c4_w1_sma50_px_ha5_side | 166461 | 0.87 | 0.029 | -0.022 | 0.051 [0.026, 0.077] | 4.0 | 4/4 | 0.126 | 0.183 |
| c4_w1_rsi21_ha5_side | 169287 | 0.88 | 0.029 | -0.024 | 0.053 [0.026, 0.080] | 3.9 | 4/4 | 0.116 | 0.163 |
| c4_w1_mfi21_ha5_ewith | 17015 | 0.09 | 0.081 | 0.017 | 0.064 [0.032, 0.096] | 3.9 | 4/4 | 0.098 | 0.088 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_rfilt_dir_ha5_against | 38602 | 0.20 | -0.025 | 0.035 | -0.060 [-0.087, -0.034] | -4.5 | 0/4 | 0.005 | -0.033 |
| c4_stPS_ha5_against | 64597 | 0.34 | -0.015 | 0.042 | -0.057 [-0.085, -0.030] | -4.1 | 0/4 | -0.114 | -0.135 |
| c4_ob_in_ha5_fresh1 | 1854 | 0.01 | -0.083 | 0.024 | -0.107 [-0.158, -0.056] | -4.1 | 0/4 | -0.275 | -0.268 |
| c4_almaS_slope_ha5_rise | 126551 | 0.66 | 0.015 | 0.039 | -0.024 [-0.037, -0.011] | -3.5 | 0/4 | -0.031 | -0.044 |
| c4_w1_mfi14_ha5_rise | 112670 | 0.59 | 0.015 | 0.034 | -0.020 [-0.031, -0.008] | -3.5 | 0/4 | -0.039 | -0.057 |
| c4_tsiS_ha5_eenter | 7436 | 0.04 | -0.030 | 0.025 | -0.055 [-0.086, -0.024] | -3.4 | 0/4 | -0.114 | -0.155 |
| c4_w1_di21_ha5_rise | 109268 | 0.57 | 0.015 | 0.033 | -0.018 [-0.029, -0.008] | -3.4 | 0/4 | -0.040 | -0.067 |
| c4_wt_ha5_rise | 139119 | 0.73 | 0.016 | 0.041 | -0.026 [-0.040, -0.011] | -3.4 | 0/4 | -0.040 | -0.061 |
| c4_ichi_score_ha5_eagainst | 9765 | 0.05 | -0.029 | 0.026 | -0.054 [-0.086, -0.023] | -3.4 | 0/4 | -0.096 | -0.116 |
| c4_stc_ha5_side | 136913 | 0.72 | 0.014 | 0.046 | -0.032 [-0.051, -0.013] | -3.3 | 1/4 | -0.079 | -0.078 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 374 of 13029 session-condition cells pass (chance-level expectation under independence ~161 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_w1_cmo21_ha5_eagainst | 405 | -0.177 | -0.107 | -4.4 | 0/4 | -0.079 |
| asia | c4_qqeS_ha5_ewith | 5469 | 0.133 | 0.091 | 3.9 | 4/4 | 0.168 |
| asia | c4_w1_mfi21_ha5_ewith | 5823 | 0.114 | 0.086 | 4.0 | 4/4 | 0.161 |
| asia | c4_w1_stoch21_ha5_divwith | 4417 | -0.105 | -0.083 | -4.1 | 0/4 | -0.182 |
| asia | c4_w1_ema100_px_ha5_side | 46739 | 0.096 | 0.080 | 4.4 | 4/4 | 0.181 |
| asia | c4_w1_demarker21_ha5_eagainst | 1734 | -0.098 | -0.080 | -4.1 | 0/4 | -0.092 |
| close | c4_kerF_dir_ha5_divwith | 1525 | 0.134 | 0.070 | 2.8 | 4/4 | 0.044 |
| close | c4_nweF_ha5_ewith | 383 | 0.207 | 0.066 | 2.8 | 4/4 | 0.268 |
| close | c4_obF_in_ha5_against | 2780 | 0.104 | 0.065 | 2.7 | 4/4 | 0.358 |
| close | c4_obS_dres_ha5_hi | 2680 | -0.101 | -0.064 | -2.6 | 0/4 | -0.079 |
| close | c4_hullS_ha5_fresh5 | 1755 | 0.100 | 0.063 | 2.6 | 4/4 | 0.115 |
| close | c4_zlema_px_ha5_divwith | 1722 | 0.113 | 0.063 | 2.5 | 4/4 | 0.008 |
| london | c4_smie_ha5_nodiv | 49721 | -0.113 | -0.083 | -3.8 | 0/4 | -0.065 |
| london | c4_w1_eom14_ha5_divwith | 5735 | 0.103 | 0.078 | 3.6 | 4/4 | 0.188 |
| london | c4_rfilt_dir_ha5_against | 11164 | -0.096 | -0.077 | -3.9 | 0/4 | -0.032 |
| london | c4_rfilt_dir_ha5_side | 46134 | 0.096 | 0.077 | 3.9 | 4/4 | 0.032 |
| london | c4_tsiF_ha5_nodiv | 49023 | -0.102 | -0.077 | -3.5 | 0/4 | -0.049 |
| london | c4_smiS_ha5_nodiv | 48088 | -0.095 | -0.074 | -3.6 | 0/4 | -0.049 |
| nyam | c4_w1_atr_pct250_ha5_hi | 23789 | 0.247 | 0.085 | 3.6 | 4/4 | 0.411 |
| nyam | c4_w1_vortex14_ha5_divwith | 2831 | -0.141 | -0.083 | -3.4 | 0/4 | -0.144 |
| nyam | c4_crsi_ha5_eagainst_z2 | 734 | -0.150 | -0.073 | -2.9 | 0/4 | -0.146 |
| nyam | c4_w1_cmo14_ha5_divwith | 2916 | -0.125 | -0.072 | -2.9 | 0/4 | -0.095 |
| nyam | c4_crsiF_ha5_eagainst | 246 | -0.254 | -0.071 | -3.2 | 0/4 | -0.271 |
| nyam | c4_sdS_near_ha5_side | 1387 | -0.122 | -0.070 | -2.8 | 0/4 | -0.221 |
| nypm | c4_obF_cnt_ha5_fresh5 | 944 | -0.170 | -0.075 | -3.0 | 0/4 | -0.306 |
| nypm | c4_stAS_ha5_fresh5 | 1151 | -0.155 | -0.072 | -2.9 | 0/4 | -0.223 |
| nypm | c4_w1_ema_stack_slow_ha5_hold3 | 14516 | 0.112 | 0.072 | 3.0 | 4/4 | 0.258 |
| nypm | c4_w1_demarker14_ha5_eenter | 3791 | -0.090 | -0.071 | -3.5 | 0/4 | -0.063 |
| nypm | c4_w1_ema100_px_ha5_fresh5 | 2884 | -0.103 | -0.069 | -2.9 | 0/4 | -0.265 |
| nypm | c4_lrcS_slope_ha5_side | 15364 | 0.107 | 0.067 | 2.7 | 4/4 | 0.235 |
| pre | c4_tsiS_ha5_eenter | 514 | -0.275 | -0.096 | -4.0 | 0/4 | -0.337 |
| pre | c4_w1_kama200_px_ha5_divwith | 814 | -0.305 | -0.078 | -3.6 | 0/4 | -0.258 |
| pre | c4_w1_ema200_px_ha5_divwith | 839 | -0.287 | -0.074 | -3.4 | 0/4 | -0.424 |
| pre | c4_seb_ha5_ewith | 1582 | -0.122 | -0.073 | -3.0 | 0/4 | -0.159 |
| pre | c4_w1_sma34_px_ha5_divwith | 923 | -0.258 | -0.072 | -3.2 | 0/4 | -0.257 |
| pre | c4_w1_ema100_px_ha5_divwith | 854 | -0.281 | -0.071 | -3.3 | 0/4 | -0.251 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (749 of 63584 cell-conditions pass; chance at t>2.5 alone ~394)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_keltner40_pos_ha5_ewith | 1102 | 0.185 | 0.020 | 0.165 | 4.8 | 4/4 | 0.118 |
| K7 | asia | c4_w1_rsi14_ha5_side | 11642 | 0.051 | -0.029 | 0.081 | 4.7 | 4/4 | 0.144 |
| K7 | asia | c4_rsima14_ha5_side | 11643 | 0.051 | -0.029 | 0.081 | 4.7 | 4/4 | 0.144 |
| K7 | asia | c4_qqeS_ha5_ewith | 772 | 0.199 | 0.023 | 0.175 | 4.7 | 3/4 | 0.282 |
| A7 | nypm | c4_w1_ema_stack_slow_ha5_hold3 | 2914 | 0.066 | -0.200 | 0.267 | 4.7 | 4/4 | 0.439 |
| K7 | asia | c4_w1_demarker21_ha5_ewith | 3989 | 0.093 | 0.011 | 0.082 | 4.6 | 4/4 | 0.044 |
| K7 | asia | c4_don55_pos_ha5_eenter | 421 | 0.198 | 0.028 | 0.170 | 4.6 | 4/4 | 0.115 |
| K7 | asia | c4_tsiS_ha5_side | 8719 | 0.071 | -0.019 | 0.089 | 4.6 | 4/4 | 0.151 |
| K7 | asia | c4_qqe_ha5_side | 10167 | 0.058 | -0.019 | 0.077 | 4.6 | 4/4 | 0.125 |
| K7 | asia | c4_w1_vwmacd_ha5_side | 8955 | 0.067 | -0.017 | 0.084 | 4.5 | 4/4 | 0.149 |
| A7 | close | c4_w1_demarker7_ha5_divwith | 125 | 0.395 | -0.062 | 0.457 | 4.5 | 4/4 | 0.336 |
| K7 | asia | c4_qqeF_ha5_ewith | 4100 | 0.085 | 0.013 | 0.072 | 4.5 | 4/4 | 0.095 |
| K7 | asia | c4_qqeS_ha5_side | 9324 | 0.065 | -0.019 | 0.084 | 4.5 | 4/4 | 0.139 |
| K7 | asia | c4_smieS_ha5_side | 9456 | 0.063 | -0.018 | 0.081 | 4.5 | 4/4 | 0.131 |
| K7 | asia | c4_w1_ema50_px_ha5_side | 10332 | 0.059 | -0.025 | 0.084 | 4.4 | 4/4 | 0.165 |
| K7 | asia | c4_w1_cmo21_ha5_ewith | 1967 | 0.118 | 0.020 | 0.098 | 4.4 | 4/4 | 0.063 |
| K7 | asia | c4_w1_rsi7_ha5_ewith | 4960 | 0.072 | 0.013 | 0.058 | 4.4 | 4/4 | 0.051 |
| K7 | asia | c4_rsima7_ha5_ewith | 4960 | 0.072 | 0.013 | 0.058 | 4.4 | 4/4 | 0.051 |
| A7 | close | c4_zlema_px_ha5_divwith | 176 | 0.323 | -0.069 | 0.392 | 4.4 | 4/4 | 0.596 |
| K7 | asia | c4_w1_ema21_hold_ha5_side | 5392 | 0.078 | 0.007 | 0.071 | 4.4 | 4/4 | 0.069 |
| K7 | asia | c4_kr_dir_ha5_side | 11380 | 0.051 | -0.023 | 0.074 | 4.4 | 4/4 | 0.125 |
| K7 | asia | c4_don55_pos_ha5_ewith | 635 | 0.176 | 0.026 | 0.150 | 4.4 | 4/4 | 0.146 |
| K7 | asia | c4_w1_ema100_px_ha5_side | 9206 | 0.070 | -0.026 | 0.096 | 4.4 | 4/4 | 0.195 |
| K7 | asia | c4_w1_sma100_px_ha5_side | 9131 | 0.069 | -0.022 | 0.091 | 4.4 | 4/4 | 0.182 |
| K7 | asia | c4_w1_macd19_39_9_line_ha5_side | 8757 | 0.069 | -0.017 | 0.086 | 4.4 | 4/4 | 0.152 |
| K7 | asia | c4_w1_donchian50_pos_ha5_eenter | 386 | 0.194 | 0.028 | 0.166 | 4.3 | 4/4 | 0.172 |
| K7 | asia | c4_w1_di21_ha5_side | 10353 | 0.057 | -0.020 | 0.077 | 4.3 | 4/4 | 0.133 |
| K7 | asia | c4_qqe_ha5_ewith | 1663 | 0.132 | 0.020 | 0.112 | 4.3 | 4/4 | 0.065 |
| K7 | asia | c4_wtS_ha5_side | 9400 | 0.060 | -0.013 | 0.073 | 4.3 | 4/4 | 0.115 |
| K7 | asia | c4_w1_trix15_ha5_side | 8599 | 0.067 | -0.013 | 0.080 | 4.3 | 4/4 | 0.148 |

## B4 alternate bars: ha60

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2248; |t|>2: 0 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha60.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha60_side | 26568 | 0.55 | nan | nan | nan [nan, nan] | nan | 1/4 | nan | nan |
| c4_wt_ha60_sig | 29532 | 0.61 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_rise | 31180 | 0.64 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_fresh5 | 17255 | 0.36 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_ewith_z1 | 3831 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eagainst_z1 | 2365 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eleave_z1 | 1409 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eenter_z1 | 1496 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_ewith_z2 | 7632 | 0.16 | nan | nan | nan [nan, nan] | nan | 1/4 | nan | nan |
| c4_wt_ha60_eagainst_z2 | 5284 | 0.11 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha60_side | 26568 | 0.55 | nan | nan | nan [nan, nan] | nan | 1/4 | nan | nan |
| c4_wt_ha60_sig | 29532 | 0.61 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_rise | 31180 | 0.64 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_fresh5 | 17255 | 0.36 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_ewith_z1 | 3831 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eagainst_z1 | 2365 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eleave_z1 | 1409 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eenter_z1 | 1496 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_ewith_z2 | 7632 | 0.16 | nan | nan | nan [nan, nan] | nan | 1/4 | nan | nan |
| c4_wt_ha60_eagainst_z2 | 5284 | 0.11 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 132 of 12506 session-condition cells pass (chance-level expectation under independence ~155 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_fvgF_near_ha60_hold3 | 108 | 0.665 | 0.095 | 5.4 | 3/3 | 0.702 |
| close | c4_ichiS_futcloud_ha60_fresh5 | 180 | 0.521 | 0.087 | 4.7 | 3/3 | 0.076 |
| close | c4_krS_dir_ha60_rise | 1663 | 0.342 | 0.083 | 3.9 | 3/3 | 0.547 |
| close | c4_sdS_near_ha60_against | 611 | -0.313 | -0.074 | -3.5 | 0/3 | -0.443 |
| close | c4_stc_ha60_eleave | 180 | -0.530 | -0.073 | -4.2 | 0/3 | -0.409 |
| close | c4_chand_ha60_side | 1381 | -0.263 | -0.069 | -3.1 | 0/3 | -0.416 |
| nyam | c4_w1_donchian50_pos_ha60_ewith | 158 | 0.663 | 0.167 | 7.7 | 4/4 | 0.773 |
| nyam | c4_don55_pos_ha60_ewith | 159 | 0.654 | 0.163 | 7.5 | 4/4 | 0.773 |
| nyam | c4_w1_cci14_ha60_nodiv | 6922 | -0.185 | -0.093 | -3.7 | 0/4 | -0.260 |
| nyam | c4_ob_cnt_ha60_fresh5 | 293 | -0.278 | -0.085 | -3.7 | 0/4 | -0.549 |
| nyam | c4_lrc_slope_ha60_fresh5 | 238 | -0.346 | -0.084 | -3.9 | 0/4 | -0.304 |
| nyam | c4_w1_vwmacd_ha60_divwith | 707 | -0.184 | -0.078 | -3.2 | 0/4 | -0.109 |
| nypm | c4_kerS_dir_ha60_eleave | 169 | -0.433 | -0.116 | -5.2 | 0/3 | -0.537 |
| nypm | c4_sebS_ha60_eagainst | 329 | -0.254 | -0.088 | -3.7 | 0/4 | -0.257 |
| nypm | c4_wtF_ha60_nodiv | 4319 | -0.337 | -0.081 | -3.8 | 0/4 | -0.181 |
| nypm | c4_w1_vwmacd_ha60_divwith | 554 | 0.267 | 0.079 | 3.5 | 4/4 | 0.159 |
| nypm | c4_lrcF_ha60_eagainst | 443 | -0.272 | -0.078 | -3.5 | 0/4 | -0.314 |
| nypm | c4_w1_sma34_px_ha60_nodiv | 4378 | -0.286 | -0.078 | -3.5 | 0/4 | -0.197 |
| pre | c4_zlemaF_slope_ha60_fresh5 | 695 | 0.279 | 0.083 | 3.6 | 3/3 | 0.243 |
| pre | c4_w1_hma200_px_ha60_side | 562 | 0.405 | 0.079 | 4.0 | 3/3 | 0.373 |
| pre | c4_lrc_slope_ha60_rise | 770 | 0.536 | 0.076 | 4.4 | 3/3 | 0.594 |
| pre | c4_t3F_slope_ha60_fresh5 | 648 | 0.292 | 0.074 | 3.4 | 3/3 | 0.161 |
| pre | c4_utbotS_ha60_fresh5 | 102 | 0.497 | 0.072 | 4.1 | 3/3 | 0.512 |
| pre | c4_qqeS_ha60_sig | 813 | 0.335 | 0.071 | 3.5 | 3/3 | 0.309 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (861 of 51931 cell-conditions pass; chance at t>2.5 alone ~321)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| P7 | nypm | c4_w1_vwmacd_ha60_divwith | 132 | 0.652 | -0.041 | 0.693 | 8.1 | 3/3 | 0.560 |
| P7 | close | c4_ichiS_futcloud_ha60_fresh5 | 63 | 0.515 | -0.089 | 0.604 | 5.3 | 3/3 | 0.255 |
| K7 | london | c4_w1_vwma34_px_ha60_nodiv | 3258 | 0.037 | -0.334 | 0.371 | 4.9 | 4/4 | 0.390 |
| M7 | london | c4_w1_vwma34_px_ha60_nodiv | 4142 | 0.037 | -0.315 | 0.353 | 4.8 | 3/4 | 0.474 |
| P7 | asia | c4_fvg_cnt_ha60_fresh5 | 96 | 0.542 | 0.064 | 0.478 | 4.8 | 3/3 | 0.612 |
| A7 | nyam | c4_kerF_dir_ha60_eenter | 199 | 0.405 | -0.166 | 0.571 | 4.7 | 3/3 | 0.496 |
| A7 | nypm | c4_t3S_px_ha60_side | 527 | 0.116 | -0.486 | 0.601 | 4.7 | 3/3 | 0.529 |
| P7 | asia | c4_sqzmF_mom_ha60_fresh1 | 136 | 0.420 | 0.063 | 0.356 | 4.7 | 3/4 | 0.608 |
| A7 | nyam | c4_kerF_abs_ha60_hi_z1 | 380 | 0.232 | -0.352 | 0.584 | 4.6 | 3/3 | 0.670 |
| P7 | pre | c4_qqeS_ha60_sig | 218 | 0.331 | -0.218 | 0.550 | 4.6 | 3/3 | 0.595 |
| K7 | london | c4_smi_ha60_nodiv | 3174 | 0.041 | -0.229 | 0.270 | 4.6 | 4/4 | 0.340 |
| M7 | london | c4_w1_vwma21_px_ha60_nodiv | 4197 | 0.037 | -0.261 | 0.298 | 4.6 | 3/4 | 0.414 |
| K7 | nypm | c4_w1_ichi_fast_tkkj_ha60_rise | 548 | 0.184 | -0.030 | 0.214 | 4.5 | 4/4 | 0.196 |
| K7 | nypm | c4_ichiF_tk_ha60_rise | 548 | 0.184 | -0.030 | 0.214 | 4.5 | 4/4 | 0.196 |
| K7 | london | c4_w1_vortex7_ha60_nodiv | 3087 | 0.044 | -0.199 | 0.242 | 4.5 | 3/4 | 0.269 |
| M7 | pre | c4_lrc_slope_ha60_rise | 221 | 0.278 | -0.325 | 0.603 | 4.4 | 3/3 | 0.650 |
| P7 | asia | c4_stA_ha60_side | 2956 | 0.147 | -0.019 | 0.166 | 4.4 | 4/4 | 0.185 |
| K7 | london | c4_w1_vwma21_px_ha60_nodiv | 3302 | 0.033 | -0.269 | 0.302 | 4.3 | 4/4 | 0.289 |
| P7 | london | c4_copp_ha60_divwith | 450 | 0.328 | 0.018 | 0.310 | 4.3 | 4/4 | 0.347 |
| P7 | asia | c4_w1_supertrend_10_3_ha60_side | 2948 | 0.146 | -0.018 | 0.164 | 4.3 | 4/4 | 0.177 |
| K7 | close | c4_nweS_ha60_rise | 247 | 0.078 | -0.374 | 0.452 | 4.2 | 3/3 | 0.604 |
| K7 | close | c4_w1_ema34_px_ha60_rise | 315 | 0.083 | -0.316 | 0.399 | 4.2 | 3/3 | 0.504 |
| K7 | close | c4_crsi_ha60_eleave_z1 | 106 | 0.220 | -0.177 | 0.397 | 4.2 | 3/3 | 0.458 |
| P7 | pre | c4_rfilt_ha60_side | 262 | 0.304 | -0.322 | 0.626 | 4.2 | 3/3 | 0.513 |
| A7 | nypm | c4_rsima14_ha60_sig | 524 | 0.111 | -0.425 | 0.535 | 4.1 | 3/3 | 0.338 |
| P7 | pre | c4_stc_ha60_ewith | 181 | 0.338 | -0.174 | 0.513 | 4.1 | 3/3 | 0.602 |
| P7 | asia | c4_stA_ha60_hold3 | 2849 | 0.146 | -0.011 | 0.158 | 4.1 | 4/4 | 0.165 |
| K7 | london | c4_w1_demarker7_ha60_nodiv | 3117 | 0.045 | -0.227 | 0.272 | 4.1 | 3/4 | 0.266 |
| A7 | nyam | c4_w1_rsi2_ha60_eenter | 202 | 0.370 | -0.152 | 0.522 | 4.1 | 3/3 | 0.496 |
| K7 | asia | c4_elderF_bull_ha60_side | 2387 | 0.111 | -0.022 | 0.133 | 4.1 | 4/4 | 0.114 |

## B4 alternate bars: range16

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2212; |t|>2: 213 (chance expectation ~100 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_range16.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_sd_cnt_range16_side | 41002 | 0.85 | 0.051 | -0.007 | 0.058 [0.036, 0.080] | 5.2 | 3/4 | 0.010 | -0.020 |
| c4_w1_ema_stack_slow_range16_hold3 | 37519 | 0.78 | 0.053 | 0.006 | 0.047 [0.028, 0.065] | 4.8 | 2/4 | 0.003 | -0.002 |
| c4_w1_ema_stack_slow_range16_side | 38395 | 0.79 | 0.052 | 0.005 | 0.048 [0.028, 0.067] | 4.8 | 3/4 | 0.012 | 0.001 |
| c4_sdF_cnt_range16_side | 41478 | 0.86 | 0.050 | -0.003 | 0.053 [0.030, 0.075] | 4.6 | 2/4 | 0.002 | -0.013 |
| c4_sdS_cnt_range16_side | 40307 | 0.83 | 0.050 | 0.002 | 0.048 [0.027, 0.069] | 4.4 | 3/4 | 0.019 | -0.009 |
| c4_w1_ema200_px_range16_side | 45448 | 0.94 | 0.046 | -0.022 | 0.068 [0.035, 0.102] | 4.0 | 3/4 | -0.008 | -0.013 |
| c4_lrcS_slope_range16_side | 37346 | 0.77 | 0.051 | 0.014 | 0.037 [0.018, 0.056] | 3.8 | 3/4 | 0.026 | 0.025 |
| c4_fvgF_cnt_range16_side | 43329 | 0.90 | 0.047 | -0.001 | 0.048 [0.023, 0.074] | 3.7 | 2/4 | -0.003 | 0.006 |
| c4_fvg_cnt_range16_side | 43248 | 0.89 | 0.047 | 0.003 | 0.043 [0.018, 0.069] | 3.4 | 2/4 | 0.003 | 0.029 |
| c4_w1_ichi_std_lag_range16_divwith | 915 | 0.02 | 0.138 | 0.040 | 0.097 [0.039, 0.156] | 3.3 | 2/4 | 0.119 | 0.213 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_w1_ema_stack_slow_range16_against | 3735 | 0.08 | -0.021 | 0.048 | -0.069 [-0.098, -0.040] | -4.6 | 0/4 | -0.015 | 0.008 |
| c4_w1_vwma200_px_range16_nodiv | 44982 | 0.93 | 0.037 | 0.106 | -0.069 [-0.100, -0.037] | -4.3 | 1/4 | -0.076 | -0.065 |
| c4_w1_kama200_px_range16_fresh5 | 5545 | 0.11 | -0.004 | 0.048 | -0.053 [-0.078, -0.028] | -4.1 | 0/4 | -0.018 | -0.036 |
| c4_sd_dsup_range16_hi | 12390 | 0.27 | 0.018 | 0.051 | -0.033 [-0.052, -0.014] | -3.5 | 2/4 | -0.080 | -0.007 |
| c4_sebS_range16_side | 34030 | 0.70 | 0.033 | 0.064 | -0.031 [-0.048, -0.013] | -3.4 | 1/4 | -0.028 | -0.019 |
| c4_sslhyb_range16_side | 32776 | 0.68 | 0.033 | 0.062 | -0.029 [-0.047, -0.012] | -3.3 | 1/4 | -0.018 | -0.009 |
| c4_w1_sma200_px_range16_nodiv | 45027 | 0.93 | 0.039 | 0.092 | -0.053 [-0.085, -0.022] | -3.3 | 1/4 | -0.051 | -0.004 |
| c4_lrcF_range16_side | 32940 | 0.68 | 0.033 | 0.062 | -0.029 [-0.046, -0.012] | -3.3 | 1/4 | -0.026 | -0.012 |
| c4_w1_trix15_range16_rise | 32018 | 0.66 | 0.033 | 0.061 | -0.028 [-0.045, -0.011] | -3.3 | 1/4 | -0.026 | -0.011 |
| c4_w1_linreg_chan50_range16_side | 32938 | 0.68 | 0.033 | 0.062 | -0.029 [-0.046, -0.012] | -3.3 | 1/4 | -0.026 | -0.012 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 382 of 12183 session-condition cells pass (chance-level expectation under independence ~151 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_tsi_range16_eleave | 108 | -0.277 | -0.080 | -3.5 | 0/4 | -0.139 |
| asia | c4_w1_cci14_range16_divwith | 1052 | 0.101 | 0.077 | 3.6 | 4/4 | 0.106 |
| asia | c4_w1_demarker14_range16_eleave | 449 | 0.128 | 0.077 | 3.1 | 4/4 | 0.178 |
| asia | c4_w1_force13_range16_divwith | 1273 | 0.093 | 0.074 | 3.7 | 4/4 | 0.141 |
| asia | c4_w1_boll10_walk_range16_divwith | 914 | 0.101 | 0.074 | 3.4 | 4/4 | 0.087 |
| asia | c4_w1_keltner10_pos_range16_divwith | 1130 | 0.093 | 0.073 | 3.5 | 4/4 | 0.101 |
| close | c4_w1_ichi_std_tkkj_range16_nodiv | 1939 | -0.218 | -0.121 | -4.8 | 0/3 | -0.234 |
| close | c4_ichi_tk_range16_nodiv | 1939 | -0.218 | -0.121 | -4.8 | 0/3 | -0.234 |
| close | c4_w1_linreg_slope20_range16_nodiv | 1956 | -0.200 | -0.109 | -4.4 | 0/3 | -0.198 |
| close | c4_sqzm_mom_range16_nodiv | 1938 | -0.190 | -0.104 | -4.2 | 0/3 | -0.190 |
| close | c4_w1_sqz_hist_range16_nodiv | 1938 | -0.190 | -0.104 | -4.2 | 0/3 | -0.190 |
| close | c4_w1_rsi2_range16_eleave | 252 | 0.235 | 0.095 | 3.9 | 3/3 | 0.242 |
| london | c4_w1_vwma200_px_range16_nodiv | 13708 | -0.114 | -0.084 | -3.9 | 0/4 | -0.109 |
| london | c4_w1_cmo21_range16_divwith | 1148 | -0.101 | -0.077 | -3.7 | 0/4 | -0.169 |
| london | c4_w1_mom20_range16_divwith | 1123 | -0.099 | -0.075 | -3.6 | 0/4 | -0.152 |
| london | c4_stAS_range16_side | 11933 | 0.083 | 0.073 | 4.4 | 4/4 | 0.053 |
| london | c4_stAS_range16_against | 2761 | -0.083 | -0.073 | -4.4 | 0/4 | -0.053 |
| london | c4_w1_roc20_range16_divwith | 1148 | -0.094 | -0.072 | -3.4 | 0/4 | -0.141 |
| nyam | c4_w1_keltner40_pos_range16_side | 6897 | -0.123 | -0.086 | -3.8 | 0/4 | -0.065 |
| nyam | c4_rsima21_range16_side | 6908 | -0.121 | -0.084 | -3.7 | 0/4 | -0.056 |
| nyam | c4_w1_rsi21_range16_side | 6908 | -0.121 | -0.084 | -3.7 | 0/4 | -0.056 |
| nyam | c4_krS_px_range16_side | 6848 | -0.116 | -0.082 | -3.6 | 0/4 | -0.066 |
| nyam | c4_w1_sma34_px_range16_side | 6620 | -0.111 | -0.082 | -3.7 | 0/4 | -0.048 |
| nyam | c4_w1_di21_range16_side | 6806 | -0.111 | -0.080 | -3.6 | 0/4 | -0.049 |
| nypm | c4_w1_trendcolor_range16_nodiv | 3869 | -0.129 | -0.093 | -4.2 | 0/4 | -0.165 |
| nypm | c4_stPS_range16_hold3 | 4167 | -0.124 | -0.083 | -3.5 | 0/4 | -0.129 |
| nypm | c4_t3_px_range16_nodiv | 3822 | -0.110 | -0.080 | -3.6 | 0/4 | -0.137 |
| nypm | c4_w1_linreg_chan20_range16_nodiv | 3697 | -0.105 | -0.078 | -3.5 | 0/4 | -0.158 |
| nypm | c4_w1_mom20_range16_side | 4201 | 0.118 | 0.078 | 3.3 | 4/4 | 0.151 |
| nypm | c4_w1_roc20_range16_side | 4201 | 0.118 | 0.078 | 3.3 | 4/4 | 0.151 |
| pre | c4_w1_updown_vol20_range16_side | 1152 | -0.237 | -0.098 | -4.0 | 0/3 | -0.234 |
| pre | c4_mcg_px_range16_fresh1 | 132 | 0.368 | 0.096 | 4.4 | 3/3 | 0.403 |
| pre | c4_stcS_range16_rise | 1068 | -0.213 | -0.095 | -3.8 | 0/3 | -0.089 |
| pre | c4_hullS_range16_fresh5 | 155 | -0.342 | -0.093 | -4.2 | 0/3 | -0.276 |
| pre | c4_kerS_abs_range16_rise | 829 | -0.186 | -0.091 | -3.6 | 0/3 | -0.202 |
| pre | c4_ichi_chikou_range16_side | 1228 | -0.236 | -0.088 | -3.6 | 0/3 | -0.230 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (342 of 48845 cell-conditions pass; chance at t>2.5 alone ~302)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_ema200_px_range16_side | 4143 | 0.066 | -0.137 | 0.203 | 5.1 | 4/4 | 0.376 |
| P7 | london | c4_w1_adx21_range16_hi_z1 | 110 | 0.400 | 0.042 | 0.358 | 4.8 | 4/4 | 0.223 |
| A7 | london | c4_rvi_range16_side | 1010 | 0.093 | -0.164 | 0.257 | 4.8 | 3/3 | 0.261 |
| K7 | asia | c4_w1_vwma200_px_range16_side | 4032 | 0.067 | -0.105 | 0.172 | 4.7 | 4/4 | 0.173 |
| K7 | asia | c4_fvgS_cnt_range16_side | 3719 | 0.073 | -0.065 | 0.138 | 4.4 | 4/4 | 0.165 |
| A7 | london | c4_smi_range16_side | 1168 | 0.067 | -0.200 | 0.267 | 4.3 | 3/3 | 0.225 |
| K7 | asia | c4_w1_ema_stack_slow_range16_side | 3163 | 0.082 | -0.030 | 0.111 | 4.2 | 3/4 | 0.137 |
| K7 | asia | c4_w1_sma200_px_range16_side | 4050 | 0.065 | -0.090 | 0.155 | 4.1 | 4/4 | 0.243 |
| P7 | london | c4_w1_kama_stack_slow_range16_hold3 | 2134 | 0.106 | -0.003 | 0.109 | 4.1 | 4/4 | 0.108 |
| K7 | asia | c4_fvgF_cnt_range16_side | 3802 | 0.069 | -0.061 | 0.130 | 4.1 | 4/4 | 0.176 |
| P7 | london | c4_w1_kama_stack_slow_range16_side | 2185 | 0.104 | -0.004 | 0.108 | 4.0 | 4/4 | 0.100 |
| M7 | london | c4_kst_range16_side | 3630 | 0.044 | -0.089 | 0.133 | 4.0 | 4/4 | 0.119 |
| A7 | london | c4_stcS_range16_rise | 1022 | 0.078 | -0.133 | 0.211 | 3.9 | 3/3 | 0.116 |
| P7 | nypm | c4_w1_mom20_range16_side | 1085 | 0.076 | -0.172 | 0.247 | 3.9 | 3/3 | 0.262 |
| P7 | nypm | c4_w1_roc20_range16_side | 1085 | 0.076 | -0.172 | 0.247 | 3.9 | 3/3 | 0.262 |
| K7 | nypm | c4_w1_trix15_range16_fresh5 | 111 | 0.322 | 0.016 | 0.307 | 3.8 | 4/4 | 0.183 |
| M7 | london | c4_stAS_range16_hold3 | 3413 | 0.045 | -0.068 | 0.113 | 3.7 | 4/4 | 0.091 |
| A7 | london | c4_hilo_range16_hold3 | 1004 | 0.076 | -0.121 | 0.196 | 3.7 | 3/3 | 0.199 |
| K7 | asia | c4_w1_ema_stack_slow_range16_hold3 | 3072 | 0.079 | -0.017 | 0.096 | 3.6 | 3/4 | 0.092 |
| K7 | asia | c4_sdF_cnt_range16_side | 3574 | 0.071 | -0.036 | 0.106 | 3.6 | 3/4 | 0.140 |
| K7 | london | c4_fvgF_cnt_range16_side | 3162 | 0.031 | -0.136 | 0.166 | 3.6 | 4/4 | 0.108 |
| M7 | asia | c4_fvgF_cnt_range16_side | 2754 | 0.100 | -0.087 | 0.187 | 3.6 | 3/3 | 0.089 |
| K7 | asia | c4_ob_cnt_range16_side | 3517 | 0.071 | -0.032 | 0.103 | 3.5 | 3/4 | 0.136 |
| A7 | london | c4_hull_range16_side | 1141 | 0.061 | -0.154 | 0.215 | 3.5 | 3/3 | 0.149 |
| H7 | asia | c4_zlemaF_px_range16_divwith | 146 | 0.305 | 0.027 | 0.278 | 3.5 | 4/4 | 0.219 |
| M7 | asia | c4_obS_cnt_range16_side | 2572 | 0.107 | -0.045 | 0.152 | 3.5 | 3/3 | 0.065 |
| A7 | london | c4_ssl_range16_hold3 | 994 | 0.074 | -0.112 | 0.186 | 3.5 | 3/3 | 0.176 |
| M7 | asia | c4_sdS_cnt_range16_side | 2588 | 0.106 | -0.044 | 0.150 | 3.5 | 3/3 | 0.047 |
| A7 | nypm | c4_w1_mom5_range16_rise | 349 | 0.158 | -0.113 | 0.271 | 3.5 | 3/3 | 0.282 |
| M7 | london | c4_stAS_range16_side | 3657 | 0.040 | -0.077 | 0.117 | 3.5 | 4/4 | 0.087 |

## B4 alternate bars: range8

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2219; |t|>2: 485 (chance expectation ~100 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_range8.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_w1_wave_short_hist_range8_side | 27391 | 0.57 | 0.057 | 0.022 | 0.035 [0.019, 0.051] | 4.2 | 3/4 | 0.045 | 0.051 |
| c4_kvo_range8_fresh5 | 16427 | 0.34 | 0.066 | 0.030 | 0.036 [0.019, 0.052] | 4.1 | 4/4 | 0.046 | 0.043 |
| c4_w1_rsi2_range8_ewith | 11643 | 0.24 | 0.071 | 0.033 | 0.038 [0.019, 0.056] | 4.0 | 4/4 | 0.067 | 0.091 |
| c4_seb_range8_side | 28775 | 0.60 | 0.055 | 0.023 | 0.032 [0.016, 0.049] | 3.9 | 3/4 | 0.037 | 0.042 |
| c4_t3S_slope_range8_rise | 26563 | 0.55 | 0.057 | 0.025 | 0.032 [0.016, 0.048] | 3.8 | 3/4 | 0.039 | 0.048 |
| c4_mcwt_range8_sig | 26981 | 0.56 | 0.056 | 0.025 | 0.032 [0.016, 0.048] | 3.8 | 3/4 | 0.039 | 0.055 |
| c4_w1_linreg_chan20_range8_side | 26738 | 0.55 | 0.056 | 0.025 | 0.031 [0.015, 0.048] | 3.8 | 3/4 | 0.036 | 0.048 |
| c4_hullF_px_range8_side | 27070 | 0.56 | 0.056 | 0.025 | 0.031 [0.015, 0.048] | 3.8 | 3/4 | 0.039 | 0.058 |
| c4_w1_hma21_px_range8_side | 27070 | 0.56 | 0.056 | 0.025 | 0.031 [0.015, 0.048] | 3.8 | 3/4 | 0.039 | 0.058 |
| c4_lrc_range8_eleave | 1408 | 0.03 | 0.133 | 0.040 | 0.094 [0.045, 0.142] | 3.8 | 4/4 | 0.071 | 0.080 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_alligator_range8_hold3 | 28752 | 0.59 | 0.031 | 0.058 | -0.027 [-0.044, -0.011] | -3.3 | 0/4 | -0.024 | -0.026 |
| c4_w1_kama_stack_slow_range8_hold3 | 27197 | 0.56 | 0.031 | 0.057 | -0.026 [-0.042, -0.009] | -3.1 | 1/4 | -0.028 | -0.003 |
| c4_w1_ema_stack_fast_range8_hold3 | 33759 | 0.70 | 0.034 | 0.061 | -0.027 [-0.045, -0.010] | -3.0 | 0/4 | -0.017 | -0.009 |
| c4_w1_ema_8_21_34_stack_range8_hold3 | 33759 | 0.70 | 0.034 | 0.061 | -0.027 [-0.045, -0.010] | -3.0 | 0/4 | -0.017 | -0.009 |
| c4_alligator_range8_side | 32309 | 0.67 | 0.034 | 0.060 | -0.026 [-0.043, -0.009] | -3.0 | 0/4 | -0.027 | -0.025 |
| c4_fvgS_in_range8_fresh5 | 30957 | 0.64 | 0.033 | 0.058 | -0.025 [-0.042, -0.008] | -3.0 | 0/4 | -0.019 | -0.028 |
| c4_w1_kama_stack_slow_range8_side | 28068 | 0.58 | 0.032 | 0.056 | -0.024 [-0.040, -0.008] | -2.9 | 1/4 | -0.023 | 0.000 |
| c4_stAS_range8_hold3 | 36046 | 0.75 | 0.035 | 0.063 | -0.027 [-0.046, -0.009] | -2.9 | 0/4 | -0.012 | -0.044 |
| c4_stcF_range8_eagainst | 15809 | 0.33 | 0.026 | 0.050 | -0.025 [-0.042, -0.008] | -2.8 | 1/4 | -0.035 | -0.034 |
| c4_stP_range8_hold3 | 37521 | 0.78 | 0.036 | 0.064 | -0.028 [-0.047, -0.008] | -2.8 | 0/4 | -0.026 | -0.021 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 319 of 12208 session-condition cells pass (chance-level expectation under independence ~151 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_w1_donchian20_pos_range8_eleave | 584 | 0.125 | 0.083 | 3.5 | 4/4 | 0.138 |
| asia | c4_don20_pos_range8_eleave | 584 | 0.125 | 0.083 | 3.5 | 4/4 | 0.138 |
| asia | c4_fvgF_cnt_range8_fresh5 | 933 | -0.091 | -0.068 | -3.2 | 0/4 | -0.076 |
| asia | c4_nweS_range8_ewith | 329 | -0.130 | -0.067 | -2.7 | 0/4 | -0.155 |
| asia | c4_fvg_cnt_range8_fresh5 | 890 | -0.083 | -0.061 | -2.8 | 0/4 | -0.042 |
| asia | c4_w1_kama_stack_slow_range8_against | 1757 | -0.055 | -0.046 | -2.5 | 0/4 | -0.053 |
| close | c4_w1_ha_run_range8_fresh5 | 1908 | 0.205 | 0.118 | 4.8 | 3/3 | 0.173 |
| close | c4_mcg_slope_range8_fresh5 | 874 | 0.182 | 0.116 | 4.8 | 3/3 | 0.238 |
| close | c4_mcg_px_range8_fresh5 | 874 | 0.182 | 0.116 | 4.8 | 3/3 | 0.238 |
| close | c4_w1_rsi2_range8_fresh5 | 1685 | 0.174 | 0.109 | 4.5 | 3/3 | 0.199 |
| close | c4_mcg_px_range8_fresh1 | 215 | 0.276 | 0.106 | 4.4 | 3/3 | 0.315 |
| close | c4_alma_px_range8_fresh5 | 1642 | 0.169 | 0.106 | 4.4 | 3/3 | 0.201 |
| london | c4_w1_linreg_chan20_range8_eenter | 558 | 0.122 | 0.077 | 3.2 | 4/4 | 0.228 |
| london | c4_w1_linreg_chan20_range8_ewith | 611 | 0.118 | 0.077 | 3.2 | 4/4 | 0.221 |
| london | c4_ob_cnt_range8_side | 12661 | 0.090 | 0.076 | 4.3 | 4/4 | 0.055 |
| london | c4_w1_boll20_walk_range8_divwith | 340 | -0.142 | -0.073 | -2.9 | 0/4 | -0.228 |
| london | c4_sd_near_range8_hold3 | 422 | 0.129 | 0.072 | 2.9 | 4/4 | 0.091 |
| london | c4_qqeF_range8_divwith | 692 | -0.106 | -0.072 | -3.1 | 0/4 | -0.106 |
| nyam | c4_w1_boll40_walk_range8_rise | 253 | 0.248 | 0.105 | 4.2 | 4/4 | 0.162 |
| nyam | c4_w1_kama_stack_fast_range8_against | 968 | 0.157 | 0.103 | 4.4 | 4/4 | 0.008 |
| nyam | c4_w1_boll40_pctb_range8_eenter | 238 | 0.225 | 0.094 | 3.8 | 4/4 | 0.098 |
| nyam | c4_lrc_range8_eleave | 335 | 0.211 | 0.091 | 3.7 | 4/4 | 0.209 |
| nyam | c4_w1_boll40_pctb_range8_ewith | 263 | 0.194 | 0.085 | 3.4 | 4/4 | 0.098 |
| nyam | c4_stA_range8_fresh5 | 743 | 0.123 | 0.081 | 3.4 | 4/4 | 0.080 |
| nypm | c4_obF_dres_range8_hi | 1169 | 0.112 | 0.077 | 3.3 | 4/4 | 0.061 |
| nypm | c4_w1_boll40_pctb_range8_fresh5 | 891 | 0.095 | 0.065 | 2.8 | 4/4 | 0.123 |
| nypm | c4_kvoS_range8_fresh5 | 1362 | 0.085 | 0.063 | 2.9 | 4/4 | 0.157 |
| nypm | c4_sdF_dsup_range8_hi | 865 | -0.086 | -0.058 | -2.5 | 0/4 | -0.125 |
| nypm | c4_hullF_px_range8_fresh5 | 2402 | 0.068 | 0.053 | 2.6 | 4/4 | 0.091 |
| nypm | c4_w1_hma21_px_range8_fresh5 | 2402 | 0.068 | 0.053 | 2.6 | 4/4 | 0.091 |
| pre | c4_w1_ema50_px_range8_fresh5 | 293 | 0.222 | 0.085 | 3.5 | 3/3 | 0.263 |
| pre | c4_lrcS_range8_side | 1052 | -0.189 | -0.085 | -3.4 | 0/3 | -0.138 |
| pre | c4_elderS_bear_range8_nodiv | 1278 | 0.243 | 0.080 | 3.4 | 3/3 | 0.209 |
| pre | c4_ichiS_score_range8_ewith | 926 | -0.153 | -0.073 | -2.9 | 0/3 | -0.164 |
| pre | c4_kstS_range8_side | 1170 | -0.180 | -0.072 | -2.9 | 0/3 | -0.121 |
| pre | c4_hullF_range8_rise | 770 | 0.148 | 0.072 | 2.9 | 3/3 | 0.107 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (428 of 49679 cell-conditions pass; chance at t>2.5 alone ~308)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| M7 | nyam | c4_w1_stoch21_range8_eenter | 319 | 0.245 | 0.003 | 0.242 | 4.6 | 4/4 | 0.193 |
| M7 | london | c4_sdflipF_in_range8_against | 560 | 0.174 | -0.004 | 0.178 | 4.6 | 4/4 | 0.164 |
| P7 | nypm | c4_w1_psar_0.03_range8_side | 859 | 0.110 | -0.118 | 0.228 | 4.3 | 3/3 | 0.307 |
| P7 | nypm | c4_smiF_range8_ewith | 538 | 0.160 | -0.061 | 0.221 | 4.3 | 3/3 | 0.245 |
| A7 | nyam | c4_smieS_range8_ewith | 75 | 0.409 | -0.027 | 0.436 | 4.0 | 3/3 | 0.510 |
| P7 | nypm | c4_smi_range8_sig | 756 | 0.116 | -0.087 | 0.203 | 3.9 | 3/3 | 0.197 |
| K7 | london | c4_w1_pat_engulf_range8_side | 119 | 0.314 | 0.002 | 0.311 | 3.9 | 3/4 | 0.458 |
| P7 | nypm | c4_w1_stoch8_range8_ewith | 456 | 0.162 | -0.042 | 0.204 | 3.8 | 3/3 | 0.190 |
| P7 | close | c4_alma_px_range8_fresh5 | 550 | 0.037 | -0.193 | 0.231 | 3.6 | 3/3 | 0.223 |
| P7 | london | c4_sfpF_range8_fresh5 | 347 | 0.209 | 0.037 | 0.172 | 3.5 | 3/4 | 0.247 |
| P7 | close | c4_zlemaF_slope_range8_fresh5 | 476 | 0.052 | -0.167 | 0.219 | 3.5 | 3/3 | 0.208 |
| P7 | asia | c4_w1_pat_engulf_range8_nodiv | 5148 | 0.080 | -0.105 | 0.185 | 3.5 | 4/4 | 0.089 |
| P7 | nypm | c4_hullS_range8_rise | 778 | 0.104 | -0.077 | 0.181 | 3.5 | 3/3 | 0.158 |
| P7 | nypm | c4_hilo_range8_side | 935 | 0.087 | -0.107 | 0.194 | 3.5 | 3/3 | 0.239 |
| P7 | nypm | c4_w1_fisher20_range8_rise | 709 | 0.111 | -0.066 | 0.178 | 3.5 | 3/3 | 0.197 |
| M7 | pre | c4_w1_ema50_px_range8_fresh5 | 94 | 0.355 | -0.023 | 0.378 | 3.5 | 3/3 | 0.365 |
| P7 | nypm | c4_w1_trix8_range8_rise | 703 | 0.112 | -0.065 | 0.177 | 3.4 | 3/3 | 0.146 |
| P7 | close | c4_w1_ha_run_range8_fresh5 | 655 | 0.013 | -0.235 | 0.247 | 3.4 | 3/3 | 0.217 |
| M7 | london | c4_ob_cnt_range8_side | 3923 | 0.035 | -0.098 | 0.133 | 3.4 | 4/4 | 0.100 |
| P7 | close | c4_almaF_slope_range8_fresh5 | 503 | 0.043 | -0.170 | 0.213 | 3.4 | 3/3 | 0.207 |
| P7 | nypm | c4_w1_stoch8_range8_side | 905 | 0.088 | -0.097 | 0.186 | 3.4 | 3/3 | 0.211 |
| A7 | asia | c4_w1_linreg_chan20_range8_fresh5 | 1022 | 0.194 | 0.066 | 0.128 | 3.4 | 4/4 | 0.185 |
| A7 | london | c4_ichiS_tk_range8_side | 1021 | 0.070 | -0.113 | 0.183 | 3.4 | 3/3 | 0.142 |
| A7 | london | c4_w1_ichi_slow_tkkj_range8_side | 1021 | 0.070 | -0.113 | 0.183 | 3.4 | 3/3 | 0.142 |
| P7 | nyam | c4_w1_boll40_walk_range8_rise | 72 | 0.329 | -0.019 | 0.348 | 3.4 | 4/4 | 0.307 |
| A7 | close | c4_w1_uo_range8_rise | 178 | -0.039 | -0.373 | 0.334 | 3.4 | 3/3 | 0.304 |
| P7 | close | c4_w1_rsi2_range8_fresh5 | 566 | 0.029 | -0.190 | 0.218 | 3.4 | 3/3 | 0.239 |
| P7 | nypm | c4_stcF_range8_side | 728 | 0.107 | -0.066 | 0.173 | 3.4 | 3/3 | 0.162 |
| P7 | close | c4_kvoF_range8_sig | 454 | 0.053 | -0.155 | 0.208 | 3.4 | 3/3 | 0.265 |
| P7 | nypm | c4_w1_hma34_px_range8_side | 735 | 0.106 | -0.067 | 0.173 | 3.4 | 3/3 | 0.183 |

## B4 alternate bars: renko16

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2163; |t|>2: 188 (chance expectation ~98 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_renko16.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_rfiltS_dir_renko16_side | 151108 | 0.79 | 0.035 | -0.021 | 0.056 [0.031, 0.081] | 4.4 | 4/4 | 0.075 | 0.078 |
| c4_rfiltS_dir_renko16_hold3 | 145418 | 0.76 | 0.034 | -0.014 | 0.048 [0.024, 0.072] | 3.9 | 4/4 | 0.063 | 0.058 |
| c4_oteS_renko16_against | 11795 | 0.06 | 0.065 | 0.020 | 0.045 [0.018, 0.073] | 3.2 | 4/4 | -0.008 | -0.039 |
| c4_ichiS_thick_renko16_hi | 143375 | 0.75 | 0.030 | 0.000 | 0.030 [0.012, 0.049] | 3.2 | 4/4 | 0.052 | 0.062 |
| c4_w1_linreg_chan50_renko16_eleave | 3295 | 0.02 | 0.092 | 0.022 | 0.070 [0.027, 0.114] | 3.2 | 4/4 | 0.064 | 0.099 |
| c4_mcgS_slope_renko16_side | 176258 | 0.92 | 0.026 | -0.011 | 0.037 [0.013, 0.061] | 3.0 | 4/4 | 0.048 | 0.040 |
| c4_mcgS_px_renko16_side | 176258 | 0.92 | 0.026 | -0.011 | 0.037 [0.013, 0.061] | 3.0 | 4/4 | 0.048 | 0.040 |
| c4_fvg_cnt_renko16_side | 158742 | 0.83 | 0.032 | -0.020 | 0.051 [0.018, 0.085] | 3.0 | 4/4 | -0.011 | -0.009 |
| c4_fvgS_cnt_renko16_side | 158742 | 0.83 | 0.032 | -0.020 | 0.051 [0.018, 0.085] | 3.0 | 4/4 | -0.011 | -0.009 |
| c4_fvgF_cnt_renko16_side | 158742 | 0.83 | 0.032 | -0.020 | 0.051 [0.018, 0.085] | 3.0 | 4/4 | -0.011 | -0.009 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_rfiltS_dir_renko16_against | 40412 | 0.21 | -0.021 | 0.035 | -0.056 [-0.081, -0.031] | -4.4 | 0/4 | -0.075 | -0.078 |
| c4_w1_kama_stack_fast_renko16_against | 20039 | 0.10 | -0.028 | 0.029 | -0.057 [-0.088, -0.026] | -3.6 | 0/4 | -0.044 | -0.095 |
| c4_ichiS_cloud_renko16_against | 15982 | 0.08 | -0.024 | 0.027 | -0.051 [-0.082, -0.020] | -3.2 | 0/4 | -0.046 | -0.030 |
| c4_wtF_renko16_eleave_z2 | 2271 | 0.01 | -0.052 | 0.024 | -0.076 [-0.122, -0.030] | -3.2 | 0/4 | -0.170 | -0.174 |
| c4_wt_renko16_eleave_z2 | 1464 | 0.01 | -0.060 | 0.023 | -0.083 [-0.134, -0.032] | -3.2 | 1/4 | -0.011 | 0.161 |
| c4_w1_ao_renko16_rise | 134322 | 0.70 | 0.016 | 0.038 | -0.022 [-0.036, -0.008] | -3.1 | 0/4 | 0.008 | 0.019 |
| c4_w1_vwmacd_renko16_sig | 131966 | 0.69 | 0.015 | 0.040 | -0.026 [-0.042, -0.009] | -3.0 | 1/4 | -0.033 | -0.027 |
| c4_obS_near_renko16_against | 33095 | 0.17 | 0.001 | 0.027 | -0.027 [-0.045, -0.009] | -2.9 | 2/4 | 0.002 | -0.012 |
| c4_w1_wave_agree_renko16_hold3 | 48606 | 0.25 | 0.005 | 0.029 | -0.023 [-0.039, -0.008] | -2.9 | 0/4 | -0.029 | -0.014 |
| c4_sdF_in_renko16_hold3 | 257 | 0.00 | -0.136 | 0.023 | -0.159 [-0.267, -0.051] | -2.9 | 1/4 | -0.250 | 0.158 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 255 of 12494 session-condition cells pass (chance-level expectation under independence ~154 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_w1_ema200_px_renko16_side | 51008 | 0.110 | 0.092 | 5.0 | 4/4 | 0.079 |
| asia | c4_w1_demarker14_renko16_eagainst | 991 | -0.121 | -0.085 | -3.7 | 0/4 | -0.047 |
| asia | c4_wt_renko16_eleave_z2 | 785 | -0.117 | -0.082 | -3.6 | 0/4 | -0.249 |
| asia | c4_obF_cnt_renko16_side | 42939 | 0.091 | 0.076 | 4.1 | 4/4 | 0.072 |
| asia | c4_ob_cnt_renko16_side | 42939 | 0.091 | 0.076 | 4.1 | 4/4 | 0.072 |
| asia | c4_w1_sma200_px_renko16_side | 50011 | 0.088 | 0.074 | 4.0 | 4/4 | 0.066 |
| close | c4_w1_uo_renko16_divwith | 769 | -0.147 | -0.079 | -3.2 | 0/4 | -0.095 |
| close | c4_w1_vortex7_renko16_divwith | 823 | -0.148 | -0.077 | -3.1 | 0/4 | -0.183 |
| close | c4_smieF_renko16_divwith | 694 | -0.162 | -0.077 | -3.1 | 0/4 | -0.283 |
| close | c4_w1_keltner10_pos_renko16_divwith | 696 | -0.157 | -0.075 | -3.0 | 0/4 | -0.251 |
| close | c4_w1_demarker7_renko16_divwith | 612 | -0.148 | -0.073 | -2.9 | 0/4 | -0.236 |
| close | c4_stc_renko16_divwith | 572 | -0.146 | -0.073 | -2.9 | 0/4 | -0.185 |
| london | c4_w1_kama_stack_fast_renko16_against | 6610 | -0.094 | -0.069 | -3.1 | 0/4 | -0.063 |
| london | c4_rfiltS_dir_renko16_side | 44606 | 0.085 | 0.065 | 3.1 | 4/4 | 0.074 |
| london | c4_rfiltS_dir_renko16_against | 12692 | -0.085 | -0.065 | -3.1 | 0/4 | -0.074 |
| london | c4_rfiltS_dir_renko16_hold3 | 42716 | 0.074 | 0.059 | 2.9 | 4/4 | 0.036 |
| london | c4_w1_vwmacd_renko16_sig | 41224 | -0.046 | -0.041 | -2.6 | 0/4 | -0.050 |
| london | c4_w1_hma8_px_renko16_nodiv | 35921 | 0.040 | 0.037 | 2.7 | 4/4 | 0.054 |
| nyam | c4_qqe_renko16_ewith | 1201 | -0.121 | -0.077 | -3.2 | 0/4 | -0.008 |
| nyam | c4_crsi_renko16_ewith_z1 | 1411 | -0.103 | -0.074 | -3.3 | 0/4 | -0.117 |
| nyam | c4_t3S_px_renko16_divwith | 1730 | 0.093 | 0.062 | 2.6 | 4/4 | 0.123 |
| nyam | c4_pd_renko16_fresh5 | 4194 | 0.070 | 0.061 | 3.7 | 4/4 | 0.052 |
| nyam | c4_lrc_renko16_ewith | 3259 | -0.072 | -0.061 | -3.4 | 0/4 | -0.044 |
| nyam | c4_crsi_renko16_eenter_z1 | 999 | -0.094 | -0.061 | -2.6 | 0/4 | -0.129 |
| nypm | c4_w1_sma8_px_renko16_divwith | 1691 | -0.130 | -0.077 | -3.1 | 0/4 | -0.155 |
| nypm | c4_stPS_renko16_fresh1 | 428 | -0.146 | -0.072 | -2.9 | 0/4 | -0.259 |
| nypm | c4_don55_pos_renko16_eleave | 141 | 0.271 | 0.067 | 3.1 | 4/4 | 0.158 |
| nypm | c4_brkF_near_renko16_against | 1575 | 0.099 | 0.067 | 2.9 | 4/4 | 0.075 |
| nypm | c4_brk_near_renko16_against | 1575 | 0.099 | 0.067 | 2.9 | 4/4 | 0.075 |
| nypm | c4_brkS_in_renko16_against | 775 | 0.116 | 0.067 | 2.7 | 4/4 | 0.185 |
| pre | c4_pd_renko16_ewith | 596 | 0.218 | 0.081 | 3.3 | 4/4 | 0.115 |
| pre | c4_w1_vortex7_renko16_divwith | 613 | -0.242 | -0.080 | -3.4 | 0/4 | -0.249 |
| pre | c4_w1_ao_renko16_rise | 6387 | -0.108 | -0.076 | -3.3 | 0/4 | -0.027 |
| pre | c4_halft_renko16_side | 7325 | -0.115 | -0.076 | -3.2 | 0/4 | -0.008 |
| pre | c4_halft_renko16_against | 1871 | 0.115 | 0.076 | 3.2 | 4/4 | 0.008 |
| pre | c4_smiF_renko16_divwith | 641 | -0.233 | -0.074 | -3.2 | 0/4 | -0.378 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (755 of 63011 cell-conditions pass; chance at t>2.5 alone ~390)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_ema200_px_renko16_side | 11040 | 0.065 | -0.054 | 0.119 | 5.4 | 4/4 | 0.203 |
| K7 | asia | c4_fvgF_cnt_renko16_side | 10162 | 0.068 | -0.038 | 0.106 | 4.9 | 4/4 | 0.199 |
| K7 | asia | c4_fvgS_cnt_renko16_side | 10162 | 0.068 | -0.038 | 0.106 | 4.9 | 4/4 | 0.199 |
| K7 | asia | c4_fvg_cnt_renko16_side | 10162 | 0.068 | -0.038 | 0.106 | 4.9 | 4/4 | 0.199 |
| K7 | asia | c4_w1_donchian50_pos_renko16_side | 12068 | 0.053 | -0.046 | 0.099 | 4.9 | 4/4 | 0.105 |
| K7 | asia | c4_w1_ema100_px_renko16_side | 11965 | 0.055 | -0.051 | 0.106 | 4.7 | 4/4 | 0.213 |
| K7 | asia | c4_don55_pos_renko16_side | 11961 | 0.053 | -0.042 | 0.095 | 4.7 | 4/4 | 0.108 |
| K7 | asia | c4_w1_ema_8_21_stack_renko16_hold3 | 10568 | 0.056 | -0.022 | 0.079 | 4.6 | 4/4 | 0.093 |
| K7 | asia | c4_krS_px_renko16_side | 12958 | 0.047 | -0.049 | 0.095 | 4.6 | 4/4 | 0.142 |
| K7 | asia | c4_ob_cnt_renko16_side | 8790 | 0.075 | -0.026 | 0.101 | 4.6 | 4/4 | 0.099 |
| K7 | asia | c4_obF_cnt_renko16_side | 8790 | 0.075 | -0.026 | 0.101 | 4.6 | 4/4 | 0.099 |
| K7 | asia | c4_qqeS_renko16_side | 11479 | 0.055 | -0.036 | 0.090 | 4.5 | 4/4 | 0.087 |
| K7 | asia | c4_mcgS_px_renko16_side | 13270 | 0.045 | -0.051 | 0.096 | 4.5 | 4/4 | 0.130 |
| K7 | asia | c4_mcgS_slope_renko16_side | 13270 | 0.045 | -0.051 | 0.096 | 4.5 | 4/4 | 0.130 |
| K7 | asia | c4_w1_keltner40_pos_renko16_side | 13096 | 0.046 | -0.050 | 0.096 | 4.5 | 4/4 | 0.125 |
| K7 | asia | c4_w1_ema34_px_renko16_side | 13287 | 0.044 | -0.049 | 0.093 | 4.5 | 4/4 | 0.145 |
| K7 | asia | c4_w1_macd12_26_9_line_renko16_side | 11476 | 0.054 | -0.033 | 0.087 | 4.5 | 4/4 | 0.058 |
| K7 | asia | c4_w1_ao_renko16_side | 11271 | 0.053 | -0.025 | 0.078 | 4.4 | 4/4 | 0.066 |
| K7 | asia | c4_w1_keltner40_pos_renko16_ewith | 9443 | 0.061 | -0.014 | 0.074 | 4.4 | 4/4 | 0.102 |
| K7 | asia | c4_w1_sma50_px_renko16_side | 12477 | 0.049 | -0.043 | 0.093 | 4.4 | 4/4 | 0.182 |
| K7 | asia | c4_w1_di21_renko16_side | 12710 | 0.048 | -0.046 | 0.093 | 4.4 | 4/4 | 0.074 |
| K7 | asia | c4_w1_cci50_renko16_side | 12283 | 0.050 | -0.042 | 0.092 | 4.4 | 4/4 | 0.158 |
| K7 | asia | c4_smieS_renko16_side | 11667 | 0.053 | -0.034 | 0.087 | 4.4 | 4/4 | 0.059 |
| K7 | asia | c4_smie_renko16_side | 12652 | 0.047 | -0.040 | 0.087 | 4.4 | 4/4 | 0.176 |
| K7 | asia | c4_rfiltS_dir_renko16_side | 10079 | 0.061 | -0.024 | 0.085 | 4.4 | 4/4 | 0.029 |
| K7 | asia | c4_w1_rsi21_renko16_side | 13064 | 0.046 | -0.047 | 0.093 | 4.4 | 4/4 | 0.148 |
| K7 | asia | c4_krS_dir_renko16_side | 12553 | 0.049 | -0.045 | 0.093 | 4.3 | 4/4 | 0.133 |
| K7 | asia | c4_rsima21_renko16_side | 13069 | 0.045 | -0.047 | 0.092 | 4.3 | 4/4 | 0.148 |
| K7 | asia | c4_w1_boll40_pctb_renko16_side | 12817 | 0.047 | -0.044 | 0.091 | 4.3 | 4/4 | 0.246 |
| K7 | asia | c4_w1_vwma50_px_renko16_side | 12475 | 0.049 | -0.043 | 0.092 | 4.3 | 4/4 | 0.174 |

## B4 alternate bars: renko8

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2136; |t|>2: 331 (chance expectation ~97 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_renko8.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_fvgS_cnt_renko8_side | 43313 | 0.90 | 0.048 | -0.011 | 0.059 [0.033, 0.086] | 4.4 | 4/4 | 0.046 | 0.068 |
| c4_fvgF_cnt_renko8_side | 43313 | 0.90 | 0.048 | -0.011 | 0.059 [0.033, 0.086] | 4.4 | 4/4 | 0.046 | 0.068 |
| c4_fvg_cnt_renko8_side | 43313 | 0.90 | 0.048 | -0.011 | 0.059 [0.033, 0.086] | 4.4 | 4/4 | 0.046 | 0.068 |
| c4_sdS_cnt_renko8_side | 39922 | 0.83 | 0.050 | 0.004 | 0.047 [0.026, 0.068] | 4.4 | 3/4 | 0.018 | 0.034 |
| c4_sd_cnt_renko8_side | 40863 | 0.85 | 0.050 | 0.001 | 0.049 [0.027, 0.070] | 4.4 | 2/4 | -0.003 | 0.013 |
| c4_kvoF_renko8_divwith | 4349 | 0.09 | 0.097 | 0.037 | 0.060 [0.032, 0.089] | 4.2 | 4/4 | 0.054 | 0.063 |
| c4_sdF_cnt_renko8_side | 40879 | 0.85 | 0.049 | 0.003 | 0.046 [0.024, 0.068] | 4.1 | 2/4 | -0.004 | 0.004 |
| c4_rfiltS_renko8_rise | 26903 | 0.56 | 0.057 | 0.024 | 0.032 [0.016, 0.049] | 3.9 | 4/4 | 0.036 | 0.044 |
| c4_lrcS_slope_renko8_side | 37569 | 0.78 | 0.051 | 0.013 | 0.037 [0.018, 0.057] | 3.8 | 4/4 | 0.039 | 0.020 |
| c4_lrcS_renko8_fresh5 | 9338 | 0.19 | 0.073 | 0.035 | 0.038 [0.018, 0.058] | 3.7 | 3/4 | 0.036 | 0.055 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_w1_boll10_walk_renko8_nodiv | 42981 | 0.89 | 0.037 | 0.082 | -0.045 [-0.070, -0.020] | -3.5 | 0/4 | -0.004 | 0.014 |
| c4_w1_stoch14_renko8_nodiv | 44707 | 0.92 | 0.038 | 0.089 | -0.051 [-0.081, -0.021] | -3.3 | 0/4 | -0.020 | -0.003 |
| c4_w1_vwma200_px_renko8_nodiv | 46574 | 0.96 | 0.040 | 0.111 | -0.071 [-0.114, -0.029] | -3.3 | 1/4 | -0.092 | 0.002 |
| c4_w1_kama_stack_slow_renko8_against | 4997 | 0.10 | 0.003 | 0.047 | -0.043 [-0.069, -0.017] | -3.2 | 0/4 | -0.024 | -0.043 |
| c4_w1_ema_stack_slow_renko8_against | 3486 | 0.07 | -0.003 | 0.046 | -0.049 [-0.079, -0.019] | -3.2 | 1/4 | 0.020 | 0.066 |
| c4_w1_trendcolor_renko8_nodiv | 43899 | 0.91 | 0.038 | 0.082 | -0.043 [-0.071, -0.016] | -3.1 | 0/4 | -0.042 | -0.065 |
| c4_w1_stoch8_renko8_nodiv | 44574 | 0.92 | 0.039 | 0.083 | -0.044 [-0.074, -0.015] | -2.9 | 0/4 | -0.006 | 0.009 |
| c4_fvgF_in_renko8_side | 15643 | 0.32 | 0.026 | 0.050 | -0.025 [-0.042, -0.007] | -2.8 | 0/4 | -0.032 | -0.044 |
| c4_fvgS_in_renko8_side | 15643 | 0.32 | 0.026 | 0.050 | -0.025 [-0.042, -0.007] | -2.8 | 0/4 | -0.032 | -0.044 |
| c4_fvg_in_renko8_side | 15643 | 0.32 | 0.026 | 0.050 | -0.025 [-0.042, -0.007] | -2.8 | 0/4 | -0.032 | -0.044 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 292 of 11709 session-condition cells pass (chance-level expectation under independence ~145 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_w1_vwma200_px_renko8_side | 14975 | 0.089 | 0.075 | 4.1 | 4/4 | 0.022 |
| asia | c4_w1_kama_stack_slow_renko8_against | 1938 | -0.085 | -0.073 | -4.2 | 0/4 | -0.066 |
| asia | c4_fvgF_cnt_renko8_side | 14669 | 0.082 | 0.071 | 4.1 | 4/4 | 0.017 |
| asia | c4_fvgS_cnt_renko8_side | 14669 | 0.082 | 0.071 | 4.1 | 4/4 | 0.017 |
| asia | c4_fvg_cnt_renko8_side | 14669 | 0.082 | 0.071 | 4.1 | 4/4 | 0.017 |
| asia | c4_w1_cmf10_renko8_divwith | 1338 | 0.088 | 0.070 | 3.5 | 4/4 | 0.053 |
| close | c4_kvoS_renko8_sig | 1495 | -0.147 | -0.094 | -3.9 | 0/3 | -0.170 |
| close | c4_lrcF_slope_renko8_rise | 1523 | -0.137 | -0.087 | -3.6 | 0/3 | -0.179 |
| close | c4_w1_linreg_slope50_renko8_rise | 1523 | -0.137 | -0.087 | -3.6 | 0/3 | -0.179 |
| close | c4_w1_adx7_renko8_lo_z1 | 413 | 0.163 | 0.086 | 3.5 | 3/3 | 0.216 |
| close | c4_w1_adx7_renko8_hi | 2033 | -0.163 | -0.086 | -3.5 | 0/3 | -0.216 |
| close | c4_w1_macd19_39_9_hist_renko8_side | 1632 | -0.139 | -0.086 | -3.5 | 0/3 | -0.135 |
| london | c4_w1_kama8_px_renko8_divwith | 522 | -0.161 | -0.100 | -4.1 | 0/4 | -0.079 |
| london | c4_w1_aroon14_renko8_eagainst | 725 | -0.122 | -0.084 | -3.6 | 0/4 | -0.165 |
| london | c4_w1_aroon25_renko8_eagainst | 521 | -0.104 | -0.064 | -2.7 | 0/4 | -0.141 |
| london | c4_stPS_renko8_side | 12707 | 0.071 | 0.060 | 3.3 | 4/4 | 0.062 |
| london | c4_stPS_renko8_against | 1987 | -0.071 | -0.060 | -3.3 | 0/4 | -0.062 |
| london | c4_w1_vortex21_renko8_divwith | 807 | -0.085 | -0.060 | -2.6 | 0/4 | -0.042 |
| nyam | c4_w1_keltner20_pos_renko8_eleave | 634 | 0.146 | 0.084 | 3.4 | 4/4 | 0.022 |
| nyam | c4_w1_uo_renko8_eleave | 356 | 0.169 | 0.073 | 2.9 | 4/4 | 0.093 |
| nyam | c4_pdS_renko8_rise | 3343 | -0.083 | -0.070 | -3.9 | 0/4 | -0.022 |
| nyam | c4_w1_keltner40_pos_renko8_eleave | 358 | 0.156 | 0.068 | 2.7 | 4/4 | 0.001 |
| nyam | c4_w1_donchian20_pos_renko8_eleave | 551 | 0.122 | 0.066 | 2.7 | 4/4 | 0.016 |
| nyam | c4_don20_pos_renko8_eleave | 551 | 0.122 | 0.066 | 2.7 | 4/4 | 0.016 |
| nypm | c4_sslhyb_renko8_fresh1 | 422 | 0.164 | 0.089 | 3.6 | 4/4 | 0.122 |
| nypm | c4_obS_dres_renko8_hi | 2220 | 0.129 | 0.087 | 3.7 | 4/4 | 0.169 |
| nypm | c4_mcmf_renko8_divwith | 243 | 0.200 | 0.080 | 3.3 | 3/3 | 0.095 |
| nypm | c4_zlemaS_px_renko8_fresh1 | 404 | 0.148 | 0.078 | 3.1 | 4/4 | 0.132 |
| nypm | c4_almaF_px_renko8_divwith | 1050 | 0.105 | 0.075 | 3.3 | 4/4 | 0.096 |
| nypm | c4_w1_hma8_px_renko8_divwith | 1100 | 0.104 | 0.075 | 3.3 | 4/4 | 0.081 |
| pre | c4_w1_kama8_px_renko8_nodiv | 1282 | -0.346 | -0.119 | -5.0 | 0/3 | -0.237 |
| pre | c4_sdS_cnt_renko8_side | 1245 | 0.257 | 0.090 | 3.8 | 3/3 | 0.072 |
| pre | c4_w1_demarker14_renko8_rise | 425 | 0.195 | 0.087 | 3.5 | 3/3 | 0.259 |
| pre | c4_w1_atr_pct100_renko8_rise | 440 | -0.188 | -0.083 | -3.4 | 0/3 | -0.151 |
| pre | c4_w1_atr_pct250_renko8_rise | 441 | -0.185 | -0.082 | -3.3 | 0/3 | -0.151 |
| pre | c4_w1_threebar_pivot_renko8_against | 245 | -0.235 | -0.081 | -3.4 | 0/3 | -0.193 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (287 of 47404 cell-conditions pass; chance at t>2.5 alone ~293)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_lrcS_slope_renko8_side | 3253 | 0.079 | -0.029 | 0.107 | 3.9 | 4/4 | 0.098 |
| K7 | asia | c4_w1_vwma200_px_renko8_side | 4132 | 0.062 | -0.092 | 0.154 | 3.8 | 4/4 | 0.210 |
| K7 | asia | c4_w1_sma200_px_renko8_side | 4143 | 0.062 | -0.092 | 0.154 | 3.8 | 4/4 | 0.249 |
| A7 | asia | c4_obF_in_renko8_against | 242 | 0.316 | 0.100 | 0.216 | 3.6 | 3/4 | 0.228 |
| A7 | asia | c4_ob_in_renko8_against | 242 | 0.316 | 0.100 | 0.216 | 3.6 | 3/4 | 0.228 |
| P7 | asia | c4_crsiF_renko8_divwith | 917 | 0.163 | 0.054 | 0.110 | 3.6 | 3/4 | 0.123 |
| M7 | london | c4_w1_ichi_slow_lag_renko8_nodiv | 4437 | 0.023 | -0.330 | 0.353 | 3.6 | 3/3 | 0.278 |
| K7 | asia | c4_w1_ema_stack_slow_renko8_hold3 | 3321 | 0.074 | -0.024 | 0.099 | 3.6 | 3/4 | 0.096 |
| K7 | nyam | c4_w1_boll40_pctb_renko8_ewith | 69 | 0.366 | -0.009 | 0.375 | 3.6 | 4/4 | 0.046 |
| K7 | london | c4_sd_cnt_renko8_side | 3024 | 0.034 | -0.111 | 0.145 | 3.6 | 3/4 | 0.014 |
| K7 | asia | c4_fvgS_cnt_renko8_side | 4080 | 0.061 | -0.070 | 0.132 | 3.5 | 4/4 | 0.089 |
| K7 | asia | c4_fvg_cnt_renko8_side | 4080 | 0.061 | -0.070 | 0.132 | 3.5 | 4/4 | 0.089 |
| K7 | asia | c4_fvgF_cnt_renko8_side | 4080 | 0.061 | -0.070 | 0.132 | 3.5 | 4/4 | 0.089 |
| K7 | asia | c4_w1_ema_stack_slow_renko8_side | 3404 | 0.072 | -0.025 | 0.097 | 3.5 | 3/4 | 0.084 |
| A7 | london | c4_turt20_renko8_side | 1022 | 0.071 | -0.116 | 0.187 | 3.5 | 3/3 | 0.165 |
| A7 | close | c4_w1_vwma8_px_renko8_fresh5 | 163 | -0.024 | -0.364 | 0.340 | 3.4 | 3/3 | 0.426 |
| A7 | london | c4_turt20_renko8_hold3 | 915 | 0.080 | -0.094 | 0.174 | 3.4 | 3/3 | 0.175 |
| P7 | nyam | c4_rfiltS_renko8_rise | 919 | 0.067 | -0.065 | 0.131 | 3.4 | 4/4 | 0.113 |
| P7 | nypm | c4_w1_stochrsi8_renko8_rise | 548 | 0.131 | -0.044 | 0.175 | 3.4 | 3/3 | 0.194 |
| P7 | nypm | c4_srsiF_renko8_rise | 547 | 0.131 | -0.044 | 0.174 | 3.4 | 3/3 | 0.194 |
| K7 | london | c4_sdF_cnt_renko8_side | 3033 | 0.033 | -0.105 | 0.138 | 3.3 | 4/4 | 0.016 |
| A7 | london | c4_w1_sma_stack_fast_renko8_side | 957 | 0.075 | -0.099 | 0.174 | 3.3 | 3/3 | 0.172 |
| M7 | london | c4_w1_linreg_slope50_renko8_side | 3625 | 0.040 | -0.071 | 0.111 | 3.3 | 4/4 | 0.129 |
| M7 | london | c4_lrcF_slope_renko8_side | 3625 | 0.040 | -0.071 | 0.111 | 3.3 | 4/4 | 0.129 |
| K7 | nyam | c4_w1_stoch21_renko8_eleave | 85 | 0.311 | -0.010 | 0.321 | 3.3 | 3/3 | 0.182 |
| M7 | london | c4_don55_pos_renko8_side | 4039 | 0.033 | -0.109 | 0.142 | 3.3 | 4/4 | 0.133 |
| K7 | asia | c4_ob_cnt_renko8_side | 3683 | 0.067 | -0.034 | 0.101 | 3.3 | 3/4 | 0.106 |
| K7 | asia | c4_obF_cnt_renko8_side | 3683 | 0.067 | -0.034 | 0.101 | 3.3 | 3/4 | 0.106 |
| P7 | london | c4_w1_kama_stack_slow_renko8_hold3 | 2144 | 0.095 | 0.007 | 0.088 | 3.3 | 4/4 | 0.025 |
| M7 | london | c4_stPS_renko8_side | 3907 | 0.035 | -0.092 | 0.126 | 3.3 | 4/4 | 0.143 |

## B4 alternate bars: tick2000

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2259; |t|>2: 278 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_tick2000.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_w1_rsi21_tick2000_ewith | 8526 | 0.04 | 0.154 | 0.017 | 0.137 [0.074, 0.201] | 4.2 | 4/4 | 0.218 | 0.235 |
| c4_rsima21_tick2000_ewith | 8543 | 0.04 | 0.153 | 0.017 | 0.137 [0.073, 0.200] | 4.2 | 4/4 | 0.218 | 0.235 |
| c4_tsiS_tick2000_ewith | 21396 | 0.11 | 0.100 | 0.013 | 0.087 [0.041, 0.133] | 3.7 | 4/4 | 0.138 | 0.234 |
| c4_qqeS_tick2000_ewith | 5219 | 0.03 | 0.179 | 0.018 | 0.161 [0.075, 0.247] | 3.7 | 4/4 | 0.194 | 0.280 |
| c4_ker_dir_tick2000_ewith | 38374 | 0.20 | 0.061 | 0.013 | 0.048 [0.023, 0.074] | 3.7 | 4/4 | 0.028 | 0.015 |
| c4_rsima21_tick2000_eenter | 4204 | 0.02 | 0.153 | 0.020 | 0.133 [0.060, 0.207] | 3.6 | 4/4 | 0.291 | 0.376 |
| c4_w1_rsi21_tick2000_eenter | 4203 | 0.02 | 0.153 | 0.020 | 0.133 [0.060, 0.206] | 3.6 | 4/4 | 0.291 | 0.376 |
| c4_smieS_tick2000_ewith | 23057 | 0.12 | 0.090 | 0.014 | 0.077 [0.034, 0.120] | 3.5 | 4/4 | 0.134 | 0.231 |
| c4_ichiF_chikou_tick2000_side | 145472 | 0.76 | 0.033 | -0.010 | 0.043 [0.018, 0.069] | 3.3 | 4/4 | 0.018 | 0.010 |
| c4_lrcS_tick2000_ewith | 30426 | 0.16 | 0.079 | 0.011 | 0.067 [0.027, 0.107] | 3.3 | 4/4 | 0.130 | 0.115 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_almaF_slope_tick2000_fresh5 | 127934 | 0.67 | 0.012 | 0.045 | -0.034 [-0.053, -0.015] | -3.5 | 0/4 | -0.010 | 0.004 |
| c4_ichiF_chikou_tick2000_against | 45549 | 0.24 | -0.010 | 0.033 | -0.043 [-0.069, -0.018] | -3.3 | 0/4 | -0.018 | -0.009 |
| c4_don20_pos_tick2000_eagainst | 942 | 0.00 | -0.097 | 0.023 | -0.120 [-0.192, -0.049] | -3.3 | 0/4 | -0.078 | -0.114 |
| c4_w1_donchian20_pos_tick2000_eagainst | 942 | 0.00 | -0.097 | 0.023 | -0.120 [-0.192, -0.049] | -3.3 | 0/4 | -0.078 | -0.114 |
| c4_w1_ha_run_tick2000_fresh5 | 121484 | 0.63 | 0.011 | 0.044 | -0.033 [-0.052, -0.013] | -3.3 | 0/4 | -0.013 | -0.007 |
| c4_alma_px_tick2000_fresh5 | 143612 | 0.75 | 0.015 | 0.047 | -0.033 [-0.053, -0.013] | -3.2 | 0/4 | -0.001 | 0.042 |
| c4_w1_cci14_tick2000_eagainst_z1 | 7820 | 0.04 | -0.033 | 0.025 | -0.058 [-0.093, -0.023] | -3.2 | 0/4 | -0.011 | -0.037 |
| c4_w1_pat_inside_tick2000_hi | 16292 | 0.09 | -0.015 | 0.026 | -0.041 [-0.066, -0.016] | -3.2 | 0/4 | -0.021 | -0.036 |
| c4_t3_px_tick2000_fresh5 | 123289 | 0.64 | 0.011 | 0.043 | -0.032 [-0.052, -0.012] | -3.2 | 0/4 | -0.015 | -0.002 |
| c4_chop_tick2000_hi_z1 | 26560 | 0.14 | -0.013 | 0.029 | -0.042 [-0.069, -0.015] | -3.1 | 0/4 | -0.026 | -0.004 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 298 of 13131 session-condition cells pass (chance-level expectation under independence ~162 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_w1_uo_tick2000_eagainst | 305 | -0.249 | -0.110 | -4.4 | 0/4 | -0.456 |
| asia | c4_lrcS_tick2000_ewith | 11049 | 0.141 | 0.105 | 4.9 | 4/4 | 0.289 |
| asia | c4_w1_rsi21_tick2000_ewith | 3747 | 0.183 | 0.094 | 3.8 | 4/4 | 0.259 |
| asia | c4_rsima21_tick2000_ewith | 3763 | 0.181 | 0.094 | 3.7 | 4/4 | 0.259 |
| asia | c4_w1_willr21_tick2000_eagainst | 3817 | -0.113 | -0.086 | -4.1 | 0/4 | -0.007 |
| asia | c4_lrc_tick2000_eagainst | 1742 | -0.126 | -0.086 | -3.7 | 0/4 | -0.190 |
| close | c4_w1_boll40_walk_tick2000_side | 731 | 0.186 | 0.081 | 3.3 | 4/4 | 0.221 |
| close | c4_fvg_near_tick2000_hold3 | 1802 | 0.141 | 0.079 | 3.2 | 4/4 | 0.153 |
| close | c4_sebF_tick2000_fresh5 | 8164 | -0.094 | -0.074 | -3.5 | 0/4 | -0.301 |
| close | c4_w1_aroon50_tick2000_nodiv | 11832 | 0.116 | 0.070 | 2.8 | 4/4 | 0.160 |
| close | c4_brkF_in_tick2000_side | 850 | 0.136 | 0.067 | 2.7 | 4/4 | 0.109 |
| close | c4_obF_near_tick2000_hold3 | 1508 | -0.131 | -0.067 | -2.7 | 0/4 | -0.108 |
| london | c4_w1_boll10_pctb_tick2000_eagainst | 780 | -0.139 | -0.077 | -3.1 | 0/4 | -0.149 |
| london | c4_ifvgS_in_tick2000_side | 1746 | 0.146 | 0.072 | 2.9 | 4/4 | 0.351 |
| london | c4_w1_willr7_tick2000_eagainst | 1818 | -0.108 | -0.071 | -3.0 | 0/4 | -0.027 |
| london | c4_ifvgF_in_tick2000_side | 2778 | 0.114 | 0.067 | 2.7 | 4/4 | 0.270 |
| london | c4_ifvgS_in_tick2000_hold3 | 501 | 0.241 | 0.064 | 2.9 | 4/4 | 0.466 |
| london | c4_wtS_tick2000_ewith_z2 | 9263 | 0.101 | 0.063 | 2.6 | 4/4 | 0.150 |
| nyam | c4_nwe_tick2000_eenter | 171 | -0.385 | -0.088 | -4.2 | 0/4 | -0.243 |
| nyam | c4_nwe_tick2000_ewith | 183 | -0.315 | -0.086 | -3.8 | 0/4 | -0.032 |
| nyam | c4_kerF_dir_tick2000_eagainst | 784 | 0.122 | 0.075 | 3.1 | 4/4 | 0.063 |
| nyam | c4_stA21_tick2000_fresh1 | 965 | -0.107 | -0.071 | -3.0 | 0/4 | -0.075 |
| nyam | c4_chochS_tick2000_fresh1 | 649 | -0.125 | -0.069 | -2.8 | 0/4 | -0.253 |
| nyam | c4_smieF_tick2000_eleave | 982 | -0.108 | -0.063 | -2.6 | 0/4 | -0.270 |
| nypm | c4_sd_cnt_tick2000_fresh5 | 1148 | -0.205 | -0.094 | -3.8 | 0/4 | -0.135 |
| nypm | c4_sdflip_in_tick2000_side | 2601 | -0.108 | -0.078 | -3.5 | 0/4 | -0.010 |
| nypm | c4_sdflipS_in_tick2000_side | 1941 | -0.123 | -0.077 | -3.2 | 0/4 | -0.046 |
| nypm | c4_sdF_cnt_tick2000_fresh5 | 1362 | -0.157 | -0.073 | -2.9 | 0/4 | -0.213 |
| nypm | c4_w1_linreg_chan50_tick2000_eleave | 295 | 0.266 | 0.069 | 3.1 | 4/4 | 0.307 |
| nypm | c4_pdF_tick2000_ewith | 1297 | 0.129 | 0.069 | 2.8 | 4/4 | 0.086 |
| pre | c4_crsiF_tick2000_eleave | 241 | 0.403 | 0.075 | 3.9 | 4/4 | 0.073 |
| pre | c4_rsima14_tick2000_nodiv | 7912 | 0.219 | 0.065 | 2.9 | 4/4 | 0.018 |
| pre | c4_w1_rsi14_tick2000_nodiv | 7912 | 0.219 | 0.065 | 2.9 | 4/4 | 0.018 |
| pre | c4_qqeF_tick2000_eenter | 806 | -0.201 | -0.060 | -2.6 | 0/4 | -0.259 |
| pre | c4_alma_x_tick2000_nodiv | 7946 | 0.205 | 0.059 | 2.6 | 4/4 | 0.368 |
| pre | c4_elderS_bear_tick2000_rise | 5501 | 0.078 | 0.057 | 2.5 | 4/4 | 0.123 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (785 of 65947 cell-conditions pass; chance at t>2.5 alone ~408)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_eom14_tick2000_side | 8311 | 0.082 | -0.028 | 0.110 | 5.4 | 4/4 | 0.126 |
| K7 | asia | c4_ichiF_chikou_tick2000_side | 8706 | 0.079 | -0.030 | 0.109 | 5.3 | 4/4 | 0.101 |
| K7 | asia | c4_w1_boll20_pctb_tick2000_side | 8889 | 0.079 | -0.033 | 0.112 | 5.3 | 4/4 | 0.102 |
| K7 | asia | c4_w1_force13_tick2000_side | 9121 | 0.075 | -0.032 | 0.107 | 5.3 | 4/4 | 0.089 |
| K7 | asia | c4_lrcS_tick2000_ewith | 1838 | 0.169 | 0.011 | 0.158 | 5.2 | 4/4 | 0.323 |
| K7 | asia | c4_w1_willr14_tick2000_side | 9043 | 0.079 | -0.036 | 0.115 | 5.2 | 4/4 | 0.111 |
| K7 | asia | c4_mcg_px_tick2000_side | 9120 | 0.076 | -0.033 | 0.109 | 5.2 | 4/4 | 0.102 |
| K7 | asia | c4_mcg_slope_tick2000_side | 9120 | 0.076 | -0.033 | 0.109 | 5.2 | 4/4 | 0.102 |
| K7 | asia | c4_w1_kama34_px_tick2000_side | 8735 | 0.079 | -0.030 | 0.109 | 5.1 | 4/4 | 0.167 |
| K7 | asia | c4_w1_keltner10_pos_tick2000_side | 9351 | 0.072 | -0.030 | 0.102 | 5.1 | 4/4 | 0.083 |
| K7 | asia | c4_krF_px_tick2000_side | 9117 | 0.075 | -0.032 | 0.107 | 5.1 | 4/4 | 0.114 |
| K7 | asia | c4_w1_vwma21_px_tick2000_side | 8844 | 0.077 | -0.030 | 0.108 | 5.1 | 4/4 | 0.108 |
| K7 | asia | c4_ichiF_kj_tick2000_side | 9067 | 0.076 | -0.032 | 0.109 | 5.0 | 4/4 | 0.121 |
| K7 | asia | c4_w1_cmo9_tick2000_ewith | 2545 | 0.131 | 0.013 | 0.119 | 5.0 | 4/4 | 0.136 |
| K7 | asia | c4_w1_sma21_px_tick2000_side | 8871 | 0.077 | -0.030 | 0.107 | 5.0 | 4/4 | 0.115 |
| K7 | asia | c4_w1_ema21_px_tick2000_side | 8996 | 0.077 | -0.032 | 0.109 | 5.0 | 4/4 | 0.132 |
| K7 | asia | c4_w1_rsi7_tick2000_side | 9170 | 0.073 | -0.030 | 0.103 | 5.0 | 4/4 | 0.090 |
| K7 | asia | c4_w1_keltner20_pos_tick2000_side | 9013 | 0.076 | -0.031 | 0.107 | 5.0 | 4/4 | 0.112 |
| K7 | asia | c4_rsima7_tick2000_side | 9180 | 0.073 | -0.029 | 0.103 | 4.9 | 4/4 | 0.090 |
| K7 | asia | c4_w1_ichi_fast_lag_tick2000_side | 7517 | 0.083 | -0.017 | 0.100 | 4.9 | 4/4 | 0.104 |
| K7 | asia | c4_nweS_tick2000_side | 8828 | 0.078 | -0.032 | 0.110 | 4.9 | 4/4 | 0.137 |
| K7 | asia | c4_almaS_px_tick2000_side | 8908 | 0.076 | -0.029 | 0.106 | 4.9 | 4/4 | 0.097 |
| K7 | asia | c4_w1_kama50_px_tick2000_side | 8566 | 0.079 | -0.027 | 0.106 | 4.9 | 4/4 | 0.196 |
| K7 | asia | c4_w1_donchian20_pos_tick2000_side | 8867 | 0.075 | -0.027 | 0.103 | 4.8 | 4/4 | 0.087 |
| K7 | asia | c4_don20_pos_tick2000_side | 8867 | 0.075 | -0.027 | 0.103 | 4.8 | 4/4 | 0.087 |
| K7 | asia | c4_w1_ema8_px_tick2000_side | 9487 | 0.069 | -0.028 | 0.098 | 4.8 | 4/4 | 0.079 |
| P7 | nypm | c4_lrc_tick2000_eagainst | 63 | 0.534 | -0.019 | 0.553 | 4.8 | 4/4 | 0.859 |
| K7 | asia | c4_rvi_tick2000_side | 8209 | 0.081 | -0.024 | 0.105 | 4.8 | 4/4 | 0.124 |
| K7 | asia | c4_mcgF_slope_tick2000_side | 9447 | 0.069 | -0.028 | 0.097 | 4.8 | 4/4 | 0.087 |
| K7 | asia | c4_mcgF_px_tick2000_side | 9447 | 0.069 | -0.028 | 0.097 | 4.8 | 4/4 | 0.087 |

## B4 alternate bars: vol2000

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2244; |t|>2: 1296 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_vol2000.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_lrcS_vol2000_ewith | 9974 | 0.21 | 0.141 | 0.016 | 0.126 [0.106, 0.145] | 12.5 | 3/4 | 0.152 | 0.164 |
| c4_smieS_vol2000_ewith | 6721 | 0.14 | 0.147 | 0.025 | 0.121 [0.099, 0.144] | 10.4 | 3/4 | 0.185 | 0.236 |
| c4_w1_supertrend_14_4_vol2000_side | 34278 | 0.71 | 0.069 | -0.023 | 0.092 [0.074, 0.110] | 10.3 | 3/4 | 0.104 | 0.080 |
| c4_tsiS_vol2000_ewith | 6384 | 0.13 | 0.148 | 0.026 | 0.121 [0.098, 0.145] | 10.2 | 3/4 | 0.171 | 0.239 |
| c4_w1_rsi21_vol2000_ewith | 2547 | 0.05 | 0.208 | 0.033 | 0.175 [0.140, 0.210] | 9.8 | 3/4 | 0.231 | 0.141 |
| c4_fractal_alli_vol2000_hold3 | 28355 | 0.59 | 0.076 | -0.005 | 0.081 [0.065, 0.097] | 9.8 | 4/4 | 0.065 | 0.074 |
| c4_rsima21_vol2000_ewith | 2547 | 0.05 | 0.208 | 0.033 | 0.175 [0.140, 0.210] | 9.8 | 3/4 | 0.231 | 0.141 |
| c4_tsi_vol2000_ewith | 11033 | 0.23 | 0.115 | 0.021 | 0.094 [0.075, 0.113] | 9.7 | 3/4 | 0.108 | 0.141 |
| c4_w1_ema_stack_fast_vol2000_hold3 | 28809 | 0.60 | 0.075 | -0.005 | 0.080 [0.064, 0.096] | 9.7 | 3/4 | 0.057 | 0.032 |
| c4_w1_ema_8_21_34_stack_vol2000_hold3 | 28809 | 0.60 | 0.075 | -0.005 | 0.080 [0.064, 0.096] | 9.7 | 3/4 | 0.057 | 0.032 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_kerS_abs_vol2000_lo_z1 | 37209 | 0.77 | 0.023 | 0.107 | -0.085 [-0.104, -0.066] | -8.8 | 1/4 | -0.123 | -0.166 |
| c4_stA_vol2000_against | 12881 | 0.27 | -0.013 | 0.062 | -0.076 [-0.094, -0.058] | -8.3 | 1/4 | -0.042 | -0.014 |
| c4_ker_dir_vol2000_divwith | 5825 | 0.12 | -0.045 | 0.054 | -0.100 [-0.124, -0.075] | -8.1 | 1/4 | -0.145 | -0.208 |
| c4_stPS_vol2000_against | 16143 | 0.33 | -0.004 | 0.065 | -0.069 [-0.086, -0.052] | -8.0 | 1/4 | -0.057 | -0.003 |
| c4_hiloS_vol2000_against | 9692 | 0.20 | -0.021 | 0.058 | -0.079 [-0.099, -0.060] | -7.9 | 0/4 | -0.032 | -0.050 |
| c4_fractal_brk_vol2000_against | 12221 | 0.25 | -0.012 | 0.061 | -0.072 [-0.091, -0.054] | -7.8 | 0/4 | -0.067 | -0.064 |
| c4_stAS_vol2000_against | 13849 | 0.29 | -0.007 | 0.062 | -0.069 [-0.086, -0.051] | -7.6 | 1/4 | -0.052 | -0.028 |
| c4_w1_cci14_vol2000_divwith | 5571 | 0.12 | -0.043 | 0.053 | -0.096 [-0.121, -0.071] | -7.6 | 1/4 | -0.102 | -0.098 |
| c4_rfilt_dir_vol2000_against | 11587 | 0.24 | -0.012 | 0.059 | -0.071 [-0.090, -0.053] | -7.5 | 2/4 | 0.003 | 0.035 |
| c4_structS_vol2000_against | 14391 | 0.30 | -0.004 | 0.062 | -0.066 [-0.084, -0.049] | -7.4 | 1/4 | -0.074 | -0.080 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 1291 of 12327 session-condition cells pass (chance-level expectation under independence ~152 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_w1_keltner10_pos_vol2000_eagainst | 370 | -0.259 | -0.149 | -6.0 | 0/4 | -0.318 |
| asia | c4_w1_mfi14_vol2000_eenter | 385 | 0.253 | 0.146 | 5.9 | 4/4 | 0.270 |
| asia | c4_sslhyb_vol2000_hold3 | 9006 | 0.156 | 0.146 | 11.7 | 4/4 | 0.168 |
| asia | c4_w1_ichi_fast_lag_vol2000_nodiv | 16096 | 0.216 | 0.138 | 5.7 | 4/4 | 0.115 |
| asia | c4_eqpool_up_vol2000_hi | 2017 | 0.194 | 0.134 | 5.8 | 4/4 | 0.205 |
| asia | c4_w1_supertrend_10_3_vol2000_nodiv | 16434 | 0.371 | 0.134 | 5.6 | 3/3 | 0.193 |
| close | c4_pdS_vol2000_eleave | 153 | 0.425 | 0.136 | 5.8 | 3/3 | 0.307 |
| close | c4_ichiS_futcloud_vol2000_against | 536 | -0.217 | -0.127 | -5.1 | 0/3 | -0.204 |
| close | c4_ichiS_futcloud_vol2000_side | 1897 | 0.214 | 0.126 | 5.1 | 3/3 | 0.183 |
| close | c4_rfiltS_dir_vol2000_side | 1865 | 0.211 | 0.125 | 5.1 | 3/3 | 0.109 |
| close | c4_rfiltS_dir_vol2000_against | 581 | -0.211 | -0.125 | -5.1 | 0/3 | -0.109 |
| close | c4_w1_trix30_vol2000_fresh5 | 106 | 0.411 | 0.122 | 5.3 | 3/3 | 0.547 |
| london | c4_w1_psar_0.01_vol2000_divwith | 1930 | -0.201 | -0.170 | -9.4 | 0/4 | -0.275 |
| london | c4_w1_donchian20_pos_vol2000_divwith | 2009 | -0.173 | -0.147 | -8.2 | 0/4 | -0.178 |
| london | c4_w1_uo_vol2000_divwith | 2158 | -0.170 | -0.146 | -8.4 | 0/4 | -0.145 |
| london | c4_w1_willr21_vol2000_divwith | 1980 | -0.163 | -0.138 | -7.7 | 0/4 | -0.151 |
| london | c4_smiF_vol2000_divwith | 2002 | -0.161 | -0.137 | -7.7 | 0/4 | -0.214 |
| london | c4_w1_donchian10_pos_vol2000_divwith | 2277 | -0.154 | -0.132 | -7.7 | 0/4 | -0.108 |
| nyam | c4_eqpool_dnS_vol2000_rise | 898 | 0.174 | 0.089 | 3.6 | 4/4 | 0.139 |
| nyam | c4_hullS_vol2000_fresh5 | 1074 | -0.118 | -0.086 | -3.9 | 0/4 | -0.070 |
| nyam | c4_w1_cmo14_vol2000_fresh5 | 2776 | -0.093 | -0.078 | -4.3 | 0/4 | -0.033 |
| nyam | c4_turt20_vol2000_against | 555 | -0.121 | -0.076 | -3.1 | 0/4 | -0.244 |
| nyam | c4_sdF_cnt_vol2000_fresh5 | 520 | -0.124 | -0.073 | -3.0 | 0/4 | -0.213 |
| nyam | c4_stPF_vol2000_fresh1 | 294 | -0.150 | -0.072 | -2.9 | 0/4 | -0.169 |
| nypm | c4_sd_dres_vol2000_hi | 647 | 0.200 | 0.123 | 5.1 | 4/4 | 0.289 |
| nypm | c4_w1_sma100_px_vol2000_nodiv | 4314 | -0.183 | -0.115 | -4.8 | 0/4 | -0.220 |
| nypm | c4_w1_vwma100_px_vol2000_nodiv | 4314 | -0.183 | -0.115 | -4.8 | 0/4 | -0.220 |
| nypm | c4_sdF_near_vol2000_hold3 | 110 | 0.410 | 0.113 | 5.1 | 3/3 | 0.503 |
| nypm | c4_hiloF_vol2000_hold3 | 3242 | 0.131 | 0.101 | 4.8 | 4/4 | 0.084 |
| nypm | c4_w1_cci20_vol2000_eleave_z1 | 280 | -0.226 | -0.100 | -4.0 | 0/3 | -0.250 |
| pre | c4_w1_aroon50_vol2000_side | 867 | 0.406 | 0.199 | 8.0 | 3/3 | 0.269 |
| pre | c4_w1_mfi14_vol2000_nodiv | 1197 | -0.476 | -0.199 | -8.1 | 0/3 | -0.506 |
| pre | c4_w1_linreg_slope20_vol2000_nodiv | 1178 | -0.454 | -0.192 | -7.8 | 0/3 | -0.507 |
| pre | c4_tsiF_vol2000_nodiv | 1231 | -0.475 | -0.191 | -7.8 | 0/3 | -0.572 |
| pre | c4_wt_vol2000_nodiv | 1331 | -0.550 | -0.188 | -7.9 | 0/3 | -0.496 |
| pre | c4_ichiF_tk_vol2000_nodiv | 1139 | -0.407 | -0.177 | -7.1 | 0/3 | -0.466 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (2103 of 48335 cell-conditions pass; chance at t>2.5 alone ~299)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| P7 | asia | c4_sslhyb_vol2000_hold3 | 2979 | 0.152 | -0.027 | 0.179 | 7.8 | 4/4 | 0.214 |
| M7 | asia | c4_w1_supertrend_14_4_vol2000_side | 2124 | 0.161 | -0.101 | 0.261 | 7.4 | 3/3 | 0.233 |
| M7 | asia | c4_stA_vol2000_hold3 | 1977 | 0.169 | -0.078 | 0.246 | 7.3 | 3/3 | 0.212 |
| M7 | asia | c4_w1_hv_pct50_vol2000_hi | 2044 | 0.159 | -0.074 | 0.234 | 7.2 | 3/3 | 0.255 |
| P7 | asia | c4_smieS_vol2000_ewith | 946 | 0.233 | 0.038 | 0.195 | 6.7 | 3/4 | 0.259 |
| K7 | asia | c4_sslhyb_vol2000_hold3 | 1899 | 0.146 | -0.022 | 0.168 | 6.6 | 4/4 | 0.184 |
| M7 | asia | c4_w1_donchian10_width_vol2000_hi | 2556 | 0.126 | -0.161 | 0.287 | 6.6 | 3/3 | 0.327 |
| P7 | asia | c4_kerS_abs_vol2000_hi | 1329 | 0.201 | 0.030 | 0.171 | 6.6 | 3/4 | 0.197 |
| M7 | asia | c4_w1_atr_pct100_vol2000_hi | 2570 | 0.125 | -0.166 | 0.292 | 6.5 | 3/3 | 0.347 |
| P7 | asia | c4_w1_hv_pct50_vol2000_hi | 3602 | 0.123 | -0.031 | 0.154 | 6.5 | 4/4 | 0.205 |
| P7 | asia | c4_smieS_vol2000_eagainst | 70 | 0.556 | 0.066 | 0.490 | 6.4 | 3/3 | 0.510 |
| K7 | asia | c4_stA_vol2000_hold3 | 2338 | 0.126 | -0.034 | 0.160 | 6.4 | 3/4 | 0.182 |
| P7 | pre | c4_w1_aroon50_vol2000_side | 232 | 0.329 | -0.255 | 0.583 | 6.3 | 3/3 | 0.473 |
| P7 | asia | c4_sqzmS_mom_vol2000_rise | 3813 | 0.118 | -0.041 | 0.159 | 6.3 | 4/4 | 0.138 |
| K7 | asia | c4_chandS_vol2000_hold3 | 2314 | 0.124 | -0.031 | 0.155 | 6.2 | 3/4 | 0.193 |
| K7 | asia | c4_fractal_alli_vol2000_hold3 | 1903 | 0.139 | -0.018 | 0.157 | 6.2 | 4/4 | 0.169 |
| K7 | asia | c4_smiS_vol2000_ewith | 1602 | 0.152 | -0.009 | 0.161 | 6.2 | 4/4 | 0.213 |
| P7 | asia | c4_tsiS_vol2000_ewith | 829 | 0.233 | 0.043 | 0.189 | 6.1 | 3/4 | 0.261 |
| K7 | asia | c4_elderS_bull_vol2000_side | 2703 | 0.111 | -0.044 | 0.156 | 6.1 | 3/4 | 0.122 |
| P7 | asia | c4_chopS_vol2000_lo_z1 | 684 | 0.248 | 0.047 | 0.201 | 6.1 | 4/4 | 0.195 |
| K7 | asia | c4_qqemod_vol2000_hold3 | 1600 | 0.151 | -0.008 | 0.159 | 6.1 | 4/4 | 0.174 |
| K7 | asia | c4_w1_supertrend_14_4_vol2000_side | 2523 | 0.116 | -0.037 | 0.153 | 6.1 | 3/4 | 0.209 |
| M7 | asia | c4_zlema_slope_vol2000_side | 2561 | 0.123 | -0.146 | 0.269 | 6.1 | 3/3 | 0.221 |
| K7 | asia | c4_turt20_vol2000_hold3 | 1853 | 0.139 | -0.015 | 0.154 | 6.1 | 4/4 | 0.179 |
| M7 | asia | c4_w1_supertrend_10_3_vol2000_side | 2177 | 0.144 | -0.072 | 0.216 | 6.1 | 3/3 | 0.178 |
| M7 | asia | c4_stA_vol2000_side | 2177 | 0.144 | -0.072 | 0.216 | 6.1 | 3/3 | 0.178 |
| P7 | asia | c4_hilo_vol2000_hold3 | 3488 | 0.123 | -0.022 | 0.145 | 6.0 | 4/4 | 0.166 |
| P7 | asia | c4_tsi_vol2000_ewith | 1424 | 0.185 | 0.032 | 0.153 | 6.0 | 3/4 | 0.188 |
| M7 | asia | c4_sqzm_bright_vol2000_hold3 | 1023 | 0.218 | 0.018 | 0.200 | 6.0 | 3/3 | 0.241 |
| K7 | asia | c4_w1_kama100_px_vol2000_side | 2718 | 0.109 | -0.043 | 0.153 | 6.0 | 4/4 | 0.179 |

## B4 alternate bars: vol500

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2246; |t|>2: 236 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_vol500.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_stAS_vol500_side | 150336 | 0.78 | 0.032 | -0.011 | 0.043 [0.017, 0.069] | 3.2 | 4/4 | -0.004 | -0.014 |
| c4_w1_ema50_px_vol500_side | 172890 | 0.90 | 0.027 | -0.015 | 0.042 [0.016, 0.068] | 3.2 | 4/4 | 0.026 | 0.014 |
| c4_krS_dir_vol500_side | 170718 | 0.89 | 0.027 | -0.013 | 0.040 [0.016, 0.065] | 3.2 | 4/4 | 0.018 | 0.012 |
| c4_w1_supertrend_14_4_vol500_side | 149437 | 0.78 | 0.032 | -0.011 | 0.044 [0.017, 0.071] | 3.2 | 4/4 | -0.016 | -0.041 |
| c4_qqeS_vol500_side | 163385 | 0.85 | 0.028 | -0.009 | 0.038 [0.014, 0.061] | 3.2 | 4/4 | 0.006 | -0.013 |
| c4_smieS_vol500_side | 163818 | 0.86 | 0.028 | -0.008 | 0.036 [0.013, 0.058] | 3.1 | 4/4 | -0.005 | -0.025 |
| c4_w1_linreg_chan10_vol500_eleave | 8273 | 0.04 | 0.063 | 0.021 | 0.042 [0.015, 0.069] | 3.1 | 3/4 | 0.033 | 0.111 |
| c4_stAS_vol500_hold3 | 144111 | 0.75 | 0.032 | -0.006 | 0.039 [0.014, 0.064] | 3.0 | 4/4 | -0.011 | -0.011 |
| c4_w1_donchian50_pos_vol500_side | 168013 | 0.88 | 0.028 | -0.011 | 0.039 [0.013, 0.064] | 3.0 | 4/4 | 0.004 | -0.031 |
| c4_kstS_vol500_side | 141080 | 0.74 | 0.033 | -0.004 | 0.037 [0.012, 0.062] | 2.9 | 3/4 | 0.011 | 0.013 |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_w1_ichi_slow_lag_vol500_divwith | 4689 | 0.02 | -0.069 | 0.025 | -0.094 [-0.146, -0.042] | -3.5 | 0/4 | -0.180 | -0.229 |
| c4_w1_ema21_hold_vol500_against | 4530 | 0.02 | -0.034 | 0.024 | -0.058 [-0.091, -0.025] | -3.4 | 0/4 | -0.066 | -0.065 |
| c4_w1_ema_8_21_34_stack_vol500_against | 17909 | 0.09 | -0.013 | 0.026 | -0.039 [-0.062, -0.017] | -3.4 | 0/4 | -0.029 | -0.024 |
| c4_w1_ema_stack_fast_vol500_against | 17909 | 0.09 | -0.013 | 0.026 | -0.039 [-0.062, -0.017] | -3.4 | 0/4 | -0.029 | -0.024 |
| c4_sfpF_vol500_against | 13088 | 0.07 | -0.010 | 0.025 | -0.035 [-0.056, -0.015] | -3.3 | 0/4 | -0.101 | -0.110 |
| c4_ichiS_score_vol500_eagainst | 9177 | 0.05 | -0.024 | 0.025 | -0.050 [-0.079, -0.020] | -3.3 | 0/4 | -0.062 | -0.006 |
| c4_stAS_vol500_against | 41184 | 0.22 | -0.011 | 0.032 | -0.043 [-0.069, -0.017] | -3.2 | 0/4 | 0.004 | 0.014 |
| c4_kstS_vol500_fresh5 | 23009 | 0.12 | -0.004 | 0.027 | -0.031 [-0.050, -0.012] | -3.2 | 0/4 | -0.043 | -0.062 |
| c4_turt55_vol500_against | 16903 | 0.09 | -0.020 | 0.027 | -0.047 [-0.076, -0.018] | -3.2 | 1/4 | -0.004 | 0.024 |
| c4_elderF_bull_vol500_nodiv | 150679 | 0.79 | 0.016 | 0.047 | -0.031 [-0.051, -0.011] | -3.0 | 0/4 | -0.056 | -0.082 |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 375 of 13033 session-condition cells pass (chance-level expectation under independence ~161 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| asia | c4_w1_keltner40_pos_vol500_eagainst | 754 | -0.170 | -0.108 | -4.5 | 0/4 | -0.271 |
| asia | c4_w1_demarker21_vol500_eagainst | 782 | -0.137 | -0.094 | -4.1 | 0/4 | -0.309 |
| asia | c4_w1_keltner20_pos_vol500_eagainst | 370 | -0.168 | -0.089 | -3.6 | 0/4 | -0.337 |
| asia | c4_tsiF_vol500_eagainst | 1214 | -0.117 | -0.087 | -3.9 | 0/4 | -0.089 |
| asia | c4_w1_ema21_hold_vol500_against | 2251 | -0.111 | -0.086 | -4.1 | 0/4 | -0.126 |
| asia | c4_w1_ema50_px_vol500_side | 53047 | 0.092 | 0.080 | 4.7 | 4/4 | 0.080 |
| close | c4_sqzmF_mom_vol500_fresh1 | 727 | -0.103 | -0.070 | -3.0 | 0/4 | -0.151 |
| close | c4_w1_vwma200_px_vol500_fresh5 | 1215 | -0.099 | -0.067 | -2.9 | 0/4 | -0.137 |
| close | c4_w1_sma200_px_vol500_fresh5 | 1209 | -0.098 | -0.066 | -2.8 | 0/4 | -0.136 |
| close | c4_fvgF_cnt_vol500_fresh5 | 748 | -0.116 | -0.066 | -2.7 | 0/4 | -0.161 |
| close | c4_stA_vol500_fresh1 | 406 | -0.117 | -0.066 | -2.6 | 0/4 | -0.241 |
| close | c4_w1_supertrend_10_3_vol500_rise | 406 | -0.117 | -0.066 | -2.6 | 0/4 | -0.241 |
| london | c4_ifvg_in_vol500_hold3 | 374 | 0.212 | 0.095 | 3.8 | 4/4 | 0.288 |
| london | c4_ifvgF_in_vol500_hold3 | 378 | 0.211 | 0.095 | 3.8 | 4/4 | 0.288 |
| london | c4_w1_ichi_fast_lag_vol500_divwith | 1412 | 0.180 | 0.084 | 3.4 | 4/4 | 0.003 |
| london | c4_rsima21_vol500_eenter | 460 | -0.160 | -0.076 | -3.0 | 0/4 | -0.135 |
| london | c4_w1_rsi21_vol500_eenter | 460 | -0.160 | -0.076 | -3.0 | 0/4 | -0.135 |
| london | c4_ifvgS_in_vol500_hold3 | 327 | 0.199 | 0.071 | 3.0 | 4/4 | 0.323 |
| nyam | c4_stcF_vol500_divwith | 1995 | 0.099 | 0.074 | 3.4 | 4/4 | 0.063 |
| nyam | c4_w1_cmo21_vol500_ewith | 1505 | -0.095 | -0.072 | -3.4 | 0/4 | -0.037 |
| nyam | c4_w1_keltner40_pos_vol500_eleave | 201 | 0.182 | 0.065 | 2.7 | 4/4 | 0.023 |
| nyam | c4_w1_linreg_chan50_vol500_ewith | 866 | -0.103 | -0.065 | -2.7 | 0/4 | -0.095 |
| nyam | c4_w1_linreg_chan20_vol500_eagainst | 229 | 0.219 | 0.063 | 2.8 | 4/4 | 0.317 |
| nyam | c4_lrc_vol500_ewith | 2239 | -0.076 | -0.060 | -2.9 | 0/4 | -0.044 |
| nypm | c4_ichiS_futcloud_vol500_fresh1 | 450 | -0.130 | -0.071 | -2.9 | 0/4 | -0.141 |
| nypm | c4_sfpF_vol500_fresh5 | 2610 | 0.089 | 0.071 | 3.5 | 4/4 | 0.076 |
| nypm | c4_ichiF_cloud_vol500_against | 1364 | 0.100 | 0.071 | 3.1 | 4/4 | 0.065 |
| nypm | c4_sfp_vol500_fresh5 | 1561 | 0.099 | 0.068 | 2.9 | 4/4 | 0.053 |
| nypm | c4_krS_px_vol500_side | 23493 | -0.091 | -0.067 | -3.1 | 0/4 | -0.006 |
| nypm | c4_w1_vwma50_px_vol500_side | 23360 | -0.088 | -0.065 | -3.0 | 0/4 | -0.005 |
| pre | c4_w1_trix15_vol500_divwith | 956 | -0.212 | -0.083 | -3.4 | 0/4 | -0.261 |
| pre | c4_stcF_vol500_divwith | 605 | 0.231 | 0.083 | 3.5 | 4/4 | 0.247 |
| pre | c4_w1_stoch21_vol500_eleave | 344 | 0.197 | 0.080 | 3.3 | 4/4 | 0.331 |
| pre | c4_w1_hv_pct50_vol500_hi | 3115 | 0.158 | 0.079 | 3.2 | 4/4 | 0.126 |
| pre | c4_mcgF_px_vol500_nodiv | 6973 | 0.122 | 0.076 | 3.2 | 4/4 | 0.088 |
| pre | c4_w1_macd12_26_9_hist_vol500_divwith | 619 | 0.197 | 0.074 | 3.0 | 4/4 | 0.257 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (597 of 65287 cell-conditions pass; chance at t>2.5 alone ~404)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_ema100_px_vol500_side | 10379 | 0.067 | -0.043 | 0.110 | 5.0 | 4/4 | 0.156 |
| K7 | asia | c4_w1_ema50_px_vol500_side | 11281 | 0.060 | -0.047 | 0.107 | 4.9 | 4/4 | 0.171 |
| K7 | asia | c4_w1_stoch21_vol500_side | 10717 | 0.059 | -0.030 | 0.088 | 4.8 | 4/4 | 0.150 |
| K7 | asia | c4_w1_keltner40_pos_vol500_side | 11677 | 0.057 | -0.047 | 0.104 | 4.8 | 4/4 | 0.172 |
| K7 | asia | c4_w1_sma100_px_vol500_side | 10064 | 0.068 | -0.038 | 0.106 | 4.8 | 4/4 | 0.145 |
| K7 | asia | c4_w1_vwma100_px_vol500_side | 10055 | 0.068 | -0.037 | 0.105 | 4.7 | 4/4 | 0.145 |
| K7 | asia | c4_stPS_vol500_side | 8588 | 0.078 | -0.027 | 0.104 | 4.7 | 4/4 | 0.119 |
| K7 | asia | c4_rsima21_vol500_side | 11631 | 0.056 | -0.046 | 0.102 | 4.7 | 4/4 | 0.169 |
| K7 | asia | c4_w1_rsi21_vol500_side | 11628 | 0.057 | -0.045 | 0.102 | 4.6 | 4/4 | 0.169 |
| K7 | asia | c4_w1_di14_vol500_side | 11409 | 0.056 | -0.038 | 0.094 | 4.6 | 4/4 | 0.124 |
| K7 | asia | c4_w1_kama200_px_vol500_side | 10032 | 0.066 | -0.033 | 0.099 | 4.6 | 4/4 | 0.139 |
| K7 | asia | c4_kr_dir_vol500_side | 12088 | 0.053 | -0.048 | 0.101 | 4.6 | 4/4 | 0.189 |
| K7 | asia | c4_krS_dir_vol500_side | 10925 | 0.061 | -0.041 | 0.102 | 4.6 | 4/4 | 0.168 |
| K7 | asia | c4_w1_donchian20_pos_vol500_side | 12159 | 0.051 | -0.041 | 0.092 | 4.6 | 4/4 | 0.174 |
| K7 | asia | c4_don20_pos_vol500_side | 12159 | 0.051 | -0.041 | 0.092 | 4.6 | 4/4 | 0.174 |
| K7 | asia | c4_w1_di21_vol500_side | 10835 | 0.060 | -0.035 | 0.095 | 4.6 | 4/4 | 0.165 |
| K7 | asia | c4_w1_kama100_px_vol500_side | 10412 | 0.065 | -0.039 | 0.104 | 4.5 | 4/4 | 0.134 |
| K7 | asia | c4_kr_px_vol500_side | 12256 | 0.051 | -0.046 | 0.098 | 4.5 | 4/4 | 0.171 |
| K7 | asia | c4_stPS_vol500_hold3 | 8338 | 0.077 | -0.022 | 0.099 | 4.5 | 4/4 | 0.117 |
| K7 | asia | c4_mcgS_slope_vol500_side | 11904 | 0.053 | -0.043 | 0.097 | 4.4 | 4/4 | 0.191 |
| K7 | asia | c4_mcgS_px_vol500_side | 11904 | 0.053 | -0.043 | 0.097 | 4.4 | 4/4 | 0.191 |
| K7 | asia | c4_w1_willr21_vol500_side | 12081 | 0.051 | -0.040 | 0.091 | 4.4 | 4/4 | 0.198 |
| K7 | asia | c4_rfiltS_vol500_side | 12295 | 0.050 | -0.041 | 0.091 | 4.4 | 4/4 | 0.170 |
| K7 | asia | c4_smie_vol500_side | 10974 | 0.057 | -0.030 | 0.087 | 4.4 | 4/4 | 0.175 |
| K7 | asia | c4_krS_px_vol500_side | 11502 | 0.056 | -0.041 | 0.097 | 4.4 | 4/4 | 0.199 |
| K7 | asia | c4_w1_ema200_px_vol500_side | 9771 | 0.067 | -0.030 | 0.097 | 4.4 | 4/4 | 0.155 |
| K7 | asia | c4_ichi_kj_vol500_side | 11751 | 0.053 | -0.038 | 0.092 | 4.3 | 4/4 | 0.221 |
| K7 | asia | c4_w1_sma200_px_vol500_side | 9553 | 0.068 | -0.028 | 0.096 | 4.3 | 4/4 | 0.139 |
| K7 | asia | c4_w1_ema34_px_vol500_side | 11946 | 0.053 | -0.043 | 0.096 | 4.3 | 4/4 | 0.199 |
| K7 | asia | c4_w1_vwma200_px_vol500_side | 9553 | 0.068 | -0.028 | 0.096 | 4.3 | 4/4 | 0.140 |
