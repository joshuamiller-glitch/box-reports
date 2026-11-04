# DS3_SIGNALS_2013: signal-level out-of-sample of the six books' raw entries, 2013-2026 (DIS-Y)

**Failed-validation sentence (kept at the top as ordered): the 1-minute approximation of the LIVE STACK failed validation (weekly correlation 0.66 v1 / 0.69 calibrated vs the 0.80 bar, DS3_STACK_2013.md), so nothing below is the live stack's P&L; it is a different object: the books' raw entry streams with fixed brackets, 1-minute fills, no Trade-Health exits, no locks, no zones, no PE 45-s confirmation, no 70/30.**

Author ZL-2, 2026-11-04. Scope note l2vast/ds3/prereg/DISY_scope.md sha256 5c58bd1daa4ee58f988f50e97baab4a8febf89151aaf23c9da6125b9261e1cfc (DECISIONS.md, before any 2013-2023 statistic). Descriptive measurement; no hypothesis test, no PASS claim, nothing live. Code l2vast/ds3/code/dis_x/ (disy*.py, apx_*.py); full cell x year tables: l2vast/ds3/out/dis_y/ (v1_cell_year.csv, v2_cell_year.csv, *_book_year.csv, *_prepost.csv, *_episodes.csv, *_rolldd.csv).

## Plain sentence
Taken as raw entries with a fixed bracket, every one of the six books lost money on average in 2013-2022 (mean -0.6 to -2.4 points per trade after costs) and made money in 2023-26 (up to +4.5), so 2023-26 sits in the best 5% of the 2013-2023 block-bootstrap distribution for five of six books at fixed 60/60 points and 4 to 5 of 6 with a percent bracket; this says the entry signals alone had no stable positive edge before 2023 and that the 2023-26 window was an unusually good one for them, NOT that the live stack lost money before 2023 (its exits and filters are not in this object and cannot be tested before 2023).

## Setup (same code both periods)
Signals: KB, PE, SM, HM, MV, PB(=PB7) engines of bars_eng/be_lib.py on the box NQ 1-minute series (volume-front, additive back-adjusted), live sessions only, one position per book. Fill: next 1-minute bar open + 0.25 pt adverse; stop first on a same-bar touch; stop slip 1.5; flat slip 0.5; fee 0.242 pt/lot; flat 16:55 ET; 1 lot, $20/point. Net points per trade. Hit rate = share of trades exiting at the target. Two bracket variants, both reported:
* V1 FIXED: 60-point stop and target (the order). Caveat: NQ traded near 3,000 in 2013 and 21,000 in 2023-26, so 60 points is 2% of price in 2013 and 0.3% later; V1 hit rates in 2013-2016 are 1-18% (most trades end at the 16:55 flat), so V1 is not volatility-comparable across years.
* V2 PERCENT: stop = target = 60 x (that year's median raw close / 20,620, the 2023-04..2026-10 median) points, i.e. the same percent-of-price bracket every year; slippage and fee scaled the same way; points reported at 2023-26 price scale. This is the comparable variant for the pre/post question.
Weeks: ISO week of the label day. Equal-risk: each book x session cell weekly 1-lot P&L multiplied by (1/sd of that cell over the full history), normalised to mean weight 1 (the weights use post-2023 data too; a description, not a trading rule). Bootstrap: stationary block (mean 4 weeks), 2,000 draws of the 2013-2023-03 weeks, once at full length (CI of the pre mean) and once at the length of the 2023-26 window (percentile of the observed 2023-26 mean in that distribution; 1.00 means above all draws; this is a one-sided descriptive percentile, 6 books and 14 cells give about 1 in 20 by chance). Frames: pre = label days 2013-01-02..2023-04-02 (488 weeks), post = 2023-04-03..2026-10-30 (187 weeks).

## Per book: pre vs post, V2 PERCENT bracket (comparable)
| unit | n pre | n post | pts/trade pre (95% CI) | pts/trade post | percentile of post in pre-bootstrap (post-length) | hit pre | hit post | $/wk 1-lot pre | post | equal-risk $/wk pre | post |
|---|---|---|---|---|---|---|---|---|---|---|---|
| KB | 21562 | 7424 | -1.19 (-1.94, -0.42) | 0.09 | 0.97 | 0.478 | 0.488 | -956 | 71 | -863 | 78 |
| PE | 16227 | 5626 | -1.28 (-2.22, -0.33) | 0.11 | 0.95 | 0.487 | 0.502 | -778 | 66 | -709 | 29 |
| SM | 3633 | 1321 | -1.39 (-3.55, 0.70) | 1.66 | 0.96 | 0.489 | 0.516 | -188 | 238 | -281 | 353 |
| HM | 9065 | 3237 | -0.59 (-1.86, 0.74) | 1.22 | 0.95 | 0.487 | 0.507 | -200 | 428 | -183 | 419 |
| MV | 12503 | 4218 | -1.28 (-2.29, -0.26) | -0.80 | 0.73 | 0.484 | 0.492 | -599 | -363 | -481 | -284 |
| PB | 2705 | 1034 | -2.12 (-4.19, 0.05) | 3.98 | 1.00 | 0.482 | 0.537 | -215 | 444 | -258 | 534 |
| HM/asia | 4611 | 1622 | -1.42 (-3.36, 0.57) | 0.62 | 0.88 | 0.489 | 0.510 | -245 | 109 | -228 | 101 |
| HM/nyam | 4454 | 1615 | 0.27 (-1.44, 1.83) | 1.83 | 0.88 | 0.485 | 0.503 | 45 | 320 | 44 | 318 |
| KB/asia | 5561 | 1959 | -2.15 (-3.58, -0.74) | 1.68 | 1.00 | 0.485 | 0.519 | -447 | 355 | -384 | 305 |
| KB/london | 4693 | 1430 | -2.15 (-3.89, -0.49) | 0.11 | 0.94 | 0.488 | 0.505 | -378 | 18 | -355 | 17 |
| KB/nyam | 6650 | 2469 | -0.02 (-1.34, 1.31) | -1.06 | 0.20 | 0.489 | 0.486 | -6 | -282 | -5 | -225 |
| KB/nypm | 4658 | 1566 | -0.72 (-2.49, 1.08) | -0.12 | 0.66 | 0.445 | 0.439 | -125 | -20 | -119 | -19 |
| MV/london | 6422 | 2074 | -2.29 (-3.82, -0.79) | -2.09 | 0.56 | 0.483 | 0.487 | -550 | -469 | -439 | -375 |
| MV/nyam | 6081 | 2144 | -0.22 (-1.59, 1.06) | 0.46 | 0.72 | 0.486 | 0.496 | -50 | 106 | -42 | 90 |
| PB/asia | 2705 | 1034 | -2.12 (-4.22, 0.06) | 3.98 | 1.00 | 0.482 | 0.537 | -215 | 444 | -258 | 534 |
| PE/asia | 5315 | 1900 | -1.40 (-3.19, 0.31) | 0.87 | 0.93 | 0.490 | 0.512 | -279 | 180 | -239 | 154 |
| PE/london | 4549 | 1427 | -1.75 (-3.38, -0.05) | -1.00 | 0.70 | 0.492 | 0.498 | -297 | -154 | -305 | -158 |
| PE/nyam | 6363 | 2299 | -0.85 (-2.16, 0.41) | 0.16 | 0.83 | 0.481 | 0.496 | -201 | 40 | -165 | 33 |
| SM/asia | 1774 | 669 | -1.00 (-3.83, 1.77) | 3.11 | 0.95 | 0.492 | 0.528 | -66 | 225 | -99 | 334 |
| SM/london | 1859 | 652 | -1.75 (-4.64, 1.23) | 0.18 | 0.79 | 0.486 | 0.505 | -122 | 13 | -182 | 19 |

## Per book: pre vs post, V1 FIXED 60/60 points
| unit | n pre | n post | pts/trade pre (95% CI) | pts/trade post | percentile of post in pre-bootstrap (post-length) | hit pre | hit post | $/wk 1-lot pre | post | equal-risk $/wk pre | post |
|---|---|---|---|---|---|---|---|---|---|---|---|
| KB | 8269 | 7979 | -1.30 (-2.40, -0.14) | 0.32 | 0.94 | 0.381 | 0.490 | -402 | 279 | -324 | 247 |
| PE | 6682 | 6164 | -1.29 (-2.48, 0.02) | 0.95 | 0.97 | 0.380 | 0.508 | -322 | 634 | -338 | 568 |
| SM | 2802 | 1352 | -1.16 (-3.06, 0.73) | 3.03 | 0.99 | 0.288 | 0.527 | -122 | 443 | -184 | 612 |
| HM | 4876 | 3406 | -2.44 (-3.70, -1.07) | 2.93 | 1.00 | 0.331 | 0.521 | -444 | 1078 | -405 | 1011 |
| MV | 5604 | 4430 | -1.59 (-2.88, -0.34) | 0.25 | 0.96 | 0.353 | 0.500 | -334 | 121 | -263 | 129 |
| PB | 2119 | 1123 | -1.52 (-3.44, 0.54) | 4.49 | 1.00 | 0.287 | 0.541 | -121 | 545 | -131 | 594 |
| HM/asia | 3135 | 1773 | -3.26 (-5.06, -1.56) | 3.14 | 1.00 | 0.280 | 0.530 | -382 | 603 | -344 | 542 |
| HM/nyam | 1741 | 1633 | -0.95 (-3.00, 1.20) | 2.69 | 0.97 | 0.422 | 0.511 | -62 | 475 | -61 | 468 |
| KB/asia | 3347 | 2232 | -2.84 (-4.38, -1.28) | 1.51 | 1.00 | 0.302 | 0.517 | -355 | 364 | -281 | 288 |
| KB/london | 1243 | 1679 | -2.44 (-5.83, 0.67) | 0.27 | 0.84 | 0.468 | 0.507 | -113 | 49 | -121 | 53 |
| KB/nyam | 2229 | 2464 | -0.64 (-2.85, 1.85) | -0.72 | 0.47 | 0.440 | 0.487 | -53 | -192 | -42 | -151 |
| KB/nypm | 1450 | 1604 | 2.20 (-0.74, 5.24) | 0.33 | 0.26 | 0.399 | 0.439 | 119 | 58 | 120 | 58 |
| MV/london | 3569 | 2220 | -2.43 (-4.01, -0.89) | -1.27 | 0.80 | 0.300 | 0.493 | -324 | -305 | -254 | -239 |
| MV/nyam | 2035 | 2210 | -0.13 (-2.27, 2.07) | 1.78 | 0.83 | 0.445 | 0.508 | -10 | 426 | -8 | 368 |
| PB/asia | 2119 | 1123 | -1.52 (-3.50, 0.37) | 4.49 | 1.00 | 0.287 | 0.541 | -121 | 545 | -131 | 594 |
| PE/asia | 3315 | 2136 | -0.87 (-2.53, 0.83) | 2.17 | 0.99 | 0.311 | 0.523 | -108 | 502 | -94 | 434 |
| PE/london | 1247 | 1644 | -4.32 (-7.38, -1.43) | 0.39 | 0.95 | 0.455 | 0.509 | -201 | 70 | -234 | 81 |
| PE/nyam | 2120 | 2384 | -0.15 (-2.36, 2.29) | 0.24 | 0.56 | 0.442 | 0.495 | -12 | 62 | -10 | 53 |
| SM/asia | 1646 | 682 | 0.10 (-2.34, 2.51) | 4.50 | 0.98 | 0.278 | 0.540 | 6 | 332 | 8 | 445 |
| SM/london | 1156 | 670 | -2.95 (-5.86, -0.10) | 1.53 | 0.96 | 0.302 | 0.513 | -128 | 111 | -191 | 166 |

Reading: V2 mean points per trade pre vs post: KB -1.19 (CI -1.94, -0.42) vs +0.09 (percentile 0.97); PE -1.28 vs +0.11 (0.95); SM -1.39 vs +1.66 (0.96); HM -0.59 vs +1.22 (0.95); MV -1.28 vs -0.80 (0.73); PB -2.12 vs +3.98 (1.00). All six pre means are negative; five post means are positive; the pre CI excludes zero from above for KB, PE, MV (and for the cells KB/asia, KB/london, MV/london, PE/london in V2). Per cell, 2023-26 is NOT unusual (percentile below 0.9) for HM/asia 0.88, HM/nyam 0.88, KB/nyam 0.20 (post worse than pre), KB/nypm 0.66, MV/london 0.56, MV/nyam 0.72, PE/london 0.70, PE/nyam 0.84, SM/london 0.79; it is unusually good (>= 0.9) for KB/asia 1.00, KB/london 0.94, PB/asia 1.00, PE/asia 0.93, SM/asia 0.95. So the 2023-26 edge sits in the Asia-session cells and PB.

## Year by year (V2 PERCENT): mean net points per trade at 1 lot
| book | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | -0.92 | -0.34 | -1.84 | 1.96 | 4.22 | 2.49 | -1.23 | -0.32 | -2.78 | -3.50 | -2.35 | 2.46 | 4.29 | -0.84 |
| KB | -2.41 | -2.17 | -1.06 | 0.91 | -1.50 | 0.62 | -1.76 | -0.93 | -3.95 | -1.17 | -0.73 | 3.40 | -0.03 | -2.18 |
| MV | -1.33 | -0.86 | -2.11 | -0.11 | 0.77 | 0.21 | -1.83 | -1.27 | -1.90 | -2.51 | -1.43 | -0.30 | 0.93 | -2.63 |
| PB | -8.73 | -0.43 | -1.52 | -0.09 | 5.23 | 0.88 | -6.31 | -4.52 | -1.91 | -3.53 | 4.97 | 6.18 | 10.89 | -1.76 |
| PE | -4.22 | -0.00 | -3.19 | 1.03 | 0.62 | -1.61 | -0.53 | -1.51 | 0.83 | -3.29 | 2.04 | 1.04 | -0.28 | -0.90 |
| SM | -2.03 | 1.24 | -3.37 | -7.08 | 3.63 | -4.15 | 1.86 | 3.89 | 0.93 | -5.50 | -1.01 | 2.17 | 3.39 | 0.03 |

Signal counts per year (trades) V2:
| book | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | 623 | 663 | 806 | 808 | 552 | 973 | 846 | 1305 | 944 | 1317 | 819 | 841 | 904 | 901 |
| KB | 1246 | 1359 | 1840 | 1830 | 946 | 2418 | 1716 | 3548 | 2111 | 3982 | 1931 | 1878 | 2178 | 2003 |
| MV | 797 | 877 | 1124 | 1084 | 639 | 1322 | 1031 | 1844 | 1257 | 2185 | 1182 | 1080 | 1212 | 1087 |
| PB | 201 | 175 | 234 | 303 | 192 | 261 | 269 | 448 | 265 | 311 | 177 | 235 | 278 | 390 |
| PE | 925 | 982 | 1383 | 1369 | 736 | 1755 | 1355 | 2704 | 1607 | 2989 | 1398 | 1396 | 1646 | 1608 |
| SM | 299 | 281 | 351 | 348 | 270 | 357 | 338 | 445 | 355 | 499 | 333 | 353 | 349 | 376 |

Hit rate (target exits) V2:
| book | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | 0.474 | 0.478 | 0.478 | 0.504 | 0.478 | 0.518 | 0.479 | 0.502 | 0.469 | 0.478 | 0.480 | 0.518 | 0.529 | 0.489 |
| KB | 0.448 | 0.450 | 0.477 | 0.487 | 0.414 | 0.498 | 0.463 | 0.496 | 0.456 | 0.496 | 0.486 | 0.513 | 0.486 | 0.472 |
| MV | 0.473 | 0.477 | 0.480 | 0.490 | 0.460 | 0.500 | 0.472 | 0.496 | 0.480 | 0.486 | 0.490 | 0.494 | 0.504 | 0.478 |
| PB | 0.423 | 0.497 | 0.496 | 0.498 | 0.500 | 0.510 | 0.446 | 0.471 | 0.479 | 0.479 | 0.542 | 0.553 | 0.594 | 0.492 |
| PE | 0.453 | 0.482 | 0.472 | 0.503 | 0.458 | 0.488 | 0.486 | 0.495 | 0.507 | 0.480 | 0.519 | 0.511 | 0.496 | 0.495 |
| SM | 0.485 | 0.505 | 0.476 | 0.445 | 0.485 | 0.471 | 0.518 | 0.542 | 0.510 | 0.463 | 0.495 | 0.521 | 0.527 | 0.505 |

Weekly P&L at 1 lot, $ per week, V2:
| book | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | -216 | -86 | -561 | 608 | 895 | 914 | -392 | -159 | -1008 | -1774 | -741 | 780 | 1463 | -362 |
| KB | -1133 | -1112 | -734 | 642 | -544 | 566 | -1142 | -1246 | -3209 | -1791 | -540 | 2410 | -26 | -2083 |
| MV | -399 | -283 | -894 | -45 | 189 | 106 | -713 | -885 | -921 | -2112 | -651 | -123 | 426 | -1361 |
| PB | -662 | -29 | -134 | -11 | 386 | 87 | -641 | -764 | -195 | -423 | 339 | 548 | 1142 | -327 |
| PE | -1471 | -1 | -1664 | 540 | 175 | -1066 | -272 | -1541 | 515 | -3787 | 1099 | 548 | -173 | -691 |
| SM | -229 | 132 | -447 | -947 | 377 | -559 | 238 | 653 | 127 | -1055 | -130 | 289 | 446 | 5 |

Equal-risk weekly P&L, $ per week (cells scaled to equal weekly sd), V2:
| book | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | -221 | -76 | -520 | 582 | 843 | 865 | -236 | -250 | -962 | -1632 | -711 | 831 | 1423 | -396 |
| KB | -990 | -1004 | -603 | 606 | -479 | 448 | -1054 | -1204 | -2924 | -1636 | -442 | 2189 | -137 | -1661 |
| MV | -363 | -250 | -673 | -20 | 146 | 171 | -660 | -690 | -738 | -1721 | -547 | -193 | 570 | -1200 |
| PB | -782 | -63 | -162 | -13 | 464 | 107 | -756 | -946 | -234 | -508 | 407 | 757 | 1286 | -359 |
| PE | -1283 | -19 | -1445 | 403 | 170 | -999 | -194 | -1523 | 493 | -3392 | 935 | 301 | -264 | -392 |
| SM | -313 | 200 | -704 | -1411 | 561 | -741 | 326 | 905 | 189 | -1575 | -196 | 372 | 779 | -36 |

## Year by year (V1 FIXED 60/60): mean net points per trade at 1 lot
| book | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | -0.37 | -0.68 | -0.09 | -2.12 | 1.09 | -2.94 | -2.49 | -2.69 | -2.16 | -4.99 | -1.81 | 3.42 | 4.83 | 2.76 |
| KB | -3.41 | 1.09 | 0.37 | 1.82 | -0.93 | -4.60 | -1.56 | -0.47 | -1.71 | -2.26 | -0.28 | 3.56 | 0.61 | -1.13 |
| MV | -2.40 | 0.35 | -0.61 | -1.38 | 1.05 | -2.23 | -1.80 | -1.99 | -0.50 | -2.48 | -0.62 | -0.73 | 1.90 | -0.67 |
| PB | -0.27 | -1.27 | -0.14 | -4.68 | 0.63 | 0.89 | -4.15 | -2.63 | -0.25 | -4.50 | 4.81 | 8.44 | 7.62 | 1.41 |
| PE | -0.41 | -3.26 | 0.98 | -1.12 | -2.17 | -2.40 | 3.13 | -2.86 | 1.83 | -4.21 | 2.97 | 1.26 | 0.62 | 0.81 |
| SM | -1.51 | -0.25 | -1.50 | -1.59 | 5.45 | -4.33 | -5.41 | 2.93 | 1.03 | -4.51 | -0.25 | 3.90 | 2.95 | 2.73 |

Hit rate V1 (note the low early values: the 60-point target is rarely reached in the 2013-2016 price regime):
| book | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | 0.020 | 0.065 | 0.168 | 0.131 | 0.117 | 0.338 | 0.270 | 0.458 | 0.453 | 0.458 | 0.464 | 0.523 | 0.540 | 0.529 |
| KB | 0.016 | 0.076 | 0.168 | 0.150 | 0.113 | 0.331 | 0.281 | 0.470 | 0.443 | 0.477 | 0.454 | 0.510 | 0.494 | 0.493 |
| MV | 0.008 | 0.061 | 0.131 | 0.136 | 0.101 | 0.332 | 0.283 | 0.460 | 0.473 | 0.482 | 0.480 | 0.487 | 0.516 | 0.501 |
| PB | 0.017 | 0.045 | 0.178 | 0.120 | 0.096 | 0.367 | 0.312 | 0.465 | 0.478 | 0.467 | 0.537 | 0.571 | 0.568 | 0.520 |
| PE | 0.020 | 0.053 | 0.186 | 0.132 | 0.097 | 0.359 | 0.335 | 0.464 | 0.495 | 0.470 | 0.510 | 0.508 | 0.506 | 0.513 |
| SM | 0.004 | 0.090 | 0.154 | 0.132 | 0.122 | 0.321 | 0.277 | 0.501 | 0.490 | 0.467 | 0.487 | 0.535 | 0.526 | 0.530 |

Weekly P&L at 1 lot, $ per week, V1:
| book | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | -35 | -68 | -11 | -242 | 115 | -479 | -372 | -815 | -611 | -1802 | -461 | 1037 | 1755 | 1528 |
| KB | -330 | 115 | 48 | 233 | -108 | -1110 | -292 | -284 | -884 | -1997 | -135 | 2296 | 566 | -1591 |
| MV | -229 | 35 | -68 | -160 | 111 | -385 | -271 | -691 | -167 | -1269 | -200 | -279 | 967 | -469 |
| PB | -18 | -74 | -9 | -389 | 43 | 66 | -321 | -299 | -22 | -423 | 303 | 713 | 851 | 322 |
| PE | -39 | -327 | 119 | -137 | -233 | -468 | 523 | -1356 | 742 | -2744 | 1095 | 606 | 433 | 911 |
| SM | -135 | -22 | -136 | -149 | 499 | -402 | -494 | 381 | 120 | -687 | -26 | 500 | 413 | 569 |

Equal-risk weekly P&L, $ per week, V1:
| book | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | -23 | -62 | -20 | -221 | 114 | -399 | -370 | -757 | -557 | -1636 | -449 | 1043 | 1714 | 1319 |
| KB | -254 | 63 | 73 | 218 | -84 | -1013 | -196 | -72 | -880 | -1732 | -62 | 2132 | 450 | -1362 |
| MV | -189 | 30 | -52 | -131 | 93 | -283 | -246 | -528 | -118 | -1022 | -172 | -220 | 994 | -481 |
| PB | -17 | -96 | 0 | -424 | 47 | 73 | -331 | -351 | -23 | -461 | 331 | 870 | 868 | 351 |
| PE | -21 | -285 | 72 | -122 | -210 | -455 | 494 | -1538 | 647 | -2558 | 901 | 437 | 355 | 1049 |
| SM | -187 | -52 | -205 | -181 | 687 | -558 | -718 | 498 | 133 | -984 | -56 | 640 | 654 | 757 |

The per book x session x year versions of every table (counts, mean points, hit, weekly 1-lot and equal-risk) are in out/dis_y/v1_cell_year.csv and v2_cell_year.csv.

Year pattern (V2 mean points): the books were positive in some single pre-2023 years (HM 2016-2018; SM 2014, 2017, 2019-2021; PE 2016-17, 2021; KB 2016 and 2018; PB 2017-18) but negative in 2022 for all six (-1.2 to -5.5), and 2024-2025 are the best years for HM, SM, PB (KB 2024). 2026 is negative or near zero for KB -2.18, MV -2.63, PE -0.90, HM -0.84, PB -1.76, SM +0.03 (V2) while the live stack earned most of its money in 2026 ($22.6k/wk reference vs APX $8.6k/wk): which suggests (not proves) that the live 2026 profit is not carried by the raw entries but by the live exits, filters and lots (consistent with the failed validation).

## Drawdown clusters (equal-risk 1-lot weekly P&L, rolling windows, depth in units of the pre-2023 weekly sd of the series)
V2 PERCENT:
| window (wks) | unit | 2026 max rolling DD (sd) | 2023-25 | pre median | pre p95 | share of pre windows >= 2026 |
|---|---|---|---|---|---|---|
| 13 | KB | 7.1 | 7.3 | 3.5 | 8.4 | 0.113 |
| 13 | PE | 6.5 | 9.4 | 3.4 | 9.9 | 0.138 |
| 13 | SM | 6.0 | 7.7 | 3.5 | 9.0 | 0.216 |
| 13 | HM | 7.0 | 6.4 | 3.0 | 7.2 | 0.057 |
| 13 | MV | 6.7 | 7.2 | 3.3 | 7.8 | 0.090 |
| 13 | PB | 9.7 | 3.3 | 3.3 | 8.1 | 0.029 |
| 13 | STACK(6 books, equal-risk cells) | 8.7 | 4.4 | 3.8 | 9.6 | 0.063 |
| 26 | KB | 10.8 | 7.6 | 6.0 | 14.3 | 0.133 |
| 26 | PE | 8.9 | 9.4 | 5.8 | 14.6 | 0.224 |
| 26 | SM | 6.0 | 9.9 | 5.5 | 13.2 | 0.453 |
| 26 | HM | 9.6 | 8.4 | 5.2 | 10.2 | 0.114 |
| 26 | MV | 9.9 | 12.2 | 5.2 | 14.1 | 0.118 |
| 26 | PB | 9.7 | 5.5 | 6.0 | 12.1 | 0.186 |
| 26 | STACK(6 books, equal-risk cells) | 10.5 | 6.1 | 6.3 | 16.1 | 0.180 |

V1 FIXED (sd normalisation is dominated by low-volatility early years, so deeper numbers in sd units; use V2 for comparison):
| window (wks) | unit | 2026 max rolling DD (sd) | 2023-25 | pre median | pre p95 | share of pre windows >= 2026 |
|---|---|---|---|---|---|---|
| 13 | KB | 23.0 | 9.3 | 1.8 | 10.8 | 0.000 |
| 13 | PE | 11.9 | 15.7 | 2.1 | 11.8 | 0.050 |
| 13 | SM | 6.0 | 8.6 | 3.1 | 8.3 | 0.176 |
| 13 | HM | 12.1 | 8.0 | 2.4 | 10.3 | 0.011 |
| 13 | MV | 15.6 | 10.4 | 2.2 | 8.8 | 0.006 |
| 13 | PB | 8.0 | 5.3 | 2.9 | 8.9 | 0.076 |
| 13 | STACK(6 books, equal-risk cells) | 11.1 | 7.1 | 2.2 | 9.8 | 0.034 |
| 26 | KB | 28.0 | 9.3 | 3.5 | 15.7 | 0.000 |
| 26 | PE | 13.3 | 15.7 | 4.1 | 19.4 | 0.153 |
| 26 | SM | 6.0 | 12.9 | 5.0 | 14.3 | 0.373 |
| 26 | HM | 12.1 | 13.1 | 3.9 | 15.6 | 0.151 |
| 26 | MV | 15.6 | 14.4 | 4.2 | 15.5 | 0.051 |
| 26 | PB | 8.0 | 9.9 | 5.3 | 11.4 | 0.222 |
| 26 | STACK(6 books, equal-risk cells) | 11.1 | 8.4 | 3.7 | 17.7 | 0.192 |

Reading (V2): the 2026 rolling 13-week drawdown of the six-book equal-risk stack (8.7 sd) is exceeded by 6.3% of the 2013-2023 13-week windows, and by 18% of pre windows at 26 weeks (10.5 sd). Per book the 2026 cluster is unusual only for PB at 13 weeks (9.7 sd; 2.9% of pre windows as deep) and HM at 13 weeks (7.1 sd; 5.7%); KB, PE, SM and MV had comparable or deeper clusters in 2013-2023 (9-22% of pre windows at 13 weeks, 11-45% at 26). The worst pre clusters (end week; sd): stack 2022 W48 (19.4), 2022 W14 (17.6), 2021 W12 (14.1); KB 2021 W22 (20.1), 2020 W11 (11.9), 2016 W2 (11.8); PE 2022 W26 (18.2); SM 2015 W41 (18.2); HM 2022 W51 (17.2); MV 2022 W48 (22.4); PB 2020 W22 (15.5). Because the raw entries had a negative drift pre-2023 (stack equal-risk mean -$2.8k/wk pre vs +$1.1k/wk post in V2), pre-2023 drawdown clusters are frequent and the whole 2013-2022 stretch is one long decline; "cluster like 2026" is therefore not rare in this object, which again says it describes the entries, not the live stack's loss controls.

## What was not done
* Q4 single-mean-shift break tests and a DIS-U-style scan on the 1-minute series were NOT rerun: DS3_HISTORY_EXTENSION.md does not exist and DS3_DISCOVER2.md has no DIS-W text yet (ZL-1 aa1950d50b8350b1b owns the regime-episode scan and the bundle proxy; the bundle proxy needs trade lists that are not rebuildable here). I only report year tables and bootstrap percentiles.
* No DIS-V bootstrap rerun on a 2013-2026 pool (the stack is not reproducible; ordered stop).
Limits: costs are modelled at 2023-26 tick conditions in every year (2013-2016 spreads/slippage in index points were different; fee 0.242 constant); pre-2021 16:15-16:30 ET halt and the 2013-2015 17:00 ET Globex open are not modelled; additive back-adjust jumps use open-close at the roll bar; hit rate by exit type only; 488 + 187 weeks; equal-risk weights use full-history sd; the bootstrap preserves 4-week dependence only; MV and PE precision against the live entries was 0.67/0.72 so some entries here are ones the live book skipped.
