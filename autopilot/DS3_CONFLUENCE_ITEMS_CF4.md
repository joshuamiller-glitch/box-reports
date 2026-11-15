# DS3_CONFLUENCE_ITEMS_CF4: STEP 3 each condition alone, Block 2 (and 4) of the indicator library

**Verdict (data ends 2026-11-11) line: Block 2 conditions built so far = 39463 scored columns across 21 sub-blocks; every one is a MAP entry only (no PASS claim; matched-count and shuffled-outcome controls belong to W-CF3).**

## IRL / ERL Step A (Addendum 5): measure-only, headline = 5-min bars, 2 pts, W=3, minor pivot 3

**Verdict line: external better than internal for FADES under the fixed rule (matched difference of the 60-min fade return > 0, CI above 0 on full history, positive in L6M, and beating the random-level control): NO under every one of the 13 range definitions. Ranges with ext-minus-int matched difference > 0 on full history: e240_10; ranges where internal is significantly better: none. Measure-only; no PASS claim.**

Units: fav/net/mae in ATR(5m,14) of the sweep; net = fade return at the horizon close (positive = reversal followed through); cont = share of sweeps where a 1m close re-closed beyond the swept level (continuation) within the horizon; stop = adverse reached poke extreme +2 pts within the horizon; mdiff = matched (poke depth tercile x ET hour x ATR tercile) ext-minus-int difference in net60 with 95% week-block bootstrap CI; ctl = random level at the same distance (2 seeds). Windows recent first.

**L1M**

| range | n ext | n int | net60 ext | net60 int | matched diff [95% CI] | cont60 ext/int | MAE60 ext/int | stop60 ext/int | win60 ext/int | ctl net60 ext/int |
|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | 22 | 1092 | -0.55 | 0.05 |  [, ] | 0.77/0.79 | 2.25/1.87 | 0.68/0.68 | 0.32/0.49 | -0.11/0.15 |
| b_ps | 56 | 1137 | 0.36 | 0.11 | 0.23 [-1.67, 1.46] | 0.71/0.78 | 2.22/1.95 | 0.61/0.68 | 0.54/0.50 | 1.10/0.20 |
| b_cs60 | 635 | 1037 | -0.13 | 0.06 | -0.23 [-0.56, 0.11] | 0.81/0.79 | 1.79/1.93 | 0.72/0.68 | 0.44/0.50 | /0.07 |
| c_on | 20 | 349 | 0.42 | 0.22 |  [, ] | 0.70/0.78 | 2.01/2.05 | 0.65/0.69 | 0.60/0.54 | 0.51/0.28 |
| d_wk | 5 | 1346 | -1.16 | 0.09 |  [, ] | 0.80/0.78 | 2.81/1.97 | 0.80/0.67 | 0.20/0.50 | 0.45/0.20 |
| e15_10 | 44 | 1060 | 0.41 | 0.09 | 1.68 [-1.30, 2.72] | 0.73/0.79 | 1.99/1.98 | 0.59/0.69 | 0.57/0.50 | 0.37/0.25 |
| e15_20 | 27 | 1144 | 0.25 | 0.09 |  [, ] | 0.81/0.78 | 1.99/2.02 | 0.56/0.67 | 0.52/0.51 | 0.68/0.22 |
| e60_10 | 12 | 1084 | -0.36 | 0.09 |  [, ] | 0.75/0.77 | 1.96/2.04 | 0.58/0.66 | 0.33/0.50 | -0.62/0.28 |
| e60_20 | 9 | 1120 | -0.94 | -0.06 |  [, ] | 0.89/0.79 | 2.37/2.08 | 0.89/0.67 | 0.11/0.48 | -1.10/0.12 |
| e240_10 | 2 | 855 | -2.73 | 0.16 |  [, ] | 1.00/0.78 | 4.35/1.92 | 1.00/0.67 | 0.00/0.51 | -0.88/0.14 |
| e240_20 | 1 | 687 | -3.54 | 0.25 |  [, ] | 1.00/0.77 | 4.32/1.95 | 1.00/0.66 | 0.00/0.54 | -2.78/0.30 |
| f_or30 | 71 | 372 | 0.19 | 0.06 | -0.49 [-1.58, 1.68] | 0.70/0.80 | 1.81/1.91 | 0.70/0.70 | 0.48/0.52 | 0.01/0.14 |
| f_or60 | 56 | 428 | 0.24 | 0.12 | 0.14 [-1.52, 1.83] | 0.80/0.80 | 1.91/1.91 | 0.71/0.69 | 0.52/0.52 | 0.29/0.22 |

**L3M**

| range | n ext | n int | net60 ext | net60 int | matched diff [95% CI] | cont60 ext/int | MAE60 ext/int | stop60 ext/int | win60 ext/int | ctl net60 ext/int |
|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | 38 | 2746 | -0.54 | -0.05 | 2.76 [-2.74, 3.00] | 0.79/0.77 | 2.32/1.98 | 0.66/0.67 | 0.29/0.51 | 0.15/0.02 |
| b_ps | 121 | 2789 | 0.13 | 0.01 | 0.51 [-0.50, 1.06] | 0.75/0.78 | 2.37/2.00 | 0.65/0.67 | 0.51/0.51 | 0.87/0.08 |
| b_cs60 | 1440 | 2492 | -0.11 | -0.00 | -0.11 [-0.42, 0.11] | 0.79/0.77 | 1.91/1.96 | 0.68/0.67 | 0.48/0.51 | /0.03 |
| c_on | 45 | 873 | 0.64 | 0.09 | 0.71 [-0.36, 1.60] | 0.64/0.76 | 2.24/2.02 | 0.64/0.66 | 0.64/0.54 | 0.17/0.15 |
| d_wk | 8 | 3085 | -0.46 | -0.01 |  [, ] | 0.88/0.77 | 2.31/2.03 | 0.88/0.67 | 0.38/0.51 | 1.03/0.10 |
| e15_10 | 106 | 2673 | -0.00 | -0.01 | 0.07 [-0.98, 0.86] | 0.75/0.78 | 2.30/1.99 | 0.64/0.67 | 0.53/0.51 | -0.07/0.12 |
| e15_20 | 59 | 2833 | -0.04 | -0.03 | 0.44 [-1.04, 1.24] | 0.78/0.78 | 2.16/2.04 | 0.64/0.67 | 0.51/0.51 | 0.31/0.09 |
| e60_10 | 25 | 2593 | -0.55 | -0.01 |  [, ] | 0.80/0.76 | 2.24/2.06 | 0.68/0.66 | 0.28/0.51 | -0.13/0.10 |
| e60_20 | 15 | 2436 | -0.92 | -0.07 |  [, ] | 0.80/0.77 | 2.46/2.08 | 0.80/0.66 | 0.27/0.49 | -0.04/0.04 |
| e240_10 | 8 | 2665 | -0.74 | 0.00 |  [, ] | 0.75/0.77 | 2.68/2.03 | 0.75/0.66 | 0.50/0.51 | -0.60/0.05 |
| e240_20 | 3 | 2889 | -3.13 | -0.00 |  [, ] | 1.00/0.77 | 3.89/2.03 | 1.00/0.66 | 0.00/0.52 | -2.82/0.08 |
| f_or30 | 166 | 893 | 0.14 | -0.06 | 0.04 [-0.44, 0.67] | 0.80/0.78 | 1.84/1.91 | 0.67/0.69 | 0.51/0.52 | -0.00/0.00 |
| f_or60 | 146 | 1025 | 0.16 | -0.03 | 0.07 [-0.50, 0.46] | 0.82/0.79 | 1.89/1.92 | 0.64/0.68 | 0.51/0.52 | 0.12/0.08 |

**L6M**

| range | n ext | n int | net60 ext | net60 int | matched diff [95% CI] | cont60 ext/int | MAE60 ext/int | stop60 ext/int | win60 ext/int | ctl net60 ext/int |
|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | 80 | 5415 | -0.46 | -0.01 | 0.33 [-1.51, 0.89] | 0.79/0.78 | 2.21/2.01 | 0.69/0.69 | 0.38/0.50 | 0.07/0.02 |
| b_ps | 243 | 5471 | -0.12 | 0.06 | -0.05 [-0.67, 0.29] | 0.77/0.78 | 2.55/2.02 | 0.67/0.69 | 0.47/0.51 | 0.38/0.06 |
| b_cs60 | 2898 | 4895 | -0.03 | 0.01 | -0.01 [-0.19, 0.17] | 0.79/0.78 | 1.89/1.93 | 0.69/0.69 | 0.48/0.50 | /0.02 |
| c_on | 94 | 1687 | -0.05 | 0.08 | -0.08 [-0.87, 0.86] | 0.70/0.77 | 2.65/2.16 | 0.64/0.69 | 0.57/0.52 | 0.03/0.05 |
| d_wk | 14 | 5891 | -0.32 | 0.01 |  [, ] | 0.86/0.78 | 1.98/2.03 | 0.79/0.68 | 0.43/0.50 | 0.96/0.06 |
| e15_10 | 232 | 5137 | -0.13 | 0.06 | -0.23 [-0.67, 0.15] | 0.78/0.78 | 2.29/1.99 | 0.67/0.68 | 0.47/0.51 | -0.06/0.11 |
| e15_20 | 124 | 5527 | -0.33 | 0.02 | -0.44 [-1.05, 0.21] | 0.81/0.78 | 2.31/2.06 | 0.69/0.69 | 0.46/0.50 | 0.06/0.03 |
| e60_10 | 57 | 5167 | -0.44 | 0.02 | -0.11 [-1.46, 0.82] | 0.82/0.77 | 2.15/2.06 | 0.70/0.68 | 0.39/0.50 | -0.24/0.08 |
| e60_20 | 33 | 5159 | -0.63 | -0.00 | 0.61 [-1.74, 1.73] | 0.82/0.78 | 2.35/2.06 | 0.82/0.68 | 0.36/0.49 | -0.18/0.04 |
| e240_10 | 15 | 4938 | -0.80 | 0.00 |  [, ] | 0.73/0.78 | 2.54/2.05 | 0.73/0.68 | 0.40/0.50 | -0.78/0.03 |
| e240_20 | 4 | 5610 | -2.59 | 0.03 |  [, ] | 1.00/0.78 | 3.26/2.02 | 1.00/0.69 | 0.00/0.51 | -1.62/0.07 |
| f_or30 | 348 | 1675 | 0.26 | 0.01 | 0.24 [-0.15, 0.61] | 0.78/0.78 | 1.85/1.94 | 0.68/0.68 | 0.51/0.52 | 0.17/0.04 |
| f_or60 | 311 | 1971 | 0.16 | 0.01 | -0.01 [-0.29, 0.35] | 0.82/0.79 | 1.88/1.92 | 0.66/0.68 | 0.51/0.51 | 0.08/0.08 |

**full**

| range | n ext | n int | net60 ext | net60 int | matched diff [95% CI] | cont60 ext/int | MAE60 ext/int | stop60 ext/int | win60 ext/int | ctl net60 ext/int |
|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | 460 | 32377 | -0.20 | -0.00 | -0.19 [-0.50, 0.13] | 0.74/0.78 | 2.16/2.10 | 0.59/0.64 | 0.50/0.51 | -0.23/-0.01 |
| b_ps | 1488 | 28981 | -0.13 | -0.00 | -0.10 [-0.30, 0.11] | 0.76/0.78 | 2.56/2.11 | 0.62/0.64 | 0.48/0.51 | 0.01/-0.01 |
| b_cs60 | 16135 | 27327 | -0.04 | 0.02 | -0.05 [-0.11, 0.00] | 0.78/0.78 | 1.92/2.00 | 0.65/0.65 | 0.50/0.51 | /-0.00 |
| c_on | 689 | 10374 | -0.26 | -0.11 | -0.08 [-0.40, 0.24] | 0.75/0.77 | 2.74/2.21 | 0.65/0.68 | 0.50/0.50 | -0.28/-0.13 |
| d_wk | 100 | 33329 | -0.07 | -0.03 | -0.37 [-1.05, 0.64] | 0.75/0.78 | 2.06/2.11 | 0.61/0.65 | 0.49/0.50 | 0.11/-0.02 |
| e15_10 | 1413 | 28042 | -0.07 | -0.03 | -0.05 [-0.19, 0.13] | 0.75/0.78 | 2.33/2.12 | 0.62/0.65 | 0.51/0.50 | -0.07/-0.03 |
| e15_20 | 715 | 32647 | -0.13 | -0.01 | -0.14 [-0.41, 0.12] | 0.74/0.78 | 2.25/2.15 | 0.60/0.65 | 0.52/0.50 | -0.04/-0.02 |
| e60_10 | 382 | 32288 | -0.12 | -0.01 | -0.15 [-0.48, 0.26] | 0.74/0.78 | 2.23/2.15 | 0.61/0.65 | 0.52/0.51 | 0.06/-0.01 |
| e60_20 | 214 | 29175 | -0.40 | -0.01 | -0.29 [-0.86, 0.15] | 0.78/0.78 | 2.36/2.13 | 0.68/0.65 | 0.47/0.51 | -0.08/-0.02 |
| e240_10 | 102 | 29122 | -0.27 | -0.03 | 0.25 [-1.01, 0.88] | 0.77/0.78 | 2.19/2.12 | 0.66/0.66 | 0.44/0.50 | -0.06/-0.01 |
| e240_20 | 39 | 29046 | -0.28 | -0.03 |  [-2.54, 1.99] | 0.79/0.78 | 2.26/2.10 | 0.74/0.66 | 0.33/0.50 | -0.50/-0.00 |
| f_or30 | 2087 | 9231 | -0.04 | 0.02 | -0.04 [-0.20, 0.07] | 0.78/0.78 | 2.05/1.98 | 0.65/0.65 | 0.50/0.52 | 0.03/0.03 |
| f_or60 | 1922 | 11009 | -0.02 | 0.01 | -0.03 [-0.17, 0.11] | 0.78/0.78 | 1.94/1.95 | 0.63/0.65 | 0.50/0.51 | -0.08/0.02 |

**Per session (matched diff net60, ext minus int)**

| range | session | window | n ext | n int | net60 ext | net60 int | matched diff [CI] |
|---|---|---|---|---|---|---|---|
| a_pd | asia | L6M | 49 | 2198 | -0.34 | -0.10 | 0.52 [-1.44, 1.25] |
| a_pd | asia | full | 172 | 9643 | -0.03 | -0.03 | 0.04 [-0.26, 0.44] |
| a_pd | london | L6M | 17 | 1962 | -0.86 | 0.08 |  [, ] |
| a_pd | london | full | 125 | 12781 | -0.08 | 0.08 | 0.18 [-1.24, 0.70] |
| a_pd | ny | L6M | 14 | 1255 | -0.40 | 0.02 |  [, ] |
| a_pd | ny | full | 163 | 9953 | -0.49 | -0.08 | -0.47 [-0.94, 0.05] |
| b_ps | asia | L6M | 49 | 2198 | -0.34 | -0.10 | 0.52 [-1.44, 1.25] |
| b_ps | asia | full | 171 | 9644 | -0.05 | -0.03 | 0.04 [-0.27, 0.44] |
| b_ps | london | L6M | 77 | 2016 | -0.24 | 0.19 | -0.32 [-1.17, 0.15] |
| b_ps | london | full | 538 | 11099 | -0.07 | 0.07 | -0.10 [-0.39, 0.19] |
| b_ps | ny | L6M | 117 | 1257 | 0.06 | 0.13 | -0.12 [-0.64, 0.43] |
| b_ps | ny | full | 779 | 8238 | -0.19 | -0.08 | -0.10 [-0.44, 0.23] |
| b_cs60 | asia | L6M | 1135 | 1683 | -0.07 | -0.12 | 0.05 [-0.19, 0.31] |
| b_cs60 | asia | full | 4471 | 7248 | -0.08 | -0.02 | -0.09 [-0.18, 0.01] |
| b_cs60 | london | L6M | 1083 | 1858 | 0.03 | 0.10 | -0.02 [-0.34, 0.28] |
| b_cs60 | london | full | 6485 | 10999 | 0.04 | 0.06 | -0.01 [-0.11, 0.09] |
| b_cs60 | ny | L6M | 680 | 1354 | -0.06 | 0.06 | -0.10 [-0.42, 0.26] |
| b_cs60 | ny | full | 5179 | 9080 | -0.09 | -0.01 | -0.08 [-0.15, 0.02] |
| c_on | asia | L6M | 0 | 0 |  |  |  [, ] |
| c_on | asia | full | 0 | 0 |  |  |  [, ] |
| c_on | london | L6M | 0 | 0 |  |  |  [, ] |
| c_on | london | full | 0 | 0 |  |  |  [, ] |
| c_on | ny | L6M | 94 | 1687 | -0.05 | 0.08 | -0.08 [-0.81, 0.94] |
| c_on | ny | full | 689 | 10374 | -0.26 | -0.11 | -0.08 [-0.41, 0.23] |
| d_wk | asia | L6M | 9 | 2107 | -0.04 | -0.13 |  [, ] |
| d_wk | asia | full | 34 | 8858 | 0.03 | -0.06 | 0.16 [-1.22, 1.04] |
| d_wk | london | L6M | 1 | 2146 | -2.43 | 0.10 |  [, ] |
| d_wk | london | full | 19 | 12713 | 0.09 | 0.02 |  [, ] |
| d_wk | ny | L6M | 4 | 1638 | -0.41 | 0.06 |  [, ] |
| d_wk | ny | full | 47 | 11758 | -0.21 | -0.07 | -0.92 [-1.61, 0.85] |
| e15_10 | asia | L6M | 77 | 2001 | -0.11 | -0.06 | 0.05 [-1.05, 0.82] |
| e15_10 | asia | full | 306 | 8943 | -0.18 | -0.03 | -0.23 [-0.46, 0.02] |
| e15_10 | london | L6M | 87 | 1834 | -0.32 | 0.18 | -0.70 [-1.47, 0.02] |
| e15_10 | london | full | 578 | 11034 | -0.01 | 0.02 | -0.05 [-0.28, 0.25] |
| e15_10 | ny | L6M | 68 | 1302 | 0.09 | 0.08 | -0.10 [-0.76, 0.58] |
| e15_10 | ny | full | 529 | 8065 | -0.07 | -0.10 | 0.04 [-0.26, 0.35] |
| e15_20 | asia | L6M | 31 | 1950 | -0.23 | -0.07 | 0.03 [-1.89, 1.51] |
| e15_20 | asia | full | 111 | 8570 | 0.15 | -0.03 | 0.20 [-0.36, 0.66] |
| e15_20 | london | L6M | 43 | 2158 | -0.65 | 0.14 | -1.14 [-2.03, 0.54] |
| e15_20 | london | full | 269 | 13966 | -0.18 | 0.07 | -0.13 [-0.88, 0.16] |
| e15_20 | ny | L6M | 50 | 1419 | -0.12 | -0.03 | -0.24 [-0.79, 0.51] |
| e15_20 | ny | full | 335 | 10111 | -0.20 | -0.11 | -0.07 [-0.39, 0.28] |
| e60_10 | asia | L6M | 14 | 1617 | -0.47 | -0.03 |  [, ] |
| e60_10 | asia | full | 46 | 7287 | 0.13 | -0.03 | 0.38 [-1.12, 1.54] |
| e60_10 | london | L6M | 21 | 2031 | -0.56 | 0.11 |  [, ] |
| e60_10 | london | full | 135 | 13333 | -0.27 | 0.06 | -0.50 [-1.61, 0.40] |
| e60_10 | ny | L6M | 22 | 1519 | -0.29 | -0.04 |  [, ] |
| e60_10 | ny | full | 201 | 11668 | -0.07 | -0.07 | 0.05 [-0.46, 0.49] |
| e60_20 | asia | L6M | 10 | 1713 | -0.69 | -0.14 |  [, ] |
| e60_20 | asia | full | 29 | 7207 | -0.28 | -0.06 |  [, ] |
| e60_20 | london | L6M | 6 | 1825 | -1.53 | 0.11 |  [, ] |
| e60_20 | london | full | 42 | 10921 | -0.65 | 0.05 | -0.31 [-2.25, 0.85] |
| e60_20 | ny | L6M | 17 | 1621 | -0.28 | 0.01 |  [, ] |
| e60_20 | ny | full | 143 | 11047 | -0.36 | -0.05 | -0.32 [-0.92, 0.24] |
| e240_10 | asia | L6M | 5 | 1696 | -1.79 | -0.15 |  [, ] |
| e240_10 | asia | full | 17 | 7286 | -0.71 | -0.07 |  [, ] |
| e240_10 | london | L6M | 2 | 1811 | -2.06 | 0.07 |  [, ] |
| e240_10 | london | full | 18 | 11285 | -0.06 | 0.02 |  [, ] |
| e240_10 | ny | L6M | 8 | 1431 | 0.14 | 0.11 |  [, ] |
| e240_10 | ny | full | 67 | 10551 | -0.22 | -0.05 | 0.35 [-0.87, 0.86] |
| e240_20 | asia | L6M | 3 | 1941 | -2.89 | -0.07 |  [, ] |
| e240_20 | asia | full | 4 | 7663 | -2.21 | -0.04 |  [, ] |
| e240_20 | london | L6M | 1 | 2019 | -1.69 | 0.10 |  [, ] |
| e240_20 | london | full | 10 | 10995 | -1.15 | 0.02 |  [, ] |
| e240_20 | ny | L6M | 0 | 1650 |  | 0.07 |  [, ] |
| e240_20 | ny | full | 25 | 10388 | 0.38 | -0.06 |  [, ] |
| f_or30 | asia | L6M | 98 | 423 | 0.39 | -0.05 | 0.31 [-0.66, 1.45] |
| f_or30 | asia | full | 467 | 2248 | 0.07 | -0.00 | 0.10 [-0.12, 0.30] |
| f_or30 | london | L6M | 126 | 579 | 0.28 | -0.04 | 0.37 [-0.11, 0.87] |
| f_or30 | london | full | 761 | 3030 | 0.09 | -0.02 | 0.18 [-0.09, 0.39] |
| f_or30 | ny | L6M | 124 | 673 | 0.14 | 0.08 | 0.08 [-0.36, 0.45] |
| f_or30 | ny | full | 859 | 3953 | -0.21 | 0.06 | -0.30 [-0.52, -0.15] |
| f_or60 | asia | L6M | 97 | 508 | 0.36 | -0.02 | -0.05 [-0.64, 0.87] |
| f_or60 | asia | full | 451 | 2581 | 0.00 | 0.01 | -0.06 [-0.30, 0.17] |
| f_or60 | london | L6M | 123 | 695 | 0.12 | 0.03 | -0.06 [-0.61, 0.53] |
| f_or60 | london | full | 784 | 3650 | 0.07 | 0.01 | 0.03 [-0.24, 0.27] |
| f_or60 | ny | L6M | 91 | 768 | 0.02 | 0.02 | 0.08 [-0.22, 0.37] |
| f_or60 | ny | full | 687 | 4778 | -0.13 | 0.00 | -0.07 [-0.24, 0.12] |

**Sensitivity: matched diff (ext - int) of net60 full history, one parameter changed at a time from the headline**

| range | head | p2 | p5 | tf1 | tf15 | tf3 | thr_atr | thr_tick | w1 | w2 | w5 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| a_pd | -0.19 | -0.21 | -0.19 | -0.06 | -0.07 | -0.15 | -0.18 | -0.22 | 0.01 | -0.12 | -0.14 |
| b_ps | -0.10 | -0.11 | -0.10 | -0.15 | -0.08 | -0.04 | -0.06 | -0.05 | -0.18 | -0.17 | -0.08 |
| b_cs60 | -0.05 | -0.05 | -0.04 | -0.02 | -0.05 | -0.03 | -0.05 | -0.04 | -0.06 | -0.05 | -0.04 |
| c_on | -0.08 | -0.07 | -0.07 | 0.02 | 0.04 | 0.07 | -0.06 | -0.10 | -0.18 | -0.19 | 0.01 |
| d_wk | -0.37 | -0.40 | -0.43 | -0.33 | -0.01 | 0.43 | -0.34 | 0.02 | 0.26 | 0.18 | -0.50 |
| e15_10 | -0.05 | -0.05 | -0.06 | -0.08 | -0.05 | 0.02 | -0.03 | -0.04 | -0.09 | -0.03 | -0.03 |
| e15_20 | -0.14 | -0.14 | -0.14 | -0.16 | 0.01 | 0.01 | -0.18 | -0.13 | -0.14 | -0.16 | -0.11 |
| e60_10 | -0.15 | -0.15 | -0.13 | -0.13 | 0.13 | -0.15 | -0.09 | -0.00 | -0.03 | -0.10 | -0.12 |
| e60_20 | -0.29 | -0.30 | -0.25 | -0.46 | -0.09 | -0.53 | -0.28 | -0.38 | 0.13 | -0.11 | -0.36 |
| e240_10 | 0.25 | 0.24 | 0.27 | -1.82 | 0.39 | 0.15 | 0.27 | 0.26 | 0.03 | 0.51 | 0.03 |
| e240_20 |  |  |  | 0.66 | -0.06 | 1.05 | -0.56 | -0.05 |  | 0.79 |  |
| f_or30 | -0.04 | -0.04 | 0.01 | 0.00 | -0.07 | 0.01 | -0.08 | -0.08 | -0.09 | -0.03 | -0.02 |
| f_or60 | -0.03 | -0.03 | 0.00 | 0.06 | -0.07 | 0.01 | -0.03 | 0.01 | -0.04 | -0.05 | -0.05 |

positive cells 34 of 138; CI above 0 in 0 cells; CI below 0 in 0 cells.


## IRL / ERL Step C: where D7 gets hurt (JN05W2 losing exits, 43 months)

**Verdict line: of 1895 full stops (Stop / StopJoin / StopJoinFallback), 4.3% were internal-level-only sweeps followed by a recovery of at least the risk within 30 min (6.8% within 60 min), and 5.8% were external-level sweeps followed by recovery within 60 min: SMALL, so the proposed stop-placement changes are not pursued from this table; recovery after a stop-out is higher when the swept level was internal-only (rec60 0.54) than external (0.34), in the direction of the claim, but descriptive only.**
A losing exit counts as "taken by a sweep" if a headline sweep event (fade direction = trade side) confirms within 15 min after the exit with the exit price inside the poke zone (level to poke extreme +-1 pt). ext = the swept level is external to at least one of the 13 ranges; int_only = tagged internal only. Recovery = price came back from the exit price toward/through the entry by at least the original risk (>= max(risk,1pt)) within 30/60 min (1m highs/lows). Descriptive only; the stop-placement tests (beyond the nearest external level within 1.25x the stop distance, lots reduced; no entry when the stop sits just inside an unswept internal level) need the exact engine hook (W-CF3) and are NOT run here.

| group | n losers | share swept | ext | int only | recovered 30m | recovered 60m | rec60 if swept | rec60 if int-only | rec60 if ext | sum loss $ |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL losers | 11135 | 0.266 | 0.106 | 0.159 | 0.295 | 0.415 | 0.458 | 0.538 | 0.338 | -16032286 |
| book A7 | 553 | 0.322 | 0.193 | 0.128 | 0.137 | 0.233 | 0.303 | 0.408 | 0.234 | -587025 |
| book H7 | 545 | 0.316 | 0.167 | 0.149 | 0.217 | 0.319 | 0.360 | 0.444 | 0.286 | -878226 |
| book K7 | 3981 | 0.257 | 0.093 | 0.165 | 0.296 | 0.416 | 0.448 | 0.511 | 0.336 | -3804342 |
| book M7 | 2323 | 0.227 | 0.079 | 0.149 | 0.325 | 0.455 | 0.489 | 0.557 | 0.361 | -2238420 |
| book O7 | 283 | 0.194 | 0.035 | 0.159 | 0.537 | 0.622 | 0.800 | 0.844 | 0.600 | -195288 |
| book P7 | 2806 | 0.277 | 0.102 | 0.175 | 0.313 | 0.438 | 0.497 | 0.574 | 0.365 | -6526100 |
| book U7 | 644 | 0.348 | 0.214 | 0.134 | 0.191 | 0.303 | 0.406 | 0.488 | 0.355 | -1802886 |
| exit BookLock | 104 | 0.183 | 0.019 | 0.163 | 0.529 | 0.596 | 0.526 | 0.529 | 0.500 | -100118 |
| exit EarlyCut | 2637 | 0.306 | 0.114 | 0.192 | 0.228 | 0.351 | 0.409 | 0.471 | 0.303 | -2852769 |
| exit StackCut | 291 | 0.402 | 0.285 | 0.117 | 0.203 | 0.309 | 0.444 | 0.412 | 0.458 | -266336 |
| exit StateCut | 6070 | 0.220 | 0.070 | 0.150 | 0.360 | 0.488 | 0.540 | 0.616 | 0.376 | -8937875 |
| exit Stop | 859 | 0.338 | 0.185 | 0.153 | 0.180 | 0.270 | 0.352 | 0.458 | 0.264 | -1248414 |
| exit StopJoin | 635 | 0.365 | 0.186 | 0.180 | 0.198 | 0.307 | 0.384 | 0.404 | 0.364 | -1476328 |
| exit StopJoinFallback | 401 | 0.382 | 0.239 | 0.142 | 0.097 | 0.202 | 0.314 | 0.404 | 0.260 | -1094865 |
| exit TimeBlock | 121 | 0.000 | 0.000 | 0.000 | 0.455 | 0.479 | nan | nan | nan | -47263 |

## IRL / ERL Step D: SCREEN of the proposed books (own 1m simulation, NOT the exact engine; no tuning; fixed small grid)

**Verdict line: Book 1 (fade external sweeps) averages -0.043 R/trade across range definitions and targets vs -0.053 R on its internal-sweep control; Book 2 (internal continuation) -0.070 R vs -0.161 R on external-sweep control. Screening only; positive cells: Book 1 ext 14 of 52, Book 1 control 0 of 52.**
Book 1 = fade the sweep of the range high/low at the close back inside, stop = poke extreme +2 pts, target 1R/1.5R/2R/range midpoint, time stop min(120 min, session end), cost 0.5 pt per trade. Control = the SAME book on internal sweeps. Book 2 = internal-sweep continuation: after an internal level is swept (poke direction), enter at the first retest of the level within 30 min, stop 1 ATR back inside, target the external boundary beyond (must be >1.5 ATR away); control = same on external sweeps. Table: expectancy in R per trade (net of cost), trades; full history and L6M. Per-session / per-side cells are in /mnt/l2/l2vast/_confl/irl/stepD.parquet. An exact-engine run through the CF hook is still to do for anything that looks interesting; screening results here are NOT leads.

**B1_ext_reversal, target 1.5R**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | ext | 460 | 0.035 | 0.45 | 80 | -0.082 |
| a_pd | int_control | 32377 | -0.048 | 0.41 | 5415 | 0.003 |
| b_ps | ext | 1488 | -0.045 | 0.41 | 243 | -0.072 |
| b_ps | int_control | 28981 | -0.050 | 0.40 | 5471 | -0.007 |
| b_cs60 | ext | 16137 | -0.056 | 0.40 | 2898 | -0.037 |
| b_cs60 | int_control | 27330 | -0.052 | 0.41 | 4898 | -0.015 |
| c_on | ext | 689 | -0.068 | 0.39 | 94 | 0.004 |
| c_on | int_control | 10374 | -0.052 | 0.40 | 1687 | -0.011 |
| d_wk | ext | 100 | 0.011 | 0.44 |  |  |
| d_wk | int_control | 33332 | -0.061 | 0.40 | 5894 | -0.017 |
| e15_10 | ext | 1413 | -0.041 | 0.41 | 232 | -0.086 |
| e15_10 | int_control | 28042 | -0.057 | 0.40 | 5137 | 0.009 |
| e15_20 | ext | 715 | 0.041 | 0.45 | 124 | -0.116 |
| e15_20 | int_control | 32647 | -0.054 | 0.40 | 5527 | -0.009 |
| e60_10 | ext | 382 | 0.042 | 0.44 | 57 | -0.152 |
| e60_10 | int_control | 32288 | -0.053 | 0.40 | 5167 | 0.004 |
| e60_20 | ext | 214 | -0.096 | 0.39 | 33 | -0.224 |
| e60_20 | int_control | 29175 | -0.061 | 0.40 | 5159 | -0.018 |
| e240_10 | ext | 102 | -0.081 | 0.40 |  |  |
| e240_10 | int_control | 29125 | -0.055 | 0.40 | 4941 | -0.018 |
| e240_20 | ext | 39 | -0.127 | 0.38 |  |  |
| e240_20 | int_control | 29049 | -0.056 | 0.40 | 5613 | -0.034 |
| f_or30 | ext | 2087 | -0.058 | 0.40 | 348 | 0.001 |
| f_or30 | int_control | 9231 | -0.039 | 0.41 | 1675 | 0.009 |
| f_or60 | ext | 1922 | -0.044 | 0.41 | 311 | 0.019 |
| f_or60 | int_control | 11009 | -0.044 | 0.41 | 1971 | 0.016 |

**B1_ext_reversal, target mid**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | ext | 455 | -0.114 | 0.33 | 79 | -0.361 |
| a_pd | int_control | 15933 | -0.092 | 0.33 | 2739 | -0.137 |
| b_ps | ext | 1443 | -0.034 | 0.38 | 234 | -0.117 |
| b_ps | int_control | 14816 | -0.064 | 0.39 | 2896 | -0.091 |
| b_cs60 | ext | 15855 | -0.076 | 0.33 | 2867 | -0.044 |
| b_cs60 | int_control | 16015 | -0.059 | 0.41 | 2834 | -0.037 |
| c_on | ext | 685 | -0.055 | 0.38 | 93 | -0.132 |
| c_on | int_control | 5608 | -0.029 | 0.42 | 916 | 0.043 |
| d_wk | ext | 100 | 0.098 | 0.33 |  |  |
| d_wk | int_control | 16414 | -0.047 | 0.28 | 2906 | -0.018 |
| e15_10 | ext | 1370 | -0.054 | 0.36 | 230 | -0.140 |
| e15_10 | int_control | 14652 | -0.083 | 0.38 | 2810 | -0.086 |
| e15_20 | ext | 705 | 0.044 | 0.37 | 124 | -0.274 |
| e15_20 | int_control | 17094 | -0.076 | 0.35 | 2998 | -0.117 |
| e60_10 | ext | 381 | 0.064 | 0.32 | 57 | -0.462 |
| e60_10 | int_control | 16826 | -0.065 | 0.32 | 2698 | -0.147 |
| e60_20 | ext | 214 | -0.176 | 0.27 | 33 | -0.521 |
| e60_20 | int_control | 14800 | -0.047 | 0.30 | 2623 | -0.022 |
| e240_10 | ext | 102 | -0.078 | 0.27 |  |  |
| e240_10 | int_control | 14653 | -0.051 | 0.29 | 2501 | -0.083 |
| e240_20 | ext | 39 | -0.072 | 0.23 |  |  |
| e240_20 | int_control | 14526 | -0.052 | 0.28 | 2859 | -0.011 |
| f_or30 | ext | 1955 | -0.056 | 0.47 | 333 | 0.148 |
| f_or30 | int_control | 3684 | -0.057 | 0.53 | 689 | 0.058 |
| f_or60 | ext | 1840 | -0.037 | 0.43 | 303 | 0.050 |
| f_or60 | int_control | 4762 | -0.045 | 0.49 | 889 | 0.059 |

**B2_int_continuation, target ext_level**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | int | 22038 | -0.099 | 0.25 | 3572 | -0.076 |
| b_ps | int | 17085 | -0.095 | 0.27 | 3328 | -0.097 |
| b_cs60 | int | 12437 | -0.067 | 0.29 | 2271 | -0.031 |
| b_cs60 | ext_control | 312 | -0.161 | 0.32 | 45 | 0.001 |
| c_on | int | 5406 | -0.062 | 0.28 | 908 | -0.104 |
| d_wk | int | 24449 | -0.043 | 0.25 | 4292 | -0.107 |
| e15_10 | int | 16812 | -0.066 | 0.27 | 3087 | -0.099 |
| e15_20 | int | 21662 | -0.081 | 0.26 | 3604 | -0.078 |
| e60_10 | int | 22649 | -0.085 | 0.25 | 3536 | -0.099 |
| e60_20 | int | 21029 | -0.064 | 0.25 | 3701 | -0.127 |
| e240_10 | int | 21495 | -0.046 | 0.25 | 3619 | -0.105 |
| e240_20 | int | 21513 | -0.055 | 0.25 | 4140 | -0.130 |
| f_or30 | int | 3315 | -0.075 | 0.31 | 646 | -0.086 |
| f_or60 | int | 4749 | -0.075 | 0.30 | 901 | -0.072 |


## B2-A momentum / oscillators

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 3105; |t|>2: 0 (chance expectation ~141 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_osc.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_1m_side | 178743 | 0.92 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_sig | 136514 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_rise | 152145 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_fresh5 | 91204 | 0.47 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_ewith_z1 | 18020 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eleave_z1 | 205 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eenter_z1 | 9388 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_ewith_z2 | 35909 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eleave_z2 | 585 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eenter_z2 | 17542 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_nodiv | 166545 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_divwith | 8697 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_side | 169040 | 0.87 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_sig | 138710 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_rise | 154270 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_fresh5 | 109746 | 0.57 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_ewith_z1 | 24078 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eleave_z1 | 358 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eenter_z1 | 17513 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_ewith_z2 | 43012 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eleave_z2 | 1179 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eenter_z2 | 27900 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_nodiv | 164115 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_divwith | 8840 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtS_1m_side | 178881 | 0.93 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_1m_side | 178743 | 0.92 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_sig | 136514 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_rise | 152145 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_fresh5 | 91204 | 0.47 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_ewith_z1 | 18020 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eleave_z1 | 205 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eenter_z1 | 9388 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_ewith_z2 | 35909 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eleave_z2 | 585 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_eenter_z2 | 17542 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_nodiv | 166545 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_1m_divwith | 8697 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_side | 169040 | 0.87 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_sig | 138710 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_rise | 154270 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_fresh5 | 109746 | 0.57 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_ewith_z1 | 24078 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eleave_z1 | 358 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eenter_z1 | 17513 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_ewith_z2 | 43012 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eleave_z2 | 1179 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_eenter_z2 | 27900 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_nodiv | 164115 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtF_1m_divwith | 8840 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wtS_1m_side | 178881 | 0.93 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 192 of 18246 session-condition cells pass (chance-level expectation under independence ~226 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_smiF_60m_eleave | 1961 | -0.150 | -0.075 | -3.0 | 0/4 | -0.115 |
| close | c4_crsi_15m_nodiv | 10631 | 0.120 | 0.072 | 3.0 | 4/4 | 0.203 |
| close | c4_elderS_bull_60m_divwith | 1868 | -0.138 | -0.067 | -2.7 | 0/4 | -0.166 |
| close | c4_sqzmS_on_3m_rise | 132 | -0.193 | -0.067 | -2.8 | 0/4 | -0.079 |
| close | c4_sqzmF_bright_1m_against | 1322 | 0.081 | 0.066 | 3.4 | 4/4 | 0.044 |
| close | c4_stc_15m_fresh5 | 3891 | 0.096 | 0.063 | 2.6 | 4/4 | 0.110 |
| london | c4_smie_5m_nodiv | 49633 | -0.118 | -0.087 | -4.0 | 0/4 | -0.080 |
| london | c4_tsiF_5m_nodiv | 49101 | -0.116 | -0.086 | -3.9 | 0/4 | -0.056 |
| london | c4_rsima7_1m_eleave | 945 | 0.114 | 0.079 | 3.5 | 4/4 | 0.145 |
| london | c4_wt_5m_nodiv | 50717 | -0.108 | -0.079 | -3.6 | 0/4 | -0.069 |
| london | c4_crsi_1d_eleave_z1 | 2856 | -0.199 | -0.077 | -3.2 | 0/4 | -0.195 |
| london | c4_qqe_5m_nodiv | 50451 | -0.108 | -0.077 | -3.4 | 0/4 | -0.086 |
| nyam | c4_elderF_bull_15m_nodiv | 20843 | 0.167 | 0.093 | 3.8 | 4/4 | 0.167 |
| nyam | c4_smiS_1m_eagainst | 179 | -0.256 | -0.084 | -3.6 | 0/4 | -0.332 |
| nyam | c4_smiF_3m_eleave | 1995 | -0.108 | -0.079 | -3.6 | 0/4 | -0.132 |
| nyam | c4_elder_bull_15m_nodiv | 21159 | 0.144 | 0.079 | 3.2 | 4/4 | 0.211 |
| nyam | c4_wtS_3m_ewith_z1 | 3449 | 0.126 | 0.075 | 3.0 | 4/4 | 0.107 |
| nyam | c4_smi_1m_eleave | 2221 | -0.090 | -0.073 | -3.7 | 0/4 | -0.095 |
| nypm | c4_wt_60m_ewith_z1 | 3432 | 0.244 | 0.101 | 4.1 | 4/4 | 0.379 |
| nypm | c4_coppS_60m_side | 14306 | 0.148 | 0.099 | 4.2 | 4/4 | 0.228 |
| nypm | c4_wtS_60m_ewith_z2 | 4004 | 0.205 | 0.098 | 3.9 | 4/4 | 0.300 |
| nypm | c4_kst_mtf_all | 4530 | 0.212 | 0.097 | 3.9 | 4/4 | 0.277 |
| nypm | c4_tsi_60m_side | 15173 | 0.144 | 0.097 | 4.1 | 4/4 | 0.215 |
| nypm | c4_kstS_mtf_all | 3649 | 0.229 | 0.096 | 3.9 | 4/4 | 0.131 |
| pre | c4_crsi_3m_eagainst_z2 | 215 | 0.299 | 0.093 | 4.0 | 4/4 | 0.042 |
| pre | c4_elderS_bear_60m_fresh5 | 2437 | 0.223 | 0.089 | 3.6 | 4/4 | 0.211 |
| pre | c4_rviS_5m_rise | 5923 | -0.129 | -0.086 | -3.7 | 0/4 | -0.221 |
| pre | c4_rvi_15m_fresh5 | 4914 | -0.135 | -0.072 | -2.9 | 0/4 | -0.349 |
| pre | c4_coppF_15m_rise | 6947 | -0.130 | -0.067 | -2.7 | 0/4 | -0.259 |
| pre | c4_rviS_5m_sig | 5984 | -0.105 | -0.066 | -2.7 | 0/4 | -0.123 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (1047 of 92392 cell-conditions pass; chance at t>2.5 alone ~572)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_qqeF_5m_ewith | 1957 | 0.139 | 0.018 | 0.120 | 5.6 | 4/4 | 0.178 |
| A7 | nypm | c4_coppS_60m_side | 2646 | 0.098 | -0.199 | 0.297 | 5.3 | 4/4 | 0.359 |
| K7 | asia | c4_tsiF_5m_ewith | 4648 | 0.091 | 0.009 | 0.082 | 5.3 | 4/4 | 0.123 |
| K7 | asia | c4_smieF_5m_ewith | 5904 | 0.075 | 0.007 | 0.068 | 5.2 | 3/4 | 0.099 |
| A7 | nypm | c4_wtS_60m_side | 2781 | 0.085 | -0.202 | 0.287 | 5.1 | 4/4 | 0.483 |
| K7 | asia | c4_tsiS_3m_ewith | 1246 | 0.181 | 0.021 | 0.161 | 5.0 | 4/4 | 0.245 |
| A7 | nypm | c4_tsi_60m_side | 2906 | 0.079 | -0.220 | 0.299 | 5.0 | 4/4 | 0.487 |
| K7 | asia | c4_smieS_3m_side | 12081 | 0.053 | -0.037 | 0.089 | 5.0 | 4/4 | 0.155 |
| K7 | asia | c4_smie_5m_ewith | 2588 | 0.123 | 0.015 | 0.108 | 5.0 | 4/4 | 0.124 |
| K7 | asia | c4_tsiS_5m_ewith | 1207 | 0.191 | 0.020 | 0.171 | 5.0 | 4/4 | 0.239 |
| K7 | asia | c4_smieF_15m_ewith | 4317 | 0.101 | 0.007 | 0.093 | 5.0 | 4/4 | 0.127 |
| K7 | asia | c4_smieS_5m_ewith | 1170 | 0.178 | 0.022 | 0.156 | 4.9 | 4/4 | 0.160 |
| K7 | asia | c4_rsima21_5m_eenter | 97 | 0.349 | 0.032 | 0.317 | 4.8 | 4/4 | 0.361 |
| K7 | asia | c4_tsi_5m_ewith | 2323 | 0.130 | 0.016 | 0.113 | 4.8 | 4/4 | 0.130 |
| K7 | asia | c4_smi_15m_ewith | 5437 | 0.087 | 0.004 | 0.083 | 4.7 | 4/4 | 0.077 |
| P7 | asia | c4_rsima14_15m_ewith | 1837 | 0.197 | 0.024 | 0.173 | 4.7 | 4/4 | 0.084 |
| K7 | asia | c4_qqe_5m_ewith | 549 | 0.212 | 0.027 | 0.185 | 4.6 | 4/4 | 0.267 |
| K7 | asia | c4_rsima14_5m_ewith | 660 | 0.196 | 0.026 | 0.170 | 4.6 | 4/4 | 0.205 |
| K7 | asia | c4_tsiF_5m_side | 11585 | 0.051 | -0.019 | 0.070 | 4.6 | 4/4 | 0.128 |
| A7 | nypm | c4_kstS_mtf_all | 943 | 0.249 | -0.087 | 0.335 | 4.6 | 4/4 | 0.177 |
| K7 | asia | c4_qqeS_5m_side | 9686 | 0.065 | -0.020 | 0.085 | 4.5 | 4/4 | 0.138 |
| K7 | asia | c4_qqeS_3m_side | 11539 | 0.055 | -0.030 | 0.085 | 4.5 | 4/4 | 0.165 |
| K7 | asia | c4_mc_comp2_15m_side | 9844 | 0.064 | -0.021 | 0.085 | 4.5 | 4/4 | 0.172 |
| K7 | asia | c4_tsiS_5m_side | 8953 | 0.071 | -0.018 | 0.089 | 4.5 | 4/4 | 0.159 |
| K7 | asia | c4_elderS_bull_3m_side | 13781 | 0.045 | -0.061 | 0.106 | 4.5 | 4/4 | 0.117 |
| A7 | nypm | c4_qqeS_60m_side | 2905 | 0.075 | -0.208 | 0.283 | 4.5 | 4/4 | 0.485 |
| K7 | asia | c4_rsima14_15m_side | 9492 | 0.069 | -0.023 | 0.092 | 4.5 | 4/4 | 0.173 |
| K7 | asia | c4_smiS_5m_ewith | 6074 | 0.077 | 0.005 | 0.071 | 4.4 | 4/4 | 0.087 |
| P7 | asia | c4_qqe_15m_ewith | 1512 | 0.219 | 0.025 | 0.194 | 4.4 | 4/4 | 0.097 |
| K7 | asia | c4_rsima7_60m_eenter | 956 | 0.200 | 0.023 | 0.178 | 4.4 | 3/4 | 0.242 |

## B2-B trend followers

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 3314; |t|>2: 0 (chance expectation ~150 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_trend.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_utbot_1m_fresh5 | 88162 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_fresh1 | 29928 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_side | 158810 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_rise | 141618 | 0.73 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_fresh5 | 88525 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_fresh1 | 30244 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_side | 159336 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_rise | 139970 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_fresh5 | 42507 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_fresh1 | 14838 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_side | 162912 | 0.84 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_rise | 146538 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_fresh5 | 41824 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_fresh1 | 13985 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_side | 176385 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_against | 16860 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_hold3 | 154146 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_fresh5 | 66190 | 0.34 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_fresh1 | 22853 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_side | 164501 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_against | 28744 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_hold3 | 129151 | 0.67 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_fresh5 | 28335 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_fresh1 | 8445 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_side | 177899 | 0.92 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_utbot_1m_fresh5 | 88162 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_fresh1 | 29928 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_side | 158810 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbot_1m_rise | 141618 | 0.73 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_fresh5 | 88525 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_fresh1 | 30244 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_side | 159336 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotF_1m_rise | 139970 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_fresh5 | 42507 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_fresh1 | 14838 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_side | 162912 | 0.84 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_utbotS_1m_rise | 146538 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_fresh5 | 41824 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_fresh1 | 13985 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_side | 176385 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_against | 16860 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chand_1m_hold3 | 154146 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_fresh5 | 66190 | 0.34 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_fresh1 | 22853 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_side | 164501 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_against | 28744 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandF_1m_hold3 | 129151 | 0.67 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_fresh5 | 28335 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_fresh1 | 8445 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chandS_1m_side | 177899 | 0.92 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 224 of 19429 session-condition cells pass (chance-level expectation under independence ~240 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_rfiltF_dir_60m_fresh5 | 3803 | -0.168 | -0.098 | -4.0 | 0/4 | -0.117 |
| close | c4_rfiltF_60m_fresh5 | 3803 | -0.168 | -0.098 | -4.0 | 0/4 | -0.117 |
| close | c4_chand_60m_fresh5 | 3473 | -0.149 | -0.082 | -3.3 | 0/4 | -0.167 |
| close | c4_chand_60m_fresh1 | 888 | -0.204 | -0.072 | -3.0 | 0/4 | -0.303 |
| close | c4_don20_pos_60m_fresh5 | 5567 | -0.108 | -0.068 | -2.8 | 0/4 | -0.117 |
| close | c4_ichi_cloud_1d_side | 6153 | 0.113 | 0.066 | 2.7 | 4/4 | 0.159 |
| london | c4_rfiltS_mtf_n | 999 | -0.168 | -0.092 | -3.7 | 0/4 | -0.128 |
| london | c4_chand_mtf_n | 632 | -0.142 | -0.078 | -3.1 | 0/4 | -0.101 |
| london | c4_halftS_mtf_n | 1326 | -0.120 | -0.073 | -3.0 | 0/4 | -0.086 |
| london | c4_nwe_15m_fresh5 | 385 | 0.292 | 0.071 | 3.3 | 4/4 | 0.088 |
| london | c4_nweS_5m_fresh5 | 392 | -0.130 | -0.070 | -2.8 | 0/4 | -0.294 |
| london | c4_turt10_mtf_all | 3359 | 0.115 | 0.070 | 2.9 | 4/4 | 0.076 |
| nyam | c4_lrcS_15m_eleave | 1127 | -0.188 | -0.082 | -3.3 | 0/4 | -0.107 |
| nyam | c4_alli_spread_1m_side | 20843 | 0.093 | 0.075 | 3.8 | 4/4 | 0.139 |
| nyam | c4_ichiF_score_60m_eleave | 3694 | -0.121 | -0.073 | -3.0 | 0/4 | -0.164 |
| nyam | c4_turt20_60m_fresh1 | 2223 | -0.136 | -0.072 | -2.9 | 0/4 | -0.055 |
| nyam | c4_alma_x_1d_fresh1 | 734 | -0.252 | -0.070 | -3.1 | 0/4 | -0.208 |
| nyam | c4_alma_x_1m_fresh1 | 1831 | -0.086 | -0.068 | -3.3 | 0/4 | -0.017 |
| nypm | c4_turt55_mtf_all | 1953 | 0.256 | 0.088 | 3.7 | 4/4 | 0.013 |
| nypm | c4_halft_60m_hold3 | 13591 | 0.137 | 0.087 | 3.6 | 4/4 | 0.105 |
| nypm | c4_stP_60m_against | 10134 | -0.135 | -0.086 | -3.6 | 0/4 | -0.153 |
| nypm | c4_stP_60m_side | 15000 | 0.135 | 0.086 | 3.6 | 4/4 | 0.153 |
| nypm | c4_stP_60m_hold3 | 13358 | 0.142 | 0.085 | 3.5 | 4/4 | 0.168 |
| nypm | c4_turt20_mtf_all | 2400 | 0.183 | 0.083 | 3.3 | 4/4 | 0.300 |
| pre | c4_sslhyb_5m_side | 7508 | -0.142 | -0.075 | -3.0 | 0/4 | -0.181 |
| pre | c4_lrcS_1m_side | 8322 | -0.196 | -0.070 | -2.9 | 0/4 | -0.265 |
| pre | c4_t3S_px_1d_rise | 4661 | 0.171 | 0.070 | 2.8 | 4/4 | 0.142 |
| pre | c4_chandF_60m_fresh1 | 824 | -0.238 | -0.069 | -3.0 | 0/4 | -0.441 |
| pre | c4_ssl_5m_against | 1149 | 0.122 | 0.069 | 2.8 | 4/4 | 0.264 |
| pre | c4_ssl_5m_side | 8107 | -0.122 | -0.069 | -2.8 | 0/4 | -0.264 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (1333 of 96890 cell-conditions pass; chance at t>2.5 alone ~600)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_rfiltF_dir_mtf_ge4 | 9657 | 0.075 | -0.037 | 0.112 | 5.9 | 4/4 | 0.177 |
| K7 | asia | c4_hiloS_5m_side | 11724 | 0.051 | -0.023 | 0.075 | 4.8 | 4/4 | 0.141 |
| K7 | asia | c4_ichiF_chikou_5m_hold3 | 8733 | 0.061 | -0.002 | 0.063 | 4.8 | 4/4 | 0.141 |
| K7 | asia | c4_rfiltS_15m_side | 9054 | 0.073 | -0.023 | 0.096 | 4.8 | 4/4 | 0.119 |
| K7 | asia | c4_ichiF_cloud_5m_hold3 | 7607 | 0.072 | -0.004 | 0.075 | 4.7 | 4/4 | 0.112 |
| K7 | asia | c4_alligator_5m_side | 7318 | 0.075 | -0.004 | 0.080 | 4.7 | 4/4 | 0.135 |
| K7 | asia | c4_fractal_alli_15m_hold3 | 6339 | 0.089 | -0.005 | 0.094 | 4.7 | 4/4 | 0.195 |
| K7 | asia | c4_rfiltS_mtf_ge4 | 10081 | 0.068 | -0.031 | 0.099 | 4.6 | 4/4 | 0.110 |
| K7 | asia | c4_alligator_5m_hold3 | 6450 | 0.078 | 0.001 | 0.077 | 4.6 | 4/4 | 0.119 |
| K7 | asia | c4_hiloS_5m_hold3 | 9542 | 0.059 | -0.008 | 0.067 | 4.6 | 4/4 | 0.120 |
| K7 | asia | c4_turt55_5m_side | 5043 | 0.095 | 0.004 | 0.091 | 4.5 | 4/4 | 0.129 |
| K7 | asia | c4_sslS_5m_hold3 | 9580 | 0.058 | -0.007 | 0.065 | 4.5 | 4/4 | 0.110 |
| K7 | asia | c4_ichi_tk_5m_side | 9019 | 0.061 | -0.006 | 0.067 | 4.5 | 4/4 | 0.098 |
| K7 | asia | c4_rfilt_mtf_ge4 | 10798 | 0.061 | -0.032 | 0.093 | 4.5 | 4/4 | 0.142 |
| H7 | asia | c4_ichiF_tk_15m_nodiv | 736 | 0.099 | -0.151 | 0.250 | 4.5 | 4/4 | 0.236 |
| K7 | asia | c4_stA21_5m_hold3 | 9297 | 0.062 | -0.010 | 0.072 | 4.5 | 4/4 | 0.097 |
| K7 | asia | c4_ichi_cloud_3m_hold3 | 8136 | 0.068 | -0.005 | 0.072 | 4.4 | 4/4 | 0.069 |
| K7 | asia | c4_fractal_alli_15m_side | 7699 | 0.076 | -0.009 | 0.086 | 4.4 | 4/4 | 0.184 |
| K7 | asia | c4_utbotS_5m_side | 10679 | 0.056 | -0.018 | 0.075 | 4.4 | 4/4 | 0.063 |
| K7 | asia | c4_sslS_5m_side | 11826 | 0.050 | -0.020 | 0.070 | 4.4 | 4/4 | 0.116 |
| K7 | asia | c4_ichiF_cloud_15m_side | 7058 | 0.080 | -0.006 | 0.086 | 4.4 | 4/4 | 0.151 |
| K7 | asia | c4_hiloS_15m_side | 8916 | 0.071 | -0.019 | 0.090 | 4.4 | 4/4 | 0.190 |
| K7 | asia | c4_alligator_mtf_ge4 | 5756 | 0.080 | 0.006 | 0.074 | 4.4 | 4/4 | 0.109 |
| K7 | asia | c4_turt55_5m_hold3 | 4881 | 0.094 | 0.006 | 0.088 | 4.3 | 4/4 | 0.131 |
| K7 | asia | c4_alli_spread_5m_side | 8823 | 0.065 | -0.009 | 0.074 | 4.3 | 4/4 | 0.145 |
| K7 | asia | c4_rfiltF_60m_side | 8360 | 0.078 | -0.019 | 0.097 | 4.3 | 4/4 | 0.141 |
| K7 | asia | c4_stAF_15m_side | 8518 | 0.072 | -0.014 | 0.086 | 4.3 | 4/4 | 0.093 |
| A7 | nypm | c4_lrcS_slope_5m_side | 2883 | 0.064 | -0.176 | 0.239 | 4.3 | 4/4 | 0.323 |
| K7 | asia | c4_hiloS_15m_hold3 | 8011 | 0.074 | -0.010 | 0.084 | 4.3 | 4/4 | 0.164 |
| K7 | asia | c4_fractal_alli_5m_hold3 | 7939 | 0.064 | 0.001 | 0.062 | 4.3 | 4/4 | 0.094 |

## B2-C smart-money / price action

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 1912; |t|>2: 0 (chance expectation ~86 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_smc.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_struct_1m_fresh5 | 41302 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_fresh1 | 16718 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_side | 164752 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_against | 28493 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_hold3 | 149020 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_fresh5 | 28631 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_fresh1 | 10256 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_side | 164752 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_against | 28493 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_hold3 | 149020 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_fresh5 | 24406 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_fresh1 | 2322 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_side | 4707 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_against | 35955 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_hold3 | 2235 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_side | 25103 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_against | 54508 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_hold3 | 14437 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_side | 146102 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_rise | 37146 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_fresh5 | 9277 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dsup_1m_hi | 48202 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dsup_1m_rise | 91177 | 0.56 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dres_1m_hi | 42012 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dres_1m_rise | 77868 | 0.52 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_struct_1m_fresh5 | 41302 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_fresh1 | 16718 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_side | 164752 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_against | 28493 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_struct_1m_hold3 | 149020 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_fresh5 | 28631 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_fresh1 | 10256 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_side | 164752 | 0.85 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_against | 28493 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_choch_1m_hold3 | 149020 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_fresh5 | 24406 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_fresh1 | 2322 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_side | 4707 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_against | 35955 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_in_1m_hold3 | 2235 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_side | 25103 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_against | 54508 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_near_1m_hold3 | 14437 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_side | 146102 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_rise | 37146 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_cnt_1m_fresh5 | 9277 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dsup_1m_hi | 48202 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dsup_1m_rise | 91177 | 0.56 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dres_1m_hi | 42012 | 0.28 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_ob_dres_1m_rise | 77868 | 0.52 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 128 of 10924 session-condition cells pass (chance-level expectation under independence ~135 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_oteF_5m_against | 1020 | -0.134 | -0.086 | -3.6 | 0/4 | -0.133 |
| close | c4_brkS_near_3m_against | 1914 | -0.133 | -0.079 | -3.2 | 0/4 | -0.134 |
| close | c4_pdS_1m_fresh5 | 1452 | -0.109 | -0.079 | -3.5 | 0/4 | -0.161 |
| close | c4_brkS_near_mtf_ge4 | 157 | 0.438 | 0.078 | 4.1 | 4/4 | 0.848 |
| close | c4_sd_in_60m_fresh1 | 820 | -0.202 | -0.070 | -2.9 | 0/4 | -0.297 |
| close | c4_ifvgS_near_15m_side | 2049 | -0.146 | -0.070 | -2.8 | 0/4 | -0.138 |
| london | c4_eqsweep_1d_fresh5 | 917 | 0.289 | 0.119 | 4.8 | 3/3 | 0.379 |
| london | c4_eqsweep_1d_against | 128 | -0.481 | -0.118 | -5.5 | 0/3 | -0.743 |
| london | c4_chochF_60m_fresh5 | 8480 | 0.109 | 0.064 | 2.6 | 4/4 | 0.167 |
| london | c4_po3_asia_conf_1m_hold3 | 8984 | 0.106 | 0.062 | 2.5 | 4/4 | 0.179 |
| london | c4_chochF_60m_side | 32303 | 0.080 | 0.060 | 2.8 | 4/4 | 0.068 |
| london | c4_structF_60m_side | 32303 | 0.080 | 0.060 | 2.8 | 4/4 | 0.068 |
| nyam | c4_brk_in_3m_against | 2472 | -0.127 | -0.090 | -4.0 | 0/4 | -0.073 |
| nyam | c4_sdflip_in_1d_against | 2978 | 0.166 | 0.082 | 3.3 | 4/4 | 0.119 |
| nyam | c4_sdS_dsup_1d_rise | 13457 | 0.123 | 0.082 | 3.5 | 4/4 | 0.121 |
| nyam | c4_fvgF_dres_1d_rise | 5101 | -0.137 | -0.082 | -3.3 | 0/4 | -0.201 |
| nyam | c4_brkS_in_15m_against | 2137 | -0.151 | -0.080 | -3.2 | 0/4 | -0.215 |
| nyam | c4_sdF_cnt_3m_fresh5 | 1516 | -0.144 | -0.079 | -3.2 | 0/4 | -0.067 |
| nypm | c4_pdS_5m_eleave | 1033 | -0.170 | -0.094 | -3.8 | 0/4 | -0.234 |
| nypm | c4_fvgS_near_60m_against | 7422 | -0.155 | -0.091 | -3.7 | 0/4 | -0.064 |
| nypm | c4_obS_cnt_mtf_all | 4526 | 0.202 | 0.089 | 3.6 | 4/4 | 0.200 |
| nypm | c4_sdS_cnt_mtf_all | 4852 | 0.175 | 0.086 | 3.5 | 4/4 | 0.158 |
| nypm | c4_pdS_60m_eagainst | 12572 | 0.125 | 0.084 | 3.6 | 4/4 | 0.328 |
| nypm | c4_fvgS_near_15m_against | 6531 | -0.126 | -0.083 | -3.5 | 0/4 | -0.143 |
| pre | c4_structS_1d_fresh1 | 135 | -0.712 | -0.105 | -5.9 | 0/4 | -0.633 |
| pre | c4_struct_1m_fresh1 | 802 | -0.120 | -0.072 | -3.0 | 0/4 | -0.042 |
| pre | c4_eqpool_dnF_5m_rise | 1663 | -0.141 | -0.068 | -2.7 | 0/4 | -0.131 |
| pre | c4_ob_in_3m_fresh5 | 1348 | 0.136 | 0.067 | 2.7 | 4/4 | 0.076 |
| pre | c4_ob_in_1m_fresh5 | 1220 | 0.102 | 0.066 | 2.7 | 4/4 | 0.125 |
| pre | c4_fvgF_cnt_mtf_n | 1199 | -0.215 | -0.066 | -2.8 | 0/4 | -0.241 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (552 of 51384 cell-conditions pass; chance at t>2.5 alone ~318)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| P7 | london | c4_eqsweep_1d_fresh5 | 299 | 0.290 | 0.014 | 0.276 | 4.8 | 3/3 | 0.341 |
| K7 | asia | c4_fvgF_cnt_60m_rise | 2168 | 0.122 | 0.019 | 0.103 | 4.3 | 4/4 | 0.191 |
| K7 | asia | c4_fvg_cnt_60m_rise | 1572 | 0.135 | 0.022 | 0.113 | 4.2 | 4/4 | 0.192 |
| A7 | nypm | c4_pdS_60m_eagainst | 2640 | 0.071 | -0.148 | 0.219 | 4.2 | 4/4 | 0.529 |
| K7 | asia | c4_fvgF_cnt_1m_side | 10236 | 0.062 | -0.023 | 0.086 | 4.1 | 4/4 | 0.164 |
| A7 | nypm | c4_obS_cnt_mtf_all | 1060 | 0.215 | -0.083 | 0.298 | 4.1 | 4/4 | 0.224 |
| M7 | pre | c4_ob_near_3m_side | 396 | 0.241 | -0.046 | 0.286 | 4.1 | 3/4 | 0.435 |
| M7 | pre | c4_ob_near_3m_hold3 | 182 | 0.332 | -0.027 | 0.359 | 4.1 | 3/4 | 0.532 |
| A7 | nypm | c4_choch_60m_hold3 | 2447 | 0.086 | -0.144 | 0.229 | 4.0 | 4/4 | 0.420 |
| A7 | nypm | c4_struct_60m_hold3 | 2447 | 0.086 | -0.144 | 0.229 | 4.0 | 4/4 | 0.420 |
| K7 | asia | c4_fvg_cnt_1m_side | 10177 | 0.062 | -0.022 | 0.083 | 4.0 | 4/4 | 0.181 |
| A7 | nypm | c4_fvgF_near_5m_side | 1658 | 0.086 | -0.068 | 0.154 | 4.0 | 4/4 | 0.061 |
| A7 | nypm | c4_ob_cnt_mtf_all | 1172 | 0.189 | -0.084 | 0.273 | 3.9 | 4/4 | 0.324 |
| K7 | asia | c4_sdF_cnt_1m_side | 9554 | 0.066 | -0.020 | 0.086 | 3.9 | 4/4 | 0.176 |
| A7 | nypm | c4_sd_cnt_15m_side | 2837 | 0.066 | -0.172 | 0.238 | 3.9 | 3/4 | 0.398 |
| P7 | nyam | c4_oteF_3m_against | 796 | 0.132 | -0.002 | 0.134 | 3.9 | 4/4 | 0.134 |
| K7 | asia | c4_sdS_cnt_1m_side | 9078 | 0.068 | -0.016 | 0.084 | 3.9 | 4/4 | 0.230 |
| A7 | london | c4_sdS_cnt_1d_fresh5 | 94 | 0.354 | 0.034 | 0.320 | 3.9 | 3/3 | 0.393 |
| A7 | nyam | c4_structS_60m_hold3 | 1904 | 0.132 | -0.079 | 0.211 | 3.9 | 4/4 | 0.238 |
| A7 | nyam | c4_chochS_60m_hold3 | 1904 | 0.132 | -0.079 | 0.211 | 3.9 | 4/4 | 0.238 |
| A7 | nypm | c4_sdS_cnt_mtf_all | 1124 | 0.183 | -0.077 | 0.260 | 3.9 | 4/4 | 0.203 |
| K7 | nypm | c4_fvg_near_mtf_ge4 | 217 | 0.217 | -0.017 | 0.234 | 3.9 | 4/4 | 0.370 |
| K7 | asia | c4_fvgF_near_1m_side | 3251 | 0.080 | 0.021 | 0.059 | 3.8 | 4/4 | 0.050 |
| K7 | london | c4_eqsweep_1d_fresh5 | 193 | 0.328 | 0.005 | 0.322 | 3.8 | 3/3 | 0.391 |
| A7 | london | c4_structS_5m_fresh1 | 576 | 0.167 | 0.027 | 0.139 | 3.8 | 4/4 | 0.159 |
| U7 | london | c4_brk_in_mtf_n | 243 | 0.188 | -0.050 | 0.238 | 3.8 | 4/4 | 0.359 |
| K7 | asia | c4_chochF_mtf_all | 1977 | 0.132 | 0.019 | 0.113 | 3.8 | 4/4 | 0.219 |
| K7 | asia | c4_structF_mtf_all | 1977 | 0.132 | 0.019 | 0.113 | 3.8 | 4/4 | 0.219 |
| K7 | asia | c4_struct_5m_hold3 | 8974 | 0.062 | -0.007 | 0.069 | 3.7 | 4/4 | 0.118 |
| K7 | asia | c4_choch_5m_hold3 | 8974 | 0.062 | -0.007 | 0.069 | 3.7 | 4/4 | 0.118 |

## B2-D volume

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 482; |t|>2: 0 (chance expectation ~21 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_vol.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_rvol_1m_hi | 95577 | 0.49 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_hi_z1 | 51834 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_lo_z1 | 57223 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_hi_z2 | 19215 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_lo_z2 | 30249 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_rise | 115667 | 0.60 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_side | 161049 | 0.83 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_rise | 135954 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_fresh5 | 183208 | 0.95 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_ewith | 46501 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eagainst | 4896 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eleave | 27206 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eenter | 45045 | 0.23 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_side | 135647 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_rise | 118995 | 0.62 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_fresh5 | 176731 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_side | 135647 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_rise | 113707 | 0.59 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_fresh5 | 173693 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_ewith | 51261 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eagainst | 6400 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eleave | 45945 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eenter | 49719 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cvd_1m_side | 142267 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cvd_1m_rise | 121190 | 0.63 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_rvol_1m_hi | 95577 | 0.49 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_hi_z1 | 51834 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_lo_z1 | 57223 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_hi_z2 | 19215 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_lo_z2 | 30249 | 0.16 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_1m_rise | 115667 | 0.60 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_side | 161049 | 0.83 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_rise | 135954 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_fresh5 | 183208 | 0.95 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_ewith | 46501 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eagainst | 4896 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eleave | 27206 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_rvol_dir_1m_eenter | 45045 | 0.23 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_side | 135647 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_rise | 118995 | 0.62 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_1m_fresh5 | 176731 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_side | 135647 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_rise | 113707 | 0.59 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_fresh5 | 173693 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_ewith | 51261 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eagainst | 6400 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eleave | 45945 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_delta_ratio_1m_eenter | 49719 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cvd_1m_side | 142267 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cvd_1m_rise | 121190 | 0.63 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 15 of 2491 session-condition cells pass (chance-level expectation under independence ~30 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| london | c4_rvol_dir_5m_eagainst | 2430 | 0.085 | 0.062 | 2.8 | 4/4 | 0.079 |
| london | c4_vp_frsw_poc_ahead | 6622 | 0.052 | 0.046 | 2.8 | 4/4 | 0.079 |
| london | c4_vp_frsw_poc_side | 50721 | -0.050 | -0.044 | -2.7 | 0/4 | -0.081 |
| london | c4_cvdS_1m_rise | 36966 | 0.021 | 0.021 | 2.6 | 4/4 | 0.027 |
| nyam | c4_avwap_swing_lo_15m_fresh5 | 3258 | -0.062 | -0.050 | -2.5 | 0/4 | -0.008 |
| nyam | c4_cvd_ema_1m_nodiv | 19313 | -0.053 | -0.046 | -2.6 | 0/4 | -0.103 |
| nypm | c4_vsa_nodemand_1d_fresh5 | 7728 | -0.150 | -0.079 | -3.2 | 0/4 | -0.117 |
| nypm | c4_avwap_month_open_far | 21725 | 0.135 | 0.070 | 2.8 | 4/4 | 0.232 |
| nypm | c4_cvdS_60m_fresh5 | 5731 | 0.121 | 0.070 | 2.8 | 4/4 | 0.083 |
| nypm | c4_cvd_ema_1m_side | 20607 | -0.068 | -0.055 | -2.8 | 0/4 | -0.106 |
| nypm | c4_rvol_3m_rise | 13007 | -0.039 | -0.037 | -3.3 | 0/4 | -0.030 |
| pre | c4_vp_psess_hvn_near | 573 | 0.257 | 0.103 | 4.2 | 4/4 | 0.092 |
| pre | c4_rvol_dir_15m_eagainst | 266 | -0.327 | -0.085 | -3.9 | 0/4 | -0.269 |
| pre | c4_cvdS_3m_side | 6937 | -0.144 | -0.066 | -2.6 | 0/4 | -0.256 |
| pre | c4_vp_frsw_pocdist_gt1.5 | 1642 | -0.150 | -0.064 | -2.6 | 0/4 | -0.253 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (86 of 11789 cell-conditions pass; chance at t>2.5 alone ~73)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_rvol_dir_15m_ewith | 1493 | 0.136 | 0.023 | 0.113 | 4.7 | 4/4 | 0.075 |
| K7 | asia | c4_rvol_dir_15m_eenter | 1405 | 0.129 | 0.024 | 0.105 | 4.4 | 4/4 | 0.067 |
| K7 | asia | c4_rvol_15m_hi_z1 | 1926 | 0.119 | 0.022 | 0.098 | 4.4 | 4/4 | 0.076 |
| K7 | asia | c4_vp_psess_va_above | 8940 | 0.075 | -0.024 | 0.100 | 4.4 | 4/4 | 0.119 |
| K7 | asia | c4_avwap_swing_lo_60m_side | 10174 | 0.066 | -0.030 | 0.096 | 4.2 | 4/4 | 0.244 |
| K7 | asia | c4_avwap_pd_low_rise | 8959 | 0.073 | -0.021 | 0.094 | 4.1 | 4/4 | 0.171 |
| K7 | asia | c4_avwap_pd_low_side | 9612 | 0.069 | -0.025 | 0.094 | 4.1 | 4/4 | 0.165 |
| K7 | asia | c4_avwap_swing_lo_60m_rise | 9340 | 0.067 | -0.018 | 0.085 | 4.0 | 4/4 | 0.203 |
| A7 | nyam | c4_delta_ratio_5m_fresh5 | 3275 | 0.058 | -0.184 | 0.242 | 3.9 | 4/4 | 0.338 |
| A7 | nyam | c4_delta_5m_fresh5 | 3275 | 0.058 | -0.184 | 0.242 | 3.9 | 4/4 | 0.338 |
| P7 | asia | c4_avwap_ge7 | 17699 | 0.058 | -0.037 | 0.095 | 3.7 | 4/4 | 0.191 |
| K7 | asia | c4_avwap_asia_open_rise | 10529 | 0.060 | -0.022 | 0.082 | 3.7 | 4/4 | 0.161 |
| K7 | asia | c4_vp_psess_poc_side | 10174 | 0.063 | -0.024 | 0.087 | 3.6 | 4/4 | 0.073 |
| P7 | asia | c4_vp_fr240_pocdist_gt1.5 | 5885 | 0.089 | 0.020 | 0.069 | 3.6 | 4/4 | 0.045 |
| K7 | asia | c4_avwap_asia_open_side | 12313 | 0.053 | -0.043 | 0.096 | 3.6 | 4/4 | 0.166 |
| K7 | asia | c4_avwap_ge9 | 8716 | 0.069 | -0.013 | 0.082 | 3.5 | 3/4 | 0.155 |
| A7 | nypm | c4_vp_fr1440_poc_side | 3712 | 0.018 | -0.257 | 0.274 | 3.5 | 4/4 | 0.322 |
| K7 | asia | c4_avwap_nypm_open_side | 9640 | 0.063 | -0.016 | 0.080 | 3.4 | 3/4 | 0.216 |
| K7 | asia | c4_avwap_nypm_open_rise | 8930 | 0.066 | -0.012 | 0.078 | 3.4 | 3/4 | 0.238 |
| K7 | london | c4_vp_frsw_poc_ahead | 825 | 0.119 | 0.003 | 0.116 | 3.4 | 3/4 | 0.227 |
| K7 | asia | c4_rvol_15m_hi_z2 | 413 | 0.208 | 0.029 | 0.179 | 3.3 | 4/4 | 0.378 |
| K7 | nypm | c4_cvdS_60m_fresh5 | 1056 | 0.096 | -0.032 | 0.128 | 3.3 | 4/4 | 0.047 |
| K7 | asia | c4_avwap_ge7 | 10591 | 0.057 | -0.018 | 0.075 | 3.3 | 3/4 | 0.210 |
| K7 | asia | c4_avwap_pd_low_far | 9436 | 0.056 | -0.002 | 0.057 | 3.2 | 4/4 | 0.112 |
| M7 | pre | c4_avwap_midnight_side | 2521 | 0.010 | -0.370 | 0.380 | 3.2 | 4/4 | 0.495 |
| K7 | asia | c4_rvol_dir_3m_eleave | 1978 | 0.087 | 0.026 | 0.061 | 3.2 | 4/4 | 0.019 |
| P7 | nypm | c4_avwap_month_open_far | 7081 | 0.010 | -0.166 | 0.176 | 3.2 | 4/4 | 0.220 |
| P7 | asia | c4_avwap_month_open_side | 12802 | 0.071 | -0.006 | 0.077 | 3.2 | 4/4 | 0.143 |
| P7 | asia | c4_avwap_ge5 | 20237 | 0.048 | -0.052 | 0.099 | 3.2 | 4/4 | 0.229 |
| P7 | asia | c4_avwap_month_open_rise | 12692 | 0.071 | -0.006 | 0.077 | 3.2 | 4/4 | 0.149 |

## B2-E causal ML-style

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 222; |t|>2: 0 (chance expectation ~10 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_ml.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_kr_dir_1m_fresh5 | 24451 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_fresh1 | 6526 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_side | 188502 | 0.98 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_rise | 155524 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_side | 188408 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_rise | 154192 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_fresh5 | 60469 | 0.31 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_fresh5 | 37389 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_fresh1 | 10234 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_side | 181298 | 0.94 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_rise | 153377 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_side | 185856 | 0.96 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_rise | 152073 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_fresh5 | 86598 | 0.45 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_fresh5 | 16465 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_fresh1 | 4634 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_side | 187660 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_rise | 156905 | 0.81 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_side | 188441 | 0.98 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_rise | 155823 | 0.81 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_fresh5 | 43835 | 0.23 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_fresh5 | 22617 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_fresh1 | 5803 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_side | 184829 | 0.96 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_rise | 127319 | 0.66 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_kr_dir_1m_fresh5 | 24451 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_fresh1 | 6526 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_side | 188502 | 0.98 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_1m_rise | 155524 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_side | 188408 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_rise | 154192 | 0.80 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_px_1m_fresh5 | 60469 | 0.31 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_fresh5 | 37389 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_fresh1 | 10234 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_side | 181298 | 0.94 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_dir_1m_rise | 153377 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_side | 185856 | 0.96 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_rise | 152073 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krF_px_1m_fresh5 | 86598 | 0.45 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_fresh5 | 16465 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_fresh1 | 4634 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_side | 187660 | 0.97 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_dir_1m_rise | 156905 | 0.81 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_side | 188441 | 0.98 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_rise | 155823 | 0.81 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_krS_px_1m_fresh5 | 43835 | 0.23 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_fresh5 | 22617 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_fresh1 | 5803 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_side | 184829 | 0.96 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_kr_dir_3m_rise | 127319 | 0.66 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 11 of 1283 session-condition cells pass (chance-level expectation under independence ~15 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_lor_3m_rise | 5317 | -0.043 | -0.039 | -2.5 | 0/4 | -0.140 |
| london | c4_lorS_60m_rise | 21179 | 0.044 | 0.040 | 2.5 | 4/4 | 0.054 |
| nyam | c4_kr_dir_1m_fresh1 | 900 | -0.134 | -0.085 | -3.5 | 0/4 | -0.232 |
| nyam | c4_krS_dir_1m_fresh5 | 2106 | -0.084 | -0.067 | -3.3 | 0/4 | -0.031 |
| nyam | c4_kr_dir_1m_fresh5 | 3240 | -0.074 | -0.062 | -3.4 | 0/4 | -0.089 |
| nyam | c4_krF_dir_1m_fresh5 | 4750 | -0.066 | -0.057 | -3.3 | 0/4 | -0.153 |
| nyam | c4_lor_60m_unanimous | 110 | -0.490 | -0.039 | -2.9 | 0/3 | -0.620 |
| nypm | c4_krF_px_60m_fresh5 | 12825 | -0.117 | -0.073 | -3.0 | 0/4 | -0.122 |
| nypm | c4_krS_px_60m_fresh5 | 9112 | -0.112 | -0.069 | -2.8 | 0/4 | -0.173 |
| pre | c4_krS_dir_60m_side | 5438 | 0.150 | 0.066 | 2.7 | 4/4 | 0.166 |
| pre | c4_krF_dir_1d_fresh1 | 276 | 0.530 | 0.054 | 3.6 | 4/4 | 0.466 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (81 of 6305 cell-conditions pass; chance at t>2.5 alone ~39)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_krS_dir_3m_side | 13692 | 0.045 | -0.058 | 0.103 | 4.7 | 4/4 | 0.170 |
| K7 | asia | c4_krF_px_15m_side | 10026 | 0.065 | -0.026 | 0.091 | 4.6 | 4/4 | 0.169 |
| K7 | asia | c4_kr_px_15m_side | 9416 | 0.070 | -0.024 | 0.093 | 4.5 | 4/4 | 0.165 |
| K7 | asia | c4_kr_dir_15m_side | 9304 | 0.070 | -0.023 | 0.094 | 4.4 | 4/4 | 0.171 |
| K7 | asia | c4_krF_dir_15m_side | 10297 | 0.059 | -0.019 | 0.078 | 4.3 | 4/4 | 0.158 |
| K7 | asia | c4_krS_px_15m_side | 8982 | 0.070 | -0.017 | 0.087 | 4.0 | 4/4 | 0.146 |
| P7 | asia | c4_krF_px_15m_side | 18658 | 0.054 | -0.041 | 0.095 | 3.9 | 4/4 | 0.082 |
| K7 | asia | c4_krS_dir_5m_side | 10735 | 0.056 | -0.018 | 0.074 | 3.8 | 3/4 | 0.148 |
| P7 | asia | c4_kr_px_15m_side | 17760 | 0.057 | -0.035 | 0.091 | 3.7 | 4/4 | 0.135 |
| K7 | asia | c4_krS_px_5m_side | 11427 | 0.051 | -0.018 | 0.069 | 3.7 | 4/4 | 0.132 |
| K7 | asia | c4_kr_dir_5m_side | 12426 | 0.047 | -0.024 | 0.071 | 3.7 | 4/4 | 0.138 |
| K7 | asia | c4_krS_px_3m_side | 14710 | 0.038 | -0.075 | 0.113 | 3.6 | 4/4 | 0.123 |
| P7 | asia | c4_krF_px_mtf_ge4 | 18583 | 0.050 | -0.022 | 0.072 | 3.6 | 4/4 | 0.058 |
| P7 | asia | c4_kr_dir_15m_side | 17929 | 0.056 | -0.033 | 0.089 | 3.6 | 4/4 | 0.134 |
| P7 | asia | c4_krF_dir_mtf_ge4 | 18697 | 0.049 | -0.020 | 0.070 | 3.6 | 4/4 | 0.095 |
| K7 | asia | c4_kr_px_5m_side | 12528 | 0.047 | -0.025 | 0.072 | 3.5 | 4/4 | 0.141 |
| K7 | asia | c4_kr_px_mtf_ge4 | 11322 | 0.053 | -0.022 | 0.075 | 3.5 | 3/4 | 0.176 |
| H7 | nypm | c4_lorS_3m_side | 188 | 0.177 | -0.100 | 0.277 | 3.5 | 4/4 | 0.059 |
| A7 | nypm | c4_krS_dir_mtf_all | 1984 | 0.109 | -0.119 | 0.228 | 3.4 | 4/4 | 0.431 |
| A7 | pre | c4_lorF_1m_flip3 | 342 | 0.056 | -0.130 | 0.185 | 3.4 | 4/4 | 0.259 |
| P7 | asia | c4_kr_px_mtf_ge4 | 18066 | 0.052 | -0.021 | 0.073 | 3.3 | 3/4 | 0.102 |
| M7 | pre | c4_krF_dir_1d_fresh1 | 78 | 0.537 | -0.024 | 0.561 | 3.3 | 4/4 | 0.653 |
| P7 | asia | c4_kr_dir_mtf_ge4 | 18101 | 0.051 | -0.019 | 0.070 | 3.3 | 4/4 | 0.119 |
| K7 | asia | c4_krS_dir_15m_side | 8663 | 0.067 | -0.010 | 0.077 | 3.2 | 4/4 | 0.135 |
| P7 | asia | c4_krS_px_15m_side | 16662 | 0.059 | -0.022 | 0.081 | 3.2 | 4/4 | 0.150 |
| K7 | asia | c4_krF_px_mtf_ge4 | 11911 | 0.049 | -0.019 | 0.068 | 3.2 | 4/4 | 0.126 |
| U7 | pre | c4_krF_px_1d_rise | 105 | 0.192 | -0.232 | 0.424 | 3.1 | 3/4 | 0.817 |
| K7 | asia | c4_kr_dir_mtf_ge4 | 11279 | 0.052 | -0.016 | 0.068 | 3.1 | 3/4 | 0.168 |
| K7 | asia | c4_krF_dir_mtf_ge4 | 12401 | 0.046 | -0.020 | 0.066 | 3.1 | 4/4 | 0.084 |
| A7 | nypm | c4_krS_px_mtf_all | 2010 | 0.095 | -0.107 | 0.203 | 3.1 | 4/4 | 0.360 |

## B2-C2 IRL/ERL sweeps (Addendum 5 Step B)

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 294; |t|>2: 0 (chance expectation ~13 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_irl.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_irl_a_pd_ext_against_5 | 387 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_15 | 1215 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_fade_30 | 256 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_30 | 2215 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_fade_60 | 677 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_60 | 3917 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_5 | 4569 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_5 | 15336 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_15 | 14139 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_15 | 39036 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_30 | 29313 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_30 | 61095 | 0.32 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_60 | 55851 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_60 | 87598 | 0.45 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_20 | 5343 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_40 | 15167 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_80 | 34841 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_danger_20 | 161 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/2 | nan | nan |
| c4_irl_a_pd_valid | 191096 | 0.99 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_5 | 138 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_5 | 1295 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_15 | 587 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_15 | 3743 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_30 | 1387 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_30 | 6523 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_irl_a_pd_ext_against_5 | 387 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_15 | 1215 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_fade_30 | 256 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_30 | 2215 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_fade_60 | 677 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_ext_against_60 | 3917 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_5 | 4569 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_5 | 15336 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_15 | 14139 | 0.07 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_15 | 39036 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_30 | 29313 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_30 | 61095 | 0.32 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_fade_60 | 55851 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_int_against_60 | 87598 | 0.45 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_20 | 5343 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_40 | 15167 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_magnet_80 | 34841 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_a_pd_danger_20 | 161 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/2 | nan | nan |
| c4_irl_a_pd_valid | 191096 | 0.99 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_5 | 138 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_5 | 1295 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_15 | 587 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_15 | 3743 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_fade_30 | 1387 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_irl_b_ps_ext_against_30 | 6523 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 32 of 1397 session-condition cells pass (chance-level expectation under independence ~17 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_irl_ge2_ext_against_60 | 1565 | 0.135 | 0.065 | 2.6 | 4/4 | 0.037 |
| london | c4_irl_f_or30_ext_against_5 | 517 | -0.128 | -0.071 | -2.9 | 0/4 | -0.108 |
| london | c4_irl_n_ext_fade_60 | 4139 | -0.092 | -0.068 | -3.1 | 0/4 | -0.110 |
| london | c4_irl_f_or30_ext_against_15 | 1464 | -0.106 | -0.067 | -2.8 | 0/4 | -0.004 |
| london | c4_irl_b_cs60_ext_fade_60 | 5279 | -0.075 | -0.056 | -2.5 | 0/4 | -0.057 |
| nyam | c4_irl_e60_10_ext_fade_30 | 103 | -0.505 | -0.093 | -4.8 | 0/4 | -0.289 |
| nyam | c4_irl_f_or30_ext_fade_15 | 137 | -0.336 | -0.087 | -4.0 | 0/4 | -0.358 |
| nyam | c4_irl_f_or60_ext_fade_60 | 481 | -0.232 | -0.072 | -3.1 | 0/4 | -0.111 |
| nypm | c4_irl_a_pd_int_against_60 | 8660 | -0.145 | -0.106 | -4.8 | 0/4 | -0.155 |
| nypm | c4_irl_n_int_fade_15 | 230 | 0.399 | 0.101 | 4.6 | 4/4 | 0.632 |
| nypm | c4_irl_a_pd_int_against_15 | 3770 | -0.135 | -0.097 | -4.3 | 0/4 | -0.130 |
| nypm | c4_irl_a_pd_int_against_30 | 5826 | -0.129 | -0.095 | -4.3 | 0/4 | -0.115 |
| nypm | c4_irl_a_pd_int_against_5 | 1512 | -0.144 | -0.095 | -4.0 | 0/4 | -0.171 |
| nypm | c4_irl_e60_20_int_against_60 | 10520 | -0.135 | -0.090 | -3.8 | 0/4 | -0.070 |
| pre | c4_irl_n_int_against_60 | 254 | 0.346 | 0.041 | 2.5 | 4/4 | 0.416 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (28 of 6075 cell-conditions pass; chance at t>2.5 alone ~37)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| M7 | nypm | c4_irl_n_int_fade_15 | 74 | 0.439 | 0.009 | 0.430 | 3.9 | 4/4 | 0.791 |
| M7 | nyam | c4_irl_f_or60_int_against_5 | 124 | 0.308 | 0.026 | 0.282 | 3.5 | 4/4 | 0.569 |
| A7 | asia | c4_irl_f_or60_magnet_20 | 187 | 0.340 | 0.088 | 0.252 | 3.5 | 4/4 | 0.562 |
| A7 | nyam | c4_irl_n_int_against_60 | 107 | 0.425 | 0.018 | 0.407 | 3.2 | 3/4 | 0.995 |
| U7 | asia | c4_irl_ge2_ext_against_30 | 67 | 0.373 | 0.048 | 0.325 | 3.2 | 3/3 | 0.373 |
| M7 | nypm | c4_irl_n_int_fade_60 | 230 | 0.291 | 0.004 | 0.286 | 3.0 | 4/4 | 0.632 |
| M7 | nyam | c4_irl_f_or60_int_against_30 | 659 | 0.162 | 0.016 | 0.145 | 2.9 | 4/4 | 0.193 |
| A7 | nypm | c4_irl_n_int_fade_30 | 80 | 0.380 | -0.013 | 0.393 | 2.9 | 4/4 | 0.767 |
| M7 | nypm | c4_irl_n_int_fade_30 | 132 | 0.327 | 0.008 | 0.319 | 2.9 | 4/4 | 0.854 |
| P7 | london | c4_irl_any_int_fade_5 | 902 | 0.111 | 0.014 | 0.097 | 2.9 | 3/4 | 0.080 |
| M7 | nyam | c4_irl_f_or60_int_against_15 | 352 | 0.189 | 0.022 | 0.167 | 2.8 | 4/4 | 0.170 |
| P7 | london | c4_irl_ge2_int_fade_5 | 882 | 0.110 | 0.014 | 0.096 | 2.8 | 3/4 | 0.071 |
| K7 | pre | c4_irl_e60_20_int_against_60 | 878 | 0.054 | -0.094 | 0.148 | 2.8 | 3/4 | 0.056 |
| M7 | close | c4_irl_a_pd_int_fade_15 | 213 | 0.212 | 0.007 | 0.205 | 2.8 | 3/4 | 0.197 |
| P7 | london | c4_irl_b_cs60_int_fade_5 | 748 | 0.112 | 0.015 | 0.097 | 2.7 | 3/4 | 0.064 |
| A7 | asia | c4_irl_f_or30_magnet_20 | 179 | 0.301 | 0.090 | 0.211 | 2.7 | 4/4 | 0.038 |
| M7 | nyam | c4_irl_f_or60_magnet_40 | 744 | 0.133 | 0.018 | 0.115 | 2.7 | 4/4 | 0.330 |
| P7 | nypm | c4_irl_e60_20_int_fade_5 | 238 | 0.143 | -0.019 | 0.161 | 2.7 | 4/4 | 0.236 |
| O7 | nyam | c4_irl_any_ext_against_30 | 118 | 0.557 | 0.133 | 0.424 | 2.6 | 4/4 | 0.768 |
| O7 | nyam | c4_irl_any_ext_against_15 | 99 | 0.604 | 0.142 | 0.462 | 2.6 | 4/4 | 0.535 |
| M7 | nyam | c4_irl_f_or60_magnet_80 | 989 | 0.122 | 0.015 | 0.107 | 2.6 | 4/4 | 0.251 |
| M7 | close | c4_irl_b_ps_int_fade_15 | 185 | 0.211 | 0.008 | 0.203 | 2.6 | 4/4 | 0.244 |
| U7 | asia | c4_irl_e240_20_int_against_15 | 169 | 0.221 | 0.036 | 0.184 | 2.6 | 3/4 | 0.341 |
| A7 | nypm | c4_irl_n_int_fade_60 | 152 | 0.289 | -0.017 | 0.306 | 2.5 | 4/4 | 0.675 |
| P7 | nyam | c4_irl_n_int_against_60 | 160 | 0.274 | 0.007 | 0.267 | 2.5 | 3/4 | 0.246 |
| P7 | close | c4_irl_ge2_ext_against_60 | 499 | 0.143 | -0.014 | 0.157 | 2.5 | 4/4 | 0.100 |
| U7 | asia | c4_irl_ge2_ext_against_60 | 87 | 0.293 | 0.048 | 0.245 | 2.5 | 3/4 | 0.159 |
| U7 | asia | c4_irl_f_or60_magnet_40 | 89 | 0.281 | 0.049 | 0.233 | 2.5 | 4/4 | 0.557 |

## B11 candlestick library

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2234; |t|>2: 0 (chance expectation ~101 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_candle.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_cdl_hammer_1m_fresh5 | 9359 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_fresh1 | 731 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_fresh3 | 5259 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against3 | 10063 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against5 | 16109 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_side | 731 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against | 3829 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh5 | 7876 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh1 | 1399 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh3 | 4405 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against3 | 11735 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against5 | 19228 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_side | 1399 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against | 3378 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh5 | 8542 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh1 | 1454 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh3 | 4743 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against3 | 9444 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against5 | 15285 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_side | 1454 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against | 2735 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh5 | 7486 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh1 | 473 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh3 | 4141 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_against3 | 11336 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_cdl_hammer_1m_fresh5 | 9359 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_fresh1 | 731 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_fresh3 | 5259 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against3 | 10063 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against5 | 16109 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_side | 731 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hammer_1m_against | 3829 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh5 | 7876 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh1 | 1399 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_fresh3 | 4405 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against3 | 11735 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against5 | 19228 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_side | 1399 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_hanging_man_1m_against | 3378 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh5 | 8542 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh1 | 1454 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_fresh3 | 4743 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against3 | 9444 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against5 | 15285 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_side | 1454 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_inv_hammer_1m_against | 2735 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh5 | 7486 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh1 | 473 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_fresh3 | 4141 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_cdl_shooting_star_1m_against3 | 11336 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 135 of 9634 session-condition cells pass (chance-level expectation under independence ~119 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_cdl_morning_star_3m_against3 | 249 | 0.290 | 0.103 | 4.3 | 4/4 | 0.591 |
| close | c4_cdl_harami_cross_1d_fresh5 | 564 | -0.257 | -0.097 | -4.0 | 0/4 | -0.287 |
| close | c4_cdl_mat_hold_15m_fresh5 | 3511 | -0.141 | -0.088 | -3.6 | 0/4 | -0.133 |
| close | c4_cdl_mat_hold_15m_fresh3 | 2460 | -0.142 | -0.082 | -3.3 | 0/4 | -0.127 |
| close | c4_cdl_morning_star_1m_side | 172 | -0.216 | -0.076 | -3.2 | 0/4 | -0.322 |
| close | c4_cdl_morning_star_1m_fresh1 | 172 | -0.216 | -0.076 | -3.2 | 0/4 | -0.322 |
| london | c4_cdl_in_neck_3m_against5 | 110 | 0.430 | 0.101 | 4.8 | 4/4 | 0.614 |
| london | c4_cdl_on_neck_3m_against5 | 107 | 0.419 | 0.097 | 4.6 | 4/4 | 0.614 |
| london | c4_cdl_three_crows_3m_against5 | 248 | -0.314 | -0.089 | -3.9 | 0/4 | -0.366 |
| london | c4_cdl_long_line_15m_against3_atlvl | 312 | 0.228 | 0.086 | 3.6 | 4/4 | 0.578 |
| london | c4_cdl_opening_marubozu_1d_against | 1841 | -0.223 | -0.079 | -3.3 | 0/4 | -0.121 |
| london | c4_cdl_star_doji_3m_fresh3 | 935 | 0.142 | 0.073 | 2.9 | 4/4 | 0.256 |
| nyam | c4_cdl_shooting_star_3m_fresh5 | 691 | -0.218 | -0.102 | -4.1 | 0/4 | -0.056 |
| nyam | c4_cdl_wide_range_trend_1m_fresh3_atlvl | 535 | -0.175 | -0.082 | -3.3 | 0/4 | -0.118 |
| nyam | c4_cdl_hanging_man_15m_against5 | 3253 | 0.146 | 0.076 | 3.0 | 4/4 | 0.124 |
| nyam | c4_cdl_gravestone_3m_against3 | 663 | 0.172 | 0.074 | 3.0 | 4/4 | 0.148 |
| nyam | c4_cdl_long_line_1m_fresh3_atlvl | 944 | -0.128 | -0.070 | -2.8 | 0/4 | -0.207 |
| nyam | c4_cdl_three_inside_1m_fresh5 | 1014 | -0.110 | -0.068 | -2.8 | 0/4 | -0.183 |
| nypm | c4_cdl_harami_cross_1d_against | 322 | 0.525 | 0.107 | 5.3 | 4/4 | 0.522 |
| nypm | c4_cdl_harami_cross_1d_against3 | 815 | 0.322 | 0.081 | 3.7 | 4/4 | 0.419 |
| nypm | c4_cdl_takuri_mtf_n | 125 | -0.359 | -0.079 | -3.8 | 0/4 | -0.364 |
| nypm | c4_cdl_harami_60m_against3_atlvl | 206 | 0.393 | 0.078 | 3.9 | 4/4 | 0.228 |
| nypm | c4_cdl_dragonfly_3m_against3 | 881 | 0.156 | 0.074 | 3.0 | 4/4 | 0.179 |
| nypm | c4_cdl_inside_break_close_15m_against5 | 2983 | -0.132 | -0.074 | -3.0 | 0/4 | -0.080 |
| pre | c4_cdl_belt_hold_1d_against | 135 | -0.612 | -0.080 | -4.7 | 0/3 | -0.955 |
| pre | c4_cdl_three_soldiers_1m_fresh5 | 198 | -0.344 | -0.072 | -3.5 | 0/4 | -0.464 |
| pre | c4_cdl_marubozu_1d_against5 | 127 | -0.371 | -0.068 | -3.5 | 0/4 | -0.174 |
| pre | c4_cdl_mat_hold_3m_fresh5 | 2077 | -0.108 | -0.067 | -2.7 | 0/4 | -0.165 |
| pre | c4_cdl_belt_hold_5m_fresh5 | 652 | 0.222 | 0.066 | 2.9 | 4/4 | 0.392 |
| pre | c4_cdl_tweezer_60m_against3 | 974 | 0.232 | 0.063 | 2.8 | 4/4 | 0.299 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (199 of 32348 cell-conditions pass; chance at t>2.5 alone ~200)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| A7 | nypm | c4_cdl_harami_cross_1d_against3 | 186 | 0.447 | -0.027 | 0.474 | 4.6 | 4/4 | 0.407 |
| A7 | nypm | c4_cdl_harami_cross_1d_against | 86 | 0.516 | -0.017 | 0.532 | 4.4 | 3/3 | 0.450 |
| A7 | nypm | c4_cdl_harami_cross_1d_against5 | 271 | 0.367 | -0.032 | 0.399 | 4.3 | 4/4 | 0.339 |
| A7 | nyam | c4_cdl_three_outside_5m_against3 | 63 | 0.461 | 0.022 | 0.439 | 4.3 | 3/3 | 0.206 |
| M7 | nypm | c4_cdl_mat_hold_3m_fresh3_atlvl | 121 | 0.350 | 0.008 | 0.342 | 4.0 | 4/4 | 0.446 |
| K7 | pre | c4_cdl_tweezer_60m_against3 | 204 | 0.269 | -0.063 | 0.332 | 3.9 | 4/4 | 0.294 |
| O7 | nyam | c4_cdl_wide_range_trend_3m_against5 | 137 | 0.607 | 0.094 | 0.513 | 3.8 | 4/4 | 0.303 |
| P7 | nypm | c4_cdl_harami_cross_1d_against3 | 232 | 0.357 | -0.025 | 0.382 | 3.8 | 4/4 | 0.535 |
| P7 | pre | c4_cdl_dragonfly_1d_fresh5 | 138 | 0.428 | 0.006 | 0.422 | 3.7 | 4/4 | 0.517 |
| K7 | asia | c4_cdl_gap_up_down_60m_fresh5 | 341 | 0.269 | 0.028 | 0.241 | 3.7 | 4/4 | 0.170 |
| K7 | nyam | c4_cdl_gravestone_3m_against3 | 102 | 0.338 | 0.015 | 0.323 | 3.6 | 4/4 | 0.628 |
| M7 | nypm | c4_cdl_harami_60m_against3_atlvl | 62 | 0.455 | 0.010 | 0.444 | 3.6 | 4/4 | 0.215 |
| H7 | pre | c4_cdl_opening_marubozu_15m_fresh5 | 66 | 0.311 | -0.123 | 0.434 | 3.5 | 4/4 | 0.597 |
| A7 | pre | c4_cdl_belt_hold_mtf_n | 101 | 0.270 | -0.111 | 0.381 | 3.5 | 3/4 | 0.596 |
| P7 | nypm | c4_cdl_hanging_man_1d_fresh1 | 116 | 0.475 | -0.021 | 0.496 | 3.5 | 4/4 | 0.221 |
| P7 | nypm | c4_cdl_hanging_man_1d_side | 116 | 0.475 | -0.021 | 0.496 | 3.5 | 4/4 | 0.221 |
| H7 | london | c4_cdl_short_line_1m_rise | 100 | 0.295 | 0.005 | 0.291 | 3.5 | 4/4 | 0.027 |
| P7 | nypm | c4_cdl_morning_star_60m_against5 | 213 | 0.319 | -0.023 | 0.342 | 3.4 | 3/4 | 0.282 |
| M7 | london | c4_cdl_marubozu_15m_fresh3 | 261 | 0.319 | 0.020 | 0.299 | 3.4 | 4/4 | 0.359 |
| A7 | nyam | c4_cdl_marubozu_60m_fresh1 | 82 | 0.530 | 0.018 | 0.512 | 3.4 | 3/3 | 0.035 |
| A7 | nyam | c4_cdl_marubozu_60m_side | 82 | 0.530 | 0.018 | 0.512 | 3.4 | 3/3 | 0.035 |
| P7 | nyam | c4_cdl_3m_nagainst3 | 1956 | 0.075 | -0.010 | 0.085 | 3.4 | 4/4 | 0.071 |
| M7 | nypm | c4_cdl_harami_cross_1d_against | 84 | 0.529 | 0.008 | 0.521 | 3.4 | 3/3 | 0.663 |
| P7 | london | c4_cdl_separating_lines_60m_fresh5 | 1305 | 0.207 | 0.005 | 0.202 | 3.3 | 4/4 | 0.238 |
| A7 | nyam | c4_cdl_three_crows_1d_against5 | 154 | 0.334 | 0.017 | 0.318 | 3.3 | 3/3 | 0.450 |
| K7 | close | c4_cdl_inside_break_3m_fresh5 | 624 | 0.098 | -0.038 | 0.136 | 3.3 | 4/4 | 0.167 |
| K7 | asia | c4_cdl_advance_block_1d_against | 84 | 0.411 | 0.031 | 0.380 | 3.3 | 3/3 | 0.286 |
| A7 | london | c4_cdl_morning_star_1d_against | 80 | 0.482 | 0.033 | 0.449 | 3.3 | 4/4 | 0.862 |
| M7 | london | c4_cdl_marubozu_15m_fresh5 | 396 | 0.260 | 0.019 | 0.241 | 3.3 | 4/4 | 0.213 |
| P7 | london | c4_cdl_hammer_3m_against | 201 | 0.210 | 0.017 | 0.193 | 3.3 | 4/4 | 0.286 |

## B12 bar-level volume at price (footprint)

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 159; |t|>2: 0 (chance expectation ~7 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_fp.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_fp_1m_poc_with | 79608 | 0.41 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_against | 38178 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mid | 75459 | 0.39 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_with_2of3 | 56427 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_with_3of5 | 42946 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig1 | 152870 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig3 | 148920 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig_all3 | 46311 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_with | 10353 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_with3 | 19124 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack2_with | 35031 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_against | 1768 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_against3 | 7188 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_ahead | 23240 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_ahead3 | 65888 | 0.34 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_behind | 29797 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_behind3 | 72220 | 0.37 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with | 149838 | 0.78 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with3 | 144619 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with5 | 142738 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_div_with | 9959 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_div_against | 21625 | 0.11 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_dbot_with | 82158 | 0.43 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_dtop_with | 172264 | 0.89 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_close_delta_with | 104974 | 0.54 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_fp_1m_poc_with | 79608 | 0.41 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_against | 38178 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mid | 75459 | 0.39 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_with_2of3 | 56427 | 0.29 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_with_3of5 | 42946 | 0.22 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig1 | 152870 | 0.79 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig3 | 148920 | 0.77 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_poc_mig_all3 | 46311 | 0.24 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_with | 10353 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_with3 | 19124 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack2_with | 35031 | 0.18 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_against | 1768 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_stack3_against3 | 7188 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_ahead | 23240 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_ahead3 | 65888 | 0.34 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_behind | 29797 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_unf_behind3 | 72220 | 0.37 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with | 149838 | 0.78 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with3 | 144619 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_with5 | 142738 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_div_with | 9959 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_delta_div_against | 21625 | 0.11 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_dbot_with | 82158 | 0.43 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_dtop_with | 172264 | 0.89 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_fp_1m_close_delta_with | 104974 | 0.54 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 4 of 896 session-condition cells pass (chance-level expectation under independence ~11 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_fp_60m_dtop_with | 11179 | -0.114 | -0.067 | -2.7 | 0/4 | -0.147 |
| nyam | c4_fp_15m_delta_div_against | 3377 | 0.086 | 0.061 | 2.7 | 4/4 | 0.131 |
| nypm | c4_fp_mtf_stack3_with_n | 7566 | 0.062 | 0.053 | 2.9 | 4/4 | 0.088 |
| pre | c4_fp_3m_delta_with3 | 6451 | -0.100 | -0.069 | -3.0 | 0/4 | -0.043 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (35 of 4790 cell-conditions pass; chance at t>2.5 alone ~29)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | c4_fp_15m_stack3_against | 253 | 0.339 | 0.085 | 0.254 | 3.8 | 3/3 | 0.226 |
| M7 | nypm | c4_fp_mtf_stack3_with_n | 2122 | 0.088 | -0.021 | 0.109 | 3.6 | 4/4 | 0.104 |
| P7 | nyam | c4_fp_15m_delta_div_against | 1088 | 0.123 | -0.006 | 0.129 | 3.6 | 4/4 | 0.149 |
| P7 | asia | c4_fp_5m_stack3_against | 275 | 0.182 | 0.036 | 0.145 | 3.4 | 4/4 | 0.176 |
| K7 | asia | c4_fp_5m_poc_with_3of5 | 2668 | 0.087 | 0.022 | 0.064 | 3.3 | 3/4 | 0.070 |
| M7 | nyam | c4_fp_3m_poc_mig_all3 | 1235 | 0.109 | 0.013 | 0.097 | 3.2 | 3/4 | 0.174 |
| P7 | pre | c4_fp_60m_poc_against | 548 | 0.208 | -0.016 | 0.223 | 3.1 | 3/4 | 0.261 |
| A7 | nyam | c4_fp_1m_stack3_against | 109 | 0.292 | 0.022 | 0.270 | 3.1 | 4/4 | 0.564 |
| K7 | london | c4_fp_5m_stack3_with3 | 1165 | 0.091 | 0.002 | 0.089 | 3.1 | 4/4 | 0.102 |
| H7 | london | c4_fp_5m_delta_div_with | 116 | 0.259 | 0.004 | 0.255 | 3.1 | 4/4 | 0.338 |
| K7 | close | c4_fp_3m_stack3_against | 83 | 0.277 | -0.018 | 0.294 | 3.0 | 3/4 | 0.636 |
| H7 | nyam | c4_fp_3m_poc_mid | 330 | 0.172 | -0.034 | 0.206 | 3.0 | 3/4 | 0.347 |
| P7 | nypm | c4_fp_1m_poc_against | 1414 | 0.049 | -0.027 | 0.076 | 2.9 | 4/4 | 0.110 |
| H7 | asia | c4_fp_1m_dtop_with | 709 | 0.085 | -0.076 | 0.161 | 2.9 | 4/4 | 0.030 |
| A7 | nyam | c4_fp_5m_poc_against | 563 | 0.140 | 0.010 | 0.130 | 2.9 | 4/4 | 0.147 |
| K7 | asia | c4_fp_15m_stack3_with3 | 2542 | 0.085 | 0.023 | 0.062 | 2.8 | 4/4 | 0.034 |
| K7 | asia | c4_fp_60m_poc_mig3 | 8132 | 0.058 | 0.006 | 0.053 | 2.8 | 4/4 | 0.108 |
| P7 | asia | c4_fp_15m_stack3_with3 | 3890 | 0.083 | 0.028 | 0.054 | 2.8 | 3/4 | 0.100 |
| A7 | london | c4_fp_1m_unf_ahead | 842 | 0.125 | 0.027 | 0.098 | 2.8 | 4/4 | 0.084 |
| K7 | asia | c4_fp_15m_poc_mig3 | 10244 | 0.045 | 0.010 | 0.036 | 2.7 | 4/4 | 0.105 |
| H7 | pre | c4_fp_3m_poc_with | 102 | 0.194 | -0.147 | 0.341 | 2.7 | 3/4 | 0.380 |
| M7 | london | c4_fp_60m_poc_mig3 | 10873 | 0.048 | -0.029 | 0.077 | 2.7 | 4/4 | 0.108 |
| M7 | london | c4_fp_5m_cen_against | 67 | 0.312 | 0.024 | 0.288 | 2.7 | 3/4 | 0.136 |
| K7 | close | c4_fp_60m_unf_ahead | 372 | 0.119 | -0.028 | 0.147 | 2.7 | 4/4 | 0.357 |
| K7 | asia | c4_fp_mtf_poc_mig1_ge4 | 7773 | 0.050 | 0.017 | 0.034 | 2.7 | 4/4 | 0.091 |
| H7 | nyam | c4_fp_1m_delta_with3 | 432 | 0.133 | -0.048 | 0.181 | 2.6 | 3/4 | 0.105 |
| M7 | london | c4_fp_15m_poc_mig_all3 | 3515 | 0.070 | 0.012 | 0.058 | 2.6 | 4/4 | 0.065 |
| A7 | close | c4_fp_5m_poc_against | 275 | 0.093 | -0.046 | 0.139 | 2.6 | 4/4 | 0.097 |
| M7 | close | c4_fp_mtf_poc_mig1_n | 100 | 0.215 | 0.013 | 0.202 | 2.6 | 4/4 | 0.303 |
| K7 | asia | c4_fp_5m_poc_with_2of3 | 3601 | 0.065 | 0.024 | 0.041 | 2.5 | 3/4 | 0.058 |

## B10 geometry and chart patterns

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 916; |t|>2: 0 (chance expectation ~41 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_geom.parquet`.

**top 25 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_tl_state_3m_fresh5 | 37466 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_fresh1 | 12273 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_side | 90960 | 0.47 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_against | 10978 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_hold3 | 72599 | 0.38 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_fresh5 | 37466 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_fresh1 | 12273 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_side | 12273 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_against | 4485 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_fresh5 | 28406 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_fresh1 | 9953 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_side | 9953 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_against | 6096 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_hold3 | 1124 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_touch3_3m_hi | 33476 | 0.17 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_touch3_3m_rise | 17956 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_hi | 41402 | 0.69 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_hi_z1 | 31873 | 0.53 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_lo_z1 | 5648 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_rise | 31210 | 0.52 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_side | 52249 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_rise | 40456 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_fresh5 | 19661 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chan_pos_3m_side | 52811 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chan_pos_3m_rise | 57392 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_tl_state_3m_fresh5 | 37466 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_fresh1 | 12273 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_side | 90960 | 0.47 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_against | 10978 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_state_3m_hold3 | 72599 | 0.38 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_fresh5 | 37466 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_fresh1 | 12273 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_side | 12273 | 0.06 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_break_3m_against | 4485 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_fresh5 | 28406 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_fresh1 | 9953 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_side | 9953 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_against | 6096 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_retest_3m_hold3 | 1124 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_touch3_3m_hi | 33476 | 0.17 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_touch3_3m_rise | 17956 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_hi | 41402 | 0.69 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_hi_z1 | 31873 | 0.53 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_lo_z1 | 5648 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_dist_up_3m_rise | 31210 | 0.52 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_side | 52249 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_rise | 40456 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_tl_slope_up_3m_fresh5 | 19661 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chan_pos_3m_side | 52811 | 0.27 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_chan_pos_3m_rise | 57392 | 0.30 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 57 of 4261 session-condition cells pass (chance-level expectation under independence ~52 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_tl_retestS_5m_fresh1 | 541 | 0.149 | 0.071 | 2.8 | 4/4 | 0.222 |
| close | c4_tl_retestS_5m_side | 541 | 0.149 | 0.071 | 2.8 | 4/4 | 0.222 |
| close | c4_tri_sym_onS_5m_hi | 516 | -0.172 | -0.068 | -2.8 | 0/4 | -0.113 |
| close | c4_lmw_tri_15m_hold3 | 471 | 0.318 | 0.065 | 3.2 | 4/4 | 0.494 |
| close | c4_tri_sym_15m_fresh1 | 210 | 0.239 | 0.052 | 2.5 | 4/4 | 0.053 |
| close | c4_tri_sym_15m_side | 210 | 0.239 | 0.052 | 2.5 | 4/4 | 0.053 |
| london | c4_pennant_60m_fresh5 | 942 | -0.310 | -0.088 | -3.9 | 0/4 | -0.338 |
| london | c4_chan_posS_15m_eenter | 3914 | -0.143 | -0.087 | -3.6 | 0/4 | -0.193 |
| london | c4_wedge_rising_onS_15m_rise | 798 | -0.146 | -0.081 | -3.3 | 0/4 | -0.153 |
| london | c4_pitchforkS_60m_fresh5 | 4801 | 0.147 | 0.077 | 3.1 | 4/4 | 0.239 |
| london | c4_pnf_15m_side | 44550 | 0.085 | 0.070 | 3.6 | 4/4 | 0.010 |
| london | c4_pnf_15m_against | 13223 | -0.085 | -0.070 | -3.6 | 0/4 | -0.010 |
| nyam | c4_wedge_rising_onS_60m_rise | 579 | 0.266 | 0.075 | 3.3 | 4/4 | 0.166 |
| nyam | c4_tri_sym_60m_fresh5 | 965 | -0.214 | -0.067 | -2.9 | 0/4 | -0.373 |
| nyam | c4_lmw_rect_15m_fresh5 | 100 | -0.541 | -0.065 | -4.0 | 0/4 | -0.148 |
| nyam | c4_chan_pos_3m_ewith | 2676 | 0.086 | 0.062 | 2.7 | 4/4 | 0.161 |
| nyam | c4_chan_pos_5m_ewith | 2628 | 0.099 | 0.061 | 2.5 | 4/4 | 0.044 |
| nyam | c4_tri_symS_15m_fresh5 | 517 | -0.293 | -0.061 | -3.0 | 0/4 | -0.443 |
| nypm | c4_kagi_60m_hold3 | 13265 | 0.143 | 0.089 | 3.7 | 4/4 | 0.228 |
| nypm | c4_tl_slope_upS_60m_side | 3868 | 0.179 | 0.082 | 3.3 | 4/4 | 0.133 |
| nypm | c4_tl_stateS_60m_hold3 | 5210 | 0.144 | 0.080 | 3.2 | 4/4 | 0.249 |
| nypm | c4_fib_clusterS_60m_hi_z1 | 2022 | -0.183 | -0.072 | -2.9 | 0/4 | -0.295 |
| nypm | c4_tl_stateS_60m_side | 6242 | 0.128 | 0.071 | 2.8 | 4/4 | 0.182 |
| nypm | c4_fib_cluster_dirS_15m_against | 3989 | -0.119 | -0.070 | -2.8 | 0/4 | -0.221 |
| pre | c4_chan_posS_60m_eagainst | 926 | 0.305 | 0.082 | 3.7 | 4/4 | 0.478 |
| pre | c4_tl_retest_60m_against | 424 | 0.381 | 0.069 | 3.6 | 4/4 | 0.522 |
| pre | c4_fib_cluster_dirS_60m_against | 1073 | 0.205 | 0.063 | 2.7 | 4/4 | 0.113 |
| pre | c4_tl_dist_upS_60m_hi_z1 | 1629 | -0.219 | -0.056 | -2.6 | 0/4 | -0.118 |
| pre | c4_fib_ext_up_3m_rise | 4471 | 0.069 | 0.054 | 2.7 | 4/4 | 0.139 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (139 of 18200 cell-conditions pass; chance at t>2.5 alone ~112)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_flag_5m_hold3 | 1245 | 0.141 | 0.024 | 0.116 | 5.2 | 4/4 | 0.027 |
| K7 | asia | c4_pnf_60m_fresh1 | 933 | 0.205 | 0.022 | 0.182 | 4.8 | 4/4 | 0.097 |
| A7 | nypm | c4_kagi_60m_hold3 | 2490 | 0.100 | -0.173 | 0.273 | 4.6 | 4/4 | 0.403 |
| K7 | asia | c4_pnf_5m_fresh5 | 3751 | 0.085 | 0.017 | 0.068 | 4.3 | 3/4 | 0.041 |
| M7 | pre | c4_tl_retest_60m_against | 119 | 0.503 | -0.026 | 0.529 | 4.2 | 3/4 | 0.994 |
| K7 | asia | c4_kagi_3m_hold3 | 9823 | 0.055 | -0.005 | 0.060 | 4.1 | 4/4 | 0.088 |
| K7 | asia | c4_pnf_15m_fresh5 | 2863 | 0.117 | 0.015 | 0.102 | 4.1 | 3/4 | 0.169 |
| M7 | pre | c4_chan_posS_60m_eagainst | 278 | 0.339 | -0.043 | 0.382 | 4.0 | 4/4 | 0.521 |
| P7 | nyam | c4_wedge_rising_onS_60m_rise | 186 | 0.346 | 0.004 | 0.342 | 3.8 | 4/4 | 0.424 |
| A7 | nypm | c4_tl_slope_upS_60m_side | 840 | 0.208 | -0.061 | 0.269 | 3.8 | 4/4 | 0.336 |
| K7 | nypm | c4_chan_posS_15m_eenter | 224 | 0.232 | -0.018 | 0.250 | 3.8 | 4/4 | 0.046 |
| K7 | pre | c4_tl_retestS_60m_against | 79 | 0.385 | -0.046 | 0.430 | 3.8 | 4/4 | 0.500 |
| A7 | nypm | c4_fib_clusterS_15m_lo_z1 | 3463 | 0.029 | -0.206 | 0.235 | 3.7 | 4/4 | 0.355 |
| P7 | nypm | c4_tl_slope_upS_60m_side | 1174 | 0.172 | -0.045 | 0.217 | 3.6 | 4/4 | 0.257 |
| K7 | asia | c4_threeline_5m_hold3 | 8723 | 0.061 | -0.002 | 0.063 | 3.6 | 4/4 | 0.109 |
| A7 | nypm | c4_kagi_60m_side | 2986 | 0.055 | -0.174 | 0.229 | 3.6 | 4/4 | 0.314 |
| K7 | asia | c4_pnf_15m_fresh1 | 1119 | 0.138 | 0.025 | 0.112 | 3.5 | 3/4 | 0.132 |
| M7 | nypm | c4_kagi_60m_hold3 | 3559 | 0.087 | -0.070 | 0.157 | 3.5 | 4/4 | 0.325 |
| A7 | london | c4_pnf_15m_hold3 | 5940 | 0.067 | -0.061 | 0.128 | 3.5 | 4/4 | 0.038 |
| M7 | london | c4_chan_pos_60m_eenter | 1084 | 0.199 | 0.012 | 0.187 | 3.4 | 4/4 | 0.226 |
| M7 | london | c4_chan_pos_60m_ewith | 1594 | 0.163 | 0.009 | 0.154 | 3.3 | 4/4 | 0.123 |
| P7 | nypm | c4_chan_pos_15m_ewith | 888 | 0.159 | -0.035 | 0.195 | 3.3 | 4/4 | 0.160 |
| P7 | nypm | c4_pitchfork_5m_fresh1 | 165 | 0.245 | -0.019 | 0.264 | 3.3 | 4/4 | 0.099 |
| M7 | close | c4_fib_cluster_dir_3m_side | 311 | 0.167 | 0.005 | 0.163 | 3.3 | 3/4 | 0.279 |
| M7 | london | c4_chan_posS_60m_eenter | 807 | 0.223 | 0.014 | 0.209 | 3.3 | 3/4 | 0.192 |
| K7 | nyam | c4_fib_ext_dn_3m_rise | 2397 | 0.070 | -0.022 | 0.092 | 3.3 | 4/4 | 0.012 |
| P7 | nypm | c4_tl_stateS_60m_hold3 | 1591 | 0.122 | -0.047 | 0.169 | 3.2 | 4/4 | 0.309 |
| K7 | asia | c4_kagi_3m_side | 11947 | 0.046 | -0.011 | 0.057 | 3.2 | 4/4 | 0.107 |
| U7 | nyam | c4_fib_cluster_15m_rise | 213 | 0.232 | -0.012 | 0.244 | 3.2 | 4/4 | 0.238 |
| K7 | london | c4_pitchforkS_60m_fresh5 | 959 | 0.144 | -0.000 | 0.145 | 3.2 | 4/4 | 0.261 |

## B4 alternate bars: ha1

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2218; |t|>2: 0 (chance expectation ~100 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha1.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha1_side | 176584 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_sig | 131974 | 0.68 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_rise | 146502 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_fresh5 | 85855 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_ewith_z1 | 19477 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_eleave_z1 | 277 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_eenter_z1 | 9431 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_ewith_z2 | 37933 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_eleave_z2 | 809 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_eenter_z2 | 17022 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha1_side | 176584 | 0.91 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_sig | 131974 | 0.68 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_rise | 146502 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_fresh5 | 85855 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_ewith_z1 | 19477 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_eleave_z1 | 277 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_eenter_z1 | 9431 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_ewith_z2 | 37933 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_eleave_z2 | 809 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha1_eenter_z2 | 17022 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 210 of 12785 session-condition cells pass (chance-level expectation under independence ~158 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_tsiS_ha1_eenter | 351 | 0.170 | 0.092 | 3.7 | 4/4 | 0.084 |
| close | c4_kerF_dir_ha1_eagainst | 945 | 0.104 | 0.075 | 3.3 | 4/4 | 0.110 |
| close | c4_ichiF_score_ha1_eagainst | 178 | 0.188 | 0.072 | 3.0 | 4/4 | 0.633 |
| close | c4_pdS_ha1_fresh5 | 1145 | -0.113 | -0.072 | -3.0 | 0/4 | -0.106 |
| close | c4_sqzmF_bright_ha1_against | 1659 | 0.086 | 0.071 | 3.8 | 4/4 | 0.084 |
| close | c4_w1_cmo9_ha1_eagainst | 322 | 0.137 | 0.069 | 2.8 | 4/4 | 0.188 |
| london | c4_sfpF_ha1_fresh1 | 476 | -0.123 | -0.075 | -3.1 | 0/4 | -0.172 |
| london | c4_sfpF_ha1_side | 476 | -0.123 | -0.075 | -3.1 | 0/4 | -0.172 |
| london | c4_w1_kama100_px_ha1_divwith | 1798 | -0.101 | -0.073 | -3.3 | 0/4 | -0.238 |
| london | c4_w1_ema100_px_ha1_divwith | 1581 | -0.103 | -0.072 | -3.1 | 0/4 | -0.242 |
| london | c4_w1_sma100_px_ha1_divwith | 1731 | -0.100 | -0.071 | -3.2 | 0/4 | -0.162 |
| london | c4_w1_ema200_px_ha1_divwith | 1612 | -0.102 | -0.071 | -3.1 | 0/4 | -0.198 |
| nyam | c4_sfpS_ha1_fresh5 | 1189 | -0.145 | -0.092 | -3.8 | 0/4 | -0.068 |
| nyam | c4_smiS_ha1_eagainst | 289 | -0.172 | -0.077 | -3.1 | 0/4 | -0.323 |
| nyam | c4_alli_spread_ha1_side | 20816 | 0.091 | 0.074 | 3.8 | 4/4 | 0.141 |
| nyam | c4_w1_vwma_stack_fast_ha1_against | 1086 | -0.111 | -0.073 | -3.1 | 0/4 | -0.002 |
| nyam | c4_w1_ao_ha1_side | 21973 | 0.094 | 0.073 | 3.5 | 4/4 | 0.165 |
| nyam | c4_hiloS_ha1_fresh1 | 1559 | -0.092 | -0.070 | -3.3 | 0/4 | -0.137 |
| nypm | c4_sqzmF_on_ha1_rise | 829 | -0.090 | -0.065 | -2.9 | 0/4 | -0.105 |
| nypm | c4_w1_kama34_px_ha1_side | 23427 | -0.087 | -0.064 | -2.9 | 0/4 | -0.058 |
| nypm | c4_ob_dsup_ha1_hi | 4162 | 0.091 | 0.063 | 2.8 | 4/4 | 0.017 |
| nypm | c4_alligator_ha1_fresh1 | 932 | -0.078 | -0.057 | -2.6 | 0/4 | -0.136 |
| nypm | c4_sqzmF_bright_ha1_against | 2778 | 0.053 | 0.045 | 2.5 | 4/4 | 0.131 |
| nypm | c4_w1_kama_stack_fast_ha1_side | 14718 | -0.051 | -0.044 | -2.6 | 0/4 | -0.097 |
| pre | c4_sebS_ha1_eleave | 412 | 0.206 | 0.071 | 3.0 | 4/4 | 0.276 |
| pre | c4_elder_impulse_ha1_against | 662 | 0.117 | 0.066 | 2.7 | 4/4 | 0.074 |
| pre | c4_sdS_in_ha1_fresh5 | 708 | 0.131 | 0.066 | 2.6 | 4/4 | 0.074 |
| pre | c4_smiS_ha1_sig | 5515 | -0.076 | -0.058 | -2.8 | 0/4 | -0.042 |
| pre | c4_tsiF_ha1_ewith | 4688 | -0.075 | -0.058 | -2.7 | 0/4 | -0.052 |
| pre | c4_w1_obv_ha1_fresh5 | 3254 | 0.076 | 0.057 | 2.7 | 4/4 | 0.082 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (273 of 59909 cell-conditions pass; chance at t>2.5 alone ~371)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_ema_stack_slow_ha1_side | 8173 | 0.076 | -0.015 | 0.091 | 5.0 | 4/4 | 0.149 |
| K7 | asia | c4_w1_ema_stack_slow_ha1_hold3 | 7874 | 0.076 | -0.011 | 0.087 | 5.0 | 4/4 | 0.135 |
| K7 | nyam | c4_sdF_dsup_ha1_hi | 269 | 0.273 | 0.010 | 0.263 | 4.9 | 4/4 | 0.137 |
| K7 | asia | c4_turt55_ha1_hold3 | 7216 | 0.070 | 0.002 | 0.068 | 4.7 | 4/4 | 0.066 |
| K7 | asia | c4_w1_sma200_px_ha1_side | 12512 | 0.050 | -0.036 | 0.086 | 4.2 | 4/4 | 0.168 |
| K7 | asia | c4_obF_cnt_ha1_side | 10120 | 0.061 | -0.019 | 0.080 | 4.1 | 4/4 | 0.177 |
| K7 | asia | c4_w1_sma_stack_slow_ha1_side | 6449 | 0.074 | 0.005 | 0.069 | 4.1 | 4/4 | 0.143 |
| K7 | asia | c4_sdF_cnt_ha1_side | 10174 | 0.061 | -0.019 | 0.080 | 4.0 | 4/4 | 0.176 |
| K7 | asia | c4_w1_ema200_px_ha1_side | 12841 | 0.047 | -0.035 | 0.082 | 3.9 | 4/4 | 0.128 |
| K7 | asia | c4_fvgS_dsup_ha1_rise | 856 | 0.110 | -0.064 | 0.175 | 3.8 | 4/4 | 0.098 |
| K7 | asia | c4_ichiF_thick_ha1_hi | 4032 | 0.070 | 0.021 | 0.050 | 3.8 | 3/4 | 0.158 |
| K7 | nyam | c4_sd_dsup_ha1_hi | 669 | 0.142 | 0.002 | 0.141 | 3.8 | 4/4 | 0.210 |
| K7 | asia | c4_tsiS_ha1_ewith | 2217 | 0.096 | 0.023 | 0.073 | 3.8 | 4/4 | 0.067 |
| K7 | asia | c4_w1_sma_stack_slow_ha1_hold3 | 6244 | 0.071 | 0.008 | 0.064 | 3.7 | 4/4 | 0.134 |
| K7 | asia | c4_ob_cnt_ha1_side | 10029 | 0.058 | -0.011 | 0.069 | 3.7 | 4/4 | 0.159 |
| K7 | asia | c4_turt55_ha1_side | 8968 | 0.056 | 0.002 | 0.054 | 3.6 | 4/4 | 0.072 |
| H7 | close | c4_pd_ha1_eagainst | 238 | 0.098 | -0.275 | 0.373 | 3.6 | 4/4 | 0.446 |
| K7 | asia | c4_lrc_slope_ha1_side | 9918 | 0.053 | -0.001 | 0.054 | 3.6 | 3/4 | 0.136 |
| A7 | london | c4_chochS_ha1_fresh5 | 282 | 0.204 | 0.032 | 0.173 | 3.6 | 4/4 | 0.236 |
| K7 | asia | c4_obS_cnt_ha1_side | 9830 | 0.059 | -0.012 | 0.071 | 3.6 | 4/4 | 0.154 |
| M7 | london | c4_w1_vwma200_px_ha1_side | 15520 | 0.027 | -0.386 | 0.413 | 3.6 | 4/4 | 0.354 |
| K7 | asia | c4_w1_vwma_stack_slow_ha1_hold3 | 6176 | 0.071 | 0.009 | 0.062 | 3.6 | 4/4 | 0.123 |
| K7 | asia | c4_fvg_dres_ha1_hi | 3161 | 0.077 | -0.004 | 0.081 | 3.6 | 4/4 | 0.090 |
| K7 | asia | c4_stPS_ha1_hold3 | 10175 | 0.051 | -0.001 | 0.053 | 3.6 | 3/4 | 0.055 |
| K7 | asia | c4_w1_vwma_stack_slow_ha1_side | 6467 | 0.069 | 0.008 | 0.062 | 3.5 | 4/4 | 0.124 |
| K7 | asia | c4_kstS_ha1_side | 11100 | 0.048 | -0.004 | 0.052 | 3.5 | 3/4 | 0.121 |
| K7 | asia | c4_stPS_ha1_side | 11648 | 0.047 | -0.009 | 0.056 | 3.5 | 3/4 | 0.087 |
| P7 | london | c4_w1_sqz_hist_ha1_fresh5 | 2862 | 0.067 | 0.010 | 0.057 | 3.5 | 4/4 | 0.078 |
| M7 | london | c4_w1_willr21_ha1_eleave | 672 | 0.141 | 0.020 | 0.121 | 3.5 | 4/4 | 0.034 |
| M7 | nyam | c4_w1_demarker14_ha1_eagainst | 73 | 0.366 | 0.028 | 0.338 | 3.5 | 4/4 | 0.659 |

## B4 alternate bars: ha15

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2267; |t|>2: 0 (chance expectation ~103 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha15.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha15_side | 135759 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_sig | 143181 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_rise | 147112 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_fresh5 | 80624 | 0.42 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_ewith_z1 | 23036 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_eagainst_z1 | 3036 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_eleave_z1 | 4839 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_eenter_z1 | 8848 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_ewith_z2 | 38549 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_eagainst_z2 | 5915 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha15_side | 135759 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_sig | 143181 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_rise | 147112 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_fresh5 | 80624 | 0.42 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_ewith_z1 | 23036 | 0.12 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_eagainst_z1 | 3036 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_eleave_z1 | 4839 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_eenter_z1 | 8848 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_ewith_z2 | 38549 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha15_eagainst_z2 | 5915 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 103 of 13212 session-condition cells pass (chance-level expectation under independence ~163 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_w1_demarker7_ha15_eenter | 3233 | 0.133 | 0.090 | 3.9 | 4/4 | 0.146 |
| close | c4_sqzmF_on_ha15_hi | 10155 | 0.120 | 0.074 | 3.1 | 4/4 | 0.017 |
| close | c4_w1_mfi7_ha15_ewith | 4162 | -0.110 | -0.070 | -2.9 | 0/4 | -0.042 |
| close | c4_w1_mfi14_ha15_ewith | 1819 | -0.149 | -0.066 | -2.7 | 0/4 | -0.266 |
| close | c4_sdF_dres_ha15_hi | 974 | -0.187 | -0.065 | -2.7 | 0/4 | -0.126 |
| close | c4_w1_linreg_chan50_ha15_fresh5 | 4189 | 0.097 | 0.064 | 2.7 | 4/4 | 0.108 |
| london | c4_nwe_ha15_fresh5 | 375 | 0.359 | 0.077 | 3.8 | 4/4 | 0.143 |
| london | c4_fvg_in_ha15_fresh5 | 433 | -0.348 | -0.074 | -3.6 | 0/4 | -0.074 |
| london | c4_chand_ha15_fresh1 | 1881 | -0.109 | -0.073 | -3.1 | 0/4 | -0.266 |
| london | c4_zlema_px_ha15_nodiv | 45422 | -0.094 | -0.070 | -3.2 | 0/4 | -0.066 |
| london | c4_ichiS_score_ha15_eleave | 3087 | -0.116 | -0.070 | -2.8 | 0/4 | -0.190 |
| london | c4_nweS_ha15_eleave | 148 | 0.427 | 0.067 | 3.7 | 4/4 | 0.127 |
| nyam | c4_fvg_cnt_ha15_side | 9247 | 0.157 | 0.110 | 4.8 | 4/4 | 0.212 |
| nyam | c4_w1_pat_pin_ha15_fresh5 | 1750 | -0.171 | -0.085 | -3.4 | 0/4 | -0.123 |
| nyam | c4_brkF_near_ha15_hold3 | 2876 | -0.119 | -0.075 | -3.1 | 0/4 | -0.162 |
| nyam | c4_sdflipS_in_ha15_side | 1498 | -0.136 | -0.072 | -2.9 | 0/4 | -0.132 |
| nyam | c4_fvg_dsup_ha15_hi | 6388 | 0.128 | 0.071 | 2.9 | 4/4 | 0.113 |
| nyam | c4_fvgF_cnt_ha15_side | 10936 | 0.095 | 0.067 | 3.0 | 4/4 | 0.081 |
| nypm | c4_w1_aroon50_ha15_ewith | 5213 | 0.165 | 0.090 | 3.6 | 4/4 | 0.175 |
| nypm | c4_fvg_cnt_ha15_side | 9867 | 0.152 | 0.089 | 3.6 | 4/4 | 0.356 |
| nypm | c4_w1_sma200_px_ha15_fresh5 | 2548 | -0.183 | -0.087 | -3.5 | 0/4 | -0.240 |
| nypm | c4_w1_trix30_ha15_side | 14870 | 0.129 | 0.083 | 3.5 | 4/4 | 0.195 |
| nypm | c4_sdflipF_in_ha15_against | 8203 | -0.121 | -0.082 | -3.5 | 0/4 | -0.141 |
| nypm | c4_lrc_slope_ha15_side | 14540 | 0.118 | 0.078 | 3.3 | 4/4 | 0.237 |
| pre | c4_sdS_cnt_ha15_rise | 1163 | -0.181 | -0.083 | -3.3 | 0/4 | -0.406 |
| pre | c4_smie_ha15_eenter | 1303 | -0.218 | -0.072 | -3.1 | 0/4 | -0.663 |
| pre | c4_obS_cnt_ha15_rise | 1000 | -0.180 | -0.071 | -2.9 | 0/4 | -0.168 |
| pre | c4_w1_rsi2_ha15_eleave | 1494 | -0.143 | -0.064 | -2.6 | 0/4 | -0.208 |
| pre | c4_w1_cci20_ha15_ewith_z2 | 1164 | -0.191 | -0.063 | -2.7 | 0/4 | -0.616 |
| pre | c4_w1_demarker7_ha15_fresh5 | 3807 | -0.126 | -0.063 | -2.5 | 0/4 | -0.149 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (868 of 67757 cell-conditions pass; chance at t>2.5 alone ~420)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_mfi7_ha15_side | 8926 | 0.065 | -0.010 | 0.075 | 5.1 | 4/4 | 0.144 |
| A7 | nyam | c4_fvg_cnt_ha15_side | 1596 | 0.195 | -0.095 | 0.290 | 5.0 | 4/4 | 0.365 |
| K7 | asia | c4_chandF_ha15_side | 8644 | 0.075 | -0.020 | 0.095 | 4.8 | 4/4 | 0.151 |
| K7 | asia | c4_w1_keltner10_pos_ha15_ewith | 756 | 0.217 | 0.024 | 0.192 | 4.8 | 4/4 | 0.217 |
| K7 | asia | c4_w1_keltner20_pos_ha15_ewith | 859 | 0.220 | 0.023 | 0.197 | 4.8 | 4/4 | 0.231 |
| K7 | asia | c4_w1_mfi14_ha15_side | 8465 | 0.074 | -0.016 | 0.089 | 4.8 | 4/4 | 0.197 |
| K7 | asia | c4_w1_willr21_ha15_ewith | 4508 | 0.096 | 0.008 | 0.088 | 4.7 | 4/4 | 0.113 |
| K7 | asia | c4_w1_keltner10_pos_ha15_side | 10056 | 0.062 | -0.019 | 0.081 | 4.7 | 4/4 | 0.161 |
| A7 | nypm | c4_w1_trix30_ha15_side | 2753 | 0.080 | -0.185 | 0.265 | 4.7 | 4/4 | 0.410 |
| K7 | asia | c4_ichiF_score_ha15_side | 8650 | 0.071 | -0.015 | 0.086 | 4.7 | 4/4 | 0.173 |
| K7 | asia | c4_krF_px_ha15_side | 9382 | 0.069 | -0.023 | 0.092 | 4.6 | 4/4 | 0.151 |
| K7 | asia | c4_w1_di7_ha15_side | 9413 | 0.066 | -0.018 | 0.085 | 4.6 | 4/4 | 0.160 |
| K7 | asia | c4_qqeF_ha15_side | 9134 | 0.069 | -0.018 | 0.087 | 4.6 | 4/4 | 0.172 |
| K7 | asia | c4_w1_vortex14_ha15_side | 8829 | 0.071 | -0.017 | 0.088 | 4.6 | 4/4 | 0.165 |
| K7 | asia | c4_krF_dir_ha15_side | 9543 | 0.066 | -0.020 | 0.086 | 4.6 | 4/4 | 0.166 |
| K7 | asia | c4_mcg_px_ha15_side | 9553 | 0.067 | -0.021 | 0.088 | 4.6 | 4/4 | 0.170 |
| K7 | asia | c4_mcg_slope_ha15_side | 9553 | 0.067 | -0.021 | 0.088 | 4.6 | 4/4 | 0.170 |
| K7 | asia | c4_rfiltS_ha15_side | 9075 | 0.074 | -0.024 | 0.098 | 4.6 | 4/4 | 0.097 |
| K7 | asia | c4_tsiF_ha15_side | 8641 | 0.072 | -0.016 | 0.089 | 4.6 | 4/4 | 0.170 |
| K7 | asia | c4_nweS_ha15_side | 8794 | 0.070 | -0.025 | 0.095 | 4.5 | 4/4 | 0.186 |
| K7 | asia | c4_smi_ha15_ewith | 4926 | 0.090 | 0.007 | 0.083 | 4.5 | 4/4 | 0.070 |
| K7 | asia | c4_w1_keltner20_pos_ha15_side | 9287 | 0.069 | -0.020 | 0.088 | 4.5 | 4/4 | 0.167 |
| K7 | asia | c4_mcgS_slope_ha15_side | 8860 | 0.075 | -0.023 | 0.099 | 4.5 | 4/4 | 0.197 |
| K7 | asia | c4_mcgS_px_ha15_side | 8860 | 0.075 | -0.023 | 0.099 | 4.5 | 4/4 | 0.197 |
| K7 | asia | c4_smieF_ha15_side | 9346 | 0.065 | -0.015 | 0.080 | 4.5 | 4/4 | 0.141 |
| P7 | nyam | c4_fvg_cnt_ha15_side | 2813 | 0.122 | -0.054 | 0.176 | 4.5 | 4/4 | 0.279 |
| K7 | asia | c4_smiF_ha15_ewith | 3560 | 0.103 | 0.013 | 0.091 | 4.5 | 4/4 | 0.050 |
| P7 | london | c4_nweS_ha15_fresh5 | 98 | 0.533 | 0.012 | 0.521 | 4.5 | 4/4 | 0.240 |
| K7 | asia | c4_w1_rsi7_ha15_ewith | 3952 | 0.100 | 0.010 | 0.090 | 4.5 | 4/4 | 0.122 |
| K7 | asia | c4_rsima7_ha15_ewith | 3953 | 0.100 | 0.011 | 0.090 | 4.5 | 4/4 | 0.122 |

## B4 alternate bars: ha3

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2229; |t|>2: 0 (chance expectation ~101 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha3.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha3_side | 168051 | 0.87 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_sig | 135629 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_rise | 137452 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_fresh5 | 83307 | 0.43 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_ewith_z1 | 25545 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eleave_z1 | 972 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eenter_z1 | 8695 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_ewith_z2 | 50149 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eagainst_z2 | 299 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eleave_z2 | 2157 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha3_side | 168051 | 0.87 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_sig | 135629 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_rise | 137452 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_fresh5 | 83307 | 0.43 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_ewith_z1 | 25545 | 0.13 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eleave_z1 | 972 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eenter_z1 | 8695 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_ewith_z2 | 50149 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eagainst_z2 | 299 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha3_eleave_z2 | 2157 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 116 of 12865 session-condition cells pass (chance-level expectation under independence ~159 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_w1_vwma100_px_ha3_divwith | 899 | 0.197 | 0.090 | 3.6 | 4/4 | 0.380 |
| close | c4_w1_kama8_px_ha3_divwith | 1471 | 0.155 | 0.082 | 3.3 | 4/4 | 0.288 |
| close | c4_w1_sma100_px_ha3_divwith | 753 | 0.204 | 0.081 | 3.3 | 4/4 | 0.352 |
| close | c4_qqeF_ha3_divwith | 856 | 0.191 | 0.081 | 3.3 | 4/4 | 0.139 |
| close | c4_w1_kama100_px_ha3_divwith | 609 | 0.204 | 0.080 | 3.3 | 4/4 | 0.283 |
| close | c4_w1_boll10_walk_ha3_divwith | 977 | 0.170 | 0.077 | 3.1 | 4/4 | 0.308 |
| london | c4_crsi_ha3_eagainst_z2 | 1399 | 0.089 | 0.070 | 3.4 | 4/4 | 0.050 |
| london | c4_w1_willr7_ha3_eagainst | 357 | 0.141 | 0.068 | 2.7 | 4/4 | 0.047 |
| london | c4_w1_rsi2_ha3_eagainst | 735 | 0.100 | 0.066 | 2.8 | 4/4 | 0.206 |
| london | c4_kerF_dir_ha3_eagainst | 2074 | 0.083 | 0.065 | 3.2 | 4/4 | 0.094 |
| london | c4_rfiltS_dir_ha3_hold3 | 45358 | 0.075 | 0.061 | 3.2 | 4/4 | 0.003 |
| london | c4_w1_ichi_fast_cloud_ha3_divwith | 427 | 0.213 | 0.057 | 2.6 | 4/4 | 0.194 |
| nyam | c4_w1_mfi21_ha3_ewith | 2353 | 0.133 | 0.083 | 3.4 | 4/4 | 0.146 |
| nyam | c4_w1_obv_ha3_side | 22126 | 0.100 | 0.074 | 3.3 | 4/4 | 0.028 |
| nyam | c4_w1_mfi14_ha3_ewith | 4028 | 0.094 | 0.070 | 3.2 | 4/4 | 0.136 |
| nyam | c4_w1_aroon50_ha3_divwith | 2086 | 0.124 | 0.070 | 2.8 | 4/4 | 0.137 |
| nyam | c4_ote_wideF_ha3_side | 900 | -0.108 | -0.067 | -2.7 | 0/4 | -0.094 |
| nyam | c4_sqzmF_bright_ha3_against | 1379 | -0.097 | -0.065 | -2.8 | 0/4 | -0.186 |
| nypm | c4_obF_cnt_ha3_fresh5 | 1095 | -0.126 | -0.069 | -2.8 | 0/4 | -0.148 |
| nypm | c4_w1_fisher5_ha3_fresh5 | 7931 | -0.050 | -0.044 | -2.7 | 0/4 | -0.058 |
| nypm | c4_rvi_ha3_fresh5 | 9076 | -0.043 | -0.039 | -2.7 | 0/4 | -0.028 |
| pre | c4_ote_wide_ha3_side | 242 | 0.241 | 0.075 | 3.3 | 4/4 | 0.515 |
| pre | c4_rsima21_ha3_eenter | 653 | -0.152 | -0.072 | -2.9 | 0/4 | -0.140 |
| pre | c4_w1_rsi21_ha3_eenter | 653 | -0.152 | -0.072 | -2.9 | 0/4 | -0.140 |
| pre | c4_lrcS_ha3_eenter | 961 | -0.135 | -0.068 | -2.7 | 0/4 | -0.127 |
| pre | c4_wtF_ha3_eenter_z1 | 551 | -0.137 | -0.066 | -2.6 | 0/4 | -0.180 |
| pre | c4_obS_dres_ha3_rise | 3265 | 0.100 | 0.065 | 2.7 | 4/4 | 0.107 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (566 of 61778 cell-conditions pass; chance at t>2.5 alone ~383)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_ema21_hold_ha3_hold3 | 4576 | 0.093 | 0.009 | 0.084 | 6.1 | 4/4 | 0.113 |
| K7 | asia | c4_w1_ema21_hold_ha3_side | 6341 | 0.076 | 0.004 | 0.073 | 5.9 | 4/4 | 0.089 |
| K7 | asia | c4_smie_ha3_ewith | 5239 | 0.080 | 0.009 | 0.071 | 5.3 | 4/4 | 0.104 |
| K7 | asia | c4_kerS_abs_ha3_hi | 4844 | 0.086 | 0.010 | 0.076 | 5.3 | 4/4 | 0.068 |
| K7 | asia | c4_tsi_ha3_ewith | 4266 | 0.097 | 0.009 | 0.088 | 5.0 | 4/4 | 0.132 |
| K7 | asia | c4_qqeS_ha3_ewith | 746 | 0.198 | 0.025 | 0.173 | 4.9 | 4/4 | 0.189 |
| K7 | asia | c4_ichi_cloud_ha3_hold3 | 8120 | 0.071 | -0.009 | 0.080 | 4.9 | 4/4 | 0.096 |
| K7 | asia | c4_qqe_ha3_side | 12798 | 0.049 | -0.041 | 0.090 | 4.9 | 4/4 | 0.122 |
| K7 | asia | c4_w1_keltner40_pos_ha3_side | 13988 | 0.044 | -0.072 | 0.117 | 4.9 | 4/4 | 0.144 |
| K7 | asia | c4_tsiS_ha3_ewith | 2680 | 0.119 | 0.016 | 0.103 | 4.8 | 4/4 | 0.088 |
| K7 | asia | c4_w1_cci50_ha3_side | 12693 | 0.050 | -0.043 | 0.092 | 4.7 | 4/4 | 0.127 |
| K7 | asia | c4_w1_ema_8_21_stack_ha3_side | 12558 | 0.048 | -0.032 | 0.080 | 4.7 | 4/4 | 0.108 |
| A7 | close | c4_stc_ha3_divwith | 74 | 0.508 | -0.048 | 0.556 | 4.7 | 3/4 | 0.788 |
| K7 | asia | c4_rsima21_ha3_side | 13905 | 0.044 | -0.068 | 0.112 | 4.7 | 4/4 | 0.123 |
| K7 | asia | c4_w1_rsi21_ha3_side | 13904 | 0.044 | -0.068 | 0.112 | 4.7 | 4/4 | 0.123 |
| K7 | asia | c4_smieS_ha3_ewith | 2775 | 0.108 | 0.017 | 0.091 | 4.6 | 4/4 | 0.092 |
| K7 | asia | c4_mcgS_px_ha3_side | 14415 | 0.042 | -0.088 | 0.129 | 4.6 | 4/4 | 0.188 |
| K7 | asia | c4_mcgS_slope_ha3_side | 14415 | 0.042 | -0.088 | 0.129 | 4.6 | 4/4 | 0.188 |
| K7 | asia | c4_tsiF_ha3_ewith | 8198 | 0.058 | 0.005 | 0.053 | 4.5 | 3/4 | 0.073 |
| K7 | asia | c4_w1_ema_stack_fast_ha3_side | 9664 | 0.060 | -0.012 | 0.072 | 4.5 | 4/4 | 0.129 |
| K7 | asia | c4_w1_ema_8_21_34_stack_ha3_side | 9664 | 0.060 | -0.012 | 0.072 | 4.5 | 4/4 | 0.129 |
| K7 | asia | c4_smiS_ha3_ewith | 6684 | 0.067 | 0.008 | 0.058 | 4.4 | 4/4 | 0.095 |
| K7 | asia | c4_qqeS_ha3_side | 11009 | 0.056 | -0.024 | 0.080 | 4.4 | 4/4 | 0.133 |
| K7 | asia | c4_chandS_ha3_hold3 | 8891 | 0.068 | -0.014 | 0.082 | 4.4 | 4/4 | 0.138 |
| K7 | asia | c4_w1_sma50_px_ha3_side | 12875 | 0.047 | -0.037 | 0.085 | 4.3 | 4/4 | 0.134 |
| K7 | asia | c4_w1_ema50_px_ha3_side | 13201 | 0.047 | -0.047 | 0.094 | 4.3 | 4/4 | 0.165 |
| K7 | asia | c4_stP_ha3_side | 9171 | 0.067 | -0.015 | 0.082 | 4.3 | 4/4 | 0.180 |
| K7 | asia | c4_qqe_ha3_ewith | 1570 | 0.128 | 0.023 | 0.105 | 4.3 | 4/4 | 0.091 |
| K7 | asia | c4_w1_ema100_px_ha3_side | 11037 | 0.058 | -0.029 | 0.087 | 4.3 | 4/4 | 0.152 |
| K7 | asia | c4_chandS_ha3_side | 9430 | 0.065 | -0.016 | 0.081 | 4.2 | 4/4 | 0.125 |

## B4 alternate bars: ha5

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2249; |t|>2: 0 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha5.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha5_side | 161681 | 0.84 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_sig | 139262 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_rise | 141099 | 0.73 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_fresh5 | 78958 | 0.41 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_ewith_z1 | 28095 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_eagainst_z1 | 497 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_eleave_z1 | 1899 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_eenter_z1 | 10085 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_ewith_z2 | 49961 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_eagainst_z2 | 1321 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha5_side | 161681 | 0.84 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_sig | 139262 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_rise | 141099 | 0.73 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_fresh5 | 78958 | 0.41 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_ewith_z1 | 28095 | 0.15 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_eagainst_z1 | 497 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_eleave_z1 | 1899 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_eenter_z1 | 10085 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_ewith_z2 | 49961 | 0.26 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha5_eagainst_z2 | 1321 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 146 of 13026 session-condition cells pass (chance-level expectation under independence ~161 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_nweF_ha5_ewith | 401 | 0.220 | 0.072 | 3.1 | 4/4 | 0.346 |
| close | c4_rsima7_ha5_divwith | 1145 | 0.179 | 0.070 | 2.9 | 4/4 | 0.020 |
| close | c4_w1_rsi7_ha5_divwith | 1145 | 0.179 | 0.070 | 2.9 | 4/4 | 0.020 |
| close | c4_nwe_ha5_ewith | 422 | 0.233 | 0.069 | 3.0 | 4/4 | 0.390 |
| close | c4_kerF_dir_ha5_divwith | 1599 | 0.123 | 0.065 | 2.6 | 4/4 | 0.010 |
| close | c4_obF_in_ha5_against | 2859 | 0.101 | 0.064 | 2.7 | 4/4 | 0.310 |
| london | c4_smie_ha5_nodiv | 50032 | -0.110 | -0.081 | -3.7 | 0/4 | -0.046 |
| london | c4_tsiF_ha5_nodiv | 49324 | -0.103 | -0.078 | -3.6 | 0/4 | -0.065 |
| london | c4_rsima7_ha5_eagainst | 308 | -0.168 | -0.076 | -3.0 | 0/4 | -0.162 |
| london | c4_w1_rsi7_ha5_eagainst | 308 | -0.168 | -0.076 | -3.0 | 0/4 | -0.162 |
| london | c4_smiS_ha5_nodiv | 48340 | -0.096 | -0.076 | -3.7 | 0/4 | -0.062 |
| london | c4_rfilt_dir_ha5_against | 10955 | -0.093 | -0.075 | -3.8 | 0/4 | -0.004 |
| nyam | c4_w1_vortex14_ha5_divwith | 2909 | -0.151 | -0.089 | -3.6 | 0/4 | -0.200 |
| nyam | c4_w1_atr_pct250_ha5_hi | 23960 | 0.246 | 0.088 | 3.7 | 4/4 | 0.388 |
| nyam | c4_crsi_ha5_eagainst_z2 | 746 | -0.156 | -0.076 | -3.1 | 0/4 | -0.190 |
| nyam | c4_w1_cmo14_ha5_divwith | 2986 | -0.129 | -0.075 | -3.0 | 0/4 | -0.117 |
| nyam | c4_crsiF_ha5_eagainst | 247 | -0.259 | -0.073 | -3.2 | 0/4 | -0.311 |
| nyam | c4_w1_demarker14_ha5_divwith | 3050 | -0.118 | -0.070 | -2.8 | 0/4 | -0.115 |
| nypm | c4_obF_cnt_ha5_fresh5 | 966 | -0.177 | -0.079 | -3.2 | 0/4 | -0.345 |
| nypm | c4_stAS_ha5_fresh5 | 1159 | -0.159 | -0.074 | -3.0 | 0/4 | -0.250 |
| nypm | c4_w1_ema100_px_ha5_fresh5 | 2923 | -0.107 | -0.072 | -3.1 | 0/4 | -0.285 |
| nypm | c4_w1_ema_stack_slow_ha5_hold3 | 14637 | 0.110 | 0.071 | 3.0 | 4/4 | 0.233 |
| nypm | c4_w1_sma_stack_slow_ha5_side | 12716 | 0.103 | 0.067 | 2.8 | 4/4 | 0.237 |
| nypm | c4_sdflipF_in_ha5_against | 6737 | -0.089 | -0.066 | -3.0 | 0/4 | -0.270 |
| pre | c4_tsiS_ha5_eenter | 523 | -0.276 | -0.099 | -4.1 | 0/4 | -0.341 |
| pre | c4_w1_kama200_px_ha5_divwith | 822 | -0.304 | -0.079 | -3.6 | 0/4 | -0.259 |
| pre | c4_seb_ha5_ewith | 1600 | -0.125 | -0.075 | -3.1 | 0/4 | -0.180 |
| pre | c4_w1_ema200_px_ha5_divwith | 844 | -0.287 | -0.074 | -3.4 | 0/4 | -0.415 |
| pre | c4_w1_sma34_px_ha5_divwith | 934 | -0.259 | -0.073 | -3.3 | 0/4 | -0.261 |
| pre | c4_w1_kama34_px_ha5_divwith | 997 | -0.243 | -0.072 | -3.2 | 0/4 | -0.166 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (705 of 63283 cell-conditions pass; chance at t>2.5 alone ~392)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_keltner40_pos_ha5_ewith | 1153 | 0.195 | 0.021 | 0.174 | 5.2 | 4/4 | 0.160 |
| K7 | asia | c4_w1_demarker21_ha5_ewith | 4094 | 0.099 | 0.010 | 0.090 | 5.1 | 4/4 | 0.094 |
| K7 | asia | c4_rsima7_ha5_ewith | 5073 | 0.076 | 0.013 | 0.063 | 5.0 | 4/4 | 0.076 |
| K7 | asia | c4_w1_rsi7_ha5_ewith | 5073 | 0.076 | 0.013 | 0.063 | 5.0 | 4/4 | 0.076 |
| K7 | asia | c4_don55_pos_ha5_eenter | 440 | 0.206 | 0.029 | 0.177 | 5.0 | 4/4 | 0.154 |
| K7 | asia | c4_w1_ema21_hold_ha5_side | 5531 | 0.083 | 0.006 | 0.077 | 5.0 | 4/4 | 0.103 |
| K7 | asia | c4_don55_pos_ha5_ewith | 672 | 0.188 | 0.027 | 0.162 | 4.9 | 4/4 | 0.201 |
| K7 | asia | c4_w1_ema_stack_fast_ha5_hold3 | 7242 | 0.079 | -0.006 | 0.085 | 4.9 | 4/4 | 0.157 |
| K7 | asia | c4_w1_ema_8_21_34_stack_ha5_hold3 | 7242 | 0.079 | -0.006 | 0.085 | 4.9 | 4/4 | 0.157 |
| K7 | asia | c4_w1_mfi21_ha5_side | 9729 | 0.061 | -0.014 | 0.075 | 4.9 | 4/4 | 0.141 |
| K7 | asia | c4_qqeF_ha5_ewith | 4196 | 0.088 | 0.013 | 0.075 | 4.9 | 4/4 | 0.107 |
| K7 | asia | c4_alligator_ha5_side | 7307 | 0.078 | -0.006 | 0.084 | 4.9 | 4/4 | 0.142 |
| K7 | asia | c4_qqeS_ha5_ewith | 799 | 0.208 | 0.024 | 0.184 | 4.8 | 3/4 | 0.305 |
| K7 | asia | c4_smie_ha5_ewith | 4276 | 0.094 | 0.010 | 0.083 | 4.8 | 4/4 | 0.134 |
| K7 | asia | c4_w1_macd8_17_9_line_ha5_side | 10344 | 0.058 | -0.018 | 0.076 | 4.8 | 4/4 | 0.128 |
| K7 | asia | c4_smie_ha5_side | 10713 | 0.057 | -0.019 | 0.076 | 4.8 | 4/4 | 0.110 |
| K7 | asia | c4_qqe_ha5_ewith | 1718 | 0.140 | 0.020 | 0.120 | 4.7 | 4/4 | 0.108 |
| K7 | asia | c4_w1_donchian50_pos_ha5_ewith | 592 | 0.189 | 0.027 | 0.162 | 4.7 | 4/4 | 0.228 |
| K7 | asia | c4_w1_donchian50_pos_ha5_eenter | 402 | 0.202 | 0.029 | 0.173 | 4.7 | 4/4 | 0.198 |
| K7 | asia | c4_w1_ema21_hold_ha5_hold3 | 4104 | 0.094 | 0.012 | 0.082 | 4.7 | 4/4 | 0.108 |
| K7 | asia | c4_w1_rsi14_ha5_ewith | 2026 | 0.127 | 0.019 | 0.108 | 4.7 | 4/4 | 0.131 |
| K7 | asia | c4_tsiS_ha5_side | 8827 | 0.073 | -0.019 | 0.092 | 4.7 | 4/4 | 0.160 |
| K7 | asia | c4_rsima14_ha5_ewith | 2027 | 0.127 | 0.019 | 0.107 | 4.7 | 4/4 | 0.131 |
| K7 | asia | c4_w1_rsi14_ha5_side | 11789 | 0.053 | -0.029 | 0.082 | 4.7 | 4/4 | 0.151 |
| K7 | asia | c4_rsima14_ha5_side | 11790 | 0.053 | -0.029 | 0.082 | 4.7 | 4/4 | 0.151 |
| K7 | asia | c4_w1_cmo21_ha5_ewith | 2024 | 0.122 | 0.020 | 0.102 | 4.7 | 4/4 | 0.085 |
| K7 | asia | c4_nweS_ha5_side | 11847 | 0.052 | -0.028 | 0.080 | 4.7 | 4/4 | 0.120 |
| K7 | asia | c4_w1_ema21_px_ha5_side | 12399 | 0.050 | -0.033 | 0.083 | 4.7 | 4/4 | 0.136 |
| A7 | nypm | c4_w1_ema_stack_slow_ha5_hold3 | 2939 | 0.068 | -0.199 | 0.267 | 4.7 | 4/4 | 0.432 |
| K7 | asia | c4_qqe_ha5_side | 10295 | 0.059 | -0.018 | 0.078 | 4.6 | 4/4 | 0.128 |

## B4 alternate bars: ha60

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2271; |t|>2: 0 (chance expectation ~103 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_ha60.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha60_side | 105183 | 0.54 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_sig | 119309 | 0.62 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_rise | 127267 | 0.66 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_fresh5 | 75065 | 0.39 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_ewith_z1 | 16369 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eagainst_z1 | 9508 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eleave_z1 | 5903 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eenter_z1 | 6443 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_ewith_z2 | 26451 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eagainst_z2 | 17191 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_ha60_side | 105183 | 0.54 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_sig | 119309 | 0.62 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_rise | 127267 | 0.66 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_fresh5 | 75065 | 0.39 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_ewith_z1 | 16369 | 0.08 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eagainst_z1 | 9508 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eleave_z1 | 5903 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eenter_z1 | 6443 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_ewith_z2 | 26451 | 0.14 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_ha60_eagainst_z2 | 17191 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 248 of 13281 session-condition cells pass (chance-level expectation under independence ~164 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_w1_cci14_ha60_eleave_z1 | 3176 | -0.126 | -0.076 | -3.1 | 0/4 | -0.093 |
| close | c4_smieF_ha60_eleave | 2090 | -0.142 | -0.074 | -3.0 | 0/4 | -0.259 |
| close | c4_w1_linreg_slope20_ha60_nodiv | 10028 | -0.112 | -0.064 | -2.6 | 0/4 | -0.103 |
| close | c4_sdflipF_near_ha60_against | 3160 | -0.103 | -0.063 | -2.6 | 0/4 | -0.150 |
| close | c4_smiF_ha60_eleave | 1168 | -0.177 | -0.062 | -2.6 | 0/4 | -0.253 |
| close | c4_w1_donchian20_width_ha60_hi | 7166 | -0.090 | -0.060 | -2.5 | 0/4 | -0.102 |
| london | c4_kr_dir_ha60_fresh5 | 2707 | 0.165 | 0.073 | 2.9 | 4/4 | 0.011 |
| london | c4_stPS_ha60_fresh5 | 826 | 0.336 | 0.071 | 3.5 | 4/4 | 0.382 |
| london | c4_w1_donchian20_pos_ha60_nodiv | 52804 | 0.145 | 0.067 | 2.7 | 4/4 | 0.228 |
| london | c4_w1_donchian50_pos_ha60_divwith | 4153 | 0.131 | 0.063 | 2.5 | 4/4 | 0.173 |
| london | c4_smiS_ha60_eleave | 2042 | 0.170 | 0.061 | 2.5 | 4/4 | 0.265 |
| london | c4_w1_kama8_px_ha60_side | 36212 | 0.074 | 0.059 | 2.9 | 4/4 | 0.113 |
| nyam | c4_ob_in_ha60_side | 1903 | -0.170 | -0.076 | -3.0 | 0/4 | -0.285 |
| nyam | c4_don55_pos_ha60_ewith | 484 | 0.353 | 0.070 | 3.5 | 4/4 | 0.385 |
| nyam | c4_w1_mfi14_ha60_divwith | 3955 | -0.121 | -0.070 | -2.8 | 0/4 | -0.122 |
| nyam | c4_w1_donchian50_pos_ha60_ewith | 462 | 0.366 | 0.069 | 3.5 | 4/4 | 0.385 |
| nyam | c4_obF_in_ha60_side | 2197 | -0.140 | -0.068 | -2.7 | 0/4 | -0.242 |
| nyam | c4_w1_keltner10_pos_ha60_eenter | 4349 | 0.125 | 0.064 | 2.6 | 4/4 | 0.234 |
| nypm | c4_ichi_kj_ha60_fresh1 | 1796 | -0.260 | -0.125 | -5.0 | 0/4 | -0.334 |
| nypm | c4_ichiS_kj_ha60_fresh1 | 1659 | -0.269 | -0.120 | -4.8 | 0/4 | -0.367 |
| nypm | c4_w1_macd12_26_9_line_ha60_side | 14831 | 0.149 | 0.101 | 4.3 | 4/4 | 0.216 |
| nypm | c4_smie_ha60_eleave | 2566 | -0.199 | -0.101 | -4.0 | 0/4 | -0.228 |
| nypm | c4_wtS_ha60_ewith_z2 | 4052 | 0.217 | 0.100 | 4.0 | 4/4 | 0.415 |
| nypm | c4_wt_ha60_ewith_z1 | 3450 | 0.244 | 0.100 | 4.1 | 4/4 | 0.385 |
| pre | c4_elderS_bear_ha60_fresh5 | 2291 | 0.207 | 0.080 | 3.3 | 4/4 | 0.210 |
| pre | c4_obS_dres_ha60_rise | 2911 | 0.172 | 0.079 | 3.2 | 4/4 | 0.312 |
| pre | c4_pdS_ha60_ewith | 2453 | -0.184 | -0.071 | -2.9 | 0/4 | -0.127 |
| pre | c4_w1_rsi21_ha60_fresh5 | 1597 | 0.219 | 0.070 | 3.0 | 4/4 | 0.389 |
| pre | c4_w1_keltner40_pos_ha60_fresh5 | 1592 | 0.205 | 0.067 | 2.8 | 4/4 | 0.264 |
| pre | c4_w1_atr_pct250_ha60_hi | 2405 | -0.146 | -0.065 | -2.6 | 0/4 | -0.098 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (1145 of 69866 cell-conditions pass; chance at t>2.5 alone ~433)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| A7 | nypm | c4_wt_ha60_side | 2892 | 0.079 | -0.215 | 0.294 | 5.0 | 4/4 | 0.532 |
| P7 | london | c4_nweF_ha60_eenter | 91 | 0.591 | 0.021 | 0.570 | 4.9 | 4/4 | 0.233 |
| P7 | london | c4_nweF_ha60_ewith | 95 | 0.571 | 0.021 | 0.550 | 4.9 | 4/4 | 0.311 |
| A7 | nypm | c4_w1_macd12_26_9_line_ha60_side | 2828 | 0.083 | -0.208 | 0.291 | 4.9 | 4/4 | 0.487 |
| A7 | nypm | c4_wtS_ha60_side | 2751 | 0.085 | -0.197 | 0.282 | 4.8 | 4/4 | 0.449 |
| A7 | nypm | c4_tsi_ha60_side | 2822 | 0.082 | -0.205 | 0.287 | 4.8 | 4/4 | 0.487 |
| A7 | nypm | c4_w1_ao_ha60_side | 2748 | 0.085 | -0.192 | 0.276 | 4.8 | 4/4 | 0.503 |
| A7 | nypm | c4_coppS_ha60_side | 2589 | 0.093 | -0.177 | 0.270 | 4.7 | 4/4 | 0.371 |
| A7 | nypm | c4_w1_ema_stack_fast_ha60_side | 2436 | 0.102 | -0.167 | 0.268 | 4.7 | 4/4 | 0.426 |
| A7 | nypm | c4_w1_ema_8_21_34_stack_ha60_side | 2436 | 0.102 | -0.167 | 0.268 | 4.7 | 4/4 | 0.426 |
| A7 | nypm | c4_w1_macd8_17_9_line_ha60_side | 2956 | 0.070 | -0.210 | 0.280 | 4.6 | 4/4 | 0.474 |
| A7 | nyam | c4_don55_pos_ha60_ewith | 89 | 0.603 | 0.025 | 0.578 | 4.6 | 4/4 | 0.779 |
| A7 | nypm | c4_w1_trix8_ha60_side | 2779 | 0.079 | -0.188 | 0.267 | 4.6 | 4/4 | 0.454 |
| A7 | nypm | c4_w1_ema_8_21_stack_ha60_side | 2935 | 0.067 | -0.196 | 0.264 | 4.5 | 4/4 | 0.505 |
| P7 | asia | c4_w1_uo_ha60_eenter | 163 | 0.469 | 0.036 | 0.432 | 4.4 | 4/4 | 0.532 |
| A7 | nypm | c4_smieS_ha60_side | 2860 | 0.075 | -0.199 | 0.274 | 4.4 | 4/4 | 0.487 |
| A7 | nyam | c4_w1_donchian50_pos_ha60_ewith | 87 | 0.594 | 0.025 | 0.568 | 4.4 | 4/4 | 0.779 |
| K7 | asia | c4_w1_ha_run_ha60_side | 8220 | 0.075 | -0.014 | 0.088 | 4.3 | 4/4 | 0.147 |
| A7 | nypm | c4_pdS_ha60_eagainst | 2440 | 0.085 | -0.150 | 0.236 | 4.3 | 4/4 | 0.473 |
| A7 | nypm | c4_qqe_ha60_side | 2951 | 0.064 | -0.192 | 0.256 | 4.3 | 4/4 | 0.505 |
| A7 | nypm | c4_w1_fisher20_ha60_side | 2681 | 0.078 | -0.168 | 0.246 | 4.3 | 4/4 | 0.290 |
| K7 | asia | c4_alma_slope_ha60_side | 8110 | 0.075 | -0.013 | 0.088 | 4.3 | 4/4 | 0.184 |
| A7 | nypm | c4_ichi_score_ha60_side | 2857 | 0.067 | -0.177 | 0.244 | 4.3 | 4/4 | 0.393 |
| K7 | asia | c4_w1_mfi21_ha60_rise | 7992 | 0.070 | -0.007 | 0.077 | 4.2 | 4/4 | 0.135 |
| K7 | asia | c4_w1_rsi21_ha60_eenter | 381 | 0.262 | 0.028 | 0.235 | 4.2 | 4/4 | 0.116 |
| A7 | nypm | c4_rviS_ha60_side | 2553 | 0.085 | -0.158 | 0.242 | 4.2 | 4/4 | 0.342 |
| A7 | nypm | c4_stPF_ha60_side | 2925 | 0.067 | -0.192 | 0.258 | 4.2 | 4/4 | 0.394 |
| P7 | asia | c4_w1_rsi21_ha60_ewith | 3188 | 0.147 | 0.020 | 0.128 | 4.1 | 4/4 | 0.172 |
| A7 | london | c4_nwe_ha60_ewith | 69 | 0.678 | 0.027 | 0.651 | 4.1 | 3/3 | 0.372 |
| M7 | nypm | c4_wt_ha60_ewith_z2 | 1258 | 0.198 | -0.029 | 0.227 | 4.1 | 4/4 | 0.336 |

## B4 alternate bars: range16

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2246; |t|>2: 0 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_range16.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_range16_side | 161602 | 0.84 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_sig | 130491 | 0.68 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_rise | 132576 | 0.69 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_fresh5 | 85148 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_ewith_z1 | 18999 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_eagainst_z1 | 159 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_eleave_z1 | 386 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_eenter_z1 | 8731 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_ewith_z2 | 37250 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_eagainst_z2 | 558 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_range16_side | 161602 | 0.84 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_sig | 130491 | 0.68 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_rise | 132576 | 0.69 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_fresh5 | 85148 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_ewith_z1 | 18999 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_eagainst_z1 | 159 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_eleave_z1 | 386 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_eenter_z1 | 8731 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_ewith_z2 | 37250 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range16_eagainst_z2 | 558 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 130 of 13086 session-condition cells pass (chance-level expectation under independence ~162 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_w1_boll20_pctb_range16_eleave | 306 | 0.201 | 0.102 | 4.1 | 4/4 | 0.267 |
| close | c4_w1_willr21_range16_eleave | 1121 | 0.112 | 0.086 | 4.1 | 4/4 | 0.156 |
| close | c4_w1_rsi2_range16_eleave | 1506 | 0.106 | 0.085 | 4.2 | 4/4 | 0.127 |
| close | c4_w1_cci14_range16_eenter_z2 | 424 | -0.136 | -0.074 | -3.0 | 0/4 | -0.174 |
| close | c4_stc_range16_nodiv | 12101 | -0.089 | -0.069 | -3.4 | 0/4 | -0.219 |
| close | c4_w1_mfi7_range16_eleave | 901 | 0.096 | 0.069 | 3.1 | 4/4 | 0.145 |
| london | c4_w1_supertrend_14_4_range16_nodiv | 57184 | -0.159 | -0.078 | -3.1 | 0/4 | -0.177 |
| london | c4_sfpF_range16_fresh1 | 901 | 0.107 | 0.077 | 3.4 | 4/4 | 0.059 |
| london | c4_sfpF_range16_side | 901 | 0.107 | 0.077 | 3.4 | 4/4 | 0.059 |
| london | c4_choch_range16_fresh1 | 1989 | -0.090 | -0.073 | -3.8 | 0/4 | -0.102 |
| london | c4_w1_pat_engulf_range16_divwith | 3163 | 0.067 | 0.053 | 2.6 | 4/4 | 0.162 |
| london | c4_w1_cci14_range16_eenter_z2 | 2147 | -0.063 | -0.052 | -2.7 | 0/4 | -0.009 |
| nyam | c4_w1_adx14_range16_hi_z1 | 3991 | -0.095 | -0.081 | -4.4 | 0/4 | -0.038 |
| nyam | c4_w1_adx21_range16_hi_z1 | 1414 | -0.107 | -0.073 | -3.1 | 0/4 | -0.039 |
| nyam | c4_vsa_nodemand_range16_against | 560 | -0.123 | -0.070 | -2.8 | 0/4 | -0.141 |
| nyam | c4_w1_di21_range16_divwith | 645 | 0.110 | 0.064 | 2.6 | 4/4 | 0.196 |
| nyam | c4_lrcS_range16_ewith | 3554 | -0.076 | -0.063 | -3.5 | 0/4 | -0.109 |
| nyam | c4_w1_adx14_range16_hi | 7856 | -0.062 | -0.056 | -3.7 | 0/4 | -0.039 |
| nypm | c4_ob_in_range16_hold3 | 214 | -0.221 | -0.090 | -3.6 | 0/4 | -0.179 |
| nypm | c4_ote_wideF_range16_hold3 | 166 | -0.201 | -0.058 | -2.6 | 0/4 | -0.515 |
| nypm | c4_krF_dir_range16_fresh1 | 1121 | -0.083 | -0.058 | -2.5 | 0/4 | -0.234 |
| nypm | c4_zlema_px_range16_fresh1 | 2852 | 0.060 | 0.053 | 3.1 | 4/4 | 0.117 |
| nypm | c4_zlemaF_px_range16_fresh1 | 4069 | 0.053 | 0.047 | 2.8 | 4/4 | 0.019 |
| nypm | c4_w1_willr7_range16_rise | 13761 | 0.044 | 0.040 | 2.9 | 4/4 | 0.023 |
| pre | c4_fractal_brk_range16_fresh1 | 350 | 0.185 | 0.085 | 3.4 | 4/4 | 0.255 |
| pre | c4_eqpool_dnF_range16_rise | 1889 | -0.158 | -0.077 | -3.1 | 0/4 | -0.119 |
| pre | c4_chochF_range16_fresh1 | 348 | 0.162 | 0.076 | 3.0 | 4/4 | 0.134 |
| pre | c4_hiloS_range16_fresh1 | 536 | 0.131 | 0.070 | 2.8 | 4/4 | 0.104 |
| pre | c4_choch_range16_side | 7119 | -0.100 | -0.066 | -2.8 | 0/4 | -0.080 |
| pre | c4_struct_range16_against | 2137 | 0.100 | 0.066 | 2.8 | 4/4 | 0.080 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (502 of 67150 cell-conditions pass; chance at t>2.5 alone ~416)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_tsiS_range16_side | 12474 | 0.048 | -0.029 | 0.078 | 5.0 | 4/4 | 0.102 |
| K7 | asia | c4_w1_ema_stack_slow_range16_hold3 | 8693 | 0.072 | -0.016 | 0.088 | 4.9 | 4/4 | 0.078 |
| K7 | asia | c4_w1_ema_stack_slow_range16_side | 8963 | 0.070 | -0.018 | 0.088 | 4.7 | 4/4 | 0.108 |
| K7 | asia | c4_w1_macd19_39_9_line_range16_side | 12542 | 0.047 | -0.027 | 0.074 | 4.7 | 4/4 | 0.058 |
| K7 | asia | c4_w1_ema200_px_range16_side | 12681 | 0.053 | -0.056 | 0.109 | 4.7 | 4/4 | 0.276 |
| K7 | asia | c4_w1_kama200_px_range16_side | 13086 | 0.047 | -0.046 | 0.093 | 4.7 | 4/4 | 0.081 |
| K7 | asia | c4_w1_sma200_px_range16_side | 12310 | 0.054 | -0.048 | 0.101 | 4.7 | 4/4 | 0.256 |
| K7 | asia | c4_stPS_range16_hold3 | 11110 | 0.055 | -0.023 | 0.079 | 4.6 | 4/4 | 0.033 |
| K7 | asia | c4_stPS_range16_side | 11634 | 0.053 | -0.026 | 0.078 | 4.5 | 4/4 | 0.080 |
| K7 | asia | c4_w1_aroon50_range16_side | 11135 | 0.052 | -0.014 | 0.066 | 4.4 | 4/4 | 0.104 |
| K7 | pre | c4_w1_rsi21_range16_side | 1897 | -0.012 | -0.446 | 0.434 | 4.4 | 3/4 | 0.657 |
| K7 | pre | c4_rsima21_range16_side | 1897 | -0.012 | -0.446 | 0.434 | 4.4 | 3/4 | 0.657 |
| K7 | asia | c4_lrcF_slope_range16_side | 11185 | 0.051 | -0.013 | 0.065 | 4.4 | 4/4 | 0.058 |
| K7 | asia | c4_w1_linreg_slope50_range16_side | 11185 | 0.051 | -0.013 | 0.065 | 4.4 | 4/4 | 0.058 |
| K7 | asia | c4_w1_trix30_range16_side | 10664 | 0.056 | -0.017 | 0.073 | 4.3 | 4/4 | 0.031 |
| K7 | asia | c4_w1_vwma200_px_range16_side | 12231 | 0.053 | -0.044 | 0.097 | 4.2 | 4/4 | 0.204 |
| K7 | pre | c4_w1_kama50_px_range16_side | 1887 | -0.011 | -0.413 | 0.401 | 4.2 | 4/4 | 0.657 |
| K7 | asia | c4_w1_ema_stack_fast_range16_side | 12165 | 0.046 | -0.015 | 0.062 | 4.1 | 3/4 | 0.004 |
| K7 | asia | c4_w1_ema_8_21_34_stack_range16_side | 12165 | 0.046 | -0.015 | 0.062 | 4.1 | 3/4 | 0.004 |
| K7 | asia | c4_fvgF_cnt_range16_side | 11167 | 0.057 | -0.030 | 0.087 | 4.1 | 4/4 | 0.164 |
| K7 | asia | c4_w1_ema100_px_range16_side | 13614 | 0.044 | -0.045 | 0.089 | 4.1 | 4/4 | 0.431 |
| M7 | pre | c4_w1_linreg_slope50_range16_nodiv | 2002 | 0.041 | -0.146 | 0.188 | 4.1 | 4/4 | 0.261 |
| K7 | asia | c4_w1_vwma_stack_slow_range16_hold3 | 6575 | 0.072 | 0.005 | 0.066 | 4.0 | 4/4 | 0.084 |
| K7 | pre | c4_w1_keltner40_pos_range16_side | 1895 | -0.013 | -0.408 | 0.395 | 4.0 | 3/4 | 0.509 |
| K7 | asia | c4_qqeS_range16_side | 13338 | 0.043 | -0.030 | 0.074 | 4.0 | 3/4 | 0.022 |
| K7 | asia | c4_ichiS_futcloud_range16_side | 11353 | 0.049 | -0.010 | 0.059 | 4.0 | 4/4 | 0.027 |
| K7 | asia | c4_w1_vwma100_px_range16_side | 13279 | 0.044 | -0.035 | 0.079 | 3.9 | 4/4 | 0.249 |
| K7 | pre | c4_w1_ema34_px_range16_side | 1893 | -0.013 | -0.404 | 0.391 | 3.9 | 4/4 | 0.320 |
| K7 | asia | c4_w1_vwma_stack_slow_range16_side | 6823 | 0.069 | 0.005 | 0.063 | 3.9 | 4/4 | 0.077 |
| K7 | asia | c4_w1_sma100_px_range16_side | 13302 | 0.044 | -0.036 | 0.080 | 3.9 | 4/4 | 0.240 |

## B4 alternate bars: range8

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2249; |t|>2: 0 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_range8.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_range8_side | 157846 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_sig | 121805 | 0.63 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_rise | 121899 | 0.63 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_fresh5 | 81147 | 0.42 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_ewith_z1 | 19071 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_eagainst_z1 | 245 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_eleave_z1 | 337 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_eenter_z1 | 8474 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_ewith_z2 | 37700 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_eagainst_z2 | 783 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_range8_side | 157846 | 0.82 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_sig | 121805 | 0.63 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_rise | 121899 | 0.63 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_fresh5 | 81147 | 0.42 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_ewith_z1 | 19071 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_eagainst_z1 | 245 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_eleave_z1 | 337 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_eenter_z1 | 8474 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_ewith_z2 | 37700 | 0.20 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_range8_eagainst_z2 | 783 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 164 of 13126 session-condition cells pass (chance-level expectation under independence ~162 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_eqpool_dnF_range8_rise | 3020 | 0.098 | 0.077 | 3.8 | 4/4 | 0.075 |
| close | c4_w1_hma200_px_range8_divwith | 397 | 0.125 | 0.069 | 2.8 | 4/4 | 0.095 |
| close | c4_ote_wideS_range8_hold3 | 314 | 0.122 | 0.067 | 2.7 | 4/4 | 0.161 |
| close | c4_lrcS_slope_range8_fresh5 | 323 | -0.121 | -0.065 | -2.6 | 0/4 | -0.068 |
| close | c4_eqpool_upS_range8_hi | 1968 | -0.170 | -0.064 | -2.6 | 0/4 | -0.364 |
| close | c4_utbot_range8_fresh1 | 1183 | 0.075 | 0.059 | 2.9 | 4/4 | 0.083 |
| london | c4_w1_cmo14_range8_eagainst | 350 | 0.124 | 0.070 | 2.8 | 4/4 | 0.107 |
| london | c4_vsa_absorb_range8_against | 425 | -0.129 | -0.064 | -2.6 | 0/3 | -0.171 |
| london | c4_sfpS_range8_fresh5 | 1604 | 0.077 | 0.060 | 2.8 | 4/4 | 0.113 |
| london | c4_sd_near_range8_hold3 | 1759 | 0.070 | 0.054 | 2.6 | 4/4 | 0.108 |
| london | c4_ob_cnt_range8_side | 49418 | 0.056 | 0.047 | 2.6 | 4/4 | 0.028 |
| london | c4_stcS_range8_divwith | 3898 | 0.052 | 0.044 | 2.5 | 4/4 | 0.053 |
| nyam | c4_w1_linreg_chan10_range8_eenter | 507 | -0.144 | -0.075 | -3.0 | 0/4 | -0.079 |
| nyam | c4_w1_linreg_chan10_range8_ewith | 511 | -0.137 | -0.071 | -2.8 | 0/4 | -0.079 |
| nyam | c4_brkS_in_range8_against | 926 | 0.099 | 0.070 | 3.0 | 4/4 | 0.218 |
| nyam | c4_w1_kama_stack_fast_range8_against | 2548 | 0.075 | 0.064 | 3.5 | 4/4 | 0.037 |
| nyam | c4_w1_uo_range8_eagainst | 103 | -0.247 | -0.061 | -2.8 | 0/4 | -0.235 |
| nyam | c4_stPS_range8_against | 4622 | 0.055 | 0.049 | 3.2 | 4/4 | 0.019 |
| nypm | c4_eqsweepF_range8_fresh5 | 234 | 0.198 | 0.088 | 3.5 | 4/4 | 0.339 |
| nypm | c4_w1_ema_stack_slow_range8_against | 1323 | 0.102 | 0.074 | 3.3 | 4/4 | 0.168 |
| nypm | c4_stA_range8_fresh1 | 586 | 0.113 | 0.069 | 2.8 | 4/4 | 0.149 |
| nypm | c4_w1_supertrend_10_3_range8_rise | 586 | 0.113 | 0.069 | 2.8 | 4/4 | 0.149 |
| nypm | c4_w1_di21_range8_divwith | 656 | 0.103 | 0.067 | 2.8 | 4/4 | 0.062 |
| nypm | c4_w1_rsi2_range8_eagainst | 1436 | -0.090 | -0.066 | -3.0 | 0/4 | -0.208 |
| pre | c4_w1_sma100_px_range8_fresh5 | 1313 | 0.123 | 0.083 | 3.5 | 4/4 | 0.102 |
| pre | c4_zlema_px_range8_fresh1 | 903 | -0.121 | -0.078 | -3.2 | 0/4 | -0.126 |
| pre | c4_w1_vwma100_px_range8_fresh5 | 1398 | 0.110 | 0.077 | 3.4 | 4/4 | 0.145 |
| pre | c4_lrcS_range8_side | 6334 | -0.088 | -0.069 | -3.4 | 0/4 | -0.135 |
| pre | c4_sebS_range8_eleave | 422 | -0.150 | -0.067 | -2.7 | 0/4 | -0.250 |
| pre | c4_tsiS_range8_side | 7685 | -0.077 | -0.056 | -2.5 | 0/4 | -0.088 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (586 of 68419 cell-conditions pass; chance at t>2.5 alone ~424)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_ema_stack_slow_range8_side | 11134 | 0.057 | -0.029 | 0.086 | 5.1 | 4/4 | 0.028 |
| K7 | asia | c4_obS_cnt_range8_side | 12134 | 0.053 | -0.039 | 0.092 | 4.6 | 4/4 | 0.141 |
| H7 | london | c4_zlema_px_range8_divwith | 165 | 0.290 | -0.013 | 0.303 | 4.5 | 4/4 | 0.635 |
| A7 | nyam | c4_w1_di14_range8_nodiv | 3212 | 0.057 | -0.144 | 0.200 | 4.4 | 4/4 | 0.072 |
| H7 | london | c4_w1_wave_short_hist_range8_divwith | 166 | 0.285 | -0.012 | 0.297 | 4.4 | 4/4 | 0.475 |
| K7 | asia | c4_sd_cnt_range8_side | 12238 | 0.049 | -0.029 | 0.078 | 4.3 | 4/4 | 0.065 |
| K7 | asia | c4_w1_ema200_px_range8_side | 14442 | 0.040 | -0.058 | 0.098 | 4.2 | 4/4 | 0.304 |
| H7 | london | c4_w1_hma34_px_range8_divwith | 140 | 0.300 | -0.007 | 0.307 | 4.0 | 4/4 | 0.556 |
| A7 | nyam | c4_w1_di7_range8_nodiv | 3133 | 0.057 | -0.120 | 0.177 | 4.0 | 4/4 | 0.116 |
| K7 | asia | c4_sdS_cnt_range8_side | 11965 | 0.050 | -0.023 | 0.072 | 4.0 | 4/4 | 0.031 |
| H7 | london | c4_w1_hma21_px_range8_divwith | 205 | 0.244 | -0.015 | 0.259 | 4.0 | 4/4 | 0.514 |
| H7 | london | c4_halftS_range8_against | 408 | 0.169 | -0.043 | 0.212 | 4.0 | 4/4 | 0.235 |
| K7 | asia | c4_ob_cnt_range8_side | 12161 | 0.049 | -0.027 | 0.076 | 3.9 | 4/4 | 0.090 |
| K7 | asia | c4_sdF_cnt_range8_side | 12414 | 0.048 | -0.026 | 0.073 | 3.9 | 4/4 | 0.129 |
| A7 | asia | c4_sqzm_mom_range8_divwith | 446 | 0.230 | 0.085 | 0.145 | 3.9 | 3/4 | 0.264 |
| A7 | asia | c4_w1_sqz_hist_range8_divwith | 446 | 0.230 | 0.085 | 0.145 | 3.9 | 3/4 | 0.264 |
| K7 | asia | c4_fvgF_cnt_range8_side | 13191 | 0.045 | -0.035 | 0.079 | 3.9 | 4/4 | 0.054 |
| K7 | close | c4_elderS_bull_range8_fresh5 | 687 | 0.089 | -0.039 | 0.128 | 3.9 | 4/4 | 0.163 |
| K7 | asia | c4_fvgS_cnt_range8_side | 12886 | 0.046 | -0.030 | 0.076 | 3.9 | 4/4 | 0.022 |
| K7 | asia | c4_lrcS_slope_range8_side | 10686 | 0.051 | -0.005 | 0.056 | 3.8 | 4/4 | 0.008 |
| M7 | pre | c4_stPS_range8_against | 546 | 0.137 | -0.039 | 0.175 | 3.7 | 4/4 | 0.220 |
| H7 | london | c4_w1_sma8_px_range8_divwith | 115 | 0.299 | 0.000 | 0.299 | 3.7 | 4/4 | 0.478 |
| A7 | nyam | c4_w1_boll10_pctb_range8_side | 2821 | 0.059 | -0.064 | 0.124 | 3.7 | 3/4 | 0.222 |
| A7 | nyam | c4_sqzmF_bright_range8_hold3 | 916 | 0.122 | -0.001 | 0.122 | 3.7 | 4/4 | 0.192 |
| H7 | london | c4_w1_trendcolor_range8_divwith | 138 | 0.281 | -0.004 | 0.285 | 3.7 | 4/4 | 0.591 |
| K7 | asia | c4_w1_vwma200_px_range8_side | 14166 | 0.040 | -0.038 | 0.078 | 3.7 | 4/4 | 0.239 |
| A7 | nyam | c4_don10_pos_range8_side | 2825 | 0.061 | -0.071 | 0.132 | 3.7 | 4/4 | 0.216 |
| A7 | nyam | c4_w1_donchian10_pos_range8_side | 2825 | 0.061 | -0.071 | 0.132 | 3.7 | 4/4 | 0.216 |
| M7 | london | c4_lrc_range8_eleave | 511 | 0.155 | 0.021 | 0.134 | 3.6 | 4/4 | 0.032 |
| A7 | nyam | c4_w1_eom14_range8_side | 2586 | 0.066 | -0.054 | 0.120 | 3.6 | 4/4 | 0.033 |

## B4 alternate bars: renko16

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2163; |t|>2: 0 (chance expectation ~98 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_renko16.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_renko16_side | 166999 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_sig | 143134 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_rise | 147300 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_fresh5 | 89479 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_ewith_z1 | 19677 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_eagainst_z1 | 222 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_eleave_z1 | 641 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_eenter_z1 | 9076 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_ewith_z2 | 40210 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_eagainst_z2 | 639 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_renko16_side | 166999 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_sig | 143134 | 0.74 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_rise | 147300 | 0.76 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_fresh5 | 89479 | 0.46 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_ewith_z1 | 19677 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_eagainst_z1 | 222 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_eleave_z1 | 641 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_eenter_z1 | 9076 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_ewith_z2 | 40210 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko16_eagainst_z2 | 639 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 117 of 12498 session-condition cells pass (chance-level expectation under independence ~154 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_w1_uo_renko16_divwith | 784 | -0.144 | -0.079 | -3.2 | 0/4 | -0.088 |
| close | c4_smieF_renko16_divwith | 705 | -0.159 | -0.076 | -3.1 | 0/4 | -0.254 |
| close | c4_w1_keltner10_pos_renko16_divwith | 706 | -0.156 | -0.075 | -3.0 | 0/4 | -0.236 |
| close | c4_w1_vortex7_renko16_divwith | 837 | -0.140 | -0.073 | -2.9 | 0/4 | -0.133 |
| close | c4_w1_demarker7_renko16_divwith | 621 | -0.145 | -0.073 | -2.9 | 0/4 | -0.216 |
| close | c4_w1_aroon50_renko16_nodiv | 12013 | 0.098 | 0.069 | 3.0 | 4/4 | 0.070 |
| london | c4_w1_kama_stack_fast_renko16_against | 6642 | -0.095 | -0.069 | -3.1 | 0/4 | -0.074 |
| london | c4_rfiltS_dir_renko16_side | 45002 | 0.084 | 0.065 | 3.1 | 4/4 | 0.067 |
| london | c4_rfiltS_dir_renko16_against | 12771 | -0.084 | -0.065 | -3.1 | 0/4 | -0.067 |
| london | c4_rfiltS_dir_renko16_hold3 | 43095 | 0.073 | 0.058 | 2.8 | 4/4 | 0.028 |
| london | c4_smiS_renko16_eleave | 3523 | -0.057 | -0.047 | -2.5 | 0/4 | -0.134 |
| london | c4_w1_demarker21_renko16_eenter | 5073 | 0.053 | 0.045 | 2.6 | 4/4 | 0.034 |
| nyam | c4_crsi_renko16_ewith_z1 | 1414 | -0.105 | -0.075 | -3.3 | 0/4 | -0.130 |
| nyam | c4_rsima14_renko16_ewith | 1849 | -0.093 | -0.070 | -3.2 | 0/4 | -0.016 |
| nyam | c4_w1_rsi14_renko16_ewith | 1849 | -0.093 | -0.070 | -3.2 | 0/4 | -0.016 |
| nyam | c4_mcmf_renko16_divwith | 1148 | 0.107 | 0.063 | 2.5 | 4/4 | 0.115 |
| nyam | c4_crsi_renko16_eenter_z1 | 1002 | -0.095 | -0.062 | -2.6 | 0/4 | -0.139 |
| nyam | c4_t3S_px_renko16_divwith | 1745 | 0.092 | 0.062 | 2.6 | 4/4 | 0.119 |
| nypm | c4_w1_sma8_px_renko16_divwith | 1704 | -0.128 | -0.076 | -3.1 | 0/4 | -0.140 |
| nypm | c4_brkS_in_renko16_against | 783 | 0.125 | 0.071 | 2.9 | 4/4 | 0.246 |
| nypm | c4_stPS_renko16_fresh1 | 429 | -0.144 | -0.071 | -2.8 | 0/4 | -0.240 |
| nypm | c4_brkF_in_renko16_against | 1271 | 0.113 | 0.070 | 2.9 | 4/4 | 0.195 |
| nypm | c4_brk_in_renko16_against | 1271 | 0.113 | 0.070 | 2.9 | 4/4 | 0.195 |
| nypm | c4_brk_near_renko16_against | 1587 | 0.104 | 0.070 | 3.0 | 4/4 | 0.114 |
| pre | c4_pd_renko16_ewith | 604 | 0.219 | 0.082 | 3.4 | 4/4 | 0.127 |
| pre | c4_w1_vortex7_renko16_divwith | 616 | -0.242 | -0.081 | -3.4 | 0/4 | -0.250 |
| pre | c4_halft_renko16_side | 7373 | -0.114 | -0.076 | -3.2 | 0/4 | -0.009 |
| pre | c4_halft_renko16_against | 1883 | 0.114 | 0.076 | 3.2 | 4/4 | 0.009 |
| pre | c4_w1_ao_renko16_rise | 6429 | -0.106 | -0.075 | -3.3 | 0/4 | -0.021 |
| pre | c4_smiF_renko16_divwith | 644 | -0.233 | -0.075 | -3.2 | 0/4 | -0.375 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (718 of 63086 cell-conditions pass; chance at t>2.5 alone ~391)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_ema200_px_renko16_side | 11164 | 0.067 | -0.054 | 0.121 | 5.5 | 4/4 | 0.206 |
| K7 | asia | c4_w1_donchian50_pos_renko16_side | 12190 | 0.054 | -0.046 | 0.101 | 5.0 | 4/4 | 0.127 |
| K7 | asia | c4_fvgS_cnt_renko16_side | 10283 | 0.069 | -0.038 | 0.106 | 4.9 | 4/4 | 0.190 |
| K7 | asia | c4_fvgF_cnt_renko16_side | 10283 | 0.069 | -0.038 | 0.106 | 4.9 | 4/4 | 0.190 |
| K7 | asia | c4_fvg_cnt_renko16_side | 10283 | 0.069 | -0.038 | 0.106 | 4.9 | 4/4 | 0.190 |
| K7 | asia | c4_w1_ema100_px_renko16_side | 12091 | 0.056 | -0.051 | 0.107 | 4.8 | 4/4 | 0.216 |
| K7 | asia | c4_w1_ema_8_21_stack_renko16_hold3 | 10688 | 0.058 | -0.022 | 0.080 | 4.8 | 4/4 | 0.105 |
| K7 | asia | c4_don55_pos_renko16_side | 12086 | 0.054 | -0.042 | 0.096 | 4.7 | 4/4 | 0.099 |
| K7 | asia | c4_krS_px_renko16_side | 13083 | 0.048 | -0.049 | 0.097 | 4.7 | 4/4 | 0.155 |
| K7 | asia | c4_ob_cnt_renko16_side | 8901 | 0.077 | -0.026 | 0.102 | 4.7 | 4/4 | 0.100 |
| K7 | asia | c4_obF_cnt_renko16_side | 8901 | 0.077 | -0.026 | 0.102 | 4.7 | 4/4 | 0.100 |
| K7 | asia | c4_qqeS_renko16_side | 11604 | 0.056 | -0.036 | 0.092 | 4.6 | 4/4 | 0.105 |
| K7 | asia | c4_mcgS_slope_renko16_side | 13395 | 0.046 | -0.052 | 0.098 | 4.6 | 4/4 | 0.145 |
| K7 | asia | c4_mcgS_px_renko16_side | 13395 | 0.046 | -0.052 | 0.098 | 4.6 | 4/4 | 0.145 |
| K7 | asia | c4_w1_macd12_26_9_line_renko16_side | 11600 | 0.055 | -0.033 | 0.089 | 4.6 | 4/4 | 0.082 |
| K7 | asia | c4_w1_keltner40_pos_renko16_side | 13222 | 0.047 | -0.050 | 0.098 | 4.6 | 4/4 | 0.169 |
| K7 | asia | c4_w1_ao_renko16_side | 11391 | 0.054 | -0.026 | 0.080 | 4.6 | 4/4 | 0.081 |
| K7 | asia | c4_w1_ema34_px_renko16_side | 13412 | 0.046 | -0.049 | 0.095 | 4.6 | 4/4 | 0.159 |
| K7 | asia | c4_w1_sma50_px_renko16_side | 12601 | 0.051 | -0.044 | 0.095 | 4.5 | 4/4 | 0.206 |
| K7 | asia | c4_w1_di21_renko16_side | 12836 | 0.049 | -0.046 | 0.095 | 4.5 | 4/4 | 0.118 |
| K7 | asia | c4_smieS_renko16_side | 11791 | 0.054 | -0.034 | 0.088 | 4.5 | 4/4 | 0.087 |
| K7 | asia | c4_w1_cci50_renko16_side | 12407 | 0.052 | -0.042 | 0.094 | 4.5 | 4/4 | 0.183 |
| K7 | asia | c4_smie_renko16_side | 12776 | 0.049 | -0.041 | 0.089 | 4.5 | 4/4 | 0.205 |
| K7 | asia | c4_rfiltS_dir_renko16_side | 10198 | 0.063 | -0.024 | 0.087 | 4.5 | 4/4 | 0.045 |
| K7 | asia | c4_w1_keltner40_pos_renko16_ewith | 9557 | 0.062 | -0.013 | 0.075 | 4.5 | 4/4 | 0.088 |
| K7 | asia | c4_w1_rsi21_renko16_side | 13190 | 0.047 | -0.048 | 0.095 | 4.5 | 4/4 | 0.190 |
| K7 | asia | c4_w1_boll40_pctb_renko16_side | 12941 | 0.048 | -0.044 | 0.093 | 4.4 | 4/4 | 0.267 |
| K7 | asia | c4_rsima21_renko16_side | 13195 | 0.047 | -0.047 | 0.094 | 4.4 | 4/4 | 0.190 |
| K7 | asia | c4_krS_dir_renko16_side | 12678 | 0.050 | -0.045 | 0.095 | 4.4 | 4/4 | 0.145 |
| K7 | asia | c4_wt_renko16_side | 12019 | 0.052 | -0.034 | 0.086 | 4.4 | 4/4 | 0.030 |

## B4 alternate bars: renko8

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2171; |t|>2: 0 (chance expectation ~98 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_renko8.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_renko8_side | 165422 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_sig | 134478 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_rise | 135086 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_fresh5 | 83283 | 0.43 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_ewith_z1 | 21000 | 0.11 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_eagainst_z1 | 243 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_eleave_z1 | 333 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_eenter_z1 | 9282 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_ewith_z2 | 41128 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_eagainst_z2 | 690 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_renko8_side | 165422 | 0.86 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_sig | 134478 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_rise | 135086 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_fresh5 | 83283 | 0.43 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_ewith_z1 | 21000 | 0.11 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_eagainst_z1 | 243 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_eleave_z1 | 333 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_eenter_z1 | 9282 | 0.05 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_ewith_z2 | 41128 | 0.21 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_renko8_eagainst_z2 | 690 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 139 of 12576 session-condition cells pass (chance-level expectation under independence ~155 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_w1_fisher10_renko8_divwith | 799 | 0.113 | 0.066 | 2.7 | 4/4 | 0.150 |
| close | c4_sebF_renko8_eagainst | 524 | -0.115 | -0.066 | -2.7 | 0/4 | -0.292 |
| close | c4_smi_renko8_divwith | 882 | 0.110 | 0.066 | 2.7 | 4/4 | 0.207 |
| close | c4_stPF_renko8_side | 11251 | -0.079 | -0.066 | -3.5 | 0/4 | -0.067 |
| close | c4_stPF_renko8_against | 2700 | 0.079 | 0.066 | 3.5 | 4/4 | 0.067 |
| close | c4_sslhyb_renko8_fresh1 | 1317 | 0.081 | 0.064 | 3.1 | 4/4 | 0.132 |
| london | c4_sd_cnt_renko8_side | 47002 | 0.074 | 0.058 | 2.8 | 4/4 | 0.002 |
| london | c4_sdF_cnt_renko8_side | 47109 | 0.071 | 0.055 | 2.6 | 4/4 | 0.006 |
| london | c4_w1_vwma100_px_renko8_nodiv | 54013 | -0.065 | -0.052 | -2.5 | 0/4 | -0.063 |
| london | c4_w1_kama_stack_slow_renko8_side | 33426 | 0.053 | 0.046 | 2.6 | 4/4 | 0.033 |
| london | c4_w1_kama_stack_slow_renko8_hold3 | 32333 | 0.052 | 0.045 | 2.6 | 4/4 | 0.037 |
| london | c4_lrc_slope_renko8_rise | 40034 | -0.043 | -0.041 | -3.8 | 0/4 | -0.037 |
| nyam | c4_tsiS_renko8_ewith | 2378 | -0.095 | -0.075 | -3.7 | 0/4 | -0.032 |
| nyam | c4_wt_renko8_eenter_z2 | 1852 | 0.091 | 0.073 | 3.6 | 4/4 | 0.113 |
| nyam | c4_qqeS_renko8_ewith | 322 | -0.153 | -0.066 | -2.7 | 0/4 | -0.048 |
| nyam | c4_smieS_renko8_ewith | 2488 | -0.079 | -0.064 | -3.2 | 0/4 | -0.041 |
| nyam | c4_qqe_renko8_ewith | 1375 | -0.083 | -0.059 | -2.6 | 0/4 | -0.091 |
| nyam | c4_w1_kama200_px_renko8_fresh5 | 2282 | 0.059 | 0.049 | 2.5 | 4/4 | 0.000 |
| nypm | c4_sqzmS_mom_renko8_divwith | 1736 | 0.082 | 0.063 | 3.0 | 4/4 | 0.121 |
| nypm | c4_mcmf_renko8_divwith | 1272 | 0.083 | 0.059 | 2.6 | 4/4 | 0.153 |
| nypm | c4_wt_renko8_eenter_z2 | 1896 | 0.066 | 0.053 | 2.7 | 4/4 | 0.088 |
| nypm | c4_w1_supertrend_7_2_renko8_rise | 1780 | 0.057 | 0.048 | 2.6 | 4/4 | 0.112 |
| nypm | c4_stAF_renko8_fresh1 | 1780 | 0.057 | 0.048 | 2.6 | 4/4 | 0.112 |
| nypm | c4_lrc_renko8_side | 17724 | 0.049 | 0.044 | 3.0 | 4/4 | 0.122 |
| pre | c4_smiS_renko8_eleave | 553 | 0.186 | 0.099 | 4.0 | 4/4 | 0.180 |
| pre | c4_rfilt_dir_renko8_hold3 | 6968 | -0.117 | -0.082 | -3.6 | 0/4 | -0.079 |
| pre | c4_stPF_renko8_hold3 | 6906 | -0.097 | -0.072 | -3.3 | 0/4 | -0.061 |
| pre | c4_rfilt_dir_renko8_side | 7351 | -0.106 | -0.072 | -3.1 | 0/4 | -0.056 |
| pre | c4_rfilt_dir_renko8_against | 1905 | 0.106 | 0.072 | 3.1 | 4/4 | 0.056 |
| pre | c4_pd_renko8_ewith | 758 | 0.146 | 0.071 | 2.8 | 4/4 | 0.106 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (559 of 65016 cell-conditions pass; chance at t>2.5 alone ~403)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_kstS_renko8_side | 11282 | 0.053 | -0.020 | 0.074 | 4.8 | 4/4 | 0.100 |
| K7 | asia | c4_w1_ema_stack_slow_renko8_hold3 | 9266 | 0.067 | -0.018 | 0.085 | 4.7 | 4/4 | 0.117 |
| K7 | asia | c4_w1_trix30_renko8_side | 11125 | 0.054 | -0.020 | 0.075 | 4.7 | 4/4 | 0.061 |
| K7 | asia | c4_obF_cnt_renko8_side | 10773 | 0.061 | -0.031 | 0.093 | 4.7 | 4/4 | 0.103 |
| K7 | asia | c4_ob_cnt_renko8_side | 10773 | 0.061 | -0.031 | 0.093 | 4.7 | 4/4 | 0.103 |
| K7 | asia | c4_fvg_cnt_renko8_side | 12348 | 0.051 | -0.039 | 0.090 | 4.6 | 4/4 | 0.141 |
| K7 | asia | c4_fvgS_cnt_renko8_side | 12348 | 0.051 | -0.039 | 0.090 | 4.6 | 4/4 | 0.141 |
| K7 | asia | c4_fvgF_cnt_renko8_side | 12348 | 0.051 | -0.039 | 0.090 | 4.6 | 4/4 | 0.141 |
| K7 | asia | c4_w1_vwma200_px_renko8_side | 12769 | 0.050 | -0.048 | 0.098 | 4.5 | 4/4 | 0.196 |
| K7 | asia | c4_w1_sma200_px_renko8_side | 12850 | 0.050 | -0.049 | 0.099 | 4.5 | 4/4 | 0.294 |
| K7 | asia | c4_w1_ema_stack_slow_renko8_side | 9528 | 0.064 | -0.017 | 0.081 | 4.3 | 4/4 | 0.099 |
| H7 | london | c4_w1_boll10_pctb_renko8_eleave | 139 | 0.300 | -0.007 | 0.307 | 4.2 | 4/4 | 0.376 |
| K7 | asia | c4_w1_ema200_px_renko8_side | 13210 | 0.047 | -0.047 | 0.094 | 4.1 | 4/4 | 0.207 |
| K7 | asia | c4_w1_ema100_px_renko8_side | 14105 | 0.041 | -0.045 | 0.086 | 4.0 | 4/4 | 0.194 |
| K7 | asia | c4_w1_vwma100_px_renko8_side | 13803 | 0.042 | -0.041 | 0.083 | 4.0 | 4/4 | 0.126 |
| A7 | nyam | c4_w1_boll10_width_pct_renko8_hi | 2061 | 0.079 | -0.032 | 0.110 | 3.8 | 4/4 | 0.148 |
| M7 | close | c4_obS_in_renko8_against | 323 | 0.189 | 0.002 | 0.187 | 3.8 | 4/4 | 0.159 |
| K7 | close | c4_stc_renko8_eagainst | 637 | 0.085 | -0.035 | 0.120 | 3.8 | 4/4 | 0.049 |
| K7 | close | c4_smi_renko8_divwith | 128 | 0.236 | -0.020 | 0.257 | 3.7 | 4/4 | 0.757 |
| A7 | asia | c4_kerF_abs_renko8_rise | 2031 | 0.147 | 0.068 | 0.079 | 3.7 | 4/4 | 0.139 |
| K7 | asia | c4_w1_kama200_px_renko8_side | 13414 | 0.044 | -0.037 | 0.081 | 3.7 | 4/4 | 0.157 |
| H7 | nypm | c4_crsi_renko8_rise | 293 | 0.131 | -0.165 | 0.296 | 3.7 | 4/4 | 0.368 |
| P7 | nypm | c4_w1_stoch8_renko8_sig | 3839 | 0.033 | -0.055 | 0.088 | 3.7 | 4/4 | 0.090 |
| H7 | london | c4_w1_rsi2_renko8_eleave | 112 | 0.307 | 0.000 | 0.307 | 3.6 | 4/4 | 0.527 |
| K7 | asia | c4_sdF_cnt_renko8_side | 10750 | 0.055 | -0.016 | 0.071 | 3.6 | 4/4 | 0.055 |
| M7 | london | c4_w1_stochrsi8_renko8_fresh5 | 8961 | 0.047 | -0.005 | 0.051 | 3.6 | 4/4 | 0.076 |
| A7 | asia | c4_smiS_renko8_eleave | 206 | 0.305 | 0.089 | 0.216 | 3.6 | 3/3 | 0.277 |
| M7 | london | c4_srsiF_renko8_fresh5 | 8962 | 0.047 | -0.004 | 0.051 | 3.5 | 4/4 | 0.076 |
| K7 | close | c4_w1_cmo14_renko8_divwith | 133 | 0.240 | -0.021 | 0.261 | 3.5 | 4/4 | 0.552 |
| M7 | pre | c4_rvi_renko8_sig | 1548 | 0.052 | -0.081 | 0.133 | 3.5 | 4/4 | 0.073 |

## B4 alternate bars: tick2000

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2259; |t|>2: 0 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_tick2000.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_tick2000_side | 139916 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_sig | 136141 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_rise | 140003 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_fresh5 | 85757 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_ewith_z1 | 20171 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_eagainst_z1 | 3007 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_eleave_z1 | 3624 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_eenter_z1 | 7764 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_ewith_z2 | 36298 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_eagainst_z2 | 6000 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_tick2000_side | 139916 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_sig | 136141 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_rise | 140003 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_fresh5 | 85757 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_ewith_z1 | 20171 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_eagainst_z1 | 3007 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_eleave_z1 | 3624 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_eenter_z1 | 7764 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_ewith_z2 | 36298 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_tick2000_eagainst_z2 | 6000 | 0.03 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 97 of 13132 session-condition cells pass (chance-level expectation under independence ~162 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_w1_boll40_walk_tick2000_side | 736 | 0.185 | 0.082 | 3.3 | 4/4 | 0.215 |
| close | c4_fvg_near_tick2000_hold3 | 1832 | 0.139 | 0.079 | 3.2 | 4/4 | 0.135 |
| close | c4_brkF_in_tick2000_side | 867 | 0.148 | 0.072 | 2.9 | 4/4 | 0.172 |
| close | c4_w1_aroon50_tick2000_nodiv | 11973 | 0.119 | 0.072 | 2.9 | 4/4 | 0.183 |
| close | c4_brk_near_tick2000_side | 2758 | 0.116 | 0.071 | 2.9 | 4/4 | 0.166 |
| close | c4_brk_in_tick2000_side | 724 | 0.151 | 0.071 | 2.8 | 4/4 | 0.053 |
| london | c4_w1_boll10_pctb_tick2000_eagainst | 781 | -0.140 | -0.077 | -3.1 | 0/4 | -0.160 |
| london | c4_ifvgS_in_tick2000_side | 1748 | 0.147 | 0.072 | 2.9 | 4/4 | 0.355 |
| london | c4_w1_willr7_tick2000_eagainst | 1824 | -0.106 | -0.070 | -2.9 | 0/4 | -0.018 |
| london | c4_ifvgF_in_tick2000_side | 2797 | 0.116 | 0.068 | 2.8 | 4/4 | 0.278 |
| london | c4_ifvgS_in_tick2000_hold3 | 501 | 0.241 | 0.064 | 2.9 | 4/4 | 0.464 |
| london | c4_obS_dres_tick2000_hi | 10052 | 0.090 | 0.063 | 2.8 | 4/4 | 0.067 |
| nyam | c4_nwe_tick2000_eenter | 172 | -0.392 | -0.091 | -4.3 | 0/4 | -0.324 |
| nyam | c4_nwe_tick2000_ewith | 184 | -0.322 | -0.088 | -3.9 | 0/4 | -0.124 |
| nyam | c4_kerF_dir_tick2000_eagainst | 790 | 0.118 | 0.073 | 3.0 | 4/4 | 0.041 |
| nyam | c4_stA21_tick2000_fresh1 | 966 | -0.109 | -0.071 | -3.0 | 0/4 | -0.087 |
| nyam | c4_w1_uo_tick2000_ewith | 1196 | -0.120 | -0.070 | -2.8 | 0/4 | -0.024 |
| nyam | c4_chochS_tick2000_fresh1 | 652 | -0.125 | -0.069 | -2.8 | 0/4 | -0.256 |
| nypm | c4_sd_cnt_tick2000_fresh5 | 1161 | -0.200 | -0.092 | -3.7 | 0/4 | -0.107 |
| nypm | c4_sdflipS_in_tick2000_side | 1959 | -0.118 | -0.074 | -3.0 | 0/4 | -0.008 |
| nypm | c4_sdF_cnt_tick2000_fresh5 | 1373 | -0.153 | -0.071 | -2.9 | 0/4 | -0.184 |
| nypm | c4_pdF_tick2000_ewith | 1309 | 0.132 | 0.071 | 2.8 | 4/4 | 0.109 |
| nypm | c4_w1_linreg_chan50_tick2000_eleave | 295 | 0.266 | 0.068 | 3.1 | 4/4 | 0.304 |
| nypm | c4_w1_roc20_tick2000_nodiv | 19440 | 0.095 | 0.066 | 2.9 | 4/4 | 0.014 |
| pre | c4_crsiF_tick2000_eleave | 242 | 0.397 | 0.074 | 3.8 | 4/4 | 0.023 |
| pre | c4_w1_rsi14_tick2000_nodiv | 7965 | 0.218 | 0.065 | 2.9 | 4/4 | 0.020 |
| pre | c4_rsima14_tick2000_nodiv | 7965 | 0.218 | 0.065 | 2.9 | 4/4 | 0.020 |
| pre | c4_w1_rsi7_tick2000_nodiv | 7638 | 0.182 | 0.060 | 2.5 | 4/4 | 0.027 |
| pre | c4_rsima7_tick2000_nodiv | 7638 | 0.182 | 0.060 | 2.5 | 4/4 | 0.027 |
| pre | c4_alma_x_tick2000_nodiv | 7999 | 0.205 | 0.059 | 2.6 | 4/4 | 0.359 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (722 of 66007 cell-conditions pass; chance at t>2.5 alone ~409)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_lrcS_tick2000_ewith | 1882 | 0.172 | 0.012 | 0.160 | 5.4 | 4/4 | 0.314 |
| K7 | asia | c4_ichiF_chikou_tick2000_side | 8800 | 0.080 | -0.028 | 0.108 | 5.3 | 4/4 | 0.091 |
| K7 | asia | c4_w1_eom14_tick2000_side | 8400 | 0.083 | -0.025 | 0.108 | 5.3 | 4/4 | 0.110 |
| K7 | asia | c4_w1_force13_tick2000_side | 9224 | 0.076 | -0.031 | 0.107 | 5.3 | 4/4 | 0.083 |
| K7 | asia | c4_w1_willr14_tick2000_side | 9143 | 0.080 | -0.035 | 0.115 | 5.3 | 4/4 | 0.108 |
| K7 | asia | c4_w1_boll20_pctb_tick2000_side | 8988 | 0.079 | -0.031 | 0.110 | 5.3 | 4/4 | 0.090 |
| K7 | asia | c4_mcg_slope_tick2000_side | 9224 | 0.077 | -0.032 | 0.109 | 5.2 | 4/4 | 0.098 |
| K7 | asia | c4_mcg_px_tick2000_side | 9224 | 0.077 | -0.032 | 0.109 | 5.2 | 4/4 | 0.098 |
| K7 | asia | c4_ichiF_kj_tick2000_side | 9168 | 0.078 | -0.031 | 0.109 | 5.1 | 4/4 | 0.119 |
| K7 | asia | c4_w1_keltner10_pos_tick2000_side | 9458 | 0.073 | -0.029 | 0.102 | 5.1 | 4/4 | 0.075 |
| K7 | asia | c4_krF_px_tick2000_side | 9222 | 0.076 | -0.030 | 0.106 | 5.1 | 4/4 | 0.104 |
| K7 | asia | c4_w1_vwma21_px_tick2000_side | 8942 | 0.078 | -0.028 | 0.106 | 5.0 | 4/4 | 0.097 |
| K7 | asia | c4_w1_kama34_px_tick2000_side | 8830 | 0.079 | -0.027 | 0.106 | 5.0 | 4/4 | 0.146 |
| K7 | asia | c4_w1_cmo9_tick2000_ewith | 2571 | 0.131 | 0.014 | 0.117 | 5.0 | 4/4 | 0.124 |
| K7 | asia | c4_w1_ichi_fast_lag_tick2000_side | 7601 | 0.084 | -0.016 | 0.100 | 5.0 | 4/4 | 0.102 |
| K7 | asia | c4_w1_ema21_px_tick2000_side | 9100 | 0.078 | -0.031 | 0.108 | 5.0 | 4/4 | 0.123 |
| K7 | asia | c4_w1_sma21_px_tick2000_side | 8970 | 0.078 | -0.028 | 0.106 | 5.0 | 4/4 | 0.102 |
| K7 | asia | c4_w1_rsi7_tick2000_side | 9276 | 0.074 | -0.028 | 0.103 | 5.0 | 4/4 | 0.083 |
| K7 | asia | c4_w1_keltner20_pos_tick2000_side | 9117 | 0.077 | -0.030 | 0.107 | 5.0 | 4/4 | 0.104 |
| K7 | asia | c4_rsima7_tick2000_side | 9286 | 0.074 | -0.028 | 0.102 | 4.9 | 4/4 | 0.083 |
| K7 | asia | c4_nweS_tick2000_side | 8930 | 0.079 | -0.030 | 0.109 | 4.9 | 4/4 | 0.128 |
| K7 | asia | c4_almaS_px_tick2000_side | 9007 | 0.077 | -0.027 | 0.104 | 4.9 | 4/4 | 0.085 |
| K7 | asia | c4_w1_ema8_px_tick2000_side | 9594 | 0.070 | -0.027 | 0.097 | 4.8 | 4/4 | 0.075 |
| K7 | asia | c4_w1_kama50_px_tick2000_side | 8660 | 0.079 | -0.025 | 0.104 | 4.8 | 4/4 | 0.180 |
| K7 | asia | c4_mcgF_slope_tick2000_side | 9555 | 0.070 | -0.026 | 0.097 | 4.8 | 4/4 | 0.081 |
| K7 | asia | c4_mcgF_px_tick2000_side | 9555 | 0.070 | -0.026 | 0.097 | 4.8 | 4/4 | 0.081 |
| P7 | nypm | c4_lrc_tick2000_eagainst | 63 | 0.534 | -0.018 | 0.553 | 4.8 | 4/4 | 0.858 |
| K7 | asia | c4_w1_donchian20_pos_tick2000_side | 8961 | 0.076 | -0.025 | 0.101 | 4.8 | 4/4 | 0.073 |
| K7 | asia | c4_don20_pos_tick2000_side | 8961 | 0.076 | -0.025 | 0.101 | 4.8 | 4/4 | 0.073 |
| K7 | asia | c4_nwe_tick2000_side | 9204 | 0.072 | -0.025 | 0.097 | 4.8 | 4/4 | 0.082 |

## B4 alternate bars: vol2000

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2257; |t|>2: 0 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_vol2000.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_vol2000_side | 145411 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_sig | 136017 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_rise | 139557 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_fresh5 | 85803 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_ewith_z1 | 19867 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_eagainst_z1 | 2162 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_eleave_z1 | 3324 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_eenter_z1 | 7719 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_ewith_z2 | 36706 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_eagainst_z2 | 4488 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_vol2000_side | 145411 | 0.75 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_sig | 136017 | 0.70 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_rise | 139557 | 0.72 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_fresh5 | 85803 | 0.44 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_ewith_z1 | 19867 | 0.10 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_eagainst_z1 | 2162 | 0.01 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_eleave_z1 | 3324 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_eenter_z1 | 7719 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_ewith_z2 | 36706 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol2000_eagainst_z2 | 4488 | 0.02 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 64 of 13094 session-condition cells pass (chance-level expectation under independence ~162 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_hullF_vol2000_fresh1 | 1035 | -0.100 | -0.074 | -3.4 | 0/4 | -0.183 |
| close | c4_w1_aroon50_vol2000_nodiv | 11840 | 0.115 | 0.071 | 2.9 | 4/4 | 0.161 |
| close | c4_w1_vortex21_vol2000_divwith | 1266 | -0.126 | -0.068 | -2.7 | 0/4 | -0.076 |
| close | c4_rviS_vol2000_divwith | 1289 | -0.126 | -0.064 | -2.6 | 0/4 | -0.094 |
| close | c4_ifvgS_in_vol2000_hold3 | 118 | -0.231 | -0.061 | -2.8 | 0/4 | -0.046 |
| close | c4_sdflipF_in_vol2000_side | 2253 | 0.081 | 0.057 | 2.5 | 4/4 | 0.099 |
| london | c4_w1_cmo21_vol2000_eleave | 1076 | 0.229 | 0.071 | 3.1 | 4/4 | 0.302 |
| london | c4_krS_dir_vol2000_fresh1 | 993 | -0.123 | -0.067 | -2.7 | 0/4 | -0.212 |
| london | c4_brkF_in_vol2000_side | 2866 | -0.099 | -0.065 | -2.7 | 0/4 | -0.071 |
| london | c4_kerS_abs_vol2000_lo_z1 | 45508 | -0.079 | -0.057 | -2.6 | 0/4 | -0.105 |
| london | c4_kerS_abs_vol2000_hi | 12180 | 0.079 | 0.057 | 2.6 | 4/4 | 0.105 |
| london | c4_w1_di21_vol2000_fresh5 | 14714 | -0.067 | -0.056 | -3.0 | 0/4 | -0.149 |
| nyam | c4_crsiF_vol2000_eleave | 1116 | 0.130 | 0.081 | 3.4 | 4/4 | 0.245 |
| nyam | c4_sdS_cnt_vol2000_fresh5 | 1059 | -0.136 | -0.078 | -3.2 | 0/4 | -0.117 |
| nyam | c4_sdF_cnt_vol2000_fresh5 | 1411 | -0.131 | -0.076 | -3.1 | 0/4 | -0.184 |
| nyam | c4_stPF_vol2000_fresh1 | 705 | -0.099 | -0.065 | -2.7 | 0/4 | -0.102 |
| nyam | c4_sebF_vol2000_eleave | 2327 | 0.081 | 0.063 | 3.0 | 4/4 | 0.240 |
| nyam | c4_alli_spread_vol2000_side | 20372 | 0.077 | 0.062 | 3.2 | 4/4 | 0.122 |
| nypm | c4_lrcS_vol2000_eleave | 223 | 0.315 | 0.082 | 3.7 | 4/4 | 0.519 |
| nypm | c4_lrcS_vol2000_side | 18809 | -0.126 | -0.076 | -3.1 | 0/4 | -0.122 |
| nypm | c4_eqsweepF_vol2000_against | 205 | -0.246 | -0.068 | -3.0 | 0/4 | -0.501 |
| nypm | c4_krF_dir_vol2000_side | 23261 | -0.078 | -0.057 | -2.6 | 0/4 | -0.043 |
| nypm | c4_mcg_px_vol2000_side | 23220 | -0.079 | -0.057 | -2.5 | 0/4 | -0.023 |
| nypm | c4_mcg_slope_vol2000_side | 23220 | -0.079 | -0.057 | -2.5 | 0/4 | -0.023 |
| pre | c4_ifvgS_near_vol2000_hold3 | 735 | -0.263 | -0.084 | -3.6 | 0/4 | -0.347 |
| pre | c4_w1_donchian50_width_vol2000_hi | 6745 | -0.182 | -0.083 | -3.3 | 0/4 | -0.180 |
| pre | c4_ifvgS_near_vol2000_against | 1484 | 0.232 | 0.082 | 3.4 | 4/4 | 0.023 |
| pre | c4_ifvgS_near_vol2000_side | 1251 | -0.198 | -0.077 | -3.2 | 0/4 | -0.283 |
| pre | c4_ifvgF_near_vol2000_against | 1871 | 0.159 | 0.075 | 3.0 | 4/4 | 0.081 |
| pre | c4_w1_hv_pct50_vol2000_hi | 7601 | -0.190 | -0.070 | -2.9 | 0/4 | -0.166 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (721 of 65461 cell-conditions pass; chance at t>2.5 alone ~405)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_kr_px_vol2000_side | 9373 | 0.077 | -0.034 | 0.111 | 5.6 | 4/4 | 0.147 |
| K7 | asia | c4_w1_rsi14_vol2000_side | 9380 | 0.077 | -0.034 | 0.111 | 5.5 | 4/4 | 0.145 |
| K7 | asia | c4_rsima14_vol2000_side | 9394 | 0.076 | -0.034 | 0.110 | 5.5 | 4/4 | 0.145 |
| K7 | asia | c4_kr_dir_vol2000_side | 9263 | 0.077 | -0.033 | 0.110 | 5.5 | 4/4 | 0.128 |
| K7 | asia | c4_ichi_kj_vol2000_side | 9304 | 0.078 | -0.034 | 0.112 | 5.4 | 4/4 | 0.078 |
| K7 | asia | c4_don20_pos_vol2000_side | 9441 | 0.077 | -0.036 | 0.113 | 5.4 | 4/4 | 0.121 |
| K7 | asia | c4_w1_donchian20_pos_vol2000_side | 9441 | 0.077 | -0.036 | 0.113 | 5.4 | 4/4 | 0.121 |
| K7 | asia | c4_w1_ema21_px_vol2000_side | 9536 | 0.075 | -0.034 | 0.109 | 5.4 | 4/4 | 0.122 |
| K7 | asia | c4_w1_willr21_vol2000_side | 9399 | 0.078 | -0.036 | 0.114 | 5.4 | 4/4 | 0.095 |
| K7 | asia | c4_w1_keltner20_pos_vol2000_side | 9578 | 0.075 | -0.034 | 0.109 | 5.3 | 4/4 | 0.117 |
| K7 | asia | c4_nweS_vol2000_side | 9306 | 0.075 | -0.031 | 0.106 | 5.2 | 4/4 | 0.109 |
| K7 | asia | c4_krF_px_vol2000_side | 9706 | 0.071 | -0.031 | 0.102 | 5.2 | 4/4 | 0.140 |
| K7 | asia | c4_ichiS_kj_vol2000_side | 9225 | 0.076 | -0.030 | 0.106 | 5.2 | 4/4 | 0.086 |
| K7 | asia | c4_w1_di14_vol2000_side | 8745 | 0.079 | -0.027 | 0.106 | 5.1 | 4/4 | 0.108 |
| K7 | asia | c4_w1_kama21_px_vol2000_side | 9335 | 0.072 | -0.026 | 0.098 | 5.1 | 4/4 | 0.111 |
| K7 | asia | c4_krS_px_vol2000_side | 9161 | 0.076 | -0.029 | 0.105 | 5.1 | 4/4 | 0.135 |
| K7 | asia | c4_w1_ema34_px_vol2000_side | 9271 | 0.074 | -0.029 | 0.103 | 5.0 | 4/4 | 0.146 |
| K7 | asia | c4_w1_keltner10_pos_vol2000_side | 10115 | 0.067 | -0.031 | 0.098 | 5.0 | 4/4 | 0.159 |
| K7 | asia | c4_mcgF_px_vol2000_side | 10231 | 0.065 | -0.030 | 0.095 | 5.0 | 4/4 | 0.156 |
| K7 | asia | c4_mcgF_slope_vol2000_side | 10231 | 0.065 | -0.030 | 0.095 | 5.0 | 4/4 | 0.156 |
| K7 | asia | c4_w1_di7_vol2000_side | 9052 | 0.074 | -0.025 | 0.099 | 4.9 | 4/4 | 0.081 |
| K7 | asia | c4_mcgS_slope_vol2000_side | 9272 | 0.074 | -0.028 | 0.102 | 4.9 | 4/4 | 0.147 |
| K7 | asia | c4_mcgS_px_vol2000_side | 9272 | 0.074 | -0.028 | 0.102 | 4.9 | 4/4 | 0.147 |
| K7 | asia | c4_w1_vwma34_px_vol2000_side | 9131 | 0.074 | -0.026 | 0.100 | 4.9 | 4/4 | 0.125 |
| K7 | asia | c4_almaS_slope_vol2000_side | 8765 | 0.077 | -0.024 | 0.101 | 4.9 | 4/4 | 0.077 |
| K7 | asia | c4_w1_sma34_px_vol2000_side | 9130 | 0.074 | -0.026 | 0.100 | 4.9 | 4/4 | 0.123 |
| K7 | asia | c4_ichiF_cloud_vol2000_hold3 | 6420 | 0.091 | -0.008 | 0.099 | 4.9 | 4/4 | 0.120 |
| K7 | asia | c4_w1_keltner40_pos_vol2000_side | 9173 | 0.074 | -0.026 | 0.101 | 4.8 | 4/4 | 0.152 |
| K7 | asia | c4_w1_stoch21_vol2000_ewith | 4197 | 0.112 | 0.004 | 0.107 | 4.8 | 4/4 | 0.140 |
| K7 | asia | c4_ichi_chikou_vol2000_side | 8835 | 0.074 | -0.021 | 0.096 | 4.8 | 4/4 | 0.084 |

## B4 alternate bars: vol500

Outcome = R (W-CF1 signals_all: every signal of the universe, taken = engine R, skipped = hypothetical 1m-bar R); lifts are in R per trade; the 95% CI and t are CLUSTER-ROBUST by calendar week (rescored with weekly clusters 2026-11-15). A second table on TAKEN trades only in net $ per base contract (engine fee) is in step3usd_<block>.parquet. Conditions with n_yes>=100 and n_no>=100 in ALL/ALL: 2246; |t|>2: 0 (chance expectation ~102 if independent; conditions are strongly correlated across timeframes and cluster counts are W-CF3's job). Full table (every condition x book x session cell, share yes, mean yes/no, win rate yes/no, lift with 95% CI, per-year and L6M/L3M/L1M lifts, years positive): `/mnt/l2/l2vast/_confl/cols_cf4/step3_alt_vol500.parquet`.

**top 10 positive lift (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_vol500_side | 160412 | 0.83 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_sig | 133962 | 0.69 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_rise | 137836 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_fresh5 | 83566 | 0.43 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_ewith_z1 | 17381 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_eagainst_z1 | 376 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_eleave_z1 | 946 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_eenter_z1 | 7820 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_ewith_z2 | 36711 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_eagainst_z2 | 943 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**top negative lift = candidate veto (ALL/ALL)**

| cond | n_yes | share | mean yes | mean no | lift [95% CI] | t | yrs+ | L6M lift | L3M lift |
|---|---|---|---|---|---|---|---|---|---|
| c4_wt_vol500_side | 160412 | 0.83 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_sig | 133962 | 0.69 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_rise | 137836 | 0.71 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_fresh5 | 83566 | 0.43 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_ewith_z1 | 17381 | 0.09 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_eagainst_z1 | 376 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_eleave_z1 | 946 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_eenter_z1 | 7820 | 0.04 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_ewith_z2 | 36711 | 0.19 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |
| c4_wt_vol500_eagainst_z2 | 943 | 0.00 | nan | nan | nan [nan, nan] | nan | 0/4 | nan | nan |

**Per session, same sign every year (>=3 years tested) and in L6M, cluster-robust |t|>2.5, shrunk lift (prior sd 0.05 R): 151 of 13038 session-condition cells pass (chance-level expectation under independence ~161 at |t|>2.5 before the sign filters)**

| session | cond | n_yes | lift R | shrunk | t | yrs+ | L6M lift |
|---|---|---|---|---|---|---|---|
| close | c4_w1_vwma200_px_vol500_fresh5 | 1223 | -0.104 | -0.071 | -3.0 | 0/4 | -0.170 |
| close | c4_sqzmF_mom_vol500_fresh1 | 735 | -0.103 | -0.070 | -3.0 | 0/4 | -0.148 |
| close | c4_w1_sma200_px_vol500_fresh5 | 1217 | -0.103 | -0.070 | -3.0 | 0/4 | -0.170 |
| close | c4_w1_ema200_px_vol500_fresh5 | 1171 | -0.105 | -0.068 | -2.9 | 0/4 | -0.213 |
| close | c4_w1_supertrend_10_3_vol500_rise | 410 | -0.119 | -0.067 | -2.7 | 0/4 | -0.252 |
| close | c4_stA_vol500_fresh1 | 410 | -0.119 | -0.067 | -2.7 | 0/4 | -0.252 |
| london | c4_ifvg_in_vol500_hold3 | 383 | 0.195 | 0.085 | 3.4 | 4/4 | 0.136 |
| london | c4_ifvgF_in_vol500_hold3 | 387 | 0.194 | 0.085 | 3.4 | 4/4 | 0.136 |
| london | c4_rsima21_vol500_eenter | 464 | -0.163 | -0.078 | -3.1 | 0/4 | -0.154 |
| london | c4_w1_rsi21_vol500_eenter | 464 | -0.163 | -0.078 | -3.1 | 0/4 | -0.154 |
| london | c4_brkS_in_vol500_hold3 | 579 | -0.181 | -0.069 | -2.8 | 0/4 | -0.163 |
| london | c4_w1_mfi14_vol500_eenter | 1045 | -0.109 | -0.066 | -2.7 | 0/4 | -0.076 |
| nyam | c4_w1_cmo21_vol500_ewith | 1521 | -0.096 | -0.073 | -3.4 | 0/4 | -0.044 |
| nyam | c4_stcF_vol500_divwith | 2017 | 0.095 | 0.071 | 3.2 | 4/4 | 0.040 |
| nyam | c4_w1_linreg_chan20_vol500_eagainst | 233 | 0.227 | 0.066 | 2.9 | 4/4 | 0.357 |
| nyam | c4_w1_keltner40_pos_vol500_eleave | 205 | 0.176 | 0.064 | 2.7 | 4/4 | 0.004 |
| nyam | c4_w1_linreg_chan50_vol500_ewith | 875 | -0.099 | -0.063 | -2.6 | 0/4 | -0.066 |
| nyam | c4_w1_cmo21_vol500_eenter | 919 | -0.090 | -0.062 | -2.7 | 0/4 | -0.035 |
| nypm | c4_ichiS_futcloud_vol500_fresh1 | 453 | -0.136 | -0.075 | -3.0 | 0/4 | -0.190 |
| nypm | c4_ichiF_cloud_vol500_against | 1376 | 0.099 | 0.071 | 3.1 | 4/4 | 0.066 |
| nypm | c4_sfpF_vol500_fresh5 | 2637 | 0.086 | 0.068 | 3.4 | 4/4 | 0.056 |
| nypm | c4_krS_px_vol500_side | 23700 | -0.090 | -0.067 | -3.1 | 0/4 | -0.005 |
| nypm | c4_w1_vwma50_px_vol500_side | 23568 | -0.090 | -0.066 | -3.0 | 0/4 | -0.018 |
| nypm | c4_w1_sma50_px_vol500_side | 23577 | -0.090 | -0.066 | -3.0 | 0/4 | -0.027 |
| pre | c4_stcF_vol500_divwith | 617 | 0.230 | 0.084 | 3.5 | 4/4 | 0.243 |
| pre | c4_w1_trix15_vol500_divwith | 965 | -0.210 | -0.083 | -3.4 | 0/4 | -0.251 |
| pre | c4_w1_hv_pct50_vol500_hi | 3128 | 0.155 | 0.078 | 3.1 | 4/4 | 0.108 |
| pre | c4_w1_stoch21_vol500_eleave | 348 | 0.189 | 0.078 | 3.2 | 4/4 | 0.274 |
| pre | c4_mcgF_px_vol500_nodiv | 7020 | 0.122 | 0.076 | 3.2 | 4/4 | 0.087 |
| pre | c4_w1_ichi_std_lag_vol500_rise | 916 | 0.125 | 0.072 | 2.9 | 4/4 | 0.261 |

**book x session cells: lift t>2.5, >=3 positive years, L6M lift positive (612 of 65346 cell-conditions pass; chance at t>2.5 alone ~405)**

| book | sess | cond | n_yes | mean yes | mean no | lift | t | yrs+ | L6M |
|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | c4_w1_ema50_px_vol500_side | 11401 | 0.062 | -0.047 | 0.108 | 5.0 | 4/4 | 0.179 |
| K7 | asia | c4_w1_ema100_px_vol500_side | 10490 | 0.068 | -0.041 | 0.109 | 5.0 | 4/4 | 0.140 |
| K7 | asia | c4_w1_stoch21_vol500_side | 10837 | 0.060 | -0.030 | 0.091 | 5.0 | 4/4 | 0.165 |
| K7 | asia | c4_w1_keltner40_pos_vol500_side | 11801 | 0.058 | -0.048 | 0.106 | 4.9 | 4/4 | 0.182 |
| K7 | asia | c4_w1_sma100_px_vol500_side | 10171 | 0.069 | -0.036 | 0.105 | 4.8 | 4/4 | 0.136 |
| K7 | asia | c4_rsima21_vol500_side | 11754 | 0.058 | -0.046 | 0.104 | 4.7 | 4/4 | 0.181 |
| K7 | asia | c4_w1_rsi21_vol500_side | 11751 | 0.058 | -0.046 | 0.104 | 4.7 | 4/4 | 0.181 |
| K7 | asia | c4_w1_vwma100_px_vol500_side | 10162 | 0.069 | -0.036 | 0.105 | 4.7 | 4/4 | 0.137 |
| K7 | asia | c4_w1_di14_vol500_side | 11534 | 0.058 | -0.038 | 0.096 | 4.7 | 4/4 | 0.138 |
| K7 | asia | c4_kr_dir_vol500_side | 12214 | 0.055 | -0.048 | 0.103 | 4.7 | 4/4 | 0.201 |
| K7 | asia | c4_w1_donchian20_pos_vol500_side | 12285 | 0.052 | -0.041 | 0.093 | 4.7 | 4/4 | 0.187 |
| K7 | asia | c4_don20_pos_vol500_side | 12285 | 0.052 | -0.041 | 0.093 | 4.7 | 4/4 | 0.187 |
| K7 | asia | c4_krS_dir_vol500_side | 11043 | 0.063 | -0.041 | 0.103 | 4.7 | 4/4 | 0.174 |
| K7 | asia | c4_w1_di21_vol500_side | 10956 | 0.062 | -0.036 | 0.097 | 4.7 | 4/4 | 0.175 |
| K7 | asia | c4_stPS_vol500_side | 8674 | 0.078 | -0.024 | 0.101 | 4.6 | 4/4 | 0.098 |
| K7 | asia | c4_kr_px_vol500_side | 12382 | 0.053 | -0.047 | 0.100 | 4.6 | 4/4 | 0.183 |
| K7 | asia | c4_w1_kama200_px_vol500_side | 10137 | 0.067 | -0.031 | 0.097 | 4.6 | 4/4 | 0.124 |
| K7 | asia | c4_mcgS_px_vol500_side | 12029 | 0.055 | -0.044 | 0.099 | 4.5 | 4/4 | 0.206 |
| K7 | asia | c4_mcgS_slope_vol500_side | 12029 | 0.055 | -0.044 | 0.099 | 4.5 | 4/4 | 0.206 |
| K7 | asia | c4_w1_willr21_vol500_side | 12207 | 0.053 | -0.040 | 0.093 | 4.5 | 4/4 | 0.209 |
| K7 | asia | c4_w1_kama100_px_vol500_side | 10519 | 0.066 | -0.036 | 0.102 | 4.5 | 4/4 | 0.118 |
| K7 | asia | c4_smie_vol500_side | 11096 | 0.058 | -0.031 | 0.089 | 4.5 | 4/4 | 0.184 |
| K7 | asia | c4_krS_px_vol500_side | 11625 | 0.058 | -0.042 | 0.100 | 4.5 | 4/4 | 0.212 |
| K7 | asia | c4_rfiltS_vol500_side | 12420 | 0.051 | -0.041 | 0.092 | 4.5 | 4/4 | 0.170 |
| K7 | asia | c4_ichi_kj_vol500_side | 11875 | 0.055 | -0.038 | 0.093 | 4.4 | 4/4 | 0.230 |
| K7 | asia | c4_w1_ema34_px_vol500_side | 12072 | 0.055 | -0.043 | 0.098 | 4.4 | 4/4 | 0.210 |
| K7 | asia | c4_qqe_vol500_side | 10619 | 0.061 | -0.029 | 0.090 | 4.4 | 4/4 | 0.175 |
| K7 | asia | c4_w1_macd8_17_9_line_vol500_side | 10617 | 0.060 | -0.026 | 0.086 | 4.4 | 4/4 | 0.172 |
| K7 | asia | c4_stPS_vol500_hold3 | 8424 | 0.077 | -0.019 | 0.096 | 4.4 | 4/4 | 0.097 |
| K7 | asia | c4_elderS_bear_vol500_side | 11097 | 0.057 | -0.027 | 0.084 | 4.3 | 4/4 | 0.182 |
